---
name: oposicion-infraccion-procesal-extraordinaria-modelo-837
description: "Redacta el escrito «Oposición a la infracción procesal extraordinaria: modelo general» (formulario 837 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición a la infracción procesal extraordinaria: modelo general

> Formulario 0837 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Oposición a un recurso extraordinario por infracción procesal, que ya no existe (art. 474 LEC sin contenido, RDL 6/2023): reconvertir en oposición al recurso de casación.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NÚMERO (3 veces)
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] FECHA (2 veces)
- [ ] LOCALIDAD
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…do en la instancia según se comprueba en»; «…º—El recurso carece de fundamento porque»; «…—Nos oponemos por las siguientes razones»; «…nsidera imprescindible para acreditar la»; «…—Mostramos nuestra disconformidad porque»; «…rso por estimar que concurre la causa de»; «…urrente. Es justicia que pido en Madrid,»; «…ra necesaria la celebración de vista por»; «…solicitado la práctica de las pruebas de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 474 de la LEC

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

### Formulario 0837 · Oposición a la infracción procesal extraordinaria: modelo general

- Año del modelo: 2013
- Revisión 17-11-2026: 20 campos de relleno marcados en blanco
- Avisos de la revisión: Oposición a un recurso extraordinario por infracción procesal, que ya no existe (art. 474 LEC sin contenido, RDL 6/2023): reconvertir en oposición al recurso de casación.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Recurso por infracción procesal n.º [NÚMERO]

A LA SALA PRIMERA DEL TRIBUNAL SUPREMO

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según tengo debidamente acreditado en el recurso referenciado, ante la Sala comparezco y como mejor proceda en derecho DIGO.

Que según permite el art. 474 de la LEC y en atención a lo acordado por esta Sala en auto de fecha [FECHA], con el presente escrito procedemos a formalizar OPOSICIÓN al RECURSO POR INFRACCIÓN PROCESAL interpuesto por la representación procesal de D./Dña. [NOMBRE Y APELLIDOS] en atención a las siguientes

ALEGACIONES

Inadmisibilidad del recurso

(En su caso)

En el trámite de admisión del recurso por esta Sala no se han estudiado las cuestiones que ahora planteamos que debieron determinar la inadmisión del recurso y ahora deberían determinar que se dicte sentencia declarando que debió declararse tal inadmisión:

(Opciones):

1.º—El motivo en el que se funda el recurso no fue alegado en la instancia según se comprueba en [COMPLETAR]

2.º—El recurso carece de fundamento porque [COMPLETAR]

En el caso de no tener en cuenta las causas aquí citadas como motivos de no admisión procedemos a impugnar la fundamentación del recurso en atención a los siguientes correlativos.

Antecedentes del recurso

En efecto los trámites procesales llevados a efecto son los que describe en el escrito de interposición de fecha [FECHA] la parte recurrente.

Fundamentación de la oposición al recurso

MOTIVO PRIMERO DEL RECURSO.—Nos oponemos por las siguientes razones [COMPLETAR]

Con relación a este motivo interesamos la práctica de la siguiente prueba que se considera imprescindible para acreditar la [COMPLETAR] (información o vulneración) producida porque

MOTIVO SEGUNDO DEL RECURSO.—Mostramos nuestra disconformidad porque [COMPLETAR]

En este apartado consideramos pruebas imprescindibles para acreditar nuestra oposición y cuya práctica interesamos las siguientes:

Costas

En aplicación del art. 398 en relación con el art. 394, ambos de la LEC, al desestimarse el recurso deberán imponerse las costas al recurrente.

Por lo expuesto,

SUPLICO A LA SALA: Que tenga por presentado este escrito con sus copias, lo admita a trámite y tenga por formulada en tiempo y forma oposición al recurso por infracción procesal planteado por D./Dña. [NOMBRE Y APELLIDOS] a fin de que en su día, y previos los trámites legales oportunos, se dicte sentencia por la que se acuerde:

(Opciones):

1.º—Inadmitir el recurso por estimar que concurre la causa de [COMPLETAR]

2.º—Desestimar dicho recurso íntegramente confirmando la sentencia n.º [NÚMERO] dictada por la Audiencia Provincial de [LOCALIDAD] en el recurso n.º [NÚMERO] y ordenando la devolución de las actuaciones a este órgano judicial.

Todo ello con expresa imposición de costas a la parte recurrente.

Es justicia que pido en Madrid, [COMPLETAR] a [DÍA] de [MES] de [AÑO]

OTROSÍ DIGO. Que esta parte considera necesaria la celebración de vista por [COMPLETAR] (haber solicitado la práctica de las pruebas de [COMPLETAR] o resultar adecuada la exposición oral para la mejor impartición de justicia).

NUEVAMENTE SUPLICO: que en atención a lo expuesto se acuerde por la Sala la celebración de vista por ser justicia que pido en mismo lugar y fecha.

========================================================================
