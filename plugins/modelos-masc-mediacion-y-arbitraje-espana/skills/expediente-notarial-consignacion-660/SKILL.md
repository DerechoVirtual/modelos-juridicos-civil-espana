---
name: expediente-notarial-consignacion-660
description: "Redacta el escrito «Expediente notarial de consignación» (formulario 660 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Expediente notarial de consignación

> Formulario 0660 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] IMPORTE (3 veces)
- [ ] LOCALIDAD (4 veces)
- [ ] FECHA (4 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…A LA NOTARÍA DE»; «…de»; «…de [COMPLETAR] de»; «…de»; «…de [COMPLETAR] de»; «…o normalmente hasta que el pasado mes de»; «…en fecha [FECHA] de»; «…en fecha [FECHA] de [COMPLETAR] de»

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

### Formulario 0660 · Expediente notarial de consignación

- Año del modelo: 2015
- Revisión 17-11-2026: 22 campos de relleno marcados en blanco; 5 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA NOTARÍA DE [COMPLETAR]

D. [NOMBRE Y APELLIDOS], actuando en su propio nombre, ante la Notaría comparezco y

DIGO:

- Que al amparo de lo dispuesto en los artículos 1176 y siguientes del Código Civil, en relación con el art. 69 de la Ley del Notariado, mediante el presente escrito deduzco expediente notarial de consignación de la cantidad de [IMPORTE] euros para la cancelación de la obligación contraída con D. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], en atención a los siguientes

HECHOS Y FUNDAMENTOS

En fecha [FECHA] de [COMPLETAR] de [COMPLETAR], mi representado concertó contrato de arrendamiento con D. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], respecto de la vivienda sita en [LOCALIDAD] (acompaño como documento número [Nº DE DOCUMENTO] contrato de arrendamiento de fecha [FECHA] de [COMPLETAR] de [COMPLETAR])

El pago de la renta mensual por importe de [IMPORTE] euros debía realizarse mediante entrega en efectivo al arrendador en su domicilio sito en [LOCALIDAD], lo cual se vino cumpliendo normalmente hasta que el pasado mes de [COMPLETAR], el arrendador se negó a recibir el pago de la renta mensual, actitud que ha reiterado este mes de

Habida cuenta del rechazo de la percepción de la renta, mi representado remitió por burofax requerimiento para que el arrendador aceptara el ofrecimiento de pago, anunciándole en otro caso la consignación judicial de la deuda, el cual fue recibido por el arrendador D. [NOMBRE Y APELLIDOS], el día [FECHA], sin que realizara manifestación alguna (acompaño como documento número [Nº DE DOCUMENTO] copia del burofax de ofrecimiento de pago y anuncio de consignación).

Atendido lo anterior y habida cuenta que se han cumplido los requisitos de los artículos 1176 y siguientes del Código Civil, se procede a la consignación en esta Notaría de la cantidad de [IMPORTE] euros que entrego en este mismo acto, solicitando que se sigan trámites preceptivos para la cancelación de la obligación de pago, en su caso.

Por lo anterior,

RUEGO A V.I. que tenga por presentada esta solicitud de consignación notarial de la obligación de pago derivada del contrato de arrendamiento concertado con D. [NOMBRE Y APELLIDOS] en fecha [FECHA] de [COMPLETAR] de [COMPLETAR], con los documentos acompañados y sus copias, deposite en legal forma la cantidad entregada, y, en su virtud, la admita y se sigan los trámites legales para la extinción de la obligación de pago en su caso.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma interesado

========================================================================
