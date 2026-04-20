# Sábado — Anatomía de una desventaja: cómo Costa Rica perdió la carrera PropTech (y cómo la recupera)

> Bucket: Authority | Formato: Carousel + long text

---

## LinkedIn Post Caption

Anatomía de una desventaja: cómo Costa Rica pasó de "Silicon Valley centroamericana" a que una PropTech salvadoreña tenga a nuestro mercado en su roadmap de expansión.

No es una sola cosa. Es un conjunto de decisiones (y no-decisiones) a lo largo de diez años.

Línea de tiempo (deslice →):

**2016–2019 — El Salvador y Panamá empiezan a moverse.**
- Panamá consolida Acobir MLS bajo una sola plataforma (400+ agencias).
- México incuba los primeros PropTechs que luego serán Habi, Pulppo, La Haus, Morada Uno.
- Costa Rica sigue siendo el referente ICT de la región — exportamos software al mundo y eso es suficiente.

**2021 — El Salvador pivota con fuerza.**
- Aprueba la Ley Bitcoin. El mundo discute si es buena idea, pero el capital empieza a mirar al país.
- Las propiedades en El Zonte suben 134.8% en cuatro años (de $34/m² a $80/m²).
- Costa Rica sigue su curso — sólido, pero sin cambios estructurales en el sector inmobiliario local.

**2022 — México consolida.**
- Habi se convierte en el primer PropTech unicornio de habla hispana ($1B de valuación, Serie C de $200M).
- Pulppo empieza a automatizar el 75% de las tareas del corredor con WhatsApp + IA.
- Costa Rica: el corredor de bienes raíces sigue sin requerir licencia.

**Abril 2024 — Google llega a El Salvador.**
- Acuerdo de ~$500M en siete años para digitalizar el gobierno. Data center anunciado. Street View en curso.
- Gigantes de la tecnología empiezan a tratar a El Salvador como hub, no como mercado secundario.

**Febrero 2025 — El Salvador aprueba la primera ley de IA de Latinoamérica.**
- Costa Rica no ha aprobado una ley equivalente.

**Junio 2025 — El Salvador, primer país con despliegue soberano de chips NVIDIA B300.**
- Laboratorio Nacional de IA en operación.

**Agosto-Septiembre 2025 — CoreNest lanza fondo tokenizado de $25M en El Salvador.**
- Plan de seguimiento: $100M para hacer del país "el Silicon Valley de Latinoamérica."

**Septiembre 2025 — Costa Rica cae 2 puestos en el Índice Global de Innovación.**
- Ahora somos #72 globales, #6 en Latinoamérica. Nos superan Chile, Brasil, México, Uruguay, Colombia.

**Diciembre 2025 — El Salvador + xAI de Elon Musk.**
- Despliegue de Grok en 5,000 escuelas públicas. Primer programa nacional de educación con IA del mundo.

**Febrero 2026 — Propi cierra su expansión regional.**
- $4.2M de Second Century Ventures. Plan textual: Honduras, RD, y Costa Rica.

**Marzo 2026 — Habi adquiere Pulppo.**
- Volumen combinado $1B+ en transacciones 2025. Consolidación PropTech en LatAm acelera.

**Hoy — Abril 2026.**
- Costa Rica sigue siendo #42 global en Network Readiness Index (mejor que los tres países mencionados).
- Pero el pilar "Technology" nos ubica en #67 — clara brecha entre potencial y aplicación.
- 91% de penetración WhatsApp. Solo ~32% de transacciones con agente certificado. Contradicción estructural.

**Cómo se recupera.**
- Profesionalizando la regulación (CCCBR como estándar obligatorio, no voluntario).
- Adoptando la arquitectura que ya funciona en la región (no hay que inventar nada).
- Empezando por el canal donde el lead llega: WhatsApp, pero como canal de ventas con estructura.
- Decidiendo, agencia por agencia, que el default ya no puede ser "WhatsApp personal + Excel."

Costa Rica tiene todos los ingredientes. Lo que falta es que el sector inmobiliario decida aplicarlos antes de que otro lo decida por nosotros.

Fuentes: bloomberglinea.com, loc.gov, bidlab.org, revistasumma.com, therealdeal.com, networkreadinessindex.org, larepublica.net

#BienesRaíces #CostaRica #PropTech #Centroamérica #ElSalvador #Panama #Mexico #IA #Trochai

---

## Visual Spec — Pillar Carousel (PillarCarousel)

**Composition type:** `PillarCarousel` (1080x1350, multi-slide)
**Composition ID prefix:** `Pillar-Timeline-W17`
**Total slides:** 9 (cover + 7 timeline milestones + CTA)

```json
{
  "slug": "timeline-w17",
  "title": "Cómo Costa Rica perdió la carrera PropTech",
  "subtitle": "10 años de decisiones (y no-decisiones) en una línea de tiempo.",
  "slides": [
    {
      "number": "2016–19",
      "headline": "La región empieza a moverse",
      "body": "Panamá consolida Acobir MLS (400+ agencias). México incuba lo que será Habi, Pulppo, La Haus. Costa Rica sigue siendo referente ICT — exportar software al mundo es suficiente.",
      "accentColor": "#64748B"
    },
    {
      "number": "2022",
      "headline": "México consolida — Habi unicornio",
      "body": "Habi alcanza $1B de valuación con Serie C de $200M. Pulppo empieza a automatizar 75% del trabajo del corredor. Costa Rica: el corredor sigue sin requerir licencia.",
      "accentColor": "#10B981"
    },
    {
      "number": "ABR 2024",
      "headline": "Google llega a El Salvador",
      "body": "Acuerdo de aprox. $500M en siete años. Data center, Street View, digitalización del gobierno. El Salvador pasa a ser hub regional, no mercado secundario.",
      "accentColor": "#F59E0B"
    },
    {
      "number": "FEB 2025",
      "headline": "Primera ley de IA de Latinoamérica",
      "body": "El Salvador aprueba la Ley de Promoción de Inteligencia Artificial. Crea ANIA. Costa Rica aún no tiene ley equivalente.",
      "accentColor": "#F59E0B"
    },
    {
      "number": "SEP 2025",
      "headline": "CR cae 2 puestos en Índice Global de Innovación",
      "body": "Ahora #72 global, #6 LatAm. Nos superan Chile, Brasil, México, Uruguay, Colombia. Primera señal clara de que el liderazgo regional no es permanente.",
      "accentColor": "#EF4444"
    },
    {
      "number": "FEB 2026",
      "headline": "Propi cierra expansión a Costa Rica",
      "body": "PropTech salvadoreña levanta $4.2M con Second Century Ventures (NAR). Plan textual: Honduras, RD, y Costa Rica. Ya maneja $300M+ en operaciones digitales.",
      "accentColor": "#4F46E5"
    },
    {
      "number": "HOY",
      "headline": "La decisión está frente a cada agencia",
      "body": "CR sigue #42 en NRI global (mejor que ES, PA, MX). Pero pilar Technology #67. La brecha no es infraestructura — es aplicación al sector inmobiliario local.",
      "accentColor": "#20A06F"
    }
  ],
  "ctaText": "La región ya construyó la arquitectura. Costa Rica decide si la aplica.",
  "ctaSubtext": "Vea cómo se ve aplicada al mercado local: trochai.com",
  "sources": [
    "Bloomberg Línea 2026",
    "NRI 2025 — networkreadinessindex.org",
    "Revista Summa 2025",
    "Library of Congress 2025"
  ],
  "locale": "es",
  "slideIndex": 0
}
```
