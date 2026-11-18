---
name: defensor-judicial-conflicto-intereses-curador-inicio-781
description: "Redacta el escrito «Defensor judicial por conflicto de intereses con el curador: inicio del expediente» (formulario 781 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Defensor judicial por conflicto de intereses con el curador: inicio del expediente

> Formulario 0781 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

- [ ] SEDE (2 veces)
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (3 veces)
- [ ] FECHA (4 veces)
- [ ] Nº DE EXPEDIENTE
- [ ] NOMBRE DEL NOTARIO
- [ ] LUGAR
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…or con funciones de representación de D.»; «…numeración del juzgado de procedencia).]»; «… habiendo fallecido entonces mi padre D.»; «…/»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (4)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 287 y 289 CCiv
- art. 27.1 LJV
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

### Formulario 0781 · Defensor judicial por conflicto de intereses con el curador: inicio del expediente

- Año del modelo: 2015
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 27 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de solicitud instando el inicio de expediente de nombramiento de defensor judicial de persona con discapacidad con medidas de apoyo para el ejercicio de su capacidad jurídica por existencia de intereses contrapuestos con su curador.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

Que por medio del presente escrito promuevo expediente de jurisdicción voluntaria para el nombramiento de defensor judicial de D./Dña. [NOMBRE Y APELLIDOS], por existir un conflicto de intereses con mi persona, como tutor del mismo, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que mi representado es hermano y curador con funciones de representación de D. [COMPLETAR], en virtud de sentencia dictada por la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] en fecha [FECHA], en autos de proceso sobre provisión de medidas judiciales de apoyo a las personas con discapacidad nº [NÚMERO], que devino firme al no ser recurrida. En dicha resolución se me nombró como curador del mismo, al ser su único hermano, habiendo fallecido entonces mi padre D. [COMPLETAR], y siendo mi madre, Dña. demasiado mayor para el ejercicio del cargo. Se incoó al efecto el expediente de tutela nº [Nº DE EXPEDIENTE] / [COMPLETAR], tramitado ante el mismo órgano judicial, sin problema ni incidencia alguna.

2.ª) Que el pasado [FECHA] falleció nuestra madre Dña. [NOMBRE Y APELLIDOS], y transcurrido el plazo legal se va a proceder a aperturar la herencia de la misma, procediendo, en su caso, la aceptación o la repudiación de lo que corresponda.

3.ª) Dado que ambos, curador y persona a la que se presta el apoyo, concurrimos a la misma como únicos herederos al ser hijos de la fallecida y haber sido instituidos como tales en testamento otorgado en fecha [FECHA] ante el Notario D./Dña. [NOMBRE DEL NOTARIO]; resulta evidente que existe un conflicto de intereses en mi ejercicio del cargo de curador. En este sentido, debería solicitar las autorizaciones o aprobaciones judiciales previstas en los arts. 287 y 289 CCiv, para que mi hermano pudiera recibir la parte a la que tiene derecho, respecto a una herencia en la cual intervendré en mi propio nombre, al corresponderme mi cuota hereditaria. Por ello, para cumplir el mandato legal previsto en el art. 282 II del citado texto legal, y desempeñar mi función con la diligencia debida; pongo de manifiesto tal circunstancia.

4.ª) En consecuencia acudo al presente expediente, regulado en los arts. 27 y ss. de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), para solicitar el nombramiento de un defensor judicial a los efectos de la herencia referida. Todo lo cual tiene encaje en el art. 27.1 LJV y en el art. 295.2º CCiv, al existir un conflicto de intereses entre la persona con discapacidad, y yo como curador, sin que se haya constituido en este caso una curatela conjunta que excepcione tal previsión. Así, me encuentro legitimado para tal solicitud, actuando en interés de mi hermana, en virtud del art. 28.2 LJV. Asimismo, se propone para dicho cargo a Dña. [NOMBRE Y APELLIDOS], prima de la persona necesitada de apoyo, hija del hermano de mi padre, y quien en modo alguno concurre a la herencia que nos ocupa. Y ello, sin perjuicio de mostrar mi consentimiento con el defensor judicial que finalmente se tenga a bien designar.

5.ª) De conformidad con el art. 29 LJV, desde la presentación de esta solicitud hasta la aceptación del cargo por el defensor judicial finalmente designado, quedarán suspendidos los plazos de prescripción o caducidad para aceptar o repudiar la herencia.

6.ª) Que es competente la Sección Civil del Tribunal de Instancia al que me dirijo conforme al art. 28.1 LJV, al encontrarse en su partido judicial el domicilio de mi hermana sito en [LOCALIDAD], calle [CALLE], nº [NÚMERO].

7.ª) Se acompañan a este escrito testimonio de la sentencia que acordó la adopción de medidas de apoyo y la designación de curador y de la diligencia de ordenación que reconoce su firmeza; certificado de fallecimiento de Dña. [NOMBRE Y APELLIDOS], y copia del testamento donde se aprecia la condición de herederos del curador y persona a la que se presta apoyo.

Por todo lo expuesto, al amparo de los arts. 295 y ss. CCiv, y de los arts. 27 y ss. LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria, previa la convocatoria de comparecencia del Ministerio Fiscal, de Dña. [NOMBRE Y APELLIDOS] como posible defensora judicial, de mi como solicitante, y de quien se estime pertinente, incluso de mi hermano D. si se cree preciso; se dicte decreto por el Letrado de la Administración de Justicia nombrándose defensor judicial para representarle en la aceptación o repudiación de la herencia reseñada.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma del solicitante

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito, el art. 28.3 LJV no exige dichos requisitos para la tramitación de la solicitud que nos ocupa.

========================================================================
