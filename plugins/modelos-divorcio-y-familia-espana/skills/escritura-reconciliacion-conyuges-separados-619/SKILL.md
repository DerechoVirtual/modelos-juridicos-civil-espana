---
name: escritura-reconciliacion-conyuges-separados-619
description: "Redacta el escrito «Escritura de reconciliación de cónyuges separados» (formulario 619 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Escritura de reconciliación de cónyuges separados

> Formulario 0619 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (8 veces)
- [ ] NÚMERO
- [ ] FECHA (2 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] DNI/NIE
- [ ] Otros 18 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…NÚMERO [NÚMERO] En»; «…En [COMPLETAR], mi residencia, a»; «…, mi residencia, a [COMPLETAR] de»; «…de [COMPLETAR] del año»; «…del año [COMPLETAR] Ante mí, Notario de»; «…y DON/DOÑA [NOMBRE Y APELLIDOS],»; «…n: EXPONEN Que contrajeron matrimonio en»; «…el día [FECHA] de»; «…el día [FECHA] de [COMPLETAR] de»; «…, al tomo n°»; «…, al tomo n° [COMPLETAR], página n°»; «…e escritura autorizada por el Notario de»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 82 CC
- Ley Orgánica 15/1999

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

### Formulario 0619 · Escritura de reconciliación de cónyuges separados

- Año del modelo: 2016
- Revisión 17-11-2026: 32 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

ESCRITURA DE RECONCILIACIÓN MATRIMONIAL

OTORGANTES: Los consortes DON/DOÑA [NOMBRE Y APELLIDOS] y DON/DOÑA [NOMBRE Y APELLIDOS]

NÚMERO [NÚMERO]

En [COMPLETAR], mi residencia, a [COMPLETAR] de [COMPLETAR] del año [COMPLETAR]

Ante mí, Notario de [COMPLETAR] y su Ilustre Colegio,

COMPARECEN

Los consortes DON/DOÑA [NOMBRE Y APELLIDOS] y DON/DOÑA [NOMBRE Y APELLIDOS], [COMPLETAR]

INTERVIENEN

Ambos en su propio nombre y derecho.

Identifico a ambos comparecientes a través de sus reseñados documentos de identidad, que me exhiben y compruebo, y tienen, a mi juicio, según intervienen, capacidad legal necesaria para otorgar la presente escritura, a cuyo fin:

EXPONEN

Que contrajeron matrimonio en [COMPLETAR] el día [FECHA] de [COMPLETAR] de [COMPLETAR], que se inscribió en el Registro Civil de [LOCALIDAD], al tomo n° [COMPLETAR], página n° [COMPLETAR] de la Sección 2ª, lo que acreditan por medio de certificado de matrimonio expedido por el Encargado del Registro Civil.

Que mediante escritura autorizada por el Notario de [COMPLETAR], DON/DOÑA [NOMBRE Y APELLIDOS], el día [FECHA] de [COMPLETAR] de .., con número de protocolo [COMPLETAR], los citados cónyuges acordaron su separación, conforme a lo dispuesto en el art. 82 CC. La separación del matrimonio fue inscrita en el Registro Civil de [LOCALIDAD], al tomo n° [COMPLETAR], página n° [COMPLETAR] de la Sección 2ª, lo que acreditan mediante certificado expedido por el Encargado del Registro Civil..

Que ambos cónyuges tienen la voluntad inequívoca de reconciliarse, dejando sin efecto la separación antes referida, a cuyo efecto,

OTORGAN

Los consortes DON/DOÑA [NOMBRE Y APELLIDOS] y DON/DOÑA [NOMBRE Y APELLIDOS] otorgan su reconciliación, que formalizan en la presente escritura conforme a lo dispuesto en el artículo 84.II CC, dejando sin efecto lo resuelto en la escritura de separación referida en el expositivo II.

No es posible remitir, por medios electrónicos, copia de la presente escritura a la Oficina General del Registro Civil, por lo que los comparecientes me requieren a mi, el notario, para que, conforme al art. 83.III CC y a los efectos en él dispuestos, remita copia autorizada en papel al Registro Civil correspondiente al lugar de celebración del matrimonio. La reconciliación producirá efectos frente a terceros a partir de su inscripción.

En cumplimiento de la Ley Orgánica 15/1999, de 13 de Diciembre, de Protección de Datos de Carácter Personal, informo a los otorgantes que los datos recogidos en el presente documento, serán incorporados a los ficheros informáticos existentes en la Notaría, conservándose en la misma con carácter confidencial. El Responsable del Fichero es el notario autorizante del presente documento, Don/Doña [NOMBRE Y APELLIDOS], con DNI [DNI/NIE] y domicilio a estos efectos en la calle de [COMPLETAR], de [COMPLETAR] Podrá ejercitar los derechos de acceso, rectificación, cancelación u oposición mediante solicitud dirigida al Responsable del Fichero, a la dirección indicada, acompañada de su DNI u otro documento oficial de identificación, especificando el derecho que desea ejercitar. Así mismo, informo que el Responsable del Fichero únicamente realizará cesiones de sus datos a aquellas Administraciones Públicas que disponga la legislación vigente.

Leo a los comparecientes esta escritura previa advertencia del derecho que para hacerlo por sí les asiste. Se ratifican, prestan su consentimiento y, en prueba de conformidad, la firman conmigo, que doy fe de lo contenido en este instrumento público.

SIGUEN LAS FIRMAS DE LOS COMPARECIENTES.- SIGNADO: .. .- RUBRICADOS Y SELLADO.

========================================================================
