---
name: oposicion-recurso-apelacion-jurisdiccion-voluntaria-653
description: "Redacta el escrito «Oposición al recurso de apelación en jurisdicción voluntaria» (formulario 653 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición al recurso de apelación en jurisdicción voluntaria

> Formulario 0653 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD
- [ ] NOMBRE Y APELLIDOS
- [ ] FECHA (4 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «…de [COMPLETAR] de»; «…de»; «…de [COMPLETAR] de»; «…de»; «…de [COMPLETAR] de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 461 de la LEC
- art. 458.3 de la LEC
- art. 458.1 de la LEC
- art. 376 de la LEC

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

### Formulario 0653 · Oposición al recurso de apelación en jurisdicción voluntaria

- Año del modelo: 2015
- Revisión 17-11-2026: 12 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA AUDIENCIA PROVINCIAL DE [LOCALIDAD]

D. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D. según tengo acreditado en el expediente arriba expresado, ante la Sala comparezco y como mejor proceda en derecho

DIGO:

Que esta representación ha sido emplazada en fecha [FECHA] de [COMPLETAR] de [COMPLETAR] para oposición e impugnación del recurso de apelación interpuesto de contrario, por lo que, de conformidad a lo dispuesto en el art. 461 de la LEC, mediante el presente escrito me opongo en base a los siguientes

MOTIVOS

Con carácter previo, y al amparo del art. 458.3 de la LEC, se alega la inadmisibilidad del recurso de apelación interpuesto al haberse interpuesto una vez transcurrido el plazo de veinte días establecido en el art. 458.1 de la LEC, al que se remite el art. 20.2 de la Ley de Jurisdicción Voluntaria.

Del examen de los autos se constata que el recurso de apelación se interpuso en fecha [FECHA] de [COMPLETAR] de [COMPLETAR], según consta en el sello de entrada que figura en el mismo escrito, cuando el auto había sido notificada a la parte apelante el día [FECHA] Por tanto, habían transcurrido más de veinte días hábiles al momento de presentarse el recurso, de lo que se concluye indudablemente que la sentencia era ya firme y que el recurso es inadmisible.

De admitirse el recurso, nos oponemos al motivo alegado por la parte apelante, puesto que expone de forma subjetiva e interesada el resultado de la prueba practicada, partiendo de unos hechos totalmente incompatibles con los declarados probados en la resolución apelada, de manera que la aplicación del precepto legal que invoca como infringido resulta de un supuesto de hecho que en absoluto se corresponde con el examinado en este expediente.

En efecto, esta parte comparte plenamente las conclusiones fácticas, y sobre todo las consideraciones jurídicas, que se exponen a lo largo del auto apelado a los fines de sustentar la estimación de la solicitud inicial presentada por esta parte en el expediente, sin que queden desvirtuadas por las alegaciones vertidas de contrario en el escrito de interposición del recurso.

Las amplias y sobre todo acertadas consideraciones que se exponen en la resolución objeto de recurso dispensan a esta parte de mayor argumentación, si bien debemos subrayar sobre todo que el Juez ha dado total credibilidad a los testigos que depusieron en el juicio exponiendo una valoración de prueba que se ajusta plenamente a los cánones de la sana crítica a que se refiere el art. 376 de la LEC, sin que deba prevalecer en modo alguno el criterio parcial e interesado del recurrente en cuanto a la valoración de la prueba.

En consecuencia, se solicita que se dicte resolución desestimatoria del recurso.

En base a lo anterior,

SUPLICO A LA SALA que tenga por presentado este escrito con sus copias y con justificante de traslado a las demás partes, teniéndome por opuesto al recurso de apelación frente al auto de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] dictado en el presente expediente, y tras la pertinente tramitación, se declare la inadmisibilidad del recurso de apelación o, en otro caso, se desestime el recurso de apelación interpuesto.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma Abogado y Procurador

========================================================================
