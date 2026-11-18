---
name: recurso-extraordinario-infraccion-procesal-art-469-1-1o-287
description: "Redacta el escrito «Recurso extraordinario por infracción procesal del art. 469.1.1º LEC (anterior al RDL 5/2023)» (formulario 287 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Recurso extraordinario por infracción procesal del art. 469.1.1º LEC (anterior al RDL 5/2023)

> Formulario 0287 del plugin **Recursos civiles** · revisado el 17-11-2026.

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
- [ ] FECHA (10 veces)
- [ ] IMPORTE
- [ ] LOCALIDAD (2 veces)
- [ ] SEDE
- [ ] Otros 21 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…/»; «…en el Rollo arriba expresado, por la que»; «…obrante en folio»; «…to. CUARTO.- Que la sentencia dictada el»; «…por parte de la Sección»; «… esta parte ante la sentencia dictada el»; «…numeración del juzgado de procedencia).]»; «…[COMPLETAR] en los autos»; «…rbitraje, tal como consta en la cláusula»; «…del contrato de fecha [FECHA] (folio»; «…sunto a arbitraje, invocando la cláusula»; «…e se recoge el convenio arbitral (folios»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 477 de la LEC
- artículo 470.1 de la LEC
- artículo 448.2 de la LEC
- artículo 215.5 LEC
- artículo 469.1 de la LEC
- artículos 11.1 de la Ley 60/2003
- art. 469.1 de la LEC
- art. 11.1 de la Ley 60/2003
- art. 471 de la LEC
- art. 39 de la LEC
- art. 394 de la LEC

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

### Formulario 0287 · Recurso extraordinario por infracción procesal del art. 469.1.1º LEC (anterior al RDL 5/2023)

- Año del modelo: 2020
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 36 campos de relleno marcados en blanco
- Avisos de la revisión: Recurso extraordinario por infracción procesal suprimido: arts. 468-476 LEC «sin contenido» y DF 16.ª suprimida (RDL 6/2023, efectos 20-3-2024); tampoco existe el acceso por cuantía superior a 600.000 €. Rehacer como recurso de casación por infracción de norma procesal con interés casacional (arts. 477.2, 477.3 y 477.6 LEC).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Rollo nº [Nº DE PROCEDIMIENTO] / [COMPLETAR].

1) Que en fecha [FECHA] esta parte ha sido notificada de la sentencia de fecha [FECHA] dictada en el Rollo arriba expresado, por la que [COMPLETAR]

2) Que entendiendo que dicha sentencia no es ajustada a derecho, dicho sea con los debidos respetos y en términos de defensa, por medio del presente escrito interpongo contra la misma RECURSO POR INFRACCIÓN PROCESAL, en base a los siguientes presupuestos de admisibilidad y motivos:

I. ADMISIBILIDAD DEL RECURSO

PRIMERO.- El presente recurso se deduce contra la sentencia dictada por la Audiencia Provincial en fecha [FECHA], que desestima el recurso de apelación de esta parte.

SEGUNDO.- El supuesto que habilita la interposición del recurso por infracción procesal contra la sentencia de forma autónoma, sin formular casación, conforme al apartado 2º de la disposición adicional decimosexta de la LEC, es el de estar comprendida en el apartado 2º del artículo 477 de la LEC, al tratarse de un proceso cuya cuantía excede de 600.000 euros, siendo superior la de este proceso al reclamarse la cantidad de [IMPORTE] euros, la cual queda fijada como cuantía del mismo en la resolución de fecha [FECHA] obrante en folio [COMPLETAR] de las actuaciones.

TERCERO. .- El presente recurso se interpone dentro del plazo de veinte días establecido en el artículo 470.1 de la LEC, computados conforme al artículo 448.2 de la LEC ( en su caso, en relación con el artículo 215.5 LEC), habiéndose constituido el depósito para recurrir tal como se expresa en el otrosí de este escrito.

CUARTO.- Que la sentencia dictada el [COMPLETAR] por parte de la Sección [COMPLETAR] de la Audiencia Provincial de [LOCALIDAD] en resolución del recurso de apelación presentado por esta parte ante la sentencia dictada el [COMPLETAR] por la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] en los autos [COMPLETAR] se estima que incurre en los siguientes motivos de infracción procesal: 1) al amparo del motivo primero del artículo 469.1 de la LEC por vulneración de los artículos 11.1 de la Ley 60/2003, de 23 de diciembre, de Arbitraje y art. 39 de la Ley de Enjuiciamiento Civil, por estar sometida la cuestión a arbitraje lo que se denunció en tiempo y forma por declinatoria y en el recurso de apelación; 2) al amparo del motivo. del artículo 469.1 de la LEC.

