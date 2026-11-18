---
name: inscripcion-registral-resolucion-extranjera-jurisdiccion-739
description: "Redacta el escrito «Inscripción registral de resolución extranjera de jurisdicción voluntaria» (formulario 739 de propiedad y derechos reales, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Inscripción registral de resolución extranjera de jurisdicción voluntaria

> Formulario 0739 del plugin **Propiedad y derechos reales** · revisado el 17-11-2026.

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

- El formulario parte de una tutela de un mayor «incapacitado»: desde la Ley 8/2021 los tutores de personas con discapacidad actúan con las normas del curador representativo (DT 2.ª) y la medida debe revisarse (DT 5.ª). Adaptar la terminología y comprobar la equivalencia de la resolución extranjera.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NÚMERO (2 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] LOCALIDAD (4 veces)
- [ ] CALLE
- [ ] FECHA (3 veces)
- [ ] LUGAR
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…DE»; «…, era residente junto con mi padre, D.»; «…, sección»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 11.1 Ley 15/2015
- art. 73 de la Ley 20/2011
- art. 11 LJV
- art. 11.1 LJV

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

### Formulario 0739 · Inscripción registral de resolución extranjera de jurisdicción voluntaria

- Año del modelo: 2015
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 17 campos de relleno marcados en blanco
- Avisos de la revisión: El formulario parte de una tutela de un mayor «incapacitado»: desde la Ley 8/2021 los tutores de personas con discapacidad actúan con las normas del curador representativo (DT 2.ª) y la medida debe revisarse (DT 5.ª). Adaptar la terminología y comprobar la equivalencia de la resolución extranjera.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Solicitud de inscripción registral de resolución extranjera de jurisdicción voluntaria consistente en constitución de tutela y nombramiento de tutor de un hermano respecto de otro tras haber sido declarado incapacitado total y haber fallecido los progenitores.

A LA OFICINA GENERAL DEL REGISTRO CIVIL Nº [NÚMERO] DE [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante este Registro comparezco y como mejor en Derecho proceda, DIGO: (1)

Que por medio del presente escrito, y al amparo de lo dispuesto en el artículo 11.1 Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo EXPEDIENTE PARA LA INSCRIPCIÓN REGISTRAL DE RESOLUCIÓN EXTRANJERA DE JURISDICCIÓN VOLUNTARIA CONSISTENTE EN CONSTITUCIÓN DE TUTELA Y NOMBRAMIENTO DE TUTOR, en base a las siguientes

ALEGACIONES

PRIMERA.- Que en fecha [FECHA], por el Tribunal de Familia de Hamburgo (Alemania) se dictó resolución en la que se me nombraba tutor de mi hermano/a D./Dña. [NOMBRE Y APELLIDOS], el cual había sido incapacitado de manera total por el mismo Tribunal mediante sentencia anterior de [LOCALIDAD]. Mi hermano/a, nacido en [LOCALIDAD], era residente junto con mi padre, D. [COMPLETAR], en dicha localidad desde hace doce años, y tras el fallecimiento de este último (quien ostentaba la representación legal de aquel), el Ministerio Público de dicho país puso en marcha un expediente no contencioso, según la legislación alemana, que desembocó en la constitución de la citada tutela nombrándome tutor. La resolución devino firme al no existir desacuerdo entre ninguna de las partes, y no ser, por ello, recurrida por nadie.

SEGUNDO.- En consecuencia, es una de las obligaciones de mi cargo el hacer constar dicha situación mediante inscripción marginal en la hoja correspondiente del Registro Civil de [LOCALIDAD], sección [COMPLETAR], donde se encuentra inscrito el nacimiento de mi hermano, de conformidad con lo dispuesto en el art. 73 de la Ley 20/2011, de 21 de julio, del Registro Civil. Todo ello, a los efectos de que se pueda dar la oportuna publicidad a terceros de la nueva situación de representación legal de mi hermano; máxime cuando se va a proceder a abrir la herencia de mi padre, existiendo diversos inmuebles sitos en España que pueden ser objeto de adjudicación y venta. En este sentido, la situación de incapacidad y de otorgamiento de la representación legal a mi padre ya consta en la citada hoja registral mediante inscripción marginal practicada en fecha [FECHA].

TERCERO.- Que, de conformidad con el art. 11 LJV, para la inscripción de tal resolución de jurisdicción voluntaria deben cumplimentarse tres requisitos:

1.- Debe superarse el trámite de exequátur o de reconocimiento incidental en España. Y así, en virtud de lo dispuesto en el art. 30.1 del Reglamento (UE) 2019/1111 del Consejo, de 25 de junio de 2019, y siendo Alemania un estado miembro de la Unión Europea, la resolución dictada por el Tribunal de Familia de Hamburgo debe ser reconocida en España sin necesidad de recurrir a procedimiento alguno.

2.- Debe ser inscrita por el Encargado del Registro correspondiente, en este caso el magistrado a quien tengo el honor de dirigirme, pues en él se encuentra inscrito el nacimiento de mi hermano/a.

3.- Debe tratarse de una resolución de carácter definitivo, lo que se acredita con el segundo testimonio que se adjunta a la presente resolución.

CUARTO.- Que acompaño a este escrito copias testimoniadas y debidamente legalizadas, de la resolución de constitución de tutela cuya inscripción marginal se pretende, de la resolución de la Secretaría Judicial del Tribunal de Familia de Hamburgo indicando la firmeza de la misma, y de la sentencia de incapacitación previa ya inscrita. Todo ello con las traducciones al castellano de cada una de las resoluciones enumeradas, elaboradas por traductor o intérprete jurado oficial.

Por lo expuesto,

SUPLICO A LA OFICINA GENERAL

que teniendo por presentado este escrito y los documentos que se acompañan, y por promovido expediente de inscripción registral de resolución extranjera de jurisdicción voluntaria de constitución de tutela y nombramiento de tutor, y de conformidad con el art. 11.1 LJV, se practique la inscripción marginal de la misma en el registro individual del solicitante, de conformidad con lo establecido en la legislación del Registro Civil.

Es Justicia que solicito en [LUGAR], a [FECHA].

Firma del solicitante

NOTAS DEL FORMULARIO

(1) No resulta exigible ser asistido por abogado y representado por procurador en el expediente.

========================================================================
