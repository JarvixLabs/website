# AGENTS.md

Guidance for AI coding agents working on this repo. See `README.md` for structure, local run and deploy.

## Working rules

- **Edit locally, then stop.** Commit and push only when the owner says "push". Every push to `main` goes live.
- **Git identity:** commits and pushes must use the personal account, `kushalgangan <kushal.gangan@gmail.com>`.
  The repo-local git config sets this, including `core.sshCommand` pointing at `~/.ssh/id_ed25519_personal_github`.
  The machine's default SSH key belongs to a different (work) account, so don't remove that setting.
- **No AI attribution** in commits, PRs or files (no `Co-Authored-By: Claude`, no "Generated with" lines).
- **Keep it plain HTML/CSS.** No frameworks, build tools or dependencies. Header and footer are duplicated in every
  page, so update every HTML file (`index.html`, `services.html`, `about.html`, `contact/`, `thank-you/`, `privacy/`, `blog/` and each post).
- Use root-absolute links and asset paths (`/style.css`, `/contact/`).
- Before reporting a change as done, serve locally (`python3 -m http.server`) and check the pages load. Screenshot
  with headless Chrome when the layout changes.

## Content rules

- **Brand:** "Jarvix" in copy. "Jarvix Private Limited" for the legal entity (footer, privacy, office).
  Domain `jarvix.in`, email `contact@jarvix.in`, office "Pune, Maharashtra, India - 411036".
  Show the location only in the address blocks (footer, contact page, privacy contact). Don't write "based in Pune" in body copy or meta descriptions.
- **Positioning:** a cloud-native engineering consultancy covering the full range below. Don't let the hero or intro
  read as Kubernetes-only or AI-only.
- **Canonical service names.** Use these exact names everywhere: cards, headings, footer, meta descriptions, contact list.
  1. Platform Engineering
  2. DevOps & CI/CD
  3. Site Reliability Engineering (SRE)
  4. Observability
  5. AI Platforms & Agents (includes agentic AI for incident analysis)
  6. MLOps
  7. Cloud Migration & Optimisation (multi-cloud, hybrid, on-prem to cloud, FinOps)
- **No invented proof.** No fake case studies, client logos, testimonials, metrics, certifications or partner badges.
  Add them only when the owner supplies real ones.
- Avoid claims that can't be backed up yet: 24x7 on-call, named compliance standards, "before customers notice".
- **Spelling:** British/Indian English (optimisation, organisation, prioritised). Professional tone, no slang.
- **Reply time:** "within 2 to 3 business days". This is the owner's deliberate choice; don't change it without asking.
- **Main button:** "Book a consultation".
- **Tagline:** "Engineering at the intersection of cloud and AI" (a nod to the X in the logo). It appears under the
  footer logo on every page.

## Blog

- Posts live in `blog/<slug>/index.html`; follow "Adding a blog post" in README.md and keep `blog/index.html`, the home page "Latest from the blog" section and `sitemap.xml` in sync.
- Byline "Jarvix Engineering". The first eight posts were deliberately back-dated (1 Sep to 26 Nov 2026) at the owner's request.
- Each post has a "Tools covered" row and at least one diagram. Diagrams are inline SVG in site colours (min-width 620px, scrolling sideways on small screens).
- Tool logos live in `assets/logos/`. CNCF project logos come from the official github.com/cncf/artwork repo. Other brands come from Simple Icons, coloured with the official brand colour. Use logos only in diagrams and tool rows, not scattered through text. Scan new SVGs for scripts or external links before adding them.
- Write genuinely useful, specific, practical content: no filler, no invented client stories or statistics, no long dashes.
- Every post ends with a call-to-action linking to the matching `/services.html#<anchor>` and `/contact/`.

## Contact form

Web3Forms with a public access key, which is safe in client HTML. The free plan only redirects to same-domain URLs,
so the inline script submits with `fetch()` and redirects to `/thank-you/` itself. The script deletes the `redirect`
field from the JSON body, because sending it makes the API answer with a redirect instead of JSON.

## Open items

Waiting on the owner (as of 2026-11-27):

- Founder name and LinkedIn URL, for the About page and the contact button.
- Company CIN, for the footer. Indian companies may need to show it on their website; the owner is confirming with their CA.
- GitHub Pages enablement and GoDaddy DNS.
- A real Web3Forms test submission on the live site.
