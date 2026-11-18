---
name: expediente-notarial-conciliacion-solicitud-masc-15
description: "Redacta el escrito «Expediente notarial de conciliación: solicitud (MASC)» (formulario 15 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Expediente notarial de conciliación: solicitud (MASC)

> Formulario 0015 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] PROFESIÓN
- [ ] LOCALIDAD (3 veces)
- [ ] CORREO ELECTRÓNICO (2 veces)
- [ ] FECHA (2 veces)
- [ ] IMPORTE (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…s. 5.1 y 14.3 LO 1/2025. A LA NOTARÍA DE»; «…, vecino de»; «…el solicitante (acompaño como documentos»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 5.1 y 14.3 LO 1/2025
- art. 5.1 de la Ley Orgánica 1/2025

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

### Formulario 0015 · Expediente notarial de conciliación: solicitud (MASC)

- Año del modelo: 2025
- Revisión 17-11-2026: 17 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de solicitud de conciliación ante Notario a los efectos de cumplir el requisito de procedibilidad para la iniciación de la vía jurisdiccional, conforme a los arts. 5.1 y 14.3 LO 1/2025.

A LA NOTARÍA DE [COMPLETAR]

D./Dª [NOMBRE Y APELLIDOS], mayor de edad, casado y de profesión [PROFESIÓN], vecino de [COMPLETAR], con domicilio en [LOCALIDAD], correo electrónico [CORREO ELECTRÓNICO] con NIF núm. comparezco ante la Notaría y solicito la celebración de ACTO DE CONCILIACIÓN con el requerido D./Dª [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD] y correo electrónico [CORREO ELECTRÓNICO], en base a los siguientes

HECHOS Y FUNDAMENTOS:

PRIMERO.- Se insta esta solicitud de conciliación al amparo de lo dispuesto en el art. 81 LN, que establece que podrá realizarse ante Notario la conciliación de los distintos intereses de los otorgantes con la finalidad de alcanzar un acuerdo extrajudicial, sobre cualquier controversia contractual como la que es objeto de esta solicitud.

SEGUNDO.- La petición se funda en que el solicitante y el requerido suscribieron en fecha [FECHA] un contrato privado de compraventa sobre el piso de propiedad del requerido sito en [LOCALIDAD] fijando un precio de [IMPORTE] euros a satisfacer en tres plazos por importe de [IMPORTE] euros cada uno, los cuales fueron abonados puntualmente por el solicitante (acompaño como documentos [COMPLETAR] contrato y recibos de pago del precio).

TERCERO.- El requerido no ha otorgado la escritura pública de compraventa a que se comprometió en el referido contrato.

CUARTO.- El objeto de la conciliación es que el requerido se avenga al otorgamiento de la escritura pública de la compraventa realizada en fecha [FECHA] y al pago de la mitad de los gastos notariales, registrales y fiscales conforme a lo pactado.

QUINTO.- La presente solicitud se formaliza asimismo, y en su caso, a los efectos de cumplir el requisito de procedibilidad para la iniciación de la vía jurisdiccional de conformidad a lo dispuesto en el art. 5.1 de la Ley Orgánica 1/2025 y conforme autoriza el art. 14.3 de la citada Ley Orgánica 1/2025, (si la solicitud es anterior a la entrada en vigor: para el caso de interposición de la demanda una vez haya entrado en vigor la citada Ley a partir del día 3 de abril de 2025), solicitando que se advierta al requerido sobre estas circunstancias.

En virtud de lo antes indicado,

SOLICITO A V.I.:

Que tenga por presentada esta solicitud de conciliación al objeto expresado, citando de comparecencia al requerido D/Dª [NOMBRE Y APELLIDOS] en la forma legalmente prevista con las advertencias oportunas; y una vez celebrado, disponga que se me entregue copia autorizada de la escritura pública de conciliación.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del/de la solicitante
