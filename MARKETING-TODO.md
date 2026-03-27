# Marketing TODO

> Action items for Trochai Inbox GTM execution. Check off as you go.
> Strategy context: [MARKETING.md](./MARKETING.md)

---

## Phase 0: Validate ICP (This Week)

Everything else is blocked until we have real conversations.

### Build Prospect List (Day 1-2)

- [x] ~~Google "inmobiliaria Costa Rica" / "bienes raíces Costa Rica" and list 20 agencies~~ → See **[PROSPECT-LIST.md](./PROSPECT-LIST.md)**
- [ ] For each agency, capture:
  - Agency name
  - Location/zone (GAM, beach, etc.)
  - Owner/manager name (if findable)
  - WhatsApp number (usually on their website or Facebook)
  - Instagram/Facebook handle
  - Approximate team size
  - Notes (anything interesting about them)
- [ ] Check CCCBR directory for registered agencies
- [ ] Browse Encuentra24 top listing agencies
- [ ] Browse Facebook groups: "Bienes Raíces Costa Rica", "Inmobiliarias CR", etc.
- [x] ~~Put all of this in a simple spreadsheet~~ → Done in PROSPECT-LIST.md (20 agencies, tiered by fit)

**Where to find them:**
- Google Maps: search "inmobiliaria" in San José, Escazú, Santa Ana, Heredia
- Instagram: search #bienesraicescr #inmobiliariascr #propiedadescostarica
- Facebook: real estate agent groups in CR
- Encuentra24.com: see which agencies list the most properties
- CCCBR website

### Discovery Calls (Day 3-7)

- [ ] Send WhatsApp messages to 10+ agencies from your list. Draft message:

> "Hola [Nombre], soy [tu nombre]. Estoy creando una herramienta de WhatsApp para inmobiliarias en Costa Rica y me encantaría entender cómo manejan sus leads actualmente. ¿Tendría 15 minutos para una llamada rápida esta semana? Sin compromiso, solo quiero escuchar su experiencia."

- [ ] Schedule and complete at least **5 discovery calls** (10 is ideal)
- [ ] On each call, ask these questions (listen more than you talk):
  1. ¿Cuántos leads por WhatsApp reciben por semana?
  2. ¿Cuánto tardan en promedio en responder un mensaje nuevo?
  3. ¿Han perdido ventas por no responder a tiempo?
  4. ¿Qué herramientas usan para manejar las conversaciones? (WhatsApp Business, CRM, Excel, nada?)
  5. ¿Cuántos agentes tienen y cómo se asignan los leads?
  6. ¿Qué les quita el sueño sobre su proceso de ventas?
  7. ¿Quién es su mayor competencia y qué hacen diferente?
  8. Si pudieran resolver un solo problema con WhatsApp, ¿cuál sería?
  9. ¿Pagarían $X/mes por una herramienta que resolviera esto? (gauge price sensitivity)
- [ ] **Record the calls** (with permission) or take detailed notes
- [ ] Write down their **exact words** when describing pain — this becomes your messaging

### After Discovery Calls

- [ ] Summarize findings: What patterns do you see? What surprised you?
- [ ] Share summary with me so we can update ICP and manifesto in MARKETING.md
- [ ] Identify your 2-3 strongest prospects who could become pilot customers

---

## Phase 1: Lock the Manifesto (Week 2)

Requires: discovery call insights.

- [ ] Share your discovery call notes/summary with me
- [ ] **I will do:** Update ICP definition based on real data
- [ ] **I will do:** Rewrite value proposition and messaging using customers' own words
- [ ] **I will do:** Write 5 headline variations for A/B testing
- [ ] Review and approve the updated manifesto (you make the final call — AI researches, you judge)

---

## Phase 2: Landing Page (Week 2-3)

Can start in parallel with discovery calls.

- [ ] Decide: are we updating `trochai.com` landing page or creating a dedicated product page?
- [ ] **I will do:** Implement benefit-first hero section with winning headline
- [ ] **I will do:** Add lead magnet capture (email/WhatsApp for a free guide)
- [ ] **I will do:** Build a "Try it now" WhatsApp demo widget if feasible
- [ ] **I will do:** Add FAQ section addressing objections from discovery calls
- [ ] Set up basic analytics (Vercel Analytics, or Google Analytics if not already)
- [ ] Share landing page with 3-5 discovery call contacts for feedback

---

## Phase 2.5: Vibe Marketing Setup (Week 2-3)

Can start in parallel with landing page work. See **[VIBE-MARKETING.md](./VIBE-MARKETING.md)** for full details.

- [ ] Set up Remotion project (`npx create-video@latest trochai-videos`)
- [ ] Install Remotion Claude Code skills (`npx skills add remotion-dev/skills`)
- [ ] Install community ad skill (`claude skill install remotion-ads`)
- [ ] Create Template 1: **Stat Reveal** (for the 5-stat video series — no filming needed)
- [ ] Create Template 2: **Product Demo Animation** (animated phone mockup of Trochai inbox)
- [ ] Create Template 3: **Before/After Split Screen** (WhatsApp chaos → Trochai organized)
- [ ] Generate all 5 stat videos from Template 1 (change props per stat)
- [ ] Generate 9:16 + 1:1 + 16:9 versions of each
- [ ] Set up Perplexity MCP for ongoing market research
- [ ] Set up Playwright MCP for competitive intelligence
- [ ] **I will do:** Create positioning/copy skills tuned to Trochai's voice and ICP
- [ ] (Later) Create Template 4: **Property Listing Video** (data-driven from Supabase — becomes a product feature)

---

## Phase 3: Broadway Show — Organic (Week 3-5)

Requires: locked manifesto + landing page ready.

- [ ] Pick primary platform: Facebook + Instagram (confirm this is where CR RE agents are)
- [ ] Create a simple content calendar (3 posts/week for 3 weeks)
- [ ] **I will do:** Draft first batch of 9 organic posts (3 pain-point, 3 value/tips, 3 behind-the-scenes)
- [ ] Post consistently for 3 weeks
- [ ] Track: which posts get engagement FROM ICP (not random people)
- [ ] After 3 weeks: share metrics with me, we decide what's working

---

## Phase 4: Outbound + Loom Videos (Week 4-6)

Requires: messaging validated via organic social.

- [ ] Start social engagement: follow 20 agency owners, engage with their posts for 1-2 weeks
- [ ] **I will do:** Write Loom video script template
- [ ] Record 5 personalized Loom videos for top prospects
- [ ] Send via WhatsApp or email with value-first framing
- [ ] Track reply rates

---

## Phase 5: Paid Social (Week 6+)

Requires: organic posts that performed well.

- [ ] Boost top 3 organic posts as paid ads on Facebook/Instagram
- [ ] Set up ICP-only conversion pixel (only fire for qualified leads)
- [ ] Run for 3 weeks, track: conversion rate, traffic quality, activation rate
- [ ] **I will do:** Help set up tracking dashboard if needed

---

## Things I Need From You

These are the things only you (the human) can do. I can help with everything else.

| What | Why |
|---|---|
| **Have the discovery calls** | Only you can have real conversations with real people |
| **Share call notes/summaries** | I need real data to update ICP and manifesto |
| **Make strategic decisions** | ICP choice, positioning, messaging — AI researches, you decide |
| **Post on social media** | I can draft content, but you need to post and engage as yourself |
| **Record Loom videos** | Personal touch requires a real human face |
| **Attend CCCBR/RE events** | In-person trust-building only happens in person |
| **Final approval on messaging** | Review what I draft, apply your taste and market intuition |

---

## Things I Can Do For You

Just ask and I'll execute:

- [x] ~~Draft discovery call script in a shareable format~~ → Included in PROSPECT-LIST.md
- [x] ~~Build the prospect list spreadsheet template~~ → PROSPECT-LIST.md with 20 agencies + personalized messages
- [ ] Write/update all messaging and copy
- [ ] Draft organic social post content (Spanish + English)
- [ ] Write Loom video scripts
- [ ] Create lead magnet content (WhatsApp guide, templates, etc.)
- [ ] Update landing page code (trochai-landing)
- [ ] Set up analytics/tracking
- [ ] Analyze metrics and recommend iterations
- [ ] Update MARKETING.md as we learn
