---
name: demanda-contra-aseguradora-impago-cobertura-sanitaria-131
description: "Redacta el escrito «Demanda contra la aseguradora por impago de cobertura sanitaria» (formulario 131 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda contra la aseguradora por impago de cobertura sanitaria

> Formulario 0131 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.

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
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] IMPORTE (6 veces)
- [ ] FECHA (8 veces)
- [ ] Nº DE DOCUMENTO (5 veces)
- [ ] Nº
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…do/a de la Administración de Justicia de»; «…ual dirijo contra la entidad aseguradora»; «…entidad demandada, con fecha de vigencia»; «…, por el Dr»; «…cual se debía realizar en el Hospital de»; «…( se acompaña como documentos»; «… diferentes informes médicos y el del Dr»; «… misma se llevó a cabo en el Hospital de»; «…a ……., que fue contestado por la entidad»; «…me pericial relacionados en el anexo. En»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 45 y 52 de la LEC
- artículo 249.2 de la LEC
- artículo 394 LEC
- artículos 251 y 252 de la LEC
- Ley Orgánica 1/2025

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

### Formulario 0131 · Demanda contra la aseguradora por impago de cobertura sanitaria

- Año del modelo: 2022
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 38 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D/Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales en representación de D/Dña. [NOMBRE Y APELLIDOS] según acredito por certificación del registro electrónico de apoderamientos judiciales que acompaño o mediante designación apud-acta otorgado ante el/la Letrado/a de la Administración de Justicia de [COMPLETAR], bajo la dirección letrada de D/Dña. [NOMBRE Y APELLIDOS], Abogado/a del Iltre. Colegio de [LOCALIDAD], ante el Tribunal comparezco y como mejor en derecho proceda DIGO:

Que, por medio de la presente, formulo demanda de juicio ordinario en ejercicio de la acción de reclamación de cantidad por impago de la cantidad de [IMPORTE] euros cubiertos por la póliza de seguro de asistencia sanitaria suscrito en fecha [FECHA], la cual dirijo contra la entidad aseguradora [COMPLETAR], con domicilio en [LOCALIDAD], en base a los siguientes

HECHOS

PRIMERO.- Se insta en este proceso demanda en reclamación de la cantidad de [IMPORTE] euros por el impago de los gastos de asistencia sanitaria cubiertos por el contrato de seguro de salud suscrito con la entidad demandada.

El día [FECHA], mi representada suscribió contrato de seguro con la entidad demandada, con fecha de vigencia [COMPLETAR], con prima anual por importe de [IMPORTE] euros, siendo tomadora mi representada y asegurados mi representada y sus hijos D/Dª [NOMBRE Y APELLIDOS] y D/Dª [NOMBRE Y APELLIDOS].

El seguro tenía por objeto la cobertura de asistencia sanitaria, describiéndose en la póliza dos modalidades, como son la prestación de asistencia sanitaria a través del cuadro y servicios médicos de la aseguradora y la de reembolso de gastos sanitarios cuando no sea posible su prestación, constando en esta segunda modalidad los límites de reembolso por asistencia ambulatoria, asistencia hospitalaria distinguiendo entre la normal, en cuidados intensivos o por tratamiento completo, por trasplantes, prótesis, honorarios médicos por intervención quirúrgica y tratamientos especiales, asistencia de maternidad y enfermedades congénitas Igualmente se establecen las especialidades, prestaciones sanitarias y servicios cubiertos, entre las cuales se encuentran la de hospitalización, tratamientos especiales, trasplantes de órganos y otros servicios entre los que se incluyen los traslados en ambulancia, matronas, preparación al parto, podología y psicología.

(acompaño como documentos número [Nº DE DOCUMENTO] póliza de seguro suscrita en fecha [FECHA], recibos del pago de las primas y condiciones generales de la entidad aseguradora).

SEGUNDO.- Mi representada precisó asistencia sanitaria como consecuencia de una grave patología por trastornos en su metabolismo, y tras agotar las diferentes alternativas, le fue prescrita intervención quirúrgica en fecha [FECHA], por el Dr [COMPLETAR], consistente en bypass gástrico por vía robótica-laparoscópica de una sola anastomosis, la cual se debía realizar en el Hospital de [COMPLETAR] con fecha prevista para el día [FECHA] ( se acompaña como documentos [COMPLETAR] historia clínica de mi representada, en el que se incluyen diferentes informes médicos y el del Dr [COMPLETAR] sobre la necesidad de la operación de bypass gástrico).

El mismo día, mi representada solicitó autorización a la aseguradora para llevar a cabo dicha operación por la modalidad de reembolso de gastos, al no existir posibilidad alguna de realizar la intervención citada de cirugía robótica a través de los servicios de la aseguradora ( se acompaña como documento número [Nº DE DOCUMENTO] solicitud de fecha [FECHA] cursada a la entidad aseguradora).

Llegada la fecha prevista para la intervención quirúrgica sin haber recibido respuesta de la aseguradora, la misma se llevó a cabo en el Hospital de [COMPLETAR], precisando de un periodo de hospitalización de [Nº] días.

Mi representada abonó los honorarios médicos y gastos de hospitalización cuyo importe ascendió a [IMPORTE] euros, tal como se acredita por la factura que se acompaña como documento número

TERCERO.- En fecha [FECHA], mi representada formuló solicitud en reclamación de reembolso de los gastos satisfechos por la intervención quirúrgica y hospitalización, de acuerdo a lo pactado en la póliza, tal como se acredita por el burofax que se acompaña como documento número [Nº DE DOCUMENTO].

En fecha [FECHA], el departamento de servicio al cliente de la aseguradora demandada informó a mi representada de la imposibilidad de autorizar la intervención y reembolsar los gastos por no estar contemplada la prestación en las coberturas de la cartera de servicios de la póliza de reembolso suscrita, y que la cláusula quinta de las condiciones generales establecía la exclusión de aquellas técnicas diagnósticas y quirúrgicas cuyo uso no sea habitual y aceptado en el Sistema Nacional de Salud, entre las que se encontraba la cirugía robótica utilizada en la intervención de mi representada.

CUARTO.- Se ejercita esta acción al entender que los gastos reclamados están dentro de la cobertura de asistencia sanitaria suscrita en el contrato de seguro.

La entidad aseguradora demandada no ha actuado de buena fe, pues omitió cualquier respuesta al solicitarse la autorización y, posteriormente, al solicitar el reembolso de los gastos se acoge a una condición general limitativa de los derechos del asegurado que restringe y excluye el derecho del asegurado a la indemnización por la prestación garantizada en el contrato, incluyéndose en las condiciones generales sin reunir la necesaria transparencia contractual en los contratos de seguro.

Debe subrayarse que la cláusula del condicionado general a que se acoge la aseguradora no se recogía en el condicionado particular, ni estaba destacada en el contrato, ni en definitiva fue específicamente aceptada por mi representada, por lo que en ningún momento puede pretenderse su aplicación.

En consecuencia, nos vemos en la obligación de ejercitar la presente acción jurisdiccional por impago de los gastos de asistencia sanitaria cubiertos por la póliza, la cual deberá incrementarse con los intereses correspondientes conforme a lo dispuesto en el art. 20 de la LCS.

QUINTO.- Mi representado envío un requerimiento fehaciente al demandado con fecha ……., que fue contestado por la entidad [COMPLETAR], en los siguientes términos

Acompaño como documento número [Nº DE DOCUMENTO], el requerimiento efectuado y como documento número [Nº DE DOCUMENTO], la contestación de la aseguradora.

FUNDAMENTOS DE DERECHO

PRIMERO.- Competencia.- Corresponde la competencia para conocer de esta clase de procesos al Tribunal de Instancia al que me dirijo, por ser el del domicilio del asegurado, por aplicación del art. 45 y 52 de la LEC, y art. 24 de la LCS.

SEGUNDO.- Legitimación.-Le corresponde a esta parte la legitimación activa en su condición de asegurada, en tanto que la legitimación pasiva corresponde a la entidad aseguradora demandada.

TERCERO.- Procedimiento: Es el proceso ordinario con fundamento en el artículo 249.2 de la LEC, al exceder la cuantía del proceso de 15.000 euros.

CUARTO.- Cumplimiento de los requisitos de procedibilidad: La presente demanda cumple con el requisito de procedibilidad exigido por la DA 7ª de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

QUINTO.- Acción ejercitada: El art. 1 de la Ley de Contrato de Seguro establece: “el contrato de seguro es aquel por el que el asegurador se obliga, mediante el cobro de una prima y para el caso de que se produzca el evento cuyo riesgo es objeto de cobertura a indemnizar, dentro de los límites pactados, el daño producido al asegurado o a satisfacer un capital, una renta u otras prestaciones convenidas”.

En cuanto al seguro de asistencia sanitaria, el art. 105 de la LCS establece: “cuando el riesgo asegurado sea la enfermedad, el asegurador podrá obligarse, dentro de los límites de la póliza, en caso de siniestro, al pago de ciertas sumas y de los gastos de asistencia médica y farmacéutica. Si el asegurador asume directamente la prestación de los servicios médicos y quirúrgicos, la realización de tales servicios se efectuará dentro de los límites y condiciones que las disposiciones reglamentarias determinan”.

Asimismo, es de aplicación lo establecido en el artículo 3 de la LCS en tanto que no nos encontramos ante una cláusula delimitadora del riesgo cubierto, sino ante una cláusula limitativa que requiere una expresa aceptación que aquí no se ha producido.

SEXTO.- Intereses: Es de aplicación el art. 20 de la LCS, que establece que la indemnización por mora se impondrá de oficio por el órgano judicial y consistirá en el pago de un interés anual igual al del interés legal del dinero vigente en el momento en que se devengue, incrementado en el 50 por 100; estos intereses se considerarán producidos por días, sin necesidad de reclamación judicial. No obstante, transcurridos dos años desde la producción del siniestro, el interés anual no podrá ser inferior al 20 por 100.

SÉPTIMO.- Costas: En materia de costas, el artículo 394 LEC señala que las de primera instancia se imponen a la parte que vea en primera instancia rechazadas sus pretensiones.

En base a lo anterior,

SUPLICO AL TRIBUNAL que tenga por presentada la presente demanda con los documentos a ella adjuntos y sus copias, en la representación que ostento, y se tenga por formulada demanda de acción de reclamación de cantidad por impago de los gastos de asistencia sanitaria cubiertos por el contrato de seguro suscrito por mi representada, y en su virtud se dicte sentencia por la que, de acuerdo a lo expuesto en esta demanda, se condene a la aseguradora demandada a que indemnice a mi mandante en la cantidad de [IMPORTE] euros, con más el interés moratorio del art. 20 de la LCS, todo ello con condena en costas a los citados demandados.

OTROSÍ PRIMERO DIGO que, de conformidad con lo dispuesto en los artículos 251 y 252 de la LEC, se fija la cuantía del presente procedimiento en [IMPORTE] euros.

SUPLICO AL TRIBUNAL se tenga por efectuada la anterior manifestación a los efectos pertinentes.

OTROSÍ SEGUNDO DIGO que se acompaña en anexo relación de documentos, debidamente foliados y con índice electrónico, para su debida localización y consulta.

SUPLICO AL TRIBUNAL tenga hecha esta manifestación a los efectos oportunos y por aportados los documentos e informe pericial relacionados en el anexo.

En [COMPLETAR]

Firma Abogado/a Firma Procurador/a
