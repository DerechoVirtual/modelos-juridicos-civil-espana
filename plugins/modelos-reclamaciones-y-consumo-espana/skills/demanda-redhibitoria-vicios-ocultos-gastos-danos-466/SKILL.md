---
name: demanda-redhibitoria-vicios-ocultos-gastos-danos-466
description: "Redacta el escrito «Demanda redhibitoria por vicios ocultos con gastos y daños y perjuicios» (formulario 466 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda redhibitoria por vicios ocultos con gastos y daños y perjuicios

> Formulario 0466 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD (2 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] CORREO ELECTRÓNICO
- [ ] Nº (5 veces)
- [ ] FECHA (3 veces)
- [ ] MARCA/MODELO (2 veces)
- [ ] MATRÍCULA
- [ ] IMPORTE (7 veces)
- [ ] NÚMERO (2 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] LUGAR
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…del Ilustre Colegio de la Abogacía de»; «…, con domicilio (2), primero en»; «…; y segundo, el domicilio laboral en»; «…; y con número de teléfono móvil»; «…to. Se acompañan como documentos números»; «…ontraba circulando desde la población de»; «…, en dirección a»; «…tas de reuniones como documentos números»; «…por aquél: Se acompañan bajo los números»; «…iguientes: Se acompañan bajo los números»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Si el poder se otorga a través de la sede judicial electrónica / Si el poder se otorga mediante comparecencia apud acta / Si el poder se otorga ante Notario — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 24.1 LEC
- arts. 85.1 LOPJ
- art. 50.1 LEC
- arts. 248 y 249.2 LEC
- art. 253.1 LEC
- art. 251 LEC
- arts. 23 y 31 LEC
- art. 399 LEC
- art. 1.490 CCiv
- art. 5 de la Ley Orgánica 1/2025
- art. 1.484 CCiv
- art. 1.486 CCiv
- art. 394 LEC
- art. 337.2 LEC
- art. 24.2 LEC
- art. 155.3 LEC

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

### Formulario 0466 · Demanda redhibitoria por vicios ocultos con gastos y daños y perjuicios

- Año del modelo: 2017
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (3); 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 42 campos de relleno marcados en blanco
- Avisos de la revisión: REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda de resolución del contrato de compraventa a resultas de la aparición en el vehículo vendido de vicios ocultos conforme a los 1.484 y 1.486 CCiv, instando el comprador la devolución del precio con sus intereses y el abono de los gastos, así como indemnización del vendedor por los daños y perjuicios.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], representación que acredito mediante escritura de poder otorgada a mi favor (existen tres posibilidades para otorgar el apoderamiento al Procurador de los Tribunales, conforme dispone el art. 24.1 LEC)

(Elegir opción en función de cómo se haya otorgado el poder) (1)

[ELEGIR UNA OPCIÓN Y REDACTARLA: Si el poder se otorga a través de la sede judicial electrónica / Si el poder se otorga mediante comparecencia apud acta / Si el poder se otorga ante Notario — el texto de cada opción no venía en el formulario original]

bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], abogado/a en ejercicio, con despacho profesional abierto en [LOCALIDAD], colegiado nº [Nº DE COLEGIADO/A] del Ilustre Colegio de la Abogacía de [COMPLETAR], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO:

Que mediante el presente escrito vengo a formular DEMANDA DE JUICIO DECLARATIVO ORDINARIO EN EJERCICIO DE ACCIÓN REDHIBITORIA POR VICIOS O DEFECTOS OCULTOS, contra D./Dña. [NOMBRE Y APELLIDOS], con domicilio (2), primero en [COMPLETAR]; y segundo, el domicilio laboral en [COMPLETAR]); con (3) email [CORREO ELECTRÓNICO]; y con número de teléfono móvil [COMPLETAR].

Que esta parte asume el compromiso de recibir cualquier comunicación dirigida por la oficina judicial, durante toda la fase declarativa, e, incluso, en una eventual fase de ejecución por medios telemáticos, en términos del art. 399.1 II LEC, consignándose a estos efectos la siguiente dirección de correo electrónico y nº [Nº] de teléfono:

Fundamento mis pretensiones en los siguientes:

HECHOS

