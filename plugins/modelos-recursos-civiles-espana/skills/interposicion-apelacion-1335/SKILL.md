---
name: interposicion-apelacion-1335
description: "Redacta el escrito «Interposición de la apelación» (formulario 1335 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Interposición de la apelación

> Formulario 1335 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] NÚMERO (5 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] FECHA (3 veces)
- [ ] ÓRGANO
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…CIÓN CIVIL DE LA AUDIENCIA PROVINCIAL DE»; «…resamente impugnamos son los siguientes:»; «…que se refieren a»; «…cesario para la práctica de la prueba de»; «…por»; «… le ha causado indefensión en la fase de»; «…al no permitírsele»; «…, tal como consta en»; «…ecialmente la documental ha servido para»; «… los fundamentos de la sentencia, ya que»; «… ha aplicado incorrectamente el artículo»; «…L: Que tenga por presentado este escrito»; …

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Pago rentas / Consignación rentas futuras — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Justificante / Exento — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 2, 4, 5 y 8.2 de la Ley 10/2012

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

### Formulario 1335 · Interposición de la apelación

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 2 bloques de opciones sin texto dejados en blanco con sus rótulos; 26 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio n.º [NÚMERO]

A LA SECCIÓN CIVIL DE LA AUDIENCIA PROVINCIAL DE [COMPLETAR]

[NOTA DE REVISIÓN (comprobar): La AP no tiene «Sección Civil» como denominación legal: se cita la Sección por su número (p. ej. «A LA SECCIÓN [ ] DE LA AUDIENCIA PROVINCIAL DE [ ]»). Fuente: LOPJ arts. 80 y 82 (Audiencia Provincial, sin cambio de denominación).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según tengo debidamente acreditado en los autos referenciados, ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que mediante el presente escrito, en aplicación del artículo 458 de la Ley de Enjuiciamiento Civil, interpongo recurso de apelación contra la sentencia n.º [NÚMERO] de fecha [FECHA] dictada en estos autos, con base en los siguientes antecedentes y alegaciones.

ANTECEDENTES

La sentencia se ha notificado a esta parte el día [FECHA], por lo que en atención a lo establecido en el artículo 458 de la Ley de Enjuiciamiento Civil se presenta en tiempo y ante el órgano competente para tener por interpuesto el recurso.

El fallo de la sentencia declara que:

Los pronunciamientos que expresamente impugnamos son los siguientes: [COMPLETAR].

Adjunto justificante de ingreso en la cuenta de depósitos y consignaciones de este Tribunal, de la cantidad de 50 euros como depósito para recurrir en apelación, según exige la disposición adicional decimoquinta de la Ley Orgánica del Poder Judicial.

:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Pago rentas / Consignación rentas futuras — el texto de cada opción no venía en el formulario original]

 En aplicación de los artículos 2, 4, 5 y 8.2 de la Ley 10/2012, de 20 de noviembre y la Orden/HAP/2662/2012, de 13 de diciembre:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Justificante / Exento — el texto de cada opción no venía en el formulario original]

ALEGACIONES

:

—Presento los docs. n.º [NÚMERO] que se refieren a [COMPLETAR], según permiten los artículos 270 y 460.1 de la Ley de Enjuiciamiento Civil y que no se presentaron en primera instancia porque

—Intereso en aplicación de lo establecido en el artículo 460.2 de la Ley de Enjuiciamiento Civil que en esta segunda instancia se admita y ordene lo necesario para la práctica de la prueba de [COMPLETAR] por [COMPLETAR].

. Esta parte alega como primer motivo del recurso que se le ha causado indefensión en la fase de [COMPLETAR] al no permitírsele [COMPLETAR] Así se hizo constar mediante [ÓRGANO], tal como consta en [COMPLETAR].

La prueba practicada ha servido para acreditar nuestras pretensiones. Especialmente la documental ha servido para [COMPLETAR]

Por este motivo se ha impugnado el pronunciamiento n.º [NÚMERO] de los fundamentos de la sentencia, ya que [COMPLETAR].

Entendemos, además, que se ha aplicado incorrectamente el artículo [COMPLETAR] por los siguientes motivos [DESCRIBIR]

En definitiva todas estas alegaciones deben llevar a la Sala a revocar la sentencia, dictada en instancia y a resolver que se estimen nuestras pretensiones iniciales que reproducimos nuevamente, es decir, que

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito [COMPLETAR] y por entregadas sus copias, lo admita y acuerde tener por interpuesto en tiempo y forma recurso de apelación contra la sentencia n.º [NÚMERO], de fecha [FECHA], dictada en estos autos, a fin de que en su día se dicte sentencia por la que, estimando íntegramente este recurso, revoque y deje sin efecto la sentencia dictada en la instancia en lo relativo a los pronunciamientos impugnados, acordando, en su lugar [COMPLETAR], todo ello con expresa imposición de costas de la instancia a la parte contraria.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

OTROSÍ DIGO:. Que, en aplicación del artículo 464.2 de la Ley de Enjuiciamiento Civil y en atención a la complejidad del asunto, esta parte interesa la celebración de vista.

NUEVAMENTE SUPLICO: Que para la resolución de este recurso se acuerde la celebración de vista por ser justicia que pido en mismo lugar y fecha.

========================================================================
