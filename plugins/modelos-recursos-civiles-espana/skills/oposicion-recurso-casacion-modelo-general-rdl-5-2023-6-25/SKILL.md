---
name: oposicion-recurso-casacion-modelo-general-rdl-5-2023-6-25
description: "Redacta el escrito «Oposición al recurso de casación: modelo general (RDL 5/2023 y 6/2023)» (formulario 25 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición al recurso de casación: modelo general (RDL 5/2023 y 6/2023)

> Formulario 0025 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (2 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (6 veces)
- [ ] Nº
- [ ] LUGAR
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Sección»; «…ncia dictada por la Audiencia Provincial»; «…e fecha [FECHA] en el rollo de apelación»; «…que dimana del procedimiento»; «…/a del Ilustre Colegio de la Abogacía de»; «… presente escrito de oposición consta de»; «…folios y un total de»

## Párrafos opcionales (2)

Inclúyelos solo si encajan en los hechos:

- OTROSÍ DIGO PRIMERO: Que, al amparo de lo establecido en el artículo 485 de la LEC, esta parte hace constar qu…
- OTROSÍ DIGO SEGUNDO: D./Dña. [NOMBRE Y APELLIDOS], Abogado/a del Ilustre Colegio de la Abogacía de [COMPLETAR]…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 485 LEC
- art. 449 LEC
- art. 438.2.4 LEC
- artículo 485 de la LEC

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

### Formulario 0025 · Oposición al recurso de casación: modelo general (RDL 5/2023 y 6/2023)

- Año del modelo: 2024
- Revisión 17-11-2026: 2 párrafos opcionales señalados; 20 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Antecedentes:

Audiencia Provincial de [LOCALIDAD] Sección [COMPLETAR]

Rollo de apelación núm. [Nº DE PROCEDIMIENTO]

A LA SALA PRIMERA DEL TRIBUNAL SUPREMO

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de [NOMBRE DEL REPRESENTADO/A], según tengo acreditado en los Autos al margen referenciados, ante la Sala COMPAREZCO y

Digo

Que, con fecha [FECHA], me ha sido notificado Auto de fecha [FECHA] por medio del cual se admite el recurso de casación interpuesto por D./Dña. [NOMBRE Y APELLIDOS] contra la Sentencia dictada por la Audiencia Provincial [COMPLETAR] de fecha [FECHA] en el rollo de apelación [COMPLETAR] que dimana del procedimiento [COMPLETAR] (en adelante, la "Sentencia").

Que, por medio del presente escrito y al amparo del artículo 485 de la Ley de Enjuiciamiento Civil (en adelante, "LEC") en su redacción vigente dada por los Reales Decretos Leyes 5/2023 y 6/2023, vengo a OPONERME al recurso de casación formulado por la parte contraria, con base en las siguientes,

Alegaciones

Primera.– Concurrencia de graves causas de inadmisión

Si bien el Auto de fecha [FECHA] admitió el recurso de casación planteado por la adversa sin apreciar causas legales que condujesen a su inadmisión, la jurisprudencia ha venido admitiendo que la parte recurrida ponga de manifiesto en su escrito de oposición aquellas causas de inadmisibilidad que considera existentes y no rechazadas previamente por el Tribunal dada la provisionalidad de la admisión (STS de 14 de marzo de 2011, rec. 2114/2007; 5 de noviembre de 2007, rec. 3460/2000; 12 de marzo de 2007, rec. 939/2000 o 12 de julio de 2007, rec. 2871/2000).

El Acuerdo de la Sala Primera del Tribunal Supremo de 27 de enero de 2017 determina que:

"La exigencia de decisión expresa en la sentencia sobre las causas de inadmisibilidad del recurso alegadas por el recurrido en su escrito de oposición al recurso, con base en lo previsto en el segundo párrafo del art. 485 LEC, debe entenderse circunscrita a lo que esta sala considera causas de inadmisión absolutas: no reunir la resolución de que se trate los requisitos establecidos para ser recurrible, falta de postulación, interposición de los recursos fuera de plazo, falta de constitución del depósito para recurrir o de la debida subsanación de tal omisión, falta de cumplimiento de los presupuestos para recurrir en los casos especiales previstos en el art. 449 LEC e inexistencia de gravamen para recurrir. Por el contrario, las denominadas causas relativas de inadmisión, referentes a mera técnica casacional, deben entenderse en principio resueltas en el auto de admisión."

Dicho lo anterior, consideramos que el recurso debió ser inadmitido por (alternativamente):

a) Falta de cumplimiento de las exigencias formales de la carátula de casación y de las exigencias contenidas en el Acuerdo de la Sala de Gobierno de 8 de septiembre de 2023.
b) Falta de cumplimiento de las exigencias de la Sala Primera sobre la finalidad y alcance de la casación (alteración de la base fáctica de la sentencia de apelación o improcedencia de la conversión en una tercera instancia).
c) Carencia manifiesta de fundamento (art. 438.2.4 LEC).
d) Falta de acreditación del interés casacional (art. 483.2.3º LEC).

Segunda.– Oposición sobre el fondo

Deberán exponerse de forma detallada y sucesiva, con la debida separación en párrafos numerados, las alegaciones fácticas y los argumentos jurídicos relativos a la falta de fundamento de cada una de las infracciones en que se basa el recurso.

Por lo expuesto,

SUPLICO A LA SALA, que teniendo por presentado este escrito junto con sus copias, se sirva admitirlo; y previos los trámites legales oportunos, tenga por formulada en tiempo y forma OPOSICIÓN AL RECURSO DE CASACIÓN interpuesto de contrario contra la Sentencia núm. [Nº] de la Audiencia Provincial de [LOCALIDAD] de fecha [FECHA], y, en virtud de lo alegado, declare la inadmisión del mismo o, con carácter subsidiario, dicte Sentencia desestimando el recurso con expresa condena en costas a la parte recurrente.

[OPCIONAL — incluir si procede]

OTROSÍ DIGO PRIMERO: Que, al amparo de lo establecido en el artículo 485 de la LEC, esta parte hace constar que no considera necesaria la celebración de vista.

SUPLICO A LA SALA: Que tenga por hecha la anterior manifestación a los efectos oportunos.

[OPCIONAL — incluir si procede]

OTROSÍ DIGO SEGUNDO: D./Dña. [NOMBRE Y APELLIDOS], Abogado/a del Ilustre Colegio de la Abogacía de [COMPLETAR], certifico que el presente escrito de oposición consta de [COMPLETAR] folios y un total de [COMPLETAR] caracteres

SUPLICO A LA SALA: Que tenga por hecha la anterior manifestación a los efectos oportunos.

En [LUGAR], a [FECHA].

Abogado/a	Procurador/a

Fdo. D./Dña. [NOMBRE Y APELLIDOS]: 	Fdo. D./Dña. [NOMBRE Y APELLIDOS]:
