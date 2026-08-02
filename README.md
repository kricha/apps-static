# kRicha Apps static website

A small, framework-free website for kRicha’s independent iOS apps. It contains the kRicha Apps developer hub plus app-specific support and privacy pages for Vault Docs and Soon.

The site uses plain HTML and CSS only. It has no package manager, build step, external fonts, scripts, trackers, cookies, forms, or runtime dependencies.

## File structure

```text
public/
  index.html
  404.html
  robots.txt
  _headers
  assets/
    styles.css
    vault-docs-icon.png  (optional; see below)
  vault-docs/
    support/
      index.html
    privacy/
      index.html
  soon/
    support/
      index.html
    privacy/
      index.html
README.md
```

## Preview locally

From the repository root, serve the `public` directory with any simple static file server. For example, if Python 3 is installed:

```sh
python3 -m http.server 8000 --directory public
```

Then open `http://localhost:8000/`. Check these clean directory URLs:

- `http://localhost:8000/vault-docs/support/`
- `http://localhost:8000/vault-docs/privacy/`

Opening files directly from the filesystem is not recommended because root-relative links such as `/assets/styles.css` expect a web server.

## Edit Vault Docs content

- Support information is in `public/vault-docs/support/index.html`.
- Privacy information is in `public/vault-docs/privacy/index.html`.
- Shared presentation styles are in `public/assets/styles.css`.

Keep support and privacy statements specific to Vault Docs. Review privacy disclosures whenever the app’s data practices, encryption behavior, advertising, analytics, purchases, or third-party services change.

To update the privacy policy date, edit both the visible effective date and the page description in `public/vault-docs/privacy/index.html`.

## Add another app

1. Add a new app card to the `apps-section` in `public/index.html`.
2. Create separate `public/app-slug/support/index.html` and `public/app-slug/privacy/index.html` files.
3. Link the new card using clean directory links such as `/app-slug/support/` and `/app-slug/privacy/`.
4. Write disclosures for that app’s actual behavior; do not reuse Vault Docs claims automatically.
5. Add any local app assets under `public/assets/` and verify every page at mobile and desktop sizes.

## Vault Docs icon

The website currently uses a CSS document mark, so there is no broken image when the official icon is unavailable. To add the real icon:

1. Export a square PNG named `vault-docs-icon.png`.
2. Place it at `public/assets/vault-docs-icon.png`.
3. Replace the CSS fallback elements in the home, support, and privacy pages with an image such as `<img src="/assets/vault-docs-icon.png" alt="" width="100" height="100">`.
4. Keep the empty alternative text because the adjacent text already names the app.

## Cloudflare Pages settings

- Project name: `kricha-apps` (or another reusable developer-level name)
- Framework preset: None
- Build command: leave empty / none
- Build output directory: `public`
- Root directory: repository root

The `public/_headers` file supplies restrictive security headers for the static site. No account IDs, credentials, tokens, or secrets belong in this repository.
