---
name: acta-constitutiva-mediacion-1503
description: "Redacta el escrito «Acta constitutiva de mediación» (formulario 1503 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acta constitutiva de mediación

> Formulario 1503 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] DNI/NIE (2 veces)
- [ ] CALLE (2 veces)
- [ ] Nº (4 veces)
- [ ] TELÉFONO (2 veces)
- [ ] LOCALIDAD
- [ ] FECHA (3 veces)
- [ ] IMPORTE (7 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 19 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, y domiciliado en»; «…, C.P., calle [CALLE], núm. [Nº], piso»; «…, núm. [Nº], piso [COMPLETAR], letra»; «…letra [COMPLETAR], dirección electrónica»; «…, y domiciliado en»; «…, C.P., calle [CALLE], núm. [Nº], piso»; «…, núm. [Nº], piso [COMPLETAR], letra»; «…letra [COMPLETAR], dirección electrónica»; «…,»; «…, dirección de correo»; «…contrato de arrendamiento sobre el local»; «…de»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 9 de la Ley 5/2012

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

### Formulario 1503 · Acta constitutiva de mediación

- Año del modelo: 2014
- Revisión 17-11-2026: 38 campos de relleno marcados en blanco; 9 huecos del original que se habían perdido sin marca, marcados (IMPORTE, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Parte
EXPONEN
Firmas

ACTA CONSTITUTIVA DE LA MEDIACIÓN

D. [NOMBRE Y APELLIDOS], mayor de edad, con DNI [DNI/NIE], y domiciliado en [COMPLETAR], C.P., calle [CALLE], núm. [Nº], piso [COMPLETAR], letra [COMPLETAR], dirección electrónica [COMPLETAR], y teléfono [TELÉFONO].

Y D. [NOMBRE Y APELLIDOS], mayor de edad, con DNI [DNI/NIE], y domiciliado en [COMPLETAR], C.P., calle [CALLE], núm. [Nº], piso [COMPLETAR], letra [COMPLETAR], dirección electrónica [COMPLETAR], y teléfono [TELÉFONO],

EXPONEN

Ambos intervienen en su propio nombre y derecho y aceptan desarrollar la mediación para la resolución del conflicto que se describe en el punto II dentro de los siguientes términos:

I. DESIGNACIÓN DE MEDIADOR:

Ambas partes de común acuerdo designan como mediador a D. [NOMBRE Y APELLIDOS], [COMPLETAR] con domicilio en [LOCALIDAD], dirección de correo [COMPLETAR].

II. OBJETO DEL CONFLICTO QUE SE SOMETE A MEDIACIÓN:

Que el conflicto que se somete a mediación deriva del contrato de arrendamiento sobre el local [COMPLETAR] suscrito por ambas partes en fecha [FECHA] de [COMPLETAR] de [COMPLETAR] otorgado en fecha [FECHA] de [COMPLETAR], concretándose la controversia en determinar a quién corresponde la obligación de pago de las obras realizadas por el arrendatario D. [NOMBRE Y APELLIDOS] en el local arrendado según contrato, cuyo importe asciende a [IMPORTE] euros.

III. PROGRAMA DE ACTUACIONES Y DURACIÓN MÁXIMA DEL PROCEDIMIENTO:

Que en presencia del mediador las partes acuerdan fijar la celebración de una sesión preliminar por separado para el día [FECHA] de [COMPLETAR] de [COMPLETAR], a las [Nº] horas para D. [NOMBRE Y APELLIDOS] y a las [Nº] horas para D.. [NOMBRE Y APELLIDOS]

Posteriormente se celebrará una sesión conjunta convocada por el mediador, celebrándose hasta un máximo de dos sesiones más si fuera necesario.

La mediación se llevará a cabo en sesiones de una duración máxima de sesenta minutos.

Las partes acuerdan que el plazo de duración máxima del procedimiento de mediación será de tres meses a contar desde la firma del presente documento, y que podrá prorrogarse durante un mes por mutuo acuerdo de las partes.

IV. COSTE DE LA MEDIACIÓN.

El coste de la mediación se dividirá por igual entre las partes firmantes, y se abonará a la finalización del procedimiento.

En concepto de provisión de fondos, cada una de las partes entregan en este acto al mediador la cantidad de [IMPORTE] euros, manifestando su conformidad el mediador con la firma de este acta.

El coste de la mediación incluirá los siguientes conceptos:

1) Bases de los honorarios del mediador que responderán a los actos efectivamente realizados por el mediador

Núm. de sesiones [COMPLETAR] por [IMPORTE] euros cada sesión: [IMPORTE] euros.

Redacción de acuerdo [IMPORTE]: euros.

2) Otros gastos

Alquiler local: [IMPORTE] euros.

Desplazamientos mediador: [IMPORTE] euros.

3) [COMPLETAR]

V. ACEPTACIÓN Y ASUNCIÓN DE OBLIGACIONES:

Las partes declaran haber sido informadas acerca de las características básicas de la mediación, Y manifiestan su voluntad de participar en la mediación y asumir las obligaciones que de ella se deriven, y tanto las partes, como el mediador se comprometen a aceptar y cumplir estos principios básicos.

De conformidad a lo dispuesto en el art. 9 de la Ley 5/2012 las partes suscriben en la misma fecha documento de confidencialidad donde establecen el alcance de sus obligaciones, así como las del mediador y de la institución de mediación.

VI: LUGAR DE CELEBRACIÓN Y LENGUA DEL PROCEDIMIENTO:

Que ambas partes convienen que la mediación se desarrolle en [COMPLETAR] y que el idioma en el que se sustanciará el procedimiento será el castellano.

Y para que así conste, se extiende esta acta con un ejemplar para cada una de les partes, a uno solo efecto, al lugar y fecha indicados.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firmas de las partes y del mediador

========================================================================
