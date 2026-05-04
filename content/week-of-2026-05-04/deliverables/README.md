# Week 19 Content — May 4 – May 10, 2026

**Pillar:** Su inventario vive en cinco lugares. Su cliente lo nota antes que vos.
**Producto detrás:** Trochai Sites (lanzado 2026-04-29)
**Promo activa:** Mayo 1–31 — plan anual de Inbox = sitio web gratis (Offer A) | 50% off à-la-carte (Offer B)

> 🚨 **No-duplication rule:** every LinkedIn caption lives in its day's MD file (`../monday-newsletter.md`, `../tuesday-growth.md`, etc.) — NOT copied here. This README points to the source. If the caption needs a rewrite, edit ONE file (the day MD), not two. The `deliverables/` folder contains only what cannot be derived from source MDs: rendered visuals, the LinkedIn Newsletter article body, and this guide.

## LinkedIn Daily Schedule

| Day | Content | Files | Bucket | Personal repost? | Caption source |
|-----|---------|-------|--------|------------------|----------------|
| Mon May 4 | Newsletter carousel + LinkedIn Newsletter article | `linkedin/monday-newsletter/` | Authority | ✅ EN (`linkedin/monday-newsletter/personal-repost-en.txt`) | `../monday-newsletter.md` |
| Tue May 5 **AM** | Microsoft AI study brandjack — growth infographic | `linkedin/tuesday-growth/` | Growth | — | `../tuesday-growth.md` |
| Tue May 5 **PM** | **Hyperframes hero video** (cross-platform) | `hero-video/` | Authority/Hero | — | `hero-video/caption-linkedin.txt` (generated Tue AM) |
| Wed May 6 | Founder commentary on the month's data (no fabricated stories) | `linkedin/wednesday-personal/` | Personal | ✅ EN (`linkedin/wednesday-personal/personal-repost-en.txt`) | `../wednesday-personal.md` |
| Thu May 7 | "Los 5 lugares" — hot take carousel | `linkedin/thursday-growth/` | Growth | — | `../thursday-growth.md` |
| Fri May 8 | Sites mechanism + promo — product carousel | `linkedin/friday-conversion/` | Conversion | — | `../friday-conversion.md` |
| Sat May 9 | "4 preguntas antes de su sitio" — deep-dive carousel | `linkedin/saturday-authority/` | Authority | — | `../saturday-authority.md` |
| Sun May 10 | Weekly digest — neutral data summary, no sales | `linkedin/sunday-recap/` | Authority/Recap | — | `../sunday-recap.md` |

## Weekly Hero Video (Hyperframes — ships Tuesday PM)

One hand-crafted cross-platform video produced Mon PM → Tue AM, ships Tue 2pm across LinkedIn vertical / IG Reels / TikTok / YouTube Shorts.

- **Brief (this week):** `../weekly-hero-video.md`
- **Output drop zone:** `hero-video/`
- **Step-by-step process:** `trochai-videos/hyperframes/WEEKLY-HERO-VIDEO.md`
- **Format pick this week:** vertical 1080×1920 (IG Reels + TikTok lead the awareness gap)
- **Veo b-roll:** SKIPPED (founder direction 2026-05-04 — graphics + avatar carry the storyboard)

The hero video is a standalone asset and does NOT replace the Tue AM growth infographic.

## Instagram (cross-post 3)

- **Monday carousel** → `instagram/carousel/` (8 slides — same PNGs as Mon LinkedIn). Caption: `instagram/carousel/ig-caption.txt`
- **Tuesday hero video (PM)** → IG Reels (rendered MP4 from Hyperframes pipeline)
- **Thursday "5 lugares" carousel** → IG carousel (cross-post when Thu carousel renders — pending)

## Blog

Active after the Mon push:

- ES: https://trochai.com/es/blog/trochai-insights-2026-s19
- EN: https://trochai.com/blog/trochai-insights-2026-s19

