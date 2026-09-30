# Synchronisation

## Détection
Un fichier de `site/` sauvegardé est détecté par le *FileSystemWatcher* et par l'événement de sauvegarde de l'éditeur. Après un *debounce* de 150 ms, son **hash SHA-256** est comparé à celui mémorisé : si le contenu n'a pas changé, rien ne se passe.

## Détection proactive des chemins
Site Sync n'attend pas que le navigateur demande une ressource : il lit les références du HTML, les résout par rapport au site, puis **teste l'URL réelle** et la télécharge si elle est absente.

```html
<link rel="stylesheet" href="/css/styles.css">
<script type="module" src="/js/main.js"></script>
<link rel="shortcut icon" href="/assets/img/logo_32x32.png">
```

| Référence | URL testée (site `https://site.ex`, page `/products/123`) |
|---|---|
| `/css/styles.css` | `https://site.ex/css/styles.css` |
| `rel.js` | `https://site.ex/products/rel.js` |
| `../up.js` | `https://site.ex/up.js` |
| `//cdn.x.com/a.js` | `https://cdn.x.com/a.js` |

Sont analysés : `<link>` (stylesheet, preload, icon, manifest), `<script>`, `<img>`/`srcset`, `<source>`, `<video>`/`<audio>`/`poster`, `<style>` et `style=""`, `<base href>`, puis, en cascade (4 niveaux max), les `url()` et `@import` des CSS et les `import` des modules JS. Les fichiers déjà présents ne sont jamais retéléchargés.

- Un **404** est signalé dans *Output › Site Sync* (`Impossible de télécharger : … HTTP 404`) et n'est pas retenté.
- Un serveur qui répond une page HTML pour un `.css` inexistant (« faux 404 ») est détecté et **rien n'est stocké**.
- Si vous ajoutez à la main `<link href="/css/new.css">` dans un fichier local, il est récupéré dès la sauvegarde.
- Désactivable : `prefetchReferenced: false` dans `.vscode/site-sync.json`.

## Cache
Pour chaque ressource, le mapping mémorise : URL, chemin local, `remoteHash`, `localHash`, `modifiedLocally`, type, date.

```json
{
  "url": "https://example.com/assets/css/main.css",
  "localPath": "assets/css/main.css",
  "remoteHash": "abc123…", "localHash": "def456…",
  "modifiedLocally": true
}
```

## Nouveaux fichiers
À chaque page, si une ressource demandée n'existe pas localement, elle est téléchargée, écrite (dossiers créés) et ajoutée au mapping. Si elle existe déjà : **aucun** téléchargement. Si vous supprimez un fichier, il sera retéléchargé à la prochaine requête.

## Conflits
Règle essentielle : **une modification locale n'est jamais écrasée automatiquement.**

Lors d'une *Actualisation*, si le fichier distant a changé **et** que votre version locale contient des modifications :

> ⚠ Le fichier distant a changé — `assets/css/main.css`. Votre version locale contient également des modifications.

| Choix | Effet |
|---|---|
| Garder ma version | Conserve le local ; la version distante est mémorisée pour ne plus redemander |
| Télécharger la version distante | Remplace le local |
| Comparer | Ouvre `vscode.diff` (distant ↔ local), puis vous redemande |

Fermer le message ne change rien : le conflit sera reproposé.

Un fichier que vous placez vous-même dans `site/` avec le bon chemin est **adopté** (`modifiedLocally = true`) et servi à la place du distant.
