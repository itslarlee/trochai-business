# Pillar — Coexistence: su WhatsApp Business app y Trochai en el mismo número

> Pilar de la Sem. 18 (27 abril – 3 mayo, 2026). Lanzamiento del feature: ~late May 2026.

---

## Tesis

La pregunta que toda agencia inmobiliaria con 3 o más agentes se ha hecho al menos una vez:

> "Si centralizamos el WhatsApp de la agencia, ¿mis agentes van a perder su WhatsApp Business app?"

Durante años, la respuesta de la industria fue **sí**. Centralizar significaba migrar todo el equipo a un inbox web — y con eso, el agente perdía la app que ya manejaba a ciegas, las llamadas de voz/video que hacía desde el celular, y los grupos donde vivían sus clientes.

**Coexistence** rompe ese supuesto. Es la arquitectura que permite que el WhatsApp Business app del agente y la plataforma Trochai operen sobre el **mismo número**, simultáneamente. La estamos lanzando como add-on en aprox. 30 días.

Este documento explica qué es, qué problema resuelve, qué NO hace, y cómo encaja con Trochai Inbox.

---

## El falso dilema actual

Hoy una agencia que quiere profesionalizar su canal de WhatsApp tiene dos caminos:

**Opción A — Quedarse con WhatsApp Business app personal.**
- ✅ Agentes cómodos. UX nativa. Audios, stickers, llamadas, grupos.
- ❌ Sin centralización. Sin métricas. Sin asignación. Sin bot. Sin historial cuando el agente renuncia.

**Opción B — Migrar a un inbox web (WhatsApp Business API tradicional).**
- ✅ Centralización total. Métricas, asignación, bot, plantillas aprobadas.
- ❌ El agente pierde su WhatsApp Business app. Las llamadas, los grupos, y la velocidad del celular se complican.
- ❌ La adopción interna se cae. Resultado típico: el equipo termina respondiendo desde otro lado.

Cuando le pides a un agente que migre, no le estás pidiendo que aprenda una herramienta. Le estás pidiendo que renuncie a llamadas, a grupos, y a la velocidad del celular. Por eso muchas migraciones fracasan — no es resistencia al cambio en abstracto, es un cálculo concreto.

Coexistence elimina ese cálculo.

---

## Qué es coexistence (en una línea)

**El mismo número de WhatsApp opera en dos interfaces a la vez: la WhatsApp Business app del agente (en el celular) y el inbox Trochai (en la web/oficina), sincronizadas en tiempo real vía webhooks oficiales de Meta.**

No hay migración de número. No hay app que abandonar. No hay re-entrenamiento del equipo. La capa de centralización (Trochai) corre **encima** del WhatsApp Business app que los agentes ya manejan.

---

## Cómo funciona técnicamente — Trochai es Meta Tech Provider

**Decisión de arquitectura:** Trochai implementa coexistence **directamente sobre Meta Cloud API**, usando su estatus como Meta Tech Provider aprobado. **No hay BSP intermedio** (no 360dialog, no Twilio, no Wati).

A grandes rasgos:

1. **El dueño de la agencia se conecta vía Embedded Signup oficial de Meta** (`featureType: 'whatsapp_business_app_onboarding'`, `sessionInfoVersion: '3'`). Inicia sesión con su Facebook Business, escanea un QR desde la WhatsApp Business app del celular, y la conexión queda hecha.

2. **Meta dispara los webhooks de coexistence directamente al endpoint de Trochai.** Los tres clave:
   - `messages` — mensajes entrantes de clientes (igual que cualquier Cloud API).
   - `smb_message_echoes` — mensajes salientes del agente desde su celular.
   - `smb_app_state_sync` — eventos de sincronización de contactos.
   - `history` — hasta 6 meses de historial al onboardear.

3. **El agente sigue usando su WhatsApp Business app exactamente como hoy.** Cuando responde desde el celular, Meta dispara `smb_message_echoes` y Trochai ve la respuesta en tiempo real con la atribución correcta del agente.

4. **El bot Trochai detecta cuando un humano respondió** (vía `smb_message_echoes` saliente) y se auto-pausa para no pisar la conversación. El agente puede re-activar el bot con un click.

5. **El cliente no nota nada** — sigue escribiendo al mismo número.

**Por qué Tech Provider direct (sin BSP):** Trochai ya tiene los permisos de Meta App (`whatsapp_business_messaging`, `whatsapp_business_management`) y los webhooks de coexistence están disponibles directamente en el dashboard. Eliminar el BSP intermedio significa: ~95% margen vs. ~50–60% con un BSP cobrando $20–89/mes por canal, sin lock-in con un proveedor externo, y operación más simple. La fuente única de verdad técnica vive en `trochai-inbox/docs/rfcs/whatsapp-coexistence-research-findings.md`.

---

## Qué problemas resuelve

### 1. **Cero fricción con el equipo de ventas.**
El agente sigue usando la app que conoce. No hay reuniones de capacitación. La adopción interna deja de ser el cuello de botella.

### 2. **Llamadas y grupos siguen vivos en el celular del agente.**
Coexistence no toca la WhatsApp Business app. Las llamadas de voz/video, los grupos con clientes, los flujos rápidos del celular — todo sigue exactamente igual.

### 3. **Continuidad para el cliente.**
El cliente no nota nada. Le sigue escribiendo al mismo número. Continuidad invisible.

### 4. **Visibilidad sin policía.**
La gerencia ve todas las conversaciones 1:1 en un solo lugar — no para microgestionar, sino para entender el funnel real, medir tiempo de respuesta, y atrapar leads que se enfrían.

### 5. **6 meses de historial al onboardear.**
Meta envía el webhook `history` durante el onboarding con todas las conversaciones previas. El inbox Trochai queda con contexto completo desde el día uno.

### 6. **Continuidad cuando un agente renuncia.**
Las conversaciones 1:1 quedan en Trochai con contexto y compromisos documentados. El reemplazo no empieza de cero.

### 7. **Cumplimiento de la ventana de 24h sin saberlo.**
Trochai detecta la ventana y solo permite plantillas aprobadas afuera de ella. El agente no tiene que recordar reglas de Meta.

---

## Qué NO hace coexistence (sea claro con su equipo)

Importante para no vender humo. Estas son limitaciones oficiales de Meta:

- ❌ **Llamadas de voz/video** — quedan en la app del agente, no se sincronizan a Trochai. (Esto es bueno — el agente las sigue haciendo desde su celular como siempre.)
- ❌ **Grupos** — los mensajes de grupos quedan en la app, NO aparecen en el inbox Trochai. Limitación de Meta.
- ❌ **Listas de difusión nuevas** — una vez activada coexistence, no se pueden crear listas de difusión nuevas. Las existentes siguen funcionando.
- ❌ **WhatsApp Web/Desktop** — solo los mensajes enviados desde la WhatsApp Business app móvil se sincronizan al inbox. Web/Desktop quedan fuera del eco.
- ❌ **Insignia azul (OBA)** — los números coexistence no pueden tener verificación OBA. Alternativa: Meta Verified for Business (suscripción separada).
- ❌ **Mensajes que se editan o borran** — deshabilitado en modo coexistence.
- ❌ **Verificación de negocio estándar** — no disponible. El número arranca con un límite de 250 conversaciones business-initiated por 24h, escalable según calidad.

Estas limitaciones son aceptables — y en algunos casos deseables — porque dejan que la app del agente mantenga lo que la app maneja mejor (llamadas, grupos, velocidad del celular) y la plataforma maneje lo que la plataforma maneja mejor (centralización 1:1, métricas, AI).

---

## Para quién es (y para quién NO es)

### Coexistence tiene sentido si:

- ✅ Su agencia tiene **3 o más agentes** activos en WhatsApp Business app.
- ✅ Sus agentes **ya tienen el WhatsApp Business app instalado** y lo usan diariamente (versión 2.24.17+).
- ✅ Su equipo usa la app para **llamadas, grupos o flujos del celular** que no quiere perder.
- ✅ Quiere **centralización sin revolución** — métricas y AI, pero sin destruir el flujo del equipo.
- ✅ Maneja **leads expatriados** que esperan respuesta fuera del horario costarricense (necesita el bot).

### Coexistence NO tiene sentido si:

- ❌ Es una agencia de 1 persona — no necesita centralizar.
- ❌ Está empezando de cero sin número operativo aún — use Trochai Inbox estándar (Cloud API directo, **sin add-on fee**).
- ❌ Su equipo no usa la app para llamadas/grupos y ya migró a un inbox web cómodamente — no rompa lo que funciona.
- ❌ Su número está actualmente conectado a otro proveedor de API (Twilio, 360dialog, Wati, HubSpot) — Meta requiere un periodo de cooldown de 30–60 días después de soltar el número del proveedor anterior antes de poder activar coexistence.

---

## Cómo encaja con el producto Trochai

Trochai Inbox tiene dos modos de conexión a WhatsApp:

| Modo | Cómo funciona | Quién lo paga | Cuándo usarlo |
|---|---|---|---|
| **Cloud API directo** (default) | El número opera 100% dentro de Trochai. Conexión vía Embedded Signup de Meta. Sin app móvil del agente en paralelo. | Solo tarifas de mensajes de Meta + mensualidad del plan. Sin add-on fee. | Agencias nuevas, equipos que ya migraron a inbox web cómodamente. |
| **Coexistence** (add-on, late May 2026) | El número opera en paralelo: WhatsApp Business app del agente + Trochai. Conexión directa con Meta Cloud API (Tech Provider, sin BSP). | Add-on de aprox. **$30–40/mes por número** + tarifas de mensajes de Meta. | Agencias con equipo establecido en WhatsApp Business app que no quiere — o no puede — migrar a inbox web. |

**Disponibilidad:** Coexistence se activará en planes Pro y Enterprise. Fecha tentativa: **late May 2026** (~30 días desde hoy). Las agencias en lista de espera reciben acceso temprano y tarifa de fundadores.

---

## Por qué importar este pillar esta semana

1. **Validación de mercado.** Cada vez que publicamos sobre coexistence, capturamos hand-raisers (agencias interesadas) y aprendemos qué objeciones quedan abiertas.
2. **Educación previa al lanzamiento.** Cuando la feature esté lista, queremos que el mercado ya entienda el concepto — no estar explicando arquitectura y vendiendo en la misma conversación.
3. **Posicionamiento contra plataformas regionales.** Las PropTechs mexicanas y salvadoreñas se posicionan como "centralización total." Trochai se posiciona como "centralización honesta — la plataforma maneja lo que la plataforma maneja mejor, la app maneja lo que la app maneja mejor." Coexistence es el feature que hace esa diferenciación tangible.

---

## Plan de la semana

| Día | Bucket | Formato | Ángulo |
|---|---|---|---|
| Lun 27 abr | Authority | Newsletter + carousel | Trochai Insights Sem. 18 — semana de noticias, con CTA al pillar |
| Mar 28 abr | Growth | Infographic | "El falso dilema: WhatsApp Business app vs. plataforma centralizada" |
| Mié 29 abr | Authority | Carousel educativo | "Coexistence en 5 pasos — directo con Meta, sin BSP" |
| Jue 30 abr | Growth | Infographic | "El problema y el beneficio, sin rodeos" — último día del descuento de lanzamiento |
| Vie 1 may | Conversion | Carousel producto | "Trochai Coexistence: qué incluye, qué cuesta, qué NO hace" — sin descuento |
| Sáb 2 may | Authority | Carousel deep-dive | "4 preguntas antes de centralizar el WhatsApp de su agencia" |
| Dom 3 may | Personal | Founder infographic | Leeren — "Por qué los agentes no sueltan su WhatsApp Business app (y por qué eso lo cambió todo)" |

---

## Métricas que vamos a medir

- **Reach orgánico:** impresiones acumuladas Lun–Dom en LinkedIn.
- **Hand-raisers:** comentarios + DMs preguntando por la fecha de lanzamiento o el precio.
- **Lista de espera:** registros en la página `/coexistence` (a publicar el lunes).
- **Conversión a Loom:** cuántos hand-raisers terminan en una llamada de descubrimiento durante mayo.

---

## Recursos referenciados

- `trochai-inbox/docs/rfcs/whatsapp-coexistence-research-findings.md` — fuente única de verdad técnica (Apr 2026)
- `trochai-inbox/docs/rfcs/whatsapp-coexistence-layer.md` — RFC de planning original
- Memory: `project_feature_rollout_2026_04.md` — secuencia de 5 fases (Coexistence es la fase 1)
- Memory: `project_launch_discount.md` — descuento expira el 30 abril, post-30 NO mencionar
