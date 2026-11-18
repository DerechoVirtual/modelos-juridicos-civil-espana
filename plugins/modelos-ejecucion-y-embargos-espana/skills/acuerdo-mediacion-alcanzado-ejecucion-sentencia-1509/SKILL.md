---
name: acuerdo-mediacion-alcanzado-ejecucion-sentencia-1509
description: "Redacta el escrito «Acuerdo de mediación alcanzado en ejecución de sentencia» (formulario 1509 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acuerdo de mediación alcanzado en ejecución de sentencia

> Formulario 1509 del plugin **Ejecución civil** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS
- [ ] LOCALIDAD
- [ ] FECHA (4 veces)
- [ ] NÚMERO (2 veces)
- [ ] SEDE
- [ ] IMPORTE (5 veces)
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…25. ACUERDO DE MEDIACIÓN En la ciudad de»; «…, a»; «…, a [COMPLETAR] de»; «…, a [COMPLETAR] de [COMPLETAR], de»; «…de»; «…de [COMPLETAR], de»; «…euros, con vencimiento el día [FECHA] de»; «…euros, con vencimiento el día [FECHA] de»; «…euros, con vencimiento el día [FECHA] de»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Ley 5/2012

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

### Formulario 1509 · Acuerdo de mediación alcanzado en ejecución de sentencia

- Año del modelo: 2014
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 22 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Fecha
Exposición de las partes
ACUERDO
Firmas

Formulario adaptado a la reforma procesal de la LO 1/2025.

ACUERDO DE MEDIACIÓN

En la ciudad de [COMPLETAR], a [COMPLETAR] de [COMPLETAR], de [COMPLETAR]

EXPONEN:

Que han seguido procedimiento de mediación ajustado a las previsiones de la Ley 5/2012, de 6 de julio, con intervención del mediador D. [NOMBRE Y APELLIDOS], y habiendo finalizado el mismo han alcanzado el siguiente

ACUERDO

El objeto de la mediación ha sido el conflicto derivado de la ejecución de la reparación de la fachada del inmueble sito en [LOCALIDAD], y titularidad del ejecutante, a que venía obligado el ejecutado por sentencia firme de fecha [FECHA] de [COMPLETAR], de [COMPLETAR], de la que dimana el proceso de ejecución número [NÚMERO] seguido ante la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

Ambas partes, a la vista de la problemática planteada en la ejecución de esta obligación de hacer, convienen la novación de la misma, la cual será sustituida íntegramente por el pago de la cantidad de [IMPORTE] euros por parte del ejecutado, en los plazos que se expresan a continuación.

En consecuencia, el EJECUTADO se compromete a abonar al EJECUTANTE la cantidad de [IMPORTE] euros en los siguientes plazos:

1.- Primer plazo por importe de [IMPORTE] euros, con vencimiento el día [FECHA] de [COMPLETAR]

2.- Segundo plazo por importe de [IMPORTE] euros, con vencimiento el día [FECHA] de [COMPLETAR]

3.- Tercer plazo por importe de [IMPORTE] euros, con vencimiento el día [FECHA] de [COMPLETAR]

Dichas cantidades serán satisfechas en la cuenta número [NÚMERO], titularidad del EJECUTANTE, con anterioridad a la fecha de su respectivo vencimiento.

El incumplimiento de cualquiera de los plazos supondrá el vencimiento de la totalidad de la obligación.

Como consecuencia de lo convenido en este acto, las partes se obligan a dar órdenes a sus respectivos representantes procesales para que, de mutuo acuerdo, soliciten de mutuo acuerdo la homologación del presente acuerdo de mediación, asumiendo cada una de las partes los costes derivados del proceso de ejecución.

Ambas partes manifiestan que han quedado advertidas por el mediador de que el presente acuerdo es vinculante y que pueden solicitar su homologación del tribunal de la ejecución.

A los efectos de formalización del acuerdo de mediación, se firma el presente acuerdo en tres ejemplares por las partes, con entrega de un ejemplar a cada uno de los intervinientes y al mediador.

Firma de las partes

========================================================================
