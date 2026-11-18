---
name: demanda-arbitral-indemnizacion-incumplimiento-1490
description: "Redacta el escrito «Demanda arbitral de indemnización por incumplimiento contractual» (formulario 1490 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda arbitral de indemnización por incumplimiento contractual

> Formulario 1490 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] LOCALIDAD
- [ ] FECHA (4 veces)
- [ ] IMPORTE (5 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] ACTO O RESOLUCIÓN
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…nio arbitral se encuentra en la cláusula»; «…e lo siguiente, «Las partes acuerdan que»; «…y resguardo de ingreso). En los meses de»; «…resultó devuelta por la entidad bancaria»; «…ión del arbitraje a la Corte Arbitral de»; «…por interpuesta Demanda de Arbitraje por»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 1445, 1544 y 1254 del CC
- art. 1258 del CC

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

### Formulario 1490 · Demanda arbitral de indemnización por incumplimiento contractual

- Año del modelo: 2014
- Revisión 17-11-2026: 20 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Encabezamiento
HECHOS
FUNDAMENTOS DE DERECHO
Solicitud a la Corte de Arbitraje
Firmas

Procedimiento arbitral número [Nº DE PROCEDIMIENTO]

AL TRIBUNAL ARBITRAL DE [LOCALIDAD]

HECHOS

Esta demanda de arbitraje trae causa del incumplimiento del demandado del contrato de fecha [FECHA], al dejar impagada la cantidad de [IMPORTE] euros, importe total de dieciséis ventanas de carpintería metálica suministradas e instaladas por el demandante.

El demandante es un empresario que se dedica a la fabricación de obras de carpintería metálica tales como puertas, ventanas, etc.

El demandante y el demandado, en su calidad de constructor, suscribieron en fecha [FECHA] un contrato privado en virtud del cual mi representado se obligaba a entregar la carpintería para las ventanas de veinte viviendas y zonas comunes, por un importe de

El convenio arbitral se encuentra en la cláusula [COMPLETAR] del referido contrato que establece lo siguiente, «Las partes acuerdan que [COMPLETAR] El arbitraje será de derecho debiendo nombrarse un único árbitro por la Corte a quien se encomienda asimismo la administración del arbitraje».

Acompaño copia del citado contrato, como doc. núm. 1.

En fecha [FECHA], el demandante efectuó la instalación de las cuatro primeras ventanas del primer piso, tal como se había convenido en el contrato, siendo satisfecha la cantidad de [IMPORTE] euros, a razón de [IMPORTE] euros por cada una de las ventanas, tal como se había pactado en el contrato (acompaño como documentos número [Nº DE DOCUMENTO] copia del albarán, factura y resguardo de ingreso).

En los meses de [COMPLETAR], el demandante instaló las otras dieciséis ventanas en cumplimiento del contrato, sin que el demandado abonara ninguna cantidad, aduciendo diferentes excusas como falta de liquidez.

Ante el tiempo transcurrido, el demandante presentó factura núm. para su pago mediante domiciliación bancaria, por importe de [IMPORTE] euros, la cual resultó devuelta por la entidad bancaria [COMPLETAR] (acompaño como doc. núm. copia de la citada factura y comunicación bancaria de devolución).

Verificado el impago, mi principal dirigió requerimiento notarial de pago al demandado, el cual contestó al mismo indicando que las ventanas presentaban defectos de instalación y no se ajustaban a lo pactado (acompaño el requerimiento y contestación como doc. núm. [Nº DE DOCUMENTO]), lo cual es totalmente incierto.

Ante esta alegación del demandado y a la vista de su contestación es interés de esta parte proponer que los árbitros designen un perito para que dictamine sobre la correcta instalación de las ventanas y el escrupuloso cumplimiento del contrato, tal como autoriza el art. 32 de la Ley de Arbitraje.

FUNDAMENTOS DE DERECHO

Capacidad y legitimación

Se dan los requisitos de legitimación activa y pasiva

Competencia y procedimiento

Corresponde la competencia para conocer de demanda al árbitro designado por la Corte Arbitral a que me dirijo en virtud del pacto de sumisión de las partes, habiendo convenido la sumisión de la controversia a arbitraje por convenio que cumple lo establecido en el art. 9 de la Ley de Arbitraje, encomendando la administración del arbitraje a la Corte Arbitral de [COMPLETAR], conforme autoriza el art. 14 de la Ley de Arbitraje, debiendo seguirse el procedimiento aprobado por su reglamento de fecha

Acción y pretensión

Es de aplicación el art. 1101, 1108 y concordantes del Código Civil, con independencia de que se califique el contrato como contrato de compraventa, de arrendamiento de obra o mixto, o incluso como un contrato atípico, puesto que el demandante ostenta la condición de acreedor al haber cumplido con las obligaciones que resultaban de lo pactado y el contrato existe desde que una o varias personas consienten en obligarse, respecto de otra u otras, a dar alguna cosa o a prestar algún servicio (art. 1445, 1544 y 1254 del CC) y obliga no solo al cumplimiento de lo expresamente pactado sino también a todas las consecuencias que, según su naturaleza, sean conformes a la buena fe, al uso y a la ley (art. 1258 del CC).

Costas y gastos

Es de aplicación lo establecido en el art. 37.6 de la Ley de Arbitraje y en los arts. del Reglamento de la Corte.

En atención a lo expuesto

SOLICITO A LA CORTE DE ARBITRAJE DE que teniendo por presentado este escrito con sus copias y documentos acompañados, se sirva admitirlo, y tener por interpuesta Demanda de Arbitraje por [COMPLETAR] frente a [ACTO O RESOLUCIÓN], y, tras los trámites previstos en el Reglamento de la Corte de Arbitraje, dicte Laudo Arbitral en el que:

1.- Declare el incumplimiento del demandado del contrato de fecha [FECHA]

2.- Declare que el demandado está obligado a abonar al demandante la cantidad de [IMPORTE], euros, más sus intereses legales desde la interposición de la demanda hasta el pago efectivo.

3.- Condene al demandado a pagar las costas de este procedimiento así como a abonar los honorarios del árbitro y la tasa de administración que se determinen.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del demandante, representante y/o abogado

========================================================================
