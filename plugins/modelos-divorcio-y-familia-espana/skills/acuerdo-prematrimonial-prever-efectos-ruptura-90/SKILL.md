---
name: acuerdo-prematrimonial-prever-efectos-ruptura-90
description: "Redacta el escrito «Acuerdo prematrimonial para prever los efectos de una ruptura» (formulario 90 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acuerdo prematrimonial para prever los efectos de una ruptura

> Formulario 0090 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] NÚMERO (2 veces)
- [ ] FECHA
- [ ] Nº (7 veces)
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] IMPORTE
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ento privado. REUNIDOS DE UNA PARTE, Don»; «…, mayor de edad, soltero, vecino de»; «…Y DE OTRA, Doña»; «…, mayor de edad, soltera, vecina de»; «…aicismo- Serán escolarizados en colegios»; «…partida y se distribuirá por períodos de»; «…atrimonio, la cantidad a abonar sería de»; «…ón del matrimonio, y con anterioridad al»; «…iversario, la cantidad a abonar sería de»; «…atrimonio, la cantidad a abonar sería de»; «…cado y a un solo efecto. En la ciudad de»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Respecto de los hijos del matrimonio / Cláusula básica de gastos extraordinarios / Cláusula detallada de gastos extraordinarios — el texto de cada opción no venía en el formulario original

## Párrafos opcionales (4)

Inclúyelos solo si encajan en los hechos:

- (Si se pacta la custodia individual a favor de uno de los progenitores)…
- (Si se pacta la custodia compartida)…
- (Si se pacta pensión compensatoria)…
- (Si se excluye la pensión compensatoria)…

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 0090 · Acuerdo prematrimonial para prever los efectos de una ruptura

- Año del modelo: 2023
- Revisión 17-11-2026: saltos de párrafo recuperados (texto venía pegado); 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 4 párrafos opcionales señalados; 32 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Los acuerdos prematrimoniales o prenupciales son pactos a través de los cuales los futuros cónyuges pactan un acuerdo económico para el caso de separación conyugal o divorcio.

En cuanto a su forma, han de realizarse en escritura pública todos aquellos pactos prematrimoniales que afecten al contenido de las capitulaciones matrimoniales, y los que expresamente deban ser establecidos en capitulaciones matrimoniales, como los pactos sucesorios de mejora y aquellos que deban tener efectos frente a terceros y que, por lo tanto, habrán de ser inscritos en los registros públicos. Sin embargo, los que recojan acuerdos en relación a otras materias que no afectan el régimen económico matrimonial o sucesorio, como los que regulen la pensión compensatoria u otros efectos de la separación o divorcio del matrimonio, podrán ser otorgados en documento privado.

REUNIDOS

DE UNA PARTE, Don [COMPLETAR], mayor de edad, soltero, vecino de [COMPLETAR], con domicilio en [LOCALIDAD] y con Documento Nacional de Identidad número [NÚMERO]

Y DE OTRA, Doña [COMPLETAR], mayor de edad, soltera, vecina de [COMPLETAR], con domicilio en [LOCALIDAD] y con Documento Nacional de Identidad número [NÚMERO]

INTERVIENEN

Ambos en su propio nombre y derecho, reconociéndose mutuamente con capacidad suficiente para otorgar el presente ACUERDO PREMATRIMONIAL y, a tal fin,

EXPONEN

I.- Que proyectan contraer matrimonio civil/canónico el próximo día [FECHA]

II.- Que, aun seguros de la perdurabilidad de su futuro matrimonio, de común acuerdo, las partes desean regular las consecuencias que pudieran producirse en caso de una eventual ruptura conyugal, tanto en lo relativo a las relaciones entre ambos como respecto de los posibles hijos de ambos, conscientes de que tales previsiones contribuirían decisivamente a reducir el grado de conflictividad que este tipo de situaciones suelen acarrear.

Por todo ello, suscriben el presente documento que se regirá por las siguientes,

CLÁUSULAS

Primera. Respecto de los hijos

Los futuros hijos fruto del matrimonio serán educados en la fe católica u otra/el laicismo-

Serán escolarizados en colegios [COMPLETAR] de su zona de residencia. La ruptura matrimonial no será en sí misma causa de cambio de colegio en el que estuvieran escolarizados al tiempo de la ruptura.

Los padres se comprometen a sufragar al 50% los gastos de un seguro médico en el que serán suscritos al nacer, hasta la edad de [Nº] años. La ruptura matrimonial no será causa en sí misma de cambio de seguro al que estuvieran suscritos al tiempo de la ruptura, y se comprometen a seguir pagando en dicho porcentaje el referido seguro médico.

[OPCIONAL — incluir si procede]

(Si se pacta la custodia individual a favor de uno de los progenitores)

En caso de ruptura matrimonial, los futuros hijos del matrimonio quedarán bajo la guarda y custodia de Don/Doña [NOMBRE Y APELLIDOS], siendo en todo caso la patria potestad ejercida por ambos progenitores.

La contribución a los alimentos de los hijos se efectuará del modo siguiente:

El régimen de visitas respecto al progenitor no custodio, se distribuirá atendiendo a los siguientes criterios:

[OPCIONAL — incluir si procede]

(Si se pacta la custodia compartida)

En caso de ruptura matrimonial, la guarda y custodia de los futuros hijos del matrimonio será compartida y se distribuirá por períodos de [COMPLETAR]

La contribución a los alimentos de los hijos se efectuará del modo siguiente:

Con este régimen de relaciones paterno-filiales las partes asumen el compromiso de comunicarse todas las decisiones que, con respecto a sus hijos, adopten en el futuro, así como todo aquello que, conforme al interés prioritario de los menores, deban conocer ambos padres.

Para ello, los progenitores deberán establecer el cauce de comunicación que mejor se adapte a sus circunstancias, obligándose a respetarlo y cumplirlo. En su defecto, la comunicación se hará vía burofax y el otro progenitor deberá contestar en plazo de cinco días. Si no contesta, y queda probado que ha recibido la comunicación, se entenderá que presta su conformidad.

Ambos padres participarán en las decisiones que, con respecto al/a los hijo/s, tomen en el futuro, siendo de especial relevancia las que se vayan a adoptar en relación a la residencia del menor o las que afecten al ámbito escolar, sanitario y los relacionados con celebraciones religiosas. Sobre esta base, se impone la intervención de ambos padres en decisiones relativas al cambio de centro escolar o cambio de modelo educativo. Se impone, así mismo, la decisión conjunta para cualquier tipo de intervención quirúrgica o de tratamiento médico no banal, tanto si entraña un gasto como si está cubierto por algún seguro, salvo supuestos de extrema urgencia. Se impone igualmente la intervención y decisión de ambos padres en las celebraciones religiosas, obligatoriamente en lo relativo a la realización del acto religioso y siempre que se pueda en la celebración lúdica, no teniendo preferencia a la hora de tomar estas decisiones ni el progenitor que tiene la guarda y custodia exclusiva, ni el progenitor que ese día lo tenga en su compañía.

Los dos padres deberán ser informados por terceros de todos aquellos aspectos que afecten a sus hijos y, concretamente, tienen derecho a que se les facilite a los dos toda la información académica y los boletines de evaluación; e igualmente tienen derecho a obtener información a través de las reuniones habituales con los tutores o servicios de orientación escolar, tanto si acuden los dos juntos, como si lo hacen por separado.

De igual forma, tienen derecho a obtener información médica de sus hijos y que se le facilite a cada progenitor que lo solicite, los informes pertinentes sobre la salud de los mismos.

El progenitor que en ese momento se encuentre en compañía del hijo, podrá adoptar decisiones respecto al mismo sin previa consulta, en los casos en que exista una situación de urgencia o en aquellas decisiones diarias, poco trascendentes o rutinarias, que en el normal transcurrir de la vida con un menor puedan producirse.

Esta y las posteriores medidas que se recogen en este acuerdo, se fijan en interés del menor y valorando la situación actual, en especial el lugar donde reside en estos momentos. Por lo tanto, cualquier cambio de domicilio o residencia del menor, se debe acordar por ambos cónyuges y, en caso de conflicto, por el juez o por el progenitor que aquel decida.

Segunda. Respecto de la vivienda familiar

El uso de la vivienda familiar se distribuirá atendiendo a los siguientes criterios:

Tercera. Respecto de la pensión compensatoria

[OPCIONAL — incluir si procede]

(Si se pacta pensión compensatoria)

Pese a que ambos firmantes manifiestan gozar de una situación solvente, reconocen que una eventual ruptura matrimonial ocasionaría en Don/Doña [NOMBRE Y APELLIDOS] un desequilibrio económico en relación con Don/Doña [NOMBRE Y APELLIDOS], que implicaría un empeoramiento en su situación anterior al matrimonio, debido especialmente a la sensible diferencia entre el salario del segundo respecto al del primero, así como de sus patrimonios personales.

Dicho esto, las partes firmantes pactan que, en caso de una eventual separación o divorcio, Don/Doña [NOMBRE Y APELLIDOS] abonará a Don/Doña [NOMBRE Y APELLIDOS] una pensión compensatoria en la cuantía y bajo las condiciones que seguidamente se disponen:

1º.- Si la separación o el divorcio se produjera antes de transcurridos [Nº] años desde la celebración del matrimonio, la cantidad a abonar sería de [COMPLETAR] mensuales durante un periodo de [Nº] años, a contar desde la fecha de la sentencia de separación o divorcio.
2º.- Si la separación o el divorcio se produjera después de transcurridos [Nº] años desde la celebración del matrimonio, y con anterioridad al [COMPLETAR] aniversario, la cantidad a abonar sería de [COMPLETAR] mensuales durante un periodo de [Nº] años, a contar desde la fecha de la sentencia de separación o divorcio.
3º.- Si la separación o el divorcio se produjera después de transcurridos [Nº] años desde la celebración del matrimonio, la cantidad a abonar sería de [COMPLETAR] mensuales durante un periodo de [Nº] años, a contar desde la fecha de la sentencia de separación o divorcio.

Las cuantías señaladas se actualizarán anualmente, a partir del mes de enero siguiente a la firma del presente documento, conforme a las oscilaciones que experimente el Índice General de Precios al Consumo, publicado por el Instituto Nacional de Estadística u Organismo que pudiera sustituirle.

Don/Doña [NOMBRE Y APELLIDOS] renuncia a reclamar a Don/Doña [NOMBRE Y APELLIDOS] ninguna otra compensación o indemnización económica diferente de la pensión compensatoria establecida anteriormente.

[OPCIONAL — incluir si procede]

(Si se excluye la pensión compensatoria)

Ambos cónyuges renuncian a la reclamación de una pensión compensatoria a cargo del otro

Cuarta. Respecto de la contribución al sostenimiento de las cargas del matrimonio

Mientras se sustancia del procedimiento de separación o de divorcio, los comparecientes contribuirán al sostenimiento de las cargas del matrimonio del modo siguiente:

Asimismo, mientras dure la situación de separación de hecho, el cónyuge no propietario de la vivienda familiar abandonará la misma. El cónyuge propietario contribuirá al alquiler de una nueva vivienda aportando [IMPORTE] euros

Quinta. Respecto de los gastos extraordinarios de los hijos

[ELEGIR UNA OPCIÓN Y REDACTARLA: Respecto de los hijos del matrimonio / Cláusula básica de gastos extraordinarios / Cláusula detallada de gastos extraordinarios — el texto de cada opción no venía en el formulario original]

Sexta. Obligatoriedad de pactos

Los pactos contenidos en el presente acuerdo, constituirán el convenio regulador de su posible separación o divorcio, siendo irrevocables sin el expreso consentimiento de ambos cónyuges.

Séptima. Elevación a escritura pública

Cualquiera de las partes podrá solicitar la elevación a escritura pública del presente acuerdo.

Octava. Generalidades

El presente contrato anula y reemplaza cualquier contrato o acuerdo anterior entre las partes con el mismo objeto y sólo podrá ser modificado por un nuevo acuerdo firmado por ambas partes.

Si alguna de las cláusulas del presente contrato fuere declarada nula o inaplicable, dicha cláusula se considerará excluida del contrato, sin que implique la nulidad del mismo. En este caso las partes harán cuanto esté a su alcance para encontrar una solución equivalente que sea válida y que refleje debidamente sus intenciones.

Los encabezamientos de las distintas cláusulas lo son sólo a efectos informativos, y no afectarán, calificarán o ampliarán la interpretación de este contrato.

Y leído el presente documento, ambas partes lo firman en señal de conformidad y ratificación de su contenido, haciéndolo por duplicado y a un solo efecto.

En la ciudad de [COMPLETAR], a [DÍA] de [MES] de [AÑO].

Firma del contrayente	Firma de la contrayente
