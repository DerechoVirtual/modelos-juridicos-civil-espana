---
name: contestacion-demanda-rescision-lesion-liquidacion-1452
description: "Redacta el escrito «Contestación a demanda de rescisión por lesión de la liquidación de gananciales del convenio» (formulario 1452 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a demanda de rescisión por lesión de la liquidación de gananciales del convenio

> Formulario 1452 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] Nº DE DOCUMENTO
- [ ] COLEGIO
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] Nº (2 veces)
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…NAL con la asistencia del Letrado D. /Dª»; «…me a lo dispuesto en el art. 394 LEC. En»; «…, a»; «…, a [COMPLETAR], de»; «…, a [COMPLETAR], de [COMPLETAR], de»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 394 LEC
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

### Formulario 1452 · Contestación a demanda de rescisión por lesión de la liquidación de gananciales del convenio

- Año del modelo: 2014
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 15 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 3 huecos del original que se habían perdido sin marca, marcados (Nº, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Al Tribunal
Comparecencia, representación y asistencia Letrada
Contestación a la demanda
HECHOS
FUNDAMENTOS DE DERECHO
Suplico
Lugar y fecha
Firmas

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dª [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dª [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], pta., representación que acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], comparezco en este TRIBUNAL con la asistencia del Letrado D. /Dª [COMPLETAR], del Ilustre Colegio de Abogados de [COLEGIO], y DIGO:

Que por medio del presente escrito y en la representación que ostento, formulo, dentro de plazo legal, CONTESTACIÓN A LA DEMANDA DE RESCISIÓN POR LESIÓN DE LA LIQUIDACIÓN DE LA SOCIEDAD DE GANANCIALES, instada por D./Dª [NOMBRE Y APELLIDOS] en autos de juicio núm. [Nº DE PROCEDIMIENTO]/[AÑO], con base en los siguientes

HECHOS

Conforme con la existencia del matrimonio y de la sentencia de divorcio en que se homologa el convenio regulador en el que los cónyuges practicaron la liquidación de su sociedad de gananciales.

No ha lugar a entrar a debatir la posible lesión en más de una cuarta parte de los derechos de la demandante en la liquidación de la sociedad de gananciales, dado que en el convenio regulador, cuya validez no se ha impugnado, se incluyó una cláusula en la que de modo expreso las partes renunciaban al ejercicio de una eventual acción de rescisión por lesión. Así, en la cláusula núm. [Nº] del convenio regulador se estipula: «»

Resultan aplicables a los anteriores hechos los siguientes

FUNDAMENTOS DE DERECHO

COMPETENCIA, PROCEDIMIENTO Y LEGITIMACIÓN

Conformes con los fundamentos de la demanda relativos a la competencia, procedimiento y legitimación.

REPRESENTACIÓN Y DEFENSA

Mi mandante comparece representado/a y defendido/a, respectivamente, por el Procurador y el Letrado que constan en el encabezamiento de este escrito, de acuerdo con lo dispuesto en los arts. 23, 31 y 399 y ss. LEC.

DERECHO SUSTANTIVO

Existe una jurisprudencia reiterada en la que se admite la validez de las renuncia efectuada en convenio regulador al ejercicio de una eventual acción de rescisión por lesión cuando resulta clara y terminante, como es el caso de la cláusula núm. [Nº] del convenio regulador objeto de este litigio, o incluso cuando se deduce de la interpretación del convenio en su conjunto.

Resulta claro ejemplo de esta jurisprudencia la STS de 19 de marzo de 2008, Rec. 73/2001, que declara: «tanto la doctrina como la jurisprudencia han considerado que puede mantenerse la validez de la renuncia cuando no concurre un vicio de la voluntad o de cualquier causa que pueda producir la invalidez de los negocios jurídicos () Así, la jurisprudencia de esta Sala ha venido admitiendo la validez de las renuncias efectuadas en convenio siempre que tengan las características de ser “() claras, terminantes o deducidas de hechos o actuaciones de interpretación unívoca, no dudosa o incierta” (SSTS de 22 de febrero de 1994, Rec. 486/1991, Rec. 2289/1997 y 6 de marzo de 2003)». Insiste en la validez de la renuncia anticipada a la acción rescisoria por lesión la STS de 30 de octubre de 2008, Rec. 2336/2004, con cita de la anterior.

No sólo esto sino que, en diversas ocasiones, se ha admitido también la renuncia tácita a la rescisión. En este sentido, p.ej., las SSTS de 6 de marzo de 2003, Rec. 2289/1997 o de 17 de marzo de 2006, Rec. 2717/1999).

En consecuencia, al contener el convenio regulador litigioso una renuncia expresa a la rescisión de la liquidación efectuada en el mismo sin que se haya cuestionado en ningún momento la ausencia de vicios del consentimiento al efectuarla, debe desestimarse la acción rescisoria interpuesta por el demandante.

COSTAS.- Deben imponerse al demandante, conforme al artículo 394 LEC.

Por lo expuesto:

SUPLICO AL TRIBUNAL

Que tras admitir este escrito con los documentos que lo acompañan, tenga por interpuesta en tiempo y forma CONTESTACIÓN A LA DEMANDA DE RESCISIÓN POR LESIÓN EN MÁS DE LA CUARTA PARTE DE LA LIQUIDACIÓN DE LA SOCIEDAD DE GANANCIALES instada de contrario y, previos los trámites procesales oportunos, dicte en su día sentencia por la que se desestimen totalmente las pretensiones de la demanda, con imposición de las costas a la parte demandante, conforme a lo dispuesto en el art. 394 LEC.

En [COMPLETAR], a [COMPLETAR], de [COMPLETAR], de [COMPLETAR]

========================================================================
