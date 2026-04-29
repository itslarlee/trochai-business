# Trochai Sites — Assets Needed (per template)

> Internal ops doc. What the founder needs to provide / commission / generate so each template demo can ship polished. Cross-references the AI tooling stack in `TROCHAI-SITES-AI-TOOLING.md` (which is $0 if disciplined).
>
> **Last updated:** 2026-04-29.

---

## Quick reference — total asset budget

| Template | Hours of asset work | Tooling cost | Status |
|---|---|---|---|
| Editorial (Verde Inmobiliaria) | ~3 hrs (mostly photo curation) | $0 | **Demo data complete** — using Unsplash CC0 placeholders. Real photos optional. |
| Maximalist (Atelier Inmobiliario) | ~6 hrs (AI atmospherics + photo curation) | $0 | Template scaffold needed; assets after |
| Boutique (Casa Sabana) | ~8 hrs (photo essay + floorplan SVGs + AI lifestyle) | $0–50 (optional Veras trial) | Template scaffold needed; assets after |
| Cinematic Full R3F (Origen) | ~12 hrs assets + ~90 hrs build | $0 (free stack) or up to $150 if pushing quality | Template scaffold needed; building model + cinematic clips after |

---

## Template 1 — Agency Editorial (Verde Inmobiliaria)

**Demo URL:** `demo-verde.sitios.trochai.com`
**Status:** Polished. Demo data already populated with 12 properties + 4 projects + 3 blog posts using Unsplash CC0 hot-linked images.

### Optional polish (nice-to-have, not required to ship)

| # | Asset | Purpose | Where it goes | Source |
|---|---|---|---|---|
| 1 | Logo for Verde Inmobiliaria | Navbar + footer + favicon | `public/logo.svg` + `public/favicon.ico` | Generate with Midjourney / Bing Image Creator (DALL-E 3) — prompt: *"minimalist real-estate logo, leaf icon, sage green, modern serif wordmark 'Verde Inmobiliaria'"* |
| 2 | Hero photo (above the fold) | Replaces gradient placeholder | `public/hero.jpg` (1920×1080, AVIF preferred) | Unsplash search "Costa Rica modern home" or Bing Image Creator: *"contemporary CR villa exterior, dusk, warm lighting, cinematic"* |
| 3 | "About" / agency story photo | If adding `/about` page later | `public/about-team.jpg` | Stock or commissioned |

**Verdict:** Editorial is shippable today as-is. The Unsplash placeholders look real on the demo. Logo is the only "obviously missing" piece, and even a text-based wordmark (currently `<span>Verde Inmobiliaria</span>`) reads fine.

---

## Template 2 — Agency Maximalist (Atelier Inmobiliario)

**Demo URL:** `demo-atelier.sitios.trochai.com`
**Status:** Template scaffold not built yet. Research output documents the full design system (Fraunces + Inter, dark warm palette, masked line reveal hero, sticky photo essay).

### Required assets

| # | Asset | Purpose | Where it goes | Source |
|---|---|---|---|---|
| 1 | Hero atmospheric image (1) | Full-bleed background, dark mood | `public/hero/atmospheric.avif` (1920×1080, AVIF) | **FLUX.1 [schnell] via Together AI** (free) — prompt: *"abstract dark architectural atmosphere, brass light through curtain wall, moody cinematic, ultra-wide"* |
| 2 | Featured listing photos (8) | Asymmetric grid section | `public/featured/01-08.avif` (varied dimensions, see grid spec) | Unsplash CC0 architectural collection OR commissioned photos when client signs |
| 3 | Numbers section background | Full-bleed dark texture | `public/textures/grain-dark.avif` (1920×1080) | FLUX schnell — *"subtle film grain on near-black, warm cast"* |
| 4 | Agent portraits (4-6) | Meet-the-team grid | `public/team/01-06.avif` (1200×1500, 4:5) | Unsplash CC0 portraits OR generated via FLUX (with caveat: AI portraits read as fake to careful viewers) |
| 5 | Logo + wordmark | Navbar + footer | `public/logo.svg` + `public/wordmark.svg` | Midjourney / Bing — prompt: *"editorial serif wordmark 'Atelier Inmobiliario', monogram 'A', warm cream on near-black, premium"* |
| 6 | Blog cover images (3) | Editorial card thumbnails | `public/blog/01-03.avif` (1200×800) | FLUX schnell or Unsplash |

