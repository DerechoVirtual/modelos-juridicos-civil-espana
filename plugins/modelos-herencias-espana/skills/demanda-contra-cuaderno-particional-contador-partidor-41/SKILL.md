---
name: demanda-contra-cuaderno-particional-contador-partidor-41
description: "Redacta el escrito «Demanda contra el cuaderno particional del contador-partidor dativo de notaría» (formulario 41 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda contra el cuaderno particional del contador-partidor dativo de notaría

> Formulario 0041 del plugin **Sucesiones** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (19 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] DNI/NIE
- [ ] NÚMERO (5 veces)
- [ ] FECHA (6 veces)
- [ ] IMPORTE (3 veces)
- [ ] Nº DE DOCUMENTO
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… domicilio a efecto de notificaciones en»; «…rado de la Administración de Justicia de»; «… domicilio a efecto de notificaciones en»; «…, que falleció el»; «…ha …. otorgada ante el Iltre. Notario de»; «…otorgada ante el Iltre. Notario de»; «…uaderno particional elevado a público el»; «…itura otorgada ante el Iltre. Notario de»; «…ional otorgada ante el Iltre. Notario de»; «…asciende a»; «…SEXTO»; «…rajudicial. En este sentido, se acudió a»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 5 de la Ley Orgánica 1/2025
- artículo 1073 del Código Civil
- artículo 1074 del Código Civil
- artículo 1077 del Código Civil
- artículo 1076 del Código Civil

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

### Formulario 0041 · Demanda contra el cuaderno particional del contador-partidor dativo de notaría

- Año del modelo: 2024
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 49 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario revisado conforme a la LO 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] QUE POR TURNO CORRESPONDA

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de [NOMBRE DEL REPRESENTADO/A], mayor de edad, con DNI [DNI/NIE] y domicilio a efecto de notificaciones en [COMPLETAR], según se acredita por certificación del registro electrónico de apoderamientos judiciales que acompaño (o mediante designación apud acta ante el Letrado de la Administración de Justicia de [COMPLETAR]), actuando bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco y como mejor proceda en Derecho,

DIGO:

Que en la representación que ostento, por medio del presente escrito, formulo DEMANDA DE JUICIO ORDINARIO EN EJERCICIO DE LA ACCIÓN DE RESCISIÓN DE LAS OPERACIONES DIVISORIAS realizadas por el contador partidor dativo de la herencia de D./Dña [NOMBRE Y APELLIDOS] contra D./Dña. [NOMBRE Y APELLIDOS] D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS], todos ellos domicilio a efecto de notificaciones en [COMPLETAR]. Todo ello sobre la base de los siguientes,

HECHOS

PRIMERO.- Mi representado, junto con los codemandados, es heredero de D./Dña. [NOMBRE Y APELLIDOS], que falleció el [COMPLETAR]

Se acompaña como Documento núm. 1 la escritura testamento notarial abierto de fecha …. otorgada ante el Iltre. Notario de [COMPLETAR] D./Dña con número [NÚMERO] de su protocolo.

Se acompaña certificado de defunción de D./Dña como Documento núm. 2.

SEGUNDO El objeto de la presente demanda es la impugnación del cuaderno particional realizado por D./Dña [NOMBRE Y APELLIDOS] contador partidor dativo de la herencia de D./Dña designado en virtud de escritura notarial de fecha [FECHA] otorgada ante el Iltre. Notario de [COMPLETAR] D./Dña con número [NÚMERO] de su protocolo.

Se acompaña como Documento núm. 3 copia de dicha escritura.

TERCERO.- El designado contador partidor, tras haber dispuesto los objetos que le eran necesarios, ha realizado y presentado el cuaderno particional con el inventario, avalúo, liquidación y división del caudal hereditario del Sr./Sra, determinando la correspondiente adjudicación a cada partícipe.

Se acompaña como Documento núm. 4 copia del cuaderno particional elevado a público el [COMPLETAR] mediante escritura otorgada ante el Iltre. Notario de [COMPLETAR] D./Dña [NOMBRE Y APELLIDOS] en fecha [FECHA] con número [NÚMERO] de su protocolo.

CUARTO. Que pese a la oposición formulada por mi mandante, el cuaderno particional ha sido aprobado por el Notario designado en fecha [FECHA]

Se acompaña como Documento núm. 5 escritura notarial de aprobación del cuaderno particional otorgada ante el Iltre. Notario de [COMPLETAR] D./Dña [NOMBRE Y APELLIDOS] en fecha [FECHA] con número [NÚMERO] de su protocolo.

QUINTO La adjudicación efectuada a mi mandante le resulta perjudicial respecto a las adjudicaciones realizadas al resto de coherederos en la medida en que la finca atribuida adolece de vicios que aminoran notablemente su valor económico.

Del simple examen del inventario y de las valoraciones dadas a los bienes inmuebles se concluye que existe una lesión a los derechos hereditarios de mi mandante en más de un 25%.

La tasación real de los bienes del causante, conforme al dictamen pericial elaborado por D./Dña. [NOMBRE Y APELLIDOS] asciende a [COMPLETAR], existiendo un exceso en la valoración de los bienes adjudicados a los codemandados, en perjuicio de mi mandante.

Se acompaña como Documento núm. 6 informe pericial elaborado por D./Dña. [NOMBRE Y APELLIDOS]

SEXTO [COMPLETAR]. Al haberse producido una lesión en más de la cuarta parte, se debe rescindir la partición y establecer que la parte que corresponderá a mi mandante será la de [IMPORTE] euros.

