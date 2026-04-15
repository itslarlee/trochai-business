# AI Content Repurposing Engine

> One topic per week → pillar post + 7 LinkedIn posts (daily, each with visual) + 3 video scripts + 1 blog article + LinkedIn newsletter. All in Spanish.

## The Pipeline

```
TOPIC (pick from backlog or current events)
    ↓
GENERATE PILLAR (Claude Code writes the long-form post, Spanish)
    ↓
REPURPOSE (Claude Code commands)
    ├── /repurpose-to-linkedin       → 7 LinkedIn posts with visuals (Spanish)
    ├── /repurpose-to-blog           → 1 blog article (ES + EN)
    ├── /repurpose-to-video-scripts  → 3 short-form video scripts (Spanish)
    ├── /repurpose-to-newsletter     → 1 newsletter edition (Spanish) + LinkedIn newsletter
    └── /repurpose-all               → all of the above + Remotion compositions + calendar
    ↓
OUTPUT FOLDER
    trochai-business/content/week-of-YYYY-MM-DD/
    ├── pillar.md                 (source long-form post, Spanish)
    ├── calendar.md               (daily checklist — what to post when)
    ├── monday-newsletter.md      (LinkedIn newsletter + carousel)
    ├── tuesday-growth.md         (brandjack/newsjack + infographic)
    ├── wednesday-authority.md    (educational framework carousel)
    ├── thursday-growth.md        (hot take + infographic)
    ├── friday-conversion.md      (product/results carousel or video)
    ├── saturday-authority.md     (deep-dive carousel)
    ├── sunday-personal.md        (founder journey infographic)
    ├── video-1.md                (video script 1 + captions + StatReveal props)
    ├── video-2.md                (video script 2 + captions + StatReveal props)
    ├── video-3.md                (video script 3 + captions + StatReveal props)
    └── blog-reference.md         (link to MDX files in trochai-landing)
    ↓
REMOTION COMPOSITIONS (auto-created in trochai-videos/)
    ├── src/compositions/{Video}.tsx                  (3 video compositions)
    ├── src/compositions/linkedin/{Infographic}.tsx    (7 infographics/carousels for LinkedIn posts)
    ├── src/compositions/carousel/                     (newsletter carousels)
    └── registered in src/Root.tsx
    ↓
RENDER ASSETS:
    cd trochai-videos
    npx tsx src/scripts/render-video.ts --id <ID> --quality social    # MP4 videos
    npx tsx scripts/render-carousel.ts <slug>                         # Newsletter carousel PNGs + LinkedIn PDF
    npx remotion still <CompositionId> --output=out/file.png          # Infographics, stat cards, thumbnails
    ↓
POST MANUALLY (open calendar.md each morning, copy-paste, check off)
```

## Channels

| Channel | Output | Frequency | Language |
|---------|--------|-----------|----------|
| **LinkedIn** | 7 posts/week (daily, each with carousel/infographic) + LinkedIn Newsletter | Daily | Spanish (ustedeo) |
| **LinkedIn Newsletter** | Trochai Insights weekly edition (pushes notification to all followers) | Monday | Spanish (ustedeo) |
| **Blog** | 1 article/week (trochai.com) | Weekly | ES primary + EN translation |
| **Instagram** | 2-3 cross-posts/week (LinkedIn carousels + 1-2 Reels) | 2-3x/week | Spanish (ustedeo) |
| **Video** | 3 scripts/week → Remotion compositions | As rendered | Spanish (ustedeo) |

## Daily Theme Structure

Every post gets a visual (carousel or infographic). No text-only posts. Visuals rendered via Remotion + Unsplash.

| Day | Bucket | Theme | Format | File |
|-----|--------|-------|--------|------|
| **Monday** | Authority | Trochai Insights newsletter | Carousel + LinkedIn Newsletter article | `monday-newsletter.md` |
| **Tuesday** | Growth | Brandjacking / Newsjacking | Infographic + text | `tuesday-growth.md` |
| **Wednesday** | Authority | Educational framework | Multi-slide carousel | `wednesday-authority.md` |
| **Thursday** | Growth | Hot take / Contrarian | Infographic + text | `thursday-growth.md` |
| **Friday** | Conversion | Product demo / Results | Carousel or video + carousel | `friday-conversion.md` |
| **Saturday** | Authority | Deep-dive / Case study | Carousel + long text | `saturday-authority.md` |
| **Sunday** | Personal | Founder journey (generic) | Infographic | `sunday-personal.md` |

## Content Buckets (40/30/20/10)

| Bucket | % | Posts/Week | What |
|--------|---|-----------|------|
| **Growth** | 40% | ~3 (Tue, Thu, + mix) | Brandjacking, newsjacking, namejacking, hot takes |
| **Authority** | 30% | ~2-3 (Mon, Wed, Sat) | Frameworks, data, case studies, educational carousels |
| **Conversion** | 20% | ~1 (Fri) | Product demos, customer results, testimonials |
| **Personal** | 10% | ~1 (Sun) | Founder journey — generic, relatable, no deep personal stories |

## Weekly Ritual

| Day | Activity | Time |
|-----|----------|------|
| **Monday** | Run `/monday-content` — generates all content + renders visuals | 30 min |
| **Monday** | Skim generated files, tweak anything that sounds off | 15 min |
| **Monday** | Schedule all 7 posts for the week (Metricool or native scheduling) | 15 min |
| **Daily** | 30 min comment flywheel (engage on ICP accounts) | 30 min/day |
| **Daily** | Reply to all comments on your posts | 10 min/day |
| **Weekend** | Review: what got engagement? What got saves? Note for next week | 10 min |

**Total weekly time: ~2 hours setup Monday + 40 min/day engagement = ~5.5 hours/week for daily LinkedIn presence.**

## How to Use

### The One Command

```
/monday-content
```

When prompted, give it a pillar topic and week number. It generates:
1. Newsletter (web research + blog MDX + carousel)
2. 7 LinkedIn posts with daily theme assignments
3. 3 video scripts with Remotion compositions
4. Blog article (ES + EN)
5. All Remotion visual compositions (infographics, carousels)
6. Daily calendar with checkboxes

Everything lands in `trochai-business/content/week-of-YYYY-MM-DD/`.

### Individual Channels

If you only need one format:

```
/repurpose-to-linkedin      # 7 LinkedIn posts with daily themes + visual specs
/repurpose-to-blog          # blog article (ES + EN MDX files)
/repurpose-to-video-scripts # 3 video scripts (Spanish)
/repurpose-to-newsletter    # newsletter edition + LinkedIn newsletter
```

Each one saves to the same weekly folder.

### Posting Workflow

1. Run `/monday-content` Monday morning
2. Review and tweak generated content (~15 min)
3. Schedule all 7 posts for the week using Metricool or LinkedIn's native scheduler
4. Each morning: 30 min comment flywheel + reply to your own post comments
5. Weekend: review analytics, note what worked

### Rendering Visual Assets (Remotion)

All visual assets use the same dark brand aesthetic — consistent across every format.

```bash
cd trochai-videos

# Newsletter carousel (Instagram PNGs + LinkedIn PDF)
npx tsx scripts/fetch-unsplash.ts trochai-insights-2026-s15   # Fetch background images
npx tsx scripts/render-carousel.ts trochai-insights-2026-s15  # Render PNGs + PDF in one go

# LinkedIn infographics (one per daily post)
npx remotion still LI-Infographic-Tue-W15 --output=out/linkedin/tue-w15.png --image-format=png

# LinkedIn stat cards (single images to accompany stat-driven posts)
npx remotion still LI-Card-97-Leads --output=out/linkedin/card-97.png --image-format=png

# Pillar carousel PDF (multi-slide educational content)
for i in Cover Slide-1 Slide-2 Slide-3 Slide-4 Slide-5 CTA; do
  npx remotion still "Pillar-W15-$i" --output="out/linkedin/pillar-$i.png" --image-format=png
done
npx tsx scripts/carousel-to-pdf.ts pillar-w15

# Videos (MP4 for LinkedIn video posts + Instagram Reels)
npx tsx src/scripts/render-video.ts --id <ID> --quality social

# Video thumbnails
npx remotion still Thumb-<id> --output=out/thumbnails/<name>.png --image-format=png
```

**Remotion composition types:**

| Composition | Format | Use Case |
|-------------|--------|----------|
| `LinkedInCard` | 1080x1350 (4:5) | Single stat card image for LinkedIn posts |
| `LinkedInInfographic` | 1080x1350 (4:5) | Daily infographic (brandjack, hot take, personal) |
| `PillarCarousel` | 1080x1350 (4:5) | Multi-slide carousel from pillar content → PDF for LinkedIn |
| `NewsletterCarousel` | 1080x1350 (4:5) | Weekly newsletter carousel → PNGs (Instagram) + PDF (LinkedIn) |
| `VideoThumbnail` | 1080x1920 (9:16) | Custom cover image for video posts |
| `StatReveal` | 1080x1920 (9:16) | Parametric stat video (short-form) |

## Claude Code Commands

All commands are in `/.claude/commands/` at the monorepo root:

| Command | Output | Saves To |
|---------|--------|----------|
| `/repurpose-all` | Pillar + all formats + Remotion compositions + calendar | `content/week-of-*/` + `trochai-videos/src/compositions/` |
| `/repurpose-to-linkedin` | 7 LinkedIn posts with daily themes (Spanish) | `monday-newsletter.md` through `sunday-personal.md` |
| `/repurpose-to-blog` | 1 MDX article (ES + EN) | `trochai-landing/content/blog/` |
| `/repurpose-to-video-scripts` | 3 video scripts (Spanish) | `video-1.md`, `video-2.md`, `video-3.md` |
| `/repurpose-to-newsletter` | 1 newsletter edition + LinkedIn newsletter (Spanish) | `newsletter.md` |

## Pillar Content Ideas (12-Week Backlog)

| Week | Topic | Angle | Best Bucket |
|------|-------|-------|-------------|
| 1 | Why 97% of real estate leads are wasted | Pain point → data → solution | Authority |
| 2 | I built an AI that sells houses at 2AM | Founder story → demo | Growth |
| 3 | The 5-minute rule agencies ignore | Urgency → framework | Authority |
| 4 | WhatsApp is broken for teams | Problem → solution comparison | Growth |
| 5 | We graded 50 agencies' response times | Original research | Authority |
| 6 | How expats actually search in CR | Buyer psychology | Authority |
| 7 | The $10K mistake every month | Revenue impact math | Growth |
| 8 | Building Trochai: week in the life | Behind-the-scenes | Personal |
| 9 | AI in real estate: what works | Industry analysis | Authority |
| 10 | The perfect WhatsApp sales flow | Framework + templates | Authority |
| 11 | Why WhatsApp Business is losing you money | Comparison + upgrade | Growth |
| 12 | Our first 10 customers: lessons | Social proof + learnings | Conversion |

## Output Per Week (Target)

| Platform | Content Type | Qty | Source |
|----------|-------------|-----|--------|
| LinkedIn | Daily posts with visual (carousel/infographic) | 7 | `monday-*.md` through `sunday-*.md` |
| LinkedIn | Newsletter article (Trochai Insights) | 1 | Monday post + LinkedIn Newsletter |
| LinkedIn | Pillar carousel PDF | 1 | `PillarCarousel` composition → PDF |
| Instagram | Cross-posted carousels | 2-3 | Same PNGs from LinkedIn carousels |
| Instagram | Reels (cross-posted videos) | 1-2 | Remotion renders |
| trochai.com | Blog article (ES + EN) | 1 | `trochai-landing/content/blog/` |
| Video | Short-form scripts + Remotion renders | 3 | `video-1.md` through `video-3.md` |
| **Total** | | **~16-18** | |

## Quality Control

### Anti-Slop Checklist

Before posting any generated content:

- [ ] Does it sound like a human wrote it? (no corporate filler, no "en el mundo actual")
- [ ] Is the hook strong enough to stop someone scrolling? (first 1-2 lines = 3-5x algorithm weight)
- [ ] Does it provide genuine value? (would you save it if you weren't promoting it?)
- [ ] Is the Trochai mention natural? (not a forced CTA?)
- [ ] Is it in the right language and tone? (ustedeo for CR, casual for social)
- [ ] Are the numbers accurate and sourced? (include "Fuentes:" with URLs)
- [ ] Does it have a visual? (every post needs carousel or infographic)
- [ ] Would YOU share this? If not, don't publish it.

### Brand Reference

- **Voice:** Confident expert, data-first, not salesy
- **Language:** Spanish (ustedeo) for everything. English only for blog translation.
- **Visual:** Dark backgrounds, brand green (#20A06F), Inter font, no emojis in formal content
- **CTA:** Always soft — "conozca mas", "vea como", never "COMPRE AHORA" or "OFERTA LIMITADA"
- **Personal content:** Generic, relatable founder stories only. No fabricated anecdotes.

## Tracking & Iteration

### Metrics to Watch

| Metric | Where | Target |
|--------|-------|--------|
| Impressions per post | LinkedIn analytics | 500+ |
| Engagement rate | LinkedIn analytics | >3% |
| Saves per post | LinkedIn analytics | Track trend (key algorithm signal) |
| Profile visits | LinkedIn analytics | 50+ per week |
| Newsletter subscribers | LinkedIn newsletter | 100+ in 90 days |
| Blog organic traffic | Google Search Console | 100+ visits/month |
| AI citations | Manual checks | 5+ per month |
| Leads from content | UTM tracking | 5+ per month |

### Monthly Review

1. Which 3 posts performed best? Why? (topic, format, hook, bucket)
2. Which bucket drove the most engagement? Adjust 40/30/20/10 if needed.
3. What topics resonated most? Update pillar backlog.
4. Which posts got the most saves? (key metric for 360 Brew)
5. Is the comment flywheel working? Track profile visits from comments.
