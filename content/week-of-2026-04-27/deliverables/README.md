# Week 18 Content — April 27 – May 3, 2026

**Pillar:** Coexistence — su WhatsApp Business app y Trochai funcionando en el mismo número.
**Lanzamiento del feature:** late May 2026 (~30 días).
**Discount:** 50% off primer mes para suscripciones antes del **30 abril**. Mon–Thu pueden mencionar. Fri–Sun NO mencionar (per memory).

Toda la semana educa al mercado costarricense sobre coexistence — el feature que permite que el WhatsApp Business app del vendedor y el inbox Trochai operen sobre el mismo número, sin migración forzada.

## Trochai Company Schedule

| Día | Fecha | Bucket | Formato | Files | Status |
|-----|-------|--------|---------|-------|--------|
| Lun | 27 abr | Authority | Newsletter + carousel | `linkedin/monday-newsletter/` | ✅ Carousel rendered (PDF + 8 slides) |
| Mar | 28 abr | Growth | Infographic | `linkedin/tuesday-growth/` | 📋 Caption + visual spec ready (composition NOT built) |
| Mié | 29 abr | Authority | Carousel educativo (7 slides) | `linkedin/wednesday-authority/` | 📋 Caption + carousel spec ready (composition NOT built) |
| Jue | 30 abr | Growth | Hot take infographic — **último día descuento** | `linkedin/thursday-growth/` | 📋 Caption + spec ready |
| Vie | 1 may | Conversion | Carousel producto (6 slides) — sin descuento | `linkedin/friday-conversion/` | 📋 Caption + spec ready |
| Sáb | 2 may | Authority | Carousel deep-dive (10 slides) — sin descuento | `linkedin/saturday-authority/` | 📋 Caption + spec ready |
| Dom | 3 may | Personal | Founder infographic | `linkedin/sunday-personal/` | 📋 Caption + spec ready |

## Estado de las visuales

✅ **Lunes — Newsletter carousel:** Renderizado y listo para postear (`monday-newsletter/carousel.pdf` + 8 slides PNG).

📋 **Tue–Sun — visual specs only.** Las compositions de Remotion NO se construyeron esta vuelta. Cada `caption.txt` está acompañado de su spec en el archivo principal del día (`../../tuesday-growth.md`, etc.). Cuando el usuario apruebe, ejecutar Step 6 del `/monday-content` skill para crear los TSX y rendir.

Las specs siguen el patrón:
- **LinkedInCard** (1080x1350 single-image infographic) para Mar, Jue, Dom
- **PillarCarousel** (1080x1350 multi-slide) para Mié, Vie, Sáb

## Instagram (cross-post 3)

- **Lunes carousel** → `instagram/carousel/monday/` (8 slides newsletter — ya copiados desde el render)
- **Miércoles carousel** → `instagram/carousel/wednesday/` (pendiente: rendir el carousel "Coexistence en 5 pasos" antes de cross-postear)
- **Sábado carousel** → `instagram/carousel/saturday/` (pendiente: rendir el carousel "8 preguntas")
- Caption corta IG: `instagram/carousel/caption.txt`
- Reels scripts (3, sin rendir): `instagram/reels/video-scripts.txt`

## Blog

Activo después del push del lunes:
- ES: https://trochai.com/es/blog/trochai-insights-2026-s18
- EN: https://trochai.com/blog/trochai-insights-2026-s18

## Render Commands (cuando se construyan las compositions)

```bash
cd trochai-videos

# Daily infographics (Mar, Jue, Dom)
npx remotion still LI-Card-FalseDilemma-W18 --output=out/linkedin/tue-w18.png --image-format=png
npx remotion still LI-Card-MigrationCost-W18 --output=out/linkedin/thu-w18.png --image-format=png
npx remotion still LI-Card-FounderCoexistence-W18 --output=out/linkedin/sun-w18.png --image-format=png

# Daily pillar carousels (Mié, Vie, Sáb) — render slide-by-slide
# Crear primero un script render-w18-daily.sh siguiendo el patrón de render-w17-daily.sh
bash scripts/render-w18-daily.sh

# Newsletter carousel (ya renderizado)
npx tsx scripts/render-carousel.ts trochai-insights-2026-s18
```

## Posting Flow

1. **Lun 27 abr 9:30am CR:** Publicar LinkedIn Newsletter (article.md) + carousel post con caption.txt + cross-post a Instagram con `instagram/carousel/monday/` slides.
2. **Mar 28 abr 9:30am:** Schedule "El falso dilema" infographic + caption (compositions deben renderizarse antes).
3. **Mié 29 abr 9:30am:** Schedule "Coexistence en 5 pasos" carousel + caption + IG cross-post.
4. **Jue 30 abr 9:30am:** Schedule "Costo real de migrar" hot-take + caption — **última mención del descuento**, urgent CTA + countdown.
5. **Vie 1 may 9:30am:** Schedule "Trochai Coexistence: producto" carousel + caption — **sin descuento**, foco en lista de espera.
6. **Sáb 2 may 10:00am:** Schedule "8 preguntas" deep-dive carousel + caption + IG cross-post.
7. **Dom 3 may 10:00am:** Schedule founder reflection + caption.

Use Metricool o LinkedIn native scheduler.

## Comment Flywheel (crítico)

- 30 min/día engageando con cuentas ICP **antes** de postear.
- Replyear todos los comentarios en el post en la primera hora.
- Target accounts esta semana: dueños de agencias GAM con presencia LinkedIn, CCCBR members, expat real estate brokers, partners regionales (Mario Cordero, Houzez resellers CR).
- DM a hand-raisers: cualquiera que comente "me interesa coexistence" debe entrar a una lista de DM con copy preparado para el waitlist.

## Launch Discount

- **Mon, Tue, Wed, Thu posts:** Pueden mencionar "50% off primer mes — válido hasta 30 abril."
- **Thu (30 abr):** Es el último día — usar urgent CTA con countdown.
- **Fri, Sat, Sun (post-30 abr):** **NO** mencionar el descuento. Foco únicamente en lista de espera coexistence.

## Lista de espera Coexistence

Forma simple a publicar el lunes en `trochai.com/coexistence`:
- Nombre + agencia + email + número WhatsApp + tamaño de equipo (#vendedores)
- Email automático de confirmación con timeline tentativo (late May 2026)

## Métricas a medir

- **Reach orgánico LinkedIn:** impresiones acumuladas Lun–Dom (target: +30% vs. semana 17).
- **Hand-raisers:** comentarios + DMs preguntando fecha de lanzamiento o precio del add-on coexistence.
- **Lista de espera:** registros nuevos en formulario coexistence.
- **Conversión a Loom:** cuántos hand-raisers terminan en una llamada de descubrimiento durante mayo.
