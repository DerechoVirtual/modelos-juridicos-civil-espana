---
name: contestacion-divorcio-reconvencion-sobre-animal-compania-109
description: "Redacta el escrito «Contestación al divorcio con reconvención sobre el animal de compañía» (formulario 109 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación al divorcio con reconvención sobre el animal de compañía

> Formulario 0109 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE
- [ ] NÚMERO (2 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO (2 veces)
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…actúa en nombre y representación de Doña»; «…/[AÑO] promovido por Don»; «…a de los cónyuges, esta parte manifiesta»; «…recido y parte en representación de Doña»; «…formula RECONVENCIÓN contra el actor Don»; «… Odín, con identificación administrativa»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 86 CCiv
- art. 32 CE
- arts. 92.8, 93 y 96 CCiv
- arts. 749.2 y 753 LEC
- art. 394 LEC
- art. 91 CCiv
- art. 94 bis CCiv
- Ley 17/2021

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

### Formulario 0109 · Contestación al divorcio con reconvención sobre el animal de compañía

- Año del modelo: 2022
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 18 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de contestación a demanda de divorcio en que se reconviene solicitando la adopción de medidas respecto a animal de compañía.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, que actúa en nombre y representación de Doña [COMPLETAR], como acredito mediante apoderamiento cuya escritura aporto para unión a los autos mediante testimonio y devolución a esta parte, bajo la dirección del/la Letrado/a D./Dña. [NOMBRE Y APELLIDOS], colegiada nº [Nº DE COLEGIADO/A] del Iltre. Colegio de [LOCALIDAD], con despacho abierto en [LOCALIDAD], calle [CALLE], nº [NÚMERO], en autos de Juicio de divorcio nº [Nº DE PROCEDIMIENTO]/[AÑO] promovido por Don [COMPLETAR], ante el Tribunal comparezco y como mejor proceda en Derecho, DIGO:

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

II.- El fondo de la pretensión actora consiste en la declaración de divorcio, a fin de la disolución del matrimonio, a instancia del marido, de conformidad con el art. 81.2º CCiv, por remisión del art. 86 CCiv, sin necesidad de que se produzca causa legal alguna, sino por la pura voluntad del casado, siendo suficiente que uno de los cónyuges no desee la continuación del matrimonio para que pueda pretender el divorcio, y sin que mi representada pueda oponer motivos materiales a la consideración judicial, al fundarse en la voluntad de no permanecer casado, como corolario legal del derecho del art. 32 CE a contraer matrimonio.

III.- Resultan de aplicación los arts. 91 y ss. CCiv sobre los efectos comunes a la nulidad del matrimonio, separación y divorcio, en especial los arts. 92.8, 93 y 96 CCiv.

IV.- Dada la existencia de un menor de edad, es preceptiva la intervención del Ministerio Fiscal, según lo establecido en los arts. 749.2 y 753 LEC.

V.- Las costas deben imponerse a la actora, de conformidad con lo dispuesto en el art. 394 LEC.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito con los documentos adjuntos y sus copias, se sirva admitirlo, habiéndome por comparecido y parte en representación de Doña [COMPLETAR], y por presentada en tiempo y forma CONTESTACIÓN A LA DEMANDA interpuesta por el demandante, y seguido que sea el juicio por sus trámites legales, dicte en su día sentencia que decrete el divorcio de los cónyuges, acordando las siguientes medidas definitivas:

1. Guarda y custodia compartida del hijo menor:

2. Alimentos en favor del hijo menor:

3. Atribución del uso de la vivienda familiar:

2º.- Al propio tiempo, pretendiéndose y siendo procedente, si es el caso, la adopción de otras medidas definitivas, sobre las que el tribunal no debe pronunciarse de oficio, no habiendo sido solicitadas en la demanda, y siendo necesarias conforme a la Ley 17/2021, esta parte formula RECONVENCIÓN contra el actor Don [COMPLETAR] en solicitud del pronunciamiento que en el suplico se concretará, y que se basa en los siguientes:

HECHOS

ÚNICO.-

Se tienen por expresamente reproducidos los hechos que, al contestar a la demanda, se han ordenado como realidad adversa a la que relaciona la demanda.

No obstante, debe destacarse la existencia de una mascota o animal de compañía en la unidad familiar, en concreto, un perro de raza schnauzer y nombre Odín, con identificación administrativa [COMPLETAR], de titularidad afectos puramente administrativos de Doña [NOMBRE Y APELLIDOS]

Pues bien, siendo necesario adoptar medidas en relación al mismo que en atención a su bienestar que como ser vivo dotado de sensibilidad, tal y como reconoce la Ley 17/2021, merece, y en atención a los especiales vínculos afectivos que las mascotas generan con los miembros de la familia, que dicha Ley ha tenido a bien establecer que deben ser considerados en el momento de regular las medidas que se suceden a una crisis matrimonial o familiar; esta parte pone en conocimiento del Tribunal la especial relación afectiva del demandante con Odín que es merecedora de tutela jurídica.

Así, para adoptar medidas acordes al interés de la mascota común hay que ponderar varias circunstancias. Por un lado, el carácter eminentemente subjetivo del sentimiento de afectividad; en segundo lugar, que la afectividad que pueda tener una persona sobre su mascota no excluye que ésta pueda recibir esa misma afectividad de otras personas, y, finalmente, la superación del elemento meramente formal relativo a la titularidad del perro en documentos y registros. Con ello se quiere decir que la mera titularidad formal del animal, sea como dueño o como adoptante, no puede prevalecer sobre la realidad del afecto del solicitante de la custodia compartida, debidamente acreditada pese a las dificultades que pueda presentar su carácter subjetivo.

En efecto, la tenencia del animal por la pareja, cuando era conviviente, durante más de un año ha generado un vínculo afectivo entre el demandante y el animal que queda plasmada en diversa prueba. Así, consta que la adopción del animal fue solicitada por ambos, demandante y demandado (documento nº [Nº DE DOCUMENTO]), lo que hace prueba de la voluntad de la demandante, junto con la de la demandada, de tener un animal de compañía. Habida cuenta las responsabilidades y tareas que implica la tenencia de una mascota no se entiende que figure como adoptante a quien no desee iniciar esa compañía. Por otro lado, el sentimiento de afectividad del demandante con el animal queda reflejado en el reportaje fotográfico que se aportan como bloque documental nº [NÚMERO] de la demanda, especialmente las que muestran a la demandante sosteniendo en brazos al animal o besándolo, ilustrativas tanto de la voluntad de la demandante de adquirir el animal, como del afecto que dispensa al mismo.

Conforme a todo ello, y en atención al interés del animal de compañía ponderado con el interés de los miembros de la familia, en relación a su tenencia, cuidados, tiempos a compartir, asunción de costes, etc., se solicita el establecimiento de las medidas interesadas por esta parte en el suplico del presente escrito reconvencional.

FUNDAMENTOS DE DERECHO

I.- Es Juez competente para conocer de la demanda reconvencional el que esté conociendo de la demanda principal.

II.- Se formula la presente demanda reconvencional al amparo de lo dispuesto en los arts. 438 y 770.2ª LEC, conforme al cual la reconvención se propondrá con la contestación a la demanda y se admitirá cuando el cónyuge demandado pretenda la adopción de medidas definitivas, que no hubieran sido solicitadas en la demanda, y sobre las que el tribunal no deba pronunciarse de oficio.

III.- Es de aplicación el art. 91 CCiv que establece que en las sentencias de nulidad, separación o divorcio, o en ejecución de las mismas, la autoridad judicial establece las medidas propias de estos procesos, incluyendo el destino de los animales de compañía, que se puede confiar a uno u otro cónyuge de manera exclusiva, o de forma compartida, determinando, en uno u otra modalidad, la forma en la que podrán tenerlos en su compañía, así como el reparto entre los cónyuges de las cargas asociadas al cuidado del animal.

Conforme al art. 94 bis CCiv redactado por Ley 17/2021, estas determinaciones se alcanzan ponderado el interés de los miembros de la familia y el bienestar del animal de compañía, con independencia de la titularidad dominical del mismo y de a quién le haya sido confiado para su cuidado. Esta circunstancia ha de constar en el correspondiente registro de identificación de animales.

IV.- Con arreglo al art. 394 LEC han de imponerse al demandado reconvencional, por el vencimiento.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito y por formulada en tiempo y forma demanda reconvencional, la admita a trámite y previos los que le correspondan por el tribunal se dicte sentencia, en la que se estime la presente reconvención acordando los siguientes pronunciamientos:

En todo caso, con imposición de las costas de esta reconvención a la parte reconvenida.

Es Justicia que finalmente pido en cuanto a principal y otrosí en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

	Firma de Procurador/a
