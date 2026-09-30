# 同期

## 検出
`site/` 内で保存されたファイルは、*FileSystemWatcher* とエディターの保存イベントで検出されます。150 ms の*デバウンス*の後、**SHA-256 ハッシュ**が保存済みの値と比較され、内容が変わっていなければ何も起こりません。

## パスの先読み検出
Site Sync は、ブラウザーがリソースを要求するのを待ちません。HTML 内の参照を読み取ってサイトを基準に解決し、**実際のURLを試して**、無ければダウンロードします。

```html
<link rel="stylesheet" href="/css/styles.css">
<script type="module" src="/js/main.js"></script>
<link rel="shortcut icon" href="/assets/img/logo_32x32.png">
```

| 参照 | 試行されるURL(サイト `https://site.ex`、ページ `/products/123`) |
|---|---|
| `/css/styles.css` | `https://site.ex/css/styles.css` |
| `rel.js` | `https://site.ex/products/rel.js` |
| `../up.js` | `https://site.ex/up.js` |
| `//cdn.x.com/a.js` | `https://cdn.x.com/a.js` |

解析対象: `<link>`(stylesheet、preload、icon、manifest)、`<script>`、`<img>`/`srcset`、`<source>`、`<video>`/`<audio>`/`poster`、`<style>` と `style=""`、`<base href>`。さらに連鎖的に(最大4階層)、CSS の `url()` と `@import`、JS モジュールの `import` も解析します。既に存在するファイルは再ダウンロードされません。

- **404** は *出力 › Site Sync* に記録され(`Unable to download: … HTTP 404` 相当)、再試行されません。
- 存在しない `.css` に対して HTML ページを返すサーバー(「ソフト404」)は検出され、**何も保存されません**。
- ローカルファイルに `<link href="/css/new.css">` を手動で追加すると、保存した時点で取得されます。
- 無効化: `.vscode/site-sync.json` の `prefetchReferenced: false`。

## キャッシュ
各リソースについて、マッピングには URL、ローカルパス、`remoteHash`、`localHash`、`modifiedLocally`、種類、日時が保存されます。

```json
{
  "url": "https://example.com/assets/css/main.css",
  "localPath": "assets/css/main.css",
  "remoteHash": "abc123…", "localHash": "def456…",
  "modifiedLocally": true
}
```

## 新しいファイル
各ページで、要求されたリソースがローカルに無ければ、ダウンロードして書き込み(フォルダーも作成)、マッピングに追加します。既に存在する場合はダウンロード**しません**。ファイルを削除した場合は、次の要求で再ダウンロードされます。

## 競合
大原則: **ローカルでの変更は、自動的に上書きされることはありません。**

*更新* の際に、リモートのファイルが変更されていて、**かつ**ローカル版にも変更がある場合:

> ⚠ リモートのファイルが変更されました — `assets/css/main.css`。ローカル版にも変更があります。

| 選択肢 | 効果 |
|---|---|
| 自分の版を保持 | ローカルを保持します。リモート版は記憶され、再度尋ねられることはありません |
| リモート版をダウンロード | ローカルファイルを置き換えます |
| 比較 | `vscode.diff`(リモート ↔ ローカル)を開き、その後もう一度尋ねます |

メッセージを閉じても何も変わりません。競合は次回また提示されます。

正しいパスで `site/` に自分で置いたファイルは**採用**され(`modifiedLocally = true`)、リモートの代わりに配信されます。
