---
name: contestacion-oponiendo-prescripcion-accion-524
description: "Redacta el escrito «Contestación oponiendo prescripción de la acción» (formulario 524 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación oponiendo prescripción de la acción

> Formulario 0524 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] FECHA (7 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] IMPORTE
- [ ] LUGAR
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…, con despacho profesional en»; «…de»; «…tique, se aportan los documentos números»; «…a»; «…relativo de la demanda. Por el contrario»; «… de fondo de la demandante, toda vez que»

## Elecciones que hay que hacer

- Procurador/a / Procurador/a a
- el Letrado / la Letrada

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 1902 CCiv
- art. 1968 CCiv
- art. 1973 CCiv
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

### Formulario 0524 · Contestación oponiendo prescripción de la acción

- Año del modelo: 2016
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 2 desplegables convertidos en elección en blanco; 22 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Contestación a demanda de juicio ordinario alegando prescripción de la acción por transcurso del plazo de un año que el art. 1968.2.º CCiv establece para el ejercicio de la acción de responsabilidad extracontractual del art. 1902 CCiv.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], [ELEGIR: Procurador/a / Procurador/a a] de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS] según acredito mediante escritura de poder inscrito en el Registro Electrónico de Apoderamientos Judiciales, a cuya justificación aporto certificación de dicho Registro como documento nº [Nº DE DOCUMENTO], dirigida por [ELEGIR: el Letrado / la Letrada] abajo firmante D./Dña. [NOMBRE Y APELLIDOS], con despacho profesional en [COMPLETAR], ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que con fecha [FECHA] de [COMPLETAR] del presente se ha procedido al emplazamiento de mi mandante en autos de Juicio Ordinario n.º [Nº DE PROCEDIMIENTO]/[AÑO], seguidos ante ese Tribunal a instancia de D./Dña. [NOMBRE Y APELLIDOS], por cuanto, mediante el presente escrito, procedo a contestar a la demanda.

Con carácter previo esta parte opone la PRESCRIPCIÓN DE LA ACCIÓN EJERCITADA, del art. 1.968.2.º CCiv, con fundamento en los siguientes:

HECHOS

ÚNICO.-

El demandante reclama indemnización de [IMPORTE] euros por los daños producidos en la vivienda de su propiedad como consecuencia de la pérdida de agua en las cañerías de la cocina de la vivienda de mi mandante, que según manifiesta se produjo en día [FECHA] y que ocasionó importantes desperfectos en los techos de su vivienda, concretamente en el baño, cocina, pasillo y salón, afectando a muebles y enseres llegando al suelo y estropeando el parquet del mismo.

Pero como se advierte de la lectura de dicha demanda, si tenemos en cuenta que el conocimiento de la avería causante del destrozo se produjo en fecha [FECHA] y la demanda no se presenta hasta el [FECHA], resulta evidente que la acción que se ejercita de contrario ha prescrito.

A este respecto, hemos de hacer alusión a que la parte actora sólo menciona supuestas reclamaciones verbales a mi mandante, reclamaciones que esta parte niega, y no acredita el haber interrumpido la prescripción por ningún medio de forma, por lo que no habiendo sido ejercitada acción ante los tribunales antes del transcurso de un año a partir de la producción del hipotético daño y no habiendo formulado reclamación extrajudicial, ni existiendo acto o documento alguno por el que esta parte haya reconocido deuda de ninguna clase, es evidente que la acción se encuentra prescrita.

A fin de acreditar lo expuesto, y sin perjuicio de la prueba que en su momento se practique, se aportan los documentos números [COMPLETAR] a [COMPLETAR].

FUNDAMENTOS JURIDICOS

PRIMERO.- La acción ejercitada debe entenderse prescrita, de conformidad con lo establecido en el art. 1968.2.º CCiv, que establece el plazo prescriptivo de un año desde la ocurrencia del hecho, para todas aquellas obligaciones derivadas de la culpa o negligencia de que trata el art. 1902.

Efectivamente, se está ejercitando de contrario la acción de responsabilidad extracontractual del art. 1902 CCiv, acción para la que el art. 1968.2.º establece un plazo de prescripción de un año.

Pues bien, si tenemos en cuenta que a tenor de la propia documentación aportada la avería causante del destrozo se produjo en fecha [FECHA], que el actor tuvo conocimiento del hecho justo al día siguiente de producirse y la demanda no se presenta hasta el [FECHA], es evidente que ha transcurrido en exceso el plazo de un año a que hace referencia el art. 1968 CCiv para considerar la acción prescrita, no habiéndose acreditado, al amparo de lo dispuesto en el art. 1973 CCiv, la interrupción de la prescripción por ningún medio, por lo que resulta evidente que la acción se encuentra prescrita

SEGUNDO.- De estimarse la prescripción alegada corresponde la imposición de costas a la demandante en virtud de lo previsto en el art. 394 LEC.

En cuanto al fondo de la cuestión, para el supuesto de no estimarse la prescripción alegada, esta parte se opone a la demanda formulada con base en los siguientes

HECHOS

Esta parte niega los hechos alegados en la demanda, excepto los que expresamente se admitan en el presente escrito.

PRIMERO.- De conformidad con el hecho primero de contrario.

SEGUNDO.- De conformidad con el hecho segundo de contrario.

TERCERO.- Se niega expresamente el correlativo de la demanda. Por el contrario [COMPLETAR].

Se aporta como DOCUMENTO NÚMERO [Nº DE DOCUMENTO].

FUNDAMENTOS DE DERECHO

I.- Se aceptan los fundamentos jurídico-procesales de la demanda reiterando la excepción planteada al inicio de este escrito.

II.- No pueden aceptarse los fundamentos de fondo de la demandante, toda vez que [COMPLETAR].

III.- Por las razones expuestas que determinan la desestimación de la pretensión de la actora, deben imponerse las costas a la demandante, de conformidad con el art. 394 LEC.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que, teniendo por presentado este escrito, tenga por contestada la demanda y previos los trámites legales, se dicte sentencia declarando prescrita la acción ejercitada, y subsidiariamente desestimando íntegramente los pedimentos de la demanda y, en ambos casos, con expresa imposición de costas a la parte actora.

Es justicia debe hacerse en [LUGAR], a [FECHA].

Firma del Abogado	Firma del Procurador/a

========================================================================
