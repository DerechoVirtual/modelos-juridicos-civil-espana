---
name: demanda-nulidad-contrato-opcion-compra-87
description: "Redacta el escrito «Demanda de nulidad de contrato de opción de compra» (formulario 87 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de nulidad de contrato de opción de compra

> Formulario 0087 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] CORREO ELECTRÓNICO
- [ ] Nº (2 veces)
- [ ] FECHA (10 veces)
- [ ] IMPORTE (9 veces)
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 17 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… Procurador/a de los Tribunales y de Don»; «…del Ilustre Colegio de la Abogacía de»; «…te, vengo a interponer demanda DE JUICIO»; «…, en ejercicio de la acción»; «…, con domicilio (2), primero en»; «…; y segundo, el domicilio laboral en»; «…; y con número de teléfono móvil»; «…; en ejercicio de la acción de»; «…cita en la presente demanda la acción de»; «…n de compra sobre la vivienda ubicada en»; «…royectos redactados por el Arquitecto D.»; «…ión que acompaño como documentos números»; …

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Si el poder se otorga a través de la sede judicial electrónica / Si el poder se otorga mediante comparecencia apud acta / Si el poder se otorga ante Notario — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 24.1 LEC
- arts. 85.1LOPJ
- art. 51.1 LEC
- art. 7.4 LEC
- arts. 248 y 249.2 LEC
- art. 253 LEC
- arts. 23 y 31 LEC
- art. 399 LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 1.265 CCiv
- art. 1.269 CCiv
- art. 1.270 CCiv
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

### Formulario 0087 · Demanda de nulidad de contrato de opción de compra

- Año del modelo: 2023
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (3); 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 49 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de demanda en ejercicio de la acción de nulidad de un contrato de opción de compra por vicios en el consentimiento.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DEQ.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de Don [COMPLETAR], con domicilio en [LOCALIDAD], representación que acredito mediante escritura de poder otorgada a mi favor (existen tres posibilidades para otorgar el apoderamiento al Procurador de los Tribunales, conforme dispone el art. 24.1 LEC)

(Elegir opción en función de cómo se haya otorgado el poder) (1)

[ELEGIR UNA OPCIÓN Y REDACTARLA: Si el poder se otorga a través de la sede judicial electrónica / Si el poder se otorga mediante comparecencia apud acta / Si el poder se otorga ante Notario — el texto de cada opción no venía en el formulario original]

bajo la dirección letrada de D./Dña [NOMBRE Y APELLIDOS], abogado/a en ejercicio, con despacho profesional abierto en [LOCALIDAD], colegiado nº [Nº DE COLEGIADO/A] del Ilustre Colegio de la Abogacía de [COMPLETAR], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO:

Que, siguiendo instrucciones de mi mandante, vengo a interponer demanda DE JUICIO [COMPLETAR], en ejercicio de la acción [COMPLETAR], contra D./Dña [NOMBRE Y APELLIDOS], con domicilio (2), primero en [COMPLETAR]; y segundo, el domicilio laboral en [COMPLETAR]); con (3) email [CORREO ELECTRÓNICO]; y con número de teléfono móvil [COMPLETAR]; en ejercicio de la acción de [COMPLETAR], según se especificará en el cuerpo del escrito y en el suplico, y todo ello de conformidad con los siguientes hechos y fundamentos de derecho.

Que esta parte asume el compromiso de recibir cualquier comunicación dirigida por la oficina judicial, durante toda la fase declarativa, e, incluso, en una eventual fase de ejecución por medios telemáticos, en términos del art. 399.1 II LEC, consignándose a estos efectos la siguiente dirección de correo electrónico y nº [Nº] de teléfono:

Se ejercita en la presente demanda la acción de [COMPLETAR]

Fundamento la misma en los siguientes hechos y consideraciones jurídicas:

HECHOS

PRIMERO.- Con fecha [FECHA] mi representado suscribió con la mercantil demandada un contrato privado de opción de compra sobre la vivienda ubicada en [COMPLETAR], según planos y proyectos redactados por el Arquitecto D. [COMPLETAR], que la demandada se proponía construir en solar de su propiedad que se especificaba. Se fijó como precio de la opción la cantidad de [IMPORTE] euros señalándose como plazo de caducidad de la opción el día [FECHA], debiéndose formalizar el contrato de compraventa de la vivienda; no se determinó ni la superficie ni el precio de la vivienda objeto del contrato de opción.

