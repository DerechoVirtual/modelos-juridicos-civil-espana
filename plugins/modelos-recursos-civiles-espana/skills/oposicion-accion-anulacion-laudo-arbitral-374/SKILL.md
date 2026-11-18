---
name: oposicion-accion-anulacion-laudo-arbitral-374
description: "Redacta el escrito «Oposición a la acción de anulación del laudo arbitral» (formulario 374 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición a la acción de anulación del laudo arbitral

> Formulario 0374 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (3 veces)
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] FECHA (5 veces)
- [ ] ÓRGANO O PERSONA
- [ ] NÚMERO
- [ ] ÓRGANO (2 veces)
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…tivo de la demanda, en el sentido de que»; «…o se acredita con los documentos números»; «…s previstas en el art. 41 LA, por cuanto»; «…ara su práctica los siguientes medios de»; «…rbitral. II.- PERICIAL, de un técnico de»; «…ica. Por ser de justicia que solicito en»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 8.5 de la Ley 60/2003
- arts. 6, 7 y 10 LEC
- art. 394 LEC

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

### Formulario 0374 · Oposición a la acción de anulación del laudo arbitral

- Año del modelo: 2019
- Revisión 17-11-2026: 24 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de contestación a impugnación judicial de laudo arbitral.

A LA SALA DE LO CIVIL Y PENAL DEL TRIBUNAL SUPERIOR DE JUSTICIA DE [LOCALIDAD]

D./DÑA. [NOMBRE Y APELLIDOS], procurador de los tribunales, en nombre de D./DÑA. [NOMBRE Y APELLIDOS], cuyas circunstancias y representación acredito con primera copia de escritura de poder que, debidamente bastanteada, acompaño bajo el nº 1 de documentos para que, testimoniada en autos, se desglose y se me devuelva por precisarla para otros usos; bajo la dirección del letrado D./DÑA. [NOMBRE Y APELLIDOS] y ante la Sala de lo Civil y Penal del Tribunal Superior de Justicia de [LOCALIDAD] comparezco y, como mejor proceda, DIGO:

Que en fecha [FECHA], mi representado ha recibido cédula de notificación y emplazamiento, con traslado de documentos respecto a la demanda ejercitando acción de anulación de laudo arbitral interpuesta por D./DÑA. [NOMBRE Y APELLIDOS], en razón a la cual se insta la nulidad del laudo de fecha [FECHA], dictado por [ÓRGANO O PERSONA], en el procedimiento arbitral n.º [NÚMERO], seguido ante [ÓRGANO].

Que, dentro del plazo al efecto concedido y por medio del presente escrito, comparezco ante esta Sala a fin de contestar a la demanda de nulidad y oponerme a la misma, de conformidad todo ello con los siguientes:

HECHOS

PRIMERO.- De conformidad con el hecho primero de contrario.

SEGUNDO.- De conformidad con el hecho segundo de contrario.

TERCERO.- Se niega expresamente el correlativo de la demanda, en el sentido de que [COMPLETAR], como se acredita con los documentos números [COMPLETAR] de la oposición a la demanda que se acompañan.

A los hechos anteriores son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- Es competente la Sala de lo Civil y Penal del Tribunal Superior de Justicia a la que me dirijo, conforme a lo dispuesto en el art. 8.5 de la Ley 60/2003, de 23 de diciembre, de Arbitraje (LA).

II.- A los puros efectos formales, las partes ostentan legitimación ad procesum y legitimación ad causam para interponer y soportar la presente acción de nulidad, de conformidad con lo dispuesto en los arts. 6, 7 y 10 LEC, y ello, sin perjuicio de oponernos de manera frontal a la demanda, y negar tajantemente los hechos aducidos en la misma.

III.- De conformidad con lo dispuesto en el art. 42 LA, deberá seguirse el procedimiento por los trámites del juicio verbal que a tal fin establece la Ley de Enjuiciamiento Civil, si bien con las modificaciones establecidas en el mencionado precepto.

IV.- Respecto a fundamentos de derecho jurídico materiales, en modo concurre ninguna de las circunstancias previstas en el art. 41 LA, por cuanto [COMPLETAR].

V.- Respecto a las costas, resulta de aplicación lo dispuesto con carácter general en el art. 394 LEC

En su virtud,

SUPLICO A LA SALA DE LO CIVIL Y PENAL DEL TRIBUNAL SUPERIOR DE JUSTICIA DE [LOCALIDAD]:

que, habiendo por presentado este escrito con sus documentos y copias, se sirva admitirlo, me tenga por parte en la representación que ostento de D./DÑA. [NOMBRE Y APELLIDOS] y por contestada en tiempo y forma la demanda en ejercicio de acción de nulidad del laudo arbitral de fecha [FECHA], interpuesta por D./DÑA. [NOMBRE Y APELLIDOS], se siga el procedimiento por sus trámites y, en su momento, dicte sentencia por la que, desestimando íntegramente la demanda de nulidad interpuesta, mantenga la validez del laudo arbitral objeto de impugnación, con expresa imposición de las costas a la parte demandante.

OTROSÍ DIGO que, de conformidad con el art. 42 LA, esta parte propone para su práctica los siguientes medios de [COMPLETAR]

PRUEBA

I.- DOCUMENTAL, consistente en los siguientes documentos acompañados por esta parte:

—Copia de la demanda de arbitraje interpuesta ante [ÓRGANO].
—Documentos acompañados junto con la referida demanda de arbitraje.
—Acta de la sesión de arbitraje celebrada en fecha [FECHA], en la que se consignó lo que constituía el objeto del arbitraje.
—Copia de los documentos acompañados en la audiencia celebrada en fecha [FECHA], en el desarrollo del procedimiento arbitral.

II.- PERICIAL, de un técnico de [COMPLETAR], lo cual se articulará en el acto de la vista.

III.- TESTIFICAL, a fin de que sean citadas judicialmente las siguientes personas:

SUPLICO A LA SALA tenga por propuesta la prueba de esta parte, la declare pertinente y acuerde lo procedente para su práctica.

Por ser de justicia que solicito en [COMPLETAR] a ..

Firma de Abogado/a	Firma de Procurador/a
