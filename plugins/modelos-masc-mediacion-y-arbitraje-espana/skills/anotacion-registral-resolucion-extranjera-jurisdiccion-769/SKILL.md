---
name: anotacion-registral-resolucion-extranjera-jurisdiccion-769
description: "Redacta el escrito «Anotación registral de resolución extranjera de jurisdicción voluntaria» (formulario 769 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Anotación registral de resolución extranjera de jurisdicción voluntaria

> Formulario 0769 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] FECHA (4 veces)
- [ ] SEDE (3 veces)
- [ ] LUGAR
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…/2025. AL ENCARGADO/A DEL REGISTRO CIVIL»; «…DE»; «…ombraba representante legal de mi tío D.»; «… judicial mediante sentencia anterior de»; «…banesa, con doble nacionalidad, nació en»; «…numeración del juzgado de procedencia).]»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 11 Ley 15/2015
- art. 40 de la Ley 20/2011
- art. 11 LJV
- Ley 29/2015

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

### Formulario 0769 · Anotación registral de resolución extranjera de jurisdicción voluntaria

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; restos de formato retirados; notas del formulario agrupadas al final (1); 21 campos de relleno marcados en blanco; 2 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Solicitud de anotación registral de resolución extranjera de jurisdicción voluntaria consistente en el nombramiento representante legal.

Formulario adaptado a la reforma procesal de la LO 1/2025.

AL ENCARGADO/A DEL REGISTRO CIVIL [COMPLETAR] DE [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Registro comparezco y como mejor en Derecho proceda, DIGO: (1)

Que por medio del presente escrito, y al amparo de lo dispuesto en el art. 11 Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo EXPEDIENTE PARA LA ANOTACIÓN REGISTRAL DE RESOLUCIÓN EXTRANJERA DE JURISDICCIÓN VOLUNTARIA DE NOMBRAMIENTO DE REPRESENTANTE LEGAL, en base a las siguientes

ALEGACIONES

PRIMERA.- Que en fecha [FECHA], por el Tribunal de Familia de Beirut (Líbano) se dictó resolución en la que se me nombraba representante legal de mi tío D. [COMPLETAR], quien había sido discapacitado parcialmente por dicho órgano judicial mediante sentencia anterior de [COMPLETAR], a causa de una serie de problemas psiquiátricos permanentes, que precisan tratamiento médico continuo. Mi tío, hijo de padre español y madre libanesa, con doble nacionalidad, nació en [COMPLETAR] en fecha [FECHA], si bien, desde que cumplió 18 años pasó a residir en dicho país de manera permanente.

SEGUNDO.- En el expediente posterior para la constitución del cargo de representación que pudiera completar la incapacidad parcial declarada, de una forma similar a lo que en nuestra legislación se conoce como el cargo de curador, se plantearon diversos intereses contrapuestos, que no pudieron ser conciliados. Así, además de mi personamiento, intervinieron en el mismo dos primos míos, D./Dña. [NOMBRE Y APELLIDOS], y D./Dña. [NOMBRE Y APELLIDOS], también sobrinos de aquel, que solicitaron su nombramiento como curadores. La resolución judicial que se pretende anotar, y que me dio finalmente la razón, se encuentra actualmente recurrida ante la Corte de Apelación de Beirut, sin que se haya resuelto el correspondiente recurso.

TERCERO.- Al carecer España y Líbano de un convenio internacional de reconocimiento de resoluciones judiciales, el pasado [FECHA] insté ante la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] el reconocimiento o exequátur de mi nombramiento como representante legal, en virtud de lo dispuesto en los arts. 41 y ss. de la Ley 29/2015, de 30 de julio, de cooperación jurídica internacional en materia civil. El expediente, admitido a trámite, actualmente se encuentra en tramitación con traslado a los interesados antes relacionados y al Ministerio Fiscal para alegaciones, sin que hayan evacuado todavía pretensión alguna.

CUARTO.- De esta forma, se pretende que en la hoja correspondiente de la sección primera del Registro Civil al cual tengo el honor de dirigirme, donde se encuentra inscrito el nacimiento del declarado incapaz parcial, conste la forma de representación finalmente decidida, que complementará el grado de incapacidad declarado. Y así, dado que la resolución que configura ésta no es firme por encontrarse actualmente recurrida, y puesto que su reconocimiento en España se encuentra todavía en tramitación; de conformidad con el art. 11 de la Ley de Jurisdicción Voluntaria, y el art. 40 de la Ley 20/2011, de 21 de julio, del Registro Civil, procede su anotación registral, con objeto de ofrecer publicidad a terceros.

QUINTO.- Que acompaño a este escrito copias testimoniadas y debidamente legalizadas, de la resolución de constitución de representación cuya anotación registral se pretende, de la resolución del Tribunal de Familia de Beirut admitiendo a trámite el recurso frente a la misma, y de la sentencia que declaraba la discapacidad parcial previa ya inscrita. Todo ello con las traducciones al castellano de cada una de las resoluciones enumeradas, elaboradas por traductor o intérprete jurado oficial. Se aporta también testimonio del decreto del Letrado de la Administración de Justicia de la Sección Civil del Tribunal de Instancia [SEDE] de [SEDE], admitiendo a trámite el exequátur referido.

Por lo expuesto,

SUPLICO A V.I.

que teniendo por presentado este escrito y los documentos que se acompañan, y por promovido expediente de anotación registral de resolución extranjera de jurisdicción voluntaria de nombramiento de representante legal, se sirva admitirlo, y de conformidad con el art. 11 LJV, acuerde la anotación registral de la resolución referenciada en el Registro Civil.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma del solicitante

NOTAS DEL FORMULARIO

(1) No resulta exigible ser asistido por abogado y representado por procurador en el expediente.

========================================================================
