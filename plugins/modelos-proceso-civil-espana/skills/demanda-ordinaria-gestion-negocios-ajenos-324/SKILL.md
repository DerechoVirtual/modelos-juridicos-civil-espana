---
name: demanda-ordinaria-gestion-negocios-ajenos-324
description: "Redacta el escrito «Demanda ordinaria por gestión de negocios ajenos» (formulario 324 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda ordinaria por gestión de negocios ajenos

> Formulario 0324 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] CORREO ELECTRÓNICO
- [ ] Nº (3 veces)
- [ ] Nº DE DOCUMENTO (5 veces)
- [ ] FECHA (3 veces)
- [ ] MARCA/MODELO (2 veces)
- [ ] MATRÍCULA
- [ ] IMPORTE (7 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…del Ilustre Colegio de la Abogacía de»; «…, con domicilio (2), primero en»; «…; y segundo, el domicilio laboral en»; «…; y con número de teléfono móvil»; «…hículos que gira bajo la denominación de»; «…ando circulaba por la carretera comarcal»; «…, entre las localidades de»; «…, entre las localidades de [COMPLETAR] y»; «…ad anteriormente indicada si añadimos el»; «… papeleta de conciliación ante el LAJ de»; «…tencia en la que: 1.º) Se condene a Doña»; «…ón de la demanda. 2.º) Se condene a Doña»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Si el poder se otorga a través de la sede judicial electrónica / Si el poder se otorga mediante comparecencia apud acta / Si el poder se otorga ante Notario — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 24.1 LEC
- arts. 45 y 50.1 LEC
- art. 249.2 LEC
- art. 10 LEC
- arts. 23 y 31 LEC
- art. 253 LEC
- art. 251 LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 1.888 CCiv
- art. 1.108 CCiv
- art. 576.1 LEC
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

### Formulario 0324 · Demanda ordinaria por gestión de negocios ajenos

- Año del modelo: 2020
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (3); 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 41 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (FECHA, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda de reclamación de cantidad del gestor de negocios ajenos frente al dominus por los gastos generados en la gestión.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], representación que acredito mediante escritura de poder otorgada a mi favor (existen tres posibilidades para otorgar el apoderamiento al Procurador de los Tribunales, conforme dispone el art. 24.1 LEC)

(Elegir opción en función de cómo se haya otorgado el poder) (1)

[ELEGIR UNA OPCIÓN Y REDACTARLA: Si el poder se otorga a través de la sede judicial electrónica / Si el poder se otorga mediante comparecencia apud acta / Si el poder se otorga ante Notario — el texto de cada opción no venía en el formulario original]

bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], abogado/a en ejercicio, con despacho profesional abierto en [LOCALIDAD], colegiado nº [Nº DE COLEGIADO/A] del Ilustre Colegio de la Abogacía de [COMPLETAR], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO:

Que mediante el presente escrito vengo a formular DEMANDA DE JUICIO ORDINARIO EN RECLAMACIÓN DE CANTIDAD, contra D./Dña. [NOMBRE Y APELLIDOS], con domicilio (2), primero en [COMPLETAR]; y segundo, el domicilio laboral en [COMPLETAR]); con (3) email [CORREO ELECTRÓNICO]; y con número de teléfono móvil [COMPLETAR].

Que esta parte asume el compromiso de recibir cualquier comunicación dirigida por la oficina judicial, durante toda la fase declarativa, e, incluso, en una eventual fase de ejecución por medios telemáticos, en términos del art. 399.1 II LEC, consignándose a estos efectos la siguiente dirección de correo electrónico y nº [Nº] de teléfono:

Fundamento mi pretensión en los siguientes:

HECHOS

PRIMERO. Que mi mandante es titular de un negocio dedicado al transporte de vehículos que gira bajo la denominación de [COMPLETAR]

Se acompaña como documento nº [Nº DE DOCUMENTO] copia de modelo 036 de Hacienda donde se puede comprobar quién es el titular de la actividad y que figura dada de alta desde el día [FECHA]

SEGUNDO. Que el día [FECHA] y sobre las [Nº] horas cuando circulaba por la carretera comarcal [COMPLETAR], entre las localidades de [COMPLETAR] y [COMPLETAR], mi representado se encontró con un accidente de circulación, siendo requerido por la Guardia Civil para que retirara a uno de los vehículos implicados, marca [MARCA/MODELO], modelo [MARCA/MODELO], matrícula [MATRÍCULA], propiedad del demandado -que resultó herido en el accidente y cuyo vehículo se había incendiado tras el mismo-, hasta sus dependencias y dejase la vía expedita, lo que así hizo mi mandante, como se comprueba con la copia del atestado que se acompaña como documento nº [Nº DE DOCUMENTO]

Acompaño asimismo como documento número [Nº DE DOCUMENTO] factura que recoge el importe de su intervención, que asciende a [IMPORTE] euros con el siguiente desglose: kilómetros recorridos desde el lugar del accidente donde fue requerido hasta las instalaciones de mi representado [IMPORTE] euros; rescate del vehículo [IMPORTE] euros; tiempo de espera cargando [IMPORTE] euros, lo que nos da la cantidad anteriormente indicada si añadimos el [COMPLETAR] por ciento de IVA.

TERCERO. Tras contactar en varias ocasiones telefónicamente con la propietaria del vehículo y no recibir más que evasivas, mi mandante realizó una reclamación expresa mediante burofax el día [FECHA], que se presenta como documento número [Nº DE DOCUMENTO], al que no se contestó. Luego se presentó una papeleta de conciliación ante el LAJ de [COMPLETAR], a los efectos de cumplir el requisito de procedibilidad para la iniciación de la vía jurisdiccional, acto que terminó sin efecto al no concurrir el representante legal de aquélla, lo que acredito con testimonio de tal actuación que se acompaña como documento número

A los anteriores hechos son de aplicación los siguientes,

FUNDAMENTOS DE DERECHO

I.- JURISDICCIÓN Y COMPETENCIA.

Es competente la Sección Civil del Tribunal de Instancia del domicilio del demandado, al que se dirige la presente demanda, por aplicación de lo dispuesto en los arts. 45 y 50.1 LEC, en relación con lo dispuesto en el art. 85.1º LOPJ.

II.- PROCEDIMIENTO.

La presente demanda deberá sustanciarse por las normas del juicio ordinario, a tenor de lo prevenido en el art. 249.2 LEC, puesto que sin pertenecer al elenco de materias que tienen asignado un cauce procesal determinado, su cuantía es superior a los [IMPORTE] euros.

III.- CAPACIDAD Y LEGITIMACIÓN.

Tanto mi mandante como el demandado son personas físicas en pleno ejercicio de sus derechos civiles, como lo son los mayores de edad sin discapacidad, por lo que tiene capacidad para ser parte y capacidad procesal ex arts. 6.1.1º y 7.1 LEC.

La legitimación activa la tiene mi mandante en cuanto que cumple con los requisitos del art. 10 LEC y ha soportado los gastos que reclama. La pasiva la ostenta la demandada, en cuanto que propietaria del vehículo.

IV.- POSTULACIÓN Y DEFENSA.

Conforme a los arts. 23 y 31 LEC se deduce esta demanda por medio de Procurador/a de los Tribunales con poder notarial para pleitos, y con dirección y firma de Letrado habilitado ante el Tribunal.

V.- CUANTÍA.

Conforme al art. 253 LEC cifro la cuantía de la presente demanda en [IMPORTE] euros, correspondiente a la cantidad reclamada y que se ha cuantificado en el antecedente de hecho segundo, por lo que es de aplicación la regla 1ª del art. 251 LEC. Se justifica tal importe con el documento número [Nº DE DOCUMENTO] de la demanda.

VI.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VII.- FONDO DEL ASUNTO.

Siendo indudable que el demandado estaba obligado a retirar el vehículo de la calzada sin que pudieran abandonarlo en una cuneta, dado el peligro que ello entraña para la circulación, y que por ello debemos admitir que la Guardia Civil les habría obligado a hacerlo y por tanto encargado al demandante su traslado, entendemos que este litigio debe resolverse en función de la regulación que contiene el CCiv sobre la gestión de negocios ajenos, que es una mera expresión de la figura del enriquecimiento injusto o sin causa, pero que nuestro CCiv, siguiendo la tradición romanista lo encuadra dentro de los denominados cuasicontratos.

En este marco, el art. 1.888 CCiv dispone que "el que se encarga voluntariamente de la agencia o administración de los negocios de otro, sin mandato de éste, está obligado a continuar su gestión hasta el término del asunto y sus incidencias, o a requerir al interesado para que le sustituya en la gestión, si se hallase en estado de poder hacerlo por sí" y el art. 1.893 del mismo cuerpo legal indica que "aunque no hubiese ratificado expresamente la gestión ajena, el dueño de bienes ó negocios que aproveche las ventajas de la misma será responsable de las obligaciones contraídas en su interés, e indemnizará al gestor los gastos necesarios y útiles que hubiese hecho y los perjuicios que hubiese sufrido en el desempeño de su cargo".

En este marco normativo, el dueño del negocio que ha aprovechado las ventajas de la gestión o ha evitado perjuicios por razón de la misma, debe asumir, en lógica consecuencia, los gastos y perjuicios que se le han ocasionado al gestor, reembolsando e indemnizando al mismo.

Se parte de un dato objetivo: que la gestión de negocios ajenos haya producido al dueño del negocio alguna ventaja de la que se aproveche o le haya evitado un perjuicio inminente y manifiesto. En uno u otro caso, el dueño del negocio es responsable de las obligaciones contraídas en su interés y debe indemnizar al gestor de los gastos necesarios y útiles que hayan tenido y de los perjuicios que haya sufrido; circunstancias que concurren en el presente caso.

VIII.- INTERESES.

Establece el art. 1.108 CCiv que si se reclama dinero la indemnización de daños y perjuicios, no habiendo pacto en contrario consistirá en el pago de los intereses convenidos, y a falta del mismo, en el interés legal. De manera que se adeuda el mismo desde que se ha procedido a su cálculo en el momento de presentar esta demanda, hasta que mi mandante se vea completamente satisfecho. Todo ello sin perjuicio de lo dispuesto en el art. 576.1 LEC.

IX.- COSTAS.

En cuanto al pago de las costas procesales, procede la imposición a la demandada, de conformidad con el art. 394.1 LEC.

Por ello es por lo que

SUPLICO AL TRIBUNAL

que tenga por presentado este escrito, los documentos que acompañan y copias preceptivas, se sirva admitirlo, tener por instada la acción que contiene, en la representación que ostento, con devolución de poder, y seguida por los trámites del juicio ordinario, emplazando a la demandada para que se persone y oponga, si a su derecho le conviene, en el plazo de veinte días, y en su día, tras los trámites oportunos, y previo recibimiento del juicio a prueba, se dicte sentencia en la que:

1.º) Se condene a Doña [COMPLETAR] a abonar al actor la cantidad de [IMPORTE] euros, más los intereses legales desde la fecha de la interposición de la demanda.
2.º) Se condene a Doña [COMPLETAR] al pago de las costas de este procedimiento.

Es justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) A la hora de su acreditación, todos los poderes deben estar inscritos en el Registro Electrónico de Apoderamientos Judiciales (REAJ). Se supone que, para su acreditación, basta con la consulta (de dicho Registro) automatizada orientada al dato. Algo que está a disposición de cualquier Letrado de la Administración de Justicia. Sin embargo, dado que el art. 24.2 LEC, configura la certificación de dicha inscripción como vía subsidiaria de acreditación, para el caso de que el sistema no permita aquella consulta automatizada; se señala en el modelo que se acompaña certificación electrónica. El sistema permite emitir dicha certificación para quien inscribe el poder.

(2) El art. 155.3 LEC permite fijar expresar varios domicilios del demandado (el que aparezca en el padrón municipal o conste oficialmente a estos efectos; el que aparezca en Registro oficial o en publicaciones de colegios profesionales, si se trata de empresas o personas colegiadas; donde desarrolle su actividad profesional o laboral no ocasional; si es empresa mercantil, el domicilio de cualquiera de sus administradores, gerentes, o apoderados; o, si es asociación que consta en registro oficial; el domicilio del presidente, miembro o gestor de la Junta correspondiente). Cuando se señalen varios, indicará el orden a seguir para la notificación, con vistas al éxito de la misma.

(3) El art. 155.3 LEC configura una obligación adicional del demandante, consistente en aportar cuantos datos sean de utilidad para localizar al demandado: número de identificación fiscal o de extranjeros, nº [Nº] de teléfono o de fax, dirección de correo electrónico, o similares.
