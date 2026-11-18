---
name: contestacion-demanda-anulacion-laudo-validez-convenio-1486
description: "Redacta el escrito «Contestación a demanda de anulación de laudo: validez del convenio arbitral» (formulario 1486 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a demanda de anulación de laudo: validez del convenio arbitral

> Formulario 1486 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD (3 veces)
- [ ] FECHA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…a de someterse a la institución arbitral»; «…s a la parte actora. OTROSÍ PRIMERO DIGO»; «…fique la titularidad del establecimiento»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 3.1 del Real Decreto Legislativo 1/2007
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

### Formulario 1486 · Contestación a demanda de anulación de laudo: validez del convenio arbitral

- Año del modelo: 2014
- Revisión 17-11-2026: 9 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Encabezamiento
HECHOS
FUNDAMENTOS DE DERECHO
Suplico
Proposición y prueba

Formulario adaptado a la reforma procesal de la LO 1/2025.

Juicio verbal de impugnación de laudo arbitral número [NÚMERO]

A LA SALA DE LO CIVIL Y PENAL DEL TRIBUNAL SUPERIOR DE JUSTICIA DE [LOCALIDAD]

HECHOS

Nos oponemos parcialmente a los hechos relatados en el escrito de demanda, pues si bien se acepta que se siguió el procedimiento arbitral entre las partes ante el árbitro que finalizó con el laudo de fecha [FECHA], en modo alguno se han producido los vicios aducidos por el demandante como motivos de impugnación del laudo, rechazando expresamente la pretendida inexistencia de convenio arbitral entre las partes.

Se pretende relacionar la nulidad invocada en la falta de validez del convenio arbitral, con la condición de consumidor del actor y por ende, haberse vulnerado la legislación protectora de consumidores y usuarios, cuando, como se desprende de los contratos aportados, por el que se adquirían cinco y cuatro terminales, respectivamente, de telefonía para empresas, no es de aplicación el Texto Refundido de la Ley General para la Defensa de Consumidores y Usuarios pues, la actora no era destinataria final del suministro, sino que dichos terminales y líneas contratadas, los mismos se encontraban integrados en un proceso de producción propio de la empresa para el que se adquirieron, estando excluida de ese régimen jurídico.

En las actuaciones aparecen unidos los dos contratos firmados entre el actor y mi representada, y en ambos contratos -bajo el epígrafe de "Condiciones del Contrato"- aparece la firma de ambas partes, constando además el sello comercial de la sociedad actora.

En dichos contratos figura también, como cláusula opcional, una cláusula arbitral con el siguiente texto: «Las partes aceptan expresamente que todo litigio, discrepancia, cuestión o reclamación resultantes de la ejecución o interpretación del presente contrato sea resuelta mediante arbitraje de equidad, manifestando su voluntad inequívoca de someterse a la institución arbitral [COMPLETAR], aceptando igualmente que sea ésta quien designe un único Árbitro y administre el arbitraje conforme a su reglamento».

De modo que, a efectos de impugnación de la cláusula arbitral, no cabe invocar como hace la actora el hipotético carácter abusivo de la cláusula arbitral porque no se están en el ámbito de protección de los consumidores y usuarios, lo que sin duda determina que la cláusula arbitral es válida y que el convenio arbitral existe y, en definitiva, que no hay la causa de nulidad del laudo arbitral prevista en el artículo 41.1.a) de la Ley de Arbitraje

FUNDAMENTOS DE DERECHO

PRIMERO.- Conformes con la competencia objetiva y territorial de la Sala, la legitimación «ad procesum», y el procedimiento adecuado escogido, compareciendo esta parte con la debida representación técnica y asistencia letrada.

SEGUNDO.- En cuanto al ejercicio de la acción, nos oponemos por no infringirse el art. 41.1.a) de la Ley de Arbitraje, al existir convenio arbitral válido, siendo de aplicación los siguientes preceptos: 1) el art. 3.1 del Real Decreto Legislativo 1/2007 (TRLGDCU) en cuanto al concepto general de consumidor y de usuario, cuando establece: “a efectos de esta norma y sin perjuicio de lo dispuesto expresamente en sus libros tercero y cuarto, son consumidores o usuarios las personas físicas que actúen con un propósito ajeno a su actividad comercial, empresarial, oficio o profesión. Son también consumidores a efectos de esta norma las personas jurídicas y las entidades sin personalidad jurídica que actúen sin ánimo de lucro en un ámbito ajeno a una actividad comercial o empresarial.”; por tanto, a efectos de impugnación de la cláusula arbitral, no cabe invocar el hipotético carácter abusivo de la cláusula arbitral porque la actora no ostenta la condición de consumidor ni de usuario; y 2) los artículos 9, apartados 1 y 2, de la Ley de Arbitraje establecen:. El convenio arbitral, que podrá adoptar la forma de cláusula incorporada a un contrato o de acuerdo independiente, deberá expresar la voluntad de las partes de someter a arbitraje todas o algunas de las controversias que hayan surgido o puedan surgir respecto de una determinada relación jurídica, contractual o no contractual. 2. Si el convenio arbitral está contenido en un contrato de adhesión, la validez de dicho convenio y su interpretación se regirán por lo dispuesto en las normas aplicables a ese tipo de contrato”; en el presente caso, estamos ante una cláusula arbitral incorporada a un contrato de venta de terminales de telefonía móvil, en el que no sólo se suscribe el contrato principal sino que además se firma expresa y específicamente el apartado que contiene la cláusula arbitral.

TERCERO.- Las costas deben imponerse a la actora, de conformidad con lo dispuesto en el artículo 394 LEC.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL que teniendo por presentado este escrito, con sus documentos, y copias de todo ello, se sirva admitirlo, y tenga por formulada CONTESTACIÓN A LA DEMANDA y, tras los trámites legales, dicte Sentencia desestimatoria de la pretensión formulada de contrario, todo ello con expresa imposición de costas a la parte actora.

OTROSÍ PRIMERO DIGO [COMPLETAR]: Que, de conformidad a lo establecido en el artículo 42.1 de la Ley de Arbitraje, esta parte solicita la celebración de vista, proponiendo los siguientes medios de prueba para que se practiquen en la misma:

1) DOCUMENTAL, dando por reproducidos los documentos acompañados en este escrito de contestación.

2) MÁS DOCUMENTAL, a fin que se requiera al Ayuntamiento de [LOCALIDAD], a fin que certifique la titularidad del establecimiento [COMPLETAR], sito en [LOCALIDAD], que gira a nombre de la actora, y las licencias, autorizaciones o declaraciones de actividad y/o comerciales que constan en el citado Ayuntamiento.

SUPLICO AL TRIBUNAL que tenga hechas las anteriores manifestaciones a los efectos legales que procedan y acuerde de conformidad

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
