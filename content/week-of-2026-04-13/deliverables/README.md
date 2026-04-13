# Week 16 Content — April 13-19, 2026

## LinkedIn Daily Schedule

| Day | Content | Files | Bucket |
|-----|---------|-------|--------|
| Mon | Newsletter carousel + LinkedIn Newsletter article | `linkedin/monday-newsletter/` | Authority |
| Tue | WhatsApp "5 devices, 0 coordination" — infographic | `linkedin/tuesday-growth/` | Growth |
| Wed | "5 signs WhatsApp is costing you leads" — educational carousel | `linkedin/wednesday-authority/` | Authority |
| Thu | "Agencies don't need a CRM" — hot take infographic | `linkedin/thursday-growth/` | Growth |
| Fri | Before vs. After — WhatsApp Business to pro inbox carousel | `linkedin/friday-conversion/` | Conversion |
| Sat | "Anatomy of a lost lead" — deep-dive timeline carousel | `linkedin/saturday-authority/` | Authority |
| Sun | "Building for an invisible problem" — founder reflection | `linkedin/sunday-personal/` | Personal |

## Visual Rendering Commands

Infographics (Tue, Thu, Sun):
```bash
cd trochai-videos
npx remotion still LI-Card-WA-Broken-W16 --output=out/linkedin/tue-w16.png --image-format=png
npx remotion still LI-Card-No-CRM-W16 --output=out/linkedin/thu-w16.png --image-format=png
npx remotion still LI-Card-Invisible-W16 --output=out/linkedin/sun-w16.png --image-format=png
```

Carousels (Wed, Fri, Sat):
```bash
# Wednesday — 5 signs
for i in Cover Slide-1 Slide-2 Slide-3 Slide-4 Slide-5 CTA; do
  npx remotion still "Pillar-WA-Signs-W16-$i" --output="out/linkedin/wed-signs-$i.png" --image-format=png
done
npx tsx scripts/carousel-to-pdf.ts wed-signs-w16

# Friday — Before/After
for i in Cover Slide-1 Slide-2 Slide-3 CTA; do
  npx remotion still "Pillar-Before-After-W16-$i" --output="out/linkedin/fri-ba-$i.png" --image-format=png
done
npx tsx scripts/carousel-to-pdf.ts fri-ba-w16

# Saturday — Lead Anatomy
for i in Cover Slide-1 Slide-2 Slide-3 Slide-4 Slide-5 Slide-6 CTA; do
  npx remotion still "Pillar-Lead-Anatomy-W16-$i" --output="out/linkedin/sat-anatomy-$i.png" --image-format=png
done
npx tsx scripts/carousel-to-pdf.ts sat-anatomy-w16
```

## Instagram (cross-post 2-3)

- Monday carousel → Instagram carousel (slides from `linkedin/monday-newsletter/`)
- Wednesday carousel → Instagram carousel (5-signs framework — saveable)
- Saturday carousel → Instagram carousel (lead anatomy timeline — visual story)

## Blog

Already live at:
- ES: trochai.com/es/blog/trochai-insights-2026-s16
- EN: trochai.com/blog/trochai-insights-2026-s16

## Comment Flywheel

Spend 30 min/day engaging on ICP accounts before posting. Reply to all comments on your posts.
