---
name: demanda-remocion-arbitro-nombramiento-sustituto-1473
description: "Redacta el escrito «Demanda de remoción de árbitro y nombramiento de sustituto» (formulario 1473 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de remoción de árbitro y nombramiento de sustituto

> Formulario 1473 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (8 veces)
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] IMPORTE
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Don»; «…io verbal para la remoción del árbitro D»; «… la cual dirijo contra el citado árbitro»; «…y contra el demandado D»; «…, con domicilio, respectivamente, en»; «…cita la acción de remoción del árbitro D»; «…plimiento de las funciones del árbitro D»; «…estación alguna (acompaño como documento»; «…arte en la representación que ostento de»; «…árbitro sustituto, contra los demandados»; «…y»; «… por la que: 1. Acuerde la remoción de D»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 23 y 31 de la LEC
- artículo 394 de la LEC
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

### Formulario 1473 · Demanda de remoción de árbitro y nombramiento de sustituto

- Año del modelo: 2014
- Revisión 17-11-2026: 27 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Encabezamiento
HECHOS
FUNDAMENTOS DE DERECHO
Suplico
Cuantía del pleito indeterminada
Otrosí de tasa
Firmas

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SALA DE LO CIVIL Y PENAL DEL TRIBUNAL SUPERIOR DE JUSTICIA DE [LOCALIDAD]

Don [COMPLETAR] Procurador de los Tribunales, en nombre y representación de [NOMBRE DEL REPRESENTADO/A], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, comparezco ante esa Sala y, como mejor proceda en Derecho, DIGO:

Que en la representación que ostento formulo demanda de juicio verbal para la remoción del árbitro D [COMPLETAR] y acumulada para el nombramiento de un árbitro sustituto, la cual dirijo contra el citado árbitro [COMPLETAR] y contra el demandado D [COMPLETAR], con domicilio, respectivamente, en [COMPLETAR], la cual fundo en los siguientes:

HECHOS

Por medio de esta demanda se ejercita la acción de remoción del árbitro D [COMPLETAR], amparada en el art. 19 de la Ley de Arbitraje, como consecuencia de no estar ejercitando sus funciones en un plazo razonable, acumulando la acción de designación de sustituto, según autoriza expresamente el art. 19.1.a) de la citada Ley.

La remoción se funda en el incumplimiento de las funciones del árbitro D [COMPLETAR], el cual fue designado de mutuo acuerdo por las partes para dirimir la controversia reflejada en el convenio arbitral de fecha [FECHA], el cual se acompaña como documento número

En los pactos reflejados en el convenio se fijaba un plazo de duración del arbitraje de seis meses a partir de la fecha de inicio que ambas partes fijaron de mutuo acuerdo el día [FECHA], acordando la designación de árbitro.

Pues bien, el árbitro aceptó el mismo día de iniciación y a partir de esta fecha se han sucedido las siguientes actuaciones en el procedimiento arbitral: 1) el día [FECHA], es decir, dos meses después de la aceptación, el árbitro concedió a esta parte un plazo de diez días para deducir demanda arbitral; 2) esta parte presentó la demanda en tiempo y forma el día [FECHA]; 3) el día [FECHA], esto es, casi tres meses después de haber presentado la demanda esta parte, el árbitro concedió un plazo de diez días al demandado para contestar a la demanda, trámite que no consta a esta parte que se haya evacuado.

Por tanto, en esta fase inicial de alegaciones han transcurrido más de cinco meses, sin que hasta la fecha se tenga constancia siquiera de la presentación de la contestación por el demandado (acompaño como documentos número [Nº DE DOCUMENTO] aceptación, resoluciones arbitrales y demanda).

Habida cuenta de los graves retrasos, injustificados, por parte del árbitro, esta parte ha dirigido numerosos escritos y requerimientos para el impulso del procedimiento arbitral, sin que recibiera respuesta alguna (acompaño como documentos número [Nº DE DOCUMENTO] escritos de fecha [FECHA] solicitando del árbitro el impulso de las actuaciones).

Ante esta situación, el pasado día [FECHA] esta parte dirigió requerimiento formal al demandado para remoción del árbitro y nombramiento de sustituto, sin que haya realizado manifestación alguna (acompaño como documento [COMPLETAR] requerimiento de fecha [FECHA] dirigido al demandado).

No siendo posible la remoción de árbitro y designación de sustituto de mutuo acuerdo, esta parte se ve en la obligación de solicitar del tribunal la remoción del árbitro conforme a lo previsto en el art. 19 de la Ley de Arbitraje, habida cuenta del incumplimiento, al menos, gravemente negligente de sus funciones sin causa alguna que lo justifique, y al tiempo la designación judicial de árbitro sustituto, conforme a lo dispuesto en los arts. 19.1.a) y 20 en relación con el art. 15.6 de la Ley de Arbitraje, proponiendo que por el tribunal se confeccione una relación con tres nombres, insaculando a un árbitro de los incluidos en la terna.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Jurisdicción y competencia

Es competente para conocer del nombramiento de árbitros la Sala de lo Civil y de lo Penal del Tribunal Superior de Justicia de la Comunidad Autónoma del lugar donde tenga lugar el arbitraje, según dispone el artículo 8.1 de la Ley de Arbitraje.

Capacidad y representación

Las partes están capacitadas para entablar la presente relación jurídico procesal conforme a los artículos 6 y siguientes de la Ley de Enjuiciamiento Civil, reuniéndose los requisitos de postulación de los artículos 23 y 31 de la LEC.

Procedimiento

De acuerdo con lo dispuesto en el artículo 19.1.a) de la Ley de Arbitraje corresponde seguir el procedimiento por los cauces del juicio verbal

Acumulación de acciones

Es de aplicación el art. 19.1.a) de la Ley de Arbitraje

Acción principal: remoción del árbitro

El art. 19.1 de la Ley de Arbitraje dispone que la remoción se acordara judicialmente si no hay acuerdo de las partes en caso de que el árbitro no ejerza sus funciones en un plazo razonable, supuesto que ha quedado expuesto en los hechos de esta demanda.

Acción acumulada: designación judicial de árbitro sustituto

Es de aplicación el art. 20 en relación con el art. 15.6 de la Ley de Arbitraje.

Al amparo del artículo 394 de la LEC, las costas deben imponerse a los demandados.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL: Tenga por presentado este escrito y demás documentos junto con las copias que se acompañan a las que se dará el curso legal, lo admita, me tenga por comparecido y parte en la representación que ostento de [COMPLETAR] entendiéndose conmigo las sucesivas diligencias. Y tenga por formulada demanda de juicio verbal para la remoción judicial de árbitro y acumulada de nombramiento de árbitro sustituto, contra los demandados [COMPLETAR] y [COMPLETAR] cuyas demás circunstancias personales constan en el encabezamiento de este escrito y, tras los trámites correspondientes, dicte sentencia por la que:

1. Acuerde la remoción de D [COMPLETAR] como árbitro en el procedimiento arbitral seguido con el codemandado D [COMPLETAR]

2. Acuerde la designación judicial de un árbitro sustituto, confeccionando una lista con tres nombres y procediendo a su nombramiento mediante sorteo.

3. Imponga las costas de este proceso a los demandados.

OTROSÍ PRIMERO DIGO: Que la cuantía del pleito es indeterminada.

OTROSÍ SEGUNDO DIGO.- Que estando la presente demanda sujeta al abono de la tasa por el ejercicio de la potestad jurisdiccional fijada por la Ley 10/2012, de 20 de noviembre, modificada por Real Decreto Ley 3/2013, de 22 de febrero, y Ley 25/2015, de 28 julio, y desarrollada por Orden HAP/2662/2012, de 13 de diciembre, modificada por Orden HAP/490/2013, de 27 de marzo, y por Orden HAP/861/2015, de 7 de mayo, siendo mi representada persona jurídica no exenta, se acompaña a la presente demanda como documento nº [Nº DE DOCUMENTO] la correspondiente autoliquidación con el ejemplar para la Administración de Justicia debidamente validado y en el que consta el pago de la cantidad de 150 euros correspondiente a la cuota fija, más la cantidad de [IMPORTE] euros por la aplicación a la base imponible de la escala prevista en el artículo 7.2 de la citada Ley

En virtud de lo anterior,

SUPLICO AL TRIBUNAL que tenga por hecha las anteriores manifestaciones a los efectos pertinentes y por acompañado el documento justificativo del abono de la tasa.

En

========================================================================
