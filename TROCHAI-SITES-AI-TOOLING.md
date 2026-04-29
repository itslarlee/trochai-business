# Trochai Sites — AI Tooling Stack (Internal Ops Reference)

> Internal operations doc for producing visual assets (images, video, 3D, architectural renders) for Trochai Sites templates and demos. **Do not surface this to clients.** It documents the founder's working stack, free-tier limits, and the realistic paid floor when free isn't enough.
>
> **Last updated:** 2026-04-29 — initial research after $45 Nano Banana Pro API surprise.

---

## 1. The 5-tool default stack ($0 cost, fully commercial-clean for the founder's use case)

| Need | Tool | Free tier | Commercial use |
|---|---|---|---|
| Hero / lifestyle / interior images | **FLUX.1 [schnell]** via Together AI or Pollinations | Together: $1 starter credit, no CC. Pollinations: no signup. | **Yes — Apache 2.0, fully commercial** |
| Hero with crisp text / brand polish | **Bing Image Creator (DALL-E 3 / GPT-4o)** | 15 fast generations/day per Microsoft account | **Yes** per Microsoft ToS |
| Architecture / interior specifically | **Veras 15-day trial** (30 renders, Nano Banana 2 underneath) → then **local SDXL + architecture LoRAs** | Veras: 30 renders / 15 days. SD: unlimited local. | Veras: paid output is commercial. SD: CreativeML OpenRAIL-M permits it. |
| Cinematic 3–8s video clips | **Google Veo 3.1 via Google Flow** + **Hailuo MiniMax** as backup | Veo 3.1: **50 daily AI credits ≈ 12 clips/day**, 8s, 720p, "Made with Veo" watermark. Hailuo: 3/day. | Veo free is "personal use" — see §5 for client-deliverable nuance. |
| 3D models for Three.js (.glb) | **Sketchfab CC0 buildings** + **Hyper3D Rodin** trial credits | Sketchfab: unlimited CC0 downloads. Rodin: trial credits. | **Yes — Rodin commercial on every tier including trial; Sketchfab CC0 unrestricted** |

**Total cost to produce the first complete Cinematic demo from scratch: $0.**

---

## 2. The Nano Banana / Gemini billing trap

The trap: Google has **two surfaces** that both say "Gemini" but bill differently.

| Surface | Free? | What got billed |
|---|---|---|
| Google AI Studio web UI (`aistudio.google.com`) | Yes — 2 Nano Banana Pro images/day, watermarked, 1MP cap. No card needed. | — |
| Gemini API (programmatic, with API key) | `gemini-2.5-flash-image` (regular Nano Banana) has ~500/day free tier. **`gemini-3-pro-image-preview` (Nano Banana Pro) has zero free API quota** and requires Tier 1 billing. | This is what charged $45. |

### Safe usage going forward

1. **In Google Cloud Console → Billing**, set a monthly **budget cap with email alerts at $1, $5, $10**. This is the only hard guard rail Google offers.
2. **Use AI Studio's web UI for Nano Banana Pro**, not the API. Free, watermarked, 2/day — fine for ideation, not production.
3. **Use the API only for `gemini-2.5-flash-image` (regular Nano Banana)** which has the ~500/day free tier.
4. **Never call `gemini-3-pro-image-preview` from the API** unless you've explicitly accepted you're paying $0.134/image (1K) or $0.24/image (4K).
5. **Disable the "Generative Language API"** in Cloud Console when not actively building — re-enable when you are.

