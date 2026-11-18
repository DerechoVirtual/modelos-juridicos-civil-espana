---
name: interposicion-casacion-civil-interes-casacional-pais-50
description: "Redacta el escrito «Interposición de casación civil por interés casacional (País Vasco, reforma RDL 5/2023)» (formulario 50 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Interposición de casación civil por interés casacional (País Vasco, reforma RDL 5/2023)

> Formulario 0050 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (5 veces)
- [ ] LOCALIDAD
- [ ] SEDE (2 veces)
- [ ] NÚMERO
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] LUGAR
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…/[AÑO] A LA SECCIÓN»; «…en el Rollo arriba expresado, por la que»; «…– Que la sentencia impugnada, dictada el»; «…por parte de la Sección»; «… esta parte ante la sentencia dictada el»; «…numeración del juzgado de procedencia).]»; «…[COMPLETAR] en los autos»; «…numeración del juzgado de procedencia).]»; «…: texto de las Sentencias de»

## Párrafos opcionales (2)

Inclúyelos solo si encajan en los hechos:

- OTROSÍ PRIMERO DIGO que, de conformidad con lo dispuesto en los apartados 3.d) y 6 de la disposición adicional…
- OTROSÍ SEGUNDO DIGO que, de conformidad a lo establecido en el art. 481.6 de la LEC y en el Acuerdo de la Sala…

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 477.3 de la LEC
- art. 4.3 de la Ley 4/2022
- artículo 479.1 de la LEC
- artículo 448.2 de la LEC
- artículo 215.5 LEC
- art. 481.4 de la LEC
- art. 12.11.d) de la Ley 7/2015
- art. 481.6 de la LEC

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

### Formulario 0050 · Interposición de casación civil por interés casacional (País Vasco, reforma RDL 5/2023)

- Año del modelo: 2023
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 2 párrafos opcionales señalados; 23 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Rollo nº [Nº DE PROCEDIMIENTO]/[AÑO]

A LA SECCIÓN [COMPLETAR] DE LA AUDIENCIA PROVINCIAL DE PARA ANTE LA SALA DE LO CIVIL Y PENAL DEL TRIBUNAL SUPERIOR DE JUSTICIA DEL PAÍS VASCO

D/Dª [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales, actuando en representación de [NOMBRE DEL REPRESENTADO/A] según viene acreditado en los presentes autos, como mejor proceda en derecho, DIGO:

1) Que en fecha [FECHA] esta parte ha sido notificada de la sentencia de fecha [FECHA] dictada en el Rollo arriba expresado, por la que [COMPLETAR]
2) Que entendiendo que dicha sentencia no es ajustada a derecho, dicho sea con los debidos respetos y en términos de defensa, por medio del presente escrito interpongo contra la misma RECURSO DE CASACIÓN ante el Tribunal Superior de Justicia del País Vasco, en base a los siguientes presupuestos de admisibilidad y motivos:

Admisibilidad del recurso

Primero.– El presente recurso se deduce contra la sentencia dictada por la Audiencia Provincial en fecha [FECHA], que desestima el recurso de apelación de esta parte.

Segundo.– El cauce de acceso a la casación es el de interés casacional definido (en cada caso, se concretará el supuesto...) en el art. 477.3 de la LEC y en el art. 4.3 de la Ley 4/2022, de 19 de mayo, del Recurso de Casación Civil Vasco, puesto que la sentencia recurrida aborda una cuestión sometida a la normativa del derecho civil vasco de la que no existe doctrina jurisprudencial del Tribunal Superior de Justicia del País Vasco.

Tercero.– El presente recurso se interpone dentro del plazo de veinte días establecido en el artículo 479.1 de la LEC, computados conforme al artículo 448.2 de la LEC (en su caso, en relación con el artículo 215.5 LEC), habiéndose constituido el depósito para recurrir tal como se expresa en el otrosí de este escrito.

