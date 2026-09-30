<p align="center">
  <img src="media/logo-wordmark.png" alt="Site Sync" width="320">
</p>

<p align="center">
  <b>Modifiez un site web existant directement depuis VS Code et voyez le résultat en direct.</b>
</p>

<p align="center">
  <a href="README.md">English</a> ·
  <b>Français</b> ·
  <a href="README.ja.md">日本語</a>
</p>

---

> ⚠️ **Avis important — projet expérimental**
>
> Site Sync est un projet **jeune et expérimental**. Son code et ses interfaces ont été **générés avec l'aide d'une intelligence artificielle** et l'extension **n'a pas fait l'objet de tests approfondis en conditions réelles**. Elle peut donc contenir des bugs, se comporter différemment selon les sites, ou ne pas fonctionner du tout sur certains d'entre eux.
>
> Elle est proposée **telle quelle, sans garantie**. Vos retours sont précieux : voir [Signaler un problème](#-signaler-un-problème--contribuer).

---

## 📖 Sommaire

1. [C'est quoi, Site Sync ?](#-cest-quoi-site-sync-)
2. [Démonstration vidéo](#-démonstration-vidéo)
3. [À quoi ça sert ?](#-à-quoi-ça-sert-)
4. [Installation](#-installation)
5. [Premiers pas en 5 minutes](#-premiers-pas-en-5-minutes)
6. [Découvrir l'interface](#-découvrir-linterface)
7. [Modifier un site](#-modifier-un-site)
8. [Navigation et nouvelles ressources](#-navigation-et-nouvelles-ressources)
9. [Actualiser et gérer les conflits](#-actualiser-et-gérer-les-conflits)
10. [Connexion et comptes utilisateurs](#-connexion-et-comptes-utilisateurs)
11. [Commandes disponibles](#-commandes-disponibles)
12. [Réglages](#-réglages)
13. [Où sont rangés mes fichiers ?](#-où-sont-rangés-mes-fichiers-)
14. [Sécurité et confidentialité](#-sécurité-et-confidentialité)
15. [Limites connues](#-limites-connues)
16. [Dépannage](#-dépannage)
17. [Questions fréquentes](#-questions-fréquentes)
18. [Utilisation responsable](#-utilisation-responsable)
19. [Langues](#-langues)
20. [Signaler un problème / Contribuer](#-signaler-un-problème--contribuer)
21. [À propos](#-à-propos)
22. [Licence](#-licence)

---

## 🧭 C'est quoi, Site Sync ?

**Site Sync** est une extension pour **Visual Studio Code** qui vous permet de **travailler en local sur un site web qui existe déjà en ligne**.

Vous saisissez l'adresse d'un site, et Site Sync :

1. **ouvre le site dans un aperçu** intégré à VS Code ;
2. **récupère sur votre ordinateur** les fichiers réellement utilisés par le site (styles, scripts, images, polices, pages…) ;
3. **affiche vos versions locales à la place** de celles du site distant ;
4. **met à jour l'aperçu en direct** dès que vous enregistrez une modification.

Vous ne touchez **jamais** au site en ligne : tout se passe sur votre machine, dans votre aperçu.

```text
Site distant  →  Récupération des fichiers  →  Vos fichiers locaux
                                                     ↓
                     Aperçu mis à jour en direct  ←  Vous modifiez dans VS Code
```

---

## 🎬 Démonstration vidéo

Une vidéo de démonstration montre l'extension en action, de l'ajout de l'adresse d'un site jusqu'à la modification en direct de son apparence et de son contenu.

**▶️ Voir la vidéo : `[LIEN DE LA VIDÉO À AJOUTER]`**

Ce qu'on y voit :

- le lancement d'une session sur un site de documentation ;
- l'affichage du site dans l'aperçu de VS Code ;
- la liste des ressources récupérées, classées par type (HTML, CSS, JavaScript, images, polices) ;
- la modification d'une feuille de style qui transforme le site en **thème sombre**, sans recharger la page ;
- la modification du HTML d'une page (changement d'un texte du logo) ;
- la récupération automatique de nouvelles pages et de plusieurs versions de la documentation en naviguant.

---

## 💡 À quoi ça sert ?

Site Sync est pensé pour toutes les situations où vous voulez **tester un changement visuel ou de contenu sur un site existant, sans avoir accès à son code source d'origine** :

- 🎨 **Tester un nouveau design** (couleurs, thème sombre, polices, espacements) sur un vrai site.
- 🧪 **Prototyper une modification** avant de la proposer à un client ou à une équipe.
- 🔍 **Comprendre comment un site est construit** en explorant ses fichiers dans votre éditeur.
- 🛠️ **Corriger un défaut d'affichage** en essayant plusieurs solutions en direct.
- 📚 **Apprendre le développement web** en modifiant de vrais sites et en voyant tout de suite l'effet.
- 🖼️ **Préparer des captures d'écran ou des maquettes** à partir d'un site réel.

Les modifications restent **locales** : elles ne sont visibles que dans votre aperçu.

---

## 📥 Installation

### Depuis VS Code (recommandé)

1. Ouvrez VS Code.
2. Ouvrez le panneau **Extensions** (`Ctrl + Shift + X`, ou `Cmd + Shift + X` sur Mac).
3. Recherchez **« Site Sync »** (éditeur : *BunnyWhite*).
4. Cliquez sur **Installer**.

### Depuis la Marketplace

Rendez-vous sur la page de l'extension : <https://marketplace.visualstudio.com/items?itemName=BunnyWhite.site-sync> puis cliquez sur **Install**.

### Prérequis

- **Visual Studio Code 1.85** ou plus récent.
- **Un dossier ouvert** dans VS Code : c'est là que Site Sync range les fichiers du site.
- Une **connexion internet** pour récupérer le site la première fois.

---

## 🚀 Premiers pas en 5 minutes

**1. Ouvrez un dossier de travail**
Dans VS Code : *Fichier › Ouvrir un dossier*. Créez-en un nouveau et vide si vous le souhaitez.

**2. Ouvrez Site Sync**
Cliquez sur l'icône **Site Sync** dans la barre d'activité (la barre verticale à gauche de VS Code).

**3. Saisissez l'adresse du site**
Par exemple `https://example.com`. Vous pouvez aussi écrire simplement `example.com` : `https://` est ajouté automatiquement. Si vous indiquez une adresse avec un chemin (`https://example.com/produits`), c'est cette page qui s'ouvrira en premier.

**4. Cliquez sur « Lancer »**
Le site s'ouvre dans l'aperçu. Les fichiers qu'il utilise sont récupérés petit à petit dans votre dossier de travail.

**5. Ouvrez un fichier et modifiez-le**
Dans la vue **Ressources**, cliquez par exemple sur un fichier CSS.

**6. Enregistrez (`Ctrl + S`)**
Le changement apparaît dans l'aperçu. 🎉

> 💡 Un **guide de démarrage** s'affiche automatiquement au premier lancement. Vous pouvez le rouvrir à tout moment avec la commande *Site Sync: Open Getting Started*.

---

## 🖥️ Découvrir l'interface

Site Sync ajoute une section dédiée dans la barre d'activité de VS Code, composée de deux vues.

### Vue « Session »

C'est le tableau de bord de l'extension :

| Élément | Rôle |
|---|---|
| **URL du site** | Le champ où saisir l'adresse du site à utiliser |
| **Lancer / Arrêter** | Démarre ou stoppe la session |
| **Session** | Indique l'état : *Arrêté*, *Démarrage…* ou *Connecté* |
| **Page actuelle** | La page affichée dans l'aperçu |
| **Ressources** | Le nombre de fichiers récupérés, et combien ont été modifiés par vous |
| **Actions** | Boutons rapides : ouvrir le site, modifier le HTML de la page, ouvrir les fichiers, actualiser, arrêter |
| **Aide** | Accès à la documentation et au guide de démarrage |
| **Langue** | Sélecteur pour changer la langue de l'interface |

### Vue « Ressources »

Une arborescence qui liste tous les fichiers récupérés, **classés par type** :

- **HTML** : les pages visitées
- **CSS** : les feuilles de style
- **JavaScript** : les scripts
- **Images** : images et icônes
- **Polices** : fichiers de polices
- **Autres** : le reste (données, médias…)

Un simple **clic** sur un fichier l'ouvre dans l'éditeur. Les fichiers que vous avez modifiés sont signalés.

### L'aperçu

L'aperçu est le navigateur intégré de VS Code (*Simple Browser*). Il affiche le site **avec vos modifications**. Vous pouvez préférer un navigateur externe (voir [Réglages](#-réglages)).

---

## ✏️ Modifier un site

### 🎨 Modifier le CSS (apparence)

Les feuilles de style sont l'endroit idéal pour changer les couleurs, les polices, les marges, etc.

1. Ouvrez un fichier CSS depuis la vue **Ressources**.
2. Modifiez-le.
3. Enregistrez (`Ctrl + S`).
4. **L'aperçu se met à jour instantanément, sans recharger la page** : votre position de défilement et l'état de la page sont conservés.

> ℹ️ Si la feuille de style est intégrée d'une manière particulière (importée depuis une autre feuille, ou écrite directement dans la page), l'aperçu **recharge la page** au lieu de la mettre à jour à chaud. C'est normal.

### 📄 Modifier le HTML (contenu et structure)

Chaque page que vous visitez est enregistrée dans votre dossier de travail.

- Cliquez sur **« Modifier le HTML de la page »** dans la vue Session (ou lancez la commande *Site Sync: Open Page HTML*) : le fichier de la page affichée s'ouvre.
- Modifiez-le et enregistrez : la page est **rechargée** avec votre version.

| Adresse du site | Fichier local |
|---|---|
| `/` | `site/index.html` |
| `/produits` | `site/produits/index.html` |
| `/produits/123` | `site/produits/123/index.html` |
| `/a-propos.html` | `site/a-propos.html` |

**Bon à savoir :**

- Une page que vous **n'avez pas modifiée** reste toujours « vivante » : elle est servie par le vrai site (contenu à jour, session connectée…).
- Dès qu'une page est **modifiée par vous**, c'est **votre version** qui est affichée. Elle est alors **figée** : son contenu dynamique (données, état de connexion affiché…) ne se met plus à jour. C'est parfait pour tester une maquette, mais gardez-le en tête pour les pages personnalisées.
- Pour revenir à la page d'origine, **supprimez le fichier local** de la page : elle sera récupérée à nouveau.

### ⚡ Modifier le JavaScript (comportement)

1. Ouvrez un fichier JavaScript depuis la vue **Ressources**.
2. Modifiez-le et enregistrez.
3. La page est **rechargée entièrement** pour prendre en compte le changement.

Le rechargement complet est volontaire : c'est la seule façon fiable d'appliquer un script modifié sur n'importe quel site.

### 🖼️ Remplacer une image, une police, etc.

Remplacez simplement le fichier dans votre dossier de travail **en gardant le même nom et le même emplacement**. Site Sync l'adopte et l'affiche à la place de l'original.

### ➕ Ajouter vos propres fichiers

Un fichier que vous placez vous-même dans le dossier `site/`, **au bon chemin**, est automatiquement pris en compte et servi à la place de la version distante.

---

## 🌐 Navigation et nouvelles ressources

Naviguez normalement dans l'aperçu, comme sur le vrai site :

- chaque nouvelle page met à jour la ligne **Page actuelle** ;
- les fichiers dont la page a besoin et que vous n'avez pas encore sont **récupérés automatiquement** ;
- les fichiers **déjà présents ne sont jamais retéléchargés ni écrasés** ;
- si vous supprimez un fichier, il sera récupéré à nouveau à la prochaine demande.

### Détection intelligente des fichiers

Site Sync n'attend pas que le navigateur demande un fichier : il **lit les pages, repère les fichiers qu'elles utilisent** (styles, scripts, images, polices, icônes…), vérifie qu'ils existent réellement, puis les récupère à l'avance. Cette détection va même plus loin : elle suit les fichiers appelés **depuis d'autres fichiers** (par exemple une image ou une police appelée par une feuille de style).

Si un fichier est introuvable (erreur 404), l'information est notée dans les journaux et **rien n'est enregistré**. Si un site renvoie une page d'erreur à la place d'un fichier manquant (« faux 404 »), Site Sync le détecte et ne l'enregistre pas non plus.

### Ce qui est récupéré

| Type | Exemples |
|---|---|
| Pages HTML | Les pages de **votre site** que vous visitez |
| Styles | `.css` |
| Scripts | `.js`, modules JavaScript |
| Images | png, jpg, gif, svg, webp, avif, ico… |
| Polices | woff, woff2, ttf, otf, eot |
| Données | `.json`, `.webmanifest` |
| Autres | xml, txt, audio, vidéo… |

Les **réponses dynamiques** (par exemple les données chargées par le site depuis un service en ligne) ne sont **pas** enregistrées : les figer casserait le site.

### Fichiers hébergés ailleurs (CDN)

Les ressources hébergées sur d'autres domaines sont rangées à part, dans un dossier `external` :

```text
https://cdn.example.com/bibliotheque.js  →  site/external/cdn.example.com/bibliotheque.js
```

### Adresses avec paramètres

`app.css?v=123` et `app.css?v=456` désignent **le même fichier local** (`app.css`). Ce qui suit le `?` n'est pas pris en compte pour nommer le fichier.

---

## 🔄 Actualiser et gérer les conflits

Le site en ligne peut évoluer pendant que vous travaillez. Le bouton **Actualiser** (ou la commande *Site Sync: Refresh*) compare vos fichiers avec ceux du site :

- les fichiers que vous **n'avez pas modifiés** sont mis à jour ;
- les fichiers que vous avez modifiés **et** qui ont aussi changé sur le site déclenchent un **conflit**.

> 🛡️ **Règle d'or : une modification faite par vous n'est jamais écrasée automatiquement.**

En cas de conflit, un message vous propose trois choix :

| Choix | Ce qui se passe |
|---|---|
| **Garder ma version** | Votre fichier est conservé. La version distante est mémorisée pour ne plus vous redemander. |
| **Télécharger la version distante** | Votre fichier est remplacé par celui du site. |
| **Comparer** | Une vue côte à côte s'ouvre pour voir les différences, puis la question vous est reposée. |

Fermer le message ne change rien : le conflit vous sera reproposé.

> ℹ️ Le HTML est traité à part : il est comparé au site à chaque visite, pas lors d'une actualisation. Pour repartir de zéro sur une page, supprimez simplement son fichier local.

### Arrêter et reprendre

**Arrêter** met fin à la session mais **conserve tous vos fichiers**. Relancer le même site reprend exactement là où vous vous étiez arrêté.

---

## 🔐 Connexion et comptes utilisateurs

Site Sync **ne vous demande jamais** de mot de passe, de cookie ou de jeton, et **n'en enregistre aucun**. Pour vous connecter à un site, faites-le **directement dans l'aperçu**, comme sur n'importe quel site.

| Situation | Comportement |
|---|---|
| Connexion par formulaire (identifiant / mot de passe) | ✅ Fonctionne en général |
| Double authentification (2FA) | ✅ Fonctionne si tout reste sur le domaine du site |
| Connexion via un fournisseur externe (Google, Microsoft, GitHub… / SSO) | ⚠️ Peut échouer : le retour vers le site peut être refusé |
| Sites très stricts sur leur origine (anti-robots, certificats clients) | ❌ Peuvent ne pas fonctionner |

**Astuce :** pour rester connecté d'un lancement à l'autre, fixez toujours le même **port** dans les réglages (`siteSync.proxyPort`). Si le port change, votre session est perdue.

Il est **interdit** de saisir un identifiant et un mot de passe dans l'adresse (`https://utilisateur:motdepasse@site.com`) : cette forme est refusée.

---

## ⌨️ Commandes disponibles

Ouvrez la palette de commandes avec `Ctrl + Shift + P` (ou `Cmd + Shift + P`) et tapez « Site Sync ».

| Commande | Ce qu'elle fait |
|---|---|
| **Site Sync: Start Website** | Lance une session sur un site |
| **Site Sync: Stop Website** | Arrête la session en cours |
| **Site Sync: Open Preview** | (Ré)ouvre l'aperçu sur la page courante |
| **Site Sync: Refresh** | Compare avec le site en ligne, gère les conflits, recharge |
| **Site Sync: Open Website Folder** | Affiche les fichiers du site dans l'explorateur |
| **Site Sync: Open Page HTML** | Ouvre le fichier HTML de la page affichée |
| **Site Sync: Select Language** | Change la langue (English / Français / 日本語) |
| **Site Sync: Open Documentation** | Ouvre la documentation intégrée (disponible hors ligne) |
| **Site Sync: Open Getting Started** | Rouvre le guide de démarrage |

> Les noms de commandes restent en anglais dans la palette ; les descriptions des réglages suivent la langue d'affichage de VS Code.

---

## ⚙️ Réglages

Ouvrez *Fichier › Préférences › Paramètres* (ou `Ctrl + ,`) et cherchez **« Site Sync »**.

| Réglage | Par défaut | Description |
|---|---|---|
| `siteSync.language` | `en` | Langue de l'interface et de la documentation : `en`, `fr` ou `ja` |
| `siteSync.showWelcome` | `true` | Affiche le guide de démarrage au premier lancement |
| `siteSync.previewTarget` | `simpleBrowser` | Où s'ouvre l'aperçu : `simpleBrowser` (navigateur de VS Code) ou `external` (votre navigateur habituel) |
| `siteSync.proxyPort` | `4173` | Port utilisé en local. Un port fixe permet de **conserver votre connexion**. Si le port est déjà pris, un autre est choisi automatiquement. |
| `siteSync.allowInsecureTls` | `false` | Accepte les certificats HTTPS invalides. **À éviter**, sauf en environnement de test. |
| `siteSync.openPreviewOnStart` | `true` | Ouvre automatiquement l'aperçu au lancement |

### Réglages avancés par projet

Un fichier `.vscode/site-sync.json` est créé dans votre dossier de travail. Il ne contient **aucun secret**. Vous pouvez notamment y désactiver :

| Option | Effet |
|---|---|
| `downloadHtml` | N'enregistre plus les pages HTML |
| `downloadExternal` | N'enregistre plus les fichiers hébergés sur d'autres domaines (CDN) |
| `prefetchReferenced` | Désactive la récupération à l'avance des fichiers repérés dans les pages |

---

## 📁 Où sont rangés mes fichiers ?

Dans votre dossier de travail, Site Sync crée :

```text
votre-dossier/
├── .vscode/
│   ├── site-sync.json              ← configuration (aucun secret)
│   └── site-sync-resources.json    ← liste des fichiers récupérés et de leur état
└── site/
    ├── index.html                  ← pages du site
    ├── assets/
    │   ├── css/
    │   ├── js/
    │   ├── images/
    │   └── fonts/
    └── external/
        └── cdn.example.com/…       ← fichiers hébergés sur d'autres domaines
```

L'organisation de `site/` **reproduit celle du site en ligne** : `https://example.com/assets/css/main.css` devient `site/assets/css/main.css`. Vous pouvez donc naviguer dans les dossiers comme si vous aviez une copie du site.

---

## 🛡️ Sécurité et confidentialité

Site Sync a été conçu avec plusieurs garde-fous :

- 🔒 **Tout reste sur votre machine** : l'aperçu n'est accessible que depuis votre ordinateur (adresse locale `127.0.0.1`).
- 📂 **Écriture protégée** : Site Sync ne peut écrire **que dans le dossier `site/`**. Une adresse malveillante ne peut pas lui faire écrire ailleurs sur votre disque.
- 🚫 **Pas d'écrasement** : un fichier existant n'est jamais écrasé automatiquement.
- 🔑 **Aucun secret stocké** : ni mot de passe, ni cookie, ni jeton.
- 🍪 **Cookies isolés** : les cookies du site ne sont jamais envoyés aux domaines externes.
- 🔐 **HTTPS strict par défaut** : les certificats invalides sont refusés.
- 🌍 **Pas de schémas exotiques** : seules les adresses `http` et `https` sont utilisées.

### ⚠️ Points de vigilance

- **Ne publiez pas le dossier `site/` sans l'avoir relu.** Les pages et fichiers enregistrés peuvent contenir des informations liées à **votre session** (nom, jetons de sécurité, clés ou adresses techniques). Ne le mettez pas dans un dépôt public (par exemple GitHub) sans vérification.
- **Dans l'aperçu, certaines protections du site sont retirées** (politique de sécurité de contenu, vérifications d'intégrité des fichiers), sans quoi vos fichiers modifiés seraient bloqués. Ces protections ne sont retirées que **dans l'aperçu**, jamais dans vos fichiers.
- **Les scripts du site s'exécutent dans l'aperçu** comme sur le vrai site. Site Sync ne les analyse pas : **n'utilisez que des sites de confiance**.

---

## ⚠️ Limites connues

Site Sync ne peut pas fonctionner parfaitement avec tous les sites. Voici ce qu'il faut savoir :

- **Pas de mise à jour à chaud pour le JavaScript** : chaque modification d'un script recharge la page (l'état de la page est perdu).
- **Le HTML est rechargé en entier**, pas mis à jour partiellement.
- **Les paramètres d'adresse sont ignorés** pour les pages : `/recherche?q=a` et `/recherche?q=b` partagent le même fichier.
- **Les connexions en temps réel du site** (WebSockets : chats, notifications en direct…) ne passent pas par Site Sync.
- **Certains « Service Workers » de sites** peuvent afficher des versions en cache sans passer par Site Sync. Si vous voyez une ancienne version, désactivez-les depuis les outils de développement du navigateur.
- **Les fichiers dont l'adresse est fabriquée dynamiquement** par le site (surtout s'ils sont hébergés sur un autre domaine) ne sont pas remplacés : ils se chargent directement depuis leur source.
- **L'adresse du site vue par le site lui-même** est celle de votre aperçu local, ce qui peut gêner les sites qui vérifient leur adresse d'origine.
- **Sites incompatibles** : ceux qui exigent leur véritable adresse (connexion externe stricte, protection anti-robots, certificats clients…) peuvent ne pas fonctionner.
- **Les fragments de page chargés en arrière-plan** ne sont pas enregistrés (seulement les pages complètes et les cadres intégrés).
- **Une page modifiée est figée** : son contenu dynamique ne se met plus à jour.

Et comme indiqué en début de document : l'extension est **expérimentale et peu testée en conditions réelles**. Des comportements inattendus sont possibles.

---

## 🧰 Dépannage

Les détails techniques de chaque session sont consignés dans le panneau **Sortie › Site Sync** (menu *Affichage › Sortie*, puis choisissez « Site Sync » dans la liste).

| Problème | Cause probable / solution |
|---|---|
| *« Ouvrez d'abord un dossier de travail »* | Site Sync stocke ses fichiers dans votre dossier : faites *Fichier › Ouvrir un dossier* |
| *« La connexion a été refusée »* | Le site est injoignable, ou l'adresse est incorrecte |
| *« Le nom de domaine est introuvable »* | Vérifiez l'orthographe de l'adresse |
| *« Le serveur n'a pas répondu à temps »* | Le site est lent ou hors service : réessayez plus tard |
| *« Le certificat HTTPS est invalide »* | Certificat auto-signé ou expiré. Si le site est de confiance, activez `siteSync.allowInsecureTls` |
| Ma modification CSS n'apparaît pas | Vérifiez que le fichier est bien dans `site/` au bon chemin, qu'il apparaît dans la vue *Ressources*, et qu'aucun *Service Worker* ne sert une copie en cache |
| Le JavaScript recharge toute la page | C'est normal : il n'y a pas de mise à jour à chaud pour les scripts |
| Page blanche ou site cassé | Le site dépend peut-être de connexions en temps réel, d'une connexion externe ou d'une adresse précise. Consultez les journaux |
| Je suis déconnecté à chaque lancement | Le port change : fixez `siteSync.proxyPort` |
| Un fichier de CDN n'est pas remplacé | Son adresse est fabriquée dynamiquement par le site (voir [Limites connues](#-limites-connues)) |
| Une ressource n'est pas récupérée (HTTP 404) | Elle n'existe pas sur le site ; l'information est dans les journaux |
| L'interface est dans la mauvaise langue | Utilisez le sélecteur *Langue* de la barre latérale ou `siteSync.language` |
| Erreur d'écriture d'un fichier | Un fichier et un dossier portent le même nom (par exemple `/a` et `/a/b.css`) |
| Une page modifiée ne se met plus à jour | Normal : elle est figée. Supprimez son fichier local pour la récupérer de nouveau |

---

## ❓ Questions fréquentes

**Est-ce que je modifie le vrai site ?**
Non. Toutes vos modifications restent sur votre ordinateur et ne sont visibles que dans votre aperçu. Site Sync ne peut pas envoyer de changements vers le site en ligne.

**Ai-je besoin d'un accès au code source du site ?**
Non, c'est justement l'intérêt : Site Sync récupère les fichiers tels que le navigateur les reçoit.

**Puis-je utiliser Site Sync hors connexion ?**
Pas pour un premier lancement : il faut récupérer le site. La documentation intégrée, elle, est disponible hors ligne. Après une première récupération, vos fichiers restent sur votre disque.

**Ça marche sur les sites protégés par un mot de passe ?**
Oui dans la plupart des cas : connectez-vous dans l'aperçu. Voir [Connexion et comptes utilisateurs](#-connexion-et-comptes-utilisateurs).

**Puis-je l'utiliser sur un site qui n'est pas le mien ?**
Techniquement oui, mais lisez la section [Utilisation responsable](#-utilisation-responsable).

**Mes modifications sont-elles sauvegardées ?**
Oui : ce sont de simples fichiers dans votre dossier `site/`. Sauvegardez-les et versionnez-les comme n'importe quel projet (en relisant leur contenu avant de les partager, voir [Sécurité](#-sécurité-et-confidentialité)).

**Puis-je appliquer mes modifications sur le vrai site ensuite ?**
Site Sync ne fait pas cela. Il vous sert à **préparer et tester** vos changements ; vous devrez ensuite les reporter vous-même dans le projet d'origine.

**Pourquoi un fichier que j'ai supprimé revient-il ?**
Parce que le site en a de nouveau besoin : Site Sync le récupère à la prochaine demande.

**L'extension collecte-t-elle des données sur moi ?**
Non. Site Sync ne demande ni ne stocke de mot de passe, cookie ou jeton, et ne fonctionne qu'en local.

---

## 🤝 Utilisation responsable

Site Sync est un outil de **test et d'apprentissage** :

- Utilisez-le **de préférence sur vos propres sites**, ou sur des sites pour lesquels vous avez **l'autorisation** de travailler.
- Les contenus, images, polices et scripts récupérés **restent la propriété de leurs auteurs**. Respectez leurs licences et droits d'auteur.
- Ne republiez pas et ne redistribuez pas les fichiers d'un site tiers.
- N'utilisez pas l'extension pour tromper des visiteurs, imiter un site (hameçonnage) ou contourner une protection.

Vous restez seul responsable de l'usage que vous faites de l'extension.

---

## 🌍 Langues

L'interface et la documentation sont disponibles en :

- 🇬🇧 **English** (langue par défaut)
- 🇫🇷 **Français**
- 🇯🇵 **日本語**

Pour changer de langue : sélecteur **Langue** en bas de la barre latérale Site Sync, commande *Site Sync: Select Language*, ou réglage `siteSync.language`. Le changement est **immédiat**.

---

## 🐞 Signaler un problème / Contribuer

Comme l'extension est encore jeune et peu testée, **vos retours sont très utiles** :

- un site sur lequel elle ne fonctionne pas ;
- un comportement inattendu ;
- une idée d'amélioration.

Lorsque vous signalez un problème, indiquez si possible :

1. la **version** de Site Sync et de VS Code ;
2. votre **système** (Windows, macOS, Linux) ;
3. le **type de site** concerné (sans donnée personnelle) ;
4. ce que vous attendiez et ce qui s'est passé ;
5. les lignes utiles du panneau **Sortie › Site Sync**.

Vous pouvez aussi laisser un **avis** sur la page de l'extension dans la Marketplace, ou contacter l'auteur via le site ci-dessous.

---

## 👤 À propos

**Site Sync** est développé par **Bunny_White**, de **Online Corps Studio**.

🌐 <https://studios.online-corps.net>

---

## 📄 Licence

Site Sync est publié sous **licence MIT**. Consultez le fichier [`LICENSE.txt`](LICENSE.txt) pour le texte complet.

---

<p align="center">
  <sub>Fait avec ❤️ par Bunny_White · Online Corps Studio<br>
  Projet expérimental — fourni tel quel, sans garantie.</sub>
</p>