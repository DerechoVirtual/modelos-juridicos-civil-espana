---
name: recurso-extraordinario-infraccion-procesal-art-469-1-3o-285
description: "Redacta el escrito «Recurso extraordinario por infracción procesal del art. 469.1.3º LEC (anterior al RDL 5/2023)» (formulario 285 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Recurso extraordinario por infracción procesal del art. 469.1.3º LEC (anterior al RDL 5/2023)

> Formulario 0285 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Recurso extraordinario por infracción procesal suprimido: arts. 468-476 LEC «sin contenido» y DF 16.ª suprimida (RDL 6/2023, efectos 20-3-2024); tampoco existe el acceso por cuantía superior a 600.000 €. Rehacer como recurso de casación por infracción de norma procesal con interés casacional (arts. 477.2, 477.3 y 477.6 LEC).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] Nº DE PROCEDIMIENTO
- [ ] FECHA (6 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] IMPORTE (2 veces)
- [ ] SEDE
- [ ] Otros 19 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…/»; «…en el Rollo arriba expresado, por la que»; «…obrante en folio»; «…to. CUARTO.- Que la sentencia dictada el»; «…por parte de la Sección»; «… esta parte ante la sentencia dictada el»; «…numeración del juzgado de procedencia).]»; «…[COMPLETAR] en los autos»; «… obra celebrado entre las partes (folios»; «…(grabación acto audiencia previa, minuto»; «…a»; «…(grabación acto audiencia previa, minuto»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 477 de la LEC
- artículo 470.1 de la LEC
- artículo 448.2 de la LEC
- artículo 215.5 LEC
- artículo 469.1 de la LEC
- art. 469.1 de la LEC
- art. 471 de la LEC
- art. 469.2 de la LEC
- art. 265.3 de la LEC
- arts. 265.3 de la LEC
- arts. 281, 282 y 283 de la LEC
- art. 24.2 CE

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

### Formulario 0285 · Recurso extraordinario por infracción procesal del art. 469.1.3º LEC (anterior al RDL 5/2023)

- Año del modelo: 2020
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; saltos de párrafo recuperados (texto venía pegado); 32 campos de relleno marcados en blanco
- Avisos de la revisión: Recurso extraordinario por infracción procesal suprimido: arts. 468-476 LEC «sin contenido» y DF 16.ª suprimida (RDL 6/2023, efectos 20-3-2024); tampoco existe el acceso por cuantía superior a 600.000 €. Rehacer como recurso de casación por infracción de norma procesal con interés casacional (arts. 477.2, 477.3 y 477.6 LEC).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Rollo nº [Nº DE PROCEDIMIENTO] / [COMPLETAR]

1) Que en fecha [FECHA] esta parte ha sido notificada de la sentencia de fecha [FECHA] dictada en el Rollo arriba expresado, por la que [COMPLETAR]

2) Que entendiendo que dicha sentencia no es ajustada a derecho, dicho sea con los debidos respetos y en términos de defensa, por medio del presente escrito interpongo contra la misma RECURSO POR INFRACCIÓN PROCESAL, en base a los siguientes presupuestos de admisibilidad y motivos:

I. ADMISIBILIDAD DEL RECURSO

PRIMERO.- El presente recurso se deduce contra la sentencia dictada por la Audiencia Provincial de [LOCALIDAD] en fecha [FECHA], que desestima el recurso de apelación de esta parte.

SEGUNDO.- El supuesto que habilita la interposición del recurso por infracción procesal contra la sentencia de forma autónoma, sin formular casación, conforme al apartado 2º de la disposición adicional decimosexta de la LEC, es el de estar comprendida en el apartado 2º del artículo 477 de la LEC, al tratarse de un proceso cuya cuantía excede de 600.000 euros, siendo superior la de este proceso al reclamarse la cantidad de [IMPORTE] euros, la cual queda fijada como cuantía del mismo en la resolución de fecha [FECHA] obrante en folio [COMPLETAR] de las actuaciones.

TERCERO.- El presente recurso se interpone dentro del plazo de veinte días establecido en el artículo 470.1 de la LEC, computados conforme al artículo 448.2 de la LEC( en su caso, en relación con el artículo 215.5 LEC), habiéndose constituido el depósito para recurrir tal como se expresa en el otrosí de este escrito.

CUARTO.- Que la sentencia dictada el [COMPLETAR] por parte de la Sección [COMPLETAR] de la Audiencia Provincial de [LOCALIDAD] en resolución del recurso de apelación presentado por esta parte ante la sentencia dictada el [COMPLETAR] por la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] en los autos [COMPLETAR] se estima que incurre en los siguientes motivos de infracción procesal: 1) al amparo del motivo tercero del artículo 469.1 de la LEC por vulneración de los artículos 265.3, 281, 282 y 283 de la Ley de Enjuiciamiento Civil, al haberse denegado la práctica de la prueba en primera y segunda instancia, habiéndose impugnado las resoluciones y habiendo producido una situación de indefensión material a esta parte; 2) al amparo del motivo. del artículo 469.1 de la LEC.