SÉPTIMO Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

A los anteriores hechos, le son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

PRIMERO. - JURISDICCIÓN Y COMPETENCIA

Al amparo de lo establecido en el artículo 52.4º de la Ley de Enjuiciamiento Civil, corresponde a los Tribunales de Instancia de [LOCALIDAD] por ser los del lugar en que el difunto tuvo su último domicilio.

SEGUNDO. – PROCEDIMIENTO Y CUANTÍA

En virtud de lo establecido en el artículo 249.2 de la Ley de Enjuiciamiento Civil, no existiendo un cauce especialmente previsto, el procedimiento se regirá por los cauces del juicio ordinario por ser de cuantía superior a 15.000 euros.

Se fija la cuantía del procedimiento en [IMPORTE] euros, de conformidad con lo establecido en los artículos 251 y 253 de la Ley de Enjuiciamiento Civil.

TERCERO. – CAPACIDAD Y LEGITIMACIÓN

Las partes poseen capacidad para intervenir en el presente procedimiento, al amparo de lo establecido en el artículo 6 y siguientes de la Ley de Enjuiciamiento Civil.

El artículo 10 de la Ley de Enjuiciamiento Civil legitima para comparecer y actuar en juicio, a los titulares de la relación jurídica o del objeto litigioso.

La legitimación activa la ostenta mi mandante en su condición de heredero del causante, habiendo sido perjudicado en más de una cuarta parte del valor total del bien adjudicado.

La legitimación pasiva corresponde a los codemandados, en su condición de coherederos de D./ Dña. [NOMBRE Y APELLIDOS]

CUARTO. - REPRESENTACIÓN PROCESAL

La parte actora comparece debidamente representada por Abogado y Procurador, tal como prevén los artículos 23.1 y 31.1 de la Ley de Enjuiciamiento Civil.

QUINTO.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

SEXTO. - FONDO DEL ASUNTO

El artículo 1073 del Código Civil dispone que “las particiones pueden rescindirse por las mismas causas que las obligaciones” y, el artículo 1074 del Código Civil, por su parte que “podrán también ser rescindidas las particiones por causa de lesión en más de la cuarta parte, atendiendo el valor de las cosas cuando fueron adjudicadas”.

En el caso que nos ocupa, el perjuicio causado en la adjudicación de bienes excede de la cuantía prevista en el artículo 1074 del Código Civil, procediendo la rescisión de la partición de la herencia.

En cuanto a los efectos de la rescisión de las operaciones particionales, el artículo 1074 del Código Civil debe ponerse en relación con el artículo 1077 del Código Civil, que ofrece al demandado la opción de indemnizar el daño o consentir que se proceda una nueva partición.

En virtud de lo establecido en el artículo 1076 del Código Civil, la presente acción se interpone dentro del plazo previsto en la norma, esto es, cuatro años desde el momento en que se realizó la partición.

SÉPTIMO. - IURA NOVIT CURIA

En todo lo no invocado en la presente demanda, opera el principio iura novit curia.

OCTAVO. - COSTAS

Deberán ser impuestas a la parte demandada en virtud de lo establecido en el artículo 394 de la Ley de Enjuiciamiento Civil.

En su virtud,

AL TRIBUNAL SUPLICO: Que teniendo por presentado este escrito junto con sus copias y documentos que le acompañan, se sirva admitirlo, teniendo por formulada DEMANDA DE JUICIO ORDINARIO EN EJERCICIO DE LA ACCIÓN DE RESCISIÓN DE LAS OPERACIONES DIVISORIAS contra D./Dña. [NOMBRE Y APELLIDOS], D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] en su calidad de coherederos de la herencia del/la Sr./Sra. [NOMBRE Y APELLIDOS] y, en su virtud, previos los trámites legales oportunos, dicte en su día sentencia por la que:

Se declare la rescisión por lesión en más de la cuarta parte del lote adjudicado al demandante en la partición hereditaria del/ de la causante D./Dña. [NOMBRE Y APELLIDOS], aprobada y protocolizada mediante escritura notarial de fecha [FECHA] otorgada ante el Iltre. Notario de [COMPLETAR] con el número [NÚMERO] de su protocolo.
Se condene a los demandados a consentir una nueva partición ajustada al valor real del caudal relicto o, alternativamente, a su elección, a indemnizar a mi representado en la cantidad de [IMPORTE] euros más los intereses legales devengados desde la fecha de adjudicación.
Se impongan las costas a la parte demandada.

OTROSI PRIMERO DIGO: De acuerdo con lo previsto en el art. 335 y 336 de la Ley de Enjuiciamiento Civil, esta parte aporta con la demanda dictamen pericial y designa como perito a D/Dña. [NOMBRE Y APELLIDOS], autor del referido dictamen, que deberá ser citado con tal carácter de perito al acto del juicio oral, a fin de ratificar el mismo, explicar su contenido y, en definitiva, a los efectos previstos en el art. 347 de la Ley de Enjuiciamiento Civil

SUPLICO AL TRIBUNAL, tenga por hecha la anterior manifestación y por propuesta la prueba pericial para su práctica en el acto del juicio oral

OTROSÍ SEGUNDO DIGO: Que en virtud de lo establecido en el artículo 231 de la Ley de Enjuiciamiento Civil esta parte

AL TRIBUNAL SUPLICO: Que tenga por hecha la anterior manifestación a los efectos oportunos.

En [LUGAR], a [FECHA].

Ldo.

Proc.
