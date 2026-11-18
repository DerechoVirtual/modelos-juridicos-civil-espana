---
name: defensor-judicial-autorizacion-aceptar-adjudicar-126
description: "Redacta el escrito «Defensor judicial y autorización para aceptar y adjudicar una herencia» (formulario 126 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Defensor judicial y autorización para aceptar y adjudicar una herencia

> Formulario 0126 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

- Hechos sobre «sentencia de incapacitación» y «tutoras» de un mayor: por la DT 2.ª Ley 8/2021 (BOE-A-2021-9233) las tutoras ejercen conforme a las normas del curador representativo; conviene indicarlo y valorar instar la revisión de la DT 5.ª.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NÚMERO (3 veces)
- [ ] NOMBRE Y APELLIDOS (20 veces)
- [ ] FECHA (5 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] LOCALIDAD
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…reforma procesal de la LO 1/2025. TUTELA»; «…numeración del juzgado de procedencia).]»; «…n nombre y representación de Dª. y de Dª»; «…para pleitos otorgado ante el Notario de»; «…nas de la persona con discapacidad, a Dª»; «…y a Dª»; «…do testamento abierto ante el Notario de»; «…olo, y en el mismo legaba a su esposa Dª»; «…toras y hermanas, las precitadas Dª y Dª»; «…ridad a la incapacitación judicial de D.»; «…, se otorgó ante el notario de»; «…- Se nombre defensor judicial de D. a Dª»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (5)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 295 del Código Civil
- arts. 9.2, 21.1 y 22 de la LOPJ
- artículo 30.2 de la Ley 15/2015
- artículo 30 de la Ley 15/2015
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

### Formulario 0126 · Defensor judicial y autorización para aceptar y adjudicar una herencia

- Año del modelo: 2022
- Revisión 17-11-2026: 10 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 26 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 19 huecos del original que se habían perdido sin marca, marcados (FECHA, NOMBRE Y APELLIDOS)
- Avisos de la revisión: Hechos sobre «sentencia de incapacitación» y «tutoras» de un mayor: por la DT 2.ª Ley 8/2021 (BOE-A-2021-9233) las tutoras ejercen conforme a las normas del curador representativo; conviene indicarlo y valorar instar la revisión de la DT 5.ª.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

TUTELA [COMPLETAR] /2013

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA, PLAZA N.º [NÚMERO],

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

DE [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR]

Encabezamiento. Acción

[NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de Dª. y de Dª [COMPLETAR] actuando ambas en calidad de tutoras de su hermano D. representación que se acredita mediante el poder general para pleitos otorgado ante el Notario de [COMPLETAR] D.el día [FECHA] al número [NÚMERO] de su protocolo que se aporta como documento nº 1/ mediante apoderamiento apud acta otorgado ante el LAJ de este Tribunal, según consta en las actuaciones, ante el Tribunal con el mayor respeto y como mejor proceda D I G O:

Que a medio del presente escrito, en la representación enunciada y en virtud de lo dispuesto en el artículo 295 del Código Civil, en la nueva redacción dada por la Ley 8/2021 de 2 de junio, venimos a formular SOLICITUD DE NOMBRAMIENTO DE DEFENSOR JUDICIAL y DE AUTORIZACIÓN JUDICIAL PARA LA ACEPTACIÓN y ADJUDICACIÓN DE HERENCIA del causante D. [NOMBRE Y APELLIDOS] en nombre de la persona con discapacidad D. [NOMBRE Y APELLIDOS] (hijo del causante) [NOTA DE REVISIÓN: Aparece dos veces (encabezamiento y suplico). Fuente: Código Civil (BOE-A-1889-4763) art. 250, redacción Ley 8/2021 (BOE-A-2021-9233).] sobre la base de los siguientes

HECHOS

Primero.- Que con fecha [FECHA] este Tribunal dictó Sentencia por la que:

Se declaraba la discapacidad total de D. haciéndola extensiva a todos los actos patrimoniales de administración y disposición de sus bienes (..) debiendo ser asistido en todo caso de sus tutores legales.
Se designaba para el cargo de tutores legales a las hermanas de la persona con discapacidad, a Dª [COMPLETAR] y a Dª [COMPLETAR], nuestras representadas en este expediente, para que ejercieran el cargo de forma conjunta y compartida.

Aportamos dicha sentencia como documento nº [Nº DE DOCUMENTO].

Segundo.- Que el pasado [FECHA] falleció D. [NOMBRE Y APELLIDOS], padre tanto de la persona con discapacidad como de nuestras representadas.

D. había otorgado testamento abierto ante el Notario de [COMPLETAR] el día [FECHA] al número de su protocolo, y en el mismo legaba a su esposa Dª [COMPLETAR] el usufructo universal y vitalicio de toda su herencia, e instituía herederos universales a sus hijos

Como hemos mencionado anteriormente, la Sentencia de incapacitación recaída en el Procedimiento de Tutela nº [Nº DE PROCEDIMIENTO] inhabilita a D. [NOMBRE Y APELLIDOS] para partir herencias o dividir cosas comunes, actos para los que debe estar representado por sus tutoras y hermanas, las precitadas Dª y Dª [COMPLETAR], quienes ostentan su cargo en virtud del Auto de

Tercero.- Que con fecha [FECHA], es decir, con anterioridad a la incapacitación judicial de D. [COMPLETAR], se otorgó ante el notario de [COMPLETAR] D. [NOMBRE Y APELLIDOS], al número [NÚMERO] de su protocolo, escritura de aceptación parcial de la herencia del padre de nuestras representadas y de la persona con discapacidad, tal y como acreditamos con la escritura de aceptación parcial de la herencia de D. [NOMBRE Y APELLIDOS] que aportamos como documento nº [Nº DE DOCUMENTO].

Cuarto.- Que tal y como se ha expuesto, nuestras representadas ostentan el cargo de tutoras conjuntas de D. [NOMBRE Y APELLIDOS] y a la vez confluyen en la herencia del padre como herederas, por lo que existe un evidente conflicto de intereses entre el cargo de tutoras de un coheredero y el de herederas en la misma herencia.

Así pues, conforme a lo dispuesto en el artículo 295.2.º del Código Civil, [NOTA DE REVISIÓN: El conflicto de intereses es el ordinal 2.º del art. 295 CC; el 1.º es la imposibilidad de prestar apoyo. Fuente: Código Civil (BOE-A-1889-4763) art. 295, redacción Ley 8/2021 (BOE-A-2021-9233): 1.º imposibilidad de quien presta apoyo; 2.º conflicto de intereses; 4.º administración de bienes mientras se tramita la provisión de apoyos.] a medio del presente escrito solicitamos del Tribunal que se proceda al nombramiento de defensor judicial que represente a D. [NOMBRE Y APELLIDOS] en juicio y fuera de él en todo lo referente a la operaciones particionales del padre del tutelado D. [NOMBRE Y APELLIDOS], concretamente en las actuaciones de otorgamiento de escritura de aceptación y adjudicación parcial de la herencia, de escrituras de protocolización de acuerdos, de subsanación y/o complemento de otras escrituras particionales, de extinción de condominios, y gestiones tributarias y registrales, incluidas las inscripciones y cancelaciones de deuda, así como la consolidación de dominio por extinción de usufructo o por otras causas legales, y todo ello en relación con la herencia del causante y padre del tutelado D.. [NOMBRE Y APELLIDOS]

Que en virtud de lo dispuesto en el artículo 295 in finde del CC, esta parte propone como persona más idónea para ostentar dicho cargo a D./Dª [NOMBRE Y APELLIDOS], quien mantiene una estrecha relación de amistad y confianza con el tutelado así como comprende los intereses y voluntad del tutelado, ofrece suficientes garantías para velar por los intereses de dicha persona con discapacidad, y se compromete a aceptar el cargo y cumplirlo con lealtad, así como a rendir cuentas de su actuación.

Quinto.- Que esta parte ofrece información testifical sobre los extremos del presente escrito a las siguientes personas:

1.- Dª (familiar de la persona con discapacidad) mayor de edad, vecina de con domicilio en Calle.

2.- D. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD].

FUNDAMENTOS DE DERECHO

I.JURISDICCIÓN Y COMPETENCIA.- Es competente la jurisdicción civil, con arreglo a lo establecido en los arts. 9.2, 21.1 y 22 de la LOPJ, y 36 de la LEC.

Ex artículo 28.1 de la Ley 15/15, será competente para el conocimiento de este expediente el Letrado de la Administración de Justicia de la Sección Civil del Tribunal de Instancia del domicilio o, en su defecto, de la residencia del menor o persona con discapacidad o, en su caso, aquél correspondiente a la Sección Civil del Tribunal de Instancia que esté conociendo del asunto que exija el nombramiento de defensor judicial.

II.- CAPACIDAD.- Las partes ostentan la capacidad procesal necesaria conforme a lo establecido en los arts. 6 y ss. de la LEC.

III.- LEGITIMACIÓN.- Corresponde a nuestras representadas en tanto son tutoras de su hermano D. [NOMBRE Y APELLIDOS], y además ostentan la cualidad de herederas instituidas por su padre D.. [NOMBRE Y APELLIDOS]

IV.- REPRESENTACIÓN.- Conforme a lo dispuesto en el artículo 28.3 de la Ley de la Jurisdicción Voluntaria, modificada por la Ley 8/2021, aun no siendo preceptiva la intervención de abogado, esta parte acudirá asistida de letrado y representada por procurador.

V.- PROCEDIMIENTO.- La presente solicitud debe sustanciarse por las reglas contenidas en los arts. 30 y ss de la Ley 15/2015 en la nueva redacción dada por la Ley 8/2021.

El LAJ convocará a convocará a comparecencia al solicitante, a los interesados que consten como tales en el expediente, a quienes estime pertinente su presencia, al menor o persona con discapacidad si tuvieren suficiente madurez y, en todo caso, al menor si tuviere más de 12 años y al Ministerio Fiscal.

Ex artículo 30.2 de la Ley 15/2015, “e n la resolución en que se acceda a lo solicitado se nombrará defensor judicial a quien el Letrado de la Administración de Justicia estime más idóneo para el cargo, con determinación de las atribuciones que le confiera”.

VI.- ASUNTO DE FONDO.Nuestro Código Civil establece en su art. 295 que «Se nombrará un defensor judicial de las personas con discapacidad en los casos siguientes:

2.º Cuando exista conflicto de intereses entre la persona con discapacidad y la que haya de prestarle apoyo”.

Esta parte ha acompañado los documentos exigidos para acreditar la concurrencia en nuestras representadas de la doble cualidad de herederas del causante D. [NOMBRE Y APELLIDOS] y de tutoras del coheredero D. por lo que existe un claro conflicto de intereses que debe evitarse con la declaración del defensor judicial propuesto por esta parte como persona más idónea para ejercer dicho cargo que vele de manera imparcial por los intereses de la persona con discapacidad.

SUPLICO

Por lo cual,

AL TRIBUNAL SUPLICO tenga por presentado este escrito, su copia y los documentos que se acompañan. Tenga por formulada SOLICITUD DE NOMBRAMIENTO DE DEFENSOR JUDICIAL y DE AUTORIZACIÓN JUDICIAL PARA LA ACEPTACIÓN y ADJUDICACIÓN DE HERENCIA del causante D. [NOMBRE Y APELLIDOS] en nombre de la persona con discapacidad D. [NOMBRE Y APELLIDOS] (hijo del causante).

Cite a las partes y al Ministerio Fiscal a la comparecencia prevista en el artículo 30 de la Ley 15/2015, y tras los demás trámites que procedan, dicte Decreto por el que:

1º.- Se nombre defensor judicial de D. a Dª [COMPLETAR].

2º.- Se determine como atribuciones de su cargo las siguientes: actuaciones de otorgamiento de escritura de aceptación y adjudicación parcial de la herencia del padre de la persona con discapacidad D. [NOMBRE Y APELLIDOS], otorgamiento de escrituras de protocolización de acuerdos, de subsanación y/o complemento de otras escrituras particionales, de extinción de condominios, y gestiones tributarias y registrales, incluidas las inscripciones y cancelaciones de deuda, así como la consolidación de dominio por extinción de usufructo o por otras causas legales, y todo ello en relación con la herencia del causante y padre del tutelado D.. [NOMBRE Y APELLIDOS]

Y se expida testimonio del Decreto que así lo acuerde.

Es Justicia que pido en [COMPLETAR], a de 2022.

Ldo. Coleg. Procurador Coleg.
