---
name: demanda-oposicion-guarda-administrativa-menor-fines-152
description: "Redacta el escrito «Demanda de oposición a la guarda administrativa de un menor con fines de adopción» (formulario 152 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de oposición a la guarda administrativa de un menor con fines de adopción

> Formulario 0152 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS
- [ ] NÚMERO
- [ ] FECHA (4 veces)
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] IMPORTE (2 veces)
- [ ] ÓRGANO O PERSONA
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…bunales en nombre y representación de Dª»; «…y D»; «…inistrativa dictada por la Consejería de»; «…mis mandantes, padres del menor»; «…formes psicosociales que obran en folios»; «… entidad pública como lo es en este caso»; «…, dictada por la Consejería de»; «… con fines de adopción relativa al menor»; «…os en el anexo. Es justicia que insto en»; «…y»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 779 de la LEC
- art. 780 de la LEC
- art. 780.1 de la LEC
- art. 3.2 LO 1/2025
- art. 172 CC
- art. 394 LEC
- Ley Orgánica 1/1996

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

### Formulario 0152 · Demanda de oposición a la guarda administrativa de un menor con fines de adopción

- Año del modelo: 2021
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 24 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D/Dª [NOMBRE Y APELLIDOS], Procurador de los Tribunales en nombre y representación de Dª [COMPLETAR] y D [COMPLETAR], cuya representación consta en autos de juicio sobre oposición a medida de protección de menores seguido en ese Tribunal con el número [NÚMERO] ante el Tribunal comparezco y como mejor proceda en Derecho, DIGO:

Que en la representación que ostento, dentro del plazo concedido, formulo DEMANDA de oposición a la resolución administrativa dictada por la Consejería de [COMPLETAR] en fecha [FECHA]. sobre la guarda del menor ……………….. con fines de adopción, fundando la demanda en los siguientes:

HECHOS

PRIMERO.- En fecha [FECHA] mis mandantes, padres del menor [COMPLETAR], recibieron notificación de la resolución de la Consejería demandada por que se declaraba el desamparo del menor y la asunción de la guarda con fines de adopción, habiéndose impugnado mediante escrito presentado en fecha [FECHA].

SEGUNDO.- La fundamentación de la medida adoptada se basa en la falta de idoneidad de los progenitores, argumentando la entidad pública que existían antecedentes de dificultad en la educación del menor, dudas en cuanto a la estabilidad de sus ingresos, no acreditando su situación económica ni labora de ellos padres, que la organización de la vivienda no es adecuada en relación a las necesidades presente y futuras del menor, por carecer de espacio suficiente, y que los progenitores presentan problemas mentales y de adicción a alcohol y sustancias tóxicas.

Negamos la concurrencia de estos fundamentos, pues mis representados han cumplido con sus obligaciones parentales en todo momento, habiendo desplegado una conducta tendente a velar por el cuidado y educación del hijo común, y si bien existió una situación transitoria donde los demandantes estuvieron en situación de paro, lo cierto es que actualmente tienen trabajo estable y han superado sus dificultades de adicción a sustancias tóxicas.

Tal como se acredita por los contratos y nóminas que se acompañan como documentos número [Nº DE DOCUMENTO], ambos progenitores están trabajando en la actualidad, percibiendo un salario mensual de [IMPORTE] euros y [IMPORTE] euros, respectivamente. Por su parte, ambos progenitores se han sometido a tratamiento de desintoxicación, acompañándose como documentos número [Nº DE DOCUMENTO] informes médicos expedidos por [ÓRGANO O PERSONA], en los cuales se pone de manifiesto que el problema de adicción a sustancias tóxicas se encuentra totalmente controlado y superado.

TERCERO.- El mantenimiento del menor en la unidad familiar resulta necesario a la vista del principio rector de los procesos sobre medidas de protección de los menores que es la necesidad de que prevalezca su interés como principio prioritario, siendo que el menor ha crecido y se ha desarrollado en un entorno familiar y social, con fuertes vínculos afectivos con sus padres y con la familia extensa, según resulta de los informes psicosociales que obran en folios [COMPLETAR] del expediente administrativo.

