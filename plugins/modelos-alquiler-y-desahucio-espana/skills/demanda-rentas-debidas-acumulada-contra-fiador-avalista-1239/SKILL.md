---
name: demanda-rentas-debidas-acumulada-contra-fiador-avalista-1239
description: "Redacta el escrito «Demanda de rentas debidas acumulada contra fiador o avalista» (formulario 1239 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de rentas debidas acumulada contra fiador o avalista

> Formulario 1239 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (12 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] IMPORTE (4 veces)
- [ ] PROFESIÓN
- [ ] LOCALIDAD (2 veces)
- [ ] DNI/NIE (2 veces)
- [ ] FECHA (3 veces)
- [ ] ÓRGANO
- [ ] Nº
- [ ] NÚMERO (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… acción de reclamación a arrendatario de»; «…,»; «…es arrendador del inmueble situado en»; «…, en su calidad de»; «…más, a abonar las siguientes cantidades:»; «…. En la cláusula»; «…asumía como»; «…erechos de mi representado. Requerido el»; «…Tercero.—»; «…futuras el importe de una mensualidad de»; «…uda, que los intereses se impongan desde»; «… D./Dña. [NOMBRE Y APELLIDOS] al pago de»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Actualizaciones e impagos / Rentas impagadas — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Tasa / Justificante / Exento de pago tasa — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Fiador / Obligación solidaria / Aval y avalista — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Rentas debidas y no pagadas, más rentas futuras impagadas / Rentas debidas y no pagadas, más rentas futuras impagadas, más otros conceptos / Cantidades por otros conceptos, más cuotas devengadas no pagadas — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 251.9 de la LEC
- art. 437.1 LEC
- art. 5 de la Ley Orgánica 1/2025
- artículo 1555.1 del Código Civil
- artículo 220.1 de la LEC

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

### Formulario 1239 · Demanda de rentas debidas acumulada contra fiador o avalista

- Año del modelo: 2013
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 4 bloques de opciones sin texto dejados en blanco con sus rótulos; 44 campos de relleno marcados en blanco
- Avisos de la revisión: REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: Un solo TI por partido judicial (art. 84.1 LOPJ): sobra «de los de». Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], ante el Tribunal comparezco bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], y como mejor proceda en derecho, DIGO:

Que mediante el presente escrito interpongo demanda a tramitar por el cauce del juicio verbal en ejercicio de acción de reclamación a arrendatario de [COMPLETAR] por importe de [IMPORTE] euros, más las cantidades que se vayan devengando en la tramitación del procedimiento, contra el arrendatario D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, de profesión [PROFESIÓN], domicilio en [LOCALIDAD] y DNI n.º [DNI/NIE] y acumulada contra D./Dña. [NOMBRE Y APELLIDOS], [COMPLETAR] del contrato de arrendamiento de fecha [FECHA], mayor de edad, con domicilio en [LOCALIDAD] y DNI nº [DNI/NIE] con base en los siguientes

HECHOS

Se presenta listado de documentos que acompañan a la demanda.

D./Dña. [NOMBRE Y APELLIDOS] es arrendador del inmueble situado en [COMPLETAR], en su calidad de [COMPLETAR] según acredito mediante [ÓRGANO].

En fecha [FECHA] se suscribió contrato de arrendamiento entre mi representado como arrendador y D./Dña. [NOMBRE Y APELLIDOS] como arrendatario, con una duración pactada de [Nº] años y una renta mensual de [IMPORTE] euros. Acredito estos extremos aportando como doc. n.º [NÚMERO] el citado contrato.

. El inquilino estaba obligado, además, a abonar las siguientes cantidades: [COMPLETAR].

En la cláusula [COMPLETAR] del contrato se pactó como garantía del pago de las cantidades, cuyo abono asumía el arrendatario, que el codemandado D./Dña. [NOMBRE Y APELLIDOS] asumía como [COMPLETAR] de forma solidaria el mismo compromiso de pago de las cantidades futuras que se devengaran.

[ELEGIR UNA OPCIÓN Y REDACTARLA: Actualizaciones e impagos / Rentas impagadas — el texto de cada opción no venía en el formulario original]

No habiendo el demandado contestado a los requerimientos tendentes a evitar la vía judicial, doc. n.º [NÚMERO], finalmente nos vemos obligados a acudir al Tribunal en defensa de los derechos de mi representado.

Requerido el [COMPLETAR] de pago en fecha [FECHA], según acredito con el documento nº [Nº DE DOCUMENTO], no ha contestado en sentido alguno.

FUNDAMENTOS DE DERECHO

Los artículos 21 y 22 de la Ley Orgánica del Poder Judicial consideran que la jurisdicción competente en esta materia es la española, y los artículos 45 y 52.1.7.º de la Ley de Enjuiciamiento Civil atribuyen la competencia al Tribunal al que nos dirigimos al ser éste el lugar donde se encuentra la finca.

El artículo 250.1.1.º de la Ley de Enjuiciamiento Civil dice que se tramitarán por el cauce del juicio verbal las reclamaciones de cantidades por impago de rentas y cantidades debidas.

La cuantía del pleito, según la regla del artículo 251.9 de la LEC, es de [IMPORTE] euros, que se corresponde al principal reclamado.

[ELEGIR UNA OPCIÓN Y REDACTARLA: Tasa / Justificante / Exento de pago tasa — el texto de cada opción no venía en el formulario original]

En aplicación del artículo 10 de la Ley de Enjuiciamiento Civil, D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] son los legitimados activa y pasivamente al ser ambos titulares de la relación jurídica de la que se deriva la deuda.

Los artículos 72 y 437.4.3.ª de la LEC permite acumular en estos procedimientos las acciones contra fiador y avalista solidario previo requerimiento de pago, que esta parte acredita haber realizado.

Los artículos 23 y 31 de la citada norma rituaria sólo exigen la intervención de Procurador y Abogado en los juicios verbales de cuantía superior a los 2.000 euros.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC en relación con el art. 437.1 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Primero.— El artículo 17 de la Ley de Arrendamientos Urbanos recoge la obligación del arrendatario de pago de la renta por el uso de la vivienda y el artículo 20 de la misma norma afirma que las partes pueden pactar que los gastos generales para el adecuado sostenimiento del inmueble, sus servicios, cargas, tributos, cargas y responsabilidades que no sean susceptibles de individualización y que correspondan a la vivienda arrendada o sus accesorios, sean a cargo del arrendatario.

Segundo.— Igualmente el artículo 1555.1 del Código Civil obliga al arrendatario a pagar el precio del arrendamiento en los términos convenidos.

[ELEGIR UNA OPCIÓN Y REDACTARLA: Fiador / Obligación solidaria / Aval y avalista — el texto de cada opción no venía en el formulario original]

Tercero.— [COMPLETAR]. El artículo 220.1 de la LEC, para los supuestos de reclamaciones de prestaciones periódicas, permite que la sentencia incluya la condena a satisfacer los intereses o prestaciones que se devenguen con posterioridad al momento en que se dicte. Por esa razón interesa esta parte que la condena sea también de futuro e incluya no sólo la obligación de pago de las cantidades devengadas hasta la fecha sino también todas aquellas que se vayan haciendo líquidas hasta el momento de su efectivo pago por el deudor. Para ello se fija como base para la liquidación de rentas futuras el importe de una mensualidad de [COMPLETAR] en este momento de presentar la demanda que asciende a [IMPORTE] euros.

Cuarto.— El artículo 576 de la Ley de Enjuiciamiento Civil permite la imposición de intereses de demora al demandado desde que se dicte la sentencia de primera instancia (en su caso). Interesa esta parte, no obstante, al haber reclamado extrajudicialmente el pago de la deuda, que los intereses se impongan desde [COMPLETAR].

En aplicación del artículo 394 de la Ley de Enjuiciamiento Civil las costas se impondrán a los demandados.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño, admita el Letrado de la Administración de Justicia a trámite la presente demanda, y en su día dictar sentencia por la que se condene solidariamente a los demandados D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] al pago de [COMPLETAR]:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Rentas debidas y no pagadas, más rentas futuras impagadas / Rentas debidas y no pagadas, más rentas futuras impagadas, más otros conceptos / Cantidades por otros conceptos, más cuotas devengadas no pagadas — el texto de cada opción no venía en el formulario original]

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
