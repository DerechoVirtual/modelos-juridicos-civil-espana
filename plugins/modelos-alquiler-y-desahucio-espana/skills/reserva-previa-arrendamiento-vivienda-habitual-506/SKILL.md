---
name: reserva-previa-arrendamiento-vivienda-habitual-506
description: "Redacta el escrito «Reserva previa al arrendamiento de vivienda habitual» (formulario 506 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reserva previa al arrendamiento de vivienda habitual

> Formulario 0506 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (9 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] CALLE (3 veces)
- [ ] NÚMERO (3 veces)
- [ ] DNI/NIE (2 veces)
- [ ] CORREO ELECTRÓNICO (2 veces)
- [ ] IMPORTE (3 veces)
- [ ] Nº
- [ ] PLAZO
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, C/ [CALLE], n.º [NÚMERO], piso»; «…, C/ [CALLE], n.º [NÚMERO], piso»; «…, en la C/ [CALLE], n.º [NÚMERO], piso»; «… piso [COMPLETAR] Tal vivienda consta de»; «…, mediante contrato suscrito el»; «… certificado de eficiencia energética de»; «…artes el presente contrato que consta de»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Real Decreto 390/2021

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

### Formulario 0506 · Reserva previa al arrendamiento de vivienda habitual

- Año del modelo: 2017
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 33 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (IMPORTE)
- Avisos de la revisión: Contrato de 2013-2016: revisar contra la LAU vigente (RDL 29/2026, desde 8-10-2026): duración 5/7 años y prórroga tácita de 3 (arts. 9-10), actualización con tope IRAV y DF 6.ª (2 % hasta 31-12-2027), pago electrónico (17.3), gastos e IBI (20), sin indemnización por desistimiento (11.3), adquisición preferente irrenunciable (25.8) y garantía adicional ≤ 2 meses sin seguro de impago (36.5).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [DÍA] de [MES] de [AÑO].

REUNIDOS

De una parte: D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD], C/ [CALLE], n.º [NÚMERO], piso [COMPLETAR] y DNI n.º [DNI/NIE], y correo electrónico [CORREO ELECTRÓNICO].

De otra parte: D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD], C/ [CALLE], n.º [NÚMERO], piso [COMPLETAR] y DNI n.º [DNI/NIE], y correo electrónico [CORREO ELECTRÓNICO].

COMPARECEN

Ambas partes en su propio, nombre e interés, reconociéndose la capacidad de obrar necesaria para el otorgamiento del presente contrato RESERVA PREVIA A CONTRATO DE ARRENDAMIENTO DE VIVIENDA HABITUAL, tras lo cual,

MANIFIESTAN

I.- Que D./Dña. [NOMBRE Y APELLIDOS] es propietario/a de la finca urbana sita en [LOCALIDAD], en la C/ [CALLE], n.º [NÚMERO], piso [COMPLETAR]

Tal vivienda consta de [COMPLETAR].

II.- Que la referida vivienda se encuentra arrendada en la actualidad a D./Dña. [NOMBRE Y APELLIDOS], mediante contrato suscrito el [COMPLETAR], finalizando el mismo el día

III.- Que D./Dña. [NOMBRE Y APELLIDOS] desea arrendar el inmueble descrito en el punto anterior para su uso como vivienda, una vez haya finalizado el arrendamiento vigente.

Por lo que llevan a efecto la suscripción de este contrato de reserva, con sometimiento a las siguientes:

CLAUSULAS

PRIMERA: D./Dña. entrega en este acto a D./Dña. [NOMBRE Y APELLIDOS] la cantidad de [IMPORTE] Euros, en concepto de pago y señal para la reserva previa al contrato de arrendamiento que se otorgará sobre la vivienda anteriormente identificada. La firma del presente documento sirve como prueba de su recibo y más eficaz carta de pago.

SEGUNDA: Una vez finalizado el arrendamiento a que se hace referencia en el expositivo II, ambas partes suscribirán, en el plazo máximo de un mes desde dicha fecha, un contrato de arrendamiento sobre el indicado inmueble.

Las condiciones por las que se regirá el contrato de arrendamiento, serán las siguientes:

a) Precio: [IMPORTE] euros anuales, pagaderos en 12 mensualidades, dentro de los [Nº] días primeros de cada mes, en la cuenta que el arrendador designe. Esta renta será actualizada anualmente, previa notificación por escrito, conforme a la variación del IPC de la anualidad inmediatamente anterior, sin que el incremento pueda exceder de la variación del Índice de Referencia para la Actualización Anual de los Contratos de Arrendamiento de Vivienda (IRAV) [NOTA DE REVISIÓN: Art. 18 LAU vigente: solo hay actualización si se pacta; el incremento anual no puede exceder de la variación del IRAV y la renta actualizada es exigible desde el mes siguiente a la notificación escrita (art. 18.2; vale la nota en el recibo). Para las anualidades que se cumplan entre el 8-10-2026 y el 31-12-2027, DF 6.ª RDL 29/2026: sin incremento si la renta supera el límite del sistema de índices de referencia; en otro caso, lo que se pacte de nuevo y, a falta de pacto, máximo 2 %. Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, art. 18 (redacción RDL 29/2026, BOE-A-2026-20823 (convalidado: BOE-A-2026-23755)); RDL 29/2026, DF 6.ª.]

b) Duración: Años

c) Uso: vivienda habitual de D./Dña. [NOMBRE Y APELLIDOS]

d) Gastos: Correrán por cuenta del arrendatario los gastos generales y de servicios individuales tales como luz, teléfono y agua. Asimismo deberá abonar la cuota de comunidad de propietarios, cuyo importe anual a la fecha del contrato asciende a [IMPORTE] euros. El impuesto sobre bienes inmuebles será a cargo del arrendador. [NOTA DE REVISIÓN: Art. 20.1 LAU (RDL 29/2026, vigente desde el 8-10-2026): el pacto de gastos generales debe constar por escrito con su importe anual y no pueden imponerse al arrendatario los tributos asociados a la vivienda (salvo que sea obligado tributario). En contratos anteriores al 8-10-2026 rige lo pactado conforme a la redacción vigente al celebrarse (el RDL no fija régimen transitorio expreso). Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, art. 20.1 (redacción RDL 29/2026, BOE-A-2026-20823 (convalidado: BOE-A-2026-23755)).]

e) Fianza: se entregará una fianza equivalente a una mensualidad de renta. La cantidad que hoy se entrega en concepto de reserva, se imputará al pago de esta fianza, y será devuelta al finalizar el arriendo si se dan las circunstancias que a tal efecto prevé la Ley de Arrendamientos Urbanos.

f) En lo no expresamente previsto el contrato se regirá por lo establecido en la Ley de Arrendamientos Urbanos

Asimismo, en el momento de otorgamiento, la arrendadora entregará a la arrendataria el certificado de eficiencia energética de [COMPLETAR], según el Real Decreto 390/2021, de 1 de junio, por el que se aprueba el procedimiento básico para la certificación de eficiencia energética de edificios

TERCERA: La propietaria del inmueble se obliga a no arrendarlo a ninguna otra persona.

Para el caso de incumplimiento de la prestación objeto del presente contrato, la parte cumplidora podrá exigir a la incumplidora, el cumplimiento del contrato u optar por su resolución. En este último supuesto, si la cumplidora es la futura arrendadora, tendrá derecho a hacer suya la cantidad entregada en concepto de señal y si la cumplidora es la futura arrendataria, tendrá derecho a recibir duplicada la cantidad entregada en concepto de señal.

Se considerará incumplido el contrato si, una vez requerida fehacientemente una de las partes, no se aviene a suscribir el contrato de arrendamiento en el plazo de [PLAZO] desde la recepción del requerimiento.

Y para que conste y surta los efectos oportunos, firman las partes el presente contrato que consta de [COMPLETAR] folios, y que suscriben en cada hoja de los dos ejemplares iguales que se otorgan mutuamente, en el lugar y fecha del encabezamiento.

Fdo.: D./Dña. [NOMBRE Y APELLIDOS] Fdo.: D./Dña. [NOMBRE Y APELLIDOS]

========================================================================
