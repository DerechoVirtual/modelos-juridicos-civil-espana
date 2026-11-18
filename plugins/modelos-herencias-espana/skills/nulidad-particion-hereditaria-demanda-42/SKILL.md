---
name: nulidad-particion-hereditaria-demanda-42
description: "Redacta el escrito «Nulidad de la partición hereditaria: demanda» (formulario 42 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Nulidad de la partición hereditaria: demanda

> Formulario 0042 del plugin **Sucesiones** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] DNI/NIE
- [ ] FECHA (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] Nº DE DOCUMENTO
- [ ] LOCALIDAD
- [ ] IMPORTE
- [ ] STS 26 de noviembre de 1974 y 3 de febrero de 1992 
- [ ] Sentencias de 16 mayo 1984 y 17 diciembre 1988 
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… domicilio a efecto de notificaciones en»; «…do/a de la Administración de Justicia de»; «…)»; «… domicilio a efecto de notificaciones en»; «…o/a es hijo/a de D./Dña, que falleció el»; «…ha …. otorgada ante el Iltre. Notario de»; «…otorgada ante el Iltre. Notario de»; «…rajudicial. En este sentido, se acudió a»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 5 de la Ley Orgánica 1/2025
- artículo 1.081 del Código Civil
- art. 1261 del Código Civil
- artículos 1300 a 1314 del Código Civil

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

### Formulario 0042 · Nulidad de la partición hereditaria: demanda

- Año del modelo: 2024
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 1 rangos de artículos despegados («25 a31» → «25 a 31»); 26 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] QUE POR TURNO CORRESPONDA

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de [NOMBRE DEL REPRESENTADO/A], mayor de edad, con DNI [DNI/NIE] y domicilio a efecto de notificaciones en [COMPLETAR], según se acredita por certificación del registro electrónico de apoderamientos judiciales que acompaño (o mediante designación apud acta ante el/la Letrado/a de la Administración de Justicia de [COMPLETAR]) [COMPLETAR], actuando bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco y como mejor proceda en Derecho,

DIGO:

Que en la representación que ostento, por medio del presente escrito, formulo DEMANDA DE JUICIO ORDINARIO EN EJERCICIO DE LA ACCIÓN DE NULIDAD DE PARTICIÓN DE LA HERENCIA de D./Dña [NOMBRE Y APELLIDOS] contra D./Dña. [NOMBRE Y APELLIDOS], con domicilio a efecto de notificaciones en [COMPLETAR]. Todo ello sobre la base de los siguientes,

HECHOS

PRIMERO.- Mi representado/a es hijo/a de D./Dña, que falleció el [COMPLETAR]

Se acompaña certificado de defunción de D./Dña .como Documento núm. 1.

SEGUNDO En fecha [FECHA] se procedió a la apertura del testamento otorgado por el/la causante, resultando que éste/a instituyó heredero/a a D./Dña, legando a mi mandante lo que le correspondiese por legítima.

Se acompaña como Documento núm. 2 la escritura testamento notarial abierto de fecha …. otorgada ante el Iltre. Notario de [COMPLETAR] D./Dña con número [NÚMERO] de su protocolo.

TERCERO El objeto de la presente demanda es la impugnación de la partición de la herencia efectuada en virtud de escritura notarial de fecha [FECHA] otorgada ante el Iltre. Notario de [COMPLETAR] D./Dña con número [NÚMERO] de su protocolo.

Se acompaña como Documento núm. 3 copia de dicha escritura.

CUARTO En virtud de la mencionada escritura, el caudal relicto del/ de la causante estaba conformado por los siguientes bienes:

Los bienes fueron adjudicados de la siguiente forma:

QUINTO Con posterioridad al otorgamiento de la escritura de partición y adjudicación de herencia, mi mandante ha tenido conocimiento de que se incluyó de manera fraudulenta un bien al caudal relicto del /de la causante, cuando, en realidad, éste/ésta no era propietario/a del mismo.

Se trata del siguiente bien:

El mencionado bien no pertenecía al/ a la causante en la medida en que se trataba de un bien privativo del padre/ de la madre de mis mandantes.

Asimismo, se ha tenido conocimiento de que D./Dña procedió a la venta de dicho bien, distrayendo así el bien inmueble del caudal hereditario en perjuicio de terceros.

SEXTO La adjudicación efectuada es nula por ser contraria a las normas imperativas y prohibitivas, adoleciendo, asimismo, de falta de un elemento esencial del negocio, al haber sido realizada sobre un objeto que no pertenecía al caudal de la herencia del/ de la causante.

SÉPTIMO Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

A los anteriores hechos, le son de aplicación los siguientes,

FUNDAMENTOS DE DERECHO

PRIMERO. - JURISDICCIÓN Y COMPETENCIA

Al amparo de lo establecido en el artículo 52.4º de la Ley de Enjuiciamiento Civil, corresponde a los Tribunales de Instancia de [LOCALIDAD] por ser los del lugar en que el difunto tuvo su último domicilio.

SEGUNDO. – PROCEDIMIENTO Y CUANTÍA

En virtud de lo establecido en el artículo 249.2 de la Ley de Enjuiciamiento Civil, no existiendo un cauce especialmente previsto, el procedimiento se regirá por los cauces del juicio ordinario por ser de cuantía superior a 15.000 euros.

Se fija la cuantía del procedimiento en [IMPORTE] euros, de conformidad con lo establecido en los artículos 251 y 253 de la Ley de Enjuiciamiento Civil.

TERCERO. – CAPACIDAD Y LEGITIMACIÓN

Las partes poseen capacidad para intervenir en el presente procedimiento, al amparo de lo establecido en el artículo 6 y siguientes de la Ley de Enjuiciamiento Civil.

El artículo 10 de la Ley de Enjuiciamiento Civil legitima para comparecer y actuar en juicio, a los titulares de la relación jurídica o del objeto litigioso.

La legitimación activa la ostenta mi mandante en su condición de legatario/a del causante.

La legitimación pasiva corresponde al/la demandado/a, en su condición de heredero/a de D./ Dña. [NOMBRE Y APELLIDOS]

CUARTO. - REPRESENTACIÓN PROCESAL

La parte actora comparece debidamente representada por Abogado y Procurador, tal como prevén los artículos 23.1 y 31.1 de la Ley de Enjuiciamiento Civil.

QUINTO.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

SEXTO. - FONDO DEL ASUNTO

No existe en el Código Civil una regulación específica de la nulidad de la partición de la herencia, a excepción de lo previsto en el artículo 1.081 del Código Civil que determina que es nula la partición hecha con quien se creyó heredero sin serlo.

No obstante, la jurisprudencia ha venido entendiendo que, cuando la partición tenga naturaleza contractual, le serán de aplicación las causas de inexistencia, nulidad y anulabilidad de los contratos.

De esta forma, si la partición hereditaria contractual se ha realizado con algún vicio del consentimiento o de capacidad, ésta podrá ser anulada [STS 26 de noviembre de 1974 y 3 de febrero de 1992 ].

Será preciso, por tanto, distinguir entre nulidad absoluta o radical y anulabilidad o nulidad relativa. Estaremos ante un supuesto de nulidad radical o de pleno derecho de la adjudicación hereditaria cuando no concurran los requisitos establecidos en el art. 1261 del Código Civil o se vulneren normas imperativas o prohibitivas, mientras que, cuando la partición tenga naturaleza de contrato, le serán aplicables las reglas previstas en los artículos 1300 a 1314 del Código Civil (SSTS de 26 marzo 1940, 7 enero 1949, 9 marzo 1951, 2 noviembre 1957, 29 marzo 1958, 13 octubre 1960, 25 noviembre 1965, 25 febrero 1966, 26 noviembre 1974 y 7 enero 1975, 12 de diciembre de 2005, rec. 506/1999 y 7 de noviembre de 2006, rec. 5237/1999, entre otras.

Como recuerda la Sentencia de la Audiencia Provincial de A Coruña núm. 4863/2009 de 17 de noviembre, “como supuestos de anulabilidad se han considerado las particiones verificadas mediando un vicio del consentimiento, es decir, violencia, intimidación o dolo (Sentencia de 26 noviembre 1974), o las realizadas con infracción de lo

dispuesto en el artículo 1057-III CC por no haberse citado por el contador partidor para la práctica del inventario a los coherederos, acreedores o legatarios cuando entre los coherederos haya un menor de edad o sujeto a tutela [Sentencias de 16 mayo 1984 y 17 diciembre 1988 ]".

La nulidad total o parcial de la adjudicación hereditaria vendrá determinada por la inexistencia de sus elementos esenciales o su inexacta constitución, incluido el defecto de su objeto por comprender bienes de terceros y no del causante o con alteración fáctica o jurídica del concepto atributivo de su dominio o titularidad, por ejemplo, si se califican de gananciales bienes que son privativos del otro cónyuge [SSTS 14-2-1989 y 22-2-1997, rec. 1235/1993).

SÉPTIMO. - IURA NOVIT CURIA

En todo lo no invocado en la presente demanda, opera el principio iura novit curia.

OCTAVO. - COSTAS

Deberán ser impuestas a la parte demandada en virtud de lo establecido en el artículo 394 de la Ley de Enjuiciamiento Civil.

En su virtud,

AL TRIBUNAL SUPLICO: Que teniendo por presentado este escrito junto con sus copias y documentos que le acompañan, se sirva admitirlo, teniendo por formulada DEMANDA DE JUICIO ORDINARIO EN EJERCICIO DE LA ACCIÓN DE NULIDAD DE PARTICIÓN DE LA HERENCIA el/la Sr./Sra. contra D./Dña. [NOMBRE Y APELLIDOS] y, en su virtud, previos los trámites legales oportunos, dicte en su día sentencia por la que:

a) Se declare la nulidad de la escritura de partición y adjudicación de herencia que se otorgó el día [FECHA] ante el Notario D./Dña. [NOMBRE Y APELLIDOS], con número …. de protocolo, por ser contraria a las normas imperativas y prohibitivas, así como por falta de un elemento esencial del negocio jurídico.

b) Se rectifique la mencionada escritura en los términos expuestos en el cuerpo de la presente demanda.

c) Se impongan las costas a la parte demandada.

OTROSÍ PRIMERO DIGO: Que en virtud de lo establecido en el artículo 231 de la Ley de Enjuiciamiento Civil esta parte

AL TRIBUNAL SUPLICO: Que tenga por hecha la anterior manifestación a los efectos oportunos.

En [LUGAR], a [FECHA].

Ldo.

Proc.
