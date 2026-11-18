---
name: demanda-contra-aseguradora-cobrar-importe-minimo-202
description: "Redacta el escrito «Demanda contra la aseguradora para cobrar el importe mínimo por incumplimiento del seguro» (formulario 202 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda contra la aseguradora para cobrar el importe mínimo por incumplimiento del seguro

> Formulario 0202 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] Nº DE DOCUMENTO (4 veces)
- [ ] Nº (2 veces)
- [ ] FECHA (2 veces)
- [ ] DESCRIBIR
- [ ] IMPORTE (4 veces)
- [ ] ACTO O RESOLUCIÓN
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, con despacho profesional en»; «…mación de cantidad contra la aseguradora»; «…ras del día [FECHA] como consecuencia de»; «…o daños cuya descripción es la siguiente»; «…gún dictamen realizado por el perito Don»; «… y su respuesta, como documentos números»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 52.2 LEC
- arts. 399 a 436 LEC
- art. 249.2 LEC
- arts. 1.157 y 1.158 CCiv
- art. 253 LEC
- arts. 23 y 31 LEC
- arts. 1.089 y 1.091 CCiv
- art. 400 LEC
- art. 394 LEC
- Real Decreto Legislativo 1/2010
- Ley Orgánica 1/2025
- Ley 50/1980

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

### Formulario 0202 · Demanda contra la aseguradora para cobrar el importe mínimo por incumplimiento del seguro

- Año del modelo: 2020
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 25 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda de juicio declarativo reclamando a la aseguradora el pago del importe mínimo de lo que el asegurador pueda deber, según las circunstancias por él conocidas que prevé el art. 18 de la Ley del Contrato de Seguro

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de [NOMBRE DEL REPRESENTADO/A] S.A., según acredito mediante escritura de poder inscrito en el Registro Electrónico de Apoderamientos Judiciales, a cuya justificación aporto certificación de dicho Registro como documento nº [Nº DE DOCUMENTO]; dirigido por el Letrado abajo firmante D./Dña. [NOMBRE Y APELLIDOS], con despacho profesional en [COMPLETAR], ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que, en la representación que ostento, interpongo demanda de juicio declarativo ordinario en reclamación de cantidad contra la aseguradora [COMPLETAR] S.A., con domicilio en

Que esta parte asume el compromiso de recibir cualquier comunicación dirigida por la oficina judicial, durante toda la fase declarativa, e, incluso, en una eventual fase de ejecución por medios telemáticos, en términos del art. 399.1 II LEC, consignándose a estos efectos la siguiente dirección de correo electrónico y nº [Nº] de teléfono:

Fundamento la misma en los siguientes hechos y consideraciones jurídicas:

HECHOS

PRIMERO.- El pasado día [FECHA] mi representado sufrió un siniestro consistente en [DESCRIBIR] cuyo riesgo estaba cubierto por un seguro de responsabilidad civil en virtud de un contrato de seguro que tiene mi mandante suscrito con la aseguradora demandada; y estando al corriente del pago de las primas al tiempo de ocurrir los hechos, cuya póliza y recibos acompaño como documentos números

El siniestro se produjo a las [Nº] horas del día [FECHA] como consecuencia de [COMPLETAR], causando daños cuya descripción es la siguiente [COMPLETAR]

Los daños y perjuicios sufridos ascienden a la cantidad de [IMPORTE] euros según dictamen realizado por el perito Don [COMPLETAR] que se acompaña como documento nº [Nº DE DOCUMENTO] de la demanda.

SEGUNDO.- Una vez acaecido el siniestro mi representado comunicó en tiempo y forma los daños sufridos y una estimación de los mismos a la compañía aseguradora y al no llegar a un acuerdo con la misma designaron los correspondientes peritos para que procedieran a elaborar un informe de valoración de los daños para proceder a la liquidación del siniestro.

En base a dicho informe se ha dirigido a la entidad aseguradora reclamación extrajudicialmente de la cantidad tasada como pago del importe mínimo exigido legalmente cuyo escrito se acompaña como documento nº [Nº DE DOCUMENTO] y al no ser atendido dicho requerimiento se procede a ejercitar acción judicial de reclamación contra la aseguradora solicitando indemnización por un siniestro en seguro de responsabilidad civil.

Se aportan las cartas, de reclamación, y su respuesta, como documentos números [COMPLETAR]

TERCERO.- Que se han intentado agotar todas las vías extrajudiciales de solución amistosa de la controversia sin que la mercantil demandada haya atendido la última reclamación efectuada mediante burofax que se acompaña como documento nº [Nº DE DOCUMENTO] por lo que no queda más remedio a esta parte que acudir a la vía judicial.

A los anteriores hechos, son aplicables los siguientes

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA.

Es competente la Sección Civil del Tribunal de Instancia del domicilio del asegurado, al que se dirige la presente demanda, por aplicación de lo dispuesto en los arts. 52.2 LEC y 24 LCS, en relación con lo dispuesto en el art. 85.1º LOPJ.

II.- PROCEDIMIENTO.

El procedimiento ajustado a derecho será el del juicio declarativo ordinario regulado en los arts. 399 a 436 LEC, atendiendo a la cantidad reclamada que es de [IMPORTE] euros, en aplicación de lo dispuesto en el art. 249.2 LEC.

III.- CAPACIDAD.

Al tratarse de sociedades mercantiles inscritas en el Registro Mercantil de conformidad con los arts. 20 y 33 del Texto Refundido de la Ley de Sociedades de Capital, aprobado por Real Decreto Legislativo 1/2010, de 2 de julio, tienen personalidad jurídica y consiguientemente capacidad para ser parte y capacidad para comparecer en juicio.

IV.- LEGITIMACIÓN.

