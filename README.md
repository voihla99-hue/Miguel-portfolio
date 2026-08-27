# Miguel Romero — Portfolio

Personal professional portfolio. Static site, no build step, served via GitHub Pages.

**Live:** https://voihla99-hue.github.io/Miguel-portfolio/

## Files

| File | What it is |
|---|---|
| `index.html` | **The site.** Single self-contained file — inline CSS + JS, Google Fonts is the only external request. |
| `index1.html` | Earlier, shorter draft of the same page. Not linked from anywhere; kept for reference. |

## Editing

Everything lives in `index.html`:

- `<head>` — title, meta description, Open Graph / Twitter cards, JSON-LD `Person` schema, canonical URL. **Update all of these together** if the deployed URL ever changes.
- `<style>` — design tokens on `:root` (light) and `html[data-theme="dark"]` (dark). Theme is stored in `localStorage` and falls back to `prefers-color-scheme`.
- `<body>` — sections in order: hero → metrics → platform → work → impact → method → experience → stack → skills → about → contact.
- `<script>` at the bottom — scroll reveal, work-card filters, theme toggle, mobile menu, scroll-spy.

Work cards are filterable. Each `<article class="card">` carries `data-cat="…"` with one or more of
`automation · data · software · infra · ai · people`; the filter bar reads those values. If you add a
card, add its categories and bump the counts in the filter buttons and `#filter-count`.

## Content rules

- **No client, employer-client, account, platform or team-member names** anywhere on the page. Scale and
  results are described in aggregate ("a 10-account operation", "two platforms"). Past employers are
  named as employment history only.
- **No infrastructure identifiers** — no hostnames, domains, IPs, tokens or file paths from the private
  systems described.
- **Every number on the page is a measurement**, not an estimate. Source of truth for the operational
  figures is the private ops knowledge base; re-measure and date-stamp before changing one.

## Deploy

Push to `main`. GitHub Pages serves it from the repository root.
