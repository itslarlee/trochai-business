# Viernes — Antes vs. Después: de WhatsApp Business a inbox profesional

> Bucket: Conversion | Formato: Carousel (before/after comparison)

---

## LinkedIn Post Caption

Mismo número de WhatsApp. Mismos agentes. Mismos leads.

Resultado completamente diferente.

Así se ve el antes y después de una agencia que pasó de WhatsApp Business a un inbox profesional (deslice →):

ANTES:
→ Leads del sábado esperaban hasta el lunes
→ 3 agentes respondían al mismo lead con info diferente
→ Sin métricas: ni idea del tiempo de respuesta promedio
→ Bot de WhatsApp Business: "Gracias por escribirnos, le respondemos pronto"
→ El director preguntaba "¿cómo van los leads?" y nadie sabía

DESPUÉS:
→ Cada mensaje se asigna automáticamente a un agente
→ Bot de IA responde en <2 min con propiedades reales del inventario
→ Dashboard muestra tiempo de respuesta promedio, por agente
→ Conversaciones etiquetadas por estado: nuevo, en progreso, cerrado
→ El director ve exactamente cuántos leads se atendieron, cuántos se perdieron

No cambiaron de número. No dejaron WhatsApp. Solo le dieron estructura.

Si maneja una agencia de 5+ agentes y su WhatsApp parece un grupo de chat más que un canal de ventas, merece ver cómo se ve esto en acción.

Fuentes:
- 78% de compradores eligen al primer agente que responde — NAR 2025 (nar.realtor)
- 47% de consultas sin respuesta — Mike DelPrete 2024 (mikedp.com)

👉 trochai.com/es/contacto

#WhatsApp #BienesRaíces #Conversión #PropTech #CostaRica #Trochai

---

## Visual Spec — Pillar Carousel (PillarCarousel)

**Composition type:** `PillarCarousel` (1080x1350, multi-slide)
**Composition ID prefix:** `Pillar-Before-After-W16`
**Total slides:** 5 (cover + 2 content + comparison + CTA)

```json
{
  "slug": "before-after-w16",
  "title": "Antes vs. Después",
  "subtitle": "Mismo WhatsApp. Mismos agentes. Diferente resultado.",
  "slides": [
    {
      "number": "ANTES",
      "headline": "WhatsApp Business solo",
      "body": "Leads del sábado esperan hasta el lunes. 3 agentes responden al mismo lead. Sin métricas. El bot dice 'le respondemos pronto'. El director no sabe cuántos leads se pierden.",
      "accentColor": "#EF4444"
    },
    {
      "number": "DESPUÉS",
      "headline": "Inbox profesional de equipo",
      "body": "Cada mensaje se asigna automáticamente. Bot de IA responde en <2 min con propiedades reales. Dashboard de tiempo de respuesta por agente. Conversaciones etiquetadas por estado.",
      "accentColor": "#20A06F"
    },
    {
      "number": "RESULTADO",
      "headline": "Sin cambiar de número ni dejar WhatsApp",
      "body": "Misma infraestructura, diferente estructura. El canal sigue siendo WhatsApp — pero ahora funciona como un canal de ventas real, no como un grupo de chat.",
      "accentColor": "#3B82F6"
    }
  ],
  "ctaText": "¿Su WhatsApp parece grupo de chat más que canal de ventas?",
  "ctaSubtext": "Vea cómo se ve un inbox profesional: trochai.com",
  "sources": [
    "NAR 2025 — nar.realtor",
    "Mike DelPrete 2024 — mikedp.com"
  ],
  "locale": "es",
  "slideIndex": 0
}
```
