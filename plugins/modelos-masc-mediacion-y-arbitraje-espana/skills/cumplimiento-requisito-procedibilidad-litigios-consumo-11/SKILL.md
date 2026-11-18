---
name: cumplimiento-requisito-procedibilidad-litigios-consumo-11
description: "Redacta el escrito «Cumplimiento del requisito de procedibilidad en litigios de consumo (MASC)» (formulario 11 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Cumplimiento del requisito de procedibilidad en litigios de consumo (MASC)

> Formulario 0011 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] FECHA
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…el escrito de demanda deberá consignarse»; «…, que fue contestado por la entidad»; «…el escrito de demanda deberá consignarse»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 30 de la Ley 44/2002
- art. 439 bis LEC
- art. 439.5 LEC
- art. 245.5 LEC
- art. 10 de la Ley 34/2002
- art. 7.1 LO 1/2025
- Ley Orgánica 1/2025
- Ley 7/2017

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

### Formulario 0011 · Cumplimiento del requisito de procedibilidad en litigios de consumo (MASC)

- Año del modelo: 2025
- Revisión 17-11-2026: saltos de párrafo recuperados (texto venía pegado); restos de formato retirados; 3 llamadas a nota sin texto retiradas; 6 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Menciones que deben constar en los escritos de demanda en los litigios en que se ejerciten acciones individuales promovidas por consumidores o usuarios, conforme a DA 7ª LO 1/2025. En el relato fáctico del escrito de demanda deberá consignarse [COMPLETAR]:RECLAMACIÓN EXTRAJUDICIAL EN MATERIA DE CONSUMO.Mi representado envío un requerimiento fehaciente al demandado con fecha [FECHA], que fue contestado por la entidad [COMPLETAR], en los siguientes términos Acompaño como DOCUMENTO NÚM [Nº DE DOCUMENTO], el requerimiento efectuado y como DOCUMENTO NÚM [Nº DE DOCUMENTO], la contestación del banco.

En la fundamentación jurídica del escrito de demanda deberá consignarse [COMPLETAR]:CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.La presente demanda cumple con el requisito de procedibilidad exigido por la DA 7ª de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia. En los litigios en que se ejerciten acciones individuales promovidas por consumidores o usuarios, la admisión de la demanda requerirá la reclamación extrajudicial previa a la empresa o profesional con el que hubieran contratado; pero en estos supuestos, la DA 7ª LO 1/2025 establece alternativas sobre el cumplimiento de este requisito procesal, de modo que se entenderá también cumplido el requisito de procedibilidad con la resolución de las reclamaciones presentadas por los usuarios de los servicios financieros ante el Banco de España, la Comisión Nacional del Mercado de Valores y la Dirección General de Seguros y Fondos de Pensiones en los términos establecidos por el artículo 30 de la Ley 44/2002, de 22 de noviembre, de Medidas de Reforma del Sistema Financiero, o por haber acudido a alguno de los procedimientos a que se refiere la Ley 7/2017, de 2 de noviembre, por la que se incorpora al ordenamiento jurídico español la Directiva 2013/11/UE, del Parlamento Europeo y del Consejo, de 21 de mayo de 2013, relativa a la resolución alternativa de litigios en materia de consumo, o los que pudieran haber sido establecidos en normativa sectorial en desarrollo de la misma.

La cuestión que se plantea respecto de esta DA 7ª II LO 1/2025 en cuanto a las resoluciones de las reclamaciones presentadas ante el Banco de España, la CNMV y la DGSFP es que acudir a tal procedimiento, como medio para cumplir el requisito de procedibilidad, puede suponer un retraso importante para el consumidor, si tenemos en cuenta que antes de acudir a estas organismos es necesario presentar la reclamación ante la empresa contra la que se reclame y una vez denegada o transcurridos dos meses sin respuesta, se podrá presentar la reclamación ante los organismos mencionados, los cuales tendrán un plazo de 4 meses para dictar resolución (vid. Orden ECC/2502/2012, de 16 de noviembre, por la que se regula el procedimiento de presentación de reclamaciones ante los servicios de reclamaciones del Banco de España, la Comisión Nacional del Mercado de Valores y la Dirección General de Seguros y Fondos de Pensiones).

Así, la LO 1/2025, de 2 de enero, ha introducido una vía privilegiada para dar por cumplido el requisito de procedibilidad en las acciones individuales de los consumidores, exceptuándolas de la actividad negociadora a través de los MASC. De este modo, el art. 439 bis LEC, con remisión al art. 439.5 LEC, fija un procedimiento de reclamación extrajudicial en cadena para demandas de nulidad contractual por abusividad fundadas en un préstamo o contrato con garantía real. Como ya se ha adelantado, los requisitos que debe reunir la reclamación extrajudicial y los términos de su realización están previstos en el art. 439 bis LEC, que establece que el consumidor deberá realizar la reclamación previa a la persona física o jurídica que realice la actividad de concesión de préstamos o créditos de manera profesional. El requerido deberá denegarla o admitirla, realizando en este último caso, un cálculo de la cantidad a devolver de manera desglosada incluyendo los intereses y reconociendo o denegando la nulidad de las cláusulas. El consumidor deberá comunicar si acepta o no la liquidación, procediendo el requerido en cao de aceptación a reconocer la nulidad de las cláusulas y a la devolución del dinero. Si considera improcedente la devolución, comunicará los motivos, respecto de los que queda vinculado para el posterior proceso judicial, no pudiendo oponer otros distintos. El plazo máximo para la negociación será de un mes desde la reclamación extrajudicial. El procedimiento extrajudicial se considerará concluido sin acuerdo si el requerido rechaza expresamente la solicitud del consumidor, si transcurre el mes sin contestación y si no existe conformidad entre requerido y requirente. En caso de acuerdo, el requerido tiene un plazo de un mes para abonar las cantidades acordadas, a partir de ese plazo, la cantidad devengará el interés legal incrementado en ocho puntos, quedando además expedita la vía judicial para el consumidor, que estará vedada para las partes durante el tiempo de negociación, teniendo carácter gratuito. La postura de las partes durante este procedimiento extrajudicial previo será valorada por el tribunal para resolver sobre la condena en costas, y en su caso, sobre la solicitud de exoneración o moderación del art. 245.5 LEC en caso de ulterior procedimiento judicial.A su vez, y de modo genérico, la DA 7ª LO 1/2025 permite dar por cumplido el trámite de admisión con una mera reclamación extrajudicial en toda acción individual de un consumidor. Todo lo anterior culmina con la penalización de intereses moratorios por tramos del nuevo art. 19 LGDCU.La aplicación del precepto exige la inmediata acotación conceptual de dos figuras, a saber: a) consumidor y b) acción individual de un consumidor.a) ConsumidorConforme a la definición legal del art. 3 LGDCU, interpretado por consolidada doctrina jurisprudencial y comunitaria, reúnen la condición de consumidores los siguientes sujetos:— Las personas físicas que actúen con un propósito ajeno a su actividad comercial, empresarial, oficio o profesión.— Las personas jurídicas y las entidades sin personalidad jurídica que actúen sin ánimo de lucro en un ámbito ajeno a una actividad comercial o empresarial.— Persona que celebra un contrato para un uso que está relacionado parcialmente con su actividad profesional y que, por tanto, tan solo es parcialmente ajeno a ésta. El Tribunal de Justicia de la UE ha considerado que podría ampararse en su condición de consumidor en el supuesto de que el vínculo de dicho contrato con la actividad profesional del interesado fuera tan tenue que pudiera considerarse marginal.

Por último, destacar también que reunirán la cualidad de consumidor las personas físicas que intervengan como fiadores o garantes de un deudor no consumidor siempre y cuando actúen con un fin ajeno a cualquier actividad profesional, con ausencia de vínculos funcionales con el prestatario (ATJUE de 14 de septiembre de 2016, asunto C-534/2015). Dicha doctrina es aplicable igualmente al hipotecante no deudor.b) Acción individual de un consumidorSobre la noción de acción individual de un consumidor, no existe una posición asentada a día de hoy.

Así, por ejemplo, el Acuerdo del Pleno de la Sección Civil de la Audiencia Provincial de Lugo, de 4 de julio de 2025 asocia las acciones individuales del consumidor a las relativas a las condiciones generales de la contratación, bajo un prisma restrictivo (seguramente inspirado en el art. 250.1.14º LEC), que ataca el principio pro consumatore. Acto seguido, y profundizando dicha tesis, viene a exigir los MASC ordinarios en las acciones de nulidad por usura (art. 3 LRU), alegando que éstas se encuentran fuera de la órbita del Derecho comunitario (como si todo el Derecho de consumo fuera comunitario).

Pero existe otra opinión doctrinal menos restrictiva que, con fundamento en la dicción legal de la DA 7ª LO 1/2025, ciertamente nítida, considera que el concepto se aplica a toda demanda formulada por un consumidor contra un empresario en ejercicio de cualquier tipo de acción individual, sin distinción, ya tenga su base en una disposición legal o en una condición contractual; y concluye que una acción de nulidad por usura, de responsabilidad civil por fraude bancario o de falta de conformidad con los bienes y servicios contratados, entre otras, no dejan de ser, estén sujetas o no al Derecho comunitario, y deriven o no de la impugnación de una condición general o particular, acciones individuales promovidas por consumidores (GÓMEZ LINACERO).

Exigir, en este tipo de pretensiones, al consumidor, un MASC típico u ordinario, desvirtúa por completo el espíritu y finalidad de la DA 7ª, antes expuesto, obligando al consumidor al peregrinaje propio de estos medios, a su coste y a la inevitable transacción sobre una materia de orden público.

En definitiva, la acción de un consumidor, colectiva o individual, es cualquier tipo de pretensión que tenga su fundamento en un contrato celebrado con un empresario en esa condición, simple y llanamente, sin mayores distinciones.

En cuanto a la validez del email como medio fehaciente, será siempre medio apto en la reclamación extrajudicial de la DA 7ª en cualquiera de los siguientes supuestos: a) cuando la empresa tuviere email de la oficina de atención al cliente, b) cuando el email constase en el contrato a cualquier efecto, c) cuando el email conste disponible en la página web de la entidad y d) cuando la empresa, aunque no reúna dichas condiciones, tenga implantación de varios puntos del territorio nacional.

Debe tenerse presente, a los anteriores efectos del apartado c), el art. 10 de la Ley 34/2002, de 11 de julio, de servicios de la sociedad de la información y de comercio electrónico.

No es necesario acreditar la recepción del email, en caso de rechazo tácito. El email, en caso de entidades financieras o bancarias con servicio de atención al cliente disponible online, se presume fehaciente, exigiéndose a las entidades financieras o bancarias la revisión diligente de su correspondencia electrónicaEl email, además, debe reputarse válido, en aplicación extensiva del art. 7.1 LO 1/2025, cuando fuere el canal habitual empleado por las partes en sus comunicaciones previas derivadas de la relación jurídica controvertida (o de otras distintas).
