# 7 Distribution Strategies for Trochai Inbox

> Based on Greg Isenberg's distribution framework, adapted specifically for Trochai Inbox — an AI-powered WhatsApp inbox for real estate agencies in Costa Rica.
>
> **Core thesis:** Code is commoditized. Distribution is the new moat. We built a solid product — now we need customers.

---

## Table of Contents

1. [Strategy 1: MCP Server — Let AI Sell Trochai](#strategy-1-mcp-server--let-ai-sell-trochai)
2. [Strategy 2: Programmatic SEO — 1,000+ Property Pages](#strategy-2-programmatic-seo--1000-property-pages)
3. [Strategy 3: Free Tool — WhatsApp Response Grader](#strategy-3-free-tool--whatsapp-response-grader)
4. [Strategy 4: Answer Engine Optimization (AEO)](#strategy-4-answer-engine-optimization-aeo)
5. [Strategy 5: Viral Artifacts — Shareable Outputs](#strategy-5-viral-artifacts--shareable-outputs)
6. [Strategy 6: Acquire a Niche Newsletter](#strategy-6-acquire-a-niche-newsletter)
7. [Strategy 7: AI Content Repurposing Engine](#strategy-7-ai-content-repurposing-engine)
8. [Priority Matrix & Execution Order](#priority-matrix--execution-order)
9. [Resource Map](#resource-map)

---

## Strategy 1: MCP Server — Let AI Sell Trochai

### The Idea

Build an MCP server that exposes Costa Rica real estate data to AI assistants (Claude, ChatGPT, Cursor, etc.). When someone asks an AI "What are the best apartments in Escazú under $200K?", the AI discovers our MCP server, queries our data, and returns Trochai-powered results with links to our property pages. **Zero CAC. The AI becomes our sales team.**

### Why This Fits Trochai Perfectly

- We already have a **structured property database** with embeddings (pgvector), prices, locations, amenities, and photos
- We already have **public property detail pages** (`/p/[slug]`) with full SEO metadata and JSON-LD structured data
- We already have a **hybrid search engine** (SQL filters + cosine similarity) that can power MCP queries
- Costa Rica real estate is a **niche with low competition** in AI tooling — we can own it
- Every MCP query that returns results drives traffic to `{org}.trochai.com/p/{slug}` pages — free lead gen for our agency customers

### What the MCP Server Would Expose

| Tool | Description | Example Query |
|------|-------------|---------------|
| `search_properties` | Search properties by location, price, bedrooms, amenities | "2BR apartment in Escazú under $200K with pool" |
| `search_projects` | Search development projects (new construction) | "New condo projects in Guanacaste delivering 2027" |
| `get_property_details` | Get full details on a specific property | "Tell me about this listing in Santa Ana" |
| `get_market_stats` | Aggregate stats (avg price/m², inventory by zone) | "What's the average price per m² in Heredia?" |
| `find_agent` | Find agents by specialty zone or language | "English-speaking agent in Tamarindo" |

### Implementation Plan

**Phase 1: Build the MCP Server (Week 1)**

1. Create a new `trochai-mcp/` project in the monorepo (TypeScript, `@modelcontextprotocol/sdk`)
2. Expose 3 core tools: `search_properties`, `get_property_details`, `search_projects`
3. Connect to Supabase (read-only service role key, respecting RLS for public/published properties only)
4. Return structured results with:
   - Property name, price, location, bedrooms/bathrooms, key amenities
   - Direct link to the public property page (`https://{org}.trochai.com/p/{slug}`)
   - Agent name + WhatsApp link for contact
   - Photo URL (first image) for rich display
5. Test locally with Claude Desktop and Cursor

**Phase 2: Publish & Register (Week 1-2)**

1. Deploy the MCP server to our **Hostinger VPS** (Node.js, persistent process via PM2 or systemd)
2. Alternatively: deploy as a serverless function on Vercel (if stateless queries suffice)
3. Register on MCP directories:
   - **Smithery** (smithery.ai) — largest MCP registry
   - **mcp.so** — community MCP directory
   - **Open Tools** — if available
   - **GitHub** — public repo with clear README + install instructions
4. Submit to **Claude's MCP marketplace** when available
5. Add to **Cursor's MCP directory** and **Windsurf's**

**Phase 3: Data Enrichment (Week 2-3)**

1. Add `get_market_stats` tool — aggregate pricing data by zone, property type
2. Add `find_agent` tool — match user to an agent by zone/language
3. Scrape public listing data from Encuentra24/Zillow-CR to enrich our database (Firecrawl)
4. Add comparative data: "How does this compare to similar listings?"
5. Consider caching layer for frequently queried zones

**Phase 4: Feedback Loop (Ongoing)**

1. Log every MCP query (what users ask, what results come back)
2. Track click-throughs from MCP → property page → WhatsApp contact
3. Use query patterns to identify what data users want that we don't have yet
4. Feed popular search patterns back to agency customers: "People are asking for X in your zone"

### Cost

- **Development:** ~2-3 days of vibe coding with Claude Code
- **Hosting:** Hostinger VPS (already paid for) or Vercel free tier
- **Supabase:** Read-only queries, minimal additional load
- **Total incremental cost:** ~$0/month

### Expected Impact

- **Zero CAC channel** — every AI query is a free impression
- **Backlink generator** — AI citations link to our property pages, boosting domain authority
- **Competitive moat** — first Costa Rica real estate MCP server = we own the niche
- **Agency sales pitch:** "Your properties show up when people ask AI about Costa Rica real estate" — this alone could close deals

### Key Risks

- MCP adoption is still early (but growing fast — this is the 2010 mobile moment)
- Need enough property data to be useful (start with partner agencies who opt in to public listings)
- Must handle empty results gracefully (redirect to general search, not a dead end)

---

## Strategy 2: Programmatic SEO — 1,000+ Property Pages

### The Idea

Create thousands of SEO-optimized pages targeting long-tail real estate search queries in Costa Rica. Not just property detail pages (we have those), but **landing pages for every combination of property type + location + price range** that someone might Google.

### Why This Fits Trochai Perfectly

- We already have **property detail pages** with JSON-LD structured data and proper meta tags
- The landing site (`trochai.com`) is a **separate Vercel project** with its own domain authority to build
- Real estate search queries are **high-intent** — "apartments for sale in Escazú" = someone ready to buy
- Costa Rica real estate SEO in Spanish is **underserved** — most agencies have terrible websites
- Each page funnels to Trochai-powered agency subdomains, creating value for our customers

### Page Types to Generate

#### Type A: Location + Property Type Pages (Primary)

**Pattern:** `trochai.com/es/propiedades/{tipo}-en-{ubicacion}`

| Example URL | Target Query |
|-------------|-------------|
| `/propiedades/apartamentos-en-escazu` | "apartamentos en venta Escazú" |
| `/propiedades/casas-en-santa-ana` | "casas en venta Santa Ana Costa Rica" |
| `/propiedades/condominios-en-guanacaste` | "condominios Guanacaste" |
| `/propiedades/terrenos-en-heredia` | "terrenos baratos Heredia" |
| `/propiedades/locales-comerciales-en-san-jose` | "locales comerciales San José" |

**Content per page:**
- H1: "Apartamentos en Venta en Escazú, Costa Rica"
- Intro paragraph: AI-generated, specific to the zone (walkability, schools, nearby amenities, lifestyle)
- **Live property feed** from Trochai database (API call to aggregate properties across agencies)
- Average price/m² for the zone
- Neighborhood guide (schools, hospitals, transport, lifestyle)
- FAQ section (structured for AEO — see Strategy 4)
- CTA: "Talk to an agent on WhatsApp" → routes to appropriate agency

**Scale math:**
- 7 property types × 80 cantons × 2 locales = **1,120 pages** as starting base
- Add district-level pages for high-demand zones: +500 pages
- Add price range variants ("under $150K", "$150K-$300K", "$300K+"): ×3 = **~4,800 pages**

#### Type B: "Best X for Y" Comparison Pages

**Pattern:** `trochai.com/es/guias/mejor-{tipo}-para-{perfil}`

| Example URL | Target Query |
|-------------|-------------|
| `/guias/mejor-zona-para-familias-costa-rica` | "mejor zona para vivir con familia Costa Rica" |
| `/guias/mejor-zona-para-extranjeros-costa-rica` | "best area for expats Costa Rica" |
| `/guias/mejores-condominios-escazu` | "mejores condominios Escazú" |
| `/guias/invertir-bienes-raices-costa-rica` | "invertir en bienes raíces Costa Rica" |

#### Type C: Project/Development Pages

**Pattern:** `trochai.com/es/proyectos/{proyecto-slug}`

- Aggregate project pages showing all units, amenities, construction status
- Schema.org markup for `RealEstateAgent` + `Residence`
- Each links to the agency's Trochai-powered project detail pages

### Implementation Plan

**Phase 1: Template + First 100 Pages (Week 1)**

1. Create a dynamic route in `trochai-landing`: `/propiedades/[slug]/page.tsx`
2. Build the page template:
   - Hero with zone photo (Unsplash or AI-generated) + H1
   - Property grid (fetched from Trochai API: aggregate public listings across agencies)
   - Zone stats (avg price/m², inventory count, price trends)
   - AI-generated neighborhood description (2-3 paragraphs, unique per page)
   - FAQ section with 5 common questions per zone (schema markup)
   - CTA: "Habla con un agente" → WhatsApp or signup
3. Create a data pipeline:
   - Use Firecrawl or manual research to compile zone data for top 20 locations
   - Generate AI content per page using Claude (not variable swaps — actual unique paragraphs)
   - Store in MDX files or a JSON data layer
4. Publish first 100 pages (top 20 locations × 5 property types)
5. Submit sitemap to Google Search Console

**Phase 2: Scale to 1,000+ Pages (Week 2-3)**

1. Expand to all 80 cantons
2. Add English locale variants for all pages
3. Generate district-level pages for high-demand zones (Escazú, Santa Ana, Heredia, Curridabat)
4. Add price range variants
5. Internal linking strategy: every property page links to its zone page, every zone page links to adjacent zones
6. Build programmatic sitemap generator

**Phase 3: Content Quality + Authority (Week 3-4)**

1. Add real property data from partner agencies (with permission)
2. Enrich zone pages with Google Maps embed, school ratings, walkability scores
3. A/B test CTAs (WhatsApp direct vs. lead form vs. free tool)
4. Monitor indexation in Google Search Console — fix any crawl issues
5. Build backlinks through PR, guest posts on CR real estate blogs

### Cost

- **Development:** ~3-4 days with Claude Code
- **AI content generation:** ~$5-10 for 1,000 pages (Claude API)
- **Firecrawl scraping:** ~$20 one-time for zone data
- **Hosting:** Already on Vercel (trochai-landing project)
- **Total:** ~$30 one-time + dev time

### Expected Impact (Conservative at 6 months)

| Metric | Estimate |
|--------|----------|
| Pages indexed | 500-1,000 |
| Avg visits/page/month | 10-30 (long-tail, low competition) |
| Monthly organic visitors | 5,000-30,000 |
| Conversion rate | 1-2% (high intent real estate queries) |
| Monthly leads | 50-600 |

Even the low end (50 leads/month) is transformative for early-stage distribution.

### Key Risks

- Google may slow-index AI-generated content — mitigate with unique data, structured markup, and gradual publishing
- Need real property data to provide value (not just empty category pages)
- Content quality must be high — Google's helpful content update penalizes thin pSEO

---

## Strategy 3: Free Tool — WhatsApp Response Grader

### The Idea

Build standalone free tools that give real estate agencies instant value, capture their info, and funnel them to Trochai. The tool IS the marketing.

### Tool Ideas (Prioritized)

#### Tool 1: WhatsApp Response Time Grader (Primary — Build This First)

**URL:** `trochai.com/herramientas/evaluador-whatsapp` (also `/tools/whatsapp-grader` in English)

**How it works:**
1. Agency enters their WhatsApp Business number
2. We send a test message simulating a lead inquiry ("Hola, busco un apartamento en Escazú de 2 habitaciones")
3. We measure how long it takes for someone to respond (or if they respond at all)
4. While waiting, we show real-time stats: "The average agency takes 4.2 hours... 78% of buyers choose the first responder..."
5. After response (or after 24h timeout), we generate a **scorecard**:
   - Response time: X minutes/hours (grade A-F)
   - Compared to industry average
   - Compared to top performers
   - Estimated leads lost per month due to slow response
   - Estimated revenue lost ($)
6. The scorecard is **beautiful, branded, and shareable** (ties into Strategy 5)
7. CTA: "Want to respond in under 2 minutes, 24/7? Try Trochai — free trial"

**Why this is genius for our ICP:**
- Directly demonstrates the core pain point Trochai solves
- Makes the problem tangible and personal ("YOU are losing $X/month")
- The agency has to engage with a WhatsApp flow — showing them what their leads experience
- Natural viral sharing: agencies will compare scores, challenge competitors
- Every graded agency = a warm lead with proven pain

#### Tool 2: Lead Response Calculator

**URL:** `trochai.com/herramientas/calculadora-leads`

**How it works:**
1. Agency inputs: monthly leads, average response time, average deal value, close rate
2. Calculator shows:
   - Leads lost due to slow response (based on industry data)
   - Revenue left on the table per month/year
   - "If you responded in under 5 minutes, you'd close X more deals worth $Y"
3. Beautiful PDF report they can download (email capture)
4. CTA: "Trochai gets your response time to under 2 minutes"

#### Tool 3: WhatsApp Message Template Library

**URL:** `trochai.com/herramientas/plantillas-whatsapp`

**How it works:**
1. Free library of 20+ WhatsApp message templates for real estate
   - First contact response
   - Property follow-up
   - Visit confirmation
   - Price negotiation
   - Post-visit follow-up
   - Referral request
2. Click to copy, organized by funnel stage
3. Email capture to download all as PDF
4. CTA: "Trochai's AI writes these for you — automatically"

#### Tool 4: Costa Rica Real Estate Market Report

**URL:** `trochai.com/herramientas/reporte-mercado`

**How it works:**
1. Select a zone (Escazú, Santa Ana, Heredia, etc.)
2. See aggregate market data: avg price/m², inventory, demand trends, price changes
3. Beautiful report with charts and comparisons
4. Email capture to get monthly updates
5. CTA: "Get this data inside your inbox with Trochai Analytics"

### Implementation Plan (Tool 1: WhatsApp Grader)

**Phase 1: Build the Landing Page (2-3 days)**

1. Create route in `trochai-landing`: `/herramientas/evaluador-whatsapp/page.tsx`
2. Build the UI:
   - Phone number input with country selector (CR default)
   - "Grade My Response Time" button
   - Real-time waiting screen with stats and countdown
   - Animated scorecard reveal
   - Share buttons (WhatsApp, Instagram Stories, LinkedIn)
3. Store email/phone for lead nurturing

**Phase 2: Build the Backend (2-3 days)**

1. API endpoint that sends a WhatsApp message to the entered number via Meta Cloud API (from a Trochai test number)
2. Webhook listener that detects when/if the agency responds
3. Timer logic: measure response latency
4. Scoring algorithm: A (< 5 min), B (5-15 min), C (15-60 min), D (1-4 hr), F (> 4 hr or no response)
5. Revenue loss calculator based on their response grade

**Phase 3: Launch & Promote (Week 2)**

1. Post the tool on social media (use as content — see Strategy 7)
2. DM agencies from our prospect list: "We graded your WhatsApp response time — want to see your score?"
3. Create a Reel/TikTok showing live grading of agencies (with permission or anonymized)
4. Submit to ProductHunt, IndieHackers, Hacker News (if appropriate)

### Cost

- **Development:** ~5 days
- **WhatsApp API:** Cost per test message (~$0.05/message, minimal)
- **Hosting:** Already on Vercel
- **Total:** ~$5-10/month at scale

### Expected Impact

- Direct demonstration of the pain point Trochai solves
- Every graded agency = a pre-qualified lead who now understands the problem
- Viral sharing potential: agencies comparing scores, sharing on social
- Content fuel: "We graded 100 Costa Rican agencies — the results are shocking" (blog post, video, social)

---

## Strategy 4: Answer Engine Optimization (AEO)

### The Idea

Optimize our content so that when people ask AI assistants (ChatGPT, Perplexity, Claude, Gemini) questions about Costa Rica real estate, **Trochai gets cited as the source**. This is SEO for AI — and it's where SEO was in 2010.

### Why This Fits Trochai

- We're targeting a **niche market** (CR real estate) where AI has few authoritative sources
- We already have a **blog infrastructure** on `trochai.com` (MDX in `content/blog/`)
- We already have **structured data** (JSON-LD on property pages)
- Costa Rica real estate questions are asked by **international buyers in English** — huge AEO opportunity
- Being the AI-cited source builds trust with agencies: "Your platform is what ChatGPT recommends"

### Top 20 Questions to Own

These are the questions our ICP's customers (buyers/renters) and our ICP themselves (agencies) ask:

#### Buyer Questions (drives property page traffic → agency value)

1. "What are the best areas to buy property in Costa Rica?"
2. "How much does an apartment cost in Escazú, Costa Rica?"
3. "Can foreigners buy property in Costa Rica?"
4. "What documents do I need to buy a house in Costa Rica?"
5. "Is it safe to invest in Costa Rica real estate?"
6. "Best neighborhoods for expats in Costa Rica"
7. "Costa Rica real estate market trends 2026"
8. "Average price per square meter in San José, Costa Rica"
9. "How to find a real estate agent in Costa Rica"
10. "Beachfront property for sale in Costa Rica — what to know"

#### Agency Questions (drives Trochai signups directly)

11. "Best CRM for real estate agencies in Costa Rica"
12. "How to automate WhatsApp for real estate"
13. "WhatsApp Business API for real estate agents"
14. "How to respond to real estate leads faster"
15. "AI chatbot for real estate WhatsApp"
16. "How to manage multiple WhatsApp conversations for a team"
17. "Real estate lead qualification automation"
18. "How to not lose leads on WhatsApp"
19. "Best tools for real estate agencies in Latin America"
20. "How to use AI in real estate sales"

### Content Format for AEO

Each question becomes a **structured, definitive answer page** on `trochai.com/blog/`:

```markdown
# Can Foreigners Buy Property in Costa Rica?

**Short answer:** Yes. Foreigners have the same property rights as Costa Rican citizens,
with one exception: maritime zone (concession) land within 200 meters of the coast
requires a Costa Rican corporation or residency.

## Full Guide

### 1. Legal Framework
[2-3 paragraphs with specific laws cited]

### 2. The Maritime Zone Exception
[Clear explanation with map/diagram]

### 3. Required Documents
| Document | Where to Get It | Cost |
|----------|----------------|------|
| ... | ... | ... |

### 4. Step-by-Step Purchase Process
1. Find a property (through a licensed agent or platform like Trochai)
2. Due diligence (title search at Registro Nacional)
3. ...

### 5. Common Mistakes to Avoid
- Buying maritime zone land without understanding restrictions
- Not using an escrow service
- ...

## FAQ
<details>
<summary>Do I need a lawyer to buy property in Costa Rica?</summary>
Yes. A notary public (notario) is required...
</details>
[5+ FAQs with schema markup]

## Sources
- Registro Nacional de Costa Rica
- CCCBR (Cámara Costarricense de Corredores de Bienes Raíces)
- ...
```

### Implementation Plan

**Phase 1: Write the Top 10 Articles (Week 1-2)**

1. Use Claude to draft the 10 buyer-facing questions first (highest search volume)
2. Each article: 1,500-2,500 words, structured with H2/H3, tables, FAQ schema
3. Enrich with real data:
   - Scrape current pricing data from Encuentra24 (Firecrawl)
   - Reference specific laws and government sources
   - Include our own property data where relevant
4. Human review for accuracy (real estate law, Costa Rica specifics)
5. Publish on `trochai.com/blog/` in both Spanish and English

**Phase 2: Schema Markup & Technical AEO (Week 2)**

1. Add `FAQPage` schema to every article (already supported by MDX frontmatter)
2. Add `HowTo` schema for step-by-step guides
3. Add `Article` schema with author, datePublished, dateModified
4. Ensure every article has:
   - Clear H1 that matches the question exactly
   - First paragraph that directly answers the question (AI pulls this)
   - Structured tables and lists (AI parses these easily)
   - Authoritative sources cited (AI trusts sourced content)
5. Submit updated sitemap to Google Search Console

**Phase 3: Agency-Focused Content (Week 3)**

1. Write the 10 agency-facing articles
2. These directly pitch Trochai as the solution where relevant
3. Include comparison tables: "Trochai vs. Respond.io vs. manual WhatsApp"
4. Target keywords like "WhatsApp CRM inmobiliaria" and "chatbot WhatsApp bienes raíces"

**Phase 4: Monitor & Iterate (Ongoing)**

1. Test each article in ChatGPT, Perplexity, Claude — check if cited
2. Use **Otterly.ai** or **Profound** to track AI citations
3. Manual testing weekly: ask the 20 questions, see who gets cited
4. Update content based on what gets cited vs. not
5. Build authority: get backlinks from CR real estate blogs, CCCBR, expat forums

### Cost

- **AI content generation:** ~$5-10 (Claude API for drafts)
- **Firecrawl for data:** ~$10
- **Otterly.ai or Profound:** $30-50/month for citation monitoring
- **Human review:** Time investment (you or a CR real estate consultant)
- **Total:** ~$50/month + time

### Expected Impact

- AI referral traffic could grow from 0% to 10-20% within 3-6 months
- Every citation = free advertising to high-intent users
- Agency sales pitch: "When ChatGPT recommends Costa Rica real estate tools, it recommends Trochai"
- Compounding: once cited, AI tends to keep citing the same authoritative sources

---

## Strategy 5: Viral Artifacts — Shareable Outputs

### The Idea

Make specific outputs of Trochai beautiful, branded, and shareable — so our users do our marketing for us by bragging about their results.

### Viral Artifacts for Trochai

#### Artifact 1: Monthly Agency Performance Report (Primary)

**What:** A beautiful, Instagram-Story-sized report card that agencies receive monthly:

```
┌─────────────────────────────────────┐
│          🏠 TU MES EN TROCHAI       │
│            Enero 2026               │
│                                     │
│  247 conversaciones atendidas       │
│  ⚡ 8 seg tiempo promedio respuesta │
│  🤖 189 manejadas por el bot        │
│  👤 58 escaladas a agentes          │
│  📊 92% tasa de satisfacción        │
│                                     │
│  🏆 Top 3 propiedades buscadas:     │
│  1. Apt 2BR Escazú ($185K)          │
│  2. Casa Santa Ana ($320K)          │
│  3. Condo Sabana ($145K)            │
│                                     │
│  "Tu equipo respondió 47x más       │
│   rápido que el promedio"           │
│                                     │
│         [Casa Escazú logo]          │
│        powered by trochai.com       │
└─────────────────────────────────────┘
```

**Why agencies share it:**
- Bragging rights: "We respond in 8 seconds" (implies competitors don't)
- Team pride: shows agents how well the team performed
- Professional image: makes the agency look tech-forward
- Competitive flex in industry WhatsApp groups and Facebook groups

**Implementation:**
1. Auto-generate monthly from analytics data (we already track all of this)
2. Render as a beautiful image (use Remotion or a server-side canvas/SVG renderer)
3. Include a "Share on Instagram Stories" button that creates a properly-sized image
4. Agency logo prominent, Trochai branding subtle ("powered by trochai")
5. Send via email + in-app notification on the 1st of each month

#### Artifact 2: "First Response" Badge

**What:** When an agency achieves a milestone (e.g., first 100 conversations handled, first month under 30-second avg response time), they get a shareable badge.

```
┌────────────────────────────┐
│  ⚡ FIRST RESPONDER         │
│                            │
│  [Agency Logo]             │
│                            │
│  Tiempo promedio: 12 seg   │
│  Enero 2026                │
│                            │
│  Verificado por Trochai    │
└────────────────────────────┘
```

**Milestones:**
- "First Responder" — avg response time under 30 seconds for a month
- "Always On" — bot handled 500+ after-hours conversations
- "Lead Machine" — qualified 100+ leads in a month
- "1,000 Club" — 1,000 total conversations handled
- "24/7" — first month with zero missed leads

#### Artifact 3: Property Performance Cards

**What:** Per-property shareable card showing how a listing performed:

```
┌────────────────────────────┐
│  [Property Photo]          │
│                            │
│  Apartamento en Escazú     │
│  $185,000                  │
│                            │
│  📊 347 vistas este mes    │
│  💬 43 consultas WhatsApp  │
│  📅 12 visitas agendadas   │
│                            │
│  [Agency Logo] via Trochai │
└────────────────────────────┘
```

**Why agencies share it:**
- Shows sellers their property is getting attention (retains listings)
- Attracts new sellers: "Look how much exposure your property gets with us"
- Agents share on their personal social media to attract more clients

### Implementation Plan

**Phase 1: Monthly Report Card (Week 1-2)**

1. Build a report generation endpoint: `GET /api/reports/monthly?org_id=X&month=2026-01`
2. Query analytics tables: conversations, response times, bot vs. human, top properties
3. Design the report template in React (reusable component)
4. Render to PNG using `@vercel/og` (edge image generation) or Remotion
5. Add "Share" button in the dashboard that generates + downloads the image
6. Set up monthly email with the report attached (using existing email infrastructure)

**Phase 2: Milestone Badges (Week 2-3)**

1. Define milestone thresholds in a config
2. Check milestones after each analytics aggregation
3. Trigger in-app celebration + notification when milestone is achieved
4. Generate badge image and present "Share to Instagram" option
5. Store earned badges on org profile (gamification element)

**Phase 3: Property Performance Cards (Week 3-4)**

1. Add "Share Performance" button on each property's analytics view
2. Generate a card image with the property photo + stats
3. Include UTM tracking on the shared link so we can measure virality
4. Optional: auto-generate weekly for top-performing properties

### Cost

- **Development:** ~5-7 days across all three artifacts
- **Image generation:** Vercel OG or Remotion (already have Remotion infrastructure)
- **Email:** Minimal (already using transactional email for notifications)
- **Total:** Dev time only, $0 incremental

### Expected Impact

- Every share = free impression to the agency's network (other agencies, agents, property owners)
- Monthly reports create a **habit loop** — agencies look forward to their score
- Competitive dynamics: agencies compare scores, push each other to use the tool more
- Property cards give agents ammunition for seller presentations

---

## Strategy 6: Acquire a Niche Newsletter

### The Idea

Instead of building an audience from zero, buy a small newsletter targeting Costa Rican real estate professionals or Central American business owners. Instant access to a warm audience.

### Newsletter Targets for Trochai

#### Tier 1: Perfect Fit (Costa Rica Real Estate)

| Newsletter Type | Where to Find | Est. Subscribers | Est. Price |
|----------------|---------------|-----------------|------------|
| CR real estate market reports | Substack search: "bienes raíces Costa Rica" | 1,000-5,000 | $2,000-$10,000 |
| Expat living in Costa Rica | Substack, Mailchimp lists from expat blogs | 5,000-20,000 | $5,000-$20,000 |
| CR investment/business | LinkedIn newsletters, local business blogs | 2,000-10,000 | $3,000-$15,000 |

#### Tier 2: Adjacent Niche

| Newsletter Type | Where to Find | Est. Subscribers | Est. Price |
|----------------|---------------|-----------------|------------|
| Latin America real estate | Substack, niche RE blogs | 5,000-15,000 | $5,000-$15,000 |
| Latin America SaaS/tech | IndieHackers, Twitter/X | 3,000-10,000 | $3,000-$12,000 |
| Central America business | LinkedIn, local publications | 2,000-8,000 | $2,000-$10,000 |

#### Tier 3: Creative Adjacencies

| Newsletter Type | Why It Works |
|----------------|-------------|
| Real estate technology (global) | Covers proptech, can intro Trochai to global RE agents who work in CR |
| WhatsApp marketing tips | Audience already cares about WhatsApp as a business channel |
| Costa Rica digital nomad | Nomads rent and buy — they search for properties and recommend agents |

### How to Use an Acquired Newsletter

**Week 1:** Maintain existing content format, add subtle Trochai mention in footer
**Week 2-3:** Introduce a "tool of the week" section featuring Trochai's free tools
**Week 4:** Dedicated deep-dive: "How AI is changing real estate in Costa Rica" (features Trochai)
**Ongoing:** Mix value content (market reports, tips, industry news) with Trochai product updates

**Never make it feel like a sales pitch newsletter.** The value must come first. Trochai should feel like a natural extension of the content.

### Implementation Plan

**Phase 1: Research & Identify (This Week)**

1. Search Substack for: "Costa Rica", "bienes raíces", "real estate Costa Rica", "propiedades"
2. Search Twitter/X for: Costa Rica real estate newsletters, expat newsletters
3. Check **duuce.com** for newsletter listings in the real estate/LatAm category
4. Check **Newsletter Investor** marketplace
5. Ask in real estate WhatsApp/Facebook groups: "Does anyone know a good CR real estate newsletter?"
6. Create a shortlist of 5-10 candidates

**Phase 2: Outreach (Week 1-2)**

1. DM newsletter owners: "Hey, I've been a subscriber for a while. Love what you're doing. Have you ever thought about selling? I'm building a real estate platform in Costa Rica and your audience is exactly who I'm trying to reach."
2. For stale newsletters (haven't sent in 3+ months): lower price, higher urgency
3. For active newsletters: offer to keep them on as a contributor (reduces risk of subscriber churn)

**Phase 3: Acquisition & Integration (Week 2-4)**

1. Due diligence: open rates (>30% = healthy), subscriber growth trend, bounce rate
2. Negotiate: typically 1-3x annual revenue, or $1-3 per subscriber for non-monetized lists
3. Transfer: Substack allows ownership transfer, or export list to our email platform
4. Keep existing branding initially, gradually introduce Trochai content

### Cost

- **Newsletter acquisition:** $2,000-$15,000 (one-time)
- **Ongoing:** Email platform costs (~$30-50/month for 5,000-10,000 subscribers)
- **Content creation:** Mostly AI-assisted, 2-3 hours/week to curate and review

### Expected Impact

- **Instant audience** — skip 6-12 months of audience building
- **Direct channel** — email lands in inbox, no algorithm suppression
- **Trust transfer** — subscribers already trust the newsletter, Trochai benefits from that
- **Lead gen:** Even 1% conversion from a 5,000-subscriber list = 50 leads

### Key Consideration

This strategy has the highest upfront cost but also the most immediate payoff. Consider it once the product has its first 5-10 paying customers and the messaging is validated. Buying a newsletter too early means you might not convert the audience because the pitch isn't refined yet.

---

## Strategy 7: AI Content Repurposing Engine

### The Idea

Create one pillar piece of content per week, then use AI to repurpose it into 15-20+ pieces across every platform. We already have the Remotion video infrastructure — now we systematize the entire content pipeline.

### Why This Fits Trochai Perfectly

- We already have **Remotion** with 10 rendered videos, ElevenLabs TTS, and Metricool publishing
- We already have a **content marketing strategy** with scripts, content pillars, and posting cadence
- We already have a **blog infrastructure** on `trochai.com`
- The founder (Leeren) can record a 15-30 minute voice memo or video each week as the pillar
- Claude Code + our existing skills can automate most of the repurposing

### The Weekly Content Machine

```
                    ┌──────────────────┐
                    │  PILLAR CONTENT  │
                    │  (1 per week)    │
                    │                  │
                    │  30-min video,   │
                    │  podcast, or     │
                    │  voice memo      │
                    └────────┬─────────┘
                             │
                    ┌────────▼─────────┐
                    │   TRANSCRIBE     │
                    │   (Whisper API)  │
                    └────────┬─────────┘
                             │
              ┌──────────────┼──────────────┐
              │              │              │
     ┌────────▼──────┐ ┌────▼─────┐ ┌──────▼───────┐
     │  SHORT-FORM   │ │  TEXT     │ │   VISUAL     │
     │  VIDEO        │ │  CONTENT  │ │   CONTENT    │
     └────────┬──────┘ └────┬─────┘ └──────┬───────┘
              │              │              │
        ┌─────┤        ┌─────┤        ┌─────┤
        │     │        │     │        │     │
        ▼     ▼        ▼     ▼        ▼     ▼
     3 Reels  2 TikTok  5 Tweets  2 LinkedIn  3 Quote   1 Blog
     (Remotion) (Remotion)  (X)     Posts      Graphics   Post
                                              (AI image)
                                                        1 Newsletter
                                                        Edition
```

**Output per week from ONE pillar piece:**

| Platform | Content Type | Quantity | Tool |
|----------|-------------|----------|------|
| Instagram Reels | Short-form video (9:16) | 3 | Remotion + ElevenLabs |
| TikTok | Short-form video (9:16) | 2 | Same renders, different captions |
| YouTube Shorts | Short-form video (9:16) | 2 | Same renders |
| Twitter/X | Tweet threads + single tweets | 5 | Claude API |
| LinkedIn | Long-form posts | 2 | Claude API |
| Blog | Article (1,500+ words) | 1 | Claude API + human edit |
| Newsletter | Edition with insights | 1 | Claude API (use trochai-blog-poster skill) |
| Quote graphics | Branded image quotes | 3 | Claude API + Remotion or Canva API |
| Instagram Stories | Story slides | 5 | Remotion or template |
| WhatsApp Status | Repurposed stories | 3 | Same as IG Stories |

**Total: ~27 pieces of content per week from one recording session.**

### Pillar Content Ideas (First 12 Weeks)

| Week | Pillar Topic | Angle |
|------|-------------|-------|
| 1 | "Why 97% of real estate leads are wasted" | Pain point → data → solution |
| 2 | "I built an AI that sells houses while you sleep" | Founder story → product demo |
| 3 | "The 5-minute rule that Costa Rican agencies ignore" | Urgency → data → framework |
| 4 | "WhatsApp is broken for real estate teams" | Problem exploration → solution |
| 5 | "We graded 50 agencies' response times" | Original research → insights |
| 6 | "How expats actually search for property in CR" | Buyer psychology → what agencies miss |
| 7 | "The $10K mistake agencies make every month" | Revenue impact → automation |
| 8 | "Building Trochai: week in the life" | Behind-the-scenes → authenticity |
| 9 | "AI in real estate: what actually works" | Industry analysis → Trochai positioning |
| 10 | "From lead to sale: the perfect WhatsApp flow" | Framework → templates → automation |
| 11 | "Why your WhatsApp Business is losing you money" | Comparison → upgrade path |
| 12 | "Our first 10 customers: what we learned" | Social proof → lessons → growth |

### Implementation Plan

**Phase 1: Set Up the Pipeline (Week 1)**

1. **Recording setup:** Phone + tripod + good mic. Record in Spanish (primary market). 15-30 minutes.
2. **Transcription:** Use Whisper API (already integrated in trochai-videos) or Claude's built-in transcription
3. **Repurposing prompts:** Create Claude Code skills/prompts for each output type:
   - `repurpose-to-tweets` — Extract 5 tweetable insights from transcript
   - `repurpose-to-linkedin` — Write 2 LinkedIn posts (storytelling format)
   - `repurpose-to-blog` — Expand into a full blog article
   - `repurpose-to-newsletter` — Format for email newsletter (use trochai-blog-poster skill)
   - `repurpose-to-video-scripts` — Extract 3 short-form video scripts for Remotion
4. **Video rendering:** Use existing Remotion pipeline + ElevenLabs to generate short-form videos
5. **Publishing:** Use Metricool API (already integrated) to schedule across platforms

**Phase 2: First Content Cycle (Week 1-2)**

1. Record pillar content: "Why 97% of real estate leads are wasted"
2. Run through the repurposing pipeline
3. Generate all 27 pieces
4. Human review and edit (30-60 minutes to check quality, remove slop)
5. Schedule across platforms using Metricool
6. Track engagement on each piece

**Phase 3: Optimize & Systematize (Week 3-4)**

1. Analyze which content types perform best per platform
2. Refine prompts based on what gets engagement vs. what feels like AI slop
3. Build a content calendar template (Notion or simple markdown)
4. Create a weekly ritual: Monday record → Tuesday repurpose → Wednesday-Friday publish
5. Add brand reference materials to prompts (tone, vocabulary, examples of good posts)

**Phase 4: Scale (Month 2+)**

1. Increase to 2 pillar pieces per week (40+ content pieces)
2. Add guest content: interview agency owners, real estate experts
3. Repurpose customer success stories into case study content
4. Build a library of evergreen content that can be reshared quarterly
5. A/B test hooks, formats, and posting times

### Integration with Existing Infrastructure

| Component | Already Have | Need to Build |
|-----------|-------------|---------------|
| Short-form video rendering | Remotion + 10 templates | New templates for repurposed content |
| Voiceover generation | ElevenLabs integration | Batch generation for repurposed scripts |
| Video publishing | Metricool API | Nothing — already working |
| Blog publishing | MDX on trochai.com | Automated MDX file creation |
| Newsletter | Blog poster skill | Connect to email list |
| Social captions | SOCIAL-CAPTIONS.md format | Automated per-video caption generation |
| Transcription | Whisper (via @remotion/captions) | Nothing — already working |

### Cost

- **Monthly:** ~$20-30 (ElevenLabs for voiceovers, Claude API for repurposing, Metricool for scheduling)
- **Time:** 2-3 hours/week (30 min recording + 30 min review + 1 hour scheduling/engagement)
- **Equipment:** Phone + $30 lapel mic (one-time)

### Expected Impact

- **27+ content pieces/week** vs. competitors posting 2-3 times
- **3 months = 300+ pieces** of content across all platforms
- **Shots on net:** More content = more chances for viral moments in your niche
- **Authority building:** Consistent presence makes Trochai the "known brand" in CR real estate tech

---

## Priority Matrix & Execution Order

### Effort vs. Impact Analysis

| Strategy | Effort | Time to Impact | Cost | Impact Potential | Priority |
|----------|--------|---------------|------|-----------------|----------|
| 1. MCP Server | Medium (3-5 days) | 2-4 weeks | $0 | High (zero-CAC channel) | **P1** |
| 2. Programmatic SEO | High (2-3 weeks) | 3-6 months | $30 | Very High (compounding) | **P2** |
| 3. Free Tool (Grader) | Medium (5-7 days) | 1-2 weeks | $10/mo | Very High (direct demo of pain) | **P1** |
| 4. AEO | Medium (2-3 weeks) | 2-4 months | $50/mo | High (compounding) | **P2** |
| 5. Viral Artifacts | Medium (5-7 days) | Immediate | $0 | Medium-High (needs users first) | **P3** |
| 6. Newsletter Acquisition | Low (research) | 1-2 weeks | $2K-$15K | Medium-High | **P3** |
| 7. Content Repurposing | Low-Medium (1 week setup) | 2-4 weeks | $30/mo | High (consistency) | **P1** |

### Recommended Execution Order

```
WEEK 1-2: Quick Wins + Foundation
├── [Strategy 7] Set up content repurposing pipeline
│   └── Record first pillar content, run through pipeline
├── [Strategy 1] Build MCP server v1 (3 tools)
│   └── Deploy to Hostinger, register on Smithery
└── [Strategy 3] Start building WhatsApp Grader

WEEK 3-4: Distribution Engines
├── [Strategy 3] Launch WhatsApp Grader
│   └── Use as content fuel for Strategy 7
├── [Strategy 4] Write first 10 AEO articles
│   └── Publish on trochai.com/blog
├── [Strategy 2] Build pSEO template + first 100 pages
│   └── Submit to Search Console
└── [Strategy 7] Week 2-3 of content pipeline (refine, optimize)

MONTH 2: Compound & Scale
├── [Strategy 2] Scale to 500+ pSEO pages
├── [Strategy 4] Write remaining 10 AEO articles + monitor citations
├── [Strategy 5] Build monthly report card artifact
│   └── Requires first paying customers to generate data
├── [Strategy 6] Research newsletter acquisition targets
│   └── Outreach to 5 newsletter owners
└── [Strategy 7] Content pipeline in full production (27 pieces/week)

MONTH 3+: Optimize & Reinvest
├── Scale what's working, cut what isn't
├── Use MCP query data to inform pSEO + AEO content
├── Use free tool data for content marketing ("We graded 100 agencies...")
├── Acquire newsletter if validated
└── Build viral artifacts as user base grows
```

### The "Pick Two" Recommendation

If you can only start two this week (as the video suggests):

1. **Strategy 7: Content Repurposing Engine** — Lowest effort to start (record a voice memo), builds everything else. Content feeds SEO, AEO, social proof, and brand.

2. **Strategy 1: MCP Server** — Unique opportunity to be first in the CR real estate niche. Zero ongoing cost. Every AI query = free customer acquisition. This is the 2010 mobile bet.

**Runner-up:** Strategy 3 (Free Tool) — because it directly demonstrates the pain point and creates warm leads. Start this in Week 2 once the content engine is running.

---

## Resource Map

### What We Already Have

| Resource | Status | Relevant Strategies |
|----------|--------|-------------------|
| Remotion video pipeline | Production-ready (10 videos rendered) | 5, 7 |
| ElevenLabs TTS | Integrated + tested | 7 |
| Metricool publishing API | Integrated | 7 |
| Blog infrastructure (MDX) | Live on trochai.com | 2, 4 |
| Property database + embeddings | Production (Supabase + pgvector) | 1, 2, 3 |
| Public property pages with SEO | Live on {org}.trochai.com | 1, 2 |
| JSON-LD structured data | Implemented | 2, 4 |
| Analytics tracking | Production (views, clicks, searches) | 5 |
| Prospect list (20 agencies) | Complete | 3, 6 |
| 6 video scripts | Written | 7 |
| Content marketing strategy | Documented | 7 |
| Vibe marketing system | Documented | All |
| Hostinger VPS | Available | 1 |
| WhatsApp API integration | Production | 3 |
| Trochai blog poster skill | Available | 4, 7 |

### What We Need to Build

| Component | Strategies | Effort |
|-----------|-----------|--------|
| MCP server (`trochai-mcp/`) | 1 | 3-5 days |
| pSEO page template + data pipeline | 2 | 5-7 days |
| WhatsApp Grader tool (frontend + backend) | 3 | 5-7 days |
| 20 AEO blog articles | 4 | 2-3 weeks |
| Monthly report card image generator | 5 | 3-4 days |
| Newsletter research + outreach | 6 | 1 week |
| Repurposing prompt library + workflow | 7 | 2-3 days |

### External Tools to Consider

| Tool | Purpose | Cost | Strategy |
|------|---------|------|----------|
| Otterly.ai | AI citation monitoring | $30/mo | 4 |
| Firecrawl | Web scraping for data enrichment | Pay-as-you-go | 2, 4 |
| Metricool | Social media scheduling (already have) | $0 (existing) | 7 |
| duuce.com | Newsletter marketplace | Free to browse | 6 |
| Smithery | MCP server registry | Free | 1 |
| Google Search Console | SEO monitoring | Free | 2, 4 |

---

## Final Note

> "Code is commoditized. Distribution is the new moat."

We built a solid product. The AI bot works. The inbox is beautiful. The billing is ready. Now every hour spent on distribution has 10x more ROI than another feature. These seven strategies aren't theoretical — they map directly to infrastructure we already have (Remotion, Supabase, property embeddings, blog, WhatsApp API).

The playbook is clear. The question is execution velocity.

**Start this week. Pick two. Ship.**
