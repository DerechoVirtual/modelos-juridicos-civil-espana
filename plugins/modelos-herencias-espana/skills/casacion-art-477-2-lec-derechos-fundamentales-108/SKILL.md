---
name: casacion-art-477-2-lec-derechos-fundamentales-108
description: "Redacta el escrito «Casación del art. 477.2 LEC por derechos fundamentales: intromisión en el honor» (formulario 108 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Casación del art. 477.2 LEC por derechos fundamentales: intromisión en el honor

> Formulario 0108 del plugin **Sucesiones** · revisado el 17-11-2026.

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

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LOCALIDAD (2 veces)
- [ ] Nº DE PROCEDIMIENTO (2 veces)
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] ACTO O RESOLUCIÓN
- [ ] FECHA (3 veces)
- [ ] Nº DE EXPEDIENTE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…a procesal de la LO 1/2025. A LA SECCIÓN»; «…la sentencia recurrida es errónea porque»; «…En efecto,»; «…parte necesaria la celebración de vista,»; «…elebración de vista del presente recurso»; «…la interposición del recurso de casación»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 477 LEC
- art. 18.1 CE
- arts. 1 y 7.7 de la Ley Orgánica 1/1982
- art. 20.1 CE
- artículo 18 de la Constitución
- arts. 18.1 CE
- art. 481.6 LEC
- Ley 5/2023

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

### Formulario 0108 · Casación del art. 477.2 LEC por derechos fundamentales: intromisión en el honor

- Año del modelo: 2022
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 19 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de interposición de recurso de casación ante la Sala Primera del Tribunal Supremo, al amparo del artículo 477.2 segundo inciso LEC (tutela judicial derechos fundamentales: derecho al honor), adaptado al RDL 5/2023.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN [COMPLETAR] DE LA AUDIENCIA PROVINCIAL DE [LOCALIDAD]

[NOTA DE REVISIÓN: Errata. La Audiencia Provincial no cambia de denominación. Fuente: LOPJ arts. 80 y 82 (Audiencia Provincial, sin cambio de denominación).]

Autos nº [Nº DE PROCEDIMIENTO]

Rollo de apelación nº [Nº DE PROCEDIMIENTO]

D./Dª. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre de D./Dª. [NOMBRE Y APELLIDOS], cuya representación tengo debidamente acreditada en los autos de juicio ordinario, sobre sobre tutela de los derechos a la intimidad y a la propia imagen, seguido a nuestra instancia contra [ACTO O RESOLUCIÓN], ante la Sala comparezco y, como mejor proceda en Derecho, DIGO:

Que, por medio del presente escrito, en virtud de lo dispuesto en el art. 477 LEC y dentro del plazo legal, interpongo en nombre de D./Dª [NOMBRE Y APELLIDOS]. RECURSO DE CASACIÓN ante la Sala Primera del Tribunal Supremo, contra la sentencia de fecha [FECHA] dictada por esta Audiencia Provincial, en grado de apelación, y notificada en fecha [FECHA]; en los autos de juicio ordinario al margen referenciados, con arreglo a los motivos siguientes:

MOTIVOS

ÚNICO

Por infracción del art. 18.1 CE, de los arts. 1 y 7.7 de la Ley Orgánica 1/1982, de 5 de mayo, de Protección Civil del Derecho al Honor, a la Intimidad Personal y Familiar y a la Propia Imagen, y de la doctrina jurisprudencial en la colisión derecho de información "versus" honor y, el presupuesto de veracidad en la comprobación de los hechos relatados.

Así se expresa en STS 64/2004 de 11 de febrero de 2004, rec. 356/1998, resumiendo la posición de la jurisprudencia:

"Como base teórica o dogmática a la presente cuestión, es necesario resaltar que el Tribunal Constitucional ha venido diferenciando desde la STC 104/1986, de 17 de julio, entre la amplitud de ejercicio de los derechos reconocidos en el art. 20.1 CE según se trate de libertad de expresión (en el sentido de la emisión de juicios personales y subjetivos, creencias, pensamientos y opiniones) y libertad de información (en cuanto a la narración de hechos). Con relación a la primera, al tratarse de la formulación de "pensamientos, ideas y opiniones" (art. 20-1-a) CE), sin pretensión de sentar hechos o afirmar datos objetivos, dispone de un campo de acción que viene sólo delimitado por la ausencia de expresiones indudablemente injuriosas o sin relación con las ideas u opiniones que se expongan y que resulten innecesarias para la exposición de las mismas (STS 105/1990, de 6 de junio, fundamentos jurídicos 4º y 8º; STEDH, S. 23 de abril de 1992 (...)

Asimismo, en este sentido hay que decir que cuando surge la colisión entre los derechos fundamentales de libertad de información y expresión de un lado y el derecho fundamental al honor, de otro, la jurisprudencia de esta Sala, así como la del Tribunal Constitucional, se ha decantado por el seguimiento de las siguientes directrices:

a) que la delimitación de la colisión entre tales derechos ha de hacerse caso por caso y sin fijar apriorísticamente los límites entre ellos,
b) que la tarea de ponderación o proporcionalidad ha de llevarse a cabo teniendo en cuenta la posición prevalente, que no jerárquica o absoluta, que sobre los derechos denominados de la personalidad, del artículo 18 de la Constitución Española, ostenta el derecho a la libertad de expresión y de información (...)

Por ello, y en conclusión hay que decir que, para que se pueda dar la referida preeminencia del derecho fundamental a expresar opiniones y a informar es preciso que concurran ineludiblemente las siguientes situaciones: a) Un interés general y la relevancia pública de la información divulgada, como presupuesto de la misma idea que noticia y como indicio de correspondencia de la información con un interés general en el conocimiento de los hechos sobre los que versa (SSTC 107/1988, 171/1990, 197/1991, 214/1991, 20/1992, 40/1992, 85/1992, 41/1994, 138/1996 y 2/1997); b) Que en consecuencia el derecho a informar se ve disminuido esencialmente si no se refiere a personalidades públicas que, al haber optado libremente por tal condición, deben soportar un cierto riesgo en el tema (por todas la STC. 138/1996); c) Que la información ha de ceñirse a una información que sea veraz, y así será la información comprobada y contrastada según los cánones de la profesionalidad informativa (SSTC 6/1988 y 3/1997, por todas) y, la ausencia de expresiones injuriosas o difamantes S. 15-10-2001", aparte de que se respete la delimitación del llamado "Reportaje Neutral", o sea, sin incorporar datos que excedan de la fuente de información, conteniendo alusiones improcedentes -S. 22-1-2002-".

Entendemos que la sentencia recurrida, al desestimar las pretensiones formuladas por esta parte en relación con la noticia difundida por la demandada, infringe, por interpretación errónea, los preceptos mencionados y la anterior doctrina dictada en aplicación de los mismos.

En efecto, la Audiencia Provincial de [LOCALIDAD] considera que la noticia en torno a la cual ha girado todo el procedimiento no constituye una intromisión ilegítima en el ámbito de protección del derecho fundamental al honor y a la propia imagen, al entender que los arts. 18.1 CE, y 1 y 7.7 de la Ley Orgánica 1/1982, de 5 de mayo, de Protección Civil del Derecho al Honor, a la Intimidad Personal y Familiar y a la Propia Imagen, deben ser interpretados, en contra de lo que sosteníamos en nuestra demanda y en el recurso de apelación, en el sentido de

A nuestro juicio, la interpretación que lleva a cabo la sentencia recurrida es errónea porque [COMPLETAR]

En efecto, [COMPLETAR]

Por consiguiente, el error interpretativo en que ha incurrido la sentencia impugnada es manifiesto, lo que constituye motivo más para que la misma sea íntegramente casada, con la consiguiente estimación de las pretensiones formuladas por esta parte en la primera instancia.

Por todo lo expuesto,

SUPLICO A LA SALA

Que teniendo por presentado este escrito, con los documentos que acompaña, se sirva admitirlo y, en su mérito, tener por interpuesto en tiempo y forma RECURSO DE CASACIÓN contra la sentencia de fecha [FECHA], remitiéndose por el Letrado de la Administración de Justicia los autos originales a la Sala Primera del Tribunal Supremo, para que, por dicho tribunal «ad quem», previa su admisión, se dicte sentencia que lo estime, casando la sentencia recurrida, recuperando la instancia, y estimando la demanda formulada por D./Dña. [NOMBRE Y APELLIDOS]; con el correspondiente pronunciamiento conforme a Ley sobre costas de las instancias y respecto de las del presente recurso.

OTROSI DIGO: Que estimando esta parte necesaria la celebración de vista, [COMPLETAR]

SUPLICO A LA SALA

Tenga por solicitado se acuerde en su día por el tribunal «ad quem» la celebración de vista del presente recurso [COMPLETAR].

SEGUNDO OTROSÍ DIGO: Que a partir de la DA 15ª LOPJ, adjunto al presente escrito resguardo de ingreso por importe de cincuenta euros (50 euros), en la cuenta expediente número [Nº DE EXPEDIENTE] de la cuenta de depósitos y consignaciones de la Audiencia Provincial como justificación del pago del depósito como requisito necesario para la interposición del recurso de casación [COMPLETAR].

SUPLICO A LA SALA

Tenga por constituido el referido depósito a los efectos procesales oportunos.

TERCERO OTROSÍ DIGO: Que de acuerdo con lo establecido en el art. 481.6 LEC, en la redacción dada por el Real Decreto-Ley 5/2023, de 28 de junio, se acompaña a este escrito copia con firma electrónica/con código seguro de verificación/certificación de la sentencia impugnada.

SUPLICO A LA SALA

Tenga por aportadas tal documentación a los efectos procesales oportunos.

Es Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

	Firma de Procurador/a
