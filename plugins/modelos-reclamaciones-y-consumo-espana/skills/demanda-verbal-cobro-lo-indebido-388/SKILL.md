---
name: demanda-verbal-cobro-lo-indebido-388
description: "Redacta el escrito «Demanda verbal de cobro de lo indebido» (formulario 388 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda verbal de cobro de lo indebido

> Formulario 0388 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] Nº
- [ ] NÚMERO (6 veces)
- [ ] FECHA (7 veces)
- [ ] NIF
- [ ] ACTO O RESOLUCIÓN
- [ ] LUGAR
- [ ] Otros 15 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…del Ilustre Colegio de la Abogacía de»; «…ndante es titular de la línea telefónica»; «…, perteneciente a la Compañía»; «… cual existe un segundo número asociado,»; «… TERCERO.- Con fecha [FECHA] la Compañía»; «…remitió sms a los números»; «…compañía telefónica durante los meses de»; «…a»; «…a [COMPLETAR] de»; «…de [COMPLETAR] como documentos núms. a»; «…se remitió a la Compañía»; «…s. b. Pasiva: Corresponde a la mercantil»; …

## Elecciones que hay que hacer

- D./Doña / la mercantil
- NIF / CIF

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Si el poder se otorga a través de la sede judicial electrónica / Si el poder se otorga mediante comparecencia apud acta / Si el poder se otorga ante Notario — el texto de cada opción no venía en el formulario original

## Párrafos opcionales (2)

Inclúyelos solo si encajan en los hechos:

- PRIMER OTROSI DIGO, que siendo el poder que acompaño, general para pleitos y necesitándolo para otros usos pro…
- SEGUNDO OTROSI DIGO, que esta parte manifiesta su voluntad, a los efectos del art. 231 de la LEC, de cumplir, …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 24.1 LEC
- artículo 85 de la LOPJ
- artículo 10 LEC
- artículo 7.1 LEC
- artículo 23 LEC
- artículo 31 LEC
- artículos 250.2 LEC
- artículo 249 LEC
- artículo 1895 CC
- artículo 1896 CC
- artículo 1900 CC
- artículo 1901 CC
- artículo 394 LEC
- art. 231 de la LEC
- art. 24.2 LEC
- art. 155.3 LEC
- Ley Orgánica 1/2025

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

### Formulario 0388 · Demanda verbal de cobro de lo indebido

- Año del modelo: 2019
- Revisión 17-11-2026: restos de formato retirados; 4 llamadas a nota sin texto retiradas; 2 desplegables convertidos en elección en blanco; 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 2 párrafos opcionales señalados; 39 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A la Sección Civil del Tribunal de Instancia de [SEDE] que por turno de reparto corresponda

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], representación que acredito mediante escritura de poder otorgada a mi favor (existen tres posibilidades para otorgar el apoderamiento al Procurador de los Tribunales, conforme dispone el art. 24.1 LEC)

(Elegir opción en función de cómo se haya otorgado el poder)

[ELEGIR UNA OPCIÓN Y REDACTARLA: Si el poder se otorga a través de la sede judicial electrónica / Si el poder se otorga mediante comparecencia apud acta / Si el poder se otorga ante Notario — el texto de cada opción no venía en el formulario original]

bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], abogado/a en ejercicio, con despacho profesional abierto en [LOCALIDAD], colegiado nº [Nº DE COLEGIADO/A] del Ilustre Colegio de la Abogacía de [COMPLETAR], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO:

Que mediante el presente escrito vengo a formular DEMANDA DE JUICIO VERBAL SOBRE RECLAMACIÓN DE CANTIDAD POR COBRO DE LO INDEBIDO por importe de según lo establecido en los artículos 1895 y ss. Del Código Civil, contra la entidad.

Que esta parte asume el compromiso de recibir cualquier comunicación dirigida por la oficina judicial, durante toda la fase declarativa, e, incluso, en una eventual fase de ejecución por medios telemáticos, en términos del art. 399.1 II con relación al art. 437.1, ambos LEC, consignándose a estos efectos la siguiente dirección de correo electrónico y nº [Nº] de teléfono:

Todo ello de conformidad con los siguientes hechos y fundamentos de derecho:

HECHOS

PRIMERO.- Mi mandante es titular de la línea telefónica [COMPLETAR], perteneciente a la Compañía [COMPLETAR], respecto a la cual existe un segundo número asociado, [COMPLETAR]. Se acompaña contrato como documento núm. [NÚMERO].

SEGUNDO.- Con fecha [FECHA] se procedió a realizar el cambio de titularidad respecto al número asociado, solicitando la separación de ambos, solicitud que se realizó a la compañía mediante escrito firmado por ambos titulares, con sus correspondientes DNI y el número de cuenta del nuevo titular donde deberían proceder a la domiciliación de las facturas emitidas a partir de la fecha efectiva de cambio de titular. Se acompaña burofax remitido al departamento de atención al cliente de la entidad como documento núm. [NÚMERO].

TERCERO.- Con fecha [FECHA] la Compañía [COMPLETAR] remitió sms a los números [COMPLETAR] y comunicando que el cambio de titular se haría efectivo con fecha [FECHA]. Se acompaña copia impresa del sms recibido en fecha [FECHA] como documento núm. [NÚMERO].

CUARTO.- Con posterioridad al cambio de titular efectuado por la compañía, se continúa por parte de la misma, a emitir el importe generado por la línea asociada, que ya no pertenece a mi mandante, a su nombre, y en consecuencia a incluirlo en la misma factura, que es cargada en la cuenta de mi mandante mensualmente. Se acompañan las facturas emitidas por la compañía telefónica durante los meses de [COMPLETAR] a [COMPLETAR] de [COMPLETAR] como documentos núms. a [COMPLETAR]. En las facturas emitidas y abonadas se puede observar como a pesar del cambio de titular así como el número de cuenta del nuevo titular, se sigue incluyendo como línea asociada el importe de su tarifa.

Estos hechos han generado un cobro indebido concurriendo todos los requisitos exigidos para su apreciación:

1. Que mi mandante, sin percatarse del cargo en su factura del coste de la línea asociada de la que ya no es titular, ha estado abonando erróneamente el importe de la misma.
2. Concurre una falta de causa en el pago realizado toda vez que el cambio de titular se hizo efectivo con fecha [FECHA].
3. Existe un error en el pago por parte de mi mandante, toda vez que al solicitar el cambio de titularidad, se acompaña el numero de cuenta, donde se deberán efectuar los nuevos cargos, no siendo voluntad de mi mandante, ni pagar en lugar del nuevo titularidad, ni mucho menos se puede deber a una mera liberalidad, puesto que en este caso no se hubiese aportado el numero de cuenta del nuevo titular.

QUINTO.- Mi mandante, percatándose meses después del error en la facturación y consiguiente cargo en cuenta efectuado por la compañía, se pone en contacto con esta, a través de su servicio de atención al cliente, manifestándose que habrá sido un error de facturación, así como que intentarán arreglarlo en la medida de lo posible. Se acompaña mensaje de la compañía demandada con número de reclamación como documento núm. [NÚMERO].

SEXTO.- A fecha de la presentación de la demanda, la compañía telefónica, habiendo procedido al cambio de la titularidad de la cuenta, sigue sin restituir a mi mandante lo cobrado en concepto de facturación por la línea de teléfono asociada, de la cual no es titular, existiendo por tanto mala fe en su conducta, siendo consciente del cobro indebido, ya cesando en la emisión de facturas a nombre de mi titular por los servicios prestados en la línea asociada, no ha procedido a la restitución de lo cobrado.

SÉPTIMO.- Con fecha [FECHA] se remitió a la Compañía [COMPLETAR] burofax solicitando la devolución de lo indebidamente cobrado, sin que se haya recibido respuesta alguna. Se acredita tal extremo mediante burofax remitido como documento núm. [NÚMERO].

A estos hechos le son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Primero.- Jurisdicción y competencia.

Corresponde al orden jurisdiccional civil conocer del asunto en base al art. 36 Ley de Enjuiciamiento Civil y artículos 9, 21 y 22 de la Ley Orgánica del Poder Judicial (LOPJ).

Corresponde la competencia territorial al Tribunal al que nos dirigimos conforme a lo dispuesto en los artículos 45 y 52.1.1º de la LEC y en el artículo 85 de la LOPJ.

Segundo.- Capacidad y legitimación

a. Activa: Corresponde a [ELEGIR: D./Doña / la mercantil], en su calidad de titular de la relación jurídica u objeto litigioso conforme al artículo 10 LEC, en concreto, de solvens que por error ha estado realizando unos pagos sin estar obligado a ellos.

b. Pasiva: Corresponde a la mercantil [COMPLETAR] con CIF [NIF], en su calidad de titular de la relación jurídica u objeto litigioso conforme al artículo 10 LEC, en concreto, de accipiens, la compañía telefónica que ha cobrado los recibos indebidamente.

Ambas partes tienen capacidad para ser parte conforme dispone el artículo 6.1.1º LEC, respecto a la actora, y 6.1.1º o 6.1.3 LEC respecto a la demandada.

Igualmente tiene la actora capacidad procesal según lo dispuesto en el artículo 7.1 LEC.

Tercero.- Representación y defensa

Comparece la actora representada por Procurador, según lo dispuesto en el artículo 23 LEC y asistida de Letrado, conforme a lo contenido en el artículo 31 LEC.

Cuarto.- Cuantía

La cuantía del presente procedimiento es de [COMPLETAR].

Quinto.- Procedimiento

Conforme a lo dispuesto en los artículos 250.2 LEC, no superando los quince mil euros ni ser ninguna de las materias comprendidas en el apartado 1 del artículo 249 LEC, corresponde dar a la presente demanda la tramitación prevista parta el juicio verbal, de los artículos 437 y ss LEC

Sexto.- Cumplimiento de los requisitos de procedibilidad

La presente demanda cumple con el requisito de procedibilidad exigido por la DA 7ª de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Séptimo.-Fundamentos jurídico materiales

Será de aplicación en artículo 1895 CC en relación al cobro de lo indebido, que establece que cuando se recibe alguna cosa que no había derecho a cobrar, y que por error ha sido indebidamente entregada, surge la obligación de restituirla.

Concurren todos y cada uno de los requisitos exigidos jurisprudencialmente (STS 534/2010, de 30 de julio):

• El pago efectivo realizado por el presunto deudor con la finalidad de extinguir la deuda, "animus solvendi", entendido como la entrega de cuerpo cierto in genere. El animus solvendi no es otra cosa que la voluntad del deudor de pagar.
• La inexistencia de obligación entre el que paga y el que recibe, denominado indebitum, y, por consiguiente, la falta de causa en el pago, existiendo un indebitum ex persona, a pesar de existir un vínculo jurídico que se habría generado a partir del cambio del titular, el deudor pasa a ser, precisamente a consecuencia del mismo, sujeto distinto a mi mandante.
• Erro por parte del que hizo el pago, mi mandante, en la errónea creencia de estar abonando las facturas cargadas correspondientes a su línea de teléfono, ha abonado durante meses las mismas, con el ánimo de extinguir la deuda.

Resulta igualmente de aplicación el párrafo primero del artículo 1896 CC siendo procedente el abono del interés legal ante la mala fe del que recibe el pago, debiendo fijarse el diez a quo desde el mismo día en que se emite la primera factura indebida, es presentada al cobro, y en consecuencia es abonada.

En relación a la prueba, conforme dispone el artículo 1900 CC, corresponde al que hubiera hecho el pago acreditarlo, así como el error alegado. En este sentido, se ha acredita el pago realizado mediante las facturas presentadas y los movimientos bancarios de la cuenta titularidad de mi mandante. Y a pesar de acreditar el error pagado, en aplicación al artículo 1901 CC, se establece la presunción del error al haberse realizado un pago que no es debido, que no puede ser desvirtuado por la mera alegación de liberalidad o por otra causa justa.

Octavo.- Costas

Procede la condena en costas de la parte demandada por el principio cuasiobjetivo de vencimiento al amparo del artículo 394 LEC, al ver vistas, ésta, rechazadas todas sus pretensiones, sin que exista duda, de hecho o derecho, alguna.

Por lo expuesto

SUPLICO AL TRIBUNAL: Que teniendo por presentado este escrito con los documentos y copias que se acompañan, y a mí por comparecido y parte en la representación que ostento, se sirva admitirlo, tenga por formulada DEMANDA DE JUICIO VERBAL, SOBRE RECLAMACIÓN DE CANTIDAD POR COBRO DE LO INDEBIDO a frente a [ACTO O RESOLUCIÓN], con domicilio en [LOCALIDAD] y [ELEGIR: NIF / CIF] número [NÚMERO] y previos los trámites legales dicte en su día sentencia en la que, estimando la demanda, y en su virtud DECLARE:

• Se declare la obligación de la demandada de restituir las cantidades indebidamente cobradas que asciende a [COMPLETAR], incrementadas por el interés legal desde el cobro de la primera factura, que asciende a [COMPLETAR]. Todo ello con la imposición de costas a la parte demandada.

Por ser Justicia que pide en [LUGAR], a [FECHA].

[OPCIONAL — incluir si procede]

PRIMER OTROSI DIGO, que siendo el poder que acompaño, general para pleitos y necesitándolo para otros usos procesales,

SUPLICO AL TRIBUNAL que previo su inserción por copia en autos, acuerde su desglose y devolución a esta parte.

[OPCIONAL — incluir si procede]

SEGUNDO OTROSI DIGO, que esta parte manifiesta su voluntad, a los efectos del art. 231 de la LEC, de cumplir, rigurosamente, los requisitos previstos en la LEC., y de subsanar cualquier defecto en que haya podido incurrir en este escrito de demanda.

SUPLICOAL TRIBUNAL que tenga por hecha la anterior manifestación a los efectos del art. 231 de la LEC.

A la hora de su acreditación, todos los poderes deben estar inscritos en el Registro Electrónico de Apoderamientos Judiciales (REAJ). Se supone que, para su acreditación, basta con la consulta (de dicho Registro) automatizada orientada al dato. Algo que está a disposición de cualquier Letrado de la Administración de Justicia. Sin embargo, dado que el art. 24.2 LEC, configura la certificación de dicha inscripción como vía subsidiaria de acreditación, para el caso de que el sistema no permita aquella consulta automatizada; se señala en el modelo que se acompaña certificación electrónica. El sistema permite emitir dicha certificación para quien inscribe el poder.

El art. 155.3 LEC permite fijar expresar varios domicilios del demandado (el que aparezca en el padrón municipal o conste oficialmente a estos efectos; el que aparezca en Registro oficial o en publicaciones de colegios profesionales, si se trata de empresas o personas colegiadas; donde desarrolle su actividad profesional o laboral no ocasional; si es empresa mercantil, el domicilio de cualquiera de sus administradores, gerentes, o apoderados; o, si es asociación que consta en registro oficial; el domicilio del presidente, miembro o gestor de la Junta correspondiente). Cuando se señalen varios, indicará el orden a seguir para la notificación, con vistas al éxito de la misma.
