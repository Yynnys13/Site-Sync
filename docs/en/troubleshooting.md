# Troubleshooting

Technical details are in **Output › Site Sync**.

| Problem | Likely cause / solution |
|---|---|
| "Open a folder first" | Site Sync stores files in the workspace: *File > Open Folder* |
| "The connection was refused" | Site unreachable, or wrong URL/port |
| "The HTTPS certificate is invalid" | Self-signed certificate: enable `siteSync.allowInsecureTls` if you trust the site |
| My CSS change does not show | Check that the file is in `site/` with the right path; a Service Worker may serve a cached copy; is the resource listed in the *Resources* view? |
| JS reloads the whole page | Expected: no HMR (see [JavaScript](javascript.md)) |
| Blank page / broken site | The site may depend on WebSockets, OAuth or a specific origin; check the logs |
| I am signed out on every start | The port changes: set `siteSync.proxyPort` |
| A CDN is not replaced | URL built dynamically in JS (see JavaScript limitations) |
| Resource not fetched (HTTP 404) | The message is in the logs; failing resources are not stored |
| Write error | A file and a folder have the same name (`/a` and `/a/b.css`) |
| Interface in the wrong language | Use the *Language* selector in the sidebar or `siteSync.language` |
