---
name: oposicion-solicitud-cesacion-actividades-prohibidas-603
description: "Redacta el escrito «Oposición a la solicitud de cesación de actividades prohibidas, dañosas o ilícitas» (formulario 603 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición a la solicitud de cesación de actividades prohibidas, dañosas o ilícitas

> Formulario 0603 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] Nº (2 veces)
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO (2 veces)
- [ ] DNI/NIE
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…el Ilustre Colegio de Procurador/a.es de»; «…, con nº [Nº] de Colegiado»; «…eneciente a la Comunidad de Propietarios»; «…, con nº [Nº] de colegiado/a»; «…umanitaria, en el marco de la Asociación»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 9.2 y 85.1 LOPJ
- art. 45 LEC
- art. 25 LEC
- arts. 23 y 31 LEC
- art. 7.2 LPH
- art. 33 CE
- art. 7 LPH
- art. 7.2 CCiv
- art. 394.1 LEC
- Ley 34/2007

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

### Formulario 0603 · Oposición a la solicitud de cesación de actividades prohibidas, dañosas o ilícitas

- Año del modelo: 2016
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 22 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Contestación a demanda de juicio ordinario en materia de propiedad horizontal oponiéndose a solicitud de cesación de actividades prohibidas, dañosas o ilícitas, con solicitud de privación del uso de la vivienda en la propiedad horizontal.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales del Ilustre Colegio de Procurador/a.es de [COMPLETAR], con nº [Nº] de Colegiado [COMPLETAR], actuando en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, casado, propietario del piso sito en [LOCALIDAD], calle [CALLE], nº [NÚMERO], perteneciente a la Comunidad de Propietarios [COMPLETAR], con DNI [DNI/NIE], y bajo la dirección Letrada de D./Dña. [NOMBRE Y APELLIDOS], con nº [Nº] de colegiado/a [COMPLETAR], como se acredita debidamente, comparece ante el Tribunal y como mejor proceda en derecho, DIGO:

Que mediante el presente escrito, formulo ESCRITO DE OPOSICION A LA DEMANDA instada en contra de mi representado/a en solicitud de cesación de actividades prohibidas, dañosas o ilícitas, con solicitud de privación del uso de la vivienda, en base a los siguientes

ANTECEDENTES DE HECHO

PRIMERO.- Se acepta el correlativo en la demanda respecto a la personalidad de actor, su condición de presidente de la Comunidad de Propietarios, tal y como se desprende de los documentos presentados.

SEGUNDO.- Se acepta el correlativo respecto la condición de arrendatario de mi mandante, la propiedad de la vivienda que ocupa desde la firma del contrato de alquiler que se acompaña (documento nº [Nº DE DOCUMENTO]), en fecha [FECHA]. Asimismo, nada que objetar al coeficiente indicado de participación del inmueble en los elementos comunes.

TERCERO.- Se niega, de manera expresa, la realización en la vivienda de las conductas que se relacionan en el correlativo. Mi cliente ni es consumidor, ni trafica con drogas ilegales en la vivienda que ocupa, ni mantiene ninguna suerte de conductas violentas frente a sus vecinos de la comunidad. En el inmueble desarrolla una actividad humanitaria, en el marco de la Asociación [COMPLETAR], a la que pertenece, y cuyos estatutos se adjuntan a la presente (documento nº [Nº DE DOCUMENTO]). La misma consiste en llevar a cabo una actividad de apoyo global a toxicómanos ya rehabilitados en orden a su reinserción completa a la vida social. Y así, se organizan reuniones con aquellos de puesta en común de las preocupaciones y vivencias de los mismos, tras dejar atrás el mundo de las drogas.

El problema reside en que a algunos de los vecinos del inmueble, y especialmente, al presidente de la Comunidad actora, no les gusta, o no es de su agrado, la presencia de mi cliente en la comunidad, ni las personas que acuden a su vivienda a desarrollar reuniones legales, amparadas por el derecho a la intimidad reconocido constitucionalmente. Lo que les ha llevado a desarrollar una actitud de confrontación continua en los espacios comunes, con agresiones verbales, en cuyo marco mi mandante se ha limitado a defender los derechos que le asisten como ocupante de una vivienda, en el marco de un contrato de alquiler, en el cual cumple puntualmente con todas sus obligaciones como arrendatario.

De hecho, no existe ninguna sentencia condenatoria por delito alguno, ni los relativos a contra la salud pública, ni contra el patrimonio o la integridad de las personas. Es cierto que han existido denuncias planteadas por los citados vecinos, o por el presidente de la comunidad, aquí demandante; pero todas han finalizado con resoluciones absolutorias, tanto en sede de instrucción, como en sede de enjuiciamiento. De hecho la documentación aportada junto con la demanda es incompleta, dado que, a pesar de que en el referido escrito expositivo se reconoce que no se tiene constancia de condena alguna; no se acompañan las resoluciones que han absuelto a mi mandante de todas y cada una de las denuncias planteadas. Se adjuntan las mismas por el orden correlativo de los documentos aportados con la demanda (bloque documental nº [NÚMERO])

CUARTO.- Se acepta el correlativo, en cuanto al requerimiento efectuado, si bien no es cierto que se hiciera caso omiso del mismo, sino que, por el mismo conducto, vía notarial, se comunicó al presidente de la comunidad, que no se iba a cesar en una actividad lícita en los términos antes expuestos, dado que mi representado era libre para llevar a cabo la misma en el marco de su vivienda. Se aporta dicha contestación al presente escrito (documento nº [Nº DE DOCUMENTO]).

QUINTO.- Se acepta el correlativo en cuanto a la junta convocada y celebrada para la interposición de la demanda que aquí se contesta, manifestando que mi representado acudió a la misma, y votó en contra del acuerdo finalmente alcanzado, con el voto favorable del resto de los propietarios.

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA

Corresponde la Jurisdicción y competencia objetiva al Tribunal al cual nos dirigimos en virtud de los arts. 9.2 y 85.1 LOPJ y art. 45 LEC. Asimismo, detenta competencia territorial al encontrarse en su partido judicial la finca en la que se constituye la comunidad de propiedad horizontal, a partir de lo dispuesto en el art. 52.1.8.º LEC.

II.- PROCEDIMIENTO

Corresponde el Juicio ordinario, conforme a lo dispuesto en el art. 249.1.8.º LEC, art. 7.2 párrafo 3.º LPH, y Disposición Final Primera LEC, sin que suponga reclamación de cantidad alguna.

III.- LEGITIMACIÓN ACTIVA Y PASIVA

A los puros efectos formales, de acuerdo con la legitimación de la parte actora, a la hora de ejercitar una acción como la que aquí se plantea, concurriendo la previa autorización de la junta de propietarios, en la que mi mandante se opuso en solitario. Asimismo, se acepta, a los mismos efectos formales, la legitimación pasiva de mi cliente, como inquilino y ocupante del inmueble cuya privación se insta. Y ello, sin perjuicio de oponernos de manera frontal a la demanda, y negar tajantemente los hechos aducidos en la demanda.

IV.- CAPACIDAD Y REPRESENTACIÓN

Nada que objetar en cuanto a la capacidad y representación de la parte actora. Por lo que respecta a mi cliente es mayor de edad y se encuentra en situación de pleno ejercicio de sus derechos civiles, en virtud de lo dispuesto en los arts. 6.1.1.º y 7.1 LEC.

V.- POSTULACIÓN Y DEFENSA

La presente contestación se presenta mediante Procurador/a. de los Tribunales que encabeza este escrito, habilitado en la demarcación del Tribunal al que tengo el honor de dirigirme. Y ello con poder general para pleitos (art. 25 LEC), representación procesal acreditable mediante consulta automatizada -o, si el sistema no lo permite, mediante certificación- del Registro Electrónico de Apoderamientos Judiciales; siendo redactado y firmado el presente escrito por abogado ejerciente colegiado que dirige el asunto y se identifica en el encabezamiento, según resulta preceptivo conforme a los arts. 23 y 31 LEC.

VI.- FONDO DEL ASUNTO

La parte actora ejercita una acción de cesación de una actividad que no es la que se indica en la demanda, a la que une una petición de privación del uso de la vivienda de mi mandante y de sus añadidos durante el plazo de dos años, la de declarar extinguido el contrato de arrendamiento de vivienda que disfruta (abonando las rentas puntualmente), así como el correlativo desalojo en plazo legal. Es decir, sobre la base de un hecho que no se corresponde a la realidad, y que ha sido descartado por diversas resoluciones firmes de la jurisdicción penal; se viene a peticionar la máxima sanción para el ocupante de la vivienda, como es la de privarle de su uso, por el tiempo nada desdeñable de dos años. Todo ello al amparo de lo dispuesto en el art. 7.2 LPH.

Al respecto, tal posibilidad legal fue declarada constitucional por STC de 21 de octubre de 1993, rec. 1210/1987, con el argumento de que dicha sanción era compatible con el derecho de propiedad del art. 33 CE, en la medida en la cual el legislador ha querido castigar civilmente el incumplimiento de una obligación legal y estatutaria, en supuestos de actividades no permitidas, dañosas, inmorales, peligrosas, incómodas o insalubres. El voto particular del Magistrado Sr. Jiménez de Parga y Cabrera en STC de amparo, de fecha 8 de marzo de 1999 señaló que se trata de una norma sancionadora de naturaleza jurídico – privada o civil, como reacción jurídica del ordenamiento frente a incumplimientos del propietario (o usuario) del piso o local sito en un inmueble constituido en régimen de propiedad horizontal. El mismo añadía que se trata de una sanción de especial intensidad, que priva del uso o disfrute del más esencial del contenido del derecho de propiedad (en este caso, cedido por contrato al inquilino); y que por ello, no puede aplicarse de manera analógica a supuestos distintos de los contemplados en la ley.

De esta forma, el citado art. 7 LPH dispone expresamente que "Al propietario y al ocupante del piso o local no les está permitido desarrollar en él o en el resto del inmueble actividades prohibidas en los estatutos, que resulten dañosas para la finca o que contravengan las disposiciones generales sobre actividades molestas, insalubres, nocivas, peligrosas o ilícitas". En consecuencia, para poder estimar la acción ejercitada de contrario, la actividad que desarrolla mi mandante tiene que encajar en alguna de las prohibiciones mencionadas en el precepto legal, sin que se pueda sostener una interpretación amplia o analógica a otras conductas.

Por lo tanto, por un lado, si se ha investigado penalmente la supuesta venta de drogas tóxicas y estupefacientes, y mi mandante ha sido absuelto de tal delito por resolución firme; debe concluirse que el hecho de reunirse con toxicómanos rehabilitados no constituye una actividad ilícita. Sin que se pueda, en la presente sede, afirmar que se ha producido una conducta ilícita que no se ha adverado en la jurisdicción penal.

Por otro, los estatutos de la comunidad de propietarios demandante no prohíben expresamente reuniones del tipo indicado, en el marco de la actividad de una asociación que tiene por objeto la rehabilitación de aquellos. Conclusión a la que se llega tras una mera lectura de los mismos, en los que no se hace ninguna suerte de referencia expresa a dicho tipo de reuniones.

A partir de lo cual, la actividad debería tener encaje en las actividades molestas, insalubres, nocivas o peligrosas; extremos que se definen expresamente en el art. 3 del Reglamento de Actividades Molestas, Insalubres, Nocivas y Peligrosas, aprobado por Decreto 2414/1961, de 30 de noviembre de 1961 (1). Evidentemente se descarta, de principio, que se trate de conductas insalubres (que den lugar a desprendimiento o evacuación de productos que puedan resultar directa o indirectamente perjudiciales para la salud humana), nocivas (que puedan ocasionar daños a la riqueza agrícola, forestal, pecuaria o piscícola), o peligrosas (que tengan por objeto fabricar, manipular, expender o almacenar productos susceptibles de originar riesgos graves por explosiones, combustiones, radiaciones, u otros de análoga importancia para las personas o los bienes).

En consecuencia sólo quedaría analizar si la actividad desarrollada puede ser considerada como molesta, extremo definido legalmente como aquella actividad que constituya una incomodidad por los ruidos o vibraciones que produzcan, o por los humos, gases, olores, nieblas, polvos en suspensión, o sustancias que eliminen. Y ciertamente, no se alcanza a comprender cómo una serie de reuniones con personas que se están reinsertando en la vida social, tras sufrir el calvario del mundo de la droga, puede alcanzar esa condición de molesta, más allá de que al resto de vecinos no le guste; de manera que conlleve una sanción de tal gravedad como la que aquí se pretende.

El concepto de actividad molesta ha sido muy trabajado jurisprudencialmente, y así la Sentencia de la Audiencia Provincial de Madrid, Sección 8ª, 2/2004 de 12 Ene. 2004, Rec. 846/2002 recuerda que debe atenderse siempre al caso concreto, reiterando la Sentencia de la Audiencia Provincial de Madrid, Sección 10ª, 102/2011 de 23 Feb. 2011, Rec. 814/2010 que la calificación de una actividad como molesta no ha de hacerse apriorísticamente y sólo por las características generales de la misma, sino atendiendo al modo de realizarse en cada caso concreto, como ya destacó la Sentencia del Tribunal Supremo, Sala Primera, de lo Civil, de 16 Jul. 1993, o el modo de desarrollarse, atendiendo a los principios que rigen las relaciones de vecindad y la prohibición del abuso de derecho del art. 7.2 CCiv y a la posición contumaz del agente ante las advertencias que le han sido hechas; incluso las objetivamente inocuas (STS de 14 de mayo de 1968 y de 29 de setiembre de 1979), debiendo valorarse inicialmente como tales las que así vengan calificadas por imperativo legal, por su propia naturaleza, por sus especiales características o desenvolvimiento, por su efectiva repercusión externa o trascendencia, debiéndose estar en cada caso a la estimación o apreciación fáctico-jurídica que en cada caso concreto merezcan el órgano judicial (STS de 20 de septiembre de 1967 o de 19 y 22 de diciembre de 1972).

Asimismo, la Sentencia de la Audiencia Provincial de A Coruña, Sección 5ª, 32/2010 de 11 Feb. 2010, Rec. 257/2009, la define como aquella actividad que disminuye el uso normal y disfrute de sus respectivos elementos a los demás condueños, los actos de emulación y las inmisiones. Se continúa, de esta forma, con la jurisprudencia clásica del Tribunal Supremo (STS de 28 de febrero de 1964, 8 de abril de 1965 y 11 de mayo de 1998, rec. 882/1994), que exige que la actividad molesta ha de exceder y perturbar el régimen o estado de hecho usual y corriente en las relaciones sociales de manera notoria (evidencia y permanencia en la molesta).

En esta misma línea, la Sentencia de la Audiencia Provincial de Valencia, Sección 6ª, 439/2007 de 11 Jul. 2007, Rec. 352/2005, tras indicar que la Ley de Propiedad Horizontal busca asegurar que el ejercicio del derecho propio no se traduzca en perjuicio del ajeno ni en menoscabo del conjunto, para así dejar establecidas las bases de una convivencia normal y pacífica; considera que las limitaciones a las facultades dominicales han de interpretarse de modo restrictivo, no extensivamente, siendo lo excepcional la prohibición o límite al ejercicio de los derechos, salvo que afecte a los elementos comunes. Cita en apoyo de tal criterio restrictivo, con exigencia del principio de proporcionalidad, la Sentencia de la Audiencia Provincial de Santa Cruz de Tenerife, Sección 3ª, 1064/2000 de 9 Dic. 2000, Rec. 647/2000, que a su vez contiene referencia a jurisprudencia clásica del Tribunal Supremo, contenida en SSTS de 29 de abril de 1979, 7 de febrero de 1989, 21 de diciembre de 1993, 10 de julio de 1995, rec. 1501/1992, 31 de mayo de 1996, rec. 3175/1996 y 20 de febrero de 1997, rec. 628/1993.

Finalmente, la Sentencia de la Audiencia Provincial de Pontevedra, Sección 1ª, 166/2015 de 30 Abr. 2015, Rec. 206/2015resume los requisitos exigidos indicando que la actividad debe exceder y perturbar el régimen o estado de hecho usual y corriente en las relaciones sociales, de manera notoria (evidencia y permanencia en la incomodidad), y debe estar suficientemente probada.

Pues bien, en el presente supuesto, la conducta imputada no se ha acreditado en sede penal, no puede serlo en sede civil; y la actividad real desarrollada no perturba la convivencia normal y pacífica, ni el estado usual de las relaciones sociales. El hecho de que una serie de personas se cruce en los elementos comunes del edificio, cuando salen o entran de la vivienda de mi mandante, no puede, de ninguna manera encuadrarse en una actividad molesta que habilite la acción ejercitada; sin perjuicio de que guste, más o menos, a los demás integrantes de la comunidad de vecinos. Y asimismo, las reuniones se llevan a cabo en el interior del inmueble, sin que se derive molestia alguna hacia el exterior, en una suerte de ruidos, vibraciones, o desprendimiento de sustancias. Procede, en consecuencia, la desestimación de la demanda.

VII.- COSTAS

Serán impuestas a la parte demandante conforme dispone al art. 394.1 LEC, al ser rechazadas totalmente sus pretensiones.

Por todo cuanto antecede,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito junto con sus documentos acompañantes y sus copias, el/la Letrado/a de la Administración de Justicia los admita y a mí por personado en tiempo y forma en nombre del demandado y por contestada la demanda, y en su día el tribunal dicte sentencia por la que Se desestime la demanda presentada de adverso y se absuelva a mi representado de todos los pedimentos de contrario, con imposición al demandante de todas las costas ocasionadas.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) El Decreto 2414/1961, de 30 de noviembre, por el que se aprueba el Reglamento de actividades molestas, insalubres, nocivas y peligrosas ha sido derogado por el número 1 de la disposición derogatoria única de la Ley 34/2007, de 15 de noviembre, de calidad del aire y protección de la atmósfera. Téngase en cuenta, no obstante, que la citada disposición mantendrá su vigencia en aquellas comunidades y ciudades autónomas que no tengan normativa aprobada en la materia, en tanto no se dicte dicha normativa.

========================================================================
