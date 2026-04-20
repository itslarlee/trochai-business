# Week 17 Content — April 20-26, 2026

**Theme:** Costa Rica fue pionera. Hoy la región nos está pasando por encima.

The week uses concrete 2025-2026 data (Propi's $4.2M seed + CR expansion plan, San Salvador +520% startup index, Pulppo 75% task reduction, CR's unlicensed corredor reality) to wake the sector up — without bashing CR.

## LinkedIn Daily Schedule

| Day | Content | Files | Bucket |
|-----|---------|-------|--------|
| Mon | Newsletter (Trochai Insights Sem. 17) carousel + LinkedIn Newsletter article | `linkedin/monday-newsletter/` | Authority |
| Tue | Propi $4.2M brandjack — infographic | `linkedin/tuesday-growth/` | Growth |
| Wed | 4 países, 4 niveles de PropTech — educational carousel (7 slides) | `linkedin/wednesday-authority/` | Authority |
| Thu | 0 licencias requeridas (CR vs región) — hot take infographic | `linkedin/thursday-growth/` | Growth |
| Fri | Misma arquitectura, contexto costarricense — product carousel (6 slides) | `linkedin/friday-conversion/` | Conversion |
| Sat | Anatomía de una desventaja — timeline carousel (9 slides) | `linkedin/saturday-authority/` | Authority |
| Sun | Soy costarricense, quiero que sigamos siendo pioneros — founder reflection | `linkedin/sunday-personal/` | Personal |

## Instagram (cross-post 3)

- Monday carousel → `instagram/carousel/monday/` (8 slides from newsletter)
- Wednesday carousel → `instagram/carousel/wednesday/` (7 slides framework)
- Saturday carousel → `instagram/carousel/saturday/` (9 slides timeline)
- Captions in `instagram/carousel/caption.txt`
- Reels scripts reference: `instagram/reels/video-scripts.txt`

## Blog

Already live at:
- ES: https://trochai.com/es/blog/trochai-insights-2026-s17
- EN: https://trochai.com/blog/trochai-insights-2026-s17

## Render Commands (if needed to re-render)

Infographics:
```bash
cd trochai-videos
npx remotion still LI-Card-Propi-W17 --output=out/linkedin/tue-w17.png --image-format=png
npx remotion still LI-Card-Unlicensed-W17 --output=out/linkedin/thu-w17.png --image-format=png
npx remotion still LI-Card-Founder-W17 --output=out/linkedin/sun-w17.png --image-format=png
```

Carousels (one-shot):
```bash
cd trochai-videos
bash scripts/render-w17-daily.sh
```

Newsletter carousel:
```bash
cd trochai-videos
npx tsx scripts/render-carousel.ts trochai-insights-2026-s17
```

## Video Scripts (optional Reels)

1. Propi-W17 — $4.2M expansion to CR (Tue companion)
2. Pulppo75-W17 — 75% automation (Fri companion)
3. ZeroLicense-W17 — 0 licenses required (Thu companion)

Scripts: `/video-1.md`, `/video-2.md`, `/video-3.md`. Compositions not yet built — requires new StatReveal-style .tsx files and voiceover generation.

## Posting Flow

1. **Monday 9:30am CR:** Publish LinkedIn Newsletter (article.md) + schedule the carousel post with caption.txt + cross-post carousel to Instagram.
2. **Tue 9:30am:** Schedule Propi infographic + caption.
3. **Wed 9:30am:** Schedule regional carousel + caption + IG cross-post.
4. **Thu 9:30am:** Schedule "0 licencias" hot-take infographic + caption.
5. **Fri 9:30am:** Schedule architecture carousel + caption — this is the final 50%-off-discount push.
6. **Sat 10:00am:** Schedule timeline deep-dive + caption + IG cross-post.
7. **Sun 10:00am:** Schedule founder reflection.

Use Metricool or LinkedIn native scheduler. All captions are in each day's `caption.txt`.

## Comment Flywheel (critical)

- Spend 30 min/day engaging on ICP accounts before posting.
- Reply to ALL comments on your post in the first hour.
- Target accounts this week: CCCBR members, Guanacaste/GAM agencies, regional PropTech accounts (Propi, Pulppo, Habi), Centroamérica RE influencers.

## Launch Discount Reminder

50% off first bill for subscriptions started before **April 30, 2026**.
- Friday post explicitly mentions the discount.
- After April 30, strip discount mentions from all future posts per memory.
