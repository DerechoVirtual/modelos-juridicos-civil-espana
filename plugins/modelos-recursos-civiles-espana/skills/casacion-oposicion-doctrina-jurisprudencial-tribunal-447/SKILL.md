---
name: casacion-oposicion-doctrina-jurisprudencial-tribunal-447
description: "Redacta el escrito «Casación por oposición a la doctrina jurisprudencial del Tribunal Supremo» (formulario 447 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Casación por oposición a la doctrina jurisprudencial del Tribunal Supremo

> Formulario 0447 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD
- [ ] Nº DE PROCEDIMIENTO (2 veces)
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] IMPORTE
- [ ] ACTO O RESOLUCIÓN
- [ ] FECHA (4 veces)
- [ ] Nº (12 veces)
- [ ] AÑO (12 veces)
- [ ] Nº DE EXPEDIENTE
- [ ] LUGAR
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…a procesal de la LO 1/2025. A LA SECCION»; «…ador de los Tribunales, en nombre de Dª.»; «…editada en los autos de juicio ordinario»; «…, por vía de omisión, al Hospital AAA de»; «… parte necesaria la celebración de vista»; «…elebración de vista del presente recurso»; «…la interposición del recurso de casación»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 477.2 LEC
- arts. 477.2 y 3 LEC
- arts. 1.902 y 1.903 del Código Civil
- artículos 1.902 y 1.903 del Código Civil
- artículo 1.902 del Código Civil
- art. 1.903 del Código Civil
- art. 481.6 LEC
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

### Formulario 0447 · Casación por oposición a la doctrina jurisprudencial del Tribunal Supremo

- Año del modelo: 2018
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; restos de formato retirados; notas del formulario agrupadas al final (2); 19 campos de relleno marcados en blanco; 13 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Interposición de recurso de casación ante la Sala Primera del Tribunal Supremo, al amparo de los artículos 477.2, primer inciso, y 477.3 LEC [NOTA DE REVISIÓN: Las modalidades de interés casacional (oposición a doctrina del TS, jurisprudencia contradictoria de AP, norma sin doctrina) están en el art. 477.3. Fuente: LEC arts. 477.1-3 (redacc. RDL 5/2023, BOE-A-2023-15135; apdo. 1 también RDL 6/2023).], cuando la resolución recurrida se oponga a doctrina jurisprudencial del Tribunal Supremo, adaptado al RDL 5/2023.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCION [COMPLETAR] DE LA AUDIENCIA PROVINCIAL DE [LOCALIDAD]

Autos nº [Nº DE PROCEDIMIENTO]

Rollo de apelación nº [Nº DE PROCEDIMIENTO]

D./Dª. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre de Dª. [COMPLETAR], cuya representación tengo debidamente acreditada en los autos de juicio ordinario [COMPLETAR], sobre reclamación de cantidad [IMPORTE], seguido a nuestra instancia contra [ACTO O RESOLUCIÓN], ante la Sala comparezco y, como mejor proceda en Derecho, DIGO:

Que, por medio del presente escrito, al amparo de lo dispuesto en el art. 477.2 LEC, en la redacción dada por el Real Decreto-Ley 5/2023, de 28 de junio, y dentro del plazo legal, interpongo en nombre de D./Dª [NOMBRE Y APELLIDOS]. RECURSO DE CASACION ante la Sala Primera del Tribunal Supremo, contra la sentencia de fecha [FECHA] dictada por esta Audiencia Provincial, en grado de apelación, y notificada en fecha [FECHA]; en los autos de juicio ordinario al margen referenciados, con arreglo a los motivos siguientes:

1.- Enumeración de los Motivos (1)

El presente recurso de casación se interpone en virtud de los siguientes motivos:

PRIMER MOTIVO

En virtud de lo dispuesto en los arts. 477.2 y 3 LEC, por interés casacional, se denuncia la oposición de la sentencia recurrida a la doctrina jurisprudencial del Tribunal Supremo y, en concreto, la emanada de sus sentencias de fecha 9 de marzo de 1998 de la Sala Primera del Tribunal Supremo, (rec. núm. [Nº]/[AÑO]), de 20 de febrero de 1992 (rec. núm. [Nº]/[AÑO]), de 22 de junio de 1992 (rec. núm. [Nº]/[AÑO]), y de fecha 22 de febrero de 1991 (rec. núm. [Nº]/[AÑO]); a la hora de la aplicación de los arts. 1.902 y 1.903 del Código Civil.

En concreto, se desestiman las pretensiones al no apreciar un reproche culpabilístico concreto, en el servicio de salud demandado, acudiendo al principio clásico de responsabilidad culposa, apartándose de la moderna interpretación jurisprudencial de tal principio, que ha evolucionado hacia una responsabilidad cuasiobjetiva, con inversión de la carga de la prueba y un acento el rigor de la diligencia requerida, según las circunstancias del caso, de manera que ha de extremarse la prudencia para evitar el daño finalmente causado.

SEGUNDO MOTIVO

2.- Justificación de los Motivos (2)

PRIMER MOTIVO

Como se ha indicado, el primer motivo que se esgrime en el presente recuso es el interés casacional dimanante de la oposición de la sentencia recurrida a la doctrina jurisprudencial del Tribunal Supremo y, en concreto, la emanada de sus sentencias de fecha 9 de marzo de 1998 de la Sala Primera del Tribunal Supremo, (rec. núm. [Nº]/[AÑO]), de 20 de febrero de 1992 (rec. núm. [Nº]/[AÑO]), de 22 de junio de 1992 (rec. núm. [Nº]/[AÑO]), y de fecha 22 de febrero de 1991 (rec. núm. [Nº]/[AÑO]); a la hora de la aplicación de los arts. 1.902 y 1.903 del Código Civil.

Por infracción, en concepto de interpretación errónea y consecuente inaplicación, de los artículos 1.902 y 1.903 del Código Civil que eran aplicables para resolver la cuestión objeto de debate, ya que la sentencia de la Audiencia declara que «las observaciones que fueron reflejando las enfermeras en la historia clínica del enfermo, vienen a demostrar la constante vigilancia, observación y atención que sobre él se mantuvo; no encontramos en los autos que se diera por parte de los profesionales de la medicina asignados al servicio, omisión de la diligencia o cuidado exigibles, falta de control del enfermo o de la debida seguridad o ignorancia del peligro que entrañaba la enfermedad diagnosticada, ni un sólo fallo en el servicio que pueda estimarse generó o facilitó la muerte del enfermo, no transgrediéndose la «lex artis» aplicable a las plantas psiquiátricas asistenciales -----», y ni la valoración del resultado probatorio, anteriormente referido, permite dichas conclusiones, pues alguna previsión o cuidado ha tenido que omitirse para que un paciente, al que se le diagnostica de «Intento de suicidio mediante inhalación de gas. Patología suicida. Depresión profunda con antecedentes de autoagresión. Marcada ansiedad», se suicide precisamente en el Centro médico en el que es ingresado para cuidarle y curarle de tales padecimientos, ni se trata en este caso de una responsabilidad esencialmente médica, sino más bien de una responsabilidad empresarial (custodia dentro de los medios de asistencia).

