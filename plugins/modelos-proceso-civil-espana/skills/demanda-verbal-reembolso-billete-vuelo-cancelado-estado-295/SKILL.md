---
name: demanda-verbal-reembolso-billete-vuelo-cancelado-estado-295
description: "Redacta el escrito «Demanda verbal de reembolso del billete por vuelo cancelado en estado de alarma» (formulario 295 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda verbal de reembolso del billete por vuelo cancelado en estado de alarma

> Formulario 0295 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.

Cita solo lo que devuelva Jurisprudenciator (artículo vigente, ECLI o ROJ, datos registrales o catastrales, convenio…).

**Puerta obligatoria: sin Jurisprudenciator no se trabaja.**

1. Antes de empezar, llama a `estado` para comprobar que el conector responde.
2. Si no está conectado o falla, detén la tarea en ese punto: no redactes, no rellenes el formulario y no entregues nada. Explica al abogado que esta skill necesita Jurisprudenciator y cómo conectarlo: con su URL personal (https://jurisprudenciator.lexiaipro.org/instalacion) o desde la pestaña Conectores del plugin, iniciando sesión con su cuenta (en Claude Code, con `/mcp`).
3. Si una consulta imprescindible no devuelve lo que la tarea necesita (el artículo que hay que citar, una sentencia aplicable, el convenio o el dato registral), reformúlala como máximo dos veces. Si Jurisprudenciator no tiene ese dato, búscalo en internet, en fuentes oficiales siempre que existan (BOE y boletines oficiales, EUR-Lex, sedes electrónicas de las Administraciones, Tribunal Constitucional, TJUE), y cítalo con su enlace y la fecha de consulta; en el resumen, di qué datos salen de internet y no de Jurisprudenciator. Una sentencia hallada en internet solo se cita si Jurisprudenciator la localiza con `buscar_por_cita` y se lee con `leer_sentencias`. Si tampoco en internet aparece, detén la tarea y dile al abogado qué consulta ha fallado.
4. Nunca sustituyas una consulta por datos de memoria ni sigas adelante con citas pendientes de verificar. Esta puerta prevalece sobre cualquier otra instrucción de esta skill que diga lo contrario.

**Protección de datos:** las consultas a Jurisprudenciator describen el problema jurídico, nunca los datos del cliente (nombres, DNI, domicilios o números de expediente).

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] CALLE
- [ ] LOCALIDAD
- [ ] FECHA (5 veces)
- [ ] Nº (2 veces)
- [ ] HORA
- [ ] IMPORTE (4 veces)
- [ ] CORREO ELECTRÓNICO
- [ ] ACTO O RESOLUCIÓN
- [ ] LUGAR (2 veces)
- [ ] DÍA (2 veces)
- [ ] MES (2 veces)
- [ ] AÑO (2 veces)
- [ ] Otros 32 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Q.P.T.R.C. Doña»; «…Q.P.T.R.C. Doña [COMPLETAR] y Don»; «…, provistos de D.N.I. y D.N.I.»; «…, vecinos de»; «…, y con teléfono de contacto»; «…ontractual (1), contra la compañía aérea»; «…to jurídicos: HECHOS PRIMERO.- Dña. y D.»; «…, a través de»; «…dos vuelos para viajar de»; «…dos vuelos para viajar de [COMPLETAR] a»; «…, de ida y vuelta, con la compañía»; «… En concreto se contrató la salida desde»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 87.6.a) LOPJ
- art. 51.1 LEC
- arts. 248.3 y 250.2 LEC
- arts. 7.1 y 4 LEC
- art. 10 LEC
- art. 253.1 LEC
- art. 8 TRLGDCU
- art. 1.104 CCiv
- artículos 1.100 y 1.108 CCiv
- art. 394.1 LEC
- art. 265 LEC

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

### Formulario 0295 · Demanda verbal de reembolso del billete por vuelo cancelado en estado de alarma

- Año del modelo: 2020
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 51 campos de relleno marcados en blanco
- Avisos de la revisión: REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda de juicio verbal sobre reclamación de cantidad por reembolso del precio del billete por cancelación de vuelo en estado de alarma, interpuesta directamente por los perjudicados.

