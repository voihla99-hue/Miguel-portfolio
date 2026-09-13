# Miguel Romero — Portfolio

Personal professional portfolio. Static site, no build step, served via GitHub Pages.

**Live:** https://voihla99-hue.github.io/Miguel-portfolio/

## Files

| File | What it is |
|---|---|
| `index.html` | **The site.** Single self-contained file — inline CSS + JS. Google Fonts is the only external request. |
| `assets/miguel.jpg` | Headshot used in the sidebar (512×512). If it fails to load, the "MR" monogram underneath shows instead. |
| `index1.html` | Earlier, shorter draft. Not linked from anywhere; kept for reference. |

## Layout

A dashboard, not a long page:

- **Sidebar** (left on desktop, a top bar with a menu drawer on phones) — headshot, name, contact icons,
  the menu, availability, theme toggle.
- **Home** (`#/`) — one screen: headline, tools belt, and a bento grid of tiles (Projects, Impact, AI
  builds, About, Services, Experience, Platform). Each tile opens its full view.
- **Views** — `#/projects`, `#/impact`, `#/platform`, `#/services`, `#/experience`, `#/method`,
  `#/stack`, `#/about`, `#/contact`. Each is a `<div class="view" data-view="…">` holding the full section.

**The no-scroll home only engages where it fits** — at least 1180px wide and 640px tall. Below that the
tiles become a normal scrolling grid (two columns on tablets, one on phones) rather than clipping. It was
measured with no clipped tile, no home scroll and no sidebar scroll at 1180×640, 1366×657, 1280×720,
1280×800, 1440×900, 1536×730, 1600×900, 1920×1080 and 2560×1440. **If you add content to a tile, re-check
the short sizes** — the `max-height:800px` and `max-height:700px` rules are where it gets tight.

### Routing

Hash routes, so every view and filter is linkable and the back button works on a static host.

- `#/projects/<filter>` opens Projects pre-filtered (`automation`, `data`, `software`, `infra`, `ai`,
  `people`, `docs`). The Home tile's category bars use these.
- Links from before the redesign still land: `#work` → Projects, `#skills` → Services, and `#impact`,
  `#platform`, `#contact` etc. map to their views.
- Unknown routes fall back to Home.

## Editing

- `<head>` — title, meta description, Open Graph / Twitter cards, JSON-LD `Person` schema (including
  `sameAs` social profiles), canonical URL. **Update these together** if the deployed URL changes.
- `<style>` — design tokens on `:root` (light) and `html[data-theme="dark"]` (dark); theme is stored in
  `localStorage` and falls back to `prefers-color-scheme`. The dashboard shell is the block headed
  `DASHBOARD SHELL` at the end.
- **Contact details appear in four places:** the JSON-LD, the sidebar icon row, the phone menu drawer
  (`.snav__contact`), and the Contact view. Change all four.
- **Home tile numbers are duplicated from the views** (e.g. `$157.9K`, `18 builds`, the category counts).
  When a figure changes in a view, change its tile too.

Work cards are filterable. Each `<article class="card">` carries `data-cat="…"` with one or more of
`automation · data · software · infra · ai · people · docs`. If you add a card, set its categories, then
update the `All · N` button, the `#filter-count` text, the Projects tile's category bars and counts, and
the "18 builds" copy.

## Content rules

- **No client, employer-client, account, platform or team-member names** anywhere on the page. Scale and
  results are described in aggregate ("a 10-account operation", "two platforms"). Past employers are
  named as employment history only.
- **No infrastructure identifiers** — no hostnames, domains, IPs, tokens or file paths from the private
  systems described.
- **No invented social proof.** No testimonials, certifications, visitor counters or badges unless they
  are real and supplied.
- **Every number on the page is a measurement**, not an estimate. Source of truth for the operational
  figures is the private ops knowledge base; re-measure and date-stamp before changing one. The revenue
  sparkline is zero-based on purpose — a truncated axis would exaggerate the growth.

## Deploy

Push to `main`. GitHub Pages serves it from the repository root.
