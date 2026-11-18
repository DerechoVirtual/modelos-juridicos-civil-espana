---
name: formalizacion-judicial-arbitraje-designacion-arbitros-1474
description: "Redacta el escrito «Formalización judicial del arbitraje y designación de árbitros» (formulario 1474 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Formalización judicial del arbitraje y designación de árbitros

> Formulario 1474 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (2 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (4 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] COLEGIO (2 veces)
- [ ] IMPORTE
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Don»; «…dicial de árbitros contra el demandado D»; «…inserto como cláusula»; «…ntrato y convenio arbitral). La cláusula»; «…s partes que suscribieron el contrato de»; «…estación alguna (acompaño como documento»; «…arte en la representación que ostento de»; «…contra el demandado»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 23 y 31 de la LEC
- artículo 394 de la LEC
- Ley 60/2003
- Ley 10/2012
- Ley 3/2013
- Ley 25/2015

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

### Formulario 1474 · Formalización judicial del arbitraje y designación de árbitros

- Año del modelo: 2014
- Revisión 17-11-2026: 20 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Parte
HECHOS
FUNDAMENTOS DE DERECHO
Suplico
Cuantía del pleito
Otrosí de tasa
Firmas

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SALA DE LO CIVIL Y PENAL DEL TRIBUNAL SUPERIOR DE JUSTICIA DE [LOCALIDAD]

Don [COMPLETAR] Procurador de los Tribunales, en nombre y representación de [NOMBRE DEL REPRESENTADO/A], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, comparezco ante esa Sala y, como mejor proceda en Derecho, DIGO:

Que en la representación que ostento formulo demanda de juicio verbal para el nombramiento judicial de árbitros contra el demandado D [COMPLETAR], con domicilio en [LOCALIDAD], la cual fundo en los siguientes:

HECHOS

Por medio de esta demanda se ejercita la acción de formalización judicial del arbitraje y nombramiento de árbitros, amparada en el art. 15 de la Ley de Arbitraje, en virtud del convenio arbitral de fecha [FECHA] inserto como cláusula [COMPLETAR] del contrato suscrito con el demandado (acompaño como documento número [Nº DE DOCUMENTO] contrato y convenio arbitral).

La cláusula [COMPLETAR] del referido contrato otorgado por las partes el día [FECHA] tiene el siguiente tenor: «Para la resolución de cualquier cuestión, controversia o diferencia que pudiera surgir con motivo de la interpretación o cumplimiento de los pactos contenidos en el presente documento, ambas partes se someten al laudo que emita un abogado en ejercicio, actuando en arbitraje de equidad, con pleno sometimiento a la Ley 60/2003, de 23 de diciembre, de Arbitraje».

Los términos en que se halla redactada dicha cláusula no dejan lugar a dudas sobre la existencia de la voluntad de las partes que suscribieron el contrato de [COMPLETAR] de someter a arbitraje, y más concretamente a arbitraje de equidad, la interpretación y ejecución de dicho contrato, siendo así que la forma adoptada para plasmar el convenio arbitral es plenamente conforme con lo dispuesto en el artículo 9. 1 de la Ley 60/2003 de 23 de diciembre de Arbitraje

Atendida la cláusula arbitral y habiendo surgido controversia entre las partes sobre el cumplimiento del contrato al no haber satisfecho la otra parte el importe de los suministros recibidos, esta parte requirió al demandado para la designación por el procedimiento de sorteo de un árbitro entre los abogados inscritos en el Colegio de Abogados de [COLEGIO], sin que el demandado haya hecho manifestación alguna (acompaño como documento [COMPLETAR] requerimiento notarial remitido al demandado a los efectos de designación de árbitro).

No siendo posible la designación de árbitro de mutuo acuerdo, esta parte se ve en la obligación de solicitar del tribunal la designación judicial, conforme a lo previsto en el art. 15.1.a) de la Ley de Arbitraje, proponiendo, en cuanto a la forma en que ha de llevarse a cabo el nombramiento y de conformidad a lo dispuesto en el art. 15.6 de la citada Ley, que: 1) que por el tribunal se confeccione una relación con tres nombres, de la que saldrá quien haya de ser el árbitro que resuelva la controversia, solicitando que se remita oficio al Colegio de Abogados de [COLEGIO] a fin de que relacione los colegiados que figuren en el turno especial de árbitros, 2) que el tribunal elabore, por el medio que considere oportuno, una terna, teniendo en cuenta que al tratarse de arbitraje de equidad no se dan requisitos de especialización; y 3) que se insacule a un árbitro de los incluidos en la terna.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Jurisdicción y competencia