Cuarto.– Que la sentencia impugnada, dictada el [COMPLETAR] por parte de la Sección [COMPLETAR] de la Audiencia Provincial de [LOCALIDAD] en resolución del recurso de apelación presentado por esta parte ante la sentencia dictada el [COMPLETAR] por la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] en los autos [COMPLETAR] se estima que incurre en los siguientes motivos de casación, que se desarrollan a continuación: 1) al amparo del art. 477.3 de la LEC y art. 4.3 de la Ley del Parlamento Vasco 4/2022, infracción del artículo 12.11 de la Ley del Parlamento Vasco, 7/2015, de 30 de junio de Relaciones Familiares en supuestos de separación o ruptura de los progenitores (LRFPV); 2) ...

Motivos del recurso

Primero.–

Encabezamiento.–

El primer motivo se interpone al amparo de lo dispuesto en el art. 477.3 de la LEC y art. 4.3 de la Ley del Parlamento Vasco 4/2022, al no existir doctrina jurisprudencial del Tribunal Superior de Justicia del País Vasco relativa a la interpretación del art. 12.11.d) de la Ley del Parlamento Vasco 7/2015, de 30 de junio, de Relaciones Familiares en supuestos de separación o ruptura de los progenitores (LRFPV), ni relativa a normas anteriores, de igual o similar contenido, entendiendo que la sentencia impugnada infringe dicho precepto al excluir del concepto de «convivencia marital» como causa de extinción del uso de la vivienda familiar, la situación de autos, donde existe una convivencia continuada y estable entre la demandada y su nueva pareja, con un proyecto en común, la cual resulta excluida erróneamente en la sentencia impugnada por el mero hecho de estar trabajando en el extranjero la pareja de la beneficiaria del uso de la vivienda.

Desarrollo del motivo.–

El motivo se funda en la infracción del artículo 12.11.d) de la Ley del Parlamento Vasco, 7/2015, de 30 de junio, así como de la doctrina del Tribunal Supremo, que establece como causa de extinción del derecho del uso a la vivienda familiar la de convivencia marital del beneficiario del uso con otra persona, salvo que expresamente se hubiera pactado lo contrario.

El cauce de acceso al recurso es el de interés casacional del art. 477.3 de la LEC, por no existir doctrina jurisprudencial del Tribunal Superior de Justicia del País Vasco relativa a la interpretación del art. 12.11.d) de la Ley del Parlamento Vasco 7/2015, ni a normas antecedentes de similar contenido, respecto del concepto de «convivencia marital» como causa de extinción del derecho de uso sobre la vivienda familiar, si bien existe jurisprudencia del Tribunal Supremo sobre dicho concepto, que avala la interpretación que sostiene esta representación, tal como se expone seguidamente.

De conformidad a lo dispuesto en el art. 481.4 de la LEC, debemos expresar que la infracción cometida es la de excluir del concepto de «convivencia marital», previsto en el citado art. 12.11.d) de la Ley 7/2015 como causa de extinción del uso de la vivienda familiar, la situación de autos, donde existe una convivencia continuada y estable entre la demandada y su nueva pareja, con un proyecto en común, la cual resulta excluida en la sentencia impugnada por el mero hecho de estar trabajando la pareja de la beneficiaria del uso de la vivienda en el extranjero, lo cual en modo alguno impide que pueda desarrollarse una relación de convivencia marital si se dan los caracteres de la misma, como sucede en el caso de autos.

Así, la sentencia recurrida, al estimar el recurso de apelación presentado de contrario contra la sentencia de la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO], de fecha [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], hace una interpretación errónea del citado art. 12.11.d) de la LRFPV, puesto que la demandada y su nueva pareja D. Benjamín mantienen una situación de verdadera convivencia marital, entendida como convivencia de una persona con otra de forma similar a la que se desenvuelve en la vida conyugal, con la asunción de las cargas correspondiente al proyecto en común, sin que el hecho de que la pareja de la demandada trabaje en el extranjero desvirtúe en modo alguno la existencia de una relación de convivencia continuada y estable a la que se refiere el precepto, de modo que procede extinguir el derecho de su uso porque se ha producido la entrada de un tercero en la vivienda familiar, dejando de servir a los fines del matrimonio, haciendo perder a la vivienda su antigua naturaleza por servir en su uso a una familia distinta y diferente.

