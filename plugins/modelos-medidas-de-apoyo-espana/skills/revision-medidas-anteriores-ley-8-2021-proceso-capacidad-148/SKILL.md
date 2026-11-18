---
name: revision-medidas-anteriores-ley-8-2021-proceso-capacidad-148
description: "Redacta el escrito «Revisión de medidas anteriores a la Ley 8/2021 en proceso de capacidad» (formulario 148 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Revisión de medidas anteriores a la Ley 8/2021 en proceso de capacidad

> Formulario 0148 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Igual que el 145: DT 5.ª Ley 8/2021 vigente en la redacción de la LO 5/2024 (revisión de oficio en un máximo de seis años).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NÚMERO (2 veces)
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] FECHA (2 veces)
- [ ] Nº DE DOCUMENTO
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…rado de la Administración de Justicia de»; «…tución de tutela, designándose tutor a D»; «…en el Registro Civil correspondiente. En»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 287 del CC
- art. 249 del CC
- Ley 8/2021

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

### Formulario 0148 · Revisión de medidas anteriores a la Ley 8/2021 en proceso de capacidad

- Año del modelo: 2021
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 17 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)
- Avisos de la revisión: Igual que el 145: DT 5.ª Ley 8/2021 vigente en la redacción de la LO 5/2024 (revisión de oficio en un máximo de seis años).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Proceso de capacidad número [NÚMERO]

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D/Dª [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en representación de D/Dª [NOMBRE Y APELLIDOS], según se acredita mediante apoderamiento apud acta que otorgado ante el Letrado de la Administración de Justicia de [COMPLETAR] (o en virtud de copia notarial digitalizada de poder), bajo la dirección letrada de D/Dª [NOMBRE Y APELLIDOS], Abogado del Iltre. Colegio de [LOCALIDAD], por medio de la presente ante el Tribunal comparezco, y como mejor proceda en Derecho, DIGO:

Que en la indicada representación, al amparo de la disposición transitoria quinta de la Ley 8/2021, de 2 de junio, solicito la REVISIÓN de las medidas adoptadas respecto de mi representado D/Dª [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], en proceso de capacidad número [NÚMERO] seguido ante el Tribunal al que me dirijo, todo ello en base a los siguientes, la cual baso en los siguientes

HECHOS

PRIMERO.- En virtud de sentencia firme de fecha [FECHA] dictada en los autos seguidos ante ese Tribunal se declaró que mi representado D/Dª [NOMBRE Y APELLIDOS] padecía un enolismo de larga evolución, señalándose que la dependencia alcohólica había derivado en una psicosis paranoide toxicofílica declarándose la incapacidad parcial del mismo y la constitución de tutela, designándose tutor a D [COMPLETAR].

SEGUNDO.- La regulación de las medidas de apoyo a personas con discapacidad por Ley 8/2021 ha suprimido la institución de la tutela, a la vez que refuerza la autonomía de la persona con discapacidad, de manera que el régimen de apoyo formal debe ser proporcionado a las necesidades de la persona que los precise, respetando siempre la máxima autonomía de ésta en el ejercicio de su capacidad jurídica y atendiendo en todo caso a su voluntad, deseos y preferencias.

Esta nueva regulación de las medidas de apoyo y la mejora significativa de la situación de mi representado determinan que se solicite la revisión de las mismas a fin de que se dejen sin efecto las medidas o, subsidiariamente, se constituya la curatela limitada a la asistencia del curador en los actos de disposición patrimonial referidos en el art. 287 del CC.

TERCERO.- Esta revisión se funda en que, en el tiempo transcurrido desde la constitución del órgano tutelar, mi representado ingresó en el centro de desintoxicación homologado dependiente del Ministerio de Sanidad al objeto de iniciar el correspondiente tratamiento de desintoxicación. Dicho tratamiento que se ha prolongado durante año y medio ha sido en régimen cerrado con supervisión médica y psiquiátrica.

Mi representado ha seguido la totalidad del tratamiento con gran éxito encontrándose a fecha de la interposición de la presente solicitud totalmente desintoxicado y lo cual ha disminuido significativamente la intensidad de la psicosis que padecía, que ha sido diagnosticada como muy leve, según consta informe expedido por el informe del psiquiatra adscrito al centro de desintoxicación que se acompaña como documento número [Nº DE DOCUMENTO].

Por ello, dada la situación actual de mi representado, y los principios de necesidad y proporcionalidad que informan la nueva regulación, expresados en el art. 249 del CC, con el fin de preservar al máximo que la persona afectada por una discapacidad pueda ejercitar por sí sus derechos, que pueda desarrollar al máximo sus posibilidades de autogobierno, esta parte solicita que se dejen sin efecto las medidas de apoyo o, subsidiariamente, se limiten estrictamente a la asistencia en los actos de disposición patrimonial.

A los anteriores hechos le son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

PRIMERO.- Revisión de las medidas adoptadas: La disposición transitoria quinta de la Ley 8/2021 establece: “las personas con capacidad modificada judicialmente, los declarados pródigos, los progenitores que ostenten la patria potestad prorrogada o rehabilitada, los tutores, los curadores, los defensores judiciales y los apoderados preventivos podrán solicitar en cualquier momento de la autoridad judicial la revisión de las medidas que se hubiesen establecido con anterioridad a la entrada en vigor de la presente Ley, para adaptarlas a esta. La revisión de las medidas deberá producirse en el plazo máximo de un año desde dicha solicitud”.

SEGUNDO.- Fundamentos de fondo. Los artículos 249 y siguientes del CC y en especial, el art. 249 que establece: “Las medidas de apoyo a las personas mayores de edad o menores emancipadas que las precisen para el adecuado ejercicio de su capacidad jurídica tendrán por finalidad permitir el desarrollo pleno de su personalidad y su desenvolvimiento jurídico en condiciones de igualdad. Estas medidas de apoyo deberán estar inspiradas en el respeto a la dignidad de la persona y en la tutela de sus derechos fundamentales. Las de origen legal o judicial solo procederán en defecto o insuficiencia de la voluntad de la persona de que se trate. Todas ellas deberán ajustarse a los principios de necesidad y

En su virtud

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos acompañados y sus copias; admita todo ello; y se tenga por solicitada la REVISIÓN de las medidas adoptadas en la sentencia de fecha [FECHA] dictada por ese Tribunal, procediéndose a extinguir la tutela constituida y dejando sin efecto las medidas de apoyo o, subsidiariamente, manteniendo únicamente la asistencia del curador para los actos de disposición patrimonial, inscribiendo la resolución en el Registro Civil correspondiente.

En [COMPLETAR]

(Firma de Abogado y Procurador)
