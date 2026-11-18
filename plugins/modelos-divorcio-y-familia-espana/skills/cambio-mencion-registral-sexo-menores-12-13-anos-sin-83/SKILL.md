---
name: cambio-mencion-registral-sexo-menores-12-13-anos-sin-83
description: "Redacta el escrito «Cambio de la mención registral del sexo en menores de 12 a 13 años, sin cambio de nombre» (formulario 83 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Cambio de la mención registral del sexo en menores de 12 a 13 años, sin cambio de nombre

> Formulario 0083 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS
- [ ] LOCALIDAD (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…tido por sus representantes legales, Don»; «…y Doña»; «…y Doña [COMPLETAR], con DNIs»; «…Doña [COMPLETAR], con DNIs [COMPLETAR] y»; «…s: Hechos y consideraciones jurídicas 1ª»; «…ue objeto de cambio con anterioridad. 2ª»; «…Y se propone la siguiente testifical: 3ª»; «…e los derechos de las personas LGTBI. 4ª»; «…on sus padres en el domicilio sito en 5ª»; «…en el encabezamiento de este escrito. 6ª»; «…te las consecuencias de su decisión". 7ª»; «…nte "será de tramitación preferente". 8ª»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 26 ter.1 LJV
- art. 43.4 de la Ley 4/2023
- art. 26 ter.2 LJV
- art. 26 ter.4 LJV
- Ley 15/2015

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

### Formulario 0083 · Cambio de la mención registral del sexo en menores de 12 a 13 años, sin cambio de nombre

- Año del modelo: 2023
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 18 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Solicitud de iniciación del expediente de jurisdicción voluntaria para obtener la aprobación judicial de la modificación de la mención registral del sexo de personas mayores de doce años y menores de catorce, sin petición de cambio de nombre.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], estudiante y con domicilio en [LOCALIDAD], asistido por sus representantes legales, Don [COMPLETAR] y Doña [COMPLETAR], con DNIs [COMPLETAR] y [COMPLETAR] respectivamente, y con el mismo domicilio, ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO:

Que por medio del presente escrito promuevo EXPEDIENTE DE JURISDICCIÓN VOLUNTARIA PARA OBTENER LA APROBACIÓN JUDICIAL DE LA MODIFICACIÓN DE LA MENCIÓN REGISTRAL DEL SEXO, en base a los siguientes:

Hechos y consideraciones jurídicas

1ª [COMPLETAR])

Que la persona menor solicitante es mayor de doce años y menor de catorce años.

Se acompaña como documento nº 1, certificado literal de nacimiento donde se aprecia la minoría de edad del solicitante; y como documento nº 2, certificado de empadronamiento.

No se solicita el cambio de nombre que aparece en el Registro, ya que éste fue objeto de cambio con anterioridad.

2ª [COMPLETAR])

Que la identidad sexual de dicha persona no coincide con el sexo asignado al nacer, manifestando su disconformidad con el sexo mencionado en su inscripción de nacimiento. Sin embargo, la persona solicitante quiere conservar su nombre propio, al ser conforme a los principios de libre elección del nombre propio previstos en la normativa reguladora del Registro Civil.

Como prueba que acredita que la persona que insta el expediente mantiene de forma estable la situación de no coincidencia o conformidad entre la identidad sexual y el sexo que consta en el registro, se aportan los siguientes documentos:

Y se propone la siguiente testifical:

3ª [COMPLETAR])

Que, en consecuencia, manifiesto mi disconformidad con el sexo mencionado en mi inscripción de nacimiento, y solicito autorización judicial para que se proceda a la correspondiente rectificación registral de la mención al sexo que aparece en la inscripción, de acuerdo a lo previsto en los arts. 26 bis y siguientes de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (LJV), según redacción dada por la Ley 4/2023, de 28 de febrero, para la igualdad real y efectiva de las personas trans y para la garantía de los derechos de las personas LGTBI.

4ª [COMPLETAR])

Que es competente la Sección Civil del Tribunal de Instancia al que me dirijo conforme al art. 26 ter.1 LJV, en relación con lo dispuesto en el art. 85.1º LOPJ, al encontrarse en su partido judicial el domicilio del menor solicitante, quien vive con sus padres en el domicilio sito en

5ª [COMPLETAR])

Que el art. 43.4 de la Ley 4/2023, de 28 de febrero, para la igualdad real y efectiva de las personas trans y para la garantía de los derechos de las personas LGTB, señala que "Las personas menores de catorce años y mayores de doce podrán solicitar la autorización judicial para la modificación de la mención registral del sexo en los términos del capítulo I bis del título II de la Ley 15/2015, de 2 de julio, de Jurisdicción Voluntaria". Y en el mismo sentido, el art. 26 ter.2 LJV, reitera que "Podrán promover este expediente las personas mayores de doce años y menores de catorce, asistidas por sus representantes legales".

A estos efectos, la identidad y demás datos de las personas titulares de la representación legal de la persona solicitante, y que la asisten en el procedimiento, figuran en el encabezamiento de este escrito.

6ª [COMPLETAR])

Que el art. 26 quinquies.1 LJV, establece que "Previa audiencia de la persona menor, el Juez resolverá sobre la concesión o denegación de la aprobación judicial, considerando en todo caso el interés superior del menor de edad y previa comprobación de su voluntad estable de modificar la inscripción registral y de su madurez suficiente para comprender y evaluar de forma razonable e independiente las consecuencias de su decisión".

7ª [COMPLETAR])

Que dado que la rectificación solicitada afecta a derechos fundamentales de una persona menor de edad, el art. 26 quater.1 LJV determina que este expediente "será de tramitación preferente".

8ª [COMPLETAR])

Que en la tramitación de este expediente no es preceptiva la intervención de abogado ni procurador (art. 26 ter.4 LJV).

En virtud de lo expuesto,

SUPLICO AL TRIBUNAL:

que teniendo por presentado este escrito, lo admita, y en atención a las circunstancias expresadas:

1º Se sirva citar a comparecer a la persona solicitante, a sus representantes legales y, en su caso, a las demás personas que estime oportuno, así como al Ministerio Fiscal.
2º Previa audiencia de la persona menor, resuelva concediendo la aprobación judicial solicitada, autorizando que se proceda a la rectificación registral de la mención al sexo de la persona solicitante ( en lugar de [COMPLETAR]), conservando el nombre que aparece en la inscripción de nacimiento.
3º Remita testimonio de dicha resolución al Registro Civil de [LOCALIDAD], donde consta inscrito el nacimiento del solicitante para proceder, en su caso, a la inscripción de la rectificación aprobada judicialmente.

Es justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del solicitante	Firmas de los titulares de la representación legal