II. MOTIVOS DEL RECURSO

PRIMERO.- (Encabezamiento.) El primer motivo se interpone al amparo de lo dispuesto en el apartado tercero del art. 469.1 de la LEC, por vulneración de los artículos 265.3, 281, 282 y 283 de la Ley de Enjuiciamiento Civil, al haberse denegado la práctica de la prueba en primera y segunda instancia, habiéndose impugnado en tiempo y forma la denegación vía reposición y protesta en ambas instancias, siendo desestimada, con resultado de indefensión para esta parte al no haber podido acreditar el cumplimiento del contrato por la correcta ejecución de la obra reclamada en las condiciones pactadas, por la indebida denegación de la prueba de interrogatorio de la parte, documental y pericial propuestas.

Desarrollo del motivo: Conforme a lo previsto en el art. 471 de la LEC se expone a continuación de forma razonada la infracción o vulneración cometida, con expresión de la manera en que influyeron en el proceso: El motivo se funda en la vulneración de los artículos 281, 282, 283 y 428 de la Ley de Enjuiciamiento Civil, al haberse denegado la práctica de la prueba en primera y segunda instancia, habiéndose impugnado en tiempo y forma la denegación, con resultado de indefensión, como seguidamente se pasa a detallar.

Actuaciones procesales en primera y segunda instancia: De las actuaciones se desprende que esta parte interpuso demanda contra la entidad promotora, en reclamación de la cantidad de [IMPORTE] euros, como precio de los trabajos realizados en virtud del contrato de obra celebrado entre las partes (folios [COMPLETAR] de las actuaciones).

En el proceso de instancia, tras contestar a la demanda la parte demandada, en la audiencia previa esta parte propuso la práctica de interrogatorio de la demandada, al existir discrepancias en la interpretación de la cláusula quinta del contrato por oscuridad que se aducía introducida por la demandada, documental consistente en facturas abonadas a industriales subcontratados, y prueba pericial para acreditar que las partidas de la obra se habían ejecutado correctamente y que el valor de la obra ejecutada era muy superior al admitido por la entidad demandada (grabación acto audiencia previa, minuto [COMPLETAR] a [COMPLETAR]).

Dichas pruebas no fueron admitidas por el juez, por lo que esta parte recurrió en reposición y el juez desestimó el recurso. Se formuló protesta por tal desestimación (grabación acto audiencia previa, minuto [COMPLETAR] a [COMPLETAR]).

El juez dictó sentencia sin más trámite, desestimando la demanda al considerar que no se había probado suficientemente la existencia de la deuda objeto de reclamación en la demanda (folios …. de las actuaciones).

