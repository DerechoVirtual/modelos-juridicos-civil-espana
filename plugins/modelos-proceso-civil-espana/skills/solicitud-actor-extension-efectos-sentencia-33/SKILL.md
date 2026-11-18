---
name: solicitud-actor-extension-efectos-sentencia-33
description: "Redacta el escrito «Solicitud del actor de extensión de efectos de la sentencia del procedimiento testigo» (formulario 33 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Solicitud del actor de extensión de efectos de la sentencia del procedimiento testigo

> Formulario 0033 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD (4 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] COLEGIO
- [ ] FECHA (9 veces)
- [ ] IMPORTE
- [ ] NÚMERO
- [ ] Nº DE PROCEDIMIENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 18 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…D.»; «…, Procurador de los Tribunales y de D.»; «…, bajo la dirección Letrada de D.»; «…tud de extensión de efectos de sentencia»; «… que me dirijo en autos de juicio verbal»; «…de la sección»; «…, rollo de apelación»; «…euros contra la entidad bancaria»; «…, con sucursal abierta al público en»; «…CHOS PRIMERO.- En autos de juicio verbal»; «…egunda instancia como documentos números»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 438 bis y 519 LEC
- artículo 519 LEC

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

### Formulario 0033 · Solicitud del actor de extensión de efectos de la sentencia del procedimiento testigo

- Año del modelo: 2024
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 41 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de la parte actora, por el que insta la extensión de efectos de la sentencia dictada en el procedimiento testigo, de conformidad con lo previsto en los arts. 438 bis y 519 LEC.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D. [COMPLETAR], Procurador de los Tribunales y de D. [COMPLETAR], mayor de edad, provisto de DNI nº [DNI/NIE], con domicilio en [LOCALIDAD], como acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], bajo la dirección Letrada de D. [COMPLETAR], Colegiado nº [Nº DE COLEGIADO/A] del Ilustre Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco y como más procedente sea en Derecho DIGO:

Que mediante este escrito y en la representación que ostento, de conformidad con lo dispuesto en los arts. 438 bis y 519 LEC, formulo escrito en solicitud de extensión de efectos de sentencia [COMPLETAR], en relación al fallo de la resolución de fecha [FECHA] dictada por el tribunal al que me dirijo en autos de juicio verbal [COMPLETAR], que ha sido confirmada por la sentencia de fecha [FECHA] de la sección [COMPLETAR] de la Audiencia Provincial de [LOCALIDAD], rollo de apelación [COMPLETAR], en solicitud de nulidad de condiciones generales de contratación y accesoria de reclamación de cantidad por la suma de [IMPORTE] euros contra la entidad bancaria [COMPLETAR], con sucursal abierta al público en [COMPLETAR], en base a los siguientes:

HECHOS

PRIMERO.- En autos de juicio verbal [COMPLETAR], se dictó sentencia de fecha [FECHA], confirmada en apelación por sentencia de la Audiencia Provincial de [LOCALIDAD], de fecha [FECHA], en la que se acordó

Se acompañan testimonios de sentencias de primera y segunda instancia como documentos números [COMPLETAR]

SEGUNDO.- Es interés de mi mandante la obtención de la extensión de efectos de la indicada resolución en relación al contrato de fecha [FECHA] y respecto de la condición general de la contratación número [NÚMERO] que es similar a la que se ha declarado nula en la resolución antes expresada.

La condición general que consta declarada nula en la sentencia de fecha [FECHA] cuya extensión de efectos se interesa es la que se transcribe a continuación [COMPLETAR] y, la condición general que consta en el contrato que suscribió mi mandante en fecha [FECHA] con el demandado, es sustancialmente idéntica, cuyo contenido es el siguiente [COMPLETAR], por lo que entiende esta parte que no es preciso realizar un control de transparencia de la cláusula ni valorar la existencia de vicios en el consentimiento del contratante, y que las condiciones generales de contratación cuestionadas tienen identidad sustancial; por lo que es interés del mismo obtener la extensión de efectos de los pronunciamientos de la indicada resolución en la que se acuerda su anulación y, al tiempo, obtener el mismo importe indemnizatorio que se deduce en la misma, referido a

Se adjunta el contrato que vincula a mi mandante con el demandado como documento nº [Nº DE DOCUMENTO]; y en fundamento de la pretensión económica se adjunta como documento números [COMPLETAR] los siguientes documentos justificativos de

TERCERO.- Que el órgano jurisdiccional sentenciador o competente para la ejecución de la sentencia cuyos efectos se pretende extender es también competente territorialmente para conocer de la pretensión de extensión de efectos de la resolución indicada.

A los anteriores hechos son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

ÚNICO.-

De conformidad con lo establecido en el artículo 519 LEC, "sin perjuicio de que se pueda optar por acudir a un procedimiento declarativo, en el caso de las demandas referidas en el artículo 250.1.14.º, los efectos de una sentencia que reconozca una situación jurídica individualizada y que, de haberse dictado en primera instancia, hubiera adquirido firmeza tras haber sido recurrida ante la Audiencia Provincial, podrán extenderse a otras cuando concurran las siguientes circunstancias: a) Que los interesados se encuentren en idéntica situación jurídica que los favorecidos por el fallo. b) Que se trate del mismo demandado, o quien le sucediera en su posición. c) Que no sea preciso realizar un control de transparencia de la cláusula ni valorar la existencia de vicios en el consentimiento del contratante. d) Que las condiciones generales de contratación tengan identidad sustancial con las conocidas en la sentencia cuyos efectos se pretenden extender. e) Que el órgano jurisdiccional sentenciador o competente para la ejecución de la sentencia cuyos efectos se pretende extender fuera también competente, por razón del territorio, para conocer de la pretensión. En estos casos, la solicitud se planteará por medio de escrito en el que se indicará el número de procedimiento en el que se hubiera dictado la sentencia cuyos efectos se pretende extender, la concreta pretensión que podrá ser de anulación, de cantidad o ambas, la identidad de la situación jurídica y un número de cuenta bancaria en la que, eventualmente, puedan realizarse ingresos, acompañando en su caso la documentación en que funde su petición. Esta solicitud deberá formularse en el plazo máximo de un año desde la firmeza de la sentencia cuyos efectos se pretende extender."

Por todo lo expuesto.

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito junto con sus copias, se sirva admitirlo y tener por formulada petición de extensión de efectos de la sentencia de fecha [FECHA] dictada por el tribunal al que me dirijo, en autos de juicio verbal nº [Nº DE PROCEDIMIENTO], que ha sido confirmada por la sentencia de fecha [FECHA] de la sección [COMPLETAR] de la Audiencia Provincial de [LOCALIDAD], rollo [COMPLETAR] y, previos los trámites legales pertinentes, dicte el Tribunal auto por el que se reconozca a mi mandante la indicada extensión de efectos solicitada.

OTROSÍ DIGO:

Que la cuenta corriente de mi representado en la que debe hacerse el ingreso por el condenado del importe indemnizatorio solicitado es [COMPLETAR], por lo que,

AL TRIBUNAL NUEVAMENTE SUPLICO: Que tenga por efectuada la anterior manifestación a los efectos legales oportunos.

Es Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

Firma de Procurador/a
