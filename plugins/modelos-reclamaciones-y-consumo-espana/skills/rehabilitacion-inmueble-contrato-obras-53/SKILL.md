---
name: rehabilitacion-inmueble-contrato-obras-53
description: "Redacta el escrito «Rehabilitación de inmueble: contrato de obras» (formulario 53 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Rehabilitación de inmueble: contrato de obras

> Formulario 0053 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] PROVINCIA (3 veces)
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] NÚMERO (2 veces)
- [ ] CORREO ELECTRÓNICO
- [ ] NIF
- [ ] FECHA (2 veces)
- [ ] DESCRIBIR
- [ ] IMPORTE (4 veces)
- [ ] Nº
- [ ] Otros 19 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…En la ciudad/localidad de»; «…, provincia de [PROVINCIA], a»; «…, a [COMPLETAR] de»; «…, a [COMPLETAR] de [COMPLETAR] del año»; «…, mayor de edad, vecino/a de»; «… con domicilio en la localidad/ciudad de»; «…, mayor de edad, vecino/a de»; «… con domicilio en la localidad/ciudad de»; «…provisto/a del N.I.F»; «…, teléfono móvil-»; «…mbre y representación de la mercantil de»; «…, CIF [NIF], domiciliada en»; …

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

### Formulario 0053 · Rehabilitación de inmueble: contrato de obras

- Año del modelo: 2023
- Revisión 17-11-2026: 38 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En la ciudad/localidad de [COMPLETAR], provincia de [PROVINCIA], a [COMPLETAR] de [COMPLETAR] del año [COMPLETAR]

REUNIDOS

De una parte D./Dª [NOMBRE Y APELLIDOS], mayor de edad, vecino/a de [COMPLETAR], con domicilio en la localidad/ciudad de [COMPLETAR], provincia de [PROVINCIA], provisto/a del N.I.F. número [NÚMERO], teléfono móvil-, correo electrónico [CORREO ELECTRÓNICO].

Y de otra parte D./Dª [NOMBRE Y APELLIDOS], mayor de edad, vecino/a de [COMPLETAR], con domicilio en la localidad/ciudad de [COMPLETAR], provincia de [PROVINCIA] provisto/a del N.I.F [COMPLETAR], teléfono móvil- [COMPLETAR], correo electrónico

INTERVIENEN

D./Dª [NOMBRE Y APELLIDOS], interviene en nombre y representación de la mercantil de [COMPLETAR], CIF [NIF], domiciliada en [COMPLETAR] y constituida en [COMPLETAR] ante el Notario de [COMPLETAR] D. [NOMBRE Y APELLIDOS], en fecha [FECHA] e inscrita en el Registro Mercantil de [COMPLETAR] inscripción [COMPLETAR] (en adelante LA CONSTRUCTORA)

D./Dª [NOMBRE Y APELLIDOS], interviene en nombre propio (en adelante, LA PROPIETARIA).

MANIFIESTAN

Que intervienen en la indicada representación, se reconocen mutua y plena capacidad legal de obrar y de obligarse para este acto, otorgando de forma libre y espontánea y a su tenor el presente CONTRATO DE OBRAS DE REHABILITACIÓN, asumiendo la responsabilidad que corresponda en función de la veracidad de sus manifestaciones, y, de mutuo acuerdo,

EXPONEN

I. Que la CONSTRUCTORA es una empresa que se dedica a la construcción y rehabilitación de inmuebles con amplia experiencia en el sector.

II. Que la PROPIETARIA es titular en pleno dominio del inmueble con la siguiente descripción: (se harían constar los datos del inmueble…)

III. Que sobre el inmueble descrito, la PROPIETARIA pretende realizar obras de rehabilitación consistentes en [DESCRIBIR], según resultan ampliamente descritas en el proyecto del Arquitecto D [COMPLETAR] que se incorpora como Anexo I de este contrato.

IV. Que la PROPIETARIA está interesada en que las obras de rehabilitación descritas en el proyecto incorporado como Anexo I sean realizadas por el CONSTRUCTORA, quien asimismo está interesada en ejecutar el encargo.

V. Que, conviniendo ambas partes en concertar el contrato, otorgan a tal fin el presente CONTRATO DE OBRAS DE REHABILITACIÓN, en base a las siguientes

CLÁUSULAS

PRIMERA.- OBJETO DEL CONTRATO

El objeto del presente contrato es la ejecución de obras de rehabilitación sobre el inmueble de la PROPIETARIA descrito en el expositivo II, según el proyecto incorporado como Anexo I, que la CONSTRUCTORA se obliga a realizar en la forma, condiciones y plazos pactados en este contrato.

La CONSTRUCTORA realizará las obras encargadas se realizarán siguiendo las

especificaciones contenidas en el citado proyecto, sin que pueda realizar ningún tipo de modificación sin permiso por escrito de la PROPIETARIA.

La CONSTRUCTORA se encargará de obtener los permisos y licencias oportunos, y suministrará la mano de obra y los materiales, según las calidades que se especifican en el presupuesto que se incorpora como documento Anexo II, como parte integrante de este contrato.

Las modificaciones solicitadas por la PROPIETARIA, o aquellas que fueran necesarias para llevar las obras a buen fin, especialmente cuando supusiesen un aumento del precio de la obra o un aumento del plazo de ejecución, se recogerán en todo caso por escrito y requerirán el acuerdo de ambas partes.

SEGUNDA,. PRECIO Y FORMA DE PAGO

El precio total de las obras es de [IMPORTE] euros, más el % de IVA

El precio pactado se abonará por la PROPIETARIA de la siguiente forma:

1) la cantidad de [IMPORTE] euros a la firma del presente contrato, sirviendo este documento de carta de pago y recibo de la citada cantidad.

2) la cantidad de [IMPORTE] euros, a la finalización de la primera fase de las obras descritas en el proyecto, en fecha [FECHA].

3) la cantidad de [IMPORTE] euros, a la finalización de las obras.

Los pagos se realizarán por transferencia bancaria de la PROPIETARIA a la CONSTRUCTORA en la cuenta corriente número [NÚMERO]

TERCERA.- PLAZO DE EJECUCIÓN DE LAS OBRAS

El plazo de ejecución de las obras será de [Nº] meses a partir de la fecha de firma del presente contrato.

Al término del plazo fijado deberán quedar finalizados todos los trabajos, incluida la retirada de medios auxiliares y limpieza de la obra, así como la retirada de maquinaria y demás elementos.

El plazo de ejecución podrá ser ampliado si existe cambios o modificaciones solicitadas por la PROPIETARIA respecto al proyecto inicial, así como en los casos de fuerza mayor.

En caso de ampliarse el plazo, deberá acordarse de mutuo acuerdo por ambas partes y reflejarse por escrito.

CUARTA.- OBLIGACIONES DE LA CONSTRUCTORA

La CONSTRUCTORA se obliga a ejecutar la obra con la mayor diligencia en el plazo previsto, con sujeción al proyecto incorporado como Anexo I y suministrando los materiales con las calidades recogidas en el presupuesto incorporado como Anexo II, y en especial asume las siguientes obligaciones:

-La CONSTRUCTORA suministrará la mano de obra necesaria, para la realización de la obra encargada, siendo de su cuenta el pago de los salarios, obligándose a cumplir todas las obligaciones de carácter laboral que impone la Ley, y especialmente las de prevención de riesgos laborales. Asimismo, asumirá el pago de todos los gastos de contratación y cuantos impuestos se devenguen como consecuencia de la ejecución de la obra.

-La CONSTRUCTORA responderá de los daños o perjuicios que pudieran irrogarse por motivo de su actividad, así como los derivados de la defectuosa ejecución de las obras.

- La CONSTRUCTORA se obliga a tener los seguros obligatorios que resulten de aplicación, en atención al objeto del contrato, que serán a su costa.

QUINTA.- OBLIGACIONES DE LA PROPIETARIA

La PROPIETARIA se obliga al cumplimiento del contrato con arreglo a las disposiciones legales que lo regulan, actuando con diligencia, lealtad y de buena fe con la CONSTRUCTORA y en especial asume las siguientes obligaciones:

- La PROPIETARIA abonará puntualmente el precio pactado.

- La PROPIETARIA procurará a la CONSTRUCTORA todas las informaciones necesarias para la ejecución del contrato, colaborando activamente en la obtención de permisos, licencias y demás gestiones que sean necesarias por motivo de las obras de rehabilitación.

SEXTA.- CAUSAS DE RESOLUCIÓN Y CLÁUSULA PENAL

Serán causas de resolución de la compraventa el incumplimiento grave y culpable de cualquiera de las partes de las obligaciones de este contrato.

En el caso de incumplimiento por la PROPIETARIA por falta de pago del precio en los plazos pactados, la CONSTRUCTORA podrá optar por resolver el contrato, previo requerimiento de pago de dichas cantidades, o por el cumplimiento.

En este caso, si la CONSTRUCTORA decidiera resolver el contrato tendrá derecho a retener como propias las cantidades entregadas hasta la fecha con el límite del veinte por ciento (20%) del precio del contrato, en concepto de cláusula penal, que sustituye a la indemnización de daños y perjuicios.

Si la CONSTRUCTORA optara por exigir el estricto cumplimiento del contrato, tendrá derecho a una indemnización consistente en la cantidad que resulte de aplicar al importe adeudado el interés de demora del 8% sobre las cantidades impagadas en concepto de cláusula penal que sustituye a indemnización de daños y perjuicios.

En el caso de incumplimiento por la CONSTRUCTORA del plazo de entrega previsto en la estipulación tercera, la PROPIETARIA podrá optar por la resolución del contrato o por el cumplimiento.

Si la PROPIETARIA opta por la resolución del contrato, la CONSTRUCTORA, además de devolver las cantidades entregadas por la PROPIETARIA, le indemnizará con una cantidad equivalente al diez por ciento del precio del contrato, en concepto de cláusula penal que sustituye a la indemnización de daños y perjuicios.

Si la PROPIETARIA opta el cumplimiento, CONSTRUCTORA le indemnizará con la suma de … euros diarios desde la fecha pactada hasta el día de la entrega efectiva de las obras, en concepto de cláusula penal que sustituye a indemnización de daños y perjuicios.

SÉPTIMA.- NOTIFICACIONES

Toda notificación que se efectúe entre las partes se hará por escrito y será entregada personalmente o de cualquier otra forma que certifique la recepción por la parte notificada en los respectivos domicilios o direcciones de correo electrónico indicados en el encabezamiento de este contrato.

Cualquier cambio de domicilio de una de las partes deberá ser notificado a la otra de forma inmediata y por un medio que garantice la recepción del mensaje.

OCTAVA.- SUMISIÓN A MEDIACIÓN Y/O ARBITRAJE

Las partes contratantes acuerdan libre y voluntariamente que todas las desavenencias, divergencias o cuestiones litigiosas que deriven de este contrato, incluso cuando la controversia verse sobre la validez o existencia del presente contrato, se resolverán a través de la Mediación (en su caso se citará la institución) de [COMPLETAR], antes de acudir a la jurisdicción o a otra solución extrajudicial de conflictos, sometiéndose a la regulación establecida en la Ley 5/2012, de 6 de julio, y (caso de fijar un plazo máximo....) fijando un plazo máximo de duración del procedimiento de sesenta días desde la solicitud de iniciación por cualquiera de las partes.

(en su caso, pacto de arbitraje...) A falta de resolución de la controversia en el procedimiento de mediación, la misma será definitivamente resuelta mediante Arbitraje de [COMPLETAR], a la que se encomienda la administración del arbitraje y la designación de los árbitros, de acuerdo con su reglamento.

Y en prueba de conformidad de cuanto antecede, las partes firman y rubrican el presente contrato y sus Anexos I y II, a un solo efecto y por duplicado ejemplar, en todas sus hojas, en el lugar y fecha del encabezamiento.

Fdo.: Fdo.:
