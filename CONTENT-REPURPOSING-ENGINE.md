# AI Content Repurposing Engine

> One topic per week → pillar post + 25 pieces across all platforms. No recording needed.

## The Pipeline

```
TOPIC (pick from backlog or current events)
    ↓
GENERATE PILLAR (Claude Code writes the long-form post)
    ↓
REPURPOSE (Claude Code commands)
    ├── /repurpose-to-tweets      → 5 tweets
    ├── /repurpose-to-linkedin    → 2 LinkedIn posts
    ├── /repurpose-to-blog        → 1 blog article (ES + EN)
    ├── /repurpose-to-video-scripts → 3 short-form video scripts
    ├── /repurpose-to-newsletter  → 1 newsletter edition
    └── /repurpose-all            → all of the above + calendar
    ↓
OUTPUT FOLDER
    trochai-business/content/week-of-YYYY-MM-DD/
    ├── pillar.md            (source long-form post)
    ├── calendar.md          (daily checklist — what to post when)
    ├── tweets.md            (5 tweets + thread suggestion)
    ├── linkedin-1.md        (LinkedIn post 1)
    ├── linkedin-2.md        (LinkedIn post 2)
    ├── video-1.md           (video script 1 + captions)
    ├── video-2.md           (video script 2 + captions)
    ├── video-3.md           (video script 3 + captions)
    ├── newsletter.md        (newsletter edition + subject lines)
    ├── stories.md           (3 Instagram Story slides)
    ├── whatsapp-status.md   (2 WhatsApp status updates)
    └── blog-reference.md    (link to MDX files in trochai-landing)
    ↓
RENDER VIDEOS (trochai-videos Remotion pipeline — optional)
    ↓
POST MANUALLY (open calendar.md each morning, copy-paste, check off)
```

## Weekly Ritual

| Day | Activity | Time |
|-----|----------|------|
| **Monday** | Run `/repurpose-all` with this week's topic | 15 min |
| **Monday** | Skim generated files, tweak anything that sounds off | 15 min |
| **Tuesday** | Render video scripts with Remotion (if using) | 15 min |
| **Tue-Fri** | Open `calendar.md`, post what's listed, check it off | 10 min/day |
| **Weekend** | Review: what got engagement? Note for next week | 10 min |

**Total weekly time: ~1.5-2 hours for 25+ pieces of content.**

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
/repurpose-to-tweets        # just tweets
/repurpose-to-linkedin      # just LinkedIn posts
/repurpose-to-blog          # just blog article (ES + EN MDX files)
/repurpose-to-video-scripts # just video scripts
/repurpose-to-newsletter    # just newsletter
```

Each one saves to the same weekly folder.

### Posting Workflow

1. Open `trochai-business/content/week-of-YYYY-MM-DD/calendar.md`
2. It looks like this:
   ```
   ## Monday
   - [ ] **Instagram Reel:** video-1 → open `video-1.md`, use caption
   - [ ] **Tweet:** Tweet #1 from `tweets.md`
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

## Claude Code Commands

All commands are in `/.claude/commands/` at the monorepo root:

| Command | Output | Saves To |
|---------|--------|----------|
| `/repurpose-all` | Pillar + all formats + calendar | `content/week-of-*/` (full folder) |
| `/repurpose-to-tweets` | 5 standalone tweets | `tweets.md` |
| `/repurpose-to-linkedin` | 2 LinkedIn posts | `linkedin-1.md`, `linkedin-2.md` |
| `/repurpose-to-blog` | 1 MDX article (ES + EN) | `trochai-landing/content/blog/` |
| `/repurpose-to-video-scripts` | 3 video scripts | `video-1.md`, `video-2.md`, `video-3.md` |
| `/repurpose-to-newsletter` | 1 newsletter edition | `newsletter.md` |

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
| Instagram Reels | 9:16 video | 3 | `video-1.md`, `video-2.md`, `video-3.md` |
| TikTok | 9:16 video | 2 | Same scripts, different captions |
| YouTube Shorts | 9:16 video | 2 | Same renders |
| Twitter/X | Tweets | 5 | `tweets.md` |
| LinkedIn | Posts | 2 | `linkedin-1.md`, `linkedin-2.md` |
| trochai.com | Blog article | 1 | `trochai-landing/content/blog/` |
| Email | Newsletter | 1 | `newsletter.md` |
| Instagram Stories | Story slides | 3 | `stories.md` |
| WhatsApp Status | Updates | 2 | `whatsapp-status.md` |
| **Total** | | **~21** | |

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
- **Language:** Spanish (ustedeo) for Instagram/TikTok/Twitter. English for LinkedIn/blog.
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
