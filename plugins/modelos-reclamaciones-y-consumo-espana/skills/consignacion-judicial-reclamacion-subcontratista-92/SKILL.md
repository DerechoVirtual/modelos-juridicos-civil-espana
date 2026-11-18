---
name: consignacion-judicial-reclamacion-subcontratista-92
description: "Redacta el escrito «Consignación judicial por reclamación del subcontratista» (formulario 92 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Consignación judicial por reclamación del subcontratista

> Formulario 0092 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD (4 veces)
- [ ] IMPORTE (5 veces)
- [ ] FECHA (7 veces)
- [ ] Nº
- [ ] Nº DE DOCUMENTO (4 veces)
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, y bajo la dirección Letrada de Don»; «…numeración del juzgado de procedencia).]»; «… comitente con la entidad subcontratista»; «…simismo la entidad contratista principal»; «…euros, con la contratista principal»; «…rabajos fue subcontratada con la entidad»; «…enda de mi representado en el mes mes de»; «…e recibido por la entidad subcontratista»; «…e a que la entidad contratista principal»; «…, tanto la entidad contratista principal»; «…, como la entidad subcontratista»; «… concertado con la contratista principal»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 1597 del Código Civil
- artículo 1176 del Código Civil
- artículos 1176 y 1177 del Código Civil
- artículo 1178 del Código Civil
- art. 1597 del CC
- artículo 1180 del Código Civil
- artículo 1179 del Código Civil

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

### Formulario 0092 · Consignación judicial por reclamación del subcontratista

- Año del modelo: 2023
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 37 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D/Dª [NOMBRE Y APELLIDOS], Procurador de los Tribunales y de D/Dª [NOMBRE Y APELLIDOS], según acredito por apoderamiento apud-acta que acompaño, con domicilio en [LOCALIDAD], y bajo la dirección Letrada de Don [COMPLETAR], ante la Sección Civil del Tribunal de Instancia de [NOTA DE REVISIÓN: Un solo TI por partido judicial (art. 84.1 LOPJ): sobra «de los de». Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] que por turno de reparto corresponda comparezco y, como mejor proceda en Derecho, DIGO:

- Que al amparo de lo dispuesto en los artículos 1176 y siguientes del Código Civil, en relación con los artículos 98 y 99 de la Ley de Jurisdicción Voluntaria, mediante el presente escrito deduzco expediente de jurisdicción voluntaria de consignación de la cantidad de [IMPORTE] euros para la cancelación de la obligación contraída por responsabilidad directa del comitente con la entidad subcontratista [COMPLETAR] con domicilio en [LOCALIDAD], debiendo ser citada asimismo la entidad contratista principal [COMPLETAR], con domicilio en [LOCALIDAD], en atención a los siguientes

HECHOS

PRIMERO .- En fecha [FECHA], mi representado concertó contrato de arrendamiento de obra para la reforma de su vivienda sita en [LOCALIDAD], pactando un precio a tanto alzado de [IMPORTE] euros, con la contratista principal [COMPLETAR], que debía ser abonado en la forma y plazos establecidos en el contrato (acompaño como documento número [Nº] contrato de arrendamiento de obra de fecha [FECHA]).

La mano de obra de los trabajos fue subcontratada con la entidad [COMPLETAR], quien efectivamente realizó las obras en la vivienda de mi representado.

En fecha [FECHA], la entidad subcontratista comunicó a mi representado que se le adeudaba por parte de la contratista principal la cantidad de [IMPORTE] euros, en concepto de trabajos realizados en la vivienda de mi representado en el mes mes de [COMPLETAR], tal como se acredita por la copia del burofax recibido y factura que acompaño como documentos número [Nº DE DOCUMENTO].

SEGUNDO.- Ante dicha comunicación y atendida la responsabilidad directa del comitente establecida por el art. 1597 del Código Civil, al coincidir el importe de la factura reclamada con el del último plazo pactado en el contrato de arrendamiento de obra, mi representado ofreció a la subcontratista el pago de la cantidad reclamada por importe de [IMPORTE] euros, mediante cheque nominativo expedido en fecha [FECHA], comunicando dicha circunstancia a la contratista principal. Este ofrecimiento fue rechazado por la subcontratista sin razón alguna.

Habida cuenta del rechazo de la percepción del cheque, mi representado ofreció formalmente el pago de la cantidad dineraria adeudada, remitiendo por conducto notarial requerimiento para que la subcontratista aceptara el ofrecimiento de pago, anunciándole en otro caso la consignación judicial de la deuda, el cual fue recibido por la entidad subcontratista [COMPLETAR] el día [FECHA], quien rechazó el ofrecimiento con base a que la entidad contratista principal [COMPLETAR] le adeudaba un importe muy superior al ofrecido (acompaño como documento número [Nº DE DOCUMENTO] copia del documento notarial de ofrecimiento de pago y anuncio de consignación).

Asimismo, se anunció la consignación a la contratista principal como acredito por la copia del documento notarial que acompaño como documento número [Nº DE DOCUMENTO].

TERCERO .- Atendido lo anterior, y habida cuenta que se han cumplido los requisitos de los artículos 1176 y siguientes del Código Civil, se procede a la consignación judicial de la cantidad de [IMPORTE] euros a disposición del órgano judicial al que me dirijo, la cual se ha ingresado en la Cuenta de Depósitos y Consignaciones del Tribunal, según acredito mediante resguardo que acompaño como documento número [Nº DE DOCUMENTO], solicitando que tras los trámites preceptivos se mande cancelar la obligación de pago derivada de la responsabilidad directa que tiene mi representado frente a la subcontratista, conforme a lo establecido en el art. 1597 del Código Civil, en tanto que su responsabilidad se limita a la cantidad adeudada al contratista principal en la fecha de la reclamación, que se corresponde con la consignada por mi representado, quedando al margen las demás relaciones comerciales y deudas que puedan tener la contratista principal y la subcontratista.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

PRIMERO.- COMPETENCIA Son competentes los Tribunales de Instancia de esta ciudad, por ser el del lugar del cumplimiento de la obligación, conforme a lo dispuesto en el art. 98 de la Ley de Jurisdicción Voluntaria.

SEGUNDO.- PROCEDIMIENTO Debe seguirse el procedimiento de jurisdicción voluntaria de consignación de los artículos 98 y 99 de la Ley de Jurisdicción Voluntaria.

TERCERO.- LEGITIMACIÓN Queda definida por el artículo 1176 del Código Civil cuando establece que si el acreedor a quien se hiciere el ofrecimiento de pago conforme a las disposiciones que regulan éste, se negare, de manera expresa o de hecho, sin razón a admitirlo, a otorgar el documento justificativo de haberse efectuado o a la cancelación de la garantía, si la hubiere, el deudor quedará libre de responsabilidad mediante la consignación de la cosa debida, estando legitimados activamente mi representado como deudor en el contrato de arrendamiento de obra de fecha [FECHA] y, pasivamente, tanto la entidad contratista principal [COMPLETAR], como la entidad subcontratista [COMPLETAR] ésta en su condición de acreedora a quien debe realizarse el pago, conforme a lo prevenido en el art. 1597 del Código Civil.

CUARTO.- OFRECIMIENTO DE PAGO Y CONSIGNACIÓN.- Se han cumplido los requisitos establecidos en los artículos 1176 y 1177 del Código Civil al haberse ofrecido el pago al acreedor y se ha comunicado a los interesados según se acredita con la documentación que se acompaña.

QUINTO .- CONSIGNACIÓN Y CANCELACIÓN DE LA OBLIGACIÓN La consignación se ha realizado en la forma prescrita en el artículo 1178 del Código Civil, habiéndose ingresado la cantidad adeudada en concepto de responsabilidad directa del comitente, según lo dispuesto en el art. 1597 del CC, en la Cuenta de Depósitos y Consignaciones del Tribunal, por lo que se está en el caso de solicitar que se declare bien hecha y se mande cancelar la obligación, tras los trámites legales preceptivos, tal como dispone el artículo 1180 del Código Civil, debiendo correr, en su caso, el acreedor con los gastos de la consignación (artículo 1179 del Código Civil).

Por lo anterior,

AL TRIBUNAL SUPLICO que tenga por presentada esta solicitud de consignación judicial de la obligación de pago por responsabilidad directa del comitente derivada del contrato de arrendamiento de obra concertado con la contratista principal [COMPLETAR], en fecha [FECHA], a favor de la subcontratista [COMPLETAR], con los documentos acompañados, resguardo acreditativo de consignación judicial y sus copias, y, en su virtud, la admita y, previos los trámites legales, se dicte resolución declarando bien hecha la consignación y declarando la extinción de la obligación de pago.

OTROSÍ PRIMERO DIGO que se acompaña en anexo relación de documentos e informe presentado, debidamente foliados y con índice electrónico, para su debida localización y consulta.

SUPLICO AL TRIBUNAL tenga hecha esta manifestación a los efectos oportunos y por aportados los documentos e informe pericial relacionados en el anexo.

Es Justicia que insto en [COMPLETAR].

Firma de procurador y letrado.
