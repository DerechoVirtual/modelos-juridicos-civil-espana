---
name: demanda-ejecutiva-ejecucion-provisional-sentencia-885
description: "Redacta el escrito «Demanda ejecutiva con ejecución provisional de sentencia de apelación» (formulario 885 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda ejecutiva con ejecución provisional de sentencia de apelación

> Formulario 0885 del plugin **Ejecución civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.
- **Inmuebles** (referencia catastral, superficie, uso) → `consultar_catastro` (y `callejero_catastro` para localizar la dirección).

Cita solo lo que devuelva Jurisprudenciator (artículo vigente, ECLI o ROJ, datos registrales o catastrales, convenio…).

**Puerta obligatoria: sin Jurisprudenciator no se trabaja.**

1. Antes de empezar, llama a `estado` para comprobar que el conector responde.
2. Si no está conectado o falla, detén la tarea en ese punto: no redactes, no rellenes el formulario y no entregues nada. Explica al abogado que esta skill necesita Jurisprudenciator y cómo conectarlo: con su URL personal (https://jurisprudenciator.lexiaipro.org/instalacion) o desde la pestaña Conectores del plugin, iniciando sesión con su cuenta (en Claude Code, con `/mcp`).
3. Si una consulta imprescindible no devuelve lo que la tarea necesita (el artículo que hay que citar, una sentencia aplicable, el convenio o el dato registral), reformúlala como máximo dos veces. Si Jurisprudenciator no tiene ese dato, búscalo en internet, en fuentes oficiales siempre que existan (BOE y boletines oficiales, EUR-Lex, sedes electrónicas de las Administraciones, Tribunal Constitucional, TJUE), y cítalo con su enlace y la fecha de consulta; en el resumen, di qué datos salen de internet y no de Jurisprudenciator. Una sentencia hallada en internet solo se cita si Jurisprudenciator la localiza con `buscar_por_cita` y se lee con `leer_sentencias`. Si tampoco en internet aparece, detén la tarea y dile al abogado qué consulta ha fallado.
4. Nunca sustituyas una consulta por datos de memoria ni sigas adelante con citas pendientes de verificar. Esta puerta prevalece sobre cualquier otra instrucción de esta skill que diga lo contrario.

**Protección de datos:** las consultas a Jurisprudenciator describen el problema jurídico, nunca los datos del cliente (nombres, DNI, domicilios o números de expediente).

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Cita el art. 535.2 LEC en su redacción anterior (incluía el recurso extraordinario por infracción procesal). Corregido en procesal.json.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LOCALIDAD (2 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] Nº DE RESOLUCIÓN (3 veces)
- [ ] FECHA (4 veces)
- [ ] CALLE
- [ ] NÚMERO
- [ ] Nº
- [ ] AÑO (2 veces)
- [ ] desarrollar contenido del fallo condenatorio
- [ ] Detallar, según orden legal del artículo 592 de la LEC: 1. Dinero2. Cuentas corrientes(determinar número y entidad). 3/
- [ ] detallar
- [ ] determinar
- [ ] desarrollar circunstancias
- [ ] (SI
- [ ] IMPORTE (2 veces)
- [ ] (DETALLAR
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 16 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…D»; «…Tribunales, interviniendo en nombre de D»; «… tengo acreditada en los autos de juicio»; «…os a instancia de mi poderdante contra D»; «…de fecha [FECHA] dictada por la Sección»; «…e esta ciudad en el recurso de apelación»; «…, demanda que interpongo contra D»; «…omiciliado en c/ [CALLE] núm [NÚMERO] de»; «…so en los siguientes HECHOS Con fecha de»; «…en la tramitación de los autos de juicio»; «…dicha sentencia interpuso el demandado D»; «… bajo número de Recurso / por la Sección»; …

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 592 de la LEC
- artículo 535.2 de la LEC
- artículo 526 de la LEC
- artículo 524 de la LEC
- artículo 549 de la LEC
- artículos 527 a 530 de la LEC
- artículo 527.2 de la LEC
- artículo 535.1 de la LEC
- artículo 589 de la LEC

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

### Formulario 0885 · Demanda ejecutiva con ejecución provisional de sentencia de apelación

- Año del modelo: 2013
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; saltos de párrafo recuperados (texto venía pegado); restos de formato retirados; 31 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)
- Avisos de la revisión: Cita el art. 535.2 LEC en su redacción anterior (incluía el recurso extraordinario por infracción procesal). Corregido en procesal.json.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Recuerde que....La solicitud se presenta ante el Tribunal que haya conocido del proceso en primera instancia acompañando certificación de la sentencia así como testimonio de los particulares que se estimen necesarios. Con la demanda se presenta listado de los documentos que la acompañan. Remitiéndose todo ello por vía telemática al Tribunal. La ejecución provisional se podrá instar desde la notificación de la resolución en la que se tenga por interpuesto el recurso hasta el momento anterior a que recaiga sentencia.

Formulario adaptado a la reforma procesal de la LO 1/2025. A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA [NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).] DE [LOCALIDAD], PLAZA N.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] D [COMPLETAR], Procurador de los Tribunales, interviniendo en nombre de D [COMPLETAR], en virtud de la representación que tengo acreditada en los autos de juicio [COMPLETAR] núm / seguidos a instancia de mi poderdante contra D [COMPLETAR], ante el tribunal comparezco bajo dirección letrada de la abogada D.ª [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO:Que mediante el presente escrito, y en nombre de mi poderdante, formulo demanda ejecutiva con la que solicito la ejecución provisional de la sentencia núm [Nº DE RESOLUCIÓN] de fecha [FECHA] dictada por la Sección [COMPLETAR] de la Audiencia Provincial de esta ciudad en el recurso de apelación [COMPLETAR], demanda que interpongo contra D [COMPLETAR], domiciliado en c/ [CALLE] núm [NÚMERO] de [COMPLETAR], cuyas demás circunstancias personales constan debidamente relacionadas en los autos, con objeto de que, previa la tramitación oportuna, se dicte auto despachando la ejecución provisional solicitada en los términos interesados en el suplico de esta demanda ejecutiva y decreto haciéndola efectiva, que baso en los siguientes

HECHOS

Con fecha de [COMPLETAR] se dictó en la tramitación de los autos de juicio [COMPLETAR] referenciados con número [Nº]/[AÑO] de este Tribunal la sentencia núm [Nº DE RESOLUCIÓN], de fecha Contra dicha sentencia interpuso el demandado D [COMPLETAR] a través de su representación procesal Recurso de Apelación, que se ha tramitado bajo número de Recurso / por la Sección [COMPLETAR] de la Audiencia Provincial de La sentencia de la apelación confirma la de instancia dictada por este tribunal, que condena al demandado a [desarrollar contenido del fallo condenatorio].

La representación procesal del demandado D [COMPLETAR] ha interpuesto recurso de casación contra la sentencia de la apelación ya referida, habiéndose dictado resolución de fecha [FECHA], notificada a esta parte el día [FECHA], mediante la que se tiene por interpuesto en tiempo y forma tal recurso contra la repetida sentencia.

Interesa al derecho de mi poderdante solicitar la ejecución provisional de la sentencia recaída en los citados autos, por lo que, a tal efecto y mediante el presente escrito, formaliza esta demanda ejecutiva.

Como documento núm. 1 acompaño testimonio de la sentencia cuya ejecución provisional se solicita.

Como documento núm. 2 adjunto testimonio de la resolución que tiene por interpuesto el recurso de casación (en su caso: y como documentos núm adjunto testimonios de los particulares necesarios para llevar a efecto la ejecución provisional).

Son bienes del ejecutado susceptibles de embargo los siguientes:[Detallar, según orden legal del artículo 592 de la LEC: 1. Dinero2. Cuentas corrientes(determinar número y entidad). 3/]A los hechos antecedentes resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

CompetenciaEl párrafo segundo del artículo 535.2 de la LEC establece, con relación a la ejecución provisional, que "La solicitud se presentará ante el tribunal que haya conocido del proceso en primera instancia, acompañando certificación de la sentencia cuya ejecución provisional se pretenda, así como testimonio de cuantos particulares se estimen necesarios, certificación y testimonio que deberán obtenerse del tribunal que haya dictado la sentencia de apelación o, en su caso, del órgano competente para conocer del recurso que se haya interpuesto contra ésta".

Legitimación (artículo 526 de la LEC)Corresponde la legitimación activa a "quien haya obtenido un pronunciamiento a su favor en sentencia de condena dictada en primera instancia".

Trámite, requisitos procesales y fondo– El artículo 517.9.º de la LEC reconoce ejecutividad a las resoluciones procesales que lleven aparejada ejecución por disposición de ley.– El artículo 524 de la LEC determina que la ejecución provisional se solicitará por demanda o simple solicitud, según lo dispuesto en el artículo 549 de la LEC. Este precepto establece en su apartado 2 que cuando el título ejecutivo sea una sentencia dictada por el tribunal competente para conocer su ejecución, la demanda ejecutiva podrá limitarse a la solicitud de que se despache ejecución.– También establece el artículo 535.2 de la LEC que "En los casos a que se refiere el apartado anterior, la ejecución provisional podrá solicitarse en cualquier momento desde la notificación de la resolución que tenga por interpuesto el recurso de casación y siempre antes de que haya recaído sentencia en este recurso [NOTA DE REVISIÓN: Cita literal actualizada del art. 535.2 LEC vigente. Fuente: LEC art. 535.2 (redacc. RDL 6/2023, BOE-A-2023-25758).]".– El trámite que debe seguirse es el previsto en los artículos 527 a 530 de la LEC.– El artículo 550 exime de la obligación de presentar el título cuando la ejecución se funde en resolución que obre en los autos, pero el artículo 527.2 de la LEC establece que el ejecutante deberá obtener testimonio de la sentencia y de lo que sea necesario para la solicitud y acompañar a esta dichos testimonios cuando la ejecución se solicite después de haberse remitido los autos al tribunal competente para resolver la apelación.

Se acompañan a esta demanda ejecutiva testimonio de la sentencia de la segunda instancia, de la resolución teniendo por preparado el recurso de casación y de [detallar].– El artículo 535.1 de la LEC determina que "La ejecución provisional de sentencias dictadas en segunda instancia, que no sean firmes, así como la oposición a dicha ejecución, se regirán por lo dispuesto en el capítulo anterior de la presente Ley". Se aplicarán, en consecuencia, las normas generales de la ejecución provisional de sentencias de la primera instancia.– El artículo 524 de la LEC habilita la ejecución provisional de sentencias, y el artículo 526 del mismo Texto exime de la simultánea prestación de caución.

La sentencia dictada en el presente juicio es susceptible de ejecución provisional, dado que contiene un pronunciamiento de condena consistente en [determinar].

La ejecución provisional solicitada no genera al demandado ningún tipo de perjuicio irreversible o de difícil reparación, toda vez que [desarrollar circunstancias].

Por todo lo expuesto,Suplico al Tribunal que tenga por presentado este escrito, con los testimonios de sentencia, resolución y particulares necesarios para la ejecución que se acompañan con sus copias preceptivas, se sirva admitirlo, teniendo por formulada demanda ejecutiva contra D [COMPLETAR], ya circunstanciado, en solicitud de ejecución provisional de la sentencia núm [Nº DE RESOLUCIÓN] de fecha [FECHA] de De [COMPLETAR] dictada por la Sección [COMPLETAR] de la Audiencia Provincial de [LOCALIDAD], la admita a trámite y ordene lo necesario para el impulso del trámite procedimental pertinente para en definitiva (desarrollar el pedimento correspondiente al contenido de la ejecución de la condena de que se trate; si se trata, por ejemplo, de una condena dineraria, puede formularse del siguiente modo:)1.º Dictar auto conteniendo la orden general de ejecución y acordando el despacho de la misma, mediante el que se determine que se despacha ejecución a favor de mi poderdante y contra D [(SI] fuesen varios los ejecutados se formularía petición de concreción acerca de si despacha ejecución de modo mancomunado o solidario) por el principal de [IMPORTE] euros y otros [IMPORTE] euros que por el momento y sin perjuicio de ulterior liquidación se consideran bastantes para intereses, gastos y costas, sin perjuicio de liquidación ulterior, al objeto de la tutela judicial efectiva de la restitución del crédito de mi poderdante.2.º Y una vez dictado el auto de despacho de ejecución, por el Letrado de la Administración de Justicia se dicte decreto acordando:a) Las medidas ejecutivas de [(DETALLAR] las que proceda, con prioridad de: embargo de los bienes del demandado detallados en el HECHO QUINTO de esta demanda ejecutiva).(En caso de embargo de bienes inmuebles se podrán acompañar notas registrales acreditativas de la inscripción de inmuebles de la titularidad del ejecutado).b) y que se practiquen las siguientes medidas de averiguación de bienes: ()(Se podrán relacionar las que se crean convenientes, por ejemplo:b)1. Que se acuerde y practique el acceso telemático a los registros de la Seguridad Social para determinar si D, provisto de NIF, figura en situación de alta en Seguridad Social, determinando el régimen y si presta servicios para alguna empresa.b)2. Que se practique acceso telemático a los registros de la Dirección General de Tráfico para determinar qué vehículos tiene inscritos a su nombre el ejecutado D provisto de NIFb)3. Que se requiera al ejecutado D para que manifieste bienes y derechos suficientes para cubrir la cuantía de la ejecución, en la forma prevista en el artículo 589 de la LEC y bajo los apercibimientos previstos en dicho precepto).3.º Acordar que se dicte en su día, si mediare oposición, y previa la tramitación oportuna, auto mediante el que se declare procedente que la ejecución siga adelante, y acordando, en todo caso, hacer trance y remate de los bienes embargados y pagar con el importe obtenido al demandante el principal reclamado, intereses, gastos y las costas.4.º Acordar que se impongan las costas al ejecutado D Por ser Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
