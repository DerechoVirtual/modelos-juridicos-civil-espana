---
name: demanda-reclamacion-hacer-523
description: "Redacta el escrito «Demanda de reclamación de hacer» (formulario 523 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de reclamación de hacer

> Formulario 0523 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] NÚMERO (3 veces)
- [ ] COLEGIO
- [ ] CALLE
- [ ] FECHA (3 veces)
- [ ] IMPORTE
- [ ] ÓRGANO O PERSONA
- [ ] LUGAR
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…o la mercantil»; «…de»; «…o la mercantil»; «…mandado/a acordaron mediante contrato de»; «…dada no ha cumplido con su obligación de»; «…anda. Se aportan como documentos números»; «…telegrama y burofax de fechas»; «…iante correspondencia escrita, en fechas»; «…o la mercantil»; «…o la mercantil [COMPLETAR] a realizar»

## Elecciones que hay que hacer

- Ordinario / Verbal
- ordinario / verbal

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de personas físicas / En caso de personas jurídicas — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de juicio ordinario / En caso de juicio verbal — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: En el caso de que se trate de un juicio ordinario o de un juicio verbal con una cuantía superior a 2.000 euros / En el caso de que se trate de un juicio verbal con una cuantía inferior a 2.000 euros — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 1098 CCiv
- art. 36 LEC
- art. 253.1 LEC
- art. 10 LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 1091 CCiv
- art. 394.1 LEC
- art. 706.2 LEC

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

### Formulario 0523 · Demanda de reclamación de hacer

- Año del modelo: 2016
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 2 desplegables convertidos en elección en blanco; 3 bloques de opciones sin texto dejados en blanco con sus rótulos; 31 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda en proceso declarativo ejercitando acción de cumplimiento de obligación de hacer en base al art. 1098 CCiv.

Adaptado a la LO 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, que actúa en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS] o la mercantil [COMPLETAR], con domicilio en [LOCALIDAD], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], a quien asiste el/la Letrado/a en ejercicio D./Dña. [NOMBRE Y APELLIDOS], colegiado/a n.º [NÚMERO] del Iltre. Colegio de Abogados de [COLEGIO], con despacho abierto en esta localidad, calle [CALLE] de [COMPLETAR], ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que, en la representación que ostento, vengo a interponer demanda de Juicio [ELEGIR: Ordinario / Verbal] frente a D./Dña. [NOMBRE Y APELLIDOS] o la mercantil [COMPLETAR], con domicilio en [LOCALIDAD].

Se ejercita en la presente demanda acción de cumplimiento de obligación de hacer en base al art. 1098 CCiv.

Fundamento la misma en los siguientes hechos y consideraciones jurídicas:

HECHOS

PRIMERO.- Que mi representado/a y la demandado/a acordaron mediante contrato de [COMPLETAR] de fecha [FECHA].

Se acompaña como documento n.º [NÚMERO] copia del contrato suscrito por las partes.

SEGUNDO.- Que a día de hoy, la parte demandada no ha cumplido con su obligación de [COMPLETAR].

TERCERO.- Que habiendo resultado infructuosas todas las gestiones realizadas por mi representada para que la demandada cumpla con su obligación, es por ello que esta parte se ve en la necesidad de interponer la presente demanda.

Se aportan como documentos números [COMPLETAR] telegrama y burofax de fechas [COMPLETAR] así como certificado de Correos de su recepción.

CUARTO.- La parte actora manifiesta que, a mayor abundamiento, previo a la presentación de la presente demanda, se han llevado a cabo negociaciones con la parte demandada, con el objetivo de cumplir el requisito de procedibilidad, y resolver la controversia de manera amistosa y extrajudicial. Dichas negociaciones se desarrollaron en cumplimiento de los principios de buena fe, con la intención de alcanzar una solución satisfactoria; incluyéndose entre las acciones realizadas el intercambio de comunicaciones formales mediante correspondencia escrita, en fechas [COMPLETAR], en las cuales esta parte expresó su disposición para dialogar y propuso alternativas de solución.

Finalmente, mi representado envió un requerimiento fehaciente al demandado con fecha [FECHA], fijando un plazo de 30 días naturales para llegar a un acuerdo amistoso, a través del abogado que firma este escrito, el cual fue contestado por el demandado por el mismo medio, rechazando el acuerdo/ habiendo sido solo posible un acuerdo parcial, viéndonos en la necesidad de acudir a la presente vía judicial, respecto a los extremos de la controversia en los que se mantiene la discrepancia.

