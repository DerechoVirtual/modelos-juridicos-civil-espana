---
name: contestacion-demanda-anulacion-laudo-modelo-generico-1485
description: "Redacta el escrito «Contestación a demanda de anulación de laudo (modelo genérico)» (formulario 1485 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a demanda de anulación de laudo (modelo genérico)

> Formulario 1485 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] NÚMERO
- [ ] LOCALIDAD
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] FECHA (3 veces)
- [ ] STS 21 de marzo de 1991, 15 de diciembre de 1987 y 4 de junio de 1991
- [ ] TS 7 de junio de 1990
- [ ] Nº DE PROCEDIMIENTO
- [ ] LUGAR
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Don/Dª»; «…rito, y bajo la dirección Letrada de Don»; «…esta parte de la demanda formulada por D»; «…dictado por la Corte de Arbitraje de»; «…bitral entre las partes ante la Corte de»; «…OTROSÍ PRIMERO DIGO:»; «…or la secretaría de la Corte Arbitral de»

## Párrafos opcionales (1)

Inclúyelos solo si encajan en los hechos:

- OTROSÍ PRIMERO DIGO: [COMPLETAR]. Que, de conformidad a lo establecido en el artículo 42.1 de la Ley de Arbitr…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 394 LEC

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

### Formulario 1485 · Contestación a demanda de anulación de laudo (modelo genérico)

- Año del modelo: 2014
- Revisión 17-11-2026: 1 párrafos opcionales señalados; 13 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Hechos
Fundamentos de derecho
Firmas

Formulario adaptado a la reforma procesal de la LO 1/2025.

Juicio verbal de impugnación de laudo arbitral número [NÚMERO]

A LA SALA DE LO CIVIL Y DE LO PENAL DEL TRIBUNAL SUPERIOR DE JUSTICIA DE [LOCALIDAD]

Don/Dª [COMPLETAR], Procurador de los Tribunales, en la representación que ostento de D. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, y bajo la dirección Letrada de Don [COMPLETAR], ante la Sala en el juicio verbal arriba expresado comparezco y, como mejor proceda en Derecho, DIGO:

Que habiéndose dado traslado a esta parte de la demanda formulada por D [COMPLETAR] en ejercicio de la acción de anulación del laudo de fecha [FECHA] dictado por la Corte de Arbitraje de [COMPLETAR], siguiendo instrucciones de mi poderdante por medio del presente escrito y en nombre del mismo formulo en tiempo y forma CONTESTACIÓN A LA DEMANDA, la cual baso en los siguientes

Hechos

Primero.- Nos oponemos parcialmente a los hechos relatados en el escrito de demanda, pues si bien se acepta que se siguió el procedimiento arbitral entre las partes ante la Corte de [COMPLETAR] que finalizó con el laudo de fecha [FECHA], en modo alguno se han producido los vicios aducidos por el demandante como motivos de impugnación del laudo.

Segundo.- Frente a la demanda formulada oponemos que la parte demandante no aduce que el laudo haya incurrido en uno de los motivos tasados del artículo 41 de la Ley de Arbitraje, sino que alega la injusticia que supone la resolución del laudo en su contra, pretendiendo una revisión de los hechos enjuiciados por los árbitros, lo cual queda al margen del recurso de anulación, según ha venido interpretando de forma reiterada y constante la Jurisprudencia que ha expresando que, por la vía del recurso de anulación, las partes no pueden volver a plantear la controversia ya resuelta por los árbitros [STS 21 de marzo de 1991, 15 de diciembre de 1987 y 4 de junio de 1991] no siendo misión de los Tribunales en este recurso corregir hipotéticas deficiencias en cuanto a las cuestiones de fondo debatidas [TS 7 de junio de 1990]. Es decir, a este Tribunal sólo le incumbe decidir sobre la regularidad del proceso y la correcta observancia de los principios esenciales por los que ha de regirse, de rogación, bilateralidad, contradicción, igualdad de partes, congruencia y proscripción de cualquier situación de indefensión, todos los cuales se plasman y quedan recogidos en los tasados motivos de nulidad del artículo 41 de la Ley de Arbitraje, cuya interpretación debe ser estricta. En este mismo sentido se ha pronunciado el Tribunal Constitucional en las SSTC 62/91, de 22 de marzo y 228/93 de 4 de octubre.

En definitiva, por medio del denominado recurso de anulación, únicamente se puede proceder al control de las garantías formales que han rodeado la emisión del laudo, pero no alcanza, ni tiene como finalidad, corregir las deficiencias que pudieran existir en la decisión de los árbitros; de ahí que no puede alcanzar a controlar y revisar, por regla general, la decisión de fondo arbitral como ahora pretende la demandante, lo cual debe determinar el acogimiento de esta excepción y la desestimación de la demanda.

Por todo ello, la demanda debe ser desestimada.

Fundamentos de derecho

Conformes con la competencia objetiva y territorial de la Sala, la legitimación «ad procesum», y el procedimiento adecuado escogido, compareciendo esta parte con la debida representación técnica y asistencia letrada.

En cuanto al ejercicio de la acción, nos oponemos por no fundarse la demanda en ninguno de los motivos tasados del artículo 41.1 de la Ley de Arbitraje, pretendiendo el demandante una nueva revisión de los hechos enjuiciados, en contra de la reiterada la interpretación de los tribunales en el sentido de que la acción de anulación no constituye un recurso de apelación que permita una revisión del fondo del asunto por el carácter tasado de los motivos previstos legalmente, a cuyo efecto nos remitimos a la jurisprudencia expresada en los hechos de esta contestación, y citamos la más reciente de las SAP Murcia 18 de febrero de 2010, rec. 587/2009 y SAP Madrid 12 de noviembre de 2010, rec. 3/2010, STSJ Comunidad Valenciana 26 de abril de 2012, rec. 17/2011, entre otras muchas.

Las costas deben imponerse a la actora, de conformidad con lo dispuesto en el artículo 394 LEC.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL que teniendo por presentado este escrito, con sus documentos, y copias de todo ello, se sirva admitirlo, y tenga por formulada CONTESTACIÓN A LA DEMANDA y, tras los trámites legales, dicte Sentencia desestimatoria de la pretensión formulada de contrario, todo ello con expresa imposición de costas a la parte actora.

[OPCIONAL — incluir si procede]

OTROSÍ PRIMERO DIGO: [COMPLETAR]. Que, de conformidad a lo establecido en el artículo 42.1 de la Ley de Arbitraje, esta parte solicita la celebración de vista, proponiendo los siguientes medios de prueba para que se practiquen en la misma:

1) DOCUMENTAL, dando por reproducidos los documentos acompañados en este escrito de contestación.
2) MÁS DOCUMENTAL, a fin que por la secretaría de la Corte Arbitral de [COMPLETAR] se remita copia auténtica de los siguientes documentos presentados por el demandante en el procedimiento arbitral número [Nº DE PROCEDIMIENTO]:

SUPLICO AL TRIBUNAL que tenga hechas las anteriores manifestaciones a los efectos legales que procedan y acuerde de conformidad

Es justicia que pido en [LUGAR], a [FECHA].

Abogado/a	Procurador/a
Fdo. D./Dña. [NOMBRE Y APELLIDOS]:	Fdo. D./Dña. [NOMBRE Y APELLIDOS]:

========================================================================
