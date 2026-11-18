---
name: demanda-medidas-previas-divorcio-entre-espanoles-293
description: "Redacta el escrito «Demanda de medidas previas al divorcio entre españoles con traslado de uno a Reino Unido» (formulario 293 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de medidas previas al divorcio entre españoles con traslado de uno a Reino Unido

> Formulario 0293 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] NIF
- [ ] DNI/NIE
- [ ] Nº DE DOCUMENTO (10 veces)
- [ ] IMPORTE (14 veces)
- [ ] Nº
- [ ] MATRÍCULA (4 veces)
- [ ] Otros 30 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ntación de Dª., mayor de edad, vecina de»; «…ISIONALES PREVIAS de divorcio contra Don»; «…ª y D. contrajeron matrimonio en España,»; «…el»; «…al Tomo»; «…al Tomo [COMPLETAR], página»; «…, página [COMPLETAR] de la Sección»; «…nión ha nacido en una hija común llamada»; «…el»; «…al Tomo»; «…l Tomo [COMPLETAR], página de la Sección»; «…mi representada/o trabaja actualmente en»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 102 y 103 del Código Civil
- art. 154 del Código Civil
- artículo 771 LEC
- artículo 102 del Código Civil
- art. 437.1 LEC
- art. 5 de la Ley Orgánica 1/2025
- artículo 103 CC
- artículo 104 CC
- arts. 23 y 31 de la LEC
- Ley 17/2021

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

### Formulario 0293 · Demanda de medidas previas al divorcio entre españoles con traslado de uno a Reino Unido

