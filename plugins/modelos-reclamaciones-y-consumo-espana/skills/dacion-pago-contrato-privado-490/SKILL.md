---
name: dacion-pago-contrato-privado-490
description: "Redacta el escrito «Dación en pago: contrato privado» (formulario 490 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Dación en pago: contrato privado

> Formulario 0490 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (18 veces)
- [ ] NACIONALIDAD (2 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] DNI/NIE (4 veces)
- [ ] IMPORTE (2 veces)
- [ ] NÚMERO
- [ ] SEDE
- [ ] Nº
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…daptado a la reforma de la LO 1/2025. En»; «…s: - + Añadir más párrafos iguales Finca»; «…autos de juicio declarativo ordinario de»; «…numeración del juzgado de procedencia).]»; «…s transmitentes y a instancias del Banco»

## Elecciones que hay que hacer

- soltero / soltera / casado / casada / divorciado / divorciada / separado / separada / viudo / viuda
- gananciales / separación de bienes

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Seleccionar en caso de que todas las partes actúen en nombre y representación propia / Seleccionar si alguna de las partes actúa en su propio nombre y representación — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Si se trata de persona física / Si se trata de una persona jurídica — el texto de cada opción no venía en el formulario original

## Párrafos opcionales (4)

Inclúyelos solo si encajan en los hechos:

- (Seleccionar en caso de estado civil casado/a)…
- (Seleccionar en caso de estado civil casado/a)…
- (Seleccionar si alguna de las partes actúa en nombre y representación de persona física o jurídica)…
- Tercera…

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

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

### Formulario 0490 · Dación en pago: contrato privado

- Año del modelo: 2017
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 4 desplegables convertidos en elección en blanco; 2 bloques de opciones sin texto dejados en blanco con sus rótulos; 4 párrafos opcionales señalados; 36 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Contrato privado de dación en pago en el que el acreedor acepta del deudor una prestación, liberándolo así de la obligación que los relacionaba, a pesar de no ser este pago lo que el deudor le debía al acreedor.

Formulario adaptado a la reforma de la LO 1/2025.

En [COMPLETAR]

REUNIDOS

DE UNA PARTE,

-
+
Añadir más párrafos iguales
(Datos del TRANSMITENTE)

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, de estado civil [ELEGIR: soltero / soltera / casado / casada / divorciado / divorciada / separado / separada / viudo / viuda], de nacionalidad [NACIONALIDAD], con domicilio en [LOCALIDAD], y DNI/Pasaporte número [DNI/NIE].

[OPCIONAL — incluir si procede]

(Seleccionar en caso de estado civil casado/a)

Casado
Casada
 con D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con DNI/Pasaporte número [DNI/NIE] en régimen económico matrimonial de [ELEGIR: gananciales / separación de bienes].

En lo sucesivo, EL TRANSMITENTE.

Y DE OTRA,

-
+
Añadir más párrafos iguales
(Datos del ADQUIRENTE)

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, de estado civil [ELEGIR: soltero / soltera / casado / casada / divorciado / divorciada / separado / separada / viudo / viuda], de nacionalidad [NACIONALIDAD], con domicilio en [LOCALIDAD], y DNI/Pasaporte número [DNI/NIE].

[OPCIONAL — incluir si procede]

(Seleccionar en caso de estado civil casado/a)

Casado
Casada
 con D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con DNI/Pasaporte número [DNI/NIE] en régimen económico matrimonial de [ELEGIR: gananciales / separación de bienes].

En lo sucesivo, EL ADQUIRENTE.

INTERVIENEN

[ELEGIR UNA OPCIÓN Y REDACTARLA: Seleccionar en caso de que todas las partes actúen en nombre y representación propia / Seleccionar si alguna de las partes actúa en su propio nombre y representación — el texto de cada opción no venía en el formulario original]

[OPCIONAL — incluir si procede]

(Seleccionar si alguna de las partes actúa en nombre y representación de persona física o jurídica)
-
+
Añadir más párrafos iguales

D./Dña. [NOMBRE Y APELLIDOS], en nombre y representación de:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Si se trata de persona física / Si se trata de una persona jurídica — el texto de cada opción no venía en el formulario original]

Ambas partes se reconocen mutuamente con capacidad suficiente para otorgar el presente contrato de DACIÓN EN PAGO y, a tal fin,

EXPONEN

I.- D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] son dueños, en pleno dominio y con carácter ganancial, de las siguientes fincas:

-
+
Añadir más párrafos iguales

Finca [COMPLETAR]

II.- D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] adeudan a D./Dña. [NOMBRE Y APELLIDOS] la cantidad de [IMPORTE] euros ( euros), por pagos efectuados por cuenta de los transmitentes en el procedimiento judicial de autos de juicio declarativo ordinario de [COMPLETAR] número [NÚMERO] seguidos en la sección civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. «De los de» es residuo de los varios juzgados de una plaza. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] contra los citados transmitentes y a instancias del Banco [COMPLETAR].

III.- Que habiendo convenido en otorgar el presente documento de dación en pago, lo efectúan de común acuerdo bajo las siguientes:

ESTIPULACIONES

Primera

D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] ceden y transmiten a D./Dña. [NOMBRE Y APELLIDOS], que acepta y adquiere en el presente acto, las fincas descritas en el apartado anterior, en pleno dominio, como cuerpos ciertos, con cuanto les sea anejo, inherente o accesorio, libres de cargas y gravámenes, sin arrendar, sin ocupantes y al corriente en el pago de todo tipo de gastos, contribuciones, impuestos y arbitrios.

Segunda

La transmisión y adquisición de las referidas fincas la efectúan los señores comparecientes en concepto de CESIÓN PRO SOLUTO o en pago de la deuda hasta ahora existente entre D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] con D./Dña. [NOMBRE Y APELLIDOS], en importe de [IMPORTE] euros, con íntegra liberación de los deudores y transmitentes en su responsabilidad.

[OPCIONAL — incluir si procede]

Tercera

El presente contrato se formalizará en escritura pública dentro del plazo de los treinta días naturales a contar desde el otorgamiento del presente contrato.

Los comparecientes subordinan la eficacia de todos los pactos anteriores en a la condición suspensiva de que el adquirente obtenga la inscripción previa en el Registro de la Propiedad de la escritura que en su momento se otorgue, en el plazo máximo de [Nº] meses, sin carga alguna y excepción hecha de las afecciones legales, quedando cumplida la condición al practicarse la inscripción.

Todos los gastos e impuestos derivados y ocasionados como consecuencia del otorgamiento del presente contrato y de la escritura pública en que en su momento se formalice, serán de cuenta del adquirente, incluso el impuesto municipal sobre incremento del valor de los terrenos urbanos, si se devengare.

Y en prueba de conformidad, firman el presente documento, por duplicado, en el lugar y fecha al principio indicados, quedando un ejemplar del mismo en poder de cada parte contratante.

TRANSMITENTES

ADQUIRENTE

Firmado: D./Dña. [NOMBRE Y APELLIDOS] 	Firmado: D./Dña. [NOMBRE Y APELLIDOS]

========================================================================
