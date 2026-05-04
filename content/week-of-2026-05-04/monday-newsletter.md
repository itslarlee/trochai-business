# Lunes — Newsletter companion: Trochai Insights Sem. 19

> Bucket: Authority | Formato: Carousel + LinkedIn Newsletter article | EN repost requerido (founder personal)

---

## Contexto editorial

Esta semana abre el pillar de **Trochai Sites — single source of truth para inventario inmobiliario**. La newsletter usa el formato estándar (CR + Global + Tech), pero las tres dimensiones convergen en un solo wedge: Costa Rica está digitalizando, las inmobiliarias quedan en el rezago, y el costo es medible (~100 horas/año de doble carga + cliente que detecta la deriva en 8 segundos).

Cierre: tease promo mayo (annual Inbox = sitio gratis).

El contenido completo del newsletter (ES + EN) está en `trochai-landing/content/blog/{locale}/trochai-insights-2026-s19.mdx`.

---

## LinkedIn Post Caption

```
Su inventario vive en lugares que no se hablan. Su cliente lo nota antes que vos.

Mientras 53% de pymes ticas avanza en transformación digital y 50% ya usa IA, las inmobiliarias siguen editando cada propiedad en superficies desconectadas — portales nacionales, sitio propio, WhatsApp, redes — sin sincronización entre ellas.

Esta semana en Trochai Insights (Sem. 19):

→ 📊 Microsoft 2023 (vía DPL News): 53% de pymes ticas avanza rápidamente en transformación digital, 78% se considera "en el journey". 42% prioriza datos para BI; 35% nueva tecnología.
→ 🤖 Microsoft Source LATAM Encuesta 2025: 50% de pymes ticas ya usa IA en operaciones diarias. 62% del uso es servicio al cliente; 48% lo usa específicamente para mejorar servicio + satisfacción.
→ 🏘️ The Costa Rica News (dic 2025): PropTech 2026 = virtual tours + IA para predicción de precios + asset management. Tres tendencias que asumen un único origen de datos sobre el inventario.
→ 🥇 ILIA 2025: CR es 5to en LATAM en preparación de IA con score 53.83/100. Top 5: Chile, Brasil, Uruguay, Colombia, CR.
→ ⚠️ Google vía Tico Times (sept 2025): IA en LATAM se acerca a EE.UU./Europa — 48% de personas y 56% de empresas. Pero el WEF estima que 1 de cada 6 trabajadores tendrá que reskillearse para 2027. Brecha de talento, no de adopción.
→ 🏗️ El inventario inmobiliario en CR vive en superficies que no se hablan entre sí (MLS interno + portales nacionales + sitio propio + WhatsApp + Instagram). El número exacto varía por agencia — el patrón no.

La fix no es otra herramienta. Es arquitectónica: un único origen de datos sobre el inventario — el Inbox — y todas las superficies de salida (sitio web, bot, app del agente) leen de ahí.

Trochai Sites lanzó la semana pasada con esa arquitectura: una propiedad nueva en el Inbox aparece automáticamente en el sitio web. Cero integración, cero doble carga.

Promo de mayo: plan anual de Inbox = sitio web gratis ($2,500–$4,500 según template). Solo mayo.

Fuentes:
- https://dplnews.com/costa-rica-mas-de-la-mitad-de-pymes-ticas-avanza-hacia-transformacion-digital/
- https://news.microsoft.com/es-xl/50-de-las-pymes-en-costa-rica-utilizan-algun-tipo-de-ia/
- https://www.laprensalibre.cr/el-50-de-las-pymes-en-costa-rica-ya-utiliza-inteligencia-artificial-segun-encuesta-de-microsoft/
- https://thecostaricanews.com/real-estate-trends-for-2026/
- https://ticotimes.net/2025/07/05/costa-rica-leads-ai-adoption-in-small-businesses-across-latin-america
- https://ticotimes.net/2025/09/25/ai-in-latin-america-nears-us-europe-use-but-talent-lags-says-google

👉 Lea el newsletter completo: trochai.com/es/blog/trochai-insights-2026-s19

#TrochaiInsights #BienesRaíces #CostaRica #TransformaciónDigital #PropTech #TrochaiSites
```

> **Fuente única:** esta caption es idéntica a la del LinkedIn promo `trochai-landing/content/linkedin/trochai-insights-2026-s19.txt`. La versión definitiva queda en este archivo + el .txt de trochai-landing.

---

## Visual Spec — Newsletter Carousel

**Composition type:** `CarouselWeek` (1080x1350, multi-slide)
**Composition ID prefix:** `S19-` (auto-registered por props.json)
**Total slides:** 8 (cover + 6 stories + CTA)

Renderiza vía `/monday-content` Steps 2–4:
- Source: `trochai-videos/public/carousel/trochai-insights-2026-s19/props.json`
- Output: `trochai-videos/out/carousel/trochai-insights-2026-s19/`
- Incluye: PNGs + `carousel.pdf` + `captions.md`

**CTA del carousel (override en props.json):**
- `ctaText`: "Edita una vez. Aparece en todos lados."
- `ctaSubtext`: "Plan anual de Inbox = sitio web gratis. Solo mayo. trochai.com/sitios"

---

## LinkedIn Newsletter article

El newsletter article se publica como **LinkedIn Newsletter** ("Trochai Insights") con:
- **Title:** "Sem. 19 — 50% de pymes ticas usan IA, CR es 5to en LATAM, e inmobiliarias siguen editando cada propiedad en superficies que no se hablan"
- **Body:** Contenido completo del MDX en `trochai-landing/content/blog/es/trochai-insights-2026-s19.mdx`
- **Cover image:** Cover slide del carousel renderizado (`out/carousel/trochai-insights-2026-s19/cover.png`)
- **CTA al final del artículo:** Tease del promo mayo (annual Inbox = sitio gratis hasta el 31 de mayo) + link al formulario de demo

---

## Cross-post Instagram

Carousel cross-posted a Instagram (8 slides — same PNGs).

Caption corta para IG: ver `instagram/carousel/caption.txt` o usar la versión en `props.json#captions.instagram`.

---

## Promoción interna

- WhatsApp del equipo: avisar lanzamiento del newsletter + share de la URL del blog.
- Email a la base actual de hand-raisers + leads "warm" del CSV: "Sem. 19 — el wedge de Trochai Sites en datos."
- Founder personal LinkedIn: repostear con caption en inglés (`personal-repost-en.txt`).
