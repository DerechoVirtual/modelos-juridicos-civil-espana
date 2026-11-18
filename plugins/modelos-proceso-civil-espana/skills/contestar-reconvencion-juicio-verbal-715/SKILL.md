---
name: contestar-reconvencion-juicio-verbal-715
description: "Redacta el escrito «Contestar la reconvención en juicio verbal» (formulario 715 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestar la reconvención en juicio verbal

> Formulario 0715 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] IMPORTE
- [ ] FECHA
- [ ] Nº DE DOCUMENTO
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 438.2 de la LEC
- art. 406.1 LEC

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

### Formulario 0715 · Contestar la reconvención en juicio verbal

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 6 campos de relleno marcados en blanco; 4 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Juicio verbal núm. [Nº DE PROCEDIMIENTO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D. [NOMBRE Y APELLIDOS] Procurador de los Tribunales, actuando en representación de la parte demandante D. [NOMBRE Y APELLIDOS], según tengo acreditado en autos de juicio verbal arriba referenciados, comparezco y como mejor proceda en derecho DIGO:

Que habiendo recibido traslado de la demanda reconvencional interpuesta contra mi principal por el demandado D. [NOMBRE Y APELLIDOS], paso a formular escrito de CONTESTACIÓN A LA RECONVENCIÓN, dentro del plazo establecido en el art. 438.2 de la LEC, en base a los siguientes:

HECHOS

Se niegan todos los hechos expuestos en la demanda reconvencional a excepción de los que se vean aceptados en la presente contestación.

Con carácter previo, se alega como excepción la de inadmisibilidad de la acción ejercitada en vía de reconvención, ya que el demandante reconvencional reclama frente a mi principal una cantidad de [IMPORTE] euros en base a un contrato de obra de fecha [FECHA] que carece de cualquier conexión con la acción que se ejercita dirigida a reclamar por culpa extracontractual derivada del accidente de tráfico que se produjo entre el vehículo de mi representado y del demandado, por lo que no se cumplen los requisitos del art. 406.1 LEC.

En cuanto al fondo de la reclamación que se ha formulado se niegan las deficiencias en la instalación de las persianas de la vivienda que efectuó mi representado, puesto que el trabajo fue recibido a satisfacción del ahora demandante reconvencional y los defectos que describe se deben a una mala conservación de los motores elevadores, con toda seguridad por no haber seguido las instrucciones que le fueron suministradas.

A tal efecto y como documentos nº [Nº DE DOCUMENTO] se aportan hoja de recepción, fotografías de la instalación y manual de mantenimiento que le fue entregado al demandante y donde constan las tareas de conservación requeridas para el correcto funcionamiento de las persianas automáticas.

Es por ello que se niega la existencia de ningún tipo de incumplimiento por mi mandante solicitando que la demanda reconvencional sea desestimada.

FUNDAMENTOS DE DERECHO

Se acepta la competencia y tramitación por el juicio verbal por aplicación del art. 438.2 de la LEC, sin perjuicio de lo que se dirá en relación a la improcedencia de la acción ejercitada.

Excepción de inadmisibilidad de la reconvención

No resulta admisible la acción ejercitada por vía de reconvención puesto que no hay conexión entre la demanda principal y la pretensión reconvencional, y por ello no se cumplen los requisitos del art. 406.1 LEC cuando dispone: “Al contestar a la demanda, el demandado podrá, por medio de reconvención, formular la pretensión o pretensiones que crea que le competen respecto del demandante. Sólo se admitirá la reconvención si existiere conexión entre sus pretensiones y las que sean objeto de la demanda principal”.

Fondo de la reclamación

Se estima no imputable a mi mandante las deficiencias que se invocan en la reconvención con lo que ningún tipo de incumplimiento contractual se le puede achacar con fundamento en el art 1.100 CC.

En materia de costas el art 394 LEC.

En base a lo anterior,

SUPLICO AL TRIBUNAL que tenga por presentado este escrito con resguardo acreditativo de traslado, teniendo por contestada la reconvención formulada frente a mi principal y tras la pertinente tramitación se sirva estimar la excepción invocada acordando la inadmisión de la reconvención o, subsidiariamente, la desestime, todo ello con imposición de costas al demandante reconvencional.

 a [DÍA] de [MES] de [AÑO]

Firma Abogado y Procurador

========================================================================
