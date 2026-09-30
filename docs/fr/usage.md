# Utiliser Site Sync

## Ajouter un site
Saisissez l'URL dans la sidebar (`example.com` est complété en `https://example.com`). Une URL avec chemin (`https://example.com/products`) définit la page de départ. Les URLs contenant des identifiants (`user:pass@`) sont refusées.

## Lancer le site
Clic sur **Lancer** ou commande *Site Sync: Start Website*. Site Sync :

1. vérifie que le site répond (sinon un message clair s'affiche, détails dans **Output › Site Sync**) ;
2. démarre le proxy local et ouvre la preview ;
3. crée `.vscode/site-sync.json` et `site/` ;
4. active la surveillance des fichiers et le live reload.

## Naviguer
Naviguez normalement dans la preview. Chaque page (y compris les changements de route d'une SPA) met à jour la ligne **Page actuelle**, et les nouvelles ressources sont téléchargées.

## Actualiser
*Actualiser* compare chaque ressource au serveur. Les fichiers **non modifiés localement** sont mis à jour ; ceux que vous avez modifiés et qui ont changé côté serveur déclenchent une [décision de conflit](synchronization.md).

## Arrêter une session
*Arrêter* coupe le proxy et la surveillance. Vos fichiers et le mapping sont conservés ; relancer le même site reprend là où vous vous êtes arrêté.

## Changer de langue
L'interface et cette documentation existent en **English** (défaut), **Français** et **日本語**. Utilisez le sélecteur *Langue* en bas de la sidebar, la commande *Site Sync: Select Language* ou le réglage `siteSync.language`. Le changement est immédiat.

> **Note** — Les noms de commandes et descriptions de réglages fournis à VS Code (palette, écran Paramètres) suivent la langue d'affichage de VS Code elle-même.

## Commandes

| Commande | Rôle |
|---|---|
| Site Sync: Start Website | Lance une session |
| Site Sync: Stop Website | Arrête la session |
| Site Sync: Open Preview | (Ré)ouvre la preview sur la page courante |
| Site Sync: Refresh | Compare au distant, gère les conflits, recharge |
| Site Sync: Open Website Folder | Révèle `site/` dans l'explorateur |
| Site Sync: Open Page HTML | Ouvre le fichier HTML local de la page courante |
| Site Sync: Select Language | English / Français / 日本語 |
| Site Sync: Open Documentation | Cette documentation |
| Site Sync: Open Getting Started | Guide de démarrage |

## Réglages VS Code

| Réglage | Défaut | Description |
|---|---|---|
| `siteSync.language` | `en` | Langue de l'interface et de la documentation (`en`, `fr`, `ja`) |
| `siteSync.showWelcome` | `true` | Guide au premier lancement |
| `siteSync.previewTarget` | `simpleBrowser` | ou `external` |
| `siteSync.proxyPort` | `4173` | Port stable = cookies conservés |
| `siteSync.allowInsecureTls` | `false` | Certificats invalides (déconseillé) |
| `siteSync.openPreviewOnStart` | `true` | Ouvrir la preview au lancement |
