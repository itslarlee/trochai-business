# Miércoles (cuenta personal de Leeren) — Soy costarricense. Esto me llamó la atención.

> Bucket: Personal (founder) | Formato: Carousel (7 slides)
> Account: Leeren Wu (personal LinkedIn), NOT Trochai company
> Complementa al Trochai Wed company post (4 países, Pillar-Regional-W17) el mismo día, desde ángulo personal

---

## LinkedIn Post Caption (personal account)

Soy costarricense.

Crecí escuchando que éramos la "Silicon Valley de Centroamérica." Que exportábamos ingenieros a las mejores empresas del mundo. Que Intel, Microsoft, y HP abrían operaciones aquí porque éramos distintos.

Todo eso sigue siendo cierto. 16 de las 100 top tech companies globales operan en Costa Rica. Exportamos el doble de servicios que el promedio OECD. La infraestructura existe.

Pero esta semana estuve mirando los datos de PropTech en la región, y algo me llamó la atención: nuestros vecinos están construyendo cosas impresionantes.

→ En 🇲🇽 México, Habi se convirtió en el primer PropTech unicornio de habla hispana. Pulppo automatiza el 75% del trabajo operativo del corredor con WhatsApp + IA. Felicitaciones al ecosistema mexicano por lo que han construido.

→ En 🇵🇦 Panamá, Acobir MLS consolida 400+ agencias bajo un solo sistema desde hace años. Un referente institucional admirable.

→ En 🇸🇻 El Salvador, aprobaron la primera ley de IA de Latinoamérica en febrero. Y Propi, PropTech local respaldada por Second Century Ventures (NAR), acaba de anunciar expansión regional con Costa Rica en su roadmap. Felicitaciones enormes al equipo y al país.

Mientras tanto, en Costa Rica:
→ El corredor de bienes raíces no requiere licencia (la certificación es voluntaria)
→ Solo aprox. 32% de transacciones usa un agente certificado
→ El MLS nacional sigue en fase de alianza institucional
→ La mayoría de agencias operan con WhatsApp personal + Excel

Lo que me deja pensando no es una comparación — es una invitación. Tenemos la capacidad. Tenemos la gente. Tenemos la infraestructura. Nos falta decidir aplicarla a nuestro propio sector inmobiliario.

No necesitamos inventar nada nuevo. La tecnología existe. WhatsApp Business API existe. Los bots con IA existen. Los dashboards de métricas existen.

Lo que necesitamos es que el sector decida adoptarlo — agencia por agencia.

Por eso construyo Trochai.

¿Ustedes qué piensan sobre el estado del sector? Me gustaría leer sus perspectivas — en comentarios o por DM.

Fuentes:
- https://quatro.legal/estan-los-corredores-y-empresas-de-bienes-raices-bajo-alguna-supervision-gubernamental/
- https://www.larepublica.net/noticia/la-necesaria-regulacion-de-los-agentes-de-bienes-raices-en-costa-rica
- https://www.bloomberglinea.com/latinoamerica/el-salvador/la-salvadorena-propi-logra-us42-millones-para-expandir-su-plataforma-inmobiliaria-en-la-region/
- https://networkreadinessindex.org/country/costa-rica/

#BuildingInPublic #SaaS #PropTech #CostaRica #Centroamérica #FounderJourney

---

## Visual Spec — Pillar Carousel

**Composition type:** `PillarCarousel` (1080x1350, multi-slide)
**Composition ID prefix:** `Pillar-Personal-Leeren-W17`
**Total slides:** 7 (cover + 5 content + CTA)

```json
{
  "slug": "personal-leeren-w17",
  "title": "Soy costarricense. Esto me llamó la atención esta semana.",
  "subtitle": "Una reflexión sobre dónde está nuestro sector inmobiliario.",
  "slides": [
    {
      "number": "🇨🇷 CR",
      "headline": "Crecimos como la Silicon Valley de Centroamérica",
      "body": "16 de las 100 top tech companies globales operan aquí. Exportamos el doble de servicios que el promedio OECD. #42 global en Network Readiness Index — el mejor de la comparación.",
      "accentColor": "#20A06F"
    },
    {
      "number": "$4.2M",
      "headline": "Propi levantó $4.2M con plan de entrar a Costa Rica",
      "body": "PropTech salvadoreña respaldada por Second Century Ventures (NAR). Plan de expansión oficial: Honduras, RD, y Costa Rica. Felicitaciones al equipo.",
      "accentColor": "#4F46E5"
    },
    {
      "number": "REGIÓN",
      "headline": "Felicitaciones a nuestros vecinos",
      "body": "México: Pulppo automatiza el 75% del trabajo del corredor. Panamá: Acobir MLS con 400+ agencias consolidadas desde hace años. El Salvador: primera ley de IA de Latinoamérica. Construcciones admirables, cada una a su modo.",
      "accentColor": "#F59E0B"
    },
    {
      "number": "🇨🇷 HOY",
      "headline": "Infraestructura fuerte. Aplicación pendiente.",
      "body": "92.6% de penetración de internet. 91% de WhatsApp. Pero la certificación del corredor sigue voluntaria, y el MLS nacional en fase de alianza institucional.",
      "accentColor": "#EF4444"
    },
    {
      "number": "→",
      "headline": "Por eso construyo Trochai",
      "body": "Tenemos la capacidad, la gente y la infraestructura. Nos falta decidir aplicarla a nuestro propio sector inmobiliario. No hay que inventar nada nuevo — la tecnología ya existe.",
      "accentColor": "#20A06F"
    }
  ],
  "ctaText": "¿Ustedes qué piensan sobre el estado del sector?",
  "ctaSubtext": "Me gustaría leer sus perspectivas — en comentarios o por DM.",
  "sources": [
    "CINDE — cinde.org",
    "NRI 2025 — networkreadinessindex.org",
    "Bloomberg Línea 2026",
    "Quatro Legal + La República (CCCBR 2024)"
  ],
  "locale": "es",
  "slideIndex": 0
}
```
