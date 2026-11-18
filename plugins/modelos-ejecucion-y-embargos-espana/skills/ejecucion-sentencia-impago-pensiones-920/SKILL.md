---
name: ejecucion-sentencia-impago-pensiones-920
description: "Redacta el escrito «Ejecución de sentencia por impago de pensiones» (formulario 920 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Ejecución de sentencia por impago de pensiones

> Formulario 0920 del plugin **Ejecución civil** · revisado el 17-11-2026.

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

- [ ] SEDE (3 veces)
- [ ] NOMBRE Y APELLIDOS (11 veces)
- [ ] NÚMERO (12 veces)
- [ ] FECHA (5 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] IMPORTE (28 veces)
- [ ] DNI/NIE (2 veces)
- [ ] LUGAR
- [ ] Otros 38 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…engo debidamente acreditado en juicio de»; «…de fecha [FECHA] dictada en juicio de»; «…de fecha [FECHA] dictada en juicio de»; «…numeración del juzgado de procedencia).]»; «…mpuesta al demandado de abono de pensión»; «….º—La tutela que se pretende consiste en»; «…de abono de pensión»; «…. Desde el mes de»; «… con su obligación de pago. En el mes de»; «…icado del IPC interanual de los meses de»; «…a»; …

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 549 de la LEC
- art. 592 de la LEC
- art. 576 de la LEC
- art. 608 de la LEC
- art. 539 de la LEC

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

### Formulario 0920 · Ejecución de sentencia por impago de pensiones

- Año del modelo: 2013
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 98 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (IMPORTE, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda ejecutiva

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según tengo debidamente acreditado en juicio de [COMPLETAR] (separación, divorcio o nulidad) n.º [NÚMERO] tramitado ante el órgano al que me dirijo, ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que mediante el presente escrito y según permiten los arts. 517.2.1.º en relación con el art. 776.1.ª de la LEC intereso la EJECUCIÓN FORZOSA de la sentencia n.º [NÚMERO] de fecha [FECHA] dictada en juicio de [COMPLETAR] (separación, divorcio, nulidad), frente a D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD], con objeto de que, previa la tramitación oportuna, se dicte auto despachando ejecución en los términos interesados en el suplico de esta demanda ejecutiva que se basa en los siguientes

PRESUPUESTOS

A los efectos previstos en el art. 549 de la LEC se reseña que:

1.º—El título ejecutivo en el que se basa esta demanda ejecutiva es la sentencia n.º [NÚMERO] de fecha [FECHA] dictada en juicio de [COMPLETAR] (nulidad, separación o divorcio) n.º [NÚMERO] por la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] cuya copia acompaño como documento n.º [NÚMERO], y en concreto el pronunciamiento del fallo relativo a la obligación impuesta al demandado de abono de pensión [COMPLETAR] (de alimentos o compensatoria).

2.º—La tutela que se pretende consiste en [COMPLETAR] (Opciones):

— el cumplimiento de la obligación de D./Dña. [NOMBRE Y APELLIDOS] de abono de pensión [COMPLETAR] (compensatoria o de alimentos) por importe de [IMPORTE] euros mensuales. Esta cantidad se liquidará por anticipado y dentro de los primeros cinco días de cada mes y será actualizable anualmente. Nos encontramos por tanto ante una ejecución dineraria.

La sentencia cuya ejecución se solicita se notificó el día [FECHA].

Desde el mes de [COMPLETAR], según acredito con copia de la cuenta de mi representado que acompaño como documento n.º [NÚMERO], D./Dña. [NOMBRE Y APELLIDOS] ha dejado de cumplir con su obligación de pago.

En el mes de [COMPLETAR] se debía producir la actualización de esta pensión. Según certificado del IPC interanual de los meses de [COMPLETAR] a [COMPLETAR] de los años [COMPLETAR] debe aplicarse a la cantidad vigente en ese momento, es decir a la cifra de [IMPORTE] euros, un porcentaje de actualización de [IMPORTE] euros, de lo que resulta que la pensión a abonar desde el mes de [COMPLETAR] importaría [IMPORTE] euros.

En consecuencia en concepto de pensión de [COMPLETAR] (alimentos o compensatoria) adeuda las siguientes cantidades:

Mes de [IMPORTE], [IMPORTE] euros

Mes de [IMPORTE], [IMPORTE] euros

Mes de [IMPORTE], [IMPORTE] euros

Mes de [IMPORTE], [IMPORTE] euros

Mes de [IMPORTE], [IMPORTE] euros

Mes de [IMPORTE], [IMPORTE] euros

Mes de [IMPORTE], [IMPORTE] euros

TOTAL: [IMPORTE] euros, que se reclaman como principal en este juicio.

