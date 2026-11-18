---
name: arrendamiento-trastero-contrato-344
description: "Redacta el escrito «Arrendamiento de trastero: contrato» (formulario 344 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Arrendamiento de trastero: contrato

> Formulario 0344 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] ESTADO CIVIL (2 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (5 veces)
- [ ] Nº (2 veces)
- [ ] FECHA
- [ ] IMPORTE (3 veces)
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de [AÑO]. REUNIDOS De una parte Don»; «…en adelante EL ARRENDADOR. Y de otra Don»; «…de la población de»; «…scrito en el Registro de la Propiedad de»; «…al Tomo»; «…al Tomo [COMPLETAR] Libro»; «…Libro [COMPLETAR] Folio»; «…bro [COMPLETAR] Folio [COMPLETAR] página»; «… cuota respecto de repetido trastero del»; «… la compra que de la misma efectuó a Don»; «…de la finca, al folio»; «… días de cada mes en la entidad bancaria»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 2 de la Ley 29/1994
- artículo 3 LAU
- artículo 34 LAU

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

### Formulario 0344 · Arrendamiento de trastero: contrato

- Año del modelo: 2019
- Revisión 17-11-2026: 28 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de contrato de arrendamiento de trastero; autónomo e independiente del contrato de arrendamiento de vivienda de la que es anejo.

Formulario adaptado a la reforma de la LO 1/2025.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

REUNIDOS

De una parte Don [COMPLETAR], mayor de edad, de estado civil [ESTADO CIVIL], con domicilio en la calle [CALLE] y con D.N.I. n.º [NÚMERO], en adelante EL ARRENDADOR.

Y de otra Don [COMPLETAR], mayor de edad, de estado civil [ESTADO CIVIL], con domicilio en la calle [CALLE] y con D.N.I. n.º [NÚMERO], en adelante EL ARRENDATARIO.

INTERVIENEN

Ambas partes en su propio nombre y derecho (o en nombre y representación de -----) y se reconocen la capacidad suficiente para la formalización del presente contrato.

MANIFIESTAN

Que EL ARRENDADOR, es propietario el trastero que se pasa a describir:

URBANA. Trastero n.º [NÚMERO] sito en la planta del inmueble sito en la calle nº [NÚMERO] de la población de [COMPLETAR] Se halla inscrito en el Registro de la Propiedad de [COMPLETAR] al Tomo [COMPLETAR] Libro [COMPLETAR] Folio [COMPLETAR] página [COMPLETAR] Inscripción

Referencia catastral:

Propiedad Horizontal: Le corresponde una cuota respecto de repetido trastero del [COMPLETAR] %, en los elementos comunes del edificio.

Le pertenece a título de dominio en virtud de la compra que de la misma efectuó a Don [COMPLETAR] en fecha según es de ver en la inscripción n.º [NÚMERO] de la finca, al folio [COMPLETAR] de éste mismo Libro y Tomo.

El presente contrato no es de adhesión y ha sido pactado por ambas partes de forma expresa y detallada, sin suscripción general del mismo, sino previa negociación particular de la diferentes estipulaciones y pactos que conforman el mismo.

Ambas partes contratantes reconocen y establecen que este CONTRATO DE ARRENDAMIENTO DE TRASTERO es autónomo e independiente de cualquier contrato de arrendamiento de vivienda, por lo que queda excluido de lo contemplado al efecto por el artículo 2 de la Ley 29/1994, de 24 de noviembre, de Arrendamientos Urbanos (en adelante LAU).

CLÁUSULAS

PRIMERA. Regulación

El presente contrato tendrá la consideración de arrendamiento para uso distinto del de vivienda conforme al artículo 3 LAU.

Por lo tanto, en todo aquello que no se encuentre regulado en el presente contrato será de aplicación lo dispuesto en el título III LAU y, supletoriamente, lo dispuesto en el Código Civil.

SEGUNDA. Uso

EL ARRENDADOR cede en uso a EL ARRENDATARIO el trastero descrito más arriba, libre de cargas y ocupantes.

EL ARRENDATARIO utilizará la cosa arrendada exclusivamente para el almacenamiento y depósito de bienes muebles no degradables. Queda expresamente prohibido utilizar la finca como vivienda, ni siquiera temporalmente.

EL ARRENDATARIO declara conocer desde este momento su uso, extensión y características comunes. Y se compromete a cumplir las obligaciones que los Estatutos de la Comunidad de Propietarios y las Ordenanzas Municipales establezcan en la materia.

TERCERA. Duración

El plazo de duración del contrato será de [Nº] años a partir de la fecha reseñada en el encabezamiento del presente documento, finalizando por lo tanto el día [FECHA]

Llegada la fecha de vencimiento del contrato, el arrendamiento se prorrogará de forma automática por plazos anuales si ninguna de las partes manifestare lo contrario con dos meses de antelación a la fecha del vencimiento de cada prórroga anual.

Transcurrido los primeros 12 meses, cuyo plazo es de duración obligatoria para el arrendatario, éste podrá rescindir el contrato anticipadamente, sin esperar a su finalización, siempre y cuando lo notifique fehacientemente a la arrendadora con un preaviso mínimo de dos meses de antelación a la fecha de desalojo, viniendo obligado a abonar el recibo de alquiler hasta la fecha de desalojo y entrega de llaves.

EL ARRENDATARIO renuncia expresamente a lo establecido en el artículo 34 LAU, por lo que la extinción del contrato por el transcurso del término convenido, no dará derecho a EL ARRENDATARIO a indemnización alguna a cargo de EL ARRENDADOR

Finalizada la duración pactada y, en su caso, las prórrogas, EL ARRENDATARIO deberá dejar el trastero a la entera disposición de EL ARRENDADOR, en buen estado de uso, salvo el desgaste normal.

CUARTA. Obras

EL ARRENDATARIO declara conocer las características y estado de conservación del trastero y aceptarlas expresamente.

Igualmente declara recibir del trastero en perfectas condiciones en cuanto a su estado de conservación y al correcto funcionamiento de todas y cada una de sus instalaciones, comprometiéndose a entregarlos como los recibe o, en su defecto, a satisfacer en metálico el importe de los desperfectos que existan a la finalización del contrato y que no sean consecuencia del uso normal del trastero.

Las modificaciones que se autoricen por la propiedad serán de cuenta y cargo de EL ARRENDATARIO quien deberá presentar el informe y proyecto de la obra a realizar con el informe de las compañías suministradoras si ello fuere preciso.

No obstante lo anterior, a la finalización del contrato, la EL ARRENDATARIO deberá volver a dejar el local en el mismo estado en que se entrega en el día de hoy.

Por su parte, EL ARRENDADOR estará obligado a realizar todas las reparaciones necesarias para el mantenimiento del trastero en perfectas condiciones para su uso normal, y a requerir a la comunidad de propietarios para que ordenen la realización de obras necesarias en los elementos comunes, al mismo objeto.

QUINTA. Renta

EL ARRENDATARIO abonará a EL ARRENDADOR en concepto de renta la cantidad de [IMPORTE] euros mensuales. El pago se realizará dentro de los 5 primeros días de cada mes en la entidad bancaria [COMPLETAR], mediante ingreso en efectivo en la cuenta n.º [Nº]

El resguardo de ingreso emitido por la entidad bancaria acreditará el pago de la renta salvo prueba en contrario.

El retraso en el pago de la renta será causa suficiente para la resolución del contrato, siendo por cuenta de EL ARRENDATARIO los gastos que ello origine, incluidos los derechos y honorarios de Procurador y Abogado aunque ellos no fuesen preceptivos.

Durante la vigencia del contrato la renta sólo podrá ser actualizada por EL ARRENDADOR o EL ARRENDATARIO en la fecha en que se cumpla cada año de vigencia del contrato, en los términos pactados por las partes. En defecto de pacto expreso, el contrato se actualizará aplicando a la renta correspondiente a la anualidad anterior la variación porcentual experimentada por el índice general nacional del sistema de índices de precios de consumo (IPC) en un período de doce meses inmediatamente anteriores a la fecha de cada actualización, tomando como mes de referencia para la primera actualización el que corresponda al último índice que estuviera publicado en la fecha de celebración del contrato, y en las sucesivas, el que corresponda al último aplicado.

La renta actualizada será exigible a EL ARRENDATARIO a partir del mes siguiente a aquel en que la parte interesada lo notifique a la otra parte por escrito, expresando el porcentaje de alteración aplicado y acompañando, si EL ARRENDATARIO lo exigiera, la oportuna certificación del Instituto Nacional de Estadística.

Será válida la notificación efectuada por nota en el recibo de la mensualidad del pago precedente.

Asimismo, corresponderá a EL ARRENDATARIO el pago del Impuesto sobre Bienes Inmuebles, correspondiente a la cuota del trastero, repercutiéndose dicha cuota en un 10% mensual.

La renta, cantidades asimiladas y demás conceptos incluidos en los recibos de alquiler, devengarán un interés de demora de tres puntos porcentuales por encima del que, en cada momento, sea el interés legal del dinero.

El interés de demora se devengará desde el día en que fuese exigible el recibo de alquiler.

SEXTA. Fianza

EL ARRENDADOR declara en este momento haber recibido de EL ARRENDATARIO en concepto de fianza la cantidad de [IMPORTE] euros, equivalente a dos mensualidades de renta, y que queda adscrita a las responsabilidades de EL ARRENDATARIO y que en ningún caso servirá de pretexto para retrasarse en el pago de la renta.

Durante los tres primeros años de duración del contrato, la fianza no estará sujeta a actualización. Pero cada vez que el arrendamiento se prorrogue, EL ARRENDADOR podrá exigir que la fianza sea incrementada, o EL ARRENDATARIO que disminuya, hasta hacerse igual a una o dos mensualidades de la renta vigente, según proceda, al tiempo de la prórroga.

La fianza será devuelta al que la prestó al finalizar el contrato dentro del mes siguiente al día en que recupere la posesión del bien el propietario, si la misma no tuviera que aplicarse a los desperfectos que haya ocasionado EL ARRENDATARIO.

GARANTÍA

Las partes pactan garantía del cumplimiento por EL ARRENDATARIO de sus obligaciones arrendaticias adicional a la fianza en metálico y, en su virtud, EL ARRENDATARIO aportará antes de la entrada en vigor del presente contrato de arrendamiento –y en todo caso en un plazo de diez días a partir de la fecha de este contrato de arrendamiento–, un aval bancario de primer requerimiento, por importe de [IMPORTE] euros, que se hará efectivo en caso de impago de las cantidades, daños y perjuicios a los que queda obligado por este contrato. Caso de no ser entregado en término y forma el precitado aval bancario, el arrendador quedará facultado para resolver de pleno derecho y sin más trámites el presente contrato.

SÉPTIMA. Obligaciones del arrendatario

EL ARRENDATARIO viene obligado:

-A no instalar transmisiones, motores, máquinas, etc., que produzcan vibraciones o ruidos molestos para los demás ocupantes del inmueble o de los colindantes de la propiedad, o que puedan afectar a la consistencia, solidez o conservación del inmueble.
-A no almacenar o manipular en el trastero materias explosivas, inflamables, incómodas o insalubres, y observar en todo momento las disposiciones vigentes.
-Hallándose el trastero integrado en un inmueble en Régimen de Comunidad en Propiedad Horizontal, a cumplir en todo momento las normas estatutarias, reglamentarias y a los acuerdos que la Comunidad de Propietarios tenga establecidos o establezcan, en orden a la utilización de los servicios, elementos comunes y buen régimen de convivencia.

Si durante el período de vigencia del arrendamiento surgiere la necesidad de realizar alguna reparación en la cosa arrendada que por su urgencia no pudiera diferirse hasta la conclusión del contrato, está EL ARRENDATARIO obligado a tolerar la obra y EL ARRENDADOR a reducir la renta en la cantidad que resulte de multiplicar el número de días que no se ha podido utilizar el bien por la renta diaria.

EL ARRENDATARIO se obliga a poner en conocimiento de EL ARRENDADOR, en el plazo más breve posible, la necesidad de reparaciones o las actuaciones molestas o dañosas de terceros en la cosa arrendada.

EL ARRENDATARIO no podrá hacer por sí o por otros, obras ni mejoras en la cosa arrendada.

OCTAVA. Tanteo y retracto

EL ARRENDATARIO no tendrá derecho de tanteo ni retracto en el que caso de que el propietario enajenare el inmueble; no obstante, el contrato de arrendamiento subsistirá para el adquiriente, que se subrogará en la posición de EL ARRENDADOR hasta la fecha de conclusión del contrato.

NOVENA. Jurisdicción.

Las partes se someten por imperativo de la Ley a los Tribunales del lugar donde radica la finca (asimismo, las partes podrán pactar la sumisión a mediación o arbitraje de aquéllas controversias que por su naturaleza puedan resolverse a través de estas formas de resolución de conflictos, de conformidad con lo establecido en la legislación reguladora de la mediación en asuntos civiles y mercantiles y del arbitraje).

Conformes los contratantes con las estipulaciones que anteceden, extienden por duplicado el presente documento, compuesto de [COMPLETAR] folios, escritos por las dos caras y lo firman, en todas y cada una de ellas, en el lugar y fecha citado en el encabezamiento.

Firma del arrendador

	Firma del arrendatario
