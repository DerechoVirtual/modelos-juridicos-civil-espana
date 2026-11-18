---
name: oposicion-credito-compensable-juicio-verbal-591
description: "Redacta el escrito «Oposición por crédito compensable en juicio verbal» (formulario 591 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición por crédito compensable en juicio verbal

> Formulario 0591 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (9 veces)
- [ ] LOCALIDAD
- [ ] CALLE (2 veces)
- [ ] NÚMERO
- [ ] Nº DE DOCUMENTO
- [ ] COLEGIO
- [ ] Nº
- [ ] SSTS de 25 de junio de 1993 y 19 de julio de 1994 
- [ ] LUGAR (2 veces)
- [ ] FECHA (2 veces)
- [ ] IMPORTE (4 veces)
- [ ] MARCA/MODELO
- [ ] MATRÍCULA
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…o se acredita con los documentos números»; «…opia se acompaña como documentos números»; «…y»

## Elecciones que hay que hacer

- Letrado / Letrada
- colegiado / colegiada
- del / de la

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 23 y 31 LEC
- art. 1254 CCiv
- art. 394 LEC
- art. 438.10 LEC
- art. 438.3 LEC
- art. 408 LEC
- art. 438 LEC

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

### Formulario 0591 · Oposición por crédito compensable en juicio verbal

- Año del modelo: 2016
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 3 desplegables convertidos en elección en blanco; 29 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de contestación a la demanda en juicio verbal oponiendo crédito compensable.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD], calle [CALLE], n.º [NÚMERO], como acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], bajo la asistencia de D./Dña. [NOMBRE Y APELLIDOS], [ELEGIR: Letrado / Letrada] del Ilustre Colegio de Abogados de [COLEGIO], con n.º [Nº] de [ELEGIR: colegiado / colegiada], ante el Tribunal comparezco y respetuosamente (1) DIGO:

Que siguiendo expresas instrucciones de mi mandante, por medio del presente me persono en los autos de juicio verbal /, seguidos en su contra por D./Dña. [NOMBRE Y APELLIDOS], y formulo CONTESTACIÓN A LA DEMANDA, en base a los hechos y fundamentos que a continuación se exponen.

HECHOS

PRIMERO

Con carácter previo se niegan los hechos expuestos en la demanda que se contesta, en cuanto no sean expresamente reconocidos en los siguientes apartados de hecho.

SEGUNDO

Es más cierto que mi mandante acudió al despacho del actor para interesarle su dictamen como profesional en la materia, requiriéndole dicho profesional que le aportara escrituras y documentos con la finalidad de que el demandante pudiera llevar a cabo su cometido. Se convino, siempre verbalmente, que el demandante tomaría una primera impresión del encargo y antes de estudiar la posibilidad de ejercer acciones, comunicaría a mi parte el importe aproximado de su minuta, que incluiría no sólo el dictamen previo sino además la llevanza del posible pleito.

En esta situación y al cabo de varios meses sin tener otra noticia ni requerimiento previo alguno nos encontramos con la presentación y exigencia de pago de su minuta de honorarios, con la natural extrañeza por nuestra parte ya que ni siquiera se le ha entregado el informe o dictamen a que dicha minuta corresponda.

TERCERO

No es cierto que mi parte haya sido notificada o requerida previamente de pago, ni que haya habido gestiones extrajudiciales para que el actor cobrara lo que aquí y ahora reclama.

A los anteriores hechos son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- JURISDICCIÓN Y COMPETENCIA

Conforme con los señalados de contrario.

II.- PROCEDIMIENTO

El juicio verbal a que se refieren los arts. 437 y siguientes LEC.

III.- LEGITIMACIÓN

Conformes con la exposición del demandante sobre legitimación activa y pasiva.

IV.- CUANTÍA

Conformes con la cuantía señalada de contrario.

V.- POSTULACIÓN Y DEFENSA

Esta parte contesta y comparece en autos por medio de Abogado y Procurador, arts. 23 y 31 LEC.

VI.- MATERIALES O SOBRE EL FONDO DEL ASUNTO

Estimamos inaplicables los fundamentos jurídicos citados por la demandante.

Citamos el art. 1254 CCiv en cuanto refiere que el contrato existe desde que una o varias personas consienten en obligarse respecto de otra u otras, a dar alguna cosa o prestar algún servicio. En el presente caso los contactos previos entre demandante y demandado no pueden generar obligación alguna en tanto el contrato no se perfeccione, no estándose ante la figura del llamado precontrato sino ante un mero trato preliminar, sin concretarse ni consolidarse ninguno de los elementos esenciales del contrato cual es la fijación del precio, a cuya determinación se pospone la prestación del consentimiento [SSTS de 25 de junio de 1993 y 19 de julio de 1994 ].

