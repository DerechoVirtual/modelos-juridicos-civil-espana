---
name: conciliacion-ante-juez-paz-663
description: "Redacta el escrito «Conciliación ante el Juez de Paz» (formulario 663 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Conciliación ante el Juez de Paz

> Formulario 0663 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- Conciliación ante el juez/a de paz con el umbral de 6.000 € del art. 140.1 LJV: el art. 47.2 LEC (LO 1/2025) habla de cuantía inferior a 10.000 €. Las dos normas no coinciden: citar ambas y comprobar el criterio del partido.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] PROFESIÓN
- [ ] LOCALIDAD
- [ ] IMPORTE (3 veces)
- [ ] MATRÍCULA
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…AL JUEZ DE PAZ DE»; «…, vecino de»; «…a Oficina de Justicia en el municipio de»; «…de»; «…de [COMPLETAR] de»

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

### Formulario 0663 · Conciliación ante el Juez de Paz

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 16 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)
- Avisos de la revisión: Conciliación ante el juez/a de paz con el umbral de 6.000 € del art. 140.1 LJV: el art. 47.2 LEC (LO 1/2025) habla de cuantía inferior a 10.000 €. Las dos normas no coinciden: citar ambas y comprobar el criterio del partido.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

AL JUEZ DE PAZ DE [COMPLETAR]

D/Dª [NOMBRE Y APELLIDOS], mayor de edad, casado y de profesión [PROFESIÓN], vecino de [COMPLETAR], con domicilio en [LOCALIDAD], con D.N.I. núm. comparezco ante la Oficina de Justicia en el municipio de [COMPLETAR], y respetuosamente

EXPONGO

Que mediante el presente escrito, y de conformidad a lo dispuesto en los artículos 139 y siguientes de la Ley de Jurisdicción Voluntaria, solicito celebrar ACTO DE CONCILIACIÓN con el requerido D./Dª. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en

Que deduzco la solicitud ante ese Juez de Paz al ser la cuantía de la petición de [NOTA DE REVISIÓN (comprobar): La cuantía («inferior a 6.000») sigue el art. 140.1 LJV; el art. 47.2 LEC (LO 1/2025) eleva el umbral del juez/a de paz a menos de 10.000 €. Mencionar ambos preceptos. Fuente: LEC art. 47.2 (redacc. LO 1/2025, BOE-A-2025-76) frente a LJV art. 140.1 (Ley 15/2015, BOE-A-2015-7391, no modificado).] [IMPORTE] euros, inferior a 6.000, y en relación a una materia no atribuida a las Secciones de lo Mercantil de los Tribunales de Instancia en el art. 87.6 de la Ley Orgánica del Poder Judicial, todo ello de conformidad a lo que dispone el art. 140.1 de la Ley de Jurisdicción Voluntaria.

Que el objeto de la conciliación es que el requerido reconozca que está en adeudarme la cantidad de [IMPORTE] euros correspondientes al resto del precio de la compraventa de la motocicleta matrícula [MATRÍCULA] formalizada en contrato privado de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] que acompaño, y que debía abonarme el pasado día [FECHA] según el citado contrato.

Que por ello solicito al requerido que se avenga abonarme la cantidad de [IMPORTE] euros en concepto de pago del resto del precio de la motocicleta vendida en el referido contrato.

En virtud de lo antes indicado,

SUPLICO: Que tenga por presentada esta solicitud con su copia, se sirva admitirla, y señalar día y hora para celebrar el acto de conciliación que se interesa, citando para el mismo al requerido D/Dª [NOMBRE Y APELLIDOS] en la forma legalmente prevista; y una vez celebrado, disponer se me entregue testimonio del acta, dictando la resolución que en su caso proceda.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

(Firma del solicitante)

========================================================================
