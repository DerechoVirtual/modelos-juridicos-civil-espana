---
name: comparecencia-adopcion-pidiendo-reconocer-necesidad-846
description: "Redacta el escrito «Comparecencia en la adopción pidiendo reconocer la necesidad de asentimiento» (formulario 846 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Comparecencia en la adopción pidiendo reconocer la necesidad de asentimiento

> Formulario 0846 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] AÑO (2 veces)
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] CALLE
- [ ] NÚMERO (2 veces)
- [ ] COLEGIO
- [ ] Nº
- [ ] LUGAR
- [ ] DÍA
- [ ] MES DE
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, con n.º [Nº] de colegiado»; «…n el procedimiento de adopción del menor»; «…e Tribunal bajo el número de actuaciones»; «…ESIDAD DE ASENTIMIENTO EN LA ADOPCIÓN DE»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 781.1 LEC

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

### Formulario 0846 · Comparecencia en la adopción pidiendo reconocer la necesidad de asentimiento

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; saltos de párrafo recuperados (texto venía pegado); restos de formato retirados; 11 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de comparecencia ante el Tribunal que está conociendo del expediente solicitando que se reconozca la necesidad de su asentimiento para la adopción.

Documento adaptado a la reforma orgánica de la LO 1/2025. A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA [NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).] DE [LOCALIDAD], PLAZA N.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] AUTOS N.º [Nº DE PROCEDIMIENTO]/[AÑO] D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre de D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD], calle [CALLE], n.º [NÚMERO], provisto de D.N.I. n.º [NÚMERO], representación que debidamente acredito con la copia de escritura de poder que se acompaña a la presente, bajo la asistencia del Letrado del Ilustre Colegio de Abogados de [COLEGIO], D./Dña. [NOMBRE Y APELLIDOS], con n.º [Nº] de colegiado [COMPLETAR], ante el Tribunal comparezco y como mejor proceda en Derecho, DIGO:Que siguiendo expresas instrucciones de mi mandante, y de conformidad con lo previsto en el artículo 781.1 LEC, por medio del presente escrito manifiesto que es intención de esta representación que se RECONOZCA LA NECESIDAD DE ASENTIMIENTO en el procedimiento de adopción del menor [COMPLETAR] tramitada en este Tribunal bajo el número de actuaciones [COMPLETAR] por lo que se SOLICITA QUE SE LE EMPLACE PARA PRESENTAR LA PERTINENTE DEMANDA CON SUSPENSIÓN DE LAS ACTUACIONES.En virtud de lo expuesto,

SUPLICO AL TRIBUNAL:Que tenga por presentado este escrito, con sus copias, y por hechas las manifestaciones que contiene, se sirva admitirlo, teniéndome por comparecido y por formulada INTENCIÓN DE INICIAR PROCEDIMIENTO PARA QUE SE RECONOZCA LA NECESIDAD DE ASENTIMIENTO EN LA ADOPCIÓN DE [COMPLETAR] EMPLAZÁNDOSE POR EL SR. LAJ A ESTA PARTE PARA PRESENTAR LA PERTINENTE DEMANDA, extremo que se acordará por Decreto que suspenderá la tramitación de este procedimiento.

Es Justicia que pido en [LUGAR], a [DÍA], de [MES DE] [AÑO]

Firma de Abogado/a

Firma de Procurador/a

========================================================================
