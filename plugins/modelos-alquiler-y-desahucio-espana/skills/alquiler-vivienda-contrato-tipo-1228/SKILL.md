---
name: alquiler-vivienda-contrato-tipo-1228
description: "Redacta el escrito «Alquiler de vivienda: contrato tipo» (formulario 1228 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alquiler de vivienda: contrato tipo

> Formulario 1228 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Contrato de 2013-2016: revisar contra la LAU vigente (RDL 29/2026, desde 8-10-2026): duración 5/7 años y prórroga tácita de 3 (arts. 9-10), actualización con tope IRAV y DF 6.ª (2 % hasta 31-12-2027), pago electrónico (17.3), gastos e IBI (20), sin indemnización por desistimiento (11.3), adquisición preferente irrenunciable (25.8) y garantía adicional ≤ 2 meses sin seguro de impago (36.5).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] LOCALIDAD
- [ ] Nº (2 veces)
- [ ] CORREO ELECTRÓNICO
- [ ] IMPORTE (4 veces)
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, en la C/, n.º [Nº], piso»; «… certificado de eficiencia energética de»; «…OE-A-2026-23755)); RDL 29/2026, DF 6.ª.]»; «…za será depositada por el propietario en»; «…tario el presente contrato que consta de»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Forma de pago / En cuenta corriente / En metálico [NOTA DE REVISIÓN: Art. 17.3 LAU vigente: el pago se efectúa por medios electrónicos; en metálico solo excepcionalmente, a solicitud de la parte que carezca de cuenta bancaria o de acceso a medios electrónicos de pago, y en la vivienda arrendada. Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, art. 17.3 (texto consolida

## Correcciones de la revisión (4)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 4.6 de la LAU
- Real Decreto 390/2021
- Ley 29/1994

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

### Formulario 1228 · Alquiler de vivienda: contrato tipo

- Año del modelo: 2013
- Revisión 17-11-2026: 3 citas normativas corregidas tras comprobarlas en el BOE; 2 puntualizaciones normativas añadidas en el texto; 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 19 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (IMPORTE)
- Avisos de la revisión: Contrato de 2013-2016: revisar contra la LAU vigente (RDL 29/2026, desde 8-10-2026): duración 5/7 años y prórroga tácita de 3 (arts. 9-10), actualización con tope IRAV y DF 6.ª (2 % hasta 31-12-2027), pago electrónico (17.3), gastos e IBI (20), sin indemnización por desistimiento (11.3), adquisición preferente irrenunciable (25.8) y garantía adicional ≤ 2 meses sin seguro de impago (36.5).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [DÍA] de [MES] de [AÑO].

MANIFIESTAN

Que D./Dña. [NOMBRE Y APELLIDOS] comparece en nombre propio y es propietario de la finca urbana sita en [LOCALIDAD], en la C/, n.º [Nº], piso [COMPLETAR]

Tal vivienda consta de.

Que D./Dña. [NOMBRE Y APELLIDOS] comparece en nombre propio y desea arrendar el inmueble descrito en el punto anterior para su uso.

Que el arrendatario designa a todos los efectos como domicilio para comunicaciones personales o judiciales el siguiente: y el otro correo electrónico [CORREO ELECTRÓNICO], este último a los efectos de notificación establecidos en el artículo 4.6 de la LAU 1994.

Que ambas partes se reconocen mutuamente la capacidad legal necesaria para otorgar el presente contrato de arrendamiento con arreglo a las siguientes

CLAUSULAS

D./Dña. [NOMBRE Y APELLIDOS] cede en arrendamiento a D./Dña. [NOMBRE Y APELLIDOS] la vivienda de su propiedad descrita en el punto I, libre de cargas y ocupantes.

El arrendatario utilizará el inmueble como vivienda, estableciendo en ella su domicilio. En este momento declara conocer su uso, extensión, características y servicios comunes y privados.

 Acompaña a este documento el certificado de eficiencia energética de [COMPLETAR], según exige el artículo único del Real Decreto 390/2021, de 1 de junio por el que se aprueba el procedimiento básico para la certificación de eficiencia energética de edificios.

El presente contrato de arrendamiento tendrá una duración de [Nº] años a contar desde la fecha de este escrito.

Si la duración pactada fuera inferior a cinco años (o a siete si el arrendador fuese persona jurídica), llegado el vencimiento el contrato se prorrogará obligatoriamente por plazos anuales hasta alcanzar dicha duración mínima, salvo que el arrendatario manifieste con treinta días de antelación su voluntad de no renovarlo. Transcurrida esa duración mínima, si ninguna de las partes notifica a la otra su voluntad de no renovarlo, con al menos cuatro meses de antelación el arrendador o dos meses el arrendatario, el contrato se prorrogará por plazos anuales hasta un máximo de tres años más. [NOTA DE REVISIÓN: Arts. 9.1 y 10.1 LAU (imperativos, contratos desde el 6-3-2019, DT 1.ª RDL 7/2019): prórroga obligatoria anual hasta 5 años (7 si el arrendador es persona jurídica) y, después, prórroga tácita anual hasta 3 años más salvo preaviso de 4 meses (arrendador) o 2 meses (arrendatario). El preaviso de 30 días/un mes con prórroga anual es la redacción de 2013. Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, arts. 9.1 y 10.1; RDL 7/2019 DT 1.ª, BOE-A-2019-3108.]

Finalizada la duración pactada y, en su caso, la prórroga anual, el arrendatario deberá dejar el inmueble en buen estado de uso, sin perjuicio del deterioro ordinario que haya sufrido.

El arrendatario abonará al arrendador en concepto de renta la cantidad de [IMPORTE] euros anuales, es decir, [IMPORTE] euros mensuales.

El pago se llevará a efecto por anticipado dentro de los cinco primeros días de cada mes

[ELEGIR UNA OPCIÓN Y REDACTARLA: Forma de pago / En cuenta corriente / En metálico [NOTA DE REVISIÓN: Art. 17.3 LAU vigente: el pago se efectúa por medios electrónicos; en metálico solo excepcionalmente, a solicitud de la parte que carezca de cuenta bancaria o de acceso a medios electrónicos de pago, y en la vivienda arrendada. Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, art. 17.3 (texto consolidado vigente).] — el texto de cada opción no venía en el formulario original]

 La renta se actualizará anualmente, previa notificación por escrito al arrendatario, [NOTA DE REVISIÓN: Art. 18 LAU vigente: solo hay actualización si se pacta; el incremento anual no puede exceder de la variación del IRAV y la renta actualizada es exigible desde el mes siguiente a la notificación escrita (art. 18.2; vale la nota en el recibo). Para las anualidades que se cumplan entre el 8-10-2026 y el 31-12-2027, DF 6.ª RDL 29/2026: sin incremento si la renta supera el límite del sistema de índices de referencia; en otro caso, lo que se pacte de nuevo y, a falta de pacto, máximo 2 %. Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, art. 18 (redacción RDL 29/2026, BOE-A-2026-20823 (convalidado: BOE-A-2026-23755)); RDL 29/2026, DF 6.ª.] [COMPLETAR].

Correrán por cuenta del arrendatario los gastos generales y de servicios individuales tales como luz, teléfono y agua. Asimismo deberá abonar la cuota de comunidad de propietarios, cuyo importe anual a la fecha del contrato asciende a [IMPORTE] euros. El impuesto sobre bienes inmuebles será a cargo del arrendador. [NOTA DE REVISIÓN: Art. 20.1 LAU (RDL 29/2026, vigente desde el 8-10-2026): el pacto de gastos generales debe constar por escrito con su importe anual y no pueden imponerse al arrendatario los tributos asociados a la vivienda (salvo que sea obligado tributario). En contratos anteriores al 8-10-2026 rige lo pactado conforme a la redacción vigente al celebrarse (el RDL no fija régimen transitorio expreso). Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, art. 20.1 (redacción RDL 29/2026, BOE-A-2026-20823 (convalidado: BOE-A-2026-23755)).]

 El arrendatario deberá proceder a poner a su nombre los servicios de teléfono, gas, agua y suministro eléctrico autorizando, en consecuencia el arrendador, para que los dé de baja a nombre de éste, siempre que sea posible el cambio de titularidad. En caso contrario, se obliga a abonar al propietario los recibos que se giren por estos suministros en el momento en que se pasen al pago.

El arrendador recibe en este momento la cantidad de [IMPORTE] euros en concepto de fianza.

La fianza será depositada por el propietario en [COMPLETAR], y se devolverá al inquilino a la finalización del contrato, salvo que la misma tenga que aplicarse al arreglo de desperfectos ocasionados por el arrendatario, o pago de rentas o cantidades asimiladas adeudadas.

 El arrendador hace constar que los datos de esta vivienda se hallan incluidos en el Registro de Viviendas Protegidas.

En todo lo no regulado en el presente contrato se someten las partes a la Ley 29/1994, de 24 de noviembre, de Arrendamientos Urbanos.

: Las partes acuerdan la inscripción del contrato en el Registro de la Propiedad, corriendo los gastos que ello ocasione por cuenta del arrendatario. [NOTA DE REVISIÓN (comprobar): Art. 20.2 LAU (RDL 29/2026): no pueden repercutirse al arrendatario los gastos de gestión inmobiliaria y de formalización del contrato; es dudoso que la inscripción registral quede fuera de ese concepto: revisar el pacto. Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, art. 20.2 (redacción RDL 29/2026, BOE-A-2026-20823 (convalidado: BOE-A-2026-23755)).]

Y para que conste y surta los efectos oportunos, firman arrendador y arrendatario el presente contrato que consta de [COMPLETAR] folios, y que suscriben en cada hoja de los dos ejemplares iguales que se otorgan mutuamente, en el lugar y fecha del encabezamiento.

Fdo.: D./Dña. [NOMBRE Y APELLIDOS] Fdo.: D./Dña. [NOMBRE Y APELLIDOS]

========================================================================
