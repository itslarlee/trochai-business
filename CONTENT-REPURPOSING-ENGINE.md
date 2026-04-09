# AI Content Repurposing Engine

> One topic per week → pillar post + ~12 pieces across 4 channels + Remotion videos. No recording needed. All in Spanish.

## The Pipeline

```
TOPIC (pick from backlog or current events)
    ↓
GENERATE PILLAR (Claude Code writes the long-form post, Spanish)
    ↓
REPURPOSE (Claude Code commands)
    ├── /repurpose-to-linkedin       → 4 LinkedIn posts (Spanish)
    ├── /repurpose-to-blog           → 1 blog article (ES + EN)
    ├── /repurpose-to-video-scripts  → 3 short-form video scripts (Spanish)
    ├── /repurpose-to-newsletter     → 1 newsletter edition (Spanish)
    └── /repurpose-all               → all of the above + Remotion compositions + calendar
    ↓
OUTPUT FOLDER
    trochai-business/content/week-of-YYYY-MM-DD/
    ├── pillar.md            (source long-form post, Spanish)
    ├── calendar.md          (daily checklist — what to post when)
    ├── linkedin-1.md        (LinkedIn post 1, Spanish)
    ├── linkedin-2.md        (LinkedIn post 2, Spanish)
    ├── linkedin-3.md        (LinkedIn post 3, Spanish)
    ├── linkedin-4.md        (LinkedIn post 4, Spanish)
    ├── video-1.md           (video script 1 + IG/TikTok captions + StatReveal props)
    ├── video-2.md           (video script 2 + IG/TikTok captions + StatReveal props)
    ├── video-3.md           (video script 3 + IG/TikTok captions + StatReveal props)
    ├── newsletter.md        (newsletter edition + subject lines)
    └── blog-reference.md    (link to MDX files in trochai-landing)
    ↓
REMOTION COMPOSITIONS (auto-created in trochai-videos/)
    ├── src/compositions/{Video}.tsx       (3 video compositions)
    ├── src/compositions/linkedin/         (stat cards + pillar carousels)
    ├── src/compositions/carousel/         (newsletter carousels)
    └── registered in src/Root.tsx
    ↓
RENDER ASSETS:
    cd trochai-videos
    npx tsx src/scripts/render-video.ts --id <ID> --quality social   # MP4 videos
    npx tsx scripts/render-carousel.ts <slug>                        # Newsletter carousel PNGs + LinkedIn PDF
    npx remotion still <CompositionId> --output=out/file.png         # Individual stills (stat cards, thumbnails)
    ↓
POST MANUALLY (open calendar.md each morning, copy-paste, check off)
```

## Channels

| Channel | Output | Language |
|---------|--------|----------|
| **LinkedIn** | 4 posts/week (founder perspective) + stat card images + pillar carousel PDFs | Spanish (ustedeo) |
| **Blog** | 1 article/week (trochai.com) | ES primary + EN translation |
| **Video** | 3 scripts/week (Reels + TikTok) → Remotion compositions + custom thumbnails | Spanish (ustedeo) |
| **Newsletter** | 1 edition/week (via MailerLite) + Instagram/LinkedIn carousel | Spanish (ustedeo) |

## Weekly Ritual

| Day | Activity | Time |
|-----|----------|------|
| **Monday** | Run `/repurpose-all` with this week's topic | 15 min |
| **Monday** | Skim generated files, tweak anything that sounds off | 15 min |
| **Tuesday** | Render video scripts with Remotion (if using) | 15 min |
| **Tue-Fri** | Open `calendar.md`, post what's listed, check it off | 10 min/day |
| **Weekend** | Review: what got engagement? Note for next week | 10 min |

**Total weekly time: ~1.5-2 hours for ~12 pieces of content across 4 channels + rendered videos.**

## How to Use

### The One Command

```
/repurpose-all
```

When prompted, give it a topic. Examples:
- "Why 97% of real estate leads are wasted"
- "The 5-minute rule agencies ignore"
- "WhatsApp is broken for teams"

It generates the pillar post + all repurposed content + a weekly calendar with checkboxes. Everything lands in `trochai-business/content/week-of-YYYY-MM-DD/`.

### Individual Channels

If you only need one format:

```
/repurpose-to-linkedin      # just LinkedIn posts (4, Spanish)
/repurpose-to-blog          # just blog article (ES + EN MDX files)
/repurpose-to-video-scripts # just video scripts (Spanish)
/repurpose-to-newsletter    # just newsletter edition (Spanish)
```

Each one saves to the same weekly folder.

### Posting Workflow

1. Open `trochai-business/content/week-of-YYYY-MM-DD/calendar.md`
2. It looks like this:
   ```
   ## Monday
   - [ ] **Instagram Reel:** video-1 → open `video-1.md`, use caption
   ```
3. Open the referenced file, copy the content, paste into the platform
4. Check the box in `calendar.md`
5. Done. Next item tomorrow.

### Rendering Videos (Optional)

If you want to turn video scripts into actual Remotion videos:

```bash
cd trochai-videos
npm run dev          # preview in Remotion studio
/new-video           # create composition from script
/generate-voiceover  # ElevenLabs voiceover
/render-video        # render to MP4
```

Otherwise, use the video scripts as content for CapCut / Instagram Edits / direct-to-camera recordings.

### Rendering Visual Assets (Remotion)

All visual assets use the same dark brand aesthetic — consistent across every format.

```bash
cd trochai-videos

# Newsletter carousel (Instagram PNGs + LinkedIn PDF)
npx tsx scripts/fetch-unsplash.ts trochai-insights-2026-s15   # Fetch background images
npx tsx scripts/render-carousel.ts trochai-insights-2026-s15  # Render PNGs + PDF in one go

# LinkedIn stat cards (single images to accompany LinkedIn posts)
npx remotion still LI-Card-97-Leads --output=out/linkedin/card-97.png --image-format=png

# Pillar carousel (LinkedIn PDF from topic content)
# Render all slides, then convert to PDF:
for i in Cover Slide-1 Slide-2 Slide-3 Slide-4 Slide-5 CTA; do
  npx remotion still "Pillar-97-$i" --output="out/linkedin/pillar-$i.png" --image-format=png
done
npx tsx scripts/carousel-to-pdf.ts pillar-97  # (after moving PNGs to out/carousel/pillar-97/)

# Video thumbnails (custom covers for Reels/TikTok)
npx remotion still Thumb-97-Leads --output=out/thumbnails/thumb-97.png --image-format=png
```

**Remotion composition types:**

| Composition | Format | Use Case |
|-------------|--------|----------|
| `LinkedInCard` | 1080×1350 (4:5) | Single stat card image for LinkedIn posts |
| `PillarCarousel` | 1080×1350 (4:5) | Multi-slide carousel from pillar content → PDF for LinkedIn |
| `NewsletterCarousel` | 1080×1350 (4:5) | Weekly newsletter carousel → PNGs (Instagram) + PDF (LinkedIn) |
| `VideoThumbnail` | 1080×1920 (9:16) | Custom cover image for Reels/TikTok videos |
| `StatReveal` | 1080×1920 (9:16) | Parametric stat video (short-form) |

## Claude Code Commands

All commands are in `/.claude/commands/` at the monorepo root:

| Command | Output | Saves To |
|---------|--------|----------|
| `/repurpose-all` | Pillar + all formats + Remotion compositions + calendar | `content/week-of-*/` + `trochai-videos/src/compositions/` |
| `/repurpose-to-linkedin` | 4 LinkedIn posts (Spanish) | `linkedin-1.md` through `linkedin-4.md` |
| `/repurpose-to-blog` | 1 MDX article (ES + EN) | `trochai-landing/content/blog/` |
| `/repurpose-to-video-scripts` | 3 video scripts (Spanish) | `video-1.md`, `video-2.md`, `video-3.md` |
| `/repurpose-to-newsletter` | 1 newsletter edition (Spanish) | `newsletter.md` |

## Pillar Content Ideas (12-Week Backlog)

| Week | Topic | Angle |
|------|-------|-------|
| 1 | Why 97% of real estate leads are wasted | Pain point → data → solution |
| 2 | I built an AI that sells houses at 2AM | Founder story → demo |
| 3 | The 5-minute rule agencies ignore | Urgency → framework |
| 4 | WhatsApp is broken for teams | Problem → solution comparison |
| 5 | We graded 50 agencies' response times | Original research |
| 6 | How expats actually search in CR | Buyer psychology |
| 7 | The $10K mistake every month | Revenue impact math |
| 8 | Building Trochai: week in the life | Behind-the-scenes |
| 9 | AI in real estate: what works | Industry analysis |
| 10 | The perfect WhatsApp sales flow | Framework + templates |
| 11 | Why WhatsApp Business is losing you money | Comparison + upgrade |
| 12 | Our first 10 customers: lessons | Social proof + learnings |

## Output Per Week (Target)

| Platform | Content Type | Qty | Source File |
|----------|-------------|-----|-------------|
| Instagram Reels | 9:16 video | 3 | `video-1.md` → Remotion compositions |
| TikTok | 9:16 video | 3 | Same renders, different captions |
| LinkedIn | Posts + stat card images | 4 | `linkedin-1.md` + `LinkedInCard` compositions |
| LinkedIn | Pillar carousel PDF | 1 | `PillarCarousel` composition → PDF |
| Instagram | Newsletter carousel | 1 | `NewsletterCarousel` → PNGs |
| LinkedIn | Newsletter carousel PDF | 1 | Same PNGs → `carousel-to-pdf.ts` |
| Video covers | Thumbnails (9:16) | 3 | `VideoThumbnail` compositions |
| trochai.com | Blog article | 1 | `trochai-landing/content/blog/` |
| Newsletter | Email edition | 1 | `newsletter.md` → MailerLite |
| **Total** | | **~18** | |

## Quality Control

### Anti-Slop Checklist

Before posting any generated content:

- [ ] Does it sound like a human wrote it? (no corporate filler, no "in today's fast-paced world")
- [ ] Is the hook strong enough to stop someone scrolling?
- [ ] Does it provide genuine value? (would you read it if you weren't promoting it?)
- [ ] Is the Trochai mention natural? (not a forced CTA?)
- [ ] Is it in the right language and tone? (ustedeo for CR, casual for social)
- [ ] Are the numbers accurate and sourced?
- [ ] Would YOU share this? If not, don't publish it.

### Brand Reference

Keep these consistent across all content:

- **Voice:** Confident expert, not salesy. Data-first, story-second.
- **Language:** Spanish (ustedeo) for everything. English only for blog translation.
- **Visual:** Dark backgrounds, brand green (#20A06F), Inter font, no emojis in formal content.
- **CTA:** Always soft — "conozca más", "vea cómo", never "COMPRE AHORA" or "OFERTA LIMITADA".

## Tracking & Iteration

### Metrics to Watch

| Metric | Where | Target |
|--------|-------|--------|
| Impressions per post | Platform analytics | 500+ |
| Engagement rate | Platform analytics | >3% |
| Profile visits from content | Instagram/TikTok analytics | 50+ per week |
| Blog organic traffic | Google Search Console | 100+ visits/month |
| AI citations | Manual checks | 5+ per month |
| Newsletter open rate | Email platform | >30% |
| Leads from content | UTM tracking | 5+ per month |

### Monthly Review

At the end of each month:
1. Which 3 pieces of content performed best? Why?
2. Which platform drove the most engagement?
3. What topics resonated most?
4. Update pillar content backlog based on learnings
5. Adjust posting frequency if a platform over/underperforms
