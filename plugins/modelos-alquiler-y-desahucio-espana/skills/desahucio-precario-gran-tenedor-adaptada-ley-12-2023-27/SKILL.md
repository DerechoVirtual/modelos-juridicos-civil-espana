---
name: desahucio-precario-gran-tenedor-adaptada-ley-12-2023-27
description: "Redacta el escrito «Desahucio por precario del gran tenedor (adaptada a la Ley 12/2023)» (formulario 27 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Desahucio por precario del gran tenedor (adaptada a la Ley 12/2023)

> Formulario 0027 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

- Gran tenedor: acreditación obligatoria con certificación registral (art. 3.k Ley 12/2023, redacción RDL 29/2026) y suspensión del art. 2 RDL 29/2026 si el ocupante es vulnerable sin alternativa.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE (2 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NOMBRE DEL REPRESENTADO/A (2 veces)
- [ ] DNI/NIE (2 veces)
- [ ] LOCALIDAD (5 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] Nº
- [ ] FECHA
- [ ] IMPORTE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «…de [COMPLETAR] al Tomo»; «…e [COMPLETAR] al Tomo [COMPLETAR], Libro»; «…, Libro [COMPLETAR], Folio»; «…de»; «…de [COMPLETAR] de»; «…rajudicial. En este sentido, se acudió a»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 3.k) de la Ley 12/2023
- artículo 439.6 de la LEC
- artículos 23 y 31 de la LEC
- art. 437.1 LEC
- art. 5 de la Ley Orgánica 1/2025
- artículos 394 y 438.5 de la LEC
- artículo 438.5 y 441.5 LEC
- artículo 438.6 de la LEC
- artículos 437.3, 438.7 y 549.3 LEC
- artículo 231 de la LEC

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

### Formulario 0027 · Desahucio por precario del gran tenedor (adaptada a la Ley 12/2023)

- Año del modelo: 2024
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 26 campos de relleno marcados en blanco
- Avisos de la revisión: Gran tenedor: acreditación obligatoria con certificación registral (art. 3.k Ley 12/2023, redacción RDL 29/2026) y suspensión del art. 2 RDL 29/2026 si el ocupante es vulnerable sin alternativa.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma orgánica y procesal de la LO 1/2025 y a la STC 26/2025, de 29 de enero.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] QUE POR TURNO CORRESPONDA

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

Don/Doña [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales y de [NOMBRE DEL REPRESENTADO/A], con DNI [DNI/NIE] y domicilio en [LOCALIDAD], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], ante el Tribunal comparezco y como mejor proceda en Derecho,

DIGO:

Que por medio del presente escrito, en la representación que me ha sido conferida, formulo DEMANDA DE JUICIO VERBAL EN EJERCICIO DE LA ACCIÓN DE DESAHUCIO POR PRECARIO contra D./Dña [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD] y DNI/NIE [DNI/NIE], con base en los siguientes,

HECHOS

PRIMERO Mi representado/a es propietario/a de la vivienda sita en [LOCALIDAD] por título de compraventa según consta inscrito en el Registro de la Propiedad núm. [Nº] de [COMPLETAR] al Tomo [COMPLETAR], Libro [COMPLETAR], Folio [COMPLETAR], Inscripción

Se acompaña como DOCUMENTO NÚM. 1 nota simple registral acreditativa de dicho extremo

SEGUNDO De conformidad con lo dispuesto en el artículo 3.k) de la Ley 12/2023 de 24 de mayo, por el derecho a la vivienda, se hace constar que mi representado/a ostenta la condición de gran tenedor.

A efectos acreditativos y, de conformidad con lo dispuesto en el artículo 439.6 de la LEC, se acompaña como DOCUMENTO NÚM. 2 certificado del Registro de la Propiedad en que se incluyen la totalidad de inmuebles de los que mi mandante es titular.

TERCERO El inmueble constituye la vivienda habitual de la persona arrendataria.

CUARTO En su día, dada la situación precaria de la parte demandada, se le permitió ocupar con carácter temporal el inmueble.

QUINTO No obstante, mi mandante puso en conocimiento de la demandada su voluntad de no prolongar la situación, requiriéndole para que procediese a dejar libre la vivienda, a lo que dicha parte se negó.

Habida cuenta lo anterior, en fecha [FECHA] de [COMPLETAR] de [COMPLETAR], se remitió comunicación a la parte demandada a efectos de requerirle formalmente para que procediese el indicado desalojo. Sin embargo, dicho requerimiento no ha sido atendido.

SEXTO Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

A los anteriores Hechos, son de aplicación los siguientes,

FUNDAMENTOS DE DERECHO

I. JURISDICCIÓN Y COMPETENCIA

Es competente el Tribunal de Instancia de [SEDE], toda vez que es el Tribunal del partido judicial en que está sita la finca, en aplicación del arts. 85.1º LOPJ y arts. 45, 52.7º y 54 de la LEC.

II. PROCEDIMIENTO

El procedimiento ajustado a Derecho será el de juicio verbal regulado en los artículos 437 y siguientes de la LEC, atendiendo a la materia objeto del presente procedimiento, en aplicación de lo establecido en el artículo 250.1.2º de la LEC.

III. LEGITIMACIÓN

Mi mandante ostenta la legitimación activa por ser quien tiene derecho a poseer la finca en su condición de propietario de la vivienda.

