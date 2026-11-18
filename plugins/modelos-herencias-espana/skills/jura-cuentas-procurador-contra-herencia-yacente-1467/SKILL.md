---
name: jura-cuentas-procurador-contra-herencia-yacente-1467
description: "Redacta el escrito «Jura de cuentas del procurador contra la herencia yacente» (formulario 1467 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Jura de cuentas del procurador contra la herencia yacente

> Formulario 1467 del plugin **Sucesiones** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Inmuebles** (referencia catastral, superficie, uso) → `consultar_catastro` (y `callejero_catastro` para localizar la dirección).

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

- [ ] LOCALIDAD
- [ ] IMPORTE (4 veces)
- [ ] Nº DE DOCUMENTO
- [ ] FECHA
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…euros, me son debidos por D»; «…ros, me son debidos por D [COMPLETAR], y»; «…o, en su caso, ignorados herederos– de D»; «…las costas derivadas de este trámite. En»; «…, a»; «…, a [COMPLETAR], de»; «…, a [COMPLETAR], de [COMPLETAR] del año»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 6.1.4 de la LEC
- art. 34 de la LEC
- art. 34.1 de la LEC
- art. 6.1.4 y 7.5 de la LEC
- artículos 657 y 659 del Código Civil
- art. 34.2 de la LEC
- artículo 34 de la LEC

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

### Formulario 1467 · Jura de cuentas del procurador contra la herencia yacente

- Año del modelo: 2014
- Revisión 17-11-2026: 13 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Encabezamiento
HECHOS
FUNDAMENTOS DE DERECHO
Suplico
Firmas

Formulario adaptado a la reforma procesal de la LO 1/2025.

Proceso número

AL LETRADO DE LA ADMINISTRACIÓN DE JUSTICIA DEL TRIBUNAL DE [LOCALIDAD]

HECHOS

Que mi poderdante, cuyas circunstancias constan en autos no me ha hecho efectiva la cuenta de derechos y gastos devengada en la tramitación del presente procedimiento, que asciende a la suma de [IMPORTE] euros en concepto de derechos y gastos derivados de la tramitación de este procedimiento, conforme aparece detallado en la cuenta de derechos y gastos que se adjunta como documento nº [Nº DE DOCUMENTO]

Habiendo fallecido mi representación el pasado día [FECHA], dirijo la reclamación contra la herencia yacente del finado, al ignorar el solicitante la posible identidad o existencia de herederos, siendo reiterada la interpretación de los Tribunales en cuanto a la posibilidad de que la herencia yacente pueda ser parte en el procedimiento, de conformidad a lo que dispone el art. 6.1.4 de la LEC, al contemplar expresamente la capacidad para ser parte que en el proceso civil pueden ostentar las masas patrimoniales o los patrimonios separados que carezcan transitoriamente de titular, señalando en el artículo siguiente que en estos casos la comparecencia en juicio se efectuará por medio de quienes legalmente les administren (art. 7.5), como habían reiterado las SSTS 20 de septiembre de 1982, 12 de marzo de 1987 y 31 de enero de 1994 ,entre otras.

Por tanto, como indica el AAP Lleida de 8 de abril de 2004, rec. 8/2004, debe admitirse la posibilidad de que el procedimiento de jura de cuentas (y el requerimiento de pago al deudor que del mismo habrá de derivarse, «ex» art. 34 de la LEC), se dirija contra «la herencia yacente o ignorados herederos» del deudor de cuyo fallecimiento se aporta acreditación documental por esta parte, designándose, a efectos de notificaciones y demás actos de comunicación, los domicilios que constan a esta parte donde viven sus familiares más cercanos –esposa e hijo–, quienes lógicamente parecen llamados a la herencia del finado.

A los efectos del art. 34.1 de la LEC, manifiesto formalmente que los derechos y gastos reflejados en la cuenta que presento, cuyo importe asciende a [IMPORTE] euros, me son debidos por D [COMPLETAR], y [COMPLETAR], en consecuencia, por su herencia yacente, y no han sido satisfechos.

FUNDAMENTOS DE DERECHO

Competencia

Es competente el Letrado de la Administración de Justicia del órgano al que me dirijo, por ser el lugar donde radica el asunto, conforme al art. 34.1 de la LEC.

Legitimación

Está legitimado activamente este Procurador para reclamar de su poderdante deudor los derechos y gastos debidos y no abonados, conforme al art. 34.1 de la LEC. En cuanto a la legitimación pasiva, el art. 6.1.4 y 7.5 de la LEC en relación con los artículos 657 y 659 del Código Civil.

Procedimiento

El art. 34.2 de la LEC establece que se requerirá al deudor para que pague la suma reclamada, más las costas, o impugne la cuenta, en el plazo de diez días bajo apercibimiento de apremio, y siguiéndose los trámites sucesivos de los apartados 2 y 3 del mismo artículo 34 de la LEC.

Costas

Artículo 34 de la LEC y preceptos concordantes, debiendo imponerse al deudor

En base a lo anterior,

SUPLICO al Letrado de la Administración de Justicia que tenga por presentado el presente escrito, se sirva admitirlo y acuerde, previa la tramitación oportuna requerir a la HERENCIA YACENTE –o, en su caso, ignorados herederos– de D [COMPLETAR] a fin de que proceda en un plazo de diez días al pago de la cantidad de [IMPORTE] euros en concepto de derechos y gastos debidos y no satisfechos, con las costas que prudencialmente se fijan en [IMPORTE] euros, o impugne la cuenta, bajo apercibimiento de apremio si no pagare ni formulare impugnación, imponiéndole las costas derivadas de este trámite.

En [COMPLETAR], a [COMPLETAR], de [COMPLETAR] del año [COMPLETAR]

Firma Procurador

========================================================================
