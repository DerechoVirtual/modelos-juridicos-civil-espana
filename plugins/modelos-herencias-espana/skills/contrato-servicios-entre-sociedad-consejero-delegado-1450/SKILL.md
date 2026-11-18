---
name: contrato-servicios-entre-sociedad-consejero-delegado-1450
description: "Redacta el escrito «Contrato de servicios entre sociedad y consejero delegado» (formulario 1450 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contrato de servicios entre sociedad y consejero delegado

> Formulario 1450 del plugin **Sucesiones** · revisado el 17-11-2026.

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
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] NÚMERO (2 veces)
- [ ] FECHA (2 veces)
- [ ] PROFESIÓN
- [ ] LOCALIDAD
- [ ] CALLE (2 veces)
- [ ] NÚMERO DE LA CALLE
- [ ] Nº
- [ ] IMPORTE (3 veces)
- [ ] MARCA/MODELO (2 veces)
- [ ] Otros 23 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… representación de la sociedad mercantil»; «…de»; «…de [COMPLETAR] de»; «…autorizada por el Notario de»; «…, e inscrito en el Registro Mercantil de»; «…el .. de»; «…el .. de [COMPLETAR] de»; «…de [COMPLETAR] Tomo .. Folio .. Sección»; «…Hoja .. inscripción»; «…s, y al efecto EXPONEN Que en reunión de»; «…de»; «…de [COMPLETAR] de»; …

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

### Formulario 1450 · Contrato de servicios entre sociedad y consejero delegado

- Año del modelo: 2014
- Revisión 17-11-2026: 38 campos de relleno marcados en blanco; 6 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, NÚMERO DE LA CALLE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Reunidos
EXPONEN
CLÁUSULAS
Firmas

En [LUGAR], a [DÍA] de [MES] de [AÑO].

REUNIDOS

De una parte, D. [NOMBRE Y APELLIDOS] con D.N.I. Nº [NÚMERO] quien interviene en representación de la sociedad mercantil [COMPLETAR] S.A, como Apoderado, según consta en escritura pública de apoderamiento de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] autorizada por el Notario de [COMPLETAR] D. [NOMBRE Y APELLIDOS] con el número [NÚMERO] de su protocolo, e inscrito en el Registro Mercantil de [COMPLETAR] el .. de [COMPLETAR] de [COMPLETAR] Tomo .. Folio .. Sección [COMPLETAR] Hoja .. inscripción [COMPLETAR] y en uso de la facultad que le atribuye.

Y de otra parte, D. [NOMBRE Y APELLIDOS] mayor de edad, de profesión [PROFESIÓN] con D.N.I. y domicilio en [LOCALIDAD] c/ [CALLE] nº [NÚMERO DE LA CALLE].. quien actúa en su propio nombre y derecho.

Las partes tienen y se reconocen capacidad bastante para suscribir el presente contrato de prestación de servicios, y al efecto

EXPONEN

Que en reunión de [COMPLETAR] de [COMPLETAR] de [COMPLETAR] el Consejo de Administración de [COMPLETAR] S.A. decidió por unanimidad autorizar a D. apoderado de la mercantil [COMPLETAR] S.A., a formalizar el presente contrato de prestación de servicios con D. [NOMBRE Y APELLIDOS], quien asumirá funciones como consejero delegado de la empresa [COMPLETAR] S.A y que D. está interesado en el referido puesto, y es por ello que, habiendo llegado las partes a un acuerdo, otorgan el presente contrato que formalizan bajo las siguientes

CLÁUSULAS

Objeto

D. desempeñará el cargo de consejero delegado de la empresa [COMPLETAR] realizando concretamente los servicios de gestión y dirección empresarial, comprometiéndose a realizarlos con la debida diligencia y pericia dada la responsabilidad de las funciones encomendadas, las que se llevarán en todo momento con profesionalidad, conducta ética y confidencialidad.

Autonomía e independencia

El directivo prestará los servicios con plena autonomía y responsabilidad, estando en régimen de dedicación exclusiva, no pudiendo realizar otras actividades por cuenta propia o ajena para cualesquiera otras empresas o terceros.

Duración del contrato

Que el presente contrato tendrá una duración de [Nº] años, iniciándose su vigencia el día [FECHA] de [COMPLETAR] de [COMPLETAR]

Dedicación

El directivo desarrollará sus servicios a tiempo completo, debiendo desarrollarlos, en la medida de lo posible, dentro de la jornada laboral general que la empresa tenga establecida para su personal, si bien con la flexibilidad necesaria dada la condición de sus funciones.

Precio

En compensación por los servicios prestados la mercantil [COMPLETAR] S.A. se obliga al pago de [IMPORTE] euros mensuales, los que se abonarán en la siguiente cuenta bancaria

Asimismo se establece que el directivo tendrá derecho a percibir una retribución variable de hasta [IMPORTE] euros año, en función de los objetivos que se establezcan anualmente como anexo al presente contrato.

Suplidos

Los gastos de viajes, desplazamientos o dietas que genere el directivo en el desempeño de sus funciones serán de exclusiva cuenta de la empresa [COMPLETAR] S.A. que estará obligada a abonarlos en la cuenta antes indicada, previa justificación por parte de D. de los referidos gastos.

Lugar

El directivo prestará sus servicios profesionales habitualmente en el domicilio social de la empresa [COMPLETAR] S.A, sito en la c/ [CALLE] No obstante, deberá realizar tantos desplazamientos y viajes como sean necesarios para poder prestar sus servicios en la forma convenida.

Vehículo

La empresa [COMPLETAR] S.A. pondrá a disposición del directivo un vehículo marca [MARCA/MODELO] modelo [MARCA/MODELO] Dicho vehículo se adquirirá por parte de la empresa en régimen de renting. El indicado vehículo podrá ser utilizado tanto para el ejercicio de las funciones de consejero delegado como para uso particular por parte de éste último.

Rescisión

El presente contrato podrá rescindirse antes de su plazo de vigencia, debiendo la parte que decida su resolución anticipada notificarlo fehacientemente a la otra con un plazo mínimo de seis meses. El incumplimiento de esta obligación dará lugar a la contraparte a una indemnización de [IMPORTE] euros.

Inexistencia de relación laboral

Inexistencia de relación laboral. Las partes establecen que en ningún momento existirá relación laboral entre la empresa [COMPLETAR] S.A. y D. [NOMBRE Y APELLIDOS]

El Profesional manifiesta que tiene plena libertad de decisión respecto a los servicios y funciones que desarrolla, estando obligado a informar mensualmente al Consejo de Administración de la marcha del negocio, de las decisiones adoptadas y del resultado de las mismas.

Ley aplicable y jurisdicción competente

Ley aplicable y jurisdicción competente. El presente contrato se regirá e interpretará de acuerdo con las Leyes de España y se someterá a la jurisdicción de los Tribunales de

Y en prueba de conformidad con todo lo que antecede, las partes suscriben el presente contrato por duplicado, en la fecha y lugar arriba indicado.

Fdo.- 	Fdo.-

========================================================================
