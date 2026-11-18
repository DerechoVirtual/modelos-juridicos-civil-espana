---
name: demanda-nulidad-compraventa-negocio-vicios-166
description: "Redacta el escrito «Demanda de nulidad de compraventa de negocio por vicios del consentimiento» (formulario 166 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de nulidad de compraventa de negocio por vicios del consentimiento

> Formulario 0166 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] LOCALIDAD (10 veces)
- [ ] FECHA (6 veces)
- [ ] IMPORTE (4 veces)
- [ ] Nº DE DOCUMENTO (4 veces)
- [ ] LUGAR
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…D»; «…bunales en representación de la sociedad»; «…do/a de la Administración de Justicia de»; «…, demanda que dirijo contra la Sociedad»; «…ribió contrato con la sociedad demandada»; «…ocio docente, concretado en un número de»; «…o vigente. Concretamente, en la cláusula»; «…ociedad vendedora en las titulaciones de»; «…reses generados desde el pago del precio»; «…rajudicial. En este sentido, se acudió a»; «…mo indica el art. 1.266 del mismo Código»

## Párrafos opcionales (3)

Inclúyelos solo si encajan en los hechos:

- OTROSÍ PRIMERO DIGO Que estando la presente demanda sujeta al abono de la tasa por el ejercicio de la potestad…
- OTROSÍ SEGUNDO DIGO que se fija la cuantía del presente procedimiento en [IMPORTE] euros.…
- OTROSÍ TERCERO DIGO que se acompaña en anexo relación de documentos e informe pericial presentados, debidament…

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 1261, 1266 y 1269 del Código Civil
- artículos 1.100 , 1.101 y 1.108 del Código Civil
- arts. 50 y 51 LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 1301 del Código Civil
- artículo 1.265 del Código Civil
- artículo 1265 y 1269 del Código Civil
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

### Formulario 0166 · Demanda de nulidad de compraventa de negocio por vicios del consentimiento

- Año del modelo: 2021
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 3 párrafos opcionales señalados; 36 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D [COMPLETAR], Procurador de los Tribunales en representación de la sociedad [COMPLETAR], según acredito por certificación del registro electrónico de apoderamientos judiciales que acompaño (o mediante designación apud acta ante el/la Letrado/a de la Administración de Justicia de [COMPLETAR], bajo la dirección letrada de D/Dña [NOMBRE Y APELLIDOS], Abogado/a del Iltre. Colegio de [LOCALIDAD], ante el Tribunal comparezco y como mejor en derecho proceda DIGO:

Que, por medio de la presente, formulo demanda de juicio ordinario en ejercicio de la acción de nulidad del contrato suscrito con la demandada en fecha [FECHA], demanda que dirijo contra la Sociedad [COMPLETAR], con domicilio en [LOCALIDAD], en base a los siguientes

Hechos

Primero.– En fecha [FECHA] mi representada suscribió contrato con la sociedad demandada [COMPLETAR], en virtud del cual se adquirió el negocio de escuela de formación de la demandada sita en [LOCALIDAD], subrogándose en el ejercicio de la actividad docente y académica que venía prestando, por precio de [IMPORTE] euros.

Según se recoge en el contrato, la demandada se obligaba a ceder las instalaciones donde se impartían los cursos de formación en las titulaciones académicas relacionadas, comprometiéndose a ceder todos los demás elementos del negocio docente, concretado en un número de [COMPLETAR] alumnos para el curso académico vigente.

Concretamente, en la cláusula [COMPLETAR] del contrato, se pactaba que mi representada se subrogaría en el ejercicio de la actividad docente que venía prestándose por la sociedad vendedora en las titulaciones de [COMPLETAR], en virtud del convenio suscrito con la Universidad de [LOCALIDAD] de fecha [FECHA].

Acredito lo anterior mediante copia del contrato y certificaciones de abono del precio pactado que acompaño como documentos número [Nº DE DOCUMENTO].

Segundo.– La demandada ocultó maliciosamente que el convenio suscrito con la Universidad de [LOCALIDAD], en virtud del cual se impartía el grueso de la docencia en el centro de formación adquirido, estaba siendo objeto de un procedimiento de resolución contractual.

En efecto, a los pocos días de concertarse el contrato, mi representada recibió comunicación de la Universidad de [LOCALIDAD] de fecha [FECHA], en virtud de la cual se ponía en su conocimiento que el contrato quedaba resuelto por incumplimiento, de manera que no se seguiría impartiendo docencia en el centro en virtud del convenio de colaboración suscrito (acompaño como documento número [Nº DE DOCUMENTO] comunicación recibida de la Universidad de [LOCALIDAD]).

Estos hechos eran conocidos perfectamente por la demandada puesto que, tal como es de ver en la comunicación acompañada, el procedimiento de resolución se inició con anterioridad a que se suscribiera el contrato, en virtud de incumplimientos imputables a la demandada que se habían producido en el curso académico anterior, lo cual fue ocultado con mala fe a mi representada, provocando de esta manera un error esencial en mi representada al concertar el contrato, pues el centro de formación es totalmente antieconómico.

Tercero.– Se ejercita la acción de nulidad por vicios en el consentimiento por dolo o, subsidiariamente, por error, dada la conducta dolosa de la demandada que ocultó intencionadamente los hechos expresados, generando un error en mi representada, quien otorgó su consentimiento con error esencial sobre el objeto del contrato, como consecuencia de la ocultación intencional realizada por la demandada sobre la situación contractual previa determinante de la resolución del convenio concertado con la Universidad de [LOCALIDAD], el cual era el que generaba el grueso de la actividad docente del centro de formación adquirido.

Por estos motivos, la prestación del consentimiento por mi representada no se correspondió con la realidad y por tanto el consentimiento prestado fue totalmente errado y por tanto nulo de acuerdo con los artículos 1261, 1266 y 1269 del Código Civil, los cuales establecen que no hay contrato sino concurren como requisitos el consentimiento, el objeto cierto de lo que sea materia del contrato y la causa de la obligación que se establezca, consentimiento que según el artículo 1265 será nulo por recaer sobre la sustancia de la cosa que fuere objeto del contrato y sobre aquellas condiciones de la misma que principalmente dieron motivo a celebrarlo conforme al art. 1266 del citado Código Civil.

Por tanto, se trata de un error en el objeto determinante de vicio del consentimiento prestado por mi representada en el momento de perfeccionarse el contrato, el cual es esencial e inexcusable, pues obedece a la ocultación intencional que realizó la demandada del estado del convenio de colaboración suscrito con la Universidad de [LOCALIDAD], el cual estaba en curso de resolución. La efectiva resolución del convenio determina que el error sea sustancial, derivado de hemos desconocidos para mi representada, e inexcusable, puesto que mi representada actuó en todo momento con arreglo a las reglas de buena fe, en la apariencia generada por la demandada de que el convenio con la Universidad estaría vigente durante todo el periodo concertado, tal como manifestó reiteradamente en el curso de las negociaciones para concertar el contrato.

Cuarto.– De acuerdo a lo expuesto en el hecho anterior, debe declararse la nulidad del contrato y, de conformidad con lo dispuesto en el artículo 1101 y siguientes en relación con el artículo 1124 y 1303 y concordantes del Código Civil, se pretende que se declare la nulidad del contrato y se condene a la demandada a indemnizar a mi representado en la cantidad de [IMPORTE] euros, con más los intereses generados desde el pago del precio [COMPLETAR], conforme a los artículos 1.100 , 1.101 y 1.108 del Código Civil.

Quinto.– Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

A estos hechos son de aplicación los siguientes:

Fundamentos de derecho

Primero.– Competencia

Corresponde a los Tribunales de [LOCALIDAD], de conformidad a lo dispuesto en los arts. 50 y 51 LEC, en relación con lo dispuesto en el art. 85.1º LOPJ.

Segundo.– Legitimación

Le corresponde la activa a esta parte ante su condición de compradora lesionada, en tanto que la pasiva corresponde al vendedor demandado, en ejercicio de la acción de nulidad del contrato de compraventa.

Tercero.– Procedimiento

Es el juicio verbal con fundamento en el art 249.2 dado el importe reclamado de ... € que excede de los 15.000 euros, por lo que deben seguirse las normas del juicio ordinario.

Cuarto.– Cumplimiento de los requisitos de procedibilidad

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Quinto.– Plazo

Es de aplicación el art. 1301 del Código Civil que establece que la acción de nulidad durará cuatro años que comenzará a correr, en el caso de error o dolo, desde la concertación del contrato.

Sexto.– Acción ejercitada

Nulidad del contrato: dolo y error en el consentimiento.– Es de aplicación el artículo 1.265 del Código Civil que declara la nulidad del consentimiento (y por ende la de los contratos en los que intervenga) prestado «por error, violencia o dolo», consistiendo el error en aquel vicio de la voluntad que da lugar a la formación de la misma sobre la base de una creencia inexacta, error que lleva al contratante afectado a consentir en un contrato que no hubiera concertado de conocer su verdadera naturaleza o efectos.

Con carácter principal, son de aplicación el artículo 1265 y 1269 del Código Civil, por dolo en la entidad demandada, fundado en la ocultación intencionada de información existente sobre el estado real del contrato con la Universidad demandada, del cual trae causa el suscrito, que estaba en curso de resolución y que deja sin contenido la prestación que se obligó a realizar la demandada.

Existe en todo caso error como vicio del consentimiento determinante de la nulidad del contrato. Como indica el art. 1.266 del mismo Código [COMPLETAR], «para que el error invalide el consentimiento, deberá recaer sobre la sustancia de la cosa que fuera objeto del contrato, o sobre aquellas condiciones de la misma que principalmente hubieran dado motivo a celebrarlo»; no es preciso por tanto que no exista causa para el contrato, o que la misma sea ilícita o fruto de una simulación, sino que basta con que el contratante que incurre en el error no la conozca en su verdadera naturaleza, y preste su consentimiento bajo la errónea creencia de ser otra distinta (en este sentido, entre otras muy numerosas, se pronuncian las sentencias del Tribunal Supremo de 12 de julio de 2002, 24 de enero de 2003 y 12 de noviembre de 2004.

Se dan los requisitos para que se aprecie el error en el objeto determinante de vicio del consentimiento prestado por los contratantes en el momento de perfeccionarse el contrato según reiterada jurisprudencia para que pueda llegar a tener trascendencia anulatoria y provocar la nulidad del contrato queda condicionada a la concurrencia en el caso de determinados requisitos como son: a) Que sea esencial e inexcusable, pues de no ser así habría que estar a la norma de que los efectos del error propio son imputables a quien los padece. b) Que sea sustancial y derivado de actos desconocidos para el que se obliga. c) Que no se haya podido evitar con una regular diligencia. d) Que quede suficientemente acreditado en las actuaciones como cuestión de hecho e) Que el error como conocimiento equivocado de alguna circunstancia de la realidad exterior que pueda influir decisivamente en el contrato o de aquello que sea sustancial al mismo, y que tienda a la determinación de lo que pueda constatar la sustancia del objeto contractual, requiere la investigación de los elementos concurrentes en cada caso particular y del fin perseguido por las partes, requiriéndose que sea esencial y derivado de actos desconocidos para el que se obliga.

Séptimo.– Efectos

Son de aplicación los artículos 1101 y siguientes y 1303 y concordantes del Código Civil, debiendo declararse la nulidad del contrato y la indemnización de daños y perjuicios a favor de mi representado, con los intereses moratorios correspondientes.

Octavo.– Costas

En materia de costas el art 394 LEC señala que las de primera instancia se imponen a la parte que vea en primera instancia rechazadas sus pretensiones.

En base a lo anterior,

SUPLICO AL TRIBUNAL que tenga por presentada la presente demanda, con el dictamen pericial y los documentos a ella adjuntos, por parte en la representación que ostento, y tras la pertinente tramitación se dicte por ese Tribunal sentencia por la que se declare la nulidad del contrato concertado por las partes en fecha [FECHA] y se condene a la demandada a que indemnice a mi representada en la cantidad de [IMPORTE] euros en concepto de indemnización de daños y perjuicios, con más los intereses legales correspondientes, todo ello con imposición de costas a la parte demandada.

[OPCIONAL — incluir si procede]

OTROSÍ PRIMERO DIGO Que estando la presente demanda sujeta al abono de la tasa por el ejercicio de la potestad jurisdiccional fijada por la Ley 10/2012, de 20 de noviembre, modificada por RDL 3/2013 y Ley 25/2015, de 28 julio, y desarrollada por Orden HAP/2662/2012, de 13 de diciembre, siendo mi representada personas jurídica no exenta de su pago, se acompaña a la presente demanda como documento nº [Nº DE DOCUMENTO] la correspondiente autoliquidación con el ejemplar para la Administración de Justicia debidamente validado y en el que consta el pago de la cantidad de 300 euros correspondiente a la cuota fija, sin que se incluya la cuota variable prevista en el artículo 7.2 de la Ley 10/2012 al haber sido declarado inconstitucional y nulo por la STC 140/2016, de 21 de julio.

Por lo que, SUPLICO AL TRIBUNAL que tenga por hecha la anterior manifestación a los efectos pertinentes y por acompañado el documento justificativo del abono de la tasa.

[OPCIONAL — incluir si procede]

OTROSÍ SEGUNDO DIGO que se fija la cuantía del presente procedimiento en [IMPORTE] euros.

Por lo que, SUPLICO AL TRIBUNAL se tenga por efectuada la anterior manifestación a los efectos pertinentes.

[OPCIONAL — incluir si procede]

OTROSÍ TERCERO DIGO que se acompaña en anexo relación de documentos e informe pericial presentados, debidamente foliados y con índice electrónico, para su debida localización y consulta.

Por lo que, SUPLICO AL TRIBUNAL tenga hecha esta manifestación a los efectos oportunos y por aportados los documentos e informe pericial relacionados en el anexo.

En [LUGAR], a [FECHA].

Procurador/a	Abogado/a

Fdo. D./Dña. [NOMBRE Y APELLIDOS]: 	Fdo. D./Dña. [NOMBRE Y APELLIDOS]:
