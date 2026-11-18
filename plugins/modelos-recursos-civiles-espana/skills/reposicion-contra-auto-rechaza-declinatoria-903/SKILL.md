---
name: reposicion-contra-auto-rechaza-declinatoria-903
description: "Redacta el escrito «Reposición contra el auto que rechaza la declinatoria» (formulario 903 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición contra el auto que rechaza la declinatoria

> Formulario 0903 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] SEDE
- [ ] Nº
- [ ] FECHA DEL AUTO (2 veces)
- [ ] FECHA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 452 de la LEC

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

### Formulario 0903 · Reposición contra el auto que rechaza la declinatoria

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 2 campos de relleno marcados en blanco; 4 huecos del original que se habían perdido sin marca, marcados (FECHA, FECHA DEL AUTO, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio (ordinario o verbal) n.º [Nº DE PROCEDIMIENTO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [Nº]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña Procurador de los Tribunales, actuando en nombre de D./Dña, demandado en los presentes Autos, representación que consta debidamente acreditada en los autos referenciados, ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que mediante Auto de fecha [FECHA DEL AUTO], notificado a esta parte el día [FECHA], se acordó rechazar la declinatoria por falta de competencia objetiva (detallar motivo: 1. falta de competencia internacional, 2. pertenencia del asunto a otro orden jurisdiccional o 3. sumisión a arbitraje) formulada a instancia de mi representado.

Dentro del plazo legal de cinco días previsto en el art. 452 de la LEC, mediante el presente escrito formulo contra el expresado Auto RECURSO DE REPOSICIÓN, formulando las siguientes

ALEGACIONES

A los efectos previstos en el art. 452 de la LEC denuncio la infracción del (detallar precepto/s que se considera/n infringido/s), según se razona en la fundamentación jurídica de este recurso.

No se ha tomado en consideración a la hora de dictar el auto mediante el que se rechaza la declinatoria la circunstancia (desarrollar motivos del recurso).

Son de aplicación los siguientes preceptos:

I. Art. 66 de la LEC, que establece, que «contra el auto por el que se rechace la falta de competencia internacional, de jurisdicción o de competencia objetiva, sólo cabrá recurso de reposición».

II. Arts. 451 a 454 de la LEC que regulan los requisitos, plazo y forma de interposición, tramitación y efectos del Recurso de Reposición.

III. Se cita como precepto infringido por la resolución recurrida Efectivamente la Juris- prudencia ha venido interpretando (desarrollar alegaciones que justifiquen la infracción con cita de apoyo legal y jurisprudencial).

IV. (desarrollar los restantes apoyos legales y jurisprudenciales en que se sustente la pretensión).

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito, se sirva admitirlo y, en su virtud, tenga por formulado en tiempo y forma RECURSO DE REPOSICIÓN contra el Auto de fecha [FECHA DEL AUTO] mediante el que se rechaza la declinatoria planteada por esta parte por falta de competencia objetiva (detallar motivo: 1. falta de competencia internacional, 2. pertenencia del asunto a otro orden jurisdiccional o

3. sumisión a arbitraje), y en virtud de las alegaciones aducidas, y previa la tramitación oportuna con audiencia de las partes por plazo común de cinco días, reponga la resolución recurrida, dictando nuevo auto mediante el que, estimando este Recurso, acuerde abstenerse de conocer del presente asunto, sobreseyendo el proceso y señalando que la parte actora ha de usar su derecho (ante el órgano o mediante arbitraje).

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

OTROSÍ DIGO: Que acompaño justificante de ingreso en la cuenta del Tribunal de la cantidad de 25 euros como depósito para recurrir.

NUEVAMENTE SUPLICO: Que se tenga por hecho el citado depósito, por ser justicia que pido en mismo lugar y fecha.

========================================================================
