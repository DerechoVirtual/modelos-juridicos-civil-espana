---
name: oposicion-expediente-fijacion-plazo-cumplimiento-650
description: "Redacta el escrito «Oposición al expediente de fijación del plazo de cumplimiento de la obligación» (formulario 650 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición al expediente de fijación del plazo de cumplimiento de la obligación

> Formulario 0650 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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
- [ ] Nº DE COLEGIADO/A
- [ ] COLEGIO
- [ ] FECHA (3 veces)
- [ ] Nº (2 veces)
- [ ] LOCALIDAD
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…D»; «…actuando en nombre y representación de D»; «…rado de la Administración de Justicia de»; «…acompaño, bajo la dirección letrada de D»; «…de»; «…de de la interpretación de las cláusulas»; «…y»; «…lada oposición al expediente instado por»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 1128 del Código Civil
- art. 97.3 de la LJV
- arts. 17.3 y 97.3 LJV
- art. 1128 CC
- art. 394 LEC

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

### Formulario 0650 · Oposición al expediente de fijación del plazo de cumplimiento de la obligación

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 19 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D [COMPLETAR], Procurador de los Tribunales, actuando en nombre y representación de D [COMPLETAR], según acredito mediante apoderamiento apud-acta otorgado ante el Letrado de la Administración de Justicia de [COMPLETAR] que acompaño, bajo la dirección letrada de D [COMPLETAR], colegiado núm [Nº DE COLEGIADO/A] del Iltre. Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco y como mejor proceda en Derecho

DIGO:

1) Que el pasado día [FECHA] mi representado ha sido citado a la comparecencia que debe celebrarse en el expediente de jurisdicción voluntaria de fijación del plazo para el cumplimiento de las obligaciones derivadas del contrato de fecha [FECHA] de [COMPLETAR] de instado por

2) Que, de conformidad con lo dispuesto en el art. 17.3 y 97.3 de la Ley de Jurisdicción Voluntaria, mediante el presente escrito formulo OPOSICIÓN a la solicitud del promotor del expediente, en base a los siguientes

HECHOS

Se acepta la existencia del contrato de permuta con el promotor del expediente, en virtud del cual mi representado se comprometió a realizar una obra nueva en el solar de titularidad del promotor y, en contraprestación, debía hacerle entrega de dos apartamentos tal como se recoge en la solicitud.

(motivos de improcedencia de la fijación del plazo) Negamos sin embargo que el contrato no contenga un plazo determinado, a diferencia de lo que alega el promotor del expediente, puesto que existe un término cierto para su cumplimiento, tal como se desprende de la interpretación de las cláusulas [COMPLETAR] y [COMPLETAR] del contrato. Así, la primera de las cláusulas establece que la obra se iniciará tan pronto mi representado disponga de los permisos y licencias correspondientes, en tanto que la segunda de las cláusulas fija un plazo de [Nº] años para realizar la obra.

Pues bien, el primero de los plazos, indeterminado, en modo alguno depende de la voluntad de mi representado, quien solicitó las licencias correspondientes ante el Ayuntamiento de [LOCALIDAD] el pasado día [FECHA], sin que hasta el momento haya obtenido respuesta (se acompaña como documentos núm [Nº DE DOCUMENTO] solicitudes de licencia formuladas por mi representado). En consecuencia, hasta tanto no se otorguen las licencias no empieza a correr el plazo para la construcción del edificio, expresamente pactado, siendo previsible que las licencias estén concedidas dentro de [Nº] meses según comunicación verbal de los servicios municipales, momento en el cual empezará a correr el segundo de los plazos para el inicio de la obra.

De ello se desprende claramente que no es de aplicación el art. 1128 del Código Civil al caso de autos, por lo que nos vemos en la obligación de formular oposición conforme a lo que dispone el art. 97.3 de la Ley de Jurisdicción Voluntaria, debiendo tornarse contencioso el expediente y seguir los trámites del juicio verbal.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

Se acepta la competencia del Tribunal al que me dirijo conforme a lo dispuesto en el art. 97.1 de la Ley de Jurisdicción Voluntaria.

Procedimiento

Al haberse formulado oposición es de aplicación lo dispuesto en el art. 97.3 de la LJV, de manera que el expediente se torna contencioso y el Letrado de la Administración de Justicia debe citar a los interesados a una vista, continuando la tramitación con arreglo a lo previsto para el juicio verbal.

Oposición

Se cumplen los requisitos para la oposición de los arts. 17.3 y 97.3 LJV fundada en la inaplicación del art. 1128 CC al caso de autos.

Costas

Es de aplicación el art. 394 LEC.

Por lo expuesto,

AL TRIBUNAL SUPLICO que tenga por presentado este escrito con los documentos que acompaño y sus copias, y en su virtud tenga por formulada oposición al expediente instado por [COMPLETAR], y, en su virtud, acuerde la transformación del expediente en contencioso, citando a las partes a la vista de juicio verbal y, tras los trámites legales, se dicte sentencia desestimando la solicitud formulada, con imposición de costas a la contraparte.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

(Firma Procurador y Abogado).

========================================================================
