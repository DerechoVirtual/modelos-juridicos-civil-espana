---
name: demanda-danos-vivienda-tras-finalizar-arrendamiento-94
description: "Redacta el escrito «Demanda por daños en la vivienda tras finalizar el arrendamiento» (formulario 94 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda por daños en la vivienda tras finalizar el arrendamiento

> Formulario 0094 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Inmuebles** (referencia catastral, superficie, uso) → `consultar_catastro` (y `callejero_catastro` para localizar la dirección).

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
- [ ] LOCALIDAD (3 veces)
- [ ] FECHA (5 veces)
- [ ] IMPORTE (11 veces)
- [ ] Nº DE DOCUMENTO (8 veces)
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…do/a de la Administración de Justicia de»; «…n estado, según se recoge en la cláusula»; «… ante lo cual se dirigió a la Notaría de»; «…ada contactó con el Arquitecto Técnico D»; «…ó presupuesto de reparación a la empresa»; «… en el informe acompañado como documento»; «…a»; «…y desperfectos se realizó por la empresa»; «…a factura que se acompaña como documento»; «…las facturas acompañadas como documentos»; «…rajudicial. En este sentido, se acudió a»; «…me pericial relacionados en el anexo. En»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 45 y 50 de la LEC
- artículo 249.2 de la LEC
- art. 5 de la Ley Orgánica 1/2025
- arts. 1561 a 1564 del CC
- art. 1561 CC
- art. 1562 CC
- art. 1563 CC
- art. 1564 CC
- arts. 110, 1101 y 1108 del Código Civil
- artículo 394 LEC
- artículos 251 y 252 de la LEC

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

### Formulario 0094 · Demanda por daños en la vivienda tras finalizar el arrendamiento

- Año del modelo: 2022
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 45 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D/Dª [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales en representación de D/Dña. [NOMBRE Y APELLIDOS] según acredito por certificación del registro electrónico de apoderamientos judiciales que acompaño o mediante designación apud-acta otorgado ante el Letrado/a de la Administración de Justicia de [COMPLETAR], bajo la dirección letrada de D/Dña. [NOMBRE Y APELLIDOS]., Abogado/a del Iltre. Colegio de [LOCALIDAD], ante el Tribunal comparezco y como mejor en derecho proceda DIGO:

Que, por medio de la presente, formulo demanda de juicio ordinario en ejercicio de la acción de responsabilidad por daños sufridos en la vivienda de mi representado tras la finalización del contrato de arrendamiento, imputables al arrendatario, la cual dirijo contra D/Dª [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], en base a los siguientes

HECHOS

PRIMERO.- Se insta en este proceso demanda en solicitud de indemnización de daños y perjuicios en la vivienda titularidad de mi representado tras finalizar el contrato de arrendamiento concertado sobre la misma, los cuales son imputables al arrendatario.

En fecha [FECHA], mi representado arrendó la vivienda de su titularidad sita en [LOCALIDAD], a la demandada, por un periodo de cinco años, pactándose una renta mensual de [IMPORTE] euros ( acompaño como documento número [Nº DE DOCUMENTO] copia del contrato de arrendamiento).

El arrendamiento incluía el mobiliario y electrodomésticos de la vivienda, tal como se recoge en el contrato, los cuales se encontraban en buen estado, según se recoge en la cláusula [COMPLETAR] del contrato.

La relación contractual se desarrolló normalmente hasta la expiración del plazo, salvo que la demandada arrendataria no abonó la última mensualidad de renta, la cual la arrendataria manifestó que debía ser imputada a la fianza constituida por una mensualidad de renta.

En cuanto a la entrega de la vivienda, ambas partes convinieron que la demandada arrendataria dejaría las llaves en el buzón de la vivienda el día [FECHA], una vez finalizara la mudanza, pudiendo recogerlas mi representada a partir de ese momento (acompaño como documento número [Nº DE DOCUMENTO], correo de la demandada con la propuesta de entrega de llaves de la vivienda, la cual fue aceptada por mi representada).

SEGUNDO.- Al día siguiente en que se pactó la entrega de llaves, en fecha [FECHA], mi representada acudió a la vivienda, encontrándose la misma en un estado lamentable, con multitud de daños y desperfectos, ante lo cual se dirigió a la Notaría de [COMPLETAR] para solicitar que se levantara acta notarial del estado de la vivienda.

Ese mismo día, acudió el/la Notario/a D/Dª [NOMBRE Y APELLIDOS], levantando acta de constancia del estado de la vivienda, a la que se adjunta reportaje fotográfico, la cual se acompaña como documento número [Nº DE DOCUMENTO].

Tal como se observa en las fotografías, la vivienda presentaba un estado de abandono total, encontrándose completamente destrozada y en estado de gran suciedad e insalubridad.

Ante esta situación, mi representada contactó con el Arquitecto Técnico D [COMPLETAR], a fin de que realizara informe pericial de daños de la vivienda, el cual fue confeccionado el día [FECHA], recogiéndose en el mismo los daños que presentaba la vivienda, imputables a la arrendataria demandada, que se acompaña como documento número [Nº DE DOCUMENTO].

La relación de daños que son imputables a la arrendataria se describen en el apartado 2 del informe y son los siguientes: 1) la madera de los marcos del inmueble se encontraba inflada por la acción del agua y lo mismo ocurría con los zócalos de madera y las puertas, en especial la de entrada, que se encontraba deteriorada hasta el punto de tener el pomo suelto y encontrarse tan hinchada por la acción de la humedad que rozaba en el suelo y dificultaba su apertura; 2) los perfiles de madera de las columnas del inmueble también se encontraban deteriorados por la acción del agua; 3) la parte baja de los marcos de las puertas, de los perfiles y de los zócalos se encontraba roída por la acción de algún animal doméstico; 4) varias piezas cerámicas de los zócalos se encontraban rotas, así como varias piezas cerámicas de la terraza; 5) las puertas correderas de acceso al balcón no abrían y cerraban correctamente debido al lamentable estado de las mismas, con las guías sucias y deterioradas por la misma suciedad; 6) las persianas del comedor y dos dormitorios no funcionaban, y la cortina de uno de los dormitorios estaba descolgada, y varios interruptores y enchufes se encontraban rotos.

En cuanto al estado de los electrodomésticos y muebles, en el apartado 3 del informe se describe que presentaban un nivel de suciedad incompatible con unas mínimas condiciones de salubridad, los electrodomésticos estaban inservibles y la pica del lavadero presentaba suciedad y moho, al igual que la bañera del cuarto de baño.

Estos daños se constatan asimismo en el reportaje fotográfico aportado con el acta notarial, en el que se aprecia el lamentable estado en el que la demandada dejó la vivienda.

TERCERO.- Ante esta situación, mi representada solicitó presupuesto de reparación a la empresa [COMPLETAR] que cuantificó el importe que le iba a suponer reparar los daños en [IMPORTE] euros.

Estas cantidades coinciden con la valoración realizada por el perito en el informe acompañado como documento [COMPLETAR] donde valoró los desperfectos fueron valorados en [IMPORTE] euros, expresando que los muebles y electrodomésticos estaban en estado inservible.

Asimismo, mi representada concertó la adquisición de los electrodomésticos y mobiliario inservible, lo cual ascendió a [IMPORTE] Euros (acompaño como documentos número [Nº DE DOCUMENTO] a [COMPLETAR] presupuestos y facturas de compra).

El total de los daños imputables a la arrendataria asciende a [IMPORTE] euros, habiéndose realizado por esta parte reclamación extrajudicial de los mismos en fecha [FECHA] por medio de burofax que se acompaña como documento número [Nº DE DOCUMENTO], sin que la demandada contestara a dicha reclamación.

CUARTO.- Se ejercita la acción por daños contra la demandada arrendataria por cuanto que ha incumplido su obligación esencial de restituir al arrendador la vivienda arrendada al concluir el arriendo, "tal como la recibió", atendido que los daños que presenta el inmueble son imputables al arrendatario y no corresponde al transcurso del tiempo ni al uso normal y diligente de la cosa.

La jurisprudencia ha reiterado que el arrendador se halla protegido por una doble presunción iuris tantum de recepción por el arrendatario de la vivienda en buen estado y de culpabilidad del arrendatario por el deterioro.

En este caso, la demandada no ha devuelto la vivienda tal como la recibió, sino que ha ocasionado daños derivados de un mal uso o uso no normal, o incívico por parte de la ocupante de la vivienda, de modo que surge su responsabilidad contractual, puesto que el origen de estos daños trae causa un mal uso de los objetos, en actos impropios de los fines a que los bienes dañados se destinan; en fin, su origen en una acción u omisión dolosa o culposa.

QUINTO.- Se reclama la cantidad de [IMPORTE] euros, que se desglosa en: 1) la cantidad de [IMPORTE] euros por daños y desperfectos en la vivienda; la reparación de estos daños y desperfectos se realizó por la empresa [COMPLETAR] según el presupuesto aportado y la valoración pericial de daños, que fue abonada por mi representada según se acredita por la factura que se acompaña como documento [COMPLETAR]; y 2) en la cantidad de [IMPORTE] euros por coste de reposición de los electrodomésticos y mobiliario inservible, según se acredita por las facturas acompañadas como documentos [COMPLETAR].

Esta parte no reclama la última mensualidad de renta, aceptando en este sentido la compensación con la fianza arrendaticia pretendida por la demandada.

Por tanto, se pretende la indemnización por importe de [IMPORTE] euros, con más los intereses legales desde la fecha de la reclamación extrajudicial a la que nos hemos referido anteriormente, realizada por el burofax acompañado como documento número [Nº DE DOCUMENTO].

SEXTO.- Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

PRIMERO.- Competencia.- Corresponde la competencia para conocer de esta clase de procesos al Tribunal de Instancia al que me dirijo, por aplicación del art. 45 y 50 de la LEC, en relación con lo dispuesto en el art. 85.1º LOPJ.

SEGUNDO.- Legitimación.-Le corresponde a esta parte la legitimación activa en su condición de arrendadora titular de la vivienda, en tanto que la legitimación pasiva corresponde a la demandada.

TERCERO.- Procedimiento: Es el juicio ordinario con fundamento en el artículo 249.2 de la LEC, al exceder la cuantía del proceso de 15.000 euros.

CUARTO.- Cumplimiento de los requisitos de procedibilidad: La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

QUINTO.- Acción ejercitada: Se ejercita la acción de responsabilidad contractual contra la demandada amparada en los arts. 1561 a 1564 del CC: 1) art. 1561 CC: El arrendatario debe devolver la finca, al concluir el arriendo, tal como la recibió, salvo lo que hubiese perecido o se hubiera menoscabado por el tiempo o por causa inevitable; 2) art. 1562 CC: A falta de expresión del estado de la finca al tiempo de arrendarla, la ley presume que el arrendatario la recibió en buen estado, salvo prueba en contrario; 3) art. 1563 CC: el arrendatario es responsable del deterioro o pérdida que tuviere la cosa arrendada, a no ser que pruebe haberse ocasionado sin culpa suya; 4) art. 1564 CC: el arrendatario es responsable del deterioro causado por las personas de su casa.

La jurisprudencia ha reiterado que el arrendatario responde del deterioro o pérdida frente al arrendador y frente a los terceros. El art. 1562 CC establece una presunción de responsabilidad por los deterioros o la pérdida de la cosa arrendada " a no ser que se pruebe haberse ocasionado sin culpa suya ". El arrendador está favorecido por una presunción "iuris tantum" -que puede ser desvirtuada mediante prueba en contrario- de que se entregó la cosa en buen estado y recae sobre el arrendatario la demostración de que los deterioros que presente la cosa al tiempo de la restitución eran preexistentes o se han ocasionado por causas ajenas a su responsabilidad (fuerza mayor), ya que responde incluso del caso fortuito como manifestaciones del deber de guarda y custodia de la cosa, y de la obligación de restituirla al término del contrato en idéntico buen estado al en que se presume recibida ex art. 1561 CC.

SEXTO.- Intereses: Son de aplicación los arts. 110, 1101 y 1108 del Código Civil, devengándose el interés legal desde la fecha de la mora.

SÉPTIMO.- Costas: En materia de costas, el artículo 394 LEC señala que las de primera instancia se imponen a la parte que vea en primera instancia rechazadas sus pretensiones.

En base a lo anterior,

SUPLICO AL TRIBUNAL que tenga por presentada la presente demanda con los documentos a ella adjuntos y sus copias, en la representación que ostento, y se tenga por formulada demanda de acción de reclamación de cantidad por responsabilidad por daños en la vivienda arrendada, y en su virtud se dicte sentencia por la que, de acuerdo a lo expuesto en esta demanda, se condene a la demandada a que indemnice a mi representada en la cantidad de [IMPORTE] euros, con más los intereses legales correspondientes, todo ello con condena en costas al demandado.

OTROSÍ PRIMERO DIGO. que, de conformidad con lo dispuesto en los artículos 251 y 252 de la LEC, se fija la cuantía del presente procedimiento en [IMPORTE] euros.

SUPLICO AL TRIBUNAL se tenga por efectuada la anterior manifestación a los efectos pertinentes.

OTROSÍ SEGUNDO DIGO que se acompaña en anexo relación de documentos e informe pericial presentados, debidamente foliados y con índice electrónico, para su debida localización y consulta.

SUPLICO AL TRIBUNAL tenga hecha esta manifestación a los efectos oportunos y por aportados los documentos e informe pericial relacionados en el anexo.

En [COMPLETAR]

El Abogado El Procurador
