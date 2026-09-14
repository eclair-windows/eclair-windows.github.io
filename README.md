# Eclair — community guide (static site)

An 8-page static site about **Eclair**, the Scala implementation of the Lightning
Network by ACINQ. Built for GitHub Pages with technical SEO and GEO (generative
engine optimization) baked in. It is an **unofficial community resource** — every
download link points to ACINQ's official GitHub releases, and every page carries
an attribution/disclaimer.

## Pages
`index.html` · `what-is-eclair.html` · `features.html` · `install.html` ·
`documentation.html` · `comparison.html` · `faq.html` · `resources.html`
Plus `404.html`, `robots.txt`, `sitemap.xml`, `assets/` (CSS, JS, favicon, OG image).

## Before you publish — find & replace 3 things

1. **`USERNAME.github.io/eclair`** → your real base URL.
   This appears in canonical tags, Open Graph URLs, JSON-LD, `sitemap.xml`, and `robots.txt`.
   - GitHub Pages project site: `https://<your-user>.github.io/<repo>/`
   - Custom domain: your domain (and add a `CNAME` file containing just the domain).

   ```bash
   # from the site folder — replace with your base (no trailing slash on the host part)
   grep -rl 'USERNAME.github.io/eclair' . | xargs sed -i 's#USERNAME.github.io/eclair#YOURNAME.github.io/eclair#g'
   ```

2. **`G-XXXXXXXXXX`** → your Google Analytics 4 Measurement ID (in every `.html`).
   ```bash
   grep -rl 'G-XXXXXXXXXX' . | xargs sed -i 's/G-XXXXXXXXXX/G-YOURID/g'
   ```

3. **Verification codes** in `index.html` (optional but recommended):
   - `REPLACE_WITH_GOOGLE_VERIFICATION` → Google Search Console meta code
   - `REPLACE_WITH_BING_VERIFICATION` → Bing Webmaster Tools meta code
   (Or delete those two `<meta>` lines and verify via DNS/file instead.)

## Deploy to GitHub Pages

1. Create a repo, put these files at its root, push.
2. Repo → **Settings → Pages** → Source: *Deploy from a branch* → `main` / root.
3. The included empty `.nojekyll` file tells Pages to serve everything as-is.
4. After it's live, submit `sitemap.xml` in Google Search Console and Bing Webmaster Tools.

## What's already done for SEO / GEO
- Unique `<title>` + meta description + canonical per page
- Open Graph + Twitter cards + a 1200×630 `assets/og.png`
- JSON-LD structured data: `WebSite`, `SoftwareApplication`, `TechArticle`,
  `HowTo` (install), and `FAQPage` (faq) — the FAQ + answer blocks are the
  parts most likely to be quoted by AI answer engines
- Semantic HTML, one `<h1>` per page, direct "answer-first" definition blocks
- `robots.txt` explicitly allows AI crawlers (GPTBot, OAI-SearchBot, ClaudeBot,
  PerplexityBot, Google-Extended, Applebot-Extended, CCBot, etc.) + sitemap
- `sitemap.xml` with all pages
- Fast, no framework, mobile-responsive, keyboard-accessible, reduced-motion respected

## A note on positioning
The site is deliberately framed as a community guide, not the official project.
That's the honest choice **and** the durable one: search engines and AI engines
penalise pages that impersonate a brand, so clear attribution + linking to the
canonical source is what keeps rankings and AI citations healthy over time.
Keep downloads pointed at `github.com/ACINQ/eclair/releases`.
