# Ressources

## Ce qui est stocké
| Type | Extensions / types MIME | Dossier local |
|---|---|---|
| HTML | pages visitées de votre domaine | `index.html` par dossier (voir [HTML](html.md)) |
| CSS | `.css` | même chemin que l'URL |
| JavaScript | `.js` `.mjs` `.cjs` | idem |
| Images | png, jpg, gif, svg, webp, avif, ico… | idem |
| Fonts | woff, woff2, ttf, otf, eot | idem |
| JSON | `.json`, `.webmanifest` | idem |
| Autres | xml, txt, map, wasm, audio/vidéo | idem |

Le **HTML** est enregistré mais n'est servi localement qu'une fois modifié ([HTML](html.md)). Les réponses JSON *sans* extension `.json` (API dynamiques) ne sont **pas** stockées : les figer casserait le site.

## Domaines externes (CDN)
```
https://cdn.example.com/library.js   →   site/external/cdn.example.com/library.js
```
Jamais confondu avec `https://example.com/library.js` → `site/library.js`. Désactivable avec `downloadExternal`.

## Query strings
`app.css?v=123` et `app.css?v=456` désignent **le même fichier** local (`app.css`). La query n'entre pas dans la clé de mapping.

## Fichiers du projet
```
.vscode/
├── site-sync.json             ← configuration (aucun secret)
└── site-sync-resources.json   ← mapping URL → fichier + hashs
site/
├── assets/{css,js,images,fonts}/...
└── external/<hôte>/...
```
