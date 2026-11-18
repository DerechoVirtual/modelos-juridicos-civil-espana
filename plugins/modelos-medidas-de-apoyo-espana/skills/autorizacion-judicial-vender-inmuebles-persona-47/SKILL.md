---
name: autorizacion-judicial-vender-inmuebles-persona-47
description: "Redacta el escrito «Autorización judicial para vender inmuebles de persona con discapacidad (Cataluña)» (formulario 47 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Autorización judicial para vender inmuebles de persona con discapacidad (Cataluña)

> Formulario 0047 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- NO VERIFICADO: formulario catalán con alternativa «tutor» para un mayor con discapacidad; tras la reforma catalana de 2021 la medida principal es la asistencia. Comprobar en el DOGC.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] LOCALIDAD (5 veces)
- [ ] FECHA
- [ ] NÚMERO (2 veces)
- [ ] IMPORTE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…na que presta asistencia a // tutor de D»; «…, propiedad de»; «…de superficie»; «…de»; «…con el número [NÚMERO], Tomo»; «…, Tomo [COMPLETAR] D»; «…ió el inmueble en virtud de escritura de»; «…, otorgada ante el Iltre. Notario»; «…de la ciudad de»; «…de la ciudad de [COMPLETAR] otorgada el»; «…astos derivados del sustento diario de D»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (4)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 0047 · Autorización judicial para vender inmuebles de persona con discapacidad (Cataluña)

- Año del modelo: 2023
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 2 puntualizaciones normativas añadidas en el texto; 27 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)
- Avisos de la revisión: NO VERIFICADO: formulario catalán con alternativa «tutor» para un mayor con discapacidad; tras la reforma catalana de 2021 la medida principal es la asistencia. Comprobar en el DOGC.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, actuando en nombre y representación de [NOMBRE DEL REPRESENTADO/A], en su condición de persona que presta asistencia a // tutor de D [COMPLETAR], con domicilio en [LOCALIDAD], según acredito mediante poder para pleitos que acompaño, ante el Tribunal comparezco y como mejor proceda en Derecho,

DIGO

Que, al amparo de lo dispuesto en los artículos 222-43.1 y siguientes del Código Civil de Cataluña en relación con los artículos 61 y siguientes de la Ley de Jurisdicción Voluntaria, mediante el presente escrito deduzco expediente de jurisdicción voluntaria en SOLICITUD DE AUTORIZACIÓN DE VENTA del bien inmueble sito en [LOCALIDAD], propiedad de [COMPLETAR], persona que precisa la asistencia de mi mandante // de la que mi mandante es tutor, en atención a los siguientes,

HECHOS

PRIMERO.- En fecha [FECHA] se dictó Sentencia por medio de la cual se designó a mi representado como asistente // tutor de D. [NOMBRE Y APELLIDOS]

Se acompaña dicha resolución como Documento núm. 1.

SEGUNDO.- Entre los bienes de la persona asistida // tutelada, tal como consta en la relación inventarial en su día efectuada, figura el siguiente bien:

Urbana sita en [LOCALIDAD] de superficie [COMPLETAR]

Está inscrita en el Registro de la Propiedad número [NÚMERO] de [COMPLETAR] con el número [NÚMERO], Tomo [COMPLETAR]

D [COMPLETAR] adquirió el inmueble en virtud de escritura de [COMPLETAR], otorgada ante el Iltre. Notario [COMPLETAR] de la ciudad de [COMPLETAR] otorgada el [COMPLETAR] bajo el número de protocolo

Se acompaña como Documento núm. 2 dicha escritura y como Documento núm. 3 la certificación del Registro de la Propiedad.

TERCERO.- La situación de la persona asistida // tutelada requiere de determinados productos y servicios para su total bienestar, habiendo aumentado recientemente la partida de gastos destinados a su sustento vital.

A efectos acreditativos, aportamos como Bloque Documental núm. 4 la relación de facturas acreditativas de las anteriores circunstancias.

CUARTO.- En atención a lo anteriormente expuesto, mi representado solicita la autorización judicial para la venta directa, sin intermediarios y sin subasta, del bien inmueble propiedad de D. [NOMBRE Y APELLIDOS], asistido por éste // de quien es tutor legal, actuando en la representación legal que tiene conferida y en su interés.

El inmueble cuya venta se pretende es el sito en [LOCALIDAD], cuyas demás circunstancias han sido expresadas en el Hecho Segundo.

La vivienda se pretende enajenar por el precio de [IMPORTE] euros al comprador (indicar si se conoce el nombre), según se acredita mediante el compromiso de venta condicionado a la obtención de la presente autorización judicial que se acompaña como Documento núm. 5.

