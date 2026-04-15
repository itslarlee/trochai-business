# Vibe Marketing System

> Using Claude Code + skills + MCPs to build a complete marketing system from the terminal.
>
> **Source:** [The Startup Ideas Podcast — "Vibe Marketing Masterclass"](https://www.youtube.com/watch?v=XXXXX) with James Dickerson (The Boring Marketer) and Greg Isenberg

---

## What Is Vibe Marketing?

Vibe marketing = using AI agents (Claude Code, skills, MCPs) to build complete marketing systems — landing pages, ad creatives, lead magnets, email sequences, SEO content, video ads — all from the terminal, the same way you'd vibe code a product.

**The key insight:** You can deploy complete marketing systems and campaigns right from the terminal, just like you'd vibe code any product. Research, copy, design, ads, video — all in one place.

---

## The 3-Layer Framework

James uses three layers stacked together:

### Layer 1: Research (MCPs)

Cast a wide net before creating anything. **This is where most people fail — they skip research and get AI slop.**

| MCP | Purpose | Cost |
|---|---|---|
| **Perplexity MCP** | Deep market research — competitors, gaps, angles, pricing, audience behavior | Free with API key |
| **Firecrawl MCP** | Scrape websites for copy, structure, pricing, positioning. New Firecrawl Agent can do research tasks (e.g., "find all Facebook pages for RE agencies in Costa Rica") | Free tier available |
| **Playwright MCP** | Browser automation — open competitor websites, take screenshots, capture design/copy/layout inspiration | Free (open source) |

**Research workflow:**
1. Use Perplexity MCP to research your market, competitors, gaps, and underserved angles
2. Use Firecrawl to scrape specific competitor websites for copy/pricing/structure
3. Use Playwright to capture screenshots for design inspiration and competitive intelligence

> "I'll spend an hour sometimes doing research with Perplexity, crawling websites, getting as much data as I possibly can about my market. A lot of people miss that part. They hop in and start trying to create stuff and that's where the AI slop thing comes from."

### Layer 2: Skills (Marketing Frameworks)

Skills are instruction manuals for Claude Code — deeply trained on specific marketing tasks. They encode frameworks, taste, and expert knowledge.

**How skills work:**
- Each skill is a markdown file with prompts, examples, frameworks, and rules
- You invoke them in your prompts: "Use the positioning angles skill to..."
- Claude Code loads the skill and applies its frameworks to your specific context
- You can stack multiple skills in sequence for a complete workflow

**Key principle:** A skill built by an expert captures the last 10-20% that generic AI prompting can't. You can create your own skills by:
1. Deep research using Perplexity/Firecrawl on the topic
2. Include world-class references and frameworks
3. Review by hand to add your taste
4. Iterate based on output quality

### Layer 3: Building (Execution)

Once you have research + skills, you execute: landing pages, ads, lead magnets, email sequences, SEO content, video ads.

---

## James's Skill Stack (17 Skills)

These are the skills he demonstrated or referenced:

| Skill | What It Does |
|---|---|
| **Positioning Angles** | Finds unique market positioning — transformation framing, competitive landscape, emotional angles, white space opportunities |
| **Direct Response Copywriting** | Generates conversion-focused copy based on Eugene Schwarz, Claude Hopkins, and modern frameworks. Includes founder story section |
| **Front-End Design** (Anthropic's) | Prevents AI-looking design (purple gradients, rounded corners, emojis). Creates distinctive, professional landing pages |
| **Orchestrator** | Helps decide what to do next — analyzes what you have vs. what's missing, recommends which skills to invoke |
| **Lead Magnet** | Generates 3-5 lead magnet concepts, scores them, picks the best one. Types: calculators, audits, PDFs, workshops, email sequences |
| **Keyword Research** | Identifies programmatic SEO opportunities, quick wins, content pipelines for organic traffic |
| **DTC Ad** | Creates ad strategies based on direct-to-consumer frameworks — hooks, angles, formats that drive conversion |
| **SEO Content** | Develops SEO-optimized pages targeting specific keywords and markets |
| **Content** | Generates long-form and short-form content with brand voice |
| **Email Sequence** | Nurture sequences for leads after signup |
| **Image Generation** | Prompts for Nano Banana Pro / Glyph MCP — creates product images, ad statics, brand visuals |
| **Video Ad** | Works with Remotion to create animated video ads programmatically |

### Creating Your Own Skills

```
Hey Claude Code, I want to create a skill around [topic].
Go deep research using Perplexity on [frameworks, experts, best practices].
Include world-class references.
Create a skill file I can invoke.
```

Or more structured:
1. Research the topic deeply (Perplexity MCP)
2. Crawl websites of experts/leaders in that space (Firecrawl)
3. Compile learnings into a skill markdown file
4. Review by hand — add your taste, remove generic stuff
5. Test the skill on real tasks, iterate

### Orchestrator Skill Pattern

When you don't know what to do next:

```
Use the orchestrator skill. I don't know what to do next.
I have [X, Y, Z]. I want to [goal].
Help me decide what skills to use and in what order.
```

The orchestrator analyzes your current assets and gaps, then recommends a prioritized action plan with specific skills to invoke.

---

## Remotion: Programmatic Video Ads

### What Is Remotion?

Remotion is an open-source React framework for creating videos programmatically. You write React components, and Remotion renders them frame-by-frame into video files (MP4, WebM, etc.) using headless Chrome + ffmpeg.

**Created by:** Jonny Burger (@JNYBGR)
**GitHub:** [github.com/remotion-dev/remotion](https://github.com/remotion-dev/remotion)
**Docs:** [remotion.dev](https://www.remotion.dev/)

### Why Remotion Matters for Marketing

- Create video ads **from the terminal** with natural language prompts
- Generate **100 video variants** from 1 template with 1 prompt
- Multiple formats in one go: 9:16 (Reels/TikTok), 1:1 (Feed), 4:5 (Carousel), 16:9 (YouTube)
- **Brand consistency** enforced by templates (colors, fonts, style)
- **Data-driven** — pull from APIs/databases to generate personalized videos
- Cost: **$0** (free for companies with 3 or fewer employees)

> "I saw a viral tweet from Remotion. They create videos and edit videos in Claude Code. I was like, wow, that looks incredible. I hate trying to create videos."

### How It Works Technically

- A video = "a function of images over time"
- `useCurrentFrame()` hook gives you the current frame number
- `interpolate()` maps frame ranges to CSS values (position, opacity, scale)
- `spring()` provides physics-based easing for natural motion
- `<Sequence>` offsets components in time (like a timeline)
- Compositions = React component + metadata (width, height, fps, duration)
- At render time: headless Chrome screenshots each frame → ffmpeg stitches into video

### Remotion + Claude Code Integration

**Official Agent Skills** (the viral tweet — 8.3M views):

```bash
npx skills add remotion-dev/skills
```

This installs **37 rule files** covering:
- Animations, transitions, text animations, sequencing
- Assets (images, videos, audio, fonts, GIFs, Lottie)
- Captions/subtitles with word-level sync
- 3D rendering (Three.js), charts, maps (Mapbox)
- ElevenLabs TTS voiceover integration
- TailwindCSS, transparent video, FFmpeg operations
- Making videos parametrizable with Zod schemas

**Key links:**
| Resource | URL |
|---|---|
| Official skills repo | [github.com/remotion-dev/skills](https://github.com/remotion-dev/skills) |
| Claude Code setup guide | [remotion.dev/docs/ai/claude-code](https://www.remotion.dev/docs/ai/claude-code) |
| Agent Skills docs | [remotion.dev/docs/ai/skills](https://www.remotion.dev/docs/ai/skills) |
| Viral tweet (8.3M views) | [x.com/Remotion/status/2013626968386765291](https://x.com/Remotion/status/2013626968386765291) |
| Beginner guide (Jonny Burger) | [x.com/JNYBGR/status/2015708193167479209](https://x.com/JNYBGR/status/2015708193167479209) |

### Community Skills for Ads

**[remotion-ads](https://github.com/Maartenlouis/remotion-ads)** — The most feature-rich community skill for marketing:
- Instagram Reels (9:16, 1080x1920, 15-60s), Website Explainers (16:9), Carousels (4:5)
- ElevenLabs voiceover with word-level timestamp precision
- Animated word-by-word captions
- URL-to-video pipeline — scrapes a webpage and auto-generates a scene structure
- Brand config system — colors, fonts, caption style, voice presets
- Suno API for background music generation
- Install: `claude skill install remotion-ads`

**[claude-remotion-kickstart](https://github.com/jhartquist/claude-remotion-kickstart)** — Starter kit with:
- Pre-built components: TitleSlide, ContentSlide, CodeSlide, DiagramSlide
- Slash commands: `/new-composition`, `/generate-image`, `/generate-video`, `/transcribe`
- Transcript-based timing to sync visuals with narration

### Setup (Step by Step)

```bash
# 1. Create new Remotion project
npx create-video@latest my-video
# Choose: Blank template, enable TailwindCSS, install Skills

# 2. Install dependencies
cd my-video && npm install

# 3. Start Remotion Studio (real-time preview)
npm run dev
# Opens at localhost:3001

# 4. Open Claude Code in same project
claude

# 5. Prompt Claude to create videos
# "Create a 15-second Instagram Reel (1080x1920, 30fps) that reveals
# the stat '78% of buyers choose the first agent to respond' with
# dramatic text animation on a dark background with Trochai brand colors"

# 6. Render final video
npx remotion render MyComposition --output out/video.mp4
```

### Video Output Capabilities

**Formats:**
| Format | Codec | Use Case |
|---|---|---|
| MP4 | H.264 (default) | Universal — social media, ads |
| MP4 | H.265 (HEVC) | Better compression |
| WebM | VP8/VP9 | Web-native |
| MOV | ProRes | Professional editing |
| GIF | — | Short loops |

**Aspect Ratios:**
| Use Case | Dimensions | Ratio |
|---|---|---|
| TikTok / Reels / Stories | 1080x1920 | 9:16 |
| Instagram Feed | 1080x1080 | 1:1 |
| Instagram Carousel | 1080x1350 | 4:5 |
| YouTube / Landscape | 1920x1080 | 16:9 |

No length limits. 30fps standard for social, 60fps supported.

### Pricing

| Tier | Cost | Who Qualifies |
|---|---|---|
| **Free** | $0 | Individuals, companies with 3 or fewer employees, non-profits |
| **Company** | From $100/month | 4+ employees ($15/dev seat + $10/1K renders) |
| **Enterprise** | From $500/month | Custom terms |

Cloud rendering on AWS Lambda: ~$0.01/minute of rendered video (separate from license).

**Trochai qualifies for the free tier.**

### What Remotion Is Good At

- Animated text/stat reveals (perfect for the 5-stat video series)
- Product demo animations (Trochai inbox mockup, bot responding)
- Data-driven property listing videos from database
- Batch ad creative generation (20+ variants from 1 template)
- Consistent branding across all video output
- Multi-format export (Reels + Feed + Stories from same source)
- Bilingual variants (Spanish + English from same template)

### What Remotion Is NOT Good At

- Talking head / founder-led content (still need to film yourself)
- Real footage editing (not a replacement for CapCut/Descript)
- UGC / testimonial filming
- Complex organic animation (it's web tech, not After Effects)
- Audio mixing / music production (basic audio support only)

---

## Remotion vs Other Video Tools

| Dimension | Remotion | CapCut / Descript |
|---|---|---|
| **Best for** | Templated, data-driven, batch generation | One-off creative edits, footage-based |
| **Skill required** | React/TypeScript | Beginner-friendly |
| **Scale** | 1,000 variants from 1 template | 1 video at a time |
| **Real footage** | Can embed, not the primary use | Core strength |
| **Talking head / UGC** | Not suitable | Core strength |
| **Brand consistency** | Perfect — templates enforce it | Depends on editor |
| **Single video speed** | Slower (code → render) | Faster (visual editor) |
| **100 videos speed** | Massively faster | Impossibly slow |
| **Cost at scale** | Near-zero marginal cost | Linear time cost |
| **AI integration** | Native via Claude Code skills | Limited |

**Recommendation:** Use both. Remotion for templated/data-driven content, CapCut for filmed/edited content.

---

## Complete Vibe Marketing Workflow

Here's the full workflow James demonstrated, adapted for Trochai:

### Step 1: Research (30-60 min)

```
I'm building an AI-powered WhatsApp inbox for real estate agencies
in Costa Rica. Use the Perplexity MCP to research:
- Who are the main competitors in LATAM proptech?
- What gaps exist in the market?
- What messaging angles are agencies responding to?
- What are the biggest pain points for RE agencies with WhatsApp?
```

Supplement with:
- Firecrawl to scrape competitor websites (pricing, copy, features)
- Playwright to capture screenshots of competitor landing pages and ads

### Step 2: Positioning (15-20 min)

```
Based on the research, use the positioning angles skill to find
how we can optimally position Trochai Inbox.
Consider our ICP: RE agency owners/managers in Costa Rica, 3-20 agents,
GAM area, WhatsApp Business users.
```

Then spin up a task-based agent to review and pick the best angle:

```
You're Greg Isenberg. You're an expert at finding positioning angles.
Analyze this positioning research and choose the angle that will work
best for us. Explain why.
```

### Step 3: Copy (15-20 min)

```
Based on our positioning angle, use the direct response copy skill
to generate conversion-optimized copy for our landing page.
Include: hero headline, subheadline, problem section, solution section,
features/benefits, social proof section, founder story, CTA.
```

### Step 4: Competitive Intelligence (10-15 min)

```
Use the Playwright MCP to visit [competitor URL]. Capture screenshots
of their website. Analyze their messaging, copy, stats, design patterns.
Create a competitive intelligence summary.
```

### Step 5: Landing Page (20-30 min)

```
Based on the competitive intelligence, positioning angle, and direct
response copy, create a conversion-optimized landing page using the
front-end design skill. Make it distinctive — no AI-looking purple
gradients or generic rounded corners.
```

### Step 6: Lead Magnet (15-20 min)

```
Use the orchestrator skill. I have a landing page with positioning
and copy. What should I do next to convert visitors?
```

Then:

```
Use the lead magnet skill to generate 3-5 concepts. Pick the best
one and build it. Add it to the landing page as a modal or section.
```

### Step 7: Traffic Strategy (20-30 min)

```
Use the keyword research skill to identify programmatic SEO
opportunities targeting our market. Also use the DTC ad skill
to come up with an ad strategy for Meta/Instagram.
```

### Step 8: Ad Creative (20-30 min)

```
Use Remotion to create video ads using our brand style, positioning,
and copy. Generate multiple formats: 9:16 for Reels, 1:1 for Feed,
16:9 for YouTube.
```

### Step 9: Email Nurture (15-20 min)

```
Create an email sequence for leads who download our lead magnet.
5-7 emails over 2 weeks. Value-first, then offer.
```

**Total time: ~3-4 hours for a complete marketing system.**

---

## How This Applies to Trochai

### What We Already Have
- ICP defined (CR RE agencies, 3-20 agents, GAM area)
- Manifesto / messaging framework (MARKETING.md)
- Prospect list with personalized messages (PROSPECT-LIST.md)
- Content strategy with 5 content pillars (CONTENT-MARKETING-STRATEGY.md)
- 6 video scripts ready to film (VIDEO-SCRIPTS.md)
- Landing page (trochai.com)

### What We Can Add With Vibe Marketing

**Remotion for content production:**
1. **Stat-based animated videos** — the 5 stats series from VIDEO-SCRIPTS.md, but as Remotion animations (no filming needed for the text/stat parts)
2. **Property listing Reels** — data-driven from Supabase, auto-generate per property
3. **Product demo animations** — animated mockup of Trochai inbox, bot responding to messages
4. **Ad creative pipeline** — batch generate Meta ad variants with different hooks/CTAs
5. **Agent profile videos** — branded intros for each agency's agents

**Skills for content quality:**
- Direct response copy skill for ad/post copy
- Positioning skill to test new angles
- Lead magnet skill for trochai.com conversion

**MCPs for research:**
- Perplexity for ongoing market research and ICP refinement
- Firecrawl to monitor competitor changes
- Playwright for competitive intelligence screenshots

### Recommended Remotion Content for Trochai

#### Template 1: Stat Reveal (for the 5-stat video series)
- Dark background, dramatic text animation
- Big number animates in → stat text appears → Trochai solution → CTA
- 15-20 seconds, 9:16 format
- Can generate all 5 stats from 1 template by changing props

#### Template 2: Product Demo Animation
- Animated phone mockup showing Trochai inbox
- WhatsApp message arrives → bot responds → property info sent
- 20-30 seconds, 9:16 format
- Perfect for "Look what this does" content pillar

#### Template 3: Before/After Split Screen
- Left: chaotic WhatsApp native (unread messages piling up)
- Right: organized Trochai inbox (sorted, assigned, responded)
- Animated transition between the two states
- 15-20 seconds, 9:16 format

#### Template 4: Property Listing Video
- Pull property data (photos, price, bedrooms, location, features) from Supabase
- Animated slide show with brand overlay, price tag, key features
- Auto-generate per property — agencies can share on Instagram
- 15 seconds, 9:16 format
- **This becomes a product feature later** ("Auto-generate Instagram Reels for your listings")

#### Template 5: Data Dashboard / Market Update
- Animated charts/stats about CR real estate market
- "This week in Costa Rica real estate" — weekly content
- Pull data from public sources
- 20-30 seconds, 9:16 or 1:1 format

### The Hybrid Approach (Remotion + Filmed Content)

| Content Type | Tool | Example |
|---|---|---|
| Stat reveals (text/animation) | **Remotion** | "97% of leads are wasted" with dramatic number animation |
| Founder talking head | **Film + CapCut** | "I built an AI WhatsApp inbox — here's what it does" |
| Product demo (animated mockup) | **Remotion** | Animated phone showing bot responding |
| Product demo (real screen recording) | **Film + CapCut** | Actual Trochai screen recording with captions |
| Pain point POV | **Film + CapCut** | "POV: 47 unread WhatsApp messages" (need your face/reactions) |
| Behind the scenes | **Film + CapCut** | "What I shipped this week" (founder journey) |
| Ad creatives (batch) | **Remotion** | 20 variants of same ad with different hooks |
| Property listings | **Remotion** | Auto-generated from Supabase data |
| Testimonials | **Film + CapCut** | Real customer quotes (once you have them) |
| Market updates / data | **Remotion** | Animated charts and stats |

---

## Tool Stack Summary

### MCPs (Research Layer)

| MCP | Purpose | Setup |
|---|---|---|
| Perplexity | Deep market/competitor research | API key in MCP config |
| Firecrawl | Website scraping, data extraction | API key, free tier |
| Playwright | Browser automation, screenshots | `npm install playwright`, free |

### Skills (Framework Layer)

Build or find skills for:
- Positioning / angles
- Direct response copywriting
- Landing page design (use Anthropic's front-end design skill)
- Lead magnets
- Orchestration (deciding what to do next)
- Keyword research / SEO
- Ad creative (DTC frameworks)
- Email sequences
- Content / brand voice

**Skill directory:** Search online for Claude Code skill directories, or create your own from deep research.

### Execution Tools

| Tool | Purpose | Cost |
|---|---|---|
| **Remotion** | Programmatic video creation | Free (< 3 employees) |
| **CapCut** | Editing filmed content | Free (Pro ~$10/mo) |
| **Instagram Edits** | Quick mobile edits, direct publishing | Free |
| **Glyph MCP** | AI image generation (Nano Banana Pro) | Varies |
| **Claude Code** | Everything — the orchestration layer | $200/mo Max subscription |

---

## Practical Tips From the Episode

1. **Split terminals** — Research in one Claude Code instance, execution in another. MCPs fill up context fast.
2. **Checkpoint after skills** — After running a skill, spin up a fresh task-based agent to review and pick the best output. Fresh context = better judgment.
3. **Record yourself working** — Use Whisper Flow to narrate while you work. Transcribe it. Turn the transcript into a lead magnet (that's how James created his playbook).
4. **Simple MCP stack** — Perplexity + Firecrawl + Playwright covers 90% of needs. Don't over-collect MCPs.
5. **Skills > generic prompting** — A skill with expert frameworks will outperform a one-shot prompt every time.
6. **DTC ad research** — Even if you're B2B SaaS, study DTC ecom ads for hooks, angles, and formats. They spend the most on testing.
7. **Multiple landing page variants** — Create separate landing pages per audience segment. One prompt per variant. Test which converts.
8. **$200/mo Max subscription** — James runs everything on this and has never run out of tokens.

---

## Resources

### James Dickerson (The Boring Marketer)
- X: [@dickersonjames](https://x.com/dickersonjames)
- Vibe Marketing Playbook: [thevibemarketer.com/vibe-marketing-playbook.html](https://www.thevibemarketer.com/vibe-marketing-playbook.html)
- GitHub Gists (skills): [gist.github.com/boringmarketer](https://gist.github.com/boringmarketer)

### Remotion
- Official site: [remotion.dev](https://www.remotion.dev/)
- GitHub: [github.com/remotion-dev/remotion](https://github.com/remotion-dev/remotion)
- Skills repo: [github.com/remotion-dev/skills](https://github.com/remotion-dev/skills)
- Claude Code docs: [remotion.dev/docs/ai/claude-code](https://www.remotion.dev/docs/ai/claude-code)
- Community ad skill: [github.com/Maartenlouis/remotion-ads](https://github.com/Maartenlouis/remotion-ads)
- Starter kit: [github.com/jhartquist/claude-remotion-kickstart](https://github.com/jhartquist/claude-remotion-kickstart)

### Guides & Tutorials
- Ad creation guide: [adlibrary.com/guides/build-viral-animated-videos-claude-code-remotion](https://adlibrary.com/guides/build-viral-animated-videos-claude-code-remotion)
- 5 video prompts: [sabrina.dev/p/5-insane-claude-code-video-prompts](https://www.sabrina.dev/p/5-insane-claude-code-video-prompts)
- Full walkthrough: [alexmcfarland.substack.com/p/claude-code-can-make-videos-now-full](https://alexmcfarland.substack.com/p/claude-code-can-make-videos-now-full)

### Anthropic
- Front-end design skill: Built into Claude Code, invoke with "use the front-end design skill"

---

*Last updated: March 26, 2026*
