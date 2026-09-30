# JavaScript

## Où trouver les JS
```
https://example.com/assets/js/app.js   →   site/assets/js/app.js
```
Les modules ES (`import`), `import()` dynamique, scripts injectés et requêtes `fetch`/XHR passent par le proxy : s'ils pointent vers votre domaine, ils sont interceptés et remplacés par la version locale.

## Modifier un JS
Modifiez, sauvegardez : Site Sync détecte le changement et **recharge la page** dans la preview.

## Rechargement
Un rechargement complet est le seul mécanisme **fiable** sur un site quelconque. Site Sync ne simule volontairement pas de « hot module replacement » : ré-évaluer un script à chaud duplique les écouteurs d'événements, l'état global et les effets de bord.

## Limitations
- Pas de HMR : chaque modification JS recharge la page (l'état de la page est perdu).
- Les scripts d'un **autre domaine** dont l'URL est construite dynamiquement en JS (absolue, non observable dans le HTML) ne sont pas réécrits : ils se chargent directement depuis leur domaine.
- Les *Service Workers* du site peuvent servir des ressources en cache sans passer par le proxy : désactivez-les (Application › Service Workers) si vous voyez des versions obsolètes.
- `integrity=` (SRI) et les CSP `<meta>`/en-têtes sont supprimés **dans la preview uniquement**, sinon les fichiers modifiés seraient bloqués.
- Le code qui compare `location.origin` à l'origine d'origine verra `http://127.0.0.1:PORT`.
- Les WebSockets du site ne sont pas proxifiés (ils se connectent directement).
