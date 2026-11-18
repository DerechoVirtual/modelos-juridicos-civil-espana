---
name: arrendamiento-vivienda-adaptado-ley-12-2023-derecho-1447
description: "Redacta el escrito «Arrendamiento de vivienda adaptado a la Ley 12/2023 por el derecho a la vivienda» (formulario 1447 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Arrendamiento de vivienda adaptado a la Ley 12/2023 por el derecho a la vivienda

> Formulario 1447 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

- Ya adaptado en parte (nota del RDL 29/2026); revisar además renta (IRAV y DF 6.ª), gastos e IBI (art. 20), adquisición preferente irrenunciable (25.8) y prórroga tácita (art. 10).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] NACIONALIDAD (2 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] DNI/NIE (4 veces)
- [ ] NÚMERO
- [ ] FECHA (2 veces)
- [ ] IMPORTE (3 veces)
- [ ] Nº
- [ ] LUGAR
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…y 12/2023. Adaptado a la Ley 12/2023. En»; «…, con una superficie de»; «…scrita en el Registro de la Propiedad de»; «…en el»; «…vigente en los últimos cinco años fue de»; «…e viviendas que resulta de aplicación es»; «…ivienda arrendada cuyo precio se fija en»; «… plaza de aparcamiento arrendados es del»; «…e resolverán a través de la Mediación de»; «…ecida en la Ley 5/2012, de 6 de julio, y»; «…suelta mediante Arbitraje de la Corte de»; «…s árbitros, de acuerdo con su reglamento»; …

## Elecciones que hay que hacer

