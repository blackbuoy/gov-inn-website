# The Governor's Inn - Website

A single-page website for [The Governor's Inn](https://www.governorsinn.com/), a restaurant and hotel on the historic Spaulding estate at 78 Wakefield Street, Rochester, NH, home of Spaulding Steak & Ale, The Garage beer garden, twenty guest rooms, weddings & events, and live music five nights a week.

## The site

**`index.html`** is the production site. It's fully self-contained (one HTML file plus `photos/` and `fonts/`), no build step, no framework, no third-party requests at load time. Deploy by uploading `index.html`, `photos/`, `fonts/`, `favicon.svg`, `favicon-32.png`, `apple-touch-icon.png`, `robots.txt`, `sitemap.xml`, and `llms.txt` to any static host. Everything else in the repo is internal (audits, design comps, photo masters) and must not be deployed.

### Design

The design is built around the inn's real hanging sign, decomposed into an identity system rather than used as decoration:

- The sign's red **"RESTAURANT · HOTEL" banner** is the recurring section label
- The sign's **changeable letterboard** is recreated as an animated split-flap board announcing hours and happenings (aria-hidden, with a visually-hidden text equivalent)
- The **full sign** appears once, in the Visit section, doing its real job: "look for the sign on Wakefield Street"
- The striped **awning valances** over each photo echo the estate's real window awnings
- The **Live Music section** is a dark "stage" set against the fog-lit Garage photo
- The footer carries the estate's old **line engraving** as a plate mark

Typography: Fraunces (display) · Archivo (body) · Oswald (letterboard + sign), self-hosted variable fonts (see Fonts). Palette: cream, hunter green, and burgundy, pulled from the sign and the building itself. All accent/surface pairs verified at WCAG 4.5:1 both directions.

Photography is the inn's own, harvested at original resolution from the current site's CDN, re-encoded as right-sized WebP srcsets with EXIF stripped. Masters live in `photos-src/` (internal, not deployed).

### Key integrations

| What | Link |
|---|---|
| Menu & takeout | [Toast - Spaulding Steak & Ale](https://www.toasttab.com/local/order/spaulding-steak-ale-78-wakefield-st) |
| Room booking | [GraceSoft EasyWebRez](https://apps.gracesoft.com/PMS/EasyWebRez/roomdetails/1042) |
| Social | [Facebook](https://www.facebook.com/profile.php/?id=100069548921660) |

Every booking/order CTA points directly at these; no intermediate pages. The Google Maps embed is a click-to-load facade (the "Get Directions" link works without it).

### Conversion layer

- **Persistent CTAs:** Book a Room in the header (desktop) and a fixed bottom action bar on mobile: Book a Room / Menu / Call.
- **Open-now status strip** under the header: computed client-side in America/New_York from the same hours as the JSON-LD; today's hours row is highlighted in the Visit section. No-JS fallback text is the static hours line.
- **Evergreen lineup:** every show row carries `data-date`; past dates hide automatically, and when the last one passes the whole lineup block hides, leaving the weekly rhythm plus the Facebook link. Nothing on the page goes stale by itself.
- **Weddings inquiry:** structured mailto (event type, date, guest count, phone) plus tap-to-call.

### SEO / AI-search layer

- JSON-LD graph: `Hotel` (geo, sameAs, ReserveAction → booking engine), `Restaurant` (hasMenu → Toast), `BarOrPub`, and `FAQPage` matching the visible FAQ word for word
- Answer-first meta tags, canonical URL, Open Graph + Twitter cards with a branded 1200x630 share image (`photos/share.jpg`)
- `llms.txt` with a blockquote summary and markdown-linked sections (Agentic Browsing check passes)
- `robots.txt` explicitly allows AI search crawlers (OAI-SearchBot, PerplexityBot, ClaudeBot, etc.)
- `sitemap.xml`: submit to Google Search Console and Bing Webmaster Tools after deploy

### Fonts

Self-hosted variable-font latin subsets in `fonts/` (Fraunces roman + italic, Archivo, Oswald), subset to ASCII plus ’ ‘ “ ” – · © ®. If new copy ever needs glyphs outside that set (accented names, for example), regenerate the subsets or the glyphs will render in the metric-matched fallback. The `@font-face` fallbacks (Georgia / Arial / Arial Narrow) carry fontaine-style `size-adjust` overrides so the swap causes no layout shift.

### Performance

Lighthouse (gzip-enabled server, `--form-factor=mobile --throttling.cpuSlowdownMultiplier=10`): mobile 97/100/100/100 (TBT 0 ms, CLS 0.006; the residual points are the simulated-network floor on FCP/LCP), desktop 100/100/100/100, Agentic Browsing 100 on both. Inline CSS is minified; images are lazy-loaded WebP with explicit dimensions; the hero is `fetchpriority=high` and sized to be the LCP element.

## Maintenance

- **The music lineup** (`<ul class="lineup">`): add rows with `data-date="YYYY-MM-DD"`; past dates hide themselves. Update the "booked through ..." line when extending.
- **The letterboard messages** are in the `MSGS` array in the inline script, two lines of max 20 characters each.
- **Hours** live in FOUR places; keep them in sync: the visible facts lists, the FAQ, the JSON-LD `openingHoursSpecification`, and the `HOURS`-style logic in the open-now script.
- **Header nav styles are scoped to `#mainnav`** (there are two `<nav>` elements; bare `nav` selectors would leak into the mobile action bar).
- **Copy style:** plain hyphens, never em dashes (U+2014); en dashes only in ranges. Grep before every push.

## Repository layout

```
index.html          The production site
photos/             Optimized WebP + share.jpg (deployed)
photos-src/         Full-res EXIF-stripped masters (internal)
fonts/              Self-hosted subset variable fonts (deployed)
favicon.svg/-32.png/apple-touch-icon.png    Icons (deployed)
llms.txt            AI-assistant site summary (deployed)
robots.txt          Crawler rules incl. AI search bots (deployed)
sitemap.xml         Sitemap: submit after deploy (deployed)
Design_1..4/        Frozen design exploration comps (internal)
GOVERNORS INN AUDIT.pdf, governorsinn-website-audit.md,
ai-search-optimization-checklist.md             Pitch documents (internal)
```

---

Site design & build with [Claude Code](https://claude.com/claude-code).
