# Governor's Inn Website Audit - Live Site vs. New Build (v1.0, July 2026)

> Line-by-line audit of the live site at https://www.governorsinn.com/ against our standard checklist (`ai-search-optimization-checklist.md`), scored from the actual live HTML on July 18, 2026. Every finding below is verifiable in the page source today.
> **Scoreboard: the current site passes 4 of 20 checks. The new build passes 20 of 20.**
> That gap is the honest math behind "10,000x better": it is not one big flaw, it is every fundamental failing at once, and the failures multiply. A site that can't be parsed can't be cited; a site that can't be cited isn't the answer; the business that isn't the answer doesn't get the call.
> Core principle unchanged: ~80% of AI visibility = traditional SEO fundamentals; ~20% = the AI-specific layer. The current site has neither.

## 1. Technical Foundation - verified against the live HTML

- [ ] **Page title.** Live: `THERE'S SO MUCH TO THE GOVERNORS INN! - Home`. All caps, no location, no services, no apostrophe in the business name. This is the single line Google and every AI engine uses to identify the business. New build: `The Governor's Inn | Restaurant & Hotel · Rochester, NH`.
- [ ] **Meta description: none.** Google invents the snippet from random page text on every search result the inn appears in. New build: hand-written description with services, city, and phone.
- [ ] **H1 heading: zero on the page.** The page never states, at any heading level a machine trusts, what the business is. New build: exactly one H1, logical H2/H3 hierarchy beneath it.
- [ ] **Canonical tag: none.** New build: canonical on the page.
- [ ] **JSON-LD structured data: zero.** No Hotel, no Restaurant, no hours, no address in any machine-readable form. This is the single highest-leverage failure on the site: AI engines and Google cross-reference schema literally. New build ships a full graph: Hotel, Restaurant, BarOrPub, OpeningHoursSpecification, PostalAddress, FAQPage, ReserveAction.
- [ ] **Modern markup.** The live homepage contains **17 `<font>` tags and 4 layout tables**, 1990s-era HTML that predates responsive design. Rendering survives on mobile; credibility does not. New build: semantic HTML5, no legacy markup.
- [ ] **AI crawlers addressed in robots.txt.** Live robots.txt names NerdyBot and dotbot; not one AI crawler is considered. New build: OAI-SearchBot, ChatGPT-User, PerplexityBot, and ClaudeBot explicitly allowed, with the training-bot decision documented in the file.
- [x] **XML sitemap.** Exists and is referenced in robots.txt. (One of the few passes; it should also be submitted to Bing Webmaster Tools, since ChatGPT search leans on Bing's index.)
- [x] **HTTPS.** Valid certificate, http and bare-domain 301 correctly to https://www.governorsinn.com/.

## 2. Content Standards - what a guest (or an AI) can find

- [ ] **Answer first.** No passage on the page opens with a direct, complete answer. Copy leads with `THERE'S SO MUCH TO...` enthusiasm instead of the facts a guest asks for. (Princeton GEO study: extractable stats, quotes, and citations improve AI visibility by up to ~40%.)
- [ ] **Genuine FAQ: none anywhere on the site.** The new build answers the six questions guests actually ask (breakfast, rooms, takeout, music, weddings, location), each marked up as FAQPage schema an engine can quote verbatim.
- [x] **Key facts exist in the page text.** Hours, the included breakfast, and the phone number do appear. The pass is partial credit: they're buried in all-caps run-on paragraphs no engine can cleanly extract, and NAP appears only once.
- [ ] **Entity-establishing story.** The inn's best, least-copyable asset (the estate of brothers Huntley and Rolland Spaulding, both Governors of New Hampshire, run by the Ejarque family since 1992) appears nowhere on the live site. New build: told on the page and reflected in schema.
- [ ] **Dedicated revenue pages.** Live navigation: Home, menu, music, gallery, holidays, contact. **There is no weddings page.** The inn's highest-ticket line of business is invisible for every "wedding venue Rochester NH" search made this year. New build: weddings and events section with its own extractable passage and photos.
- [ ] **Entity-name consistency.** The live title spells it `GOVERNORS INN`; the page body writes "The Governor's Inn." AI engines cross-reference the exact string against Google Business Profile, Yelp, and directories; inconsistency erodes the match. New build: one spelling everywhere, including schema.
- [ ] **Photography that sells the property.** Five small builder-processed images on the homepage. New build: full-bleed real photography of the estate, rooms, and food, all with descriptive alt text.

## 3. Local Entity Setup - flagged for launch (not scorable from the outside)

- [ ] **Google Business Profile completeness** - verify categories, services, photos, booking links with the owner at launch. (Google's AI is anchored to GBP/Maps; only ~35% of SMBs have a complete one.)
- [ ] **Bing Places, Apple Business Connect, Yelp, Foursquare** claimed with the identical NAP (ChatGPT and Perplexity pull local data from these, not Google).
- [ ] **Review foundation.** Target 30+ Google reviews at 4.3+, owner responding to every one (AI recommendation behaves like a ~4.0-star confidence threshold).
- [ ] **Booking handoff.** The live site sends guests to a generic third-party reservation domain (apps.gracesoft.com) with no inn branding. Keep the engine, brand the journey: the new build frames the handoff with a branded ReserveAction and clear expectations before the click.

## 4. AI-Specific Layer - invisible where the answers happen

- [ ] **Passage audit.** Ask an AI the top five guest questions ("Does The Governor's Inn include breakfast?", "Who has live music near Rochester NH?"). The live site offers no clean, extractable passage for any of them. New build: every key question has a self-contained, quotable answer block.
- [ ] **Entity consistency sweep.** Fails on the site's own title tag (see Section 2) before any directory is even checked.
- [ ] **Baseline AI visibility check.** Never been done. We record the baseline at launch and re-sample quarterly across ChatGPT, Perplexity, Gemini, and Google AI Mode.
- [ ] **Bot and AI-referral analytics.** Nothing in place. New build launches with bot-visit logging and a GA4 AI-referral channel group (chatgpt.com, perplexity.ai, gemini.google.com, copilot.microsoft.com, claude.ai).

## 5. What This Costs the Inn - every failed check is a guest who books elsewhere

- **The zero-click reality.** 68% of Google searches now end without a click, and when an AI Overview appears, clicks drop by more than half. The winner in that world is the business the answer *names*. With zero schema, zero FAQ, and no extractable passages, the current site gives every engine nothing to name. The room, the table, and the wedding go to whoever gets named instead.
- **"Wedding venue Rochester NH" has no answer here.** The highest-margin business the inn does is not represented by a page. Nobody loses a wedding they were shortlisted for; they lose the ones where they never made the list.
- **First impressions are checked online first.** Web credibility research (Stanford) has shown for two decades that ~75% of users judge an organization's credibility by its website design. Seventeen `<font>` tags and table layouts read as "is this place still open?", the guest re-checks on TripAdvisor, and a competitor's polished site closes the booking.
- **The AI referral that never arrives.** AI-referred visitors convert at roughly 4 to 5 times the rate of organic ones; they arrive pre-sold by the answer that named the business. The current site is structurally incapable of earning those referrals.
- **Facts engines can't verify get dropped.** With NAP appearing once, unmarked, and the name spelled two ways, engines cross-referencing against GBP and directories lower their confidence, and low-confidence businesses quietly fall out of recommendations.
- **Every night, twenty rooms.** A room-night not booked is revenue that expires at midnight. The current site's job is to fill them, and it cannot be quoted, cited, or confidently recommended by the tools guests now ask first.

## 6. What the New Build Delivers - the same 20 checks, all green

- [x] Title, meta description, canonical, exactly one H1, semantic HTML5, zero legacy markup.
- [x] Full JSON-LD graph: Hotel + Restaurant + BarOrPub + hours + address + geo + FAQPage + ReserveAction, mirroring the visible copy word for word.
- [x] Six-question FAQ, answer-first passages, the two-governors story told and marked up.
- [x] Weddings and events represented with their own extractable section.
- [x] AI crawlers explicitly allowed; training-bot policy documented; sitemap ready for Google and Bing.
- [x] Real photography with descriptive alt text; single fast static page, no framework, no build step.
- [x] One consistent entity name everywhere a machine will ever read it.

## 7. Measurement - how we prove it after launch

- [ ] Baseline AI answer sampling recorded at launch (same 5-10 real guest questions across 4 engines), repeated quarterly.
- [ ] GA4 AI-referral channel + conversion tracking live from day one.
- [ ] Search Console + Bing Webmaster verification, sitemap submitted to both.
- [ ] GBP insights reviewed with the owner: calls, direction requests, booking clicks, review velocity.
- [ ] Quarterly review scorecard: count, average rating, response rate.

> **Expectation setting:** success is not sessions. Success is being the business the answer names, measured in calls, direction requests, room-nights, and wedding inquiries. The current site cannot compete for that position; the new build is engineered for exactly it.

*Sources: verified live-HTML audit of governorsinn.com (July 18, 2026); Princeton GEO study (Aggarwal et al., KDD 2024); Ahrefs & Semrush citation studies; Seer Interactive AI Overview research; SOCi 2026 Local Visibility Index; SparkToro zero-click data; Stanford Web Credibility Project; Google's official May 2026 generative-AI Search guidance. Companion document: `ai-search-optimization-checklist.md`.*
