# Jueves — Hot take carousel: las superficies que no se hablan

> Bucket: Growth | Formato: Pillar carousel multi-slide (tour por superficie) + text

---

## LinkedIn Post Caption

Cuando una agencia agrega una propiedad nueva al inventario, ¿cuántas superficies tiene que tocar?

La cantidad varía por agencia — algunas tocan tres, otras siete. Pero el patrón es consistente: un MLS o CRM interno, los portales nacionales, el sitio propio, el catálogo de WhatsApp, y las captions de Instagram. Ninguna se sincroniza con las demás.

Aquí va el tour del costo real, superficie por superficie (deslice →):

**🗂️ El MLS o CRM interno** — Excel, Notion, o una herramienta dedicada. ~5 minutos. La fuente "verdadera" para la agencia, pero ninguna otra superficie la lee.

**🌐 Los portales nacionales** — re.cr, Encuentra24, otros agregadores. ~10–15 minutos cada uno. Donde realmente llegan los compradores ticos. Cero sincronización con su sitio propio.

**💻 El sitio web propio** — típicamente WordPress con un plugin de listings. ~10–20 minutos. Lo que el cliente abre cuando le pasan el link. Cero conexión con su Inbox.

**📱 El catálogo de WhatsApp Business** — donde el bot busca cuando un cliente pregunta. ~5–10 minutos. Si no se actualiza, el bot da respuestas que ya no aplican.

**📸 Las captions de Instagram** — ~5 minutos. El canal de descubrimiento más visual, pero el menos sincronizado. La propiedad ya se vendió y el caption sigue diciendo "available."

—

**Total por listing nuevo: 35–60 minutos.**
**Multiplicado por 50 listings activos × 4 actualizaciones promedio al año: cien horas o más al año.**

Eso son semanas de trabajo de un agente, gastadas en mover la misma información entre sistemas que no se hablan.

Pero ese es el costo medible. El costo invisible es peor:

→ La deriva entre las superficies siempre existe. Una propiedad vendida en abril sigue apareciendo en el sitio web hasta junio.
→ El cliente nota la deriva en 8 segundos. Pregunta por WhatsApp, el bot dice "ya no está", el sitio dice que sí. La confianza se rompe ahí.
→ Sin consolidar, ninguna tendencia PropTech 2026 (virtual tours, AI para predicción de precios, asset management) se puede agregar bien — porque todas asumen un único origen de datos.

—

Las pymes ticas que están en el 50% que ya usa IA (Microsoft 2025) no son las que tienen más herramientas. Son las que tienen una sola fuente de verdad sobre el catálogo, los precios, la disponibilidad. Todo lo demás (bot, sitio, app del agente) lee de ahí.

Esa es la pregunta arquitectónica que define quién compite en 2027.

—

**¿Cuántas superficies está tocando usted hoy?** Cuéntelo en los comentarios. Si toca varias y ninguna se sincroniza, no es disciplina lo que le falta — es arquitectura.

Promo de mayo: plan anual de Trochai Inbox = sitio web gratis ($2,500–$4,500 según template). El sitio comparte la base de datos del Inbox, así que una propiedad nueva aparece automáticamente en su sitio. trochai.com/sitios

Fuentes:
- Observación de mercado — patrón consistente en agencias CR (multi-portal + sitio + redes)
- https://news.microsoft.com/es-xl/50-de-las-pymes-en-costa-rica-utilizan-algun-tipo-de-ia/
- https://thecostaricanews.com/real-estate-trends-for-2026/

#PropTech #BienesRaíces #CostaRica #TransformaciónDigital #TrochaiSites

---

## Visual Spec — Pillar Carousel (PillarCarousel)

**Composition type:** `PillarCarousel` (1080x1350, multi-slide)
**Composition ID prefix:** `Pillar-FivePlaces-W19` (composition ID kept as internal label — slide content describes the pattern, not a fixed count)
**Total slides:** 9 (cover + 5 surface slides + 2 cost slides + CTA)

```json
{
  "slug": "five-places-w19",
  "title": "Las superficies donde vive su inventario",
  "subtitle": "Un tour del costo real por cada superficie típica. La cantidad varía por agencia, el patrón no.",
  "slides": [
    {
      "number": "🗂️",
      "headline": "El MLS o CRM interno",
      "body": "Excel, Notion, o una herramienta dedicada. ~5 min por update. La fuente 'verdadera' para la agencia, pero ninguna otra superficie la lee. La agencia confía en él; el cliente nunca lo ve.",
      "accentColor": "#20A06F"
    },
    {
      "number": "🌐",
      "headline": "Los portales nacionales",
      "body": "Donde realmente llegan los compradores ticos. ~10–15 min cada uno. Cero sincronización con el sitio propio: una rebaja en uno no aparece en el otro hasta que alguien la copie a mano.",
      "accentColor": "#3B82F6"
    },
    {
      "number": "💻",
      "headline": "El sitio web propio",
      "body": "Típicamente WordPress con un plugin de listings. ~10–20 min por update. Lo que el cliente abre cuando le pasan el link. Cero conexión con su Inbox — el bot que contesta WhatsApp no sabe qué hay acá.",
      "accentColor": "#8B5CF6"
    },
    {
      "number": "📱",
      "headline": "El catálogo de WhatsApp Business",
      "body": "Donde el bot busca cuando un cliente pregunta. ~5–10 min por update. Si no se actualiza, el bot da respuestas obsoletas — la propiedad ya se vendió, el bot sigue ofreciéndola.",
      "accentColor": "#25D366"
    },
    {
      "number": "📸",
      "headline": "Las captions de Instagram",
      "body": "~5 min por update. El canal de descubrimiento más visual, pero el menos sincronizado. La propiedad ya se vendió y el caption sigue diciendo 'available' — y abre el DM.",
      "accentColor": "#EC4899"
    },
    {
      "number": "💸",
      "headline": "El costo medible",
      "body": "35–60 min por listing × 50 listings × 4 updates/año = cien horas o más al año por agencia. Semanas de trabajo de un agente, gastadas en mover la misma data entre sistemas que no se hablan. Y ese es solo el costo visible.",
      "accentColor": "#F59E0B"
    },
    {
      "number": "👁️",
      "headline": "El costo invisible: la deriva",
      "body": "La deriva entre las superficies siempre existe. Una propiedad vendida en abril sigue en el sitio hasta junio. El cliente lo nota en 8 segundos: pregunta por WhatsApp, el bot dice 'ya no está', el sitio dice que sí. Confianza rota.",
      "accentColor": "#EF4444"
    }
  ],
  "ctaText": "La fix no es otra herramienta. Es arquitectura: un único origen, todo lee de ahí.",
  "ctaSubtext": "Plan anual de Inbox = sitio web gratis. Solo mayo. trochai.com/sitios",
  "sources": [
    "Observación de mercado — patrón consistente en agencias CR",
    "Microsoft — Encuesta Source LATAM 2025"
  ],
  "locale": "es",
  "slideIndex": 0
}
```
