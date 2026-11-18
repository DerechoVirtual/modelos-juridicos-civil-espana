---
name: contestacion-demanda-indignidad-rehabilitacion-tacita-329
description: "Redacta el escrito «Contestación a la demanda de indignidad con rehabilitación tácita o expresa del causante» (formulario 329 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a la demanda de indignidad con rehabilitación tácita o expresa del causante

> Formulario 0329 del plugin **Sucesiones** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Inmuebles** (referencia catastral, superficie, uso) → `consultar_catastro` (y `callejero_catastro` para localizar la dirección).

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
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] LOCALIDAD
- [ ] FECHA
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…ales, en nombre y representación de Dona»; «…sentado hacia la persona del finado, Don»; «… al haber atentado contra la vida de Don»; «… desestime la demanda presentada por Don»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 25 LEC
- arts. 23 y 31 LEC
- art. 757 CCiv
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

### Formulario 0329 · Contestación a la demanda de indignidad con rehabilitación tácita o expresa del causante

- Año del modelo: 2020
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 12 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Contestación a demanda de declaración de indignidad de heredero para suceder por la causa del art. 756.1º CCiv con fundamento en la rehabilitación del demandado por el causante.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de Dona [COMPLETAR], según acredito mediante copia de la escritura de poder que acompaño para su unión a los autos por copia testimoniada con devolución del original, y bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], con despacho profesional abierto en [LOCALIDAD], ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que mediante el presente escrito y dentro del término conferido, paso a contestar la demanda formulada de adverso, oponiéndome a la misma en base a los siguientes:

HECHOS

PRELIMINAR.- (1)

Esta parte niega los hechos alegados en la demanda, excepto los que expresamente se admitan en el presente escrito.

A estos hechos son de aplicación, los siguientes,

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA.

Conforme esta parte respecto a la competencia del Tribunal al que tengo el honor de dirigirme.

II.- PROCEDIMIENTO.

Nada que objetar respecto a la clase de procedimiento, el juicio declarativo ordinario que regulan los arts. 399 y ss. LEC, en razón a la pretensión deducida en la demanda.

III.- LEGITIMACIÓN ACTIVA Y PASIVA.

A los puros efectos formales, de acuerdo con la legitimación de la parte actora, a la hora de ejercitar una acción como la que aquí se plantea. Asimismo, se acepta, a los mismos efectos formales, la legitimación pasiva de mi cliente, y ello, sin perjuicio de oponernos de manera frontal a la demanda, y negar tajantemente los hechos aducidos en la demanda.

IV.- CAPACIDAD Y REPRESENTACIÓN.

Se asume la capacidad del demandante, para ser parte en este proceso, en cuanto se presume persona física mayor de edad sin discapacidad, en virtud de lo dispuesto en los arts. 6.1.1.º y 7.1 LEC, afirmándose la capacidad de mi patrocinado, igualmente persona física, conforme a los citados preceptos legales.

V.- POSTULACIÓN Y DEFENSA.

La presente contestación se presenta mediante Procurador de los Tribunales que encabeza este escrito, habilitado en la demarcación del Tribunal al que tengo el honor de dirigirme. Y ello con poder general para pleitos (art. 25 LEC), siendo redactado y firmado el presente escrito por abogado ejerciente colegiado que dirige el asunto y se identifica en el encabezamiento, según resulta preceptivo conforme a los arts. 23 y 31 LEC.

VI.- FUNDAMENTO LEGAL DE LA OPOSICIÓN.

Se alega la rehabilitación del indigno por el causante, en aras al principio de la soberanía de la voluntad del causante, uno de los principios básicos de la sucesión mortis causa. La indignidad no es como una sanción penal que se persigue y sanciona de oficio, sino una sanción civil que el causante, como víctima del acto causa de indignidad, puede evitar mediante la rehabilitación del indigno, que puede hacerlo expresa o tácitamente.

La rehabilitación tácita consiste en que el testador, que conocía la causa de indignidad al tiempo de hacer testamento, en él instituye al indigno, heredero o legatario, con lo que éste queda rehabilitado.

La rehabilitación expresa la prevé el segundo inciso del art. 757 CCiv: "las causas de indignidad remitiere en documento público", tanto si las conoce después de haber otorgado testamento (único caso al que se refiere el art. 757) como si las conocía antes o incluso si no hace testamento; esta rehabilitación se debe hacer en documento público o, también, en testamento, sea éste hecho en documento público (abierto o cerrado) o privado (comunes extraordinarios o especiales o el ológrafo) que, al protocolizarse posteriormente, deviene público.

En este caso, en fecha [FECHA], es decir, con posterioridad al ataque de mi representado hacia la persona del finado, Don [COMPLETAR], este último emitió una declaración notarial (documento nº [Nº DE DOCUMENTO]) en la cual manifestaba su intención de no modificar ni revocar el testamento otorgado con anterioridad para no perjudicar a mi mandante, y ello a sabiendas de lo inadmisible de la acción atentatoria contra su vida.

Y para el caso improbable de que se cuestione la intención y voluntad rehabilitadora por parte del causante, a través de la declaración de anterior referencia, conviene apuntar, a mayor abundamiento, que no existe duda alguna de que el testador conocía la sentencia por la que se condenaba a mi mandante al haber atentado contra la vida de Don [COMPLETAR] y, a pesar de ello, otorgó el testamento que designa expresamente a mi representado como heredero, perdonando en consecuencia la indignidad del hijo y habiendo sido rehabilitado, cuanto menos, tácitamente por el causante.

Se acreditará que el causante conocía de la existencia de la sentencia condenatoria y que pese a ello no modificó su testamento en el momento procesal oportuno.

El efecto de la rehabilitación es que la indignidad, fruto de una causa legal, deja de surtir efecto, como expresa el art. 757 CCiv y, en consecuencia, el ex-indigno recibe la delación hereditaria y puede adquirir la herencia o el legado a él deferida.

Todo lo anteriormente expuesto lleva a colegir la desestimación de la demanda.

VII.- COSTAS.

Serán impuestas a la parte demandante conforme dispone al art. 394.1 LEC, al ser rechazadas totalmente sus pretensiones.

Por lo expuesto,

SUPLICO AL TRIBUNAL:

Que teniendo por presentado este escrito con los documentos y copias que le acompañan, lo admita y tenga por contestada en tiempo y forma la demanda y opuesto a la misma; y previos los trámites que corresponden, dicte en su día sentencia por la que se desestime la demanda presentada por Don [COMPLETAR], absolviendo de la misma a mi mandante, con expresa imposición de costas a la actora.

Por ser de justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) Se irá mostrando conformidad o disconformidad con los hechos que se relacionan en la demanda, en párrafos separados y numerados, ordenadamente, con indicación de los documentos procesales y de fondo que se acompañen, numerados correlativamente. En caso de disconformidad con alguno/s de los hechos, se relatarán de igual modo que se han de reflejar en el escrito de demanda los que a juicio de la parte han acaecido.
