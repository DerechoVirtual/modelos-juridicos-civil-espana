---
name: demanda-cumplimiento-compromiso-hacer-190
description: "Redacta el escrito «Demanda de cumplimiento de un compromiso de hacer» (formulario 190 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de cumplimiento de un compromiso de hacer

> Formulario 0190 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.

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
- [ ] LOCALIDAD (4 veces)
- [ ] FECHA (5 veces)
- [ ] NÚMERO (2 veces)
- [ ] IMPORTE (6 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…D»; «…rado de la Administración de Justicia de»; «…, bajo la dirección letrada de D»; «… perjuicios, demanda que dirijo contra D»; «…dante, como arrendador, y el demandado D»; «…rajudicial. En este sentido, se acudió a»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 9.3 de la LAU
- art. 10.3 de la LAU
- arts. 1088, 1089, 1091 y 1098 del Código Civil
- artículo 249 LEC
- art. 5 de la Ley Orgánica 1/2025
- artículo 1091 del CC
- art. 1098 CC
- art. 1809 CC
- artículo 1100 CC
- art. 1101 CC
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

### Formulario 0190 · Demanda de cumplimiento de un compromiso de hacer

- Año del modelo: 2021
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 27 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D [COMPLETAR], Procurador de los Tribunales en representación de [LOCALIDAD] según acredito por apoderamiento apud-acta otorgado ante el Letrado de la Administración de Justicia de [COMPLETAR], bajo la dirección letrada de D [COMPLETAR], Abogado del Iltre. Colegio de [LOCALIDAD], ante el Tribunal comparezco y como mejor en derecho proceda DIGO:

Que, por medio de la presente, formulo demanda de juicio ordinario en ejercicio de la acción para el cumplimiento de obligación de hacer y resarcimiento de daños y perjuicios, demanda que dirijo contra D [COMPLETAR], con domicilio en [LOCALIDAD], en base a los siguientes

HECHOS

PRIMERO.- Se insta en este proceso demanda para el cumplimiento del compromiso la obligación de hacer contraído por el demandado el cual se recoge en el documento de fecha [FECHA] que se acompaña como documento número

El citado compromiso trae causa del contrato de arrendamiento de vivienda suscrito el día [FECHA] entre mi mandante, como arrendador, y el demandado D [COMPLETAR], como arrendatario, que se acompaña como documento n.º [NÚMERO] En dicho contrato se pactaba una renta mensual de [IMPORTE] euros y una duración de

SEGUNDO.- Transcurrido el primer año del arrendamiento y teniendo mi representado la necesidad ocupar la vivienda para su hijo mayor que había sido trasladado por motivos de trabajo a la localidad donde se encuentra la vivienda, y constando la cláusula número [NÚMERO] del contrato la posibilidad de recuperarla según lo establecido en el art. 9.3 de la LAU, mi representado comunicó al arrendatario su voluntad de recuperar la vivienda, según acredito por el burofax de fecha [FECHA] que acompañó como documento número

Ante esta comunicación, el arrendatario solicitó a mi mandante seguir con el arrendamiento de la vivienda por un periodo de seis meses, alegando graves trastornos personales y familiares por el cambio de domicilio, a lo cual accedió mi representado, por lo que ambas partes suscribieron el documento de fecha [FECHA], en virtud del cual el arrendatario se comprometía a desalojar la vivienda dentro de los seis meses siguientes a la de la fecha de la firma del documento, tal como se acredita por el compromiso que se acompaña como documento número

Dicho compromiso tiene amparo en el art. 10.3 de la LAU que permite que las partes lleguen a un acuerdo distinto sobre el plazo de entrega de la vivienda arrendada, de manera que mi representado, de buena fe y atendiendo a las razones del arrendatario, convino con el mismo un plazo máximo de seis meses en lugar de los dos contemplados legalmente, el cual resultó dolosamente incumplido por el inquilino, tal como se relata a continuación.

TERCERO.- Vencido el plazo máximo de seis meses pactado, el arrendatario se niega a desalojar la vivienda, pese a los reiterados requerimientos de mi representado, tal como se acredita por el burofax de fecha [FECHA] que acompaño como documento número [Nº DE DOCUMENTO], ante lo cual nos vemos en la obligación de ejercitar esta acción judicial para la extinción del contrato y desalojo efectivo del inquilino.

La acción se funda en lo dispuesto en los arts. 1088, 1089, 1091 y 1098 del Código Civil en relación con lo dispuesto en los arts. 1809 y siguientes del Código Civil y art. 10.3 de la LAU, puesto que el arrendatario asumió el compromiso de desalojo voluntario de la vivienda a fin de evitar el ejercicio de la acción que correspondía a mi representado para la recuperación de la misma, de manera que se obligó a dejar la vivienda arrendada en el término estipulado, lo cual no ha hecho en contravención con la obligación de hacer contraída, por lo que se ejercita esta acción para el cumplimiento de dicha obligación.

CUARTO.- La conducta del demandado, de mala fe, ha ocasionado graves daños y perjuicios a mi representado, quien ha tenido que alquilar una vivienda en la misma localidad como consecuencia de la negativa dolosa del demandado al desalojo de la vivienda, habiendo satisfecho la cantidad de [IMPORTE] euros en concepto de comisión de agencia inmobiliaria, así como una cantidad mensual de [IMPORTE] euros, superior en [IMPORTE] euros a la que percibe como renta arrendaticia y que está abonando por una vivienda de menor calidad que la de su propiedad, todo lo cual justifico por el informe del agente de la propiedad inmobiliaria D. [NOMBRE Y APELLIDOS] y los documentos que acompaño como número

En consecuencia, se reclaman unos daños y perjuicios por importe total de [IMPORTE] euros, derivados del incumplimiento del demandado, los cuales se reclaman en esta demanda.

QUINTO.- Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

A estos hechos son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

PRIMERO.- Competencia.-Corresponde a los Tribunales de [LOCALIDAD] al ser el lugar en el que se encuentra la finca (art. 52.1.1.ºLEC, en relación con lo dispuesto en el art. 85.1º LOPJ).

SEGUNDO.- Legitimación.-Le corresponde a esta parte la legitimación activa en su condición de arrendador y parte acreedora en el acuerdo alcanzado con el arrendatario, en tanto que la legitimación pasiva corresponde al inquilino demandado.

TERCERO.- Procedimiento: Es el juicio ordinario con fundamento en el artículo 249 LEC.

CUARTO.- Cumplimiento de los requisitos de procedibilidad: La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia

QUINTO.- Acción ejercitada: Es de aplicación lo dispuesto en los arts. 1088, 1089, 1091 y 1098 del Código Civil en relación con lo dispuesto en los arts. 1809 y siguientes del Código Civil y art. 10.3 de la LAU. El artículo 1091 del CC “las obligaciones que nacen de los contratos tienen fuerza de ley entre las partes contratantes, y deben cumplirse a tenor de los mismos, en tanto que el art. 1098 CC dispone: “Si el obligado a hacer alguna cosa no la hiciere, se mandará ejecutar a su costa. Esto mismo se observará si la hiciere contraviniendo al tenor de la obligación. Además podrá decretarse que se deshaga lo mal hecho.

El art. 1809 CC establece: “La transacción es un contrato por el cual las partes, dando, prometiendo o reteniendo cada una alguna cosa, evitan la provocación de un pleito o ponen término al que había comenzado”.

El art. 10.3 de la LAU dispone: “Una vez transcurrido el primer año de duración del contrato y siempre que el arrendador sea persona física, no procederá la prórroga obligatoria del contrato cuando, al tiempo de su celebración, se hubiese hecho constar en el mismo, de forma expresa, la necesidad para el arrendador de ocupar la vivienda arrendada antes del transcurso de cinco años para destinarla a vivienda permanente para sí o sus familiares en primer grado de consanguinidad o por adopción o para su cónyuge en los supuestos de sentencia firme de separación, divorcio o nulidad matrimonial.

Para ejercer esta potestad de recuperar la vivienda, el arrendador deberá comunicar al arrendatario que tiene necesidad de la vivienda arrendada, especificando la causa o causas entre las previstas en el párrafo anterior, al menos con dos meses de antelación a la fecha en la que la vivienda se vaya a necesitar y el arrendatario estará obligado a entregar la finca arrendada en dicho plazo si las partes no llegan a un acuerdo distinto”.

SEXTO.- Indemnización de daños y perjuicios: El artículo 1100 CC en cuanto a la mora, y el art. 1101 CC en cuanto a la indemnización por incumplimiento, estableciendo este último precepto: “Quedan sujetos a la indemnización de los daños y perjuicios causados los que en el cumplimiento de sus obligaciones incurrieren en dolo, negligencia o morosidad, y los que de cualquier modo contravinieren al tenor de aquéllas”. Por su parte, el art. 1102 del mismo texto legal dispone: “La responsabilidad procedente del dolo es exigible en todas las obligaciones(..)” en tanto que el art. 1107.II establece:” En caso de dolo responderá el deudor de todos los que conocidamente se deriven de la falta de cumplimiento de la obligación”.

SÉPTIMO.- En materia de costas el artículo 394 LEC señala que las de primera instancia se imponen a la parte que vea en primera instancia rechazadas sus pretensiones

En base a lo anterior,

SUPLICO AL TRIBUNAL que tenga por presentada la presente demanda con los documentos a ella adjuntos y sus copias, en la representación que ostento, y se tenga por formulada demanda de acción en ejercicio de la acción para el cumplimiento de obligación de hacer y resarcimiento de daños y perjuicios, y en su virtud se dicte sentencia por la que, de acuerdo a lo expuesto en esta demanda, se acuerde el desalojo forzoso del demandado de la vivienda arrendada, la cual deberá dejar libre y a disposición del actor, y que se le condene a que indemnice a mi representado en la cantidad de [IMPORTE] euros, todo ello con condena en costas al demandado.

OTROSÍ DIGO que se acompaña en anexo relación de documentos e informe pericial presentados, debidamente foliados y con índice electrónico, para su debida localización y consulta.

SUPLICO AL TRIBUNAL tenga hecha esta manifestación a los efectos oportunos y por aportados los documentos e informe pericial relacionados en el anexo.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

El Abogado El Procurador
