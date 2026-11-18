---
name: demanda-remocion-albacea-testamentario-1498
description: "Redacta el escrito «Demanda de remoción del albacea testamentario» (formulario 1498 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de remoción del albacea testamentario

> Formulario 1498 del plugin **Sucesiones** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] CORREO ELECTRÓNICO
- [ ] Nº (2 veces)
- [ ] FECHA (6 veces)
- [ ] NÚMERO (3 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] STS de 13 de abril de 1992 
- [ ] LUGAR
- [ ] Otros 17 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…del Ilustre Colegio de la Abogacía de»; «…, con domicilio (2), primero en»; «…; y segundo, el domicilio laboral en»; «…; y con número de teléfono móvil»; «…de teléfono: HECHOS PRIMERO D./Doña»; «…andantes, sus dos citados hijos, D./Doña»; «…y D./Doña»; «…tario a su hermano, el demandado D./Doña»; «…obra en el protocolo del Notario D./Doña»; «…). SEGUNDO Dicho causante falleció el»; «…siguiente— D./Doña»; «…uerimiento notarial practicado a D./Doña»; …

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Si el poder se otorga a través de la sede judicial electrónica / Si el poder se otorga mediante comparecencia apud acta / Si el poder se otorga ante Notario — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 24.1 LEC
- art. 85 LOPJ
- art. 45 LEC
- art. 50.1 LEC
- art. 7.1 LEC
- art. 10 LEC
- art. 5.2 LEC
- art. 23.1 LEC
- art. 31.1 LEC
- arts. 248 y 249.2 LEC
- arts. 399 a 436 LEC
- art. 253.3 LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 902 CCiv
- art. 1057 CCiv
- art. 898 CCiv
- art. 904 CCiv
- art. 910 CCiv
- art. 1902 CCiv
- art. 394.1 LEC
- art. 24.2 LEC
- art. 155.3 LEC

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

### Formulario 1498 · Demanda de remoción del albacea testamentario

- Año del modelo: 2014
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (3); 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 42 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Receptor
HECHOS
FUNDAMENTOS DE DERECHO
SUPLICO AL TRIBUNAL:
Firmas

Demanda de juicio declarativo ordinario solicitando la remoción de albacea contador-partidor testamentario con indemnización de daños y perjuicios.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD] y D./Dña. [NOMBRE Y APELLIDOS], con domicilio en representación que acredito mediante escritura de poder otorgada a mi favor (existen tres posibilidades para otorgar el apoderamiento al Procurador de los Tribunales, conforme dispone el art. 24.1 LEC)

(Elegir opción en función de cómo se haya otorgado el poder) (1)

[ELEGIR UNA OPCIÓN Y REDACTARLA: Si el poder se otorga a través de la sede judicial electrónica / Si el poder se otorga mediante comparecencia apud acta / Si el poder se otorga ante Notario — el texto de cada opción no venía en el formulario original]

bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], abogado/a en ejercicio, con despacho profesional abierto en [LOCALIDAD], colegiado nº [Nº DE COLEGIADO/A] del Ilustre Colegio de la Abogacía de [COMPLETAR], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO:

Que mediante el presente escrito vengo a formular DEMANDA DE JUICIO DECLARATIVO ORDINARIO, contra D./Dña. [NOMBRE Y APELLIDOS], con domicilio (2), primero en [COMPLETAR]; y segundo, el domicilio laboral en [COMPLETAR]); con (3) email [CORREO ELECTRÓNICO]; y con número de teléfono móvil [COMPLETAR]; en ejercicio de la acción que se concretará en el cuerpo del escrito y en el suplico, y todo ello de conformidad con los hechos y fundamentos de derecho que se desarrollarán a continuación.

Que esta parte asume el compromiso de recibir cualquier comunicación dirigida por la oficina judicial, durante toda la fase declarativa, e, incluso, en una eventual fase de ejecución por medios telemáticos, en términos del art. 399.1 II LEC, consignándose a estos efectos la siguiente dirección de correo electrónico y nº [Nº] de teléfono:

HECHOS

PRIMERO

D./Doña [COMPLETAR] otorgó testamento con fecha [FECHA], designando herederos únicos y universales a mis mandantes, sus dos citados hijos, D./Doña [COMPLETAR] y D./Doña [COMPLETAR], y albacea contador partidor testamentario a su hermano, el demandado D./Doña [COMPLETAR], y al tiempo lo promovía al cargo de tutor mientras sus hijos fueran menores de edad.

Se aporta copia autorizada del testamento, señalando que el original obra en el protocolo del Notario D./Doña [COMPLETAR] (documento n.º [NÚMERO]).

SEGUNDO

Dicho causante falleció el [COMPLETAR] y a medio de instrumento notarial de fecha [FECHA] —practicado el día [FECHA] siguiente— D./Doña [COMPLETAR] fue requerido para proceder a la formalización de las correspondientes operaciones particionales, fijándosele un plazo máximo de 10 días, dada su condición de albacea testamentario, con el apercibimiento de ser responsable de los perjuicios que pudieran imputársele y sin que hubiera llevado a cabo en ningún tiempo el encargo testamentario.

Se adjunta la copia auténtica del acta de requerimiento notarial practicado a D./Doña [COMPLETAR], el día [FECHA], por el Notario de [COMPLETAR], D./Doña [COMPLETAR], con n.º [NÚMERO] de su protocolo general corriente (documento n.º [NÚMERO]).

TERCERO

CUARTO

La parte actora manifiesta que, previo a la presentación de la presente demanda, se han llevado a cabo negociaciones con la parte demandada, con el objetivo de cumplir el requisito de procedibilidad, y resolver la controversia de manera amistosa y extrajudicial. Dichas negociaciones se desarrollaron en cumplimiento de los principios de buena fe, con la intención de alcanzar una solución satisfactoria; incluyéndose entre las acciones realizadas el intercambio de comunicaciones formales mediante correspondencia escrita, en fechas [COMPLETAR], en las cuales esta parte expresó su disposición para dialogar y propuso alternativas de solución (documentos números [COMPLETAR]).

Finalmente, mi representado envió un requerimiento fehaciente al demandado con fecha [FECHA], fijando un plazo de 30 días naturales para llegar a un acuerdo amistoso, a través del abogado que firma este escrito, el cual fue contestado por el demandado por el mismo medio, rechazando el acuerdo/ habiendo sido solo posible un acuerdo parcial, viéndonos en la necesidad de acudir a la presente vía judicial, respecto a los extremos de la controversia en los que se mantiene la discrepancia.

Acompaño como documento nº [Nº DE DOCUMENTO], el requerimiento efectuado y como documento nº [Nº DE DOCUMENTO], la contestación del demandado.

A los anteriores hechos son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA

Sin duda en cuanto a la jurisdicción de los tribunales del Reino en su orden civil, le corresponde conocer de este asunto al Tribunal a quien tengo el honor de dirigirme por ser el de Instancia (art. 85 LOPJ y art. 45 LEC) del domicilio del demandado persona física, si se estima que es aplicable el fuero general del art. 50.1 LEC, en todo caso, coincidente con aquél en que el finado testador tuvo su último domicilio, si se entiende que cuando el art. 52.1.4.º LEC se refiere a cuestiones hereditarias, se está refiriendo a todo litigio en el que se plantee alguna acción o pretensión relacionada con el derecho de sucesiones.

II.- CAPACIDAD

Tanto los actores, mis patrocinados, como el demandado son personas físicas mayores de edad, respecto de las que no consta limitación de ejercicio de derechos civiles, por lo que detentan capacidad para ser parte (art. 6.1.1.º LEC), y capacidad procesal, o de obrar en este concreto juicio (art. 7.1 LEC).

III.- LEGITIMACIÓN

Les corresponde la legitimación activa ordinaria directa (art. 10 LEC) a mis representados por su condición de herederos de D./Dña. [NOMBRE Y APELLIDOS], y ostenta el demandado la legitimación pasiva correlativa, por su condición de albacea de las disposiciones testamentarias del obitado, sujeto a quien afecta la pretensión de declaración que se formula (art. 5.2 LEC).

IV.- POSTULACIÓN

Esta parte, como será debido para la personación que convenga a la contraria, comparece por medio de Procurador/a habilitado ante el Tribunal (art. 23.1 LEC), y bajo la dirección de Letrado en ejercicio (art. 31.1 LEC).

V.- CUANTÍA Y PROCEDIMIENTO

El procedimiento a través del cual se ha de sustanciar la pretensión es el correspondiente al JUICIO ORDINARIO, conforme a los arts. 248 y 249.2 LEC, y se seguirá por los trámites de los arts. 399 a 436 LEC, de manera que la cuantía de la demanda, que se manifiesta a efectos del art. 253.3 LEC, resulta indeterminada, ya que aun siendo económicamente estimable, no puede calcularse conforme a ninguna de las reglas legales de determinación de cuantía.

VI.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VII.- CUESTIÓN DE FONDO

El albaceazgo, más que un propio mandato, por la dificultad de ejercicio dado que el mandante ha fallecido (art. 1732.3.º CCiv), se configura como cargo testamentario de gestión y ejecución de las últimas voluntades del testador [STS de 13 de abril de 1992 ], ya que designa a persona de su confianza para llevar a cabo el cometido de liquidación, partición y adjudicación de sus bienes y demás que prevé el art. 902 CCiv. Las funciones tuitivas que lo integran abarcan asimismo las acumuladas correspondientes a los contadores-partidores (art. 1057 CCiv).

Cuando el testador no ha fijado plazo al ejecutor designado para realizar sus principales actividades de división de los bienes, como es el caso, ha de tenerse en cuenta y partirse al momento de la aceptación del cargo. No acreditándose aceptación expresa ni tácita entra en juego la aceptación por ministerio de la Ley, que opera cuando no se efectúa excusa dentro de los 6 días siguientes a aquél en que se tenga noticia del nombramiento (art. 898 CCiv). El silencio del designado ha de interpretarse, consecuentemente, como aceptación.

A estos efectos ha de determinarse como fecha la correspondiente al requerimiento judicial que se practicó personalmente el [COMPLETAR] y, a partir del mismo, ha de computarse que el demandado contaba con 6 días para excusarse, lo que no realizó y transcurrido dicho plazo, comenzó a correr el término legal que establece el art. 904 CCiv de 1 año para el desempeño de sus funciones.

Pues bien, el demandado en ningún momento ha llevado a cabo el encargo testamentario que presuntamente aceptó, lo que no efectuó y su nula actividad, negligencia y omisión resultan bien patentizadas, por lo que la remoción postulada es totalmente procedente.

El art. 910 CCiv menciona la remoción como terminación del albaceazgo, sin embargo no hace referencia alguna a las causas motivadoras de la misma, vacío que ha ido contemplando la Jurisprudencia, aunque no se ha logrado una definitiva determinación de los supuestos integrantes de tal caso, por tratarse de una construcción doctrinal abierta a las diferentes cuestiones litigiosas.

Se postula en la demanda la extinción del albaceazgo, que también contempla el referido art. 910 CCiv y que ha sido producida por haber transcurrido cumplidamente el plazo legal del año de que se disponía para llevar a cabo el encargo testamentario confiado al demandado que, en forma alguna, realizó, apartándose así de la confianza que le otorgó el testador.

Extinción que opera en forma automática, aunque la norma no lo especifique, pero que reiteradamente también ha mantenido la Jurisprudencia, ya que las funciones delegadas a dichos ejecutores testamentarios no les son concedidas para que meramente las ostente, sino y primordialmente para que las utilice y cumpla con su correspondiente, adecuado y diligente ejercicio.

Por otro lado, como dice la STS de 20 de febrero de 1993, Rec. 2017/1990, la indemnización de daños y perjuicios en materia de albaceazgos opera no como una responsabilidad propiamente contractual, sino como consecuencia obligada del deber jurídico que asume por razón de su aceptación del cargo. De esta manera está obligado a la indemnización de daños y perjuicios cuando actúa con negligencia o morosidad, con culpa o dolo, según los arts. 1101 a 1104 y de aplicada concordancia del CCiv, pero no conforme al art. 1902 CCiv.

Incluso cabe también atribuir responsabilidad indemnizatoria, no sólo cuando se da ejercicio incorrecto y anómalo del cargo, sino por su no ejercicio, en base a una conducta relacionada y constatada con resultados dañosos debidamente adverados.

En este caso, la indemnización que se solicita, a fijar en trámite de ejecución de sentencia, consistirá en el importe de los recargos e intereses de los impuestos de sucesión y plusvalía de cuyo pago no se ocupó el demandado y de cuya gestión venía legalmente encargado, como se acreditará debidamente en el momento procesal oportuno.

VIII.- COSTAS

Serán de cuenta del demandado por lo dispuesto en el art. 394.1 LEC, respecto del principio de vencimiento cuasiobjetivo para declarativos en primera instancia.

Por lo expuesto,

SUPLICO AL TRIBUNAL:

Que tenga por presentado este escrito, lo admita, tenga por deducida DEMANDA DE JUICIO ORDINARIO y en su virtud y previa la tramitación que sea adecuada en Derecho en se sirva en su día dictar sentencia en la que se remueva de su cargo al demandado, D./Dña. [NOMBRE Y APELLIDOS], así como condenarle al pago de la indemnización de los daños y perjuicios que resulten acreditados en la dilación probatoria, y se determinen definitivamente, en su cuantía en trámite de ejecución de sentencia, así como al pago de las costas causadas en este pleito.

Es justicia de hacerse en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

NOTAS DEL FORMULARIO

(1) A la hora de su acreditación, todos los poderes deben estar inscritos en el Registro Electrónico de Apoderamientos Judiciales (REAJ). Se supone que, para su acreditación, basta con la consulta (de dicho Registro) automatizada orientada al dato. Algo que está a disposición de cualquier Letrado de la Administración de Justicia. Sin embargo, dado que el art. 24.2 LEC, configura la certificación de dicha inscripción como vía subsidiaria de acreditación, para el caso de que el sistema no permita aquella consulta automatizada; se señala en el modelo que se acompaña certificación electrónica. El sistema permite emitir dicha certificación para quien inscribe el poder.

(2) El art. 155.3 LEC permite fijar expresar varios domicilios del demandado (el que aparezca en el padrón municipal o conste oficialmente a estos efectos; el que aparezca en Registro oficial o en publicaciones de colegios profesionales, si se trata de empresas o personas colegiadas; donde desarrolle su actividad profesional o laboral no ocasional; si es empresa mercantil, el domicilio de cualquiera de sus administradores, gerentes, o apoderados; o, si es asociación que consta en registro oficial; el domicilio del presidente, miembro o gestor de la Junta correspondiente). Cuando se señalen varios, indicará el orden a seguir para la notificación, con vistas al éxito de la misma.

(3) El art. 155.3 LEC configura una obligación adicional del demandante, consistente en aportar cuantos datos sean de utilidad para localizar al demandado: número de identificación fiscal o de extranjeros, nº [Nº] de teléfono o de fax, dirección de correo electrónico, o similares.

========================================================================
