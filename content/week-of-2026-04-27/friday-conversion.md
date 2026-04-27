# Viernes — Trochai Coexistence: qué incluye y qué NO hace (incluido en Pro/Enterprise, sin add-on fee)

> Bucket: Conversion | Formato: Carousel (product positioning) | **SIN mención de descuento (post-30 abril)**

---

## LinkedIn Post Caption

Esta semana hablamos del problema (el falso dilema), de la arquitectura (5 pasos, directo con Meta) y del costo. Hoy toca producto.

Trochai Coexistence — qué incluye, qué cuesta, qué NO hace. Sin marketing (deslice →):

📦 **Qué incluye:**
→ Conexión directa al Cloud API de Meta — Trochai es Meta Tech Provider, sin BSPs intermedios.
→ Onboarding oficial de Meta — el dueño escanea un QR desde la WhatsApp Business app y queda conectado. Sin migrar número, sin reinstalar.
→ Eco bidireccional 1:1 entre la app del agente y el inbox Trochai.
→ Importación de hasta 6 meses de historial al onboardear.
→ Auto-pausa del bot cuando el humano respondió desde el celular.
→ Mismo bot de IA, plantillas, asignación y métricas que Trochai estándar.

💵 **Qué cuesta — incluido en Pro y Enterprise, sin add-on fee:**
→ **Coexistence está incluido sin costo adicional.** No cobramos por número.
→ ¿Por qué? Un BSP (360dialog, Twilio, Wati) tiene que cobrar por número para cubrir su propio fee — es estructural. Trochai va directo con Meta como Tech Provider, así que no tenemos esa fee y no se la pasamos al cliente.
→ Tarifas de mensajes de Meta (~$0.03–0.08/conversación) son pass-through, igual que con cualquier proveedor.

🎯 **Para quién:**
→ Agencias con 3 o más agentes activos en WhatsApp Business app que **no quieren forzar al equipo a cambiar de app**.
→ Equipos que usan la app diariamente (v2.24.17+).
→ Agencias con leads expatriados fuera de horario CR.

🚫 **Qué NO hace (sea claro con su equipo):**
→ **Llamadas de voz/video:** quedan en la app del agente. (Bueno — las sigue haciendo desde el celular como siempre.)
→ **Grupos:** en la app, no aparecen en el inbox (limitación oficial de Meta).
→ **Hasta 4 dispositivos compañeros** — WhatsApp Web/Mobile sí, **Windows y WearOS NO**.
→ **Sin insignia OBA** (use Meta Verified como alternativa).
→ **Listas de difusión nuevas:** no se pueden crear post-activación. Las existentes siguen.
→ **Límite inicial:** 250 mensajes business-initiated/24h, escalable.

📅 Lanzamiento **late May 2026** — incluido en Pro y Enterprise. Lista de espera (prioridad de onboarding): trochai.com

¿Cuántos agentes tiene en WhatsApp Business hoy? Eso es lo más útil para saber si coexistence le encaja.

#Coexistence #WhatsApp #BienesRaíces #CostaRica #PropTech #Trochai

---

## Visual Spec — Pillar Carousel (PillarCarousel)

**Composition type:** `PillarCarousel` (1080x1350, multi-slide)
**Composition ID prefix:** `Pillar-Coexistence-Product-W18`
**Total slides:** 6 (cover + 4 detail slides + CTA)

```json
{
  "slug": "coexistence-product-w18",
  "title": "Trochai Coexistence — el add-on",
  "subtitle": "Qué incluye, qué cuesta, qué NO hace. Descripción directa.",
  "slides": [
    {
      "number": "01",
      "headline": "Qué incluye",
      "body": "Conexión directa al Cloud API de Meta (Trochai es Meta Tech Provider, sin BSP). Onboarding Embedded Signup oficial. Eco bidireccional 1:1 entre la WhatsApp Business app y el inbox. Hasta 6 meses de historial al onboardear. Auto-pausa del bot cuando responde un humano.",
      "accentColor": "#25D366"
    },
    {
      "number": "02",
      "headline": "Qué cuesta — incluido en Pro/Enterprise",
      "body": "Coexistence está incluido sin costo adicional en planes Pro y Enterprise. No cobramos por número. Trochai va directo con Meta como Tech Provider — sin fee de BSP que pasarle al cliente. Solo las tarifas de mensajes de Meta como pass-through.",
      "accentColor": "#20A06F"
    },
    {
      "number": "03",
      "headline": "Qué NO hace (sea claro con su equipo)",
      "body": "Llamadas de voz/video: en la app del agente, no en Trochai. Grupos: en la app, no aparecen en el inbox. Hasta 4 dispositivos compañeros — Windows y WearOS NO son compatibles. OBA blue badge: no disponible (use Meta Verified). Límite inicial: 250 mensajes business-initiated/24h.",
      "accentColor": "#F59E0B"
    },
    {
      "number": "04",
      "headline": "Para quién tiene sentido",
      "body": "Agencias con 3 o más agentes activos en WhatsApp Business app que no quieren obligar al equipo a cambiar de app. Versión 2.24.17+. Equipos con leads expatriados fuera de horario CR (necesitan el bot).",
      "accentColor": "#3B82F6"
    }
  ],
  "ctaText": "Incluido en Pro y Enterprise — sin add-on fee. Lanzamiento late May 2026.",
  "ctaSubtext": "Lista de espera (prioridad de onboarding): trochai.com",
  "sources": [
    "Meta — Embedded Signup Coexistence",
    "Trochai — Coexistence Research Findings (Apr 2026)"
  ],
  "locale": "es",
  "slideIndex": 0
}
```
