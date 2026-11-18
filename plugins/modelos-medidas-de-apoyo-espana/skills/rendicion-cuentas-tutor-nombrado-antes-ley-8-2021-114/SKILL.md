---
name: rendicion-cuentas-tutor-nombrado-antes-ley-8-2021-114
description: "Redacta el escrito «Rendición de cuentas del tutor nombrado antes de la Ley 8/2021» (formulario 114 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Rendición de cuentas del tutor nombrado antes de la Ley 8/2021

> Formulario 0114 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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
- [ ] Nº
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] IMPORTE (2 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (4 veces)
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 17 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…s hechos y consideraciones jurídicas: 1ª»; «…tación del tutor como documentos números»; «…2ª»; «…2ª [COMPLETAR]) Que debido a»; «…fin, se adjuntan como documentos números»; «…nº [NÚMERO] de»; «…. -»; «…de»; «…de [COMPLETAR], al Tomo»; «… [COMPLETAR], al Tomo [COMPLETAR], Libro»; «…, Libro [COMPLETAR], Folio»; «…nº [NÚMERO] de -»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 43.2 LJV
- art. 43.3 LJV
- art. 51.4 LJV
- art. 51.2 LJV
- Ley 8/2021

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

### Formulario 0114 · Rendición de cuentas del tutor nombrado antes de la Ley 8/2021

- Año del modelo: 2022
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 35 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito del tutor de una persona con discapacidad nombrado conforme al régimen anterior a la Ley 8/2021 presentando al Tribunal rendición de cuentas por extinción de la tutela, aplicando las normas de la rendición de cuentas del curador.

Formulario adaptado a la reforma orgánica y procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [Nº]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, comparezco ante el Tribunal y, como mejor proceda en derecho, DIGO:

Que por medio del presente escrito formulo expediente de RENDICIÓN FINAL DE CUENTAS POR EXTINCIÓN DE LA TUTELA de D./Dña. [NOMBRE Y APELLIDOS]

La presente solicitud se fundamenta en los siguientes hechos y consideraciones jurídicas:

1ª [COMPLETAR])

Que mediante sentencia dictada por el Tribunal al que me dirijo, en autos de juicio verbal nº [Nº DE PROCEDIMIENTO], mi representado fue nombrado tutor de D./Dña. [NOMBRE Y APELLIDOS], respecto del que se establecieron judicialmente medidas de apoyo en la referida resolución judicial, atribuidas al mismo; cargo de tutor aceptado por mi mandante en fecha

Se acompaña copia de la referida sentencia y acta de aceptación del tutor como documentos números [COMPLETAR]

2ª [COMPLETAR])

Que debido a [COMPLETAR] mi mandante ha cesado en sus funciones, por lo que, dentro del plazo legal de tres meses, se presenta rendición de la cuenta general justificada de la administración del patrimonio del que fuera mi tutelado.

A tal fin, se adjuntan como documentos números [COMPLETAR], detallando a continuación el estado de los ingresos y gastos acumulados durante el ejercicio del cargo, teniendo en cuenta el inventario de bienes inicial que consta en autos y que reproducimos con en este escrito con el fin de facilitar la interpretación de la rendición de cuentas:

I. INVENTARIO INICIAL

a) Dinero en efectivo:

b) Efectos públicos y valores mobiliarios:

c) Alhajas:

d) Semovientes:

e) Frutos:

- Renta arrendaticia mensual por importe de [IMPORTE] euros correspondiente al alquiler del piso sito en calle [CALLE] nº [NÚMERO] de [COMPLETAR] que satisface el inquilino Sr./a. según contrato de arrendamiento de fecha [FECHA].
- [COMPLETAR]

f) Muebles:

g) Inmuebles:

- Finca registral nº [NÚMERO] inscrita al Registro de la Propiedad nº [NÚMERO] de [COMPLETAR], al Tomo [COMPLETAR], Libro [COMPLETAR], Folio [COMPLETAR], que se corresponde con el piso sito en la calle [CALLE] nº [NÚMERO] de
- [COMPLETAR]