PRIMERO.- Con fecha [FECHA], mi representado adquirió del hoy demandado el vehículo marca [MARCA/MODELO], modelo [MARCA/MODELO], matrícula [MATRÍCULA], el cual se encontraba, según manifestaba el vendedor, en magnífico estado y en perfectas condiciones de uso y utilización, por precio de [IMPORTE] euros, los cuales fueron abonados en el momento de la firma del contrato.

Se acompañan como documentos números [COMPLETAR] contrato privado de compraventa así como el recibí del pago del precio.

Interesa señalar que mi representado nada tiene que ver con la industria de vehículos a motor, la compraventa de los mismos, ni tiene relación alguna ni conocimiento respecto a mecánica de éstos.

SEGUNDO.- Lo cierto es que al poco tiempo de adquirir el referido vehículo, empezaron a producirse diversas anomalías, hasta el punto de que había ocasiones en que el motor se paraba.

Concretamente, el día [FECHA], a las [Nº] horas, y cuando mi representado se encontraba circulando desde la población de [COMPLETAR], en dirección a [COMPLETAR], el vehículo se paró definitivamente, por lo que hubo de llamar a los servicios de asistencia de una población cercana.

Personado en el lugar de los hechos el vehículo taller-grúa del servicio técnico de la marca del automóvil, fue remolcado hasta los talleres más próximos, al objeto de comprobar por los mecánicos del referido servicio oficial, la avería que había sufrido el vehículo.

A tal fin, el servicio técnico elaboró un informe o diagnóstico respecto de la avería sufrida observando que el vehículo en cuestión tenía un defecto importante en el funcionamiento del motor consistente en la rotura de determinados elementos del mismo, que no se encontraban en buen estado, cuya situación de deterioro lo hacían impropio para el uso a que se destina.

A estos efectos, interesa poner de manifiesto que estas deficiencias ya existían antes de la conclusión del contrato sin que fueran reconocibles por el comprador en el momento de la celebración del contrato, observándose por parte de los técnicos que los citados elementos, habían sufrido un deterioro progresivo a lo largo del tiempo, que pudieran tener su origen en una fecha que se sitúa sobre [Nº] meses antes de adquirir el vehículo.

Se acompaña como documento n.º [NÚMERO], informe técnico debidamente firmado y sellado por el jefe de taller del mencionado servicio, que acredita las deficiencias que presentaba el vehículo adquirido y que las mismas existían al momento de celebración del contrato y no eran reconocibles por el comprador.

Por otra parte, el vendedor era perfectamente conocedor de dichas deficiencias, extremo que se acreditará en el momento procesal oportuno (interrogatorio, testigos...).

En el propio informe técnico que hemos acompañado ya se indica que la avería tuvo que ser observada por el anterior propietario del vehículo, habida cuenta que difícilmente podía el citado turismo circular más de [Nº] kilómetros seguidos, sin que el mismo se parase inmediatamente.

TERCERO.- A la vista de las circunstancias mi representado se dirigió nuevamente al vendedor, comunicándole el contenido del referido informe técnico y solicitando que, estando obligado al saneamiento por vicios ocultos, procediera de inmediato a dar por resuelto el contrato, recogiendo el vehículo que había sido objeto de la venta y reintegrando a mi mandante el importe de dicha venta, ascendente a [IMPORTE] euros.

A tal fin remitió primeramente el correspondiente burofax cuya copia se adjunta como documento nº [Nº DE DOCUMENTO] y, posteriormente, un requerimiento notarial que se adjunta como documento nº [Nº DE DOCUMENTO].

CUARTO.- Se han agotado todas las vías extrajudiciales de solución amistosa de la controversia sin que el demandado haya atendido las reclamaciones efectuadas, por lo que no queda más remedio a esta parte que impetrar el auxilio judicial, lo que, efectivamente, se hace por medio del presente escrito.

Se adjuntan como prueba copias de las comunicaciones enviadas y recibidas durante el proceso de negociación, incluidas cartas, correos electrónicos y/o actas de reuniones como documentos números [COMPLETAR].

A los hechos anteriores son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- JURISDICCIÓN Y COMPETENCIA.

Radicando la competencia genérica en el orden civil de la jurisdicción, detenta la competencia objetiva y funcional la Sección Civil del Tribunal de Instancia, por aplicación de lo dispuesto en los arts. 85.1 LOPJ y 45 LEC, y puesto que no está prevenido un fuero territorial preceptivo específico, con arreglo a lo previsto en el art. 50.1 LEC, resulta territorialmente competente el Tribunal a que me dirijo, puesto que es el del partido del lugar donde tienen su domicilio el demandado.

