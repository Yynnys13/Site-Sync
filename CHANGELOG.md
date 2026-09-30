# Changelog

## 0.5.0
- New sidebar interface: compact dashboard that adapts to the state (before start / running), with native VS Code icons (codicons), site card with live-reload status, quick actions, colored resource bar by type, recent activity feed, recent sites, clearer error box with a "Show logs" button, footer with help and language selector. Works with light, dark and high-contrast themes.
- Resources view: badge with the number of files, site host as description, rich tooltips, and a right-click menu (reveal in explorer, open remote version, copy remote URL).
- Actions that used to be cut off or hard to read when the view was small are now always visible.

## 0.4.4
- Update Readme

## 0.4.3
- Update Readme

## 0.4.2
- Update Readme

## 0.4.1
- Update Readme

## 0.4.0
- Interface and documentation in English (default), Français and 日本語, with a language selector (sidebar, `Site Sync: Select Language`, `siteSync.language`); the change applies immediately.
- Localized manifest (`package.nls.*.json`), documentation in `docs/en`, `docs/fr`, `docs/ja`, READMEs in three languages.
- New `Open Page HTML` command, extension icon and logo set, HTML editing and proactive resource detection (see 0.2 / 0.3).
- Fixed a race between a download and a local read that could flag a file as "modified" by mistake.

## 0.3.1
- Logo Site Sync (icône Marketplace, barre d’activité monochrome, sidebar, guide, documentation) ; correction d’une course entre téléchargement et lecture locale qui pouvait marquer un fichier « modifié » à tort.

## 0.3.0
- Détection proactive des ressources référencées (HTML, CSS, modules JS) : URL résolue, testée, téléchargée si absente ; garde-fou contre les faux 404.

## 0.2.0
- HTML : les pages visitées sont enregistrées (dossier/index.html), servies localement une fois modifiées, rechargées à chaud ; commande « Open Page HTML ».

## 0.1.0
- Première version : proxy inverse local, interception et téléchargement des ressources, mapping persistant,
  remplacement par les fichiers locaux, live reload CSS (à chaud) et JS (reload), gestion des conflits, documentation intégrée.
