---
name: casacion-interes-casacional-normas-sin-doctrina-448
description: "Redacta el escrito «Casación por interés casacional: normas sin doctrina jurisprudencial del Tribunal Supremo» (formulario 448 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Casación por interés casacional: normas sin doctrina jurisprudencial del Tribunal Supremo

> Formulario 0448 del plugin **Recursos civiles** · revisado el 17-11-2026.

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
- [ ] ACTO O RESOLUCIÓN
- [ ] FECHA (4 veces)
- [ ] DESCRIBIR
- [ ] Nº DE EXPEDIENTE
- [ ] LUGAR
- [ ] Otros 28 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…a procesal de la LO 1/2025. A LA SECCIÓN»; «…editada en los autos de juicio ordinario»; «…condiciones generales de la contratación»; «…tras la reforma operada por la Ley /, de»; «…, de»; «…dispuesto en su DF 1ª, entró en vigor el»; «…correspondiente Tribunal de Instancia el»; «…de contenido diferente, en cuanto que no»; «…tras la reforma operada por la Ley /, de»; «…, de»; «…12 de la LCGC en similares términos de «»; «…tras la reforma operada por la Ley /, de»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 477.2 LEC
- arts. 477.2 y 3 LEC
- arts. 17.2 y 12.3 de la Ley 7/1998
- artículo 12.3, de la Ley 7/1998
- artículo 12 de la Ley 7/1998
- artículo 1 de la Ley 7/1998
- art. 481.6 LEC
- Ley 5/2023
- Ley 1/2000
- Real Decreto Legislativo 1/2007

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

### Formulario 0448 · Casación por interés casacional: normas sin doctrina jurisprudencial del Tribunal Supremo

- Año del modelo: 2018
- Revisión 17-11-2026: 3 citas normativas corregidas tras comprobarlas en el BOE; restos de formato retirados; notas del formulario agrupadas al final (2); 40 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Interposición de recurso de casación ante la Sala Primera del Tribunal Supremo, al amparo de los artículos 477.2, primer inciso, y 477.3 LEC [NOTA DE REVISIÓN: Las modalidades de interés casacional (oposición a doctrina del TS, jurisprudencia contradictoria de AP, norma sin doctrina) están en el art. 477.3. Fuente: LEC arts. 477.1-3 (redacc. RDL 5/2023, BOE-A-2023-15135; apdo. 1 también RDL 6/2023).], cuando la resolución recurrida aplique normas sobre las que no existiese doctrina jurisprudencial del Tribunal Supremo, adaptado al RDL 5/2023.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN [COMPLETAR] DE LA AUDIENCIA PROVINCIAL DE [LOCALIDAD]

[NOTA DE REVISIÓN: Errata. La Audiencia Provincial no cambia de denominación; sus Secciones se identifican por su número. Fuente: LOPJ arts. 80 y 82 (Audiencia Provincial, sin cambio de denominación).]

Autos nº [Nº DE PROCEDIMIENTO]

Rollo de apelación nº [Nº DE PROCEDIMIENTO]

D./Dª. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre de D./Dª. [NOMBRE Y APELLIDOS], cuya representación tengo debidamente acreditada en los autos de juicio ordinario [COMPLETAR], sobre ejercicio de acción colectiva de retractación contra la recomendación de utilización de condiciones generales de la contratación [COMPLETAR], seguido a nuestra instancia contra [ACTO O RESOLUCIÓN], ante la Sala comparezco y, como mejor proceda en Derecho, DIGO:

Que, por medio del presente escrito, al amparo de lo dispuesto en el art. 477.2 LEC en la redacción dada por el Real Decreto-Ley 5/2023, de 28 de junio, y dentro del plazo legal, interpongo en nombre de D./Dª [NOMBRE Y APELLIDOS]. RECURSO DE CASACION ante la Sala Primera del Tribunal Supremo, contra la sentencia de fecha [FECHA] dictada por esta Audiencia Provincial, en grado de apelación, y notificada en fecha [FECHA]; en los autos de juicio ordinario al margen referenciados, con arreglo a los motivos siguientes:

1.- Enumeración de los Motivos (1)

El presente recurso de casación se interpone en virtud de los siguientes motivos:

PRIMER MOTIVO

En virtud de lo dispuesto en los arts. 477.2 y 3 LEC, por interés casacional, se denuncia incorrecta aplicación de precepto legal, sin que conste la existencia de doctrina jurisprudencial de normas anteriores de igual o similar contenido.

En concreto, al desestimarse la demanda en función de la falta de legitimación pasiva "ad causam" de la parte demandada, la sentencia impugnada interpreta incorrectamente los arts. 17.2 y 12.3 de la Ley 7/1998, de 13 de abril, sobre Condiciones Generales de Contratación, tras la reforma operada por la Ley /, de [COMPLETAR], de [COMPLETAR]. Dicha norma, en función de lo dispuesto en su DF 1ª, entró en vigor el [COMPLETAR], y fue invocada en el presente procedimiento en el escrito de contestación con fecha de entrada en el correspondiente Tribunal de Instancia el [COMPLETAR]. Asimismo, la norma por ella sustituida, de contenido diferente, en cuanto que no [COMPLETAR], tampoco ha sido objeto de análisis por jurisprudencia del Tribunal Supremo que se conozca por esta parte.

SEGUNDO MOTIVO

2.- Justificación de los Motivos (2)

PRIMER MOTIVO

Como se ha indicado, el primer motivo que se esgrime en el presente recuso es el interés casacional dimanante de la incorrecta aplicación de precepto legal, sin que conste la existencia de doctrina jurisprudencial de normas anteriores de igual o similar contenido.

Es decir, se denuncia la infracción, en concepto de violación o errónea interpretación del artículo 17.2, en relación con el artículo 12.3, de la Ley 7/1998, de 13 de abril, sobre Condiciones Generales de la Contratación, que, entiende esta parte, se comete al apreciar la sentencia recurrida la falta de legitimación pasiva «ad causam» que opusiera la parte demandada apelante en base a no haber sido utilizada en ocasión alguna por ningún predisponente la condición general que se considera nula, ya que tras la reforma operada por la Ley /, de [COMPLETAR], de [COMPLETAR], ya no es preciso que dicha condición general haya sido efectivamente usada, bastando en consecuencia para la procedencia de la acción de retractación que exista una posibilidad de ser usada o que se haya previsto su utilización.

Por la acción de retractación residenciada en el nº 3 del artículo 12 de la Ley sobre Condiciones Generales de la Contratación de 13 de abril de 1998 (en adelante, LCGC), se pretende obtener una sentencia que declare e imponga al demandado, sea o no predisponente, el deber de retractarse de la recomendación que haya efectuado de utilizar condiciones generales de la contratación que sean consideradas nulas, así como de abstenerse en un futuro de seguir recomendándolas, siendo presupuesto básico de la misma que previamente esas condiciones generales de la contratación hayan sido declaradas nulas por contrarias a la propia LCGC o a cualquier otra ley imperativa o prohibitiva, declaración de nulidad que habrá de ser decretada en el mismo proceso, siendo no obstante factible que dicha declaración se haya producido previamente en proceso anterior sobre nulidad o cesación. Conforme al artículo 16.3 de la LCGC, se encuentran legitimadas para el ejercicio de la acción de retractación las asociaciones de consumidores y usuarios que reúnan los requisitos establecidos en la Ley General para la Defensa de los Consumidores y Usuarios, o, en su caso, en la legislación autonómica en materia de defensa de los consumidores, circunstancias cuya concurrencia en la demandante, amén de probada, no ha sido cuestionada en el proceso; en tanto que la legitimación pasiva corresponderá, según la literalidad del artículo 17.2 de la LCGC, a cualquier profesional (en el sentido del artículo 2.2 de la LCGC) «que recomiende públicamente la utilización de determinadas condiciones generales que se consideren nulas o manifieste de la misma manera su voluntad de utilizarlas en el tráfico, siempre que en alguna ocasión hayan sido efectivamente utilizadas por algún predisponente».

Este último requisito de que las condiciones generales "hayan sido utilizadas en alguna ocasión" se encontraba también recogido inicialmente en el último inciso del apartado 3 del artículo 12 de la LCGC en similares términos de « [COMPLETAR], siempre que hayan sido efectivamente utilizadas por el predisponente en alguna ocasión», pero, sin embargo, esta última mención desapareció tras la reforma operada por la Ley /, de [COMPLETAR], de [COMPLETAR]. En efecto, el legislador por Ley 1/2000 de Enjuiciamiento Civil modificó, entre otros, el apartado 3 del artículo 12 de la Ley 7/1998, de 13 de abril, referido a la acción de retractación, suprimiendo el requisito recogido en el último inciso del anterior apartado 3 que exigía que esas condiciones generales de la contratación "hayan sido efectivamente utilizadas por el predisponente en alguna ocasión" (Disposición final sexta de la Ley 1/2000), y así pues a partir de esa reforma, como ya se dejó dicho, ya no es necesario que las condiciones generales de la contratación contra las que se accione hayan sido utilizadas.

El problema se plantea en cuanto que, si bien hubiese sido lógico y consecuente que también se hubiese modificado por el legislador el apartado 2 del artículo 17 de la LCGC, referido a la legitimación pasiva en la acción de retractación, eliminando el último inciso del mismo y suprimiendo, con ello, el requisito de la previa utilización efectiva por algún predisponente, sin embargo ello no ha acaecido así, manteniéndose dicho inciso final del apartado 2 del artículo 17 en una regulación de la legitimación pasiva claramente contradictoria en su relación con el artículo 12.3.

Pues bien la Sala sentenciadora, realizando una interpretación literal del apartado 2 del artículo 17, en una hermenéutica que se antoja poco recomendable por cerrada y rígida, estima que esta parte hoy recurrente carece de acción contra el demandado --en quien, no obstante, declara probado concurren los requisitos de profesionalidad y recomendación pública de la utilización de la condición general que se considera nula--, por el hecho de no haber sido utilizada en ninguna ocasión por predisponente alguno dicha condición general, en tanto que entendemos que una interpretación según el contexto (art. 3º.1 CC) aconseja poner en conexión ese apartado 2 del artículo 17 con el apartado 3 del artículo 12, en su redacción dada por Ley 1/2000, entre los que se presupone debe haber coherencia e interdependencia, que deben llevar a entender también eliminado el requisito de la previa utilización a efectos de legitimación del demandado, pues entenderlo de otra manera es tanto como vaciar de contenido la reforma operada por el legislador. Conclusión a la de igual modo se llega de seguirse las reglas de la lógica jurídica, que proscriben la contradicción y los resultados absurdos, no encontrándose razón alguna para que el legislador haya suprimido el tan mentado requisito de la previa utilización de la condición general de la contratación como presupuesto básico para el ejercicio de la acción de retractación, y no lo haya hecho cuando disciplina quien se encuentra legitimado para soportar las consecuencias dicho ejercicio.

El razonamiento precedente, entendemos, merece ser acogido y permite concluir que la demandante tiene acción contra el demandado, no obstante la falta de utilización hasta la fecha de la condición general objeto de litis, y, ello así, declarado probado por la sentencia recurrida que Don [COMPLETAR] recomendó públicamente, con ocasión de su intervención profesional en las jornadas sobre [DESCRIBIR] celebradas en [COMPLETAR] los días [COMPLETAR] y [COMPLETAR] de [COMPLETAR] de [COMPLETAR], la utilización por las empresas concesionarias del servicio público de [COMPLETAR], en su contratación con los usuarios de dicho servicio, de la cláusula que dice «», y no cabiendo duda alguna de que la cláusula en cuestión reúne todos los requisitos para ser calificada como condición general, tal y como aparecen definidas en el artículo 1 de la Ley 7/1998, de 13 de abril, sobre Condiciones Generales de la Contratación, es decir, «predisposición e incorporación al contrato impuesta por la empresa suministradora y redacción con la finalidad de ser incorporadas a una pluralidad de contratos», circunstancias todas ellas probadas en autos, la demanda interpuesta por esta parte ha de ser estimada, en cuanto que la nulidad de pleno derecho de la cláusula que se combate deviene de su inclusión sin la preceptiva autorización administrativa, según resulta de lo dispuesto en el artículo [COMPLETAR] del Reglamento de [COMPLETAR], de acuerdo con el número 3 del artículo 81 del Texto Refundido de la Ley General para la Defensa de los Consumidores y Usuarios, aprobado por Real Decreto Legislativo 1/2007, de 16 de noviembre, precepto que exige la aprobación por la Administración competente de las cláusulas que utilicen las empresas concesionarias de servicios públicos cuando así se disponga como requisito de validez, procediendo, en consecuencia, declarar su nulidad y asimismo declarar e imponer al demandado aquí recurrido el deber de retractarse de la recomendación efectuada de utilización de la cláusula declarada nula y de abstenerse de seguir haciéndolo en el futuro.

SEGUNDO MOTIVO

Por todo lo expuesto,

SUPLICO A LA SALA

Que teniendo por presentado este escrito, con los documentos que acompaña, se sirva admitirlo y, en su mérito, tener por interpuesto en tiempo y forma RECURSO DE CASACION contra la sentencia de fecha [FECHA] de [COMPLETAR] de [COMPLETAR], remitiéndose por el Letrado de la Administración de Justicia los autos originales a la Sala Primera del Tribunal Supremo, para que, por dicho tribunal «ad quem», previa su admisión, se dicte sentencia estimándolo, casando la sentencia recurrida y, recuperando la instancia, estimando íntegramente la demanda formulada por esta parte contra DON [COMPLETAR], haciendo el pronunciamiento procedente conforme a Ley sobre costas de las instancias, y sin declaración especial respecto de las del presente recurso.

OTROSI DIGO: Que estimando esta parte necesaria la celebración de vista [COMPLETAR],

SUPLICO A LA SALA

Tenga por solicitado se acuerde en su día por el tribunal «ad quem» la celebración de vista del presente recurso [COMPLETAR].

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
