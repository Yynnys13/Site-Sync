# How to use Site Sync

Site Sync lets you **edit the HTML, CSS, JS and other resources of a remote website locally** and see the result live in a preview.

## 1. Enter a URL
In the **Site Sync** sidebar, type for example `https://example.com`.

## 2. Click Start
The site opens in the preview (VS Code's integrated browser). It is loaded **through a local proxy** (`http://127.0.0.1:4173`).

## 3. Wait for the resources
Site Sync fetches the resources actually loaded by the page (CSS, JS, images, fonts…) into the `site/` folder.

## 4. Edit the files
Open for example `site/assets/css/main.css` from Site Sync's **Resources** explorer.

## 5. Save
`Ctrl + S`.

## 6. See the result
CSS is applied **without reloading the page**. A modified JS or HTML file reloads the page.

## 7. Navigate
When you move to another page, missing resources are fetched automatically. Files that already exist are never downloaded again nor overwritten.

> **Note** — This guide opens automatically only once. Setting: `siteSync.showWelcome`. Command: *Site Sync: Open Getting Started*.

Going further: [Using Site Sync](usage.md) · [CSS](css.md) · [JavaScript](javascript.md).

## Importing a website
First open a **workspace folder** (File > Open Folder), then start the site. The `site/` folder and the `.vscode/site-sync.json` file are created there.