Acredito lo anterior mediante copia del contrato y certificaciones de abono del precio pactado de la opción que acompaño como documentos números [COMPLETAR]

SEGUNDO.- Con fecha [FECHA] se firmó contrato de compraventa privado sobre la misma vivienda, cuyo precio se fijó en [IMPORTE] euros y su forma de pago aplazada.

El comprador se vio compelido a la firma de ese contrato pese a exceder el precio del que en un principio se les había comunicado y ante el temor de perder las cantidades entregadas a cuenta, planteándose en fecha [FECHA] denuncia por estafa contra la gerente de la mercantil vendedora, que fue archivada por auto de fecha [FECHA] (documentos números [COMPLETAR]). Lo que se deja expreso a efectos de interrupción de la prescripción ante una eventual excepción de la parte contraria.

TERCERO.- Terminada la vivienda según certificado de fin de obra con fecha [FECHA], remitió la mercantil demandada carta por conducto notarial el día [FECHA], requiriendo al comprador para la firma de la escritura pública, lo que se reiteró en requerimiento notarial practicado el [COMPLETAR] (documentos números [COMPLETAR]).

A su vez el comprador remitió carta a través de Notario con fecha [FECHA] (documento nº [Nº DE DOCUMENTO]), interesando la resolución de los contratos suscritos y la devolución de las cantidades entregadas, solicitud que no ha sido atendida y fuerza la interposición de esta demanda.

CUARTO.- La parte actora manifiesta que, previo a la presentación de la presente demanda, a mayor abundamiento, se han llevado a cabo negociaciones con la parte demandada, con el objetivo de cumplir el requisito de procedibilidad, y resolver la controversia de manera amistosa y extrajudicial. Dichas negociaciones se desarrollaron en cumplimiento de los principios de buena fe, con la intención de alcanzar una solución satisfactoria; incluyéndose entre las acciones realizadas el intercambio de comunicaciones formales mediante correspondencia escrita, en fechas [COMPLETAR], en las cuales esta parte expresó su disposición para dialogar y propuso alternativas de solución.

Finalmente, mi representado envió un requerimiento fehaciente al demandado con fecha [FECHA], fijando un plazo de 30 días naturales para llegar a un acuerdo amistoso, a través del abogado que firma este escrito, el cual fue contestado por el demandado por el mismo medio, rechazando el acuerdo/ habiendo sido solo posible un acuerdo parcial, viéndonos en la necesidad de acudir a la presente vía judicial, respecto a los extremos de la controversia en los que se mantiene la discrepancia.

Acompaño como documento nº [Nº DE DOCUMENTO], el requerimiento efectuado y como documento nº [Nº DE DOCUMENTO], la contestación del demandado.

FUNDAMENTOS DE DERECHO

I.- JURISDICCIÓN Y COMPETENCIA.

Radicando la competencia genérica en el orden civil de la jurisdicción, detenta la competencia objetiva y funcional la Sección Civil del Tribunal de Instancia, por aplicación de lo dispuesto en los arts. 85.1LOPJ y 45 LEC, y puesto que no está prevenido un fuero territorial preceptivo específico, con arreglo a lo previsto en el art. 51.1 LEC, resulta territorialmente competente el Tribunal a que me dirijo, puesto que es el del partido del lugar donde tienen su domicilio la demandada.

II.- CAPACIDAD.

Mi mandante es persona física, mayor de edad sin discapacidad, por lo que tiene capacidad para ser parte y capacidad procesal ex arts. 6.1.1º y 7.1 LEC, como lo es la entidad demandada, persona jurídico mercantil con capacidad para ser parte que se reconoce en el art. 6.1.3º LEC, debiendo comparecer en juicio por medio de sus representantes legales (art. 7.4 LEC).

III.- LEGITIMACIÓN.

Corresponde la legitimación activa directa a mi mandante, por cuanto ha acreditado su legítimo interés en la nulidad del contrato en cuestión y se ha visto perjudicado por los efectos del mismo.

En cuanto a la legitimación pasiva, corresponde a todos aquéllos que pudieran verse afectados por la resolución que en su día se dicte, en este caso, el vendedor, que intervino en el negocio que se impugna.

