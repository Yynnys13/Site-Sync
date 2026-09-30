# Using Site Sync

## Adding a website
Type the URL in the sidebar (`example.com` is completed to `https://example.com`). A URL with a path (`https://example.com/products`) sets the start page. URLs containing credentials (`user:pass@`) are refused.

## Starting the website
Click **Start** or run *Site Sync: Start Website*. Site Sync:

1. checks that the site responds (otherwise a clear message is shown; details in **Output › Site Sync**);
2. starts the local proxy and opens the preview;
3. creates `.vscode/site-sync.json` and `site/`;
4. enables file watching and live reload.

## Navigating
Browse the preview normally. Each page (including route changes in a SPA) updates the **Current page** line, and new resources are downloaded.

## Refreshing
*Refresh* compares every resource with the server. Files **not modified locally** are updated; those you modified whose remote version changed trigger a [conflict decision](synchronization.md).

## Stopping a session
*Stop* shuts down the proxy and the file watcher. Your files and the mapping are kept; restarting the same site resumes where you left off.

## Changing the language
The interface and this documentation are available in **English** (default), **Français** and **日本語**. Use the *Language* selector at the bottom of the sidebar, the *Site Sync: Select Language* command, or the `siteSync.language` setting. The change applies immediately.

> **Note** — Command names and setting descriptions contributed to VS Code (palette, Settings UI) follow VS Code's own display language.

## Commands

| Command | Purpose |
|---|---|
| Site Sync: Start Website | Starts a session |
| Site Sync: Stop Website | Stops the session |
| Site Sync: Open Preview | (Re)opens the preview on the current page |
| Site Sync: Refresh | Compares with the remote site, handles conflicts, reloads |
| Site Sync: Open Website Folder | Reveals `site/` in the explorer |
| Site Sync: Open Page HTML | Opens the local HTML file of the current page |
| Site Sync: Select Language | English / Français / 日本語 |
| Site Sync: Open Documentation | This documentation |
| Site Sync: Open Getting Started | Getting started guide |

## VS Code settings

| Setting | Default | Description |
|---|---|---|
| `siteSync.language` | `en` | Interface and documentation language (`en`, `fr`, `ja`) |
| `siteSync.showWelcome` | `true` | Guide on first launch |
| `siteSync.previewTarget` | `simpleBrowser` | or `external` |
| `siteSync.proxyPort` | `4173` | A stable port keeps your cookies |
| `siteSync.allowInsecureTls` | `false` | Invalid certificates (not recommended) |
| `siteSync.openPreviewOnStart` | `true` | Open the preview on start |
