---
name: citacion-interesados-u-oyentes-comparecencia-676
description: "Redacta el escrito «Citación de interesados u oyentes a la comparecencia» (formulario 676 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Citación de interesados u oyentes a la comparecencia

> Formulario 0676 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.

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
- [ ] NOMBRE Y APELLIDOS (8 veces)
- [ ] Nº DE COLEGIADO
- [ ] COLEGIO
- [ ] FECHA
- [ ] DESCRIBIR
- [ ] LOCALIDAD (3 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…rado de la Administración de Justicia de»; «…(abuelo materno); Dª»; «…y Dª»; «…Dª»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 213 del Código Civil

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

### Formulario 0676 · Citación de interesados u oyentes a la comparecencia

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 12 campos de relleno marcados en blanco; 9 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE COLEGIADO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en nombre y representación de D. [NOMBRE Y APELLIDOS], según acredito mediante apoderamiento apud-acta otorgado ante el Letrado de la Administración de Justicia de [COMPLETAR] que acompaño, bajo la dirección letrada de D. [NOMBRE Y APELLIDOS], colegiado núm. [Nº DE COLEGIADO] del Iltre. Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco y como mejor proceda en Derecho

DIGO:

1) Que el pasado día [FECHA] mi representado ha sido citado a la comparecencia en su condición de interesado, en el expediente de jurisdicción voluntaria sobre [DESCRIBIR] instado por

2) Que, atendido el escrito de solicitud, se han omitido datos de personas que puedan estar interesadas en este expediente, así como de otras que han de ser oídas, por lo cual, por razones de economía procesal, ponemos en conocimiento del Tribunal estas circunstancias a los efectos de citación para la comparecencia de acuerdo a los siguientes

HECHOS Y FUNDAMENTOS

El presente expediente se ha instado para la constitución de tutela del menor D. por parte de D. [NOMBRE Y APELLIDOS], hermano de la madre fallecida del menor, quien pretende asimismo ser designado tutor.

En el hecho cuarto de la solicitud se relacionan los siguientes parientes más próximos del menor: D. [NOMBRE Y APELLIDOS] (tío materno), D. [NOMBRE Y APELLIDOS] (abuelo materno); Dª [COMPLETAR] (abuela materna); y mi representado en su condición de tío, hermano del padre también fallecido.

Lo primero que hay que poner de relieve es que no se han designado a todos los parientes más próximos del menor en la solicitud.

En primer lugar, no se han recogido las menciones de identidad y datos de localización de los abuelos paternos D. [NOMBRE Y APELLIDOS] y Dª [COMPLETAR], con domicilio en [LOCALIDAD], quienes además nos consta que están interesados en ser designados tutores de su nieto, que convivió con ellos varios años durante la enfermedad de la madre hasta que, recientemente y tras su fallecimiento, fue a vivir con el tío materno que insta la constitución de la tutela. Asimismo, los abuelos paternos están interesados en el expediente puesto que están llamados a la designación como tutores, según lo dispuesto en el art. 213 del Código Civil.

Asimismo, también se han omitido los datos de identidad de los tíos maternos, hermanos del solicitante, que son los siguientes:

D. [NOMBRE Y APELLIDOS], hermano del solicitante y tío del menor, con domicilio en [LOCALIDAD]

Dª [COMPLETAR], hermana de la solicitante y tía del menor, con domicilio en [LOCALIDAD]

Atendido lo anterior, solicitamos del Tribunal que se cite a la comparecencia a los abuelos paternos y a los tíos maternos del menor, con las circunstancias de identidad y domicilio antes expuestas, por ser preceptivo conforme a lo que dispone el art. 45.2 de la Ley de Jurisdicción Voluntaria y art. 213 del Código Civil en cuanto al llamamiento para el nombramiento de tutor, estimando esta parte que los abuelos maternos son interesados en este expediente y los tíos deben ser oídos en la comparecencia.

Por lo expuesto,

AL TRIBUNAL SUPLICO que tenga por presentado este escrito con los documentos que acompaño y sus copias, y en su virtud, cite a la comparecencia a los abuelos paternos y tíos maternos del menor en la condición y a los efectos expuestos.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

(Firma Procurador y Abogado).

========================================================================
