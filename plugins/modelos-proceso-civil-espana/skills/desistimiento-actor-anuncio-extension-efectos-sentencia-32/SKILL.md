---
name: desistimiento-actor-anuncio-extension-efectos-sentencia-32
description: "Redacta el escrito «Desistimiento del actor y anuncio de extensión de efectos de la sentencia del procedimiento testigo» (formulario 32 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Desistimiento del actor y anuncio de extensión de efectos de la sentencia del procedimiento testigo

> Formulario 0032 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] DNI/NIE
- [ ] LOCALIDAD (2 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] COLEGIO
- [ ] FECHA (7 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NÚMERO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…D.»; «…, Procurador de los Tribunales y de D.»; «…, según tengo acreditado en autos»; «…, bajo la dirección Letrada de D.»; «…de la sección»; «…, rollo de apelación»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 20.2 LEC
- art. 438 bis.3 LEC
- art. 483 bis.4 LEC

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

### Formulario 0032 · Desistimiento del actor y anuncio de extensión de efectos de la sentencia del procedimiento testigo

- Año del modelo: 2024
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 22 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de la parte actora, por el que insta el desistimiento del procedimiento y anuncia que solicitará la extensión de efectos de la sentencia dictada en el procedimiento testigo, de conformidad con lo previsto en el art. 20.2, 438 bis.3 y 519 LEC.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D. [COMPLETAR], Procurador de los Tribunales y de D. [COMPLETAR], mayor de edad, provisto de DNI nº [DNI/NIE], con domicilio en [LOCALIDAD], según tengo acreditado en autos [COMPLETAR], bajo la dirección Letrada de D. [COMPLETAR], Colegiado nº [Nº DE COLEGIADO/A] del Ilustre Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco y como más procedente sea en Derecho DIGO:

Que mediante providencia de fecha [FECHA], notificada a esta parte en fecha [FECHA], se me confiere plazo de cinco días al objeto de pronunciarme en relación a la forma de continuar los presentes autos y, por el presente escrito, en la representación que acredito y dentro del plazo de cinco días conferido formulo solicitud de desistimiento unilateral del proceso y ya dejo adelantado que es interés de mi mandante SOLICITAR LA EXTENSIÓN DE EFECTOS DE LA SENTENCIA DICTADA EN EL PROCEDIMIENTO TESTIGO de conformidad con lo previsto en los arts. 20.2, 438 bis.3 y 519 LEC; todo ello con base en las siguientes

ALEGACIONES

PRIMERA.- Que las presentes actuaciones tuvieron inicio en virtud de demanda de juicio verbal de fecha [FECHA] en ejercicio de acción individual de nulidad de condiciones generales de contratación y accesoria de reclamación de cantidad, interpuesta por el/ Procurador de los Tribunales D. [NOMBRE Y APELLIDOS] en nombre y representación de D. [NOMBRE Y APELLIDOS] contra la entidad

SEGUNDA.- Que previa la tramitación legal correspondiente, por auto de fecha [FECHA] se acordó la suspensión del curso de las actuaciones hasta la resolución definitiva del procedimiento testigo relativo al juicio verbal número [NÚMERO] seguido ante ese mismo tribunal, por ser idénticas las pretensiones en el mismo deducidas y seguidas que las que se suscitaban por mi mandante en los presentes autos.

TERCERA.- Que en fecha [FECHA] se nos ha notificado la resolución definitiva del procedimiento testigo antes identificado de fecha [FECHA], que ha sido confirmada por la sentencia de fecha [FECHA] de la sección [COMPLETAR] de la Audiencia Provincial de [LOCALIDAD], rollo de apelación [COMPLETAR], en ejercicio de acción individual de nulidad de condiciones generales de contratación y accesoria de reclamación de cantidad, que es sustancialmente la misma pretensión ejercitada por mi mandante, por lo que mi mandante no tiene interés en la continuación de los presentes autos, sin perjuicio de que se deje ya adelantado que sí es interés de mi mandante personarse en el procedimiento testigo al objeto de interesar en el mismo la extensión de efectos de la indicada sentencia, en su beneficio.

CUARTA.- Que establece el art. 20.2 LEC que el demandante podrá desistir unilateralmente del juicio antes de que el demandado sea emplazado para contestar a la demanda o citado para juicio.

QUINTA.- Que conforme al art. 438 bis.3 LEC, "una vez adquiera firmeza la sentencia dictada en el procedimiento testigo, el tribunal dictará providencia en la que indicará si considera procedente o no la continuación del procedimiento suspendido instado, por haber sido resueltas o no todas las cuestiones planteadas en él en la sentencia del procedimiento testigo, relacionando aquellas que considere no resueltas y dando traslado al demandante del procedimiento suspendido para que en cinco días solicite: a) El desistimiento en sus pretensiones (...) c) La extensión de los efectos de la sentencia dictada en el procedimiento testigo."; y según lo dispuesto en el art. 483 bis.4 LEC, "en caso de desistimiento, el letrado o letrada de la Administración de Justicia dictará decreto acordando el mismo, sin condena en costas."

Por lo expuesto,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito junto con sus copias, se sirva admitirlo y, previos los trámites legales, proceda a dictarse por LAJ resolución por la que acuerde el sobreseimiento y archivo de las actuaciones interesadas con reserva expresa de esta parte del derecho a promover nuevo juicio sobre el mismo objeto sin condena en costas.

Es Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

Firma de Procurador/a
