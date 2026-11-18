---
name: medidas-guarda-administracion-inadecuada-bienes-persona-149
description: "Redacta el escrito «Medidas por guarda o administración inadecuada de bienes de persona con discapacidad» (formulario 149 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Medidas por guarda o administración inadecuada de bienes de persona con discapacidad

> Formulario 0149 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (9 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] FECHA (4 veces)
- [ ] Nº DE DOCUMENTO
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…allecimiento de ambos. Mi representado D»; «…y»; «…oyo. Adjunto acompañamos como documentos»; «…la representación que, otorgada por Doña»; «…ados sean citados a la comparecencia. En»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 249 del Código Civil
- art. 249 del CC
- art. 87.1.b) de la LJV
- artículo 249 del CC

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

### Formulario 0149 · Medidas por guarda o administración inadecuada de bienes de persona con discapacidad

- Año del modelo: 2021
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 24 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dª [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre de D./Dª [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, ante el Tribunal comparezco y como mejor proceda en Derecho, DIGO:

Que mediante el presente escrito, al amparo del artículo 87 de la Ley de Jurisdicción Voluntaria y artículo 249 del Código Civil, promuevo expediente de jurisdicción voluntaria solicitando que se proceda a la adopción de MEDIDAS DE PROTECCIÓN urgentes respecto de la persona con discapacidad D/Dª [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], por inadecuado ejercicio de la administración de bienes por parte de su guardador D./Dª [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], en base a los siguientes

HECHOS

PRIMERO .- En fecha [FECHA], por testamento otorgado por los padres de la persona con discapacidad D/Dª [NOMBRE Y APELLIDOS], afecto desde su nacimiento de un retraso mental severo, se dispuso que su hermano D/Dª [NOMBRE Y APELLIDOS], se encargara de su cuidado y administración de sus bienes para el caso de fallecimiento de ambos.

Mi representado D [COMPLETAR] es hermano de ambos y fue designado como guardador en el mismo testamento, para el caso de imposibilidad o fallecimiento del inicialmente designado, lo cual le legitima para esta solicitud, según se expone seguidamente.

En fecha [FECHA] y [COMPLETAR], fallecieron los padres, aceptándose la herencia en fecha [FECHA] y pasando a desempeñar desde entonces el hermano D/Dª [NOMBRE Y APELLIDOS] la función de guarda sin que se formalizara ninguna medida judicial de apoyo.

Adjunto acompañamos como documentos [COMPLETAR], testamento de fecha [FECHA], aceptación de herencia y certificaciones del Registro Civil acreditativas de lo expuesto.

SEGUNDO .- El solicitante ha tenido conocimiento de que el guardador D/Dª [NOMBRE Y APELLIDOS] perdió hace aproximadamente unos seis meses su puesto de trabajo, como consecuencia de un despido disciplinario en la empresa en la que trabajaba. No obstante tal circunstancia, el guardador y su familia siguen manteniendo el mismo nivel de gastos, lo cual alarmó a mi representado, pues era conocedor que los padres habían dejado un depósito dinerario de cuantía muy elevada a favor del hermano con discapacidad, pues padecía la minusvalía desde su nacimiento y con el fin de cubrir sus futuras necesidades.

A la vista de ello, mi representado acudió a la entidad bancaria donde estaba constituido el depósito dinerario, habiendo podido constatar que en los últimos seis meses se han realizado disposiciones por importe de 35.000 euros, las cuales son totalmente excesivas para las necesidades de la persona con discapacidad, por lo que existen indicios ciertos de que se está aplicando el dinero a cubrir las necesidades y gastos personales del curador y su familia, en grave perjuicio de la persona con discapacidad.

Acompaño como documentos número [Nº DE DOCUMENTO] extracto bancario del depósito y cuentas de la persona con discapacidad, a las que tiene acceso mi representado al figurar como autorizado en las mismas.

TERCERO.- La situación está poniendo al hermano de mi representado en grave riesgo, pues está disminuyendo de forma considerable su patrimonio en beneficio del curador, por lo que, al amparo del art. 249 del CC, se insta por medio del presente expediente que se nombre provisionalmente a mi representado como administrador de los bienes de su hermano con discapacidad, privando de dichas facultades a su otro hermano guardador, como medida de protección de carácter urgente derivada del ejercicio inadecuado de la función de guarda por parte de éste.

A los anteriores hechos les son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

PRIMERO .- COMPETENCIA. Son competentes las secciones civiles de los tribunales de instancia de esta ciudad, por ser la del domicilio de la persona con discapacidad, conforme a lo dispuesto en el art. 87.2 de la Ley de Jurisdicción Voluntaria.

SEGUNDO.- PROCEDIMIENTO. Debe seguirse el procedimiento de jurisdicción voluntaria regulado en los artículos 87 y siguientes de la Ley de Jurisdicción Voluntaria, estableciendo el art. 87.1.b) de la LJV que el procedimiento se seguirá para la adopción de las medidas previstas en el artículo 249, último párrafo, del Código Civil en relación con las personas con discapacidad.

TERCERO.- LEGITIMACIÓN. Esta parte está legitimada conforme a lo dispuesto en el 87.3 de la Ley de Jurisdicción Voluntaria.

CUARTO.- FUNDAMENTOS DE FONDO. El artículo 249 del CC establece que las medidas de apoyo a las personas mayores de edad o menores emancipadas que las precisen para el adecuado ejercicio de su capacidad jurídica tendrán por finalidad permitir el desarrollo pleno de su personalidad y su desenvolvimiento jurídico en condiciones de igualdad, debiendo estar inspiradas en el respeto a la dignidad de la persona y en la tutela de sus derechos fundamentales; en su último párrafo, el art. 249 del CC habilita a la autoridad judicial a la adopción de medidas de protección en defecto o por insuficiencia de estas medidas de naturaleza voluntaria, y a falta de guarda de hecho que suponga apoyo suficiente, como sucede en este caso conforme a lo expuesto, revistiendo carácter urgente.

Por lo expuesto:

SUPLICO AL TRIBUNAL tenga por presentado este escrito, me tenga por parte en la representación que, otorgada por Doña [COMPLETAR], asumo, entendiéndose conmigo las sucesivas actuaciones, por promovido y se incoe el oportuno expediente de jurisdicción voluntaria, y una vez oído la persona con discapacidad, los interesados y el Ministerio fiscal, y practicadas cuantas actuaciones se consideren necesarias, se dicte en su día auto por el que se acuerde, como medida de protección de la persona con discapacidad, la designación de mi representado para encargarse del apoyo de la persona con discapacidad, singularmente todo lo relativo a la administración de sus bienes.

OTROSÍ PRIMERO DIGO que se acompaña en anexo relación de documentos e informes presentados, debidamente foliados y con índice electrónico, para su debida localización y consulta.

SUPLICO AL TRIBUNAL tenga hecha esta manifestación a los efectos oportunos y por aportados los documentos e informe pericial relacionados en el anexo.

OTROSÍ SEGUNDO DIGO que, en este expediente, además de la persona con discapacidad y el guardador con los domicilios ya mencionados, pueden estar interesadas las siguientes personas:

-D/Dª [NOMBRE Y APELLIDOS], hermano de los indicados y de mi representado, con domicilio en [LOCALIDAD].

SUPLICO AL TRIBUNAL que tenga por realizada la anterior manifestación a los efectos de que los interesados sean citados a la comparecencia.

En [COMPLETAR]

Firma del Abogado y Procurador.
