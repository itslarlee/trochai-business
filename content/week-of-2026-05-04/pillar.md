# Pillar — Su inventario vive en lugares que no se hablan. Su cliente lo nota antes que vos.

> Pilar de la Sem. 19 (4 mayo – 10 mayo, 2026). Producto que se vende detrás: **Trochai Sites** (lanzado 2026-04-29).

---

## Tesis

Costa Rica está en un momento singular para una pyme: una encuesta Microsoft de 2023 (vía DPL News) reportó que el 53% ya avanzaba rápidamente en transformación digital y el 78% se consideraba "en el journey"; tres años después, la encuesta Microsoft Source LATAM 2025 confirma que el 50% ya usa IA en operaciones diarias. El país ranquea 5to en LATAM en preparación de IA con un score de 53.83/100 (ILIA 2025). El cliente costarricense ya está acostumbrado a recibir respuesta automatizada de su banco, su aerolínea, su hotel, su súper.

**La excepción dentro de esa historia es bienes raíces.** El stack típico de una agencia con 3 a 20 agentes y 30 a 100 listings activos incluye: un MLS o CRM interno (Excel o herramienta dedicada), los portales nacionales, el sitio propio (típicamente WordPress con un plugin de listings), el catálogo de WhatsApp Business, y las captions de Instagram. La cantidad exacta de superficies varía por agencia — algunas tocan tres, otras siete — pero el patrón es consistente: ninguna se sincroniza con las demás.

Cada propiedad nueva requiere subir las mismas fotos, el mismo texto y el mismo precio en cada superficie por separado. Cada actualización (cambio de precio, "ya se vendió", reducción de cuartos) requiere repetir el trabajo. Para una agencia con 50 listings activos × 4 actualizaciones/año son fácilmente cien horas o más al año de doble carga.

Y eso es solo el costo medible. El costo invisible es peor: la deriva entre las superficies siempre existe. Una propiedad que se vendió en abril sigue apareciendo en el sitio web hasta junio. Una rebaja de precio queda actualizada en un portal pero no en el catálogo de WhatsApp. Cuando un cliente pregunta por WhatsApp "vi esta casa en su sitio, ¿sigue disponible?", el bot — sin saberlo — responde con el catálogo donde la propiedad ya no está. **El cliente nota el desfase en 8 segundos. La confianza se pierde antes de que el agente humano se entere.**

La pregunta para 2026 no es "¿qué herramienta agrego?" Es: "¿de qué arquitectura parten todas mis herramientas?"

---

## El argumento (arco narrativo de la semana)

1. **Costa Rica está digitalizando más rápido de lo que la gente cree.** Microsoft 2023: 53% de pymes avanzaban rápido en transformación digital, 78% en el journey. Microsoft 2025: 50% ya usa IA. ILIA 2025: CR es 5to en LATAM en preparación de IA. El cliente tico ya internalizó esa expectativa.

2. **Bienes raíces es la excepción dentro de esa historia.** Mientras hospitalidad, banca, retail y manufactura consolidan herramientas, las inmobiliarias siguen manteniendo el inventario distribuido entre superficies que no se hablan entre sí.

3. **El "single-edit nightmare" es el costo escondido.** Cien horas o más al año de pure rework por agencia. Y deriva permanente — al menos una de las superficies siempre está mal.

4. **Los clientes lo notan.** Mensaje en WhatsApp pidiendo una propiedad que vio en el sitio. Bot dice "ya no está disponible". Sitio dice que sí. Confianza se pierde en 8 segundos.

5. **El fix no es otra herramienta. Es una decisión arquitectónica.** Un único origen de datos sobre el inventario. El sitio web, el bot de WhatsApp y la app del agente leen de ahí. Edita una vez, aparece en todos lados.

---

## Datos clave (con fuentes)

- **53% de pymes ticas avanzaban rápidamente en transformación digital; 78% se consideraba "en el journey".** Microsoft 2023 (vía DPL News).
- **50% de pymes ticas ya usan IA en operaciones diarias. 62% del uso es servicio al cliente. 48% lo usa específicamente para mejorar servicio + satisfacción del cliente.** Microsoft Source LATAM Encuesta 2025 (vía La Prensa Libre).
- **65% de líderes pymes reportan que la IA mejora la calidad del trabajo; 61% reporta más productividad.** Microsoft Source LATAM 2025.
- **CR es 5to en LATAM en preparación de IA — ILIA 2025 score 53.83/100.** Top 5: Chile, Brasil, Uruguay, Colombia, CR. CR específicamente fuerte en talento humano (3er lugar regional). Tico Times (jul 2025) lo posiciona como líder regional en adopción PYME.
- **42% de pymes ticas prioriza usar datos para business intelligence; 35% prioriza adoptar nueva tecnología.** Microsoft 2023 (vía DPL News).
- **Penetración de internet en CR: 92.6% (4.78M usuarios).** DataReportal Digital 2026 Costa Rica (nov 2025).
- **48% de personas y 56% de empresas en LATAM usan IA — cerca de EE.UU. y Europa.** Google vía Tico Times (sept 2025), Adriana Noreña.
- **WEF: 1 de cada 6 trabajadores tendrá que reskillearse para 2027.** Citado en el mismo artículo de Tico Times — la brecha de talento es el riesgo principal de la curva de adopción.
- **PropTech 2026 en CR: virtual tours, IA para predicción de precios, asset management automatizado.** The Costa Rica News (dic 2025).

**Fuentes (URLs completas):**
- https://dplnews.com/costa-rica-mas-de-la-mitad-de-pymes-ticas-avanza-hacia-transformacion-digital/
- https://news.microsoft.com/es-xl/50-de-las-pymes-en-costa-rica-utilizan-algun-tipo-de-ia/
- https://www.laprensalibre.cr/el-50-de-las-pymes-en-costa-rica-ya-utiliza-inteligencia-artificial-segun-encuesta-de-microsoft/
- https://ticotimes.net/2025/07/05/costa-rica-leads-ai-adoption-in-small-businesses-across-latin-america
- https://datareportal.com/reports/digital-2026-costa-rica
- https://thecostaricanews.com/real-estate-trends-for-2026/
- https://ticotimes.net/2025/09/25/ai-in-latin-america-nears-us-europe-use-but-talent-lags-says-google

---

## Posicionamiento del producto (Trochai Sites — copia verbatim de POSITIONING-ONE-LINERS.md)

**Diferenciador (la línea que nadie más puede usar):**
> *"Trochai Sites es el único sitio web inmobiliario en Costa Rica que comparte la misma base de datos que su Inbox. La IA del bot conoce su catálogo. Las propiedades se actualizan en un solo lugar."*

**Beneficio primario:**
> *"Una propiedad nueva en su Inbox aparece automáticamente en su sitio web. Cero integración. Cero doble carga."*

**Promo de mayo (Offer A — el ask por defecto):**
> *"Don/doña [name], le doy una noticia rápida: solo durante mayo, cuando agarra el plan anual de Trochai Inbox — el Pro le sale a $1,188 al año — le incluimos sin costo el sitio web de su agencia, que normalmente vale $4,500. Diseñado a la medida, conectado al Inbox, listo en dos semanas."*

**Promo de mayo (Offer B — para quien solo quiere el sitio):**
> *"Si solo quiere el sitio web por ahora — sin entrar todavía al Inbox — durante mayo está al 50% de descuento. El template de agencia arranca en $1,250 (precio normal $2,500), incluye el dominio personalizado y queda listo para conectarse al backend del Inbox cuando decida activarlo después."*

---

## Beneficios específicos a destacar durante la semana

- **Una sola edición.** Agrega una propiedad en el Inbox → aparece en el sitio en segundos. Sin sincronizar, sin importar, sin "lo subo después."
- **El bot conoce el catálogo.** Cuando un cliente pregunta por WhatsApp "¿tienen casas en Escazú bajo $500k?", el bot responde con propiedades reales del mismo inventario que ven en la web.
- **Diseño profesional, no plantilla.** Cuatro plantillas elegidas (Esmeralda, Sable, Sabana, Aleteo) con identidad visual real, no un WordPress genérico.
- **Build rápido.** Plantilla → datos → online en días, no meses.
- **Mismo backend que ya pagaste.** Si ya usás Trochai Inbox, el sitio se conecta sin migración.

---

## Plan de la semana

