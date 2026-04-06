# Launch Checklist — Template Library + Distribution

Follow in order. Each step has where to find the info.

---

## Phase 1: Deploy (Today — 30 min)

- [ ] **Push trochai-landing to main**
  ```bash
  cd trochai-landing && git push origin main
  ```
  Then go to GitHub → merge the Release Please PR → deploys to `trochai.com`

- [ ] **Verify live pages work:**
  - `trochai.com/es/herramientas/plantillas-whatsapp` (template library ES)
  - `trochai.com/tools/whatsapp-templates` (template library EN)
  - `trochai.com/es/propiedades/apartamentos-en-escazu` (sample pSEO page)
  - `trochai.com/es/blog/best-crm-real-estate-costa-rica` (sample blog article)
  - Check the "Tools" dropdown in the navbar

- [ ] **Submit sitemap to Google Search Console**
  - Go to Search Console → Sitemaps → submit `trochai.com/sitemap.xml`
  - This notifies Google about the 116 new pSEO pages + 10 new blog articles

---

## Phase 2: Generate Videos (Today — 1 hr)

- [ ] **Generate voiceovers for both promo videos**
  ```bash
  cd trochai-videos
  npx tsx src/scripts/generate-voiceover.ts --id template-reveal
  npx tsx src/scripts/generate-voiceover.ts --id template-error
  ```
  Scripts are in: `VOICEOVER-SCRIPTS.md` (#11 and #12)

- [ ] **Preview compositions in Remotion studio**
  ```bash
  npm run dev
  ```
  Open browser → select "Template-Library-Reveal" and "Template-Library-Error"

- [ ] **Render both videos**
  ```bash
  npx tsx src/scripts/render-video.ts --id Template-Library-Reveal --quality social
  npx tsx src/scripts/render-video.ts --id Template-Library-Error --quality social
  ```
  Output: `out/Template-Library-Reveal.mp4` and `out/Template-Library-Error.mp4`

- [ ] **Record Screen Recording video (Script A)**
  This one is NOT Remotion — it's a real screen recording of you using the template library:
  1. Open `trochai.com/es/herramientas/plantillas-whatsapp` on your phone or desktop
  2. Record yourself: open a template, type in a name, see the preview update, click copy
  3. Keep it under 15 seconds
  4. Add the voiceover in CapCut or Instagram Edits

---

## Phase 3: LinkedIn Networking (Today + ongoing — 1 hr today)

- [ ] **Connect with Tier 1 targets (20-30 requests today)**
  - File: `trochai-business/linkedin-networking-targets.md`
  - Start with Category 1 (CR Real Estate Industry) — these are the people who'll see your posts
  - Send connection request with a short note: "Hola, estoy construyendo herramientas de tecnología para el sector inmobiliario en CR. Me encantaría conectar."
  - Do NOT pitch Trochai in the connection request

- [ ] **Follow all company pages listed**
  - RE/MAX CR, Coldwell Banker CR, KW CR, NATIVU, LX, Sotheby's CR, etc.
  - This makes your posts visible in their ecosystem

- [ ] **Connect with PropTech / SaaS founders (10-15 requests)**
  - Category 2 and 3 from the networking targets file
  - These people amplify your content when they engage

---

## Phase 4: Social Media Launch (Mon Apr 7)

### Monday
- [ ] **Post LinkedIn announcement (Post 5 — "We just shipped")**
  - Full caption ready in: `trochai-business/TEMPLATE-LIBRARY-PROMO-PLAN.md` → Section 2, Post 5
  - Post from your personal profile, not a company page

- [ ] **Post Instagram Reel (Script A — screen recording)**
  - Caption ready in: Promo plan → Section 2, Post 1 (Instagram caption)
  - Or schedule via Metricool

- [ ] **Post same video on TikTok**
  - Caption ready in: Promo plan → Section 2, Post 1 (TikTok caption)

### Tuesday
- [ ] **Post in 3 Facebook groups**
  - Template post ready in: Promo plan → Section 4, "Facebook Groups"
  - Groups: Bienes Raices Costa Rica, Agentes Inmobiliarios CR, Inmobiliarias y Propiedades CR
  - Stagger posts (don't post all 3 at once — space by 2-3 hours)

- [ ] **Instagram Stories (3 slides)**
  - Slide 1: "El problema" (agents don't know what to write)
  - Slide 2: Screenshot of template library
  - Slide 3: Link sticker to the tool

### Wednesday
- [ ] **Post Instagram Reel (Template-Library-Reveal video)**
  - Caption ready in: Promo plan → Section 2, Post 2 variant
  - Schedule via Metricool

- [ ] **Post same on TikTok**

### Thursday
- [ ] **Post LinkedIn educational post (Post 4 — "The follow-up problem")**
  - Full caption ready in: Promo plan → Section 2, Post 4
  
- [ ] **Instagram Carousel (5 slides)**
  - Content ready in: Promo plan → Section 2, Post 2
  - Take screenshots of 5 templates from the live tool, add as slides

### Friday
- [ ] **Post Instagram Reel (Template-Library-Error video)**
  - Schedule via Metricool

- [ ] **Post remaining 2 Facebook groups**
  - Emprendedores Costa Rica, Real Estate Costa Rica (English)

---

## Phase 5: Direct Outreach to Prospects (Week 1-2)

- [ ] **Wave 1: DM Tier A agencies from original prospect list (7 agencies)**
  - File: `trochai-business/PROSPECT-LIST.md` → Tier 1
  - Send on WhatsApp (numbers are in the file)
  - Message:
    ```
    Hola [nombre], le escribo de Trochai. Creamos una herramienta gratuita 
    de plantillas de WhatsApp para agentes inmobiliarios. Tiene 23 plantillas 
    editables para primer contacto, seguimiento, visitas, negociación y más.
    
    Es 100% gratis, sin registro: trochai.com/es/herramientas/plantillas-whatsapp
    
    Ojalá le sirva a su equipo.
    ```

- [ ] **Wave 2: DM Tier A agencies from expanded list (20 agencies)**
  - File: `trochai-business/PROSPECT-LIST-EXPANDED.md` → Tier A
  - Same message template

- [ ] **Wave 3: Tier B agencies (both lists)**
  - 28 remaining agencies
  - Send after Wave 1-2 responses come in (adjust message if needed)

---

## Phase 6: MCP Server Deploy (Week 2)

- [ ] **Create GitHub repo for trochai-mcp**
  ```bash
  cd trochai-mcp
  gh repo create trochai-mcp --private --source=. --push
  ```

- [ ] **Add Supabase credentials**
  - Copy your Supabase anon key to `.env`
  - Test locally: `npm run dev` (then test with Claude Desktop)

- [ ] **Deploy to Hostinger VPS**
  ```bash
  # On Hostinger
  git clone <repo-url>
  cd trochai-mcp && npm install && npm run build
  cp .env.example .env  # Fill in credentials
  pm2 start dist/index.js --name trochai-mcp
  ```

- [ ] **Register on MCP directories**
  - Smithery (smithery.ai) — submit via GitHub
  - mcp.so — community directory

---

## Phase 7: Content Repurposing Engine (Week 2+)

- [ ] **Record first pillar content**
  - Topic suggestion: "Why 97% of real estate leads are wasted"
  - Format: 30-min voice memo or video on your phone
  
- [ ] **Run the repurposing pipeline**
  ```bash
  # In the Trochai monorepo root, with Claude Code:
  /repurpose-all
  # Paste your transcript when prompted
  ```
  This generates: 5 tweets, 2 LinkedIn posts, 1 blog article, 3 video scripts, 1 newsletter

- [ ] **Schedule repurposed content in Metricool**
  - Follow the content calendar in: `trochai-business/CONTENT-REPURPOSING-ENGINE.md`

---

## Ongoing Weekly Ritual

| Day | Action | Time |
|-----|--------|------|
| Mon | Record pillar content (voice memo or video) | 30 min |
| Mon | Run `/repurpose-all`, review output | 15 min |
| Tue | Edit generated content, render any video scripts | 30 min |
| Tue | Send 10-15 LinkedIn connection requests | 15 min |
| Wed-Fri | Publish per calendar (Metricool auto-posts) | 5 min/day |
| Thu | DM 5 prospect agencies with value (tool link, tip, etc.) | 20 min |
| Sat | Review analytics: what worked, what didn't | 15 min |

**Total weekly commitment: ~3 hours**

---

## Quick Reference: Where to Find Everything

| What | File |
|------|------|
| Social media post captions (5 posts) | `trochai-business/TEMPLATE-LIBRARY-PROMO-PLAN.md` → Section 2 |
| Video scripts (3 scripts) | `trochai-business/TEMPLATE-LIBRARY-PROMO-PLAN.md` → Section 3 |
| FB group template post | `trochai-business/TEMPLATE-LIBRARY-PROMO-PLAN.md` → Section 4 |
| SEO keywords to target | `trochai-business/TEMPLATE-LIBRARY-PROMO-PLAN.md` → Section 5 |
| LinkedIn networking targets (76) | `trochai-business/linkedin-networking-targets.md` |
| Original prospect list (20 agencies) | `trochai-business/PROSPECT-LIST.md` |
| Expanded prospect list (48 agencies) | `trochai-business/PROSPECT-LIST-EXPANDED.md` |
| Distribution strategies (all 7) | `trochai-business/DISTRIBUTION-STRATEGIES.md` |
| Content repurposing workflow | `trochai-business/CONTENT-REPURPOSING-ENGINE.md` |
| Repurposing commands | `/.claude/commands/repurpose-*.md` |
| Video compositions (Remotion) | `trochai-videos/src/compositions/TemplateLibrary*.tsx` |
| Voiceover scripts (#11, #12) | `trochai-videos/VOICEOVER-SCRIPTS.md` |
| Render command | `cd trochai-videos && npx tsx src/scripts/render-video.ts --id <ID>` |
| Publish command | `cd trochai-videos && npx tsx src/scripts/publish-video.ts` |
