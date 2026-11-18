---
name: arrendamiento-vivienda-comunidad-propietarios-1210
description: "Redacta el escrito «Arrendamiento de vivienda por comunidad de propietarios» (formulario 1210 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Arrendamiento de vivienda por comunidad de propietarios

> Formulario 1210 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] Nº (4 veces)
- [ ] FECHA DE LA JUNTA
- [ ] CALLE
- [ ] CORREO ELECTRÓNICO
- [ ] IMPORTE (3 veces)
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…n.º [Nº] de»; «…legal arrendar esta vivienda autorizando»; «…ifra que esté en cada anualidad en vigor»; «… servicios y suministros de la vivienda.»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 1210 · Arrendamiento de vivienda por comunidad de propietarios

- Año del modelo: 2013
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 12 campos de relleno marcados en blanco; 5 huecos del original que se habían perdido sin marca, marcados (FECHA DE LA JUNTA, IMPORTE, Nº)
- Avisos de la revisión: Contrato de 2013-2016: revisar contra la LAU vigente (RDL 29/2026, desde 8-10-2026): duración 5/7 años y prórroga tácita de 3 (arts. 9-10), actualización con tope IRAV y DF 6.ª (2 % hasta 31-12-2027), pago electrónico (17.3), gastos e IBI (20), sin indemnización por desistimiento (11.3), adquisición preferente irrenunciable (25.8) y garantía adicional ≤ 2 meses sin seguro de impago (36.5).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [DÍA] de [MES] de [AÑO].

EXPONEN

Que D./Dña. [NOMBRE Y APELLIDOS] actúa en nombre y representación de la Comunidad de Propietarios de la C/ n.º [Nº] de de la que es, según acuerdo adoptado en Junta General de fecha [FECHA DE LA JUNTA].

Que la finca objeto de arrendamiento pertenece en proindiviso y por partes equivalentes a la cuota de participación de cada comunero a los propietarios de los distintos elementos del inmueble de la C/ [CALLE] n.º [Nº] de [COMPLETAR], según consta en la escritura de compraventa de cada uno de ellos y en la escritura de división horizontal de la finca.

Que en Junta General celebrada el día se ha acordado por mayoría legal arrendar esta vivienda autorizando [COMPLETAR] para que en nombre de la Comunidad suscriba el presente contrato, y que designan como dirección de correo electrónico, para las comunicaciones con el arrendatario, la de su administrador

Que D./Dña. [NOMBRE Y APELLIDOS] comparece en nombre propio, así como la dirección de correo electrónico [CORREO ELECTRÓNICO] para las comunicaciones con el arrendador.

Que ambas partes se reconocen mutuamente la capacidad legal necesaria para otorgar el presente contrato de arrendamiento con arreglo a las siguientes

CLÁUSULAS

La Comunidad de Propietarios de n.º [Nº] de cede en arrendamiento la vivienda descrita libre de cargas y ocupantes.

La vivienda consta de.

El arrendatario utilizará el inmueble exclusivamente como vivienda y en este momento declara conocer su uso, extensión, características, estado de conservación y servicios comunes y privados. Igualmente declara conocer y aceptar las disposiciones de los estatutos de la Comunidad de Propietarios en lo que se refiere a actividades prohibidas en el inmueble. El incumplimiento de estas limitaciones permitiría a la Comunidad resolver este contrato.

El arrendatario se obliga a dar un uso adecuado a la vivienda y a conservarla en buen estado, realizando al efecto las reparaciones necesarias derivadas del desgaste por uso ordinario de la vivienda.

El arrendador está obligado a realizar el resto de las obras necesarias para conservar la vivienda en condiciones de habitabilidad.

El presente contrato tendrá una duración de años a contar desde su firma.

