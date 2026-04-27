# Lunes — Newsletter companion: Trochai Insights Sem. 18

> Bucket: Authority | Formato: Carousel + LinkedIn Newsletter article

---

## Contexto editorial

Esta semana abre el pillar de **coexistence**. La newsletter mantiene el formato estándar (CR + Global + Tech), pero la sección Tech & Operación destaca novedades del ecosistema WhatsApp Business / coexistence cuando hay noticia relevante. La sección de cierre tease el lanzamiento del add-on en ~30 días.

El contenido completo del newsletter (ES + EN) está en `trochai-landing/content/blog/{locale}/trochai-insights-2026-s18.mdx`.

---

## LinkedIn Post Caption

> Esta caption se finaliza en el archivo `trochai-landing/content/linkedin/trochai-insights-2026-s18.txt`. La versión definitiva la genera el subagente del newsletter (research + draft).
>
> Estructura esperada:

```
{Hook scroll-stopping conectando la noticia top con coexistence}

Esta semana en Trochai Insights (Sem. 18):

→ 🇨🇷 {bullet CR 1}
→ 🇨🇷 {bullet CR 2}
→ 🇨🇷 {bullet CR 3}
→ 📉 {bullet global 1}
→ 📊 {bullet global 2}
→ 🤖 {bullet tech — coexistence/WhatsApp si aplica}

{Cierre tease: "El próximo mes lanzamos coexistence — su WhatsApp Business y Trochai en el mismo número, sin que sus agentes cambien de app."}

Fuentes:
- {urls completas, no solo dominio}

👉 Lea el newsletter completo: trochai.com/es/blog/trochai-insights-2026-s18

#TrochaiInsights #BienesRaíces #CostaRica #Coexistence #WhatsApp #PropTech
```

---

## Visual Spec — Newsletter Carousel

**Composition type:** `CarouselWeek` (1080x1350, multi-slide)
**Composition ID prefix:** `S18-` (auto-registered por props.json)
**Total slides:** 8 (cover + 6 stories + CTA)

Renderiza vía `/monday-content` Steps 2–4:
- Source: `trochai-videos/public/carousel/trochai-insights-2026-s18/props.json`
- Output: `trochai-videos/out/carousel/trochai-insights-2026-s18/`
- Incluye: PNGs + `carousel.pdf` + `captions.md`

**CTA del carousel (override en props.json):**
- `ctaText`: "Su WhatsApp Business y su plataforma. Mismo número. En 30 días."
- `ctaSubtext`: "Lista de espera coexistence: trochai.com (link en blog)"

---

## LinkedIn Newsletter article

El newsletter article se publica como **LinkedIn Newsletter** ("Trochai Insights") con:
- **Title:** "Sem. 18 — {tema editorial generado por subagente}"
- **Body:** Contenido completo del MDX en `trochai-landing/content/blog/es/trochai-insights-2026-s18.mdx`
- **Cover image:** Cover slide del carousel renderizado (`out/carousel/trochai-insights-2026-s18/cover.png`)
- **CTA al final del artículo:** Mencionar el lanzamiento de coexistence + link a la lista de espera

---

## Cross-post Instagram

Carousel cross-posted a Instagram (8 slides — same PNGs).

Caption corta para IG: ver `instagram/carousel/caption.txt`.

---

## Promoción interna

- WhatsApp del equipo: avisar lanzamiento del newsletter
- Email a la base actual de hand-raisers: "Sem. 18 — y prep para el lanzamiento de coexistence"
