---
name: inicio-expediente-jurisdiccion-voluntaria-675
description: "Redacta el escrito «Inicio de expediente de jurisdicción voluntaria» (formulario 675 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Inicio de expediente de jurisdicción voluntaria

> Formulario 0675 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] NIF
- [ ] LOCALIDAD (4 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… domicilio a efectos de notifiaciones en»; «…rado de la Administración de Justicia de»; «…, y bajo la dirección Letrada de Don»; «…numeración del juzgado de procedencia).]»; «…cuerdo con lo establecido en el artículo»; «…untaria, en base a los siguientes HECHOS»; «…, en su condición de»; «…amente el solicitante en su condición de»; «…amentos de fondo Es de aplicación el art»; «…del»; «…del [COMPLETAR] que establece que»; «…expediente de jurisdicción voluntaria de»; …

## Correcciones de la revisión (2)

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

### Formulario 0675 · Inicio de expediente de jurisdicción voluntaria

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 21 campos de relleno marcados en blanco; 4 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en nombre y representación de D. [NOMBRE Y APELLIDOS], con domicilio a efectos de notifiaciones en [COMPLETAR] y CIF [NIF] según acredito mediante apoderamiento apud acta otorgado ante el Letrado de la Administración de Justicia de [COMPLETAR], y bajo la dirección Letrada de Don [COMPLETAR], ante la Sección Civil del Tribunal de Instancia de [NOTA DE REVISIÓN: Un solo TI por partido judicial (art. 84.1 LOPJ): sobra «de los de». Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] que por turno de reparto corresponda comparezco y, como mejor proceda en Derecho,

DIGO:

Que mediante el presente escrito promueve expediente de jurisdicción voluntaria para (se dirá el objeto del expediente), de acuerdo con lo establecido en el artículo [COMPLETAR] de la Ley de Jurisdicción Voluntaria, en base a los siguientes

HECHOS

[COMPLETAR]

(caso de menciones de identidad específicas de interesados o terceros) A los efectos del art.LJV, debo hacer constar que, al margen del solicitante, son interesados en el expediente las personas que relaciono a continuación, con sus datos de identidad, y que son las siguientes:

D. [NOMBRE Y APELLIDOS], en su condición de [COMPLETAR], con domicilio en [LOCALIDAD]

FUNDAMENTOS DE DERECHO

Competencia

El art. establece que será competente para el conocimiento de este expediente el Tribunal de [LOCALIDAD] correspondiente al lugar de [LOCALIDAD]

Procedimiento

El procedimiento a seguir en el presente supuesto es el de jurisdicción voluntaria, regulado en los arts.de la LJV.

Legitimación y postulación

Está legitimado activamente el solicitante en su condición de [COMPLETAR], compareciendo (en su caso voluntariamente o por ser preceptivo) mediante Procurador y Abogado (en su caso, por ser el valor de superior a los seis mil euros), conforme a lo dispuesto en el art. de la LJV.

Fundamentos de fondo

Es de aplicación el art [COMPLETAR] del [COMPLETAR] que establece que [COMPLETAR]

Por lo expuesto,

AL TRIBUNAL SUPLICO: Que tenga por presentado este escrito con los documentos que se acompañan y sus copias, lo admita, y tenga por promovido expediente de jurisdicción voluntaria de [COMPLETAR] y, previos los trámites legales, incluida la práctica en la comparecencia de la prueba testifical que se interesa en el otrosí, dicte resolución en la que se acuerde

OTROSÍ PRIMERO DIGO: Que acreditar la certeza de los hechos relatados, solicito que en la comparecencia sean oídos [COMPLETAR] y propongo los siguientes testigos para acreditar la certeza de los hechos expresados:

- D. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD]

- [COMPLETAR]

SUPLICO AL TRIBUNAL: Tenga por propuestos a los testigos indicados, solicitando que sean citados por la Oficina Judicial para la práctica de la prueba en la comparecencia.

Es Justicia que insto en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Procurador y Letrado.

========================================================================
