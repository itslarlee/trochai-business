# Trochai Sites — Pricing & Product Reference

> Master pricing doc for **Trochai Sites** — done-for-you premium real-estate landing pages, auto-synced to Trochai Inbox. This document is the single source of truth for à-la-carte rates, the May 2026 promo, change-request fees, and retainers. The landing page at `trochai.com/sites` renders from this doc — keep them in sync.
>
> **Last updated:** 2026-04-29 — initial draft following board synthesis on Trochai Sites launch.

---

## What Trochai Sites is

A separate paid service from Trochai Inbox: custom real-estate landing pages, designed to the agency's brand, **sharing the same Supabase backend as Trochai Inbox**. Properties created in Inbox surface automatically on the Sites page. The bot's AI consumes the same data — no double entry, no integration to maintain.

**The single most important differentiator** vs every other RE site builder (Wix, Squarespace, WordPress, Luxury Presence, Agent Image): zero data sync. Add a property in Inbox → it's live on the site within minutes. The site doesn't have its own CMS — it *is* the Inbox.

---

## Two product archetypes, four templates

| # | Name | Archetype | Style | Best for |
|---|---|---|---|---|
| 1 | **Agency Editorial** | Multi-listing real-estate agency | Clean, magazine-layout, photo-led | Default. Wins when photos are decent, fails gracefully when they're not. |
| 2 | **Agency Maximalist** | Multi-listing real-estate agency | Dark, type-driven, motion accents, AI hero atmospherics | Premium boutique pitch — for agencies that will invest in content. |
| 3 | **Development Boutique** | Single-development site | Quieter, narrative-led, premium-but-not-tech-bro | Smaller developers wanting elegance without the WebGL cost. |
| 4 | **Development Cinematic (Lite)** | Single-development site | Scroll-driven video + parallax + AI renders, **no hand-rolled WebGL** | Mid-to-premium developers wanting the "wow" hero without a custom Three.js build. |
| 4+ | **Development Cinematic (Full R3F)** | Single-development site | Real-time WebGL via react-three-fiber + custom shaders | Paid upgrade only, deposit-gated. Not built spec on the founder's clock. |

### What's in every template

- Tailwind v4 + Next.js 16, deployed to Vercel with custom domain
- Per-tenant brand tokens (colors, typography, accent fonts) via `client.config.ts`
- Connected to the Trochai Inbox Supabase backend — properties, projects, agents, blog posts auto-sync
- Mobile-first, responsive, performance-tuned
- WhatsApp CTA + ContactForm wired to the Inbox `contact_submissions` flow
- SEO basics: metadata, Open Graph tags, sitemap

---

## À-la-carte pricing (CR/LATAM-anchored)

Anchored to LATAM premium top, well above CR WordPress shops ($180–$1,500 floor) and below international premium (Luxury Presence at $5K–$15K). Delivers $100–$240/hr realized rate at solo-founder build speed — healthy for the CR market.

| Template | List price (USD) | Founder hours | $/hr realized | Notes |
|---|---|---|---|---|
| Agency Editorial | **$2,500** | ~25 | $100 | Default. Photo-led. |
| Agency Maximalist | **$4,500** | ~45 | $100 | Adds motion + dark mode + AI atmospherics. |
| Development Boutique | **$5,500** | ~50 | $110 | Single-development narrative. |
| Development Cinematic (Full R3F) | **$13,500** | ~90 | $150 | **Default Cinematic offering.** Real-time WebGL via R3F + custom shaders + glTF building model. The Trochai Sites landing-page demo is a Full R3F build — it doubles as the showcase that anchors the premium pitch. **First build (May 2026) is the founder's marketing investment; all subsequent client builds require 50% deposit ($6,750) before kickoff.** |
| Development Cinematic (Lite) | **$9,500** | ~40 | $238 | **Value option** within Cinematic tier. Scroll-driven video + parallax + AI renders, no WebGL. ~80% of the visual impact at ~40% of the build hours. Best margin. |

