# HTML

Site Sync permet aussi de **modifier le HTML des pages** et de voir le résultat dans la preview.

## Où trouver le HTML
Chaque page visitée est enregistrée sous `site/`, sur le modèle « dossier + `index.html` » :

| URL | Fichier local |
|---|---|
| `/` | `site/index.html` |
| `/products` | `site/products/index.html` |
| `/products/123` | `site/products/123/index.html` |
| `/about.html` | `site/about.html` |
| `/page.php` | `site/page.php.html` |

Le plus simple : dans la sidebar, **📄 Modifier le HTML de la page** (ou *Site Sync: Open Page HTML*) ouvre le fichier de la page affichée.

## Modifier une page
1. Ouvrez le fichier HTML, modifiez-le, sauvegardez (`Ctrl + S`).
2. Site Sync détecte le changement et **recharge la page** dans la preview.
3. Tant que le fichier diffère de la version d'origine, il est **servi à la place de la page distante**.

## Page non modifiée = toujours « live »
Une page que vous n'avez pas touchée reste servie par le site distant (contenu dynamique, session connectée). Sa copie locale est simplement **rafraîchie** à chaque visite. Si vous remettez le fichier à l'identique de l'original, la page redevient live.

> **Attention** — dès qu'une page est modifiée localement, elle est **figée** : son contenu dynamique (données, jetons CSRF, état de connexion affiché) ne se met plus à jour. Utile pour tester une maquette, à garder en tête pour les pages personnalisées.

## Ce que Site Sync réécrit (preview uniquement)
Le fichier local reste **votre HTML tel quel**. À la volée, dans la preview seulement : URLs absolues de votre domaine → relatives, CDN → proxy, `integrity` et CSP `<meta>` retirés, client de live reload ajouté. Rien de cela n'est écrit dans votre fichier.

## Limitations
- La **query string est ignorée** : `/search?q=a` et `/search?q=b` partagent le même fichier.
- Le HTML est **rechargé en entier** (pas de mise à jour partielle du DOM, pour ne pas casser l'état du JS).
- Le HTML est comparé au serveur à chaque visite, pas lors de *Actualiser* (une requête anonyme ne représenterait pas la page connectée). Une page modifiée n'est donc pas comparée au distant : *Télécharger la version distante* n'existe pas pour le HTML — supprimez le fichier local pour repartir de zéro.
- Seuls les documents de **votre domaine** sont enregistrés. Réglage : `downloadHtml` dans `.vscode/site-sync.json`.
- Les fragments HTML chargés en `fetch`/XHR ne sont pas enregistrés (seulement les pages et iframes).
- Les copies peuvent contenir des données personnelles de votre session : ne versionnez pas `site/` sans vérifier.
