---
name: acta-requerimiento-designar-contador-partidor-acuerdo-541
description: "Redacta el escrito «Acta de requerimiento para designar contador-partidor por acuerdo mayoritario (Galicia)» (formulario 541 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acta de requerimiento para designar contador-partidor por acuerdo mayoritario (Galicia)

> Formulario 0541 del plugin **Sucesiones** · revisado el 17-11-2026.

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

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LUGAR
- [ ] FECHA (4 veces)
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] NÚMERO (3 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] PROVINCIA
- [ ] Nº
- [ ] Otros 35 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, mayor de edad, estado civil, nacido el»; «…en»; «…en [COMPLETAR], vecino/a de»; «…, mayor de edad, estado civil, nacido el»; «…en»; «…en [COMPLETAR], vecino/a de»; «…, mayor de edad, estado civil, nacido el»; «…en»; «…en [COMPLETAR], vecino/a de»; «…mparecientes en unión de su hermana Doña»; «…os herederos abintestato de su padre Don»; «…, fallecido el»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Ley 2/2006

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

### Formulario 0541 · Acta de requerimiento para designar contador-partidor por acuerdo mayoritario (Galicia)

- Año del modelo: 2016
- Revisión 17-11-2026: 49 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [FECHA].

Ante mí, Notario del Ilustre Colegio de Galicia,

Comparecen

[NOMBRE Y APELLIDOS], mayor de edad, estado civil, nacido el [COMPLETAR] en [COMPLETAR], vecino/a de [COMPLETAR], con D.N.I..

[NOMBRE Y APELLIDOS], mayor de edad, estado civil, nacido el [COMPLETAR] en [COMPLETAR], vecino/a de [COMPLETAR], con D.N.I..

[NOMBRE Y APELLIDOS], mayor de edad, estado civil, nacido el [COMPLETAR] en [COMPLETAR], vecino/a de [COMPLETAR], con D.N.I..

Intervienen en su propio nombre y derecho.

Les identifico por sus reseñados documentos y tienen, a mi juicio, interés legítimo para promover la presente ACTA DE REQUERIMIENTO y al efecto

Exponen

Que por acta autorizada por el infrascrito Notario el día [FECHA], bajo el número [NÚMERO] de protocolo, los comparecientes en unión de su hermana Doña [COMPLETAR], fueron declarados herederos abintestato de su padre Don [COMPLETAR], fallecido el [COMPLETAR], sin perjuicio de la cuota legal usufructuaria correspondiente a la viuda [COMPLETAR].

Que por acta autorizada por el insfrascrito Notario el día [FECHA], bajo el número [NÚMERO] de protocolo, los comparecientes en unión de su hermana Doña [COMPLETAR], fueron declarados herederos abintestato de su madre Doña [COMPLETAR], fallecida el [COMPLETAR], en estado de viuda de Don [COMPLETAR].

Que como resulta de lo expuesto, al día de la fecha los únicos interesados en las herencias de Don [COMPLETAR] y de su esposa Doña [COMPLETAR], son los tres aquí requirentes así como su hermana Doña [COMPLETAR], ostentando los cuatro hermanos, los mismos derechos sobre los dos patrimonios hereditarios; esto es, siendo coherederos por cuartas e iguales partes.

Que Doña [COMPLETAR], emigró a [COMPLETAR] hace más de cincuenta años, sin que los requirentes hubiesen vuelto a tener noticias de ella desde hace más de treinta años, y cuyo domicilio en [LOCALIDAD] ignoran, siendo su último domicilio en España antes de emigrar, el de [COMPLETAR].

Que no hay contador-partidor designado por los causantes expresados y los tres requirentes, que representan las tres cuartas partes de los patrimonios hereditarios descritos, son tres de los cuatro herederos de los mismos.

Que desean proceder a la partija de las herencias de Don [COMPLETAR] y Doña [COMPLETAR], de conformidad con lo dispuesto en el artículo 298 de la Ley de Derecho Civil de Galicia, Ley 2/2006, de 14 de junio, a cuyo efecto designan contadores-partidores de las mismas a las siguientes personas:, [COMPLETAR], [COMPLETAR] y [COMPLETAR].

Y, expuesto cuanto antecede

Me requieren

A mí, el Notario, para que, de conformidad con lo dispuesto en los artículos 295 y siguientes de la Ley de Derecho Civil de Galicia, Ley 2/2006, de 14 de junio, notifique a la heredera Doña [COMPLETAR], mediante la publicación de edictos en el Boletín Oficial de la Provincia de [PROVINCIA], en el tablón de anuncios del Ayuntamiento de [LOCALIDAD], y en uno de los periódicos de mayor circulación en dicho Municipio, su propósito de promover la partición de las herencias de Don [COMPLETAR] y de Doña [COMPLETAR], así como la posibilidad que tiene de nombrar, en el plazo de treinta días hábiles siguientes a contar desde la publicación del último de los tres edictos citados, hasta un máximo de tres contadores-partidores, procediéndose a la designación por sorteo ante el infrascrito Notario del contador-partidor que realizará las operaciones particionales el día [FECHA] a las [Nº] horas, entre los designados por los requirentes y los que designe la requerida.

Y yo, Notario, acepto el requerimiento, de cuyo resultado dejaré constancia por diligencia a continuación de la presente.

Cláusula LOPD. De acuerdo con lo establecido en la Ley, los comparecientes quedan informados y aceptan la incorporación de sus datos y la copia del Documento de identidad a los ficheros automatizados existentes en la Notaría, que se conservarán en la misma con carácter confidencial, sin perjuicio de las remisiones de obligado cumplimiento a las Administraciones Públicas que estipula la ley y, en su caso, al Notario que suceda al actual en esta plaza. Su finalidad es realizar la formalización de la presente acta, su facturación y seguimiento posterior y las funciones propias de la actividad notarial. La identidad y dirección del responsable son las siguientes: Don [COMPLETAR], con dirección en [COMPLETAR].

Hago las reservas y advertencias legales.

Les leo, por su elección, esta acta, después de hacerles saber su derecho a leerla por sí, se ratifican en su contenido y firman.

De haber identificado a los promoventes por sus reseñados documentos y de todo lo demás contenido en esta acta extendida en [COMPLETAR] folios de papel del Estado, de uso notarial, serie [COMPLETAR], número [NÚMERO], yo, el Notario, DOY FE.

========================================================================
