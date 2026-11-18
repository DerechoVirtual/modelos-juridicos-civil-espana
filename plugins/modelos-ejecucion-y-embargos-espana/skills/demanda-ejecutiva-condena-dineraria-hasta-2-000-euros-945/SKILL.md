---
name: demanda-ejecutiva-condena-dineraria-hasta-2-000-euros-945
description: "Redacta el escrito «Demanda ejecutiva de condena dineraria hasta 2.000 euros» (formulario 945 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda ejecutiva de condena dineraria hasta 2.000 euros

> Formulario 0945 del plugin **Ejecución civil** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS
- [ ] LOCALIDAD
- [ ] DNI/NIE
- [ ] Nº DE RESOLUCIÓN
- [ ] FECHA
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Autos»; «…, PLAZA N.º»; «…és de los siguientes medios electrónicos»; «…, según consta en los autos de juicio»; «…núm / seguidos a mi instancia contra D»; «…de fecha [FECHA] de»; «…de fecha [FECHA] de [COMPLETAR] de»; «…autos, dirigiendo dicha demanda contra D»; «…ia cuya ejecución solicito establece que»; «… demanda a obtener la tutela judicial de»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 580 de la LEC
- artículo 592 de la LEC

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

### Formulario 0945 · Demanda ejecutiva de condena dineraria hasta 2.000 euros

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 27 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Autos [COMPLETAR] núm / Ejecución

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./D.ª [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD] y DNI nº [DNI/NIE], pudiendo ser notificada a través de los siguientes medios electrónicos [COMPLETAR], según consta en los autos de juicio [COMPLETAR] núm / seguidos a mi instancia contra D [COMPLETAR], ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que mediante el presente escrito formulo demanda ejecutiva mediante la que solicito la ejecución de la sentencia núm [Nº DE RESOLUCIÓN] de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] dictada en estos autos, dirigiendo dicha demanda contra D [COMPLETAR], cuyas circunstancias personales constan en los autos referenciados, con objeto de que, previa la tramitación oportuna, se dicte auto despachando ejecución en los términos interesados en el suplico de esta demanda ejecutiva que baso en los siguientes

ANTECEDENTES

El título ejecutivo en que se funda este demanda ejecutiva la sentencia referida en el párrafo anterior.

El fallo de la sentencia cuya ejecución solicito establece que [COMPLETAR]. Se dirige, en consecuencia, esta demanda a obtener la tutela judicial de [COMPLETAR].

Han transcurrido más de veinte días hábiles desde la firmeza de la sentencia sin que el condenado al pago haya cumplido voluntariamente el contenido de la condena impuesta.

Siendo el título ejecutivo una sentencia (o una resolución judicial o arbitral o que apruebe la transacción acordada en el proceso), no procede requerimiento de pago al deudor para proceder al embargo de sus bienes —artículo 580 de la LEC—.

Detallo los siguientes bienes del ejecutado susceptibles de embargo:

[Detallar según el orden legal

—artículo 592 de la LEC—:

1. Dinero

2. Cuentas corrientes(determinar número y entidad).

3. ().

(En caso de que se solicite el embargo de inmuebles se podrán adjuntar notas registrales: Acompaño reseñados como documentos núm.1 a notas registrales acreditativas de la inscripción de inmuebles de la titularidad del ejecutado).

(En caso de que proceda:)

Los bienes detallados en el ordinal precedente no resultan suficientes para cubrir las sumas reclamadas, por lo que para la localización de bienes del ejecutado con los que hacer frente a su obligación de pago solicito que se practiquen las siguientes medidas de investigación judicial [detallar las que convengan. Por ejemplo:

a) ()

b) Que por el Tribunal se practique acceso telemático a al punto neutro de información judicial en averiguación de los ingresos, capital y bienes de los que es titular el demandado

c) Que se requiera al ejecutado D para que manifieste bienes y derechos suficientes para cubrir la cuantía de la ejecución, en la forma prevista en el artículo 589 de la LECy bajo los apercibimientos previstos en dicho precepto.

d) ()].

Por todo lo expuesto,

Suplico al Tribunal que tenga por presentado este escrito, documentos y copias de todo ello, se sirva admitirlo, teniendo por formulada demanda ejecutiva contra D [COMPLETAR], ya circunstanciado, en solicitud de ejecución de la sentencia núm [Nº DE RESOLUCIÓN] de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] dictada en los autos de juicio [COMPLETAR] núm / de este Tribunal, la admita a trámite y acuerde impulsar su tramitación pertinente, para [COMPLETAR], en definitiva, acordar:

1.º Dictar, sin requerimiento de pago al ejecutado, auto conteniendo orden general de ejecución, mediante el que se determine que se despacha ejecución en favor de la firmante y contra el demandado D [COMPLETAR] al objeto de la tutela judicial de la restitución de mi crédito por el principal de [IMPORTE] euros, más otros [IMPORTE] euros que por el momento y sin perjuicio de liquidación ulterior se consideran bastantes para intereses, gastos y costas.

2.º Que se decrete por el Letrado de la Administración de Justicia, una vez dictado el auto señalado en el ordinal anterior, decreto acordando el embargo de los bienes del demandado detallados en el cuerpo del presente escrito (o que se adopten las siguientes medidas ejecutivas:) y se practiquen las medidas de averiguación judicial de bienes propuestas,

3.º Dictando en su día, si mediare oposición, y previa la tramitación oportuna, auto mediante el que se declare procedente que la ejecución siga adelante, y acordando, en todo caso, hacer trance y remate de los bienes embargados y pagarme con el importe obtenido el principal reclamado, intereses, gastos y las costas causadas y que se causen hasta el completo pago que expresamente se impondrán al ejecutado.

Por ser Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