II. MOTIVOS DEL RECURSO

PRIMERO.- (Encabezamiento.) El primer motivo se interpone al amparo de lo dispuesto en el apartado primero del art. 469.1 de la LEC, por infracción de las normas sobre jurisdicción con vulneración del art. 11.1 de la Ley 60/2003, de 23 de diciembre, de Arbitraje y art. 39 de la Ley de Enjuiciamiento Civil, por falta de jurisdicción de los tribunales civiles al haberse sometido la cuestión a arbitraje, tal como consta en la cláusula [COMPLETAR] del contrato de fecha [FECHA] (folio [COMPLETAR]), habiéndose planteado en tiempo y forma declinatoria y alegado como motivo de apelación, resultando desestimadas en ambas instancias.

Desarrollo del motivo: Conforme a lo previsto en el art. 471 de la LEC se expone a continuación de forma razonada la infracción o vulneración cometida, con expresión de la manera en que influyeron en el proceso: El motivo se funda en la vulneración del art. 11.1 de la Ley 60/2003, de Arbitraje y art. 39 de la Ley de Enjuiciamiento Civil, al haberse sometido la cuestión a arbitraje en virtud de convenio arbitral, habiéndose planteado declinatoria de jurisdicción en ambas instancias, tal como se expone a continuación.

Actuaciones procesales en primera y segunda instancia: De las actuaciones se desprende que esta parte planteó en tiempo y forma la falta de jurisdicción de los tribunales civiles, por haberse sometido la cuestión a arbitraje, en ambas instancias.

En primera instancia, y tras ser emplazada esta parte para contestar a la demanda, formuló en tiempo y forma declinatoria de falta de jurisdicción por estar sometido el asunto a arbitraje, invocando la cláusula [COMPLETAR] del contrato de fecha [FECHA] donde se recoge el convenio arbitral (folios [COMPLETAR]). Tras la tramitación legal, el Tribunal dictó auto de fecha [FECHA], desestimado la declinatoria planteada por esta parte (folios [COMPLETAR]).

Frente a dicho auto, se interpuso recurso de reposición (folios [COMPLETAR]) que, tras los trámites correspondientes, fue desestimado por auto del Tribunal de fecha [FECHA] (folios [COMPLETAR]).

Contra dicha resolución esta parte formuló protesta con reserva de alegar la falta de presupuestos procesales en la apelación (folios [COMPLETAR]) y, tras dictarse sentencia de primera instancia en fecha [FECHA], interpuso recurso de apelación contra la misma fundado, como primer motivo, en la falta de jurisdicción del órgano civil al haberse sometido la cuestión a arbitraje (folios [COMPLETAR]), motivo que fue desestimado por la sentencia de apelación aquí recurrida.

Procedencia del recurso extraordinario por infracción procesal: Frente a esta decisión, es procedente interponer el recurso extraordinario por infracción procesal y en este sentido debe indicarse que la STS del Pleno número 640/2017, de 24 de noviembre ha interpretado que la infracción relativa a la falta de jurisdicción, por sumisión a arbitraje, ha de ser planteada a través del recurso extraordinario por infracción puesto que se está planteando es una cuestión de índole procesal ajena al recurso de casación y propia del recurso extraordinario por infracción procesal, como es la competencia o no de la jurisdicción por existir un pacto de sumisión a arbitraje, y ello pese a que el estudio del problema orgánico procesal (incompetencia de jurisdicción por existencia de sumisión a arbitraje) requiera aplicar normas de interpretación de la cláusula compromisoria como cuestión previa que condiciona y, en su caso, impide la resolución de la cuestión objeto del proceso.

Cláusula de sumisión a arbitraje: validez, eficacia y contenido. Esta parte alegó en la declinatoria planteada en la instancia que el contrato recogía el convenio arbitral en forma de cláusula incorporada al mismo, tal como contempla el art. 9.1 de la Ley de Arbitraje, el cual se recogía en la cláusula [COMPLETAR] con el siguiente tenor literal: "Las partes intervinientes acuerdan que todo litigio, cuestión o reclamación resultantes de la ejecución o interpretación del presente contrato u operación relacionada con él, directa o indirectamente, se resolverá definitivamente mediante arbitraje de Derecho, por un único árbitro, en el marco de la Corte de Arbitraje de [COMPLETAR], a la que se encomienda la administración del arbitraje y la designación de los árbitros de acuerdo con su Reglamento y Estatutos, sin más excepciones o derogaciones que las contempladas en la presente cláusula arbitral" (folios [COMPLETAR]).

