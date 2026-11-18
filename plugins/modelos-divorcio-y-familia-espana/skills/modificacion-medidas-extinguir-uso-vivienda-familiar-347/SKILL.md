---
name: modificacion-medidas-extinguir-uso-vivienda-familiar-347
description: "Redacta el escrito «Modificación de medidas para extinguir el uso de la vivienda familiar por un tercero» (formulario 347 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Modificación de medidas para extinguir el uso de la vivienda familiar por un tercero

> Formulario 0347 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] COLEGIO
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] FECHA (3 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] LUGAR
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Don»; «…nales, en nombre y representación de Don»; «…os, y que es dirigido por el Letrado Don»; «…CIÓN DE MEDIDAS DEFINITIVAS, contra Doña»; «…, cuyo domicilio es»; «…damentos de derecho: HECHOS PRIMERO Doña»; «…hijos menores, con una nueva pareja, Don»; «…rajudicial. En este sentido, se acudió a»; «…ación de medidas definitivas contra Doña»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 775.1 LEC
- arts. 81, 86, 90 y 91 CCiv
- art. 770 LEC
- art. 749.2 LEC
- art. 437.1 LEC
- art. 5 de la Ley Orgánica 1/2025
- arts. 90 y 91 CCiv
- artículo 96 del Código Civil
- art. 96 CCiv
- art. 394 LEC
- Ley 42/2015

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

### Formulario 0347 · Modificación de medidas para extinguir el uso de la vivienda familiar por un tercero

- Año del modelo: 2019
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 19 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda contenciosa en procedimiento de modificación de medidas definitivas, solicitando la extinción del derecho de uso sobre la vivienda familiar por la convivencia del progenitor custodio de los hijos con una nueva pareja.

Adaptado a la LO 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia

AL TRIBUNAL DE INSTANCIA DE [SEDE]

SECCIÓN CIVIL

SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD
 [NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]
Don [COMPLETAR], Procurador de los Tribunales, en nombre y representación de Don [COMPLETAR], según acredito con aportación de la copia de la escritura de poderes, a la que se acompaña reproducción para testimonio bastante en los autos y devolución de la auténtica, que se necesita para otros usos, y que es dirigido por el Letrado Don [COMPLETAR], ejerciente en el Iltre. Colegio de Abogados de [COLEGIO], y con despacho abierto en [LOCALIDAD], calle [CALLE] n.º [NÚMERO], ante el Tribunal comparezco y, como mejor proceda en Derecho, DIGO:

Que mediante el presente escrito, formulo DEMANDA DE MODIFICACIÓN DE MEDIDAS DEFINITIVAS, contra Doña [COMPLETAR], cuyo domicilio es [COMPLETAR], basándola en los siguientes hechos y fundamentos de derecho:

HECHOS

PRIMERO

Doña [COMPLETAR] y mi representado se hallan separados en virtud de sentencia de fecha [FECHA], dictada por este Tribunal en los autos n.º [Nº DE PROCEDIMIENTO]/[AÑO], en cuyo fallo, entre otras medidas definitivas, se acordó en relación a la vivienda familiar, de naturaleza ganancial:

"Atribuir a los hijos menores de edad el uso y disfrute del domicilio familiar, sito en -----, así como el ajuar doméstico, quienes vivirán en compañía de su madre, como progenitor que ostentará la guarda y custodia, sin perjuicio de que Don [NOMBRE Y APELLIDOS] ----- retire previo inventario sus efectos personales"

SEGUNDO

Dicha sentencia, que es firme y ejecutiva, no ha sido modificada por ninguna otra resolución firme. Se acompaña copia de la sentencia como documento número [Nº DE DOCUMENTO]

TERCERO

En el momento de dictarse la sentencia de separación el interés familiar más digno de protección era el de los dos hijos entonces menores, y como consecuencia el del progenitor custodio en cuya compañía quedaban los mismos.

CUARTO

En la actualidad, la demandada convive en el domicilio familiar, junto a los hijos menores, con una nueva pareja, Don [COMPLETAR], como se demostrará mediante prueba de fuente personal que se articulará en su momento procesal idóneo.

QUINTO

Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA

Conforme a lo establecido por el art. 775.1 LEC, en la redacción dada por la Ley 42/2015, de 5 de octubre, es competente para conocer del presente procedimiento el Tribunal al que me dirijo, por ser el que acordó la medida que se quiere modificar.

II.- LEGITIMACIÓN

La legitimación activa y pasiva para intervenir en el procedimiento corresponde a ambos cónyuges (arts. 81, 86, 90 y 91 CCiv).

III.- PROCEDIMIENTO

La modificación de las medidas definitivas tiene asignado el procedimiento previsto en el art. 770 LEC, o lo que es lo mismo, los trámites del procedimiento principal de separación y divorcio, de conformidad con el art. 775.2, dado que no son de mutuo acuerdo o propuestas por un cónyuge con el consentimiento del otro.

IV.- INTERVENCIÓN DEL MINISTERIO FISCAL

De conformidad con lo dispuesto en el art. 749.2 LEC, afectando la medida cuya modificación se insta a hijos menores de edad, es preceptiva la intervención del Ministerio Fiscal.

V.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 en relación con el art. 437.1 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VI.- FUNDAMENTOS DE DERECHO MATERIALES O SOBRE EL FONDO DEL ASUNTO

Los arts. 90 y 91 CCiv señalan que las medidas que el Juez acuerde en defecto de acuerdo o las convenidas por los cónyuges, podrán ser modificadas judicialmente o por nuevo convenio cuando se alteren sustancialmente las circunstancias, prevención que es presupuesto de este proceso, según la mención explícita del art. 775.1 LEC.

En este sentido, la STS -Pleno- de 20 de noviembre de 2018, rec. 982/2018, fija como doctrina que "La introducción de un tercero en la vivienda en manifiesta relación estable de pareja con la progenitora que se benefició del uso por habérsele asignado la custodia de los hijos, aspecto que se examina, cambia el estatus del domicilio familiar. No se niega que al amparo del derecho a la libertad personal y al libre desarrollo de la personalidad se puedan establecer nuevas relaciones de pareja con quien se estime conveniente, lo que se cuestiona es que esta libertad se utilice en perjuicio de otros, en este caso del progenitor no custodio. Una nueva relación de pareja, tras la ruptura del matrimonio, tiene evidente influencia en la pensión compensatoria, en el derecho a permanecer en la casa familiar e incluso en el interés de los hijos, desde el momento en que introduce elementos de valoración distintos de los que se tuvieron en cuenta inicialmente y que, en relación a lo que aquí se cuestiona, se deberán tener en cuenta, sin perder de vista ese interés de los hijos, que es el que sirvió de título de atribución del uso, al amparo del artículo 96 del Código Civil".

En relación al precitado art. 96 CCiv, el TS establece lo siguiente: "hay dos factores que eliminan el rigor de la norma cuando no existe acuerdo previo entre los cónyuges: uno, el carácter no familiar de la vivienda sobre la que se establece la medida, entendiendo que una cosa es el uso que se hace de la misma vigente la relación matrimonial y otra distinta que ese uso permita calificarla de familiar si no sirve a los fines del matrimonio porque los cónyuges no cumplen con el derecho y deber propio de la relación. Otro, que el hijo no precise de la vivienda por encontrarse satisfechas las necesidades de habitación a través de otros medios; solución que requiere que la vivienda alternativa sea idónea para satisfacer el interés prevalente del menor (sentencias 671/2012, de 5 de noviembre;284/2016, de 3 de mayo;646/2017, de 27 de noviembre y 181/2018 de 4 abril)".

Manifiesta el Alto Tribunal que "El derecho de uso de la vivienda familiar existe y deja de existir en función de las circunstancias que concurren en el caso. Se confiere y se mantiene en tanto que conserve este carácter familiar. La vivienda sobre la que se establece el uso no es otra que aquella en que la familia haya convivido como tal, con una voluntad de permanencia (sentencia 726/2013, de 19 de noviembre). En el presente caso, este carácter ha desaparecido, no porque la madre e hijos hayan dejado de vivir en ella, sino por la entrada de un tercero, dejando de servir a los fines del matrimonio. La introducción de una tercera persona hace perder a la vivienda su antigua naturaleza «por servir en su uso a una familia distinta y diferente», como dice la sentencia recurrida".

Asimismo, concluye el TS que "El interés de los hijos no puede desvincularse absolutamente del de sus padres, cuando es posible conciliarlos. El interés en abstracto o simplemente especulativo no es suficiente y la misma decisión adoptada en su día por los progenitores para poner fin al matrimonio, la deben tener ahora para actuar en beneficio e interés de sus hijos respecto de la vivienda, una vez que se ha extinguido la medida inicial de uso, y que en el caso se ve favorecida por el carácter ganancial del inmueble y por la posibilidad real de poder seguir ocupándolo si la madre adquiere la mitad o se produce su venta y adquiere otra vivienda".

VII.- COSTAS

No hay razón para inaplicar el principio del vencimiento en punto a costas procesales, en armonía con el art. 394 LEC, a fin de que esta parte salga indemne de que se le reconozca su derecho frente a la resistencia de la demandada.

En su virtud,

SUPLICO AL TRIBUNAL

que, habiendo por presentado este escrito junto con los documentos y copias que se acompañan, se sirva admitirlo, teniéndome por parte en la representación que acredito y por formulada demanda de modificación de medidas definitivas contra Doña [COMPLETAR], y previos los trámites legales, se dicte sentencia por la que se decrete la extinción del uso y disfrute de la vivienda que constituyó el domicilio familiar a favor de la esposa e hijos del actor establecida en la sentencia de separación de fecha [FECHA], dictada en proceso contencioso / seguido en este Tribunal, pudiendo las partes proceder a la venta de la misma o a su adjudicación a uno de ellos con el consiguiente abono al otro del importe correspondiente, con expresa condena en costas a la parte demandada.

Por ser de justicia que solicito en [LUGAR], a [FECHA].

Firma de Abogado/a

	Firma de Procurador/a
