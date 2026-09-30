# JavaScript

## Where to find the JS
```
https://example.com/assets/js/app.js   →   site/assets/js/app.js
```
ES modules (`import`), dynamic `import()`, injected scripts and `fetch`/XHR requests go through the proxy: if they point to your domain, they are intercepted and replaced by the local version.

## Editing a JS file
Edit and save: Site Sync detects the change and **reloads the page** in the preview.

## Reloading
A full reload is the only **reliable** mechanism on an arbitrary site. Site Sync deliberately does not simulate "hot module replacement": re-evaluating a script live duplicates event listeners, global state and side effects.

## Limitations
- No HMR: every JS change reloads the page (page state is lost).
- Scripts from **another domain** whose URL is built dynamically in JS (absolute, not observable in the HTML) are not rewritten: they load directly from their domain.
- The site's *Service Workers* may serve cached resources without going through the proxy: disable them (Application › Service Workers) if you see stale versions.
- `integrity=` (SRI) and CSP `<meta>`/headers are removed **in the preview only**, otherwise modified files would be blocked.
- Code comparing `location.origin` with the original origin will see `http://127.0.0.1:PORT`.
- The site's WebSockets are not proxied (they connect directly).
