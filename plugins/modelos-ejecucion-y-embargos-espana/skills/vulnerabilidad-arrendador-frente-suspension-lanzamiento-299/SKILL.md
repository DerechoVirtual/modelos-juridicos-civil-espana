---
name: vulnerabilidad-arrendador-frente-suspension-lanzamiento-299
description: "Redacta el escrito «Vulnerabilidad del arrendador frente a la suspensión del lanzamiento (art. 1.4 RDL 11/2020)» (formulario 299 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Vulnerabilidad del arrendador frente a la suspensión del lanzamiento (art. 1.4 RDL 11/2020)

> Formulario 0299 del plugin **Ejecución civil** · revisado el 17-11-2026.

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

- [ ] Nº (2 veces)
- [ ] AÑO
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] FECHA (3 veces)
- [ ] Nº DE DOCUMENTO (8 veces)
- [ ] IMPORTE (2 veces)
- [ ] NÚMERO
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…tá compuesta por los siguientes miembros»; «…tándose de unidad familiar compuesta por»; «…, no se alcanza el límite de»; «…de vulnerabilidad de mi representado. En»

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 1.2 del Real Decreto-ley 11/2020
- art. 5 del RD 11/2020
- art. 5.2 del RD 11/2020
- art. 1.4 del RDL 11/2020
- art. 5 del RDL 11/2020
- art. 150.4 de la LEC
- arts. 5 y 6 del RDL 11/2020

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

### Formulario 0299 · Vulnerabilidad del arrendador frente a la suspensión del lanzamiento (art. 1.4 RDL 11/2020)

- Año del modelo: 2020
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 2 puntualizaciones normativas añadidas en el texto; 21 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº)
- Avisos de la revisión: Medida COVID caducada: la suspensión de los arts. 1/1 bis RDL 11/2020 dejó de surtir efecto el 31-12-2025 (BOE-A-2020-4208; prórrogas de los RDL 16/2025 y 2/2026 derogadas, BOE-A-2026-2024 y BOE-A-2026-4667); hoy se pide al amparo del art. 2 RDL 29/2026 (hasta 31-12-2030, BOE-A-2026-20823) o se invoca la enervación extraordinaria del art. 22.6 LEC.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Procedimiento de desahucio núm. [Nº]/[AÑO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D. /Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D. /Dña. [NOMBRE Y APELLIDOS], según tengo debidamente acreditado en el procedimiento referenciado, ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que mediante el presente escrito y al amparo de lo dispuesto en el art. 1.2 del Real Decreto-ley 11/2020, de 31 de marzo [NOTA DE REVISIÓN: La suspensión extraordinaria de los arts. 1 y 1 bis RDL 11/2020 dejó de surtir efecto el 31-12-2025 (texto consolidado vigente; los RDL 16/2025 y 2/2026 fueron derogados por el Congreso). Desde el 8-10-2026 rige el art. 2 RDL 29/2026 (suspensión hasta el 31-12-2030, también en ejecuciones en curso, DT 2.ª) y la enervación extraordinaria por la Administración del art. 22.6 LEC. Fuente: RDL 11/2020, arts. 1 y 1 bis, BOE-A-2020-4208 (redacción tras BOE-A-2026-4667); BOE-A-2026-2024; RDL 29/2026, BOE-A-2026-20823 (convalidado: BOE-A-2026-23755), art. 2 y DT 2.ª; LEC (Ley 1/2000), BOE-A-2000-323, art. 22.6.], por el que se adoptan medidas urgentes complementarias en el ámbito social y económico para hacer frente al COVID-19, habiendo recibido traslado de la solicitud de la contraparte de suspensión extraordinaria del procedimiento, mediante el presente escrito ALEGO LA SITUACIÓN DE ESPECIAL VULNERABILIDAD de mi representado, en base a los siguientes

HECHOS Y FUNDAMENTOS

PRIMERO .- Por resolución de fecha [FECHA] se fijó la celebración de la vista de este juicio de desahucio para el próximo día [FECHA], habiendo solicitada la parte arrendataria la suspensión extraordinaria del procedimiento de desahucio por escrito presentado en fecha [FECHA], del que se ha dado traslado a esta representación.

SEGUNDO .- Mi representado y su familia se han visto asimismo gravemente afectados por la situación de emergencia sanitaria derivada del COVID-19, siendo los únicos ingresos de la unidad familiar los de mi representado, trabajador por cuenta propia, quien ha pasado a la situación de desempleo al hacer cerrado su bar, el cual era la única fuente de ingresos de la familia, lo cual supone una pérdida total de ingresos, no alcanzando por ello el conjunto de los ingresos de los miembros de la unidad familiar, en el mes anterior a la solicitud de la moratoria, los límites establecidos en el art. 5 del RD 11/2020.

La unidad familiar, de acuerdo a la definición del art. 5.2 del RD 11/2020, está compuesta por los siguientes miembros [COMPLETAR] Acompaño como documentos número [Nº DE DOCUMENTO] libro de familia (o documento acreditativo de pareja de hecho) y certificado de empadronamiento actual con referencia a los seis meses anteriores.

Los ingresos de la unidad familiar en el mes anterior a la solicitud de la moratoria son los derivados de la prestación extraordinaria de desempleo del arrendador por importe de [IMPORTE] euros mensuales, tal como acredito por el certificado expedido por la entidad gestora de las prestaciones que acompaño como documento número

Por tanto, tratándose de unidad familiar compuesta por [COMPLETAR], no se alcanza el límite de [COMPLETAR] veces el IPREM previsto en el art. 5.1.a), subapartado (en cada caso se indicará v.gr. i, ii, iii, iv ó v).