| Día | Bucket | Formato | Ángulo | Promo |
|---|---|---|---|---|
| Lun 4 may | Authority | Newsletter + carousel + LinkedIn Newsletter | Sem. 19 — la macro/data: 53% DT (2023) + 50% IA (2025) + CR 5to LATAM. Wedge: "inmobiliarias mantienen inventario en superficies que no se hablan entre sí" | Tease promo mayo |
| Mar 5 may | Growth | Brandjack/newsjack — infographic | Newsjack del estudio Microsoft sobre 50% de pymes con IA. Hot take: "Bienes raíces es la excepción de esa estadística — y por qué" | Mención promo mayo |
| Mié 6 may | Personal | Founder commentary on data | Opinión del founder sobre los datos del mes — qué pregunta levantan para una agencia inmobiliaria. Sin historias inventadas, solo opinión sobre la data publicada. | Sin promo (Wed founder = voz humana, no venta) |
| Jue 7 may | Growth | Hot take carousel — "Las superficies que no se hablan" | Visual tour de las superficies típicas + tiempo invertido en cada una + cost real. Hot take: "Sin consolidar, no hay PropTech 2026 que valga" | Mención promo mayo |
| Vie 8 may | Conversion | Product carousel | "Cómo se ve una sola edición": carousel mostrando flow Inbox → Sites + bot. Mecanismo concreto, no marketing | Promo mayo full CTA |
| Sáb 9 may | Authority | Deep-dive carousel | "4 preguntas antes de hacer un sitio web inmobiliario en 2026" — filtro de discovery, sin venta directa | Mención promo mayo (sin urgencia) |
| Dom 10 may | Authority/Recap | Weekly digest infographic | Resumen neutral de los 5 datos de la semana + pregunta de cierre. Sin opinión fuerte, sin venta. | Sin promo |

---

## Tono y voz

- **Ustedeo** (CR, nunca tú/vos en voz de negocio)
- **Voz del fundador** — primera persona, experiencia vivida ("Vimos esto en cada discovery call que hicimos en abril...")
- **Específico sobre genérico.** No "real estate is digitalizing." Sí "una agente en Escazú nos dijo la semana pasada: 'subo cada propiedad cuatro veces y siempre se me olvida una.'"
- **Empático, no predicador.** Las agencias no son lentas — las herramientas les fallaron. El pillar es "la industria ha sido subatendida," no "ustedes están atrás."
- **Soportado por datos.** Cada claim macro tiene cita. Cada claim de Trochai tiene mecanismo concreto.

---

## Qué NO decir esta semana

- ❌ No mencionar el stack técnico (no Vercel, OpenAI, Anthropic, Supabase, Mapbox). Posición de marca: "nosotros manejamos la infraestructura" sin nombrar proveedores.
- ❌ No comparar a competidores específicos por nombre (los portales nacionales se mencionan SOLO como descripción factual de las superficies donde vive el inventario, no como competidores a vencer).
- ❌ No claim "todas las agencias CR están atrás." Muchas son sofisticadas — el wedge es la arquitectura multi-edit, no la competencia.
- ❌ No parafrasear las líneas de posicionamiento. Cópialas verbatim.
- ❌ No prometer features PropTech que no están shipped (no virtual tours, no AI price prediction — son tendencias macro, no capacidades de Trochai todavía).

---

## Métricas que vamos a medir

- **Reach orgánico LinkedIn:** impresiones acumuladas Lun–Sáb (target: paridad o +10% vs. semana 18; semana 18 fue puro Coexistence — semana 19 cambia el tema, hay riesgo de baja transitoria)
- **Hand-raisers:** comentarios + DMs preguntando por Trochai Sites o el promo de mayo
- **Demos agendadas atribuibles al contenido:** cuántas conversaciones llegan a discovery call durante mayo gracias a este pillar
- **Conversión Offer A vs. Offer B:** medir cuántos hand-raisers escogen "annual Inbox = sitio gratis" vs. "50% off à-la-carte"

---

## Recursos referenciados

- `trochai-business/POSITIONING-ONE-LINERS.md` — líneas verbatim de Trochai Sites + promo de mayo (decisión 2026-04-29)
- `trochai-business/TROCHAI-SITES-PRICING.md` — pricing locked (Esmeralda $2,500 / Sable $4,500 / Sabana $5,500 / Aleteo $9,500 / Cinematic Full R3F $13,500)
- `trochai-landing/content/blog/{locale}/trochai-insights-2026-s19.mdx` — newsletter completo (ES + EN)
- `STATE.md` — Trochai Sites como segundo producto pago (lanzado 2026-04-29); promo mayo confirmado
