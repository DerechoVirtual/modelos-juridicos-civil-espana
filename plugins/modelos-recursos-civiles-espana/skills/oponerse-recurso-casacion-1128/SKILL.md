---
name: oponerse-recurso-casacion-1128
description: "Redacta el escrito «Oponerse al recurso de casación» (formulario 1128 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oponerse al recurso de casación

> Formulario 1128 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- Oposición a casación que discute la cuantía de 600.000 €: el acceso por cuantía se suprimió (art. 477 LEC, redacc. RDL 5/2023); centrar la oposición en la falta de interés casacional (art. 477.3).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NÚMERO (3 veces)
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] DESCRIBIR
- [ ] FECHA
- [ ] LOCALIDAD
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…lcanza el valor del 600.000 euros porque»; «…atan el supuesto que nos ocupa, sino que»; «…rios para la admisión del recurso porque»; «…—Nos oponemos por las siguientes razones»; «…—Mostramos nuestra disconformidad porque»; «…rso por estimar que concurre la causa de»; «…currente. Es justicia que pido en Madrid»; «…al fundarse el recurso principalmente en»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 485 de la LEC

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

### Formulario 1128 · Oponerse al recurso de casación

- Año del modelo: 2013
- Revisión 17-11-2026: 19 campos de relleno marcados en blanco
- Avisos de la revisión: Oposición a casación que discute la cuantía de 600.000 €: el acceso por cuantía se suprimió (art. 477 LEC, redacc. RDL 5/2023); centrar la oposición en la falta de interés casacional (art. 477.3).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Recurso de casación n.º [NÚMERO]

A LA SALA PRIMERA DEL TRIBUNAL SUPREMO

D./Dña [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña [NOMBRE Y APELLIDOS], según tengo debidamente acreditado en el recurso referenciado, ante la Sala comparezco y como mejor proceda en derecho DIGO.

Que según permite el art. 485 de la LEC, y en atención a lo acordado por el Letrado de la Administración de Justicia, con el presente escrito procedemos a formalizar OPOSICIÓN al RECURSO DE CASACIÓN interpuesto por la representación procesal de D./Dña [NOMBRE Y APELLIDOS] en atención a las siguientes

ALEGACIONES

(En su caso) PREVIA.—INADMISIBILIDAD DEL RECURSO.

En el trámite de admisión del recurso por esta Sala no se han estudiado las cuestiones que ahora planteamos que deben determinar la inadmisión del recurso:

(Opciones):

1.º—Se ha producido el defecto formal consistente en [DESCRIBIR] (presentación fuera de plazo del recurso o de la personación, falta de acreditación de la representación) que deben determinar sin más que se dicte sentencia declarando la desestimación por inadmisión del recurso.

2.º—El recurso no se funda en realidad en la infracción de normas aplicables para resolver el objeto del proceso sino que lo que intenta es buscar la aceptación de su visión de la prueba practicada en la primera instancia ya que

3.º—La cuantía del recurso en realidad no alcanza el valor del 600.000 euros porque [COMPLETAR]

4.º—Las sentencias presentadas para apoyar el interés casacional que se alega, no tratan el supuesto que nos ocupa, sino que [COMPLETAR])

En el caso de no tener en cuenta las causas aquí citadas como motivos de no admisión procedemos a impugnar la fundamentación del recurso en atención a los siguientes correlativos.

PRIMERO.— ANTECEDENTES DEL RECURSO

En efecto los trámites procesales llevados a efecto son los que describe en el escrito de interposición de fecha [FECHA] la parte recurrente

SEGUNDO.— PRESUPUESTOS Y REQUISITOS

(Opciones)

– Según hemos expuesto en el apartado previo consideramos que no se dan los requisitos necesarios para la admisión del recurso porque [COMPLETAR]

– Conformes con los presupuestos formales alegados de contrario.

TERCERO.— FUNDAMENTACIÓN DEL RECURSO

MOTIVO PRIMERO DE CASACIÓN.—Nos oponemos por las siguientes razones [COMPLETAR] MOTIVO SEGUNDO DE CASACIÓN.—Mostramos nuestra disconformidad porque [COMPLETAR]

COSTAS.—En aplicación del art. 398 en relación con el art. 394, ambos de la LEC, al desestimarse el recurso deberán imponerse las costas al recurrente.

Por lo expuesto,

SUPLICO A LA SALA: Que tenga por presentado este escrito con sus copias, lo admita a trámite y tenga por formulada en tiempo y forma oposición al recurso de casación planteado por D./Dña [NOMBRE Y APELLIDOS] a fin de que en su día, y previos los trámites legales oportunos, se dicte sentencia por la que se acuerde:

(Opciones):

1.º—Inadmitir el recurso por estimar que concurre la causa de [COMPLETAR]

2.º—Desestimar dicho recurso íntegramente confirmando la sentencia n.º [NÚMERO] dictada por la Audiencia Provincial de [LOCALIDAD] en el recurso n.º [NÚMERO]

Todo ello con expresa imposición de costas a la parte recurrente.

Es justicia que pido en Madrid [COMPLETAR] a [DÍA] de [MES] de [AÑO]

OTROSÍ DIGO. Que esta parte considera necesaria la celebración de vista al fundarse el recurso principalmente en [COMPLETAR] y resultar adecuada la exposición oral para

NUEVAMENTE SUPLICO: que en atención a lo expuesto se acuerde por la Sala la celebración de vista por ser justicia que pido en mismo lugar y fecha.

========================================================================