La venta del bien inmueble es de interés de D. [NOMBRE Y APELLIDOS], correspondiendo el precio de venta con el ofertado actualmente en el mercado. Ello se acredita mediante el dictamen pericial elaborado por D. de valoración de precio de mercado de la citada vivienda que se acompaña como Documento núm. 6.

La necesidad y utilidad de la enajenación del inmueble se justifica con el hecho de que el importe íntegro de la venta se destinará a los gastos derivados del sustento diario de D [COMPLETAR] y que han sido relacionados anteriormente, cumpliéndose los requisitos previstos en los artículos 221-1 y 222-44 del Código Civil de Cataluña por realizarse en interés de la persona tutelada.

A los anteriores hechos, resultan de aplicación los siguientes,

FUNDAMENTOS DE DERECHO

PRIMERO.- JURISDICCIÓN Y COMPETENCIA

Resultan competentes las Secciones de lo Civil de los Tribunales de Instancia de esta ciudad, por ser los del lugar del domicilio de la persona que precisa asistencia // tutelada conforme a lo dispuesto en el artículo 62.1 de la Ley de Jurisdicción Voluntaria.

SEGUNDO .- PROCEDIMIENTO

El procedimiento debe tramitarse conforme a lo dispuesto en los artículos 61 y siguientes de la Ley de Jurisdicción Voluntaria.

TERCERO.- LEGITIMACIÓN, CUANTÍA Y POSTULACIÓN

Mi representado está legitimado al habérsele conferido funciones de asistencia sobre D [COMPLETAR] // ostentar la tutela sobre la persona en situación de discapacidad conforme a lo dispuesto en los artículos 226-1 // 222-1 del Código Civil de Cataluña. [NOTA DE REVISIÓN (sin verificar en el BOE): La alternativa «tutor» para un mayor con discapacidad parece desfasada tras la reforma catalana de 2021 (asistencia como medida principal); no se ha podido verificar en el BOE con el conector. Fuente: Ley 25/2010, Libro II CCCat (BOE-A-2010-13312) y su reforma de 2021.]

Asimismo, comparece representado por Procurador y asistido por Abogado según lo establecido en el art. 62.3 de la Ley de Jurisdicción Voluntaria, por exceder el valor de la venta el importe de 6.000 euros.

CUARTO.- INTERVENCIÓN DEL MINISTERIO FISCAL

Será necesaria la intervención del Ministerio Fiscal, de conformidad con lo expresado en el apartado 1 del artículo 64 de la Ley de Jurisdicción Voluntaria.

QUINTO.- FONDO

Resultan aplicables los siguientes preceptos:

- El art. 222-44 del Código Civil de Cataluña en cuanto a la necesidad y requisitos de la autorización judicial, justificándose las circunstancias y características fundamentales de la enajenación que se pretende realizar, así como la utilidad de la misma para la persona en situación de discapacidad.

- Los artículos 61 y siguientes de la Ley de Jurisdicción Voluntaria en cuanto a los requisitos que debe cumplir la solicitud de autorización judicial para la enajenación de los bienes inmuebles de la persona que precisa asistencia // tutelada.

- El artículo 65 de la Ley de Jurisdicción Voluntaria en cuanto a la resolución de la autorización solicitada.

SEXTO.- IURA NOVIT CURIA

En todo lo no invocado, resulta de aplicación el principio iura novit curia.

Por lo anterior,

AL TRIBUNAL SUPLICO: Que tenga por presentada esta solicitud de autorización para la enajenación de la vivienda sita en [LOCALIDAD], descrita en el hecho segundo, propiedad de [COMPLETAR],y, tras los trámites legales oportunos, previa práctica de la testifical que dejo ofrecida en el otrosí y audiencia del Ministerio Fiscal, dicte auto por el que conceda la autorización para enajenar el inmueble antes expresado.

OTROSI PRIMERO DIGO: Que a los efectos establecidos en el artículo 64.1 de la Ley de Jurisdicción Voluntaria, solicito que sea citado a la comparecencia la persona que precisa asistencia // tutelada, a fin de que sea oída, cuidándose esta parte de la comparecencia en el día y hora señalados a tal efecto.

En su virtud,

AL TRIBUNAL SUPLICO: Que tenga por propuesta la audiencia de la persona a persona que precisa asistencia // tutelada, acordando de conformidad.

OTROSÍ SEGUNDO DIGO: Que al amparo de lo dispuesto en el artículo 231 de la Ley de Enjuiciamiento Civil, esta parte manifiesta su voluntad de corregir cualquier defecto de carácter procesal en que pudiera haber incurrido.

En su virtud,

AL TRIBUNAL SUPLICO: Que tenga por hecha la anterior manifestación a los efectos oportunos.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Ldo. Proc
