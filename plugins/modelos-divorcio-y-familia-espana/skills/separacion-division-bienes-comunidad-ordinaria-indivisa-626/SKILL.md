---
name: separacion-division-bienes-comunidad-ordinaria-indivisa-626
description: "Redacta el escrito «Separación con división de bienes en comunidad ordinaria indivisa: demanda» (formulario 626 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Separación con división de bienes en comunidad ordinaria indivisa: demanda

> Formulario 0626 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] DNI/NIE
- [ ] LOCALIDAD (3 veces)
- [ ] CALLE (2 veces)
- [ ] Nº DE DOCUMENTO (4 veces)
- [ ] NÚMERO
- [ ] COLEGIO
- [ ] FECHA (3 veces)
- [ ] LUGAR
- [ ] Otros 17 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…DE»; «… actúa en nombre y representación de Don»; «…, cuyo despacho se abre en»; «…INARIA INDIVISA, frente a su esposa Doña»; «…, con domicilio actual en»; «…atos y argumentos: HECHOS PRIMERO.- Doña»; «…y Don»; «…contrajeron matrimonio civil en»; «…es que se especifican a continuación: 1)»; «…2)»; «…2) [COMPLETAR] 3)»; «…Se acompaña como documentos números»; …

## Elecciones que hay que hacer

- SECCIÓN CIVIL / SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 753 LEC
- art. 770 LEC
- arts. 81 CCiv
- art. 437.1 LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 774.4 LEC
- art. 755 LEC
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

### Formulario 0626 · Separación con división de bienes en comunidad ordinaria indivisa: demanda

- Año del modelo: 2016
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 desplegables convertidos en elección en blanco; 34 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda de separación contenciosa acumulando acción de división de cosa común con respecto a los bienes que los cónyuges tienen en pro indiviso.

Formulario adaptado a la reforma procesal de la LO 1/2025.

AL TRIBUNAL DE INSTANCIA [ELEGIR: SECCIÓN CIVIL / SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD] DE [COMPLETAR]

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, que actúa en nombre y representación de Don [COMPLETAR], provisto de DNI n.º [DNI/NIE], con domicilio en [LOCALIDAD], calle [CALLE], como acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], bajo dirección del Letrado D./Dña. [NOMBRE Y APELLIDOS], colegiado/a n.º [NÚMERO] del Iltre. Colegio de Abogados de [COLEGIO], cuyo despacho se abre en [COMPLETAR], calle [CALLE], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO:

Que por medio del presente escrito, siguiendo la instrucción de mi mandante, vengo a formular DEMANDA DE SEPARACIÓN MATRIMONIAL con ejercicio simultáneo de ACCIÓN DE DIVISIÓN DE BIENES EN COMUNIDAD ORDINARIA INDIVISA, frente a su esposa Doña [COMPLETAR], con domicilio actual en [COMPLETAR], con base a los siguientes datos y argumentos:

HECHOS

PRIMERO.- Doña [COMPLETAR] y Don [COMPLETAR] contrajeron matrimonio civil en [COMPLETAR], el día [FECHA], a cuya acreditación se acompaña certificación expedida por el Registro Civil de [LOCALIDAD], como documento número

Desde la celebración de dicho matrimonio ha transcurrido sobradamente, por tanto, un período de tiempo superior a los tres meses.

SEGUNDO.- De este matrimonio no ha habido descendencia.

TERCERO.- El matrimonio fue celebrado bajo el régimen económico matrimonial de separación de bienes.

No obstante, ambos cónyuges son cotitulares en proindiviso, de los siguientes bienes que se especifican a continuación:

1) [COMPLETAR]
2) [COMPLETAR]
3) [COMPLETAR]

Se acompaña como documentos números [COMPLETAR] escrituras de propiedad correspondientes, notas registrales y facturas acreditativas de la titularidad en pro indiviso de dichos bienes.

CUARTO.- Mi representado Don [COMPLETAR], sin que haya sido posible tramitarlo de mutuo acuerdo, mediante la presente demanda, interesa se decrete judicialmente la separación conyugal, frente a su esposa Doña [COMPLETAR], y ejerce simultáneamente la acción de división de cosa común con respecto a los citados bienes que tienen en pro indiviso, interesando igualmente, dado que como se ha señalado existen varios bienes en comunidad ordinaria indivisa, sean considerados en conjunto a efectos de formar lotes y adjudicarlos.

A tales efectos, se acompaña como documento número [Nº DE DOCUMENTO] propuesta de inventario y de división de los bienes, en la que se han realizado los oportunos lotes.