VII.- COSTAS

Conforme al art. 394 LEC, las costas han de imponerse a la parte demandante.

Por lo expuesto,

SUPLICO AL TRIBUNAL:

Que tenga por presentado este escrito con sus documentos y copias de todo ello, teniéndome por comparecido y parte en la representación que ostento, mandando se entiendan conmigo las sucesivas actuaciones; tenerme por contestado y opuesto a la demanda, y siguiendo el pleito su curso, dictar sentencia desestimando la demanda y absolviendo de sus pedimentos al demandado, con expresa imposición de costas a la parte actora.

Es Justicia que solicito en [LUGAR], a [FECHA].

OTROSÍ PRIMERO DIGO: Que interesa a esta parte la celebración de vista, al existir controversia sobre los hechos y ser necesaria la práctica de prueba para la resolución de este proceso.

SUPLICO AL TRIBUNAL: Que, teniendo por causada la manifestación antecedente a los efectos del art. 438.10 LEC, se sirva señalar la celebración de vista.

OTROSÍ SEGUNDO DIGO: Que por el presente escrito, en la representación que acredito y, de forma conjunta a la contestación a la demanda principal, siguiendo instrucciones de mi mandante formulo OPOSICIÓN DE CREDITO COMPENSABLE por importe de [IMPORTE] euros de principal, contra D./Dña. [NOMBRE Y APELLIDOS], todo ello de conformidad con lo previsto en el art. 438.3 LEC y con base en los siguientes hechos y fundamentos de derecho:

HECHOS

PRIMERO

Mi mandante se dedica a la reparación de vehículos de motor, ejerciendo su profesión en esta localidad, calle [CALLE], donde radican sus talleres mecánicos y de chapa, y satisfaciendo por ello la correspondiente contribución y estando en posesión de la preceptiva licencia fiscal que ampara su actividad.

SEGUNDO

El
La
 demandante D./Dña. [NOMBRE Y APELLIDOS] se personó en el taller de reparaciones de mi representado, trayendo el vehículo de su propiedad marca [MARCA/MODELO] y matrícula [MATRÍCULA], encargándole a mi mandante su reparación en la parte mecánica, por los problemas de funcionamiento que había observado, así como en los de chapa y pintura a causa de varios golpes y arañazos que presentaba la carrocería en su parte delantera, aceptando mi mandante el encargo bajo la fórmula de presupuesto previo.

TERCERO

En cumplimiento del encargo, por mi mandante se examinó el vehículo y se comprobaron las partes de su mecánica en mal estado, así como el estado de la carrocería en su parte dañada, elaborando el correspondiente presupuesto de reparación, que alcanzaba la cantidad de [IMPORTE] euros, que le fue comunicado al demandado, que mostró su conformidad y dio orden de reparación.

CUARTO

Verificada la reparación del vehículo, se puso a disposición [ELEGIR: del / de la] demandante, junto con la factura correspondiente, que estaba en consonancia con el presupuesto previo aceptado, personándose D./Dña. [NOMBRE Y APELLIDOS] en el taller y retirando de su propia mano el susodicho vehículo, ofreciendo pagar el importe de la reparación en el día siguiente o en los más próximos, lo que aceptó mi mandante guiado por su buena fe, pero que no encontró la justa correspondencia en el comportamiento posterior del demandado, que ha hecho caso omiso a los diversos requerimientos de pago que se le han hecho, dando largas al asunto y sin dar ninguna satisfacción a mi cliente.

Todo ello se acredita con los documentos números [COMPLETAR].

QUINTO

Con carácter previo a la alegación de la presente oposición en alegación de crédito compensable, mi representado/a se ha dirigido por escrito en dos ocasiones al actor al objeto de requerirle de pago del importe expresado, mediante envío de sendos burofax cuya copia se acompaña como documentos números [COMPLETAR] y [COMPLETAR], que no han tenido contestación, viéndose en la desagradable sorpresa de que D./Dña. [NOMBRE Y APELLIDOS] no solo no ha pagado los importes adeudados a mi mandante, sino que ha formulado demanda contra el mismo en reclamación de cantidad, respecto de la que mi mandante alega en oposición y, sin perjuicio de la correspondiente contestación a la demanda que en su momento procesal efectúe a la demanda, el presente crédito compensable.

