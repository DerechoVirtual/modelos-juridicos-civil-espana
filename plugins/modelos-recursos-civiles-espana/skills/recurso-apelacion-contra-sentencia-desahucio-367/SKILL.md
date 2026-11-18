---
name: recurso-apelacion-contra-sentencia-desahucio-367
description: "Redacta el escrito «Recurso de apelación contra sentencia de desahucio» (formulario 367 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Recurso de apelación contra sentencia de desahucio

> Formulario 0367 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] NÚMERO
- [ ] Nº DE COLEGIADO/A
- [ ] COLEGIO
- [ ] FECHA (7 veces)
- [ ] LOCALIDAD
- [ ] IMPORTE
- [ ] LUGAR
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…CIÓN CIVIL DE LA AUDIENCIA PROVINCIAL DE»; «… el demandado las rentas de los meses de»; «…e constata el incumplimiento del pago de»; «… la demanda; este burofax tiene fecha de»; «…ndose al requerimiento del art. 22.4 LEC»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 458.1 LEC
- art. 458.2 LEC
- art. 458.1 y 3 LEC
- art. 448.1 LEC
- arts. 23.1 y 31.1 LEC
- art. 22.4 LEC
- artículo 22.4 LEC
- artículo 1258 CC
- arts. 394 y 398 LEC
- art. 276 LEC

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

### Formulario 0367 · Recurso de apelación contra sentencia de desahucio

- Año del modelo: 2019
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 22 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de interposición de recurso de apelación contra sentencia desestimatoria de juicio verbal de desahucio por falta de pago, fundado en la improcedencia de la enervación de la acción.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DE LA AUDIENCIA PROVINCIAL DE [COMPLETAR]

