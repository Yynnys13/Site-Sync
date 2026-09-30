# CSS

## Where to find the CSS
The remote path is reproduced as is under `site/`:

```
https://example.com/assets/css/main.css   →   site/assets/css/main.css
```

CSS files also appear in Site Sync's **Resources › CSS** view (click = open).

## Editing a CSS file
1. Open the CSS file.
2. Edit the code.
3. Save (`Ctrl + S`).
4. Site Sync detects the change (after a short 150 ms *debounce*).
5. The preview applies the new CSS.

## Live reload
CSS is updated **hot**: the matching `<link rel="stylesheet">` is replaced by a reloaded copy, then the old one is removed. The page does not reload; JS state and scroll position are kept.

> **Limits** — If the CSS is not referenced by a `<link>` tag (for example an `@import` inside another CSS file, or an inline `<style>`), the whole page is reloaded. CSS injected dynamically by JavaScript follows the same rule.

Absolute `url(...)` and `@import` pointing to your domain are brought back into the proxy; those pointing to a CDN go through `/__ss_ext/…` so they are intercepted too.