**Why these numbers:** they sit above CR locals (Trochai's tech stack is materially better — Tailwind v4 + Next 16 + Supabase + auto-sync) and below international premium (Trochai is local, Spanish-first, and has lower integration cost). Defensible from either direction.

### Cinematic Lite vs Full R3F (technical reference)

| Dimension | Lite | Full R3F |
|---|---|---|
| What's rendering | Pre-rendered video + AI stills, scroll-scrubbed | Real-time WebGL scene |
| Stack | GSAP, Lenis, Framer Motion, optionally Theatre.js | Lite + R3F + drei + custom GLSL shaders + glTF model |
| Build time solo | ~40 hrs | ~90+ hrs (mostly perf tuning) |
| Mobile perf | Usually fine — browsers handle video well | Brutal by default — every frame is a budget fight |
| Interactivity | No (passive scroll experience) | Yes (drag, hover, click change the scene) |
| When it earns the cost | — | Click-to-explore unit selectors, configurators, live availability heatmaps |

**Default offering for the Cinematic tier:** **Full R3F.** Founder rationale: the Sites landing-page demo at `trochai.com/sites` is itself a portfolio piece — clients pick a tier based on what they see in the showcase, so the showcase has to demonstrate "best of the best." Building Full R3F first (May 2026) anchors the premium pitch and pays back across every prospect for years. Lite remains available as a value option for budget-conscious developer clients. **After the initial May 2026 showcase demo, all Cinematic Full R3F builds for paying clients require 50% deposit before kickoff** (founder's clock isn't free).

---

## Content production add-ons

Variable — only kicks in if the client lacks usable photos / video / CGI. Sold as a separate line item so the website price stays clean and the conversation about content costs is up-front.

| Item | Price (USD) | When |
|---|---|---|
| AI atmospheric hero (Nano Banana, 3 variants) | **$200** | Editorial / Maximalist when photos are weak |
| Per-listing AI photo restoration | **$25/listing** | Up to 30 listings; bulk discount above |
| Cinematic AI render set (10 hero + 3 key visuals via Midjourney + Runway) | **$1,800** | Cinematic only |
| Drone-footage repurposing (client-supplied) | **$600** | Maximalist / Cinematic |
| Custom 3D building model + walkthrough (outsourced) | **$3,500** | Cinematic Full R3F only — outsource ceiling, do not promise solo |

---

## Per-change rate card (after launch — for any client, any plan)

### Free forever (CMS via Trochai Inbox — client self-serves)

- Add / edit / remove **properties**, **projects**, **blog posts**, **agent profiles**
- Update **contact info**, **social links**, **WhatsApp number**
- Upload / replace **photos** on existing listings
- Update **prices, descriptions, status** (active / paused / sold)

### Paid (design / structural — billable)

| Change | Price (USD) | Turnaround |
|---|---|---|
| Color tweak (existing tokens) | **$150** | 48h |
| Typography swap | **$250** | 48h |
| New section (existing template patterns) | **$450** | 5 business days |
| New page (using existing patterns) | **$650** | 5 business days |
| Layout restructure | **$950** | 7 business days |
| New animation / scroll behavior | **$750** | 7 business days |
| Archetype re-skin (e.g., Editorial → Maximalist) | **50% of new template list price** | 14 business days |
| Out-of-band hourly rate | **$80/hr**, billed in 30-min increments, 1-hour minimum | as-arranged |

**Hourly rate intentionally below Luxury Presence ($150–$200/hr) to win small jobs and above CR-local ($20–$50/hr) to defend brand.**

---

## Payment terms (all builds, with or without promo)

Standard for design work: **50% upfront on signing the SOW, 50% on delivery**. Protects against ghosting, gives the client skin in the game, and keeps the founder's cash flow honest.

- **50% upfront** = invoice issued the day the SOW is signed. Build kickoff happens **after** payment lands.
- **50% on delivery** = invoice issued when the staging site passes the founder's QA + the agreed revision round. Site goes live to the client's domain after final payment lands.
- **Refunds:** if either party walks before kickoff, the upfront 50% is refundable minus any documented design discovery hours billed at $80/hr. Once the build has started, the upfront 50% is non-refundable.
- **Promo redemptions (May 2026 free-with-Inbox-annual):** the *site* is free, but the **annual Inbox subscription is paid in full upfront** (no installments) — that's what funds the Sites build. Polar invoice processes the Inbox annual payment on signing; Sites build kicks off after the Inbox payment clears.

---

## Maintenance — the long-term revenue engine

Trochai Sites delivers a website. **The retainers below are how Trochai Sites makes money long-term**, not the build fees. Every Sites client should be pitched a retainer at handoff. Industry data: design agencies earn 60–70% of LTV from retainers, not initial builds.

Stickier revenue, better margin, and predictable monthly cash flow. Anchored to industry benchmarks ($500–$3K/mo small business; $2K–$6K/mo standard).

| Tier | Price/mo (USD) | Included | Best for |
|---|---|---|---|
| **Care** | **$350/mo** | 2 hours design changes + unlimited CMS support + 48h response | Solo agencies who want someone "on call" |
| **Grow** | **$950/mo** | 6 hours + priority response (24h) + monthly check-in call | Agencies actively iterating sections, A/B testing copy |
| **Scale** | **$2,200/mo** | 14 hours + monthly strategy call + 3-month roll-over of unused hours | Multi-development developers, larger agencies |

---

## May 2026 launch — two simultaneous offers

Both run **May 1–31, 2026.** They do **not** stack — clients pick one.

### Offer A — Inbox annual promo (free Sites template)

For new annual Trochai Inbox subscribers in May. Site choice is gated by Inbox tier:

| Inbox annual tier | Annual price (USD) | Free template | Claimed value | Multiple |
|---|---|---|---|---|
| Solo | $348/yr | Agency Editorial | "$2,500 site included" | 7.2× |
| Pro | $1,188/yr | Editorial OR Maximalist | "$4,500 site included" | **3.8× — make this the default ask** |
| Enterprise | $2,988/yr | Any (incl. Cinematic Lite) | "$9,500+ site included" | 3.2× |

**Hard cap: 3 redemptions** to start (raise to 5 only if delivery quality holds). Cap exists to protect founder sales hours from "free site" scope creep.

**Scope contract for promo redeemers (non-negotiable, goes in the SOW):**

- ONE template (matching their tier)
- ONE round of revisions on launch
- Ongoing free CMS edits forever (via Inbox)
- Anything beyond that triggers the per-change rate card immediately
- 14-day delivery from kickoff after content + brand inputs received

### Offer B — 50% off à-la-carte (for non-Inbox-annual buyers)

For clients who want a Trochai Site in May but aren't ready to commit to annual Inbox.

| Template | May 50%-off price | List price | Savings |
|---|---|---|---|
| Agency Editorial | **$1,250** | $2,500 | $1,250 |
| Agency Maximalist | **$2,250** | $4,500 | $2,250 |
| Development Boutique | **$2,750** | $5,500 | $2,750 |
| Development Cinematic (Lite) | **$4,750** | $9,500 | $4,750 |

**Cinematic Full R3F is excluded from the May 50% off** — always list-price + 50% deposit, no exceptions. Cinematic Lite is available at $4,750 in May. The reasoning: a 90-hour Full R3F build at half-price burns the founder's clock; a 40-hour Lite build at half-price is sustainable.

**Why Offer B works:** the $1,250 Editorial entry point matches CR WordPress-shop pricing, but the client gets a Tailwind v4 / Next.js 16 site auto-synced to the same backend Trochai Inbox uses. Strong wedge into the local market — and these clients become natural upgrades to Inbox later.

---

## Solo-founder scope rules (internal — do not surface to clients)

Per `.claude/rules/solo-founder-constraints.md` and `.claude/rules/client-first-priority.md`:

- **AM block (4 hrs/day max):** Sites build work
- **PM block:** Inbox sales (3 Looms/day minimum, master-leads.csv discipline per `DAILY-CHECKLIST.md`)
- **No build ever exceeds the AM block** without explicit override; mid-day mode-switches kill output
- **Promo redeemers are scoped tight:** SOW must specify the ONE template, ONE revision round, and the per-change rate card kicks in immediately afterward
- **Cinematic Full R3F:** the *first* build (the Sites landing-page showcase demo, May 2026) is a deliberate marketing investment by the founder — ~90 engineering hours absorbed as Trochai's portfolio piece, justified by "anchor the premium pitch with what's possible." **All subsequent Cinematic Full R3F builds for paying clients require 50% deposit ($6,750) before kickoff.** Lite remains the default for clients on tight budgets.
- **Founder overruled the board's 1-template-by-May recommendation and committed to all four by May, including Cinematic Full R3F.** Slip risk is on the founder. CPO/CFO/CMO recorded their dissent at 2026-04-29.

---

## Trochai Sites product page on `trochai-landing` (spec)

The landing repo (`trochai-landing/`) gets a new page at `/sites` (and `/sitios` localized) and a new top-nav item.

### What the page renders

1. **Hero** — the shared-backend differentiator one-liner + CTA "Ver demos en vivo"
2. **Live demos grid** — four cards, each linking to the live demo on its own subdomain (e.g., `demo-editorial.sitios.trochai.com`). Each card shows: thumbnail, template name, archetype badge, "Ver demo" CTA. Placeholder cards with "Disponible mayo 2026" badge for any not yet shipped.
3. **What's included in every template** — bullets from the "What's in every template" section above
4. **À-la-carte pricing table** — pulled from the rate card above
5. **May 2026 promo callout** — both offers side-by-side, with the Inbox-annual offer highlighted as the better deal (3.8× multiple at Pro tier)
6. **Per-change rate card + retainer tiers** — collapsible accordion (don't lead with this; it's a trust-builder, not a pitch)
7. **The shared-backend explainer** — short visual diagram showing Inbox ↔ Supabase ↔ Sites, with the *"Cero doble carga de datos"* line as the headline
8. **FAQ** — covering: domain ownership, what we deliver vs maintain, change-request process, content production add-ons, what counts as a "free CMS edit" vs paid change
9. **Final CTA** — WhatsApp form + Calendly link for a 15-min site consultation

### Demo subdomains

Each of the four template demos lives at `demo-<slug>.sitios.trochai.com` (or as a subroute under `sitios.trochai.com/demos/<slug>` — TBD). Demos use seeded data from a `_demo` organization in the inbox Supabase (status = active so they're anon-readable).

### Implementation order

1. Lock pricing copy in this doc (✓ done)
2. Build Editorial template demo first — it's the first thing the page links to (May 1–19)
3. Build the `/sites` page in `trochai-landing` with placeholder demo cards and "Disponible mayo 2026" badges on the unfinished archetypes
4. As each template ships, replace the placeholder card with the live demo link
5. Launch the page **Monday May 4, 2026** (newsletter day) with whatever demos are ready

### Nav placement

Existing `trochai-landing` top nav: see `trochai-landing/CLAUDE.md` for current items. Insert **Sitios** as a new item, OR rename **Producto** → **Productos** with a dropdown listing `Inbox` and `Sitios`. The dropdown approach scales as future Trochai products land; recommend that route.

---

## AI tooling stack (internal ops reference)

Visual asset production for templates and demos uses a $0 free-tier stack documented in `trochai-business/TROCHAI-SITES-AI-TOOLING.md`. Headlines:

- **Images:** FLUX.1 [schnell] (Apache 2.0, fully commercial, scriptable) + Bing Image Creator (DALL-E 3, free, commercial)
- **Video:** Google Veo 3.1 via Flow (free, 50 credits/day, watermarked) + LTX-2.3 local (Apache 2.0, watermark-free for clients)
- **Architecture renders:** Veras 15-day trial → local SDXL + interior LoRAs
- **3D for Three.js:** Sketchfab CC0 + Hyper3D Rodin trial (commercial-clean)

**Realistic paid floor for a $13,500 Cinematic client: $50–150 in tooling.** That's <1% of revenue — bake into the SOW under "production add-ons" or absorb as COGS.

**The Nano Banana trap** ($45 surprise April 2026): Pro endpoint via API has no free quota. Use AI Studio web UI for Pro, or `gemini-2.5-flash-image` via API. See AI tooling doc §2.

---

## What this doc IS the source of truth for

- Trochai Sites price points (à-la-carte, change-request, retainer)
- May 2026 promo offers and tier-gating
- Free-vs-paid policy
- Scope contract terms for promo redeemers
- Cinematic Lite vs Full R3F policy

If this doc and the landing page diverge, **this doc wins** — the landing page is updated to match, not the other way around.

## What this doc is NOT

- Implementation guide for the templates (that's `trochai-client-sites/CLAUDE.md`)
- Loom outreach scripts (those live in `loom-scripts/`)
- The Sites SOW itself — that's a separate per-client document derived from this one
