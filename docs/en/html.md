# HTML

Site Sync also lets you **edit the HTML of pages** and see the result in the preview.

## Where to find the HTML
Every visited page is saved under `site/`, using a "folder + `index.html`" layout:

| URL | Local file |
|---|---|
| `/` | `site/index.html` |
| `/products` | `site/products/index.html` |
| `/products/123` | `site/products/123/index.html` |
| `/about.html` | `site/about.html` |
| `/page.php` | `site/page.php.html` |

The easiest way: in the sidebar, **📄 Edit page HTML** (or *Site Sync: Open Page HTML*) opens the file of the page currently displayed.

## Editing a page
1. Open the HTML file, edit it, save (`Ctrl + S`).
2. Site Sync detects the change and **reloads the page** in the preview.
3. As long as the file differs from the original, it is **served instead of the remote page**.

## An unmodified page stays "live"
A page you have not touched is still served by the remote site (dynamic content, logged-in session). Its local copy is simply **refreshed** on every visit. If you put the file back to the original content, the page becomes live again.

> **Warning** — as soon as a page is modified locally, it is **frozen**: its dynamic content (data, CSRF tokens, displayed login state) no longer updates. Useful for testing a mock-up, but keep it in mind for personalized pages.

## What Site Sync rewrites (preview only)
Your local file stays **your HTML, as is**. On the fly, in the preview only: absolute URLs of your domain → relative, CDNs → proxy, `integrity` and CSP `<meta>` removed, live-reload client added. None of this is written to your file.

## Limitations
- The **query string is ignored**: `/search?q=a` and `/search?q=b` share the same file.
- HTML is **fully reloaded** (no partial DOM update, so JS state is not broken).
- HTML is compared with the server on every visit, not on *Refresh* (an anonymous request would not represent the logged-in page). A modified page is therefore not compared with the remote one: there is no *Download remote version* for HTML — delete the local file to start over.
- Only documents from **your domain** are saved. Setting: `downloadHtml` in `.vscode/site-sync.json`.
- HTML fragments loaded via `fetch`/XHR are not saved (only pages and iframes).
- Copies may contain personal data from your session: do not commit `site/` without checking.