Para evitar futuras reclamaciones judiciales interesamos además que desde este momento, y sin perjuicio de la pretensión anterior, se acuerde el embargo del salario que el ejecutado percibe por su trabajo en [LOCALIDAD], con sede en [COMPLETAR] en la cantidad de [IMPORTE] euros mensuales, para hacer frente a las futuras obligaciones. A este efecto se deberá requerir a su empleador para que practique mensualmente la retención indicada (más la que se acuerde para liquidar la deuda atrasada), ordenando el ingreso de esa cantidad en la cuenta de mi representada abierta en la entidad [COMPLETAR] con el n.º [NÚMERO].

3.º—Se designan en el apartado siguiente bienes susceptibles de embargo.

4.º—Que la ejecución ha de despacharse frente a D./Dña. [NOMBRE Y APELLIDOS]

Han transcurrido más de veinte días hábiles desde la firmeza de la sentencia cuya ejecución se pretende.

Como bienes susceptibles de embargo, art. 592 de la LEC, y sin perjuicio de los que se pudieran encontrar si los que citamos resultan insuficientes, esta parte designa los siguientes:

a) Saldos en cuenta abierta en [COMPLETAR] a nombre de [COMPLETAR] DNI n.º [DNI/NIE].

b) Parte de la vivienda de su propiedad situada en [COMPLETAR]. Acompaño como documento n.º [NÚMERO] nota registral acreditativa de la titularidad del inmueble.

c) Salario que percibe D/Dña. [NOMBRE Y APELLIDOS] como [COMPLETAR] en [COMPLETAR].

d) [COMPLETAR].

Si los bienes detallados en el ordinal precedente no resultaran suficientes para cubrir la suma reclamada, interesamos que a través del punto neutro de información judicial se requiera información para averiguación de los bienes, ingresos y derechos de los que pueda ser titular D./Dña. [NOMBRE Y APELLIDOS]: [COMPLETAR].

El cálculo de intereses se hará aplicando el art. 576 de la LEC y el interés legal del dinero para el año [COMPLETAR], que se fijó en la ley de presupuestos del Estado en [COMPLETAR] %. Ese porcentaje incrementado en dos puntos será el que se utilizará para el cálculo.

(En su caso) Esta parte solicita embargo de los bienes del ejecutado en la cantidad de [IMPORTE] euros más [IMPORTE] euros en los que se fijan provisionalmente los intereses y costas de esta ejecución, y sin perjuicio de ulterior liquidación de los mismos. Total [IMPORTE] euros.

Además deberá acordarse la retención mensual de su nómina de [IMPORTE] euros para asegurar los pagos de las obligaciones futuras. Para ello deberá tenerse en cuenta lo establecido en el art. 608 de la LEC que en materia de prestación alimenticia prescinde de los límites para los embargos de sueldos y pensiones fijados en el art. 607 del mismo texto legal.

En aplicación del art. 539 de la LEC las costas deberán imponerse al demandado.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos y copias que acompaño, lo admita y tenga por formulada demanda ejecutiva frente a D./Dña. [NOMBRE Y APELLIDOS], en solicitud de despacho de ejecución de la sentencia n.º [NÚMERO] de fecha [FECHA] dictada en juicio de [COMPLETAR] (separación, divorcio o nulidad) n.º [NÚMERO] por la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO], dictando auto mediante el que se acuerde:

1.º—Que se dicte auto despachando ejecución dineraria frente a D./Dña. [NOMBRE Y APELLIDOS] por importe de [IMPORTE] euros más otros [IMPORTE] euros en los que se calculan provisionalmente y sin perjuicio de ulterior liquidación los intereses y costas.

2.º—Que por el Letrado de la Administración de Justicia se decrete el embargo de los siguientes bienes del ejecutado:

a) Saldos en cuenta abierta en [COMPLETAR] a nombre de [COMPLETAR] DNI n.º [DNI/NIE].

b) Parte de la vivienda de su propiedad situada en [COMPLETAR].

c) Salario que percibe D/Dña. [NOMBRE Y APELLIDOS] como [COMPLETAR] en [COMPLETAR].

d) [COMPLETAR].

3.º—Que se declare que la pensión actualizada que corresponde abonar desde el mes de [COMPLETAR] tiene un importe de [IMPORTE] euros mensuales.

4.º—Que se acuerde requerir a su empleador [COMPLETAR] con sede en [COMPLETAR] para que mensualmente retenga de su nómina la cantidad de [IMPORTE] euros para hacer frente a las mensualidades futuras, ordenando el ingreso en la cuenta de mi representado n.º [NÚMERO] de la Entidad [COMPLETAR].

5.º—Y que se dé a los autos la tramitación procesal pertinente, para que se dicte en su día, si mediare oposición y previa la tramitación oportuna, auto mediante el que se declare procedente que la ejecución siga adelante hasta el cumplimiento efectivo de la resolución judicial [COMPLETAR] (En su caso) y la liquidación de la deuda principal e intereses, todo ello con imposición de costas al demandado.

Es justicia que pido en [LUGAR], a [FECHA].

========================================================================