El demandante tiene legitimación activa como asegurado, al amparo de lo dispuesto por los arts. 1 y 7 LCS, y como acreedor frente al incumplimiento contractual de la demandada, en base a los arts. 1.157 y 1.158 CCiv.

La demandada ostenta la correlativa legitimación pasiva como entidad aseguradora y parte del contrato de seguro, al amparo de lo dispuesto por el art. 1 LCS y como deudora por incumplimiento de sus obligaciones contractuales al no haber indemnizado a mi representado por el siniestro producido.

V.- CUANTÍA.

Conforme al art. 253 LEC cifro la cuantía de la presente demanda en [IMPORTE] euros, que es el importe de la cantidad que se reclama (art. 251 regla 1ª LEC).

VI.- POSTULACIÓN Y DEFENSA.

Conforme a lo previsto en los arts. 23 y 31 LEC, se presenta la demanda por medio de Procurador/a legalmente habilitado y bajo dirección de Letrado firmante de la misma.

VII.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con el requisito de procedibilidad exigido por la DA 7ª de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VIII.- FONDO DE LA CUESTIÓN CONTROVERTIDA.

La acción de reclamación solicitando la indemnización se hace en base a la Ley 50/1980, de 8 de octubre, de Contrato de Seguro (LCS), estableciendo el art. 18 que "El asegurador está obligado a satisfacer la indemnización al término de las investigaciones y peritaciones necesarias para establecer la existencia del siniestro y, en su caso, el importe de los daños que resulten del mismo. En cualquier supuesto, el asegurador deberá efectuar, dentro de los cuarenta días, a partir de la recepción de la declaración del siniestro, el pago del importe mínimo de lo que el asegurador pueda deber, según las circunstancias por él conocidas".

Asimismo, son de aplicación los arts. 1.089 y 1.091 CCiv en cuanto a la eficacia de las obligaciones derivadas de los contratos, y los arts. 23 y ss. LCS en relación al seguro de daños.

Es evidente que estando en vigor la póliza de contrato de seguro, habiéndose materializado el riesgo objeto de cobertura, en este caso, la producción de daños en el vehículo asegurado, y habiendo satisfecho mi representado la prima correspondiente al período en que se produce el siniestro, el asegurador debió pagar el importe mínimo de lo que el asegurador pueda deber como prestación indemnizatoria derivada del contrato de seguro. Al no hacerlo ha incumplido grave y culpablemente el contrato y debe satisfacer a mi representado el importe del mencionado pago mínimo.

A efectos de litispendencia y de cosa juzgada, se deja constancia de que, una vez fijado, después de sustanciada la presente instancia, el importe mínimo de la indemnización que se solicita en la presente demanda, ya no existe razón alguna para no poder discutir en un juicio posterior el importe total de la indemnización, sin que opere el efecto preclusivo del art. 400 LEC, pues el citado artículo impide reservar alegaciones para hechos posteriores, permitiendo tener por aducidos todos los hechos y fundamentos o títulos jurídicos en que el demandante pudiera haber fundado lo pretendido en su demanda, hayan sido o no alegados, pero no permite tener por formulado un pedimento, a efectos de litigios posteriores, que efectivamente no lo haya sido en el litigio anterior; sin embargo esta limitación solo alcanza a las causas de pedir deducibles pero no deducidas, no a las pretensiones deducibles pero no deducidas.

El Tribunal Supremo sigue esta tesis en los últimos pronunciamientos al afirmar que el art. 400 LEC no impide al demandante volver a formular una nueva demanda si en ella lo que se ejercita es una acción distinta aunque se hubiera podido acumular en el primer pleito, relegando la aplicación de la cosa juzgada a aquellos procesos en que se deduzca igual pretensión en las demandas de uno y otro. Es, en tal caso, cuando no cabe iniciar válidamente un segundo proceso para solicitar lo mismo con apoyo en distintos hechos o diferentes fundamentos jurídicos, pues en tal caso la vigente Ley de Enjuiciamiento Civil obliga a estimar bien la excepción de litispendencia (si el primer proceso se halla pendiente) o la de cosa juzgada (si en el mismo ha recaído sentencia dotada de efectos de cosa juzgada material); (SSTS 485/2009 de 25 de junio de 2009, rec. 2534/2004; 189/2011 de 30 de marzo de 2011, rec. 1694/2008; 768/2013 de 5 de diciembre de 2013, rec. 1708/2011; 671/2014 de 19 de noviembre de 2014, rec. 2452/2013; y 515/2016 de 21 de julio de 2016, rec. 1851/2014.

IX.- INTERESES.

El art. 20.3º LCS establece que el asegurador incurrirá en mora cuando no hubiere cumplido su prestación en el plazo de tres meses desde la producción del siniestro, o no hubiere procedido al pago del importe mínimo de lo que pueda deber dentro de los cuarenta días a partir de la recepción de la declaración de siniestro.

X.- COSTAS.

Conforme al art. 394 LEC, las costas han de imponerse a la demandada.

Por lo expuesto,

SUPLICO AL TRIBUNAL:

Que habiendo por presentado este escrito de demanda con los documentos que lo acompañan y copias de uno y otros, los admita y me tenga por comparecido en parte en la representación que ostento y que acreditada dejo; y por promovido juicio declarativo ordinario frente a [ACTO O RESOLUCIÓN] S.A. acuerde dar traslado al demandado para que comparezca y la conteste, y previo los trámites legales y recibimiento a prueba que desde ahora se interesa se dicte en su día sentencia en la que se condene a la aseguradora a indemnizar a mi principal la cantidad de [IMPORTE] euros, con más el interés de mora desde la fecha del siniestro, e imponiendo a la citada demandada el pago de las costas procesales.

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del Abogado

Firma del Procurador
