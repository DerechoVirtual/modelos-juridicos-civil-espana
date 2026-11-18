---
name: apelacion-obtener-custodia-compartida-hijos-menores-1442
description: "Redacta el escrito «Apelación para obtener la custodia compartida de hijos menores» (formulario 1442 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Apelación para obtener la custodia compartida de hijos menores

> Formulario 1442 del plugin **Familia** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Formulario de 2004-2005 que razona sobre el informe «favorable» y vinculante del Fiscal para la custodia compartida (art. 92.8 CC antiguo): el texto vigente solo exige «informe del Ministerio Fiscal»; rehacer la fundamentación.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] Nº
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] FECHA (3 veces)
- [ ] IMPORTE
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…CIÓN CIVIL DE LA AUDIENCIA PROVINCIAL DE»; «…aración matrimonial de los cónyuges, Don»; «…y Doña»; «…justicia que se interesa en la ciudad de»; «…a»

## Elecciones que hay que hacer

- SEPARACION MATRIMONIAL / DIVORCIO
- separación matrimonial / divorcio
- la separación matrimonial de los cónyuges / la disolución matrimonial por divorcio

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 90 CC
- artículo 92.8 del Código Civil
- Ley 15/2005

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

### Formulario 1442 · Apelación para obtener la custodia compartida de hijos menores

- Año del modelo: 2004
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 4 desplegables convertidos en elección en blanco; 16 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)
- Avisos de la revisión: Formulario de 2004-2005 que razona sobre el informe «favorable» y vinculante del Fiscal para la custodia compartida (art. 92.8 CC antiguo): el texto vigente solo exige «informe del Ministerio Fiscal»; rehacer la fundamentación.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Receptor
ALEGACIONES (1)
AL TRIBUNAL SUPLICO:
Firmas

Recurso de apelación contra la sentencia estimatoria de la separación matrimonial (o divorcio), que atribuye la guarda y custodia de los hijos menores a la parte contraria, solicitando la parte apelante que ésta sea compartida.

Formulario adaptado a la reforma orgánica y procesal de la LO 1/2025.

AUTOS [ELEGIR: SEPARACION MATRIMONIAL / DIVORCIO] Nº [Nº]

A LA SECCIÓN CIVIL DE LA AUDIENCIA PROVINCIAL DE [COMPLETAR]

[NOTA DE REVISIÓN (comprobar): La AP no tiene «Sección Civil» como denominación legal: se cita la Sección por su número (p. ej. «A LA SECCIÓN [ ] DE LA AUDIENCIA PROVINCIAL DE [ ]»). Fuente: LOPJ arts. 80 y 82 (Audiencia Provincial, sin cambio de denominación).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, actuando en nombre y representación procesal de D./Dña. [NOMBRE Y APELLIDOS], conforme tengo debidamente acreditado en los autos arriba referenciados, sobre [ELEGIR: separación matrimonial / divorcio], por medio del presente escrito vengo a interponer, en tiempo y forma, y de conformidad con lo establecido por los artículos 458 y siguientes de la Ley de Enjuiciamiento Civil el correspondiente RECURSO DE APELACION, contra la sentencia de fecha [FECHA], sobre la base de las siguientes

ALEGACIONES (1)

PRIMERA. Con fecha [FECHA], recayó en este procedimiento sentencia en cuya virtud se acordaba haber lugar a declarar la separación matrimonial de los cónyuges, Don [COMPLETAR] y Doña [COMPLETAR] (o a la disolución matrimonial por divorcio), estimando, en consecuencia, la demanda interpuesta por esta parte. Sin embargo, el Tribunal de instancia resuelve atribuir la guardia y custodia de la hija menor habida en el matrimonio a D./Dña. [NOMBRE Y APELLIDOS], estableciendo un régimen de visitas en favor de mi mandante, y también a su cargo el establecimiento de una pensión de alimentos por importe de [IMPORTE] euros mensuales, otorgando, por último, el uso del que había venido siendo domicilio conyugal a D./Dña. [NOMBRE Y APELLIDOS]

Esta parte, se aquieta con los pronunciamientos referidos a la propia declaración de [ELEGIR: separación matrimonial / divorcio] y al establecimiento en favor de D./Dña. [NOMBRE Y APELLIDOS] del uso y disfrute del que había venido siendo domicilio conyugal. Así pues, centramos nuestra impugnación en la atribución de la guarda y custodia de la hija menor a D./Dña. [NOMBRE Y APELLIDOS], por considerar, como ya hiciéramos en nuestra demanda (o contestación) que resulta lo procedente en este caso mantener, no solo la patria potestad, sino también la guarda y custodia de la hija menor compartida. Naturalmente, y como consecuencia de lo anterior, interesamos también, para el caso de que resulte estimada, como esperamos, nuestra pretensión principal, que se rectifique en los términos que se propondrán el régimen de visitas establecido en favor de mi mandante y que se deje sin efecto la pensión de alimentos fijada a su cargo.

SEGUNDA. Esta parte no desconoce que no es práctica habitual entre nuestros tribunales el establecimiento de la guarda y custodia de los hijos menores de forma compartida en favor de ambos progenitores. No es menos cierto, sin embargo, que esta concreta medida vino obteniendo progresivamente una acogida favorable en el ámbito de la doctrina científica y que también entre nuestros órganos jurisdiccionales comenzó lentamente a abrirse paso. Desde luego, cualquier medida adoptada en el ámbito de un procedimiento de crisis matrimonial que concierna o se refiera a los hijos menores ha de estar orientada, como en la propia sentencia de instancia se reconoce, a la mejor satisfacción del interés de éstos, preferente, en todos los sentidos, al de sus progenitores. No es, naturalmente, que haya de desconocerse o ignorarse el derecho de los padres a relacionarse con sus hijos o el natural deseo de aquéllos respecto a que esta relación se prolongue en el tiempo de la forma más intensa posible. Se trata simplemente de poner el acento en la circunstancia de que aquel derecho y aquellos legítimos deseos han de aparecer subordinados al interés del menor, especialmente digno de protección por muy diferentes razones y, sin duda, por expresa decisión del legislador. En este sentido, la Convención sobre los derechos del niño, adoptada por la Asamblea General de las Naciones Unidas el 20 de noviembre de 1989, y ratificada por España el 30 de noviembre de 1990, prevé que en todas las medidas que les conciernan los Tribunales, las autoridades administrativas o los órganos legislativos atenderán, como consideración primordial, al interés superior del niño. En la misma dirección se orienta, lógicamente, el artículo 39.4 de nuestra Constitución y los artículos 90 CC siguientes y concordantes del Código Civil.

Ahora bien, esta parte no alberga duda alguna respecto a que, siendo ello posible al no interferir decisivamente en la vida cotidiana del menor, lo preferible para él habrá de ser que la relación con ambos progenitores no quede indefinidamente interrumpida o limitada a un régimen de visitas que, en cualquiera de sus modelos, resulta angosto y limitador de aquellas relaciones. Desde luego que no siempre será posible establecer, sin detrimento del natural desarrollo del menor, ese sistema compartido de guarda y custodia que resulta, seguramente, inconveniente cuando comporte cambios en la localidad de residencia y, por ende, en el entorno cotidiano del menor (amistades, centro escolar, relaciones con la familia extensa, etc.). Sin embargo, en el supuesto que ahora se somete a la consideración de la Sala, ambos progenitores, con independencia de su separación, continuarán viviendo en esta misma localidad, en domicilios además particularmente próximos, lo que habrá de permitir que la hija menor conserve en todo su habitual entorno pese a las modificaciones periódicas de la guarda y custodia. Y esa situación, atendiendo a la actividad laboral que desarrollan los progenitores, se mantendrá presumiblemente en el futuro. Por otro lado, ha quedado en el procedimiento suficiente acreditado que ambos progenitores se encuentran perfectamente capacitados para atender a la menor y que ésta mantiene con los dos unas óptimas relaciones que mi mandante no podrá conservar bajo las extremas condiciones de un régimen de visitas bisemanal.

TERCERA. Consideramos en este sentido que resulta aquí de particular interés invocar la sentencia dictada por la Audiencia Provincial de Valencia de fecha dos de febrero del año dos mil cuando señala que el régimen usual de atribución de la custodia del hijo a un progenitor con exclusión del otro no satisface las exigencias de un saludable equilibrio de la figura materna y paterna en el niño. Su convivencia continuada con uno solo de ellos provoca que tome a éste como único modelo de comportamiento, desdibujándose las referencias del otro, con el que se relaciona esporádicamente. Como bien concluye la referida sentencia, no existía en la regulación entonces vigente ningún precepto que prohibiera aplicar soluciones distintas. Tan es así, que aunque en el supuesto que entonces enjuiciaba la Audiencia de Valencia ninguna de las partes había propuesto la guarda y custodia compartida así se decretó. En aquél caso ambos progenitores vivían en el mismo edificio (mi mandante y D./Dña. [NOMBRE Y APELLIDOS] residen como hemos dicho y consta en las actuaciones en domicilios próximos). Ambos cónyuges, entonces como ahora, deseaban cuidar a su hija y los dos tenían y tienen capacidad para cuidarla adecuadamente.

Como es sabido, la Ley 15/2005, de 8 de julio, por la que se modifican el Código Civil y la Ley de Enjuiciamiento Civil en materia de separación y divorcio, articula ya expresamente la posibilidad de que se establezca el ejercicio compartido de la guarda y custodia de los hijos. Y aunque es verdad que, con carácter general, sujeta la referida decisión a la previa petición conforme de ambos progenitores, no lo es menos que el artículo 92.8 del Código Civil, si quiera sea con carácter excepcional autoriza a que se acuerde también la guarda y custodia compartida, a instancia de una sola de las partes y previo informe favorable del Ministerio Fiscal.

Esta parte solicita, por eso, el mismo régimen de guarda y custodia compartida que en la referida sentencia de la Audiencia Provincial de Valencia se estableció, consistente en que la misma se ejerciera por meses alternos, con un amplio régimen de vistas, a modo de complemento que se extendería en fines de semana alternos, de 10 de la mañana del sábado a 20 horas del domingo, y todos los martes y jueves desde la salida del colegio por la tarde (o desde las cinco horas en los períodos vacacionales) hasta las 20 horas.

CUARTA. Por último, y como también se señalaba en la sentencia que se comenta, procede dejar sin efecto la pensión de alimentos establecida a cargo de mi mandante, sustituyendo este mecanismo de pensión alimenticia tradicional por el de establecer que el progenitor bajo cuya custodia se encuentre la niña en cada momento atienda a todas las necesidades ordinarias que tenga durante ese período, mientras que las extraordinarias (tratamientos médicos costosos, viajes escolares o de recreo, etc.) sean satisfechos por mitad por ambos progenitores, lo que, a juicio de esta parte, resulta particularmente adecuado atendiendo a que ambos perciben por su trabajo unos ingresos, si no iguales, bastante semejantes.

Por todo ello, en méritos de lo anterior,

AL TRIBUNAL SUPLICO:

Que se sirva admitir este escrito, teniendo por interpuesto en tiempo y forma el correspondiente recurso de apelación contra la sentencia de fecha [FECHA] y, previo cumplimiento de los trámites procesales oportunos, entre ellos el preceptivo informe del Ministerio Fiscal y en mérito de lo en él expuesto, se dicte en su día sentencia por la que, revocando la recurrida, se declare haber lugar a [ELEGIR: la separación matrimonial de los cónyuges / la disolución matrimonial por divorcio] con los efectos legales que le son inherentes y, en particular, que la patria potestad y la guarda y custodia de la menor será compartida por ambos cónyuges en los términos que se contienen en el cuerpo de este escrito o en los que el Tribunal resuelva, determinándose un régimen de visitas respecto del progenitor que, en cada período, no tenga a la niña, en los términos propuestos, dejando, por fin, sin efecto, la pensión de alimentos establecida en la sentencia que se recurre a cargo de mi mandante; todo ello, sin expresa imposición de las costas procesales correspondientes a la segunda instancia a ninguna de las partes.

OTROSÍ PRIMERO DIGO: Que esta parte no considera necesaria la celebración de vista para la resolución del presente recurso, sin perjuicio de que, naturalmente, estemos a lo que sobre el particular decida la Sala.

AL TRIBUNAL SUPLICO: Que se tengan por realizadas las manifestaciones que se dejan efectuadas.

OTROSÍ SEGUNDO DIGO que se acompaña a este escrito resguardo acreditativo del pago del depósito de 50 euros en la Cuenta de Depósitos y Consignaciones del Tribunal al que se dirige, conforme exige la DA 15.ª LOPJ, por lo que,

SUPLICO AL TRIBUNAL que tenga por causada la manifestación anterior a los efectos oportunos.

Es todo ello justicia que se interesa en la ciudad de [COMPLETAR] a [COMPLETAR]

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La sentencia dictada por la Audiencia Provincial de Barcelona, Sección 18ª, de fecha 20 de febrero de 2007, señala que cuando se alude a custodia compartida nos estamos refiriendo a un sistema de alternancia o reparto de tiempos y estancias de los hijos con cada uno de sus padres. Al respecto, el artículo 92.8 del Código Civil, en su redacción actual, dispone que de forma excepcional y aún cuando no se den los presupuestos del apartado 5 de este artículo, el Juez, a instancia de una de las partes y con informe favorable del Ministerio Fiscal (cuyo carácter vinculante se contempló en la tramitación parlamentaria como una garantía más establecida a favor de los menores), podrá acordar la guarda y custodia compartida, con fundamento en que de esta forma se protege adecuadamente el interés del menor. Su regulación viene motivada, porque en la sociedad actual, la dinámica de algunas familias empieza a ser distinta cada vez que, factores como el acceso de la mujer al mercado laboral, y los cambios en determinadas pautas de educación están provocando que, cada vez más, los padres tengan una mayor intervención en el cuidado diario de sus hijos y se produzca en muchos casos una coparticipación en el cuidado, asistencia y educación de los menores. La referida sentencia considera que el nuevo sistema presenta ventajas e inconvenientes. Empezando por estos últimos, es de destacar como tales, la posible inestabilidad de los menores producida por los continuos cambios de domicilio; los problemas de adaptación e integración a los nuevos núcleos familiares que se vayan creando; y las dificultades para unificar criterios en las cotidianas cuestiones de la vida de los menores. En cuanto a sus ventajas o beneficios, siempre según la sentencia que se comenta, realmente son mayores y superiores a aquellos ya que con la custodia compartida se garantiza a los hijos la posibilidad dotar de la presencia de ambos progenitores, pese a la ruptura de las relaciones de pareja, siendo similar la presencia de ambas figuras parentales y constituye el modelo de convivencia que más se acerca a la forma de vivir de los hijos durante la convivencia de pareja de sus padres por lo que la ruptura resulta menos traumática. Además, se editan determinados sentimientos negativos en los menores entre los cuales cabe relacionar los siguientes: miedo al abandono, sentimiento de lealtad, sentimiento de culpa, sentimiento de negación, de suplantación, etc. Por otra parte, se fomenta una actitud más abierta de los hijos hacia la separación de los padres que permite una mayor aceptación del nuevo contexto y se evitan situaciones de manipulación consciente o inconsciente por parte de los padres frente a los hijos. Finalmente, se garantiza a los padres la posibilidad de seguir ejerciendo sus derechos y obligaciones inherentes a la potestad o responsabilidad parental, evitando así el sentimiento de pérdida que experimenta el progenitor cuando se atribuye la custodia al otro, consiguiéndose además con ello una mayor concienciación de ambos en la necesidad de contribuir a los gastos de los hijos.

Por su parte, sentencia dictada por la Audiencia Provincial de Valencia, Sección 10ª, de fecha 22 de julio 2005, rec. 531/2005, ya acordaba la guarda y custodia compartida de los menores teniendo en consideración que ambos progenitores estaban capacitados para ostentar la guarda y custodia de sus hijos y que los dos tienen estilos educativos adecuados y similares, comprobando también que los litigantes viven a poca distancia, lo que facilitará que los hábitos y actividades cotidianas de los menores, entre los que destaca la asistencia al colegio, no experimenten cambios perturbadores.

Desde una perspectiva relativamente distinta, la sentencia dictada por la Audiencia Provincial de Córdoba, Sección 1ª, de fecha 10 de marzo de 2005, rec. 74/2005, -nótese: anterior a la nueva regulación legal-, pone el acento en la consideración de que viene siendo de aplicación, hasta entonces, por la mayor parte de las Audiencias Provinciales de España un criterio restrictivo en orden a establecer la guarda y custodia compartida cuando no existan razones de peso que así lo aconsejen.

========================================================================