QUINTO.- Previamente a la presentación de la presente demanda, se han llevado a cabo negociaciones con la parte demandada, con el objetivo de cumplir el requisito de procedibilidad, y resolver la controversia de manera amistosa y extrajudicial. Dichas negociaciones se desarrollaron en cumplimiento de los principios de buena fe, con la intención de alcanzar una solución satisfactoria; incluyéndose entre las acciones realizadas el intercambio de comunicaciones formales mediante correspondencia escrita, en fechas [COMPLETAR], en las cuales esta parte expresó su disposición para dialogar y propuso alternativas de solución.

Finalmente, mi representado envió un requerimiento fehaciente al demandado con fecha [FECHA], fijando un plazo de 30 días naturales para llegar a un acuerdo amistoso, a través del abogado que firma este escrito, el cual fue contestado por el demandado por el mismo medio, rechazando el acuerdo/ habiendo sido solo posible un acuerdo parcial, viéndonos en la necesidad de acudir a la presente vía judicial, respecto a los extremos de la controversia en los que se mantiene la discrepancia.

Acompaño como documento nº [Nº DE DOCUMENTO], el requerimiento efectuado y como documento nº [Nº DE DOCUMENTO], la contestación del demandado.

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA.

Es competente el Tribunal de Instancia del lugar del domicilio de la demandada, que es el último domicilio conyugal común, conforme al art. 769.1 párrafo 1.º LEC.

II.- PROCEDIMIENTO.

El proceso adecuado es el del juicio verbal (arts. 437 y ss.), como se diseña especialmente por el art. 753 LEC, y con las peculiaridades del art. 770 LEC para conocer de las demandas contenciosas de separación.

III.- LEGITIMACIÓN.

Tiene legitimación activa ordinaria el demandante por hallarse en la situación jurídica de relación conyugal, como detenta la pasiva su esposa demandada (arts. 81 CCiv y 10 LEC).

IV.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 en relación con el art. 437.1 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

V.- FONDO.

El fondo de la pretensión consiste en la declaración de separación conyugal sin consenso de los cónyuges, a instancia de uno de ellos (art. 81.2.º CCiv), sin otra base que la libre voluntad del consorte, transcurridos más de tres meses desde la celebración del matrimonio.

VI.- ACUMULACIÓN OBJETIVA DE ACCIONES.

Conforme a lo dispuesto en el art. 437.4.4.ª LEC, se ejercita simultáneamente la acción de división de cosa común con respecto a los bienes que los cónyuges tienen en pro indiviso, solicitando, dado que existen varios bienes en comunidad ordinaria indivisa, que sean considerarlos en conjunto a efectos de formar lotes y adjudicarlos.

VII.- ADOPCIÓN DE MEDIDAS.

El art. 774.4 LEC establece que el Tribunal determinará en la propia sentencia las medidas sobre la disolución del régimen económico.

VIII.- REGISTRO CIVIL.

La sentencia de separación se comunicará de oficio por el Letrado de la Administración de Justicia al Registro Civil, en el que consta el matrimonio de los litigantes, según dispone el art. 755 LEC.

IX.- COSTAS.

Las costas procesales deben ser impuestas a la parte demandada, por criterio del íntegro vencimiento, en atención al art. 394 LEC.

Y demás normas y jurisprudencia de general y pertinente aplicación.

En virtud de lo expuesto,

SUPLICO AL TRIBUNAL

que, teniendo por presentado este escrito con los documentos que se acompañan y sus copias, por el Letrado de la Administración de Justicia se digne admitirlos, tenerme por comparecido y parte en la representación que ostento, y por interpuesta DEMANDA DE SEPARACIÓN CONYUGALY ACCIÓN DE DIVISIÓN DE COSA COMÚN CON RESPECTO A LOS BIENES EN COMUNIDAD ORDINARIA INDIVISA, y seguido que sea el procedimiento por sus pertinentes trámites, se sirva dictar sentencia por la que, estimando la presente demanda, decrete la separación de matrimonio formado por Don [COMPLETAR] y Doña [COMPLETAR], así como la división de su patrimonio común adquirido constante el matrimonio en pro indiviso, compuesto por los bienes relacionados en la propuesta adjunta, en la que se han realizado los oportunos lotes, acordándose asimismo la inscripción de la sentencia en el Registro Civil de [LOCALIDAD], y expresa imposición de las costas procesales a la demandada si no consiente la pretensión actora que ha forzado.

Como es Justicia de hacerse en [LUGAR], a [FECHA].

OTROSÍ DIGO: Que por necesitar para otros usos la copia de escritura de poder acreditativa de la representación del suscrito Procurador, intereso y

SUPLICO AL TRIBUNAL. Se sirva acordar su desglose y devolución a esta parte, dejando en autos testimonio de la misma.

Reitero Justicia en lugar y fecha "ut supra".

Firma del Abogado/a	Firma del Procurador/a

========================================================================
