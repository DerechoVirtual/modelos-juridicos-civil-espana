---
name: escritura-publica-separacion-divorcio-mutuo-acuerdo-659
description: "Redacta el escrito «Escritura pública de separación o divorcio de mutuo acuerdo: solicitud» (formulario 659 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Escritura pública de separación o divorcio de mutuo acuerdo: solicitud

> Formulario 0659 del plugin **Familia** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Escritura notarial de separación/divorcio: añadir el destino de los animales de compañía si los hay (art. 90.1.b) bis CC) y recordar que el notario o el LAJ no pueden intervenir si hay hijos menores no emancipados o mayores con medidas de apoyo atribuidas a los progenitores (arts. 82.2 y 87 CC).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] PROFESIÓN (2 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO
- [ ] NOMBRE Y APELLIDOS
- [ ] Nº DE COLEGIADO
- [ ] COLEGIO
- [ ] FECHA (2 veces)
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] LOCALIDAD
- [ ] PROVINCIA
- [ ] Nº (3 veces)
- [ ] IMPORTE
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Don»; «…y Doña»; «…la esposa, vecinos de la localidad de»; «…, del mes de»; «…, del mes de [COMPLETAR], del año»; «… del año [COMPLETAR], en la localidad de»; «…égimen económico del matrimonio es el de»; «… que ambos esposos tenían vecindad civil»; «…micilio conyugal sito en la localidad de»; «…EUROS MENSUALES (- euros/mes)»; «…, que deberá ingresar Don»; «…en la cuenta de Doña»; …

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

### Formulario 0659 · Escritura pública de separación o divorcio de mutuo acuerdo: solicitud

- Año del modelo: 2015
- Revisión 17-11-2026: 28 campos de relleno marcados en blanco; 5 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE COLEGIADO, Nº DE DOCUMENTO)
- Avisos de la revisión: Escritura notarial de separación/divorcio: añadir el destino de los animales de compañía si los hay (art. 90.1.b) bis CC) y recordar que el notario o el LAJ no pueden intervenir si hay hijos menores no emancipados o mayores con medidas de apoyo atribuidas a los progenitores (arts. 82.2 y 87 CC).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Don [COMPLETAR] y Doña [COMPLETAR], mayores de edad, de profesión [PROFESIÓN] el marido y de profesión [PROFESIÓN] la esposa, vecinos de la localidad de [COMPLETAR], con domicilio en calle [CALLE], número [NÚMERO], asistidos por el Letrado D. [NOMBRE Y APELLIDOS], colegiado núm. [Nº DE COLEGIADO] del Iltre. Colegio de Abogados de [COLEGIO], por medio de la presente solicitan el otorgamiento de escritura de divorcio (o separación) de su matrimonio, de acuerdo a los siguientes

HECHOS Y FUNDAMENTOS

Que los solicitantes contrajeron matrimonio en forma (civil o religiosa que corresponda), el día [FECHA], del mes de [COMPLETAR], del año [COMPLETAR], en la localidad de [COMPLETAR], conforme acredito mediante certificación literal de matrimonio expedida por el Registro civil, que acompaño se acompaña como documento núm. [Nº DE DOCUMENTO]

Los solicitantes no tienen hijos ( acompaño libro de familia como documento núm. [Nº DE DOCUMENTO]).

El domicilio común está sito en [LOCALIDAD], según consta en la certificación de empadronamiento que se acompaña como documento núm. [Nº DE DOCUMENTO]

El régimen económico del matrimonio es el de [COMPLETAR], ya que ambos esposos tenían vecindad civil [COMPLETAR] cuando contrajeron matrimonio y no se han otorgado capitulaciones matrimoniales.

Es voluntad de ambos solicitantes acordar notarialmente de mutuo acuerdo el divorcio (o separación matrimonial) mediante la formalización del correspondiente convenio regulador, con arreglo a los siguientes PACTOS:

1) DE LA DISOLUCIÓN POR DIVORCIO: Ambos cónyuges, acuerdan con carácter definitivo la disolución por divorcio de su matrimonio, y declaran que nada tienen que decirse ni reclamarse por razón del divorcio y de sus causas, salvo lo que en el presente documento se determina.

2) DEL DOMICILIO CONYUGAL Y AJUAR FAMILIAR. El uso y disfrute del domicilio conyugal sito en la localidad de [COMPLETAR], provincia de [PROVINCIA], calle [CALLE], núm. [Nº], queda atribuido a la esposa durante un plazo de [Nº] meses, hasta el día [FECHA] en que deberá desalojarlo. A partir de dicho momento, los esposos procederán a la venta del domicilio conyugal del que son copropietarios.

La hipoteca que grava la vivienda del hasta ahora domicilio conyugal será pagada por mitad por ambos progenitores, así como el Impuesto sobre Bienes Inmuebles (IBI) y cualquier otro importe que tenga su origen en la propiedad del inmueble. Por otra parte, los servicios de suministros y mantenimiento de la finca serán a cargo de la esposa en el periodo atribuido el uso y disfrute.

En cuanto al ajuar doméstico y objetos de uso ordinario que se encuentran en el domicilio conyugal, nada cabe acordar, dado que ya han sido previamente repartidos de común acuerdo entre ambos consortes con anterioridad a la firma del presente documento.

3) DE LA PENSIÓN COMPENSATORIA. Se establece como pensión compensatoria en favor de la esposa la cantidad de [IMPORTE] EUROS MENSUALES (- euros/mes) [COMPLETAR], que deberá ingresar Don [COMPLETAR] en la cuenta de Doña [COMPLETAR] núm. [Nº], de la entidad financiera [COMPLETAR], y que deberá actualizar anualmente, cada mes de enero, a partir del mes de enero del año [COMPLETAR], conforme al Índice Oficial de precios al Consumo para el conjunto del Estado.

4) DE LA DISOLUCIÓN DEL RÉGIMEN ECONÓMICO MATRIMONIAL. Dado que el régimen económico es el de sociedad de gananciales, y que los únicos bienes que lo conforman son el domicilio que ha venido siendo conyugal y muebles constitutivos del ajuar doméstico, ambas partes consideran oportuno diferir su liquidación al momento en que dichos bienes dejen de quedar afectados del derecho de uso anteriormente establecido y se proceda a la enajenación del inmueble.

Una vez enajenado, la cantidad líquida resultante será repartida por mitad entre ambos cónyuges.

De conformidad a lo dispuesto en el art. 54 de la Ley del Notariado, se solicita que por V.I. se disponga lo necesario para el otorgamiento de la correspondiente escritura pública en el día y hora que se indique en que comparecerán ambos cónyuges, asistido del letrado que asimismo suscribe, para prestar su consentimiento.

Por lo expuesto,

RUEGO A V.I. que tenga por formulada esta solicitud y autorice el otorgamiento de escritura pública de divorcio de mutuo acuerdo con el convenio regulador que se deja interesado.

Lugar, fecha y firma de los solicitantes y letrado

========================================================================
