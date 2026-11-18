---
name: contestacion-oponiendo-falta-legitimacion-pasiva-428
description: "Redacta el escrito «Contestación oponiendo falta de legitimación pasiva» (formulario 428 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación oponiendo falta de legitimación pasiva

> Formulario 0428 del plugin **Sucesiones** · revisado el 17-11-2026.

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

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (8 veces)
- [ ] Nº DE DOCUMENTO
- [ ] FECHA (4 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] MARCA/MODELO (2 veces)
- [ ] MATRÍCULA
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…, con despacho profesional en»; «…, se aportan los documentos números»; «…a»; «…rita por mi principal y el citado Sr./a.»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 405.3 LEC
- arts. 10 LEC
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

### Formulario 0428 · Contestación oponiendo falta de legitimación pasiva

- Año del modelo: 2018
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 22 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Contestación a la demanda de juicio ordinario oponiendo falta de legitimación pasiva.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a /a de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante escritura de poder inscrito en el Registro Electrónico de Apoderamientos Judiciales, a cuya justificación aporto certificación de dicho Registro como documento nº [Nº DE DOCUMENTO], dirigida por el/la Letrado/a abajo firmante D./Dña. [NOMBRE Y APELLIDOS], con despacho profesional en [COMPLETAR], ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que con fecha [FECHA] del presente se ha procedido al emplazamiento de mi mandante en autos de Juicio Ordinario n.º [Nº DE PROCEDIMIENTO]/[AÑO], seguidos ante ese Tribunal a instancia de D./Dña. [NOMBRE Y APELLIDOS], por cuanto, mediante el presente escrito, procedo a contestar a la demanda, con el solo efecto de oponer la FALTA DE LEGITIMACION PASIVA, con base en los siguientes:

HECHOS

ÚNICO.-

En la fecha del siniestro mi mandante no era propietario ni conductor del vehículo causante de los daños marca [MARCA/MODELO], modelo [MARCA/MODELO], matrícula [MATRÍCULA], por haberlo vendido a D./Dña. [NOMBRE Y APELLIDOS]

A fin de acreditar la referida falta de titularidad, y sin perjuicio de dejar designado a efectos probatorios el archivo de la Jefatura Provincial de Tráfico de [LOCALIDAD], se aportan los documentos números [COMPLETAR] a [COMPLETAR] consistentes en:

a) contrato privado de compraventa de fecha [FECHA].
b) Copia del D.N.I. del titular del vehículo D./Dña. [NOMBRE Y APELLIDOS], obtenida con motivo del trámite de compraventa.
c) copia del impreso de traspaso, con validación mecánica del pago efectuado el día [FECHA], de la venta del vehículo suscrita por mi principal y el citado Sr./a. [COMPLETAR].

FUNDAMENTOS JURIDICOS

I.- Se aceptan los fundamentos jurídico-procesales de la demanda reiterando la excepción planteada al inicio de este escrito.

Se opone la falta de legitimación pasiva de mi representado al amparo de lo dispuesto en el art. 405.3 LEC, por no ser el conductor del vehículo causante de los daños y perjuicios reclamados de adverso.

En efecto, mi mandante D./Dña. [NOMBRE Y APELLIDOS], carece de legitimación pasiva para soportar la acción ejercitada, a partir de una interpretación contrario sensu de los arts. 10 LEC y 1 LRCSCVM, por cuanto no es responsable de los hechos que le atribuye el demandante, como queda demostrado con la lectura de los hechos que se recoge en esta demanda.

II.- Esta parte no puede entrar en el fondo del asunto toda vez que desconoce en absoluto los hechos alegados por la demandante, por hallarse, como se ha expuesto, el día del accidente desvinculado del vehículo causante de los daños.

III.- Por las razones expuestas que determinan la desestimación de la pretensión de la actora, deben imponerse las costas a la demandante, de conformidad con el art. 394 LEC.

Por todas las consideraciones anteriores,

SUPLICO AL TRIBUNAL

que, teniendo por presentado este escrito, tenga por contestada la demanda y previos los trámites legales, se dicte sentencia por la que, con estimación de la excepción de falta de legitimación pasiva y sin entrar a conocer del fondo del asunto, se absuelva a D./Dña. [NOMBRE Y APELLIDOS] de las pretensiones contra él formuladas, todo ello con expresa condena en costas al demandante.

Es justicia debe hacerse en [LUGAR], a [FECHA].

Firma del Abogado	Firma del Procurador/a

========================================================================
