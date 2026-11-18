---
name: contestacion-oponiendo-litispendencia-527
description: "Redacta el escrito «Contestación oponiendo litispendencia» (formulario 527 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación oponiendo litispendencia

> Formulario 0527 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (8 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] Nº
- [ ] AÑO
- [ ] FECHA (2 veces)
- [ ] NÚMERO
- [ ] LUGAR
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…de los Tribunales y de la mercantil»; «…, con despacho profesional en»; «…, que se aportan como DOCUMENTOS NÚMEROS»; «…y»; «…relativo de la demanda. Por el contrario»; «… de fondo de la demandante, toda vez que»

## Elecciones que hay que hacer

- Procurador/a / Procurador/a a
- el Letrado / la Letrada

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 421.1 LEC
- art. 394 LEC
- art. 421 LEC

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

### Formulario 0527 · Contestación oponiendo litispendencia

- Año del modelo: 2016
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 2 desplegables convertidos en elección en blanco; 21 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Contestación a demanda de juicio ordinario alegando excepción procesal de litispendencia.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], [ELEGIR: Procurador/a / Procurador/a a] de los Tribunales y de la mercantil [COMPLETAR] según acredito mediante escritura de poder inscrito en el Registro Electrónico de Apoderamientos Judiciales, a cuya justificación aporto certificación de dicho Registro como documento nº [Nº DE DOCUMENTO], dirigida por [ELEGIR: el Letrado / la Letrada] abajo firmante D./Dña. [NOMBRE Y APELLIDOS], con despacho profesional en [COMPLETAR], ante el Tribunal comparezco y como mejor proceda en Derecho (1) DIGO:

Que en nombre de mi mandante comparezco y contesto a la demanda de Juicio Declarativo Ordinario sobre otorgamiento de escritura pública, interpuesta por D./Dña. [NOMBRE Y APELLIDOS], quien demanda en beneficio de la comunidad hereditaria de D./Dña. [NOMBRE Y APELLIDOS], seguida en ese Tribunal con el número [Nº]/[AÑO].

Con carácter previo esta parte opone la EXCEPCION PROCESAL DE LITISPENDENCIA, del art. 416.1.2.ª LEC, con fundamento en los siguientes:

HECHOS

ÚNICO.-

En fecha [FECHA], D./Dña. [NOMBRE Y APELLIDOS] presentó demanda sobre otorgamiento de escritura pública contra mi mandante que fue repartida al Tribunal de Instancia, plaza n.º [NÚMERO], de esta [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] ciudad donde, admitida a trámite, se encuentra en fase de periodo probatorio, conforme se acredita mediante testimonio de la mencionada demanda y certificación librada por el Letrado de la Administración de Justicia del mencionado Tribunal, que se aportan como DOCUMENTOS NÚMEROS [COMPLETAR] y [COMPLETAR].

Como se advierte de la lectura de dicha demanda, el demandante es hermano de la ahora demandante, quien reclama a mi representada el cumplimiento de la misma obligación que ahora se reclama, con fundamento en los mismos hechos ahora alegados. Aunque D./Dña. [NOMBRE Y APELLIDOS] comparece personalmente a diferencia de D./Dña. [NOMBRE Y APELLIDOS], que lo hace en beneficio de la comunidad hereditaria de D./Dña. [NOMBRE Y APELLIDOS], es fácil advertir que la resolución que recaiga en aquel procedimiento beneficiará o perjudicará a dicha comunidad hereditaria.

FUNDAMENTOS JURIDICOS

PRIMERO.- Se dan en el presente caso las tres identidades que doctrina y jurisprudencia vienen exigiendo para apreciar la existencia de litispendencia y que son identidad de sujetos, de objeto y de causa o razón de pedir. Por lo que procede su estimación al amparo de lo previsto en el art. 421.1 LEC, que determina el sobreseimiento del proceso.

SEGUNDO.- De estimarse la presente excepción corresponde la imposición de costas a la demandante en virtud de lo previsto en el art. 394 LEC.

En cuanto al fondo de la cuestión, para el supuesto de no estimarse la cuestión procesal alegada, esta parte se opone a la demanda formulada con base en los siguientes

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

que, teniendo por presentado este escrito, tenga por contestada la demanda y previos los trámites legales, se estime la excepción planteada dictando auto que acuerde el sobreseimiento del proceso por la concurrencia de litispendencia, o, en su caso, se dicte sentencia desestimatoria de la pretensión de la demanda, con expresa imposición de costas, en todo caso, a la demandante.

Es justicia debe hacerse en [LUGAR], a [FECHA].

Firma del Abogado	Firma del Procurador/a

NOTAS DEL FORMULARIO

(1) La litispendencia, en un sentido amplio, es la situación procesal que se produce por la existencia de un segundo proceso con igual contenido al de otro ya en curso que impone la exclusión del promovido en segundo lugar.

Esta exclusión, que puede tener lugar de oficio o a instancia de parte, constituye uno de los efectos procesales de aquel estado, que se conoce con la misma denominación, y se regula en el art. 421 LEC.

Si tiene lugar a instancia de parte, aunque es posible presentar un escrito alegando exclusivamente la excepción de litispendencia, lo habitual será en el escrito de contestación a la demanda, planteando con carácter previo la excepción, como cualquier otra más que impide la válida prosecución y termino del proceso.

La excepción de litispendencia trata de evitar que sobre una misma controversia, sometida judicialmente con anterioridad, se produzca otro litigio posterior con posibilidad de establecer resoluciones judiciales que resulten contradictorias, conforme reiterada y conocida doctrina jurisprudencial, actuando como institución jurídica preventiva y de tutela de la cosa juzgada.

En este sentido, la litispendencia no es sino un correlato de la cosa juzgada, variando únicamente en cuanto al alcance cronológico de sus efectos, pues mientras la cosa juzgada excluye la decisión sobre un proceso ulterior al que ya ha sido resuelto por sentencia firme, la litispendencia produce igual efecto mientras el proceso no está finalizado por sentencia o la misma no ha ganado firmeza, pero su acogimiento requiere las mismas identidades subjetiva, objetiva y causal de las acciones que se ejercitan en distintos procesos, exigiéndose que, sin variación alguna se dé la identidad de ambos procesos en cuanto a los sujetos, a las cosas en litigio y a la causa de pedir.

========================================================================
