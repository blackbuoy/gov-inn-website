# The Governor's Inn — Website

A single-page website for [The Governor's Inn](https://www.governorsinn.com/), a restaurant and hotel on the historic Spaulding estate at 78 Wakefield Street, Rochester, NH — home of Spaulding Steak & Ale, The Garage beer garden, twenty guest rooms, weddings & events, and live music five nights a week.

## The site

**`index.html`** is the production site. It's fully self-contained (one HTML file plus the `photos/` folder) — no build step, no framework. Deploy by uploading `index.html`, `photos/`, `Gov_1.jpg`, `Gov_2.png`, `robots.txt`, and `sitemap.xml` to any static host.

### Design

The design is built around the inn's real hanging sign, decomposed into an identity system rather than used as decoration:

- The sign's red **"RESTAURANT · HOTEL" banner** is the recurring section label
- The sign's **changeable letterboard** is recreated as an animated split-flap board announcing hours and happenings
- The **full sign** appears once, in the Visit section, doing its real job: "look for the sign on Wakefield Street"
- The striped **awning valances** over each photo echo the estate's real window awnings

Typography: Fraunces (display) · Archivo (body) · Oswald (letterboard + sign). Palette: cream, hunter green, and burgundy — pulled from the sign and the building itself.

### Key integrations

| What | Link |
|---|---|
| Menu & takeout | [Toast — Spaulding Steak & Ale](https://www.toasttab.com/local/order/spaulding-steak-ale-78-wakefield-st) |
| Room booking | [GraceSoft EasyWebRez](https://apps.gracesoft.com/PMS/EasyWebRez/roomdetails/1042) |
| Social | [Facebook](https://www.facebook.com/profile.php/?id=100069548921660) |

### SEO / AI-search layer

- JSON-LD structured data: `Hotel` (with `ReserveAction` → booking engine), `Restaurant` (with `hasMenu` → Toast), `BarOrPub`, and `FAQPage` matching the visible FAQ
- Answer-first meta tags, canonical URL, Open Graph tags
- `robots.txt` explicitly allows AI search crawlers (OAI-SearchBot, PerplexityBot, ClaudeBot, etc.)
- `sitemap.xml` — submit to Google Search Console and Bing Webmaster Tools after deploy

## Maintenance

- **The summer music lineup** in the Live Music section (`<ul class="lineup">`) is hard-coded — edit the rows as shows pass or get announced.
- **The letterboard messages** are in the `MSGS` array in the inline script at the bottom of `index.html` — each message is two lines of max 20 characters.
- **Hours** appear in three places; keep them in sync: the visible facts lists, the FAQ, and the JSON-LD `openingHoursSpecification`.

## Repository layout

```
index.html        The production site
photos/           Photography (sourced from the inn's original site)
Design_1..4/      Design exploration comps (Design 4 became the site)
robots.txt        Crawler rules incl. AI search bots
sitemap.xml       Sitemap — submit after deploy
Gov_1.jpg/2.png   Original estate photos
```

---

Site design & build with [Claude Code](https://claude.com/claude-code).
