---
name: acuerdo-desalojo-vivienda-necesidad-arrendador-820
description: "Redacta el escrito «Acuerdo de desalojo de la vivienda por necesidad del arrendador» (formulario 820 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acuerdo de desalojo de la vivienda por necesidad del arrendador

> Formulario 0820 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] DOMICILIO (2 veces)
- [ ] DNI/NIE (2 veces)
- [ ] FECHA (4 veces)
- [ ] HORA
- [ ] IMPORTE
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… arrendamiento de la vivienda situada en»; «…le para dedicarlo a vivienda habitual de»; «…a las»; «… la necesidad es temporal, transcurridos»; «… en el lugar y fecha del encabezamiento.»; «…(Arrendador)»

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

### Formulario 0820 · Acuerdo de desalojo de la vivienda por necesidad del arrendador

- Año del modelo: 2015
- Revisión 17-11-2026: 25 huecos del original que se habían perdido sin marca, marcados (COMPLETAR, DNI/NIE, DOMICILIO, DÍA, FECHA, HORA, IMPORTE, LUGAR, MES, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [DÍA] de [MES] de [AÑO]

REUNIDOS

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [DOMICILIO] y DNI n.º [DNI/NIE] y

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [DOMICILIO] y DNI n.º [DNI/NIE]

EXPONEN

1.º Que en fecha [FECHA] suscribieron contrato de arrendamiento de la vivienda situada en [COMPLETAR] actuando D./Dña. [NOMBRE Y APELLIDOS] como arrendador y D./Dña. [NOMBRE Y APELLIDOS] como arrendatario.

2.º Que en fecha [FECHA] el arrendador ha comunicado al arrendatario la necesidad del inmueble para dedicarlo a vivienda habitual de [COMPLETAR] (si mismo o de D./Dña. [NOMBRE Y APELLIDOS]), conminándole a que lo dejara libre tras el transcurso de dos meses.

3.º Que para resolver el contrato de arrendamiento por la causa indicada, los comparecientes libremente

ACUERDAN

Primero.— Que el arrendatario dejará libre la vivienda y a disposición de D./Dña. [NOMBRE Y APELLIDOS] (quien se haya indicado que la usará como vivienda habitual) el día [FECHA] a las horas [HORA], momento en que se procederá a la entrega de llaves en la citada vivienda.

Segundo.— Opciones: (En su caso):

• (Si se dejara antes del tiempo pactado): El arrendador compensará al arrendatario por dejar la vivienda antes de los dos meses legalmente indicados como tiempo mínimo de preaviso, con la cantidad de [IMPORTE] euros.

• Atendiendo a las necesidades del arrendatario, el arrendador consiente en alargar el plazo de entrega de la vivienda hasta el día [FECHA] a las [COMPLETAR] horas.

•Teniendo en cuenta que la necesidad es temporal, transcurridos [COMPLETAR] meses, el arrentario podrá volver a ocupar la vivienda en las mismas condiciones del contrato ahora vigente si así le interesara.

Tercero.— Tras la inspección de la vivienda y la comprobación de que no debe aplicarse a reparaciones o pagos de cantidades atrasadas, se procederá al reembolso de la fianza al arrendatario.

Y para que conste y surta los efectos oportunos, suscriben el presente documento en el lugar y fecha del encabezamiento.

[COMPLETAR] (Arrendador)[COMPLETAR] (Arrendatario)

========================================================================
