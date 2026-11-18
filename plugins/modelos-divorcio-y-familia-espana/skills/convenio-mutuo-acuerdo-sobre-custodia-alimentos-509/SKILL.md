---
name: convenio-mutuo-acuerdo-sobre-custodia-alimentos-509
description: "Redacta el escrito «Convenio de mutuo acuerdo sobre custodia, alimentos y relaciones con hijo menor y nasciturus» (formulario 509 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Convenio de mutuo acuerdo sobre custodia, alimentos y relaciones con hijo menor y nasciturus

> Formulario 0509 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] LOCALIDAD (5 veces)
- [ ] NÚMERO (5 veces)
- [ ] C.P. (2 veces)
- [ ] NOMBRE Y APELLIDOS (8 veces)
- [ ] FECHA (4 veces)
- [ ] Nº DE RESOLUCIÓN
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…una parte, Dª., mayor de edad, vecina de»; «…, mayor de edad, vecino de»; «…, al Tomo»; «…sos de enfermedad leve. - Comunicaciones»; «…a su notificación en el número de cuenta»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 0509 · Convenio de mutuo acuerdo sobre custodia, alimentos y relaciones con hijo menor y nasciturus

- Año del modelo: 2017
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 21 campos de relleno marcados en blanco; 8 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma de la LO 1/2025.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

REUNIDOS

De una parte, Dª., mayor de edad, vecina de [COMPLETAR], con domicilio en [LOCALIDAD], nº [NÚMERO], C.P. [C.P.] y provista de D.N.I. nº [NÚMERO];

Y de otra, D. [NOMBRE Y APELLIDOS], mayor de edad, vecino de [COMPLETAR], con domicilio en [LOCALIDAD], nº [NÚMERO], C.P. [C.P.] y provisto de D.N.I. nº [NÚMERO]

Los comparecientes, que intervienen en su propio nombre y derecho, se reconocen plena capacidad legal para el otorgamiento del presente documento en el que formalizan CONVENIO REGULADOR de las relaciones paterno-filiales, guarda y custodia, y alimentos, en relación con su hija menor Dª. y su hijo concebido, no nacido; y al efecto,

EXPONEN

1º) Que mis representados, Dª. y D. [NOMBRE Y APELLIDOS], estuvieron unidos en matrimonio hasta fecha [FECHA], cuando de mutuo acuerdo decidieron instar la disolución de su vínculo matrimonial por divorcio; lo cual se llevó a efecto a medio de Sentencia número [Nº DE RESOLUCIÓN], de Divorcio de Mutuo Acuerdo, de fecha [FECHA], seguida ante la sección de familia, infancia y capacidad del Tribunal [NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).] de Instancia de [LOCALIDAD], número de autos

2º) Hace aproximadamente tres años, la Sra. [NOMBRE Y APELLIDOS] y el Sr. [NOMBRE Y APELLIDOS], reanudaron su relación afectiva, la cual finalizó antes del inicio del verano del presente año.

Fruto de dicha reciente relación entre mis representados, nació una hija, Dª., en fecha [FECHA], estando inscrito su nacimiento en el Registro Civil de [LOCALIDAD], al Tomo [COMPLETAR], Página de la Sección

Asimismo y como consecuencia de la mentada relación sentimental habida entre D. [NOMBRE Y APELLIDOS] y Dª, en la actualidad, ésta se halla embarazada del que será su segundo hijo en común, es decir, han concebido un segundo hijo todavía no nato.

Dª., en la actualidad, cuenta con semanas de gestación, por lo cual el nacimiento del segundo hijo en común tendrá lugar, según estimaciones médicas especializadas, aproximadamente sobre el

3º) No existe domicilio familiar en propiedad, sino que éste se halla establecido en la vivienda propiedad de los padres de Dª., sita en [LOCALIDAD]; vivienda en la que continúa residiendo mi representada, junto con sus padres, en compañía de su hija, y así lo seguirá haciendo cuando alumbre a su hijo concebido no nacido, atribuyéndose en todo caso el uso de la misma a Dª., su hija Dª. y su hijo concebido aún no nacido.

