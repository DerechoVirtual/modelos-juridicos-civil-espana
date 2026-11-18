---
name: contestacion-demanda-verbal-allanamiento-parcial-169
description: "Redacta el escrito «Contestación a demanda verbal con allanamiento parcial» (formulario 169 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a demanda verbal con allanamiento parcial

> Formulario 0169 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] NÚMERO
- [ ] SEDE (2 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] Nº DE DOCUMENTO
- [ ] IMPORTE (5 veces)
- [ ] Sentencia del Tribunal Supremo de 17 de diciembre de 1990 
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…representación que ostento de la entidad»; «…, y bajo la dirección Letrada de Don»; «…numeración del juzgado de procedencia).]»; «…e de la demanda formulada por la entidad»; «…aticias por el periodo comprendido entre»; «… acreditativos, acompaño como documentos»; «…lo 217 de la Ley de Enjuiciamiento Civil»

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 19 y 21 LEC
- arts. 438.8 y 438.10 de la LEC

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

### Formulario 0169 · Contestación a demanda verbal con allanamiento parcial

- Año del modelo: 2021
- Revisión 17-11-2026: 3 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 19 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Juicio verbal número [NÚMERO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D/Dª [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en la representación que ostento de la entidad [COMPLETAR], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], y bajo la dirección Letrada de Don [COMPLETAR] ante la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] en el juicio verbal arriba expresado comparezco y, como mejor proceda en Derecho, DIGO:

Que habiéndose dado traslado a esta parte de la demanda formulada por la entidad [COMPLETAR], en reclamación de [IMPORTE] euros por impago de renta arrendaticia e indemnización de daños y perjuicios, siguiendo instrucciones de mi poderdante, por medio del presente escrito y en nombre del mismo, formulo en tiempo y forma CONTESTACIÓN A LA DEMANDA, oponiéndome en parte a la misma, con allanamiento parcial en los términos que se dirán, y ello en base a los siguientes

HECHOS

PRIMERO.- La demanda que se ha interpuesto frente a mi principal tiene por objeto las pretensiones relativas a la reclamación de rentas arrendaticias por el periodo comprendido entre [COMPLETAR] e indemnización de daños y perjuicios por desperfectos en la vivienda arrendada y lucro cesante.

De la reclamación presentada se acepta la relación arrendaticia y el importe reclamado de las rentas por el periodo adeudado. Lo que no se acepta es la pretensión indemnizatoria por daños y perjuicios, negándose los hechos expuestos en el escrito de demanda con relación a esta pretensión.

Es por ello que la oposición objeto de esta contestación solamente se centra en este extremo, allanándose mi representada a los pedimentos que se contienen en la demanda relativos al pago de las rentas arrendaticias adeudadas por importe de [IMPORTE] euros.

SEGUNDO.- Se niegan todos los demás hechos expuestos en la demanda que sostienen la pretensión indemnizatoria de la parte actora en concepto de desperfectos y lucro cesante.

Mi representada entregó la vivienda en buen estado, sin que los desperfectos alegados por la actora resulten imputables a esta parte, puesto que se trata de deficiencias que corresponden a la antigüedad del inmueble y no son consecuencia de un indebido uso del mismo por parte del arrendatario. A efectos acreditativos, acompaño como documentos [COMPLETAR] fotografías correspondientes al día en que se produjo el desalojo del inmueble, donde se puede comprobar que se encontraba en buen estado.

La jurisprudencia afirma que la reparación por el incumplimiento total o parcial de las obligaciones derivadas del contrato requiere la constancia de la existencia de daños y perjuicios y la prueba de los mismos, correspondiendo a quien solicita su reparación la carga de la prueba de los daños y perjuicios, de acuerdo con la norma general de distribución de la carga de la prueba del artículo 217 de la Ley de Enjuiciamiento Civil [COMPLETAR], como hecho positivo y constitutivo de su pretensión de resarcimiento, lo cual aquí no se produce donde se describen unas reparaciones que corresponden a reformas de la vivienda, a conveniencia del propietario, y que encajan en el concepto de obras de mejora, de las que se pretende derivar, además, un inexistente derecho al lucro cesante por no haber podido alquilar el inmueble en el periodo de las obras, que además a todas luces es excesivo.

Por tanto, ni existen daños en el inmueble imputables al arrendatario, ni es procedente la pretensión de lucro cesante con base a los supuestos desperfectos que no son tales, puesto que se trata de obras de reforma o mejora derivadas de la antigüedad del inmueble y estado que presentaba con anterioridad a ser arrendado, siendo totalmente improcedente y abusivo la pretensión indemnizatoria de lucro cesante por obras que se realizan a conveniencia del arrendador, en un periodo de tiempo reclamado que es absolutamente desproporcionado.

Por todo lo expuesto, se solicita la desestimación de la demanda en relación a estas pretensiones

FUNDAMENTOS DE HECHO

PRIMERO.- Competencia y procedimiento.- Se acepta la competencia y la tramitación de la causa por los tramites del juicio verbal, aceptando asimismo la cuantía de [IMPORTE] euros y asumiendo las alegaciones en este sentido vertidas en el escrito de demanda.

SEGUNDO.- Allanamiento parcial: Se acepta la pretensión referente a lo que son las rentas reclamadas por importe de [IMPORTE] euros, allanándose mi mandante con fundamento en los arts. 19 y 21 LEC a los pedimentos a ellos referidos.

TERCERO.- Oposición parcial de fondo: Nos oponemos a las pretensión indemnizatoria al no haber quedado acreditados los daños y perjuicios alegados. En este sentido, en cuanto a los daños materiales, es doctrina reiterada (Sentencias del Tribunal Supremo de 6 de abril de 1995, rec. 443/1992, y 29 de diciembre de 2004, rec. 3394/1998) que la indemnización por el incumplimiento total o parcial de las obligaciones derivadas del contrato requiere la constancia de la existencia de daños y perjuicios y la prueba de los mismos, correspondiendo al demandante la carga de la prueba de los daños y perjuicios, de acuerdo con la norma general de distribución de la carga de la prueba del artículo 217 de la Ley de Enjuiciamiento Civil, como hecho positivo y constitutivo de su pretensión de resarcimiento. En cuanto al lucro cesante, es doctrina reiterada [Sentencia del Tribunal Supremo de 17 de diciembre de 1990 ], que la alegación del lucro cesante exige no sólo la posibilidad de haber podido obtener ganancias en ]caso de no haberse producido el evento causante de los daños, sino que los perjuicios o lucro cesante han de apreciarse restrictivamente y ha de probarse rigurosamente que se dejaron de obtener las ganancias, sin que sean dudosas o contingentes y sólo fundadas en esperanzas, debiendo además guardar la debida relación de causa a efecto con la actuación negligente de la demandada.

CUARTO.- Costas. En materia de costas los arts 394 y 395 LEC, debiendo imponerse a la parte actora si mantiene sus pretensiones con relación a la pretensión controvertida.

En base a lo anterior,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito junto con sus copias, teniendo a esta parte por personada en las presentes actuaciones entendiéndose conmigo las siguientes diligencias y por contestada a la demanda interpuesta contra mi principal y tras la pertinente tramitación se sirva en cuanto a la pretensión a la que se allana mi mandante dictar, si así lo solicitare el demandante, auto por el que se acepte el allanamiento parcial en [IMPORTE] euros, sin costas. En lo referente a la pretensión de indemnización de daños y perjuicios se solicita que, tras la tramitación completa del proceso, se sirva en su momento dictar sentencia por la que se desestime la pretensión, con imposición de costas al demandante.

OTROSÍ PRIMERO DIGO que, a los efectos de los arts. 438.8 y 438.10 de la LEC, esta parte interesa la celebración de vista al existir controversia sobre los hechos y ser necesaria la práctica de prueba para la resolución de este proceso.

Por lo que,

SUPLICO AL TRIBUNAL tenga por efectuadas las anteriores manifestaciones y acuerde la celebración de vista.

OTROSÍ SEGUNDO DIGO que se acompaña en anexo relación de documentos presentados debidamente foliados y con índice electrónico para su debida localización y consulta.

Por lo que,

SUPLICO AL TRIBUNAL tenga hecha esta manifestación a los efectos oportunos y por aportados los documentos relacionados en el anexo.

En [LUGAR], a [FECHA].

Firma Abogado y Procurador
