# AI Content Repurposing Engine

> One pillar piece of content per week → 25+ pieces across all platforms.

## The Pipeline

```
RECORD (30 min)
    ↓
TRANSCRIBE (Whisper)
    ↓
REPURPOSE (Claude Code commands)
    ├── /repurpose-to-tweets      → 5 tweets
    ├── /repurpose-to-linkedin    → 2 LinkedIn posts  
    ├── /repurpose-to-blog        → 1 blog article (ES + EN)
    ├── /repurpose-to-video-scripts → 3 short-form video scripts
    ├── /repurpose-to-newsletter  → 1 newsletter edition
    └── /repurpose-all            → runs all of the above + calendar
    ↓
RENDER VIDEOS (trochai-videos Remotion pipeline)
    ↓
PUBLISH (Metricool API → Instagram, TikTok, YouTube)
    ↓
TRACK (Metricool analytics)
```

## Weekly Ritual

| Day | Activity | Time |
|-----|----------|------|
| **Monday** | Record pillar content (video/voice memo) | 30 min |
| **Monday** | Transcribe + run `/repurpose-all` | 15 min |
| **Tuesday** | Review and edit generated content | 30 min |
| **Tuesday** | Render video scripts with Remotion | 15 min |
| **Wed-Fri** | Publish per calendar (automated via Metricool) | 5 min/day |
| **Weekend** | Review analytics, note what worked | 15 min |

**Total weekly time: ~2-3 hours for 25+ pieces of content.**

## Claude Code Commands

All commands are in `/.claude/commands/` at the monorepo root:

| Command | Output | Platform |
|---------|--------|----------|
| `/repurpose-to-tweets` | 5 standalone tweets | Twitter/X |
| `/repurpose-to-linkedin` | 2 LinkedIn posts (founder-led) | LinkedIn |
| `/repurpose-to-blog` | 1 MDX article (ES + EN) | trochai.com/blog |
| `/repurpose-to-video-scripts` | 3 Remotion-ready video scripts | Reels/TikTok/Shorts |
| `/repurpose-to-newsletter` | 1 newsletter edition | Email |
| `/repurpose-all` | All of the above + content calendar | All platforms |

## Pillar Content Ideas (12-Week Backlog)

| Week | Topic | Format | Angle |
|------|-------|--------|-------|
| 1 | Why 97% of real estate leads are wasted | Voice memo | Pain point → data → solution |
| 2 | I built an AI that sells houses at 2AM | Video (screen record) | Founder story → demo |
| 3 | The 5-minute rule agencies ignore | Voice memo | Urgency → framework |
| 4 | WhatsApp is broken for teams | Video | Problem → solution comparison |
| 5 | We graded 50 agencies' response times | Voice memo | Original research |
| 6 | How expats actually search in CR | Voice memo | Buyer psychology |
| 7 | The $10K mistake every month | Voice memo | Revenue impact math |
| 8 | Building Trochai: week in the life | Video (vlog) | Behind-the-scenes |
| 9 | AI in real estate: what works | Voice memo | Industry analysis |
| 10 | The perfect WhatsApp sales flow | Screen record | Framework + templates |
| 11 | Why WhatsApp Business is losing you money | Voice memo | Comparison + upgrade |
| 12 | Our first 10 customers: lessons | Video | Social proof + learnings |

## How to Use

### Quick Start (One Command)

```bash
# In the Trochai monorepo root, with Claude Code:
# Paste your transcript and run:
/repurpose-all
```

### Individual Channels

```bash
# Just need tweets?
/repurpose-to-tweets

# Just need a blog post?
/repurpose-to-blog

# Just need video scripts for Remotion?
/repurpose-to-video-scripts
```

### Rendering Videos

After generating video scripts, go to trochai-videos and use:

```bash
cd trochai-videos
# Create new video composition from script
/new-video

# Generate voiceover audio
/generate-voiceover

# Render to MP4
/render-video

# Publish to social media
/publish-video
```

## Output Per Week (Target)

| Platform | Content Type | Qty | Source |
|----------|-------------|-----|--------|
| Instagram Reels | 9:16 video | 3 | `/repurpose-to-video-scripts` → Remotion |
| TikTok | 9:16 video | 2 | Same renders, different captions |
| YouTube Shorts | 9:16 video | 2 | Same renders |
| Twitter/X | Tweets | 5 | `/repurpose-to-tweets` |
| LinkedIn | Posts | 2 | `/repurpose-to-linkedin` |
| trochai.com | Blog article | 1 | `/repurpose-to-blog` |
| Email | Newsletter | 1 | `/repurpose-to-newsletter` |
| Instagram Stories | Story slides | 3 | Repurpose from blog/tweets |
| WhatsApp Status | Updates | 2 | Repurpose best performers |
| **Total** | | **~21** | |

## Quality Control

### Anti-Slop Checklist

Before publishing any generated content:

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
- **Language:** Spanish (ustedeo) for Instagram/TikTok/Twitter. English for LinkedIn/blog.
- **Visual:** Dark backgrounds, brand green (#20A06F), Inter font, no emojis in formal content.
- **CTA:** Always soft — "learn more", "see how", never "BUY NOW" or "LIMITED OFFER".

## Tracking & Iteration

### Metrics to Watch

| Metric | Where | Target |
|--------|-------|--------|
| Impressions per post | Metricool | 500+ |
| Engagement rate | Metricool | >3% |
| Profile visits from content | Instagram/TikTok analytics | 50+ per week |
| Blog organic traffic | Google Search Console | 100+ visits/month |
| AI citations | Otterly.ai / manual | 5+ per month |
| Newsletter open rate | Email platform | >30% |
| Leads from content | UTM tracking | 5+ per month |

### Monthly Review

At the end of each month:
1. Which 3 pieces of content performed best? Why?
2. Which platform drove the most engagement?
3. What topics resonated most?
4. Update pillar content backlog based on learnings
5. Adjust posting frequency if a platform over/underperforms
