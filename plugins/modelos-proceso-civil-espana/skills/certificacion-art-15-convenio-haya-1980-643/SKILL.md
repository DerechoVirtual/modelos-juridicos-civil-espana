---
name: certificacion-art-15-convenio-haya-1980-643
description: "Redacta el escrito «Certificación del art. 15 del Convenio de La Haya de 1980» (formulario 643 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Certificación del art. 15 del Convenio de La Haya de 1980

> Formulario 0643 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] FECHA (5 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] NÚMERO
- [ ] Nº (3 veces)
- [ ] Nº DE DOCUMENTO
- [ ] Nº DE PROCEDIMIENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 34 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…Don»; «…en la representación que ostento de Doña»; «…rado de la Administración de Justicia de»; «…, y bajo la dirección Letrada de Don»; «…numeración del juzgado de procedencia).]»; «…edite la ilicitud del traslado del menor»; «…, nacido el día [FECHA] de»; «… nacido el día [FECHA] de [COMPLETAR] de»; «…de [COMPLETAR], al Estado de»; «… al Estado de [COMPLETAR] por parte de D»; «…, con último domicilio en España, en»; …

## Correcciones de la revisión (4)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 749 de la LEC

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

### Formulario 0643 · Certificación del art. 15 del Convenio de La Haya de 1980

- Año del modelo: 2015
- Revisión 17-11-2026: 4 citas normativas corregidas tras comprobarlas en el BOE; 46 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (Nº, Nº DE DOCUMENTO, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL/SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

Don [COMPLETAR], Procurador de los Tribunales, en la representación que ostento de Doña [COMPLETAR], según acredito mediante designación apud-acta otorgada ante el Letrado de la Administración de Justicia de [COMPLETAR], y bajo la dirección Letrada de Don [COMPLETAR] ante la Sección Civil del Tribunal de Instancia de [NOTA DE REVISIÓN: Un solo TI por partido judicial (art. 84.1 LOPJ): sobra «de los de». Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] que por turno de reparto corresponda (o Sección de Familia, Infancia y Capacidad) [NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).] comparezco y como mejor proceda en Derecho,

DIGO:

Que por medio del presente escrito, al amparo de lo dispuesto en el art. 778 quáter de la Ley de Enjuiciamiento Civil, solicito que se emita la certificación prevenida en el art. 15 del Convenio de la Haya de 25 de octubre de 1980 sobre los aspectos civiles de la sustracción internacional de menores, que acredite la ilicitud del traslado del menor [COMPLETAR], nacido el día [FECHA] de [COMPLETAR] de [COMPLETAR], al Estado de [COMPLETAR] por parte de D [COMPLETAR], con último domicilio en España, en [COMPLETAR], y que actualmente al parecer se encuentra en el Estado de [COMPLETAR] en el siguiente domicilio [COMPLETAR], solicitud que fundo en los siguientes

HECHOS

Mi representada ha iniciado procedimiento de restitución ante los tribunales del Estado de [LOCALIDAD] de su hijo menor [COMPLETAR], el cual fue trasladado ilícitamente por su ex pareja D [COMPLETAR], padre del citado menor, quien nació el día [FECHA], del mes de [COMPLETAR], del año [COMPLETAR], según acredito mediante certificación del Registro Civil que acompaño como documento número

El procedimiento de restitución fue iniciado por mi representada en fecha [FECHA] de [COMPLETAR] de [COMPLETAR] mediante solicitud dirigída al tribunal de [LOCALIDAD], siguiéndose con el número [NÚMERO], y en cuya tramitación se ha dictado resolución de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] requiriendo a esta parte para que obtenga de las autoridades del Estado de residencia habitual del menor una decisión o una certificación que acredite que el traslado o retención del menor era ilícito en el sentido previsto en el artículo 3 del Convenio (acompaño como documentos núm. testimonio del procedimiento de restitución y traducción realizada por el intérprete [COMPLETAR]).