Como resume la sentencia de 9 de marzo de 1998 de la Sala Primera del Tribunal Supremo (rec. núm. [Nº]/[AÑO]), la aplicación del principio de responsabilidad por culpa acogido en el artículo 1.902 del Código Civil, «requiere, por regla general, la necesidad ineludible de un reproche culpabilístico al eventual responsable del resultado, y si bien es cierto que la jurisprudencia de la Sala ha ido evolucionando en el sentido de objetivar la responsabilidad extracontractual, no lo es menos que tal cambio se ha hecho moderadamente, recomendando una inversión de la carga de la prueba y acentuando el rigor de la diligencia requerida, según las circunstancias del caso, de manera que ha de extremarse la prudencia para evitar el daño, pero sin erigir el riesgo en fundamento único de la obligación de resarcir y sin excluir, en todo caso y de modo absoluto, el clásico principio de la responsabilidad culposa -----, así pues, en definitiva, la doctrina de la Sala ha ido evolucionando hacia una minoración del culpabilismo originario, hacia un sistema que, sin hacer plena abstracción del factor moral o psicológico y del juicio de valor sobre la conducta del agente, viene a aceptar soluciones cuasiobjetivas, demandadas por el incremento de las actividades peligrosas propias del desarrollo tecnológico y por el principio de ponerse a cargo de quien obtiene el beneficio o provecho, la indemnización del quebranto sufrido por el tercero, habiéndose producido el acercamiento a la responsabilidad por riesgo, en una mayor medida, en los supuestos de resultados dañosos originados en el ámbito de la circulación de vehículo de motor».

La doctrina del Tribunal Supremo matiza esos criterios generales apuntados cuando se trata de supuestos de exigencia de responsabilidad a profesionales médicos o sanitarios, declarando la sentencia de 20 de febrero de 1992 que «en la conducta de los profesionales sanitarios queda, en general, descartada toda clase de responsabilidad más o menos objetiva; y finalmente, tampoco en estos casos opera la inversión de la carga de la prueba, admitida para otros supuestos, quedando, por tanto, a cargo del paciente la prueba de la relación o nexo causal, así como la de la culpa, pues a la pura relación material o física ha de sumársele el reproche culpabilístico (sentencias de 13-7-87; 12-7-88; 7-2, 12-2 y 6-11-90, etc.)».

