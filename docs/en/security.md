# Security

## Paths
A remote URL never freely controls the write path. Every segment is decoded, then rejected if it is `.`/`..` or contains `/`, `\` or NUL (including `%2e%2e`, `..%2f`); forbidden characters are replaced; the final path is checked: it must stay **inside `site/`**. Files are written in "never overwrite" mode (`wx`).

## Network
- The proxy listens **on 127.0.0.1 only** and rejects unexpected `Host` headers (DNS-rebinding protection).
- No request is sent to a scheme other than http/https.
- **Invalid certificates**: refused by default (`siteSync.allowInsecureTls` for test environments).
- Redirects: followed inside the proxy; navigating to **another domain** (OAuth, payment) leaves the preview.
- The site's **cookies are never sent** to external domains (CDNs), and third-party cookies are not kept.

## Secrets
Site Sync never asks for, reads or stores **any** password, cookie or token. URLs with credentials are refused. You sign in inside the preview as on any website: the session lives in the browser (cookies of `127.0.0.1`).

> **Warning** — downloaded resources may contain client-side keys/URLs that are sensitive. Do not add `site/` to a public repository without checking.

## HTML copies
Saved pages may contain data from your session (name, CSRF tokens…). Do not commit `site/` publicly without reviewing it.

## Untrusted content
The scripts of the site and of its third parties run in the preview just as on the real site. Site Sync does not analyze them; only use sites you trust. CSP and `integrity` are removed in the preview only.

## Authentication: limitations
| Topic | Behavior |
|---|---|
| Form login, cookies | Works (cookies rewritten for `http://127.0.0.1`); a fixed port keeps the session |
| OAuth / SSO | The redirect to the provider leaves the preview; returning to the site's origin may fail (registered callback URL) |
| 2FA | Works if the flow stays on the site's domain |
| `__Host-`/`Secure` cookies | `Secure` is removed for local http; some sites refuse |
| CORS | Requests to the site's origin are brought into the proxy (same origin) |
| CSP | Removed in the preview |
