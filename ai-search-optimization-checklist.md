# AI Search Optimization, Standard Site Checklist (v1.0, July 2026)

> Standard operating procedure applied to **every site we build and maintain**.
> Core principle: ~80% of AI visibility = traditional SEO fundamentals; ~20% = a new AI-specific layer.
> Sections 1–4 are verified by us before launch. Section 5 is the client's ongoing role.
> This file is intended both as a human checklist and as context for Claude Code when building/reviewing sites.

## 1. Technical Foundation, every build, before launch

- [ ] **Static-first rendering (Astro).** All meaningful content present in initial HTML; no critical content inside client-only islands. (~69% of AI crawlers can't execute JS.)
- [ ] **AI crawlers allowed in robots.txt:** OAI-SearchBot, ChatGPT-User, PerplexityBot, ClaudeBot. Blocking OAI-SearchBot removes the site from ChatGPT search entirely. GPTBot / Google-Extended (training bots) = separate per-client decision, documented.
- [ ] **CDN/firewall audit (Netlify / Vercel / Cloudflare):** confirm no bot-protection layer silently blocks AI crawlers above robots.txt (Cloudflare blocks them by default on new domains since July 2025). Test with real bot user-agents post-launch.
- [ ] **XML sitemap** generated and submitted to Google Search Console **and Bing Webmaster Tools** (ChatGPT search leans on Bing's index).
- [ ] **Semantic HTML:** one H1, logical H2/H3 hierarchy, unique title + meta description per page, canonical tags, no orphan pages.
- [ ] **Performance:** Core Web Vitals pass on mobile; images optimized/lazy-loaded; fonts subset.
- [ ] **JSON-LD structured data:** LocalBusiness (most specific subtype) with name, address, phone, hours, geo, sameAs; Organization; FAQPage where genuine; Service/Product as applicable. Validate with Rich Results Test.
- [ ] **NAP on-site matches everywhere**, exact business name, address, phone *format* identical to Google Business Profile and all directories. (AI engines cross-reference these literally.)
- [ ] **Indexed and snippet-eligible:** no accidental noindex/nosnippet; verified live in Search Console.

## 2. Content Standards, every page

- [ ] **Answer first.** Every page/section opens with a direct, complete answer in 1–2 sentences, then elaborates.
- [ ] **Self-contained sections.** Each H2/H3 block stands alone as a quotable passage: heading states the question, passage resolves it.
- [ ] **Specifics:** statistics, prices/ranges, timelines, named sources, real quotes from owner/customers. (Princeton GEO study: stats + quotes + citations improved AI visibility by up to ~40%.)
- [ ] **Non-commodity content only.** Something on every page that couldn't be written without this client: real photos, process, pricing approach, service area, actual customer questions.
- [ ] **Genuine FAQ section** on service pages, real customer questions, 2–4 sentence answers.
- [ ] **Dedicated service + location/service-area pages**, one clear topic per page, covering the sub-questions AI query fan-out generates. Depth over volume; never mass-produced thin pages.
- [ ] **Entity-establishing About page:** who runs it, credentials/licenses, years in business, service area, associations, matching sameAs schema.
- [ ] **Plain language, no keyword stuffing** (zero measured AI benefit; slightly hurts in some engines).
- [ ] **Visible published/updated dates;** core pages reviewed every 6 months.

## 3. Local Entity Setup, done with the client at launch

- [ ] **Google Business Profile 100% complete:** correct primary + secondary categories, services, hours, 10+ real photos, description, attributes, booking links. (Google's AI is anchored to GBP/Maps. Only ~35% of SMBs even have one.)
- [ ] **Bing Places, Apple Business Connect, Yelp** claimed with identical NAP (ChatGPT/Perplexity pull from Foursquare, Bing, Yelp, TripAdvisor, not Google).
- [ ] **Foursquare listing** verified/claimed (supplies a large share of ChatGPT's local place data).
- [ ] **Industry directories** for the vertical (Angi, Houzz, Avvo, Healthgrades, etc.) with consistent NAP.
- [ ] **Review foundation:** review link generated; ask-every-happy-customer process agreed; owner committed to responding to all reviews. Target 30+ reviews at 4.3+ (AI recommendation behaves like a ~4.0-star confidence threshold; ~3.4 stars + low response rate ≈ excluded).
- [ ] **LocalBusiness schema mirrors GBP exactly.**

## 4. AI-Specific Layer, the new 20%

- [ ] **Passage audit:** for each key page, the 3–5 questions a customer would ask an AI each have a clean, extractable answer on the site.
- [ ] **Entity consistency sweep:** identical business name everywhere; duplicate/stale listings corrected.
- [ ] **Baseline AI visibility check recorded:** ask ChatGPT, Perplexity, Gemini, Google AI Mode the client's top 5 customer questions; log results; repeat quarterly. (Answers are probabilistic, sample over time, never read one response.)
- [ ] **Third-party presence plan:** shortlist of realistic mention targets, local news, chamber, "best of [town]" lists, supplier/partner pages, 1–2 relevant communities. (Brand mentions, even unlinked, are the strongest measured predictor of AI visibility; ~85% of brand mentions in AI answers come from third-party pages.)
- [ ] **Bot analytics enabled** (server logs / host analytics) to see which AI crawlers visit.
- [ ] **GA4 'AI referral' channel group:** chatgpt.com, perplexity.ai, gemini.google.com, copilot.microsoft.com, claude.ai.

## 5. Client's Ongoing Role (we coach)

- [ ] Ask every happy customer for a Google review, steady, never bursts, never incentivized.
- [ ] Respond to every review within a few days.
- [ ] Post to GBP at least monthly; keep hours current.
- [ ] Send us real material (job photos, customer questions, pricing/service changes) for content updates.
- [ ] Say yes to local visibility opportunities (chamber, sponsorships, local press) and tell us.
- [ ] Never buy reviews, mentions, or "guaranteed ChatGPT placement" (doesn't exist).

## 6. What We Deliberately DON'T Do

- **No llms.txt.** No major AI system reads it (97% never fetched in a 137k-site study; Google compares it to the keywords meta tag). Revisit if a platform commits.
- **No artificial "chunking"** or machine-first rewriting. Google: no ideal page length. Structure for humans.
- **No keyword stuffing.**
- **No mass-produced keyword/city page grids** (scaled content abuse). Fewer, deeper pages.
- **No bought mentions/reviews/"AI placement."**
- **No treating third-party AI-visibility dashboards as primary KPI**, directional estimates only; report conversions first.

## 7. Measurement

- [ ] Quarterly AI answer sampling (same 5–10 real questions across 4 engines; log named/cited/recommended).
- [ ] AI referral traffic + conversion rate in dedicated GA4 channel (expect tiny volume, ~4–5x organic conversion).
- [ ] Search Console: impressions, position, generative-AI performance report where available.
- [ ] GBP insights: calls, direction requests, website clicks, review velocity.
- [ ] Review scorecard quarterly: count, average, response rate.
- [ ] Content freshness log: every core page touched within 6 months.

> **Expectation setting:** 68% of Google searches now end without a click; when an AI Overview appears, clicks drop by more than half. Success = being the business the answer names, measured in calls, bookings, and direction requests, not sessions.

*Sources: Princeton GEO study (Aggarwal et al., KDD 2024); Ahrefs & Semrush citation studies; Seer Interactive AI Overview research; SOCi 2026 Local Visibility Index; Whitespark & BrightLocal local research; SparkToro zero-click data; Google's official May 2026 generative-AI Search guidance. Review quarterly.*
