---
name: demanda-anulacion-laudo-arbitraje-consumo-1471
description: "Redacta el escrito «Demanda de anulación de laudo de arbitraje de consumo» (formulario 1471 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de anulación de laudo de arbitraje de consumo

> Formulario 1471 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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
- [ ] FECHA (5 veces)
- [ ] Nº DE PROCEDIMIENTO (2 veces)
- [ ] Nº DE DOCUMENTO (5 veces)
- [ ] IMPORTE (3 veces)
- [ ] NÚMERO
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Don»; «…tado por la Junta Arbitral de Consumo de»; «…, contra el demandado D»; «…ada durante el periodo comprendido entre»; «…euros (acompaño como documentos»; «…arte en la representación que ostento de»; «…tado por la Junta Arbitral de Consumo de»; «…contra la demandada»; «…oficio a la Junta Arbitral de Consumo de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 40.1 del RD 713/2024
- art. 24.1 de la CE
- artículos 23 y 31 de la LEC
- artículo 42 de Ley 60/2003
- artículo 41.4 de la Ley 60/2003
- artículos 24 CE
- artículo 31 RD 713/2024
- art. 40 RD 713/2024
- art. 24 CE
- artículo 394 de la LEC
- Ley 11/2011
- Ley 10/2012
- Ley 3/2013

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

### Formulario 1471 · Demanda de anulación de laudo de arbitraje de consumo

- Año del modelo: 2014
- Revisión 17-11-2026: 28 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Encabezamiento
HECHOS
FUNDAMENTOS DE DERECHO
Suplico
Devolución del poder general para pleitos
Cuantía del pleito
Proposición del prueba
Suplico (efectos legales y conformidad)
Tasa
Firmas

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SALA DE LO CIVIL Y PENAL DEL TRIBUNAL SUPERIOR DE JUSTICIA DE [LOCALIDAD]

Don [COMPLETAR] Procurador de los Tribunales, en nombre y representación de [NOMBRE DEL REPRESENTADO/A], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, comparezco ante este Tribunal y DIGO:

Que en la representación que ostento formulo demanda en ejercicio de la acción de anulación contra el laudo arbitral dictado por la Junta Arbitral de Consumo de [COMPLETAR] en fecha [FECHA] en el procedimiento arbitral número [Nº DE PROCEDIMIENTO], que acompaño como documento número [Nº DE DOCUMENTO], contra el demandado D [COMPLETAR], con domicilio en [LOCALIDAD], la cual fundo en los siguientes:

HECHOS

Por medio de esta demanda se ejercita la acción de anulación del laudo arbitral dictado en el procedimiento número [Nº DE PROCEDIMIENTO] de arbitraje de consumo arriba expresado que se acompaña como documento número [Nº DE DOCUMENTO] de la demanda, con fundamento en los siguientes motivos: a) al amparo del artículo 41.1.f) de la Ley de Arbitraje, por ser el laudo contrario al orden público.

En efecto, el laudo arbitral que se impugna contraviene el orden público por cuanto: 1) esta parte presentó reconvención en el procedimiento arbitral sin que se hiciera ninguna mención a ella en todo el procedimiento ni en el laudo, pese a haber sido expuesta nuestra protesta hasta en cuatro ocasiones; y 2) el laudo adolece de absoluta falta de motivación.

En relación al primero de los submotivos amparado en el art. 41.1.f) de la Ley de Arbitraje, alegamos que se han infringido las garantías básicas del procedimiento, con lesión del derecho a la tutela de esta parte, al no haber sido tramitada ni inadmitida la reconvención deducida en tiempo y forma por esta parte.

En efecto, la solicitud de arbitraje del demandante se dedujo en fecha [FECHA], siendo notificada a esta parte en fecha [FECHA] y contestando a la solicitud, y formulando reconvención como consecuencia que el demandante había dejado de abonar las cuotas del servicio de seguridad prestado por mi representada durante el periodo comprendido entre [COMPLETAR], reclamando una indemnización por importe de [IMPORTE] euros (acompaño como documentos [COMPLETAR] solicitud de arbitraje, notificación y escrito de contestación y reconvención, designando los originales del procedimiento que obran en la Secretaría de la Junta Arbitral y que serán propuestos como prueba).

