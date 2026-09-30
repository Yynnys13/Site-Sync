# アーキテクチャ

```
VS Code ── サイドバー / リソース / ドキュメント
   │
BrowserSession ──► ProxyServer (127.0.0.1) ◄── Simple Browser(プレビュー)
   │                   │
   │             RequestHandler
   │        ┌──────────┼───────────┐
   │   ローカルファイル?  │   なければリモートサイトへ転送
   │     (配信)          │   ├─ HTML: 書き換え + クライアント挿入
   │                     │   └─ CSS/JS/画像/フォント: 保存 + 応答
   ▼                     ▼
ResourceManager ─► site/ + .vscode/site-sync-resources.json
   ▲
FileWatcher ─► SyncManager(デバウンス、ハッシュ) ─► LiveReloadManager (SSE) ─► ページ内の client.js
```

## なぜリバースプロキシなのか
Webview は何も傍受できません。操作されるブラウザー(Playwright、CDP の `Fetch.fulfillRequest`)は置き換えを可能にしますが、別の Chromium が必要です。プロキシは(`fetch`、XHR、`import()` を含む)**すべての**リクエストを把握でき、内蔵ブラウザーでも動作します。

## リクエストの流れ
1. `GET /assets/css/main.css` → プロキシがリモートURLに変換します。
2. ローカルファイルがある? → **配信**します(リモートへのリクエストなし)。
3. なければ → リモートへリクエストし、応答を `site/assets/css/main.css` に保存してから返します。

## ユーザープロジェクトの構成
```
.vscode/
├── site-sync.json             設定
└── site-sync-resources.json   マッピング + キャッシュ
site/
├── assets/css|js|images|fonts
└── external/<ホスト>/…          CDN のリソース
```

## モジュール
`proxy/`(サーバー、リクエスト、書き換え) · `resources/`(保存、マッピング、ダウンロード、検出) · `sync/`(監視、デバウンス、ライブリロード、クライアント) · `storage/`(設定、メタデータ) · `ui/`(サイドバー、ツリー、ドキュメント、ガイド) · `i18n/`(en, fr, ja) · `utils/`(URL、パス、ハッシュ、ログ)。

## ライブリロードにSSEを使う理由
サーバー → ページの一方向ストリームで、再接続が組み込まれており、**依存関係ゼロ**です。ここでは WebSocket を使っても利点がありません。

## 言語
`src/i18n` には言語ごとのカタログがあります(`en.ts` がキーを定義し、`fr.ts` と `ja.ts` はそのすべてを実装する必要があります。テストで検証されます)。ドキュメントは `docs/<言語>/` にあり、英語がフォールバックです。
