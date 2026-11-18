---
name: demanda-ejecutiva-ampliacion-nuevos-plazos-general-870
description: "Redacta el escrito «Demanda ejecutiva con ampliación por nuevos plazos (general)» (formulario 870 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda ejecutiva con ampliación por nuevos plazos (general)

> Formulario 0870 del plugin **Ejecución civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.
- **Inmuebles** (referencia catastral, superficie, uso) → `consultar_catastro` (y `callejero_catastro` para localizar la dirección).

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
- [ ] AÑO (2 veces)
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (10 veces)
- [ ] Nº
- [ ] COLEGIO
- [ ] NÚMERO (8 veces)
- [ ] FECHA (6 veces)
- [ ] CALLE
- [ ] IMPORTE (10 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…e la LO 1/2025. Demanda ejecutiva Juicio»; «…, PLAZA N.º»; «…n.º [NÚMERO] de»; «…o en los siguientes: HECHOS Con fecha de»; «…ediante la que se condena al demandado a»; «…euros en concepto de»; «…del mes hasta el mes de»; «…se hasta el día >de cada mes ascienden a»; «…dictada en los autos de juicio»; «…ientes medidas de investigación judicial»; «…tica de la ejecución para el pago de las»; «…del mes hasta el mes de»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 61 y 545 de la LEC
- artículo 550 de la LEC
- artículo 578 de la LEC
- artículo 549 de la LEC
- artículo 592 LEC
- artículo 549 LEC
- artículo 576 de la LEC

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

### Formulario 0870 · Demanda ejecutiva con ampliación por nuevos plazos (general)

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 50 campos de relleno marcados en blanco; 4 huecos del original que se habían perdido sin marca, marcados (IMPORTE, NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Demanda ejecutiva

Juicio [COMPLETAR] (ordinario/verbal) n.º [Nº DE PROCEDIMIENTO]/[AÑO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS] según tengo debidamente acreditado en el procedimiento referenciado seguido a instancia de mi poderdante contra D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco bajo la dirección del Letrado D./Dña. [NOMBRE Y APELLIDOS], con n.º [Nº] de colegiado del Ilte. Colegio de Abogados de [COLEGIO], y como mejor proceda en Derecho DIGO:

Que por medio del presente escrito formulo demanda ejecutiva mediante la que solicito que se despa-che la EJECUCIÓN de la sentencia n.º [NÚMERO] de fecha [FECHA] dictada en el presente proceso frente a D./ Dña. [NOMBRE Y APELLIDOS] (demandado condenado en la sentencia), domiciliado en Calle [CALLE] n.º [NÚMERO] de [COMPLETAR], cuyas demás circunstancias personales constan en los indicados autos, con objeto de que, previa la tramitación oportuna, se dicte por el Tribunal auto conteniendo orden general de ejecución y de despacho de ella y por el Letrado de la Administración de Justicia decreto para su efectividad en los términos interesados en el suplico de esta demanda ejecutiva que baso en los siguientes:

HECHOS

Con fecha de [COMPLETAR] se dictó, en la tramitación de este proceso, la sentencia n.º [NÚMERO] mediante la que se condena al demandado a [COMPLETAR];

(Opciones):

1. No habiendo sido objeto de recurso, la sentencia referenciada ha resultado firme.

2. Habiéndose recurrido la sentencia, la Audiencia Provincial, mediante sentencia n.º [NÚMERO] de fecha [FECHA], dictada en el recurso de apelación n.º [NÚMERO], ha confirmado el fallo dictado en la instancia.

El demandado no está cumpliendo voluntariamente la obligación derivada del pronuncia-miento de la sentencia, por lo que mediante el presente escrito formalizo la demanda ejecutiva para impul-sar su ejecución, que comprende el pago de la cantidad de [IMPORTE] euros en concepto de [COMPLETAR], así como el pago de >mensualidades pendientes de desde el día [FECHA] del mes hasta el mes de [COMPLETAR], por importe cada una de [IMPORTE] euros.

Por tanto:

• La deuda ya vencida reconocida en sentencia asciende a [IMPORTE] euros.

• (Opciones)

— las >(número de mensualidades pendientes de abonar) ascienden a >mensualidades X [IMPORTE] euros por mensualidad = [IMPORTE] euros

— los pagos periódicos que deben efectuarse hasta el día >de cada mes ascienden a [COMPLETAR]

• Cálculo de los intereses producidos durante la ejecución: [IMPORTE] euros

Han transcurrido más de veinte días hábiles desde la firmeza de la sentencia. A los hechos antecedentes resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

Es competente para conocer de esta ejecución el Tribunal a que me dirijo, por ser quien dictó la resolución cuya ejecución se pide (artículos 61 y 545 de la LEC).

Legitimación

Artículo 549 de la LEC: La ejecución se despachará «a petición de parte».

Tramitación y requisitos procesales

— Consta acreditada la representación del procurador firmante, por lo que no es preciso aportar nue-vamente su acreditación (artículo 550.1.2.º de la LEC).

— A los efectos previstos en el artículo 549.1.1.º de la LEC se reseña que el título ejecutivo en que se funda esta demanda ejecutiva es la sentencia n.º [NÚMERO] de fecha [FECHA] dictada en los autos de juicio [COMPLETAR] n.º [NÚMERO] de este Tribunal.

— A los efectos previstos en el artículo 549.1.2.º de la LEC se señala que la tutela jurídica perseguida es el cumplimiento del fallo de la sentencia cuya ejecución se pide, mediante la que se condena a D./Dña. [NOMBRE Y APELLIDOS] a pagar a mi mandante la suma de [IMPORTE] euros ya vencida así como los pagos periódicos de la deuda pendiente de liquidar y los intereses de todo ello.

— Artículo 517.2.1.º LEC: La sentencia firme es título que lleva aparejada ejecución.

— Artículo 580 de la LEC: No procede requerimiento de pago al ejecutado para embargar bienes cuan-do el título sea resolución judicial que obliga a entregar una cantidad determinada de dinero.

— Artículo 548 de la LEC: No se despachará ejecución dentro de los veinte días posteriores a aquel en que la resolución de condena sea firme. La demanda se presenta transcurrido este plazo.

— El artículo 550 de la LEC exime de la obligación de presentar el título cuando la ejecución se funde en resolución que obre en los autos.

— El artículo 578 de la LEC permite solicitar en este momento la ampliación de la ejecución a los plazos que vayan venciendo de la deuda, siempre que se presente, como hacemos en la fundamentación fáctica, una liquidación final de la deuda que incluya los vencimientos de principal e intereses producidos durante la ejecución. Resultando esta ejecución conforme con el título ejecutivo, como es el caso, el auto en el que se despache ejecución advertirá al ejecutado de que la ejecución se entenderá ampliada automáticamente si a las fechas de vencimiento no se hubieran consignado a disposición del Tribunal las cantidades correspondientes y de que el pago a esta parte se hará conforme a la liquidación que en este momento presentamos. Desde este momento dejamos apuntada la posibilidad de solicitar mejora de embargo si, como consecuencia de esta pretensión, no se cubriera el total de la deuda que se acumule.

— Artículos 551 y ss. de la LEC sobre trámite para el despacho de la ejecución y oposición a ésta.

— A los restantes efectos previstos en el artículo 549 de la LEC establezco los siguientes presupuestos:

A) Designo como bienes del ejecutado susceptibles de embargo los siguientes: (detallar según el orden legal —artículo 592 LEC—). Acompaño reseñados como documentos núms. notas registrales acreditativas de la inscripción de inmuebles de la titularidad del ejecutado.

(entre ellos indicar, si existen ingresos periódicos, su embargo mensual en la cantidad de vencimiento de cada mensualidad)

B) Los bienes detallados en el ordinal precedente no parecen suficientes para cubrir las sumas reclamadas, por lo que, para la localización de bienes del ejecutado con los que hacer frente a su obligación de pago, resultan necesarias las siguientes medidas de investigación judicial [COMPLETAR]:

1. Que a través del punto neutro de información judicial se aporte relación de bienes, derechos y cuentas bancarias de las que es titular D./Dña. [NOMBRE Y APELLIDOS], con DNI

2. Otras:

Fondo

Fondo:

— Artículo 517.1.º de la LEC: reconoce naturaleza ejecutiva a la sentencia firme.

— Sólo se despachará ejecución a petición de parte y en forma de demanda con los requisitos que se desarrollan en el artículo 549 LEC.

— Mora procesal: artículo 576 de la LEC. Desde que se dictó sentencia la cantidad devengará un interés anual igual del interés legal del dinero incrementado en dos puntos. La Ley de Presupuestos Generales del Estado, fija el interés legal del dinero para este año en el 3%.

Costas

Artículos 539, 561.1.1.ª y 583 de la LEC: Deberán imponerse al demandado ejecutado.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL: Tenga por presentado este escrito con los documentos que acompaño, se sirva admitirlo, teniendo por formulada demanda ejecutiva frente a D./Dña. [NOMBRE Y APELLIDOS] en solicitud de despacho de ejecución de la sentencia n.º [NÚMERO] de fecha [FECHA] dictada en estos autos, la admita a trámite y acuerde lo siguiente:

1.º Que se dicte auto de orden general de ejecución despachando ésta en el que

• Se determine que se despacha ejecución frente a D./Dña. [NOMBRE Y APELLIDOS] por el principal de [IMPORTE] euros y otros [IMPORTE] euros que, por el momento y sin perjuicio de ulterior liquidación, se consideran bastantes para intereses, gastos y costas. (En su caso, añadir las precisiones necesarias respecto de las partes, o del contenido de la ejecución, de los responsables personales de la deuda o personas a las que ha de extenderse la ejecución).

• Que dicho auto recoja igualmente la ampliación automática de la ejecución para el pago de las [COMPLETAR] (número) mensualidades pendientes de abonar reconocidas en sentencia por importe de [IMPORTE] euros cada una de ellas, del día [FECHA] del mes hasta el mes de [COMPLETAR] A esta deuda se añadirán los intereses que de manera aproximada, y sin perjuicio de ulterior concreción, se han dejado señalados en el cuerpo de este escrito.

2.º Que en el mismo día o en el siguiente hábil por el Letrado de la Administración de Justicia:

• se decrete el embargo de los siguientes bienes concretos del demandado: (o que se adopten las siguientes medidas ejecutivas [COMPLETAR]).

• se practique las siguientes medidas de averiguación de bienes: [COMPLETAR];

y se dé a los autos la tramitación procesal pertinente, para que se dicte en su día, si mediare oposición, y previa la tramitación oportuna, auto mediante el que se declare procedente que la ejecución siga adelante, acordando, en todo caso, hacer trance y remate de los bienes embargados y pagar con el importe obtenido al demandante el principal reclamado, intereses, gastos y las costas.

Con expresa imposición de costas, en todo caso, al ejecutado D./Dña. [NOMBRE Y APELLIDOS]

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