Esta situación puede verse alterada con la resolución administrativa impugnada en contra del interés superior del menor, pues el cambio del régimen de guarda acordado en ningún caso es beneficioso para el niño, dada su integración en un entorno familiar satisfactorio, en el que se han desarrollado vínculos afectivos entre todos ellos y se han puesto a su disposición los medios necesarios para su desarrollo físico y psíquico, estando superada la situación transitoria que motivó la intervención de la entidad pública, según se recoge en el reciente informe de los servicios sociales que se acompaña como documento número [Nº DE DOCUMENTO], donde se recoge que se ha normalizado la situación laboral y económica de los padres, así como las condiciones de la vivienda, y que se estima beneficioso para el niño que se mantenga su convivencia en la unidad familiar, añadiendo que un cambio en la situación del menor le expondrá probablemente a un notable desajuste psicológico compatible con problemas emocionales, conductuales y educativos.

Por todo ello, mis representados se oponen a la referida declaración de desamparo y asunción de guarda con fines de adopción, por ser contraria al interés del menor y por no ser ciertos los hechos sobre los que se fundamenta, como acreditarán mediante la prueba oportuna, puesto que los demandantes reúnen todas las condiciones para el adecuado cuidado de su hijo.

FUNDAMENTOS DE DERECHO

PRIMERO.- Competencia. Es competente este Tribunal por ser el del domicilio de la Entidad Pública, de acuerdo a lo previsto en el artículo 779 de la LEC.

SEGUNDO.- Procedimiento: Es de aplicación lo dispuesto en el art. 780 de la LEC en cuanto al procedimiento, sin que sea necesaria reclamación previa y al haberse interpuesto la oposición dentro de plazo, debiendo ser oído el menor en este procedimiento.

TERCERO.- Legitimación. La ostentan mis representados como progenitores del menor, según lo establecido en el art. 780.1 de la LEC, estando legitimada pasivamente la entidad pública demandada y debiendo intervenir el Ministerio Fiscal.

CUARTO.- Cumplimiento de los requisitos de procedibilidad. Conforme a lo dispuesto en el art. 3.2 LO 1/2025, la presente demanda no está sujeta al requisito de MASC, en cuanto se dirige contra una entidad pública como lo es en este caso [COMPLETAR].

QUINTO.- Fundamentos de fondo: Es de aplicación el principio de interés del menor y el de inserción en la propia familia, recogido en el art. 172 CC, arts. 2 y 18 la Ley Orgánica 1/1996, así como en la normativa internacional, estableciendo el artículo 9 de la Convención de Derechos del Niño su derecho a ser educado en su propia familia. En este caso, se dan las condiciones para el mantenimiento de la unidad familiar, por el trabajo estable de los padres, la posesión de una vivienda en condiciones y los vínculos afectivos del menor con su familia biológica, siendo estas medidas las más favorables para el desarrollo físico, intelectivo e integración social del menor tal como se exige en la jurisprudencia que interpreta dichos preceptos debiendo citarse las SSTS 565/2009, de 31 de julio, 397/2011, de 13 de junio y 444/2015, de 14 de julio, entre otras.

SEXTO.- Costas: Procede imponer las costas a la entidad pública demandada, conforme al art. 394 LEC, de cuya aplicación no está exenta.

Por ello,

AL TRIBUNAL SUPLICO Tenga por presentado este escrito, con los documentos adjuntos y sus copias, teniendo por interpuesta demanda en oposición a la resolución administrativa de fecha [FECHA], dictada por la Consejería de [COMPLETAR], admitiendo la misma y tras la tramitación legalmente establecida y la práctica de la prueba pertinente, se dicte sentencia por la que se deje sin efecto la resolución administrativa arriba expresada y, por tanto, la medida de asunción de guarda con fines de adopción relativa al menor [COMPLETAR], reintegrando al mismo en el domicilio familiar bajo la patria potestad de sus progenitores.

OTROSÍ DIGO que se acompaña en anexo relación de documentos presentados, debidamente foliados y con índice electrónico, para su debida localización y consulta.

SUPLICO AL TRIBUNAL tenga hecha esta manifestación a los efectos oportunos y por aportados los documentos relacionados en el anexo.

Es justicia que insto en [COMPLETAR] y [COMPLETAR]

Firma de Abogado y Procurador
