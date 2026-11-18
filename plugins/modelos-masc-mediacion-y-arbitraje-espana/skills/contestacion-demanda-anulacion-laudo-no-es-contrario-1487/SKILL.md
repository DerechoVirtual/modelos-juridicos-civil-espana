---
name: contestacion-demanda-anulacion-laudo-no-es-contrario-1487
description: "Redacta el escrito «Contestación a demanda de anulación de laudo: no es contrario al orden público» (formulario 1487 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a demanda de anulación de laudo: no es contrario al orden público

> Formulario 1487 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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
- [ ] FECHA
- [ ] Nº DE EXPEDIENTE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…rbitral entre las partes ante el árbitro»; «…stitución que se acompaña como documento»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 9.3 de la Constitución
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

### Formulario 1487 · Contestación a demanda de anulación de laudo: no es contrario al orden público

- Año del modelo: 2014
- Revisión 17-11-2026: 7 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Encabezamiento
HECHOS
FUNDAMENTOS DE DERECHO
Suplico
Proposición de prueba
Firmas

Formulario adaptado a la reforma procesal de la LO 1/2025.

Juicio verbal de impugnación de laudo arbitral número [NÚMERO]

A LA SALA DE LO CIVIL Y PENAL DEL TRIBUNAL SUPERIOR DE JUSTICIA DE [LOCALIDAD]

HECHOS

Nos oponemos parcialmente a los hechos relatados en el escrito de demanda, pues si bien se acepta que se siguió el procedimiento arbitral entre las partes ante el árbitro [COMPLETAR] que finalizó con el laudo de fecha [FECHA], en modo alguno se han producido los vicios aducidos por el demandante como motivos de impugnación del laudo, rechazando expresamente la pretendida contravención del orden público del laudo dictado.

En el presente caso, la parte demandante alega la injusticia que se produjo en la tramitación del procedimiento arbitral y en la resolución del laudo en su contra, pero no aduce en ningún momento que aduce que se hayan infringido sus derechos fundamentales o que el laudo en cuestión haya incurrido en uno de los motivos tasados del artículo 41 de la Ley de Arbitraje, aunque aparentemente intenta ampararse en la posible contravención del orden público.

En ningún momento de la demanda se alega algún extremo que suponga un incumplimiento de los requisitos de contradicción, posibilidad de audiencia, igualdad y defensa de las partes por parte del órgano arbitral, por lo que no puede entenderse vulnerado ningún principio esencial del procedimiento que no se concreta en la demanda, a salvo que dice no haber sido notificada de la inadmisión de la reconvención formulada.

Sin embargo, también debemos negar que no fuera notificada la demandante de dicha resolución, puesto que consta en el expediente diligencia de notificación de la Secretaría de la institución que se acompaña como documento [COMPLETAR], sobre la cual no hizo ningún tipo de protesta o reserva la contraparte, por lo que, por aplicación del art. 6 de la Ley de Arbitraje, se produjo una renuncia tácita a su impugnación.

En definitiva, en el arbitraje se han garantizado todos los principios esenciales que permiten obtener la tutela judicial efectiva de la demandante, y que la pretensión real de la accionante para que se deje sin efecto el laudo se funda en cuestionar y criticar el fondo sustantivo del laudo, por lo que solicitamos la desestimación de la demanda.

FUNDAMENTOS DE DERECHO

Conformes con la competencia objetiva y territorial de la Sala, la legitimación «ad procesum» y el procedimiento adecuado escogido, compareciendo esta parte con la debida representación técnica y asistencia letrada.

En cuanto al ejercicio de la acción, nos oponemos por no concurrir el motivo del art. 41.1.f) de la Ley de Arbitraje, por no existir contravención del orden público; en cuanto a lo que se debe entender por orden público, la STC 54/1989, de 23 de febrero, expresa que es aquel conjunto de principios, normas rectoras generales y derechos fundamentales constitucionalizados en el ordenamiento jurídico español, siendo sus normas jurídicas básicas e inderogables por la voluntad de las partes, tanto en lo social como en lo económico, y por ende, a los efectos previstos en el citado artículo, debe considerarse contrario al orden público, aquel Laudo que vulnere los derechos y libertades fundamentales reconocidos en el Capítulo II, Título I de la Constitución, garantizados a través de lo dispuesto en términos de generalidad en el artículo 24 de la misma, incluyendo la arbitrariedad patente referida en el art. 9.3 de la Constitución, y desde luego, quedando fuera de éste concepto la posible justicia del laudo, las deficiencias del fallo o el modo más o menos acertado de resolver la cuestión".

Las costas deben imponerse a la actora, de conformidad con lo dispuesto en el artículo 394 LEC.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL que teniendo por presentado este escrito, con sus documentos, y copias de todo ello, se sirva admitirlo, y tenga por formulada CONTESTACIÓN A LA DEMANDA y, tras los trámites legales, dicte Sentencia desestimatoria de la pretensión formulada de contrario, todo ello con expresa imposición de costas a la parte actora.

OTROSÍ PRIMERO DIGO: Que, de conformidad a lo establecido en el artículo 42.1 de la Ley de Arbitraje, esta parte solicita la celebración de vista, proponiendo los siguientes medios de prueba para que se practiquen en la misma:

1) DOCUMENTAL, dando por reproducidos los documentos acompañados en este escrito de contestación.

2) MÁS DOCUMENTAL, a fin que se requiera a la Secretaría de la institución arbitral a fin que remita copia completa del expediente número [Nº DE EXPEDIENTE],

SUPLICO AL TRIBUNAL que tenga hechas las anteriores manifestaciones a los efectos legales que procedan y acuerde de conformidad

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
