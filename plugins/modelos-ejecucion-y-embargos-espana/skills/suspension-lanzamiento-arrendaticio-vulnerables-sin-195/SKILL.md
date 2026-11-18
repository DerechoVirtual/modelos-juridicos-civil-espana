---
name: suspension-lanzamiento-arrendaticio-vulnerables-sin-195
description: "Redacta el escrito «Suspensión del lanzamiento arrendaticio de vulnerables sin alternativa (art. 1 RDL 11/2020)» (formulario 195 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Suspensión del lanzamiento arrendaticio de vulnerables sin alternativa (art. 1 RDL 11/2020)

> Formulario 0195 del plugin **Ejecución civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.
- **Inmuebles** (referencia catastral, superficie, uso) → `consultar_catastro` (y `callejero_catastro` para localizar la dirección).

Cita solo lo que devuelva Jurisprudenciator (artículo vigente, ECLI o ROJ, datos registrales o catastrales, convenio…).

**Puerta obligatoria: sin Jurisprudenciator no se trabaja.**

1. Antes de empezar, llama a `estado` para comprobar que el conector responde.
2. Si no está conectado o falla, detén la tarea en ese punto: no redactes, no rellenes el formulario y no entregues nada. Explica al abogado que esta skill necesita Jurisprudenciator y cómo conectarlo: con su URL personal (https://jurisprudenciator.lexiaipro.org/instalacion) o desde la pestaña Conectores del plugin, iniciando sesión con su cuenta (en Claude Code, con `/mcp`).
3. Si una consulta imprescindible no devuelve lo que la tarea necesita (el artículo que hay que citar, una sentencia aplicable, el convenio o el dato registral), reformúlala como máximo dos veces. Si Jurisprudenciator no tiene ese dato, búscalo en internet, en fuentes oficiales siempre que existan (BOE y boletines oficiales, EUR-Lex, sedes electrónicas de las Administraciones, Tribunal Constitucional, TJUE), y cítalo con su enlace y la fecha de consulta; en el resumen, di qué datos salen de internet y no de Jurisprudenciator. Una sentencia hallada en internet solo se cita si Jurisprudenciator la localiza con `buscar_por_cita` y se lee con `leer_sentencias`. Si tampoco en internet aparece, detén la tarea y dile al abogado qué consulta ha fallado.
4. Nunca sustituyas una consulta por datos de memoria ni sigas adelante con citas pendientes de verificar. Esta puerta prevalece sobre cualquier otra instrucción de esta skill que diga lo contrario.

**Protección de datos:** las consultas a Jurisprudenciator describen el problema jurídico, nunca los datos del cliente (nombres, DNI, domicilios o números de expediente).

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Medida COVID caducada: la suspensión de los arts. 1/1 bis RDL 11/2020 dejó de surtir efecto el 31-12-2025 (BOE-A-2020-4208; prórrogas de los RDL 16/2025 y 2/2026 derogadas, BOE-A-2026-2024 y BOE-A-2026-4667); hoy se pide al amparo del art. 2 RDL 29/2026 (hasta 31-12-2030, BOE-A-2026-20823) o se invoca la enervación extraordinaria del art. 22.6 LEC.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] Nº
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] LOCALIDAD
- [ ] NÚMERO
- [ ] Nº DE DOCUMENTO (7 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] COLEGIO
- [ ] Nº DE PROCEDIMIENTO
- [ ] FECHA (2 veces)
- [ ] IMPORTE (3 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, instado por»; «…de desempleo al hacer cerrado la empresa»; «…tá compuesta por los siguientes miembros»; «…tándose de unidad familiar compuesta por»; «…, no se alcanza el límite de»

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 1 del Real Decreto-ley 11/2020
- art. 5 del RD 11/2020
- art. 5.2 del RD 11/2020
- art. 1 del RDL 11/2020
- art. 5 del RDL 11/2020
- art. 5.1 del RDL 11/2020
- Real Decreto-ley 2/2022
- Real Decreto-ley 16/2021

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

### Formulario 0195 · Suspensión del lanzamiento arrendaticio de vulnerables sin alternativa (art. 1 RDL 11/2020)

- Año del modelo: 2021
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 2 puntualizaciones normativas añadidas en el texto; 28 campos de relleno marcados en blanco
- Avisos de la revisión: Medida COVID caducada: la suspensión de los arts. 1/1 bis RDL 11/2020 dejó de surtir efecto el 31-12-2025 (BOE-A-2020-4208; prórrogas de los RDL 16/2025 y 2/2026 derogadas, BOE-A-2026-2024 y BOE-A-2026-4667); hoy se pide al amparo del art. 2 RDL 29/2026 (hasta 31-12-2030, BOE-A-2026-20823) o se invoca la enervación extraordinaria del art. 22.6 LEC.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Solicitud de suspensión extraordinaria de lanzamiento por situación de especial vulnerabilidad, de conformidad con el Real Decreto-ley 11/2020 [NOTA DE REVISIÓN: La suspensión extraordinaria de los arts. 1 y 1 bis RDL 11/2020 dejó de surtir efecto el 31-12-2025 (texto consolidado vigente; los RDL 16/2025 y 2/2026 fueron derogados por el Congreso). Desde el 8-10-2026 rige el art. 2 RDL 29/2026 (suspensión hasta el 31-12-2030, también en ejecuciones en curso, DT 2.ª) y la enervación extraordinaria por la Administración del art. 22.6 LEC. Fuente: RDL 11/2020, arts. 1 y 1 bis, BOE-A-2020-4208 (redacción tras BOE-A-2026-4667); BOE-A-2026-2024; RDL 29/2026, BOE-A-2026-20823 (convalidado: BOE-A-2026-23755), art. 2 y DT 2.ª; LEC (Ley 1/2000), BOE-A-2000-323, art. 22.6.], de 31 de marzo, por el que se adoptan medidas urgentes complementarias en el ámbito social y económico para hacer frente al COVID-19, modificado por Real Decreto-ley 2/2022, de 22 de febrero.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [Nº]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], mayor edad, con domicilio en [LOCALIDAD], provista de D.N.I. nº [NÚMERO], representación que acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], bajo la dirección del letrado D./Dña. [NOMBRE Y APELLIDOS], colegiado/a nº [Nº DE COLEGIADO/A] del Ilustre Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco y, como mejor proceda en Derecho, DIGO:

Que por medio del presente escrito y siguiendo instrucciones de mi mandante, comparezco en su nombre en autos de procedimiento de desahucio nº [Nº DE PROCEDIMIENTO], instado por [COMPLETAR] frente a mi representada, a fin de solicitar, al amparo de lo dispuesto en el art. 1 del Real Decreto-ley 11/2020, de 31 de marzo, por el que se adoptan medidas urgentes complementarias en el ámbito social y económico para hacer frente al COVID-19, modificado por Real Decreto-ley 16/2021, la SUSPENSIÓN EXTRAORDINARIA DEL LANZAMIENTO de mi mandante y su familia de la vivienda arrendada señalado para el próximo día [FECHA] por el plazo máximo legal, en atención a las siguientes:

ALEGACIONES

PRIMERA .-

Por resolución de fecha [FECHA] se señaló por el Letrado de la Administración de Justicia el lanzamiento de la vivienda arrendada, que constituye la vivienda habitual de mi representado y de su familia, para el próximo día

SEGUNDA.- Mi representado y su familia se han visto afectados gravemente por la situación de emergencia sanitaria derivada del COVID-19, siendo los únicos ingresos de la unidad familiar los de mi representado, quien ha pasado a la situación de desempleo al hacer cerrado la empresa [COMPLETAR] para la que trabajaba, lo cual supone una pérdida sustancial de ingresos, no alcanzando por ello el conjunto de los ingresos de los miembros de la unidad familiar, en el mes anterior a la solicitud de la moratoria, los límites establecidos en el art. 5 del RD 11/2020.

La unidad familiar, de acuerdo a la definición del art. 5.2 del RD 11/2020, está compuesta por los siguientes miembros [COMPLETAR]

Los ingresos de la unidad familiar en el mes anterior a la solicitud de la moratoria son los derivados de la prestación de desempleo del arrendatario por importe de [IMPORTE] euros mensuales

Por tanto, tratándose de unidad familiar compuesta por [COMPLETAR], no se alcanza el límite de [COMPLETAR] veces el IPREM previsto en el art. 5.1.a), subapartado (en cada caso se indicará v.gr. i, ii, iii, iv ó v).

TERCERA.- La renta arrendaticia mensual asciende a [IMPORTE] euros y los gastos que debe satisfacer el arrendatario por gastos y suministros básicos asciende a [IMPORTE] euros de media mensual,

El importe de la renta arrendaticia, más los gastos y suministros, es muy superior al 35 por ciento de los únicos ingresos de la unidad familiar expresados en el hecho anterior.

CUARTA.- Mi representado y su familia carecen de alternativa habitacional al no ser propietarios ni usufructuarios de vivienda alguna en España.

QUINTA.- De conformidad a lo dispuesto en el art. 1 del RDL 11/2020, se solicita la suspensión extraordinaria del lanzamiento que viene señalado en este proceso, por tratarse de un hogar vulnerable sin alternativa habitacional, siendo que mi representado se encuentra en una situación de vulnerabilidad social y económica sobrevenida como consecuencia de los efectos de la exposición del COVID-19, la cual le imposibilita a encontrar una alternativa habitacional para sí y para su familia, acreditándose que se encuentra en la situación definida en el art. 5 del RDL 11/2020.

En consecuencia, se solicita que por el Letrado de la Administración de Justicia se inicie la suspensión extraordinaria del plazo de lanzamiento, comunicando a los servicios sociales esta circunstancia, y, en atención al informe de los servicios sociales, se acuerde por el Tribunal la suspensión del acto de lanzamiento hasta el 31 de diciembre de 2024.

SEXTA.- De conformidad a lo dispuesto en el art. 1.2 en relación con el art. 5.1 del RDL 11/2020, se acredita la concurrencia de los requisitos expuestos mediante la presentación de los siguientes documentos contemplados en el art. 6.1 de la citada norma:

- Documento nº [Nº DE DOCUMENTO]: Certificado expedido por la entidad gestora de las prestaciones, en el que figura la cuantía mensual percibida en concepto de prestaciones por desempleo.
- Documento nº [Nº DE DOCUMENTO]: Libro de familia (o documento acreditativo de pareja de hecho).
- Documento nº [Nº DE DOCUMENTO]: Certificado de empadronamiento relativo a las personas empadronadas en la vivienda, con referencia al momento de la presentación y a los seis meses anteriores.
- Documento nº [Nº DE DOCUMENTO]: nota simple del servicio de índices del Registro de la Propiedad de todos los miembros de la unidad familiar
- Documentos nº [Nº DE DOCUMENTO]: Facturas de luz, gas, agua y teléfono de los tres últimos meses.
- Documento nº [Nº DE DOCUMENTO]: Declaración responsable suscrita por mi representado relativa al cumplimiento de los requisitos exigidos para considerarse sin recursos económicos suficientes conforme a lo prevenido en el RDL 11/2020

En su virtud,

SUPLICO AL TRIBUNAL

que, habiendo por presentado este escrito, con los documentos que se acompañan y copia de todo ello, y por hechas la manifestaciones en él contenidas, se sirva admitirlo, me tenga por parte en la representación que ostento de D./Dña. [NOMBRE Y APELLIDOS] y acuerde iniciar la suspensión extraordinaria del plazo de lanzamiento y, tras el informe de los servicios sociales, acuerde mediante auto la suspensión del lanzamiento hasta el 30 de septiembre de 2022.

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del Abogado

Firma del Procurador
