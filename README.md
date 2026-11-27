# jarvix.in

Website for **Jarvix Private Limited**, a cloud-native engineering consultancy.
Plain HTML + CSS, no build step, hosted on GitHub Pages at <https://jarvix.in>.

## Structure

| Path | URL | What |
|---|---|---|
| `index.html` | `/` | Home: hero, services overview, how we work, why Jarvix, who we work with |
| `services.html` | `/services.html` | 7 services, each with an anchor (`#platform`, `#devops`, `#sre`, `#observability`, `#ai`, `#mlops`, `#cloud`) |
| `about.html` | `/about.html` | Mission, principles, engagement models |
| `contact/index.html` | `/contact/` | Contact form (Web3Forms), email, office address |
| `thank-you/index.html` | `/thank-you/` | Shown after a successful form submission (`noindex`) |
| `privacy/index.html` | `/privacy/` | Privacy policy (DPDP Act 2023) |
| `style.css` | | Shared styles; brand colours are CSS variables in `:root` |
| `assets/` | | `logo.png`, `favicon.png` |
| `CNAME` | | Custom domain for GitHub Pages (`jarvix.in`) |
| `_config.yml` | | Keeps `README.md` / `AGENTS.md` off the live site |

All links and asset paths are root-absolute (`/style.css`, `/contact/`), so the site must be served from a domain root.
Header and footer are duplicated in every page: change them in all six HTML files.

## Run locally

```bash
python3 -m http.server 8000
```

Open <http://localhost:8000/>. Don't open the files directly (`file://`): root-absolute paths won't resolve.

## Contact form

The form posts to [Web3Forms](https://web3forms.com) using the public access key in `contact/index.html`.
A small inline script submits it with `fetch()` and redirects to `/thank-you/` on success. This is needed because
Web3Forms' free plan only honours its `redirect` field for same-domain URLs. Without JavaScript the form still
posts normally and uses the hidden `redirect` field.

Submitting locally sends a real enquiry.

## Deploy

Every push to `main` is published by GitHub Pages (Settings → Pages → Deploy from branch `main`, `/ (root)`).

DNS (GoDaddy, `jarvix.in`):

| Type | Name | Value |
|---|---|---|
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| CNAME | `www` | `jarvixlabs.github.io` |

Then enable **Enforce HTTPS** in the Pages settings.
