---
name: acta-junta-constituyente-1387
description: "Redacta el escrito «Acta de la junta constituyente» (formulario 1387 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acta de la junta constituyente

> Formulario 1387 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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

- [ ] HORA (2 veces)
- [ ] Nº (2 veces)
- [ ] NOMBRE Y APELLIDOS (39 veces)
- [ ] NÚMERO DE LA CALLE
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… Junta como Presidente y Secretario. 2.º»; «…, propietario de»; «…nstituir la Comunidad de Propietarios de»; «…manifestó su desacuerdo con»; «…e los presentes el texto de la propuesta»; «…, piso»; «…ia se aprueba el presupuesto para el año»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Candidaturas / Concurrencia de candidaturas voluntarias / Ausencia de candidaturas y sistema de elección — el texto de cada opción no venía en el formulario original

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

### Formulario 1387 · Acta de la junta constituyente

- Año del modelo: 2013
- Revisión 17-11-2026: 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 46 campos de relleno marcados en blanco; 5 huecos del original que se habían perdido sin marca, marcados (HORA, NOMBRE Y APELLIDOS, NÚMERO DE LA CALLE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En la ciudad de a las [HORA] horas del día de de se reunieron los propietarios que a continuación se indicarán, en en en Junta Constituyente de la Comunidad de Propietarios situada en la C/ n.º [Nº], previa convocatoria por D./Dña. [NOMBRE Y APELLIDOS] en su calidad de.

El orden del día ya indicado en la convocatoria fue el siguiente:

1.º Presentación de los propietarios y determinación de personas que actuarán en esta Junta como Presidente y Secretario.

2.º [COMPLETAR] Exposición por la del funcionamiento de servicios comunes y del mantenimiento necesario.

3.º Propuesta y votación del acuerdo de constituir la Comunidad de Propietarios de y delegación en quien se designe para la realización de los trámites necesarios para su legalización.

4.º Exposición de proyecto de Estatutos para la Comunidad y, en su caso, votación para su aprobación o modificación. Este proyecto se une como anexo n.º 1 a esta convocatoria.

5.º Exposición de presupuesto para el año, dotación de fondo de reserva y fijación de cuantía mensual de contribución de cada propietario según cuota de participación a los gastos comunes. El presupuesto, proyecto de fondo de reserva y propuesta de cuotas se unen a esta convocatoria como anexo n.º 2.

6.º Elección de Presidente y Secretario de la Comunidad para el período y estudio, y aprobación en su caso, de la necesidad de contratar un Administrador.

7.º Ruegos y preguntas.

A esta reunión asistieron los siguientes propietarios:

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS], de los pisos y, con coeficientes de participación de y%, respectivamente, son válidamente representados en la Junta por D./Dña. [NOMBRE Y APELLIDOS], en virtud de apoderamiento que se une a esta acta.

A pesar de haber sido citados, y constar la recepción de la carta, no asisten a la reunión:

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

A estas personas se les remitirá copia de esta acta que incluye los acuerdos adoptados a efectos de alcanzar la mayoría necesaria para su aprobación o para que puedan impugnarlos si no estuvieran de acuerdo con su contenido o forma.

Preside la Junta D./Dña. [NOMBRE Y APELLIDOS] y actúa como Secretario D./Dña. [NOMBRE Y APELLIDOS]

ACTUACIONES Y ACUERDOS ADOPTADOS

Los propietarios asistentes procedieron a presentarse haciendo constar su nombre, piso o local del que son propietarios e indicando los miembros de la unidad familiar que iban a ocupar la vivienda o la finalidad del local del que son titulares. Para presidir la reunión se eligió al copropietario de mayor edad y para que actuara como Secretario al más joven.

La empresa pasó a exponer el funcionamiento de servicios comunes y las necesidades de su mantenimiento. Propuso igualmente las actuaciones que han de contratarse y entregó datos de empresas que se dedican a esas actividades.

D./Dña. [NOMBRE Y APELLIDOS], propietario de [COMPLETAR], manifestó que.

Con el voto unánime de los presentes se acordó constituir la Comunidad de Propietarios de [COMPLETAR], delegando en D./Dña. [NOMBRE Y APELLIDOS] para que realizara los trámites necesarios para su legalización.

Se debatió el proyecto de Estatutos de la Comunidad.

D./Dña. [NOMBRE Y APELLIDOS] manifestó su desacuerdo con [COMPLETAR], y D./Dña. [NOMBRE Y APELLIDOS] propuso modificar la redacción de proponiendo en su lugar que. Se procedió después a votar la aprobación de los Estatutos y la modificación propuesta. Se aprobó por unanimidad de los presentes el texto de la propuesta [COMPLETAR] salvo el n.º [Nº], que se modificaba en el sentido de. Se une a esta acta copia del texto definitivo de los Estatutos de la Comunidad de Propietarios de la C/ n.º [NÚMERO DE LA CALLE] que pasarán a regir, como norma de obligado cumplimiento, el uso de los elementos comunes y las relaciones de los vecinos.

Tras la explicación del presupuesto de gastos para el año y la necesidad de constitución de un fondo de reserva se discutió éste interesando D./Dña. [NOMBRE Y APELLIDOS] que se suprimiera la partida de por innecesaria y que se incluyera la de. Por otro lado D./Dña. [NOMBRE Y APELLIDOS] propuso que con el fondo de reserva se contratara un seguro que cubra los daños causados en la finca. El voto para la aprobación de los presupuestos y la propuesta de modificaciones arrojó el siguiente resultado:

Votos a favor: propietarios que representan un% del total y que suman una cuota de participación con relación a la total de%.

Propietarios que votaron a favor y cuota de participación que representan:

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], local, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], local, con coeficiente de participación del%.

Propietarios que votaron en contra y cuota de participación que representan:

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del%.

En consecuencia se aprueba el presupuesto para el año [COMPLETAR].

Después se pasó a fijar la cantidad mensual de contribución de cada propietario según cuota de participación a los gastos comunes.

Las cantidades resultantes para el año que se aprobaron por unanimidad de los presentes fueron:

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%: euros

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%: euros.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%: euros.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%: euros.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%: euros.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%: euros.

D./Dña. [NOMBRE Y APELLIDOS], local, con coeficiente de participación del%: euros.

D./Dña. [NOMBRE Y APELLIDOS], local, con coeficiente de participación del%: euros.

Igualmente se acordó por unanimidad abrir una cuenta en la entidad bancaria para domiciliar los pagos de las cuotas.

Se une como anexo de esta acta el texto del presupuesto aprobado para el año.

Para la elección de los cargos de Presidente y Secretario de la Comunidad de Propietarios para el período:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Candidaturas / Concurrencia de candidaturas voluntarias / Ausencia de candidaturas y sistema de elección — el texto de cada opción no venía en el formulario original]

En consecuencia para el año actuará como Presidente D./Dña. [NOMBRE Y APELLIDOS] y como Secretario D./Dña. [NOMBRE Y APELLIDOS]

Respecto a la contratación de Administrador se acordó solicitar presupuestos y adoptar la decisión en la siguiente Junta.

Ruegos y preguntas.

Por D./Dña. [NOMBRE Y APELLIDOS] se propuso que. Los vecinos decidieron tomar en consideración esta propuesta y.

No habiendo más asuntos que tratar se dio por terminada la reunión a las [HORA] horas, firmando esta acta el Presidente y Secretario designados para este acto.

Firmado:

========================================================================