II.- PROCEDIMIENTO.

La presente demanda deberá sustanciarse por las normas del juicio ordinario, a tenor de lo prevenido en los arts. 248 y 249.2 LEC, toda vez que el criterio de atribución preferente de la materia objeto del proceso resulta inaplicable, ya que carece de especialidad típica la de éste, y cumplir entonces el criterio de cuantía, que supera los quince mil euros.

III.- CUANTÍA.

Cumpliendo lo prevenido en el art. 253.1 LEC, se cifra la cuantía de esta demanda en la cantidad de [IMPORTE] euros, correspondiente a la suma de cantidades reclamadas, todo ello con arreglo a la regla 1.ª del art. 251 LEC.

IV.- CAPACIDAD Y LEGITIMACIÓN.

Tanto mi mandante como el demandado son personas físicas, mayores de edad, en pleno ejercicio de sus derechos civiles, por lo que tienen capacidad para ser parte y capacidad procesal ex arts. 6.1.1.º y 7.1 LEC.

Corresponde la legitimación activa directa a mi mandante, como comprador de una cosa con vicios o defectos ocultos que la hacen impropia para el uso a que se la destina, de conformidad con lo dispuesto en los arts. 1.484 y ss. CCiv, frente al vendedor de la misma, sobre quien recae la legitimación pasiva para el ejercicio de esta acción.

V.- POSTULACIÓN Y DEFENSA.

Conforme a los arts. 23 y 31 LEC se formula esta demanda a través de Procurador/a de los Tribunales con poder notarial para pleitos, y con dirección y firma de Letrado habilitado ante el tribunal. Asimismo se cumplen los requisitos formales del art. 399 LEC.

VI.- PLAZO DE EJERCICIO DE LA ACCIÓN.

En lo que se refiere al plazo de ejercicio de la acción, el art. 1.490 CCiv prevé que las acciones que emanan de lo dispuesto en los cinco artículos precedentes se extinguirán a los seis meses, contados desde la entrega de la cosa vendida.

VII.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VIII.- FUNDAMENTOS MATERIALES.

Dispone el art. 1.484 CCiv que el vendedor estará obligado al saneamiento por los defectos ocultos que tuviere la cosa vendida, si la hacen impropia para el uso a que se la destina, o si disminuyen de tal modo este uso que, de haberlos conocido el comprador, no la habría adquirido o habría dado menos precio por ella; pero no será responsable de los defectos manifiestos o que estuvieren a la vista, ni tampoco de los que no lo estén, si el comprador es un perito que, por razón de su oficio o profesión, debía fácilmente conocerlos.

En este caso, se trata de defectos que no son manifiestos ni han estado a la vista, ni mi representado es perito o experto en la industria de vehículos a motor.

Asimismo, el art. 1.485 del mismo texto legal dispone que el vendedor responde al comprador del saneamiento por los vicios o defectos ocultos de la cosa vendida, aunque los ignorase. Esta disposición no regirá cuando se haya estipulado lo contrario, y el vendedor ignorara los vicios o defectos ocultos de lo vendido.

En el contrato no se estipuló pacto alguno relativo a la exoneración del vendedor por los vicios o defectos ocultos, aunque éste conocía perfectamente estas deficiencias, por lo que no quedaría en ningún caso exonerado de responsabilidad por este concepto

Finalmente, el art. 1.486 CCiv prevé que, en los casos de los dos artículos anteriores, el comprador podrá optar entre desistir del contrato, abonándosele los gastos que pagó, o rebajar una cantidad proporcional del precio, a juicio de peritos. Si el vendedor conocía los vicios o defectos ocultos de la cosa vendida y no los manifestó al comprador, tendrá éste la misma opción y además se le indemnizará de los daños y perjuicios, si optare por la rescisión.

En el caso que nos ocupa, mi mandante ejerce acción de desistimiento del contrato, interesando la devolución de lo que constituyó el objeto de la compra y la recuperación del importe satisfecho con sus intereses, así como el abono de los gastos que pagó por razón del contrato celebrado, a cuyos efectos se señalan las diferentes partidas de gastos abonados por aquél:

Se acompañan bajo los números [COMPLETAR], los documentos que acreditan el importe de las cantidades reclamadas.

Dado que, según se ha expuesto más arriba, el demandado conocía la existencia de los vicios o defectos y no los manifestó al comprador, se solicita, además del vendedor indemnización por los daños y perjuicios causados, a cuyos efectos se señalan los siguientes:

Se acompañan bajo los números [COMPLETAR], los documentos que acreditan el importe de los daños y perjuicios reclamados.

IX.- COSTAS.

Conforme a lo establecido en el art. 394 LEC las costas procesales se impondrán a la parte demandada.

En virtud de todo lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito, documentos que acompañan y copias preceptivas, se sirva admitir todo ello, y, en su virtud, de conformidad con las manifestaciones que contiene, tenga por interpuesta en la representación ostento, demanda de juicio declarativo ordinario, en ejercicio de acción redhibitoria, contra D./Dña. [NOMBRE Y APELLIDOS], y previos los trámites legales pertinentes, dicte sentencia que verse sobre los siguientes extremos:

a) Declare resuelto, por ejercicio de la acción redhibitoria el contrato celebrado entre mi representado, como parte compradora, y el demandado, como parte vendedora.
b) Condene al demandado a la restitución del precio abonado por mi representado, por un importe de [IMPORTE] euros, más los intereses correspondientes, así como al abono de los gastos satisfechos por mi representado, por importe de [IMPORTE] euros, lo que asciende a un total de [IMPORTE] euros.
c) Declare la obligación de mi mandante a devolver al demandado la posesión del vehículo en el estado en que la recibió
d) Condene al demandado a indemnizar a mi representado por los daños y perjuicios sufridos, que se han cifrado en la cantidad de [IMPORTE] euros

Todo ello con expresa condena en costas del presente procedimiento.

OTROSÍ PRIMERO DIGO que siendo el poder que acompaño, general para pleitos y necesitándolo para otros usos procesales,

SUPLICO AL TRIBUNAL que previo su inserción por copia en autos, acuerde su desglose y devolución a esta parte.

OTROSÍ SEGUNDO DIGO que a los efectos de lo previsto en el art. 337.2 LEC esta parte hace mención especial al hecho de que es de su interés que el perito de parte que ha emitido el dictamen pericial aportado como documento n.º [NÚMERO] de la demanda, sea citado al acto de juicio al objeto de que pueda exponer y explicar el mismo o responder a las preguntas de aclaración que se le formulen in situ, para mayor claridad del contenido del mismo.

SUPLICO AL TRIBUNAL que tenga por efectuadas las anteriores manifestaciones a los efectos legales oportunos y, acuerde en su momento procesal oportuno la citación al perito de parte al acto de juicio para que pueda exponer y explicar el dictamen y responder a las preguntas que se le formulen.

Es justicia de hacerse en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

NOTAS DEL FORMULARIO

(1) A la hora de su acreditación, todos los poderes deben estar inscritos en el Registro Electrónico de Apoderamientos Judiciales (REAJ). Se supone que, para su acreditación, basta con la consulta (de dicho Registro) automatizada orientada al dato. Algo que está a disposición de cualquier Letrado de la Administración de Justicia. Sin embargo, dado que el art. 24.2 LEC, configura la certificación de dicha inscripción como vía subsidiaria de acreditación, para el caso de que el sistema no permita aquella consulta automatizada; se señala en el modelo que se acompaña certificación electrónica. El sistema permite emitir dicha certificación para quien inscribe el poder.

(2) El art. 155.3 LEC permite fijar expresar varios domicilios del demandado (el que aparezca en el padrón municipal o conste oficialmente a estos efectos; el que aparezca en Registro oficial o en publicaciones de colegios profesionales, si se trata de empresas o personas colegiadas; donde desarrolle su actividad profesional o laboral no ocasional; si es empresa mercantil, el domicilio de cualquiera de sus administradores, gerentes, o apoderados; o, si es asociación que consta en registro oficial; el domicilio del presidente, miembro o gestor de la Junta correspondiente). Cuando se señalen varios, indicará el orden a seguir para la notificación, con vistas al éxito de la misma.

(3) El art. 155.3 LEC configura una obligación adicional del demandante, consistente en aportar cuantos datos sean de utilidad para localizar al demandado: número de identificación fiscal o de extranjeros, nº [Nº] de teléfono o de fax, dirección de correo electrónico, o similares.

========================================================================
