---
name: adveracion-apertura-protocolizacion-testamento-oral-671
description: "Redacta el escrito «Adveración, apertura y protocolización de testamento oral» (formulario 671 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Adveración, apertura y protocolización de testamento oral

> Formulario 0671 del plugin **Sucesiones** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (4 veces)
- [ ] FECHA (3 veces)
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…D»; «…, mayor de edad, con domicilio»; «…, provisto del D.N.I»; «…ación del testamento oral otorgado por D»; «…falleció D»; «…y»; «… curso de la intervención, el causante D»; «… instrumentales fueron los siguientes: D»; «…D»; «…stamento oral otorgado por el causante D»

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

### Formulario 0671 · Adveración, apertura y protocolización de testamento oral

- Año del modelo: 2015
- Revisión 17-11-2026: 19 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D [COMPLETAR], mayor de edad, con domicilio [COMPLETAR], provisto del D.N.I [COMPLETAR], en mi propio nombre, ante la Notaría comparezco y DIGO:

- Que al amparo de lo dispuesto en el art. 64 y siguientes de la Ley del Notariado, promuevo expediente para la protocolización del testamento oral otorgado por D [COMPLETAR], con último domicilio en [LOCALIDAD] en fecha [FECHA] en base a los siguientes

HECHOS

El pasado día [FECHA] falleció D [COMPLETAR], nacido el día [FECHA], padre del solicitante y vecino de esta localidad, a las pocas horas de ser ingresado en el Hospital de

El finado dejó viuda y otro hijo, con domicilio en [LOCALIDAD] y [COMPLETAR], respectivamente.

Acompaño certificados de nacimiento del solicitante y de su padre, libro de familia y certificado de defunción acreditativos de los anteriores extremos.

El día del fallecimiento el causante fue ingresado en urgencias del referido Hospital donde le fue diagnosticado un inicio de infarto de miocardio, debiendo pasar de forma inmediata a la sala de operaciones para ser intervenido quirúrgicamente a vida o muerte.

Ante el peligro inminente de muerte y no habiendo otorgado testamento anteriormente, ante cinco testigos, manifestó expresamente su voluntad de otorgarlo en dicho acto, el cual fue registrado en grabación por teléfono móvil cuyo soporte se acompaña como documento núm [Nº DE DOCUMENTO], y el cual puede ser adverado por los testigos que presenciaron el otorgamiento.

Se acompaña asimismo certificado del Registro General de Actos de Última Voluntad acreditativo de la inexistencia de otras disposiciones testamentarias.

Tal como se ha expresado, a las pocas horas del ingreso y en el curso de la intervención, el causante D [COMPLETAR] falleció, por lo que es obvio que concurrió causa legal para el otorgamiento del testamento.

A los efectos del art. 64.3 de la Ley del Notariado, y para la adveración y protocolización del testamento, manifiesto los testigos instrumentales fueron los siguientes:

D [COMPLETAR], mayor de edad, con domicilio en [LOCALIDAD]

D [COMPLETAR], mayor de edad, con domicilio en [LOCALIDAD]

()

Por todo lo expuesto,

RUEGO A V.I.: Tenga por presentado este solicitud y demás documentos junto con las copias que se acompañan, lo admita, y tenga por formulada solicitud de protocolización de testamento oral otorgado por el causante D [COMPLETAR], citando a los testigos instrumentales, tal como dejo interesado y, previos los trámites legales, proceda a la apertura y protocolización del testamento otorgado oralmente por el referido causante.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

(Firma del solicitante)

========================================================================