- soltero / soltera / casado / casada / divorciado / divorciada / separado / separada / viudo / viuda
- gananciales / separación de bienes
- propietaria / usufructuaria
- metálico / lo que se pacte

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Seleccionar en caso de que todas las partes actúen en nombre y representación propia / Seleccionar si alguna de las partes actúa en su propio nombre y representación — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Si se trata de persona física / Si se trata de una persona jurídica — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de vivienda amueblada / En caso de vivienda no amueblada — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Con puesta a disposición y entrega de llaves / Puesta a disposición posterior — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de que la renta se revise conforme a lo pactado / (Si la renta se revisa conforme a índices/IPC) [NOTA DE REVISIÓN: Art. 18 LAU vigente: solo hay actualización si se pacta; el incremento anual no puede exceder de la variación del IRAV y la renta actualizada es exigible desde el mes siguiente a la notificación escrita (art. 18.2; vale la nota en el recibo). P
- ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de pactar no elevar la renta si se realizan obras de mejora / Si se pacta elevar la renta si se realizan obras de mejora — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de no incluir los gastos generales en la renta / En caso de incluir los gastos generales en la renta — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de contrato inferior a 5 años / En caso de pactar una duración diferente del contrato / En caso de contrato superior a 5 años e inferior a 7 años / En caso de inmueble ubicado en una zona de mercado residencial tensionado — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Si se nombra avalista o fiador sin poder ante notario / Si se nombra avalista o fiador ante notario — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Si se permite subarrendar la vivienda / En caso de que no se permita subarrendar la vivienda — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: (En caso de que no se pacte el derecho de adquisición preferente) [NOTA DE REVISIÓN: Art. 25.8 LAU (RDL 29/2026): las partes no pueden pactar la renuncia del arrendatario de vivienda al derecho de adquisición preferente; esta opción solo sirve para contratos anteriores al 8-10-2026. Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, art. 25.8 (redacción RDL 29/2026, BOE-A
- ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de que se excluya el derecho de subrogación / En caso de que se pacte el derecho de subrogación — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Si se pacta la resolución del contrato por falta de pago de renta y la restitución inmediata del inmueble al arrendador / En caso de que no se pacte la resolución por falta de pago de renta — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de que se pacte indemnización al arrendador por desistimiento del arrendatario / En caso de que no se pacte indemnización al arrendador por desistimiento del arrendatario — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: (A cargo de la arrendataria) [NOTA DE REVISIÓN: Art. 20.1-2 LAU (RDL 29/2026): no pueden imponerse al arrendatario los tributos asociados a la vivienda (salvo que sea obligado tributario, p. ej. ITP del arrendamiento) ni los gastos de gestión inmobiliaria y de formalización del contrato. Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, art. 20.1-2 (redacción RDL 29/2026

## Párrafos opcionales (7)

Inclúyelos solo si encajan en los hechos:

- Casado…
- (Seleccionar en caso de estado civil casado/a)…
- (Seleccionar si alguna de las partes actúa en nombre y representación de persona física o jurídica)…
- Cuando la vivienda que vaya a ser objeto de arrendamiento como vivienda habitual se encuentre ubicada en una z…
- (Si se pacta el derecho de opción de compra)…
- (Si se pacta el pago por el arrendatario de gastos de comunidad y otros)…
- (Si se pacta por las partes que, durante un plazo determinado, la obligación del pago de la renta sea reemplaz…

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 31 de la Ley 12/2023
- artículo 4.6 LAU
- Ley 29/1994
- Ley 5/2012
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

### Formulario 1447 · Arrendamiento de vivienda adaptado a la Ley 12/2023 por el derecho a la vivienda

- Año del modelo: 2014
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 4 puntualizaciones normativas añadidas en el texto; saltos de párrafo recuperados (texto venía pegado); restos de formato retirados; notas del formulario agrupadas al final (1); 6 desplegables convertidos en elección en blanco; 15 bloques de opciones sin texto dejados en blanco con sus rótulos; 7 párrafos opcionales señalados; 35 campos de relleno marcados en blanco
- Avisos de la revisión: Ya adaptado en parte (nota del RDL 29/2026); revisar además renta (IRAV y DF 6.ª), gastos e IBI (art. 20), adquisición preferente irrenunciable (25.8) y prórroga tácita (art. 10).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

REUNIDOS
INTERVIENEN
EXPONEN
CLÁUSULAS
Firmas
Anexo

Modelo de contrato locativo de arrendamiento de finca urbana para uso de vivienda, contemplando las distintas opciones legales para arrendatario y arrendador. Adaptado a la Ley 12/2023.

Adaptado a la Ley 12/2023.

En [COMPLETAR]

REUNIDOS

DE UNA PARTE,

-
+
Añadir más párrafos iguales
(Datos de EL/LA ARRENDADOR/A)

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, de estado civil [ELEGIR: soltero / soltera / casado / casada / divorciado / divorciada / separado / separada / viudo / viuda], de nacionalidad [NACIONALIDAD], con domicilio en [LOCALIDAD], y DNI/Pasaporte número [DNI/NIE].

[OPCIONAL — incluir si procede]

Casado
Casada
 con D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con DNI/Pasaporte número [DNI/NIE] en régimen económico matrimonial de [ELEGIR: gananciales / separación de bienes].

En lo sucesivo, EL/LA ARRENDADOR/A.

Y DE OTRA,

-
+
Añadir más párrafos iguales
(Datos de EL/LA ARRENDATARIO/A)

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, de estado civil [ELEGIR: soltero / soltera / casado / casada / divorciado / divorciada / separado / separada / viudo / viuda], de nacionalidad [NACIONALIDAD], con domicilio en [LOCALIDAD], y DNI/Pasaporte número [DNI/NIE].

[OPCIONAL — incluir si procede]

(Seleccionar en caso de estado civil casado/a)

Casado
Casada
 con D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con DNI/Pasaporte número [DNI/NIE] en régimen económico matrimonial de [ELEGIR: gananciales / separación de bienes].

En lo sucesivo, EL/LA ARRENDATARIO/A.

INTERVIENEN

[ELEGIR UNA OPCIÓN Y REDACTARLA: Seleccionar en caso de que todas las partes actúen en nombre y representación propia / Seleccionar si alguna de las partes actúa en su propio nombre y representación — el texto de cada opción no venía en el formulario original]

[OPCIONAL — incluir si procede]

(Seleccionar si alguna de las partes actúa en nombre y representación de persona física o jurídica)
-
+
Añadir más párrafos iguales

D./Dña. [NOMBRE Y APELLIDOS], en nombre y representación de:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Si se trata de persona física / Si se trata de una persona jurídica — el texto de cada opción no venía en el formulario original]

Ambas partes se reconocen mutuamente con capacidad suficiente para otorgar el presente contrato de ARRENDAMIENTO DE VIVIENDA y, a tal fin,

EXPONEN

PRIMERO.- Que EL/LA ARRENDADOR/A es [ELEGIR: propietaria / usufructuaria] de la vivienda sita en [LOCALIDAD], con una superficie de [COMPLETAR] metros cuadrados, constando inscrita en el Registro de la Propiedad de [COMPLETAR] en el [COMPLETAR] e inscripción número [NÚMERO].

Que la mencionada vivienda se encuentra libre de cargas y gravámenes y al corriente en el pago de impuestos.

[OPCIONAL — incluir si procede]

Cuando la vivienda que vaya a ser objeto de arrendamiento como vivienda habitual se encuentre ubicada en una zona de mercado residencial tensionado

A los efectos de dar cumplimiento a la Ley 12/2023 de Vivienda se indica lo siguiente:

1º Que la última renta del contrato de arrendamiento de vivienda habitual que ha estado vigente en los últimos cinco años fue de [COMPLETAR], suscrito mediante contrato de fecha [FECHA].
2º Que el valor que le corresponde a la vivienda, atendiendo al índice de referencia de precios de alquiler de viviendas que resulta de aplicación es [COMPLETAR].

SEGUNDO.- Que LA ARRENDATARIA solicita se le arriende el mencionado inmueble, en virtud de lo establecido en la Ley 29/1994, de 24 de noviembre, de Arrendamientos Urbanos (en lo sucesivo, LAU), a lo que accede EL/LA ARRENDADOR/A y lo llevan a efecto de conformidad con las siguientes:

CLÁUSULAS

I.- OBJETO DEL CONTRATO

[ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de vivienda amueblada / En caso de vivienda no amueblada — el texto de cada opción no venía en el formulario original]

II.- ENTREGA

[ELEGIR UNA OPCIÓN Y REDACTARLA: Con puesta a disposición y entrega de llaves / Puesta a disposición posterior — el texto de cada opción no venía en el formulario original]

III.- RENTA

El precio de este arrendamiento se fija en la cantidad de [IMPORTE] euros mensuales, que serán abonados de la forma siguiente:

a) Fecha:
b) Lugar: El abono de la renta se deberá verificar por LA ARRENDATARIA mediante transferencia bancaria [NOTA DE REVISIÓN: Errata: quien paga la renta es la arrendataria. Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, art. 17.], a la cuenta del arrendador cuyos datos son los siguientes:

El resguardo de ingreso emitido por la entidad bancaria acreditará el pago de la renta salvo prueba en contrario.

El precio establecido en el presente contrato no incluye los impuestos indirectos que según la legislación fueren aplicables.

IV.- ACTUALIZACIÓN DE LA RENTA

[ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de que la renta se revise conforme a lo pactado / (Si la renta se revisa conforme a índices/IPC) [NOTA DE REVISIÓN: Art. 18 LAU vigente: solo hay actualización si se pacta; el incremento anual no puede exceder de la variación del IRAV y la renta actualizada es exigible desde el mes siguiente a la notificación escrita (art. 18.2; vale la nota en el recibo). Para las anualidades que se cumplan entre el 8-10-2026 y el 31-12-2027, DF 6.ª RDL 29/2026: sin incremento si la renta supera el límite del sistema de índices de referencia; en otro caso, lo que se pacte de nuevo y, a falta de pacto, máximo 2 %. Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, art. 18 (redacción RDL 29/2026, BOE-A-2026-20823 (convalidado: BOE-A-2026-23755)); RDL 29/2026, DF 6.ª.] — el texto de cada opción no venía en el formulario original]

Publicado el índice correspondiente al mes de la actualización, EL/LA ARRENDADOR/A comunicará a LA ARRENDATARIA de forma fehaciente su voluntad de actualizar la renta conforme a lo establecido legalmente, expresando la cantidad en que se fija la renta revisada, y adjuntando certificación del Instituto Nacional de Estadística.

La base sobre la que se efectuará la citada revisión será la renta que se pague el mes inmediatamente anterior a la fecha de revisión.

V.- ELEVACIÓN DE RENTA POR MEJORAS

[ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de pactar no elevar la renta si se realizan obras de mejora / Si se pacta elevar la renta si se realizan obras de mejora — el texto de cada opción no venía en el formulario original]

VI.- GASTOS GENERALES

[ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de no incluir los gastos generales en la renta / En caso de incluir los gastos generales en la renta — el texto de cada opción no venía en el formulario original]

Los gastos por servicios con que cuente la finca arrendada que se individualicen mediante aparatos contadores serán en todo caso de cuenta de LA ARRENDATARIA.

VII.- DURACIÓN DEL CONTRATO

[ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de contrato inferior a 5 años / En caso de pactar una duración diferente del contrato / En caso de contrato superior a 5 años e inferior a 7 años / En caso de inmueble ubicado en una zona de mercado residencial tensionado — el texto de cada opción no venía en el formulario original]

VIII.- AVALISTA/FIADOR

[ELEGIR UNA OPCIÓN Y REDACTARLA: Si se nombra avalista o fiador sin poder ante notario / Si se nombra avalista o fiador ante notario — el texto de cada opción no venía en el formulario original]

IX.- CONSERVACIÓN Y OBRAS

LA ARRENDATARIA recibe la finca en buen estado de conservación, y se compromete a devolverla, al concluir el contrato, en el mismo estado.

EL/LA ARRENDADOR/A está obligada a realizar, sin derecho a elevar por ello la renta, todas las reparaciones que sean necesarias para conservar la finca en condiciones adecuadas para servir al uso de vivienda convenido, salvo cuando el deterioro de cuya reparación se trate sea imputable a LA ARRENDATARIA o a las personas que con ella convivan.

LA ARRENDATARIA debe poner en conocimiento de EL/LA ARRENDADOR/A, en el plazo más breve posible, la necesidad de las reparaciones que sean necesarias para conservar la finca en condiciones adecuadas para servir al uso de vivienda convenido, a cuyos solos efectos debe facilitar a EL/LA ARRENDADOR/A la verificación directa, por sí mismo o por los técnicos que designe, del estado de la finca.

En todo momento, y previa comunicación a EL/LA ARRENDADOR/A, LA ARRENDATARIA puede realizar las reparaciones que sean urgentes para evitar un daño inminente o una incomodidad grave, y exigir de inmediato su importe a EL/LA ARRENDADOR/A.

Las pequeñas reparaciones que exija el desgaste por el uso ordinario de la finca serán de cargo de LA ARRENDATARIA.

LA ARRENDATARIA no podrá realizar sin el consentimiento de EL/LA ARRENDADOR/A expresado por escrito, obras que modifiquen la configuración de la finca destinada a vivienda, o que provoquen una disminución en la estabilidad o seguridad de la misma.

LA ARRENDATARIA está obligada a soportar la realización por EL/LA ARRENDADOR/A de obras de mejora cuya ejecución no pueda razonablemente diferirse hasta la conclusión del contrato, sin perjuicio del derecho que, en su caso, la parte arrendataria pueda tener a desistir del contrato, o a una reducción de la renta y una indemnización de los gastos que se le causen.

X.- FIANZA

En este acto, LA ARRENDATARIA entrega a EL/LA ARRENDADOR/A, la cantidad de [IMPORTE] euros, importe igual a una mensualidad de renta, en concepto de fianza y garantía adicional, que será restituida, en su integridad o disminuirá en la cantidad que sea necesaria en caso de daños a la finalización de este contrato, estando obligada EL/LA ARRENDADOR/A a hacer efectivo su depósito legal conforme a la Ley que lo regula.

La existencia de esta fianza, no será obstáculo para que EL/LA ARRENDADOR/A pueda instar el desahucio por falta de pago, ni facultará a LA ARRENDATARIA al impago de alguna mensualidad de renta. La fianza no devengará interés a favor de LA ARRENDATARIA, quedando facultada EL/LA ARRENDADOR/A para practicar la liquidación hacedera según los perjuicios que hubieren causado.

XI.- CESIÓN Y SUBARRIENDO

[ELEGIR UNA OPCIÓN Y REDACTARLA: Si se permite subarrendar la vivienda / En caso de que no se permita subarrendar la vivienda — el texto de cada opción no venía en el formulario original]

XII.- DERECHO DE ADQUISICIÓN PREFERENTE

[ELEGIR UNA OPCIÓN Y REDACTARLA: (En caso de que no se pacte el derecho de adquisición preferente) [NOTA DE REVISIÓN: Art. 25.8 LAU (RDL 29/2026): las partes no pueden pactar la renuncia del arrendatario de vivienda al derecho de adquisición preferente; esta opción solo sirve para contratos anteriores al 8-10-2026. Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, art. 25.8 (redacción RDL 29/2026, BOE-A-2026-20823 (convalidado: BOE-A-2026-23755)).] / En caso de que se pacte el derecho de adquisición preferente — el texto de cada opción no venía en el formulario original]

XIII.- SUBROGACIÓN POR FALLECIMIENTO DEL ARRENDATARIO

[ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de que se excluya el derecho de subrogación / En caso de que se pacte el derecho de subrogación — el texto de cada opción no venía en el formulario original]

XIV.- RESOLUCIÓN DEL CONTRATO

[ELEGIR UNA OPCIÓN Y REDACTARLA: Si se pacta la resolución del contrato por falta de pago de renta y la restitución inmediata del inmueble al arrendador / En caso de que no se pacte la resolución por falta de pago de renta — el texto de cada opción no venía en el formulario original]

XV.- PACTO DE INDEMNIZACIÓN POR DESISTIMIENTO DEL ARRENDATARIO (1)

[ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de que se pacte indemnización al arrendador por desistimiento del arrendatario / En caso de que no se pacte indemnización al arrendador por desistimiento del arrendatario — el texto de cada opción no venía en el formulario original]

XVI.- CLÁUSULA ADICIONAL DE OPCIÓN DE COMPRA

[OPCIONAL — incluir si procede]

(Si se pacta el derecho de opción de compra)

Se concede gratuitamente por EL/LA ARRENDADOR/A a LA ARRENDATARIA, durante la vigencia del presente contrato, un derecho de opción de compra sobre la vivienda arrendada cuyo precio se fija en [COMPLETAR], de las que se deducirán las cantidades abonadas en concepto de renta por LA ARRENDATARIA hasta el momento en que se haga uso del derecho de opción de compra. El precio se abonará en [ELEGIR: metálico / lo que se pacte] en el momento de hacerse uso de la opción. La finca se transmitirá libre de cargas y al corriente en el pago de impuestos.

XVII.- CLÁUSULA ADICIONAL DE PAGO POR EL ARRENDATARIO DE GASTOS DE COMUNIDAD Y OTROS

[OPCIONAL — incluir si procede]

(Si se pacta el pago por el arrendatario de gastos de comunidad y otros)

En particular, se estipula que el arrendatario viene obligado también al pago de los gastos de la Comunidad de Propietarios de la vivienda y de la plaza de aparcamiento, en la cuantía que en cada momento se establezca [NOTA DE REVISIÓN: Art. 20.1 y 20.3 LAU: el pacto debe fijar el importe anual de los gastos y, durante los 5 primeros años (7 si persona jurídica), solo pueden subir anualmente y nunca más del doble de lo que pueda subir la renta según el art. 18.1. Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, art. 20.1 y 20.3 (redacción RDL 29/2026, BOE-A-2026-20823 (convalidado: BOE-A-2026-23755)).]. A los indicados efectos, se hace constar que la cuota de participación en gastos comunes que corresponde a la vivienda y plaza de aparcamiento arrendados es del [COMPLETAR] y que en la actualidad los mencionados gastos ascienden a la cantidad de [IMPORTE] euros trimestrales, sin perjuicio de su aumento o disminución por acuerdo de la Junta de Propietarios. Las variaciones que se pudieran producir en lo sucesivo serán debidamente notificadas al arrendatario.

XVIII.- CLÁUSULA ADICIONAL DE PAGO DE LA RENTA MEDIANTE OBLIGACIÓN DE HACER

[OPCIONAL — incluir si procede]

(Si se pacta por las partes que, durante un plazo determinado, la obligación del pago de la renta sea reemplazada total o parcialmente por el compromiso del arrendatario de reformar o rehabilitar el inmueble)

Las partes acuerdan que durante un período de [Nº] meses, la obligación del arrendatario de pagar la renta quedará sustituida por la obligación de reformar (o rehabilitar) la vivienda, en los términos siguientes:

XIX.- INFORMACIÓN AL ARRENDATARIO

Ambas partes convienen en que el arrendador ha cumplido con los deberes de información, en formato accesible y en soporte duradero, acerca de las condiciones de la operación y de las características de la vivienda y del edificio en el que se encuentra, tal y como establece el art. 31 de la Ley 12/2023, de 24 de mayo, por el derecho a la vivienda.

.- GASTOS E IMPUESTOS

[ELEGIR UNA OPCIÓN Y REDACTARLA: (A cargo de la arrendataria) [NOTA DE REVISIÓN: Art. 20.1-2 LAU (RDL 29/2026): no pueden imponerse al arrendatario los tributos asociados a la vivienda (salvo que sea obligado tributario, p. ej. ITP del arrendamiento) ni los gastos de gestión inmobiliaria y de formalización del contrato. Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, art. 20.1-2 (redacción RDL 29/2026, BOE-A-2026-20823 (convalidado: BOE-A-2026-23755)).] / A cargo del arrendador — el texto de cada opción no venía en el formulario original]

.- SUMISIÓN A MEDIACIÓN Y/O ARBITRAJE; JURISDICCIÓN COMPETENTE Y LEY APLICABLE

Las partes contratantes acuerdan libre y voluntariamente que todas las desavenencias, divergencias o cuestiones litigiosas que deriven de este contrato, incluso cuando la controversia verse sobre la validez o existencia del presente contrato, se resolverán a través de la Mediación de [COMPLETAR], antes de acudir a la jurisdicción o a otra solución extrajudicial de conflictos, sometiéndose a la regulación establecida en la Ley 5/2012, de 6 de julio, y [COMPLETAR] fijando un plazo máximo de duración del procedimiento de sesenta días desde la solicitud de iniciación por cualquiera de las partes.

A falta de resolución de la controversia en el procedimiento de mediación, la misma será definitivamente resuelta mediante Arbitraje de la Corte de [COMPLETAR], a la que se encomienda la administración del arbitraje y la designación de los árbitros, de acuerdo con su reglamento [COMPLETAR].

La competencia para conocer de toda controversia relacionada con el presente contrato corresponderá al Juez de Primera Instancia del lugar donde está sita la vivienda arrendada.

Los gastos judiciales que se ocasionen por incumplimiento del presente contrato serán por cuenta de la parte incumplidora, incluidos honorarios del Procurador y Abogado aunque sus intervenciones no fueran preceptivas.

El presente contrato tiene carácter civil, se regirá por sus propias cláusulas, y en lo en ellas no dispuesto, por lo previsto en la Ley de Arrendamientos Urbanos de 24 de noviembre de 1.994.

.- NOTIFICACIONES

Todas las notificaciones, requerimientos, peticiones y otras comunicaciones que hayan de efectuarse las partes en relación con el presente contrato, deberán realizarse por escrito, fijándose como domicilio de EL/LA ARRENDADOR/A el señalado en el encabezamiento del presente contrato, y como domicilio de LA ARRENDATARIA el correspondiente a la vivienda arrendada.

De conformidad a lo dispuesto en el artículo 4.6 LAU 1994, las partes designan las siguientes direcciones electrónicas para realizar las notificaciones:

- Por EL/LA ARRENDADOR/A [COMPLETAR]
- Por LA ARRENDATARIA [COMPLETAR]

Cualquier cambio de domicilio de una de las partes deberá ser notificado a la otra de forma inmediata y por un medio que garantice la recepción del mensaje.

.- INSCRIPCIÓN EL EN REGISTRO

Cualquiera de las partes podrá solicitar la inscripción del presente arrendamiento en el Registro de la Propiedad, gasto que correrá a cargo del que lo solicite.

.- CERTIFICADO DE EFICIENCIA ENERGÉTICA

En cumplimiento de lo dispuesto en el Real Decreto 390/2021, de 1 de junio, por el que se aprueba el procedimiento básico para la certificación de la eficiencia energética de los edificios, se pone a disposición del arrendatario en este acto el certificado de eficiencia energética, emitido por técnico competente.

Y leído el presente documento, ambas partes lo firman en señal de conformidad y ratificación de su contenido, haciéndolo por duplicado y a un solo efecto.

En [LUGAR], a [FECHA].

Firma de EL/LA ARRENDADOR/A:	Firma de LA ARRENDATARIA

DESCRIPCIÓN DE LOS BIENES MUEBLES

NOTAS DEL FORMULARIO

(1) Desde la reforma operada por RDL 29/2026, aplicable a los contratos celebrados a partir del 8 de octubre de 2026, ya no se permite pactar ninguna indemnización en favor del arrendador.

========================================================================