Es competente para conocer de la nombramiento de árbitros la Sala de lo Civil y de lo Penal del Tribunal Superior de Justicia de la Comunidad Autónoma del domicilio o residencia del demandado, según dispone el artículo 8.1 de la Ley de Arbitraje.

Capacidad y representación

Las partes están capacitadas para entablar la presente relación jurídico procesal conforme a los artículos 6 y siguientes de la Ley de Enjuiciamiento Civil, reuniéndose los requisitos de postulación de los artículos 23 y 31 de la LEC.

Procedimiento

De acuerdo con lo dispuesto en el artículo 15.4 de la Ley de Arbitraje corresponde seguir el procedimiento por los cauces del juicio verbal

Designación judicial de árbitros

La Ley 60/2003, de 23 de diciembre, de Arbitraje establece en su artículo 15 que si no resulta posible designar árbitro a través del procedimiento acordado por las partes, cualquiera de ellas podrá solicitar al tribunal competente el nombramiento de los árbitros o en su caso la adopción de las medidas necesarias para ello, expresándose en su preámbulo que el juez sólo debe desestimar la petición de nombramiento de árbitros en el caso excepcional de inexistencia de convenio arbitral, esto es, cuando "prima facie" puede estimar que realmente no existe un convenio arbitral; pero el juez no está llamado en este procedimiento a realizar un control de los requisitos de validez del convenio.

Procedimiento de designación

Es de aplicación lo dispuesto en el art. 15.6 de la Ley de Arbitraje.

Costas

Al amparo del artículo 394 de la LEC, las costas deben imponerse a la parte cuyas pretensiones sean totalmente desestimadas, debiendo subrayarse que el demandado ha hecho caso omiso del requerimiento para designación de árbitros en el mismo sentido ahora solicitado, obligando a esta parte a ejercitar esta acción jurisdiccional.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL: Tenga por presentado este escrito y demás documentos junto con las copias que se acompañan a las que se dará el curso legal, lo admita, me tenga por comparecido y parte en la representación que ostento de [COMPLETAR] entendiéndose conmigo las sucesivas diligencias. Y tenga por formulada demanda de juicio verbal para la designación judicial de árbitro en cumplimiento del convenio arbitral de fecha [FECHA] contra el demandado [COMPLETAR] cuyas demás circunstancias personales constan en el encabezamiento de este escrito y, tras los trámites correspondientes, dicte sentencia por la que:

1. Acuerde la designación judicial de un árbitro para dirimir la controversia entre las partes derivada del contrato de fecha [FECHA]

2. Confeccione una lista con tres nombres y proceda a su nombramiento mediante sorteo.

3. Imponga las costas de este proceso a la parte demandada.

OTROSÍ PRIMERO DIGO: Que la cuantía del pleito es indeterminada..

OTROSÍ SEGUNDO DIGO.- Que estando la presente demanda sujeta al abono de la tasa por el ejercicio de la potestad jurisdiccional fijada por la Ley 10/2012, de 20 de noviembre, modificada por Real Decreto Ley 3/2013, de 22 de febrero, y Ley 25/2015, de 28 julio, y desarrollada por Orden HAP/2662/2012, de 13 de diciembre, modificada por Orden HAP/490/2013, de 27 de marzo, y por Orden HAP/861/2015, de 7 de mayo, siendo mi representada persona jurídica no exenta, se acompaña a la presente demanda como documento nº [Nº DE DOCUMENTO] la correspondiente autoliquidación con el ejemplar para la Administración de Justicia debidamente validado y en el que consta el pago de la cantidad de 150 euros correspondiente a la cuota fija, más la cantidad de [IMPORTE] euros por la aplicación a la base imponible de la escala prevista en el artículo 7.2 de la citada Ley

En virtud de lo anterior,

SUPLICO AL TRIBUNAL que tenga por hecha las anteriores manifestaciones a los efectos pertinentes y por acompañado el documento justificativo del abono de la tasa.

En

========================================================================
