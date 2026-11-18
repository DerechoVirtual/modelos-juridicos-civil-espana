---
name: demanda-ordinaria-incumplimiento-contrato-renta-1460
description: "Redacta el escrito «Demanda ordinaria por incumplimiento de contrato de renta vitalicia» (formulario 1460 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda ordinaria por incumplimiento de contrato de renta vitalicia

> Formulario 1460 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] Nº
- [ ] IMPORTE (3 veces)
- [ ] FECHA (3 veces)
- [ ] NÚMERO (4 veces)
- [ ] RDGRN de 26 de abril de 1991
- [ ] ACTO O RESOLUCIÓN
- [ ] LUGAR
- [ ] Otros 16 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, con despacho profesional en»; «…LARATIVO ORDINARIO frente a la mercantil»; «…blica otorgada ante la fe del Notario de»; «… destacar los siguientes: "SEGUNDO (...)»; «… las pensiones mensuales hasta el mes de»; «…del año»; «…ntidades correspondientes a los meses de»; «…de»; «…de [COMPLETAR] hasta»; «…de [COMPLETAR] hasta [COMPLETAR] de»; «…iante correspondencia escrita, en fechas»; «…ón en reuniones llevadas a cabo los días»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 9.2 LOPJ
- art. 45 LEC
- art. 51 LEC
- art. 7.4 LEC
- art. 10 LEC
- arts. 248 y 249.2 LEC
- art. 253.1 LEC
- art. 251 LEC
- arts. 23 y 31 LEC
- art. 399 LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 1805 CCiv
- art. 394 LEC

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

### Formulario 1460 · Demanda ordinaria por incumplimiento de contrato de renta vitalicia

- Año del modelo: 2014
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 39 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Receptor
HECHOS
FUNDAMENTOS DE DERECHO
SUPLICO AL TRIBUNAL
Firmas

Demanda de juicio declarativo ordinario sobre reclamación de rentas atrasadas y aseguramiento de rentas futuras, dimanante de un contrato de renta vitalicia.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante escritura de poder inscrito en el Registro Electrónico de Apoderamientos Judiciales, a cuya justificación aporto certificación de dicho Registro que acompaño como documento nº [Nº DE DOCUMENTO], dirigido por el Letrado abajo firmante D./Dña. [NOMBRE Y APELLIDOS], con despacho profesional en [COMPLETAR], ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que en la representación que ostento, interpongo DEMANDA DE JUICIO DECLARATIVO ORDINARIO frente a la mercantil [COMPLETAR], Sociedad Cooperativa, con domicilio en

Que esta parte asume el compromiso de recibir cualquier comunicación dirigida por la oficina judicial, durante toda la fase declarativa, e, incluso, en una eventual fase de ejecución por medios telemáticos, en términos del art. 399.1 II LEC, consignándose a estos efectos la siguiente dirección de correo electrónico y nº [Nº] de teléfono:

Fundamento la misma en los siguientes hechos y consideraciones jurídicas:

HECHOS

PRIMERO.- D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] concertaron contrato de préstamo con la entidad demandada por la que ésta recibió de los anteriores la cantidad de [IMPORTE] euros, que desembocó a fecha [FECHA] en condonación de la deuda a la cooperativa a cambio de la constitución de una renta vitalicia a medio de escritura pública otorgada ante la fe del Notario de [COMPLETAR], D./Dña. [NOMBRE Y APELLIDOS], n.º [NÚMERO] de su protocolo general corriente, que se acompaña como documento número

De entre las condiciones contenidas al constituir dicha renta vitalicia interesa ahora destacar los siguientes:

"SEGUNDO (...) [COMPLETAR], Sociedad Cooperativa se obliga en cambio a pagar a los cedentes una renta vitalicia consistente en la pensión deeuros mensuales, para cada uno de ellos, pagaderos por mensualidades vencidas en el domicilio de los pensionistas".

"CUARTO En todos los casos, la renta vitalicia será revisada anualmente, e incrementada con el Índice de Precios al Consumo".

SEGUNDO.- La sociedad demandada sólo ha satisfecho las pensiones mensuales hasta el mes de [COMPLETAR] del año [COMPLETAR], quedando a deber las cantidades correspondientes a los meses de [COMPLETAR] de [COMPLETAR] hasta [COMPLETAR] de [COMPLETAR], conforme al siguiente desglose:

TERCERO.- Previamente a la presentación de la presente solicitud, se llevaron a cabo diversos esfuerzos de negociación con la parte demandada, con el objetivo de cumplir el requisito de procedibilidad, y resolver la controversia de manera amistosa y extrajudicial. Dichas negociaciones se desarrollaron en cumplimiento de los principios de buena fe, con la intención de alcanzar una solución satisfactoria.

