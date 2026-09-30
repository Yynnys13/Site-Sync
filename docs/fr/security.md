# Sécurité

## Chemins
Une URL distante ne contrôle jamais librement le chemin d'écriture. Chaque segment est décodé puis rejeté s'il vaut `.`/`..` ou contient `/`, `\` ou NUL (`%2e%2e`, `..%2f` inclus) ; les caractères interdits sont remplacés ; le chemin final est vérifié : il doit rester **dans `site/`**. Écriture en mode « ne jamais écraser » (`wx`).

## Réseau
- Le proxy écoute **uniquement sur 127.0.0.1** et refuse les en-têtes `Host` inattendus (anti DNS-rebinding).
- Aucune requête n'est envoyée vers un schéma autre que http/https.
- **Certificats invalides** : refusés par défaut (`siteSync.allowInsecureTls` pour les environnements de test).
- Redirections : suivies dans le proxy ; une navigation vers un **autre domaine** (OAuth, paiement) quitte la preview.
- Les **cookies du site ne sont jamais envoyés** aux domaines externes (CDN), et ceux des tiers ne sont pas conservés.

## Secrets
Site Sync ne demande, ne lit et ne stocke **aucun** mot de passe, cookie ou token. Les URLs avec identifiants sont refusées. Vous vous connectez dans la preview comme sur n'importe quel site : la session vit dans le navigateur (cookies de `127.0.0.1`).

> **Attention** — les ressources téléchargées peuvent contenir des clés/URLs sensibles côté client. N'ajoutez pas `site/` à un dépôt public sans vérification.

## Copies HTML
Les pages enregistrées peuvent contenir des données de votre session (nom, jetons CSRF…). Ne commitez pas `site/` publiquement sans relecture.

## Contenu non fiable
Les scripts du site et de ses tiers s'exécutent dans la preview comme sur le vrai site. Site Sync ne les analyse pas ; n'utilisez que des sites de confiance. Le CSP et l'`integrity` sont retirés dans la preview uniquement.

## Authentification : limitations
| Sujet | Comportement |
|---|---|
| Login par formulaire, cookies | Fonctionne (cookies réécrits pour `http://127.0.0.1`) ; un port fixe conserve la session |
| OAuth / SSO | La redirection vers le fournisseur quitte la preview ; le retour vers l'origine du site peut échouer (URL de callback enregistrée) |
| 2FA | Fonctionne si le flux reste sur le domaine du site |
| Cookies `__Host-`/`Secure` | `Secure` est retiré pour http local ; certains sites refusent |
| CORS | Les requêtes vers l'origine du site sont ramenées dans le proxy (même origine) |
| CSP | Retiré dans la preview |
