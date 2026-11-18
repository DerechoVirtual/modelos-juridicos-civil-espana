---
name: demanda-nulidad-matrimonial-incapacidad-canon-1095-3-1456
description: "Redacta el escrito «Demanda de nulidad matrimonial por incapacidad (canon 1095.3)» (formulario 1456 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de nulidad matrimonial por incapacidad (canon 1095.3)

> Formulario 1456 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (3 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] CALLE
- [ ] Nº (3 veces)
- [ ] NÚMERO (3 veces)
- [ ] FECHA (2 veces)
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 38 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… calidad de abogado y procurador de Doña»; «…, mayor de edad, católica, vecina de»; «…emanda de NULIDAD MATRIMONIAL contra Don»; «…tizado en la Iglesia Católica, vecino de»; «…y fundamenta en los siguientes: HECHOS y»; «…, contando ambos»; «…nio canónico en la Iglesia Parroquial de»; «…de la Diócesis de»; «…de la Diócesis de [COMPLETAR], el»; «…, el [COMPLETAR] de»; «…su unión matrimonial nacieron dos hijos:»; «…, en»; …

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

### Formulario 1456 · Demanda de nulidad matrimonial por incapacidad (canon 1095.3)

- Año del modelo: 2014
- Revisión 17-11-2026: 52 campos de relleno marcados en blanco; 1 menciones a juzgados actualizadas (LO 1/2025); 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Al Rvdo. Tribunal Eclesiástico
Procurador, representación y asistencia Letrada
Interposición de demanda de nulidad
HECHOS
FUNDAMENTOS DE DERECHO
Suplico
Otrosí
Lugar y fecha
Firmas

AL RVDO. TRIBUNAL ECLESIÁSTICO DEL ARZOBISPADO DE [LOCALIDAD]

D. [NOMBRE Y APELLIDOS], Letrado del Ilustre Colegio de Valencia, en calidad de abogado y procurador de Doña [COMPLETAR], mayor de edad, católica, vecina de [COMPLETAR], con domicilio en [LOCALIDAD], según resulta del Acta de mandato procuratorio y comisión a letrado que se acompaña, ante el Tribunal comparezco y DIGO:

Que en la representación y defensa que ostento y siguiendo instrucciones de mi mandante, interpongo demanda de NULIDAD MATRIMONIAL contra Don [COMPLETAR], mayor de edad, bautizado en la Iglesia Católica, vecino de [COMPLETAR], con domicilio en calle [CALLE], la que se basa y fundamenta en los siguientes:

HECHOS

 y [COMPLETAR], contando ambos [COMPLETAR] y [Nº] años de edad respectivamente, contrajeron formalmente matrimonio canónico en la Iglesia Parroquial de [COMPLETAR] de la Diócesis de [COMPLETAR], el [COMPLETAR] de [COMPLETAR] de

Se adjunta a la presente demanda Partida de matrimonio con número [NÚMERO] de documentos.

De su unión matrimonial nacieron dos hijos: [COMPLETAR], en [COMPLETAR], el día [FECHA] de [COMPLETAR] de [COMPLETAR] y [COMPLETAR] el día [FECHA] de [COMPLETAR] de

Se adjunta a la presente demanda Partida de Bautismo como número [NÚMERO] y [COMPLETAR] de documentos.

Los cónyuges cesaron la convivencia marital a finales del año [COMPLETAR], encontrándose en la actualidad en situación legal civil de divorciados según Sentencia dictada por el Tribunal de Instancia (Sección Civil, plaza n.º [NÚMERO]) de [LOCALIDAD], de [COMPLETAR] de [COMPLETAR] de

Se adjunta bajo documento número [Nº DE DOCUMENTO] copia testimoniada de la referida resolución judicial junto al Convenio Regulador suscrito de mutuo acuerdo.

 es la tercera de cuatro hijos habidos en el matrimonio de [COMPLETAR] y [COMPLETAR]

Estudió en el colegio Escolapias, donde recibió educación religiosa, para posteriormente estudiar Pedagogía.

