# Sábado — 4 preguntas clave antes de centralizar el WhatsApp de su agencia

> Bucket: Authority | Formato: Carousel + long text deep-dive | **SIN mención de descuento**

---

## LinkedIn Post Caption

Antes de invertir en cualquier plataforma para centralizar el WhatsApp de su agencia — Trochai, regional, o cualquier otra — hágase estas 4 preguntas.

Si responde mal aunque sea una, no tiene sentido empezar todavía. Centralizar mal cuesta más que no centralizar.

(Deslice →)

**1. ¿Cuántos agentes activos tiene en WhatsApp Business hoy?**
Si son menos de 3, probablemente no necesita centralizar — necesita templates y disciplina. Una plataforma con 1–2 usuarios es overhead sin ROI. La centralización paga cuando el flujo crece más rápido que la capacidad de la gerencia para verlo todo manualmente.

**2. ¿Sus agentes manejan WhatsApp Business app, o WhatsApp personal?**
Si manejan WhatsApp personal sin separación, el primer paso no es la plataforma — es instalar WhatsApp Business app y separar negocio de lo personal. Es gratis. Sin esa base, centralizar no funciona porque ni el dueño tiene control del número.

**3. ¿Su equipo usa la app para llamadas, grupos, o flujos en el celular que no quiere perder?**
Si sí: necesita coexistence específicamente. Una plataforma sin coexistence requiere que el agente abandone su WhatsApp Business app — y con eso, sus llamadas, sus grupos y su flujo en el celular se complican. Coexistence permite mantener todo eso intacto en el celular y centralizar lo demás. Si su equipo no usa nada de eso, una plataforma estándar (sin coexistence) puede bastar.

**4. ¿Tiene un MLS o inventario digitalizado para que el bot pueda responder?**
Sin inventario estructurado, el bot solo da respuestas genéricas — peor que un humano con delay. Antes (o en paralelo) de centralizar, digitalice el inventario. Las dos inversiones se potencian.

—

**Y si es agente solo o agencia muy chica:**

Las 4 preguntas de arriba están pensadas para agencias con equipo. Pero si trabaja solo o tiene 1–2 personas, coexistence probablemente no aplica — sin embargo, el inbox Trochai con asistente de IA sí.

El asistente AI de Trochai responde a sus leads en menos de 2 minutos, en cualquier idioma (español, inglés, lo que escriba el cliente), 24/7, mostrando propiedades reales de su catálogo con fotos y precios. Funciona aunque esté manejando, en una visita, o durmiendo. No es un chatbot genérico — busca en su inventario y manda lo que tiene disponible.

Para un agente solo, eso es la diferencia entre cerrar leads expatriados que escriben a las 11pm o perderlos hasta la mañana. Trochai estándar (sin coexistence) cubre ese caso completo.

—

Este es el filtro que usamos en discovery con agencias. Si responden mal a una de las 4, les decimos qué resolver primero antes de centralizar. Vender una plataforma a una agencia que no está lista es la peor manera de quemar relación de largo plazo.

Coexistence específicamente resuelve la pregunta #3 — la objeción más común en las agencias costarricenses con equipo establecido. Si la respuesta es 1, 2 o 4, una plataforma no las resuelve por usted. Si trabaja solo, vea el bloque de arriba.

Lanzamiento del add-on coexistence — late May 2026. Lista de espera: trochai.com

¿Qué pregunta agregaría a esta lista? Comente con la suya.

Fuentes:
- https://developers.facebook.com/documentation/business-messaging/whatsapp/embedded-signup/onboarding-business-app-users/
- Trochai — Coexistence Research Findings (Apr 2026)

#BienesRaíces #CostaRica #WhatsApp #PropTech #Coexistence #Trochai

---

## Visual Spec — Pillar Carousel (PillarCarousel)

**Composition type:** `PillarCarousel` (1080x1350, multi-slide)
**Composition ID prefix:** `Pillar-Coexistence-Checklist-W18`
**Total slides:** 7 (cover + 4 questions + 1 solo-agent slide + CTA)

```json
{
  "slug": "coexistence-checklist-w18",
  "title": "4 preguntas antes de centralizar",
  "subtitle": "Si responde mal aunque sea una, centralizar es prematuro. Filtro real, sin marketing.",
  "slides": [
    {
      "number": "01",
      "headline": "¿Cuántos agentes en WhatsApp Business?",
      "body": "Menos de 3, probablemente no necesita centralizar — necesita templates y disciplina. La centralización paga cuando el flujo crece más rápido que la capacidad de la gerencia para verlo todo manualmente.",
      "accentColor": "#25D366"
    },
    {
      "number": "02",
      "headline": "¿Business app o WhatsApp personal?",
      "body": "Si manejan WhatsApp personal sin separación, el primer paso es instalar WhatsApp Business app y separar negocio de lo personal. Sin esa base, ninguna plataforma funciona porque ni el dueño tiene control del número.",
      "accentColor": "#20A06F"
    },
    {
      "number": "03",
      "headline": "¿Usan la app para llamadas, grupos o flujos del celular?",
      "body": "Si sí: necesita coexistence específicamente — el equipo mantiene el celular intacto. Si no: una plataforma estándar (sin coexistence) puede bastar. Esta es la pregunta que define cuál arquitectura le encaja.",
      "accentColor": "#3B82F6"
    },
    {
      "number": "04",
      "headline": "¿Tiene MLS o inventario digitalizado?",
      "body": "Sin inventario estructurado, el bot solo da respuestas genéricas — peor que un humano con delay. Digitalice el inventario antes (o en paralelo) de centralizar. Las dos inversiones se potencian.",
      "accentColor": "#8B5CF6"
    },
    {
      "number": "BONUS",
      "headline": "¿Es agente solo? Coexistence no aplica — Trochai sí.",
      "body": "Si trabaja solo, no necesita centralización. Pero el asistente AI de Trochai responde leads en <2 min, en cualquier idioma, 24/7, mostrando propiedades reales de su catálogo. Sirve cerrando leads expatriados a las 11pm que sin bot se enfrían hasta la mañana.",
      "accentColor": "#EC4899"
    }
  ],
  "ctaText": "Coexistence resuelve la pregunta #3. El resto las resuelve la agencia.",
  "ctaSubtext": "Lanzamiento late May 2026. Lista de espera: trochai.com",
  "sources": [
    "Meta — Embedded Signup Coexistence",
    "Trochai — Coexistence Research Findings (Apr 2026)"
  ],
  "locale": "es",
  "slideIndex": 0
}
```
