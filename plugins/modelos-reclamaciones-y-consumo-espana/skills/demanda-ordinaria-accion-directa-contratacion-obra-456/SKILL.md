---
name: demanda-ordinaria-accion-directa-contratacion-obra-456
description: "Redacta el escrito «Demanda ordinaria de acción directa en contratación de obra» (formulario 456 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda ordinaria de acción directa en contratación de obra

> Formulario 0456 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] IMPORTE (6 veces)
- [ ] FECHA (4 veces)
- [ ] Nº DE DOCUMENTO (6 veces)
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…rado de la Administración de Justicia de»; «…ción directa contra la entidad comitente»; «…ondición de subcontratista de la entidad»; «…l impago de la factura núm. con fecha de»; «…omotora o comitente la entidad demandada»; «…rajudicial. En este sentido, se acudió a»; «…la que se condene a la entidad demandada»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 1597 CC
- artículo 1597 CC
- art. 1597 del Código Civil
- arts. 45, 47, 50 y 51 de la LEC
- art. 5 de la Ley Orgánica 1/2025
- artículo 1597 del Código Civil
- arts. 1100 y 1108 del CC
- artículos 251 y 252 de la LEC

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

### Formulario 0456 · Demanda ordinaria de acción directa en contratación de obra

- Año del modelo: 2018
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 30 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario revisado conforme a la LO 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales, actuando en representación de D./Dña [NOMBRE Y APELLIDOS] según se acredita por certificación del registro electrónico de apoderamientos judiciales que acompaño (o mediante designación apud acta ante el Letrado de la Administración de Justicia de [COMPLETAR] bajo la dirección letrada de D/Dª [NOMBRE Y APELLIDOS], Abogado/a del Iltre. Colegio de [LOCALIDAD], ante el Tribunal comparezco y como mejor en derecho proceda formulo demanda de juicio ordinario en ejercicio de la acción directa contemplada en el art. 1597 CC en materia de contratación de obra, la cual dirijo contra la entidad comitente, con domicilio en la calle [CALLE], fundando mi pretensión en los siguientes:

HECHOS

PRIMERO.- Mi representado ejercita la acción directa contra la entidad comitente [COMPLETAR] en su condición de subcontratista de la entidad [COMPLETAR], contratista principal, en reclamación de cantidad por el impago de la factura núm. con fecha de [COMPLETAR] y por importe de [IMPORTE] euros, IVA incluido, la cual acompaño como documento número

En fecha [FECHA], esta entidad, contratista principal de la obra, suscribió un contrato de ejecución de obra con mi representado, empresario dedicado a la fabricación de elementos prefabricados para su instalación en obras.

Tal como consta en el contrato que se aporta como documento número [Nº DE DOCUMENTO], el objeto de dicho contrato fue el suministro y montaje de vigas y placas de encofrado para las obras de de la que era promotora o comitente la entidad demandada [COMPLETAR] y cuya ejecución había sido adjudicada a la citada contratista principal. El contrato contempló un precio a tanto alzado de [IMPORTE] euros, sin IVA, por los trabajos previstos.

Dichos trabajos fueron aceptados y recepcionados por el dueño de la obra o comitente, tal como consta en la certificación final de obra que se acompaña como documento número [Nº DE DOCUMENTO] suscrito por el representante de la entidad demandada.

SEGUNDO.- Se cumplen los presupuestos para el ejercicio de la acción directa del artículo 1597 CC, conforme a la interpretación que ha hecho la jurisprudencia, puesto que existe un contrato de obra a precio alzado, en cuya virtud mi representada puso el trabajo y los materiales en la obra.

Asimismo, la entidad demandada es deudora del importe de la factura reclamada, al no haber sido abonada al contratista principal, de manera que existe un crédito del contratista frente al dueño de la obra.

A este efecto, mi representada remitió en fecha [FECHA] burofax a la entidad demanda, con fecha de recepción, en el cual comunicó la reclamación extrajudicial de la deuda con base a los previsto en el art. 1597 del Código Civil, reclamando el pago de la referida factura y, en su caso, la retención del pago de las certificaciones pendientes al contratista principal (Acompaño como documentos número [Nº DE DOCUMENTO] burofax y acuse de recibo).

La entidad demandada contestó en fecha [FECHA], alegando que era ajena a la relación negocial existente entre el contratista principal y mi representada, sin que en ningún momento negara la existencia de la deuda reclamada (acompaño como documento número [Nº DE DOCUMENTO] contestación de la demandada).

TERCERO.- De acuerdo a lo anterior, se interpone la presente demanda frente a la comitente, al tener constancia esta parte que la deuda no había sido abonada cuando fue reclamada en tiempo y forma, lo cual fue notificado asimismo a la entidad, contratista principal, requiriéndole que se abstuviera de realizar ninguna reclamación frente a la comitente ( acompaño como documento número [Nº DE DOCUMENTO] burofax remitido a la contratista principal en fecha [FECHA]).

En el caso que por la demandada se alegara que ha pagado con posterioridad la deuda, debe subrayarse que la jurisprudencia ha reiterado que la reclamación es la que marca el momento a partir del cual el comitente no puede efectuar el pago con plenos efectos liberatorios, ni directamente ni mediante consignación a favor del contratista, pues desde ese momento desaparece la buena fe (SSTS de 16 de abril de 2014, rec. 2340/2011; 4 de julio de 2013, rec. 513/2011; 21 de mayo de 2013, rec. 2221/2010; 25 de abril de 2013, rec. 214/2011 y 8 de mayo de 2008, rec. 3193/2001, entre otras).

Por tanto, cumpliéndose los requisitos para el ejercicio de la acción directa prevenida en el art. 1597 CC, solicitamos que la entidad demandada sea condenada al pago de la cantidad de [IMPORTE] euros reclamada, con el interés legal desde la interpelación judicial.

CUARTO.- Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

PRIMERO.- Competencia.- Corresponde la competencia al Tribunal de Instancia al que me dirijo, por aplicación del art. 85.1º LOPJ, arts. 45, 47, 50 y 51 de la LEC.

SEGUNDO.- Legitimación.- De acuerdo al art. 1597 CC “los que ponen su trabajo y materiales en una obra ajustada alzadamente por el contratista, no tienen acción contra el dueño de ella sino hasta la cantidad que éste adeude a aquél cuando se hace la reclamación”, estando legitimado activamente mi representada para el ejercicio de la acción directa contra el dueño de la obra.

TERCERO.- Procedimiento.- Es el juicio ordinario con fundamento en el art 249.2 dado el importe reclamado de [IMPORTE] euros que excede de los 15.000 € a partir de los que se deben seguir las reclamaciones por las normas del juicio ordinario.

CUARTO.- Cumplimiento de los requisitos de procedibilidad.- La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

QUINTO.- En cuanto al fondo, es de aplicación el art. 1101 y siguientes del CC en relación con el mencionado art. 1597, debiendo citarse la STS 85/2017, de 15 de febrero, que interpreta que la tutela que prevé el citado artículo 1597 del Código Civil, en favor del subcontratista de la obra, también alcanza o se proyecta en el deber que incumbe al comitente o dueño de la obra de «abstenerse» de realizar el pago liberatorio al contratista principal cuando el subcontratista le comunica previamente, bien extrajudicialmente, o bien judicialmente, la existencia y reclamación de la deuda contraída por el contratista principal en la ejecución de la obra adjudicada, requisitos éstos que se cumplen en este caso, por lo que solicitamos la estimación de la demanda.

SEXTO.- Intereses-. Son de aplicación los arts. 1100 y 1108 del CC, debiendo devengarse desde la interpelación extrajudicial.

SÉPTIMO.- Costas.- En materia de costas el art 394 LEC señala que las de primera instancia se imponen a la parte que vea en primera instancia rechazadas sus pretensiones

En base a lo anterior,

SUPLICO AL TRIBUNAL que tenga por presentada la presente demanda con sus documentos y, tras la pertinente tramitación, se dicte por ese Tribunal sentencia por la que se condene a la entidad demandada [COMPLETAR] a que indemnice a la actora en la cantidad de [IMPORTE] euros, con más los intereses desde la interpelación extrajudicial, todo ello con imposición de costas a la citada demandada.

OTROSÍ PRIMERO DIGO. Que, de conformidad con lo dispuesto en los artículos 251 y 252 de la LEC, se fija la cuantía del presente procedimiento en [IMPORTE] euros.

En base a lo anterior, SUPLICO AL TRIBUNAL se tenga por efectuada la anterior manifestación a los efectos pertinentes.

a [DÍA] de [MES] de [AÑO]

Firma Abogado Firma Procurador

========================================================================
