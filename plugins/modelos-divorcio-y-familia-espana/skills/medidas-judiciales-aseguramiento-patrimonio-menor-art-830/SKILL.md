---
name: medidas-judiciales-aseguramiento-patrimonio-menor-art-830
description: "Redacta el escrito «Medidas judiciales de aseguramiento del patrimonio del menor (art. 167 CC)» (formulario 830 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Medidas judiciales de aseguramiento del patrimonio del menor (art. 167 CC)

> Formulario 0830 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (11 veces)
- [ ] PROFESIÓN
- [ ] LOCALIDAD
- [ ] CALLE (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] COLEGIO
- [ ] NIF
- [ ] Nº
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, con número de colegiado»; «…, con DNI/NIF [NIF], vecino/a de»; «…uientes: HECHOS PRIMERO.- Mi mandante es»; «…, domiciliados en»; «…patrimonio del hijo. (...)" VIII. Gastos»; «…la Ley de la Jurisdicción Voluntaria. En»; «…, a»; «…, a [COMPLETAR], de»; «…, a [COMPLETAR], de [COMPLETAR], de»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 158, 164, 165, 167, 200 y 249 del Código Civil
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

### Formulario 0830 · Medidas judiciales de aseguramiento del patrimonio del menor (art. 167 CC)

- Año del modelo: 2015
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 30 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dª [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dª [NOMBRE Y APELLIDOS], mayor de edad, de profesión [PROFESIÓN], con domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], pta., según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, comparezco en este TRIBUNAL con la asistencia del Letrado D./Dª [NOMBRE Y APELLIDOS], del Ilustre Colegio de Abogados de [COLEGIO], con número de colegiado [COMPLETAR], y DIGO:

Que por medio del presente escrito y en la representación que ostento, promuevo EXPEDIENTE DE JURISDICCIÓN VOLUNTARIA EN SOLICITUD DE LA ADOPCIÓN DE LAS MEDIDAS JUDICIALES ESTABLECIDAS EN EL ART. 167 DEL CÓDIGO CIVIL (en relación con el patrimonio del menor D./Dª [NOMBRE Y APELLIDOS], con DNI/NIF [NIF], vecino/a de [COMPLETAR], con domicilio en la calle [CALLE], nº [NÚMERO], pta., con base en los siguientes:

HECHOS

PRIMERO.- Mi mandante es [COMPLETAR] (tipo de parentesco que une al solicitante con el menor) de D./Dª [NOMBRE Y APELLIDOS]

SEGUNDO.- Que D./Dª [NOMBRE Y APELLIDOS], de [Nº] años de edad, se encuentra bajo la patria potestad de sus padres: D./Dª [NOMBRE Y APELLIDOS] y D./Dª [NOMBRE Y APELLIDOS], domiciliados en [COMPLETAR], que se ocupan, en virtud de la misma, de la administración de los bienes del menor.

TERCERO.- Que en la administración del patrimonio del menor por los citados titulares de la patria potestad se han observado las siguientes conductas y actos que ponen en peligro el patrimonio del hijo:

Como justificación de los anteriores hechos, se acompañan los siguientes DOCUMENTOS:

Pueden concretarse las medidas que se proponen, justificando su idoneidad. Por ej.: “En concreto, solicitamos que se obligue a los titulares de la patria potestad a prestar caución suficiente para continuar en la administración de los bienes o, en el caso de que no se considere oportuno o de que no se preste la citada caución en determinado plazo, el nombramiento de un Administrador.

QUINTO.- Se propone como persona idónea para ostentar el cargo de defensor judicial a D./Dª [NOMBRE Y APELLIDOS] …… (datos personales). Su idoneidad se basa en las siguientes razones: …… (entre otras, se puede aducir un parentesco cercano con el menor [NOTA DE REVISIÓN: El expediente es del art. 167 CC (bienes del menor). Fuente: Código Civil (BOE-A-1889-4763) art. 167; Ley 15/2015 de la Jurisdicción Voluntaria (BOE-A-2015-7391) art. 87, redacción Ley 8/2021 (BOE-A-2021-9233).]

Resultan aplicables a los citados hechos los siguientes

FUNDAMENTOS DE DERECHO

I. Jurisdicción y competencia. Es competente el Tribunal de Instancia al que me dirijo, conforme a lo dispuesto en los arts. 2 y 87.2 de la Ley de la Jurisdicción Voluntaria, en la nueva redacción dada por la Ley 8/2021 de 2 de junio, por ser el correspondiente al domicilio (o, en su defecto, residencia) del menor

II. Procedimiento. El procedimiento debe tramitarse conforme a lo establecido en los artículos 17 a 22, 87 y 88 de la Ley de la Jurisdicción Voluntaria, en la nueva redacción dada por la Ley 8/2021 de 2 de junio.

III. Capacidad. Tiene mi mandante capacidad para promover este procedimiento, conforme con lo dispuesto en los artículos 6 y ss LEC.

IV. Legitimación. Mi representado está legitimado activamente para promover este procedimiento, conforme al artículo 167 del Código civil y al artículo 87.3 de la Ley de la Jurisdicción Voluntaria.

La legitimación pasiva corresponde a D./Dª [NOMBRE Y APELLIDOS] y D./Dª [NOMBRE Y APELLIDOS], padres del menor, que vienen ocupándose hasta la fecha de la administración de los bienes de este.

V. Representación y defensa. Aunque en virtud del art. 85.3 de la Ley de la Jurisdicción Voluntaria, en la tramitación del presente expediente no es preceptiva la intervención de Abogado ni Procurador, el art. 3.2, segundo inciso de la citada ley establece que las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente, como se hace en la presente solicitud.

VI. Intervención del Ministerio Fiscal. Debe intervenir y ser oído el Ministerio Fiscal conforme a lo dispuesto en los artículos 4 y 30.1 de la Ley de la Jurisdicción Voluntaria.

VII. Derecho sustantivo. El art. 167 del Código civil establece: “Cuando la administración de los padres ponga en peligro el patrimonio del hijo, el Juez, a petición del propio hijo, del Ministerio Fiscal o de cualquier pariente del menor, podrá adoptar las providencias que estime necesarias para la seguridad y recaudo de los bienes, exigir caución o fianza para la continuación en la administración o incluso nombrar un Administrador”.

Por su parte, el artículo 87 de la Ley de la Jurisdicción Voluntaria, modificado por la Ley 8/2021 de 2 de junio, dispone: “

1. Se aplicarán las disposiciones de esta Sección para adoptar medidas en relación al ejercicio inadecuado de la potestad de guarda de menores o personas con discapacidad o a la administración de sus bienes en los casos a que se refieren los artículos 158, 164, 165, 167, 200 y 249 del Código Civil o a las disposiciones análogas de la legislación civil aplicable. Y en concreto:

(...)

e) Para la adopción de las medidas necesarias para asegurar y proteger los bienes de los hijos, exigir caución o fianza para continuar los progenitores con su administración o incluso nombrar un administrador cuando la administración de los progenitores ponga en peligro el patrimonio del hijo.

(...)"

VIII. Gastos [COMPLETAR]. Se rigen por lo dispuesto en el artículo 7 de la Ley de la Jurisdicción Voluntaria.

Por lo expuesto

AL TRIBUNAL SUPLICO que tenga por presentado este escrito con los documentos que lo acompañan y sus copias; me tenga por comparecido y parte en la representación que ostento y se sirva incoar expediente de jurisdicción voluntaria para la ADOPCIÓN DE LAS MEDIDAS NECESARIAS PARA ASEGURAR Y PROTEGER LOS BIENES DE LOS HIJOS, EXIGIR CAUCIÓN O FIANZA PARA CONTINUAR LOS PROGENITORES CON SU ADMINISTRACIÓN O INCLUSO NOMBRAR UN ADMINISTRADOR CUANDO LA ADMINISTRACIÓN DE LOS PROGENITORES PONGA EN PELIGRO EL PATRIMONIO DEL HIJO, se admita a trámite todo ello. Y, previos los trámites legales oportunos, con intervención del Ministerio Fiscal y demás personas que se considere oportuno, dicte este Tribunal resolución en que se adopte las medidas necesarias para la seguridad y recaudo de los bienes del menor solicitadas en el cuerpo de este escrito

OTROSÍ DIGO.-Así mismo se solicita la imposición de las costas de este procedimiento, en su caso, a la parte que se haya opuesto temeraria e irracionalmente a la presente solicitud, conforme a lo dispuesto en el artículo 394 de la Ley de Enjuiciamiento Civil, por remisión del art. 8 de la Ley de la Jurisdicción Voluntaria.

En [COMPLETAR], a [COMPLETAR], de [COMPLETAR], de [COMPLETAR]

Firma del Promotor del expediente

========================================================================