Tras el señalamiento de la audiencia, esta parte presentó escrito de fecha [FECHA] solicitando que se acordara lo procedente sobre la reconvención (acompañado como documento número [Nº DE DOCUMENTO]), sin que la Junta contestara sobre la solicitud.

En la audiencia esta parte reprodujo su protesta, ante lo cual los árbitros se limitaron a reflejarla en el acta, sin resolver sobre la reconvención.

Finalmente, en el laudo no se hace ninguna referencia a la reconvención, ni en los antecedentes ni en su fundamentación.

Los anteriores hechos suponen la infracción de una norma esencial del procedimiento, y la vulneración de los principios informadores del procedimiento arbitral de consumo de audiencia, contradicción e igualdad, al preterirse el derecho de esta parte a formular reconvención, establecido en el art. 40.1 del RD 713/2024, y al no pronunciarse los árbitros, de forma totalmente incongruente sobre la misma, con infracción de lo dispuesto en el art. 40.2 del citado RD 713/2024.

Por ello, concurre el motivo de anulación del art. 41.1.f) de la Ley de Arbitraje, interesando la nulidad al amparo del precepto.

En relación al segundo de los submotivos amparado asimismo en el art. 41.1.f) de la Ley de Arbitraje, alegamos que el laudo adolece de una absoluta falta de motivación, por lo que vulnera el orden público procesal por infracción del art. 24.1 de la CE, en la medida en afecta a su derecho a obtener del árbitro una resolución motivada que resuelva la cuestión conforme a las reglas de la lógica y de la razón.

La STS de 29 de marzo de 2010 recuerda que el derecho a una resolución fundada, exige una fundamentación jurídica y una coherencia formal, de modo que la resolución ha de contener los elementos y razones de juicio que permitan conocer cuáles han sido los criterios jurídicos que fundamentan la decisión.

Pues bien, tal como se constata de la lectura del laudo impugnado acompañado como documento número [Nº DE DOCUMENTO], se limita a plasmar los alegatos realizados por las partes contendientes, pero en absoluto fundamenta el/los motivo/s que llevan a la desestimación de la reclamación formulada. Así, a efectos demostrativos de la falta de motivación del laudo, se transcribe la parte del mismo que contiene la única explicación no meramente narrativa cuando dice «a la vista de las alegaciones expuestas y de la documentación que obra en el expediente, previa deliberación y en equidad, entendemos que debe estimarse la reclamación, al quedar plenamente justificados los hechos en que se funda».

De ello resulta claro que la motivación del laudo de referencia no sólo es exigua y realmente insuficiente, sino que es más bien aparente, amén de arbitraria e irrazonable, por lo que solicitamos asimismo la nulidad por este motivo.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Jurisdicción y competencia

Es competente para conocer de la acción de anulación del laudo la Sala de lo Civil y de lo Penal del Tribunal Superior de Justicia de la Comunidad Autónoma donde aquél se hubiere dictado, según dispone el artículo 8.5 de la Ley de Arbitraje.

Capacidad y representación

Las partes están capacitadas para entablar la presente relación jurídico procesal conforme a los artículos 6 y siguientes de la Ley de Enjuiciamiento Civil, reuniéndose los requisitos de postulación de los artículos 23 y 31 de la LEC.

Procedimiento

De acuerdo con lo dispuesto en el artículo 42 de Ley 60/2003, de Arbitraje, modificado por Ley 11/2011, corresponde seguir el procedimiento por los cauces del juicio verbal, con las especialidades allí establecidas.

Plazo

Conforme a lo dispuesto en el artículo 41.4 de la Ley 60/2003, de Arbitraje, la acción de nulidad del laudo se ejercita dentro de los dos meses, desde la notificación del mismo a mi representado en fecha

Motivos de anulación

Al amparo del art. 41.1.f) de la Ley de Arbitraje (laudo contrario al orden público):

1) Se infringen los principios fundamentales del procedimiento de arbitraje de consumo, artículos 24 CE y artículo 31 RD 713/2024, de 23 de julio, al dejar de tramitarse la reconvención y omitir cualquier pronunciamiento sobre su admisibilidad, con infracción asimismo del art. 40 RD 713/2024.

2) Se infringe el art. 24 CE y art. 37.4 de la Ley de Arbitraje puesto que el laudo carece de la más mínima motivación. Citamos las SSTC 187/2000, de 10 de julio y 214/2000, de 18 de septiembre y las SSTS 2 de noviembre de 2001 y de 20 de octubre de 2005, doctrina ésta que, trasladada a la motivación que necesariamente deben contener los laudos arbitrales ex art. 37.4. LA, determina la nulidad del laudo.

Costas

Al amparo del artículo 394 de la LEC, las costas deben imponerse a la parte cuyas pretensiones sean totalmente desestimadas.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL: Tenga por presentado este escrito, la copia electrónica del poder notarial de representación informática (o digitalizada) y demás documentos junto con las copias que se acompañan a las que se dará el curso legal, lo admita, me tenga por comparecido y parte en la representación que ostento de [COMPLETAR] entendiéndose conmigo las sucesivas diligencias. Y tenga por formulada demanda de juicio verbal civil en ejercicio de la acción de anulación del laudo arbitral de fecha [FECHA] dictado por la Junta Arbitral de Consumo de [COMPLETAR] contra la demandada [COMPLETAR] cuyas demás circunstancias personales constan en el encabezamiento de este escrito y, tras los trámites correspondientes con celebración de vista que expresamente solicito, dicte sentencia por la que se declare la nulidad del expresado laudo arbitral, condenando a la parte demandada al pago de las costas del proceso.

OTROSÍ PRIMERO DIGO: Que intereso la devolución del poder general para pleitos por precisarlo para otro menester quedando en los autos copia debidamente testimoniada.

OTROSÍ SEGUNDO DIGO: Que la cuantía del pleito es de [IMPORTE] euros.

OTROSÍ TERCERO DIGO: Que, de conformidad a lo establecido en el artículo 42.1 de la Ley de Arbitraje, esta parte solicita la celebración de vista, proponiendo los siguientes medios de prueba para que se practiquen en la misma:

1) DOCUMENTAL, dando por reproducidos los documentos acompañados en el escrito de demanda.

2) MÁS DOCUMENTAL, remitiendo oficio a la Junta Arbitral de Consumo de [COMPLETAR] para que aporte copia autenticada completa del procedimiento de arbitraje de consumo seguido con el número [NÚMERO] al que se refiere este proceso.

SUPLICO AL TRIBUNAL que tenga hechas las anteriores manifestaciones a los efectos legales que procedan y acuerde de conformidad.

OTROSÍ CUARTO DIGO.- Que estando la presente demanda sujeta al abono de la tasa por el ejercicio de la potestad jurisdiccional fijada por la Ley 10/2012, de 20 de noviembre, modificada por Real Decreto Ley 3/2013, de 22 de febrero, y RDL 1/2015, de 27 de febrero, y desarrollada por Orden HAP/2662/2012, de 13 de diciembre, modificada por Orden HAP/490/2013, de 27 de marzo, y por Orden HAP/861/2015, de 7 de mayo, siendo mi representada persona jurídica no exenta, se acompaña a la presente demanda como documento nº [Nº DE DOCUMENTO] la correspondiente autoliquidación con el ejemplar para la Administración de Justicia debidamente validado y en el que consta el pago de la cantidad de 150 euros correspondiente a la cuota fija, más la cantidad de [IMPORTE] euros por la aplicación a la base imponible de la escala prevista en el artículo 7.2 de la citada Ley

En virtud de lo anterior,

SUPLICO AL TRIBUNAL que tenga por hecha la anterior manifestación a los efectos pertinentes y por acompañado el documento justificativo del abono de la tasa.

En

========================================================================
