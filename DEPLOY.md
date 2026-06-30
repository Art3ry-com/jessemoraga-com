# jessemoraga.com — static site (deploy notes)

New personal-brand front door. Positioning: **a developer who builds with AI to
ship fast + affordable, so small businesses can take on the mainstream
corporations.** Built from a claude.ai/design `.dc.html` package; rendered
client-side by `support.js` (loads React from unpkg).

## Files
- `index.html` — homepage (root DC)
- `blog.html` — writing index (topic filter + search)
- `article.html` — sample post template
- `support.js` — claude.ai/design React runtime (do not edit by hand)
- `favicon.svg`, `robots.txt`, `sitemap.xml`

## Local preview
```bash
python3 -m http.server 8099   # then open http://localhost:8099/index.html
```

## Live (GitHub Pages, mirrors art3ry.com)
1. Push to `main` → Pages auto-builds in ~1 min.
2. **Preview** (no DNS change): served at the repo's `*.github.io` URL.
3. **Apex cutover (GATED — needs Jesse's explicit yes):** add a `CNAME` file with
   `jessemoraga.com`, then re-point the domain DNS off WordPress.com → GitHub Pages
   (A records 185.199.108–111.153 + `www` CNAME → `<owner>.github.io`), Cloudflare
   per the art3ry.com pattern. **This replaces the current live WordPress site and
   its published blog — migrate/abandon that content first.**

## Known follow-ups (harden before/after cutover)
- Runtime depends on unpkg (React/Babel) → weaker SEO + CDN-fragile vs static HTML.
  Consider pre-rendering to static or self-hosting React.
- Image placeholders (`[ drop image ]`, headshot, OG image) still to fill.
- Newsletter form `action="#"` → wire to an email-capture provider.
- Social links are `#` placeholders → real profile URLs.
