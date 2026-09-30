# Site Sync の使い方(詳細)

## サイトを追加する
サイドバーにURLを入力します(`example.com` は `https://example.com` に補完されます)。パス付きのURL(`https://example.com/products`)は開始ページになります。認証情報を含むURL(`user:pass@`)は拒否されます。

## サイトを開始する
**開始** をクリックするか、*Site Sync: Start Website* を実行します。Site Sync は次を行います。

1. サイトが応答するか確認します(応答しない場合は分かりやすいメッセージを表示。詳細は **出力 › Site Sync**)。
2. ローカルプロキシを起動し、プレビューを開きます。
3. `.vscode/site-sync.json` と `site/` を作成します。
4. ファイル監視とライブリロードを有効にします。

## ページを移動する
プレビュー内を通常どおり移動します。各ページ(SPA のルート変更を含む)で **現在のページ** の表示が更新され、新しいリソースがダウンロードされます。

## 更新する
*更新* は、すべてのリソースをサーバーと比較します。**ローカルで変更していない**ファイルは更新され、ローカルで変更済みでリモートも変わったファイルは[競合の判断](synchronization.md)が求められます。

## セッションを停止する
*停止* はプロキシとファイル監視を終了します。ファイルとマッピングは保持され、同じサイトを再開すると続きから作業できます。

## 言語を変更する
インターフェースとこのドキュメントは **English**(既定)、**Français**、**日本語** で利用できます。サイドバー下部の *言語* セレクター、*Site Sync: Select Language* コマンド、または `siteSync.language` 設定を使用します。変更はすぐに反映されます。

> **メモ** — VS Code に登録されるコマンド名や設定の説明(コマンドパレット、設定画面)は、VS Code 自体の表示言語に従います。

## コマンド

| コマンド | 内容 |
|---|---|
| Site Sync: Start Website | セッションを開始 |
| Site Sync: Stop Website | セッションを停止 |
| Site Sync: Open Preview | 現在のページでプレビューを(再)表示 |
| Site Sync: Refresh | リモートと比較し、競合を処理して再読み込み |
| Site Sync: Open Website Folder | `site/` をエクスプローラーで表示 |
| Site Sync: Open Page HTML | 現在のページのローカルHTMLファイルを開く |
| Site Sync: Select Language | English / Français / 日本語 |
| Site Sync: Open Documentation | このドキュメント |
| Site Sync: Open Getting Started | はじめにガイド |

## VS Code の設定

| 設定 | 既定値 | 説明 |
|---|---|---|
| `siteSync.language` | `en` | インターフェースとドキュメントの言語(`en`, `fr`, `ja`) |
| `siteSync.showWelcome` | `true` | 初回起動時のガイド |
| `siteSync.previewTarget` | `simpleBrowser` | または `external` |
| `siteSync.proxyPort` | `4173` | 固定ポートにするとCookieが維持されます |
| `siteSync.allowInsecureTls` | `false` | 無効な証明書(非推奨) |
| `siteSync.openPreviewOnStart` | `true` | 開始時にプレビューを開く |
