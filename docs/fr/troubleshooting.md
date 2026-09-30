# Dépannage

Les détails techniques sont dans **Output › Site Sync**.

| Problème | Cause probable / solution |
|---|---|
| « Ouvrez d'abord un dossier de travail » | Site Sync stocke les fichiers dans le workspace : *Fichier > Ouvrir un dossier* |
| « La connexion a été refusée » | Site injoignable ou mauvais port/URL |
| « Le certificat HTTPS est invalide » | Certificat auto-signé : activez `siteSync.allowInsecureTls` si le site est de confiance |
| Ma modification CSS n'apparaît pas | Vérifiez que le fichier est dans `site/` avec le bon chemin ; un Service Worker peut servir une copie en cache ; la ressource est-elle dans la vue *Ressources* ? |
| Le JS recharge toute la page | Normal : pas de HMR (voir [JavaScript](javascript.md)) |
| Page blanche / site cassé | Le site peut dépendre de WebSockets, d'OAuth ou d'une origine précise ; consultez les logs |
| Je suis déconnecté à chaque lancement | Le port change : fixez `siteSync.proxyPort` |
| Un CDN n'est pas remplacé | URL construite dynamiquement en JS (voir limitations JavaScript) |
| Ressource non récupérée (HTTP 404) | Le message est dans les logs ; les ressources en erreur ne sont pas stockées |
| Interface dans la mauvaise langue | Sélecteur *Langue* de la sidebar ou `siteSync.language` |
| Erreur d'écriture | Un fichier et un dossier portent le même nom (`/a` et `/a/b.css`) |
