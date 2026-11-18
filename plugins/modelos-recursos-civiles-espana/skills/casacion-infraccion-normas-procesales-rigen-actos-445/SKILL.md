---
name: casacion-infraccion-normas-procesales-rigen-actos-445
description: "Redacta el escrito «Casación por infracción de normas procesales que rigen los actos y garantías del proceso» (formulario 445 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Casación por infracción de normas procesales que rigen los actos y garantías del proceso

> Formulario 0445 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (3 veces)
- [ ] Nº DE PROCEDIMIENTO (4 veces)
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] ACTO O RESOLUCIÓN
- [ ] FECHA (8 veces)
- [ ] AÑO (2 veces)
- [ ] SEDE (2 veces)
- [ ] NÚMERO
- [ ] IMPORTE
- [ ] Nº DE EXPEDIENTE
- [ ] LUGAR
- [ ] Otros 16 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…a procesal de la LO 1/2025. A LA SECCIÓN»; «…editada en los autos de juicio ordinario»; «…lamación por responsabilidad contractual»; «…numeración del juzgado de procedencia).]»; «… en recurso de reposición interpuesto el»; «…iteró en el acto del juicio celebrado el»; «…, el»; «…raba presente asistida por el Letrado D.»; «…y del representante legal de la entidad»; «…ntencia de primera instancia, dictada el»; «…fue desestimado mediante auto dictado el»; «…odido realizar. Mediante auto dictado el»; …

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 477.2 LEC
- art. 477.2 LEC
- arts. 477.2 y 3 LEC
- art. 414 LEC
- art. 429.1 LEC
- art. 414.2 LEC
- art. 432 LEC
- art. 414.1 LEC
- art. 23 LEC
- arts. 399 y 405 LEC
- art. 481.6 LEC
- art. 481 LEC
- Ley 5/2023

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

### Formulario 0445 · Casación por infracción de normas procesales que rigen los actos y garantías del proceso

- Año del modelo: 2018
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (2); 40 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de interposición de recurso de casación fundado en infracción de norma procesal [NOTA DE REVISIÓN: En casación por infracción procesal hay que acreditar la denuncia previa en la instancia y, en su caso, la petición de subsanación (arts. 477.6 y 479.2 LEC); citarlos. Fuente: LEC arts. 477.2, 477.6 y 479.2 (redacc. RDL 5/2023, BOE-A-2023-15135).] ante la Sala Primera del Tribunal Supremo, al amparo del artículo 477.2 LEC (infracción de las normas legales que rigen los actos y garantías del proceso), adaptado al Real Decreto-Ley 5/2023, de 28 de junio.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN [COMPLETAR] DE LA AUDIENCIA PROVINCIAL DE [LOCALIDAD]

[NOTA DE REVISIÓN: Errata. La Audiencia Provincial no cambia de denominación; sus Secciones se identifican por su número. Fuente: LOPJ arts. 80 y 82 (Audiencia Provincial, sin cambio de denominación).]

Autos nº [Nº DE PROCEDIMIENTO]

Rollo de apelación nº [Nº DE PROCEDIMIENTO]

D./Dª. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre de D./Dª. [NOMBRE Y APELLIDOS], cuya representación tengo debidamente acreditada en los autos de juicio ordinario [COMPLETAR], sobre reclamación por responsabilidad contractual [COMPLETAR], seguido a nuestra instancia contra [ACTO O RESOLUCIÓN], ante la Sala comparezco y, como mejor proceda en Derecho, DIGO:

Que, por medio del presente escrito, en virtud de lo dispuesto en el art. 477.2 LEC, en la redacción dada por el Real Decreto-Ley 5/2023, de 28 de junio, y dentro del plazo legal, interpongo en nombre de D./Dª [NOMBRE Y APELLIDOS]. RECURSO DE CASACIÓN ante la Sala Primera del Tribunal Supremo, contra la sentencia de fecha [FECHA] dictada por esta Audiencia Provincial, en grado de apelación, y notificada en fecha [FECHA]; en los autos de juicio ordinario al margen referenciados, con arreglo a los motivos siguientes:

1.- Enumeración de los Motivos (1)

El presente recurso de casación se interpone en base a los siguientes motivos:

PRIMER MOTIVO

En virtud de lo dispuesto en los arts. 477.2 y 3 LEC, se denuncia la infracción de las normas legales que rigen los actos y garantías del proceso, que han colocado a mi mandante en una situación de indefensión absoluta. De esta forma, se vulneró el art. 414 LEC al tener por no comparecida a esta parte al acto de la Audiencia Previa, celebrada en el marco del Juicio Ordinario nº [Nº DE PROCEDIMIENTO]/[AÑO], tramitado ante el Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], con el argumento de que no intervenía el Procurador de los Tribunales. Y ello, a pesar de que mi mandante compareció personalmente asistida de Letrado, preparado para intervenir en tal acto procesal. Como consecuencia de ello, no se pudor proponer prueba para su práctica en juicio, a lo que tenía derecho esta parte, en virtud de lo dispuesto en el art. 429.1 LEC.

La infracción se denunció en recurso de reposición interpuesto el [COMPLETAR]., frente a la resolución oral emitida en la Audiencia Previa, desestimado mediante auto de fecha [FECHA]. Se reiteró en el acto del juicio celebrado el [COMPLETAR]., denegándose la práctica de prueba (consistente en tres testificales y un interrogatorio) mediante resolución oral dictada en la propia vista, frente a la que se protestó. Se sostuvo también en el recurso de apelación, volviéndose a denegar la práctica de la prueba por auto dictado por la Audiencia Provincial de [LOCALIDAD], el [COMPLETAR].; y desestimándose el antedicho recurso de apelación mediante la sentencia que aquí se impugna.

La imposibilidad de practicar las pruebas que se iban a proponer en la Audiencia Previa, causaron un perjuicio material y efectivo al derecho de defensa de mi mandante, toda vez que se trataba de contar con el testimonio de tres personas (un transportista y dos empleados de la demandada) que intervinieron en el suministro, que finalmente se tuvo por no acreditado en la sentencia de instancia (confirmada por la de apelación), como base para la desestimación de la demanda.

SEGUNDO MOTIVO

2.- Justificación de los Motivos (2)

PRIMER MOTIVO

Como se ha indicado, el primer motivo que se esgrime en el presente recuso es la infracción de las normas legales reguladoras de los actos y garantías procesales del proceso cuando la infracción determinare la nulidad conforme a la ley o hubiere podido producir indefensión. En concreto, en el marco de la primera instancia desarrollada ante la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO], Juicio Ordinario nº [Nº DE PROCEDIMIENTO]/[AÑO], se tuvo por no comparecida a mi mandante en la Audiencia Previa, por no acudir representado por Procurador de los Tribunales, mediante resolución oral dictada en ese acto (minuto / del acta audiovisual). Y ello, a pesar de que mi representada, D./Dª [NOMBRE Y APELLIDOS], se encontraba presente asistida por el Letrado D. [COMPLETAR]. Como consecuencia de tal decisión, esta parte no pudo proponer las pruebas testificales de D./Dª [NOMBRE Y APELLIDOS], D./Dª [NOMBRE Y APELLIDOS] y del representante legal de la entidad [COMPLETAR] SL, ni el interrogatorio de la parte demandada. La sentencia de primera instancia, dictada el [COMPLETAR], desestimó las pretensiones de mi mandante, al no tener por acreditada la realización de los suministros por cuyo impago se reclamaba la cantidad de [IMPORTE] euros. Extremo que se habría determinado, sin género de dudas, con las testificales que no se pudieron practicar, de los dos empleados, antes reseñados, que recibieron los suministros, y el representante legal de la entidad transportista que los trasladó hasta las instalaciones propiedad del demandado.

La decisión de no tener por comparecida a mi mandante fue recurrida en reposición, denunciando la infracción de lo dispuesto en el art. 414 LEC, y el derecho de mi cliente a intervenir en el acto de la Audiencia Previa y proponer las pruebas que considere procedente. Tal recurso fue desestimado mediante auto dictado el [COMPLETAR]. El juicio, que tuvo lugar en fecha [FECHA], se celebró sin la práctica de las pruebas indicadas. Las mismas se intentaron proponer de nuevo en la vista, siendo denegada la petición mediante resolución oral (minuto / del acta audiovisual), formulándose la correspondiente propuesta. Frente a la sentencia desestimatoria de las pretensiones de mi mandante, se interpuso recurso de apelación que denunciaba, entre otras infracciones, la vulneración del mencionado art. 414 LEC. También se solicitaba la práctica de las pruebas cuya proposición no se había podido realizar. Mediante auto dictado el [COMPLETAR], la Audiencia Provincial de [LOCALIDAD] denegó la práctica de dichas pruebas, lo que se recurrió en reposición, también denegado mediante auto de fecha [FECHA]. Finalmente, la sentencia de apelación, dictada el [COMPLETAR], confirmó la sentencia de instancia, considerando no acreditados los suministros por los que se reclama.

De una interpretación literal del art. 414 LEC se deprende que si concurre personalmente la parte no se requiere la presencia de Procurador de los Tribunales, siendo facultativa su presencia. Es decir, no cabe exigir como preceptiva la asistencia de éste cuando lo haga la parte. Asimismo, es necesaria la asistencia de abogado, que en el caso en concreto sí que acudió. A la misma conclusión se llega, acudiendo a los elementos teleológico, sistemático e histórico de interpretación. No cabe desconectar, el apartado primero de tal precepto legal, de los respectivos apartados 2 y 3, ni estimar que la alternativa parte o procurador con poder (para renunciar, allanar o transigir) se refiere exclusivamente al intento de arreglo o transacción, de modo que en cuanto a otros efectos (restante contenido, eventual, de la audiencia) sería preceptiva en todo caso la asistencia de Procurador. Debe entenderse que la parte puede asistir personalmente o hacerlo por medio de su Procurador con el poder legalmente exigible, y en el primer caso no es indispensable que también asista el causídico. En esta línea, el art. 414.2 LEC dispone "las partes habrán de comparecer en la audiencia asistidas de abogado", el art. 432 LEC establece que "sin perjuicio de la intervención personal en el interrogatorio que se hubiere admitido, las partes comparecerán en juicio representadas por procurador y asistidas de abogado". Se llega a la misma conclusión, atendiendo al elemento teleológico en relación con la finalidad o "ratio" de la audiencia previa (art. 414.1 LEC), y el antecedente histórico, toda vez que el art. 414.1 LEC optó por el criterio del Anteproyecto (el art. 310.2 decía que los litigantes, asistidos de abogado, intervendrán en la comparecencia por sí o por medio de Procurador con poder para renunciar, allanarse o transigir) en lugar del que seguía el Proyecto (en cuyo art. 416.2 se disponía que las partes habrán de comparecer en la audiencia representadas por Procurador y asistidas de Abogado, y añadía en párrafo aparte que al efecto del intento de arreglo o transacción, los litigantes habrán de otorgar a su Procurador poder para renunciar, allanarse o transigir, salvo que, a dicho efecto, concurriesen e interviniesen personalmente, si no concurrieren personalmente ni otorgaren aquel poder, se les tendrá por no comparecidos a la audiencia).

Finalmente, y respondiendo a los argumentos opuestos por la contratarte en el escrito de oposición al recurso de apelación, el art. 23 LEC se refiere a la comparecencia en juicio, y no obsta que para en otro acto procesal concreto no sea ineludible la intervención del procurador, y los arts. 399 y 405 LEC se refieren exclusivamente a los escritos de demanda y de contestación. En esta línea se pronunció el propio Tribunal Supremo en sentencia de 23.07.09 (rec. 2486/2004), confirmando el derecho de cada parte de intervenir en la Audiencia Previa, asistida de Letrado.

En consecuencia, la infracción de la norma legal analizada, ha generado una indefensión directa a mi representada, al verse privada de los medios necesarios para acreditar el suministro impagado por el que reclama: la testifical de quien realizó el transporte, y de los empleados que recibieron los mismos. Indefensión que cristaliza en las sentencias que determinan que no se ha probado, con los medios probatorios a su disposición, tal premisa para decidir el litigio en cuestión. Concurren, de esta manera, los requisitos que exige la jurisprudencia constitucional al respecto de la indefensión, STC 14.02.89 (STC 35/1989): valoración según las circunstancias de cada caso, apreciando la indefensión material directa derivada de la infracción legal, traducida en un perjuicio real y efectivo del derecho de defensa (STC 22.07.88, 155/1988).

En consecuencia, procede estimar el presente recurso, declarar la nulidad de actuaciones hasta el acto de la Audiencia Previa, sin perjuicio del principio de conservación de los actos procesales no afectados por la nulidad.

SEGUNDO MOTIVO

Por todo lo expuesto,

SUPLICO A LA SALA

Que teniendo por presentado este escrito, con los documentos que acompaña, se sirva admitirlo y, en su mérito, tener por interpuesto en tiempo y forma RECURSO DE CASACIÓN contra la sentencia de fecha [FECHA], remitiéndose por el Letrado de la Administración de Justicia los autos originales a la Sala Primera del Tribunal Supremo, para que, por dicho tribunal «ad quem», previa su admisión, se dicte sentencia estimándolo, estimar el presente recurso, declarar la nulidad de actuaciones hasta el acto de la Audiencia Previa celebrado el día [FECHA], sin perjuicio del principio de conservación de los actos procesales no afectados por la nulidad. Y ello, haciendo el pronunciamiento procedente conforme a Ley sobre costas de las instancias, y sin declaración especial respecto de las del presente recurso.

OTROSI DIGO: Que estimando esta parte necesaria la celebración de vista [COMPLETAR],

SUPLICO A LA SALA

Tenga por solicitado se acuerde en su día por el tribunal «ad quem» la celebración de vista del presente recurso [COMPLETAR].

SEGUNDO OTROSÍ DIGO: Que a partir de la DA 15ª LOPJ, adjunto al presente escrito resguardo de ingreso por importe de cincuenta euros (50 euros), en la cuenta expediente número [Nº DE EXPEDIENTE] de la cuenta de depósitos y consignaciones de la Audiencia Provincial como justificación del pago del depósito como requisito necesario para la interposición del recurso de casación [COMPLETAR].

SUPLICO A LA SALA

Tenga por constituido el referido depósito a los efectos procesales oportunos.

TERCER OTROSÍ DIGO: Que de acuerdo con lo establecido en el art. 481.6 LEC, en la redacción dada por el Real Decreto-Ley 5/2023, de 28 de junio, se acompaña a este escrito copia con firma electrónica/con código seguro de verificación/certificación de la sentencia impugnada.

SUPLICO A LA SALA

Tenga por aportadas tal documentación a los efectos procesales oportunos.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) Conforme al art. 481 LEC, en la redacción dada por el Real Decreto-Ley 5/2023, de 28 de junio:

- En el escrito de interposición se identificará el cauce de acceso a la casación y, de ser este el interés casacional, se identificará asimismo la modalidad que se invoca y la justificación, con la necesaria claridad, de la concurrencia del interés casacional invocado. Además de ello, se expresará la norma procesal o sustantiva infringida, precisando, en las peticiones, la doctrina jurisprudencial que se interesa de la Sala, en su caso, y los pronunciamientos correspondientes sobre el objeto del pleito. También se podrá pedir la celebración de vista, que solo tendrá lugar si el tribunal lo considera necesario.

- El recurso de casación se articulará en motivos. No podrán acumularse en un mismo motivo infracciones diferentes.

- Solo podrán denunciarse las infracciones que sean relevantes para el fallo, siempre que hubieran sido invocadas oportunamente en el proceso o consideradas por la Audiencia Provincial.

- Cada motivo se iniciará con un encabezamiento, que contendrá la cita precisa de la norma infringida y el resumen de la infracción cometida.

- En el desarrollo de cada motivo se expondrán los fundamentos del mismo, sin apartarse del contenido esencial del encabezamiento y con la claridad expositiva necesaria para permitir la identificación del problema jurídico planteado.

(2) En el régimen legal precedente al instaurado por el Real Decreto-Ley 5/2023, los criterios de admisión de los recursos de casación y extraordinario por infracción procesal, de fecha 27 de enero de 2017, exigían que, en la justificación de los motivos de todo recurso extraordinario por infracción procesal:

2.1.- No haya una extensión excesiva, recomendando un máximo de veinticinco páginas con interlineado 1,5 y fuente Times New Roman con un tamaño de 12 puntos en el texto y de 10 puntos en las notas a pie de página o en la transcripción literal de preceptos o párrafos de sentencias que se incorporen.
2.2.- El objeto del desarrollo será la exposición razonada de la infracción o vulneración denunciada en el encabezamiento y de cómo influyó en el resultado del proceso. No podrá apartarse del contenido esencial del encabezamiento y deberá tener la razonable claridad expositiva para permitir la identificación del problema jurídico planteado y para fundamentar adecuadamente la infracción del ordenamiento jurídico alegada en relación con la norma, derecho fundamental, principio general.
2.3.- En el desarrollo de cada motivo se deberá hacer referencia exacta a las actuaciones sustanciadas en primera y segunda instancia con indicación de la resolución judicial supuestamente infractora; cuando se trate de un error fáctico, patente e inmediatamente verificable en la valoración de la prueba, se deberá indicar la prueba concreta, incluso con referencia al folio de las actuaciones o al minuto del soporte audiovisual, y exponer cómo, dónde o cuándo se ha producido el error.

========================================================================