Entre las acciones realizadas, se incluyen el intercambio de comunicaciones formales mediante correspondencia escrita, en fechas [COMPLETAR], en las cuales esta parte expresó su disposición para dialogar y propuso alternativas de solución; así como la participación en reuniones llevadas a cabo los días [COMPLETAR], cuyos objetivos fueron buscar una conciliación respecto de las diferencias planteadas.

Se adjuntan como prueba copias de las comunicaciones enviadas y recibidas durante el proceso de negociación, incluidas cartas, correos electrónicos y/o actas de reuniones como documentos números [COMPLETAR].

Finalmente, el día [FECHA], los actores remitieron burofax a la cooperativa, requiriéndole para que procediese a efectuar la liquidación de las cantidades adeudadas con la revisión de la renta a tenor del incremento del IPC (documento número [Nº DE DOCUMENTO]).

Dicho requerimiento no ha sido atendido por la demandada lo que fuerza la interpelación judicial.

CUARTO.- Se señala a los oportunos efectos que en la actualidad, y según ha podido averiguar nuestra representada, la sociedad deudora sólo es titular de la finca registral n.º [NÚMERO], inscrita al tomo [COMPLETAR], Libro [COMPLETAR], folio [COMPLETAR], tal y como se acredita mediante el documento número [Nº DE DOCUMENTO], consistente en certificación del Registro de la Propiedad de

FUNDAMENTOS DE DERECHO

I.- JURISDICCIÓN Y COMPETENCIA.

Sobre materia de la competencia genérica del orden civil de la jurisdicción (art. 9.2 LOPJ), tiene la competencia objetiva y funcional (art. 45 LEC, en relación con lo dispuesto en el art. 85.1º LOPJ) la Sección Civil del Tribunal de Instancia, y la territorial, puesto que la entidad demandada tiene su domicilio social en el partido judicial del Tribunal al cual tengo el honor de dirigirme (art. 51 LEC).

II.- CAPACIDAD Y LEGITIMACIÓN.

Mis representados son mayores de edad y se encuentran en situación de pleno ejercicio de sus derechos civiles, en virtud de lo dispuesto en los arts. 6.1.1.º y 7.1 LEC. Asimismo, la demandada es persona jurídica, cuya capacidad se reconoce en el art. 6.1.3.º LEC, derivándose su personalidad de su constitución en escritura pública inscrita en el Registro de Sociedades Cooperativas, con la necesidad de comparecer en juicio por medio de sus representantes legales (art. 7.4 LEC).

La legitimación activa corresponde a los demandantes en su calidad de titulares del derecho a percibir las rentas atrasadas de la sociedad cooperativa demandada, que ostenta la legitimación pasiva correlativa como deudor obligado al pago (art. 10 LEC).

III.- PROCEDIMIENTO.

La presente demanda deberá sustanciarse por las normas del juicio ordinario, a tenor de lo prevenido en los arts. 248 y 249.2 LEC, toda vez que el criterio de atribución preferente de la materia objeto del proceso resulta inaplicable, al carecer de especialidad típica la de éste, y cumplir entonces el criterio de cuantía, que supera los 15.000 euros.

IV.- CUANTÍA.

Cumpliendo lo prevenido en el art. 253.1 LEC, hacemos constar que la cuantía de esta demanda es de [IMPORTE] euros ( €), importe total del principal reclamado en esta demanda, con arreglo a la regla 1.ª del art. 251 LEC.

V.- POSTULACIÓN Y DEFENSA.

Conforme a los arts. 23 y 31 LEC se formula esta demanda a través de Procurador/a de los Tribunales con poder notarial para pleitos, y con dirección y firma de Letrado habilitado ante el Tribunal. Asimismo, se cumplen los requisitos formales del art. 399 LEC.

VI.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VII.- FONDO DEL ASUNTO

1) Sobre la naturaleza del contrato suscrito por las partes.

Señala el Código Civil en el art. 1.802 el contrato de renta vitalicia, que ha sido definido como un contrato consensual, oneroso, sinalagmático y aleatorio, siendo incierto lo que durara la obligación de pagar la renta en cuanto depende de un elemento incierto, es decir el tiempo exacto que durará la vida de la persona que se toma como módulo para medir la duración de la situación jurídica de la renta sin perjuicio de no perder de vista una cierta equivalencia.

