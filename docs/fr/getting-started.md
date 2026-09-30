# Comment utiliser Site Sync

Site Sync vous permet de **modifier localement les CSS, JS et autres ressources d'un site distant** et de voir le résultat en direct dans une preview.

## 1. Entrer une URL
Dans la barre latérale **Site Sync**, saisissez par exemple `https://example.com`.

## 2. Cliquer sur Lancer
Le site s'ouvre dans la preview (navigateur intégré de VS Code). Il est chargé **via un proxy local** (`http://127.0.0.1:4173`).

## 3. Attendre la récupération
Site Sync récupère les ressources réellement chargées par la page (CSS, JS, images, fonts…) dans le dossier `site/`.

## 4. Modifier les fichiers
Ouvrez par exemple `site/assets/css/main.css` depuis l'explorateur **Ressources** de Site Sync.

## 5. Sauvegarder
`Ctrl + S`.

## 6. Voir le résultat
Le CSS est appliqué **sans recharger la page**. Un JS modifié recharge la page.

## 7. Naviguer
Quand vous changez de page, les ressources manquantes sont récupérées automatiquement. Les fichiers déjà présents ne sont jamais retéléchargés ni écrasés.

> **Note** — Ce guide s'ouvre automatiquement une seule fois. Réglage : `siteSync.showWelcome`. Commande : *Site Sync: Open Getting Started*.

Pour aller plus loin : [Utiliser Site Sync](usage.md) · [CSS](css.md) · [JavaScript](javascript.md).

## Importer un site
Ouvrez d'abord un **dossier de travail** (Fichier > Ouvrir un dossier), puis lancez le site. Le dossier `site/` et le fichier `.vscode/site-sync.json` y sont créés.