Por tanto, existiendo un convenio arbitral válido, según establece el artículo 9 de la Ley de Arbitraje, y tratándose de materia susceptible de arbitraje, por ser un contrato privado de suministro sujeto al principio de la autonomía de la voluntad, ambas partes vienen obligadas a cumplir lo estipulado, impidiendo a los tribunales conocer la controversia sometida a arbitraje, tal como imperativamente dispone el artículo 11 de la Ley de Arbitraje y, en concordancia, el art. 39 de la LEC.

A pesar de lo anterior, tanto el Tribunal, en las resoluciones desestimatoria de la declinatoria, como la sentencia dictada en sede de apelación por la Audiencia Provincial, razonan que el pacto de arbitraje no exime necesariamente del acceso a la jurisdicción y que la cuestión planteada estaba fuera del ámbito del contrato.

Dicho razonamiento es totalmente erróneo, dicho sea en términos de defensa, puesto que la cláusula transcrita cumple los requisitos del convenio arbitral del art. 9.1 de la Ley Arbitraje, tanto de forma como de contenido, como expresión del principio de autonomía de la voluntad en que se funda la institución del arbitraje según la jurisprudencia constitucional. La STC 9/2005, de 17 de enero declara que el arbitraje es un medio heterónomo de arreglo de controversias que se fundamenta en la autonomía de la voluntad de los sujetos privados, lo que constitucionalmente lo vincula con la libertad como valor superior del ordenamiento jurídico, de lo que la STS de 11 de febrero de 2010, rec. 2524/2005, concluye que el arbitraje supone una verdadera renuncia a la intervención de los tribunales cuando no es absolutamente indispensable, siempre que la parte interesada invoque oportunamente la cláusula arbitral, como es el caso, y que esta renuncia ampara la exclusión de la intervención judicial, cuyos inconvenientes se compensan con los beneficios de la rapidez y flexibilidad en el orden procedimental y sustantivo que constituyen la razón de ser del arbitraje.

El texto de la cláusula del contrato transcrita expresa de forma inequívoca la voluntad de someter las controversias en relación a la interpretación o cumplimiento de lo pactado a arbitraje de Derecho, tanto en relación al contrato como en las demás operaciones relacionadas con el mismo, aun en el caso de que lo fueran de forma indirecta. Las cuestiones en que la parte actora funda en su demanda (folios [COMPLETAR]) la pretensión de condena por incumplimiento contractual (principalmente, utilización de materiales de peor calidad, necesidad de asumir deudas contraídas con un tercero por la sociedad demandada para hacer posible el suministro y con ello la realización de la obra y la venta no consentida de la piedra del muro que se excavó por la demandada) son cuestiones que deben considerarse indisolublemente ligadas al cumplimiento del contrato, comprendiendo operaciones relacionadas con el mismo y, por lo tanto, expresamente incluidas en la cláusula arbitral.

La sentencia recurrida argumenta que no se incluyeron expresamente en la cláusula arbitral estas cuestiones de manera específica, pero lo cierto es que todas las cuestiones que se plantean en la demanda se invocan como manifestaciones directas o indirecta del presunto defectuoso cumplimiento del contrato por esta parte demandada y no como conductas susceptibles de indemnización ajenas a éste.

Como la jurisprudencia, las cláusulas del convenio arbitral, como las de cualquier negocio jurídico, debe ser interpretadas con arreglo a las normas generales sobre interpretación contenidas en los preceptos del CC que se refieren a los contratos (STS 27 de mayo de 2007, rec. 2613/2000), debiendo revisarse la interpretación cuando, como en este caso, la misma sea ilógica o arbitraria o contradiga las normas hermenéuticas aplicables. En este sentido, la STS de 5 de septiembre de 2006, rec. 4202/1999, destaca la prelación del contenido literal en la interpretación de las cláusulas arbitrales, poniendo de manifiesto que ha de estarse a lo efectivamente pactado como objeto de arbitraje, pues, conforme a los artículos 1 y 9 de la Ley de Arbitraje, la sumisión a la decisión arbitral ha de entenderse con carácter decisorio y exclusivo, no de forma concurrente o alternativa con otras jurisdicciones.

En este caso, el contrato se concertó entre dos sociedades que sometieron a arbitraje de Derecho “todo litigio, cuestión o reclamación resultantes de la ejecución o interpretación del presente contrato u operación relacionada con él, directa o indirectamente”, de cuyo términos literales resulta claro que la pretensión del demandante queda incluida en el ámbito del convenio, por lo que la sumisión a la decisión arbitral es excluyente del conocimiento de los tribunales de la jurisdicción civil al haberse opuesto en tiempo y forma la correspondiente declinatoria por esta parte, tal como ha quedado relatado anteriormente.

La falta de jurisdicción del órgano judicial por sumisión de la cuestión a arbitraje. En estos términos, es de aplicación el art. 11.1 de la Ley de Arbitraje, que resulta infringido por la resolución impugnada, el cual dispone que “el convenio arbitral obliga a las partes a cumplir lo estipulado e impide a los tribunales conocer de las controversias sometidas a arbitraje, siempre que la parte a quien interese lo invoque mediante declinatoria. El plazo para la proposición de la declinatoria será dentro de los diez primeros días del plazo para contestar a la demanda”. De forma concordante, el art. 39 de la LEC, que también resulta infringido, dispone que el demandado podrá denunciar mediante declinatoria la falta de jurisdicción por haber sido sometido el asunto a arbitraje.

Como reitera la jurisprudencia, el arbitraje supone una renuncia a la intervención de los tribunales cuando no es absolutamente indispensable (siempre que la parte interesada invoque oportunamente la cláusula arbitral). Esta renuncia ampara la exclusión de la intervención judicial, cuyos inconvenientes se compensan con los beneficios de la rapidez y flexibilidad en el orden procedimental y sustantivo que constituyen la razón de ser del arbitraje.

En este caso, ante el hecho de constar la sumisión de la cuestión litigiosa a arbitraje según la cláusula del contrato que antes se ha transcrito, el conocimiento de este litigio no corresponde a la jurisdicción civil, con fundamento en los arts. 1, 4, 5 y 9 de la Ley de Arbitraje, y, especialmente, en el artículo 11 de la citada Ley, alegado como infringido, puesto que, como reitera la jurisprudencia, el poder de disposición de las partes en orden a la exclusión de los órganos jurisdiccionales del Estado en las materias de derecho disponible es prácticamente total, como indica la STC 136/2010, de modo que el convenio arbitral es apto para expresar "la voluntad de las partes de someter a arbitraje todas o algunas de las controversias que hayan surgido o puedan surgir respecto de una determinada relación, contractual o no contractual", todo lo cual determina la falta de jurisdicción de los tribunales del orden civil, al haberse planteado la cuestión procesal en tiempo y forma, por medio de declinatoria, y siendo válido y eficaz el convenio arbitral, el cual incluye las cuestiones objeto de la demanda en el ámbito de la materia arbitrable.

Pretensión y efectos. Por lo anteriormente expuesto, se solicita la estimación del recurso extraordinario por infracción procesal y, de conformidad a lo establecido en el art. 476.2.II de la LEC, que se case la resolución impugnada por falta de jurisdicción al existir sumisión a arbitraje, quedando a salvo el derecho de las partes a ejercitar la pretensión ante quien correspondiere, con imposición a la actora de las costas del proceso de instancia conforme al art. 394 de la LEC.

SEGUNDO.- (en su caso, se formularía el motivo de forma subsidiaria al tener que resolverse en primer lugar la cuestión sobre la jurisdicción)

En base a lo anterior,

SUPLICO A LA SALA: Que tenga por presentado este escrito teniendo por interpuesto el recurso por infracción procesal frente a la sentencia dictada por esa Sala en las presentes actuaciones de fecha [FECHA] y tras la pertinente tramitación y remisión de las actuaciones al Tribunal Superior de Justicia de [LOCALIDAD], se dicte por la Sala sentencia en la que declarando haber lugar al recurso por infracción procesal presentado, se case la resolución impugnada, declarando la falta de jurisdicción y quedando a salvo el derecho de las partes a ejercitar las pretensiones ante quien correspondiere. Se solicita asimismo la imposición a la actora de las costas del proceso de instancia.

OTROSÍ PRIMERO DIGO que, de conformidad con lo dispuesto en los apartados 3.c) y 6 de la disposición adicional decimoquinta de la LOPJ acompaño a este escrito resguardo de consignación en la cuenta de Depósitos y Consignaciones abierta a nombre del Tribunal del depósito exigido para interponer el recurso por importe de 50 euros.

Por lo que, SUPLICO A LA SALA que tenga por constituido el depósito, dejando interesada desde este momento su devolución para el caso de estimación total o parcial del recurso.

En L. y F.

(Firma Procurador y Abogado)