- Año del modelo: 2020
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 53 campos de relleno marcados en blanco; 14 huecos del original que se habían perdido sin marca, marcados (IMPORTE, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD DEL TRIBUNAL DE INSTANCIA DE [SEDE] QUE POR TURNO CORRESPONDA.

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

D. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de Dª., mayor de edad, vecina de [COMPLETAR], con domicilio en [LOCALIDAD], y provisto de NIF [NIF], representación que consta (en el poder general para pleitos que se aporta/apoderamiento apud acta que a tal fin se otorgará ante el Letrado de la Administración de Justicia, ante el Tribunal con el mayor respeto comparezco bajo la dirección letrada de D. [NOMBRE Y APELLIDOS] y como mejor proceda DIGO:

Que de conformidad con lo dispuesto en los artículos 102 y 103 del Código Civil, y el artículo 771 de la Ley de Enjuiciamiento Civil, solicito la adopción de MEDIDAS PROVISIONALES PREVIAS de divorcio contra Don [COMPLETAR], mayor de edad, con domicilio en y NIE [DNI/NIE].

Se basa la presente solicitud en los siguientes

HECHOS

PRIMERO.- Que Dª y D. contrajeron matrimonio en España, [COMPLETAR] el [COMPLETAR] bajo el régimen económico matrimonial de gananciales, tal y como consta en el Registro Civil de [LOCALIDAD] al Tomo [COMPLETAR], página [COMPLETAR] de la Sección [COMPLETAR].

Aportamos certificado de matrimonio como documento nº [Nº DE DOCUMENTO].

SEGUNDO.- Que de esa unión ha nacido en una hija común llamada [COMPLETAR] el [COMPLETAR], tal y como consta en el Registro Civil de [LOCALIDAD] al Tomo [COMPLETAR], página de la Sección [COMPLETAR].

Aportamos certificado de nacimiento como documento nº [Nº DE DOCUMENTO].

TERCERO Que el domicilio familiar ha estado situado en C/, donde en la actualidad sigue residiendo la madre con su hija menor de edad.

CUARTO.- El régimen económico del matrimonio es el de gananciales.

QUINTO.- El esposo/a de mi representada/o trabaja actualmente en [COMPLETAR], percibiendo un salario neto de [IMPORTE] euros mensuales, tal y como acreditamos con las nóminas de [COMPLETAR] que aportamos como documentos nº [Nº DE DOCUMENTO], [COMPLETAR] y [COMPLETAR].

SEXTO.- Los gastos habituales de la familia rondan alrededor de [IMPORTE] € mensuales, concretándose en:

- Media mensual de consumo de agua: [IMPORTE] €.

(Se adjunta extracto como Documento número [Nº DE DOCUMENTO]).

- Media mensual de suministro de electricidad y gas: [IMPORTE] €.

(Se acredita con el extracto, documento número [Nº DE DOCUMENTO]).

- Media mensual de teléfono: [IMPORTE] €.

(Se acredita con el extracto, documento número [Nº DE DOCUMENTO])

Cuota mensual de guardería/colegio: [IMPORTE] €.

(Se acredita con el extracto, documento número [Nº DE DOCUMENTO]).

- Media mensual de gastos de alimentación: [IMPORTE] €.

- Media mensual de ropa y otras necesidades de la hija común: [IMPORTE] €.

- Cuota mensual préstamo hipotecario de la vivienda familiar: [IMPORTE] €.

- Cuota mensual préstamo coche del esposo: [IMPORTE] €.

(Se acredita con el extracto, documento número [Nº DE DOCUMENTO]).

- Cuota mensual préstamo coche de la esposa: [IMPORTE] €.

(Se acredita con el extracto, documento número [Nº DE DOCUMENTO]).

IMPORTE TOTAL APROXIMADO DE GASTOS MENSUALES: [IMPORTE] €.

SÉPTIMO.- El ahora demandado ha trasladado su residencia a la localidad escocesa de [COMPLETAR] como consecuencia de un nuevo trabajo ofertado por la empresa [COMPLETAR] para la que lleva prestando servicios desde hace más de [Nº] años.

OCTAVO Dada la situación personal y patrimonial expuesta y acreditada en este escrito, se solicitan como medidas provisionales previas las que se exponen a continuación:

VIII.1Revocación de poderes y consentimientos entre los cónyuges.

VIII.2.-La patria potestad sobre la menor [COMPLETAR] se ejercerá por ambos progenitores conforme establece el art. 154 del Código Civil en la nueva redacción dada por la L.O. 8/2021 de 4 de junio.

VIII.3.- La guarda y custodia de la menor se atribuye a la madre [COMPLETAR].

VIII.4.- Visitas: el progenitor no custodio disfrutará de su hija al menos un fin de semana al mes durante 3 días consecutivos, que comenzarán el viernes a la salida del colegio y la reintegrará el lunes a la entrada del colegio. Se harán coincidir los puentes escolares para que el padre tenga más días disponibles de estancia con su hija.

Vacaciones de Navidad, por mitad de las vacaciones escolares.

Vacaciones de verano: el padre tendrá derecho a estar con su hija un mes consecutivo de julio o de agosto, a su elección. A falta de acuerdo, elegirá el padre los años pares y la madre los impares.

Las vacaciones de Semana Santa serán disfrutadas íntegramente por cada progenitor por años alternativos, comenzando su disfrute el padre.

VIII.5.- Uso del domicilio familiar. Se atribuye el uso de la vivienda familiar y del ajuar doméstico a la madre para que viva en ella con su hija.

El ahora demandado retirará de la vivienda sus enseres y efectos personales.

VIII.6.- Contribución a las cargas del matrimonio. Se solicita por esta parte que en concepto de contribución a las cargas del matrimonio que Don [COMPLETAR] abone a mi mandante la cantidad de [IMPORTE] EUROS mensuales.

VIII.7.- Atribuir provisionalmente el uso del vehículo [COMPLETAR] matrícula [MATRÍCULA] a Dª [COMPLETAR] en exclusiva.

VIII.8.- D. deberá pagar en exclusiva la cuota mensual del vehículo [COMPLETAR] matrícula [MATRÍCULA], así como de la cuota del renting del teléfono móvil del que hace uso particular y en exclusiva.

NOVENO Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

I.- Competencia: Es competente el Tribunal al que me dirijo por tratarse de un litigio entre españoles, según disponen los arts. 21.1 y 36.1 ambos de la Ley de Enjuiciamiento Civil; en concreto el artículo 22.3 del mismo cuerpo legal dispone que serán competentes los tribunales españoles en materia de separación y divorcio cuando ambos cónyuges tengan fijada su residencia en España al tiempo de interponer la demanda. Territorialmente es competente este Tribunal pues su último domicilio familiar estaba sito en España, concretamente en la localidad de [COMPLETAR].

II.- Legitimación: Está legitimada activamente nuestra mandante en su cualidad de cónyuge y se interpone contra el ahora demandado, que es su esposo y padre de la hija común habida en el matrimonio.

III.- Cuantía: La cuantía es indeterminada.

IV.- Procedimiento: El artículo 771 LEC, en la redacción dada por la Ley 17/2021, de 15 de diciembre, dispone [NOTA DE REVISIÓN: El texto que transcribe el formulario ya es el vigente (incluye animales de compañía), cuya redacción procede de la Ley 17/2021. Fuente: LEC 1/2000 (BOE-A-2000-323) art. 771 (redacción Ley 17/2021 (BOE-A-2021-20727), vigente desde 05-01-2022).] el cauce procedimental:

1. El cónyuge que se proponga demandar la nulidad, separación o divorcio de su matrimonio puede solicitar los efectos y medidas a que se refieren los artículos 102 y 103 del Código Civil ante el tribunal de su domicilio.

Para formular esta solicitud no será precisa la intervención de procurador y abogado, pero sí será necesaria dicha intervención para todo escrito y actuación posterior.

2. A la vista de la solicitud, el letrado de la Administración de Justicia citará a los cónyuges y, si hubiere hijos menores o hijos con discapacidad con medidas de apoyo atribuidas a sus progenitores, al Ministerio Fiscal, a una comparecencia en la que se intentará un acuerdo de las partes, que señalará el letrado de la Administración de Justicia y que se celebrará en los diez días siguientes. A dicha comparecencia deberá acudir el cónyuge demandado asistido por su abogado y representado por su procurador.

De esta resolución dará cuenta en el mismo día al Tribunal para que pueda acordar de inmediato, si la urgencia del caso lo aconsejare, los efectos a los que se refiere el artículo 102 del Código Civil y lo que considere procedente en relación con la custodia de los hijos y uso de la vivienda, atribución, convivencia y necesidades de los animales de compañía y ajuar familiares. Contra esta resolución no se dará recurso alguno.

3. En el acto de la comparecencia a que se refiere el apartado anterior, si no hubiere acuerdo de los cónyuges sobre las medidas a adoptar o si dicho acuerdo, oído, en su caso, el Ministerio Fiscal, no fuera aprobado en todo o en parte por el Tribunal, se oirán las alegaciones de los concurrentes y se practicará la prueba que éstos propongan y que no sea inútil o impertinente, así como la que el Tribunal acuerde de oficio. Si alguna prueba no pudiera practicarse en la comparecencia, el Letrado de la Administración de Justicia señalará fecha para su práctica, en unidad de acto, dentro de los diez días siguientes.

La falta de asistencia, sin causa justificada, de alguno de los cónyuges a la comparecencia podrá determinar que se consideren admitidos los hechos alegados por el cónyuge presente para fundamentar sus peticiones sobre medidas provisionales de carácter patrimonial.

4. Finalizada la comparecencia o, en su caso, terminado el acto que se hubiere señalado para la práctica de la prueba que no hubiera podido producirse en aquélla, el tribunal resolverá, en el plazo de tres días, mediante auto, contra el que no se dará recurso alguno.

5. Los efectos y medidas acordados de conformidad con lo dispuesto en este artículo sólo subsistirán si, dentro de los treinta días siguientes a su adopción se presenta la demanda de nulidad, separación o divorcio. ».

V.- Cumplimiento de los requisitos de procedibilidad:

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC en relación con el art. 437.1 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VI.- Fondo del asunto:

- El artículo 102 del Código Civil, como efecto automático de la nulidad, separación o divorcio, se producen por ministerio de la Ley los efectos siguientes:

“1.- Los cónyuges podrán vivir separados y cesa la presunción de convivencia conyugal.

2.- Quedan revocados los consentimientos y poderes que cualquiera de los cónyuges hubiera otorgado al otro.

3.- Salvo pacto en contrario, cesa la posibilidad de vincular los bienes privativos del otro cónyuge en el ejercicio de la potestad doméstica”.

- El artículo 103 CC dispone: «Admitida la demanda, el Juez, a falta de acuerdo de cónyuges aprobado judicialmente, adoptará, con audiencia de éstos las medidas siguientes:

“1.ª Determinar, en interés de los hijos, con cuál de los cónyuges han de quedar los sujetos a la patria potestad de ambos y tomar las disposiciones apropiadas de acuerdo con lo establecido en este Código y, en particular, la forma en que el cónyuge que no ejerza la guarda y custodia de los hijos podrá cumplir el deber de velar por éstos y el tiempo, modo y lugar en que podrá comunicar con ellos y tenerlos en su compañía (…).

2ª) Determinar, teniendo en cuenta el interés familiar más necesitado de protección, cuál de los cónyuges ha de continuar en el uso de la vivienda familiar y asimismo, previo inventario, los bienes y objetos del ajuar que continúan en ésta y los que se ha de llevar el otro cónyuge, así como también las medidas cautelares convenientes para conservar el derecho de cada uno.

3ª) Fijar la contribución de cada cónyuge a las cargas del matrimonio, incluidas si procede las "litis expensas", establecer las bases para la actualización de cantidades y disponer las garantías, depósitos, retenciones u otras medidas cautelares convenientes, a fin de asegurar la efectividad de lo que por estos conceptos un cónyuge haya de abonar al otro.

