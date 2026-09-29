# ncg-dera — Groupe Immobilier Deragon (static site)

Static rebuild of the WordPress/Kallyas site at `deragroupederagon.kinsta.cloud`, migrated 2026-09-28.
Plain HTML + one stylesheet. No build step, no JavaScript, no plugins.

## Structure

| Path | Page (EN) | Path | Page (FR) |
|---|---|---|---|
| `/` | Home | `/fr/` | Accueil |
| `/about/` | About Us | `/fr/entreprise/` | Entreprise |
| `/finishing/` | Finishing | `/fr/tirage/` | Tirage de joints |
| `/real-estate/` | Real Estate | `/fr/immobilier/` | Immobilier |
| `/development/` | Property Development | `/fr/gestion/` | Gestion de projet |
| `/construction/` | Construction | `/fr/construction/` | Construction |
| `/contact/` | Contact | `/fr/contact/` | Nous joindre |

- `assets/site.css` — all styles (palette and type scale taken from the original: brand blue `#1148b8`, Montserrat + Open Sans via Google Fonts).
- `assets/img/` — photos, re-encoded to WebP (max 1920 px). `assets/icons/` — the original division icons (SVG).
- `assets/logo.svg`, `assets/logo-footer.png`, favicons — original brand files.
- `404.html`, `.nojekyll`.
- All internal links are relative, so the site works both at `https://<owner>.github.io/ncg-dera/` and later on a custom domain.

Pages were generated from `build.py` (kept outside the repo in the migration package); edit the HTML directly from here on, or regenerate.

## Publish on GitHub Pages

1. Push these files to the root of `main`.
2. Settings → Pages → Build and deployment → *Deploy from a branch* → `main` / `(root)`.
3. The site appears at `https://<owner>.github.io/ncg-dera/` within a few minutes.

## Adding a custom domain later

1. Add a file `CNAME` containing the bare domain (e.g. `groupederagon.com`).
2. Settings → Pages → Custom domain → same domain → *Enforce HTTPS* once the certificate issues.
3. DNS at the registrar (remove any old A/AAAA/CNAME on `@` and `www` first; never touch MX/TXT):

```
@    A     185.199.108.153
@    A     185.199.109.153
@    A     185.199.110.153
@    A     185.199.111.153
@    AAAA  2606:50c0:8000::153
@    AAAA  2606:50c0:8001::153
@    AAAA  2606:50c0:8002::153
@    AAAA  2606:50c0:8003::153
www  CNAME <owner>.github.io
```

## What changed versus the WordPress site

Removed: contact form (replaced by email/phone/address block), login panel, search, empty blog, empty portfolio carousels, social follower counters, "Awesome facts" counters, "Our Commitment" page (theme demo content for an unrelated Toronto agent).
Edited: see the migration note in the project for the list of copy corrections to confirm with the client.
