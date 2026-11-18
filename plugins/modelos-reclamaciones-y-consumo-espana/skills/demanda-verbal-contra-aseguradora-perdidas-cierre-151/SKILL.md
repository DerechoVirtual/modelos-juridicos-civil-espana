---
name: demanda-verbal-contra-aseguradora-perdidas-cierre-151
description: "Redacta el escrito «Demanda verbal contra aseguradora por pérdidas del cierre del negocio por COVID» (formulario 151 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda verbal contra aseguradora por pérdidas del cierre del negocio por COVID

> Formulario 0151 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD (5 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] FECHA (5 veces)
- [ ] IMPORTE (8 veces)
- [ ] Nº (6 veces)
- [ ] ÓRGANO (2 veces)
- [ ] NÚMERO
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…D»; «…rado de la Administración de Justicia de»; «…que dirijo contra la entidad aseguradora»; «…, sito en [LOCALIDAD] de la población»; «…euros. En la página»; «…l periodo comprendido entre los meses de»; «…días a razón de»; «…me pericial relacionados en el anexo. En»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 45, 51 y 52.2 de la LEC
- artículo 250.2 de la LEC
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

### Formulario 0151 · Demanda verbal contra aseguradora por pérdidas del cierre del negocio por COVID

- Año del modelo: 2021
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 39 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D [COMPLETAR], Procurador de los Tribunales en representación de [LOCALIDAD] según acredito por certificación del registro electrónico de apoderamientos judiciales que acompaño (o mediante designación apud acta ante el Letrado de la Administración de Justicia de [COMPLETAR]), bajo la dirección letrada de D/Dña. [NOMBRE Y APELLIDOS], Abogada/o del Iltre. Colegio de [LOCALIDAD], ante el Tribunal comparezco y como mejor en derecho proceda DIGO:

Que, por medio de la presente, formulo demanda de juicio verbal en ejercicio de la acción de reclamación de cantidad por pérdidas derivadas del cierre del negocio por COVID-19 en virtud de contrato de seguro de fecha [FECHA], demanda que dirijo contra la entidad aseguradora [COMPLETAR], con domicilio en [LOCALIDAD], en base a los siguientes

HECHOS

PRIMERO.- Se insta en este proceso demanda en reclamación de [IMPORTE] euros, amparada con el contrato de seguro suscrito con la entidad demandada por cierre del negocio de mi representado durante [Nº] días, como consecuencia de la pandemia del COVID.

En fecha [FECHA], la demandante concertó póliza de seguro en la modalidad multirriesgo con la entidad demandada, referida a un local de negocio destinado a restaurante, concretamente el denominado restaurante [ÓRGANO], sito en [LOCALIDAD], en el que se contemplaban diversas contingencias a cubrir, entre las cuales se incluye las pérdidas por paralización de la actividad.

En efecto, en las condiciones particulares se recoge como contratada la garantía de pérdida de explotación, habiéndose pactado una indemnización diaria de …. euros, fijándose como máximo de días de indemnización el de [Nº] días (condición particular número [NÚMERO] de la póliza).

La citada póliza recoge, además, las siguientes estipulaciones: a) La fecha del efecto empezó a las [Nº] horas del día [FECHA] b) El negocio asegurado era el restaurante [ÓRGANO], sito en [LOCALIDAD] de la población [COMPLETAR] c) Entre las coberturas de daño, figuraba el apartado: "Pérdida de beneficios/Paralización de la actividad", donde se contemplaba una indemnización diaria de [IMPORTE] euros (periodo de indemnización: días), sin franquicia. d) El pago de la primera prima se fijó el día [FECHA], que fue satisfecho por mi representada por importe [IMPORTE] euros.

En la página [COMPLETAR] del Condicionado General de la Póliza, se recoge la descripción respecto de esta garantía contratada por cierre del negocio, concretamente en el artículo … relativo a garantías del período de explotación y en el apartado relativo al objeto de la cobertura, donde se establece lo siguiente: "hasta la cantidad y por el período máximo indicado en las condiciones particulares, las pérdidas que usted sufra con motivo de la paralización parcial o total de la actividad de negocio asegurado, a consecuencia de cualquier siniestro cuyos daños materiales encuentren amparados por esta póliza."

Acompaño como documentos número [Nº DE DOCUMENTO] copia de la póliza y recibos del pago de las primas acreditativas de su vigencia.

SEGUNDO.- Como consecuencia de la pandemia del COVID-19, y dadas las restricciones del estado de alarma, mi representado tuvo que cerrar su negocio en el periodo comprendido entre los meses de [COMPLETAR], durante un total de [Nº] días.

Durante dicho periodo se produjo la paralización total de la actividad, por lo que, de acuerdo al condicionado particular de la póliza, corresponde a mi representado una indemnización por un periodo de [Nº] días, a razón de [IMPORTE] euros diarios, lo que totaliza un importe de [IMPORTE] euros, el cual debe ser satisfecho por la aseguradora en cumplimiento de sus obligaciones derivadas del contrato de seguro.

El fundamento de esta pretensión es que el condicionado particular contiene una cláusula "delimitadora del riesgo cubierto", que contempla el supuesto de pérdida de beneficios por paralización de la actividad negocial, en cuyo supuesto el pacto es claro, pues contempla un máximo de [Nº] días a razón de [COMPLETAR] por día.

Por tanto, aunque la póliza examinada no contempla expresamente, la cobertura del riesgo referido a la paralización del negocio por la pandemia, es un supuesto que se encuentra dentro de la cobertura pactada de “pérdida de beneficios/paralización de la actividad”, sin que sea aceptable restringir la cobertura esperada por el asegurado, dejando desnaturalizada la paralización del negocio cubierto por el seguro contratado.

TERCERO.- En fecha [FECHA], mi representado remitió un burofax de reclamación a la aseguradora demandada, quien rechazó el siniestro, manifestando que el riesgo estaba excluido por el condicionado general del contrato (acompaño como documentos número [Nº DE DOCUMENTO] burofax y contestación de la aseguradora).

Sin embargo, dicha exclusión no puede tener eficacia para el asegurado pues no cumple los requisitos del art. 3 de la Ley de Contrato de Seguro, al tratarse de la condición general alegada por la aseguradora de una cláusula limitativa del riesgo, en tanto que se trata de condiciones generales predispuestas exclusivamente por la aseguradora que el artículo 3 exige que se incluyan "necesariamente en la póliza de contrato o en un documento complementario, que se suscribirá por el asegurado y al que se entregará copia del mismo".

La jurisprudencia ha determinado, de forma práctica, el concepto de cláusula limitativa, referenciándolo al contenido natural del contrato, derivado, entre otros elementos, de las cláusulas identificadas por su carácter definidor, de las cláusulas particulares del contrato y del alcance típico o usual que corresponde a su objeto con arreglo a lo dispuesto en la ley o en la práctica aseguradora. Según la jurisprudencia, el principio de transparencia, fundamento del régimen especial de las cláusulas limitativas, opera con especial intensidad que restringen la cobertura o la indemnización esperada por el asegurado o "cláusulas limitativas de los derechos del asegurado", manda el referido art. 3 de la LCS que se destaquen y que sean específicamente aceptadas por escrito".

En este caso, la cláusula delimitadora del riesgo era la pérdida por paralización de actividad, sin que se pactara otra exclusión en las cláusulas particulares, no destacándose ninguna exclusión de la cobertura del riesgo en las condiciones generales, las cuales ni tan siquiera fueron firmadas por mi representado, y sobre las que no recibió ninguna información precontractual.

La póliza suscrita, si bien no contempla expresamente la cobertura del riesgo referido a la paralización del negocio por la pandemia, impondría en todo caso que la exclusión de este riesgo en el condicionado general por la aseguradora cumpliera los requisitos del art. 3 LCS (estar destacada de forma especial y aceptación por escrito del asegurado) y ello, por aplicación de la jurisprudencia sobre el contenido natural del contrato de seguro y a las expectativas que podía tener el asegurado, ya que la póliza cubría, de manera expresa, la "Pérdida de beneficios/Paralización de la actividad".

La redacción de la cláusula del condicionado general invocada por la aseguradora no deja lugar a dudas que es de cláusula limitativa del riesgo asumido y no delimitador del mismo ya que, al hacer constar que se incluye en la definición del riesgo la pérdida de beneficios como consecuencia de cualquier siniestro cuyos daños materiales encuentren amparados por esta póliza, indica que cualquier tipo causa de paralización de la actividad se encuentra incluida en el ámbito del contrato, debiendo de haber sido aceptada expresamente por el asegurado la que excluya aquella conforme al artículo 3 de la LCS, y las causas de exclusión que indica la aseguradora debían de haber sido expresamente destacadas del condicionado y expresamente aceptadas por el demandante, circunstancia esta que no consta.

En definitiva, no siendo oponible la exclusión y no discutiéndose la paralización de la actividad y las pérdidas sufridas por mi representado, debe entenderse que la cantidad reclamada está dentro de la cobertura del seguro.

CUARTO.- Por lo expuesto, se reclama la indemnización por importe de [IMPORTE] euros que está cubierta por la póliza suscrita por mi representado, como consecuencia de las pérdidas por paralización de actividad, que no han sido cuestionadas por la aseguradora, la cual debe incrementarse con el interés prevenido en el art. 20 de la Ley de Contrato de Seguro, todo lo cual se reclama en esta demanda.

FUNDAMENTOS DE DERECHO

PRIMERO.- Competencia.- Corresponde la competencia para conocer de esta clase de procesos al Tribunal de Instancia al que me dirijo, por aplicación del art. 45, 51 y 52.2 de la LEC, en relación con lo dispuesto en el art. 85.1º LOPJ.

SEGUNDO.- Legitimación.-Le corresponde a esta parte la legitimación activa en su condición de tomador y asegurado, en tanto que la legitimación pasiva corresponde a la aseguradora.

TERCERO.- Procedimiento: Es el juicio verbal con fundamento en el artículo 250.2 de la LEC, al no exceder la cuantía del proceso de 15.000 euros.

CUARTO.- Cumplimiento de los requisitos de procedibilidad: La presente demanda cumple con el requisito de procedibilidad exigido por la disp. adic. 7ª de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

QUINTO.- Acción ejercitada: Se ejercita la acción amparada en el art. 1 de la Ley de Contrato de Seguro y preceptos concordantes que establece que el contrato de seguro es aquel por el que el asegurador se obliga, mediante el cobro de una prima y para el caso de que se produzca el evento cuyo riesgo es objeto de cobertura a indemnizar, dentro de los límites pactados, el daño producido al asegurado o a satisfacer un capital, una renta u otras prestaciones convenidas.

Como indica la STS de 6 de mayo de 2021, el tomador debe tomar constancia real y efectiva no sólo del riesgo, constituido en verdadera alma y nervio del contrato, sino de los límites en los que opera la cobertura de la compañía aseguradora, en tanto en cuanto si la finalidad del seguro es diluir, neutralizar o anular el riesgo, el asegurado ha de conocer, desde el primer momento, el concreto marco dentro del cual se encuentra amparado en el supuesto de que dicho riesgo se convierta en siniestro, habiéndose incluido en este caso de forma precisa en las cláusulas particulares la cobertura por pérdidas derivadas de la paralización del negocio asegurado.

SEXTO.- Ineficacia de las cláusulas limitativas: Es de aplicación el art. 3 de la Ley de Contrato de Seguro y la jurisprudencia que lo interpreta. El art. 3 LCS establece: "Las condiciones generales, que en ningún caso podrán tener carácter lesivo para los asegurados, habrán de incluirse por el asegurador en la proposición de seguro si la hubiere y necesariamente en la póliza de contrato o en un documento complementario, que se suscribirá por el asegurado y al que se entregará copia del mismo. Las condiciones generales y particulares se redactarán de forma clara y precisa. Se destacarán de modo especial las cláusulas limitativas de los derechos de los asegurados, que deberán ser específicamente aceptadas por escrito".

Según la jurisprudencia, ello obliga a las aseguradoras a la redacción clara y precisa de sus condiciones contractuales tanto particulares como generales, así como que las condiciones calificables como limitativas gocen de la garantía de hallarse debidamente destacadas en las pólizas, así como específicamente amparadas por las firmas de los tomadores, todo lo que aquí no ha sucedido, por lo que las limitaciones no son oponibles al asegurado.

SÉPTIMO.- Indemnización e intereses: Debe indemnizarse a mi representado en las cantidades reclamadas, que están cubiertas por el contrato de seguro, con más los intereses por mora prevenidos en el art. 20 de la Ley de Contrato de Seguro desde la fecha de la paralización del negocio.

OCTAVO.- En materia de costas, el artículo 394 LEC señala que las de primera instancia se imponen a la parte que vea en primera instancia rechazadas sus pretensiones.

En base a lo anterior,

SUPLICO AL TRIBUNAL que tenga por presentada la presente demanda con los documentos a ella adjuntos y sus copias, en la representación que ostento, y se tenga por formulada demanda de acción de reclamación de cantidad por pérdidas derivadas de paralización del negocio cubierta por contrato de seguro, y en su virtud se dicte sentencia por la que, de acuerdo a lo expuesto en esta demanda, se condene a la aseguradora demandada a que indemnice a mi representado en la cantidad de [IMPORTE] euros, con más los intereses por mora del art. 20 de la Ley de Contrato de Seguro, todo ello con condena en costas al demandado.

OTROSÍ PRIMERO DIGO. que, de conformidad con lo dispuesto en los artículos 251 y 252 de la LEC, se fija la cuantía del presente procedimiento en [IMPORTE] euros.

SUPLICO AL TRIBUNAL se tenga por efectuada la anterior manifestación a los efectos pertinentes.

OTROSÍ SEGUNDO DIGO que se acompaña en anexo relación de documentos e informe pericial presentados, debidamente foliados y con índice electrónico, para su debida localización y consulta.

SUPLICO AL TRIBUNAL tenga hecha esta manifestación a los efectos oportunos y por aportados los documentos e informe pericial relacionados en el anexo.

En [COMPLETAR]

El Abogado El Procurador
