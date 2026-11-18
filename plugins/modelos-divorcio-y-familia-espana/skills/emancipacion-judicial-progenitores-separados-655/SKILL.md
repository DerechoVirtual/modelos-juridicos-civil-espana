---
name: emancipacion-judicial-progenitores-separados-655
description: "Redacta el escrito «Emancipación judicial con progenitores separados» (formulario 655 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Emancipación judicial con progenitores separados

> Formulario 0655 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] FECHA (3 veces)
- [ ] LOCALIDAD (4 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, nacido el día [FECHA] de»; «… nacido el día [FECHA] de [COMPLETAR] de»; «…, y bajo la dirección letrada de Don»; «…numeración del juzgado de procedencia).]»; «…de»; «…de [COMPLETAR] de»; «…de»; «…de [COMPLETAR] de»; «…que el padre convive maritalmente con Dª»; «…eparados ambos progenitores desde el año»; «…omo testigos las siguientes personas: Dª»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 244 del Código Civil
- art. 244 del Código Civil

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

### Formulario 0655 · Emancipación judicial con progenitores separados

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 20 campos de relleno marcados en blanco; 5 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

D. [NOMBRE Y APELLIDOS], nacido el día [FECHA] de [COMPLETAR] de [COMPLETAR], actuando en su nombre y representación con la asistencia de su padre D. [NOMBRE Y APELLIDOS], y bajo la dirección letrada de Don [COMPLETAR], al amparo de lo dispuesto en el artículo 244 del Código Civil y artículo 54 de la Ley de Jurisdicción Voluntaria, ante la Sección Civil del Tribunal de Instancia de [NOTA DE REVISIÓN: Un solo TI por partido judicial (art. 84.1 LOPJ): sobra «de los de». Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] que por turno de reparto corresponda comparezco y, como mejor proceda en Derecho,

DIGO:

Que mediante el presente escrito promueve expediente de jurisdicción voluntaria para la CONCESIÓN JUDICIAL DE LA EMANCIPACIÓN, en base a los siguientes

HECHOS

Que el solicitante nació el día [FECHA] de [COMPLETAR] de [COMPLETAR], por lo que es mayor de dieciséis años.

Sus padres son D. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], con quien convive el solicitante y que le asiste en esta solicitud, y D.ª [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], sin que existan otros hermanos de doble vínculo, y ostentando ambos la patria potestad del solicitante.

En fecha [FECHA] de [COMPLETAR] de [COMPLETAR], los padres del solicitante se divorciaron, poniendo fin a la convivencia, estando separados desde esa fecha.

El solicitante ha residido a temporadas con cada uno de los progenitores, si bien actualmente la situación se ha hecho problemática desde el punto de vista personal, puesto que el padre convive maritalmente con Dª [COMPLETAR], en tanto que la madre ha contraído nuevas nupcias y tiene dos hijos con D. [NOMBRE Y APELLIDOS]

Atendido lo anterior, y de acuerdo a lo dispuesto en el art. 244 del Código Civil y art. 53.1 de la Ley de Jurisdicción Voluntaria, es voluntad del solicitante el de que se le conceda la emancipación al vivir separados ambos progenitores desde el año [COMPLETAR] y, además, estar conviviendo ambos con personas distintas, dándose por tanto los requisitos legalmente establecidos.

FUNDAMENTOS DE DERECHO

Competencia

Son competentes las secciones civiles de los tribunales de instancia de esta ciudad, por ser el del domicilio del menor, conforme a lo dispuesto en el art. 53.1 de la Ley de Jurisdicción Voluntaria.

Procedimiento

Debe seguirse el procedimiento de jurisdicción voluntaria regulado en los artículos 53 y siguientes de la Ley de Jurisdicción Voluntaria.

Legitimación

Esta parte está legitimada conforme a lo dispuesto en el art. 54.1 de la Ley de Jurisdicción Voluntaria, al ser mayor de 16 años y actuar con asistencia de su padre.

Fundamentos de fondo

El art. 244 del Código Civil establece que el Juez podrá conceder la emancipación de los hijos mayores de dieciséis años si éstos la pidieren y previa audiencia de los padres: 1.° Cuando quien ejerce la patria potestad contrajere nupcias o conviviere maritalmente con persona distinta del otro progenitor. 2.° Cuando los padres vivieren separados. 3.° Cuando concurra cualquier causa que entorpezca gravemente el ejercicio de la patria potestad, precepto concordante con el art. 53 de la Ley de Jurisdicción Voluntaria.

Por lo expuesto,

AL TRIBUNAL SUPLICO: Que tenga por presentado este escrito con los documentos que se acompañan, lo admita, y tenga por promovido expediente de jurisdicción voluntaria de concesión judicial de la emancipación, y practicadas las diligencias oportunas, incluida la información testifical que se interesa en el otrosí y con intervención del Ministerio Fiscal, y previos los demás trámites con arreglo a Derecho dicte resolución le sea concedida judicialmente la emancipación, procediendo a su inscripción en el Registro Civil correspondiente.

OTROSÍ DIGO que, al amparo del art. 54.2 de la Ley de Jurisdicción Voluntaria, intereso que sean citados a la comparecencia como testigos las siguientes personas:

Dª [COMPLETAR], pareja del padre del solicitante, con domicilio en [LOCALIDAD]

D. [NOMBRE Y APELLIDOS], cónyuge de la madre del solicitante, con domicilio en [LOCALIDAD]

Por lo que SUPLICO AL TRIBUNAL que tenga por propuestos los testigos indicados y acuerde su citación para la práctica de la prueba en la comparecencia.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

(Firmas solicitante, padre y abogado)

========================================================================
