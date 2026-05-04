# Jueves — Hot take carousel: "Los 5 lugares" — el costo invisible de cada surface

> Bucket: Growth | Formato: Pillar carousel multi-slide (countdown) + text

---

## LinkedIn Post Caption

Cuando una agencia agrega una propiedad nueva al inventario, ¿cuántos lugares tiene que tocar?

Conté con dueños reales esta semana. La respuesta promedio: cinco. La máxima: ocho.

Aquí va el tour del costo real, surface por surface (deslice →):

**🗂️ 1. El MLS o CRM interno** — Excel, Notion, o una herramienta dedicada. ~5 minutos. La fuente "verdadera" para la agencia, pero ninguna otra superficie la lee.

**🌐 2. Los portales nacionales** — re.cr, Encuentra24, otros agregadores. ~10–15 minutos cada uno. Donde realmente llegan los compradores ticos. Cero sincronización con su sitio propio.

**💻 3. El sitio web propio** — típicamente WordPress con un plugin de listings. ~10–20 minutos. Lo que el cliente abre cuando le pasan el link. Cero conexión con su Inbox.

**📱 4. El catálogo de WhatsApp Business** — donde el bot busca cuando un cliente pregunta. ~5–10 minutos. Si no se actualiza, el bot da respuestas que ya no aplican.

**📸 5. Las captions de Instagram** — ~5 minutos. El canal de descubrimiento más visual, pero el menos sincronizado. La propiedad ya se vendió y el caption sigue diciendo "available."

—

**Total por listing nuevo: 35–60 minutos.**
**Multiplicado por 50 listings activos × 4 actualizaciones promedio al año: ~100 horas/año.**

Eso son 2.5 semanas de trabajo de un agente, gastadas en mover la misma información entre sistemas que no se hablan.

Pero ese es el costo medible. El costo invisible es peor:

→ La deriva entre los 5 lugares siempre existe. Una propiedad vendida en abril sigue apareciendo en el sitio web hasta junio.
→ El cliente nota la deriva en 8 segundos. Pregunta por WhatsApp, el bot dice "ya no está", el sitio dice que sí. La confianza se rompe ahí.
→ Sin consolidar, ninguna tendencia PropTech 2026 (virtual tours, AI para predicción de precios, asset management) se puede agregar bien — porque todas asumen un único origen de datos.

—

Las pymes ticas que están en el 50% que ya usa IA (Microsoft 2025) no son las que tienen más herramientas. Son las que tienen una sola fuente de verdad sobre el catálogo, los precios, la disponibilidad. Todo lo demás (bot, sitio, app del agente, futuros virtual tours) lee de ahí.

Esa es la pregunta arquitectónica que define quién compite en 2027.

—

**¿Cuántos lugares está editando usted hoy?** Cuéntelo en los comentarios. Si la respuesta es 5 o más, no es disciplina lo que le falta — es arquitectura.

Promo de mayo: plan anual de Trochai Inbox = sitio web gratis ($2,500–$4,500 según template). El sitio comparte la base de datos del Inbox, así que una propiedad nueva aparece automáticamente en su sitio. trochai.com/sitios

Fuentes:
- Trochai — discovery calls Q1–Q2 2026 (n=20+ agencias)
- https://news.microsoft.com/es-xl/50-de-las-pymes-en-costa-rica-utilizan-algun-tipo-de-ia/
- https://thecostaricanews.com/real-estate-trends-for-2026/

#PropTech #BienesRaíces #CostaRica #TransformaciónDigital #TrochaiSites

---

## Visual Spec — Pillar Carousel (PillarCarousel)

**Composition type:** `PillarCarousel` (1080x1350, multi-slide)
**Composition ID prefix:** `Pillar-FivePlaces-W19`
**Total slides:** 8 (cover + 5 surfaces + cost summary + CTA)

```json
{
  "slug": "five-places-w19",
  "title": "Los 5 lugares donde vive su inventario",
  "subtitle": "Un tour del costo real, surface por surface. Sin marketing, con datos de discovery.",
  "slides": [
    {
      "number": "01",
      "headline": "El MLS o CRM interno",
      "body": "Excel, Notion, o una herramienta dedicada. ~5 min por update. La fuente 'verdadera' para la agencia, pero ninguna otra superficie la lee. La agencia confía en él; el cliente nunca lo ve.",
      "accentColor": "#20A06F"
    },
    {
      "number": "02",
      "headline": "Los portales nacionales",
      "body": "Donde realmente llegan los compradores ticos. ~10–15 min cada uno. Cero sincronización con el sitio propio: una rebaja en uno no aparece en el otro hasta que alguien la copie a mano.",
      "accentColor": "#3B82F6"
    },
    {
      "number": "03",
      "headline": "El sitio web propio",
      "body": "Típicamente WordPress con un plugin de listings. ~10–20 min por update. Lo que el cliente abre cuando le pasan el link. Cero conexión con su Inbox — el bot que contesta WhatsApp no sabe qué hay acá.",
      "accentColor": "#8B5CF6"
    },
    {
      "number": "04",
      "headline": "El catálogo de WhatsApp Business",
      "body": "Donde el bot busca cuando un cliente pregunta. ~5–10 min por update. Si no se actualiza, el bot da respuestas obsoletas — la propiedad ya se vendió, el bot sigue ofreciéndola.",
      "accentColor": "#25D366"
    },
    {
      "number": "05",
      "headline": "Las captions de Instagram",
      "body": "~5 min por update. El canal de descubrimiento más visual, pero el menos sincronizado. La propiedad ya se vendió y el caption sigue diciendo 'available' — y abre el DM.",
      "accentColor": "#EC4899"
    },
    {
      "number": "💸",
      "headline": "El costo medible",
      "body": "35–60 min por listing × 50 listings × 4 updates/año = ~100 horas/año por agencia. 2.5 semanas de trabajo de un agente, gastadas en mover la misma data entre sistemas que no se hablan. Y ese es solo el costo visible.",
      "accentColor": "#F59E0B"
    },
    {
      "number": "👁️",
      "headline": "El costo invisible: la deriva",
      "body": "La deriva entre los 5 lugares siempre existe. Una propiedad vendida en abril sigue en el sitio hasta junio. El cliente lo nota en 8 segundos: pregunta por WhatsApp, el bot dice 'ya no está', el sitio dice que sí. Confianza rota.",
      "accentColor": "#EF4444"
    }
  ],
  "ctaText": "La fix no es otra herramienta. Es arquitectura: un único origen, todo lee de ahí.",
  "ctaSubtext": "Plan anual de Inbox = sitio web gratis. Solo mayo. trochai.com/sitios",
  "sources": [
    "Trochai — discovery calls Q1–Q2 2026 (n=20+ agencias)",
    "Microsoft — Encuesta Source LATAM 2025"
  ],
  "locale": "es",
  "slideIndex": 0
}
```
