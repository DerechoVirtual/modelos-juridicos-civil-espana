---
name: aprobacion-judicial-particion-hecha-defensor-judicial-144
description: "Redacta el escrito «Aprobación judicial de la partición hecha por un defensor judicial» (formulario 144 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Aprobación judicial de la partición hecha por un defensor judicial

> Formulario 0144 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

- [ ] SEDE (3 veces)
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] FECHA (8 veces)
- [ ] NÚMERO
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] IMPORTE
- [ ] Otros 16 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, y bajo la dirección Letrada de Don»; «…numeración del juzgado de procedencia).]»; «… PARTICIÓN DE LA HERENCIA DEL CAUSANTE D»; «…otorgada ante el Notario D»; «…numeración del juzgado de procedencia).]»; «…en la herencia. (acompaño como documento»; «…numeración del juzgado de procedencia).]»; «…ticionales de la herencia del causante D»; «…s dos hermanos (acompaño como documentos»; «…, ante el Notario D»; «…en el expediente, son los coherederos: D»; «…, y D»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (5)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 1060 del Código Civil
- art. 1061 del CC
- art. 14.2 LJV
- art. 287.5 del CC
- arts. 93 a 95 de la LJV
- art. 93 y 94 de la LJV
- art. 93.2.b) y 94.2 de la LJV
- art. 93.1 de la LJV

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

### Formulario 0144 · Aprobación judicial de la partición hecha por un defensor judicial

- Año del modelo: 2021
- Revisión 17-11-2026: 3 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 39 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D/Dª [NOMBRE Y APELLIDOS], Procurador de los Tribunales y de D/Dª [NOMBRE Y APELLIDOS], según acredito por apoderamiento apud-acta que acompaño, quien actúa en su condición de defensor judicial de la persona con discapacidad D/Dª [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], y bajo la dirección Letrada de Don [COMPLETAR], ante la Sección Civil del Tribunal de Instancia de [NOTA DE REVISIÓN: Un solo TI por partido judicial (art. 84.1 LOPJ): sobra «de los de». Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] que por turno de reparto corresponda comparezco y, como mejor proceda en Derecho, DIGO:

Que mediante el presente escrito promueve expediente de jurisdicción voluntaria para la APROBACIÓN JUDICIAL DE LA PARTICIÓN DE LA HERENCIA DEL CAUSANTE D [COMPLETAR] del que es heredera la persona con discapacidad, realizada en escritura pública de fecha [FECHA] otorgada ante el Notario D [COMPLETAR], de acuerdo con lo establecido en el art. 93 y siguientes de la Ley de Jurisdicción Voluntaria, en concordancia con lo establecido en el art. 1060 del Código Civil, en base a los siguientes

HECHOS

PRIMERO.- El solicitante es defensor judicial de D/Dª [NOMBRE Y APELLIDOS], el cual fue designado por decreto de fecha [FECHA] dictado por el Letrado de la Administración de Justicia de la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], para intervenir en la aceptación y partición de la herencia del causante D, como medida de apoyo en el ejercicio de su capacidad, al apreciarse conflicto de intereses con el curador, quien es hermano y coheredero en la herencia.

(acompaño como documento [COMPLETAR] sentencia dictada en proceso de provisión de medidas de apoyo de fecha [FECHA], testimonio del decreto de fecha [FECHA] de nombramiento de defensor judicial y certificados del Registro Civil).

SEGUNDO.- La herencia fue aceptada a beneficio de inventario por el solicitante (o la aceptación pura de la herencia se autorizó por auto de la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO], de fecha [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], que se acompaña por testimonio), tal como consta en la escritura particional.

El solicitante intervino como defensor judicial en las operaciones particionales de la herencia del causante D [COMPLETAR], hermano de la persona con discapacidad, fallecido en fecha [FECHA], del cual había sido instituido heredero por vía testamentaria la persona con discapacidad por partes iguales con sus otros dos hermanos (acompaño como documentos [COMPLETAR] certificado de defunción y copia del testamento).

En fecha [FECHA], ante el Notario D [COMPLETAR] se realizaron las operaciones particionales de adjudicación de los bienes y derechos que le correspondía a la persona con discapacidad procedentes de la herencia de su hermano junto sus otros dos hermanos. En nombre y representación de la persona con discapacidad actuó el solicitante en su condición de defensor judicial, adjudicándose previa aceptación en pago de su haber hereditario el 33,33 % del pleno dominio e indiviso de una finca urbana y una rústica que componían la herencia, así como la cantidad de 30.000 euros equivalente a la tercera parte del dinero y bienes fungibles que componían la herencia del causante (acompaño como documento número [Nº DE DOCUMENTO] escritura de partición de la herencia).

TERCERO.- Tal como ha quedado expuesto, la partición se ajusta a lo dispuesto en el art. 1061 del CC, puesto que se respeta escrupulosamente la igualdad de los lotes adjudicados a cada uno de los coherederos, siendo que el mantener en indiviso las dos fincas adjudicadas se debe a que es de interés de todos los coherederos proceder a su venta posterior para repartirse el dinero que se obtenga, siendo que no era posible su división y no existía interés en la adquisición de los inmuebles por ninguno de los coherederos, constando las características y valoración de los inmuebles en el informe pericial que se acompaña como documento número [Nº DE DOCUMENTO] y que está referenciado en la escritura de partición.

Toda la actuación del solicitante se hizo de acuerdo a la voluntad y preferencias de la persona que precisa el apoyo, tal como se constatará en la audiencia, resultando conveniente a sus intereses por todo lo expuesto.

