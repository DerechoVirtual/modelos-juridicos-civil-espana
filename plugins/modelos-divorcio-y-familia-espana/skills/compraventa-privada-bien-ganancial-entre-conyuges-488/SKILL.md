---
name: compraventa-privada-bien-ganancial-entre-conyuges-488
description: "Redacta el escrito «Compraventa privada de bien ganancial entre cónyuges» (formulario 488 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Compraventa privada de bien ganancial entre cónyuges

> Formulario 0488 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] FECHA (2 veces)
- [ ] NOMBRE Y APELLIDOS (10 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] NÚMERO (5 veces)
- [ ] IMPORTE
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…se describe a continuación: DESCRIPCIÓN:»; «…ante el Notario de»; «…de»; «…de [COMPLETAR], al»; «…, fechado el»; «…y expedido por la entidad bancaria»; «…, sucursal de»; «…, sucursal de [COMPLETAR], que Don»

## Elecciones que hay que hacer

- DNI / pasaporte

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Si se concreta la fecha de otorgamiento / Si no se concreta la fecha de otorgamiento — el texto de cada opción no venía en el formulario original

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

### Formulario 0488 · Compraventa privada de bien ganancial entre cónyuges

- Año del modelo: 2017
- Revisión 17-11-2026: 2 desplegables convertidos en elección en blanco; 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 28 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Contrato privado de compraventa de bien ganancial entre cónyuges. Se estipula el objeto de la compraventa, el sistema de pago, el saneamiento por evicción y vicios ocultos y la previsión de otorgamiento de la escritura pública de compraventa.

En [LUGAR], a [FECHA].

REUNIDOS

DE UNA PARTE, D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, casado/a en régimen de gananciales, con domicilio en [LOCALIDAD], vecindad civil común, y [ELEGIR: DNI / pasaporte] n.º [NÚMERO].

Y DE OTRA, D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, casado/a en régimen de gananciales, con domicilio en [LOCALIDAD], vecindad civil común, y [ELEGIR: DNI / pasaporte] n.º [NÚMERO].

Ambas partes intervienen en su propio nombre y derecho, reconociéndose, como así lo verifican en este acto, la mutua capacidad legal necesaria para la formalización del presente documento y, con su expreso consentimiento,

EXPONEN

I.- Que los cónyuges D. y Dña. son dueños con carácter ganancial de la finca que se describe a continuación:

DESCRIPCIÓN: [COMPLETAR].

TÍTULO: Les pertenece por compra constante matrimonio, en virtud de escritura pública de compraventa otorgada en fecha [FECHA] ante el Notario de [COMPLETAR] D./Dña. [NOMBRE Y APELLIDOS] con el número [NÚMERO] de su protocolo.

INSCRIPCIÓN: Se haya inscrita a su favor en el Registro de la Propiedad número [NÚMERO] de [COMPLETAR], al [COMPLETAR].

CARGAS: Libre de cargas y gravámenes

II.- Que estando interesado D./Dña. [NOMBRE Y APELLIDOS] en enajenar la parte indivisa que le corresponde de la referida finca, y D./Dña. [NOMBRE Y APELLIDOS] en adquirirla, se suscribe el presente CONTRATO PRIVADO DE COMPRAVENTA que se regirá conforme a las siguientes:

CLÁUSULAS

Primera.- Objeto

D./Dña. [NOMBRE Y APELLIDOS] vende a D./Dña. [NOMBRE Y APELLIDOS], su cuota en plena propiedad de la finca descrita en el expositivo I de este contrato, transmitiéndole aquélla sin carga alguna.

Segunda.- Precio

El precio de la compraventa es de [IMPORTE] euros, que D./Dña. [NOMBRE Y APELLIDOS] paga con dinero privativo, quedando integrada la finca como un bien privativo de la compradora, formalizándose el pago mediante entrega de cheque bancario n.º [NÚMERO], fechado el [COMPLETAR] y expedido por la entidad bancaria [COMPLETAR], sucursal de [COMPLETAR], que Don [COMPLETAR] recibe y acepta como efectivo metálico, otorgando a la adquirente carta de pago total del precio de la venta.

Tercera.- Saneamiento por evicción y vicios ocultos

El vendedor queda obligado a la evicción y saneamiento de la finca transmitida con arreglo a derecho.

Cuarta.- Otorgamiento de la escritura pública de compraventa

[ELEGIR UNA OPCIÓN Y REDACTARLA: Si se concreta la fecha de otorgamiento / Si no se concreta la fecha de otorgamiento — el texto de cada opción no venía en el formulario original]

Si llegado el día fijado para la firma de la escritura pública, no se lleva a cabo el citado otorgamiento por cualquier causa que no sea por fuerza mayor o caso fortuito, la parte a la que no sea imputable la no perfección del contrato podrá dar por resuelto el contrato o podrá demandar su cumplimiento, en ambos casos con derecho a indemnización de daños y perjuicios.

Y leído el presente documento, ambas partes lo firman en señal de conformidad y ratificación de su contenido, haciéndolo por duplicado y a un solo efecto.

COMPRADOR

VENDEDOR

Firmado: D./Dña. [NOMBRE Y APELLIDOS] 	Firmado: D./Dña. [NOMBRE Y APELLIDOS]

========================================================================
