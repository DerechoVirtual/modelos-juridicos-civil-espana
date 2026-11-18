---
name: recurso-queja-inadmision-apelacion-1048
description: "Redacta el escrito «Recurso de queja por inadmisión de la apelación» (formulario 1048 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Recurso de queja por inadmisión de la apelación

> Formulario 1048 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] NÚMERO (7 veces)
- [ ] SEDE (3 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] FECHA (6 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Juicio»; «…, plaza n.º»; «…A LA SALA»; «…mediante el que se acuerda»; «…, mediante la/el que se acordaba»; «…ético incumplimiento de la obligación de»; «…Sin embargo»; «…, dictada en los autos de juicio»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 495 de la LEC
- art. 494 de la LEC

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

### Formulario 1048 · Recurso de queja por inadmisión de la apelación

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 29 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio [COMPLETAR] (ordinario o verbal), n.º [NÚMERO]

Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [COMPLETAR]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

A LA SALA [COMPLETAR] DE LA AUDIENCIA PROVINCIAL DE [LOCALIDAD]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], en virtud de la representación que acredito mediante la escritura de apoderamiento que en debida forma acompaño y cuya devolución intereso previo su testimonio en autos, ante la Sala comparezco y como mejor proceda en derecho DIGO:

Que dentro del plazo legal y amparándome en lo dispuesto en el art. 495 de la LEC, mediante el presente escrito interpongo el RECURSO DE QUEJA contra el auto de fecha [FECHA] mediante el que se deniega la admisión del recurso de apelación formulado contra la sentencia n.º [NÚMERO] de fecha [FECHA] dictada en el presente procedimiento (o el auto de fecha [FECHA] mediante el que se acuerda [COMPLETAR])

Señalo, con carácter previo al desarrollo de las alegaciones en que se funda este recurso de queja, los siguientes

ANTECEDENTES Y PRESUPUESTOS PREVIOS

I. En el proceso que se deja referenciado en el encabezamiento de este escrito se dictó por la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO], la sentencia n.º [NÚMERO] (auto), de fecha [FECHA], mediante la/el que se acordaba [COMPLETAR] Acompaño copia de la mencionada resolución reseñada como doc. n.º 1.

II. En tiempo y forma y cumpliendo los requisitos legales interpuse recurso de apelación contra ella, declarándose su inadmisión por auto de fecha [FECHA], cuya copia acompaño y que es objeto del presente recurso.

Interpongo este recurso dentro de plazo legal de diez días siguientes a la notificación del auto recurrido señalado en el art. 495 de la LEC, y acompaño justificante del depósito para recurrir, según exige la disposición adicional decimoquinta de la LOPJ.

III. Será competente para conocer este recurso de queja la Sala de la Audiencia Provincial de [LOCALIDAD], a que me dirijo como Tribunal competente para conocer el recurso no tramitado (art. 494 de la LEC).

Formulo para impugnar la resolución recurrida las siguientes

ALEGACIONES

PRIMERA.—La resolución recurrida aduce, para fundamentar la inadmisión del recurso de apelación, un hipotético incumplimiento de la obligación de [COMPLETAR] Sin embargo [COMPLETAR] (desarrollar las alegaciones pertinentes para combatir las causas por las que se deniega la admisión de la preparación, presentando los documentos que acrediten las alegaciones).

Por lo expuesto,

SUPLICO A LA SALA: Que tenga por presentado este escrito con sus copias preceptivas, se sirva admitirlo y, en su virtud dicte resolución mediante la que, estimando íntegramente este recurso, se revoque la resolución recurrida y se acuerde ordenar a la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO], que declare la admisión del recurso de apelación interpuesto contra la sentencia n.º [NÚMERO] de fecha [FECHA], dictada en los autos de juicio [COMPLETAR] n.º [NÚMERO], y continúe con la tramitación de dicho recurso.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
