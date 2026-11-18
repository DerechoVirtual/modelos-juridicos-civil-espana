---
name: contestacion-demanda-indemnizacion-compensatoria-entre-629
description: "Redacta el escrito «Contestación a la demanda de indemnización compensatoria entre convivientes» (formulario 629 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a la demanda de indemnización compensatoria entre convivientes

> Formulario 0629 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD (2 veces)
- [ ] NÚMERO (3 veces)
- [ ] COLEGIO
- [ ] CALLE
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…te, que es funcionaria del Ministerio de»; «…, con la categoría»; «…según resulta de la regulación de la Ley»

## Elecciones que hay que hacer

- Procurador/a / Procurador/a a
- colegiado / colegiada

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 394.1 LEC

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

### Formulario 0629 · Contestación a la demanda de indemnización compensatoria entre convivientes

- Año del modelo: 2016
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 2 desplegables convertidos en elección en blanco; 17 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Contestación a demanda de juicio ordinario dirigida al Tribunal de Instancia, sobre reclamación de indemnización compensatoria entre convivientes.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], [ELEGIR: Procurador/a / Procurador/a a] de los Tribunales, que actúa en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], provisto de D.N.I. n.º [NÚMERO], conforme al poder para pleitos que se acepta y acompaña por copia auténtica, con ruego de su devolución, previo testimonio en autos, por necesitarlo a otros usos, y asistido del Letrado en ejercicio D./Dña. [NOMBRE Y APELLIDOS], [ELEGIR: colegiado / colegiada] n.º [NÚMERO] del Iltre. Colegio de Abogados de [COLEGIO], con despacho abierto en [LOCALIDAD], calle [CALLE], n.º [NÚMERO], ante el Tribunal comparezco, en sus autos de juicio ordinario n.º [Nº DE PROCEDIMIENTO]/[AÑO], y como mejor proceda en Derecho, DIGO:

Que en los meritados autos que contra mi principal se siguen por D./Dña. [NOMBRE Y APELLIDOS] en reclamación de efectos económicos derivados de la extinción de la relación estable de pareja de hecho, dentro del término conferido, me persono y contesto a la demanda, resistiendo a la misma, en base a los siguientes:

HECHOS

Con carácter previo esta parte se opone a todos cuantos hechos aducidos en la demanda a la que se contesta no sean expresamente reconocidos en las siguientes alegaciones.

PRIMERO.- Nada que objetar en cuanto a la convivencia de los litigantes durante el período de tiempo referenciado.

SEGUNDO.- Incierto el correlativo en cuanto a la existencia de una convivencia «more uxorio» entre la demandante y el demandado.

Lo cierto es que en ningún momento ha existido una relación estable de pareja de hecho entre los litigantes.

En el caso de la demandante y el demandado, si bien convivían en el mismo domicilio, lo era por razones esencialmente económicas al compartir gastos de alquiler de la vivienda; en ningún momento han tenido una relación afectiva análoga a la conyugal, de tal manera que negamos rotundamente que esta relación pueda ser conceptuada como de pareja de hecho.

Pero aun aceptando la existencia de una relación afectiva entre los litigantes, lo cierto es que no se ha producido la convivencia marital durante el período de tiempo que exige la normativa autonómica relativa a parejas estables no casadas, ni se ha manifestado la voluntad de constituirla mediante ningún pacto.

Tampoco se ha inscrito en ningún momento la relación en el Registro prevenido al efecto, siendo que la citada normativa exige la inscripción en el Registro como requisito constitutivo de la pareja de hecho.

TERCERO.- En disconformidad con el hecho correlativo de la demanda en los términos expuestos de contrario.

Para el improbable supuesto que se estimara que la relación de mi mandante con la actora constituye una unión estable de hecho, contradecimos abiertamente que se haya producido la situación que se expone de desequilibrio patrimonial y enriquecimiento injusto de mi mandante, puesto que la demandante, que es funcionaria del Ministerio de [COMPLETAR], con la categoría [COMPLETAR], no ha visto disminuidas sus retribuciones en razón a la convivencia, y si mi representado ha visto aumentado su patrimonio de una manera moderada es debido al acierto en el desenvolvimiento de su actividad profesional.

Negamos asimismo que la demandante se haya dedicado al cuidado del hogar familiar, ni desde luego al cuidado de los hijos de mi representado, ya que éstos son mayores de edad y siempre han sido atendidos por su progenitor, y que todas las tareas de la vivienda han sido compartidas, como se acreditará oportunamente en la fase probatoria de este proceso, de lo que resulta la improcedencia de la reclamación formulada de contrario.

FUNDAMENTOS DE DERECHO

I.- JURÍDICO-PROCESALES

Conforme con los aducidos por la actora sobre jurisdicción, competencia, legitimación "ad procesum", procedimiento aplicable y postulación.

Como se ha adelantado al exponer los hechos de esta contestación, esta parte, con carácter previo, alega por falta de legitimación "ad causam" al no existir pareja de hecho entre los litigantes, según resulta de la regulación de la Ley [COMPLETAR], concretamente de sus artículos

II.- JURÍDICO-MATERIALES

Asimismo, y en cuanto al fondo, nos oponemos a la pretensión indemnizatoria por falta de fundamento, al no darse los requisitos establecidos legalmente para que se fije ninguna indemnización o compensación económica, por cuanto la supuesta convivencia no ha generado ningún perjuicio económico a la demandante ni ha producido una situación de enriquecimiento injusto en mi mandante.

III.- COSTAS

Las costas del presente procedimiento deberán ser impuestas a la parte demandante, con arreglo al art. 394.1 LEC, que recoge el principio objetivo del vencimiento en la materia por lo que respecta a los juicios declarativos en su primera instancia.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito, con sus documentos, y copias de todo ello, se sirva admitirlo, y tenga por formulada CONTESTACIÓN A LA DEMANDA y, tras los trámites legales, dicte sentencia desestimatoria de la pretensión formulada de contrario, todo ello con expresa imposición de costas a la parte actora.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado	Firma del Procurador/a

========================================================================
