---
name: oposicion-interesado-jurisdiccion-voluntaria-669
description: "Redacta el escrito «Oposición de un interesado en jurisdicción voluntaria» (formulario 669 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición de un interesado en jurisdicción voluntaria

> Formulario 0669 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] Nº DE COLEGIADO
- [ ] COLEGIO
- [ ] FECHA
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…rado de la Administración de Justicia de»; «…te el presente escrito formulo oposición»; «…lada oposición al expediente instado por»; «…a oposición a la solicitud efectuada por»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 3.2 LJV

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

### Formulario 0669 · Oposición de un interesado en jurisdicción voluntaria

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 9 campos de relleno marcados en blanco; 4 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE COLEGIADO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en nombre y representación de D. [NOMBRE Y APELLIDOS], según acredito mediante apoderamiento apud-acta otorgado ante el Letrado de la Administración de Justicia de [COMPLETAR] que acompaño, bajo la dirección letrada de D. [NOMBRE Y APELLIDOS], colegiado núm. [Nº DE COLEGIADO] del Iltre. Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco y como mejor proceda en Derecho

DIGO:

1) Que el pasado día [FECHA] mi representado ha sido citado a la comparecencia que debe celebrarse en el expediente de jurisdicción voluntaria sobre [DESCRIBIR] instado por

2) Que, de conformidad con lo dispuesto en el art. 17.3, párrafo segundo, de la Ley de Jurisdicción Voluntaria, en mi condición de interesado, mediante el presente escrito formulo oposición [COMPLETAR], en base a los siguientes

HECHOS

 Los anteriores hechos nos llevan a oponernos a la solicitud, como acreditaremos en la comparecencia, debiendo desestimarse la petición del promotor del expediente

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

Se acepta la competencia del Tribunal al que me dirijo conforme a lo dispuesto en el art. de la Ley de Jurisdicción Voluntaria.

Procedimiento

Son de aplicación los preceptos mencionados por el promotor, así como el art. 17.3, párrafo segundo, LJV que dispone que “si alguno de los interesados fuera a formular oposición, deberá hacerlo en los 5 días siguientes a su citación, y no se hará contencioso el expediente, ni impedirá que continúe su tramitación hasta que sea resuelto, salvo que la ley expresamente lo prevea. Del escrito de oposición se dará traslado a la parte solicitante inmediatamente”.

Legitimación y postulación

Mi representado está legitimado en su condición de interesado en el expediente, compareciendo con Abogado y Procurador, debiendo requerirse al solicitante para que a partir de este momento actúe defendido por Abogado y representado por Procurador por ser preceptiva su intervención según preceptúa el art. 3.2 LJV.

Oposición

Es de aplicación el art., de donde resulta la procedencia de la oposición conforme se ha expresado en los hechos de esta resolución con la consecuente desestimación de la solicitud del promotor.

Por lo expuesto,

AL TRIBUNAL SUPLICO que tenga por presentado este escrito con los documentos que acompaño y sus copias, y en su virtud tenga por formulada oposición al expediente instado por [COMPLETAR], y, en su virtud, acuerde la transformación del expediente en contencioso, citando a las partes a la vista de juicio verbal y, tras los trámites legales, se dicte sentencia desestimando la solicitud formulada, con imposición de costas a la contraparte.

Por lo anterior,

AL TRIBUNAL SUPLICO que tenga por presentado este escrito con los documentos que acompaño y sus copias, y en su virtud tenga por formulada oposición a la solicitud efectuada por [COMPLETAR] y, tras los trámites legales, se dicte resolución desestimando la solicitud del promotor.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

(Firma Procurador y Abogado).

========================================================================
