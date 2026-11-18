---
name: acta-aprobacion-ascensor-1214
description: "Redacta el escrito «Acta de aprobación de ascensor» (formulario 1214 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acta de aprobación de ascensor

> Formulario 1214 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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

- [ ] Nº (2 veces)
- [ ] CALLE
- [ ] NÚMERO
- [ ] FECHA
- [ ] NOMBRE Y APELLIDOS (72 veces)
- [ ] IMPORTE (4 veces)
- [ ] Otros 91 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…En»; «…a las [Nº] horas se reúne en»; «…horas se reúne en [COMPLETAR] en»; «…se hicieron constar y que consistían en»; «…, piso»; «…, piso»; «…, piso»; «…, piso»; «…, piso»; «…, piso»; «…, piso»; «…, piso»; …

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

### Formulario 1214 · Acta de aprobación de ascensor

- Año del modelo: 2013
- Revisión 17-11-2026: 171 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [COMPLETAR] a las [Nº] horas se reúne en [COMPLETAR] en [COMPLETAR] convocatoria la Junta General extraordinaria de la Comunidad de Propietarios de la c/ [CALLE] n.º [NÚMERO], previa convocatoria en forma a todos sus integrantes con las cuestiones a tratar que en el orden del día de ésta de fecha [FECHA] se hicieron constar y que consistían en [COMPLETAR].

A la Junta asisten los siguientes propietarios:

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], local [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], local [COMPLETAR], con coeficiente de participación del.

 D./Dña. [NOMBRE Y APELLIDOS] propietario del piso [COMPLETAR] y con coeficiente de participación del % autorizó a D./Dña. [NOMBRE Y APELLIDOS] para que lo representara en la Junta y votara en su nombre, según escrito que presentó con esa autorización y cuya copia se une a esta acta.

 Se hace constar que D./Dña. [NOMBRE Y APELLIDOS] propietario del local [COMPLETAR] y con coeficiente de participación del % no se encuentra al corriente del pago de las cuotas de la Comunidad por adeudar las de los meses de [COMPLETAR] cuyo importe total asciende a [IMPORTE] euros. Al no haber procedido antes de la celebración de la Junta a pagar ni a consignar su importe y no constando que haya impugnado judicialmente esta deuda, su persona y cuota de participación no son tenidas en cuenta para los efectos de calcular la mayoría legalmente exigida para los acuerdos que se adoptaron.

D./Dña. [NOMBRE Y APELLIDOS], que figuraba como moroso en la convocatoria a esta Junta, ha procedido a liguidar las cuotas pendientes y ponerse al día en esta obligación, de modo que podrá participar en las deliberaciones con voz y voto.

Preside la Junta el Presidente D./Dña. [NOMBRE Y APELLIDOS] y actúa como Secretario D./Dña. [NOMBRE Y APELLIDOS]

El Presidente da inicio a la reunión en la que se debatieron los puntos recogidos en el orden del día con el siguiente resultado:

1.º Lectura y aprobación del acta de la Junta anterior, después de aclarar que [COMPLETAR] se aprueba por todos los asistentes.

2.º Instalación de ascensor desde el portal del edificio hasta el último piso.

Por el Presidente se expone la solicitud de numerosos vecinos para que se lleve a cabo esta obra, que supondría una mejora evidente de los servicios de la Comunidad y una revalorización del inmueble.

 D./Dña. [NOMBRE Y APELLIDOS] solicitó la instalación de ascensor para eliminar barreras arquitectónicas y en atención a su [COMPLETAR]. Se presenta en la Junta la documentación que acredita este extremo que [COMPLETAR] es impugnada por los vecinos.

Por parte del vecino del piso [COMPLETAR], D./Dña [NOMBRE Y APELLIDOS], se plantea la posibilidad de [COMPLETAR], replica el Presidente en el sentido de [COMPLETAR].

D./Dña. [NOMBRE Y APELLIDOS], propietario del local [COMPLETAR], se opone por considerar que los dueños de locales deben estar exentos de contribución económica a la instalación de ascensor. Por el Administrador se explica que esta cuestión ha sido resuelta de forma prácticamente unánime por los Tribunales en el sentido de considerar que, si se adopta la decisión con la mayoría legalmente exigida de votos favorables de propietarios, el acuerdo obliga a todos ellos y, en consecuencia, todos deberán participar en los gastos.

D./Dña. [NOMBRE Y APELLIDOS], propietario del piso [COMPLETAR], propone que el reparto del importe de la obra se haga entre los propietarios no en atención a su cuota de participación, sino en atención a la altura del inmueble que ocupen, de manera que los titulares de los pisos superiores abonarían una cantidad mayor que los de los inferiores. Por el Administrador se explica que esa opción, de asumirse, podría considerarse nula, porque la ley exige, en principio, que la contribución a los gastos comunes se realice según la cuota de participación de los propietarios. Esta alteración, en consecuencia, sólo podría adoptarse por unanimidad de todos los implicados. En todo caso, esta cuestión debería ser objeto de estudio no en este punto, sino, precisamente, en el relativo a la distribución de los gastos una vez aprobado el que nos ocupa.

