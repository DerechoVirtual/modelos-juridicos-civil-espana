---
name: contestacion-desahucio-extincion-plazo-contractual-406
description: "Redacta el escrito «Contestación al desahucio por extinción del plazo contractual» (formulario 406 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación al desahucio por extinción del plazo contractual

> Formulario 0406 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
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

- Antes de demandar por expiración del plazo, comprobar si el inquilino puede pedir la prórroga extraordinaria de la DF 5.ª RDL 29/2026 (hasta dos años, obligatoria salvo excepciones) o las de los arts. 10.2-10.3 LAU.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO (2 veces)
- [ ] Nº DE DOCUMENTO
- [ ] COLEGIO
- [ ] Nº
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…, con n.º [Nº] de colegiada»; «…sta parte opone la EXCEPCION PROCESAL de»; «… vigencia de la relación contractual (1)»; «…concurrencia de la excepción procesal de»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 9.1 LAU
- art. 394 LEC

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

### Formulario 0406 · Contestación al desahucio por extinción del plazo contractual

- Año del modelo: 2019
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 19 campos de relleno marcados en blanco
- Avisos de la revisión: Antes de demandar por expiración del plazo, comprobar si el inquilino puede pedir la prórroga extraordinaria de la DF 5.ª RDL 29/2026 (hasta dos años, obligatoria salvo excepciones) o las de los arts. 10.2-10.3 LAU.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de contestación a demanda de juicio verbal de desahucio por expiración del término.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD], calle [CALLE], n.º [NÚMERO], representación que debidamente acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], bajo la asistencia de D./Dña. [NOMBRE Y APELLIDOS], Abogada del Ilustre Colegio de Abogados de [COLEGIO], con n.º [Nº] de colegiada [COMPLETAR], ante el Tribunal comparezco y respetuosamente DIGO:

Que siguiendo expresas instrucciones de mi mandante, por medio del presente me persono en los autos de juicio verbal de desahucio /, seguidos en su contra por D./Dña. [NOMBRE Y APELLIDOS], y formulo CONTESTACIÓN A LA DEMANDA.

Con carácter previo esta parte opone la EXCEPCION PROCESAL de [COMPLETAR]
Falta de capacidad de los litigantes o de representación en sus diversas clases
Cosa juzgada o litispendencia
Falta del debido litisconsorcio
Inadecuación del procedimiento
Defecto legal en el modo de proponer la demanda por falta de claridad o precisión en la determinación de las partes o de la petición que se deduzca
Defecto legal en el modo de proponer la reconvención, por falta de claridad o precisión en la determinación de las partes o de la petición que se deduzca
[NOMBRE Y APELLIDOS], con fundamento en las siguientes alegaciones:

Para el supuesto de no estimarse la cuestión procesal alegada, procedemos a contestar la demanda con arreglo a los siguientes hechos y fundamentos legales:

HECHOS

Esta parte niega los hechos alegados en la demanda, excepto los que expresamente se admitan en el presente escrito.

PRIMERO.- De conformidad con el hecho primero de contrario.

SEGUNDO.- De conformidad con el hecho segundo de contrario.

TERCERO.- Se niega expresamente el correlativo de la demanda. Mi mandante ocupa el citado inmueble en virtud de un contrato de arrendamiento de vivienda celebrado con fecha —, estando vigente la relación contractual entre las partes al no haber transcurrido los plazos, convencional y de prórroga, de la vigencia de la relación contractual (1)

[COMPLETAR]

Se acompaña como documento n.º [NÚMERO], original del contrato de arrendamiento.

FUNDAMENTOS DE DERECHO

I.- Se aceptan los fundamentos jurídico-procesales de la demanda reiterando la excepción planteada al inicio de este escrito.

II.- No pueden aceptarse los fundamentos de fondo de la demandante, toda vez que resulta de aplicación la prórroga legal del art. 9.1 LAU 1994 en la redacción dada al mismo por el RDLey 21/2018, de 14 de diciembre, de medidas urgentes en materia de vivienda y alquiler, aplicable a los contratos celebrados a partir de su entrada en vigor, que es lo que acontece en el presente supuesto, a cuyo tenor "La duración del arrendamiento será libremente pactada por las partes. Si esta fuera inferior a cinco años, o inferior a siete años si el arrendador fuese persona jurídica, llegado el día del vencimiento del contrato, este se prorrogará obligatoriamente por plazos anuales hasta que el arrendamiento alcance una duración mínima de cinco años, o de siete años si el arrendador fuese persona jurídica, salvo que el arrendatario manifieste al arrendador, con treinta días de antelación como mínimo a la fecha de terminación del contrato o de cualquiera de las prórrogas, su voluntad de no renovarlo", sin que el arrendador haya notificado fehacientemente al arrendatario su voluntad de no renovar el contrato, una vez transcurrido el plazo de duración inicial mínima.

III.- Por las razones expuestas que determinan la desestimación de la pretensión de la actora, deben imponerse las costas a la demandante, de conformidad con el art. 394 LEC.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que, teniendo por presentado este escrito, tenga por contestada la demanda y previos los trámites legales, se estime la excepción planteada dictando auto que acuerde el sobreseimiento del proceso por la concurrencia de la excepción procesal de [COMPLETAR], o, en su caso, se dicte sentencia desestimatoria de la pretensión de la demanda, con expresa imposición de costas, en todo caso, a la demandante.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) En cada caso, se alegarán las razones por las que se entiende válido el contrato.

========================================================================
