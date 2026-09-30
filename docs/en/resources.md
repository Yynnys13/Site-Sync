# Resources

## What is stored
| Type | Extensions / MIME types | Local folder |
|---|---|---|
| HTML | visited pages of your domain | `index.html` per folder (see [HTML](html.md)) |
| CSS | `.css` | same path as the URL |
| JavaScript | `.js` `.mjs` `.cjs` | same |
| Images | png, jpg, gif, svg, webp, avif, ico… | same |
| Fonts | woff, woff2, ttf, otf, eot | same |
| JSON | `.json`, `.webmanifest` | same |
| Other | xml, txt, map, wasm, audio/video | same |

**HTML** is saved but only served locally once modified ([HTML](html.md)). JSON responses *without* a `.json` extension (dynamic APIs) are **not** stored: freezing them would break the site.

## External domains (CDNs)
```
https://cdn.example.com/library.js   →   site/external/cdn.example.com/library.js
```
Never mixed up with `https://example.com/library.js` → `site/library.js`. Can be disabled with `downloadExternal`.

## Query strings
`app.css?v=123` and `app.css?v=456` designate **the same** local file (`app.css`). The query is not part of the mapping key.

## Project files
```
.vscode/
├── site-sync.json             ← configuration (no secrets)
└── site-sync-resources.json   ← mapping URL → file + hashes
site/
├── assets/{css,js,images,fonts}/...
└── external/<host>/...
```
