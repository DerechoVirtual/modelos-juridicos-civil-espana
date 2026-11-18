---
name: demanda-cumplimiento-contrato-venta-cosa-ajena-273
description: "Redacta el escrito «Demanda de cumplimiento de contrato por venta de cosa ajena» (formulario 273 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de cumplimiento de contrato por venta de cosa ajena

> Formulario 0273 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD (2 veces)
- [ ] Nº DE DOCUMENTO (6 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] COLEGIO
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] CALLE
- [ ] IMPORTE (5 veces)
- [ ] FECHA (2 veces)
- [ ] ACTO O RESOLUCIÓN
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…D.»; «…e actúa en nombre y representación de D.»; «…, mayor de edad, vecina de»; «…entes: HECHOS PRIMERO.- Que con fecha de»; «…ado contrato quedó fijado en la cláusula»; «…euros, de los cuales un»; «…mbre del demandado sino de su padre, Don»; «…nota simple del Registro de la Propiedad»; «…uicios que a continuación se relacionan:»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 85.1 LOPJ
- arts. 45 LEC
- art. 50.1 LEC
- art. 7.1 LEC
- arts. 248 y 249.2 LEC
- arts. 399 a 436 LEC
- art. 249.1 LEC
- art. 253.1 LEC
- art. 10 LEC
- art. 23.1 LEC
- art. 31.1 LEC
- art. 1.964 CCiv
- art. 5 de la Ley Orgánica 1/2025
- art. 1.124 CCiv
- arts. 1.124 y 1.101 CCiv
- art. 394.1 LEC

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

### Formulario 0273 · Demanda de cumplimiento de contrato por venta de cosa ajena

- Año del modelo: 2020
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 1 rangos de artículos despegados («25 a31» → «25 a 31»); 29 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO)
- Avisos de la revisión: REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda en ejercicio de acción de cumplimiento de contrato en supuesto de venta de cosa ajena

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D. [COMPLETAR], Procurador de los Tribunales, que actúa en nombre y representación de D. [COMPLETAR], con domicilio en [LOCALIDAD], como acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], y asistida de la Letrada en ejercicio Dña. colegiada nº [Nº DE COLEGIADO/A] del Iltre. Colegio de Abogados de [COLEGIO], con despacho abierto en [LOCALIDAD], ante el Tribunal comparezco y como mejor proceda en Derecho, DIGO:

Que en la representación que ostento y a través del presente escrito, formulo demanda de JUICIO DECLARATIVO ORDINARIO, en ejercicio de ACCIÓN DE CUMPLIMIENTO DE CONTRATO DE COMPRAVENTA, contra Dña. [NOMBRE Y APELLIDOS], mayor de edad, vecina de [COMPLETAR], calle [CALLE], en base a los siguientes:

HECHOS

PRIMERO.- Que con fecha de [COMPLETAR], hallándose en trámites de búsqueda de primera vivienda, mi mandante, en calidad de comprador, convino con Dña. [NOMBRE Y APELLIDOS], la compra de una vivienda sita en

En el citado contrato quedó fijado en la cláusula [COMPLETAR] que el precio de la compraventa era de [IMPORTE] euros, de los cuales un [COMPLETAR] % fueron abonados en el momento de la firma del contrato mediante transferencia bancaria, quedando aplazado el resto del precio hasta el momento de otorgamiento de la escritura, la cual debía otorgarse dentro del término fijado en el contrato.

Se acredita con copia simple del contrato de compraventa que se acompaña como documento nº [Nº DE DOCUMENTO] y copia del resguardo de la transferencia bancaria como documento nº [Nº DE DOCUMENTO]

SEGUNDO.- En el momento de celebración del contrato la finca no figuraba inscrita a nombre del demandado sino de su padre, Don [COMPLETAR] aunque el vendedor alegó que la finca ya era de su propiedad, por haberla adquirido a título hereditario del titular registral, aunque todavía no se había puesto al día el Registro y se comprometió frente a mi representado a subsanar la falta de inscripción, dentro del plazo establecido para el otorgamiento de escritura.

Se acompaña nota simple del Registro de la Propiedad [COMPLETAR], de fecha [FECHA], como documento nº [Nº DE DOCUMENTO]

TERCERO.- Llegado el plazo convenido para su otorgamiento, estando preparada la escritura en la notaría para la venta, la vendedora no compareció en dicha notaría en la fecha señalada, por lo que no fue posible llenar dicha formalidad, ante lo cual mi representada procedió a la consignación del resto del precio de la compraventa, como se acredita con el justificante de la consignación que se acompaña como documento nº [Nº DE DOCUMENTO]

CUARTO.- Como consecuencia del incumplimiento de lo estipulado por parte de la vendedora, aparte de los ocasionados por la falta de entrega de la cosa, mi representado ha sufrido los daños y perjuicios que a continuación se relacionan: [COMPLETAR]; a cuya justificación se acompañan los siguientes documentos

QUINTO.- Mi patrocinado ha intentado una solución amistosa con la demandada, resultando infructuosas todas sus gestiones.

Finalmente, en fecha [FECHA] fue remitido burofax al objeto de dejar constancia fehaciente de la reclamación. Se adjunta certificación del Servicio de Correos como documento nº [Nº DE DOCUMENTO]

A los anteriores Hechos son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA.

Sin duda en cuanto a la jurisdicción de los tribunales del Reino en su orden civil, le corresponde conocer de este asunto al Tribunal a quien tengo el honor de dirigirme por ser el de Instancia (art. 85.1 LOPJ y arts. 45 LEC) del lugar del domicilio de la demandada, puesto que corresponde al fuero genérico de las personas físicas del art. 50.1 LEC, dado que no hay previsto otro específico para la materia o acción que se ejercita.

II.- CAPACIDAD.

Tanto el actor, mi patrocinado, como la demandada son personas físicas mayores de edad, respecto de las que no consta discapacidad, por lo que detentan capacidad para ser parte (art. 6.1.1º LEC), y capacidad procesal, o de obrar en este concreto juicio (art. 7.1 LEC).

III- PROCEDIMIENTO.

El procedimiento a través del cual se ha de sustanciar las pretensiones es el correspondiente al juicio ordinario, conforme a los arts. 248 y 249.2 LEC, y se seguirá por los trámites de los arts. 399 a 436 LEC, puesto que es aplicable el criterio subordinado de la cuantía, dado que la materia no es de las listadas en el art. 249.1 LEC, y el valor de lo reclamado es superior a 15.000 euros.

IV.- CUANTÍA.

Cumpliendo la exigencia del art. 253.1 LEC, se cifra la cuantía de la demanda en la cantidad de [IMPORTE] euros.

Dicha cifra se obtiene de agregar, conforme al art. 252.2ª LEC, al valor del inmueble que se vendiera, conforme al precio pactado (art. 251.2ª párrafo 2º LEC), dado que se pide la condena a su entrega, a la que se pide como indemnización por incumplimiento, de [IMPORTE] euros (art. 251.1ª LEC).

V.- LEGITIMACIÓN.

El art. 10 LEC legitima para comparecer y actuar en juicio a los titulares de la relación jurídica o del objeto litigioso. En el caso de autos, corresponde la legitimación activa ordinaria a mi representado, como comprador del inmueble, frente al vendedor, quien ostenta la legitimación pasiva correlativa para el ejercicio de la acción.

VI.- POSTULACIÓN.

Esta parte, como será debido para la personación que convenga a la contraria, comparece por medio de Procurador/a de los Tribunales habilitado ante el tribunal (art. 23.1 LEC), y bajo la dirección del Letrado en ejercicio (art. 31.1 LEC).

VI.- PRESCRIPCIÓN.

A falta de un plazo específico de prescripción para el ejercicio de esta acción, será aplicable el plazo general de cinco años establecido en el art. 1.964 CCiv para el ejercicio de las acciones personales.

VII.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VIII.- FONDO DEL ASUNTO.

La venta de cosa ajena fue admitida por el Digesto y las Partidas. El CCiv, siguiendo el precedente del Proyecto de 1851 no regula esta situación, lo que sin duda está muy relacionado con el sistema de transmisión de la propiedad consagrado en sus normas, sistema que, como en el derecho romano, niega al contrato virtualidad traslativa, configurando la compraventa como un negocio de carácter obligacional.

La jurisprudencia ha definido la venta de cosa ajena como aquélla en la que al perfeccionarse la venta, el vendedor no sea el dueño de la cosa vendida. En efecto, la STS de 11 de octubre de 2006, rec. 4490/1999, establece que lo determinante para entender vendida una cosa ajena es que, al perfeccionarse el segundo contrato, el vendedor no sea el dueño, lo cual puede resultar porque nunca lo hubiere sido o hubiera dejado de serlo por haberla enajenado antes.

Doctrina y jurisprudencia vienen señalando de consuno la validez de la venta de cosa ajena, con fundamento en el carácter obligacional y no traslativo de la compraventa en nuestro Derecho. Del contrato de compraventa nace la obligación del vendedor de adquirir la cosa para poder entregarla y trasmitirla al comprador. A partir de aquí, siguiendo a LLAMAS POMBO, puede ocurrir que el vendedor cumpla tal obligación, en cuyo caso el contrato no presenta la más mínima particularidad o que el vendedor incumpla su obligación, porque no puede o no quiere adquirir la cosa perteneciente a un tercero, en cuyo caso puede suceder dos cosas: A) que pese a la titularidad del tercero, el comprador entre en posesión de la cosa, en cuyo caso, a su vez habrá que distinguir dos supuestos: que el verdadero propietario reivindique la cosa y prive de ella al comprador; B) que el comprador no llegue nunca a entrar en posesión de la cosa, lo que dará lugar a un incumplimiento definitivo del contrato por parte del vendedor, y a los efectos que ello produce, con aplicación de la facultad resolutoria del art. 1.124 CCiv y, en todo caso, de la indemnización de daños y perjuicios conforme a los arts. 1.101 y ss. CCiv.

La jurisprudencia en relación a la venta de cosa ajena ha sido oscilante en la materia, puesto que algunas sentencias antiguas sostuvieron la nulidad de la venta de cosa ajena fundamentalmente basándola en la inexistencia del contrato por carencia de objeto. Sin embargo, a partir de la sentencia de 1 de marzo de 1954 es unánime la admisión de la validez de la venta de cosa ajena, no pudiendo en ningún caso tildarse de inexistente por falta de objeto. Por cuanto el objeto existe, señalando la STS de fecha 20 de marzo de 2007, rec. 1098/2000, que "el caso de una persona, en general, que vende cosa que antes ha transmitido a otro es venta de cosa ajena que la jurisprudencia y la doctrina han aceptado su validez, en el sentido de que el vendedor puede adquirirla posteriormente y dejar como definitiva la transmisión, o puede darse la obligación de saneamiento por evicción, o puede dar lugar a la adquisición a non domino por el juego de los artículos mencionados: lo cual lo han reiterado, entre otras, las sentencias de 14 de abril de 2000, 7 de febrero de 2001, 8 de marzo de 2001, 10 de junio de 2003 . Lo que no tiene sentido es la afirmación que hacen las sentencias de instancia de que en tal caso la compraventa es nula o inexistente por falta de objeto. El objeto del contrato de compraventa es la cosa y el precio (rectius, las obligaciones recíprocas de entregar la cosa y el precio) que no comprende el que la cosa sea ajena; ésta, pues, es válida y puede llegar a ser eficaz, tal como se ha dicho y esta doctrina es la proclamada claramente por la sentencia del pleno de esta Sala, de 5 de marzo de 2007, seguida como no podía ser menos, por la de 16 del mismo mes y año". Viniendo a precisar la STS de fecha 5 de mayo de 2008, rec. 786/2001 que "La venta de cosa ajena será ineficaz frente al verdadero propietario que podrá ejercitar acción reclamando la declaración de su ineficacia o acción declarativa de dominio o reivindicatoria sobre el objeto de aquélla. Pero entre las partes, vendedora y compradora, será eficaz".

Conforme a la jurisprudencia citada y de acuerdo con lo establecido en el art. 1.124 CCiv, mi representado puede optar por exigir el cumplimiento del contrato, esto es, la entrega de la cosa, o instar la resolución del mismo, todo ello con indemnización de los daños y perjuicios causados. Mi representado opta por la primera opción citada, solicitando que el demandado proceda a la entrega de la cosa vendida mediante el correspondiente otorgamiento de escritura pública a su favor, reclamación que se traducirá en la indemnización de daños y perjuicios, en cuanto el propietario no esté dispuesto a entregar la cosa vendida. Y todo ello, con indemnización de los daños y perjuicios causados en los términos que se indican en el antecedente de hecho cuarto de esta demanda, de conformidad con lo establecido en los arts. 1.124 y 1.101 CCiv.

IX.- COSTAS.

Las costas del presente procedimiento deberán ser impuestas a la parte demandada, con arreglo al art. 394.1 LEC, que recoge el principio objetivo del vencimiento en la materia por lo que respecta a los juicios declarativos en su primera instancia.

En atención a todo lo anterior es por lo que,

SUPLICO AL TRIBUNAL,

que teniendo por presentado este escrito, documentos que acompañan y copias preceptivas, se sirva admitir todo ello, y, en su virtud, de conformidad con las manifestaciones que contiene, tenga por interpuesta en la representación ostento, demanda de juicio declarativo ordinario, en ejercicio de acción de cumplimiento de contrato, contra [ACTO O RESOLUCIÓN], y previos los trámites legales pertinentes, y previo recibimiento del juicio a prueba, dicte sentencia con los siguientes pronunciamientos:

1.º que se condene al demandado a cumplir el contrato privado de compraventa suscrito por mi representado, ordenando su elevación a escritura pública, así como al pago de la cantidad de [IMPORTE] euros, en concepto de indemnización de daños y perjuicios, conforme a lo indicado en el antecedente de hecho cuarto de esta demanda;
2.º subsidiariamente, para el caso de que no se pueda dar cumplimiento a lo anterior, que se condene a la vendedora al pago de [IMPORTE] euros, en concepto de daños y perjuicios causados a mi representada por la falta de entrega de la vivienda.

Todo ello con expresa condena en costas del presente procedimiento.

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado

	Firma de Procurador
