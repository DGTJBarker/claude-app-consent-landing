# claude-app-consent-landing

Static landing page served via GitHub Pages. Target of the Web RedirectUri on
the DGT Management multi-tenant Entra apps (Standard + Elevated).

When a client's Global Administrator clicks an admin-consent URL like

```
https://login.microsoftonline.com/{client-tenant-id}/adminconsent?client_id={app_id}
```

and grants consent, Microsoft redirects the browser to the configured Web
RedirectUri on the app. Previously `https://localhost`, which left admins
staring at a browser "can't reach this page" error — confusing because the
consent itself succeeded.

This repo hosts a single `index.html` that renders a clean "consent recorded"
acknowledgment so admins see an on-brand confirmation page instead of a
browser error.

## Live URL

**https://dgtjbarker.github.io/claude-app-consent-landing/**

Used as the Web RedirectUri on:

| App | AppId |
|---|---|
| DGT Management - Standard | `1fe456e7-06a7-43db-8ad7-5273817e69f7` |
| DGT Management - Elevated | `691169ef-fefd-40b8-add0-aee72d6dcf73` |

## Deploying changes

Edit `index.html` → commit + push. GitHub Pages auto-builds from `main`
branch root; changes live within ~30-60 seconds.

## Notes

- `<meta name="robots" content="noindex, nofollow">` on the page — we don't
  want search engines indexing a generic consent-landing URL.
- No JS, no external dependencies, no tracking. Pure static HTML + CSS.
- The page is intentionally generic: no client-specific identifiers, no
  session state. It's reached only from a successful consent flow.
