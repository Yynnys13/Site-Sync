<p align="center">
  <img src="https://github.com/Yynnys13/Site-Sync/blob/main/media/logo-wordmark.png" alt="Site Sync" width="320">
</p>

<p align="center">
  <b>Edit an existing website right from VS Code and see the result live.</b>
</p>

<p align="center">
  <b>English</b> ·
  <a href="README.fr.md">Français</a> ·
  <a href="README.ja.md">日本語</a>
</p>

---

> ⚠️ **Important notice — experimental project**
>
> Site Sync is a **young, experimental** project. Its code and interfaces were **generated with the help of artificial intelligence**, and the extension has **not been thoroughly tested in real-world conditions**. It may contain bugs, behave differently from one site to another, or not work at all on some of them.
>
> It is provided **as is, without any warranty**. Your feedback is very welcome: see [Reporting a problem](#-reporting-a-problem--contributing).

---

## 📖 Table of contents

1. [What is Site Sync?](#-what-is-site-sync)
2. [Video demo](#-video-demo)
3. [What is it for?](#-what-is-it-for)
4. [Installation](#-installation)
5. [Getting started in 5 minutes](#-getting-started-in-5-minutes)
6. [Discovering the interface](#-discovering-the-interface)
7. [Editing a site](#-editing-a-site)
8. [Browsing and new resources](#-browsing-and-new-resources)
9. [Refreshing and handling conflicts](#-refreshing-and-handling-conflicts)
10. [Signing in and user accounts](#-signing-in-and-user-accounts)
11. [Available commands](#-available-commands)
12. [Settings](#-settings)
13. [Where are my files stored?](#-where-are-my-files-stored)
14. [Security and privacy](#-security-and-privacy)
15. [Known limitations](#-known-limitations)
16. [Troubleshooting](#-troubleshooting)
17. [Frequently asked questions](#-frequently-asked-questions)
18. [Responsible use](#-responsible-use)
19. [Languages](#-languages)
20. [Reporting a problem / Contributing](#-reporting-a-problem--contributing)
21. [About](#-about)
22. [License](#-license)

---

## 🧭 What is Site Sync?

**Site Sync** is an extension for **Visual Studio Code** that lets you **work locally on a website that already exists online**.

You enter a website's address, and Site Sync:

1. **opens the site in a preview** built into VS Code;
2. **fetches to your computer** the files the site actually uses (styles, scripts, images, fonts, pages…);
3. **shows your local versions instead** of the remote ones;
4. **updates the preview live** as soon as you save a change.

You **never** touch the live website: everything happens on your machine, in your preview.

```text
Remote site  →  Files fetched  →  Your local files
                                        ↓
              Preview updated live  ←  You edit in VS Code
```

---

## 🎬 Video demo

A demo video shows the extension in action, from entering a site's address to changing its look and content live.

**▶️ Watch the video: `[VIDEO LINK TO ADD]`**
<video controls width="800">
  <source src="https://api-online.alwaysdata.net/media/site-ssync-exemple.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

What you can see in it:

- starting a session on a documentation website;
- the site displayed in VS Code's preview;
- the list of fetched resources, sorted by type (HTML, CSS, JavaScript, images, fonts);
- editing a stylesheet that turns the site into a **dark theme**, without reloading the page;
- editing a page's HTML (changing the logo text);
- new pages and several documentation versions being fetched automatically while browsing.

---

## 💡 What is it for?

Site Sync is designed for any situation where you want to **try a visual or content change on an existing site, without access to its original source code**:

- 🎨 **Test a new design** (colors, dark theme, fonts, spacing) on a real site.
- 🧪 **Prototype a change** before proposing it to a client or a team.
- 🔍 **Understand how a site is built** by exploring its files in your editor.
- 🛠️ **Fix a display issue** by trying several solutions live.
- 📚 **Learn web development** by editing real sites and seeing the effect immediately.
- 🖼️ **Prepare screenshots or mockups** from a real site.

Your changes stay **local**: they are only visible in your preview.

---

## 📥 Installation

### From VS Code (recommended)

1. Open VS Code.
2. Open the **Extensions** panel (`Ctrl + Shift + X`, or `Cmd + Shift + X` on Mac).
3. Search for **"Site Sync"** (publisher: *BunnyWhite*).
4. Click **Install**.

### From the Marketplace

Go to the extension page: <https://marketplace.visualstudio.com/items?itemName=BunnyWhite.site-sync> and click **Install**.

### Requirements

- **Visual Studio Code 1.85** or newer.
- **An open folder** in VS Code: this is where Site Sync stores the site's files.
- An **internet connection** to fetch the site the first time.

---

## 🚀 Getting started in 5 minutes

**1. Open a working folder**
In VS Code: *File › Open Folder*. Create a new empty one if you like.

**2. Open Site Sync**
Click the **Site Sync** icon in the activity bar (the vertical bar on the left of VS Code).

**3. Enter the site's address**
For example `https://example.com`. You can also simply type `example.com`: `https://` is added automatically. If you enter an address with a path (`https://example.com/products`), that page opens first.

**4. Click "Start"**
The site opens in the preview. The files it uses are gradually fetched into your working folder.

**5. Open a file and edit it**
In the **Resources** view, click a CSS file for example.

**6. Save (`Ctrl + S`)**
The change appears in the preview. 🎉

> 💡 A **getting started guide** appears automatically on first launch. You can reopen it at any time with the *Site Sync: Open Getting Started* command.

---

## 🖥️ Discovering the interface

Site Sync adds a dedicated section to VS Code's activity bar, made of two views.

### "Session" view

This is the extension's dashboard:

| Element | Purpose |
|---|---|
| **Site URL** | The field where you enter the address of the site to use |
| **Start / Stop** | Starts or stops the session |
| **Session** | Shows the state: *Stopped*, *Starting…* or *Connected* |
| **Current page** | The page displayed in the preview |
| **Resources** | The number of fetched files, and how many you have modified |
| **Actions** | Quick buttons: open the site, edit the page's HTML, open the files, refresh, stop |
| **Help** | Access to the documentation and the getting started guide |
| **Language** | Selector to change the interface language |

### "Resources" view

A tree listing all fetched files, **sorted by type**:

- **HTML**: the pages you visited
- **CSS**: stylesheets
- **JavaScript**: scripts
- **Images**: images and icons
- **Fonts**: font files
- **Other**: everything else (data, media…)

A simple **click** on a file opens it in the editor. Files you have modified are flagged.

### The preview

The preview is VS Code's built-in browser (*Simple Browser*). It displays the site **with your changes**. You can prefer an external browser (see [Settings](#-settings)).

---

## ✏️ Editing a site

### 🎨 Editing CSS (appearance)

Stylesheets are the ideal place to change colors, fonts, margins, and so on.

1. Open a CSS file from the **Resources** view.
2. Edit it.
3. Save (`Ctrl + S`).
4. **The preview updates instantly, without reloading the page**: your scroll position and the page's state are kept.

> ℹ️ If the stylesheet is included in a particular way (imported from another stylesheet, or written directly in the page), the preview **reloads the page** instead of updating it live. This is normal.

### 📄 Editing HTML (content and structure)

Every page you visit is saved in your working folder.

- Click **"Edit page HTML"** in the Session view (or run the *Site Sync: Open Page HTML* command): the file of the displayed page opens.
- Edit it and save: the page is **reloaded** with your version.

| Site address | Local file |
|---|---|
| `/` | `site/index.html` |
| `/products` | `site/products/index.html` |
| `/products/123` | `site/products/123/index.html` |
| `/about.html` | `site/about.html` |

**Good to know:**

- A page you **have not modified** always stays "live": it is served by the real site (up-to-date content, signed-in session…).
- As soon as a page is **modified by you**, **your version** is displayed. It is then **frozen**: its dynamic content (data, displayed sign-in state…) no longer updates. This is perfect for testing a mockup, but keep it in mind for personalized pages.
- To go back to the original page, **delete the page's local file**: it will be fetched again.

### ⚡ Editing JavaScript (behavior)

1. Open a JavaScript file from the **Resources** view.
2. Edit it and save.
3. The page is **fully reloaded** to apply the change.

The full reload is intentional: it is the only reliable way to apply a modified script on any site.

### 🖼️ Replacing an image, a font, etc.

Simply replace the file in your working folder **keeping the same name and location**. Site Sync adopts it and displays it instead of the original.

### ➕ Adding your own files

A file that you place yourself in the `site/` folder, **at the right path**, is automatically taken into account and served instead of the remote version.

---

## 🌐 Browsing and new resources

Browse normally in the preview, like on the real site:

- each new page updates the **Current page** line;
- files the page needs that you don't have yet are **fetched automatically**;
- files that are **already present are never downloaded again or overwritten**;
- if you delete a file, it will be fetched again the next time it is requested.

### Smart file detection

Site Sync doesn't wait for the browser to ask for a file: it **reads the pages, spots the files they use** (styles, scripts, images, fonts, icons…), checks that they really exist, then fetches them in advance. Detection even goes further: it follows files called **from other files** (for example an image or a font called by a stylesheet).

If a file cannot be found (404 error), the information is noted in the logs and **nothing is saved**. If a site returns an error page in place of a missing file (a "soft 404"), Site Sync detects it and does not save it either.

### What is fetched

| Type | Examples |
|---|---|
| HTML pages | The pages of **your site** that you visit |
| Styles | `.css` |
| Scripts | `.js`, JavaScript modules |
| Images | png, jpg, gif, svg, webp, avif, ico… |
| Fonts | woff, woff2, ttf, otf, eot |
| Data | `.json`, `.webmanifest` |
| Other | xml, txt, audio, video… |

**Dynamic responses** (for example data the site loads from an online service) are **not** saved: freezing them would break the site.

### Files hosted elsewhere (CDN)

Resources hosted on other domains are stored separately, in an `external` folder:

```text
https://cdn.example.com/library.js  →  site/external/cdn.example.com/library.js
```

### Addresses with parameters

`app.css?v=123` and `app.css?v=456` refer to **the same local file** (`app.css`). What follows the `?` is not taken into account when naming the file.

---

## 🔄 Refreshing and handling conflicts

The live site may change while you work. The **Refresh** button (or the *Site Sync: Refresh* command) compares your files with the site's:

- files you **have not modified** are updated;
- files you modified **and** that also changed on the site trigger a **conflict**.

> 🛡️ **Golden rule: a change you made is never overwritten automatically.**

When there is a conflict, a message offers three choices:

| Choice | What happens |
|---|---|
| **Keep my version** | Your file is kept. The remote version is remembered so you won't be asked again. |
| **Download remote version** | Your file is replaced by the site's. |
| **Compare** | A side-by-side view opens to see the differences, then you are asked again. |

Closing the message changes nothing: the conflict will be offered again.

> ℹ️ HTML is handled separately: it is compared with the site at each visit, not on refresh. To start over on a page, simply delete its local file.

### Stopping and resuming

**Stop** ends the session but **keeps all your files**. Restarting the same site picks up exactly where you left off.

---

## 🔐 Signing in and user accounts

Site Sync **never asks you** for a password, cookie or token, and **does not store any**. To sign in to a site, do it **directly in the preview**, like on any website.

| Situation | Behavior |
|---|---|
| Form sign-in (username / password) | ✅ Generally works |
| Two-factor authentication (2FA) | ✅ Works if everything stays on the site's domain |
| Sign-in through an external provider (Google, Microsoft, GitHub… / SSO) | ⚠️ May fail: the return to the site may be refused |
| Sites very strict about their origin (anti-bot, client certificates) | ❌ May not work |

**Tip:** to stay signed in from one launch to the next, always keep the same **port** in the settings (`siteSync.proxyPort`). If the port changes, your session is lost.

Entering a username and password in the address (`https://user:password@site.com`) is **not allowed**: this form is rejected.

---

## ⌨️ Available commands

Open the command palette with `Ctrl + Shift + P` (or `Cmd + Shift + P`) and type "Site Sync".

| Command | What it does |
|---|---|
| **Site Sync: Start Website** | Starts a session on a site |
| **Site Sync: Stop Website** | Stops the current session |
| **Site Sync: Open Preview** | (Re)opens the preview on the current page |
| **Site Sync: Refresh** | Compares with the live site, handles conflicts, reloads |
| **Site Sync: Open Website Folder** | Shows the site's files in the explorer |
| **Site Sync: Open Page HTML** | Opens the HTML file of the displayed page |
| **Site Sync: Select Language** | Changes the language (English / Français / 日本語) |
| **Site Sync: Open Documentation** | Opens the built-in documentation (available offline) |
| **Site Sync: Open Getting Started** | Reopens the getting started guide |

> Command names appear in English in the palette; setting descriptions follow VS Code's display language.

---

## ⚙️ Settings

Open *File › Preferences › Settings* (or `Ctrl + ,`) and search for **"Site Sync"**.

| Setting | Default | Description |
|---|---|---|
| `siteSync.language` | `en` | Interface and documentation language: `en`, `fr` or `ja` |
| `siteSync.showWelcome` | `true` | Shows the getting started guide on first launch |
| `siteSync.previewTarget` | `simpleBrowser` | Where the preview opens: `simpleBrowser` (VS Code's browser) or `external` (your usual browser) |
| `siteSync.proxyPort` | `4173` | Local port used. A fixed port lets you **stay signed in**. If the port is already taken, another one is chosen automatically. |
| `siteSync.allowInsecureTls` | `false` | Accepts invalid HTTPS certificates. **Avoid**, except in a test environment. |
| `siteSync.openPreviewOnStart` | `true` | Automatically opens the preview at launch |

### Advanced per-project settings

A `.vscode/site-sync.json` file is created in your working folder. It contains **no secrets**. Among other things, you can turn off:

| Option | Effect |
|---|---|
| `downloadHtml` | Stops saving HTML pages |
| `downloadExternal` | Stops saving files hosted on other domains (CDN) |
| `prefetchReferenced` | Disables fetching in advance the files spotted in pages |

---

## 📁 Where are my files stored?

In your working folder, Site Sync creates:

```text
your-folder/
├── .vscode/
│   ├── site-sync.json              ← configuration (no secrets)
│   └── site-sync-resources.json    ← list of fetched files and their state
└── site/
    ├── index.html                  ← site pages
    ├── assets/
    │   ├── css/
    │   ├── js/
    │   ├── images/
    │   └── fonts/
    └── external/
        └── cdn.example.com/…       ← files hosted on other domains
```

The layout of `site/` **mirrors the online site's**: `https://example.com/assets/css/main.css` becomes `site/assets/css/main.css`. You can therefore browse the folders as if you had a copy of the site.

---

## 🛡️ Security and privacy

Site Sync was designed with several safeguards:

- 🔒 **Everything stays on your machine**: the preview is only reachable from your computer (local address `127.0.0.1`).
- 📂 **Protected writing**: Site Sync can **only write inside the `site/` folder**. A malicious address cannot make it write elsewhere on your disk.
- 🚫 **No overwriting**: an existing file is never overwritten automatically.
- 🔑 **No secrets stored**: no password, cookie or token.
- 🍪 **Isolated cookies**: the site's cookies are never sent to external domains.
- 🔐 **Strict HTTPS by default**: invalid certificates are rejected.
- 🌍 **No exotic schemes**: only `http` and `https` addresses are used.

### ⚠️ Points to watch

- **Do not publish the `site/` folder without reviewing it.** Saved pages and files may contain information tied to **your session** (name, security tokens, technical keys or addresses). Do not put it in a public repository (for example GitHub) without checking.
- **In the preview, some of the site's protections are removed** (content security policy, file integrity checks); otherwise your modified files would be blocked. These protections are only removed **in the preview**, never in your files.
- **The site's scripts run in the preview** just like on the real site. Site Sync does not analyze them: **only use sites you trust**.

---

## ⚠️ Known limitations

Site Sync cannot work perfectly with every site. Here is what you should know:

- **No hot update for JavaScript**: each script change reloads the page (the page's state is lost).
- **HTML is fully reloaded**, not partially updated.
- **Address parameters are ignored** for pages: `/search?q=a` and `/search?q=b` share the same file.
- **The site's real-time connections** (WebSockets: chats, live notifications…) do not go through Site Sync.
- **Some sites' "Service Workers"** may display cached versions without going through Site Sync. If you see an old version, disable them from your browser's developer tools.
- **Files whose address is built dynamically** by the site (especially if hosted on another domain) are not replaced: they load directly from their source.
- **The site's address as seen by the site itself** is that of your local preview, which can bother sites that check their origin.
- **Incompatible sites**: those requiring their real address (strict external sign-in, anti-bot protection, client certificates…) may not work.
- **Page fragments loaded in the background** are not saved (only full pages and embedded frames).
- **A modified page is frozen**: its dynamic content no longer updates.

And as stated at the top: the extension is **experimental and not thoroughly tested in real-world conditions**. Unexpected behavior is possible.

---

## 🧰 Troubleshooting

Technical details of each session are recorded in the **Output › Site Sync** panel (*View › Output* menu, then choose "Site Sync" in the list).

| Problem | Likely cause / solution |
|---|---|
| *"Open a working folder first"* | Site Sync stores its files in your folder: use *File › Open Folder* |
| *"The connection was refused"* | The site is unreachable, or the address is wrong |
| *"The domain name could not be found"* | Check the spelling of the address |
| *"The server did not respond in time"* | The site is slow or down: try again later |
| *"The HTTPS certificate is invalid"* | Self-signed or expired certificate. If you trust the site, enable `siteSync.allowInsecureTls` |
| My CSS change doesn't show | Check the file is in `site/` at the right path, that it appears in the *Resources* view, and that no *Service Worker* is serving a cached copy |
| JavaScript reloads the whole page | This is normal: there is no hot update for scripts |
| Blank page or broken site | The site may depend on real-time connections, external sign-in or a specific address. Check the logs |
| I'm signed out at every launch | The port changes: set `siteSync.proxyPort` |
| A CDN file is not replaced | Its address is built dynamically by the site (see [Known limitations](#-known-limitations)) |
| A resource is not fetched (HTTP 404) | It doesn't exist on the site; the information is in the logs |
| The interface is in the wrong language | Use the *Language* selector in the sidebar or `siteSync.language` |
| File write error | A file and a folder share the same name (for example `/a` and `/a/b.css`) |
| A modified page no longer updates | Normal: it is frozen. Delete its local file to fetch it again |

---

## ❓ Frequently asked questions

**Do I modify the real site?**
No. All your changes stay on your computer and are only visible in your preview. Site Sync cannot send changes to the live site.

**Do I need access to the site's source code?**
No, that's the whole point: Site Sync fetches the files as the browser receives them.

**Can I use Site Sync offline?**
Not for a first launch: the site has to be fetched. The built-in documentation, however, is available offline. After a first fetch, your files stay on your disk.

**Does it work on password-protected sites?**
Yes in most cases: sign in inside the preview. See [Signing in and user accounts](#-signing-in-and-user-accounts).

**Can I use it on a site that isn't mine?**
Technically yes, but read the [Responsible use](#-responsible-use) section.

**Are my changes saved?**
Yes: they are simple files in your `site/` folder. Back them up and version them like any project (reviewing their content before sharing, see [Security](#-security-and-privacy)).

**Can I then apply my changes to the real site?**
Site Sync doesn't do that. It helps you **prepare and test** your changes; you then have to carry them over yourself into the original project.

**Why does a file I deleted come back?**
Because the site needs it again: Site Sync fetches it at the next request.

**Does the extension collect data about me?**
No. Site Sync neither asks for nor stores any password, cookie or token, and only works locally.

---

## 🤝 Responsible use

Site Sync is a **testing and learning** tool:

- Preferably use it **on your own sites**, or on sites you have **permission** to work on.
- Fetched content, images, fonts and scripts **remain the property of their authors**. Respect their licenses and copyrights.
- Do not republish or redistribute the files of a third-party site.
- Do not use the extension to deceive visitors, imitate a site (phishing) or bypass a protection.

You remain solely responsible for how you use the extension.

---

## 🌍 Languages

The interface and documentation are available in:

- 🇬🇧 **English** (default language)
- 🇫🇷 **Français**
- 🇯🇵 **日本語**

To change language: **Language** selector at the bottom of the Site Sync sidebar, the *Site Sync: Select Language* command, or the `siteSync.language` setting. The change is **immediate**.

---

## 🐞 Reporting a problem / Contributing

Since the extension is still young and lightly tested, **your feedback is very useful**:

- a site on which it doesn't work;
- unexpected behavior;
- an idea for improvement.

When reporting a problem, please include if possible:

1. the **version** of Site Sync and VS Code;
2. your **system** (Windows, macOS, Linux);
3. the **type of site** concerned (without personal data);
4. what you expected and what happened;
5. the relevant lines from the **Output › Site Sync** panel.

You can also leave a **review** on the extension's Marketplace page, or contact the author via the website below.

---

## 👤 About

**Site Sync** is developed by **Bunny_White**, of **Online Corps Studio**.

🌐 <https://studios.online-corps.net>

---

## 📄 License

Site Sync is released under the **MIT License**. See the [`LICENSE.txt`](LICENSE.txt) file for the full text.

---

<p align="center">
  <sub>Made with ❤️ by Bunny_White · Online Corps Studio<br>
  Experimental project — provided as is, without warranty.</sub>
</p>