Estudiadas estas cuestiones, se procede a la votación que arroja el siguiente resultado:

Votos a favor: propietarios, % de cuotas de participación:

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], local [COMPLETAR], con coeficiente de participación del.

Votos en contra: propietarios, % de cuotas de participación:

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], local [COMPLETAR], con coeficiente de participación del.

Se aprueba la instalación del ascensor en atención al resultado anterior: votos favorables que representan un [COMPLETAR] % de los propietarios y un [COMPLETAR] % de las cuotas de participación.

D./Dña. [NOMBRE Y APELLIDOS] salva su voto a los efectos de una posible impugnación ante el Tribunal.

3.º Elección del presupuesto para la instalación del ascensor.

Por el Presidente se hace un resumen de las ofertas que han estado a disposición de los propietarios y que han podido ser estudiadas por ellos.

Por parte de D./Dña. [NOMBRE Y APELLIDOS] se plantea que la oferta de [COMPLETAR], que económicamente parece la más ventajosa, en realidad no incluye [COMPLETAR] obra, que debería ser contratada con otra empresa. Por esta razón ese presupuesto debería excluirse de los sometidos a votación.

D./Dña. [NOMBRE Y APELLIDOS] pregunta si el presupuesto de la empresa [COMPLETAR] incluye el IVA. Se contesta por el Administrador en sentido negativo. En consecuencia, a la cifra de [IMPORTE] euros deberán sumar euros para fijar su importe total.

Por último, se piden explicaciones por parte de D./Dña. [NOMBRE Y APELLIDOS] sobre las facilidades de pago que ofrece cada una de las empresas. Contesta el Presidente en el sentido siguiente: [COMPLETAR].

Sometidos a votación los presupuestos, el resultado es el siguiente:

Presupuesto de la empresa [COMPLETAR] por importe de [IMPORTE] euros:

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

Presupuesto de la empresa [COMPLETAR] por importe de [IMPORTE] euros:

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], local [COMPLETAR], con coeficiente de participación del.

Abstenciones:

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS] salva su voto a los efectos de una posible impugnación ante el Tribunal.

A la vista de la votación se elige el presupuesto presentado por la empresa [COMPLETAR] por resultar el votado por un mayor número de propietarios.

4.º Distribución de los gastos derivados de la instalación de ascensor entre todos los propietarios.

En la propuesta que se remitió en la convocatoria, cuya copia se une a esta acta, se proponía, en síntesis, que el pago del importe total de la instalación se distribuyera entre todos los propietarios en atención a su cuota de participación, mediante derramas extraordinarias en número de [COMPLETAR] que se abonarían de la siguiente manera [COMPLETAR]. En cuanto a las ayudas y subvenciones se proponía que [COMPLETAR].

Expuestos estos extremos el Presidente, D./Dña. [NOMBRE Y APELLIDOS] vuelve a proponer nuevamente que el reparto de los gastos se haga en atención a la altura de cada piso en el inmueble, de manera que paguen más los de los pisos más altos, puesto que los gastos que se derivarán de su uso serán mayores que los de los pisos bajos. Propone también que los dueños de los locales estén exentos de contribuir al coste de esta instalación, puesto que no se beneficiarán de ella. Por el Administrador se le recuerda lo expuesto en el punto primero, pero el comunero insiste en que se vote esta propuesta por si se alcanzará la unanimidad necesaria para alterar el criterio general de participación en los gastos.

En consecuencia, se somete esta propuesta a votación de los propietarios.

Votos a favor: propietarios, [COMPLETAR] % de cuotas de participación:

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], local [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], local [COMPLETAR], con coeficiente de participación del.

Votos en contra: propietarios, [COMPLETAR] % de cuotas de participación:

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

Abstenciones:

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

Se desestima esta pretensión al no alcanzar la unanimidad exigida legalmente.

Se pasa a votar, en consecuencia, la propuesta recogida en el orden del día.

Votos a favor: propietarios, [COMPLETAR] % de cuotas de participación:

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], local [COMPLETAR], con coeficiente de participación del.

Votos en contra: propietarios, [COMPLETAR] % de cuotas de participación:

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del.

D./Dña. [NOMBRE Y APELLIDOS], local [COMPLETAR], con coeficiente de participación del.

Se aprueba la creación de [COMPLETAR] derramas extraordinarias para la instalación de ascensor que se distribuyen entre todos los propietarios en atención a su cuota de participación, mediante derramas extraordinarias en número de [COMPLETAR] que se abonarán de la siguiente manera [COMPLETAR]:

 votos favorables que representan un [COMPLETAR] % de los propietarios y un [COMPLETAR] % de las cuotas de participación.

D./Dña. [NOMBRE Y APELLIDOS] salva su voto a los efectos de una posible impugnación ante el Tribunal.

5.º En el apartado ruegos y preguntas se expuso por D./Dña. [NOMBRE Y APELLIDOS] lo siguiente [COMPLETAR].

No habiendo más asuntos a tratar, se dio por terminada la reunión a las [Nº] horas, firmando esta acta Presidente y Secretario.

Firmado:

========================================================================
