---
name: demanda-saneamiento-gravamenes-ocultos-412
description: "Redacta el escrito «Demanda de saneamiento por gravámenes ocultos» (formulario 412 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de saneamiento por gravámenes ocultos

> Formulario 0412 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] COLEGIO
- [ ] CALLE
- [ ] LOCALIDAD (2 veces)
- [ ] NÚMERO (4 veces)
- [ ] FECHA (5 veces)
- [ ] IMPORTE (4 veces)
- [ ] LUGAR
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, mayor de edad y vecino de»; «…gales: HECHOS PRIMERO.- Que con fecha de»; «…e la existencia de un embargo a favor de»; «…ión del proceso de apremio entablado por»; «…omunicación realizada por el registrador»; «…cionados mediante los documentos números»; «…iante correspondencia escrita, en fechas»; «…tas de reuniones como documentos números»; «…nto del proceso de apremio entablado por»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 656 y 659 LEC
- art. 85.1 LOPJ
- art. 45 LEC
- art. 50.1 LEC
- arts. 248 y 249.2 LEC
- art. 253.1 LEC
- art. 251 LEC
- arts. 23 y 31 LEC
- art. 399 LEC
- art. 1483 CCiv
- art. 5 de la Ley Orgánica 1/2025
- art. 1101 CCiv
- art. 394 LEC

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

### Formulario 0412 · Demanda de saneamiento por gravámenes ocultos

- Año del modelo: 2018
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 36 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda de juicio ordinario reclamando indemnización en ejercicio de la acción de saneamiento por cargas o gravámenes ocultos (acción estimatoria o quanti minoris).

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], conforme acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], y con la asistencia del Letrado D./Dña. [NOMBRE Y APELLIDOS], del Ilustre Colegio de Abogados de [COLEGIO], cuyo despacho está abierto en esta población, calle [CALLE], ante la Sección Civil del Tribunal de Instancia que por turno de reparto corresponda, comparezco y, como mejor proceda en Derecho, DIGO:

Que mediante el presente escrito formulo DEMANDA DE JUICIO DECLARATIVO ORDINARIO POR LA QUE SE RECLAMA INDEMNIZACIÓN EN EJERCICIO DE ACCIÓN DE SANEAMIENTO POR GRAVÁMENES OCULTOS, contra D./Dña. [NOMBRE Y APELLIDOS], mayor de edad y vecino de [COMPLETAR], con domicilio en [LOCALIDAD], demanda que fundamento en los siguientes hechos y fundamentos legales:

HECHOS

PRIMERO.- Que con fecha de [COMPLETAR], mi representado, suscribió en calidad de comprador un contrato de compraventa con el demandado, D./Dña. [NOMBRE Y APELLIDOS], por el que éste me transmitía una finca urbana sita en [LOCALIDAD].

Se acompaña copia simple de la escritura de compraventa como documento n.º [NÚMERO].

En la expresada escritura nada se menciona acerca de la existencia de un embargo a favor de [COMPLETAR], decretado contra la finca con fecha [FECHA] y, por tanto, antes de la perfección del contrato de compraventa, el cual fue anotado preventivamente en el Registro después de celebrarse la misma, con fecha [FECHA].

Se acompaña certificación registral acreditativa de este extremo como documento n.º [NÚMERO].

SEGUNDO.- Que posteriormente a dicha venta, con fecha [FECHA], por lo tanto, con una antelación inferior a un año respecto de la presentación de la demanda, esta parte tuvo conocimiento de la existencia de dicho embargo, a raíz de la comunicación del proceso de apremio entablado por [COMPLETAR], en el seno del cual se había decretado el embargo, toda vez que su titularidad figuraba en la certificación de cargas expedida por el registrador conforme a lo dispuesto en los arts. 656 y 659 LEC.

Se acompaña como documento n.º [NÚMERO] copia de la comunicación realizada por el registrador [COMPLETAR].

En consecuencia, estamos ante una carga o gravamen existente con anterioridad a la perfección del negocio de compraventa, omitido por el vendedor en su escritura, lo que indica su carácter de oculto, que de haber sido conocido por mi representado es dable suponer que no lo habría adquirido, ya que de otro modo se vería obligado a soportar las consecuencias derivadas del proceso de apremio entablado contra la finca.

TERCERO.- Que interesa poner de manifiesto, a los efectos de reclamar los daños y perjuicios causados a esta parte, que el vendedor conocía perfectamente al tiempo de perfeccionar la venta la existencia del embargo referido, toda vez que aquél tuvo conocimiento de la apertura de la vía de apremio y de la existencia del embargo antes de la perfección del contrato de compraventa, lo que evidencia su mala fe al ocultar este dato en la escritura de compraventa que me unía con el ahora demandado.

Se acompaña como documento n.º [NÚMERO] testimonio de la resolución dictada por el Letrado de la Administración de Justicia decretando el embargo.

Los daños y perjuicios sufridos como consecuencia de la existencia del embargo son los que a continuación se relacionan y valoran:

Se acredita el importe de los daños y perjuicios relacionados mediante los documentos números [COMPLETAR] de los que acompañan a la demanda.

A los hechos anteriores son de aplicación los siguientes:

CUARTO.- Previamente a la presentación de la presente demanda, se han llevado a cabo negociaciones con la parte demandada, con el objetivo de cumplir el requisito de procedibilidad, y resolver la controversia de manera amistosa y extrajudicial. Dichas negociaciones se desarrollaron en cumplimiento de los principios de buena fe, con la intención de alcanzar una solución satisfactoria; incluyéndose entre las acciones realizadas el intercambio de comunicaciones formales mediante correspondencia escrita, en fechas [COMPLETAR], en las cuales esta parte expresó su disposición para dialogar y propuso alternativas de solución.

Se adjuntan como prueba copias de las comunicaciones enviadas y recibidas durante el proceso de negociación, incluidas cartas, correos electrónicos y/o actas de reuniones como documentos números [COMPLETAR].

Finalmente, mi representado envió un requerimiento fehaciente al demandado con fecha [FECHA], fijando un plazo de 30 días naturales para llegar a un acuerdo amistoso, a través del abogado que firma este escrito, el cual fue contestado por el demandado por el mismo medio, rechazando el acuerdo, viéndonos en la necesidad de acudir a la presente vía judicial.

Acompaño como documento nº [Nº DE DOCUMENTO], el requerimiento efectuado y como documento nº [Nº DE DOCUMENTO], la contestación del demandado.

FUNDAMENTOS DE DERECHO

I.- JURISDICCIÓN Y COMPETENCIA.

Radicando la competencia genérica en el orden civil de la jurisdicción, detenta la competencia objetiva y funcional la Sección Civil del Tribunal de Instancia, por aplicación de lo dispuesto en el art. 85.1 LOPJ y art. 45 LEC, y puesto que no está prevenido un fuero territorial preceptivo específico, con arreglo a lo previsto en el art. 50.1 LEC, resulta territorialmente competente el Tribunal a que me dirijo, puesto que es el del partido del lugar donde tienen su domicilio el demandado.

II.- PROCEDIMIENTO.

La presente demanda deberá sustanciarse por las normas del juicio ordinario, a tenor de lo prevenido en los arts. 248 y 249.2 LEC, toda vez que el criterio de atribución preferente de la materia objeto del proceso resulta inaplicable, ya que carece de especialidad típica la de éste, y cumplir entonces el criterio de cuantía, que supera los quince mil euros.

III.- CUANTÍA.

Cumpliendo lo prevenido en el art. 253.1 LEC, se cifra la cuantía de esta demanda en la cantidad de [IMPORTE] euros, correspondiente a la cantidad reclamada, todo ello con arreglo a la regla 1.ª del art. 251 LEC.

IV.- CAPACIDAD Y LEGITIMACIÓN.

Tanto mi mandante como el demandado son personas físicas, mayores de edad, en pleno ejercicio de sus derechos civiles, por lo que tienen capacidad para ser parte y capacidad procesal ex arts. 6.1.1.º y 7.1 LEC.

Corresponde la legitimación activa directa a mi mandante, como comprador de una finca con cargas o gravámenes ocultos, frente al vendedor de la misma, sobre quien recae la legitimación pasiva para el ejercicio de esta acción.

V.- POSTULACIÓN Y DEFENSA.

Conforme a los arts. 23 y 31 LEC se formula esta demanda a través de Procurador/a de los Tribunales con poder notarial para pleitos, y con dirección y firma de Letrado habilitado ante el tribunal. Asimismo se cumplen los requisitos formales del art. 399 LEC.

VI.- PLAZO DE EJERCICIO DE LA ACCIÓN.

En lo que se refiere al plazo de ejercicio de la acción, el art. 1483 CCiv prevé el plazo de un año, que es de caducidad, para el ejercicio de los derechos a favor del comprador, consistente en el ejercicio de acción rescisoria o en la solicitud de indemnización de daños y perjuicios, a contar desde el otorgamiento de la escritura (art. 1483, párrafo 2.º CCiv). Pero transcurrido el año, sólo podrá reclamar la indemnización dentro de un período igual, a contar desde el día en que haya descubierto la carga o servidumbre (art. 1483 párrafo 3.º CCiv).

En consecuencia, por haber transcurrido más de un año desde el otorgamiento de la escritura, la acción por la que se insta la indemnización sólo puede ejercitarse en el plazo de un año a contar desde el día en que se haya descubierto la carga o servidumbre, y al no haber transcurrido dicho plazo desde que el actor tuvo conocimiento del proceso de apremio entablado por [COMPLETAR], la presente demanda se presenta dentro del plazo establecido en dicho precepto.

VII.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VIII.- FUNDAMENTOS MATERIALES.

A tenor de lo expuesto, se reclama indemnización en ejercicio de acción de saneamiento por gravámenes ocultos de la finca vendida, conforme a lo dispuesto en el citado art. 1483 CCiv.

Concurren todos los requisitos del saneamiento por gravámenes ocultos; a saber:

1.º) Que la finca esté gravada con alguna carga o servidumbre, cual es la existencia del embargo sobre la finca.
2.º) Que sea oculta. Lo que comprende varios extremos: en primer lugar, que no esté mencionada en la escritura; en segundo lugar, que el comprador, por la razón que fuere, no tenga conocimiento de su existencia; en tercer lugar, que la carga o servidumbre no sea aparente; en cuarto lugar, que no esté inscrita en el registro de la Propiedad.
3.º) Que el gravamen sea tan importante que, de haberla conocido el comprador, no habría adquirido la finca.

Los efectos de este saneamiento son que el comprador tiene opción (art. 1483, primer párrafo in fine) para resolver (en realidad se trata de resolución, aunque el código la llame rescisión) el contrato (acción redhibitoria) o para exigir indemnización (acción estimatoria o quanti minoris), que será la correspondiente al valor del gravamen que tiene que soportar, es decir, el menor precio que a la finca se le atribuye por causa del gravamen.

Por lo tanto, el ejercicio de esta acción legitima a mi representado, como parte compradora, para obtener una rebaja del precio satisfecho por la finca transmitida, tomando en consideración el menor valor de la misma por causa del gravamen, que se cifra en una cantidad equivalente a la del embargo que pesa sobre la finca.

Por otra parte, habida cuenta que el vendedor ha actuado de mala fe, por cuanto conocía la existencia del embargo sobre la finca antes de perfeccionarse la compraventa, se reclaman los daños y perjuicios causados a mi representado que se indican en el hecho tercero de la demanda, de conformidad con el art. 1101 CCiv, por un importe total de [IMPORTE] euros.

IX.- COSTAS.

Conforme a lo establecido en el art. 394 LEC las costas procesales se impondrán a la parte demandada.

En virtud de todo lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito, documentos que acompañan y copias preceptivas, se sirva admitir todo ello, y, en su virtud, de conformidad con las manifestaciones que contiene, tenga por interpuesta en la representación ostento, demanda de juicio declarativo ordinario, en ejercicio de acción de saneamiento por gravámenes ocultos, contra D./Dña. [NOMBRE Y APELLIDOS], y previos los trámites legales pertinentes, dicte sentencia que condene al demandado:

a) al pago de [IMPORTE] euros en concepto de indemnización por el menor valor de la finca por la existencia del embargo;
b) al pago de [IMPORTE] euros en concepto de indemnización por los daños y perjuicios causados a mi representado por razón de la mala fe del vendedor conocedor del embargo.

Todo ello con expresa condena en costas del presente procedimiento.

OTROSÍ PRIMERO DIGO que siendo el poder que acompaño, general para pleitos y necesitándolo para otros usos procesales,

SUPLICO AL TRIBUNAL que previo su inserción por copia en autos, acuerde su desglose y devolución a esta parte.

Es justicia de hacerse en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

========================================================================
