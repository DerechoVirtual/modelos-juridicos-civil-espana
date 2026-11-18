---
name: demanda-desahucio-rentas-atrasadas-arrendamiento-uso-1256
description: "Redacta el escrito «Demanda de desahucio y rentas atrasadas en arrendamiento para uso distinto de vivienda» (formulario 1256 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de desahucio y rentas atrasadas en arrendamiento para uso distinto de vivienda

> Formulario 1256 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] LOCALIDAD (3 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] Nº DE COLEGIADO
- [ ] CALLE (2 veces)
- [ ] DNI/NIE
- [ ] IMPORTE (8 veces)
- [ ] ÓRGANO
- [ ] NÚMERO (3 veces)
- [ ] FECHA (2 veces)
- [ ] Nº
- [ ] LUGAR
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…del Ilustre Colegio de la Abogacía de»; «…ompañan a la demanda. Mi representado es»; «…euros»; «…euros. Desde el mes de»; «…olución por el Banco por falta de fondos»; «…de meses,»; «…en concepto de cantidades asimiladas por»; «…rajudicial. En este sentido, se acudió a»

## Elecciones que hay que hacer

- Procede / No procede

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: No procede / No procede / Procede — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Todo o parte / Las costas — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Requerir al demandado / No oposición, lanzamiento / Oposición, se dicte sentencia — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 438.5 y 6 de la LEC
- art. 438 de la LEC
- artículos 437.3 y 549.3 de la LEC
- art. 437.1 LEC
- art. 5 de la Ley Orgánica 1/2025
- artículo 437 de la LEC

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

### Formulario 1256 · Demanda de desahucio y rentas atrasadas en arrendamiento para uso distinto de vivienda

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 1 desplegables convertidos en elección en blanco; 3 bloques de opciones sin texto dejados en blanco con sus rótulos; 37 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE COLEGIADO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DEQ.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de [NOMBRE DEL REPRESENTADO/A], con domicilio en [LOCALIDAD], representación que acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO]; bajo la dirección letrada de D./Dña [NOMBRE Y APELLIDOS], abogado/a en ejercicio, con despacho profesional abierto en [LOCALIDAD], colegiado nº [Nº DE COLEGIADO] del Ilustre Colegio de la Abogacía de [COMPLETAR], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO:

Que mediante el presente escrito interpongo demanda a tramitar por el cauce del juicio verbal con las especialidades recogidas en el art. 438.5 y 6 de la LEC, en ejercicio de las acciones acumuladas de desahucio por falta de pago con resolución de contrato por desahucio por falta de pago contra el arrendatario para uso distinto del de vivienda D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, casado/a, con domicilio en [LOCALIDAD], C/ [CALLE] y DNI n.º [DNI/NIE], y de reclamación de la cantidad de [IMPORTE] euros en concepto de rentas atrasadas más las cantidades que vayan venciendo en concepto de rentas y cantidades asimiladas hasta la efectiva entrega del inmueble e intereses de todo ello, con base en los siguientes

Hechos

Se presenta listado de documentos que acompañan a la demanda.

Mi representado es [COMPLETAR] del local de negocio situado en la C/ [CALLE] de esta ciudad, según acredito mediante [ÓRGANO], que presento como doc. n.º [NÚMERO]

En fecha [FECHA], el propietario firmó contrato de arrendamiento con D./Dña. [NOMBRE Y APELLIDOS], tal como consta en el doc. n.º [NÚMERO] que adjuntamos como prueba. La renta estipulada ascendía a [IMPORTE] euros mensuales. La fianza que en ese momento se entregó ascendía al importe de [IMPORTE] euros [COMPLETAR].

En la actualidad la renta vigente es de [IMPORTE] euros.

Desde el mes de [COMPLETAR] los recibos presentados al cobro no han sido atendidos y se procede a la devolución por el Banco por falta de fondos [COMPLETAR]. Lo impagado asciende en este momento a [IMPORTE] euros, resultado de multiplicar la renta mensual vigente por el n.º [Nº] de meses, [COMPLETAR] que no se han liquidado, y sumar [IMPORTE] euros en concepto de cantidades asimiladas por [COMPLETAR].

[NOMBRE Y APELLIDOS], y sumar el IVA.

A pesar de los requerimientos tendentes a evitar la vía judicial, doc. n.º [NÚMERO], finalmente nos vemos obligados a acudir al Tribunal en defensa de los derechos de mi representado, reclamando la cantidad de [IMPORTE] euros.

[ELEGIR UNA OPCIÓN Y REDACTARLA: No procede / No procede / Procede — el texto de cada opción no venía en el formulario original]

. Esta parte asume el compromiso de condonar (opciones):

[ELEGIR UNA OPCIÓN Y REDACTARLA: Todo o parte / Las costas — el texto de cada opción no venía en el formulario original]

Sobre el proceso de negociación previo y medios de solución de controversias de manera amistosa y extrajudicial.

Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

Fundamentos de derecho

Los artículos 21 y 22 de la Ley Orgánica del Poder Judicial y artículo 36 de la Ley de Enjuiciamiento Civil declaran que la jurisdicción competente en esta materia es la española, y el art. 85.1º LOPJ y arts. 45 y 52.1.7.º de la Ley de Enjuiciamiento Civil atribuyen la competencia al Tribunal al que nos dirigimos por encontrarse la finca dentro de la zona de su jurisdicción.

Del cauce del juicio verbal con técnica monitoria: El artículo 437.4.3.ª, en concordancia con el artículo 71.2 de la Ley de Enjuiciamiento Civil permite la acumulación por el cauce del juicio verbal de acciones de reclamación de rentas o cantidades análogas vencidas y no pagadas, cualquiera que sea la cantidad reclamada, cuando se trate de juicios de desahucio de finca por falta de pago.

Deben tenerse en cuenta, no obstante, las especialidades reguladas en los apartados 5 y 6 del art. 438 de la LEC, según las cuales el Letrado de la Administración de Justicia requerirá en el emplazamiento al demandando para que en el plazo de 10 días proceda a enervar si tiene derecho a ello, pagar y desalojar el inmueble, o formular oposición alegando sucintamente las razones por las que no procede el desahucio. Indicará igualmente en esta resolución la fecha de la eventual vista y la del lanzamiento, con apercibimiento de inmediato lanzamiento si no formulare oposición.

– De la ejecución directa si se dicta sentencia estimatoria o auto o decreto que ponga fin al procedimiento: Los artículos 437.3 y 549.3 de la LEC permiten solicitar en la demanda la ejecución directa del lanzamiento, y a tal fin en la resolución que se dicte citando a juicio se señalará ya día y hora para tal actuación, que se llevará a efecto en tal fecha. Cuando se solicitase en la demanda la recuperación de la posesión de una vivienda o parte de ella, aquélla podrá dirigirse genéricamente contra los desconocidos ocupantes de la misma, sin perjuicio de la notificación que de ella se realice a quien en concreto se encontrare en el inmueble al tiempo de llevar a cabo dicha notificación. A la demanda se deberá acompañar el título en que el actor funde su derecho a poseer.

– De la cuantía del pleito: La cuantía del procedimiento se fija en [IMPORTE] euros, en aplicación del artículos 251.3.ª y 9.ª y 252.2 de la Ley de Enjuiciamiento Civil, que afirma que si las acciones acumuladas son las de desahucio y reclamación de rentas o cantidades debidas la cuantía de la demanda vendrá determinada por la acción de mayor valor, es decir, o una anualidad de renta o el importe de la cuantía reclamada.

La activa corresponde al propietario del inmueble y la pasiva al inquilino que no paga la renta en aplicación del artículo 10 de la Ley de Enjuiciamiento Civil por ser ambos los titulares de la relación jurídica de la que deriva la deuda.

Los artículos 23 y 31 del mismo texto legal exigen la intervención de procurador y abogado cuando la cuantía del pleito exceda de 2.000 euros.

Cumplimiento de los requisitos de procedibilidad. La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC en relación con el art. 437.1 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Primero.– Los artículos 27.2.a) y 35 de la Ley de Arrendamientos Urbanos de 1994 recogen la posibilidad de promover la resolución del contrato de pleno derecho en los casos de falta de pago.

Segundo.– Artículo 1555.1 del Código Civil por el que el arrendatario está obligado a pagar el precio del arrendamiento en los términos convenidos, y artículo 220.2 de la Ley de Enjuiciamiento Civil que permite reclamar prestaciones periódicas que se devenguen con posterioridad al momento de dictar sentencia y en el caso presente de acumulación de acción de desahucio y de pago de rentas, la sentencia incluirá la condena al pago de las rentas que se devenguen desde la presentación de la demanda hasta la entrega de la finca.

Tercero.– Artículo 1569.2 del Código Civil: el arrendador puede desahuciar judicialmente al arrendatario por no pagar el precio convenido.

Cuarto.– El Reglamento del Impuesto sobre la Renta de las Personas Físicas obliga a practicar una retención sobre los rendimientos procedentes de arrendamientos, excluido el IVA.

Quinto.– Artículo 36 de la Ley de Arrendamientos Urbanos de 1994, sobre el destino de la fianza.

Sexto.– [ELEGIR: Procede / No procede] enervar la presente acción en aplicación de los artículos 22.4 y 439.3 de la Ley de Enjuiciamiento Civil, regulación que ha de hacerse extensiva al caso de acumulación de acciones de desahucio y reclamación de cantidad.

Séptimo.– Artículo 438.5 de la Ley de Enjuiciamiento Civil: En el requerimiento, se apercibirá al demandado de que en los diez días siguientes a esta notificación desaloje el inmueble, pague al actor o, en caso de pretender la enervación, pague la totalidad de lo que deba o ponga a disposición de aquel en el tribunal o notarialmente el importe de las cantidades reclamadas en la demanda y el de las que adeude en el momento de dicho pago enervador del desahucio. En todo caso se fijará el día y la hora para que tenga lugar, en su caso, el lanzamiento, que deberá producirse antes de treinta días desde la fecha señalada para la vista, advirtiendo al demandado de que si la sentencia es condenatoria y no se recurre, se procede al lanzamiento sin notificación posterior.

Octavo.– El artículo 437 de la LEC permite en las demandas de desahucio anunciar que el arrendador asume el compromiso de condonar todo o parte de la deuda y las costas si el arrendatario abandona la finca en el plazo que indique aquél, que no podrá ser inferior a quince días desde que se notifique la demanda. Cuando se solicitase en la demanda la recuperación de la posesión de una vivienda o parte de ella, aquélla podrá dirigirse genéricamente contra los desconocidos ocupantes de la misma, sin perjuicio de la notificación que de ella se realice a quien en concreto se encontrare en el inmueble al tiempo de llevar a cabo dicha notificación. A la demanda se deberá acompañar el título en que el actor funde su derecho a poseer.

En aplicación del artículo 394 de la Ley de Enjuiciamiento Civil las costas deben imponerse a la otra parte.

En aplicación del artículo 576 de la Ley de Enjuiciamiento Civil, se impondrá también la obligación de pagar intereses sobre la cantidad adeudada.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito junto con los documentos que acompaño, lo admita el Letrado de la Administración de Justicia y, previos los trámites legales oportunos, acuerde:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Requerir al demandado / No oposición, lanzamiento / Oposición, se dicte sentencia — el texto de cada opción no venía en el formulario original]

Es justicia que pido en [LUGAR], a [FECHA].

Procurador/a	Abogado/a

Fdo. D./Dña. [NOMBRE Y APELLIDOS]: 	Fdo. D./Dña. [NOMBRE Y APELLIDOS]:

========================================================================
