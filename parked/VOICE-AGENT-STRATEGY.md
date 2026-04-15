# Trochai Voice Agent — Strategy & Feasibility Review

> Internal strategic memo. Not a product spec. Goal: decide **whether** to build, **what** to build, and **how** to build it — informed by the Sofia Voice Agent template (`github.com/santmun/sofia-voice-agent`) that triggered this review.
>
> Date: 2026-04-14
> Author: Leeren + Claude (research synthesis)
> Status: recommendation in place; no green-light yet — needs customer-signal validation (see §11).

---

## 1. TL;DR

1. **Do it — but not now, and not the way the template does it.** Voice AI for LATAM real estate is greenfield; the Sofia template is a credible demo but wrong for Trochai's stack.
2. **Make it a module of Trochai Inbox, not a standalone product.** Our unfair advantage is that we already hold the contact, property, project, embedding, intent-classifier, and multi-tenant layer — the template rebuilds all of that from scratch in Notion. Integrated voice + WhatsApp is a moat; standalone voice is a commodity race against Fonema, Synthflow, and the Horizontes IA reseller tail.
3. **Lead with WhatsApp Business Calling API, not PSTN.** Meta shipped WABA voice calling on July 1 2025, already supports Vapi/ElevenLabs pipelines, and LATAM consumer trust in WhatsApp is ~2× trust in cold phone calls. This plays to our strength and sidesteps 80% of the telephony compliance mess.
4. **Recommended v1 stack:** WABA Calling API (primary) + Retell AI + Telnyx SIP trunk (PSTN fallback) + existing Supabase + existing AI layer. Drop Modal, Notion, and Cal.com from the template entirely.
5. **Recommended name:** **Trochai Línea** (English: *Trochai Line*). Pairs naturally with Trochai Inbox. "Inbox + Línea" = text + voice under one platform.
6. **Effort to production-grade MVP:** ~2 weeks engineering if we go Option A (Retell+Supabase), ~4–6 weeks for Option B (LiveKit+OpenAI Realtime native). Start with A, migrate later if economics force it.
7. **Do NOT launch in Spain.** Post-June 2025 mobile-number ban + June 2023 opt-in requirement + August 2026 EU AI Act Article 50 = outbound cold calling is illegal and inbound alone doesn't justify the compliance overhead. Costa Rica + Mexico first.

---

## 2. What the Sofia template actually is

A working reference implementation of a Spanish-speaking inbound/outbound voice agent for real estate, built by Santiago Muñoz (Horizontes IA community, `iahorizontesacademy.com`). The "template" is the free, open-source version; Horizontes IA monetises it via a course that trains freelancers to resell the system at ~$2,500 USD/client.

| Layer | Choice | Verdict for Trochai |
|---|---|---|
| Conversation orchestration | Retell AI | **Keep for v1** — fastest path to production voice |
| Backend compute | Modal (Python, serverless) | **Drop** — split-brain with our Vercel/Supabase stack |
| Telephony | Twilio SIP trunk | **Keep the model, swap vendor** — Telnyx is 30–50% cheaper for CR |
| CRM | Notion (3 DBs: properties, leads, calls) | **Drop** — toy-grade (3 req/s, no bulk writes, no RLS) |
| Scheduling | Cal.com | **Drop** — we already own the contact + agent layer; a `visit_bookings` table in Supabase is strictly better |
| Post-call analysis | Claude Sonnet 4.5 | **Keep** — same vendor we already use |
| Dashboard | Next.js + shadcn/ui | **Drop the separate app** — surface everything inside Trochai Inbox's sidebar app |

The template is valuable as a **reference for agent prompts, Retell dynamic-variables usage, webhook shapes, and post-call-summary patterns** — not as code we ship. Treat `trochai-voice-agent/` as study material, port the ideas into `trochai-inbox/`, archive the template repo.

---

## 3. Market snapshot (April 2026)

### The pain is real and measurable
- 73% of real estate leads are **never contacted** (AgentZap, 2026)
- 52% of leads arrive **after business hours** (Apten, 2026)
- Responding within **5 min = 21× more likely to qualify** vs waiting 30 min (GreetNow)
- LATAM agent average response time: **47 hours** (RubixOne)
- Grupo Herso (Mexico): 1,400 leads/mo via WhatsApp AI → $30M annual revenue, sub-5-second response

### But the LATAM channel reality is WhatsApp-first
- **85% of LATAM consumers prefer a real human over the phone** (ServiceNow 2025)
- **93% feel wary of voice assistants**
- WhatsApp is the *trusted* channel — treated as the cultural default for business and personal
- >80% of Costa Ricans use WhatsApp daily

**Implication:** A voice-first product in LATAM loses to a WhatsApp-first product. But a WhatsApp-inbox-native voice *layer* wins, because it (a) operates inside the trusted channel via WABA Calling API, (b) falls back to PSTN only for customers who actually call in, and (c) carries existing conversation context into the call.

### Competitors
| Competitor | Position | Threat level |
|---|---|---|
| **Fonema AI** | LATAM-native voice (regional accents, <1s latency) | **High** — only purpose-built LatAm player; likely custom-priced enterprise |
| **Retell / Vapi / Synthflow / Bland** | Horizontal voice platforms | **Medium** — will be used by our competitors and resellers, but lack WhatsApp data context |
| **Horizontes IA resellers (Sofia stack)** | Freelancers selling Sofia-template installs at ~$2.5k | **Medium** — will flood the market with low-polish implementations; opportunity to be the "real" option |
| **HubSpot Breeze Prospecting Agent** | CRM-native AI, $1/qualified lead (launched today) | **Medium-long** — LATAM SMBs rarely run HubSpot; but signals commoditisation of voice bolt-ons in 12–18 months |
| **VivaSpeak / Ropofy** | Spain-focused | **Low for CR/MX**, relevant if we ever enter Spain (which we shouldn't) |

### Spanish voice quality 2026
- Best stacks (GPT-4 Nano + Cartesia Sonic-Turbo): **750–1,070 ms time-to-first-token for Spanish** — usable for inbound receptionist, noticeably laggy for outbound
- ElevenLabs Flash v2.5: 75 ms first-audio; Cartesia Sonic-2: 95 ms
- Generic platforms default to **Castilian** voices; LatAm accents require explicit voice-ID selection or Fonema
- Sub-500ms end-to-end for Spanish **not yet achieved** industry-wide (vs English sub-500 is routine)

---

## 4. Compliance reality check (by country)

| Market | Inbound AI call | Cold outbound AI call | Blocker? |
|---|---|---|---|
| **Costa Rica** | ✅ Clean | ⚠️ SUTEL Art. 44 requires prior opt-in; Ley 8968 requires PRODHAB-registered data-transfer agreement for US-hosted call recordings | No, but need CR business entity for +506 number + PRODHAB filing |
| **Mexico** | ✅ Clean | ⚠️ REPEP registry check + 8am-7pm window + LFPDPPP 2025 requires AI disclosure | No — doable with a compliant workflow |
| **Colombia** | ✅ Clean | ⚠️ SIC "previo, expreso, informado" consent — strictest in LATAM | No — but outbound only with documented consent |
| **Spain** | ✅ Clean | ❌ **Blocked.** June 2023 mandatory opt-in + June 2025 mobile-number ban + Aug 2026 EU AI Act Art. 50 | **Do not launch outbound in Spain.** Inbound-only doesn't justify overhead |

### Mandatory call-open script (all markets, safe default)

> *"Hola, soy [Nombre], un asistente de inteligencia artificial de [Empresa]. Esta llamada puede ser grabada. ¿Está de acuerdo en continuar?"*

Gate the conversation on explicit "sí". This single script handles:
- EU AI Act Article 50 (transparency)
- Mexico LFPDPPP 2025 (AI disclosure)
- Two-party consent for recording (Spain, Colombia, and safe default for CR)

### Legal must-haves before a single call ships
1. Register a CR SRL (Cédula Jurídica) to buy a +506 Twilio/Telnyx number — ~$500–1,000 via local abogado
2. File PRODHAB data-transfer agreement covering Retell + Anthropic + Deepgram (all US-hosted processors)
3. Add AI-disclosure + recording-consent script as a **locked first-turn** of every agent
4. Implement per-organization opt-in/do-not-call list (schema change in `contacts`)
5. Scope v1 to **inbound + warm outbound only** (contacts who opted in via WhatsApp or web form in the last 30 days)

---

## 5. The WhatsApp Business Calling API changes everything

Meta launched the WhatsApp Business Calling API on **July 1, 2025**. Key facts from the research:

- **Inbound (user-to-business) calls are FREE**
- **Outbound** requires prior in-WhatsApp permission request, then pay-per-call
- **Supports AI voice pipelines via Vapi and ElevenLabs** (confirmed by Meta + TechCrunch)
- Limit: 100 simultaneous calls per WABA
- Globally available to API-tier WABA accounts as of late 2025

**Why this matters for Trochai:**
1. We already have active WhatsApp threads with leads — consent is implicit, answer rates are high, and conversation context carries into the call
2. It's not cannibalistic with WhatsApp — it's a **channel escalation** (chat → voice → visit) inside the same thread
3. It sidesteps ~80% of telephony compliance pain (no REPEP / Robinson List / mobile-ban issues)
4. It's a feature no horizontal voice-AI vendor (Retell, Vapi, Fonema) can replicate cleanly — they don't hold the WhatsApp relationship

**This is the product.** Not "AI that answers your phone." It's **"AI that turns a WhatsApp chat into a voice call in one tap, with full context."** PSTN voice is a secondary fallback for customers who genuinely call an agency number.

---

## 6. Should it be part of Trochai Inbox, or a new product?

### Integrated (part of Inbox) — **recommended**

**Pros:**
- Reuses existing multi-tenant RLS (`organization_id`) — zero re-implementation
- Reuses intent classifier, filter extractor, hybrid search, Whisper transcription (`web/src/lib/ai/` is channel-agnostic enough to be adapted in days, not weeks)
- Voice calls thread into existing `conversations` table as a new message type — unified inbox is the selling story
- Billing on existing Polar subscriptions as a tier upgrade (add voice to Pro/Enterprise plans) — no separate SKU / checkout
- Customer support, docs site, admin panel, domain routing, auth — all already built
- Matches positioning: "Trochai is the platform for agency conversations, across channels"

**Cons:**
- Inbox codebase grows — discipline required (keep voice logic in `web/src/lib/voice/`)
- Harder to spin off later if we ever want to sell Trochai Línea to non-real-estate verticals (the template's target market)

### Standalone product

**Pros:**
- Clean separation, could be sold to verticals outside real estate (Sofia's dream)
- Doesn't bloat the inbox

**Cons:**
- We'd rebuild contacts, multi-tenancy, RLS, billing, admin, auth — that's 6–8 weeks of yak-shaving for something we already have
- The integrated story ("Inbox + Línea") is genuinely our differentiator; standalone voice is a commodity race
- Two codebases to maintain, two deployment pipelines, two sets of env vars, two CI/CD flows

**Verdict:** Integrated. Call it **Trochai Línea** (or Trochai Line in English). Ship it as a module inside `trochai-inbox`, surfaced in the sidebar as a peer of "Inbox", "Propiedades", "Proyectos".

The `trochai-voice-agent/` folder becomes a **reference/study repo** that we can delete after porting ideas, or keep as a public showcase.

---

## 7. CRM question: do we need to build our own?

> *User asked: "Should we have our own small CRM because we have, like, a small CRM?"*

**No — but we need to mature the one that's already implicit in Trochai Inbox.** The inbox already has:

- `contacts` (with status pipeline, tags, source, assigned agent)
- `conversations` (with channel, assignment, bot enable/disable)
- `messages` (unified history per contact)
- `properties` + `projects` (with pgvector embeddings)
- `scheduled_followups` (cron-driven outreach)

The gaps the audit identified (what a voice agent needs that doesn't exist yet):

| Gap | Proposed addition | Complexity |
|---|---|---|
| Call records | `calls` table: duration, direction, disposition, recording URL, cost | 1 migration |
| Call transcripts | `call_transcripts` table: Whisper/Retell transcript, embedded for search | 1 migration |
| Lead scoring / temperature | Columns on `contacts`: `lead_score`, `temperature`, `next_action`, `last_contact_at` | 1 migration |
| Contact activity timeline | `contact_activity` unified table (message sent, call made, property viewed, visit booked) | 1 migration |
| Visit bookings (replace Cal.com) | `visits` table tied to properties + agents | 1 migration + simple picker UI |
| Voice channel config | Extend `channels` table to support `type: voice` with phone_number / carrier config (or separate `voice_channels`) | 1 migration |
| Opt-in / do-not-call list | `contact_preferences.voice_opt_in`, `voice_opt_out_at` | 1 migration |

Total: **~7 migrations, 2–3 days of schema work.** This is maturing the implicit CRM, not building a new one. Don't separate it into a product — it's part of Inbox.

**Do NOT build a standalone CRM UI.** HubSpot/Salesforce/Pipedrive exist. Our wedge is "conversation-first" — leads live in chats and calls, not in a form-filled record. The contact profile page in Inbox is the CRM.

---

## 8. Devil's advocate — reasons NOT to build this

Taking this seriously because it's the hardest section to write honestly.

1. **LATAM consumers don't want to talk to bots.** 85% prefer humans, 93% are wary. We could ship a technically-excellent product nobody uses. *Counter:* inbound receptionist + warm WhatsApp escalation is a lower-tolerance-needed use case than cold outbound.

2. **CRM-native voice is coming (HubSpot Breeze, Zoho Zia).** In 18 months, voice-AI may be a bundled feature in every CRM. We'd be building something that commoditises into a checkbox. *Counter:* LATAM SMB real estate doesn't run HubSpot — they run WhatsApp. Our voice layer is WhatsApp-native, not CRM-native, so the commoditisation threat is different.

3. **Fonema AI is already LATAM-native.** They have regional accents, sub-1s latency, and purpose-built agent templates for real estate. They could eat our lunch on voice quality alone. *Counter:* we don't compete on voice quality — we compete on integration depth with WhatsApp + contact history + property data. Fonema has none of that.

4. **We're not resourced for it.** Trochai Inbox has a long product roadmap; voice adds complexity, ops burden, compliance work, and a new failure surface. Every minute on voice is a minute not on Inbox polish. *Counter:* real. This is why §11 requires customer signal before green-lighting.

5. **The Sofia template is a course-selling asset, not a product.** Santiago's economic incentive is to train resellers who sell $2.5k installs — not to ship a scalable product. If we lift ideas from it we're implicitly competing with the course's alumni. *Counter:* irrelevant — we build our own implementation, not theirs. The template is just reference material.

6. **PSTN voice costs compound badly.** $0.28/min blended on Costa Rican mobile × 10k min/mo = $2,800/mo pure infra for a single high-volume customer. Margins on voice are worse than on messaging. *Counter:* WABA Calling API flips this — inbound is free, outbound is pay-per-call but against consented numbers. PSTN becomes a fallback, not the primary path.

7. **Retell is a black box with confusing pricing.** Advertised $0.07/min becomes $0.13–$0.31/min in practice. Vendor could 2× pricing overnight. *Counter:* valid, so plan the migration path to Option B (LiveKit + OpenAI Realtime) from day 1 — keep voice-agent logic framework-agnostic.

8. **Outbound is where the revenue is, but it's the most regulated.** Inbound-only keeps us legally clean but limits the revenue ceiling. *Counter:* warm outbound to already-opted-in WhatsApp contacts is compliant in all target markets. That's the 80/20.

**Overall:** reasons to not build are strong enough that this isn't an immediate next-quarter priority. But none are deal-breakers, and the WABA Calling API is a genuinely new strategic opening that didn't exist 9 months ago.

---

## 9. Tech stack recommendation

### v1 (Option A — fast path, ~2 weeks)

```
Inbound PSTN call (+506 number, Telnyx SIP trunk)
        or
Inbound WhatsApp voice call (WABA Calling API via Vapi integration)
        ↓
Retell AI (conversation, STT, LLM, TTS — Spanish voice via ElevenLabs or Cartesia)
        ↓
Webhook → Next.js API route in trochai-inbox/web/src/app/api/voice/*
        ↓
Tool calls → reuse existing:
  - intent-classifier.ts
  - filter-extractor.ts
  - hybrid-search.ts (property + project search)
  - visit-scheduler.ts
        ↓
Supabase:
  - insert call record, transcript
  - update contact (last_contact_at, lead_score)
  - book visit in new `visits` table
        ↓
Post-call async (Vercel Background Function):
  - Claude Sonnet 4.5 summary + lead scoring
  - Push summary into existing conversation thread in Inbox
```

**Changes to existing Trochai Inbox codebase:**
- 7 migrations (§7)
- `web/src/lib/voice/` — new module with Retell client, webhook handlers, agent prompt templates (port from Sofia)
- `web/src/app/api/voice/*` — 6–8 route handlers (webhook, call-started, call-ended, tool-search-properties, tool-create-lead, tool-book-visit)
- `web/src/app/[locale]/(app)/llamadas/*` — new inbox sub-route for call history, listening to recordings, agent config
- Extend Polar billing with a "Voice add-on" price — per-minute or flat monthly with included minutes

**What we do NOT build:**
- ~~Modal deployment~~ (dropped — use Next.js API routes)
- ~~Notion databases~~ (dropped — use Supabase)
- ~~Cal.com~~ (dropped — use new `visits` table)
- ~~Separate dashboard app~~ (dropped — integrate into existing Inbox sidebar)

**Estimated blended cost at 10k min/mo:** ~$0.18–$0.22/min (Retell blend + Telnyx CR)

### v2 (Option B — native build, post-PMF)

- LiveKit Agents (open-source Python framework; $0.01/min + model costs)
- OpenAI Realtime API for speech-to-speech
- Deepgram Nova-3 for Spanish STT ($0.0059/min)
- ElevenLabs Flash for TTS
- Cuts Retell dependency; **~$0.10–0.11/min blended, 20–35% cheaper**
- Migrate only once we have >50k min/mo (where Retell's pricing compounds painfully)

### Red flags to guard against (from tech review)
1. **Webhook HMAC validation** — Retell provides `X-Retell-Signature` with replay-window. The Sofia template may not implement it. Require this from day 1.
2. **Idempotency keys** on every webhook handler — concurrent calls to same agent will race.
3. **Multi-tenant leakage in Retell** — Retell's agent config lives in their dashboard. Each Trochai org needs its own Retell agent + phone number + SIP trunk. Plan this in the schema (`organization_retell_config`).
4. **Secrets rotation** — all API keys go through Vercel env vars, never committed to `.env`. Same pattern as the rest of Trochai Inbox.
5. **Recording retention policy** — Ley 8968 + LFPDPPP both require purpose limitation. Default: delete recordings after 90 days unless customer opts into longer retention. Make this configurable per org.

---

## 10. Naming

Top candidate: **Trochai Línea** *(Spanish primary; English: Trochai Line)*

Rationale:
- Pairs naturally with Trochai Inbox. "Inbox + Línea" = text + voice. Easy story on the landing page.
- "Línea" is warm and Spanish-native — better than a Castilian-feeling agent name (Sofia, Ana, Laura) which would clash if we later localise to Mexico-Argentina-Colombia accents.
- Not a person's name — avoids the gendered-assistant trope and the "replace a human" framing. Positions as infrastructure, not a replacement hire.
- Short, easy to trademark in CR/MX, not obviously taken in LATAM proptech.

**Runners-up:**
- **Trochai Voz** — too generic
- **Trochai Atiende** — great verb ("answers") but long and Spanish-only
- **Trochai Concierge** — premium positioning but English-leaning and overused in hospitality
- **Trochai Responde** — clear, but risks sounding like a ticketing/helpdesk tool
- **A named agent persona (Sofia-style)** — rejected. Creates brand confusion if we sell to multiple industries, and puts us in Santiago's exact market framing.

**Decision parking lot:** if we ever spin out as a standalone product for non-real-estate verticals, the neutral "Trochai Línea" travels well to any industry (dental, clinic, restaurant, etc.) — which was exactly the template's "mega-sistema" ambition in `BRIEF_MEGA_SISTEMA.md`.

---

## 11. Recommended next steps

Do not green-light engineering yet. Do these first, in order:

1. **Customer signal (1 week).** Interview 5 existing Trochai Inbox customers. Ask:
   - How many inbound phone calls do you get per week that currently go unanswered or to voicemail?
   - What happens to a lead who calls instead of WhatsApps?
   - Would you pay an extra $X/mo for an AI that answers after-hours calls + escalates to WhatsApp?
   - Would you let an AI call back warm WhatsApp leads who haven't responded in 48 hours?
   - **Kill criterion:** if <3 of 5 say "yes, I'd pay for this," shelve for 6 months.

2. **PRODHAB + CR entity legal scoping (1 week, parallel).** Confirm cost and timeline for CR SRL + PRODHAB filing. Confirm that Retell + Anthropic + Deepgram adequacy-transfer agreements are workable. If this adds >$5k and >2 months upfront, revisit plan.

3. **Technical spike (3 days, after green-light).** Wire Retell to a test +506 Telnyx number. Make one end-to-end inbound call. Have it call `hybrid-search` to find a property in a test org. Verify latency, Spanish voice quality, tool-call reliability. This is the kill/proceed gate before real engineering investment.

4. **WABA Calling API pilot (1 week, after spike).** Get one org's WABA approved for Calling API access. Confirm Meta's current rate limits for LATAM accounts. Build a "click to voice call" action in the inbox that escalates a chat to an AI voice call over WhatsApp. This is the differentiator demo.

5. **MVP build (~2 weeks, Option A).** If steps 1–4 clear, ship v1 behind a Polar feature flag to 3–5 design-partner customers. Iterate on prompts and transcripts for 4 weeks before broader launch.

---

## 12. Open questions / decisions needed

- [ ] Does Leeren want this on the roadmap for 2026, or parked until Inbox reaches a specific MRR/customer threshold?
- [ ] Is there existing LATAM real estate voice-AI customer demand in the Loom Outreach Initiative conversations, or is this a greenfield ask?
- [ ] If we ship, does the Polar billing model become per-minute metered, flat monthly with included minutes, or a pure add-on tier?
- [ ] Brand: do we commit to "Trochai Línea" or workshop more names with a Spanish-native copywriter before locking it?
- [ ] Is the Sofia template repo (`trochai-voice-agent/`) kept as public reference, archived, or deleted after porting ideas?

---

## 13. Appendix — template contents inventory

File-by-file audit of what we actually received, for posterity:

```
trochai-voice-agent/
├── Agente de Voz.pdf                # Points to github.com/santmun/sofia-voice-agent + Notion prompt page
├── README.md                        # Course-recruitment colored README ("sell this for $2,500+")
├── BRIEF_MEGA_SISTEMA.md             # Santiago's brief for the paid "mega-sistema-ia" version (config-driven, 8 verticals)
├── CLAUDE.md                         # Stack summary (Retell + Modal + Twilio + Notion + Cal.com + Claude)
├── .env.example                      # All 9 required API keys
├── pyproject.toml                    # Python deps
├── app/                              # Python backend
│   ├── main.py                       # 8 FastAPI endpoints on Modal (health, retell-webhook, twilio-webhook, search-properties, create-lead, book-visit, update-lead-status, post-call-summary, trigger-outbound)
│   ├── config.py                     # env var loader
│   ├── outbound_worker.py            # cron-driven outbound dialer
│   ├── services/                     # notion_service, retell_service, twilio_service, calcom_service, claude_service
│   └── webhooks/                     # retell_handler, twilio_handler
├── dashboard/                        # Next.js + shadcn/ui (standalone analytics app, parallel to Inbox)
└── scripts/
    ├── create_retell_agent.py        # one-shot Retell agent provisioning
    ├── create_outbound_agent.py      # one-shot outbound variant
    └── test_functions.py             # smoke tests
```

**Everything of lasting value here is in `app/services/` (Retell + Claude prompt patterns) and `scripts/create_retell_agent.py` (Retell provisioning API usage).** The rest is infrastructure we'd replace.

---

*End of memo. Decision pending input from Leeren on §11 and §12.*
