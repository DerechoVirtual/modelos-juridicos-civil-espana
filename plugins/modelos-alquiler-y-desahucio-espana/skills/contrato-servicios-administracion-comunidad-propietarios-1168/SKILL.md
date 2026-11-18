---
name: contrato-servicios-administracion-comunidad-propietarios-1168
description: "Redacta el escrito «Contrato de servicios de administración de comunidad de propietarios» (formulario 1168 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contrato de servicios de administración de comunidad de propietarios

> Formulario 1168 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] FECHA (3 veces)
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] DNI/NIE
- [ ] LOCALIDAD (2 veces)
- [ ] NIF
- [ ] NÚMERO (3 veces)
- [ ] IMPORTE (3 veces)
- [ ] Nº (3 veces)
- [ ] PLAZO (2 veces)
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… Colegio de Administradores de Fincas de»; «… Colegio de Administradores de Fincas de»; «…, con el número de colegiado»

## Elecciones que hay que hacer

- tan pronto se ocasionen / cuando este presente /trimestralmente /anualmente
- toda la documentación de la comunidad / solamente las convocatorias, comunicaciones, apoderamientos o documentos relevantes

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 1168 · Contrato de servicios de administración de comunidad de propietarios

- Año del modelo: 2015
- Revisión 17-11-2026: 2 desplegables convertidos en elección en blanco; 27 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [FECHA].

REUNIDOS

DE UNA PARTE,

D./Dña. [NOMBRE Y APELLIDOS], con DNI n.º [DNI/NIE], Presidente/a de la Comunidad de Propietarios del edificio sito en [LOCALIDAD], con CIF n.º [NIF], nombrado en la Junta Ordinaria de fecha [FECHA] según consta en el folio n.º [NÚMERO] del libro de actas de la Comunidad, actuando en representación de la misma,

Y DE OTRA,

D D./Dña. [NOMBRE Y APELLIDOS], Administrador/a de Fincas colegiado/a n.º [NÚMERO] del Ilustre Colegio de Administradores de Fincas de [COMPLETAR], con despacho profesional abierto en

Ambos con capacidad legal suficiente, que mutuamente se reconocen para celebrar el presente contrato de arrendamientos de servicios de administración, y

MANIFIESTAN

I.- Que la Comunidad de Propietarios, en su reunión de fecha [FECHA] según consta en el folio n.º [NÚMERO] del libro de actas de la comunidad, acordó encomendar las funciones de Administrador/a a un profesional colegiado, facultando al Presidente/a para designarlo y suscribir el oportuno contrato, previo señalamiento de la retribución.

II.- Que D./Dña. [NOMBRE Y APELLIDOS] es Administrador de Fincas en ejercicio, inscrito en el Ilustre Colegio de Administradores de Fincas de [COMPLETAR], con el número de colegiado [COMPLETAR], estando dado de Alta en el Impuesto de Actividades Económicas, Seguridad Social en el régimen de autónomos y al corriente en el cumplimiento de sus obligaciones tributarias.

Manifiesta que tiene cualificación profesional suficiente y legalmente reconocida para ejecutar las funciones de administrador y administrador secretario de Comunidades de Propietarios.

III.- Que es deseo de ambas partes formalizar el presente contrato de arrendamiento de servicios profesionales adecuado y sujeto a las previsiones de los artículos 1.542 y siguientes del Código Civil, respecto al contrato de mandato, en lo que fuere de aplicación, sin perjuicio de lo que se estipula en las siguientes cláusulas.

IV.- Que D./Dña. [NOMBRE Y APELLIDOS] acepta el desempeño del cargo de Administrador de la citada comunidad de propietarios, suscribiendo el presente contrato de administración, con sujeción a las siguientes,

CLAÚSULAS

PRIMERA.- La duración del contrato será de un año, prorrogable por períodos de la misma duración, si cualquiera de las partes no manifiesta su voluntad en contrario, comunicándole a la otra con un mes de antelación a la conclusión de cada periodo anual.

Si la Junta de Propietarios acordase la revocación del contrato antes de la terminación del mismo o de sus prórrogas, deberá abonar al administrador los honorarios correspondientes al tiempo que medie hasta el transcurso del año, a no ser que la revocación obedeciese a justa causa, derivada del incumplimiento por aquel de sus obligaciones.

SEGUNDA.- Por el desempeño del cargo de Administrador y las funciones que al mismo le atribuyen las leyes percibirá de la Comunidad la cantidad de [IMPORTE] euros. cada año y por el cargo de Secretario/a, la cantidad de [IMPORTE] euros.

El pago de los honorarios se efectuará cada trimestre /a fin de año /a principio de cada año.

En los honorarios

se incluyen la totalidad de los gastos que el desempeño de las funciones ocasione al Administrador/a y Secretario/a

no se incluyen los gastos de correo, notificaciones, papel, asistencia a la celebración de asambleas, pago del alquiler de la sala que asciende en el momento actual a [IMPORTE] euros por sesión de dos /tres / horas.

Dichos importes se abonarán al Administrador [ELEGIR: tan pronto se ocasionen / cuando este presente /trimestralmente /anualmente].

TERCERA.- Conforme a lo establecido en la vigente Ley de Propiedad Horizontal el Administrador realizará las siguientes funciones, bajo la dependencia del Presidente/a de la comunidad de propietarios.

Como Administrador/a:

— Convocar las Juntas de Propietarios Ordinaria y Extraordinaria encargándose de todos los trámites incluso la redacción y envío de la convocatoria según las instrucciones de quién sea Presidente/a debiendo advertir al Presidente de los cargos que se deban renovar por expiración de plazo u otros motivos.
— Presentar a las Juntas respectivas las cuentas y presupuestos para su aprobación facilitando a los propietarios la consulta de cuantos justificantes de gastos o presupuestos existieran en la comunidad.
— Girar los recibos de provisiones de fondos en el plazo de [Nº] días desde la aprobación por la Junta o en los plazos y fechas que esta establezca.
— Controlar y poner en conocimiento del Presidente/a cuantas incidencias, reclamaciones y pagos hubiere que realizar por las obras que se ejecuten en el edificio ya sean ordinarias o extraordinarias.
— Llevar relación de los domicilios actualizados de los propietarios del inmueble, notificando al Presidente/a los nombres de los propietarios con domicilio desconocido a fin de la localización del mismo, si ello es posible.
— Notificar al Presidente/a la relación de morosos que no pueden ejercer el derecho de voto en las Juntas respectivas.
— Notificar al Presidente/a en el mismo día la impugnación de las Juntas que se lleven a cabo.
— Efectuar la distribución de las derramas tanto ordinarias como extraordinarias entre los propietarios según los acuerdos de las Juntas celebradas.
— Orientar en las Juntas al Presidente/a sobre los acuerdos a tomar y si los mismos se acomodan o no a la legalidad vigente.
— Redactar el acta de las Juntas y transcribirla al libro de actas, enviarla por correo certificado o burofax en un plazo de [PLAZO] / días a todos los propietarios al último domicilio que conste en la Comunidad.
— Comunicar al Presidente/a, si tiene conocimiento de las mismas, las obras que realicen los vecinos en sus pisos respectivos por si pueden afectar a los elementos comunes.
— Librar, con el conforme del Presidente/a, los certificados que precisen los propietarios que vendan el piso respectivo o por cualquier otro motivo, de estar al día o no estar al día en los pagos a la comunidad.
— Inspeccionar periódicamente el edificio para comprobar el funcionamiento de los servicios.
— Encargar la realización de las reparaciones urgentes y comunicarlas al Presidente/a.
— Presentar al Sr./a Presidente/a con una antelación de [Nº] semanas el/los presupuesto/s del próximo ejercicio y de las obras que sea necesario realizar.
— Redactar, si hubiera cambio en cuanto a la distribución de los pisos, los nuevos coeficientes.
— Redactar los requerimientos para que firme el Presidente/a a los vecinos u ocupantes que desarrollen actividades prohibidas, dañosas, molestas, insalubres, nocivas, peligrosas o ilícitas y seguir los requerimientos efectuados.

Como Secretario/a

— Redactar el acta de las Juntas y transcribir al libro de actas, enviarla por correo certificado o burofax en un plazo de ocho días a todos los propietarios al último domicilio que conste en la Comunidad.
— Guardará los libros de actas que deberán estar debidamente legalizados.
— Conservará durante cinco años [ELEGIR: toda la documentación de la comunidad / solamente las convocatorias, comunicaciones, apoderamientos o documentos relevantes].

CUARTA.- El Administrador estará obligado:

a) A desempeñar su cargo fielmente y con la diligencia necesaria.
b) A rendir cuentas a la comunidad en un plazo máximo de [Nº] días a partir de la notificación de su cese.
c) A entregar a la comunidad de propietarios toda documentación y datos de la misma de los que esté en posesión en el mismo plazo.
d) A desempeñar simultáneamente el cargo de Secretario/a de la comunidad de propietarios.

QUINTA.- El Administrador podrá ser cesado a voluntad del Presidente/a por las causas que estime oportunas pero en todo caso se le deberán abonar los honorarios hasta finalizar el año si no hay causa justificada del cese.

El Administrador está obligado a entregar toda la documentación y podrá pedir que se le firme el justificante de la entrega, incluso quedarse fotocopias de la documentación entregada para la reclamación que pudiera proceder pero bajo ningún concepto el Administrador podrá retener la documentación que por razón del cargo obre en su poder.

La Junta de Propietarios queda obligada a liquidar al Administrador/a y éste entregar, los saldos negativos o favorables a la Comunidad, todo ello en un plazo de [PLAZO] desde que le sea notificada la revocación del cargo de Administrador.

En caso de discrepancia en cuanto a los honorarios y gastos podrá la parte que le interesa, acudir a los Tribunales en defensa de sus intereses pero ni el Administrador retendrá documentación ni el Presidente se negará a firmar la recepción de la documentación que se le entregue.

El Administrador/a podrá rescindir el contrato con un preaviso a la comunidad de dos meses.

SEXTA.- El presente contrato pertenece al ámbito del Derecho privado, ha sido formalizado por la Comunidad de Propietarios en consideración al carácter de Administrador/a independiente del Profesional, y en modo alguno podrá interpretarse como constitutivo de vínculo de naturaleza laboral entre ambas partes.

SÉPTIMA.- Para las cuestiones o controversias que puedan derivarse de la interpretación o aplicación del presente contrato, ambas partes conviene en someterse al fuero de los Jueces y Tribunales de [LOCALIDAD], con expresa renuncia de cualquier otro que pudiera corresponderles.

Y en prueba de conformidad con cuanto antecede, firman ambas partes el presente documento, por duplicado ejemplar y a un solo efecto, en el lugar y fecha indicados en el encabezamiento.

Firma del Presidente/a de la Comunidad	Firma del Administrador/a
D./D.ª [NOMBRE Y APELLIDOS]	D./D.ª [NOMBRE Y APELLIDOS]

========================================================================