No obstante y desde el ámbito jurisprudencial se ha distinguido la renta vitalicia del contrato de vitalicio; así se determina que el contrato por el que una de las partes recibe de otro un capital o unos bienes determinados, a cambio de lo cual se obliga a darle alojamiento, manutención y toda clase de asistencia y cuidados durante toda su vida, no es la de donación o de contrato de renta vitalicia, sino el de un contrato autónomo innominado y atípico, al que se viene conociendo como contrato de vitalicio o de pensión alimenticia o de alimentos vitalicios.

El contrato de renta vitalicia, es un contrato aleatorio que no precisa de la equivalencia de prestaciones, equivalencia que implicaría convertir el contrato en conmutativo e incluso, como dice la STS de 18 de enero de 2001, rec. 3711/1995, "ir más allá pues en éstos no se exige que, siendo bilaterales, las prestaciones de cada parte sean equivalentes, pues basta el consentimiento no viciado de las partes para llegar a la perfección del contrato".

2) Sobre el incumplimiento del demandado.

Expuesto lo anterior, es obvio que se ha producido un incumplimiento del contrato suscrito por las partes que autoriza a mis representados a reclamar judicialmente al demandado las cantidades debidas como pensiones no pagadas, conforme al art. 1805 CCiv, que dispone que "la falta de pago de las pensiones vencidas no autoriza al perceptor de la renta vitalicia a exigir el reembolso del capital ni a volver a entrar en la posesión del predio enajenado; sólo tendrá derecho a reclamar judicialmente el pago de las rentas atrasadas y el aseguramiento de las futuras".

3) Sobre la actualización de las pensiones por incremento del IPC.

La actualización se pactó, si bien no se reclamó hasta que se produjo el incumplimiento. Esto no significa una renuncia a obtener la actualización en relación a las pensiones futuras, de acuerdo con las cláusulas del contrato, sino que afectará solo a las pensiones ya devengadas.

4) Sobre la obligación de garantizar el pago de las pensiones futuras.

No exige el art. 1805 CCiv que exista un pacto entre las partes que fije el tipo de garantía que debe prestarse por el deudor de las pensiones en el caso de impago de las mismas y ello con la finalidad de asegurar las pensiones futuras. La mencionada disposición contiene dos reglas: i) el impago de las pensiones vencidas no autoriza la resolución del contrato de renta vitalicia, y ii) pero sí permite reclamarlas judicialmente, además de requerir el "aseguramiento" de las rentas futuras. Por ello se ha afirmado que "el art. 1805 CCiv no implica una prohibición del pacto resolutorio, sino una previsión legal de carácter dispositivo para el caso de silencio contractual al respecto" [RDGRN de 26 de abril de 1991].

El incumplimiento del contrato de renta vitalicia, lo que permite pedir es el aseguramiento de que se trate, ya que si el acreedor de la pensión no puede pedir la resolución por incumplimiento, ante esta situación, no debe quedar a merced del deudor, exponiéndose a sucesivos y constantes incumplimientos, con las consiguientes reclamaciones.

De este modo, el art. 1805 CCiv equilibra las consecuencias del no cumplimiento del contrato, para lo cual viene a interesar esta parte se constituya hipoteca sobre la finca descrita en el hecho cuarto de la presente demanda a efectos de garantizar el pago de rentas futuras.

VIII.- INTERESES.

Arts. 1.100, 1.101 y 1.108 CCiv.

IX.- COSTAS.

Conforme al art. 394 LEC, las costas han de imponerse a la demandada.

En virtud de lo expuesto,

SUPLICO AL TRIBUNAL

que habiendo por presentado este escrito de demanda con los documentos que lo acompañan y copias de uno y otros, los admita y me tenga por comparecido en parte en la representación que ostento y que acreditada dejo; y por promovido juicio declarativo ordinario frente a [ACTO O RESOLUCIÓN], Sociedad Cooperativa, dé al mismo el curso señalado en la ley y, en su día, dicte sentencia en la que, estimando íntegramente esta demanda se efectúen los siguientes pronunciamientos:

a) Se condene a la demandada a abonar a mis representados la cantidad de [IMPORTE] euros, más la cantidad resultante de aplicar el IPC a las pensiones no satisfechas, más los intereses resultantes de la suma no abonada por incremento del IPC.
b) Se condene a la demandada a constituir hipoteca para garantizar el pago de las pensiones futuras sobre la finca de su propiedad registral n.º [NÚMERO] del Registro de la Propiedad n.º [NÚMERO] de

Y todo ello con expresa condena en costas a la parte demandada y cuanto más proceda en Derecho.

Es justicia de hacerse en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

========================================================================