FUNDAMENTOS DE DERECHO

I

Conforme a dispuesto en el art. 438.3 LEC, el demandado podrá oponer en la contestación a la demanda un crédito compensable, en los términos previstos para el juicio ordinario en el art. 408 LEC, lo que significa que el demandante podrá controvertir dicha oposición en la forma prevenida para la contestación a la reconvención.

II

Contestada la demanda y, en su caso, la reconvención o el crédito compensable, o transcurridos los plazos correspondientes, el Letrado de la Administración de Justicia, cuando haya de celebrarse vista de acuerdo con lo expresado en el art. 438 LEC, citará a las partes a tal fin dentro de los cinco días siguientes. La vista habrá de tener lugar dentro del plazo máximo de un mes (art. 440 II LEC).

En virtud de todo lo expuesto.

SUPLICO AL TRIBUNAL:

Que teniendo por efectuada la presente OPOSICIÓN DE CREDITO COMPENSABLE contra D./Dña. [NOMBRE Y APELLIDOS], se convoque a las partes a la vista para la resolución del litigio y la alegación de oposición formulada, sin perjuicio del derecho de la parte actora a poder controvertir la presente alegación en la forma prevenida para la contestación a la reconvención, en el plazo de diez días, aunque mi mandante solo pretende la absolución de la petición en su contra y no la condena a su favor del importe que pueda resultar como diferencia entre lo peticionado por el actor y el crédito opuesto por mi mandante y, previo los trámites legales, para el caso de que el Tribunal no desestime la demanda formulada de contrario en la sentencia definitiva que al efecto dicte, subsidiariamente, dicte el mismo sentencia por la que apreciando el crédito compensable alegado por mi mandante por el importe de [IMPORTE] euros, declare compensado el crédito del actor por importe de [IMPORTE] euros.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

NOTAS DEL FORMULARIO

(1) Conforme a lo dispuesto en el art. 438.3 LEC, el demandado puede oponer frente a la pretensión de condena dineraria del actor la existencia de un crédito a su favor de cuantía igual o inferior a la del demandante, lo que supone oponer un hecho excluyente, vía excepción sin necesidad de reconvención, pues no se pretende una sentencia que declare su derecho.

El demandado igualmente puede oponer la compensación como excepción, si el importe del crédito fuera superior, pero dentro de los límites del juicio verbal, para obtener la extinción del crédito del actor en la cantidad concurrente. En este caso, se entiende que renuncia al exceso de su crédito, que no podrá reservarse para reclamarlo en el proceso que corresponda, pues se dividiría la contienda de la causa, ya que la posterior exigencia del exceso por vía judicial, estaría condicionada por la anterior resolución, vinculante en el segundo litigio por el efecto positivo de la cosa juzgada, que tiene un carácter prejudicial.

El art. 438.3 LEC prevé también que "si la cuantía de dicho crédito fuese superior a la que determine que se siga el juicio verbal, el tribunal tendrá por no hecha tal alegación en la vista, advirtiéndolo así al demandado, para que use de su derecho ante el tribunal y por los trámites que correspondan". En este último caso, parece que no habría inconveniente en admitir que el demandado renunciara expresamente a la parte del crédito que exceda del límite del juicio verbal y a la que exceda del crédito del actor por interesarle únicamente que se extinga el de éste último.

Si el demandado alega un crédito compensable, la ley le da el mismo tratamiento que a la reconvención, aunque el demandado sólo pretendiese su absolución y no la condena al saldo que a su favor pudiera resultar. Eso significa que el demandante podrá controvertir dicha oposición en la forma prevenida para la contestación a la reconvención. En consecuencia, tanto si el demandado pretende la mera absolución por compensación de créditos como que además se condene al actor a pagarle la diferencia, lo hará en la propia contestación a la demanda. Ahora bien, hay que entender que si simplemente pretende la extinción del crédito sin solicitud de condena no será necesario que se plantee en forma de demanda, pues no se trata de una demanda reconvencional, sino de una simple oposición de compensación de créditos, por lo que podrá alegarlo por otrosí en la contestación.

Por el contrario, hay quien opina que, como sucede con la reconvención, en todo caso deberá revestir forma de demanda que se adicione a la contestación. La compensación deberá pues plantearse por escrito en los mismos términos que la reconvención, acompañando los documentos de los que se desprenda la existencia de su crédito, y las copias del escrito y documentos para darle traslado al actor.

========================================================================
