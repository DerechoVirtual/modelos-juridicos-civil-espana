---
name: cesacion-actividad-contra-propietario-general-1339
description: "Redacta el escrito «Cesación de actividad contra propietario (general)» (formulario 1339 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Cesación de actividad contra propietario (general)

> Formulario 1339 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (9 veces)
- [ ] Nº (3 veces)
- [ ] NIF
- [ ] Nº DE COLEGIADO/A
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «…rajudicial. En este sentido, se acudió a»; «…alubres, nocivas y peligrosas. Tercero.—»; «…rma de abogado y procurador OTROSÍ DIGO:»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Acciones / Comuneros / Presidente — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Estatutos / Normativa local / Actividad ilícita manifiesta — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Ausentes / Reserva voto — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 85 de la LOPJ
- art. 10 de la Ley 10/2012
- artículo 10 de la LEC
- artículos 23 y 31 de la LEC
- art. 5 de la Ley Orgánica 1/2025
- artículo 7.2 de la LPH
- artículo 394 de la LEC

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

### Formulario 1339 · Cesación de actividad contra propietario (general)

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 3 bloques de opciones sin texto dejados en blanco con sus rótulos; 19 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Acción de cesación

Demanda. Juicio ordinario

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS] Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], Presidente de la Comunidad de Propietarios de la C/ n.º [Nº], con CIF nº [NIF], que actúa en nombre y por orden de ésta, según acredito mediante poder notarial que acompaño, ante el Tribunal comparezco con la asistencia letrada de D. /Dña. [NOMBRE Y APELLIDOS] (Colegiado nº [Nº DE COLEGIADO/A]) y como mejor proceda en derecho DIGO:

Que mediante el presente escrito y según permite el artículo 7.2 de la Ley de Propiedad Horizontal (LPH), interpongo demanda a tramitar por el cauce del juicio ordinario en ejercicio de acción de cesación de actividad contra D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en y DNI n.º [Nº], que se basa en los siguientes

HECHOS

Acompañamos índice numerado de los documentos que se presentan como prueba con la demanda.

El demandado es propietario de situado en la C/ n.º [Nº] de [COMPLETAR], que forma parte de la Comunidad demandante. Acredito la titularidad con nota simple del Registro de la Propiedad que acompaño como documento n.º [Nº DE DOCUMENTO].

Desde el mes de los vecinos comenzaron a notar que y

- pusieron los hechos en conocimiento del Presidente de la Comunidad requiriéndole para que tomara las medidas oportunas, según acredito con escrito suscrito por varios comuneros que acompaño como documento nº [Nº DE DOCUMENTO]

- el presidente decidió, ante la evidencia de los hechos, requerir al autor para que depusiera en su actitud.

[ELEGIR UNA OPCIÓN Y REDACTARLA: Acciones / Comuneros / Presidente — el texto de cada opción no venía en el formulario original]

Así las cosas, el Presidente requirió de forma fehaciente al propietario del inmueble situado en para que cesara en la actividad con apercibimiento de que, en caso contrario, se vería obligado a iniciar las actuaciones judiciales oportunas. Adjunto como documentos n.º copia del burofax remitido y certificado de acuse de recibo.

D./Dña. [NOMBRE Y APELLIDOS] se entrevistó con el Presidente de la Comunidad el día para manifestarle que no consideraba que la actividad de tuviera el carácter que le concedían el resto de los comuneros, aunque procuraría aminorar los, pero que no iba a cesar en ella.

Por parte del perito con título en se elaboró informe pericial en el que se hace constar que la actividad de realizada por D./Dña. [NOMBRE Y APELLIDOS] es porque Con el n.º aportamos informe pericial.

[ELEGIR UNA OPCIÓN Y REDACTARLA: Estatutos / Normativa local / Actividad ilícita manifiesta — el texto de cada opción no venía en el formulario original]

A la vista de que el propietario no tomó en consideración el requerimiento enviado por la presidencia de la Comunidad, se convocó Junta Extraordinaria a celebrar el día en cuyo orden del día se incluía el siguiente punto: “Tras el requerimiento a D./Dña. [NOMBRE Y APELLIDOS] para que cesara en la actividad de se ha podido constatar que el comunero persiste en su actitud, motivo por el que se procederá al estudio de la posibilidad de interponer demanda ante el Tribunal de cesación de actividad. Se someterá a votación si se interpone dicha demanda autorizando al Presidente para que actúe a tal fin ante los Jueces y Tribunales de y, en caso afirmativo, se votará también si se autoriza al Presidente para que otorgue poderes a favor de Procurador, designando también Abogado, para que representen y defiendan, respectivamente, a la Comunidad. Acompaño como documentos n.º copia de la convocatoria y acuse de recibo de la notificación al demandado”.

En la referida Junta se acordó por mayoría presentar esta demanda, según acredito con certificación del acta expedida por de la Comunidad con el visto bueno del Presidente.

[ELEGIR UNA OPCIÓN Y REDACTARLA: Ausentes / Reserva voto — el texto de cada opción no venía en el formulario original]

Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

Consecuentemente, se han cumplido los requisitos previos exigidos en la ley para poder interponer la demanda una vez constatada la imposibilidad de llegar a un acuerdo extrajudicial.

FUNDAMENTOS DE DERECHO

Los artículos 21 y 22 de la Ley Orgánica del Poder Judicial (LOPJ) y 36 de la Ley de Enjuiciamiento Civil (LEC) atribuyen con carácter general a la jurisdicción española y al orden civil el conocimiento de esta materia. Los artículos 85 de la LOPJ y 45 de la LEC designan a las secciones civiles de los Tribunales de Instancia como los encargados de resolver estos pleitos. Y, por último, el artículo 52.1.8.º de la LEC determina la competencia territorial que vendrá marcada por el lugar donde radique la finca.

El artículo 7.2, párrafo tercero, de la LPH remite al cauce del juicio ordinario con las especialidades recogidas en este precepto. En el mismo sentido se pronuncia el artículo 249.1.8.º de la LEC.

Se fija la cuantía de este pleito como indeterminada.

(En su caso) En aplicación del art. 10 de la Ley 10/2012, de 20 de noviembre, se aplica a la tasa resultante una bonificación del 10% por utilización de medios telemáticos en la presentación de escritos.

El artículo 10 de la LEC legitima para comparecer en juicio a los titulares de la relación jurídica u objeto litigioso. Aunque el artículo 6.1.5.º de la LEC dice que podrán ser parte en los procesos civiles las entidades sin personalidad jurídica a las que la ley reconozca capacidad para ser parte, y el artículo 7.6 del mismo texto legal dice que estas entidades comparecerán en juicio por medio de las personas a quienes la ley atribuya en cada caso su representación en juicio, el artículo 7.2, párrafo tercero de la LPH indica que será el Presidente de la Comunidad quien presentará la demanda ejercitando la acción de cesación.

En aplicación de los artículos 23 y 31 de la LEC, las partes deberán comparecer representadas por Procurador y asistidas de Letrado.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Primero.— El artículo 7.2 de la LPH prohíbe al propietario de un piso o local realizar en él o en el resto del inmueble actividades prohibidas en los estatutos, que resulten dañosas para la finca o que contravengan las disposiciones generales sobre actividades molestas, insalubre, nocivas, peligrosas o ilícitas.

Segundo.— El artículo 6.a) del Real Decreto legislativo 7/2015, de 30 de octubre, por el que se aprueba el texto refundido de la Ley de Suelo y Rehabilitación Urbana, obliga a los ciudadanos a cumplir los requisitos y condiciones a que la legislación sujete las actividades molestas, insalubres, nocivas y peligrosas.

Tercero.— [COMPLETAR]

Cuarto.— El artículo 9.1 en sus apartados a) y b) de la Ley de Propiedad Horizontal impone al propietario la obligación de hacer un uso adecuado de las instalaciones generales y la de mantener en buen estado de conservación el propio piso o local.

Quinto.— Se han cumplido las formalidades previas que exige el citado artículo 7.2 de la LPH:

— Requerimiento por el Presidente de la Comunidad al propietario para que cese en la actividad que se considera, con apercibimiento de iniciar acciones judiciales si continuaba ejerciéndola.

— Autorización de la Junta de Propietarios al Presidente para entablar la acción de cesación.

— Autorización de la Junta de Propietarios al Presidente para dar poder a Procurador y designar Letrado para formular la demanda y continuar el juicio.

En aplicación del artículo 394 de la LEC deberán imponerse al demandado.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y copia de todo ello, lo admita a trámite dictando el Letrado de la Administración de Justicia el Oportuno decreto y tenga por formulada demanda en ejercicio de acción de cesación contra D./Dña. [NOMBRE Y APELLIDOS] a fin de que en su día y, previos los trámites legales oportunos, se dicte sentencia por la que se declare:

1.º Que la actividad de se considera.

2.º Que D./Dña. [NOMBRE Y APELLIDOS] deberá cesar inmediatamente en el ejercicio de la actividad descrita en el párrafo anterior.

3.º Que se impongan al demandado las costas de este procedimiento.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de abogado y procurador

OTROSÍ DIGO: [COMPLETAR].

Es justicia que pido en mismo lugar y fecha.

Firma de abogado y procurador

========================================================================