CUARTO.- A los efectos del art. 14.2 LJV, debo hacer constar que las personas que pueden estar interesadas en el expediente, son los coherederos: D [COMPLETAR], hermano y curador con quien se apreció el conflicto de intereses que determinó el nombramiento, con domicilio en [LOCALIDAD], y D [COMPLETAR], hermano, con domicilio en

QUINTO.- (únicamente para el caso de aceptación pura de la herencia sin haber solicitado antes autorización judicial…) La aceptación y partición de la herencia se realizó en el mismo acto, de manera que no se instó la autorización judicial para aceptar la herencia pura y simplemente por error, pues no se tuvo en cuenta que el art. 287.5 del CC establece la necesidad de autorización para aceptar sin beneficio de inventario, en lo cual no se reparó dada la saneada situación económica del causante y la inexistencia de cargas hereditarias.

El causante D [COMPLETAR] tenía una situación económica totalmente saneada, con un patrimonio valorado en [IMPORTE] euros, tal como se acredita del inventario notarial y sin que exista pasivo alguno, por lo que la aceptación de la herencia pura y simple no causa perjuicio alguno a la persona con discapacidad, por lo que se está en el caso de solicitar que se autorice en este mismo expediente la aceptación, convalidando de esta forma la aceptación realizada en la escritura particional por razones de economía procesal y por ser de interés de la persona que precisa el apoyo, puesto que la situación del causante era totalmente saneada, tal como se desprende del inventario acompañado, y no hay ningún tipo de carga en la herencia.

El procedimiento para la autorización es el mismo de los arts. 93 a 95 de la LJV y su dilación por este error, perjudica a la persona que precisa el apoyo, quien es totalmente ajeno a este defecto, en tanto que se dilatan los trámites y no puede inscribirse la escritura en el Registro de la Propiedad hasta tanto no se legalice la partición, solicitando a este efecto que sea citado el Ministerio Fiscal para que intervenga en el expediente.

Subsidiariamente, en caso de que el Tribunal estime que debe iniciarse otro expediente para su acumulación o para la previa autorización judicial de aceptación, se solicita que se nos conceda un plazo de subsanación para la presentación en forma de solicitud o autorización judicial para aceptar la herencia, tal como se solicita por medio de otrosí (se trasladarían las pretensiones al suplico y al otrosí).

FUNDAMENTOS DE DERECHO

PRIMERO.- COMPETENCIA. Son competentes los Tribunales de Instancia de esta ciudad, por ser el lugar del último domicilio del causante conforme a lo dispuesto en el art. 94.1 de la Ley de Jurisdicción Voluntaria.

SEGUNDO.- PROCEDIMIENTO El procedimiento a seguir en el presente supuesto es el de jurisdicción voluntaria, regulado en el art. 93 y 94 de la LJV.

TERCERO.- LEGITIMACIÓN. Mi representado está legitimado en su condición de defensor judicial conforme a lo dispuesto en el art. 93.2.b) y 94.2 de la LJV compareciendo con representación y asistencia técnica al ser la cuantía del haber hereditario superior a 6.000 euros.

CUARTO.- FUNDAMENTOS DE FONDO. El art. 1060 del Código Civil establece, en su último párrafo, que “la partición realizada por el defensor judicial designado para actuar en la partición en nombre de un menor o de una persona a cuyo favor se hayan establecido medidas de apoyo, necesitará la aprobación judicial, salvo que se hubiera dispuesto otra cosa al hacer el nombramiento”. En concordancia, el art. 93.1 de la LJV establece que se aplicarán las disposiciones de este Capítulo en todos los casos en que, conforme a la ley, la validez de la aceptación o repudiación de la herencia necesite autorización o aprobación judicial determina la procedencia de las pretensiones sostenidas en esta solicitud.

La aplicación de ambos preceptos, de acuerdo al principio de protección de la persona con discapacidad y de la voluntad expresada por la misma,

Por lo expuesto,

AL TRIBUNAL SUPLICO: Que tenga por presentado este escrito con los documentos que se acompañan, lo admita, y tenga por promovido expediente de jurisdicción voluntaria de extinción de poderes preventivos otorgados por D/Dª [NOMBRE Y APELLIDOS] en escritura de fecha [FECHA] a favor del apoderado D/Dª [NOMBRE Y APELLIDOS], y practicadas las diligencias oportunas con intervención del Ministerio Fiscal, y previos los demás trámites con arreglo a Derecho dicte resolución en la que se apruebe judicialmente la partición realizada por el solicitante en escritura de fecha [FECHA] en su condición defensor judicial de la persona que precisa el apoyo.

OTROSÍ PRIMERO DIGO que se acompaña en anexo relación de documentos e informe presentado, debidamente foliados y con índice electrónico, para su debida localización y consulta.

SUPLICO AL TRIBUNAL tenga hecha esta manifestación a los efectos oportunos y por aportados los documentos e informe pericial relacionados en el anexo.

OTROSÍ SEGUNDO DIGO que solicito que sea citado a la comparecencia la persona que precisa el apoyo a fin de ser oído, cuidando esta parte de su comparecencia el día y hora que se señale, así como la de los coherederos D [COMPLETAR] y D [COMPLETAR], de cuya comparecencia cuidará asimismo esta parte.

SUPLICO AL TRIBUNAL: Tenga por propuesta la audiencia de la persona que precisa el apoyo, así como los coherederos que se proponen como testigos para acreditar la certeza de los hechos expresados:

Es Justicia que insto en [COMPLETAR]

Firma de procurador y letrado.
