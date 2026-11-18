---
name: demanda-ejecutiva-aval-primer-requerimiento-titulo-no-252
description: "Redacta el escrito «Demanda ejecutiva por aval a primer requerimiento (título no judicial)» (formulario 252 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda ejecutiva por aval a primer requerimiento (título no judicial)

> Formulario 0252 del plugin **Ejecución civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.
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

- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO (2 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] FECHA (6 veces)
- [ ] NÚMERO (3 veces)
- [ ] IMPORTE (9 veces)
- [ ] LOCALIDAD
- [ ] Nº
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…reforma procesal de la LO 1/2025. Juicio»; «…a cual dirijo contra la entidad bancaria»; «…otorgó por la entidad bancaria ejecutada»; «…erimiento respecto de la titular avalada»; «…(Se acompaña como documento»; «…y»; «…l de requerimiento a la entidad bancaria»; «… públicas, con tal que sea primera copia»; «…ntencia de 4 de marzo de 2014 señala que»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 50 y 51 de la LEC
- artículo 550 de la LEC
- artículos 551 a 554 LEC
- art. 539.2 de la LEC

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

### Formulario 0252 · Demanda ejecutiva por aval a primer requerimiento (título no judicial)

- Año del modelo: 2020
- Revisión 17-11-2026: 33 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Juicio [COMPLETAR] n.º [Nº DE PROCEDIMIENTO]/[AÑO]

Que por medio de la presente demanda y en la meritada representación solicito la ejecución del aval a primer requerimiento autorizado por escritura otorgada por el Notario D. [NOMBRE Y APELLIDOS] en fecha [FECHA], e inscrito en el Registro Especial de Avales con el número [NÚMERO], en reclamación de la suma de [IMPORTE] euros en concepto de principal e intereses vencidos, más la cantidad de [IMPORTE] euros, que se presupuesta en concepto de intereses que se pueden devengar en la presente ejecución y costas, la cual dirijo contra la entidad bancaria [COMPLETAR], con domicilio en [LOCALIDAD], con base en los siguientes:

HECHOS

PRIMERO.- En fecha [FECHA], ante el Notario D. [NOMBRE Y APELLIDOS], se otorgó por la entidad bancaria ejecutada [COMPLETAR], aval solidario y a primer requerimiento respecto de la titular avalada [COMPLETAR], siendo beneficiaria esta parte ejecutante. El aval se otorgó en garantía del cumplimiento de las obligaciones vencidas por las relaciones comerciales y financieras derivadas del contrato de fecha [FECHA] suscrito entre mi representada y la titular avalada.

Tal como consta en el clausulado del aval, la entidad bancaria se obligaba de forma incondicional e irrevocable a pagar a primer requerimiento a la ejecutante hasta la suma total de [IMPORTE] euros, contra la presentación de las facturas impagadas a su vencimiento por conducto fehaciente y en el plazo de siete días hábiles siguientes a su recepción.

El aval a primer requerimiento estaba en vigor durante el plazo de [Nº] años desde la fecha de su formalización.

El citado aval fue inscrito en el Registro especial de avales con el número [NÚMERO] (Se acompaña como documento [COMPLETAR] escritura notarial de aval a primer requerimiento de fecha [FECHA]).

SEGUNDO.- En fecha [FECHA], y transcurrido el plazo de su vencimiento, la parte avalada dejó de abonar las facturas número [NÚMERO] y [COMPLETAR] por importe de [IMPORTE] euros, las cuales derivan del citado contrato garantizado de fecha [FECHA] (acompaño como documentos número [Nº DE DOCUMENTO] las facturas no abonadas).

Mi representada, ante la imposibilidad de cobrar las facturas de la avalada, remitió acta notarial de requerimiento a la entidad bancaria [COMPLETAR] para el pago de [IMPORTE] euros, importe de las citadas facturas (acompaño como documento número [Nº DE DOCUMENTO] acta notarial de requerimiento).

TERCERO.- Transcurrido el plazo de siete días hábiles, la entidad bancaria ejecutada no ha abonado la cantidad reclamada por lo que esta parte se ve en la obligación de interponer la presente demanda ejecutiva en reclamación de [IMPORTE] euros, importe del principal de las facturas reclamadas y que fueron garantizadas por la ejecutada, y de [IMPORTE] euros en concepto de intereses vencidos, con más los que se devenguen en el curso de este proceso.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

PRIMERO.- Competencia: Art. 545.3 de la LEC: Es competente el Tribunal al que me dirijo al tratarse de un título extrajudicial con arreglo a lo establecido en los arts. 50 y 51 de la LEC.

SEGUNDO.- Procedimiento: Artículo 549 LEC en relación con el que debe ser el contenido de la demanda ejecutiva y artículo 550 de la LEC en cuanto a los documentos a aportar. Y artículos 551 a 554 LEC en relación al despacho de ejecución.

TERCERO.- Título ejecutivo: Artículo 517.2.4º de la LEC: “4.º Las escrituras públicas, con tal que sea primera copia [COMPLETAR]; o si es segunda que esté dada en virtud de mandamiento judicial y con citación de la persona a quien deba perjudicar, o de su causante, o que se expida con la conformidad de todas las partes”.

CUARTO.- Tutela ejecutiva que se pretende: Se pretende la ejecución de la escritura de aval a primer requerimiento por la cantidad líquida derivada del importe de las facturas impagadas por la avalada y que la entidad ejecutada avaló con renuncia expresa de los beneficios de orden, excusión y división, y reconociendo su obligación de pago en virtud del aval a primer requerimiento. En el presente supuesto, la garantía que supone el aval a primer requerimiento es inmediata ante el impago de las obligaciones por parte de la avalada, habiendo expresado el Tribunal Supremo, entre otras, en su Sentencia de 4 de marzo de 2014 señala que [COMPLETAR]: "la característica del aval a primer requerimiento, según reiterada jurisprudencia de esta Sala, es la de dar nacimiento a una obligación de garantía inmediata que pierde su carácter accesorio de la obligación principal (a diferencia de la fianza), en el que obligación del garante es independiente de la obligación del garantizado y del contrato inicial" (Sentencias de 26 de octubre de 2010, rec. 1951/2006, con cita de las anteriores, de 27 de septiembre de 2005, rec. 80/1999 y de 1 de octubre de 2007, rec. 3542/2000)... " de modo que el garante no puede oponer al beneficiario, que reclama el pago, otras excepciones que las que derivan de la garantía misma" (Sentencia de 4 de diciembre de 2009, rec. 1654/2005).

QUINTO.- Costas procesales: Es de aplicación lo dispuesto en el art. 539.2 de la LEC en relación a las costas y gastos de la ejecución.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que teniendo por presentado este escrito con los documentos que lo acompañan y sus copias, se acuerde, sin necesidad de previo requerimiento al deudor, se dicte auto conteniendo la orden general de ejecución y despachando la misma, en el que conforme al artículo 551.2.3º LEC, fije la cantidad reclamada conforme a lo solicitado en la cantidad de [IMPORTE] euros en concepto de principal, más la cantidad de [IMPORTE] euros en concepto de intereses, gastos y costas.

OTROSÍ DIGO: Que, una vez dictado el auto general de ejecución y de conformidad con el art. 551.3.1º de la LEC, se solicita que por el Letrado de la Administración de Justicia responsable de la misma que, tras los trámites legales y en su caso, se proceda el embargo de los siguientes bienes que se estimen suficientes para cubrir las indicadas responsabilidades en su totalidad.

Por lo que, SUPLICO que, tras los trámites legales oportunos, se dicte decreto en el que se contengan las medidas que dejo interesadas.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].
