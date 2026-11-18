---
name: apelacion-contra-auto-abstiene-falta-competencia-1088
description: "Redacta el escrito «Apelación contra el auto que se abstiene por falta de competencia objetiva» (formulario 1088 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Apelación contra el auto que se abstiene por falta de competencia objetiva

> Formulario 1088 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] NÚMERO (3 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (3 veces)
- [ ] SEDE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Juicio»; «…CIÓN CIVIL DE LA AUDIENCIA PROVINCIAL DE»; «…redacción se deduce que no es así ya que»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 66.1 y 455.1 y 458 de la LEC
- art. 458 de la LEC

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

### Formulario 1088 · Apelación contra el auto que se abstiene por falta de competencia objetiva

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 14 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio [COMPLETAR] (ordinario o verbal) n.º [NÚMERO]

A LA SECCIÓN CIVIL DE LA AUDIENCIA PROVINCIAL DE [COMPLETAR]

[NOTA DE REVISIÓN (comprobar): La AP no tiene «Sección Civil» como denominación legal: se cita la Sección por su número (p. ej. «A LA SECCIÓN [ ] DE LA AUDIENCIA PROVINCIAL DE [ ]»). Fuente: LOPJ arts. 80 y 82 (Audiencia Provincial, sin cambio de denominación).]

D./Dña. [NOMBRE Y APELLIDOS] Procurador de los Tribunales, en nombre y representación de [NOMBRE DEL REPRESENTADO/A]

D./Dña. [NOMBRE Y APELLIDOS], según tengo debidamente acreditado en el procedimiento referenciado, ante la Sala comparezco y como mejor proceda en derecho DIGO:

Que según permiten los arts. 66.1 y 455.1 y 458 de la LEC, mediante el presente escrito formulo recurso de apelación contra el auto n.º [NÚMERO] de fecha [FECHA], dictado en este procedimiento, por el que se acuerda la abstención del conocimiento de este asunto por falta de competencia objetiva en atención a los siguientes presupuestos y alegaciones:

PRESUPUESTOS

Formulo el presente Recurso de Apelación contra el Auto n.º [NÚMERO] de fecha [FECHA] mediante el que se acuerda por el Tribunal de Instancia de [SEDE] abstenerse de conocer del presente asunto, se sobresee el proceso, señalando que la parte actora ha de usar su derecho mediante sumisión al arbitraje convenido.

Formulo el recurso de apelación dentro del plazo legal de veinte días previsto en el art. 458 de la LEC.

Dirijo el presente Recurso de Apelación a impugnar los siguientes pronunciamientos del Auto recurrido:

1. el acuerdo de abstenerse de conocer del presente asunto,

2. y los acuerdos consecuentes de sobreseer el proceso y señalar que la parte actora ha de usar su derecho mediante sumisión al arbitraje convenido.

ALEGACIONES

Considera el auto recurrido que en el pacto suscrito por las partes se sometieran éstas a arbitraje en todas las cuestiones litigiosas que pudieran derivarse de la interpretación y ejecución de este documento.

Del tenor literal de su redacción se deduce que no es así ya que [COMPLETAR]

Por lo expuesto,

SUPLICO A LA SALA: Que tenga por presentado este escrito, lo admita y tenga por formulado RECURSO DE APELACIÓN contra el Auto de fecha [FECHA] mediante el que se acuerda abstenerse de conocer del presente asunto, sobreseer el proceso y señalar que la parte actora ha de usar su derecho mediante sumisión al arbitraje convenido, a fin de que en su día y, previos los trámites legales oportunos, se acuerde por la Audiencia Provincial dejar sin efecto esta resolución manteniendo la competencia objetiva del Tribunal de Instancia.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

OTROSÍ I DIGO: Que según exige la disposición adicional decimoquinta de la LOPJ, se ha procedido a consignar en la cuenta del Tribunal la cantidad de 50 euros como depósito para recurrir, según se acredita con el justificante que acompaño.

NUEVAMENTE SUPLICO: Que se tenga por realizado el depósito para recurrir, por ser justicia que pido en mismo lugar y fecha.

========================================================================
