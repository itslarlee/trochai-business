# Sábado — Deep Dive: Anatomía de un lead perdido

> Bucket: Authority | Formato: Carousel + long text

---

## LinkedIn Post Caption

Anatomía de un lead perdido — minuto por minuto.

Viernes, 8:47 PM. Un comprador de California escribe a una agencia en Guanacaste: "Hola, vi una casa en Playa Flamingo. ¿Todavía está disponible?"

Lo que pasa después (deslice →):

8:47 PM — El mensaje llega. Nadie en la oficina.
8:48 PM — WhatsApp Business envía: "Gracias por su mensaje, le responderemos pronto."
9:15 PM — El comprador escribe a una segunda agencia.
9:16 PM — La segunda agencia tiene un inbox con bot. El bot responde con 3 propiedades en Flamingo que coinciden con su presupuesto.
9:22 PM — El comprador pide agendar una videollamada con la segunda agencia.
Sábado 9:00 AM — Un agente de la primera agencia ve el mensaje. Responde: "¡Hola! Sí, todavía está disponible."
Sábado 9:01 AM — El comprador ya tiene videollamada con la otra agencia a las 10 AM.

Tiempo total perdido: 12 horas y 14 minutos.
Comisión perdida: ~$7,500.

No fue por falta de inventario. No fue por falta de experiencia. Fue por 12 horas sin respuesta.

El 78% de los compradores trabaja con el primer agente que responde (NAR 2025). La primera agencia tenía la propiedad perfecta. Pero la segunda respondió primero.

Esta historia se repite cada fin de semana en agencias de todo Costa Rica. ¿La suya incluida?

Fuentes:
- NAR 2025 — 78% compran con el primer agente que responde (nar.realtor)
- NAR/Zillow 2025 — 62% de leads llegan fuera de horario (zillow.com/research)
- Real Trends 2025 — $7,500 comisión promedio perdida por lead ignorado (realtrends.com)

#BienesRaíces #WhatsApp #LeadManagement #CostaRica #PropTech #Trochai

---

## Visual Spec — Pillar Carousel (PillarCarousel)

**Composition type:** `PillarCarousel` (1080x1350, multi-slide)
**Composition ID prefix:** `Pillar-Lead-Anatomy-W16`
**Total slides:** 8 (cover + 6 timeline + CTA)

```json
{
  "slug": "lead-anatomy-w16",
  "title": "Anatomía de un lead perdido",
  "subtitle": "Minuto por minuto: cómo se pierde una comisión de $7,500",
  "slides": [
    {
      "number": "8:47 PM",
      "headline": "El mensaje llega",
      "body": "Un comprador de California escribe: '¿Todavía está disponible la casa en Flamingo?' Nadie en la oficina. WhatsApp Business: 'Le responderemos pronto.'",
      "accentColor": "#F59E0B"
    },
    {
      "number": "9:15 PM",
      "headline": "28 minutos sin respuesta real",
      "body": "El comprador no espera. Escribe a una segunda agencia. Cada minuto sin respuesta, la probabilidad de conversión cae.",
      "accentColor": "#EF4444"
    },
    {
      "number": "9:16 PM",
      "headline": "La segunda agencia responde en <2 min",
      "body": "Un bot de IA busca en el inventario y responde con 3 propiedades en Flamingo que coinciden con su presupuesto. Con fotos y precios.",
      "accentColor": "#20A06F"
    },
    {
      "number": "9:22 PM",
      "headline": "Videollamada agendada",
      "body": "El comprador pide agendar una videollamada para el sábado a las 10 AM. Todo sin intervención humana.",
      "accentColor": "#20A06F"
    },
    {
      "number": "9:00 AM +1",
      "headline": "12 horas después, la primera agencia responde",
      "body": "'¡Hola! Sí, todavía está disponible.' Pero el comprador ya tiene cita con otra agencia. Tenían la propiedad perfecta. Respondieron segundo.",
      "accentColor": "#EF4444"
    },
    {
      "number": "$7,500",
      "headline": "Comisión perdida",
      "body": "No fue por falta de inventario ni experiencia. Fue por 12 horas sin respuesta. El 78% de compradores eligen al primer agente que responde.",
      "accentColor": "#EF4444"
    }
  ],
  "ctaText": "¿Cuántos leads pierde su agencia cada fin de semana?",
  "ctaSubtext": "Conozca cómo las agencias eliminan este problema: trochai.com",
  "sources": [
    "NAR 2025 — nar.realtor",
    "NAR/Zillow 2025 — zillow.com/research",
    "Real Trends 2025 — realtrends.com"
  ],
  "locale": "es",
  "slideIndex": 0
}
```
