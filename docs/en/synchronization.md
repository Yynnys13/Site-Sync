# Synchronization

## Detection
A saved file in `site/` is detected by the *FileSystemWatcher* and by the editor's save event. After a 150 ms *debounce*, its **SHA-256 hash** is compared with the stored one: if the content did not change, nothing happens.

## Proactive path detection
Site Sync does not wait for the browser to request a resource: it reads the references in the HTML, resolves them against the site, then **tests the real URL** and downloads it if missing.

```html
<link rel="stylesheet" href="/css/styles.css">
<script type="module" src="/js/main.js"></script>
<link rel="shortcut icon" href="/assets/img/logo_32x32.png">
```

| Reference | URL tested (site `https://site.ex`, page `/products/123`) |
|---|---|
| `/css/styles.css` | `https://site.ex/css/styles.css` |
| `rel.js` | `https://site.ex/products/rel.js` |
| `../up.js` | `https://site.ex/up.js` |
| `//cdn.x.com/a.js` | `https://cdn.x.com/a.js` |

Analyzed: `<link>` (stylesheet, preload, icon, manifest), `<script>`, `<img>`/`srcset`, `<source>`, `<video>`/`<audio>`/`poster`, `<style>` and `style=""`, `<base href>`, then, cascading (up to 4 levels), the `url()` and `@import` of CSS files and the `import` statements of JS modules. Files that already exist are never downloaded again.

- A **404** is reported in *Output › Site Sync* (`Unable to download: … HTTP 404`) and is not retried.
- A server answering an HTML page for a missing `.css` (a "soft 404") is detected and **nothing is stored**.
- If you manually add `<link href="/css/new.css">` to a local file, it is fetched as soon as you save.
- Can be disabled: `prefetchReferenced: false` in `.vscode/site-sync.json`.

## Cache
For each resource, the mapping stores: URL, local path, `remoteHash`, `localHash`, `modifiedLocally`, type, date.

```json
{
  "url": "https://example.com/assets/css/main.css",
  "localPath": "assets/css/main.css",
  "remoteHash": "abc123…", "localHash": "def456…",
  "modifiedLocally": true
}
```

## New files
On every page, if a requested resource does not exist locally, it is downloaded, written (folders created) and added to the mapping. If it already exists: **no** download. If you delete a file, it will be downloaded again on the next request.

## Conflicts
Golden rule: **a local modification is never overwritten automatically.**

During a *Refresh*, if the remote file changed **and** your local version contains modifications:

> ⚠ The remote file has changed — `assets/css/main.css`. Your local version also contains changes.

| Choice | Effect |
|---|---|
| Keep my version | Keeps the local file; the remote version is remembered so you are not asked again |
| Download remote version | Replaces the local file |
| Compare | Opens `vscode.diff` (remote ↔ local), then asks again |

Closing the message changes nothing: the conflict will be offered again.

A file you place yourself in `site/` with the right path is **adopted** (`modifiedLocally = true`) and served instead of the remote one.
