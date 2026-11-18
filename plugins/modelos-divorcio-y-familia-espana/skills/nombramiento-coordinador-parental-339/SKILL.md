---
name: nombramiento-coordinador-parental-339
description: "Redacta el escrito «Nombramiento de coordinador parental» (formulario 339 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Nombramiento de coordinador parental

> Formulario 0339 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] NÚMERO
- [ ] COLEGIO
- [ ] FECHA (6 veces)
- [ ] Nº DE DOCUMENTO
- [ ] Nº DE RESOLUCIÓN (2 veces)
- [ ] Nº (2 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…Procurador/a de los Tribunales y de Doña»; «… consideraciones jurídicas: 1.ª) Que Don»; «…jante a la de los casados entre los años»; «…, fruto de cuya unión nació el menor»; «…que se atribuía la misma a la madre Doña»; «…ntonces entre las partes con los números»; «… y ante la Fiscalía de Menores en el año»; «…(se acredita mediante documentos números»; «…bilidad emocional, en especial del menor»; «…funciones de parentalidad sobre el menor»; «…e el mismo afecte negativamente al menor»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 87.1.a) de la Ley 15/2015
- art. 39 CE
- arts. 158 CCiv
- arts. 3.2 y 85.3 LJV
- art. 87.2 LJV

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

### Formulario 0339 · Nombramiento de coordinador parental

- Año del modelo: 2019
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 34 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de solicitud de nombramiento de coordinador de parentalidad en expediente de jurisdicción voluntaria.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

Don/Doña [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de Doña [COMPLETAR], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, asistida por el/la Letrado/a Don/Doña [NOMBRE Y APELLIDOS], colegiado/a n.º [NÚMERO] del Ilustre Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco y, como mejor proceda en Derecho, DIGO:

Que por medio del presente escrito, y de conformidad con lo previsto en el art. 87.1.a) de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo EXPEDIENTE EN SOLICITUD DE NOMBRAMIENTO DE COORDINADOR PARENTAL DEL MENOR, con base en los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que Don [COMPLETAR] y mi patrocinada mantuvieron una relación de pareja semejante a la de los casados entre los años [COMPLETAR], fruto de cuya unión nació el menor [COMPLETAR], hasta que convinieron en separarse de hecho, siguiéndose proceso civil sobre guarda y custodia en el que se dictó sentencia de fecha [FECHA] en la que se atribuía la misma a la madre Doña [COMPLETAR], fijándose un régimen de visitas a favor del padre.

Se acompaña copia de la sentencia como documento número [Nº DE DOCUMENTO].

2.ª) Que existe una situación de grave y persistente conflicto entre los progenitores, que permanece enquistada ya desde antes de que se dictara la citada sentencia de fecha [FECHA], que se objetiva no solo en el recurso de apelación interpuesto contra dicha sentencia, sino también en los procesos de ejecución seguidos desde entonces entre las partes con los números [COMPLETAR], terminado por auto de fecha [FECHA], nº [Nº DE RESOLUCIÓN], terminado por auto de fecha [FECHA] y nº [Nº DE RESOLUCIÓN], terminado por auto de fecha [FECHA], a los que se suman diversas denuncias interpuestas por la madre contra el padre en Comisaria y ante la Fiscalía de Menores en el año [COMPLETAR] (se acredita mediante documentos números [COMPLETAR]). Tales disputas traen causa, fundamentalmente, de la resistencia del padre al cumplimiento de lo acordado en la sentencia de este Tribunal de fecha [FECHA] por la no contribución al pago de los gastos extraordinarios del hijo común, así como los distintos estilos educativos y estudios de los padres a realizar por su hijo menor.

Se ha establecido entre las partes una dinámica adversarial de enfrentamiento y judicialización y litigación constantes de todas sus controversias que está generando importantes problemas entre los progenitores y que, de agravarse, podría impedir un ejercicio positivo de la parentalidad por los mismos, podría generar un deterioro profundo del conflicto inter parental y terminaría afectando muy negativamente la estabilidad emocional, en especial del menor [COMPLETAR], que acaba de cumplir [Nº] años. Esa judicialización constante de todas las desavenencias y controversias surgidas entre los progenitores en relación con el ejercicio de la parentalidad respecto del hijo común y su mantenimiento durante un periodo prolongado de tiempo, que, en este supuesto, se inició hace [Nº] años, pone de relieve, de una parte, que las resoluciones judiciales que dilucidan las controversias entre aquellos, si bien dan respuesta a cada problema jurídico suscitado, resultan notoriamente insuficientes para normalizar las relaciones entre los progenitores en todas las cuestiones atinentes al correcto ejercicio de las funciones de parentalidad sobre los hijos, cuyo desarrollo precisa de manera necesaria e imprescindible una mínima comunicación, coordinación y cooperación de aquellos, y, de otra, que el enquistamiento del conflicto entre los progenitores, con continuos enfrentamientos por decisiones relativas a los hijos, y los resquemores, resentimientos u odios que aquellos generan, terminan por afectar negativamente al menor que, víctima inocente de un conflicto no provocado por él, se ve inmersos en el mismo y termina por sufrir, de modo casi inevitable, sus perniciosas consecuencias (presiones directas o indirectas de uno o ambos progenitores; intentos de manipulación; indebida implicación en el conflicto de los padres; conflicto de lealtades y, en suma, procesos de desestabilización emocional de todo orden, con graves repercusiones en su personalidad, sus estudios y sus relaciones sociales y familiares).

Se hace precisa una mejora de las relaciones entre los progenitores que permita un correcto ejercicio de las funciones de parentalidad sobre el menor [COMPLETAR], cuyo desarrollo precisa de manera necesaria e imprescindible una mínima comunicación, coordinación y cooperación de aquellos. Se corre el serio riesgo de que se pueda producir un enquistamiento del conflicto entre los progenitores y que el mismo afecte negativamente al menor [COMPLETAR] y éste termine sufriendo de modo inevitable sus perniciosas consecuencias.

Por ello, teniendo en cuenta la incapacidad de las partes para lograr por sí solos un adecuada, ordenada y pacífica ejecución y desarrollo del régimen de estancias y del correcto ejercicio coordinado y normalizado de sus funciones parentales en relación con el cumplimiento del régimen de visitas y estancias establecido y el ejercicio ordinario de las funciones parentales, se estima conveniente que por la autoridad judicial se acuerde, en interés y beneficio del hijo común, y para evitar a éste cualquier riesgo emocional o psicológico, presente o futuro, derivado del enfrentamiento de sus progenitores que pueda alterar su estabilidad y condicionar o perjudicar un desarrollo ordenado y armónico de su personalidad, el nombramiento de un coordinador de parentalidad del grupo familiar a fin de colaborar con los progenitores en el ejercicio de sus funciones, ayudar al tribunal en la resolución de las controversias que se generen y proteger a los menores de la conflictividad parental.

3.ª) Se solicita el nombramiento de esta figura al amparo de las previsiones contenidas en el art. 39 CE y en los arts. 91, 92.5 y 158.6º CCiv, que habilitan legalmente al juez para acordar, en las sentencias recaídas en los procesos de familia, en ejecución de las mismas, o en cualquier procedimiento, específicamente, las cautelas y garantías que estime oportunas para asegurar el eficaz cumplimiento de las medidas personales referidas a los hijos en relación con el sistema de guarda establecido o el régimen de comunicaciones y estancias fijado, y, en general, para adoptar las demás disposiciones que considere oportunas a fin de apartar a los menores de un peligro o evitarle perjuicios en su entorno familiar o social.

En efecto, el art. 158.6º CCiv ofrece un marco jurídico, mínimo pero suficiente, para poder acordar ese tipo de nombramiento. Dicho artículo faculta a los jueces en cualquier proceso civil para adoptar de oficio o a instancia de parte "las disposiciones que considere oportunas a fin de apartar al menor de un peligro o evitarle perjuicios". Resulta evidente que una ruptura parental hiperconflictivizada genera gravísimos perjuicios a los hijos menores de esas parejas, pudiéndose calificar, incluso, de maltrato psicológico hacia sus hijos, la actuación de determinados progenitores en su ruptura como pareja. Por tanto, el art. 158.6º CCiv faculta a los jueces, a petición de alguna de las partes, del Ministerio Fiscal o de oficio si ninguno de ellos lo solicita, a designar a un coordinador parental, siempre que concurran los requisitos exigidos por dicho precepto: que esté abierto un proceso judicial, que se constate una situación de riesgo para algún menor derivada de la actuación de los padres y que la misma pueda ser evitada o al menos disminuida con la intervención de un profesional como el coordinador parental.

En este sentido, aunque sin una regulación específica en nuestra legislación estatal, la figura del coordinador de parentalidad, de creación relativamente reciente, se ha venido aplicando con éxito desde el año 1990 tanto en el ámbito del Derecho comparado (USA, Canadá, y Argentina) como en el ámbito español, donde se ha venido utilizando, primero con carácter experimental y luego con carácter consolidado mediante varios proyectos piloto desarrollados principalmente, a partir del año 2013, en Cataluña (Barcelona y Sabadell) y, posteriormente, en Baleares y Valencia. Los resultados de dichas experiencias se han revelado positivos y beneficiosos para la disminución del nivel de conflicto familiar, para la solución de las controversias y para el aprendizaje de pautas de ejercicio positivo de la parentalidad por parte de ambos progenitores.

Se trata de la persona de un perito, con conocimientos multidisciplinares en Psicología, Trabajo Social, Mediación, Técnicas de negociación y Conciliación y Derecho de Familia, que actúa, por delegación del juez y como auxiliar del mismo, en el ámbito de la ejecución con el cometido genérico de supervisar y controlar la ejecución de las resoluciones judiciales; elaborar un plan de Parentalidad, si no existiere ya; mediar, conciliar o conducir la negociación entre los progenitores con ocasión de las controversias suscitadas entre los mismos para alcanzar acuerdos y, especialmente, impulsar y promover habilidades y técnicas de ejercicio positivo y adecuado de la parentalidad.

 El nombramiento deberá recaer en la persona que designe la Subdirección General de Familia dependiente de la Dirección General de la Familia y el Menor, integrada en la Consejería de Políticas Sociales y Familia de la Comunidad Autónoma de [LOCALIDAD], en el marco de la experiencia piloto que se desarrolla actualmente en los Tribunales de Familia de [LOCALIDAD], de la que este órgano judicial forma parte.

4.ª) Que mi representada está legitimada activamente para el ejercicio de la solicitud efectuada en petición de adopción de tales medidas, conforme a lo dispuesto en los arts. 158 CCiv y 87.3 LJV, por cuanto es uno de los progenitores del menor.

5.ª) Que no obstante no ser preceptiva la intervención de Procurador y Abogado, conforme a lo dispuesto en los arts. 3.2 y 85.3 LJV, se presenta por medio de Procurador legalmente habilitado para actuar ante los tribunales de este partido, y bajo la dirección de Letrado en ejercicio que redacta y firma

6.ª) Que es competente el Tribunal de Instancia al que me dirijo conforme al art. 87.2 LJV en relación con lo dispuesto en el art. 85.1º LOPJ, al haber conocido del procedimiento en el que se estableció la guarda y custodia en favor de la madre y un régimen de visitas en favor del padre.

Por todo lo expuesto, al amparo del art. 158.6.º CCiv, y de los arts. 87 y ss. LJV,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito, y documentos que lo acompañan, lo admita, y por promovido expediente de jurisdicción voluntaria de medidas de protección en relación al menor [COMPLETAR], y practicadas las diligencias oportunas, con audiencia del menor e intervención del Ministerio Fiscal, y previos los demás trámites con arreglo a Derecho dicte resolución en forma de auto en la que se acuerde la intervención en estos autos de un coordinador de parentalidad, (en su caso) cuyo nombramiento recaerá en la persona que designe la Subdirección General de Familia de la Dirección General de la Familia y el Menor, integrada en la Consejería de Políticas Sociales y Familia de la Comunidad Autónoma de [LOCALIDAD], en el marco del Proyecto de Coordinación de las Funciones Parentales suscrito entre dicha Dirección General y la entidad [COMPLETAR].

 OTROSÍ DIGO: Que para los fines expuestos se interesa de este Tribunal que por el Letrado de la Administración de Justicia se libre oficio a la Subdirección General de Familia de la Dirección General de la Familia y el Menor referida para que, en el marco del Proyecto de Coordinación expresado proceda a la designación del coordinador que corresponda.

SUPLICO AL TRIBUNAL que tenga por realizadas las anteriores manifestaciones.

Por ser de justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

	Firma de Procurador/a