Actuaciones procesales en primera y segunda instancia:

Ante la interpretación errónea que se realiza en la sentencia impugnada, solicitamos que se fije la correcta doctrina jurisprudencial sobre el art. 12.11.d) de la LRFPV, y que se declare que el concepto de «convivencia marital» contemplado como causa de extinción de uso de la vivienda familiar, salvo pacto en contrario, incluye los supuestos en que exista una relación sentimental estable, seria y duradera con la nueva pareja, mediante una convivencia común, que resulte pública y conocida en el entorno familiar y social, con independencia de que no exista una permanencia continuada en el domicilio, como es el caso en que el trabajo de la nueva pareja se desarrolla en el extranjero y no se convive a diario.

Es por ello que se pretende, con estimación del recurso de casación y que se case la sentencia, acordando en su lugar la estimación de la demanda, con la consecuente extinción del derecho del uso de la demandada de la vivienda familiar sita

Segundo.– (en su caso, se desarrollarían otros motivos...)

Por lo expuesto,

SUPLICO A LA SALA Que tenga por presentado este escrito con certificación de traslado, se sirva admitirlo y, en su virtud, tenga por interpuesto recurso de casación contra la sentencia de fecha [FECHA] dictada en el Recurso arriba indicado y que se remitan los autos a la Sala Primera del Tribunal Supremo, suplicando a la Excma. Sala estime el recurso de casación interpuesto, casando la sentencia dictada, y acuerde:

1) Fijar como doctrina jurisprudencial que el art. 12.11.d) de la LRFPV que el concepto de «convivencia marital», contemplado como causa de extinción de uso de la vivienda familiar, salvo pacto en contrario, incluye los supuestos en que exista una relación sentimental estable, seria y duradera con la nueva pareja, mediante una convivencia común, que resulte pública y conocida en el entorno familiar y social, con independencia de que no exista una permanencia continuada en el domicilio, como es el caso en que el trabajo de la nueva pareja se desarrolla en el extranjero y no se convive a diario.
2) Estimar la demanda de modificación de medidas interpuesta por esta representación, decretando la extinción del derecho de uso de la demandada sobre la vivienda sita en

[OPCIONAL — incluir si procede]

OTROSÍ PRIMERO DIGO que, de conformidad con lo dispuesto en los apartados 3.d) y 6 de la disposición adicional decimoquinta de la LOPJ acompaño a este escrito resguardo de consignación en la cuenta de Depósitos y Consignaciones abierta a nombre del Tribunal del depósito exigido para interponer el recurso por importe de 50 euros.

Por lo que, SUPLICO A LA SALA que tenga por constituido el depósito, dejando interesada desde este momento su devolución para el caso de estimación total o parcial del recurso.

[OPCIONAL — incluir si procede]

OTROSÍ SEGUNDO DIGO que, de conformidad a lo establecido en el art. 481.6 de la LEC y en el Acuerdo de la Sala de Gobierno del Tribunal Supremo de fecha 8 de septiembre de 2023, acompaño los siguientes documentos: 1) documento número [Nº DE DOCUMENTO]: copia de la resolución impugnada, que contiene la firma electrónica que la identifica; 2) documento número [Nº DE DOCUMENTO] copia de la resolución dictada en primera instancia; 3) documentos número [Nº DE DOCUMENTO]: texto de las Sentencias de [COMPLETAR] que se aducen como fundamento de interés casacional.

Por lo que, SUPLICO A LA SALA que tenga por aportados los citados documentos.

De conformidad con lo dispuesto en el Acuerdo de la Sala de Gobierno del TS de 8 de septiembre de 2023, el Abogado firmanteCERTIFICAque el presente escrito tiene 15.586 caracteres con espacio.

En [LUGAR], a [FECHA].

Procurador/a	Abogado/a

Fdo. D./Dña. [NOMBRE Y APELLIDOS]: 	Fdo. D./Dña. [NOMBRE Y APELLIDOS]:
