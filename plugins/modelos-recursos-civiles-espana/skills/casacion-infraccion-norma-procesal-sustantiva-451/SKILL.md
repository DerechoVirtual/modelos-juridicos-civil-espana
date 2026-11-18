---
name: casacion-infraccion-norma-procesal-sustantiva-451
description: "Redacta el escrito «Casación por infracción de norma procesal y sustantiva» (formulario 451 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Casación por infracción de norma procesal y sustantiva

> Formulario 0451 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (2 veces)
- [ ] Nº DE PROCEDIMIENTO (2 veces)
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] FECHA (7 veces)
- [ ] IMPORTE (3 veces)
- [ ] SEDE (2 veces)
- [ ] NÚMERO
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] LUGAR
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…a procesal de la LO 1/2025. A LA SECCIÓN»; «…editada en los autos de juicio ordinario»; «…lamación por responsabilidad contractual»; «…do a nuestra instancia contra la entidad»; «…SA»; «…tido, se reclamó a la entidad financiera»; «…numeración del juzgado de procedencia).]»; «…n el recurso de apelación interpuesto el»; «… parte necesaria la celebración de vista»; «…elebración de vista del presente recurso»; «…la interposición del recurso de casación»

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 477.2 LEC
- arts. 477.2 y 3 LEC
- art. 218.2 LEC
- arts. 318 y 319 LEC
- art. 120.3 CE
- arts. 209 LEC
- art. 24 CE
- art. 487.6 LEC
- art. 481.6 LEC
- Ley 5/2023
- Ley 57/1968

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

### Formulario 0451 · Casación por infracción de norma procesal y sustantiva

- Año del modelo: 2018
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (2); 32 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Interposición conjunta de recurso de casación fundado en infracción de norma procesal [NOTA DE REVISIÓN: En casación por infracción procesal hay que acreditar la denuncia previa en la instancia y, en su caso, la petición de subsanación (arts. 477.6 y 479.2 LEC); citarlos. Fuente: LEC arts. 477.2, 477.6 y 479.2 (redacc. RDL 5/2023, BOE-A-2023-15135).] y sustantiva, adaptado al Real Decreto-Ley 5/2023, de 28 de junio.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN [COMPLETAR] DE LA AUDIENCIA PROVINCIAL DE [LOCALIDAD]

[NOTA DE REVISIÓN: Errata. La Audiencia Provincial no cambia de denominación; sus Secciones se identifican por su número. Fuente: LOPJ arts. 80 y 82 (Audiencia Provincial, sin cambio de denominación).]

Autos nº [Nº DE PROCEDIMIENTO]

Rollo de apelación nº [Nº DE PROCEDIMIENTO]

D./Dª. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre de D./Dª. [NOMBRE Y APELLIDOS], cuya representación tengo debidamente acreditada en los autos de juicio ordinario [COMPLETAR], sobre reclamación por responsabilidad contractual [COMPLETAR], seguido a nuestra instancia contra la entidad [COMPLETAR] SA [COMPLETAR], ante la Sala comparezco y, como mejor proceda en Derecho, DIGO:

Que, por medio del presente escrito, al amparo de lo dispuesto en el art. 477.2 LEC, en la redacción dada por el Real Decreto-Ley 5/2023, de 28 de junio, y dentro del plazo legal, interpongo en nombre de D./Dª [NOMBRE Y APELLIDOS]. RECURSO DE CASACIÓN ante la Sala Primera del Tribunal Supremo, contra la sentencia de fecha [FECHA] dictada por esta Audiencia Provincial, en grado de apelación, y notificada en fecha [FECHA]; en los autos de juicio ordinario al margen referenciados, con arreglo a los siguientes:

MOTIVOS

1.- Enumeración de los Motivos (1)

PRIMERO

De conformidad con lo establecido en los arts. 477.2 y 3 LEC, se denuncia la infracción de las normas procesales reguladoras de la sentencia recurrida, por falta absoluta de motivación de las dos sentencias dictadas en el presente procedimiento, con vulneración del art. 218.2 LEC, en relación a los arts. 318 y 319 LEC. En este sentido, se reclamó a la entidad financiera [COMPLETAR] SA, como avalista, el pago de la cantidad de [IMPORTE] euros, abonada por mi mandante, en el marco de una compraventa de vivienda. La legitimación pasiva de la demandada se acreditaba con la amplia documental acompañada a la demanda, si bien la sentencia de instancia, dictada por la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], en fecha [FECHA], desestimó la demanda, con el único argumento consistente en que no se acreditaba dicha condición. La motivación se reducía a ello, sin ningún argumento de soporte, ni una referencia, siquiera mínima, para descartar la prueba documental reseñada.

Tal extremo fue denunciado en el recurso de apelación interpuesto el [COMPLETAR], si bien la sentencia aquí recurrida confirmó la sentencia de instancia, de la misma manera, sin ningún argumento adicional a la conclusión de no tener por acreditada la condición de avalista de la mercantil demandada. Todo lo cual se reitera en el presente recurso.

SEGUNDO

En virtud de lo dispuesto en los arts. 477.2 y 3 LEC, por interés casacional, se denuncia la oposición de la sentencia recurrida a la doctrina jurisprudencial del Tribunal Supremo y, en concreto, la emanada de las SSTS —Pleno— 540/2013 de 13 de septiembre de 2013 —rec. 281/2013—, y 778/2014 de 20 de enero de 2015 —rec. 196/2013—; al aplicar los arts. 1, 3 y 7 de la hoy derogada Ley 57/1968, de 27 de julio, sobre percibo de cantidades anticipadas en la construcción y venta de viviendas.

En las mismas se declara que la garantía establecida por dicha ley para la devolución de las cantidades anticipadas por el comprador no tenía un carácter accesorio mientras la vivienda no estuviera terminada y en disposición de ser entregada. Se trata no de un aval sino un seguro de caución, ajustada al espíritu y finalidad de la mencionada ley, y que cualquier duda interpretativa debía resolverse aplicando la Constitución, en especial sus arts. 47 y 51 en cuanto el primero reconoce el derecho a disfrutar de una vivienda digna y el segundo impone a los poderes públicos garantizar la defensa de los consumidores y usuarios, de manera que la protección legal de los compradores de viviendas no podía ser en la actualidad inferior a la que tenían en 1968. La sentencia impugnada opta por la solución contraria, considerando que se trata de un aval, de carácter accesorio, y concluye que la demandada no debe devolver las cantidades que se reclaman por un importe global de [IMPORTE] euros.

TERCERO

2.- Justificación de los Motivos (2)

PRIMER MOTIVO

Como se ha indicado, el primer motivo que se esgrime en el presente recuso es la infracción de las normas reguladoras de la sentencia, por falta absoluta de motivación de las dos sentencias dictadas en el presente procedimiento, con vulneración del art. 218.2 LEC, en relación a los arts. 318 y 319 del mismo texto legal. La sentencia aquí impugnada, y la sentencia confirmada por ésta, dictada en fecha [FECHA], por el Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO]; incurren en dicho vicio al limitarse a no tener por acreditada la condición de avalista de la parte demandada, sin ofrecer ni un solo argumento al respecto, y no valorar, siquiera para descartar, la amplia prueba documental, obrante a los documentos nº [Nº DE DOCUMENTO] al nº [Nº DE DOCUMENTO] de la demanda de mi cliente, al respecto.

Extremo denunciado en el recurso de apelación interpuesto frente a la sentencia de instancia en fecha [FECHA], que se reproduce en el presente escrito, al haberse continuado con la misma infracción en la sentencia dictada por la Audiencia Provincial de [LOCALIDAD].

