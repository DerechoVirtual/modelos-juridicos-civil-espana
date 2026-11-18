---
name: contestacion-divorcio-reconvencion-modelo-general-502
description: "Redacta el escrito «Contestación al divorcio con reconvención (modelo general)» (formulario 502 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación al divorcio con reconvención (modelo general)

> Formulario 0502 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NÚMERO (3 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] IMPORTE (3 veces)
- [ ] Nº
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…actúa en nombre y representación de Doña»; «…/[AÑO] promovido por Don»; «…a de los cónyuges, esta parte manifiesta»; «…recido y parte en representación de Doña»; «…formula RECONVENCIÓN contra el actor Don»; «… como consecuencia de su trabajo por Don»; «…ue ha venido desarrollando en la empresa»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 86 CCiv
- art. 32 CE
- arts. 92.8, 93 y 96 CCiv
- arts. 749.2 y 753 LEC
- art. 394 LEC
- art. 409 LEC
- art. 253 LEC
- art. 251 LEC
- art. 97 CCiv

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

### Formulario 0502 · Contestación al divorcio con reconvención (modelo general)

- Año del modelo: 2017
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 22 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Contestación a demanda de divorcio en que se reconviene solicitando el reconocimiento del derecho a una prestación compensatoria.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, que actúa en nombre y representación de Doña [COMPLETAR], como acredito mediante apoderamiento cuya escritura aporto para unión a los autos mediante testimonio y devolución a esta parte, bajo la dirección del/la Letrado/a D./Dña. [NOMBRE Y APELLIDOS], colegiada n.º [NÚMERO] del Iltre. Colegio de [LOCALIDAD], con despacho abierto en [LOCALIDAD], calle [CALLE], n.º [NÚMERO], en autos de Juicio de divorcio n.º [Nº DE PROCEDIMIENTO]/[AÑO] promovido por Don [COMPLETAR], ante el Tribunal comparezco y como mejor proceda en Derecho, DIGO:

Que, en la representación que ostento y dentro del plazo legal, vengo a CONTESTAR a la demanda y formular RECONVENCIÓN.

1º.- Fundamento la CONTESTACIÓN A LA DEMANDA en los siguientes hechos y consideraciones jurídicas:

HECHOS

PRIMERO.- De acuerdo con el correlativo de la demanda, sobre los datos del matrimonio celebrado, filiación, domicilio familiar, régimen económico de los cónyuges y la vecindad civil común de ambos, negando el resto de los hechos alegados en la misma, en los que justifica la solicitud de las medidas relativas al hijo menor, la determinación de la contribución económica para su manutención y educación, y la atribución del uso de la vivienda familiar.

SEGUNDO.- Respecto a la situación laboral y capacidad económica de los cónyuges, esta parte manifiesta [COMPLETAR]

TERCERO.- Disconforme con el contenido de las medidas definitivas solicitadas en relación con la guarda y custodia del hijo menor, los alimentos a favor de éste y la atribución del uso de la vivienda habitual de la familia, se formula oposición en cuanto a estos extremos debiendo señalarse que

Se solicita por lo expuesto la adopción de las siguientes medidas definitivas:

1. Guarda y custodia compartida del hijo menor:
2. Alimentos en favor del hijo menor:
3. Atribución del uso de la vivienda familiar:

FUNDAMENTOS DE DERECHO

I.- Conformes con la competencia objetiva y territorial del Tribunal, la legitimación de los cónyuges, y el procedimiento adecuado escogido, compareciendo esta parte con la debida representación técnica y asistencia letrada.

II.- El fondo de la pretensión actora consiste en la declaración de divorcio, a fin de la disolución del matrimonio, a instancia del marido, de conformidad con el art. 81.2.º CCiv, por remisión del art. 86 CCiv, sin necesidad de que se produzca causa legal alguna, sino por la pura voluntad del casado, siendo suficiente que uno de los cónyuges no desee la continuación del matrimonio para que pueda pretender el divorcio, y sin que mi representada pueda oponer motivos materiales a la consideración judicial, al fundarse en la voluntad de no permanecer casado, como corolario legal del derecho del art. 32 CE a contraer matrimonio.

III.- Resultan de aplicación los arts. 91 y ss. CCiv sobre los efectos comunes a la nulidad del matrimonio, separación y divorcio, en especial los arts. 92.8, 93 y 96 CCiv.

IV.- Dada la existencia de un menor de edad, es preceptiva la intervención del Ministerio Fiscal, según lo establecido en los arts. 749.2 y 753 LEC.

V.- Las costas deben imponerse a la actora, de conformidad con lo dispuesto en el art. 394 LEC.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito con los documentos adjuntos y sus copias, se sirva admitirlo, habiéndome por comparecido y parte en representación de Doña [COMPLETAR], y por presentada en tiempo y forma CONTESTACIÓN A LA DEMANDA interpuesta por el demandante, y seguido que sea el juicio por sus trámites legales, dicte en su día sentencia que decrete el divorcio de los cónyuges, acordando las siguientes medidas definitivas:

2º.- Al propio tiempo esta parte formula RECONVENCIÓN contra el actor Don [COMPLETAR] en solicitud del pronunciamiento que en el suplico se concretará, y que se basa en los siguientes:

HECHOS

ÚNICO.-

Se tienen por expresamente reproducidos los hechos que, al contestar a la demanda, se han ordenado como realidad adversa a la que relaciona la demanda.

FUNDAMENTOS DE DERECHO

I.- Es Juez competente para conocer de la demanda reconvencional el que esté conociendo de la demanda principal.

II.- Conforme al art. 770.2.ª LEC"La reconvención se propondrá con la contestación a la demanda. El actor dispondrá de 10 días para contestarla (...) Solo se admitirá la reconvención (...) d) Cuando el cónyuge demandado pretenda la adopción de medidas definitivas, que no hubieran sido solicitadas en la demanda, y sobre las que el tribunal no deba pronunciarse de oficio."

El art. 409 LEC señala a este respecto que la reconvención se sustanciará y resolverá al propio tiempo y en la misma forma que la cuestión principal del pleito y será resuelta con éste en la sentencia definitiva.

III.- Las partes en la cuestión reconvencional son las mismas que en la demanda principal, pero con su papel invertido, esto es, el actor en la principal es aquí el demandado reconvencional, y el demandado es aquí demandante reconvencional.

IV.- Conforme a la admonición del art. 253 LEC, puesto que se reclama una prestación pecuniaria, cifro la cuantía de esta reconvención en [IMPORTE] euros, que es la pensión compensatoria anualizada multiplicada por diez, en armonía con la regla 7.ª del art. 251 LEC.

V.- Fundamento legal de la reconvención. Esta parte considera que al amparo de lo establecido en el art. 97 CCiv resulta procedente el establecimiento de una pensión compensatoria a favor de mi mandante al habérsele producido un evidente desequilibrio en relación con la posición del demandado reconvencional, que implica un empeoramiento en su situación económica anterior en el matrimonio.

En este sentido, y a los efectos de fijar el importe de la meritada pensión, esta parte considera necesario valorar la edad de mi mandante, [Nº] años, así como su estado de salud, lo mismo que sus escasas posibilidades de obtener un puesto de trabajo debido a su falta de formación y al hecho de que ha dedicado gran parte de su vida adulta al cuidado de su familia y no al desarrollo de ninguna clase de profesión. El matrimonio se benefició siempre de los ingresos obtenidos como consecuencia de su trabajo por Don [COMPLETAR], trabajo que ha venido desarrollando en la empresa [COMPLETAR], sin que haya tenido más modificación en sus rendimientos que las lógicas actualizaciones anuales.

En atención a todo lo anterior, esta parte considera lo procedente el establecimiento de una pensión compensatoria a favor de mi mandante por importe de [IMPORTE] euros mensuales, actualizable por períodos anuales de conformidad con las fluctuaciones del índice de precios al consumo. A nuestro juicio, y siempre de conformidad con lo establecido en el mencionado art. 97 CCiv, la solicitada pensión compensatoria deberá establecerse con carácter periódico y sin limitación temporal alguna -naturalmente sin perjuicio de eventuales cambios futuros en las circunstancias esenciales que ahora concurren-, tomando en cuenta la edad de mi mandante, sus escasas perspectivas de incorporarse en el futuro al mercado de trabajo, así como, muy especialmente, la prolongada duración del matrimonio.

VI.- Con arreglo al art. 394 LEC han de imponerse al demandado reconvencional, por el vencimiento.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito y por formulada en tiempo y forma demanda reconvencional, la admita a trámite y previos los que le correspondan acuerde el establecimiento de una pensión compensatoria en favor de mi mandante y a cargo de la parte reconvenida por importe de [IMPORTE] euros mensuales, a pagar mediante ingreso en la cuenta corriente n.º [NÚMERO], de la que es titular mi representada, durante los cinco primeros días de cada mes y actualizable anualmente de acuerdo con las variaciones del Índice de Precios al Consumo publicado por el Instituto Nacional de Estadística u organismo, público o privado, que en el futuro le sustituya, con imposición de las costas de esta reconvención a la parte reconvenida.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

========================================================================
