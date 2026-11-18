---
name: defensor-judicial-conflicto-intereses-progenitor-480
description: "Redacta el escrito «Defensor judicial por conflicto de intereses con un progenitor» (formulario 480 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Defensor judicial por conflicto de intereses con un progenitor

> Formulario 0480 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (8 veces)
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] FECHA (3 veces)
- [ ] NOMBRE DEL NOTARIO
- [ ] LUGAR

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 27.1 LJV
- art. 163 del Código Civil
- art. 28.2 LJV
- art. 29 LJV
- art. 28.1 LJV
- art. 3.2 LJV
- art. 28.3 LJV
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

### Formulario 0480 · Defensor judicial por conflicto de intereses con un progenitor

- Año del modelo: 2017
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 21 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de solicitud instando el inicio de expediente de nombramiento de defensor judicial de un menor por existencia de intereses contrapuestos con su progenitor.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], n.º [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

Que por medio del presente escrito promuevo expediente de jurisdicción voluntaria para el nombramiento de defensor judicial del menor D./Dña. [NOMBRE Y APELLIDOS], por existir un conflicto de intereses con mi persona, como progenitor del mismo, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que la madre del menor D./Dña. [NOMBRE Y APELLIDOS] y esposa del solicitante falleció el pasado día [FECHA], y transcurrido el plazo legal se va a proceder a aperturar la herencia de la misma, siendo necesario proveer al menor de un defensor judicial que lo represente en el momento de la aceptación y partición hereditaria por existir intereses contrapuestos o incompatibles entre el menor y su padre quien tiene su patria potestad, aquí solicitante.

2.ª) Dado que ambos concurrimos a la misma como únicos herederos al ser cónyuge e hijo de la fallecida y haber sido instituidos como tales en testamento otorgado en fecha [FECHA] ante el Notario D./Dña. [NOMBRE DEL NOTARIO]; la existencia de conflicto de intereses entre el solicitante y su hijo menor de edad se evidencia desde el momento en que entre el solicitante y su fallecida esposa, existen bienes comunes que habrá que dividir con carácter previo a la partición.

3.ª) En consecuencia acudo al presente expediente, regulado en los arts. 27 y ss. de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), para solicitar el nombramiento de un defensor judicial a los efectos de la herencia referida. Todo lo cual tiene encaje en el art. 27.1 LJV y en el art. 163 del Código Civil, al existir un conflicto de intereses entre el solicitante y su hijo menor de edad. Así, me encuentro legitimado para tal solicitud, actuando en interés del menor, en virtud del art. 28.2 LJV. Asimismo, se propone para dicho cargo a D./Dña. [NOMBRE Y APELLIDOS], tío del menor, padrino de bautismo, hermano del fallecido D./Dña. [NOMBRE Y APELLIDOS], que tiene una especial relación afectiva con el mismo, y quien en modo alguno concurre a la herencia que nos ocupa. Y ello, sin perjuicio de mostrar mi consentimiento con el defensor judicial que finalmente se tenga a bien designar.

4.ª) De conformidad con el art. 29 LJV, desde la presentación de esta solicitud hasta la aceptación del cargo por el defensor judicial finalmente designado, quedarán suspendidos los plazos de prescripción o caducidad para aceptar o repudiar la herencia.

5.ª) Que es competente el Tribunal de Instancia al que me dirijo conforme al art. 28.1 LJV en relación con lo dispuesto en el art. 85.1º LOPJ, al encontrarse en su partido judicial el domicilio del menor sito en [LOCALIDAD], calle [CALLE], n.º [NÚMERO].

6.ª) Se acompañan a este escrito certificación de nacimiento del menor en la que consta reconocida su filiación; certificado de fallecimiento de D./Dña. [NOMBRE Y APELLIDOS], y copia del testamento donde se aprecia la condición de herederos del cónyuge de ésta y viudo de dicho causante y del hijo común de ambos menor de edad.

Por todo lo expuesto, al amparo de los arts. 299 y ss. del Código Civil, y de los arts. 27 y ss. LJV,

SUPLICO AL TRIBUNAL:

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria, previa la convocatoria de comparecencia del Ministerio Fiscal, de D./Dña. [NOMBRE Y APELLIDOS] como posible defensor judicial, de mí como solicitante, y de quien se estime pertinente, incluso del menor D./Dña. [NOMBRE Y APELLIDOS] si se cree preciso; se dicte decreto por el Letrado de la Administración de Justicia nombrándose defensor judicial para representarle en la aceptación y partición de la herencia reseñada.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma del solicitante

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito, el art. 28.3 LJV no exige dichos requisitos para la tramitación de la solicitud que nos ocupa.

========================================================================