La presente solicitud la dirigimos al Tribunal en tanto que ha tenido conocimiento del proceso sobre guarda y custodia del menor [COMPLETAR], siguiéndose autos con el núm. [Nº], en el que recayó sentencia firme acordando la guarda y custodia compartida (designo los citados autos a efectos acreditativos y acompaño testimonio de la sentencia como documento núm. [Nº DE DOCUMENTO]).

Mi representada y su hijo residían desde esa fecha en el domicilio de [COMPLETAR] de la localidad de [COMPLETAR], hasta que el padre trasladó al hijo común al Estado de [COMPLETAR], del que es nacional, de forma unilateral y aprovechando un fin de semana de visitas.

En efecto, y pese a lo establecido en la sentencia, mi representada ha ejercido la custodia efectiva del hijo en solitario. Ante el incumplimiento de las obligaciones parentales, mi representada instó la ejecución forzosa del pago de las pensiones económicas no satisfechas en el citado proceso de guarda y custodia núm. [Nº] seguido ante ese Tribunal, que dictó auto despachando ejecución el día [FECHA] de [COMPLETAR] de [COMPLETAR] (designo los citados autos a efectos acreditativos y acompaño testimonio del auto despachando ejecución como documento núm. [Nº DE PROCEDIMIENTO]).

A la vista de los anteriores hechos y de acuerdo al requerimiento recibido por esta parte, se insta del Tribunal este procedimiento para que certifique la ilicitud del traslado del menor al Estado [COMPLETAR], conforme previene el art. 15 del Convenido de La Haya, al darse los requisitos en el art. 3 del citado Convenio por cuanto: a) hay una clara infracción del derecho de custodia establecido judicialmente por parte del padre; b) el menor residía habitualmente con su madre; c) el derecho de custodia se ejercía de forma efectiva- y exclusiva- por parte de la madre; y d) el padre en modo alguno estaba autorizado a modificar el domicilio del menor sin el consentimiento de la madre.

A los anteriores hechos les son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia y procedimiento

Artículo 778 quáter al ser ese Tribunal el que conoció del último proceso de guarda y custodia núm. [Nº], debiendo seguir los trámites de los arts. 771 y ss de la LEC.

Legitimación e intervención del Ministerio Fiscal

Esta parte ostenta legitimación conforme al art. 778 quáter LEC, debiendo intervenir el Ministerio Fiscal según dispone el art. 749 de la LEC.

Certificación del art. 15 del Convenio de La Haya

Es de aplicación el art. 15 del Convenio de La Haya que establece que “las autoridades judiciales o administrativas de un Estado contratante, antes de emitir una orden para la restitución del menor podrán pedir que el solicitante obtenga de las autoridades del Estado de residencia habitual del menor una decisión o una certificación que acredite que el traslado o retención del menor era ilícito en el sentido previsto en el artículo 3 del Convenio, en tanto que este último precepto del Convenio establece que un traslado o retención es ilícita: a) cuando se hayan producido con infracción de un derecho de custodia atribuido, separada o conjuntamente, a una persona, a una institución, o a cualquier otro organismo, con arreglo al Derecho vigente en el Estado en que el menor tenía su residencia habitual inmediatamente antes de su traslado o retención; y b) cuando este derecho se ejercía de forma efectiva, separada o conjuntamente, en el momento del traslado o de la retención, o se habría ejercido de no haberse producido dicho traslado o retención.

En su virtud,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos acompañados y sus copias; por interpuesta por el Procurador que suscribe, con quien se entiendan las sucesivas diligencias, en nombre y representación de Doña [COMPLETAR], solicitud de certificación del art. 15 del Convenio de La Haya acreditativa de la ilicitud del traslado del hijo menor [COMPLETAR] al Estado de [COMPLETAR] por parte de D [COMPLETAR]; y previos los trámites pertinentes y con intervención del Ministerio Fiscal, emita certificación del artículo 15 del Convenio de La Haya de 25 de octubre de 1980 sobre los aspectos civiles de la sustracción internacional de menores, que acredite que el traslado o retención del citado menor era ilícito en el sentido previsto en el artículo 3 del Convenio.

Es justicia que insto en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firmas de Letrado y Procurador

========================================================================
