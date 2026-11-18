---
name: expediente-notarial-nombramiento-perito-contrato-seguro-633
description: "Redacta el escrito «Expediente notarial de nombramiento de perito en contrato de seguro» (formulario 633 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Expediente notarial de nombramiento de perito en contrato de seguro

> Formulario 0633 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.

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

- [ ] NIF (2 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] CORREO ELECTRÓNICO (2 veces)
- [ ] TELÉFONO
- [ ] FECHA (3 veces)
- [ ] NÚMERO
- [ ] IMPORTE (2 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…A LA NOTARÍA DE»; «…D.»; «…egurado en el contrato que se dirá, y D.»; «…en nombre y representación de la entidad»; «…de»; «…de [COMPLETAR] de»; «…de»; «…de [COMPLETAR] de»; «…de»; «…de [COMPLETAR] de»; «…a aseguradora y mi representado, D. y D.»

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

### Formulario 0633 · Expediente notarial de nombramiento de perito en contrato de seguro

- Año del modelo: 2015
- Revisión 17-11-2026: 26 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA NOTARÍA DE [COMPLETAR]

D. [COMPLETAR], con NIF [NIF], con domicilio en [LOCALIDAD], correo electrónico [CORREO ELECTRÓNICO], teléfono [TELÉFONO], actuando en mi propio nombre en condición de asegurado en el contrato que se dirá, y D. [COMPLETAR], con NIF [NIF], y domicilio en [LOCALIDAD], correo electrónico [CORREO ELECTRÓNICO], actuando en nombre y representación de la entidad [COMPLETAR], en condición de aseguradora en el contrato que se dirá, comparecemos ante esa Notaría y formulamos solicitud de expediente notarial para el NOMBRAMIENTO DE TERCER PERITO que emita dictamen en el siniestro ocurrido en fecha [FECHA] de [COMPLETAR] de [COMPLETAR], la cual fundamos en los siguientes:

HECHOS Y FUNDAMENTOS

Las partes solicitantes, en su condición respectiva de asegurado y aseguradora, en fecha [FECHA] de [COMPLETAR] de [COMPLETAR] suscribieron la póliza de seguro de daños sobre el edificio de propiedad del asegurado sito en [LOCALIDAD], con el núm. [NÚMERO], la cual cubría, entre otros riesgos, los daños producidos por cortes o alteraciones de suministro eléctrico ( acompañamos póliza de seguro).

En fecha [FECHA] de [COMPLETAR] de [COMPLETAR] se produjo siniestro que fue comunicado oportunamente y aceptado por la aseguradora, y, no existiendo acuerdo en la indemnización, se designó perito por cada una de las partes conforme a lo dispuesto en el art. 38 de la Ley de Contrato de Seguro, siendo designados, respectivamente por la aseguradora y mi representado, D. y D. [COMPLETAR].

Emitido dictamen por ambos peritos, existe una discordancia clara en cuanto al valor de los daños en las bombas y equipos dañados por el corte de tensión, que el perito de la aseguradora valora en [IMPORTE] euros, en tanto que el perito del asegurado valora en [IMPORTE] euros, existiendo una discordancia en cuanto al número de horas de mano de obra requeridas y al coste de reposición de los equipos (acompañamos copia de los dictámenes periciales emitidos por D. y D. [NOMBRE Y APELLIDOS]).

Atendida la discordancia y no habiéndose puesto de acuerdo los solicitantes para la designación de tercer perito, se insta este expediente a fin de que sea designado notarialmente, al amparo de lo dispuesto en el art. 38 de la Ley de Contrato de Seguro y artículo 80 de la Ley del Notariado, interesando que el dictamen se emita en el plazo de treinta días.

Por todo lo expuesto,

SOLICITAMOS que tenga por promovido para designación judicial de tercer perito en el contrato de seguro expresado, y tras los trámites legales, proceda a su nombramiento y disponiendo la aceptación y emisión del dictamen conforme a lo interesado.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de los solicitantes

========================================================================