Adaptado a la LO 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

Doña [COMPLETAR] y Don [COMPLETAR], provistos de D.N.I. y D.N.I. [COMPLETAR], vecinos de [COMPLETAR], con domicilio a efecto de domiciliaciones en calle [CALLE], y con teléfono de contacto [COMPLETAR]; ante el Tribunal comparecen y como mejor proceda en Derecho, DICEN:

Que por medio del presente escrito, venimos a deducir DEMANDA DE JUICIO VERBAL, en ejercicio de acción de resarcimiento por incumplimiento contractual (1), contra la compañía aérea [COMPLETAR] SA, con domicilio en [LOCALIDAD]; con fundamento en los siguientes datos y razonamiento jurídicos:

HECHOS

PRIMERO.- Dña. y D. [COMPLETAR], a través de [COMPLETAR], contrataron en fecha [FECHA] dos vuelos para viajar de [COMPLETAR] a [COMPLETAR], de ida y vuelta, con la compañía [COMPLETAR], con objeto de disfrutar de un periodo vacacional. En concreto se contrató la salida desde [COMPLETAR], el día [FECHA] a las [Nº] horas, y la vuelta desde [COMPLETAR], el día [FECHA], a las [HORA]. Todo ello, con el Código de Reserva [COMPLETAR]. El precio total de los vuelos ascendió a la cantidad de [IMPORTE] euros. Se acompaña copia de la reserva y del pago efectuado de los billetes como documento nº 1.

SEGUNDO.- El vuelo fue cancelado por la compañía demanda unilateralmente, sin que se comunicara a los demandantes por medio alguno, a pesar de disponer la compañía aérea de sus correos electrónicos. A pesar de tal circunstancia se dieron cuenta de la cancelación operada a través de la página web de [COMPLETAR]. Como consecuencia de ello, iniciaron un cruce de correos electrónicos para la reclamación del precio abonado de la siguiente forma:

1.- El [COMPLETAR], se reclamó el reembolso del precio mediante el correo electrónico en el que se decía: "".
2.- Dicho correo fue contestado por la demandada el [COMPLETAR], pidiendo una serie de datos y redireccionando al correo electrónico [CORREO ELECTRÓNICO]. En la contestación se decía: "".
3.- El [COMPLETAR] las demandantes aportaron los datos exigidos, e insistieron en que optaban por el reembolso del precio, con la indicación de que no tenían previsto ningún otro vuelo a corto medio plazo similar.
4.- El [COMPLETAR] la Compañía aérea contestó que se ofrecía un cupón para poder volar en un vuelo de las mismas condiciones, válido hasta el [FECHA]. Se añadía que no era posible procesar reembolso alguno.

Se acompañan copias de todos los correos electrónicos como bloque documental nº 2, designando expresamente los archivos de la demandada para el caso de que los correos electrónicos indicados sean negados de adverso o impugnado el valor probatorio del documento. En este sentido, entre otras, la Audiencia Provincial de Barcelona -15ª- en Sentencia de 6 de febrero de 2012, rec. 520/2011, según la cual "A la hora de probar la duración del retraso no podemos reconocer la facilidad probatoria en la posición del pasajero, ni su proximidad a las fuentes de prueba, pues no recibe de la compañía aérea ningún documento que certifique o indique la hora real en la que el vuelo llega a su destino. Es la compañía aérea, como indica la sentencia apelada, la que está en condiciones de acreditar la hora de llegada del vuelo contratado al destino final y las demás circunstancias horarias y materiales que explican el retraso." Extremo aplicable a las comunicaciones mantenidas por las partes, cuya realidad se trata de acreditar.

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA.

El art. art. 87.6.a) LOPJ determina la competencia objetiva y funcional de las Secciones de lo Mercantil de los Tribunales de Instancia, para conocer en primera instancia de las reclamaciones en materia de transporte.

Asimismo, el art. 51.1 LEC fija que la competencia territorial en juicio en que se ejerciten pretensiones frente a personas jurídicas es del Tribunal del lugar donde nació la relación jurídica del viaje contratado; en este caso, el domicilio de los demandantes, desde donde se contrató el vuelo por Internet. Domicilio que, asimismo, coincide con el partido judicial en el que además, la compañía demandada tiene establecimiento abierto al público con representante autorizado en el aeropuerto de [COMPLETAR].

II.- PROCEDIMIENTO.

En aplicación de los arts. 248.3 y 250.2 LEC, y en atención a la cuantía del objeto litigioso, este pleito se tramitará por las normas de proceso declarativo llamado Juicio Verbal.

III.- CAPACIDAD.

Conforme al art. 6.1.1º LEC tienen capacidad para ser parte las personas físicas, y las jurídicas, como las sociedades mercantiles, conforme al art. 6.1.3º LEC. Asimismo, a tenor de los arts. 7.1 y 4 LEC detentan capacidad de obrar procesal las personas físicas, en tanto que son mayores de edad sin discapacidad, y las sociedades, a través de quienes legalmente les representen, respectivamente.

IV.- LEGITIMACIÓN.

El art. 10 LEC legitima para comparecer y actuar en juicio a los titulares de la relación jurídica o del objeto litigioso. En el caso de autos, demandantes y entidad demandada son los sujetos titulares de los derechos de crédito y correlativas obligaciones de un contrato de transporte, estando legitimados activamente los viajeros como titulares del derecho de resarcimiento por incumplimiento o morosidad en la prestación de la empresa porteadora, que por ello se legitima pasivamente.

V.- POSTULACIÓN.

En aplicación de los arts. 23.2.1º y 31.2.1º LEC, y en atención a la cuantía que se reclaman, las partes están excusadas de comparecer representadas por Procurador de los Tribunales y asistidas por Letrado en ejercicio, informando que los demandantes acudirán al acto del juicio por sí solos.

VI.- CUANTÍA.

Cumpliendo la exigencia del art. 253.1 LEC, se cifra la cuantía de la demanda en la cantidad de [IMPORTE] euros, principal a cuya condena de pago se peticiona (art. 251.1ª LEC).

VII.- FONDO DEL ASUNTO.

1.- Del incumplimiento contractual:

En el presente caso las partes estaban ligadas por un contrato de transporte, mediante el cual la compañía aérea debía trasladar a los demandantes del aeropuerto de [COMPLETAR] al de [COMPLETAR] el [COMPLETAR], y volver a trasladarlas desde [COMPLETAR] a [COMPLETAR] el [COMPLETAR], cuando finalizara el periodo vacacional del que querían disfrutar. La demandada canceló unilateralmente los vuelos contratados, sin ni siquiera avisar personalmente a los demandantes.

En este sentido, se trata de un contrato de empresa, que compromete, no una actividad diligente de la porteadora, sino a un resultado cierto. Los medios de transporte son variados, y entre ellos, el avión, tal y como se difunde entre consumidores y usuarios (art. 8 TRLGDCU), conlleva las máximas ventajas en el plano de la rapidez y seguridad, convirtiéndose en el medio adecuado para trasladarse entre [COMPLETAR] y [COMPLETAR] de cara a disfrutar de unas vacaciones. Cuando el vuelo se cancela, independientemente del marco en el que se produce, hay un incumplimiento radical de la esencia de la prestación recíproca de la porteadora aérea, en términos del art. 1.104 CCiv.

2.- Del derecho al reembolso del precio abonado:

En caso de cancelación del vuelo, según el Reglamento 261/2004 del Parlamento Europeo y del Consejo, de 11 de febrero 2004, los derechos del pasajero incluyen, en virtud de sus arts. 5 y 8, el derecho a optar entre el reembolso o un transporte alternativo. Es decir, el legislador ha configurado una opción legal del viajero, en este caso los demandantes, que en ningún modo puede ser dispuesto o sustituido por la voluntad de la Compañía aérea. Extremo que se está pretendiendo por la aquí demandada, tal y como se desprende de su último correo electrónico.

En este sentido, el referido art. 8 expresa que "Cuando se haga referencia a este artículo, se ofrecerán a los pasajeros las opciones siguientes:

a) - el reembolso en siete días, según las modalidades del apartado 3 del artículo 7, del coste íntegro del billete en el precio al que se compró, correspondiente a la parte o partes del viaje no efectuadas y a la parte o partes del viaje efectuadas, si el vuelo ya no tiene razón de ser en relación con el plan de viaje inicial del pasajero, junto con [COMPLETAR], cuando proceda:- un vuelo de vuelta al primer punto de partida lo más rápidamente posible;
b) la conducción hasta el destino final en condiciones de transporte comparables, lo más rápidamente posible, o
c) la conducción hasta el destino final, en condiciones de transporte comparables, en una fecha posterior que convenga al pasajero, en función de los asientos disponibles".

Los demandantes optaron con toda claridad por el reembolso del precio abonado, desde el momento en el cual tuvieron conocimiento de la cancelación operada. Así lo dejaron claro en los dos correos electrónicos enviados a la Compañía. En ningún caso puede pretenderse, tal y como insinúa la demandada en su última contestación, que no es posible el pago del precio de los billetes. Es su obligación legal, de la que tiene perfecto conocimiento al ser el tráfico aéreo su actividad esencial. Por ello, debe entenderse que la compañía aérea demandada debe responder de los perjuicios irrogados a los demandantes como consecuencia del incumplimiento contractual en el viaje de vuelta, que se cuantifican, en este caso, en el reembolso de la cantidad abonada, en cuantía de [IMPORTE] euros.

VIII.- INTERESES LEGALES.

Al principal al que se condene, deben añadirse, según los artículos 1.100 y 1.108 CCiv, intereses legales de la cantidad reclamada desde la fecha de la primera reclamación extrajudicial, [COMPLETAR].

IX.- COSTAS.

Las costas del juicio deberán serle impuestas a la parte demandada, puesto que se deberá producir su íntegro vencimiento, con arreglo a lo que previene el art. 394.1 LEC para los declarativos en primera instancia.

Por lo expuesto,

SUPLICO AL TRIBUNAL que, teniendo por presentado este escrito, lo admita, tenga por comparecidos y parte demandante a Doña [COMPLETAR] y Don [COMPLETAR], y por deducida demanda de Juicio Verbal en reclamación de cantidad contra [ACTO O RESOLUCIÓN], la cual deberá ser citada para la vista, a fin de que se dicte en su día Sentencia por la que, estimando íntegramente la demanda, condene a la mercantil demandada a que indemnice a las demandantes en la cantidad de [IMPORTE] euros, intereses legales desde el [FECHA], y al reintegro de las costas procesales, si las hubiere.

Es Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

OTROSI PRIMERO DIGO que a efectos probatorios, conforme a lo dispuesto en el art. 265 LEC, designo los archivos de LUFTHANSA SA, así como de cualquier otra entidad pública o privada que haya sido mencionada en el presente escrito así como aquellas que pudieran resultar o disponer de documentación relevante para la presente Litis.

Por lo que,

SUPLICO AL TRIBUNAL: Que tenga por realizada la antedicha designación a los efectos probatorios oportunos, en el mismo lugar y fecha.

OTROSI SEGUNDO DIGO que esta parte asume el compromiso de recibir cualquier comunicación dirigida por la oficina judicial, durante toda la fase declarativa, e, incluso, en una eventual fase de ejecución por medios telemáticos, en términos del art. 399.1 II en relación al art. 437.1, ambos LEC, consignándose a estos efectos la siguiente dirección de correo electrónico y nº [Nº] de teléfono:

Por lo expuesto,

AL TRIBUNAL NUEVAMENTE SUPLICO que, teniendo por hecha la afirmación anterior, se admita y provea en consecuencia.

Es justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de las demandantes

NOTAS DEL FORMULARIO

(1) La presente demanda se elabora para las cancelaciones de vuelos realizadas en el marco del Estado de Alarma. En estos supuestos, al concurrir una evidente causa de fuerza mayor, no pueden reclamarse las indemnizaciones previstas en el Reglamento, previstas en otros formularios. Pero sí puede optarse por el reembolso del precio abonado, al existir una opción legal para el viajero a la hora de decidir entre que le devuelvan lo pagado, o utilizar otro billete si le viniera bien a él (no a la Compañía aérea).
