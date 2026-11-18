---
name: demanda-verbal-complemento-legitima-352
description: "Redacta el escrito «Demanda verbal de complemento de legítima» (formulario 352 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda verbal de complemento de legítima

> Formulario 0352 del plugin **Sucesiones** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] LOCALIDAD (6 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] CORREO ELECTRÓNICO
- [ ] Nº (3 veces)
- [ ] FECHA (6 veces)
- [ ] Nº DE DOCUMENTO (6 veces)
- [ ] IMPORTE (3 veces)
- [ ] ACTO O RESOLUCIÓN
- [ ] LUGAR
- [ ] Otros 28 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…del Ilustre Colegio de la Abogacía de»; «…con domicilio (2), primero en»; «…; y segundo, el domicilio laboral en»; «…; y con número de teléfono móvil»; «…de teléfono: HECHOS PRIMERO.- Don»; «…, padre de mi mandante, falleció en»; «…iudo, y habiendo otorgado testamento, en»; «…, el día [FECHA], ante el Notario»; «… Copia simple del testamento otorgado en»; «…, el día [FECHA], ante el Notario»; «…o del matrimonio nacieron dos hijos, Don»; «…y Don <»; …

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Si el poder se otorga a través de la sede judicial electrónica / Si el poder se otorga mediante comparecencia apud acta / Si el poder se otorga ante Notario — el texto de cada opción no venía en el formulario original
- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS
- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 815 CCiv
- art. 24.1 LEC
- art. 36 LEC
- arts. 9 y 21 LOPJ
- art. 85 LOPJ
- art. 10 LEC
- art. 7.1 LEC
- art. 23 LEC
- art. 31 LEC
- art. 250.2 LEC
- art. 249 LEC
- art. 437.1 LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 808 CCiv
- art. 818 CCiv
- art. 819 CCiv
- art. 820 CCiv
- art. 394 LEC
- art. 231 LEC
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

### Formulario 0352 · Demanda verbal de complemento de legítima

- Año del modelo: 2019
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (3); 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 2 bloques de alternativas señalados; 56 campos de relleno marcados en blanco; 6 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda de juicio declarativo verbal en ejercicio de acción de complemento o adición de legítima, conforme al art. 815 CCiv.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] QUE POR TURNO DE REPARTO CORRESPONDA

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], representación que acredito mediante escritura de poder otorgada a mi favor (existen tres posibilidades para otorgar el apoderamiento al Procurador de los Tribunales, conforme dispone el art. 24.1 LEC)

(Elegir opción en función de cómo se haya otorgado el poder) (1)

[ELEGIR UNA OPCIÓN Y REDACTARLA: Si el poder se otorga a través de la sede judicial electrónica / Si el poder se otorga mediante comparecencia apud acta / Si el poder se otorga ante Notario — el texto de cada opción no venía en el formulario original]

bajo la dirección letrada de D./Dña [NOMBRE Y APELLIDOS], abogado/a en ejercicio, con despacho profesional abierto en [LOCALIDAD], colegiado nº [Nº DE COLEGIADO/A] del Ilustre Colegio de la Abogacía de [COMPLETAR], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO:

Que por medio del presente escrito vengo a formular DEMANDA DE JUICIO VERBAL, SOBRE EJERCICIO DE ACCIÓN DE COMPLEMENTO DE LEGÍTIMA según lo establecido en los artículos 815 y ss. del Código Civil, contra D./Dña. [NOMBRE Y APELLIDOS] con domicilio en [LOCALIDAD] y contra D./Dña [NOMBRE Y APELLIDOS] con domicilio (2), primero en [COMPLETAR]; y segundo, el domicilio laboral en [COMPLETAR]); con (3) email [CORREO ELECTRÓNICO]; y con número de teléfono móvil [COMPLETAR]; y todo ello de conformidad con los siguientes hechos y fundamentos de derecho.

Que esta parte asume el compromiso de recibir cualquier comunicación dirigida por la oficina judicial, durante toda la fase declarativa, e, incluso, en una eventual fase de ejecución por medios telemáticos, en términos del art. 399.1 II LEC, consignándose a estos efectos la siguiente dirección de correo electrónico y nº [Nº] de teléfono:

HECHOS

PRIMERO.- Don [COMPLETAR], padre de mi mandante, falleció en [COMPLETAR], el día [FECHA], siendo viudo, y habiendo otorgado testamento, en [COMPLETAR], el día [FECHA], ante el Notario [COMPLETAR].

Como documentos acreditativos de este extremo se acompaña:

• Certificado de defunción del registro Civil de [LOCALIDAD] como documento núm. [Nº DE DOCUMENTO]
• Certificado e Registro de últimas Voluntades del Ministerio de Justicia, que se acompaña como documento núm. [Nº DE DOCUMENTO]
• Copia simple del testamento otorgado en [COMPLETAR], el día [FECHA], ante el Notario [COMPLETAR] que se acompaña como documento núm. [Nº DE DOCUMENTO]
SEGUNDO.- Como figura en el testamento que se acompaña como documento núm. Fruto del matrimonio nacieron dos hijos, Don [COMPLETAR] y Don < [COMPLETAR].

TERCERO.- En dicho testamento instituye herederos a partes iguales a sus dos hijos y lega al demandado el bien [COMPLETAR] haciendo las siguientes adjudicaciones concretas.

• Se atribuye a mi hijo [COMPLETAR] el inmueble sito en [LOCALIDAD]
• Se atribuye a mi hijo [COMPLETAR] el inmueble sito en [LOCALIDAD]

A su vez, en la cláusula [COMPLETAR] otorga un legado a favor de Don [COMPLETAR].

Como establece en la cláusula [COMPLETAR] del testamento, dispone que, de existir excesos en las adjudicaciones realizadas, se imputarán al tercio de mejora, y en su defecto al tercio de libre disposición.

CUARTO.- Con fecha [FECHA]. El causante, realizó una donación por importe de [IMPORTE] a favor el ahora demandado, donación que ha de ser colacionable e imputada al tercio de legítima.

QUINTO.- El total del caudal relicto asciende a [COMPLETAR] teniendo en cuenta la valoración de sendos inmuebles así como la donación realizada. Atendiendo al caudal, la porción que corresponde a cada heredero en concepto de legítima sería [COMPLETAR] lo que equivale a un tercio de la masa hereditaria, lo que asciende a [IMPORTE] euros.

Se acompañan sendos informes periciales de los bienes adjudicados en el testamento como documento núm. [Nº DE DOCUMENTO] y núm. [Nº]

SEXTO.- A tenor de la valoración acompañada y aun imputado el exceso de adjudicación al tercio de mejora y al tercio de libre disposición, la legítima estricta de mi mandante se ve reducida en [COMPLETAR].

SÉPTIMO.- Procede, por tanto, la reducción del legado realizado a favor de demandado, por importe de [IMPORTE] a fin de ser imputada a la cuota legítima de mi mandante.

OCTAVA.- La parte actora manifiesta que, previo a la presentación de la presente demanda, se han llevado a cabo negociaciones con la parte demandada, con el objetivo de cumplir el requisito de procedibilidad, y resolver la controversia de manera amistosa y extrajudicial. Dichas negociaciones se desarrollaron en cumplimiento de los principios de buena fe, con la intención de alcanzar una solución satisfactoria; incluyéndose entre las acciones realizadas el intercambio de comunicaciones formales mediante correspondencia escrita, en fechas [COMPLETAR], en las cuales esta parte expresó su disposición para dialogar y propuso alternativas de solución.

Finalmente, mi representado envió un requerimiento fehaciente al demandado con fecha [FECHA], fijando un plazo de 30 días naturales para llegar a un acuerdo amistoso, a través del abogado que firma este escrito, el cual fue contestado por el demandado por el mismo medio, rechazando el acuerdo/ habiendo sido solo posible un acuerdo parcial, viéndonos en la necesidad de acudir a la presente vía judicial, respecto a los extremos de la controversia en los que se mantiene la discrepancia.

Acompaño como documento nº [Nº DE DOCUMENTO], el requerimiento efectuado y como documento nº [Nº DE DOCUMENTO], la contestación del demandado.

A estos hechos le son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

Primero.- Jurisdicción y competencia.

Corresponde al orden jurisdiccional civil conocer del asunto en base al art. 36 LEC y arts. 9 y 21 LOPJ.

Corresponde la competencia territorial al Tribunal al que nos dirigimos conforme a lo dispuesto en los arts. 45 y 52.1.4º LEC y en el art. 85 LOPJ.

Segundo.- Capacidad y legitimación

a. Activa: Corresponde a D./Doña. [NOMBRE Y APELLIDOS] en su calidad titular de la relación jurídica u objeto litigioso conforme al art. 10 LEC, en concreto, legitimario que ve menguada su cuota legítima en la atribución realizada por el testador.

b. Pasiva: Corresponde a D./Doña [COMPLETAR] en su calidad titular de la relación jurídica u objeto litigioso conforme al art. 10 LEC, en concreto, heredero que se ve beneficiado, en detrimento de la legítima de mi causante

Ambas partes tienen capacidad para ser parte conforme dispone el art. 6.1.1º LEC.

Igualmente tienen capacidad procesal según lo dispuesto en el art. 7.1 LEC.

Tercero.- Representación y defensa

Comparece la actora representada por Procurador, según lo dispuesto en el art. 23 LEC y asistida de Letrado, conforme a lo contenido en el art. 31 LEC.

Cuarto.- Cuantía

La cuantía del presente procedimiento es [COMPLETAR].

Quinto.- Procedimiento

Conforme a lo dispuesto en el art. 250.2 LEC, no superando los quince mil euros ni ser ninguna de las materias comprendidas en el apartado 1 del art. 249 LEC, corresponde dar a la presente demanda la tramitación prevista parta el juicio verbal, de los arts. 437 y ss. LEC

Sexto.- Cumplimiento de los requisitos de procedibilidad

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 en relación con el art. 437.1 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Séptimo.- Fundamentos jurídico materiales

Resulta de aplicación lo dispuesto en el art. 815 CCiv por el cual, todo heredero forzoso, que haya dejado, por cualquier título menos de la legítima que le corresponda, podrá pedir el complemento de la misma.

Igualmente, a tenor de lo dispuesto en el art. 808 CCiv, la legítima de los hijos y descendientes estará constituida por las dos terceras partes del haber hereditario del padre y de la madre, sin embargo, éstos podrán disponer de una parte de las dos que forman la legítima, para aplicarla como mejora a sus hijos o descendientes.

A su vez, el art. 818 CCiv, dispone que para fijar la legítima estricta se atenderá al valor de los bienes que quedaren a la muerte del testador, con deducción de las deudas y cargas, sin comprender en ellas, las impuestas en el testamento, agregando al valor líquido de los bienes hereditarios el de las donaciones colacionables. Imputándose, conforme dispone el art. 819 CCiv, las donaciones hechas a los hijos, cuando no tengan el concepto de mejora, a su legítima.

Por último, será de aplicación lo dispuesto en el art. 820 CCiv en relación a la reducción, de tal forma que se respetarán las donaciones mientras pueda cubrirse la legítima, reduciendo a anulando, su fuere necesario, las mandas hecha en el testamento, las cuales se reducirán a prorrata, sin distinción alguna.

Octavo.- Costas

Procede la condena en costas de la parte demandada por el principio cuasiobjetivo de vencimiento al amparo del art. 394 LEC, al ver vistas, ésta, rechazadas todas sus pretensiones, sin que exista duda, de hecho o derecho, alguna.

Por lo expuesto

SUPLICO AL TRIBUNAL:

Que teniendo por presentado este escrito con los documentos y copias que se acompañan, y a mí por comparecido y parte en la representación que ostento, se sirva admitirlo, tenga por formulada DEMANDA DE JUICIO VERBAL, SOBRE EJERCICIO DE ACCIÓN DE COMPLEMENTO DE LEGÍTIMA según lo establecido en los arts. 815 y ss. del Código Civil, frente a [ACTO O RESOLUCIÓN] y previos los trámites legales dicte en su día sentencia en la que, estimando la demanda, y en su virtud DECLARE:

• Se declare la reducción del legado que figura en el testamento otorgado por el causante en [COMPLETAR], el [COMPLETAR], ante el Notario [COMPLETAR] a favor de la actora, que verá complementada su legítima en la cuantía correspondiente a su legítima legal.

Todo ello con la imposición de costas a la parte demandada.

Por ser Justicia que pide en a [COMPLETAR]

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

PRIMER OTROSI DIGO que siendo el poder que acompaño, general para pleitos y necesitándolo para otros usos procesales,

SUPLICO AL TRIBUNAL que previo su inserción por copia en autos, acuerde su desglose y devolución a esta parte.

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

SEGUNDO OTROSI DIGO, que esta parte manifiesta su voluntad, a los efectos del art. 231 LEC, de cumplir, rigurosamente, los requisitos previstos en la LEC, y de subsanar cualquier defecto en que haya podido incurrir en este escrito de demanda.

SUPLICOAL TRIBUNAL que tenga por hecha la anterior manifestación a los efectos del art. 231 LEC.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

NOTAS DEL FORMULARIO

(1) A la hora de su acreditación, todos los poderes deben estar inscritos en el Registro Electrónico de Apoderamientos Judiciales (REAJ). Se supone que, para su acreditación, basta con la consulta (de dicho Registro) automatizada orientada al dato. Algo que está a disposición de cualquier Letrado de la Administración de Justicia. Sin embargo, dado que el art. 24.2 LEC, configura la certificación de dicha inscripción como vía subsidiaria de acreditación, para el caso de que el sistema no permita aquella consulta automatizada; se señala en el modelo que se acompaña certificación electrónica. El sistema permite emitir dicha certificación para quien inscribe el poder.

(2) El art. 155.3 LEC permite fijar expresar varios domicilios del demandado (el que aparezca en el padrón municipal o conste oficialmente a estos efectos; el que aparezca en Registro oficial o en publicaciones de colegios profesionales, si se trata de empresas o personas colegiadas; donde desarrolle su actividad profesional o laboral no ocasional; si es empresa mercantil, el domicilio de cualquiera de sus administradores, gerentes, o apoderados; o, si es asociación que consta en registro oficial; el domicilio del presidente, miembro o gestor de la Junta correspondiente). Cuando se señalen varios, indicará el orden a seguir para la notificación, con vistas al éxito de la misma.

(3) El art. 155.3 LEC configura una obligación adicional del demandante, consistente en aportar cuantos datos sean de utilidad para localizar al demandado: número de identificación fiscal o de extranjeros, nº [Nº] de teléfono o de fax, dirección de correo electrónico, o similares.
