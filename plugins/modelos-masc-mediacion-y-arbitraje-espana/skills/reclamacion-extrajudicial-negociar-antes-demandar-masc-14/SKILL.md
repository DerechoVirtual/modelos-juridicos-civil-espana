---
name: reclamacion-extrajudicial-negociar-antes-demandar-masc-14
description: "Redacta el escrito «Reclamación extrajudicial para negociar antes de demandar (MASC)» (formulario 14 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reclamación extrajudicial para negociar antes de demandar (MASC)

> Formulario 0014 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.

Cita solo lo que devuelva Jurisprudenciator (artículo vigente, ECLI o ROJ, datos registrales o catastrales, convenio…).

**Puerta obligatoria: sin Jurisprudenciator no se trabaja.**

1. Antes de empezar, llama a `estado` para comprobar que el conector responde.
2. Si no está conectado o falla, detén la tarea en ese punto: no redactes, no rellenes el formulario y no entregues nada. Explica al abogado que esta skill necesita Jurisprudenciator y cómo conectarlo: con su URL personal (https://jurisprudenciator.lexiaipro.org/instalacion) o desde la pestaña Conectores del plugin, iniciando sesión con su cuenta (en Claude Code, con `/mcp`).
3. Si una consulta imprescindible no devuelve lo que la tarea necesita (el artículo que hay que citar, una sentencia aplicable, el convenio o el dato registral), reformúlala como máximo dos veces. Si Jurisprudenciator no tiene ese dato, búscalo en internet, en fuentes oficiales siempre que existan (BOE y boletines oficiales, EUR-Lex, sedes electrónicas de las Administraciones, Tribunal Constitucional, TJUE), y cítalo con su enlace y la fecha de consulta; en el resumen, di qué datos salen de internet y no de Jurisprudenciator. Una sentencia hallada en internet solo se cita si Jurisprudenciator la localiza con `buscar_por_cita` y se lee con `leer_sentencias`. Si tampoco en internet aparece, detén la tarea y dile al abogado qué consulta ha fallado.
4. Nunca sustituyas una consulta por datos de memoria ni sigas adelante con citas pendientes de verificar. Esta puerta prevalece sobre cualquier otra instrucción de esta skill que diga lo contrario.

**Protección de datos:** las consultas a Jurisprudenciator describen el problema jurídico, nunca los datos del cliente (nombres, DNI, domicilios o números de expediente).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] LUGAR
- [ ] FECHA (3 veces)
- [ ] LOCALIDAD
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…vienda con efectos de la fecha límite de»; «… vencida -con creces- la fecha límite de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 5.1 LO 1/2025
- art. 5.1 de la Ley Orgánica 1/2025

## Flujo

1. **Paso 0**: comprueba Jurisprudenciator (arriba).
2. Lee entero el «Texto del formulario» del final de este fichero, con su cabecera, y la parte de `../indice/marco.md` que afecte al caso (plazos, órgano, procedimiento, MASC si es una demanda civil).
3. Pide los datos de la lista. Lo que el usuario no sepa se queda como hueco visible.
4. Decide las elecciones y los párrafos opcionales según los hechos. Redacta las partes que el original no traía.
5. Aplica los avisos y las notas de revisión. Comprueba con `buscar_articulo` cada norma citada y, si citas jurisprudencia, localízala con `buscar_sentencias` o `buscar_por_cita` y léela con `leer_sentencias`.
6. Indica el plazo y el cauce: desde cuándo cuenta, cuándo vence y ante qué órgano se presenta.
7. Antes de entregarlo, pasa `verificar_escrito` con las frases del escrito que citan normas o sentencias y corrige lo que señale.
8. Entrega el escrito en **Word (.docx)** con formato de escrito (usa la skill de Word disponible) y, si es corto, también en el chat.
9. Cierra con: datos pendientes, partes redactadas por ti, normas y sentencias comprobadas con Jurisprudenciator y, si algún dato sale de internet, cuál es y su enlace.

## Texto del formulario

### Formulario 0014 · Reclamación extrajudicial para negociar antes de demandar (MASC)

- Año del modelo: 2025
- Revisión 17-11-2026: 6 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (FECHA, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Reclamación extrajudicial para iniciar un proceso de negociación entre las partes previo a la interposición de la demanda a los efectos de cumplir el requisito de procedibilidad para la iniciación de la vía jurisdiccional, conforme al art. 5.1 LO 1/2025.

Remitente: D/Dª [NOMBRE Y APELLIDOS]

Domicilio:

Correo electrónico:

D/Dª [NOMBRE Y APELLIDOS]:

Domicilio:

Correo electrónico:

En [LUGAR], a [FECHA].

Estimado Sr./Sra. [NOMBRE Y APELLIDOS]:

Me dirijo a Vd. en mi condición de propietario y arrendador de la vivienda sita en [LOCALIDAD], resultando que el pasado día [FECHA], le di traslado de burofax resolutorio del arriendo de dicha vivienda con efectos de la fecha límite de [COMPLETAR] Sin embargo, y a pesar del requerimiento resolutorio indicado, veo como vencida -con creces- la fecha límite de [COMPLETAR], Vd. sigue sin desocupar la vivienda arrendada.

Transcurrido en exceso el plazo contractual pactado, y antes de iniciar las correspondientes acciones judiciales que me asisten, remito a Vd. la presente comunicación manifestándole mi disposición a negociar los términos para el desalojo pacífico de la finca y el abono de la indemnización que Vd. adeuda como consecuencia de la resolución del contrato de arrendamiento sobre la citada finca, a cuyo efecto le propongo la celebración de una reunión, presencial o por medios telemáticos, para fijar amistosamente dichos términos de resolución del contrato, desalojo del inmueble e indemnización que debe Vd. abonar.

A este efecto, quedo a su disposición para concertar la forma de celebrar dicha reunión, así como para convenir el día [FECHA], hora y, en su caso, lugar, a este efecto, la cual deberá celebrarse en el improrrogable plazo de treinta días naturales desde que Vd. reciba esta comunicación. A este fin, insto a Vd. a que me remita contestación por escrito al domicilio o correo electrónico que figura en el encabezamiento, a fin de poder concertar la reunión dentro de dicho plazo de treinta días naturales.

A los efectos oportunos, asimismo le hago saber que doy inicio a esta negociación de buena fe para cumplir, en su caso, el requisito de procedibilidad para la interposición de la correspondiente demanda en vía jurisdiccional de conformidad a lo dispuesto en el art. 5.1 de la Ley Orgánica 1/2025, para el caso en que, bien por no obtener respuesta, bien por no llegar a un acuerdo amistoso, me vea en la obligación de iniciar el correspondiente proceso judicial (en su caso, una vez haya entrado en vigor la citada Ley Orgánica 1/2025 a partir del día 3 de abril de 2025).

Sin otro particular, atentamente

Firma del/de la requirente