h) Derechos y acciones:

i) Otros bienes:

II. VARIACIONES RESPECTO AL INVENTARIO INICIAL

Bien/Valor afectado	Operación	Fecha	Importe

TOTAL

III. INGRESOS

Descripción	Fecha	Importe anual
Alimentación
Educación
Gastos médicos
TOTAL

IV. DESTINO DE LOS INGRESOS OBTENIDOS

Descripción	Fecha	Importe anual
Reinversiones
Gastos de mantenimiento de inversiones

V. GASTOS CORRIENTES POR CUENTA DEL TUTELADO

Descripción	Fecha	Importe anual
Pensiones
Rentas del capital mobiliario
Rentas del capital inmobiliario
Otros
TOTAL

Diferencia ingresos-gastos:

Como resulta de los justificantes aportados, resulta una cantidad remanente a favor de D./D.ª [NOMBRE Y APELLIDOS] de [IMPORTE] euros, que en fecha [FECHA] ha sido ingresada en su libreta de ahorros y que constituye la última anotación de ésta.

3ª [COMPLETAR])

Conforme a lo establecido en la disposición transitoria segunda de la Ley 8/2021, de 2 de junio, por la que se reforma la legislación civil y procesal para el apoyo a las personas con discapacidad en el ejercicio de su capacidad jurídica, los tutores nombrados bajo el régimen de la legislación anterior ejercerán su cargo conforme a las disposiciones de esta Ley a partir de su entrada en vigor. A los tutores de las personas con discapacidad se les aplicarán las normas establecidas para los curadores representativos.

4ª [COMPLETAR])

Según lo establecido en el art. 43.2 LJV, el órgano judicial que haya conocido de un expediente sobre tutela, curatela o guarda de hecho, será competente para conocer de todas las incidencias, trámites y adopción de medidas o revisiones posteriores, siempre que el menor o persona con discapacidad resida en la misma circunscripción. En caso contrario, para conocer de alguna de esas incidencias, será preciso que se pida testimonio completo del expediente al Tribunal que anteriormente conoció del mismo, el cual lo remitirá en los diez días siguientes a la solicitud.

5ª [COMPLETAR])

En estos expedientes no será preceptiva la intervención de Abogado ni Procurador (art. 43.3 LJV). No obstante, mi mandante comparece representado por Procurador.

6ª [COMPLETAR])

Conforme a lo establecido en el art. 292 I CCiv, "el curador, sin perjuicio de la obligación de rendición periódica de cuentas que en su caso le haya impuesto la autoridad judicial, al cesar en sus funciones deberá rendir ante ella la cuenta general justificada de su administración en el plazo de tres meses, prorrogables por el tiempo que fuere necesario si concurre justa causa". Según dispone el art. 51.4 LJV, estas disposiciones serán de aplicación en los supuestos de rendición final de cuentas por extinción de la tutela o curatela, debiendo ser presentada, en su caso, en el plazo de tres meses desde el cese del cargo, prorrogables por el tiempo que fuere necesario si concurre justa causa. En estos casos también se oirá, si procediera, al nuevo tutor o curador y a los herederos del tutelado o asistido, en su caso.

7ª [COMPLETAR])

En virtud de lo dispuesto en el art. 51.2 LJV, presentados los informes, el letrado de la Administración de Justicia los trasladará a la persona con discapacidad, al menor si tuviera suficiente madurez y, en todo caso, si fuere mayor de doce años, a aquellos que aparecieran como interesados en el expediente y al Ministerio Fiscal. Si alguno de los anteriormente mencionados lo solicitara en el plazo de diez días, se citará a todos ellos a una comparecencia, pudiéndose proponer de oficio o a instancia de parte las diligencias y pruebas que se estimen oportunas.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que, teniendo por presentado este escrito junto con los documentos que se acompañan y copias de todo ello, se sirva admitirlo, y con intervención del Ministerio Fiscal, previos los trámites legales, dicte resolución aprobando la rendición final de cuentas presentada.

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del Procurador