En segunda instancia, esta parte interpuso recurso de apelación contra la sentencia de primera instancia. En su escrito de interposición del recurso propuso la práctica por el tribunal de apelación de la prueba inadmitida en primera instancia por haber sido indebidamente denegada en primera instancia (folios [COMPLETAR] de las actuaciones).

El Tribunal de apelación, por auto de fecha [FECHA], denegó el recibimiento a prueba en segunda instancia por entender que el supuesto no estaba previsto en el artículo 460 de la Ley de Enjuiciamiento Civil (folios [COMPLETAR] de las actuaciones).

Contra el referido auto, esta parte interpuso recurso de reposición, el cual fue desestimado por la Audiencia Provincial (folios [COMPLETAR] de las actuaciones), formulando esta parte protesta con reserva del derecho a alegar la infracción procesal vía recurso extraordinario (folios [COMPLETAR] de las actuaciones).

Por tanto, esta parte denunció la vulneración de la infracción procesal tanto en primera como en segunda instancia, tal como exige el art. 469.2 de la LEC.

Procedencia del recurso extraordinario por infracción procesal: Frente a esta decisión, es procedente interponer el recurso extraordinario por infracción procesal y en este sentido debe indicarse que la jurisprudencia de la Sala Primera del Tribunal Supremo viene reiterando de forma uniforme, a partir de la STS de 12 de marzo de 2014 (RC 105/2012), que la denegación indebida de prueba en la primera instancia se remedia mediante su proposición y práctica en segunda instancia, amparada en el art. 460.2.1º de la LEC que prevé que el apelante puede pedir en el escrito de interposición del recurso la práctica en segunda instancia de las pruebas que hubieren sido indebidamente denegadas en la primera instancia, lo cual cumplió esta parte como ha quedado expuesto. Asimismo, es criterio reiterado de la Sala a la que nos dirigimos que el recurso extraordinario debe formularse por la vía del apartado 3 del art. 469.1 de la LEC, y no por la del apartado 4 del mismo precepto, por lo que se cumplen los requisitos para su interposición. Así se expresa en la STS de 19 de octubre de 2015 (RC 669/2013), que afirma que el ordinal adecuado es el 3º, ya que la consecuencia de una eventual estimación del motivo es el de la reposición de las actuaciones para la práctica, ante el tribunal de segunda instancia, de las pruebas indebidamente denegadas, a la vez de subrayar que el derecho fundamental a la tutela judicial efectiva es de configuración legal, por lo que debe citarse el precepto procesal infringido como se hace en este recurso.

Pertinencia y relevancia decisiva de la prueba propuesta y alcance de la denegación.

El hecho concreto que la denegación ha impedido acreditar es el cumplimiento del contrato en las condiciones pactadas por la correcta ejecución de toda la obra reclamada.A este objeto se propusieron los medios de prueba por esta parte, por lo que su denegación es injustificada y tiene una influencia decisiva en el resultado del proceso, puesto que ambas sentencias, dictadas en primera y segunda instancia, desestiman la demanda por falta de prueba, cuando precisamente el objeto de los medios propuestos por esta parte era el de acreditar los mismos extremos que fundan la desestimación, lo cual deja a esta parte en una situación de absoluta indefensión. En este punto, los hechos relevantes y necesarios para la estimación de la pretensión de esta parte eran los de acreditar que se cumplió escrupulosamente el contrato, sin que fuera de aplicación la exención aducida por la demandada derivada de una incorrecta interpretación de la cláusula quinta del contrato, y que se ejecutó la obra correctamente en todas las partidas reclamadas por esta parte, lo cual no se ha podido acreditar al denegarse la prueba propuesta a dicho objeto.

La jurisprudencia de la Sala a la que tenemos el honor de dirigirnos, reflejada entre otras en la STS 400/2012, de 12 de junio, recuerda que el derecho a utilizar los medios de prueba pertinentes para la defensa de los propios intereses, protegido por el artículo 24, apartado 2, de la Constitución Española, deriva, según la doctrina constitucional, de que su reconocimiento cumpla la función de garantizar a las partes la posibilidad de impulsar una actividad probatoria de acuerdo con lo que reclamen sus intereses, y que la sanción reclamada por la recurrente por la violación del derecho de que se trata está sujeta a la concurrencia de ciertas condiciones. En primer término, la de pertinencia, ya que el artículo 24 no ampara un hipotético derecho a una actividad probatoria ilimitada, sino que atribuye sólo el de exigir la admisión y práctica de las pruebas que sean pertinentes, entendiendo por tales las que tengan una relación con el tema o supuesto que deba decidirse; en segundo término, la de legalidad, ya que, al tratarse de un derecho de configuración legal, su efectivo ejercicio ha de ajustarse al marco legal establecido por el ordenamiento jurídico; y, finalmente, la de relevancia, que impone se acredite por la parte recurrente - a quien corresponde la carga procesal de hacerlo - la realidad de una indefensión constitucionalmente relevante, lo que implica la demostración de que la actividad probatoria no admitida o no practicada era decisiva en términos de defensa, pues hubiera podido tener una influencia determinante en la resolución del pleito, al ser susceptible de alterar el fallo en favor del recurrente.

En este caso se cumplen las condiciones para la estimación del recurso extraordinario de infracción procesal pues la prueba propuesta era pertinente y decisiva en términos de defensa. Así, en primer lugar, la prueba de interrogatorio de la demandada estaba dirigida a aclarar la interpretación de la cláusula quinta del contrato, que fue introducida a instancias de la demandada, cuyo redactado se alegaba oscuro, puesto que sometía el pago de la indemnización por incumplimiento a la condición de que la obra realizada lo estuviera “a satisfacción de la promotora”, y a cuyo amparo la promotora dejó de abonar diferentes partidas que estaban ejecutadas aduciendo que no se habían ejecutado a su satisfacción al amparo de dicha cláusula. Esta parte alegó que esta cláusula fue redactada por la demandada y que la misma tenía como objeto que no se abonaran partidas ejecutadas de forma defectuosa, según se convino por ambas partes al concertar el contrato, pero no confería a la promotora demandada un derecho a dejar de abonar partidas ejecutadas correctamente con la excusa de que no se habían realizado a su satisfacción. A este mismo objeto se dirigía en parte la prueba pericial propuesta por esta parte, donde se pretendía probar que las partidas de la obra se habían ejecutado correctamente, sin que pudieran ser rechazadas por la promotora amparadas en dicha cláusula oscura.

En la sentencia de apelación se interpreta que la cláusula permitía rechazar a la demandada aquellas partidas que entendía que no cumplían las exigencias de control de calidad de sus propios servicios técnicos, sin dar la oportunidad a esta parte a rebatir la interpretación de la cláusula al ver denegada la prueba tendente a fijar su sentido y a acreditar que la obra se ejecutó debidamente mediante la pericia técnica propuesta. Por tanto, esta parte no pretende revisar la interpretación del contrato efectuada por el Tribunal de apelación, sino que lo que se pretende es determinar si la inadmisión de los medios de prueba sobre cuál había sido la voluntad contractual a interpretar, y tendente a demostrar que la obra se realizó correctamente, infringió los preceptos procesales alegados y, en definitiva, si respetó o no el derecho que el artículo 24, apartado 2, de la CE reconoce. Y la conclusión debe ser negativa, pues los medios de prueba propuestos guardan directa relación con la tutela judicial pretendida en la demanda, no eran inútiles ni impertinentes, y su relevancia guarda directa relación con la escasa claridad de la cláusula discutida y con la acreditación del estricto cumplimiento del contrato, con la correspondiente obligación de indemnizar por la parte demandada.

A este mismo objeto eran pertinentes y relevantes, la prueba documental y la parte de la pericia técnica dirigidas a acreditar la realización de las partidas no admitidas por la demandada. Precisamente, las partidas no admitidas fueron las realizadas por los subcontratistas cuyas facturas se aportaban, cuestión ésta que introdujo la demandada de forma novedosa en su contestación a la demanda, por lo que la pertinencia y utilidad de la documental estaba amparada por lo dispuesto en el art. 265.3 de la LEC, precepto que resulta infringido, a la vez que era totalmente decisivo para el resultado del pleito acreditar que dicha obra se había realizado a cuyo efecto las facturas y la pericial propuesta a este objeto, para demostrar que la obra cuestionada se había ejecutado efectivamente a cargo de mi defendida, eran totalmente necesarias.

La infracción de las normas y el efecto indefensión.

Tal como se ha expuesto, la resolución impugnada ha infringido los arts. 265.3 de la LEC, así como los arts. 281, 282 y 283 de la LEC, en configuración del derecho constitucional a la prueba del art. 24.2 CE, al denegar indebidamente los tres medios de prueba propuestos por esta parte, los cuales eran decisivos para acreditar que las cantidades reclamadas correspondían a prestaciones realizadas en cumplimiento del contrato, tanto en calidad de obra ejecutada, como en cantidad de la misma, de manera que la indebida denegación de esta prueba deja a esta parte en una situación de absoluta indefensión. Esta parte actuó diligentemente recurriendo en reposición las denegaciones de prueba, tanto en primera como en segunda instancia, resultando desestimadas sus pretensiones y proyectándose dicha denegación en la decisión final al haberse desestimado la demanda por falta de prueba, lo cual abunda en la situación de total indefensión en que se ve inmersa esta parte como consecuencia de las infracciones legales denunciadas.

Pretensión y efectos. Por lo anteriormente expuesto, se solicita la estimación del recurso extraordinario por infracción procesal y, de conformidad con lo dispuesto en el artículo 476 de la Ley de Enjuiciamiento Civil [COMPLETAR], que se declare la nulidad de la sentencia recurrida, con reposición de las actuaciones al momento en que se produjo la infracción, esto es y conforme señala la citada STS de 19 de octubre de 2015, rec. 669/2013, aquel en que se inadmitieron en la segunda instancia los tres medios de prueba de que se trata, a fin de que sean admitidos y se practiquen, antes de dictar nueva sentencia de apelación.

SEGUNDO.- El segundo motivo se interpone al amparo de lo dispuesto en el apartado [COMPLETAR] del art. 469.1 de la LEC

En base a lo anterior,

SUPLICO A LA SALA: Que tenga por presentado este escrito teniendo por interpuesto el recurso por infracción procesal frente a la sentencia dictada por esa Sala en las presentes actuaciones de fecha [FECHA] y tras la pertinente tramitación y remisión de las actuaciones al Tribunal Superior de Justicia de [LOCALIDAD], se dicte por la Sala sentencia en la que declarando haber lugar al recurso por infracción procesal presentado, se declare la nulidad de la sentencia recurrida, con reposición de las actuaciones al momento en que se produjo la infracción, esto es, aquel en que se inadmitieron en la segunda instancia los tres medios de prueba de que se trata, a fin de que sean admitidos y se practiquen, antes de dictar nueva sentencia de apelación.

OTROSÍ PRIMERO DIGO que, de conformidad con lo dispuesto en los apartados 3.c) y 6 de la disposición adicional decimoquinta de la LOPJ acompaño a este escrito resguardo de consignación en la cuenta de Depósitos y Consignaciones abierta a nombre del Tribunal del depósito exigido para interponer el recurso por importe de 50 euros.

Por lo que, SUPLICO A LA SALA que tenga por constituido el depósito, dejando interesada desde este momento su devolución para el caso de estimación total o parcial del recurso.

En L. y F.

(Firma Procurador y Abogado)
