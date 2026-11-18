---
name: solicitud-amparo-colegio-abogacia-letrado-54
description: "Redacta el escrito «Solicitud de amparo al colegio de la abogacía por un letrado» (formulario 54 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Solicitud de amparo al colegio de la abogacía por un letrado

> Formulario 0054 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] COLEGIO (2 veces)
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] CORREO ELECTRÓNICO
- [ ] SEDE (3 veces)
- [ ] NÚMERO (4 veces)
- [ ] FECHA (3 veces)
- [ ] Nº
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ue me dirijo, con el número de colegiado»; «…numeración del juzgado de procedencia).]»; «…probar esta intervención desde el minuto»; «…, hasta el minuto»; «…probar esta intervención desde el minuto»; «…, hasta el minuto»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Ley Orgánica 3/2018

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

### Formulario 0054 · Solicitud de amparo al colegio de la abogacía por un letrado

- Año del modelo: 2023
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 28 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA JUNTA DE GOBIERNO DEL ILTRE. COLEGIO DE ABOGADOS DE [COLEGIO]

D./Dª [NOMBRE Y APELLIDOS], Abogado/a del Iltre. Colegio al que me dirijo, con el número de colegiado [COMPLETAR], con domicilio profesional en [LOCALIDAD], y con correo electrónico [CORREO ELECTRÓNICO], por medio del presente escrito solicita AMPARO COLEGIAL, con fundamento en los siguientes:

MOTIVOS

PRIMERO:- Se insta el amparo colegial, conforme a lo establecido en el art. 58 del Estatuto General de la Abogacía, al considerar el profesional que suscribe que la actuación de D/Dª [NOMBRE Y APELLIDOS], juez de la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], en el juicio verbal número [NÚMERO], celebrado el día [FECHA] a las [Nº] horas, ha coartado la independencia y libertad necesarias para cumplir con mis deberes profesionales, y ha sido desconsiderada con la función que desempeño, lo cual ya se hizo constar en el acto del juicio y de lo que se da cuenta a la Junta de Gobierno, según el relato de hechos que expongo a continuación, para que se adopten las medidas necesarias en amparo de la libertad, independencia y dignidad profesionales.

SEGUNDO.- El juicio verbal que origina la petición de amparo estaba señalado a las 10.30 horas, estando precedido de dos vistas anteriores a las 9.30 y 10.00 horas en el mismo Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO].

El juez se presentó a las 11.00 horas, siendo conocida su sistemática impuntualidad, lo cual viene originando generalizados retrasos en el Tribunal, lo cual se pretende compensar por dicho juez con una actitud de constante apremio e intolerancia para cuantos intervienen en los distintos actos procesales, según es notorio.

Tras celebrar los dos juicios anteriores, a las 12.15 horas se inició el juicio verbal en el que quien suscribe asistía como letrado de la parte demandante, asistiendo el letrado D/Dª [NOMBRE Y APELLIDOS], como defensa de la parte demandada, así como sus respectivos procuradores.

Antes de empezar el juicio, el juez, con muy malos modos, conminó a ambos letrados a que llegaran a un acuerdo, manifestando literalmente a esta parte que “no le voy a estimar más de 2.000 euros de lo que pide” e indicándole que “más le vale conciliar, no sea cosa que lo pierda todo”. Ante la queja de este abogado por dicha actitud, el juez le ordenó que enumerara los medios de prueba de que se iba a valer, manifestando esta parte que iba a solicitar la testifical de tres personas, documental y pericial, ante lo cual el juez le dijo que no iba a admitir ninguna testifical ni pericial, por lo que me indicó que debía abstenerme de proponerlas, a lo que el letrado que suscribe le manifestó que se reservaba su derecho a proponer la prueba en el momento oportuno.

Tras iniciarse el juicio, y tal como consta en la grabación, el juez manifestó su desagrado con que no hubiera acuerdo y, tras la proposición de la prueba por esta parte, manifestó textualmente lo siguiente: “señor letrado, no se ha enterado de que le he dicho que no le iba a admitir la testifical y la pericial, pues se la inadmito por impertinente”. Ante ello, el que suscribe manifestó su voluntad de interponer recurso de reposición, a lo que el juez le dijo: “no le admito ningún recurso, señor letrado, porque carece de fundamento” (acompaño grabación del juicio, donde se puede comprobar esta intervención desde el minuto [COMPLETAR], hasta el minuto [COMPLETAR]).

Tras desarrollarse el juicio, donde el juez observó una actitud totalmente autoritaria y destemplada, según se constata del visionado de la grabación y, llegada la fase de conclusiones, concedió dos minutos a cada uno de los letrados. Al empezar la exposición este letrado con la queja por la situación de indefensión generada, el juez cortó las conclusiones y le retiró la palabra al letrado que suscribe, gritando “no toleraré ofensas a este tribunal” (en la grabación del juicio acompañada, se puede comprobar esta intervención desde el minuto [COMPLETAR], hasta el minuto [COMPLETAR]).

TERCERO.- Ante el grave atentado a la dignidad profesional y al ejercicio del derecho de defensa, y sin perjuicio de impugnar por la vía procesal correspondiente las resoluciones dictadas en el citado proceso, me veo en la obligación de solicitar amparo colegial, en aras de la garantía en el ejercicio del derecho de defensa, solicitando que se declare que el juez D/Dª [NOMBRE Y APELLIDOS] ha coartado la independencia y libertad del abogado que suscribe y no ha guardado la consideración debida a su función, instando a que se formule denuncia por estos hechos ante el Consejo General del Poder Judicial y la Sala de Gobierno del Tribunal Superior de Justicia de [LOCALIDAD], así como que se adopten cualesquiera otras medidas que estime oportunas en defensa del ejercicio profesional.

Por todo lo expuesto,

SOLICITO A LA JUNTA DE GOBIERNO que, previos los trámites legales, conceda el AMPARO al abogado/a que suscribe, declarando que el/la juez D/Dª [NOMBRE Y APELLIDOS] ha coartado la independencia y libertad del abogado/a que suscribe y no ha guardado la consideración debida a su función en el acto del juicio verbal celebrado el pasado día [FECHA], instando a que se formule denuncia por esta conducta ante el Consejo General del Poder Judicial y la Sala de Gobierno del Tribunal Superior de Justicia de [LOCALIDAD], y que se adopten cualesquiera otras medidas que la Junta de Gobierno estime oportunas en defensa del ejercicio profesional.

OTROSÍ PRIMERO DIGO que acompaño grabación del acto del juicio verbal número [NÚMERO], celebrado el pasado día [FECHA] ante la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO].

OTROSÍ SEGUNDO DIGO que, de conformidad con la Ley Orgánica 3/2018, de Protección de Datos Personales y garantía de los derechos digitales, y en cumplimiento del RGPD concedo autorización expresa al Servicio correspondiente del Colegio de Abogados de [COLEGIO] para el examen, tratamiento, cesión y utilización de los datos y documentos físicos y digitales aportados para gestionar la solicitud planteada, manifestando que dichos datos y documentos son veraces.

En (Lugar y fecha).

Firma del solicitante