Llegado el término del contrato, si la duración pactada fuera inferior a cinco años (o a siete si el arrendador fuese persona jurídica), llegado el vencimiento el contrato se prorrogará obligatoriamente por plazos anuales hasta alcanzar dicha duración mínima, salvo que el arrendatario manifieste con treinta días de antelación su voluntad de no renovarlo. Transcurrida esa duración mínima, si ninguna de las partes notifica a la otra su voluntad de no renovarlo, con al menos cuatro meses de antelación el arrendador o dos meses el arrendatario, el contrato se prorrogará por plazos anuales hasta un máximo de tres años más. [NOTA DE REVISIÓN: Arts. 9.1 y 10.1 LAU (imperativos, contratos desde el 6-3-2019, DT 1.ª RDL 7/2019): prórroga obligatoria anual hasta 5 años (7 si el arrendador es persona jurídica) y, después, prórroga tácita anual hasta 3 años más salvo preaviso de 4 meses (arrendador) o 2 meses (arrendatario). El preaviso de 30 días/un mes con prórroga anual es la redacción de 2013. Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, arts. 9.1 y 10.1; RDL 7/2019 DT 1.ª, BOE-A-2019-3108.]

Finalizada la duración pactada y, en su caso, las prórrogas, el arrendatario deberá dejar el inmueble en buen estado de uso, sin perjuicio del desgaste ordinario que haya sufrido por el transcurso del tiempo.

La renta se fija en [IMPORTE] euros anuales. El arrendatario abonará cada mes al arrendador en concepto de renta la cantidad de [IMPORTE] euros. El pago se realizará por anticipado dentro de los cinco primeros días de cada mes mediante ingreso en la cuenta corriente que la Comunidad de Propietarios de la C/ n.º tiene abierta a su nombre en la entidad con n.º [Nº]. El justificante de ingreso que emita la entidad bancaria servirá a todos los efectos como recibo.

La renta será objeto de actualización al cumplimiento de cada anualidad del contrato, previa notificación por escrito al arrendatario, [NOTA DE REVISIÓN: Art. 18 LAU vigente: solo hay actualización si se pacta; el incremento anual no puede exceder de la variación del IRAV y la renta actualizada es exigible desde el mes siguiente a la notificación escrita (art. 18.2; vale la nota en el recibo). Para las anualidades que se cumplan entre el 8-10-2026 y el 31-12-2027, DF 6.ª RDL 29/2026: sin incremento si la renta supera el límite del sistema de índices de referencia; en otro caso, lo que se pacte de nuevo y, a falta de pacto, máximo 2 %. Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, art. 18 (redacción RDL 29/2026, BOE-A-2026-20823 (convalidado: BOE-A-2026-23755)); RDL 29/2026, DF 6.ª.] aplicando a la cifra que esté en cada anualidad en vigor [COMPLETAR].

Correrán por cuenta del arrendatario todos los gastos por servicios y suministros de la vivienda.

[COMPLETAR]

El arrendador recibe en este momento la cantidad de [IMPORTE] euros en concepto de fianza a la que dará el destino legal correspondiente.

El arrendatario autoriza al arrendador a hacer suyo en la cantidad debida el valor de la fianza, una vez extinguido el contrato, si aquél adeudara alguna cantidad por impago de renta o cantidades asimiladas, sin perjuicio del derecho a reclamar la deuda por las vías oportunas hasta su completa liquidación.

El arrendatario no podrá ceder el contrato de arrendamiento ni subarrendar total o parcialmente la vivienda.

En todo lo no regulado en este contrato se someten las partes a lo dispuesto en la Ley de Arrendamientos Urbanos.

Los gastos de asesoramiento y representación que pudieran ocasionarse por cualquier reclamación judicial frente al arrendatario, siempre que la pretensión sea estimada por el Tribunal, correrán por cuenta de él, aunque no sea preceptiva la comparecencia con Abogado y Procurador o no se declare expresa imposición de costas.

Y para que conste y surta los efectos oportunos, firman el presente documento el de la Comunidad de Propietarios en nombre de ésta y el arrendatario en cada uno de los folios de los dos ejemplares idénticos que se emiten de este contrato, en el lugar y fecha del encabezamiento.

Firmado: Firmado:

========================================================================
