# Architecture

```
VS Code ── Sidebar / Resources / Docs
   │
BrowserSession ──► ProxyServer (127.0.0.1) ◄── Simple Browser (preview)
   │                   │
   │             RequestHandler
   │        ┌──────────┼───────────┐
   │   local file?      │   otherwise forward to the remote site
   │     (served)       │   ├─ HTML: rewrite + injected client
   │                    │   └─ CSS/JS/img/font: store + respond
   ▼                    ▼
ResourceManager ─► site/ + .vscode/site-sync-resources.json
   ▲
FileWatcher ─► SyncManager (debounce, hash) ─► LiveReloadManager (SSE) ─► client.js in the page
```

## Why a reverse proxy?
A Webview cannot intercept anything. A driven browser (Playwright, CDP `Fetch.fulfillRequest`) allows replacement but requires a separate Chromium. The proxy sees **all** requests (including `fetch`, XHR, `import()`) and works in the integrated browser.

## Request flow
1. `GET /assets/css/main.css` → the proxy converts it to the remote URL.
2. Local file exists? → **served** (no remote request).
3. Otherwise → remote request, response stored in `site/assets/css/main.css`, then returned.

## User project layout
```
.vscode/
├── site-sync.json             configuration
└── site-sync-resources.json   mapping + cache
site/
├── assets/css|js|images|fonts
└── external/<host>/…          CDN resources
```

## Modules
`proxy/` (server, requests, rewriting) · `resources/` (storage, mapping, downloading, detection) · `sync/` (watcher, debounce, live reload, client) · `storage/` (config, metadata) · `ui/` (sidebar, tree, docs, guide) · `i18n/` (en, fr, ja) · `utils/` (URLs, paths, hash, logs).

## Live reload: why SSE?
One-way server → page stream, built-in reconnection, **zero dependencies**. A WebSocket would add nothing here.

## Languages
`src/i18n` holds one catalog per language (`en.ts` defines the keys, `fr.ts` and `ja.ts` must implement them all — enforced by a test). Documentation lives in `docs/<lang>/`, with English as fallback.