IV.- PROCEDIMIENTO.

La presente demanda deberá sustanciarse por las normas del juicio ordinario, a tenor de lo prevenido en los arts. 248 y 249.2 LEC, toda vez que el criterio de atribución preferente de la materia objeto del proceso resulta inaplicable, al carecer de especialidad típica la de éste, y cumplir entonces el criterio de cuantía, que supera los 15.000 euros.

V.- CUANTÍA.

Conforme al art. 253 LEC cifro la cuantía de la presente demanda en [IMPORTE] euros, correspondiente a la cantidad reclamada y al total de lo debido, conforme a lo dispuesto en los arts. 251.1ª y 8ª LEC.

V.- POSTULACIÓN Y DEFENSA.

Conforme a los arts. 23 y 31 LEC se formula esta demanda a través de Procurador/a de los Tribunales con poder notarial para pleitos, y con dirección y firma de Letrado habilitado ante el Tribunal. Asimismo se cumplen los requisitos formales del art. 399 LEC.

VI.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VII.- FONDO DE LA CUESTIÓN CONTROVERTIDA.

De la acción ejercitada

Se ejercita en la presente demanda acción de nulidad contractual por dolo, siendo de aplicación el art. 1.265 CCiv que declara la nulidad del consentimiento (y por ende la de los contratos en los que intervenga) prestado "por error, violencia o dolo".

El dolo, como vicio de la voluntad, aparece definido en el art. 1.269 CCiv, conforme al cual "hay dolo cuando, con palabras o maquinaciones insidiosas de parte de uno de los contratantes, es inducido el otro a celebrar un contrato que, sin ellas, no hubiera hecho". Y el art. 1.270 CCiv añade que "para que el dolo produzca la nulidad de los contratos, deberá ser grave y no haber sido empleado por las dos partes contratantes".

De esta regulación se desprende que el concepto legal del dolo, vicio de la voluntad, consta de dos elementos: a) una conducta insidiosa, que ejerza tal influencia sobre quien declara que su voluntad no puede considerarse libre; y b) que sea grave, es decir, que sea causa determinante del contrato en el que concurre. El concepto central que revela el art. 1.269 CCiv es el de una "estratagema que se utiliza para que se produzca una percepción errónea en el otro contratante y por ello se considera que, en definitiva, el dolo induce a un error, si bien lo que se pone de relieve en este vicio de la voluntad no es tanto el resultado, sino la maquinación utilizada para llegar a él" (STS de 16 de febrero de 2010, rec. 2400/2005).

La jurisprudencia, en concordancia con la doctrina científica, viene exigiendo para apreciar este vicio del consentimiento los siguientes requisitos: i) una conducta insidiosa, intencionada o dirigida a provocar la declaración negocial, mediante palabras o maquinaciones adecuadas; ii) la voluntad del declarante debe haber quedado viciada por haberse emitido sin la natural libertad y conocimiento a causa del engaño; iii) esta conducta debe ser determinante de la declaración; iv) el carácter grave de la conducta insidiosa; y v) el engaño no debe haber sido ocasionado por un tercero, ni empleado por las dos partes (SSTS de 29 de octubre de 2013, rec. 1972/2011; 1 de marzo de 2017, rec. 1181/2014; y 2 de marzo de 2020, rec. 3677/2017).

Específicamente, el concepto de "maquinaciones insidiosas" ha sido interpretado por la jurisprudencia con una considerable amplitud en el sentido de comprender todas aquellas actuaciones de uno de los contratantes dirigidas a obtener el consentimiento por parte del otro que, sin ellas, no habría prestado (STS de 28 de septiembre de 2011, rec. 809/2008).

En ese sentido amplio, el dolo, en cuanto vicio del consentimiento contractual, comprende no sólo la insidia directa o inductora de la conducta errónea del otro contratante sino también la reticencia dolosa del que calla o no advierte a la otra parte en contra del deber de informar que exige la buena fe (dolo negativo u omisivo). Esta modalidad de dolo negativo implica el comportamiento desleal de ocultar intencionadamente información relevante y decisiva y obtener de esta forma el consentimiento del contratante que padece el vicio. Como ha señalado la jurisprudencia, "tal modalidad del dolo exige la reticencia, consistente en la omisión de hechos y circunstancias influyentes o determinantes para la conclusión del contrato, con infracción del deber de informar conforme a la buena fe y a los usos del tráfico. Se calla o no se advierte, cuando había la obligación de hacerlo".

Pues bien, se dan en este caso todos los requisitos para que el dolo produzca la nulidad de los contratos

De la subsunción del supuesto de hecho

Como se ha expuesto en el fáctico, y se acreditará en el momento procesal oportuno, el precio que tuvo en cuenta el comprador al firmar la opción fue de unos [IMPORTE] euros, y así se constata en la oferta que les remitió la empresa demandada, lo que la obligaba según el art. 61TRLGCU, pues en ese documento aparece que el precio para la vivienda de tres dormitorios, sería de [IMPORTE] euros de entrada, [COMPLETAR] efectos de [IMPORTE] euros cada uno y resto «una cantidad similar a la de los efectos», mientras que en el contrato de compraventa, el precio había subido hasta los [IMPORTE] euros, es decir, un incremento superior a [IMPORTE] euros, y como además al firmante del contrato de opción se le pone en la tesitura de perder lo ya pagado o firmar el contrato de compraventa, debe apreciarse que existió dolo que recoge el art. 1.269 CCiv, sancionado con la nulidad, pues es evidente que la actitud de la vendedora constituye una maquinación insidiosa, pues si los compradores hubieran tenido conocimiento de que la vivienda adquirida no valía el precio que se les indicó, sino más del doble, no habrían firmado ese contrato de opción, cuya nulidad ocasiona a su vez la nulidad del de compraventa, por lo que procede el íntegro acogimiento de las pretensiones articuladas en la demanda.

Efectos

Siendo nulo el contrato de opción de compra por concurrencia de dolo contractual, son de aplicación los arts. 1.101 y ss. y 1.303 y concordantes CCiv, debiendo declararse la nulidad del contrato y la indemnización de daños y perjuicios a favor de mi representado, con los intereses moratorios correspondientes.

VIII. COSTAS.-

La parte demandada soportará el reintegro de todas las costas del juicio por el principio cuasiobjetivo de vencimiento del art. 394.1 LEC, para declarativos en primera instancia.

En virtud de lo expuesto,

SUPLICO AL TRIBUNAL

que tenga por presentada la presente demanda, con el dictamen pericial y los documentos a ella adjuntos, por parte en la representación que ostento, y tras la pertinente tramitación se dicte por ese Tribunal sentencia por la que se declare la nulidad del contrato concertado por las partes en fecha [FECHA] y se condene a la demandada a que indemnice a mi representada en la cantidad de [IMPORTE] euros en concepto de indemnización de daños y perjuicios, con más los intereses legales correspondientes, todo ello con imposición de costas a la parte demandada.

Es justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) A la hora de su acreditación, todos los poderes deben estar inscritos en el Registro Electrónico de Apoderamientos Judiciales (REAJ). Se supone que, para su acreditación, basta con la consulta (de dicho Registro) automatizada orientada al dato. Algo que está a disposición de cualquier Letrado de la Administración de Justicia. Sin embargo, dado que el art. 24.2 LEC, configura la certificación de dicha inscripción como vía subsidiaria de acreditación, para el caso de que el sistema no permita aquella consulta automatizada; se señala en el modelo que se acompaña certificación electrónica. El sistema permite emitir dicha certificación para quien inscribe el poder.

(2) El art. 155.3 LEC permite fijar expresar varios domicilios del demandado (el que aparezca en el padrón municipal o conste oficialmente a estos efectos; el que aparezca en Registro oficial o en publicaciones de colegios profesionales, si se trata de empresas o personas colegiadas; donde desarrolle su actividad profesional o laboral no ocasional; si es empresa mercantil, el domicilio de cualquiera de sus administradores, gerentes, o apoderados; o, si es asociación que consta en registro oficial; el domicilio del presidente, miembro o gestor de la Junta correspondiente). Cuando se señalen varios, indicará el orden a seguir para la notificación, con vistas al éxito de la misma.

(3) El art. 155.3 LEC configura una obligación adicional del demandante, consistente en aportar cuantos datos sean de utilidad para localizar al demandado: número de identificación fiscal o de extranjeros, nº [Nº] de teléfono o de fax, dirección de correo electrónico, o similares.
