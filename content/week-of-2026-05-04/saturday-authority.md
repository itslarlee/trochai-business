# Sábado — 4 preguntas antes de hacer un sitio web inmobiliario en 2026

> Bucket: Authority | Formato: Pillar carousel multi-slide + long text deep-dive | Mención promo mayo (sin urgencia)

---

## LinkedIn Post Caption

Antes de invertir en cualquier sitio web inmobiliario en 2026 — Trochai Sites, WordPress, plantilla genérica, cualquiera — hágase estas 4 preguntas.

Si responde mal aunque sea una, no tiene sentido empezar todavía. Un sitio mal arquitecturado cuesta más que no tener sitio.

(Deslice →)

**1. ¿Su inventario tiene una sola fuente de verdad hoy?**
Si está distribuido entre varias superficies (MLS, portales, WhatsApp, IG, sitio anterior), agregar un sitio nuevo es agregar otra superficie al stack. La pregunta arquitectónica es cuál de las superficies va a ser la fuente — no agregar otro canal de salida sobre fuentes desconectadas.

**2. ¿Quiere que el bot de WhatsApp y el sitio respondan con el mismo catálogo?**
Si la respuesta es sí, el sitio tiene que compartir la base de datos del Inbox — no sincronizarse con ella vía API o importar/exportar. La diferencia es que "compartir" es un evento atómico (escribís una vez, todos leen); "sincronizar" siempre tiene un delay y siempre tiene errores.

**3. ¿Cuánto tiempo de su semana puede dedicar a mantener el sitio actualizado?**
Si la respuesta honesta es "muy poco" — y es la respuesta de la mayoría — entonces el sitio tiene que actualizarse solo. No con disciplina, no con voluntad, no con "le vamos a dar mantenimiento mensual". Tiene que actualizarse porque la arquitectura no le da otra opción.

**4. ¿Quiere un sitio único, o uno que parece de plantilla?**
Cuatro plantillas elegidas (Esmeralda, Sable, Sabana, Aleteo) con identidad visual real, no un WordPress genérico que se ve igual al de la agencia de al lado. Si el visual no diferencia, es ruido más que ayuda — el cliente confía menos cuando todos los sitios se ven iguales.

—

**Y si está empezando como agente solo:**

Las 4 preguntas son para agencias con equipo y catálogo. Si trabaja solo con menos de 10 propiedades activas, probablemente no necesita un sitio dedicado — necesita un perfil bien curado, fotos de calidad, y un WhatsApp que responda 24/7. El bot del Inbox puede empezar ahí, sin sitio. Cuando crezca, el sitio se agrega encima sin migrar nada.

—

Este es el filtro que usamos en discovery. Vender un sitio a una agencia que no está lista es la peor forma de quemar relación.

Promo de mayo si después de esas 4 preguntas decide avanzar: plan anual de Trochai Inbox = sitio web gratis ($2,500–$4,500 según template). Solo mayo. Sin urgencia falsa — la promo se queda hasta el 31, no hay countdown.

¿Qué pregunta agregaría a esta lista? Comente con la suya.

#TrochaiSites #BienesRaíces #CostaRica #PropTech #TransformaciónDigital

---

## Visual Spec — Pillar Carousel (PillarCarousel)

**Composition type:** `PillarCarousel` (1080x1350, multi-slide)
**Composition ID prefix:** `Pillar-SitesChecklist-W19`
**Total slides:** 7 (cover + 4 questions + 1 solo-agent slide + CTA)

```json
{
  "slug": "sites-checklist-w19",
  "title": "4 preguntas antes de hacer su sitio inmobiliario",
  "subtitle": "Si responde mal aunque sea una, esperar es más barato que avanzar. Filtro real, sin marketing.",
  "slides": [
    {
      "number": "01",
      "headline": "¿Su inventario tiene una sola fuente de verdad?",
      "body": "Si vive distribuido entre varias superficies (MLS, portales, WhatsApp, IG, sitio anterior), agregar un sitio nuevo es agregar otra. La pregunta arquitectónica es cuál de las superficies va a ser la fuente — no sumar otro canal sobre fuentes desconectadas.",
      "accentColor": "#20A06F"
    },
    {
      "number": "02",
      "headline": "¿El bot y el sitio deben responder con el mismo catálogo?",
      "body": "Si sí: el sitio tiene que compartir la base de datos del Inbox — no sincronizarse vía API o importar/exportar. 'Compartir' es atómico (escribís una vez, todos leen). 'Sincronizar' siempre tiene delay y siempre tiene errores.",
      "accentColor": "#3B82F6"
    },
    {
      "number": "03",
      "headline": "¿Cuánto tiempo de su semana para mantenerlo al día?",
      "body": "Si la respuesta honesta es 'poco' — y es la respuesta de la mayoría — el sitio tiene que actualizarse solo. No con disciplina, no con voluntad, no con 'mantenimiento mensual'. Por arquitectura, no por esfuerzo.",
      "accentColor": "#8B5CF6"
    },
    {
      "number": "04",
      "headline": "¿Único, o de plantilla?",
      "body": "Cuatro plantillas elegidas (Esmeralda, Sable, Sabana, Aleteo) con identidad visual real, no un WordPress genérico. Si el visual no diferencia, es ruido más que ayuda — el cliente confía menos cuando todos los sitios se ven iguales.",
      "accentColor": "#EC4899"
    },
    {
      "number": "BONUS",
      "headline": "¿Es agente solo? Quizá no necesita sitio todavía.",
      "body": "Si trabaja solo con <10 propiedades activas, no necesita sitio dedicado. Necesita perfil curado + fotos de calidad + WhatsApp que responde 24/7. El bot del Inbox puede empezar ahí. Cuando crezca, el sitio se agrega encima sin migrar nada.",
      "accentColor": "#F59E0B"
    }
  ],
  "ctaText": "Si las 4 respuestas le encajan, el sitio acelera. Si no, esperar es más barato.",
  "ctaSubtext": "Promo mayo: annual Inbox = sitio gratis. Sin countdown — hasta 31 may. trochai.com/contacto",
  "sources": [
    "Trochai — discovery calls Q1–Q2 2026 (n=20+ agencias)",
    "Trochai Sites — POSITIONING-ONE-LINERS.md (2026-04-29)"
  ],
  "locale": "es",
  "slideIndex": 0
}
```
