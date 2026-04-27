# Miércoles — Cómo funciona Trochai Coexistence: 5 pasos, sin BSP, directo con Meta

> Bucket: Authority | Formato: Multi-slide carousel (educational framework)

---

## LinkedIn Post Caption

Coexistence parece magia hasta que entiende cómo funciona. Después es obvio.

Lo voy a explicar como se lo explico a una agencia en una llamada de 20 minutos. Si maneja una agencia con 3 o más agentes en WhatsApp Business, esto le va a doler menos que la migración (deslice →):

🏷️ **Paso 1 — Sin intermediarios. Trochai conecta directo con Meta.**
Trochai es **Meta Tech Provider aprobado**. Eso significa que conectamos su número directamente al Cloud API de Meta — sin BSPs (360dialog, Twilio, Wati), sin proxies, sin capas extra. Menos puntos de falla, mejor margen, sin lock-in con un proveedor externo.

🔌 **Paso 2 — Onboarding oficial de Meta, no migración.**
El dueño de la agencia inicia sesión con su Facebook Business, escanea un QR desde la WhatsApp Business app del celular, y la conexión queda hecha. Sin migrar el número, sin perder contactos, sin reinstalar nada. El equipo no nota nada.

📥 **Paso 3 — Los mensajes aparecen en ambas interfaces, en tiempo real.**
Cuando entra un mensaje, aparece simultáneamente en la WhatsApp Business app del agente y en el inbox Trochai. Cuando el agente responde desde su celular, ese mensaje saliente se sincroniza al inbox con la atribución correcta del agente.

📜 **Paso 4 — Importamos hasta 6 meses de historial al onboardear.**
Durante el onboarding, Meta entrega todas las conversaciones previas (texto + media reciente) al inbox Trochai. La gerencia entra con el contexto completo desde el día uno — no empieza vacío.

⏸️ **Paso 5 — El bot se auto-pausa cuando un humano respondió desde el celular.**
Cuando el agente responde desde su celular, el bot detecta que un humano tomó la conversación y se pausa para no pisarla. El agente puede re-activar el bot con un click cuando termine.

El resultado neto:

→ El agente sigue usando la app que conoce. **Llamadas, grupos y stickers siguen funcionando en su celular** (la app es la app — coexistence no la toca).
→ La agencia gana visibilidad total — métricas, búsqueda, asignación, AI fuera de horario, plantillas aprobadas.
→ El cliente no nota nada — sigue escribiendo al mismo número.
→ La adopción interna deja de ser el cuello de botella.

Coexistence no es un feature de marketing. Es una decisión arquitectónica. Y al ir directo con Meta — sin BSP intermedio — el costo es más bajo y la operación es más simple.

Lanzamiento como add-on en planes Pro y Enterprise — late May 2026 (~30 días). Lista de espera: trochai.com

Guarde este post si maneja una agencia y planea profesionalizar su WhatsApp este año.

(Descuento de lanzamiento del 50% en el primer mes — válido hasta mañana 30 de abril.)

Fuentes:
- https://developers.facebook.com/documentation/business-messaging/whatsapp/embedded-signup/onboarding-business-app-users/
- https://developers.facebook.com/documentation/business-messaging/whatsapp/webhooks/reference/smb_message_echoes/
- Trochai Inbox — Coexistence Research Findings (Apr 2026)

#Coexistence #WhatsApp #PropTech #BienesRaíces #CostaRica #Trochai

---

## Visual Spec — Pillar Carousel (PillarCarousel)

**Composition type:** `PillarCarousel` (1080x1350, multi-slide)
**Composition ID prefix:** `Pillar-Coexistence-Howto-W18`
**Total slides:** 7 (cover + 5 step slides + CTA)

```json
{
  "slug": "coexistence-howto-w18",
  "title": "Coexistence en 5 pasos",
  "subtitle": "Trochai es Meta Tech Provider — conexión directa al Cloud API, sin BSP intermedio.",
  "slides": [
    {
      "number": "01",
      "headline": "Sin intermediarios — directo con Meta",
      "body": "Trochai es Meta Tech Provider aprobado. Conectamos el número directamente al Cloud API de Meta. Sin BSPs (360dialog, Twilio, Wati), sin proxies. Menos puntos de falla, mejor margen, sin lock-in con un tercero.",
      "accentColor": "#1877F2"
    },
    {
      "number": "02",
      "headline": "Onboarding oficial de Meta — no migración",
      "body": "El dueño inicia sesión con su Facebook Business, escanea un QR desde la WhatsApp Business app del celular, y queda conectado. Sin migrar número, sin perder contactos, sin reinstalar nada. El equipo no nota nada.",
      "accentColor": "#25D366"
    },
    {
      "number": "03",
      "headline": "Mensajes en ambas interfaces, tiempo real",
      "body": "Cuando entra un mensaje, aparece simultáneamente en la WhatsApp Business app del agente y en el inbox Trochai. Cuando el agente responde desde el celular, ese mensaje se sincroniza al inbox con su atribución correcta.",
      "accentColor": "#20A06F"
    },
    {
      "number": "04",
      "headline": "6 meses de historial al onboardear",
      "body": "Durante el onboarding, Meta entrega todas las conversaciones previas (texto + media reciente) al inbox Trochai. La gerencia entra con el contexto completo desde el día uno — no empieza vacío.",
      "accentColor": "#8B5CF6"
    },
    {
      "number": "05",
      "headline": "Bot auto-pausa al responder humano",
      "body": "Cuando el agente responde desde el celular, el bot detecta que un humano tomó la conversación y se pausa. El agente re-activa con un click cuando termine. Sin pisar al equipo.",
      "accentColor": "#F59E0B"
    }
  ],
  "ctaText": "Llamadas, grupos y stickers siguen en la app del agente. La gerencia ve todo en Trochai.",
  "ctaSubtext": "Lanzamiento late May 2026. Lista de espera: trochai.com",
  "sources": [
    "Meta — Embedded Signup (Coexistence)",
    "Meta — smb_message_echoes webhook reference",
    "Trochai — Coexistence Research Findings"
  ],
  "locale": "es",
  "slideIndex": 0
}
```
