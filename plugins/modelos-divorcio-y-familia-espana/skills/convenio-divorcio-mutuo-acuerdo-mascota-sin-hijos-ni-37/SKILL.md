---
name: convenio-divorcio-mutuo-acuerdo-mascota-sin-hijos-ni-37
description: "Redacta el escrito «Convenio de divorcio de mutuo acuerdo con mascota, sin hijos ni bienes (Cataluña)» (formulario 37 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Convenio de divorcio de mutuo acuerdo con mascota, sin hijos ni bienes (Cataluña)

> Formulario 0037 del plugin **Familia** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.

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

- [ ] LUGAR (2 veces)
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] FECHA (2 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] Nº (2 veces)
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] IMPORTE
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, a [DÍA] de [MES] de [AÑO].l»; «…en»; «…arecientes viven de forma separada desde»; «… se mantenga en su domicilio habitual en»; «…, atribuyéndose así a»; «…al animal. Excepto que pacten otra cosa,»; «… un fin de semana al mes, a convenir con»; «…, siempre y cuando ésta se encuentre en»; «…1 al 5 de cada mes en la cuenta bancaria»

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

### Formulario 0037 · Convenio de divorcio de mutuo acuerdo con mascota, sin hijos ni bienes (Cataluña)

- Año del modelo: 2024
- Revisión 17-11-2026: 20 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma de la LO 1/2025.

En [LUGAR], a [DÍA] de [MES] de [AÑO].l [COMPLETAR]

MANIFIESTAN

PRIMERO. Que ambos esposos contrajeron matrimonio el día [FECHA] en [COMPLETAR], habiéndose inscrito dicho matrimonio en el Registro Civil de [LOCALIDAD]

SEGUNDO. Que de dicho matrimonio no ha habido descendencia.

TERCERO -Que el matrimonio se encuentra acogido al régimen económico matrimonial de separación de bienes ya que, por residencia y lugar de celebración del matrimonio, la vecindad de los cónyuges es la catalana, no habiéndose otorgado nunca capitulaciones matrimoniales.

CUARTO - El último domicilio familiar fue el sito en [LOCALIDAD]

QUINTO. -

Que los comparecientes viven de forma separada desde [COMPLETAR], habiendo cesado su convivencia de forma efectiva, y desean proceder a solicitar el divorcio de su matrimonio.

SEXTO - Que, al amparo de lo establecido en el artículo 233-2 del Código Civil de Cataluña y en cumplimiento del artículo 777 de la Ley de Enjuiciamiento Civil, ambas partes, de común acuerdo, convienen en otorgar el presente CONVENIO REGULADOR, por mutuo acuerdo o consenso, para regular todos los aspectos del DIVORCIO que, en el día de hoy, inician bajo los siguientes.

PACTOS

PRIMERO. - DEL DIVORCIO

Las partes ratifican su separación matrimonial de forma efectiva, quedando revocados los poderes que pudieran haberse concedido mutuamente, acordando proceder a solicitar el divorcio de su matrimonio y sus efectos de conformidad con los pactos establecidos en el presente convenio, por lo que se comprometen a presentar la demanda para su solicitud y homologación judicial y a su ratificación cuando sean requeridos al efecto.

SEGUNDO. - DEL DOMICILIO CONYUGAL

En cuanto al último domicilio conyugal sito en [LOCALIDAD] en el que los comparecientes residían en régimen de alquiler, las partes declaran que han trasladado su domicilio y retirado todos sus bienes y enseres.

TERCERO. - DE LA CUSTODIA INDIVIDUAL RESPECTO AL PERRO COMÚN AL MATRIMONIO

Los cónyuges tienen un perro en común de [Nº] años de edad respecto al que acuerdan se mantenga en su domicilio habitual en [COMPLETAR], atribuyéndose así a [COMPLETAR] la custodia exclusiva del mismo y asumiendo éste/a mismo/a todos los gastos que deriven del cuidado diario, alimentación, veterinario y cualquier otro gasto asociado al animal.

Excepto que pacten otra cosa, [COMPLETAR] tendrá derecho a visitarlo un fin de semana al mes, a convenir con [COMPLETAR], siempre y cuando ésta se encuentre en [COMPLETAR]

CUARTO.- PRESTACIÓN COMPENSATORIA

Ambos cónyuges acuerdan no establecer pensión compensatoria alguna, ni equivalente en concepto alimenticio, a favor del otro, toda vez que no se produce desequilibrio alguno entre la situación actual y la anterior.

(alternativa)

Como consecuencia del divorcio, se ha producido un desequilibrio económico en D./Dña. [NOMBRE Y APELLIDOS], por lo que durante el periodo de [Nº] años tendrá derecho a percibir en concepto de prestación compensatoria la cantidad de [IMPORTE] euros, que se ingresará del 1 al 5 de cada mes en la cuenta bancaria [COMPLETAR], de la que es titular D./Dña. [NOMBRE Y APELLIDOS]

Entienden ambos cónyuges que dicho periodo de tiempo es suficiente para que D./Dña. [NOMBRE Y APELLIDOS] haya superado dicho desequilibrio económico pues actualmente se encuentra trabajando tiempo parcial, estando prevista la ampliación de la jornada en el tiempo indicado.

QUINTO. – DISOLUCIÓN DEL RÉGIMEN ECONÓMICO

El régimen económico vigente del matrimonio es el de separación de bienes, acordando ambas partes que quedará disuelto a partir de la fecha en que se dicte sentencia de divorcio y ésta adquiera firmeza.

SEXTO. - SALDO Y FINIQUITO

Ambos cónyuges acuerdan darse por saldados y finiquitados en la liquidación de la sociedad de gananciales, comprometiéndose a nada más pedirse ni reclamarse por otro concepto.

SÉPTIMO.- RATIFICACIÓN DEL PRESENTE CONVENIO

Los efectos del presente contrato entrarán en vigor en la fecha de la firma del mismo.

Ambos cónyuges se obligan a presentar la demanda de divorcio y solicitar la homologación del presente convenio, obligándose a su ratificación ante el tribunal, cuando sean requeridos para ello.

Y, en prueba de conformidad, las partes firman el presente documento por triplicado y a un solo efecto en [LUGAR], a [FECHA].

Fdo. Fdo.