La parte demandada ostenta legitimación pasiva en cuanto a ocupante de la vivienda.

IV.CUANTÍA

De conformidad con lo dispuesto en los artículos 251.2º y 253.1 de la LEC, la cuantía de la demanda se fija en [IMPORTE] euros, correspondiente al valor del inmueble cuya posesión se pretende recuperar.

V. POSTULACIÓN Y DEFENSA

De acuerdo con lo previsto en los artículos 23 y 31 de la LEC, se presente la demanda por medio de Procurador/a legalmente habilitado/a y bajo la dirección del/ de la Letrado/a firmante.

VI. CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC en relación con el art. 437.1 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VII. FONDO DEL ASUNTO

Se ejercita en la presente demanda acción de desahucio por precario con el fin de recuperar la posesión efectiva de la vivienda propiedad de mi mandante.

Si bien el precario no se encuentra legalmente establecido, conforme a la reiterada jurisprudencia, se trata de aquella situación en la que una persona disfruta de la cosa ajena, sin pagar renta ni ostentar título que legitime la posesión.

En este sentido, la Sentencia de la Audiencia Provincial de Toledo de 1 de septiembre de 2006, rec. 322/2005:

“La figura de precario no se identifica exclusivamente con aquel negocio jurídico en el que una de las partes concede a la otra, de forma gratuita, el uso de una cosa que puede ser revocado cuando el concedente lo estime conveniente, aspecto que le atribuyó el Derecho romano y al que parece referirse el art. 1750, párrafo 2º, del Código Civil, sino que se extiende a los supuestos en que una persona, sin pagar mered, ostenta el uso de un bien por mera tolerancia del titular del mismo o sin título que lo legitime o en virtud de uno que resulta en este momento ineficaz (SSTS 13/2/1958, 39/10/1986).

VII. COSTAS

Con arreglo a lo dispuesto en los artículos 394 y 438.5 de la LEC, procede la condena en costas a la parte demandada.

Por todo ello,

AL TRIBUNAL SUPLICO, que teniendo por presentado este escrito junto con los documentos que se acompañan y sus copias, se sirva admitirlos, tener por personada al/ a la Procurador/a de los Tribunales que suscribe la representación que ostenta, ordenando se entiendan con el/ella las sucesivas diligencias; tener por formulada, en nombre de [NOMBRE DEL REPRESENTADO/A] demanda de JUICIO VERBAL EN EJERCICIO DE LA ACCIÓN DE DESAHUCIO POR PRECARIO correspondiente a la vivienda sita en [LOCALIDAD], y, previos los trámites legales oportunos, la admita a trámite y con traslado a la parte demandada de la demanda y documentos con ella acompañados, tenga a bien acordar el requerimiento previo a la vista de los artículo 438.5 y 441.5 LEC, procediendo, en caso de oposición, a señalar día y hora para la eventual vista y, tras los trámites legales oportunos previstos en dicho artículo, dicte Sentencia mediante la cual:

Declare que la parte demandada ocupa el inmueble sito en [LOCALIDAD] sin título alguno y sin pagar renta y, en consecuencia, en situación de precario.

Decrete el desahucio solicitado, condenando a la parte demandada a desalojar el inmueble, dejándolo vacío y a disposición de esta parte, en el plazo que fije la resolución judicial, apercibiéndole de lanzamiento en caso de incumplimiento, lanzamiento que tendrá lugar el día y hora que se señala en el decreto de admisión de la demanda.

Se condene expresamente en costas a la parte demandada.

OTROSÍ PRIMERO DIGO que al amparo del artículo 438.6 de la LEC se aperciba a la parte demandada, en el requerimiento que se le realice, de que, en caso de no comparecer a la vista, se declarará el desahucio sin más trámites, y que se entenderá citado para recibir la notificación de la Sentencia que se dicte el sexto día siguiente al señalado para la celebración de la vista.

SUPLICO AL TRIBUNAL se sirva acordar de conformidad el anterior Otrosí.

OTROSÍ SEGUNDO DIGO que, de conformidad con lo dispuesto en la nueva redacción de los artículos 437.3, 438.7 y 549.3 LEC, por medio del presente escrito vengo a solicitar que la fecha del lanzamiento se señale dentro del plazo de un mes a contar desde la celebración de la vista y se tenga por solicitada la ejecución directa de la Sentencia condenatoria que se pueda dictar y el lanzamiento de la parte demandada, en la fecha y hora que se fije por el Tribunal en el Decreto de admisión a trámite de la demanda o en la propia Sentencia, para obtener el lanzamiento de forma directa y sin más trámites, y en su virtud,

AL TRIBUNAL SUPLICO se sirva señalar fecha para el lanzamiento en el Decreto de admisión a trámite de la demanda dentro del plazo legalmente previsto y tener por solicitada la ejecución directa de la Sentencia de desahucio que se dicte, sin necesidad de demanda de ejecución ni más trámites.

OTROSÍ TERCERO DIGO que esta parte manifiesta su firme voluntad de subsanar todos los defectos en que pueda incurrir el presente procedimiento, y ello de conformidad con el artículo 231 de la LEC.

SUPLICO AL TRIBUNAL se sirva tener por hecha la anterior manifestación a los efectos legales oportunos.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma Letrado Firma Procurador
