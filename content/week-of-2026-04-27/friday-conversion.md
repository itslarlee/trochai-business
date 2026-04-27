# Viernes — Trochai Coexistence: qué incluye y qué NO hace (incluido en Pro/Enterprise, sin add-on fee)

> Bucket: Conversion | Formato: Carousel (product positioning) | **SIN mención de descuento (post-30 abril)**

---

## LinkedIn Post Caption

Esta semana hablamos del problema (el falso dilema), de la arquitectura (5 pasos, directo con Meta), y del costo de no resolverlo. Hoy toca hablar del producto.

Trochai Coexistence — qué incluye, qué cuesta, qué NO hace. Sin marketing, descripción directa (deslice →):

📦 **Qué incluye:**
→ Conexión directa al WhatsApp Cloud API de Meta — Trochai es Meta Tech Provider, sin BSPs intermedios.
→ Onboarding oficial de Meta — el dueño escanea un QR desde la WhatsApp Business app del celular y queda conectado. Sin migrar número, sin re-instalar nada.
→ Eco bidireccional de mensajes 1:1 entre la WhatsApp Business app del agente y el inbox Trochai.
→ Importación automática de hasta 6 meses de historial al onboardear.
→ Auto-pausa del bot cuando el humano respondió desde el celular.
→ Mismo bot de IA, mismas plantillas, misma asignación, mismas métricas que Trochai Inbox estándar.

💵 **Qué cuesta — incluido en Pro y Enterprise, sin add-on fee:**
→ **Coexistence está incluido sin costo adicional** en los planes Pro y Enterprise. No cobramos por número.
→ ¿Por qué? Cuando un proveedor usa un BSP (360dialog, Twilio, Wati), tiene que cobrar por número para cubrir la fee del BSP — eso es estructural. Trochai va directo con Meta como Tech Provider, así que no tenemos esa fee. Y como no la tenemos, no se la pasamos al cliente.
→ Tarifas de mensajes de Meta (~$0.03–0.08 por conversación, según país) sí se pasan como pass-through (igual que con cualquier proveedor — esas las cobra Meta).
→ Trochai Inbox estándar (Cloud API directo, sin coexistence) sigue disponible en planes inferiores.

🎯 **Para quién tiene sentido:**
→ Agencias con 3 o más agentes activos en WhatsApp Business app que **no quieren obligar al equipo a cambiar de app**.
→ Equipos que ya manejan el WhatsApp Business app diariamente — versión 2.24.17+.
→ Agencias con leads expatriados que esperan respuesta fuera de horario CR (necesitan el bot).

🚫 **Qué NO hace coexistence (sea claro con su equipo):**
→ **Llamadas de voz/video:** quedan en la app del agente, NO se sincronizan a Trochai. (Esto es bueno — el agente las sigue haciendo desde su celular como siempre.)
→ **Grupos:** quedan en la app del agente, los mensajes de grupo NO aparecen en el inbox Trochai. (Limitación oficial de Meta — los grupos siguen en el celular del agente.)
→ **Listas de difusión nuevas:** una vez activada coexistence, no se pueden crear listas de difusión nuevas desde la app. Las existentes siguen funcionando.
→ **Dispositivos compañeros:** WhatsApp Business app permite hasta 4 dispositivos compañeros (Web móvil, otros teléfonos vinculados) además del celular principal. Al activar coexistence, todos los compañeros se desvinculan y luego solo se pueden re-vincular los compatibles. **WhatsApp para Windows y WearOS NO son compatibles con coexistence** — esos quedan permanentemente fuera. Mensajes enviados desde dispositivos no compatibles no se sincronizan al inbox.
→ **Insignia azul (OBA):** los números coexistence no pueden tener verificación OBA. Alternativa: Meta Verified for Business (suscripción separada).
→ **Límite inicial de mensajes "business-initiated":** 250 conversaciones por 24h al arrancar (escalable según calidad de mensajería con Meta).

📅 **Cuándo:**
Lanzamiento incluido en Pro y Enterprise — fecha tentativa **late May 2026**. Lista de espera abre el upgrade temprano y prioridad de onboarding.

Lista de espera: trochai.com

¿Cuántos agentes tiene en WhatsApp Business hoy? Eso es lo más útil para entender si coexistence le encaja.

Fuentes:
- https://developers.facebook.com/documentation/business-messaging/whatsapp/embedded-signup/onboarding-business-app-users/
- Trochai — Coexistence Research Findings (Apr 2026)

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