The MDX file is at `trochai-landing/content/blog/{locale}/trochai-insights-2026-s19.mdx`. A copy of the ES article is in `linkedin/monday-newsletter/article.md` (used as the LinkedIn Newsletter body).

## Render Commands

```bash
cd trochai-videos

# Monday newsletter carousel (already rendered)
npx tsx scripts/render-carousel.ts trochai-insights-2026-s19
# Output: out/carousel/trochai-insights-2026-s19/ (8 PNGs + carousel.pdf + captions.md)

# Daily LinkedIn visuals (one-shot script)
bash scripts/render-w19-daily.sh
# Outputs:
#   out/linkedin/tue-w19.png, wed-w19.png
#   out/carousel/thu-five-places-w19/ (9 PNGs + PDF)
#   out/carousel/fri-sites-mechanism-w19/ (8 PNGs + PDF)
#   out/carousel/sat-sites-checklist-w19/ (7 PNGs + PDF)

# Hyperframes hero video (manual production Mon PM → Tue AM)
# See trochai-business/content/week-of-2026-05-04/weekly-hero-video.md
```

After `bash scripts/render-w19-daily.sh` finishes, copy outputs into the per-day `linkedin/{day}/` folders here:

```bash
cp trochai-videos/out/linkedin/tue-w19.png \
   trochai-business/content/week-of-2026-05-04/deliverables/linkedin/tuesday-growth/infographic.png

cp trochai-videos/out/linkedin/wed-w19.png \
   trochai-business/content/week-of-2026-05-04/deliverables/linkedin/wednesday-personal/infographic.png

cp -r trochai-videos/out/carousel/thu-five-places-w19/* \
   trochai-business/content/week-of-2026-05-04/deliverables/linkedin/thursday-growth/

cp -r trochai-videos/out/carousel/fri-sites-mechanism-w19/* \
   trochai-business/content/week-of-2026-05-04/deliverables/linkedin/friday-conversion/

cp -r trochai-videos/out/carousel/sat-sites-checklist-w19/* \
   trochai-business/content/week-of-2026-05-04/deliverables/linkedin/saturday-authority/

cp trochai-videos/out/linkedin/sun-w19.png \
   trochai-business/content/week-of-2026-05-04/deliverables/linkedin/sunday-recap/infographic.png
```

## Posting Flow (Costa Rica timezone, GMT-6)

| Day | Time | Action |
|-----|------|--------|
| Mon May 4 | 7:30 AM | Publish LinkedIn Newsletter (article body = `linkedin/monday-newsletter/article.md`) |
| Mon May 4 | 8:00 AM | Publish LinkedIn carousel post (caption from `../monday-newsletter.md` LinkedIn block) |
| Mon May 4 | 8:30 AM | Cross-post IG carousel (`instagram/carousel/`) with caption `instagram/carousel/ig-caption.txt` |
| Mon May 4 | 9:00 AM | Repost from founder personal LinkedIn (caption from `linkedin/monday-newsletter/personal-repost-en.txt`, link to ES original) |
| Mon May 4 | PM | **Hyperframes hero video production starts** (per `../weekly-hero-video.md`) |
| Tue May 5 | 7:30–9:00 AM | Schedule "Microsoft AI study brandjack" infographic (caption from `../tuesday-growth.md`) |
| Tue May 5 | 9:00–10:00 AM | **Hyperframes render finishes**. Copy MP4 + write platform captions into `hero-video/` |
| Tue May 5 | 2:00 PM | LinkedIn vertical: hero video (caption from `hero-video/caption-linkedin.txt`) |
| Tue May 5 | 2:30 PM | IG Reels: hero video (caption from `hero-video/caption-ig.txt`) |
| Tue May 5 | 3:00 PM | TikTok: hero video (caption from `hero-video/caption-tiktok.txt`) |
| Tue May 5 | 4:00 PM | YouTube Shorts: hero video (long-form caption) |
| Wed May 6 | 12:00 PM | Founder reflection on Trochai company page (caption from `../wednesday-personal.md`) |
| Wed May 6 | 12:30 PM | Repost from founder personal LinkedIn (caption from `linkedin/wednesday-personal/personal-repost-en.txt`) |
| Thu May 7 | 7:30–9:00 AM | "Los 5 lugares" carousel (caption from `../thursday-growth.md`); cross-post IG carousel |
| Fri May 8 | 7:30–9:00 AM | Sites mechanism carousel + promo CTA (caption from `../friday-conversion.md`) |
| Sat May 9 | 9:00–10:00 AM | "4 preguntas" deep-dive carousel (caption from `../saturday-authority.md`) |
| Sun May 10 | 10:00–11:00 AM | Weekly digest infographic (caption from `../sunday-recap.md`) — neutral, no sales |