Acompaño como documento nº [Nº DE DOCUMENTO], el requerimiento efectuado y como documento nº [Nº DE DOCUMENTO], la contestación del demandado.

A los anteriores Hechos, son aplicables los siguientes:

FUNDAMENTOS DE DERECHO

I.- JURISDICCIÓN Y COMPETENCIA.

El art. 36 LEC atribuye con carácter general a la jurisdicción de nuestro Estado y al orden civil, el conocimiento de una materia como la presente.

Los arts. 85.1º LOPJ y 45 LEC, designan a los Tribunales de Instancia, como los órganos con la competencia específica objetiva y funcional para resolver estos pleitos.

[ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de personas físicas / En caso de personas jurídicas — el texto de cada opción no venía en el formulario original]

II.- PROCEDIMIENTO.

[ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de juicio ordinario / En caso de juicio verbal — el texto de cada opción no venía en el formulario original]

III.- CUANTÍA.

Cumpliendo la exigencia del art. 253.1 LEC, y en atención al coste de la obligación de hacer cuya realización se insta, se cifra la cuantía de la demanda en [IMPORTE] euros ( €), conforme al art. 251.11.ª LEC, a cuya acreditación se acompaña dictamen pericial, que hace documento n.º [NÚMERO], emitido por [ÓRGANO O PERSONA] (1).

IV.- LEGITIMACIÓN.

El art. 10 LEC legitima para comparecer y actuar en juicio a los titulares de la relación jurídica o del objeto litigioso. En el caso de autos, la ostenta el actor, como parte perjudicada por el incumplimiento del demandado, sobre quien recae la legitimación pasiva para el ejercicio de esta acción.

V.- POSTULACIÓN.

[ELEGIR UNA OPCIÓN Y REDACTARLA: En el caso de que se trate de un juicio ordinario o de un juicio verbal con una cuantía superior a 2.000 euros / En el caso de que se trate de un juicio verbal con una cuantía inferior a 2.000 euros — el texto de cada opción no venía en el formulario original]

VI.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VII.- FONDO DEL ASUNTO.

El art. 1091 CCiv dispone que las obligaciones que nacen de los contratos tienen fuerza de ley entre las partes contratantes.

Tratándose de una obligación de hacer cuyo cumplimiento se reclama, se le debe aplicar la regla contenida en el art. 1098 CCiv, de manera que "si el obligado a hacer alguna cosa no la hiciere, se mandará ejecutar a su costa".

VIII.- COSTAS.

En aplicación del art. 394.1 LEC deberán imponerse las costas a la parte demandada.

Por lo expuesto,

SUPLICO AL TRIBUNAL,

que teniendo por presentado este escrito, documentos que acompañan y copias preceptivas, se sirva admitir todo ello, y, en su virtud, de conformidad con las manifestaciones que contiene, tenga por interpuesta en la representación ostento, demanda de juicio declarativo [ELEGIR: ordinario / verbal], y previos los trámites legales pertinentes, dicte sentencia condenando a D./Dña. [NOMBRE Y APELLIDOS] o la mercantil [COMPLETAR] a realizar [COMPLETAR], con condena en costas a la demandada.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

NOTAS DEL FORMULARIO

(1) Cuando la demanda tiene por objeto una prestación de hacer no personalísima, su cuantía consiste en el importe de su realización, o el de los daños y perjuicios derivados del incumplimiento, otorgándose facultad de elección al actor.

En orden a la fijación de la cuantía, salvo en el supuesto que el título haya previsto expresamente las consecuencias del incumplimiento, la determinación inicial del coste de aquello cuya realización se inste precisará normalmente la elaboración de dictamen pericial, sin perjuicio de que, escogida por el actor esta opción en ejecución de sentencia, conforme al art. 706.2 LEC, se valorará previamente el coste de dicho hacer por un perito tasador designado por el Letrado de la Administración de Justicia. Por el contrario, la valoración de los daños y perjuicios cabe hacerla en forma relativa.

Si además de instarse el cumplimiento, se solicita también la indemnización, la cuantía de la demanda vendrá determinada por la suma de ambas cantidades.

Cuando la prestación sea de hacer personalísimo o consista en un no hacer, la cuantía se determina exclusivamente por el importe o cálculo de los daños y perjuicios.

========================================================================