Durante su adolescencia y juventud fue una joven modosa que no gustaba mucho de salir. Así, su primer y único novio fue Juan.

En este instante es profesora de Religión en la enseñanza secundaria.

 conoció a [COMPLETAR] en [COMPLETAR] de [COMPLETAR], cuando ella estaba a punto de terminar sus estudios de Pedagogía, e inmediatamente formalizaron su relación. En aquel instante ella contaba [Nº] años y él [COMPLETAR] Recuerda ella que él inicialmente le mintió diciéndole que tenía [Nº] años.

El joven [COMPLETAR], oriundo de [COMPLETAR], trabajaba entonces como militar en el cuartel de Gandía. Era un chico bastante engreído, mujeriego y extraordinariamente irascible.

Su noviazgo duró casi cuatro años y durante ese tiempo ella estudio Ciencias Religiosas y él preparó oposiciones a la Guardia Civil.

La decisión matrimonial era para [COMPLETAR] un paso natural. Ella estaba enamorada de [COMPLETAR], el único hombre de su vida, y el proceso, por tanto, debía continuar con el paso matrimonial. Y ello, pese a que durante el tiempo de noviazgo había observado en [COMPLETAR] un carácter extremadamente iracundo y ciertamente violento, sobre el que, no obstante, no llegó a vislumbrarlo como impedimento. En un momento dado, en fechas próximas a la celebración matrimonial, [COMPLETAR] llego a descubrir, por información que le ofrecieron los propios amigos de [COMPLETAR], que este había sido condenado como autor de un delito de violencia contra una anterior novia, si bien, le parecieron suficientes y comprensibles los argumentos que este le ofreció sobre la cuestión.

Una vez decidido el matrimonio fue ella quien se ocupó de todo, no participando Juan en nada y manteniendo, por tanto, su normal ritmo de vida: trabajo, aficiones, amigos, ocio. Este aspecto se constituyó en una constante dentro de su matrimonio.

La vida matrimonial se inicia con gran ilusión por parte de [COMPLETAR] Ella experimenta un gran enamoramiento de [COMPLETAR] y se dedica a él en cuerpo y alma: es una mujer completamente sumisa, desarrolla todas las labores de casa, asume los tiempos de ocio de su esposo y el mantenimiento por su parte de todas las actividades que ya realizaba de soltero, se preocupa por estar guapa para él Él es el centro de la relación y ella así se lo demuestra y consiente. Así, pronto, la esposa –según recuerda- comienza a darse cuenta de que no existe una mínima reciprocidad en tal relación: para Juan lo más importante era él, y en su complacencia no reparaba ni en tiempo ni en gastos. Cada una de sus demandas, en todo orden, debía ser atendida. Se reveló un joven completamente intolerante a la frustración, poco constante y, por otro lado, insensible a las necesidades ajenas, siquiera a las de su esposa. Es más, tal intolerancia e incomprensión, desencadenaba con frecuencia en graves episodios de violencia que, ahora ya, alertaron gravemente a la esposa.

Al momento de nacer la primera de los dos hijos habidos en el matrimonio, [COMPLETAR] ya es plenamente consciente de cuáles eran las reales prioridades de su esposo y qué lugar ocupaba ella. Pese a que busca complacerle en todo, no parece lograr conseguirlo, y sobre tal constatación –pese a los extraordinarios sacrificios que ha realizado– su autoestima disminuye de modo alarmante y aparece la tristeza. Ella empieza a temer a su marido y la vida familiar se divide completamente: ella y los niños por un lado y por el otro Juan, autocentrado en sus cosas.

En los últimos tiempos de su matrimonio, con ocasión de un cambio de actividad laboral por parte de [COMPLETAR] y el nuevo entorno social en el que se mueve, se pronuncia la división entre los esposos. Las nuevas amistades y sus circunstancias influyen en la percepción del esposo sobre su realidad. Finalmente, la relación con otra mujer pone punto y final a la convivencia. El tiempo inmediato posterior a la ruptura fue tremendamente duro. Consecuencia de un nuevo episodio violento fue acordada una medida judicial de alejamiento del esposo sobre la esposa. quedó muy afectada de los acontecimientos que se sucedían y necesitó demandar ayuda psicológica.

Como quiera que la esposa, tras el tiempo transcurrido desde la ruptura convivencial en su matrimonio, está completamente segura de que este es insanable y que le asisten razones fundadas para considerar su nulidad, es por lo que ha decidido iniciar el oportuno procedimiento a fin de que la Iglesia discierna sobre esa realidad y ponga, con ello, claridad en su vida de Fe.

A los anteriores hechos, le son de aplicación, entre otros, los siguientes:

FUNDAMENTOS DE DERECHO

JURISDICCIÓN

Canon 1671 CIC y art. 3 Instrucción Dignitas Connubii.

COMPETENCIA

Resulta competente el Tribunal al que me dirijo en virtud del c. 1673.1 del CIC y art. 10.1.1º de la Instrucción DC, dado el lugar de celebración del matrimonio y el domicilio de los esposos.

LEGITIMACIÓN ACTIVA Y PASIVA

Gozan, por una parte de legitimación activa mi representada y esposa actora, por ser uno de los cónyuges del matrimonio y, por otra, de legitimación pasiva el esposo demandado, de conformidad con los c. 1476 y 1674.1. CIC y art. 92.1º Inst. DC [COMPLETAR].

FONDO DEL ASUNTO

4.1) El canon 1.057-1, según el cual «el matrimonio lo produce el consentimiento de las partes legítimamente manifestado entre personas jurídicamente hábiles, consentimiento que ningún poder humano puede suplir».

4.2) El canon 124 dispone que «para que un acto jurídico sea válido, se requiere que haya sido realizado por una persona capaz, y que en el mismo concurran los elementos que constituyen esencialmente ese acto, así como los requisitos y formalidades impuestos por el derecho para la validez de ese acto»

4.3) El canon 1.057.2 que determina que «El consentimiento matrimonial es el acto de la voluntad por el cual varón y mujer se entregan y aceptan mutuamente en alianza irrevocable para constituir el matrimonio».

4.4) El número 3 del canon 1.095, que dispone que son incapaces para contraer validamente quienes al tiempo de contraer no pueden asumir y cumplir las obligaciones esenciales del matrimonio por causas de naturaleza psíquica.

Dicho supuesto de incapacidad consensual se centra en el objeto del consentimiento y ocurre no por faltar el uso de razón o porque haya ausencia de discreción de juicio, sino porque existe una verdadera imposibilidad de asumir y cumplir las obligaciones esenciales del mismo por causas de naturaleza psíquica. En tal persona se dan condiciones anómalas y, aunque posea condiciones intelectivas y de juicio suficientes, sin embargo, no puede comprometerse responsablemente con dichas obligaciones. La voluntad matrimonial tiene que ser libre en el acto de deliberación y de decisión y, además, tiene que ser eficiente en el acto de ejecución, es decir, tiene que estar dotada de fuerza para poder cumplir en la práctica esas cargas esenciales del matrimonio.

Este canon resulta la formalización canónico-positiva del principio de derecho natural recogido en el axioma jurídico «impossibilium nulla obligatio est».

POSTULACIÓN

El canon 1.483 en lo que se refiere a los requisitos de abogados y procuradores.

En su virtud,

SUPLICO AL TRIBUNAL, que habiendo por presentada esta demanda, la admita, teniéndome por comparecido en la representación que ostento, se sirva dar traslado de la misma al esposo demandado y al Defensor del Vínculo; y en su día, tras recibimiento a prueba en fase de instrucción de la causa y demás trámites legales, dicte sentencia por la que declare la nulidad del matrimonio contraído por la actora con la demandada por el capítulo de Incapacidad para asumir las obligaciones esenciales del matrimonio por causas de naturaleza psíquica, concurrente en el esposo, en virtud del canon 1.095.3.

PRIMER OTROSÍ DIGO: Que reuniendo quien suscribe los requisitos necesarios para defender y representar a la actora, interesa del Tribunal confiera a su favor la oportuna comisión canónica a tal efecto, SUPLICO DEL TRIBUNAL, así se acuerde.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
