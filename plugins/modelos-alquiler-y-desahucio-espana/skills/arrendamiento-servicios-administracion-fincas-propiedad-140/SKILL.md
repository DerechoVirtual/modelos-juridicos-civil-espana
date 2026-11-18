---
name: arrendamiento-servicios-administracion-fincas-propiedad-140
description: "Redacta el escrito «Arrendamiento de servicios de administración de fincas en propiedad vertical» (formulario 140 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Arrendamiento de servicios de administración de fincas en propiedad vertical

> Formulario 0140 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

- [ ] PROVINCIA (3 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NÚMERO
- [ ] CORREO ELECTRÓNICO (2 veces)
- [ ] IMPORTE
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…En la ciudad/localidad de»; «…, provincia de [PROVINCIA], a»; «…, mayor de edad, vecino/a de»; «… con domicilio en la localidad/ciudad de»; «…, teléfono móvil»; «…, mayor de edad, vecino/a de»; «… con domicilio en la localidad/ciudad de»; «…provisto/a del N.I.F»; «…, teléfono móvil»; «…(en su caso se citará la institución) de»; «…tivamente resuelta mediante Arbitraje de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Ley 5/2012

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

### Formulario 0140 · Arrendamiento de servicios de administración de fincas en propiedad vertical

- Año del modelo: 2021
- Revisión 17-11-2026: 20 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En la ciudad/localidad de [COMPLETAR], provincia de [PROVINCIA], a [COMPLETAR]

REUNIDOS

De una parte D./Dª [NOMBRE Y APELLIDOS], mayor de edad, vecino/a de [COMPLETAR], con domicilio en la localidad/ciudad de [COMPLETAR], provincia de [PROVINCIA], provisto/a del N.I.F. número [NÚMERO], dirección de correo electrónico [CORREO ELECTRÓNICO], teléfono móvil [COMPLETAR].

Y de otra parte D./Dª [NOMBRE Y APELLIDOS], mayor de edad, vecino/a de [COMPLETAR], con domicilio en la localidad/ciudad de [COMPLETAR], provincia de [PROVINCIA] provisto/a del N.I.F [COMPLETAR], dirección de correo electrónico [CORREO ELECTRÓNICO], teléfono móvil [COMPLETAR].

MANIFIESTAN

Que intervienen en la indicada representación, se reconocen mutua y plena capacidad legal de obrar y de obligarse para este acto, otorgando de forma libre y espontánea y a su tenor el presente CONTRATO DE ARRENDAMIENTO DE SERVICIOS DE ADMINISTRACIÓN DE FINCAS EN RÉGIMEN DE PROPIEDAD VERTICAL, asumiendo la responsabilidad que corresponda en función de la veracidad de sus manifestaciones, y, de mutuo acuerdo,

EXPONEN

I. I. Que la PROPIETARIA es titular en pleno dominio del inmueble con la siguiente descripción:

II. Que la PROPIETARIA está interesada en concertar el servicio de administración de fincas en vertical sobre el citado inmueble.

III. Que la ADMINISTRADORA se dedica a la actividad de administración de fincas, prestando sus servicios de administración en régimen de propiedad vertical, estando interesada en la gestión del referido inmueble

IV. Que conviniendo ambas partes en concertar el contrato, otorgan a tal fin el presente CONTRATO DE ARRENDAMIENTO DE SERVICIOS, en base a las siguientes

CLÁUSULAS

PRIMERA.- OBJETO DEL CONTRATO

El objeto del presente contrato es la prestación de servicios de administración de la finca descrita en el expositivo I, en régimen de propiedad vertical, el cual será prestado por la ADMINISTRADORA sobre el inmueble titularidad de la PROPIETARIA.

La ADMINISTRADORA asume la obligación de prestar los servicios necesarios para la administración de la propiedad en vertical, en nombre y por cuenta de la PROPIETARIO, incluyendo la gestión de alquiler y captación de inquilinos, a cambio de la retribución que se obliga a satisfacer la PROPIETARIA en los términos y condiciones que se detallan en las siguientes cláusulas.

SEGUNDO.- CONTENIDO DE LA ADMINISTRACIÓN EN RÉGIMEN DE PROPIEDAD EN VERTICAL

Ambas partes se obligan a cumplir sus respectivas obligaciones para que pueda llevarse a cabo la administración de la finca descrita en régimen de propiedad vertical, con el objetivo de optimizar el rendimiento y garantizar su sostenibilidad a largo plazo según las directrices de la PROPIETARIA, estableciéndose expresamente los siguientes pactos:

. La ADMINISTRADORA asumirá la gestión integral de los arrendamientos que se realicen en el inmueble, con sujeción a lo dispuesto en la legislación vigente, incluyendo la gestión comercial (captación, preselección y selección de inquilinos), redacción de contratos con negociación de las condiciones contractuales, gestión de firmas, depósito de fianzas, gestión de cobro de los alquileres, reclamación de impagados, certificado energético, comunicación con inquilinos, y gestión de reclamaciones judiciales y de seguros de alquiler.

- La ADMINISTRADORA gestionará el mantenimiento y conservación del edificio, incluyendo todos sus elementos e instalaciones, así como los servicios de conserjería, limpieza, retirada de basura, jardinería y otros similares, seleccionando los proveedores, técnicos y empleados por cuenta de la PROPIETARIA, según sus instrucciones.

-La ADMINISTRADORA cuidará de la gestión técnica y administrativa del edificio, incluyendo inspecciones técnicas, de baja tensión, gestión de permisos y licencias administrativas, concertación de seguros sobre el inmueble, pago de impuestos y tributos, y demás gastos que deban satisfacerse con cargo al inmueble.

-La ADMINISTRADORA asumirá la gestión financiera del inmueble, mediante la presentación de un plan que debe ser aprobado por la PROPIETARIA, y que se será revisado con periodicidad bianual, en el que se incluirán cálculos de rentabilidad, reducción de costes, estudio de coberturas, inversiones, uso de posibles préstamos de institutos de crédito y otros elementos económicos y financieros que sean convenientes para la explotación del inmueble.

- Se procederá a la apertura de una cuenta bancaria exclusivamente para los ingresos y gastos de las fincas arrendadas y demás ingresos, gastos y costes que deban ser satisfechos con cargo al inmueble. Dicha cuenta será abierta por la PROPIETARIA y a su nombre, estando autorizada la ADMINISTRADORA para operar con plenas facultades en la misma, pudiendo ver la PROPIETARIA en todo momento las cuentas, facilitándole las claves de acceso del banco.

- Los gastos del inmueble serán cubiertos con carácter general con las cuotas por las rentas ingresadas en la citada cuenta, o eventualmente por los ingresos que se realicen por la PROPIETARIA a tal fin.

- La ADMINISTRADORA asumirá el control de facturas de proveedores, gestión de pago a los mismos, confección de recibos, contabilización y cobro mensual, y realizará el pago de los saldos líquidos al propietario con carácter mensual, una vez deducidos sus honorarios.

- Se elaborarán por la ADMINISTRADORA estados de cuentas, gastos e ingresos y liquidaciones con carácter mensual.

- La ADMINISTRADORA comunicará a la PROPIETARIA la propuesta de obras y de reparaciones requeridas, que excedan del normal mantenimiento del inmueble, a fin de que sean autorizadas por ésta.

TERCERA.- PLAZO

El plazo del contrato es de DIEZ AÑOS desde la fecha de su firma.

El contrato se renovará tácitamente, por periodos de dos años, de no mediar preaviso en contrario de una de las partes, con una antelación mínima de seis meses.

CUARTA.- HONORARIOS Y FORMA DE PAGO

La ADMINISTRADORA percibirá, en concepto de honorarios, una cantidad fija de [IMPORTE] euros mensuales, más una cantidad variable del 5% del rendimiento neto del inmueble, una vez detraídos todos los gastos, entre los cuales se incluyen los honorarios pactados en esta cláusula.

Los pagos se realizarán contra la liquidación que debe realizar la ADMINISTRADORA con carácter mensual a la PROPIETARIA, detrayendo la cantidad fija y variable correspondiente a los honorarios.

QUINT A.- OBLIGACIONES DE LA PROPIETARIA

La PROPIETARIA se obliga al cumplimiento del contrato con arreglo a las disposiciones legales que lo regulan, actuando con diligencia, lealtad y de buena fe con la ADMINISTRADORA y en especial asume las siguientes obligaciones:

- Formalizar en el plazo más breve posible la contratación de los arrendatarios, profesionales, agentes y proveedores seleccionados por la ADMINISTRADORA en ejecución del contrato, o a apoderar a la ADMINISTRADORA para que formalice los contratos en su nombre, y al diligente cumplimiento de los contratos concertados.

- Procurar a la ADMINISTRADORA todas las informaciones y comunicaciones necesarias para la ejecución del contrato.

- Satisfacer puntualmente la remuneración pactada.

SEXTA.- OBLIGACIONES DE LA ADMINISTRADORA

La ADMINISTRADORA se obliga al cumplimiento del contrato con arreglo a las disposiciones legales que lo regulan, actuando con diligencia, lealtad y de buena fe con la PROPIETARIA y en especial asume las siguientes obligaciones:

- Asumir la gestión y explotación económica, administrativa y financiera del edificio, así como las demás obligaciones que se derivan del objeto del contrato.

-Al puntual cumplimiento de sus obligaciones, recabando la autorización previa de la PROPIETARIA en los casos que resulte necesario.

- A rendir cuentas de los gastos satisfechos por cuenta de la PROPIETARIA anticipando, en su caso, las cantidades para atender gastos urgentes e imprevistos si ello fuera necesario.

- A procurar a la PROPIETARIA todas las informaciones necesarias para la ejecución del contrato.

SEXTA.- CONFIDENCIALIDAD

Ambas partes se comprometen a no divulgar la información y documentación confidencial referente a la otra parte de la que hayan tenido conocimiento por razón de la ejecución del presente contrato, salvo las indispensables para su cumplimiento, y a mantenerla en secreto, incluso después de la finalización del mismo.

SÉPTIMA.- CAUSAS DE RESOLUCIÓN Y EXTINCIÓN DEL CONTRATO

El incumplimiento grave y culpable por una de las partes de cualquiera de las obligaciones estipuladas facultará a la parte contraria a resolver de forma inmediata el presente contrato o exigir su cumplimiento, sin perjuicio de la indemnización de daños y perjuicios que proceda en ambos casos.

En cualquier caso, la Parte que pretenda resolver el presente contrato alegando incumplimiento de la contraparte, deberá requerirle al cumplimiento de la obligación de forma fehaciente, otorgándole un plazo de quince días a la Parte incumplidora para que pueda subsanar dicho incumplimiento. Transcurrido dicho plazo sin que los incumplimientos hubiesen sido subsanados, el perjudicado podrá ejercitar la mencionada facultad. En el supuesto de que los incumplimientos fueren de imposible subsanación, el perjudicado podrá ejercitar directamente la facultad opción, sin necesidad de remitir, previamente, el antedicho requerimiento.

OCTAVA.- NOTIFICACIONES

Toda notificación que se efectúe entre las partes se hará preferentemente en las direcciones de correo electrónico que figuran en el encabezamiento, sin perjuicio de que también puedan ser realizadas en los respectivos domicilios indicados en el encabezamiento de este contrato.

Cualquier cambio de dirección de correo electrónico y/o de domicilio de una de las partes deberá ser notificado a la otra de forma inmediata y por un medio que garantice la recepción del mensaje.

NOVENA.- SUMISIÓN A MEDIACIÓN Y/O ARBITRAJE

Las partes contratantes acuerdan libre y voluntariamente que todas las desavenencias, divergencias o cuestiones litigiosas que deriven de este contrato, incluso cuando la controversia verse sobre la validez o existencia del presente contrato, se resolverán a través de la Mediación (en su caso se citará la institución) de [COMPLETAR], antes de acudir a la jurisdicción o a otra solución extrajudicial de conflictos, sometiéndose a la regulación establecida en la Ley 5/2012, de 6 de julio, y (caso de fijar un plazo máximo....) fijando un plazo máximo de duración del procedimiento de sesenta días desde la solicitud de iniciación por cualquiera de las partes.

( en su caso, pacto de arbitraje...) A falta de resolución de la controversia en el procedimiento de mediación, la misma será definitivamente resuelta mediante Arbitraje de [COMPLETAR], a la que se encomienda la administración del arbitraje y la designación de los árbitros, de acuerdo con su reglamento.

Y en prueba de conformidad de cuanto antecede, las partes firman y rubrican el presente contrato, a un solo efecto y por duplicado ejemplar, en todas sus hojas, en el lugar y fecha del encabezamiento.

Fdo.: Fdo.:
