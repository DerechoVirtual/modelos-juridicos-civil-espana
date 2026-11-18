---
name: demanda-retracto-arrendamiento-rustico-829
description: "Redacta el escrito «Demanda de retracto en arrendamiento rústico» (formulario 829 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de retracto en arrendamiento rústico

> Formulario 0829 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Cita la Ley 83/1980, derogada por la Ley 49/2003 (DD única); solo para contratos vigentes al 27-5-2004 (DT 1.ª); para los posteriores, art. 22 Ley 49/2003 (agricultor profesional, 60 días hábiles).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (10 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] Nº DE DOCUMENTO (4 veces)
- [ ] Nº
- [ ] FECHA (5 veces)
- [ ] NÚMERO (4 veces)
- [ ] IMPORTE (2 veces)
- [ ] LUGAR
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Emiliano»; «…el»; «…nada "", sita en el término municipal de»; «…TERCERO.- A finales del mes de»; «…tataba que mediante escritura pública de»; «…de»; «…iante correspondencia escrita, en fechas»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 9.2, 21.1 y 85.1 LOPJ
- arts. 36.1 y 45 LEC
- arts. 14.1 y 93.2 de la Ley 83/1980
- art. 13 LEC
- art. 269.2 LEC
- art. 1518 CCiv
- art. 399.3 de la LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 253.1 LEC
- arts. 23 y 31 LEC
- art. 394 LEC
- art. 266 LEC
- Ley 49/2003
- Ley 26/2005

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

### Formulario 0829 · Demanda de retracto en arrendamiento rústico

- Año del modelo: 2015
- Revisión 17-11-2026: 2 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (3); 36 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO)
- Avisos de la revisión: Cita la Ley 83/1980, derogada por la Ley 49/2003 (DD única); solo para contratos vigentes al 27-5-2004 (DT 1.ª); para los posteriores, art. 22 Ley 49/2003 (agricultor profesional, 60 días hábiles).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de demanda de juicio declarativo ordinario ejercitando acción de retracto arrendaticio rústico.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a. de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], dirigido por Abogado ejerciente, D./Dña. [NOMBRE Y APELLIDOS], con despacho profesional en esta capital sito en [LOCALIDAD], ante el Tribunal comparezco y como mejor proceda en derecho, DIGO:

Que mediante el presente escrito y en nombre de mi mandante formulo DEMANDA DE JUICIO ORDINARIO SOBRE ACCIÓN DE RETRACTO ARRENDATICIO RÚSTICO contra D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], en virtud de los siguientes hechos y fundamentos de derecho:

HECHOS

PRIMERO.- Mi mandante, D./Dña. [NOMBRE Y APELLIDOS], es profesional de la agricultura desde hace más de [Nº] años, como se acredita con la certificación de la TGSS sobre su vida laboral, como trabajador autónomo sujeto al régimen especial agrario, de alta desde el [FECHA] en cuya situación continúa.

Se adjunta certificación de la TGSS como documento n.º [NÚMERO]

SEGUNDO.- D./Dña. [NOMBRE Y APELLIDOS] Emiliano [COMPLETAR] concertó con D./Dña. [NOMBRE Y APELLIDOS] el [COMPLETAR] el arrendamiento de la finca denominada "", sita en el término municipal de [COMPLETAR], finca registral n.º [NÚMERO], inscrita al tomo

Desde entonces mi mandante ha venido explotando la misma dedicada al cultivo de espárragos.

Se acompaña copia del contrato de arrendamiento como documento n.º [NÚMERO]

TERCERO.- A finales del mes de [COMPLETAR] mi mandante tuvo conocimiento, por algunas noticias de los vecinos de la zona, que la finca había sido vendida a un tercero, y como quiera que no pudo comunicar en ningún momento con D./Dña. [NOMBRE Y APELLIDOS], acudió al Registro de la Propiedad del partido, donde con fecha [FECHA] obtuvo certificación de la finca registral, en la que se constataba que mediante escritura pública de [COMPLETAR] fue vendida al demandado D./Dña. [NOMBRE Y APELLIDOS], por el precio de [IMPORTE] euros.

Se adjunta dicha certificación como documento n.º [NÚMERO]

CUARTO.- Mi mandante, a quien D./Dña. [NOMBRE Y APELLIDOS] no había notificado su intención de vender y que hasta el [FECHA] de [COMPLETAR], como queda dicho, no tuvo conocimiento de la realidad de la misma y sus condiciones, desea ejercitar el derecho de retracto que la legislación arrendaticia rústica le concede y adquirir la finca en cuestión, por lo que se ve en la necesidad de interponer la presente demanda de retracto en legal plazo.

QUINTO.- Se ha procedido el mismo día de la interposición de este escrito a consignar el precio de la venta de la citada finca rústica a disposición del adquirente, como se demuestra con el resguardo del abonaré realizado en la cuenta de Depósitos y Consignaciones del Tribunal, que se adjunta como documento n.º [Nº DE DOCUMENTO]

SEXTO.- La parte actora manifiesta que, previo a la presentación de la presente demanda, se han llevaron a cabo negociaciones con la parte demandada, con el objetivo de cumplir el requisito de procedibilidad, y resolver la controversia de manera amistosa y extrajudicial. Dichas negociaciones se desarrollaron en cumplimiento de los principios de buena fe, con la intención de alcanzar una solución satisfactoria; incluyéndose entre las acciones realizadas el intercambio de comunicaciones formales mediante correspondencia escrita, en fechas [COMPLETAR], en las cuales esta parte expresó su disposición para dialogar y propuso alternativas de solución.

Finalmente, mi representado envío un requerimiento fehaciente al demandado con fecha [FECHA], fijando un plazo de 30 días naturales para llegar a un acuerdo amistoso, a través del abogado que firma este escrito, el cual fue contestado por el demandado por el mismo medio, rechazando el acuerdo/ habiendo sido solo posible un acuerdo parcial, viéndonos en la necesidad de acudir a la presente vía judicial, respecto a los extremos de la controversia en los que se mantiene la discrepancia.

Acompaño como documento nº [Nº DE DOCUMENTO], el requerimiento efectuado y como documento nº [Nº DE DOCUMENTO], la contestación del demandado.

A los anteriores hechos son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- JURISDICCIÓN Y COMPETENCIA.

Es de aplicación el art. 52.1.1.º LEC, para la competencia territorial, en cuanto que se ejercita una acción real sobre bien inmueble, y el Tribunal al que me dirijo es el del lugar en que está sito aquél. Y en cuanto a la jurisdicción y competencia genérica y objetiva, citamos los arts. 9.2, 21.1 y 85.1 LOPJ y arts. 36.1 y 45 LEC.

II.- PROCEDIMIENTO.

Art. 249.1.7.º LEC, que ordena sustanciar las pretensiones de retracto de cualquier tipo a través del juicio ordinario.

III.- LEGITIMACIÓN ACTIVA Y PASIVA.

La legitimación activa corresponde a mi poderdante como titular del derecho de retracto, en su condición de arrendatario, que además reúne la condición de profesional de la agricultura, conforme a los arts. 14.1 y 93.2 de la Ley 83/1980, de 31 de diciembre, de Arrendamientos Rústicos [NOTA DE REVISIÓN: La Ley 83/1980 está derogada (DD única.a Ley 49/2003); solo rige para contratos vigentes al 27-5-2004 (DT 1.ª). En contratos posteriores, art. 22.2 Ley 49/2003: tanteo y retracto del arrendatario agricultor profesional, 60 días hábiles. Fuente: Ley 49/2003, DD única, DT 1.ª y art. 22, BOE-A-2003-21616.], y corresponde pasivamente únicamente al demandado, como adquirente de la finca (1).

Respecto a la válida constitución de la relación jurídico procesal en los supuestos de ejercicio de la acción de retracto, la doctrina jurisprudencial, SSTS de 24 de mayo de 1986, 30 de enero de 1989, 11 de mayo de 1992, viene a establecer que esa acción real se ha de dirigir contra quien haya adquirido la cosa arrendada, ya que de prosperar el retracto se colocará el retrayente en el lugar del comprador, sin necesidad de otorgar nuevo contrato puesto que la compraventa no se resuelve sino que simplemente queda modificada subjetivamente por el cambio de la persona del comprador.

Solamente la existencia de transmisiones posteriores a la fecha de interposición de la demanda impone dirigirla conjuntamente contra los dos adquirentes, y al margen de la intervención voluntaria adhesiva que pueda pedir ex art. 13 LEC el vendedor.

IV.- PRESUPUESTOS PROCESALES.

Se han llenado, en atención al art. 266.2.º LEC los requisitos específicos de acreditación preliminar de la legitimación mediante determinados documentos, que son presupuesto de admisión (art. 269.2 LEC), y así se acompañan: el contrato de arrendamiento que constituye un principio de prueba del título en que se funda el derecho de retracto, y el documento que acredita haber consignado el importe del precio satisfecho por el adquirente que se desprende de la escritura de compraventa registrada (2).

A los efectos oportunos, esta parte expresa su compromiso de abonar los gastos legítimos a que se refiere el art. 1518 CCiv cuando sean conocidos.

La presente demanda cumple asimismo con los requisitos de procedibilidad exigidos por el art. 264.4º y art. 399.3 de la LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

V.- CUANTÍA.

Cumpliendo lo prevenido en el art. 253.1 LEC, puesto que la importancia económica del pleito es determinable, hacemos constar que la cuantía de esta demanda es la de [IMPORTE] euros, que resulta el precio de la finca que consta satisfecho por el demandado, según certificación registral -superior al valor catastral-, en armonía con el art. 251.3.ª.4.º LEC.

VI.- POSTULACION Y DEFENSA.

Se cumplen en la presente demanda lo dispuesto en los arts. 23 y 31 LEC, en cuanto a la representación procesal mediante Procurador/a. de los Tribunales habilitado en el Tribunal y a la dirección técnica de Abogado colegiado, que elabora y suscribe la presente demanda.

VII.- FONDO DEL ASUNTO.

Se ejercita en esta demanda una acción de retracto al amparo de lo dispuesto en los arts. 84.1.1.º y 86 y siguientes de la Ley 83/1980, de 31 de diciembre, de Arrendamientos Rústicos, aplicable al caso por razones de vigencia temporal, conforme a la Disposición Transitoria Primera de la Ley 49/2003, de 26 de noviembre, de arrendamientos rústicos (3).

Se ejercita el derecho dentro del plazo legal establecido de sesenta días hábiles, pues no habiendo sido notificado mi mandante de la transmisión, como debió haberlo sido, el plazo debe contarse desde que ha tenido cabal conocimiento de la misma y sus condiciones esenciales, lo que no ha ocurrido sino cuando recibió certificación del Registro de la Propiedad.

VIII.- COSTAS.

Conforme al art. 394 LEC las costas han de imponerse a la parte demandada.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que, teniendo por presentada esta demanda con sus documentos y copias la admita a trámite teniéndome por comparecido y parte en la representación que ostento; acordando dar traslado al demandado para que comparezca y la conteste, y previos los trámites legales de la audiencia previa y el acto del juicio, se dicte en su día sentencia por la que estimando la demanda:

1.º Se declare haber lugar al retracto arrendaticio de mi mandante sobre la finca denominada "" descrita en el hecho segundo de la demanda.
2.º Se condene al demandado a que, firme que sea la sentencia y en el plazo que se señale, otorgue a favor de mi mandante escritura pública de venta conforme al precio y demás condiciones que figuran en la escritura de adquisición por ella de dicha finca, bajo apercibimiento que de no hacerlo se podrá tener por emitida la correspondiente declaración de voluntad.
3.º Se impongan a la parte demandada las costas causadas.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

NOTAS DEL FORMULARIO

(1) En los arrendamientos sujetos a la Ley 49/2003, de 26 de noviembre, de arrendamientos rústicos, en la redacción dada por Ley 26/2005, de 30 de noviembre, el requisito de profesionalidad agraria de los arrendatarios para ejercitar el derecho de retracto se recoge en los arts. 9.1 y 22.2.

Téngase en cuenta que la Ley 49/2003, de 26 de noviembre, de arrendamientos rústicos, en su redacción original, suprimió tanto la profesionalidad agraria como condición para los arrendatarios, como los derechos de tanteo, retracto y adquisición preferente, que se volvieron a introducir con la reforma de la Ley 26/2005, de 30 de noviembre.

(2) La presentación de aval bancario a primer requerimiento a favor de la demandada por el importe del precio satisfecho para el ejercicio del derecho de retracto es práctica que cumple las exigencias del art. 266 LEC, como tuvo ocasión de declarar el Tribunal Constitucional, que en la sentencia 145/1998, de 30 de junio, estimó contrario al derecho a la tutela judicial efectiva entender que tal forma de consignar no cumple las exigencias legales, doctrina perfectamente aplicable a la actual regulación procesal.

(3) La vigente Ley 49/2003, de 26 de noviembre, de arrendamientos rústicos, en su redacción original, suprimió los derechos de tanteo, retracto y adquisición preferente, desde su entrada en vigor, el 27 de mayo de 2004, hasta el 31 de diciembre de 2005, en que entró en vigor la modificación operada por Ley 26/2005 que reintrodujo dichos derechos dando nueva redacción al art. 22, aplicable a los contratos celebrados bajo su vigencia.

En todo caso, estos derechos se mantienen respecto a los contratos concertados bajo el imperium de la Ley 83/1980, de 31 de diciembre, de Arrendamientos Rústicos, en que será aplicables los citados arts. 84.1.1.º y 86 y ss.

========================================================================