[NOTA DE REVISIÓN (comprobar): La AP no tiene «Sección Civil» como denominación legal: se cita la Sección por su número (p. ej. «A LA SECCIÓN [ ] DE LA AUDIENCIA PROVINCIAL DE [ ]»). Fuente: LOPJ arts. 80 y 82 (Audiencia Provincial, sin cambio de denominación).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en nombre de D./Dña. [NOMBRE Y APELLIDOS], cuya representación tengo acreditada en los autos de juicio verbal de desahucio seguidos con el nº [NÚMERO], contra D./Dña. [NOMBRE Y APELLIDOS], ante la Sala comparezco, con la asistencia del Letrado D./Dña. [NOMBRE Y APELLIDOS], colegiado nº [Nº DE COLEGIADO/A] del Ilustre Colegio de Abogados de [COLEGIO], y como mejor proceda en derecho DIGO:

Que el pasado día [FECHA] se me ha notificado la resolución de fecha [FECHA], recaída en las presentes actuaciones, y estimando la misma gravosa para los intereses de mi mandante, dicho sea en términos de defensa, dentro del plazo de veinte días legalmente establecido en el art. 458.1 LEC, INTERPONGO RECURSO DE APELACIÓN contra dicha resolución, lo que hago por medio del presente escrito en el que expongo los siguientes:

REQUISITOS PROCESALES

I.- Se presenta este escrito de interposición ante ese Tribunal, que es el competente para conocer del recurso, con arreglo al art. 458.1 LEC.

La sentencia es impugnada en todos sus pronunciamientos, en cuanto que ha desestimado íntegramente lo pretendido en nuestra demanda (art. 458.2 LEC).

II.- Se presenta este escrito de interposición dentro del plazo de veinte días contados desde el día siguiente a la notificación de la resolución impugnada (art. 458.1 y 3 LEC).

III.- Esta parte se halla legitimada por afectarle desfavorablemente la resolución impugnada, conforme exige el art. 448.1 LEC.

IV.- Las exigencias de postulación se llenan para este escrito de interposición, ya que está comparecida esta parte mediante Procurador de los Tribunales, y asistida de abogado en ejercicio, ambos colegiados y habilitados para ejercer ante el Tribunal (arts. 23.1 y 31.1 LEC).

FUNDAMENTOS DEL RECURSO

PRIMERO.- En cuanto al fondo, infracción del art. 22.4 LEC, por improcedencia de la enervación de la acción de desahucio.

Mediante la demanda origen del presente procedimiento mi representado ejercitó una acción de desahucio por falta de pago de rentas y reclamación de rentas vencidas contra D./Dña. [NOMBRE Y APELLIDOS].

La demanda se sustentaba en que las partes suscribieron un contrato de arrendamiento con fecha [FECHA] sobre la vivienda sita en [LOCALIDAD], adeudando el demandado las rentas de los meses de [COMPLETAR], por lo que con indicación de no ser posible la enervación por haberse requerido de pago al demandado e interponerse la demanda 30 días después del requerimiento se solicitaba la resolución del contrato con condena al demandado al pago de la cantidad de [IMPORTE] euros, una vez descontadas las cantidades entregadas como depósito y fianza, además de las rentas y cantidades asimiladas que se devenguen con posterioridad a la demanda hasta la entrega efectiva de la finca.

El demandado presentó escrito manifestando haber abonado todas las cantidades reclamadas y las sucesivas, así como que el requerimiento mediante burofax no le fue entregado por lo que no tuvo conocimiento del mismo, por lo que pidió la desestimación de la demanda.

El Juez de instancia dictó sentencia en la que considera que concurrían las circunstancias establecidas en el art. 22.4 LEC para declarar enervada la acción, entendiendo que el requerimiento de pago al demandado mediante burofax que el mismo no recogió permite la mencionada enervación, estándose ante un retraso puntual en el pago que no habría de dar lugar a la resolución del contrato, por lo que desestima íntegramente la demanda.

Lo cierto es que la enervación de la acción es la cuestión que ha de resolverse ahora y que la misma sentencia de instancia aborda al valorar lo dispuesto en el art. 22.4 LEC, siendo así que el demandado pretendería no proceder la acción resolutoria al haber abonado las rentas reclamadas antes de haber sido requerido de pago y de conocer la demanda contra él interpuesta, estándose ante un mero retraso no reproducido.

Pues bien, con carácter general ha de recordarse que de acuerdo con una reiterada y constante jurisprudencia del Tribunal Supremo, en el desahucio por falta de pago de la renta no cabe hablar de "mero retraso en el pago" y no es necesario que concurra un especial ánimo de incumplir ni es exigible para que concurra la causa resolutoria la existencia de una voluntad contumaz o deliberadamente rebelde al pago del arrendatario, bastando el hecho objetivo de que no se haya procedido al pago de la renta en el plazo legal o contractualmente pactado, sin que el pago total de la renta del arrendamiento de una vivienda, fuera de plazo y después de presentada la demanda de desahucio, excluya la posibilidad de la resolución arrendaticia, o en su caso de declarar enervada la acción de desahucio, aunque la demanda se funde en el impago de una sola mensualidad de la renta, y sin que el arrendador venga obligado a soportar que el arrendatario se retrase de ordinario en el abono de las rentas periódicas (SSTS de 24 de julio de 2008, Rec. 508/2002, 19 de diciembre de 2008, Rec. 648/2004, 26 de marzo de 2009, Rec. 1507/2004, 20 de octubre de 2009, Rec. 1559/2004, 30 de octubre de 2009, Rec. 2629/2004 y 27 de marzo de 2014, Rec. 141/2011), teniéndose en cuenta que como señala la STS de 26 de marzo de 2009, Rec. 1507/2004, la enervación del desahucio no se configura tanto como un derecho cuanto como una oportunidad del arrendatario para evitar el desahucio por falta de pago, porque al arrendador no le es indiferente el momento en que se le pague la renta estipulada, postura que ha reiterado el Alto Tribunal en sentencias de 28 de mayo de 2014, Rec. 1051/2012 y 22 de septiembre de 2015, Rec. 1818/2013.

En el presente supuesto la demanda se interpone con fecha [FECHA] y el pago de las rentas y otras cantidades adeudadas por el arrendatario tiene lugar con fecha [FECHA], por tanto después de interpuesta la demanda, de modo que se constata el incumplimiento del pago de [COMPLETAR] mensualidades consecutivas de rentas y de una pequeña parte de una mensualidad más.

En estas condiciones solo la enervación de la acción permitiría el mantenimiento del contrato, y esta cuestión pretende ser eludida por el demandado sobre la base de negar haber recibido el requerimiento fehaciente de pago que prevé la ley al rechazar haber recibido el burofax acompañado con la demanda; este burofax tiene fecha de [COMPLETAR] y contiene un claro requerimiento de pago de las cantidades adeudadas y luego abonadas.

La STS de 13 de octubre de 2015, Rec. 2117/2013 -señala:

"...sobre la interpretación del art. 22.4 LEC y de los requisitos del requerimiento de pago contemplado en el mismo al objeto de impedir la enervación de la acción en el procedimiento de desahucio, esta Sala ya se pronunció en su sentencia de 28 de mayo de 2014, rec. 1051/2012, desestimatoria de un recurso extraordinario por infracción procesal y de un recurso de casación por interés casacional, en su modalidad de jurisprudencia contradictoria de las Audiencias Provinciales, interpuestos contra una sentencia que había acordado la resolución de un arrendamiento precisamente por falta de pago del IBI, y en la que, refiriéndose al requerimiento del art. 22.4 LEC [COMPLETAR], esta Sala declaró lo siguiente:

«1 . La comunicación ha de contener un requerimiento de pago de renta o cantidad asimilada.
2. Ha de ser fehaciente, es decir, por medio que permita acreditar que llegó a conocimiento del arrendatario, con la claridad suficiente.
3. Ha de referirse a rentas impagadas.
4. Debe transcurrir el plazo legalmente previsto, que ha venido fluctuando entre uno y dos meses, en las sucesivas reformas legales.
5. Que el arrendatario no haya puesto a disposición del arrendador la cantidad reclamada.

Sin embargo, en dicho precepto no se exige que se comunique al arrendatario:

1. Que el contrato va a ser resuelto.
2. Que no procederá enervación de la acción de desahucio si no se paga en el plazo preceptivo.

El legislador no obliga al arrendador a que se constituya en asesor del arrendatario, sino tan solo a que le requiera de pago».

Posteriormente, la STS de 23 de junio de 2014, Rec. 1437/2013, resolutoria de un recurso de casación por interés casacional en la misma modalidad de jurisprudencia contradictoria de las Audiencias Provinciales, casó la sentencia recurrida y, en consecuencia, realizó el siguiente pronunciamiento: «2.- Se fija como doctrina jurisprudencial, la siguiente: "el requerimiento de pago que se hace al amparo artículo 22 de la Ley de Enjuiciamiento Civil, no exige que se comunique al arrendatario que el contrato va a ser resuelto y que no procederá enervación de la acción de desahucio si no se paga en el plazo preceptivo"».

De modo que en el caso enjuiciado el requerimiento efectuado cumple las previsiones del artículo 22.4 LEC y se ve avalado por los correos electrónicos aportados por la actora y que justifican en el criterio de la Sala las conversaciones habidas para el pago de lo adeudado, siendo la única cuestión objeto de discusión ahora el hecho de que el burofax en cuestión no habría sido entregado al demandado al dejarse aviso del mismo y no ser recogido.

Sobre esta cuestión ha habido diferentes pronunciamientos judiciales. Así, aborda esta problemática la sentencia de la Audiencia Provincial de Pontevedra de fecha 27 de mayo de 2013, Rec. 31/2012, "No hay duda alguna acerca de la corrección de la dirección a que fue enviado el burofax (efectivo domicilio del demandado) por lo que, a salvo de mejor prueba, hemos de entender que sólo al demandado cabe imputar la no recepción efectiva de la comunicación en la que se señala que "Hay que establecer como principio general que ambas partes contratantes han de adecuar su conducta a las exigencias de la buena fe, según dispone el artículo 1258 CC. En el presente proceso resulta probado, como antes se ha dicho, que se cursó el burofax por el que se requería al arrendatario el pago de la renta adeudada con el apercibimiento en caso de no abonar las mismas de ejercitar las acciones legales pertinentes y que al no poder ser entregado fue dejado aviso al destinatario a fin de que pasara a recogerlo por el servicio de Correos. No se discute por la parte recurrente que no se haya recibido ese aviso, debiendo además partir de una presunción de normalidad de funcionamiento del servicio de Correos, por lo que cuando se aporta la comunicación de este servicio de que el destinatario de la comunicación estaba ausente y se le ha dejado aviso, hemos de partir de que así es. Por lo tanto resulta preciso establecer los efectos de la no retirada. No hay duda alguna acerca de la corrección de la dirección a que fue enviado el burofax (efectivo domicilio del demandado) por lo que, a salvo de mejor prueba, hemos de entender que sólo al demandado cabe imputar la no recepción efectiva de la comunicación. Lo contrario equivaldría a dejar prácticamente en manos del arrendatario la decisión sobre el particular, pues bastaría su negativa a ser notificado para eludir la acción planteada por el arrendador. Tal criterio es seguido en materia de arrendamientos, entre otras, en SAP de Vizcaya, sec. 5ª, de 15 de junio de 2000, Rec. 845/1998; SAP de Navarra de 31 de mayo de 2001 ; SAP de Málaga, sec. 5ª, de 3 de diciembre 2004 ; y SAP de Barcelona, sec. 13ª, de 6 de abril de 2011, Rec. 284/2010. En la SAP de Madrid, sec. 21ª, de 26 de abril de 2011, Rec. 356/2009 se declara que no resulta admisible dicha conducta contraria a la buena fe que ha de presidir las relaciones contractuales y en concreto las arrendaticias".

Por todo ello se solicita la estimación del recurso interpuesto revocando la resolución de instancia, y en su lugar se dicte sentencia resolviendo sobre la cuestión que es objeto de proceso, estimando en su integridad la demanda, todo ello con imposición de costas a la parte demandada en ambos casos.

SEGUNDO.- Respecto de las costas, ante la estimación total de las pretensiones de la demanda que se considera procedente en caso de verse aceptado este recurso, las mismas deben imponerse a la parte demandada, conforme al criterio de los arts. 394 y 398 LEC.

Por lo expuesto,

SUPLICO A LA AUDIENCIA PROVINCIAL

que, teniendo por presentado este escrito con su copia, y documento/s acompañado/s, de lo que se ha dado traslado al Procurador de la parte contraria en la forma que previene el art. 276 LEC, se sirva tener por INTERPUESTO RECURSO DE APELACIÓN contra la resolución de fecha [FECHA], y

SUPLICO AL TRIBUNAL que, seguido que sea el legal procedimiento, se dicte en su día sentencia por la que, estimando el recurso de apelación y la demanda interpuesta en su día, se revoque la sentencia dictada en la primera instancia y se dicte otra acogiendo las pretensiones que esta parte formuló en su demanda, con condena en costas a la parte demandada, tanto de las causadas en la primera como en la presente instancia

OTROSÍ PRIMERO DIGO, que se acompaña a este escrito resguardo acreditativo del pago del depósito de 50 euros en la Cuenta de Depósitos y Consignaciones del Tribunal al que se dirige, conforme exige la disposición adicional 15.ª LOPJ, por lo que,

SUPLICO AL TRIBUNAL que tenga por causada la manifestación anterior a los efectos oportunos.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a