**Total time to source:** ~4 hours if AI-generating. Total cost: $0 with FLUX schnell.

**Note:** Portraits are the riskiest AI assets. For the demo, Unsplash CC0 portraits are safer than AI-generated. When a real client signs, commission a photographer ($300-500 for 4-6 agent portraits is standard in CR).

---

## Template 3 — Development Boutique (Casa Sabana)

**Demo URL:** `demo-casa-sabana.sitios.trochai.com`
**Status:** Template scaffold not built yet. Research output documents IA, narrative scroll patterns, floorplan selector UX.

### Required assets

| # | Asset | Purpose | Where it goes | Source |
|---|---|---|---|---|
| 1 | Hero exterior render (1) | Full-bleed hero image | `public/hero/exterior.avif` (1920×1080) | **Veras 15-day trial** (~30 renders, CR architecture-specific). Or Hyper3D Rodin from sketch + render in Blender. Prompt for Veras: *"single-story residential complex, gated community, tropical Costa Rica, cream stucco, terracotta roof, lush gardens, dusk lighting"* |
| 2 | Photo essay set (5-7 scenes) | Sticky narrative scroll sections | `public/essay/01-07.avif` (1920×1080) | Veras + FLUX schnell mix. One per chapter: arrival, architecture, community, amenities, lifestyle, location, finishes |
| 3 | Floorplan SVGs (3) | Unit-type selector | `public/floorplans/2br.svg`, `3br.svg`, `4br.svg` (vector, ~5-30KB each) | **Hand-draw in Figma** (1-2 hrs) — simple architectural lines, no detail; must be SVG (not raster) to look sharp at any size. Reference: real estate floorplan SVGs on Behance |
| 4 | Amenity icons (8-12) | Amenities grid | `public/icons/pool.svg`, `gym.svg`, etc. | **Lucide icons** (already in deps) or hand-drawn SVG. No license cost. |
| 5 | Gallery / lookbook (12-30) | Lookbook section | `public/gallery/01-30.avif` | Veras + Unsplash + FLUX mix. Mix interior + exterior + lifestyle |
| 6 | Location map / neighborhood graphic | Location section | `public/map/sabana-context.svg` | Hand-draw in Figma OR use Mapbox static export with custom style |
| 7 | Logo + wordmark | Navbar + footer | `public/logo.svg` | Midjourney — *"hand-drawn boutique residential logo, single line, terracotta on cream, organic, refined"* |

**Total time:** ~6-8 hours.
**Cost:** Veras trial = $0 (15 days, 30 renders). Need to run Veras burn within 15 days of starting Boutique build.

**Critical note:** The floorplan SVGs are the most-asked-about asset and the biggest differentiator vs. WordPress competitors. Don't skip these. Use a real floorplan reference from any small CR development as visual inspiration, then hand-redraw simplified SVG.

---

## Template 4 — Development Cinematic Full R3F (Origen)

**Demo URL:** `demo-origen.sitios.trochai.com`
**Status:** Template scaffold not built yet. R3F + GSAP + Lenis stack documented. This is the heaviest asset workload.

### Required assets