TERCERO.- Mi representado está viviendo en un piso de alquiler, donde satisface una renta arrendaticia mensual de [IMPORTE] euros y los gastos que debe satisfacer el arrendatario por gastos y suministros básicos asciende a ….. euros de media mensual, según se acredita con los documentos acompañados como número [NÚMERO] consistentes en los tres últimos recibos de renta y las tres últimas facturas de luz, gas, agua y teléfono.

El importe de la renta arrendaticia, más los gastos y suministros, es muy superior al 35 por ciento de los únicos ingresos de la unidad familiar expresados en el hecho anterior.

CUARTO.- La vivienda arrendada es la única alternativa habitacional de que dispone en este momento la familia, al no ser propietarios ni usufructuarios de vivienda alguna en España, tal como se acredita por la nota simple del servicio de índices del Registro de la Propiedad de todos los miembros de la unidad familiar, que se acompaña como documento número [Nº DE DOCUMENTO].

QUINTO.- De conformidad a lo dispuesto en el art. 1.4 del RDL 11/2020, se solicita que no se dé lugar a la suspensión extraordinaria del lanzamiento, puesto que la persona arrendataria lleva un total de [Nº] meses sin satisfacer la renta arrendaticia, siendo totalmente injusto que mi representado se vea privado de este ingreso y de la vivienda de su propiedad, en tanto que su hogar es igualmente vulnerable sin alternativa habitacional, siendo que mi representado ha perdido totalmente su fuente de ingresos como consecuencia de los efectos de la exposición del COVID-19, acreditándose que se encuentra en la situación definida en el art. 5 del RDL 11/2020, y aportándose los documentos indicados en el art. 6 del citado RDL 11/2020, consistentes en la documentación ya expresada anteriormente y la declaración responsable prevenida en el art. 6.1.e) de mi representado relativa al cumplimiento de los requisitos exigidos para considerarse sin recursos económicos suficientes conforme a lo prevenido en el RDL 11/2020.

En consecuencia, se solicita que por el Letrado de la Administración de Justicia, y tras comunicar a los servicios sociales esta circunstancia, a cuyo efecto mi representado presta consentimiento expreso de acuerdo a lo establecido en el art. 150.4 de la LEC y que se dicte auto en el que se desestime la suspensión extraordinaria del plazo de lanzamiento solicita por el inquilino o, subsidiariamente, se fije un plazo no superior a un mes.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y copia de todo ello, lo admita y, tras los trámites legales, acuerde desestimar la suspensión extraordinaria del plazo de lanzamiento en este procedimiento de desahucio.

OTROSÍ DIGO que, de conformidad a lo dispuesto en el art. 1.2 en relación con los arts. 5 y 6 del RDL 11/2020 acompaño los siguientes documentos:

-Documentos número [Nº DE DOCUMENTO]: Certificado de la AEAT de cese de actividad y certificado expedido por la entidad gestora de las prestaciones, en el que figura la cuantía mensual percibida en concepto de prestaciones por desempleo.

- Documento número [Nº DE DOCUMENTO]: Libro de familia (o documento acreditativo de pareja de hecho).

- Documento número [Nº DE DOCUMENTO]: Certificado de empadronamiento relativo a las personas empadronadas en la vivienda, con referencia al momento de la presentación y a los seis meses anteriores.

- Documento número [Nº DE DOCUMENTO]: nota simple del servicio de índices del Registro de la Propiedad de todos los miembros de la unidad familiar.

- Documento número [Nº DE DOCUMENTO]: Declaración responsable del arrendatario relativa al cumplimiento de los requisitos exigidos para considerarse sin recursos económicos suficientes según el RDL 11/2020.

- Documentos número [Nº DE DOCUMENTO]: Recibos de alquiler, facturas de luz, gas, agua y teléfono de los tres últimos meses.

Por lo que, AL TRIBUNAL SUPLICO tenga por acompañados estos documentos a efectos de acreditar la situación de vulnerabilidad de mi representado.

En [COMPLETAR] L. y F.

 Firma de procurador

 Firma de abogado