A su vez, sobre la responsabilidad empresarial (empresa médica, clínica, hospital, etc.), que es la exigida en este caso, tiene declarado la Sala Primera del Tribunal Supremo que «el art. 1.902 es directamente aplicable a las personas jurídicas, cualquiera que sea la persona singular a través de la cual actúen, encomendándole el trabajo, sin asegurarse de los riesgos que efectivamente puedan surgir» (Sentencia de 22 de junio de 1992 (rec. núm. [Nº]/[AÑO]), que «----- la responsabilidad derivada del art. 1.903 del Código Civil es una responsabilidad directa no subsidiaria, que puede ser directamente exigida al empresario por su propia culpa «in vigilando» o «in eligendo» y con independencia de la clase de responsabilidad en que haya incurrido el autor material del hecho -----» (Sentencia de 22 de febrero de 1991 (rec. núm. [Nº]/[AÑO]), y que «----- la posible responsabilidad a imputar a los Centros hospitalarios por la vía indicada, tendría que ser indagada a través de las medidas de seguridad, control y vigilancia adoptadas, para cada caso concreto, en definitiva, por culpa in eligendo o in vigilando, es decir, exigiéndoles, desde el punto de vista de organización de los servicios, una individualización en la adopción de las medidas o medios materiales y personales en orden al caso particular de que se trate» (Sentencia, ya antes citada, de 9 de marzo de 1998 (rec. núm. [Nº]/[AÑO]).

En el caso de autos es claro que no sería exigible una responsabilidad culposa al personal médico propiamente dicho, que actuó correctamente, mediante la inmovilización del enfermo durante cierto tiempo y la administración de fármacos para calmarle, lo que se logró, cuando menos aparentemente, y advirtió en todo momento de la necesaria vigilancia del paciente por su acusado riesgo de suicidio, sino que la responsabilidad se desvía a las medidas adoptadas, en el caso concreto, para prever las consecuencias de tal riesgo, pues ante el ingreso de un paciente por enfermedad psiquiátrica, el centro hospitalario no solo estará obligado a prestarle la asistencia médica, farmacológica o asistencial necesaria para curarle o disminuir su padecimiento, sino también a poner en juego todos los medios humanos y materiales necesarios, de seguridad y vigilancia, para evitar cualquier daño que pueda originarse a sí mismo, suceso éste perfectamente previsible, dadas las reacciones propias de estas enfermedades, y máxime en paciente diagnosticado de tendencia al suicidio.

Lo cierto es que en el presente supuesto faltaron los mecanismos de vigilancia y custodia a tener en cuenta, pues para ello, como bien puso de relieve la sentencia del Tribunal de Instancia, hubiese sido preciso que la habitación en que quedó instalado el Sr./Sra. no permitiera el acceso a las plantas altas del edificio desde las que poder consumar sus advertidas ideas suicidas y de autodestrucción, o bien haber procedido al traslado del enfermo a otra dependencia desde que se prescindió de su sujeción, con el que se hubiera evitando aquel riesgo previsible. Y es evidente que la carencia de tales precauciones ha de ser atribuida, finalmente, por vía de omisión, al Hospital AAA de [COMPLETAR] y, por ende, al demandado Insalud, cuya responsabilidad deviene de las tres culpas que aquella sentencia de primera instancia oportunamente le imputó: «in vigilando», «in eligendo» e «in organizando», y como dicha negligencia fue causa directa y eficiente del desgraciado resultado, no cabía sino declarar la responsabilidad del Insalud a tenor de lo establecido en los artículos 1.902 y 1.903 del Código Civil.

No habiéndolo entendido así la sentencia recurrida, ha de estimarse que la misma ha infringido, por el concepto de violación por inaplicación, ambos preceptos reguladores de la culpa extracontractual.

SEGUNDO MOTIVO

Por todo lo expuesto,

SUPLICO A LA SALA

Que teniendo por presentado este escrito, con los documentos que acompaña, se sirva admitirlo y, en su mérito, tener por interpuesto en tiempo y forma RECURSO DE CASACION contra la sentencia de fecha [FECHA], remitiéndose por el Letrado de la Administración de Justicia los autos originales a la Sala Primera del Tribunal Supremo, para que, por dicho tribunal «ad quem», previa su admisión, se dicte sentencia estimándolo, casando la sentencia recurrida y, recuperando la instancia, estimando íntegramente la demanda formulada por Don/Doña [NOMBRE Y APELLIDOS] contra el Insalud, condenándole a abonar a la actora la cantidad de doscientos cuarenta mil euros, con sus intereses legales, haciendo el pronunciamiento procedente conforme a Ley sobre costas de las instancias, y sin declaración especial respecto de las del presente recurso.

OTROSI DIGO: Que estimando esta parte necesaria la celebración de vista [COMPLETAR],

SUPLICO A LA SALA: Tenga por solicitado se acuerde en su día por el tribunal «ad quem» la celebración de vista del presente recurso [COMPLETAR].

SEGUNDO OTROSÍ DIGO: Que a partir de la DA 15ª LOPJ, adjunto al presente escrito resguardo de ingreso por importe de cincuenta euros (50 euros), en la cuenta expediente número [Nº DE EXPEDIENTE] de la cuenta de depósitos y consignaciones de la Audiencia Provincial como justificación del pago del depósito como requisito necesario para la interposición del recurso de casación [COMPLETAR].

SUPLICO A LA SALA

Tenga por constituido el referido depósito a los efectos procesales oportunos.

TERCERO OTROSÍ DIGO: Que de acuerdo con lo establecido en el art. 481.6 LEC, en la redacción dada por el Real Decreto-Ley 5/2023, de 28 de junio, se acompaña a este escrito copia con firma electrónica/con código seguro de verificación/certificación de la sentencia impugnada.

SUPLICO A LA SALA

Tenga por aportadas tal documentación a los efectos procesales oportunos.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) Breve resumen del motivo

(2) Desarrollo del motivo

========================================================================