References: [Gemini API Rate Limits](https://ai.google.dev/gemini-api/docs/rate-limits) · [Gemini API Billing](https://ai.google.dev/gemini-api/docs/billing).

---

## 3. Detailed comparisons

### 3a. Image generation

| Tool | Quality for RE/architecture | Free tier | Paid ramp | Commercial on free |
|---|---|---|---|---|
| **FLUX.1 [schnell]** (open source) | Strong atmospherics, lifestyle, exteriors. Slightly weaker text than Pro variants. **Best free baseline for RE.** | Unlimited locally; or hosted free via Together AI ($1 starter credit, no CC) and Pollinations (no signup). | FLUX.1 Pro ~$0.04/image via fal.ai/Replicate. | **Yes — Apache 2.0, fully commercial** |
| **FLUX.1 [dev]** | Higher quality than schnell. | Free local — but **non-commercial license**. | Commercial license: bfl.ai/licensing. | **No** without paid license. **Skip.** |
| **Bing Image Creator (DALL-E 3 + GPT-4o)** | Photoreal, excellent text rendering, weaker than FLUX/SDXL on architectural materials. | 15 fast/day + 200 prompt cap, slow generations after. | Copilot Pro $20/mo for unlimited fast. | **Yes** per Microsoft ToS |
| **ChatGPT Free (GPT Image 1.5)** | Excellent prompt adherence, weaker on architectural realism. | 2–3 images/day, 24h reset. Painfully tight. | Plus $20/mo (~50 images/3h). | Allowed per OpenAI ToS |
| **Google AI Studio / Nano Banana Pro** | Top-tier photorealism for "moody atmospheric" vibe. | 2 Pro/day in web UI (1MP, watermarked). ~500/day Nano Banana (regular) on API free tier. | $0.134–$0.24/image for Pro on API. | Web UI watermark restricts pro use |
| **Leonardo.ai** | Decent SDXL-based. | 150 tokens/day; commercial on free **but all free creations are public**. | Apprentice $12/mo. | Yes (with public-gallery caveat) |
| **Ideogram** | Best-in-class text rendering on signage. | 10 prompts/day; **public + non-commercial on free**. | Basic $7/mo for private + commercial. | **No** on free. **Skip for client work.** |
| **Krea.ai** | Realtime canvas — best for sketch-to-render iteration. | 100 compute units/day, no CC. **Non-commercial on free.** | Basic $9/mo. | **No** on free |
| **Recraft** | Strong vectors + branded graphics, weaker photoreal. | 30–50 daily credits; **no commercial rights, public on free**. | Basic $10/mo. | **No** on free |
| **Adobe Firefly** | Solid photoreal, fully indemnified. | 25 generative credits/mo; **personal use only on free**, watermarked. | Standard $9.99/mo for 2K credits + commercial. | **No** on free |
| **Stable Diffusion XL / SD3 (Forge or ComfyUI, local)** | With architectural LoRAs from CivitAI + ControlNet, **secret weapon** for unlimited interior/exterior renders. RE-specific checkpoints exist. | Unlimited local; one-time hardware cost. | $0 ongoing. | **Yes** under CreativeML OpenRAIL-M |
| **Midjourney** | Industry-best aesthetics. | No real free tier. | Basic $10/mo. | Paid only |

**Recommended image stack:** **FLUX.1 [schnell]** (default workhorse, scriptable) + **Bing Image Creator** (when you need DALL-E/GPT-4o for hero text/brand shots). Skip Leonardo / Ideogram / Krea / Recraft free tiers — public-gallery + non-commercial restrictions are client-work landmines.

### 3b. Video generation

| Tool | Quality | Free tier | Paid ramp | Commercial on free |
|---|---|---|---|---|
| **Google Veo 3.1 (via Google Flow)** | Best free option in 2026. Native audio. 720p free. | **50 daily AI credits ≈ 12 clips/day**, 8s max, 720p, "Made with Veo" watermark. Free for all Google account holders April 2026. | Google AI Pro $20/mo. | **Personal use only** on free per Google's wording — watermark must remain |
| **Runway Gen-4 / Gen-3** | Industry standard, best motion control. | **125 one-time credits ≈ 25s** of Gen-4 Turbo, 720p, watermark. **Does not refill.** | Standard $12–15/mo for 625 credits. | Free is essentially trial |
| **Hailuo MiniMax (Hailuo 2.3)** | Surprisingly good motion + character consistency. | **3 watermarked 720p 6s videos/day** + 200–500 starter credits. | $9.99/mo+. | Watermarked free |
| **Kling 2.x** | Cinematic motion, slow camera moves are excellent. | **66 credits/day ≈ 1–2 short clips**, watermarked. | $6.99/mo+. | Watermarked |
| **Pika 2.5** | Stylized, weaker realism. | **80 monthly credits ≈ 6 clips**, 480p, watermarked, image-to-video only. | Basic $10/mo. | Watermarked |
| **Luma Dream Machine (Ray)** | Excellent fluid motion. | **30 generations/mo**, watermarked, **commercial NOT allowed on free**. | Standard ~$29.99/mo. | **No** on free |
| **LTX-Video / LTX-2.3** (open source) | LTX-2.3 claims "on par with Veo 3" output, 4K@50fps. | Unlimited local; **free for companies under $10M ARR (Trochai qualifies)**. | License fee >$10M ARR. | **Yes** under that bar |
| **Stable Video Diffusion** | Older now; still works for short loops. | Unlimited local, 8–12 GB VRAM. | $0. | Yes under OpenRAIL-M |
| **Wan 2.2 / 2.5** (Alibaba, open source) | 2.5 is Apache 2.0, 720p, audio-sync. Strong open competitor to Veo. | Unlimited local. | Cloud API on Atlas/fal/etc. | **Yes** under Apache 2.0 |

**Recommended video stack:** **Veo 3.1 via Google Flow** for hero clips (best free quality, watermark is the cost). If watermark is a deal-breaker for a paying Cinematic client, install **LTX-2.3 locally** (Apache 2.0, free under $10M ARR, native 4K). **Hailuo** as creative B-roll source.

### 3c. Architecture-specific tools

| Tool | Strength | Free tier | Paid |
|---|---|---|---|
| **Veras (EvolveLAB / Chaos)** | Native plugin in Revit/SketchUp/Forma/Vectorworks/Rhino. Designed for sketch→render. Now runs on Nano Banana 2. | **30 renders / 15-day trial**, 1024×1024, no batch. | $20–40/mo seat |
| **ArkoAI** | Plugin to SketchUp/Rhino/Revit with active-view rendering. | 30 free renders. | $29/mo unlimited |
| **PromeAI** | Sketch-to-render and 100+ style presets. | Watermarked, low-res, blurry on free; **no download on free**. | $19/mo |
| **Maket.ai** | Floor plan generation, not photoreal renders. | 50 one-time credits, single-story. | Pro $20/mo, 300 credits |

**Recommendation:** Burn the **Veras 15-day trial strategically** — generate 25–30 hero renders for 5–10 prospect mockups all in the same fortnight, then drop to local SDXL + interior LoRAs.

### 3d. 3D models for Three.js (.glb)

| Tool | Quality | Free tier | Commercial on free | glb? | Local? |
|---|---|---|---|---|---|
| **Hyper3D Rodin Gen-2** | Best image-to-3D quality available, production-ready. | Trial credits. | **Yes — full commercial rights on every tier including free trial** | Yes (FBX/GLB/OBJ) | No |
| **Tripo3D** | Good quality, fast. | 300 credits/mo (~24–30 models). | **No — CC BY 4.0, attribution required** | Yes (GLB) | No |
| **Meshy AI v6** | Solid, with PBR textures. | 100 credits/mo (~5 generations). | **No — CC BY attribution required on free** | Yes | No |
| **Hunyuan3D-2.1 / 2.5** (Tencent, open source) | Production-grade per Tencent's claims; PBR materials. | Unlimited local. | **Yes — Apache 2.0** | Yes | **Yes** — 6 GB VRAM (shape) / 16 GB (shape + texture) |
| **Sketchfab CC0/CC-BY models** | Pre-made buildings, hand-modeled. | Unlimited free downloads. | Yes (CC0 unrestricted; CC-BY requires attribution) | Yes (FBX/GLB/DAE) | Download local |
| **BlenderKit** | Pre-made; Blender ecosystem. | Limited free assets, low-poly. | Mixed. | Via Blender export | Local |

**Recommendation:** **Sketchfab CC0 buildings as base** + **Hyper3D Rodin** for 1–2 custom hero objects (commercial-clean even on the free trial). For unlimited custom 3D: install **Hunyuan3D-2.1 locally**.

---

## 4. Recommended first-pass workflow for one Cinematic demo

Goal: produce all visual assets for one prospect-facing demo in **one day, $0 cost, fully commercial-clean**.

**Step 1 — Heroes (60 min):**
- Generate 6 candidates per shot in **FLUX.1 [schnell]** via Together AI: hero exterior, drone angle, jungle/beach/mountain context, interior wide.
- Resolution: 1536×1024 minimum, upscale via local SDXL Tiled or Topaz trial if needed.
- *Backup if FLUX feel is wrong:* Bing Image Creator for the brand-text hero.

**Step 2 — Interior renders, RE-specific (90 min):**
- Burn the **Veras 15-day trial** *now* if shipping demos this fortnight: 25–30 hero interior renders across multiple prospect mockups in the same window.
- After trial expires: **local SDXL Forge + interior architecture LoRAs** from CivitAI ("interior architecture", "modern villa", "Costa Rica architecture").

**Step 3 — Scroll-scrubbed cinematic clips (60 min):**
- **Veo 3.1 via Google Flow** (50 credits/day ≈ 12 clips). Generate 4–6 candidates per shot at 720p, 8 seconds.
- Watermark caveat: "Made with Veo" sits in the corner. For a $13.5K Cinematic deliverable this is probably unacceptable — see §5.
- Backup: **Hailuo MiniMax** (3/day) for B-roll variety.
- Post: convert MP4 to looping H.265/MP4 for `<video>` scroll-scrub. Trim to 3–5s — lands better than 8s for parallax.

**Step 4 — 3D building scene (only if Three.js, 90 min):**
- Source 1 base building from **Sketchfab CC0** "modern residential building .glb".
- Generate 1–2 custom hero objects on **Hyper3D Rodin** free trial (commercial-clean).
- Drop into Three.js scene; bake lighting, set camera path, ship.

**Total time: ~5 hours. Total spend: $0.**

**Commercial-use legal note:** "Personal use only" on Veo's free tier and the Microsoft Bing terms are the murky ones. Microsoft has explicitly allowed commercial use of Bing Image Creator output. Veo's free tier is officially personal/Pro tier — if the demo goes on a paying client's website, either keep it watermarked, upgrade to AI Pro for that month ($20), or replace those clips with local **LTX-2.3** output (Apache 2.0, fully commercial under Trochai's revenue tier). **FLUX.1 [schnell], Hunyuan3D, Rodin trial, and CC0 Sketchfab assets are unambiguously commercial-clean.** Stick to those four for hard guarantees.

---

## 5. Where the free tier isn't enough — paid floor for a $13,500 Cinematic client

| Need | Free option's gap | Cheapest paid path |
|---|---|---|
| Watermark-free 8s clips at 1080p+ | Veo 3.1 watermark; Runway free is one-time 25s | Google AI Pro $20/mo (one month per project) **or** local LTX-2.3 (Apache 2.0, free at scale). **Local LTX-2.3 is the real long-term answer.** |
| High-fidelity bespoke architecture renders | Veras trial expires after 30 renders / 15 days | Veras Web $20/mo, or commit to local SDXL + architecture LoRAs (no ongoing cost) |
| Brand-tier text-on-image hero (specific typography) | DALL-E 3 / Ideogram free have public-gallery / 2-3/day caps | ChatGPT Plus $20/mo for project duration, or Ideogram Basic $7/mo |
| Production-clean 3D assets (clean topology, textures) | Rodin trial credits run out, Hunyuan3D needs operator skill | Rodin paid ~$15/mo for a project, or hire a 3D pass on Fiverr ~$50–200/asset |

**Realistic paid floor for a $13,500 Cinematic client:** $20 Google AI Pro + $20 Veras Web (or substitute Adobe Firefly Standard $9.99 + Ideogram Basic $7) + maybe $50–100 in Rodin/Hunyuan compute = **~$50–150 in tooling per Cinematic project**. **<1% of revenue.** Not worth running a free-tier marathon for a paying client when $50 buys an evening's headache reduction.

The free stack is right for **demos, prospect mockups, and the first 3–5 Trochai Sites clients while proving the model.** Once a Cinematic deliverable is paid, charge through the tooling — bake $150 into the SOW under "production add-ons" or absorb it as COGS.

---

## 6. Costa Rica-specific notes

- **No documented blocks** on Together AI, Pollinations, Bing Image Creator, ChatGPT, Google AI Studio, Veras, ArkoAI, Tripo3D, Meshy, or Rodin from CR. All work without VPN per public docs.
- **Kling AI** has had intermittent phone-verification glitches with non-Asian numbers; if hit, use Twilio/Google Voice US number or skip (Veo + Hailuo cover the same need).
- **Hailuo MiniMax** signs up with email; CR-accessible.
- **Gemini API billing** uses Google Cloud Console region. CR is fully supported — the $45 trap in §2 is universal, not CR-specific.
- **Together AI's $1 starter credit + 3-month free FLUX schnell** redemption is reliable from CR per docs.
- **Local installs** (FLUX schnell, SDXL, Hunyuan3D, LTX-2.3) sidestep all geo concerns. With a 12 GB+ NVIDIA GPU, this is the most reliable long-term path. On Mac (Apple Silicon), FLUX/Hunyuan have AS paths but slower.

---

## 7. References

- [Gemini Image Free Tier Guide 2026](https://www.aifreeapi.com/en/posts/gemini-image-generation-free-api)
- [Nano Banana Pro Rate Limits (LaoZhang)](https://blog.laozhang.ai/en/posts/gemini-nano-banana-pro-free-vs-pro-limits)
- [Gemini API Rate Limits (official)](https://ai.google.dev/gemini-api/docs/rate-limits) · [Gemini API Billing (official)](https://ai.google.dev/gemini-api/docs/billing)
- [FLUX.1 schnell on Hugging Face (Apache 2.0)](https://huggingface.co/black-forest-labs/FLUX.1-schnell) · [BFL Licensing](https://bfl.ai/licensing) · [FLUX Local Setup Guide 2026](https://localaimaster.com/blog/flux-local-image-generation)
- [Together AI FLUX schnell free endpoint](https://www.together.ai/models/flux-1-schnell) · [Pollinations.AI](https://pollinations-ai.com/)
- [Leonardo.ai pricing](https://leonardo.ai/pricing) · [Ideogram plans](https://docs.ideogram.ai/plans-and-pricing/available-plans) · [Krea pricing](https://www.krea.ai/pricing) · [Recraft free plan](https://www.recraft.ai/docs/plans-and-billing/free-plan) · [Adobe Firefly credits FAQ](https://helpx.adobe.com/creative-cloud/apps/generative-ai/generative-credits-faq.html)
- [Bing Image Creator](https://www.bing.com/images/create) · [DALL-E free guide 2026](https://www.jenova.ai/en/resources/dall-e-free) · [ChatGPT free image limits 2026](https://www.aifreeapi.com/en/posts/chatgpt-image-generation-limit-free-plan)
- [Runway pricing](https://runwayml.com/pricing) · [Pika pricing](https://pika.art/pricing) · [Hailuo terms](https://hailuoai.video/doc/payment-policy.html) · [Kling AI 2026 limits](https://aiimagetovideo.pro/blog/free-kling-ai-video-generator/) · [Luma pricing](https://lumalabs.ai/pricing)
- [Veo 3.1 free for everyone (April 2026)](https://www.veo3ai.io/blog/veo-3-1-free-for-everyone-how-to-use-2026)
- [LTX Desktop / LTX-2.3](https://github.com/Lightricks/LTX-Desktop) · [LTX-2 Open Source](https://ltx.io/model/open-source) · [Wan 2.2 GitHub](https://github.com/Wan-Video/Wan2.2) · [Wan 2.5 overview](https://www.mindstudio.ai/blog/what-is-wan-2-5-video-open-source) · [Stable Video Diffusion local](https://stable-diffusion-art.com/stable-video-diffusion-img2vid/)
- [Veras (EvolveLAB)](https://www.evolvelab.io/veras) · [Chaos Veras](https://www.chaos.com/veras) · [ArkoAI](https://arko.ai/) · [Maket pricing](https://www.maket.ai/pricing) · [PromeAI review](https://techjarvisai.com/promeai-review/)
- [Tripo3D pricing](https://lorphic.com/tripo-ai-pricing-3d-models-full-guide-and-review/) · [Meshy pricing](https://www.meshy.ai/pricing) · [Hunyuan3D-2.1 GitHub](https://github.com/Tencent-Hunyuan/Hunyuan3D-2.1) · [Hyper3D Rodin](https://hyper3d.ai/) · [Rodin v2 review](https://gaga.art/blog/rodin-gen-2-review/)
- [Sketchfab CC0 collection](https://sketchfab.com/nebulousflynn/collections/cc0-9e9b8c5442ab4b59ba16b6fa5e43b8da) · [Sketchfab CC license guide](https://sketchfab.com/blogs/community/an-introduction-to-creative-commons-licenses/)