4º) En cuanto a los hijos de la pareja, deben realizarse ciertas precisiones, a fin de lograr un pleno entendimiento de las medidas suscritas en el presente convenio regulador del que ambos progenitores solicitan su autorización judicial.

Por lo que respecta al segundo hijo de la pareja, nasciturus, concebido pero aún no nacido, debe especificarse que según las indicaciones médicas, su alumbramiento tendrá lugar aproximadamente en fecha [FECHA] Recogiéndose en este convenio regulador, desde este momento, las medidas que han de regular su relación con sus progenitores, las cuales no producirán efectos hasta el momento en el que el nacimiento del menor ocurra.

5º) En cuanto a los gastos que genera el sostenimiento de la hija menor, debe destacarse que ésta debido a su edad, todavía no ha iniciado sus estudios en ningún centro escolar

Tomando en consideración únicamente los gastos habituales de la menor desde su nacimiento, alimentación, vestido; etc. Se estima que la cuantía de los mismos, en la actualidad, asciende a una cantidad aproximada de seiscientos euros mensuales (600,00€). A los cuales habrán de añadirse los restantes gastos anteriormente señalados, así como las variaciones necesarias en su alimentación.

En cuanto a los gastos que el concebido no nacido pueda ocasionar, en estos momentos son de muy difícil cuantificación, por lo cual ambas partes ha fijado un mínimo indispensable en la cuantía de cuatrocientos euros mensuales (400,00€), la cual podría verse incrementada al momento del nacimiento, según las necesidades de éste. Salvado la parte de los gastos extraordinarios que todo nacimiento trae aparejado, tales como, la adquisición de una cuna, silla de paseo, etc.

6º) Por razones que no viene al caso detallar surgieron entre los progenitores desavenencias, que determinaron que ambos hayan roto su relación sentimental.

Ante tal circunstancia, han decidido solicitar judicialmente la regularización de las relaciones paterno-filiales, guarda y custodia, y alimentos en relación a su hija D. [NOMBRE Y APELLIDOS], y a su hijo concebido, no nacido; para lo cual otorgan el presente CONVENIO REGULADOR, según las siguientes,

Estipulaciones

PRIMERA .- Patria Potestad y Guarda y Custodia. La patria potestad de la hija menor de la pareja, Dª., y del hijo concebido, no nacido, para cuando éste nazca, se ejercerá por ambos progenitores conjuntamente; atribuyéndose a la madre, Dª., la guarda y custodia de los hijos.

SEGUNDA .- Régimen de visitas. Con el fin de que el progenitor no custodio, pueda relacionarse y estar con su hija y su hijo concebido, todavía no nato, para el momento que se produzca su nacimiento, se establece el siguiente régimen de visitas que ha de ser progresivo dada la edad de su hija mayor, Dª. y de la especialidad de que su segundo hijo aún no haya nacido.

Así el régimen de visitas a favor del padre, D. [NOMBRE Y APELLIDOS], será el siguiente:

En relación a la hija menor Dª.:

• Hasta que ésta alcance los 3 años de edad, es decir, hasta fecha:

a) Un día intersemanal, durante tres horas, preferiblemente los jueves. El día exacto intersemanal en el que el padre tendrá consigo a la menor no se establece taxativamente, sino que si por cualquier circunstancia de entidad que pudiera ocurrir tanto a los progenitores como a la menor, la visita no se pudiera efectuar el día señalado, los padres se han de comunicar a la mayor brevedad posible, por medio de SMS con acuse de recibo, el cambio de día intersemanal.

En caso de que la menor realice alguna actividad formativa o lúdica, el padre deberá recoger a la hija en el domicilio familiar, acompañarla a dicha actividad, entregándola de nuevo en el domicilio familiar a la hora estipulada.

b) Tardes de sábados alternos durante 4 horas. Recogiendo y entregando el padre a la menor en el domicilio familiar.

Desde que la menor alcance los 3 años de edad, es decir, a partir de:

a) Un día intersemanal, preferiblemente los jueves, desde las 16:00 a las 20:00 horas. El día exacto intersemanal en el que el padre tendrá consigo a la menor no se establece taxativamente, sino que si por cualquier circunstancia de entidad que pudiera ocurrir tanto a los progenitores como a la menor, la visita no se pudiera efectuar el día señalado, los padres se han de comunicar a medio de SMS con acuse de recibo, el cambio de día intersemanal.

En caso de que la menor realice alguna extraescolar o lúdica, el padre deberá recoger a la hija en el domicilio familiar, acompañarla a dicha actividad, entregándola de nuevo en el domicilio familiar a la hora estipulada.

b) Sábados alternos desde las 12:00 a las 20:00 horas. Recogiendo y entregando el padre a la menor en el domicilio familiar.

En relación al hijo concebido, aún no nacido:

• Desde que se produzca su nacimiento, hasta que éste alcance su primer año de vida:

a) Un día intersemanal, durante una hora, preferiblemente los jueves. El día exacto intersemanal en el que el padre tendrá consigo al menor no se establece taxativamente, sino que si por cualquier circunstancia de entidad que pudiera ocurrir tanto a los progenitores como al hijo, la visita no se pudiera efectuar el día señalado, los padres se han de comunicar a medio de SMS con acuse de recibo, el cambio de día intersemanal.

En caso de que el menor realice alguna actividad formativa o lúdica, el padre deberá recoger al hijo en el domicilio familiar, acompañarlo a dicha actividad, entregándolo de nuevo en el domicilio familiar a la hora estipulada.

b) Tardes de sábados alternos durante 2 horas. Recogiendo y entregando el padre al menor en el domicilio familiar.

Desde que el menor cumpla su primer año de vida y hasta que alcance los 3 años de edad:

a) Un día intersemanal, durante tres horas, preferiblemente los jueves. El día exacto intersemanal en el que el padre tendrá consigo al menor no se establece taxativamente, sino que si por cualquier circunstancia de entidad que pudiera ocurrir tanto a los progenitores como al menor, la visita no se pudiera efectuar el día señalado, los padres se han de comunicar a medio de SMS con acuse de recibo, el cambio de día intersemanal.

En caso de que el menor realice alguna formativa o lúdica, el padre deberá recoger al hijo en el domicilio familiar, acompañarlo a dicha actividad, entregándolo de nuevo en el domicilio familiar a la hora estipulada.

b) Tardes de sábados alternos durante 4 horas. Recogiendo y entregando el padre al menor en el domicilio familiar.

* No se establece el horario exacto en el cual el padre tiene derecho a visita intersemanal o de sábados alternos, puesto que por la especialidad del caso, al no haber nacido todavía el hijo concebido, se desconoce cuál vaya a ser su forma de alimentación, circunstancias de salud, etc. Circunstancias todas ellas que podrían llevar a tener que modificar un supuesto horario estipulado.

Desde que el hijo alcance los 3 años de edad:

a) Un día intersemanal, preferiblemente los jueves, desde las 16:00 a las 20:00 horas. El día exacto intersemanal en el que el padre tendrá consigo a la menor no se establece taxativamente, sino que si por cualquier circunstancia de entidad que pudiera ocurrir tanto a los progenitores como a la menor, la visita no se pudiera efectuar el día señalado, los padres se han de comunicar a medio de SMS con acuse de recibo, el cambio de día intersemanal.

En caso de que la menor realice alguna extraescolar o lúdica, el padre deberá recoger a la hija en el domicilio familiar, acompañarla a dicha actividad, entregándola de nuevo en el domicilio familiar a la hora estipulada.

b) Sábados alternos desde las 12:00 a las 20:00 horas. Recogiendo y entregando el padre a la menor en el domicilio familiar.

* El padre se encargará de alimentar al menor durante el tiempo en que la tenga en su compañía, atendiendo a las circunstancias óptimas establecidas para ello, a las que el menor viene acostumbrado.

- El presente convenio se establece diferenciando a ambos hijos, puesto que el cumplimiento de las medidas establecidas para el nasciturus se hallan bajo la condición de su efectivo nacimiento. No obstante, atendiendo al mayor interés de los dos hijos, el padre intentará siempre tener a los menores en su compañía a la vez, buscando no separarlos.