En esta línea, la STS 176/2016 de 17 de marzo de 2016 —rec. 2888/2014— estima la infracción procesal que aquí se denuncia por idéntica falta de razonamiento, que lleva a la Sala a desconocer el motivo de la desestimación de la demanda. Debe recordarse que la motivación es una garantía para el justiciable, elevada a rango de derecho constitucional en el art. 120.3 CE, y acorde con los arts. 209 LEC y 248.3 LOPJ. La doctrina constitucional señala que la motivación del pronunciamiento constituye requisito ineludible de la actividad judicial, existiendo incongruencia omisiva cuando se omite todo razonamiento respecto de algún punto esencial, lo que no es extensivo a todas las alegaciones, pero si a los aspectos fácticos que sirvan de base para exteriorizar el fundamento jurídico de la decisión y para permitir su control. Y ello, aunque no sea necesaria una referencia exhaustiva siempre que permita esas dos finalidades, pues ello es inherente al derecho fundamental reconocido en el art. 24 CE, bastando con que la motivación ponga de manifiesto que la decisión judicial adoptada responde a una concreta interpretación y aplicación del derecho ajena a toda arbitrariedad y que permita la eventual revisión jurisdiccional mediante los recursos legalmente establecidos. Así, la STS de 13 de abril de 1996 —rec. 2987/1992—, recogiendo la de 22 de mayo de 1997 —rec. 2051/1996— del mismo tribunal con cita de la de 7 de julio de 1995 —rec. 1054/1992—, que el derecho a la tutela judicial efectiva incluye como contenido básico el derecho a obtener de los órganos judiciales una respuesta a las pretensiones planteadas que sea motivada y fundada en derecho y no manifiestamente arbitraria o irrazonable, aunque la fundamentación jurídica pueda estimarse disentible o respecto de ella puedan formularse reparos (SSTC 74/1990 de 23 de abril de 1990 —rec. 476/1988— y 1/1991 de 14 de enero de 1991 —rec. 715/1988—), habiendo sido matizado este derecho a la motivación por la doctrina constitucional en el sentido de que no autoriza a exigir un razonamiento judicial exhaustivo y pormenorizado de todos los aspectos y perspectivas que las partes puedan tener de la cuestión que se decide, sino que deben considerarse suficientemente motivadas aquellas resoluciones judiciales que vengan apoyadas en razones que permitan conocer cuáles han sido los criterios jurídicos esenciales fundamentadores de la decisión. Véase la STC 14/1991 de 28 de enero de 1991 —rec. 1154/1988—, afirmando la STC 70/1990 de 5 de abril de 1990 —rec. 1761/1987— que basta que la motivación cumpla la doble finalidad de exteriorizar el fundamento de la decisión adoptada y permita su eventual control jurisdiccional, concretando la STC 44/1998 de 24 de febrero de 1998 —rec. 2459/1996— que la incongruencia omisiva, como es sabido, únicamente tiene lugar cuando en la decisión cuestionada se haya omitido todo pronunciamiento sobre los términos esenciales en que aparezca planteado el debate procesal. Se citan, las SSTC 77/1986 de 12 de junio de 1986 —rec. 56/1985—, 142/1987 de 23 de julio de 1987 —rec. 857/1986— o 39/1991 de 25 de febrero de 1991 —rec. 1191/1988—, entre otras.

En el presente caso, no se alcanzan ninguno de los mínimos establecidos por la jurisprudencia citada, siendo huérfanas las resoluciones recurridas de toda motivación al respecto de no apreciar la condición de avalista de la demandada consecuencia, procede estimar el presente recurso, anular la sentencia desestimatoria aquí impugnada, y entrar a analizar la prueba ignorada, resolviendo conforme al recurso de casación que se interpone conjuntamente, con el pronunciamiento correspondiente a las costas.

De acuerdo con lo establecido en el art. 487.6 LEC, procederá la resolución en primer términos de la cuestión planteada en el presente motivo de recurso, en tanto, en el caso de admitirse éste y de estimarse el motivo, deberían retrotraerse las actuaciones, con reposición del proceso al momento anterior a la comisión de la infracción formal de referencia.

SEGUNDO MOTIVO

Se denuncia en este segundo motivo de casación, primero de carácter sustantivo, en virtud de lo dispuesto en los arts. 477.2 y 3 LEC, por interés casacional, la oposición de la sentencia recurrida a la doctrina jurisprudencial del Tribunal Supremo y, en concreto, la emanada de las SSTS —Pleno— 540/2013 de 13 de septiembre de 2013 —rec. 281/2013—, y 778/2014 de 20 de enero de 2015 —rec. 196/2013—; al aplicar los arts. 1, 3 y 7 de la hoy derogada Ley 57/1968, de 27 de julio, sobre percibo de cantidades anticipadas en la construcción y venta de viviendas.

En las mismas se declara que la garantía establecida por dicha ley para la devolución de las cantidades anticipadas por el comprador no tenía un carácter accesorio mientras la vivienda no estuviera terminada y en disposición de ser entregada. Se trata no de un aval sino un seguro de caución, ajustada al espíritu y finalidad de la mencionada ley, y que cualquier duda interpretativa debía resolverse aplicando la Constitución, en especial sus arts. 47 y 51 en cuanto el primero reconoce el derecho a disfrutar de una vivienda digna y el segundo impone a los poderes públicos garantizar la defensa de los consumidores y usuarios, de manera que la protección legal de los compradores de viviendas no podía ser en la actualidad inferior a la que tenían en 1968. La sentencia impugnada opta por la solución contraria, considerando que se trata de un aval, de carácter accesorio, y concluye que la demandada no debe devolver las cantidades que se reclaman por un importe global de [IMPORTE] euros.

TERCER MOTIVO

SUPLICO DE LA SALA

Que teniendo por presentado este escrito, con los documentos que acompaña, se sirva admitirlo y, en su mérito, tener por interpuesto en tiempo y forma RECURSO DE CASACIÓN contra la sentencia de fecha [FECHA], remitiéndose por el Letrado de la Administración de Justicia los autos originales a la Sala Primera del Tribunal Supremo, para que, por dicho tribunal «ad quem», previa su admisión, se dicte sentencia en la que, estimando el citado recurso, acuerde casar la sentencia impugnada, reponiendo actuaciones al momento procesal anterior la comisión de la infracción normativa de carácter procesal cometida y acreditada, si se estimare el primer motivo del presente recurso, y resolviendo sobre el fondo en otro caso; con imposición de las costas causadas en la Primera Instancia a la contraparte, y demás proceda en Derecho.

PRIMERO OTROSI DIGO: Que estimando esta parte necesaria la celebración de vista [COMPLETAR],

SUPLICO A LA SALA

Tenga por solicitado se acuerde en su día por el tribunal la celebración de vista del presente recurso [COMPLETAR].

Que tenga por efectuadas las anteriores manifestaciones y en relación a la prueba propuesta acuerde la admisión de la misma con señalamiento de vista para su práctica en el mismo auto de admisión de la apelación, previa a la resolución de las presentes actuaciones.

SEGUNDO OTROSÍ DIGO: Que en cumplimiento de lo dispuesto en la DA 15ª LOPJ, adjunto al presente escrito resguardo de ingreso por importe de cincuenta euros (50 euros), en la cuenta expediente número de la cuenta de depósitos y consignaciones de la Audiencia Provincial como justificación del pago del depósito como requisito necesario para la interposición del recurso de casación [COMPLETAR].

SUPLICO A LA SALA

Que tenga por efectuadas las anteriores manifestaciones a los efectos legales oportunos y, una vez dictada la resolución definitiva por la que se acuerde la revocación de la resolución objeto del recurso extraordinario por infracción procesal y casación, que ahora se interpone, se acuerde en la misma la devolución a mi mandante del depósito consignado mediante mandamiento expedido por el Letrado de la Administración de Justicia.

TERCERO OTROSÍ DIGO: Que de acuerdo con lo establecido en el art. 481.6 LEC, en la redacción dada por el Real Decreto-Ley 5/2023, de 28 de junio, se acompaña a este escrito copia con firma electrónica/con código seguro de verificación/certificación de la sentencia impugnada.

SUPLICO A LA SALA

Tenga por aportadas tal documentación a los efectos procesales oportunos.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) Breve resumen del motivo

(2) Desarrollo del motivo

========================================================================
