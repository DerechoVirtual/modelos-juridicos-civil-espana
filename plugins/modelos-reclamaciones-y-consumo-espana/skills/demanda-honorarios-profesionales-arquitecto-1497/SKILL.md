---
name: demanda-honorarios-profesionales-arquitecto-1497
description: "Redacta el escrito «Demanda de honorarios profesionales de arquitecto» (formulario 1497 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de honorarios profesionales de arquitecto

> Formulario 1497 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (10 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] CORREO ELECTRÓNICO
- [ ] Nº (2 veces)
- [ ] FECHA (3 veces)
- [ ] NÚMERO (3 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] IMPORTE (3 veces)
- [ ] LUGAR
- [ ] entre otras, SSTS de 10 de febrero de 1989, 18 de noviembre de 1990 ) ó 19 de abril de 2002, Rec. 3315/1996
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…del Ilustre Colegio de la Abogacía de»; «…, con domicilio (3), primero en»; «…; y segundo, el domicilio laboral en»; «…; y con número de teléfono móvil»; «…SEGUNDO.- El proyecto fue visado el»; «…por el Colegio Oficial de Arquitectos de»; «…, presentándose el»; «… el Se acompañan como documentos números»; «…a»; «…iante correspondencia escrita, en fechas»; «…ón en reuniones llevadas a cabo los días»; «…AD. La tiene mi representada, la entidad»; …

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Si el poder se otorga a través de la sede judicial electrónica / Si el poder se otorga mediante comparecencia apud acta / Si el poder se otorga ante Notario — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 24.1 LEC
- art. 45 LEC
- art. 50.1 LEC
- art. 10 LEC
- art. 5.2 LEC
- art. 23.1 LEC
- art. 31.1 LEC
- arts. 248 y 249.2 LEC
- arts. 399 a 436 LEC
- art. 249.1 LEC
- art. 5 de la Ley Orgánica 1/2025
- arts. 1089 y 1091 CCiv
- arts. 1100 y 1108 CCiv
- art. 394 LEC
- art. 24.2 LEC
- art. 155.3 LEC
- art. 5 p) de la Ley 2/1974
- Ley 7/1997
- Real Decreto 129/2018

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

### Formulario 1497 · Demanda de honorarios profesionales de arquitecto

- Año del modelo: 2014
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; saltos de párrafo recuperados (texto venía pegado); restos de formato retirados; notas del formulario agrupadas al final (5); 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 39 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Receptor
HECHOS
FUNDAMENTOS DE DERECHO
SUPLICO AL TRIBUNAL
Firmas

Demanda de juicio declarativo ordinario reclamando el importe de los honorarios devengados como consecuencia de la intervención profesional de un Arquitecto en la redacción del proyecto básico para la edificación de una vivienda unifamiliar.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], representación que acredito mediante escritura de poder otorgada a mi favor (existen tres posibilidades para otorgar el apoderamiento al Procurador de los Tribunales, conforme dispone el art. 24.1 LEC)

(Elegir opción en función de cómo se haya otorgado el poder) (1)

[ELEGIR UNA OPCIÓN Y REDACTARLA: Si el poder se otorga a través de la sede judicial electrónica / Si el poder se otorga mediante comparecencia apud acta / Si el poder se otorga ante Notario — el texto de cada opción no venía en el formulario original]

bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], abogado/a en ejercicio, con despacho profesional abierto en [LOCALIDAD], colegiado nº [Nº DE COLEGIADO/A] del Ilustre Colegio de la Abogacía de [COMPLETAR], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO (2):

Que mediante el presente escrito vengo a formular DEMANDA DE JUICIO ORDINARIO SOBRE RECLAMACIÓN DE CANTIDAD, contra D./Dña [NOMBRE Y APELLIDOS], con domicilio (3), primero en [COMPLETAR]; y segundo, el domicilio laboral en [COMPLETAR]); con (4) email [CORREO ELECTRÓNICO]; y con número de teléfono móvil [COMPLETAR]; todo ello de conformidad con los hechos y fundamentos de derecho que se especificarán.

Que esta parte asume el compromiso de recibir cualquier comunicación dirigida por la oficina judicial, durante toda la fase declarativa, e, incluso, en una eventual fase de ejecución por medios telemáticos, en términos del art. 399.1 II LEC, consignándose a estos efectos la siguiente dirección de correo electrónico y nº [Nº] de teléfono:

HECHOS

PRIMERO.- Con fecha [FECHA], el demandado D./Dña. [NOMBRE Y APELLIDOS] encargó a mi representado, la redacción de un proyecto básico para una edificación unifamiliar, a ejecutar en un terreno de su propiedad.

Se acompaña como documento n.º [NÚMERO] hoja de encargo profesional suscrita entre la demandada y mi representado, y como documento n.º [NÚMERO] copia del proyecto básico que realizó el Arquitecto D./Dña. [NOMBRE Y APELLIDOS]

SEGUNDO.- El proyecto fue visado el [COMPLETAR] por el Colegio Oficial de Arquitectos de [COMPLETAR], presentándose el [COMPLETAR] ante el Ayuntamiento solicitando la expedición de la licencia municipal de obras, que la otorgó el

Se acompañan como documentos números [COMPLETAR] a [COMPLETAR], copia de la solicitud de licencia de obras para el proyecto básico, informes y resolución del Ayuntamiento de

TERCERO.- El abogado que suscribe ha reclamado infructuosamente en diferentes ocasiones, por teléfono y hasta personalmente, el importe de los honorarios devengados como consecuencia de la intervención profesional de mi mandante por el proyecto básico redactado, cuya minuta acompañamos al presente escrito de demanda como documento n.º [Nº DE DOCUMENTO]

Interesa a esta parte actora manifestar que, previamente a la presentación de la presente solicitud, se llevaron a cabo diversos esfuerzos de negociación con la parte demandada, con el objetivo de cumplir el requisito de procedibilidad, y resolver la controversia de manera amistosa y extrajudicial. Dichas negociaciones se desarrollaron en cumplimiento de los principios de buena fe, con la intención de alcanzar una solución satisfactoria.

Entre las acciones realizadas, se incluyen el intercambio de comunicaciones formales mediante correspondencia escrita, en fechas [COMPLETAR], en las cuales esta parte expresó su disposición para dialogar y propuso alternativas de solución; así como la participación en reuniones llevadas a cabo los días [COMPLETAR], cuyos objetivos fueron buscar una conciliación respecto de las diferencias planteadas.

Se adjuntan como prueba copias de las comunicaciones enviadas y recibidas durante el proceso de negociación, incluidas cartas, correos electrónicos y/o actas de reuniones como bloque documental nº [NÚMERO].

Finalmente, en fecha [FECHA] fue remitido burofax al objeto de dejar constancia fehaciente de la reclamación formulada al demandado, cuyo contenido y acuse de recibo remitido por el servicio de Correos, se acompaña como documento n.º [Nº DE DOCUMENTO]

CUARTO.- Hasta la fecha no se tiene conocimiento de contestación alguna por parte de D./Dña. [NOMBRE Y APELLIDOS]; por este motivo nos vemos obligados a acudir a la vía judicial reclamando los honorarios de mi representada que ascienden a la suma de [IMPORTE] euros, más el interés de demora desde que debió hacerse efectivo el pago.

A los anteriores hechos, les son de aplicación los siguientes,

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA.

Sin duda en cuanto a la jurisdicción de los tribunales del Reino en su orden civil, le corresponde conocer de este asunto al Tribunal a quien tengo el honor de dirigirme por ser el de Instancia (ars. 85 LOPJ y art. 45 LEC) del lugar del domicilio del demandado D./Dña. [NOMBRE Y APELLIDOS], que corresponde al genérico de las personas físicas del art. 50.1 LEC, dado que no hay previsto otro específico para la materia o acción que se ejercita.

II.- CAPACIDAD.

La tiene mi representada, la entidad [COMPLETAR], dado que es sociedad mercantil de capital inscrita en el Registro Mercantil, por lo que tiene reconocida personalidad jurídica diferenciada de sus socios o partícipes, de la que deriva su capacidad para ser titular de derechos, obligaciones y cargas del proceso, y la capacidad de obrar procesal, a través de sus representantes necesarios (arts. 6.1.3.º y 7.4 LEC), y la tiene más obviamente D./Dña. [NOMBRE Y APELLIDOS], en cuanto que persona física mayor de edad, a tenor de lo dispuesto en los arts. 6.1.1.º y 7.1 LEC.

III.- LEGITIMACIÓN.

De conformidad con lo establecido en el art. 10 LEC, corresponde la legitimación activa ordinaria a mi mandante, por su condición de acreedor de los honorarios devengados como consecuencia de los servicios profesionales prestados al demandado, que ostenta la correlativa legitimación pasiva por ser la persona que encargó el proyecto, sujeto a quien afecta la pretensión de declaración que se formula (art. 5.2 LEC) (5).

IV.- POSTULACIÓN.

Esta parte, como será debido para la personación que convenga a la contraria, comparece por medio de Procurador/a de los Tribunales habilitado ante el tribunal (art. 23.1 LEC), y bajo la dirección del Letrado en ejercicio (art. 31.1 LEC).

V.- TRÁMITE.

El procedimiento a través del cual se ha de sustanciar la pretensión es el correspondiente al JUICIO ORDINARIO, conforme a los arts. 248 y 249.2 LEC, y se seguirá por los trámites de los arts. 399 a 436 LEC, puesto que es aplicable el criterio subordinado de la cuantía superior a quince mil euros, dado que la materia no es de las listadas en el art. 249.1 LEC.

VI.- CUANTÍA.

Se señala como cuantía de la demanda la de [IMPORTE] euros, que integra la cantidad líquida reclamada conforme al art. 251.1.ª LEC.

VII.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VIII.- FONDO DE LA CUESTIÓN CONTROVERTIDA.

Actualmente se configura el denominado "contrato de arquitecto" como de obra o empresa, en cuanto el profesional se obliga a prestar al comitente, más que una actividad, el resultado de la misma; la prestación está ligada a la finalidad perseguida por los contratantes, consistente en el trabajo constituido por el proyecto que siempre ha de estar revestido de las condiciones o cualidades de viabilidad para que la obra pueda ser ejecutada. Y quien encarga un trabajo profesional queda obligado al pago de los honorarios (SSTS de 12 de diciembre de 2007, Rec. 4923/2000 y 24 de abril de 2001, Rec. 726/1996).

Indudable la existencia del encargo de redacción del proyecto básico, igualmente está probado que el proyecto básico se confeccionó, fue presentado ante el Ayuntamiento con la solicitud de la licencia de obras, y ésta se obtuvo. Luego el encargo se realizó, y era viable. Surge por ello la obligación de pago de los honorarios, por lo que resultan de aplicación los arts. 1089 y 1091 CCiv, así como, los arts. 1254 y 1258 y concordantes, todos ellos relativos a que las obligaciones nacen de la Ley y de los contratos y que dichas obligaciones tienen fuerza de ley entre las partes, obligando a su cumplimiento, en el marco de la relación jurídica entre el arquitecto y su cliente (art. 1544 y concordantes).

IX.- INTERESES.

Corresponde a la parte demandada el pago de los intereses legales desde la fecha de la reclamación extrajudicial, por aplicación de los arts. 1100 y 1108 CCiv.

X.- COSTAS.

Las costas han de imponerse a la parte demandada en virtud del principio objetivo de vencimiento, de conformidad con lo establecido en el art. 394 LEC.

SUPLICO AL TRIBUNAL

que, teniendo por presentado este escrito con los documentos acompañados y copias simples, el/la Letrado de la Administración de Justicia/a judicial lo admita, teniéndome por personado y parte en la representación acreditada de [COMPLETAR] y por formulada DEMANDA DE JUICIO DECLARATIVO ORDINARIO en reclamación de cantidad por los honorarios devengados y no percibidos por mi poderdante, dictándose en su día, por el tribunal previa la pertinente tramitación, sentencia por la que se condene al demandado D./Dña. [NOMBRE Y APELLIDOS] a pagar a mi mandante la cantidad de [IMPORTE] euros, más intereses legales procedentes, así como pronuncie el abono de las costas del procedimiento a cargo de la parte demandada.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

NOTAS DEL FORMULARIO

(1) A la hora de su acreditación, todos los poderes deben estar inscritos en el Registro Electrónico de Apoderamientos Judiciales (REAJ). Se supone que, para su acreditación, basta con la consulta (de dicho Registro) automatizada orientada al dato. Algo que está a disposición de cualquier Letrado de la Administración de Justicia. Sin embargo, dado que el art. 24.2 LEC, configura la certificación de dicha inscripción como vía subsidiaria de acreditación, para el caso de que el sistema no permita aquella consulta automatizada; se señala en el modelo que se acompaña certificación electrónica. El sistema permite emitir dicha certificación para quien inscribe el poder.

(2) Para esta reclamación podrá acudirse también al juicio monitorio siempre que el acreedor aporte con su solicitud algún documento que acredite indiciariamente la existencia de la deuda. El proceso monitorio regulado en los arts 812 y ss. LEC, es una opción a favor de la protección jurisdiccional del crédito dinerario y permite que quien se considera acreedor de una deuda pecuniaria vencida, líquida, exigible y documentada pueda pedir al tribunal competente que formule un requerimiento de pago a quien considera su deudor para que éste atienda el requerimiento y pague, se oponga al pago dando razones, en cuyo caso será necesario sustanciar un proceso declarativo, o no pague ni se oponga, en cuyo caso se despachará ejecución frente al deudor, permitiendo al acreedor dotarse de un título ejecutivo si el deudor no cumple la obligación dineraria que se le reclama ni formula oposición al requerimiento que se le realiza.

(3) El art. 155.3 LEC permite fijar expresar varios domicilios del demandado (el que aparezca en el padrón municipal o conste oficialmente a estos efectos; el que aparezca en Registro oficial o en publicaciones de colegios profesionales, si se trata de empresas o personas colegiadas; donde desarrolle su actividad profesional o laboral no ocasional; si es empresa mercantil, el domicilio de cualquiera de sus administradores, gerentes, o apoderados; o, si es asociación que consta en registro oficial; el domicilio del presidente, miembro o gestor de la Junta correspondiente). Cuando se señalen varios, indicará el orden a seguir para la notificación, con vistas al éxito de la misma.

(4) El art. 155.3 LEC configura una obligación adicional del demandante, consistente en aportar cuantos datos sean de utilidad para localizar al demandado: número de identificación fiscal o de extranjeros, nº [Nº] de teléfono o de fax, dirección de correo electrónico, o similares.

(5) La legitimación por sustitución del Colegio de Arquitectos para encargarse del cobro de las percepciones, remuneraciones y honorarios profesionales de sus colegiados frente a sus clientes ha sido generalmente admitida por la jurisprudencia de nuestro Tribunal Supremo desde su sentencia de 21 de noviembre de 1958 a la que han seguido otras muchas [entre otras, SSTS de 10 de febrero de 1989, 18 de noviembre de 1990 ) ó 19 de abril de 2002, Rec. 3315/1996] y la llamada jurisprudencia menor de las Audiencias Provinciales.

Consagra la citada doctrina jurisprudencial las previsiones contenidas en el art. 10 LEC ya que si bien en su apartado primero dispone que "serán considerados parte legitimas quienes comparezcan y actúe en juicio como titulares de la relación jurídica u objeto litigioso", en un segundo expresamente exceptúa "los casos en que por ley se atribuya legitimación a persona distinta del titular" siendo así que el art. 5 p) de la Ley 2/1974 de 13

de febrero de Colegios Profesionales (redacción dada por Ley 7/1997 de 14 de abril de medidas liberalizadoras en materia de suelo y de Colegios Profesionales) atribuye a estos, la función de "encargarse del cobro de las percepciones, remuneraciones u honorarios profesionales cuando el colegiado lo solicite libre y expresamente, en el caso de que el Colegio tenga creados los servicios adecuados y en las condiciones que se determinan en los Estatutos de cada Colegio", y a ello debe añadirse lo establecido por el Real Decreto 129/2018 dictado en desarrollo de la Disposición Adicional Única de la antes citada Ley 7/1997, por el que se aprueban los Estatutos Generales de los Colegios de Arquitectos y su Consejo Superior ya que en su art. 7.2 b) contempla expresamente la posibilidad de que los Colegios puedan actuar ante los Jueces y Tribunales por cuenta y en sustitución procesal de sus miembros "en la defensa que ellos mismos voluntariamente les encomienden", señalando en su apartado 4 g), como función del Colegio "Encargarse del cobro de los honorarios profesionales de los colegiados ejercientes en su ámbito territorial, a solicitud de los mismos y en las condiciones que se determinan en los Estatutos y demás normas colegiales".

========================================================================
