# リソース

## 保存されるもの
| 種類 | 拡張子 / MIME タイプ | ローカルフォルダー |
|---|---|---|
| HTML | 自ドメインの訪問済みページ | フォルダーごとの `index.html`([HTML](html.md) を参照) |
| CSS | `.css` | URLと同じパス |
| JavaScript | `.js` `.mjs` `.cjs` | 同上 |
| 画像 | png, jpg, gif, svg, webp, avif, ico… | 同上 |
| フォント | woff, woff2, ttf, otf, eot | 同上 |
| JSON | `.json`, `.webmanifest` | 同上 |
| その他 | xml, txt, map, wasm, 音声/動画 | 同上 |

**HTML** は保存されますが、変更された場合にのみローカルから配信されます([HTML](html.md))。拡張子が `.json` **ではない** JSON レスポンス(動的API)は保存**されません**。固定してしまうとサイトが壊れるためです。

## 外部ドメイン(CDN)
```
https://cdn.example.com/library.js   →   site/external/cdn.example.com/library.js
```
`https://example.com/library.js` → `site/library.js` と混同されることはありません。`downloadExternal` で無効にできます。

## クエリ文字列
`app.css?v=123` と `app.css?v=456` は**同じ**ローカルファイル(`app.css`)を指します。クエリはマッピングのキーに含まれません。

## プロジェクトのファイル
```
.vscode/
├── site-sync.json             ← 設定(シークレットなし)
└── site-sync-resources.json   ← マッピング URL → ファイル + ハッシュ
site/
├── assets/{css,js,images,fonts}/...
└── external/<ホスト>/...
```
