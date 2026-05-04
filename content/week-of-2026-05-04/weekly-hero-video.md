# Weekly Hero Video Brief — Week 19 (4 mayo – 10 mayo, 2026)

> One hand-crafted, high-effort marketing video per week, built with Hyperframes
> in `trochai-videos/`. Produce Mon afternoon → Tue morning, ship Tuesday afternoon.
> Standalone cross-platform asset — does NOT replace any daily LinkedIn post.

## Topic
Su inventario vive en cinco lugares — y por qué el cliente lo nota antes que vos. Trochai Sites como la fix arquitectónica.

**Why this video, this week:** la macro-data del 50%/53%/CR-5to-LATAM funciona en LinkedIn (Mon newsletter), pero su impacto visual completo necesita un canal donde el storytelling y el reveal del mecanismo de Sites se sienta. IG Reels y TikTok son los canales que más necesitan el levante en mayo (Sites recién lanzado, sin awareness fuera de LinkedIn). Y la estructura "5 lugares → 1 Inbox" es naturalmente vertical — un countdown visual que se expande en pantalla móvil.

## Format pick
**Vertical 1080×1920**

**Why this format:** IG Reels y TikTok tienen el mayor delta de awareness por cerrar — Trochai Sites lleva 5 días en producción y la conversación está atrapada en LinkedIn. Vertical extiende la audiencia fuera del círculo profesional. El storyboard "5 cards apiladas verticalmente que colapsan en 1 Inbox" funciona bárbaro en aspect ratio vertical (cards son altas, no anchas), y mediocre en horizontal (cards quedan pequeñas).

## Hook (first 1.5 seconds)
**Visual:** Cinco cards flotantes apiladas verticalmente con etiquetas: "MLS / Portales / Sitio / WhatsApp / Instagram". Cada card pulsa rojo brevemente con un timer encima ("5 min" "15 min" "20 min" "10 min" "5 min"). El timer total slams al medio: "55 min × cada propiedad."

**Frozen thumbnail value:** la imagen sola — 5 cards + 55 min — comunica el problema sin sonido. Funciona como thumbnail de Reels/TikTok.

## Voiceover script (Spanish ustedeo, ~28s total)

Reglas seguidas (per `trochai-videos/CLAUDE.md` § Voiceover & Script Rules): nunca leer lo que está en pantalla, abrir con el stat, citar la fuente en la escena 1, mencionar Trochai en la escena de resolución, usar "menos de dos minutos" (nunca "instantáneo"/"5 segundos").

### Scene 1 — Hook (0-3s)
**Voiceover:** "Según Microsoft, el cincuenta por ciento de pymes ticas ya usa IA. Bienes raíces no aparece en esa estadística."

### Scene 2 — Problem (3-9s)
**Voiceover:** "El catálogo vive en cinco lugares — MLS, portales, sitio, WhatsApp, Instagram. Cada actualización cuesta entre treinta y sesenta minutos. Por cincuenta listings al año, son cien horas perdidas en doble carga."

### Scene 3 — Real cost: client notices (9-15s)
**Voiceover:** "Pero el costo invisible es peor. Un cliente pregunta por WhatsApp por una propiedad que vio en su sitio. El bot dice que ya no está. El sitio dice que sí. La confianza se rompe en ocho segundos."

### Scene 4 — Trochai resolution (15-22s)
**Voiceover:** "Con Trochai Sites — el sitio web comparte la misma base de datos que su Inbox. Una propiedad nueva aparece automáticamente. El bot conoce el catálogo. En menos de dos minutos."

### Scene 5 — CTA (22-28s)
**Voiceover:** "Promo mayo: plan anual Inbox incluye su sitio gratis. Trochai punto com diagonal sitios — agende su consulta."

## Storyboard

| Time | Track 0 (avatar) | Track 1 (motion graphics) | Track 2 (b-roll) |
|---|---|---|---|
| 0-3s | Avatar lipsyncs S1 | "50%" big counter slams + Microsoft source citation below | — |
| 3-9s | Avatar speaks S2 | 5 floating cards (MLS/Portales/Sitio/WA/IG), timers tick on each, total slams "55 min × 50 listings × 4 = 100 horas/año" | — |
| 9-15s | (cut to graphics) | WhatsApp conversation: client asks → bot says "ya no está" → website still shows "available" → red flash conflict | — |
| 15-22s | Avatar returns | 5 cards collapse into single "Inbox" hub. 3 lines fan out to "Sitio web," "Bot," "App agente." All glow in sync. | — |
| 22-28s | Avatar closes | Trochai logo + CTA chip + "trochai.com/sitios" + breathing pulse | — |

## Asset prompts

### Nano Banana Pro — avatar variants (free tier in AI Studio)
Open https://aistudio.google.com → Gemini 2.5 Flash Image. Master prompt (locked in `trochai-business/content-strategy/AVATAR-PROMPT.md` if it exists; otherwise add it on first generation):

```
Photorealistic portrait of Leeren Wu — Trochai founder, Asian-American male
late 20s/early 30s, professional but approachable, neutral modern office backdrop
with subtle Costa Rica feel (palm leaf shadow on the wall), soft key lighting,
eyes to camera, subtle warmth. Aspect ratio 9:16 vertical. Photo-real, no
stylization, no logos in frame.
```

Run **5 variants** swapping in expression cues:
- "...neutral expression, looking directly at camera" (S1)
- "...slightly concerned, glancing off-camera right" (S2)
- (skip S3 — pure motion graphics, no avatar)
- "...resolved, slight nod, one hand subtly gesturing" (S4)
- "...warm closing smile" (S5)

Save to `trochai-videos/hyperframes/compositions/sites-five-places-w19/assets/avatar-{n}.png`.

### ElevenLabs Aurora — lipsync (existing sub, ~$0 marginal)

For each scene where the avatar speaks (1, 2, 4, 5):

1. Generate voiceover MP3 per scene via:
   ```bash
   cd trochai-videos
   npx tsx src/scripts/generate-voiceover.ts \
     --voice tTQzD8U9VSnJgfwC6HbY \
     --stability 0.2 --style 0.8 --similarity 0.75 --speed 1.2 \
     --text "{scene voiceover}" \
     --output hyperframes/compositions/sites-five-places-w19/assets/voice-s{n}.mp3
   ```
2. Upload `avatar-{n}.png` + `voice-s{n}.mp3` to ElevenLabs (Studio → Image+Audio → Aurora).
3. Save the resulting MP4 as `assets/avatar-s{n}.mp4`.

### Veo 3.1 — b-roll plates
**SKIPPED esta semana** (per founder direction 2026-05-04). Storyboard funciona puramente con motion graphics + avatar; b-roll cinematográfico no agrega información — solo presupuesto.

## Hyperframes scaffolding

```bash
cd trochai-videos
npm run hf:new -- sites-five-places-w19 --vertical --title "Inventario en 5 lugares — Sites lo arregla"
```

This creates `hyperframes/compositions/sites-five-places-w19/` with the right starter +
the `shared/` junction. Open `/hyperframes` in Claude Code from that directory
and paste this brief — Claude builds the comp from here.

## Production checklist (Mon afternoon → Tue morning)

For the full step-by-step with copy-paste commands, see
`trochai-videos/hyperframes/WEEKLY-HERO-VIDEO.md`. The high-level beats:

- [ ] **Mon PM (1.5h):** Scaffold composition (`npm run hf:new`), generate 5 Nano Banana avatar variants, generate ElevenLabs voiceover per scene (S1, S2, S4, S5)
- [ ] **Mon evening (45m):** Lipsync avatar in ElevenLabs Aurora → save 4 MP4s per scene
- [ ] **Mon evening (skipped this week):** Veo 3.1 b-roll plates — N/A
- [ ] **Tue 7-9am (1.5h):** Open `/hyperframes` in Claude Code from `compositions/sites-five-places-w19/`, paste this brief, build comp, preview, iterate
- [ ] **Tue 9am:** `npx hyperframes lint && npx hyperframes validate && npx hyperframes inspect` (must all pass)
- [ ] **Tue 9:15am:** `npx hyperframes render --dir hyperframes/compositions/sites-five-places-w19 --output out/sites-five-places-w19.mp4`
- [ ] **Tue 9:30am:** Copy MP4 to `deliverables/hero-video/` + write platform captions
- [ ] **Tue 10am:** Schedule via `/publish-video` skill for the afternoon slots below

## Distribution plan

The hero video ships **Tuesday afternoon** so it doesn't compete algorithmically with the Tuesday morning growth infographic (Microsoft AI study brandjack, ships Tue 8-9am per the daily matrix).

| Platform | Time (CR, Tuesday May 5) | Caption source |
|---|---|---|
| LinkedIn vertical | 2:00 PM | `../deliverables/hero-video/caption-linkedin.txt` |
| Instagram Reels | 2:30 PM | `../deliverables/hero-video/caption-ig.txt` |
| TikTok | 3:00 PM | `../deliverables/hero-video/caption-tiktok.txt` |
| YouTube Shorts | 4:00 PM | `../deliverables/hero-video/caption-linkedin.txt` (long-form) |

These captions are NEW (not duplicates of any daily MD) — the hero video is its own asset with its own messaging. Generate them as part of the production pass on Tuesday morning, save to `deliverables/hero-video/`.