| # | Asset | Purpose | Where it goes | Source / cost |
|---|---|---|---|---|
| 1 | **Building 3D model (.glb)** | The hero. Real-time WebGL scene | `public/models/building.glb` (compressed via gltf-transform, target 4-8MB) | Three options: (a) **Sketchfab CC0** "modern residential building" — fastest, free, generic. (b) **Hyper3D Rodin** image-to-3D from a Veras-generated render — better quality, free trial. (c) **Blender block-out** — 30 min for a stack-of-cubes that reads as a building from far away |
| 2 | Building 3D model — mobile fallback | Lower-poly version for mobile | `public/models/building-low.glb` (~1.5-3MB) | `gltf-transform simplify` from #1 (`--ratio 0.4`) |
| 3 | HDRI environment | Lighting realism | `public/hdri/studio_warm_2k.hdr` (~2-4MB) | **Poly Haven** ([polyhaven.com/hdris](https://polyhaven.com/hdris)) — CC0, free. Search "studio" or "outdoor sunset". Resize to 2k for desktop, 1k for mobile |
| 4 | Hero static AVIF fallback | For `prefers-reduced-motion` users + low-end GPU detection | `public/hero/static.avif` (1920×1080) | Render the same Blender scene as a still and export AVIF. Or use #1's source render |
| 5 | Cinematic video clips (3-5) | Scroll-driven sequences (sunlight on facade, lobby reveal, amenity sweep) | `public/video/01-05.mp4` (8-second loops, H.265, ~2-5MB each) | **Google Veo 3.1 via Flow** (free, 50 credits/day, watermarked). Strip watermark via Runway free tier (25s) OR commit to LTX-2.3 local install for clean output |
| 6 | Lobby / amenity render set (8) | Inner section heroes | `public/renders/lobby-01.avif`, etc. | Veras (architecture-specific) + FLUX schnell mix |
| 7 | Floorplan set (6) | Unit-type selector | `public/floorplans/*.svg` | Hand-draw in Figma, same as Boutique |
| 8 | Logo + wordmark | Navbar + footer | `public/logo.svg` | Midjourney — *"luxury developer monogram 'O' + wordmark 'Origen', minimal, brass on near-black"* |

**Total time:** ~12 hours of asset work + ~90 hours of R3F engineering.
**Cost:** $0 if disciplined ($0 stack: Sketchfab + Hyper3D Rodin trial + Veras trial + Veo Flow + LTX-2.3 local). Realistic upgrade to ~$50-150 if pushing for production-clean watermark-free clips and Rodin paid for hero objects.

### Critical R3F-specific notes

- **The building model is non-negotiable.** Without a 3D model, there is no Cinematic template. Start with Sketchfab CC0 to unblock everything else, upgrade later.
- **HDRI must be self-hosted.** drei's `Environment preset="*"` hits a Google CDN that fails ~5% of the time. Use `<Environment files="/hdri/studio_warm_2k.hdr" />`.
- **Compress everything via gltf-transform CLI** (`npm install -g @gltf-transform/cli`). Raw uncompressed Blender exports are 50-100MB; properly compressed: 4-8MB. The pipeline is: Draco geometry compression → KTX2 texture compression → simplify for mobile fallback. Recipe in `TROCHAI-SITES-AI-TOOLING.md`.
- **Reduced-motion fallback is required** — about 8-15% of users have `prefers-reduced-motion: reduce` set. Without a static fallback, those users see a blank canvas. The fallback AVIF (#4 above) is mandatory.

---

## What the founder needs to do, in order

### Now (before any template polish work)

1. **Generate the Verde Inmobiliaria logo** (15 min via Midjourney / Bing). Drop into `_template/public/logo.svg`. Editorial demo is ready to deploy.
2. **Set up a Together AI account** (5 min — for FLUX schnell). $1 starter credit, no CC.
3. **Set up a Google account budget cap** in Cloud Console — $10/mo cap, alerts at $1, $5, $10. Prevents another Nano Banana surprise.

### When ready to build Maximalist (1-2 days of work)

1. Generate hero atmospheric (15 min, FLUX schnell)
2. Source 8 listing photos from Unsplash CC0 (1 hr curation)
3. Generate Atelier logo + wordmark (15 min)
4. Build the template (~30-40 hrs solo, per Maximalist research)

### When ready to build Boutique (2-3 days of work)

1. **Activate Veras 15-day trial** — burn 25-30 renders for Boutique + Cinematic in the same window (don't waste the clock)
2. Generate hero exterior + photo essay scenes (3 hrs in Veras)
3. Hand-draw floorplan SVGs in Figma (1-2 hrs)
4. Build the template (~40-50 hrs solo)

### When ready to build Cinematic R3F (5-7 days of work)

1. Source / generate building model (Sketchfab CC0 to unblock; upgrade later)
2. Compress via gltf-transform CLI (30 min)
3. Source HDRI from Poly Haven (10 min)
4. Generate cinematic video clips with Veo 3.1 (1-2 hrs to find good takes)
5. Render static AVIF fallback (15 min from Blender scene)
6. Build the R3F template (~80-100 hrs solo, per Cinematic research)

---

## Cross-references

- **AI tooling stack (the $0 path):** `trochai-business/TROCHAI-SITES-AI-TOOLING.md`
- **Pricing (what each template lists for):** `trochai-business/TROCHAI-SITES-PRICING.md`
- **Repository:** `trochai-client-sites/` — `_template/` is Editorial baseline; the other three template directories don't exist yet
- **Landing page:** `trochai-landing/src/app/[locale]/sitios/page.tsx` — already renders all four templates as cards (live demo for Editorial, "Disponible mayo 2026" for the rest)
