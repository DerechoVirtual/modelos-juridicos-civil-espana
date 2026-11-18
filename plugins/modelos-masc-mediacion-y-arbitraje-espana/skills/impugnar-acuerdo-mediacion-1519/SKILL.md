---
name: impugnar-acuerdo-mediacion-1519
description: "Redacta el escrito «Impugnar un acuerdo de mediación» (formulario 1519 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Impugnar un acuerdo de mediación

> Formulario 1519 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (8 veces)
- [ ] Nº DE EXPEDIENTE
- [ ] LOCALIDAD (2 veces)
- [ ] IMPORTE (7 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] ACTO O RESOLUCIÓN
- [ ] LUGAR
- [ ] Otros 18 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «…de [COMPLETAR] de»; «…de»; «…de [COMPLETAR] de»; «…iones sufridas (acompaño como documentos»; «…de»; «…de [COMPLETAR] de»; «…trabajando en la empresa de construcción»; «…de»; «…de [COMPLETAR] de»; «…á trabajando actualmente para la empresa»; «…de»; …

## Párrafos opcionales (1)

Inclúyelos solo si encajan en los hechos:

- OTROSÍ DIGO Que estando la presente demanda sujeta al abono de la tasa por el ejercicio de la potestad jurisdi…

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 23.4 de la Ley 5/2012
- art. 1265 del Código Civil
- art. 1269 del Código Civil
- arts. 50 de la LEC
- art. 249.2 de la LEC
- art. 23.4 de la Ley 5/2012
- artículo 7.2 de la Ley 10/2012
- Ley 25/2015

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

### Formulario 1519 · Impugnar un acuerdo de mediación

- Año del modelo: 2014
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 1 párrafos opcionales señalados; 41 campos de relleno marcados en blanco; 5 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)
- Avisos de la revisión: REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Receptor
Hechos
Fundamentos de derecho
Firmas

Demanda de nulidad de acuerdo de mediación.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D. [NOMBRE Y APELLIDOS] Procurador de los Tribunales, actuando en representación de [NOMBRE DEL REPRESENTADO/A], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, por medio de la presente, al amparo de lo dispuesto en el artículo 23.4 de la Ley 5/2012, de 6 de julio, de mediación en asuntos civiles y mercantiles, formulo demanda de impugnación del acuerdo de mediación de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] alcanzado en expediente de mediación número [Nº DE EXPEDIENTE], demanda que dirijo contra D. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], en base a los siguientes

Hechos

Mi representado y el demandado iniciaron un procedimiento de mediación con motivo del accidente sufrido por el demandado cuando fue contratado por mi representado para realizar unas reparaciones en el tejado de su vivienda en fecha [FECHA] de [COMPLETAR] de [COMPLETAR] Al realizar los trabajos de reparación, el techo de la vivienda de mi representado cedió por su mal estado, cayendo el demandado al piso inferior y sufriendo lesiones.

Para dirimir la controversia, se siguió procedimiento de mediación ante el mediador D. [NOMBRE Y APELLIDOS], alcanzado las partes un acuerdo en virtud del cual mi representado se comprometía a indemnizar al demandado en la cantidad de [IMPORTE] euros por las lesiones sufridas (acompaño como documentos [COMPLETAR] copia del expediente de mediación y del acuerdo de mediación de fecha [FECHA] de [COMPLETAR] de [COMPLETAR]).

La impugnación de lo convenido en mediación viene originada por el dolo con que actuó el demandado al simular que las lesiones sufridas le incapacitaron completamente para su trabajo habitual, cuando lo cierto es que mi representado ha tenido conocimiento posterior que el demandado está trabajando en la empresa de construcción [COMPLETAR], realizando el mismo trabajo para el que fue contratado y con una antigüedad anterior al inicio del procedimiento de mediación, lo que patentiza el dolo con el que ha actuado.

En efecto, la mala fe con que actuó el demandado se constata por la mera lectura del acuerdo de mediación acompañado como documento número [Nº DE DOCUMENTO], concretamente en el apartado tercero, cuando el demandado manifiesta expresamente que como consecuencia de las lesiones sufridas está impedido para realizar cualquier tipo de trabajo, habiendo solicitado la invalidez permanente ante el Instituto Nacional de la Seguridad Social, lo cual determinó que se fijara una indemnización por el elevado importe de [IMPORTE] euros por tratarse de lesiones que produjeron una «incapacidad permanente».

Mi representado, en la lícita creencia que el demandado actuaría con la exigible buena fe que debe informar su conducta, dio por ciertas las afirmaciones de que estaba totalmente impedido para trabajar, según las lesiones que constaban en el informe médico de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] que aportó el demandado en el procedimiento de mediación, y lógicamente también creyó de buena fe que el demandado había solicitado la invalidez permanente como consecuencia de este desgraciado accidente, por lo cual otorgó su consentimiento a la pretensión del demandado a ser indemnizado dicho concepto, abonando la indemnización convenida en el acuerdo de mediación.

Sin embargo, tales hechos han resultado absolutamente falsos, puesto que el demandado está trabajando actualmente para la empresa [COMPLETAR], incluso desde antes de iniciarse el procedimiento de mediación como acreditaremos oportunamente, y desde luego no tiene ninguna incapacidad para desarrollar su trabajo, como falsamente afirmó en el procedimiento de mediación.

De los hechos expuestos queda constatado que el consentimiento prestado por esta parte se obtuvo como consecuencia de la conducta dolosa del demandado, quien a sabiendas creó una apariencia de estar impedido para desarrollar su trabajo, simulando estar en situación de incapacidad permanente, con el único fin de ser indemnizado por mi representado, quien satisfizo la cantidad de [IMPORTE] euros por este concepto en cumplimiento del acuerdo de mediación.

Por este motivo, es de aplicación el art. 1265 del Código Civil que establece la nulidad del consentimiento prestado por dolo, siendo que la conducta del demandado reúne los dos requisitos de la conducta dolosa establecidos en el art. 1269 del Código Civil como son el subjetivo, o ánimo de perjudicar al actor, obteniendo una indemnización a la que no tenía derecho, y el objetivo, al simular consciente y deliberadamente una situación de incapacidad para su trabajo que no tenía.

Asimismo, y de conformidad a lo dispuesto en el art. 1303 y siguientes del Código Civil, el demandado debe indemnizar a esta parte por los daños y perjuicios sufridos que comprenden las cantidades ya satisfechas, que ascienden a [IMPORTE] euros, y el interés moratorio de dichas cantidades desde el [FECHA] de [COMPLETAR] de [COMPLETAR], fecha de la entrega, que asciende a [IMPORTE] euros.

Por lo expuesto, se ejercita acción de nulidad, conforme a lo dispuesto en el art. 23.4 de la LM, pretendiendo la indemnización de daños y perjuicios derivada de la conducta dolosa del demandado.

Fundamentos de derecho

Primero.– Competencia

Corresponde a las secciones civiles de los tribunales de instancia de [LOCALIDAD], conforme a lo dispuesto en los arts. 50 de la LEC y 85.1º LOPJ.

Segundo.– Procedimiento y cuantía

Debe seguirse el proceso ordinario conforme a lo dispuesto en el art. 249.2 de la LEC y siendo la cuantía de este proceso la de [IMPORTE] euros.

Tercero.– Legitimación

Le corresponde a esta parte la legitimación activa y la pasiva al demandado, conforme a lo que dispone el artículo 23.4 de la Ley 5/2012.

Cuarto.– Acción ejercitada

Es de aplicación lo dispuesto en el art. 23.4 de la Ley 5/2012 que establece que «contra lo convenido en el acuerdo de mediación sólo podrá ejercitarse la acción de nulidad por las causas que invalidan los contratos», lo que debe ser puesto en relación con lo dispuesto en los arts. 1265, 1269, 1270 y concordantes del Código Civil. El art. 1265 del C .Civil determina que «será nulo el consentimiento prestado por error, violencia, intimidación o dolo», a la vez que el art. 1269 del Código Civil establece que «hay dolo cuando, con palabras o maquinaciones insidiosas de parte de uno de los contratantes, es inducido el otro a celebrar un contrato que, sin ellas, no hubiera hecho».

Quinto.– Efectos

Articulos 1300 y siguientes del Código Civil.

Sexto.– Costas

Artículo 394 LEC, debiéndose imponer las costas al demandado por su mala fe.

En base a lo anterior,

SUPLICO AL TRIBUNAL que tenga por presentada la presente demanda con los documentos a ella adjuntos y sus copias, en la representación que ostento, y se tenga por formulada demanda de juicio ordinario contra [ACTO O RESOLUCIÓN] en impugnación del acuerdo de mediación de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] y en su virtud, tras los trámites legales, se dicte sentencia por la que se declare la nulidad del acuerdo de mediación de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] y se condene al demandado a indemnizar a mi representado en la cantidad de [IMPORTE] euros, con más los intereses correspondientes, todo ello con condena en costas al demandado.

[OPCIONAL — incluir si procede]

OTROSÍ DIGO Que estando la presente demanda sujeta al abono de la tasa por el ejercicio de la potestad jurisdiccional fijada por la Ley 10/2012, de 20 de noviembre, modificada por RDL 3/2013 y Ley 25/2015, de 28 julio, y desarrollada por Orden HAP/2662/2012, de 13 de diciembre, siendo mi representada personas jurídica no exenta de su pago, se acompaña a la presente demanda como documento nº [Nº DE DOCUMENTO] la correspondiente autoliquidación con el ejemplar para la Administración de Justicia debidamente validado y en el que consta el pago de la cantidad de 300 euros correspondiente a la cuota fija [COMPLETAR], sin que se incluya la cuota variable prevista en el artículo 7.2 de la Ley 10/2012 al haber sido declarado inconstitucional y nulo por la STC 140/2016, de 21 de julio.

En virtud de lo anterior,

SUPLICO AL TRIBUNAL que tenga por hecha la anterior manifestación a los efectos pertinentes y por acompañado el documento justificativo del abono de la tasa.

En [LUGAR], a [FECHA].

Abogado/a	Procurador/a

Fdo. D./Dña. [NOMBRE Y APELLIDOS]: 	Fdo. D./Dña. [NOMBRE Y APELLIDOS]:

========================================================================
