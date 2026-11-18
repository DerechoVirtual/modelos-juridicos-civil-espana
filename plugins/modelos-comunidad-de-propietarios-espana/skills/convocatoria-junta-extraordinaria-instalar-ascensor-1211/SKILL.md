---
name: convocatoria-junta-extraordinaria-instalar-ascensor-1211
description: "Redacta el escrito «Convocatoria de junta extraordinaria para instalar ascensor» (formulario 1211 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Convocatoria de junta extraordinaria para instalar ascensor

> Formulario 1211 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] FECHA
- [ ] Nº (2 veces)
- [ ] IMPORTE (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…dente de la Comunidad de Propietarios de»; «…dente de la Comunidad de Propietarios de»; «…Junta Extraordinaria que tendrá lugar en»; «…parto de las derramas extraordinarias en»; «…, piso»; «…, piso [COMPLETAR],»; «…, local»; «…, local [COMPLETAR],»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Ascensores / Exposición necesidad eliminar barreras arquitectónicas / Exposición proyecto instalación ascensor / Mandato solicitud de presupuestos / — y además elegir: Presupuestos / Diferentes presupuestos / Ayudas y subvenciones / — y además elegir: Solicitud de ocupación / Superficie privada / Superficie suelo público — el texto de cada opción no venía en el form

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

### Formulario 1211 · Convocatoria de junta extraordinaria para instalar ascensor

- Año del modelo: 2013
- Revisión 17-11-2026: 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 18 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./Dña. [NOMBRE Y APELLIDOS]

Presidente de la Comunidad de Propietarios de [COMPLETAR]

A la atención de:

D./Dña. [NOMBRE Y APELLIDOS]

CONVOCATORIA DE JUNTA EXTRAORDINARIA

El Sr. Presidente de la Comunidad de Propietarios de [COMPLETAR] convoca a todos los propietarios de este inmueble a Junta Extraordinaria que tendrá lugar en [COMPLETAR] el día [FECHA] a las [Nº] horas en primera convocatoria o a las [Nº] horas en segunda convocatoria.

El orden del día de la reunión será el siguiente:

ORDEN DEL DÍA

Lectura y aprobación, en su caso, del acta de la Junta anterior.

[ELEGIR UNA OPCIÓN Y REDACTARLA: Ascensores / Exposición necesidad eliminar barreras arquitectónicas / Exposición proyecto instalación ascensor / Mandato solicitud de presupuestos / — y además elegir: Presupuestos / Diferentes presupuestos / Ayudas y subvenciones / — y además elegir: Solicitud de ocupación / Superficie privada / Superficie suelo público — el texto de cada opción no venía en el formulario original]

Explicación de la propuesta de derramas extraordinarias que corresponderá abonar a cada comunero en atención al presupuesto aprobado. Deliberación y votación para la aprobación de la forma de pago y de aportación de cada propietario. Acompaña a esta convocatoria la documentación relativa al presupuesto elegido con el importe de la obra y la propuesta de reparto de las derramas extraordinarias en [COMPLETAR] pagos y según cuota de participación de los titulares.

Ruegos y preguntas.

Según requiere el artículo 16.2 de la Ley de Propiedad Horizontal se presenta relación de los comuneros que no se encuentran al corriente del pago de las deudas vencidas a favor de la Comunidad de Propietarios, advirtiéndoles de esta manera expresamente de que si al momento de iniciarse la Junta para la que ahora se convoca no hubieran liquidado la deuda o consignado su importe por vía judicial o notarial o impugnado dicha deuda ante el Tribunal, se verán privados del derecho de voto, aunque podrán asistir a la Junta y participar en las deliberaciones:

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], [COMPLETAR] cuotas pendientes, total [IMPORTE] euros.

D./Dña. [NOMBRE Y APELLIDOS], local [COMPLETAR], [COMPLETAR] cuotas pendientes, total [IMPORTE] euros.

En atención a la trascendencia del asunto a tratar se ruega encarecidamente la asistencia de todos los propietarios.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firmado:

Recibí:

========================================================================