Se considerará contribución a dichas cargas el trabajo que uno de los cónyuges dedicará a la atención de los hijos comunes sujetos a patria potestad.

4ª) Señalar, atendidas las circunstancias, los bienes gananciales o comunes que, previo inventario, se hayan de entregar a uno u otro cónyuge y las reglas que deban observar en la administración y disposición, así como en la obligatoria rendición de cuentas sobre los bienes comunes o parte de ellos que reciban y los que adquieran en lo sucesivo.

5ª) Determinar, en su caso, el régimen de administración y disposición de aquellos bienes privativos que por capitulaciones o escritura pública estuvieran especialmente afectados a las cargas del matrimonio. ”

- El artículo 104 CC: «El cónyuge que se proponga demandar la nulidad, separación o divorcio de su matrimonio puede solicitar los efectos y medidas a que se refieren los dos artículos anteriores».

VII.- Postulación:

En virtud de lo dispuesto en los arts. 23 y 31 de la LEC la demandante comparece representada por procurador y asistida de letrado.

Resulta preceptiva la intervención del Ministerio Fiscal al haber intereses de hijos menores.

VIII.- Medidas solicitadas: son las contenidas en Hecho Octavo de esta demanda que se dan por íntegramente reproducidas a fin de evitar reiteraciones innecesarias.

