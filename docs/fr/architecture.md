# Architecture

```
VS Code ── Sidebar / Ressources / Docs
   │
BrowserSession ──► ProxyServer (127.0.0.1) ◄── Simple Browser (preview)
   │                   │
   │             RequestHandler
   │        ┌──────────┼───────────┐
   │   fichier local ?  │   sinon forward vers le site distant
   │     (servi)        │   ├─ HTML : réécriture + client injecté
   │                    │   └─ CSS/JS/img/font : stockage + réponse
   ▼                    ▼
ResourceManager ─► site/ + .vscode/site-sync-resources.json
   ▲
FileWatcher ─► SyncManager (debounce, hash) ─► LiveReloadManager (SSE) ─► client.js dans la page
```

## Pourquoi un proxy inverse ?
Une Webview ne peut rien intercepter. Un navigateur piloté (Playwright, CDP `Fetch.fulfillRequest`) permet le remplacement, mais impose un Chromium séparé. Le proxy voit **toutes** les requêtes (dont `fetch`, XHR, `import()`) et fonctionne dans le navigateur intégré.

## Flux d'une requête
1. `GET /assets/css/main.css` → le proxy convertit en URL distante.
2. Fichier local existant ? → **servi** (sans requête distante).
3. Sinon → requête distante, réponse stockée dans `site/assets/css/main.css`, puis renvoyée.

## Arborescence du projet utilisateur
```
.vscode/
├── site-sync.json             configuration
└── site-sync-resources.json   mapping + cache
site/
├── assets/css|js|images|fonts
└── external/<hôte>/…          ressources de CDN
```

## Modules
`proxy/` (serveur, requêtes, réécriture) · `resources/` (stockage, mapping, téléchargement) · `sync/` (watcher, debounce, live reload, client) · `storage/` (config, métadonnées) · `ui/` (sidebar, arbre, docs, guide) · `i18n/` (en, fr, ja) · `utils/` (URL, chemins, hash, logs).

## Live reload : pourquoi SSE ?
Flux unidirectionnel serveur → page, reconnexion native, **zéro dépendance**. Un WebSocket n'apporterait rien ici.