- Los progenitores habrán de informarse mutuamente, con antelación razonable, del destino, dirección concreta de estancia y número de teléfono de localización en los supuestos de viajes dentro del territorio nacional, así como del estado de salud y tratamientos de los hijos, incluso en los casos de enfermedad leve.

- Comunicaciones [COMPLETAR]: ambos progenitores podrán, en el periodo en que los menores no estén en su compañía, comunicarse con ellos por los medios habituales (teléfono, whatsapp, etc.), respetando sus horarios de estudio, comida y descanso. Siempre atendiendo a las circunstancias excepcionales de la edad de los menores y a su capacidad de comprensión y habla.

TERCERA .- De la atribución del uso de la vivienda y ajuar familiar. No existe domicilio familiar en propiedad, sino que ésta se halla establecida en la vivienda propiedad de los padres de Dª. vivienda en la que continúa residiendo ésta en compañía de su hija y así lo seguirá haciendo cuando alumbre a su hijo concebido no nacido, atribuyéndose en todo caso el uso de la misma a Dª., su hija Dª. y su hijo concebido aún no nacido.

CUARTA .- Pensión de alimentos. El padre, D. [NOMBRE Y APELLIDOS], abonará en concepto de pensión alimenticia para su hija, Dª., la cantidad de trescientos euros mensuales (300,00€).

Por su parte, el padre abonará en concepto de pensión alimenticia para su hijo concebido, aún no nacido y desde que se produzca el alumbramiento del mismo, la cantidad de doscientos euros mensuales (200,00€).

El padre ingresará dentro de los cinco primeros días de cada mes, en la cuenta abierta a nombre de Dª., número [NÚMERO], las cuantías antes establecidas en concepto de pensión alimenticia para sus dos hijos, encargándose de gestionar la madre tales cantidades a favor de los menores.

Dichas cantidades podrán verse incrementadas anualmente conforme a las variaciones que experimente el Índice de Precios al Consumo (IPC) que publica periódicamente el I.N.E. (o cualquier organismo público que pudiera sustituirle en el futuro), tomando como base para el comienzo del cómputo la fecha de la sentencia que apruebe el presente convenio regulador, y sin que sea necesario el previo requerimiento o notificación de dichos índices al obligado al pago.

QUINTA .- Gastos extraordinarios.- En concepto de gastos extraordinarios (entre otros: gastos del colegio, material escolar, autobús escolar, clases particulares, actividades extraordinarias, gastos médicos y farmacéuticos no incluidos en seguros médicos, desplazamientos a centros hospitalarios, afiliaciones a asociaciones relacionadas con los menores, mobiliario doméstico, etc.) respecto de la hija y el hijo concebido, aún no nacido, el padre abonará el 50% de los mismos, a la presentación de las correspondientes facturas o recibos justificativos por la madre, debiendo abonar tales cantidades, dentro del plazo de los 5 días siguientes a su notificación en el número de cuenta [COMPLETAR], del cual es titular Dª.

SEXTA .- Dª. se compromete a abonar la totalidad de los gastos judiciales inherentes a este procedimiento, incluidos los honorarios de procurador que los represente y abogado que los defienda.

SÉPTIMA El presente convenio resuelve todas las posibles diferencias existentes entre ambos progenitores e implica transacción de todas las cuestiones planteadas entre los mismos, por lo que ambos se comprometen a formular demanda de mutuo acuerdo de juicio verbal sobre guarda y custodia, alimentos y relaciones paternofiliales, respecto a la hija menor de la pareja, Dª. y del hijo concebido aun no nacido; constituyendo el presente documento como propuesta de convenio regulador de todos sus efectos. Asimismo ambos comparecientes se comprometen, previo traslado del mismo al Ministerio Fiscal, a ratificar y reconocer el presente convenio ante la autoridad judicial a fin de llevar a cabo la efectividad de los acuerdos plasmados en el mismo.

Y en prueba de conformidad, ratificándose los reunidos en el contenido de todos y cada uno de los pactos que integran el presente documento, los cuales han sido redactados según sus propias instrucciones, lo suscriben y firman en el lugar y fecha indicados en el encabezamiento.

Fdo. Fdo.

========================================================================
