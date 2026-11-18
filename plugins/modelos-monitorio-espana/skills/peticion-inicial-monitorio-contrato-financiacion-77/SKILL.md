---
name: peticion-inicial-monitorio-contrato-financiacion-77
description: "Redacta el escrito «Petición inicial de monitorio por contrato de financiación de vehículos» (formulario 77 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Petición inicial de monitorio por contrato de financiación de vehículos

> Formulario 0077 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] IMPORTE (9 veces)
- [ ] FECHA
- [ ] MARCA/MODELO (2 veces)
- [ ] MATRÍCULA
- [ ] NÚMERO
- [ ] Nº DE DOCUMENTO (4 veces)
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… representación de la entidad financiera»; «…nterés remuneratorio al tipo nominal del»; «…ual (TAE %) y se pagaría en un número de»; «… en los términos pactados en la cláusula»; «…y»; «…s cuotas correspondientes a los meses de»; «…, de»; «…, de [COMPLETAR]. y de»; «… fundado en la aplicación de la cláusula»; «…interés de demora pactado en la cláusula»; «…aciones que se acompañan como documentos»; «… documentos relacionados en el anexo. En»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 10.2 de la Ley 28/1998
- art. 813 de la LEC
- art. 812.2 de la LEC
- artículo 7.2 de la Ley 10/2012
- Ley 25/2015

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

### Formulario 0077 · Petición inicial de monitorio por contrato de financiación de vehículos

- Año del modelo: 2023
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 43 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D/Dª [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales en representación de la entidad financiera [COMPLETAR], según acredito por apoderamiento apud-acta otorgado ante el Letrado de la Administración de Justicia de (o por certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño), bajo la dirección letrada de D/Dª [NOMBRE Y APELLIDOS], Abogado/a del Iltre. Colegio de [LOCALIDAD], ante el Tribunal comparezco y como mejor en derecho proceda

DIGO

Por medio del presente escrito formulo PETICIÓN INICIAL DE PROCESO MONITORIO frente a D/Dª [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], en su condición de deudora principal, y frente a D/Dª [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], en su condición de fiadora solidaria, reclamando la cantidad de [IMPORTE] euros, más los intereses pactados, con base en los siguientes

HECHOS

PRIMERO.- Se formula esta solicitud de procedimiento monitorio por impago del contrato de financiación de bienes muebles concertado por lasdemandadas, en su condición de deudora principal y fiadora solidaria, respectivamente, con mi representada, que ascienden a la cantidad total de [IMPORTE] euros, la cual dirijo contra las citadas personas deudoras que residen en los domicilios designados.

Mi representada concertó con la parte demandada D/Dª [NOMBRE Y APELLIDOS], un contrato de financiación a comprador de bienes muebles a plazos de fecha [FECHA], que tenía como objeto financiar la compra de un vehículo automóvil marca [MARCA/MODELO] modelo [MARCA/MODELO] matrícula [MATRÍCULA].

La cantidad prestada era de [IMPORTE] euros, estipulándose por ambas partes un interés remuneratorio al tipo nominal del [COMPLETAR] % anual (TAE %) y se pagaría en un número de [COMPLETAR] plazos mensuales.

El interés de demora se fijaba en un tipo nominal del % anual.

Dicho contrato fue avalado solidariamente por D/Dª [NOMBRE Y APELLIDOS], en los términos pactados en la cláusula [COMPLETAR] del contrato con el siguiente tenor literal: "los fiadores afianzan solidariamente entre sí y con carácter solidario respecto de los deudores el cumplimiento de todas las obligaciones del contrato, con renuncia expresa a los beneficios legales de orden, división y excusión".

El contrato fue redactado conforme al modelo aprobado por la Dirección General de Registros y del Notariado de contrato de financiación a comprador de bienes muebles. Estas estipulaciones se encuentran recogidas en las cláusulas particulares número [NÚMERO] y [COMPLETAR] del contrato de financiación de bienes muebles, así como en las condiciones generales del contrato, aceptadas por el prestatario, que se acompañan, con la correspondiente información precontractual, como documentos número [Nº DE DOCUMENTO].

SEGUNDO.- La parte demandada dejó de abonar las cuotas correspondientes a los meses de [COMPLETAR], de [COMPLETAR]. y de [COMPLETAR], por importe de [IMPORTE] euros, por lo que mi representada, tras requerir de pago a la demandada y a la fiadora solidaria, que hicieron caso omiso a dicho requerimiento, se ve en la obligación de acudir a la vía jurisdiccional a fin de que se abonen las cantidades adeudadas que ascienden a [IMPORTE] euros, en concepto de recibos impagados, y a la cantidad de [IMPORTE] euros en concepto de capital pendiente, con más los intereses pactados.

Acompañamos como documentos número [Nº DE DOCUMENTO] burofax de requerimientos de pago, recibos impagados, declaración de vencimiento anticipado y liquidación del capital pendiente realizada por los servicios contables de la entidad que represento, a la que se incorpora el extracto de la cuenta del préstamo, con desglose de las partidas de cargo y abono y liquidación de saldo resultante.

Mi representada, ante el impago de las tres cuotas referenciadas, aplicó el vencimiento anticipado del contrato, fundado en la aplicación de la cláusula [COMPLETAR] del contrato suscrito que ha sido aportado como documento número [Nº DE DOCUMENTO], que establece: " La falta de pago de dos cualquiera de los plazos a que se hace referencia en el epígrafe “reconocimiento de deuda” facultará al financiador para exigir de inmediato del citado prestatario el abono de la totalidad de la deuda pendiente extinguiéndose el aplazamiento".

Este vencimiento por impago de dos plazos está expresamente autorizado por el art. 10.2 de la Ley 28/1998, de 13 de julio, de Venta a Plazos de Bienes Muebles, limitándose el contrato a recoger el contenido legal.

Asimismo, se reclama el interés de demora pactado en la cláusula [COMPLETAR] del contrato, que no excede en dos puntos del remuneratorio, tal como viene exigiendo la jurisprudencia.

De las cantidades adeudadas responden solidariamente la deudora principal y la fiadora, en virtud del pacto de fianza solidaria. Dicha cláusula de afianzamiento se ajusta a los requisitos establecidos jurisprudencialmente, habiendo expresado la STS núm. 56/2020, de 27 de enero (Recurso núm. 1624/2017), que el pacto de fianza solidaria, prevista expresamente en el art. 1822-2 CC, es ajustado a la regulación del Código Civil, y que el pacto de solidaridad excluye por sí mismo, sin necesidad de renuncia, tanto el beneficio de excusión (art. 1831.2º CC), como el de división (art. 1837-1 CC), de lo que resulta indudablemente la responsabilidad solidaria de la fiadora.

TERCERO.- Según lo expuesto, se reclama el pago de la deuda dineraria por la cantidad de [IMPORTE] euros, más los intereses pactados, al tratarse de una obligación líquida, determinada, vencida y exigible, la cual se acredita mediante principio de prueba suficiente mediante los documentos que habitualmente documentan los créditos y deudas en relaciones de esta clase, derivadas de una relación contractual duradera, las cuales se acreditan por los contratos, recibos, facturas y liquidaciones que se acompañan como documentos [COMPLETAR], cuyo pago se pretende mediante la presente reclamación.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

PRIMERO.- Jurisdicción y competencia. Conforme a lo dispuesto en el art. 813 de la LEC, en relación con lo dispuesto en el art. 85.1º LOPJ, será exclusivamente competente para el proceso monitorio el Tribunal de Instancia del domicilio o residencia del deudor, si no fueren conocidos, el del lugar en que el deudor pudiera ser hallado a efectos de requerimiento de pago por el tribunal, salvo que se trate de la reclamación de la deuda a que se refiere el número 2º del apartado 2 del art. 812, en cuyo caso serán también competente el Tribunal del lugar en donde se halle la finca, a elección del solicitante, ejercitándose en este caso la acción en el domicilio de los deudores.

SEGUNDO.- Representación y legitimación. Se cumplen los requisitos de representación y legitimación, ostentando legitimación activa mi representada en su condición de financiadora acreedora, en tanto que la legitimación pasiva de las personas demandadas lo es por su condición de financiado deudor y fiadora solidaria, respectivamente.

TERCERO.- Procedimiento. El procedimiento debe seguir el cauce establecido en los artículos 814 y siguientes de la LEC.

CUARTO.- Procedencia del proceso monitorio. Procede la reclamación por la vía del monitorio al reclamarse el pago de deuda dineraria líquida, determinada, acreditada mediante documentos, facturas, certificaciones y demás documentos, en el ámbito de las relaciones contractuales entre el acreedor y el deudor y su avalista, en este caso derivadas del contrato de financiación de bienes muebles, tal como exige el art. 812.2 de la LEC, siendo que además constituyen un sólido principio de prueba del derecho del peticionario.

Por lo expuesto,

SUPLICO AL TRIBUNAL se tenga por presentado este escrito con sus documentos y copias, se sirva admitirlo y tener por interpuesta petición de juicio monitorio frente a D/Dª [NOMBRE Y APELLIDOS] en reclamación de [IMPORTE] euros, acordándose por el Letrado de la Administración de Justicia:

1.° Que se requiera a las personas deudoras para que, en el plazo de veinte días, paguen la cantidad de [IMPORTE] euros y, para el caso de que en dicho plazo no atiendan el requerimiento o no comparezcan alegando razones de la negativa de pago, se dicte decreto dando por terminado el proceso monitorio y se me dé traslado del mismo para que pueda instar el despacho de ejecución por el principal, intereses y costas.

2.º Que si las personas deudoras se oponen por escrito alegando razones para negarse total o parcialmente al pago, se dé por terminado el monitorio y se acuerde seguir por los trámites del juicio verbal, dándome traslado de la oposición para poder impugnarla por escrito en diez días (o para formular demanda en el plazo de un mes, en el caso del cuantía del proceso ordinario).

OTROSÍ PRIMERO DIGO. (caso de persona jurídica no exenta y cuantía superior a 2.000 euros) Que estando la presente demanda sujeta al abono de la tasa por el ejercicio de la potestad jurisdiccional fijada por la Ley 10/2012, de 20 de noviembre, modificada por RDL 3/2013 y Ley 25/2015, de 28 julio, y desarrollada por Orden HAP/2662/2012, de 13 de diciembre, siendo mi representada persona jurídica no exenta de su pago, se acompaña a la presente demanda como documento nº [Nº DE DOCUMENTO] la correspondiente autoliquidación con el ejemplar para la Administración de Justicia debidamente validado y en el que consta el pago de la cantidad de 100 euros correspondiente a la cuota fija, sin que se incluya la cuota variable prevista en el artículo 7.2 de la Ley 10/2012 al haber sido declarado inconstitucional y nulo por la STC 140/2016, de 21 de julio.

SUPLICO AL TRIBUNAL que tenga por hecha la anterior manifestación a los efectos pertinentes y por acompañado el documento justificativo del abono de la tasa.

OTROSÍ SEGUNDO DIGO que se acompaña en anexo relación de documentos presentados, debidamente foliados y con índice electrónico, para su debida localización y consulta.

SUPLICO AL TRIBUNAL tenga hecha esta manifestación a los efectos oportunos y por aportados los documentos relacionados en el anexo.

En [COMPLETAR] a. de [COMPLETAR] de [COMPLETAR]

El Abogado El Procurador