IX.- COSTAS: Se impondrán al demandado si se opusiera temerariamente a esta demanda.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL: Que teniendo por presentado este escrito, su copia y los documentos que se acompañan. Admita todo ello y tenga por SOLICITADAS MEDIDAS PROVISIONALES PREVIAS A LA DEMANDA en nombre de Dª, para lo que se acordará la formación de pieza separada; y previo emplazamiento del demandado, acuerde convocar a las partes a la comparecencia prevista en la Ley de Enjuiciamiento Civil y tras la celebración de dicho acto, en el que se intentará un acuerdo de las partes, y demás trámites legales pertinentes, se dicte Auto por el que se decrete la adopción de las medidas provisionales expuestas e interesadas en el cuerpo de este escrito, y que reproducimos a continuación:

Revocación de poderes y consentimientos entre los cónyuges.

La patria potestad sobre la menor se ejercerá por ambos progenitores conforme establece el art. 154 del Código Civil.

La guarda y custodia de la menor se atribuye a la madre [COMPLETAR].

Visitas: el progenitor no custodio disfrutará de su hija al menos un fin de semana al mes durante 3 días consecutivos, que comenzarán el viernes a la salida del colegio y la reintegrará el lunes a la entrada del colegio. Se harán coincidir los puentes escolares para que el padre tenga más días disponibles de estancia con su hija.

Vacaciones de Navidad, por mitad de las vacaciones escolares.

Vacaciones de verano: el padre tendrá derecho a estar con su hija un mes consecutivo de julio o de agosto, a su elección. A falta de acuerdo, elegirá el padre los años pares y la madre los impares.

Las vacaciones de Semana Santa serán disfrutadas íntegramente por cada progenitor por años alternativos, comenzando su disfrute el padre.

Uso del domicilio familiar. Se atribuye el uso de la vivienda familiar y del ajuar doméstico a la madre para que viva en ella con su hija.

El ahora demandado retirará de la vivienda sus enseres y efectos personales.

Contribución a las cargas del matrimonio. Se solicita por esta parte que en concepto de contribución a las cargas del matrimonio que Don Julio abone a mi mandante la cantidad de [IMPORTE] EUROS mensuales.

Atribuir provisionalmente el uso del vehículo [COMPLETAR], matrícula [MATRÍCULA] a Dª [COMPLETAR] en exclusiva.

D. deberá pagar en exclusiva la cuota mensual del vehículo [COMPLETAR], matrícula [MATRÍCULA], así como de la cuota del renting del teléfono móvil del que hace uso particular y en exclusiva.

Y condene al demandado a las costas en caso de oponerse temerariamente a esta demanda. Es Justicia que pido [COMPLETAR].

Fdo. Fdo..