## Comment Flywheel (critical, 30 min/day before posting)

- 30 min/day engaging on ICP accounts BEFORE posting.
- Reply to every comment in the first hour — especially anything asking about the promo or Sites mechanism.
- DM playbook: anyone who asks "¿cuánto cuesta?" or "¿en cuánto tiempo se hace?" → DM with personalized Loom of the Sites demo + link to the promo form.

## May Promo — Mention Rules

- **Mon, Tue, Thu, Fri, Sat:** Can mention the May promo (Offer A or B).
- **Wed (founder):** **NO promo mention.** Wed founder is human voice, not sales. Product mention OK; discount mention NOT OK.
- **Fri (Conversion):** Full promo CTA with Offer A first, Offer B as fallback. Direct link to demo form.
- **Sun (recap):** **NO promo mention.** Sunday is a neutral data digest — closing question is for reflection, not click.

## ⚠️ Founder content rule (Wed) — added 2026-05-04

Wednesday founder posts are **opinion grounded in real data**, NOT fabricated experience. The previous draft of this week's Wed post invented "20+ discovery calls with one specific question" — that didn't actually happen and was rewritten. Going forward (per skill update on 2026-05-04):

- ✅ Allowed: opinion on a published study, summary of what stands out across the week's data, "if I were running an agency today, the question I'd be asking is..."
- ❌ Forbidden: invented discovery calls, made-up customer quotes, specific numbers about meetings/conversations that didn't happen, anecdotes presented as the founder's lived experience when they weren't.

## ⚠️ Fact corrections — applied 2026-05-04

The first draft of this week shipped with several inaccuracies that were corrected after the user fact-checked:

- **52% client experience benefit** → **48%** (Microsoft article actually says 48%, not 52%; verified directly)
- **"Lidera junto a Colombia, Ecuador, RD"** → removed (Tico Times July 2025 only names CR; the others not mentioned)
- **"1% de líderes siente dominio total / Trycore"** → removed (not in cited Tico Times Sept 2025 article); replaced with **WEF "1 in 6 reskill by 2027"** which IS in the article
- **53% / 78% framed as recent** → tagged as **Microsoft 2023 (vía DPL News)** since the source article is from April 2023
- **"futuro virtual tour, futura predicción de precios"** as Trochai surfaces → removed (those are macro PropTech trends, not Trochai-shipped features)

The narrative wedge ("inventory in 5 places, real estate is the architectural exception") survives all corrections — the data is still solid, just dated correctly.

## Metrics This Week

- **LinkedIn organic reach:** impressions accumulated Mon–Sat. Baseline = Wk 18 (pure Coexistence). Target = parity or +10%.
- **Hand-raisers:** comments + DMs about Trochai Sites or May promo.
- **Demos booked:** attributable to this week's content (UTM or direct ask in discovery).
- **Offer A vs. Offer B split:** how many prospects ask for "annual Inbox = free site" vs. "50% off à-la-carte". Indicates bundle vs. point appetite.
- **Saves on the "5 lugares" carousel (Thu):** 360 Brew signal — predicts next week's reach.
