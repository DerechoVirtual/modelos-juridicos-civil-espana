---
name: divorcio-mutuo-acuerdo-division-cosa-comun-demanda-201
description: "Redacta el escrito «Divorcio de mutuo acuerdo con división de cosa común: demanda (Cataluña)» (formulario 201 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Divorcio de mutuo acuerdo con división de cosa común: demanda (Cataluña)

> Formulario 0201 del plugin **Familia** · revisado el 17-11-2026.

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

- MASC mal fundado: invoca el art. 89.9 LOPJ (veto de MASC en violencia sobre la mujer) en un divorcio de mutuo acuerdo sin violencia. Justificar el requisito como cumplido por la negociación directa plasmada en el convenio (arts. 5.1 y 10.2 LO 1/2025).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] LOCALIDAD (4 veces)
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…bunales en nombre y representación de Dª»; «…y D»; «…y D [COMPLETAR], la Sra»; «…con domicilio en [LOCALIDAD] y el Sr»; «…y el Sr [COMPLETAR] vecino de»; «…matrimonio contraído por los cónyuges Dª»; «…y D»; «…os cónyuges contrajeron matrimonio el en»; «…monio nacieron y viven en la actualidad,»; «…y»; «…[COMPLETAR] nacidos, respectivamente, el»; «…, y el»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 86.5.a) LOPJ
- art. 81 del Código Civil
- art. 89.9 LOPJ

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

### Formulario 0201 · Divorcio de mutuo acuerdo con división de cosa común: demanda (Cataluña)

- Año del modelo: 2020
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 23 campos de relleno marcados en blanco
- Avisos de la revisión: MASC mal fundado: invoca el art. 89.9 LOPJ (veto de MASC en violencia sobre la mujer) en un divorcio de mutuo acuerdo sin violencia. Justificar el requisito como cumplido por la negociación directa plasmada en el convenio (arts. 5.1 y 10.2 LO 1/2025).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

D/Dª [NOMBRE Y APELLIDOS], Procurador de los Tribunales en nombre y representación de Dª [COMPLETAR] y D [COMPLETAR], la Sra [COMPLETAR] con domicilio en [LOCALIDAD] y el Sr [COMPLETAR] vecino de [COMPLETAR], ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que mediante el presente escrito, y al amparo de lo dispuesto en el artículo 777 y preceptos concordantes de la Ley de Enjuiciamiento Civil, se formula DEMANDA DE DIVORCIO DE MUTUO ACUERDO del matrimonio contraído por los cónyuges Dª [COMPLETAR] y D [COMPLETAR], en base a los siguientes

HECHOS

PRIMERO.- Los cónyuges contrajeron matrimonio el

 en [COMPLETAR] inscrito en el Registro Civil de [LOCALIDAD], según consta en la certificación literal de matrimonio que se aporta como documento núm. uno, procediendo a separarse de hecho en fecha [FECHA].

SEGUNDO.- Del citado matrimonio nacieron y viven en la actualidad, [COMPLETAR] y [COMPLETAR] nacidos, respectivamente, el [COMPLETAR], y el [COMPLETAR], según acredito mediante las respectivas certificaciones literales de nacimiento expedidas por el Registro civil de [LOCALIDAD], que acompaño como documentos núms. dos y tres.

TERCERO.- El domicilio familiar está sito en [LOCALIDAD]

[NOMBRE Y APELLIDOS], según acredito mediante certificación de empadronamiento, que acompaño como documento núm. cuatro.

CUARTO.- El régimen económico del matrimonio es el separación de bienes, ya que ambos esposos tenían vecindad civil catalana cuando contrajeron matrimonio y no se han otorgado capitulaciones matrimoniales.

QUINTO.- Siendo voluntad de ambas partes proceder a la disolución por divorcio de mutuo acuerdo, acompañan como documentos núm. cinco y seis, la preceptiva propuesta de convenio regulador y plan de parentalidad, a fin de que, previa su ratificación por separado, e Informe del Ministerio Fiscal, sea aprobado judicialmente y queden regulados conforme al mismo los efectos derivados de dicha disolución.

SEXTO.- El convenio regulador contiene los pactos sobre la división de los bienes en comunidad ordinaria de ambos cónyuges, cuya aprobación se solicita expresamente al amparo de lo establecido en el art. 233-2, apartado 5, del CCCat.

FUNDAMENTOS DE DERECHO

PRIMERO.- Competencia y procedimiento. Es competente este Tribunal por razón del domicilio conyugal, conforme prevé el artículo 769.1 de la Ley de Enjuiciamiento Civil, en relación con lo dispuesto en el art. 86.5.a) LOPJ, debiendo seguirse el procedimiento previsto en el articulo 777 de la citada Ley procesal.

SEGUNDO.- Legitimación. La ostentan ambas partes por su condición de cónyuges del matrimonio cuyo divorcio de mutuo acuerdo se solicita, de conformidad con lo previsto en el art. 81 y 86 del Código civil.

TERCERO.- Divorcio de mutuo acuerdo.

Artículo 86 en relación con el art. 81 del Código civil (o artículo 82 en relación con el art. 81 del Código Civil en caso de mutuo acuerdo).

CUARTO.- Cumplimiento de los requisitos de procedibilidad

La presente demanda no está sujeta al previo intento de resolución de controversias en vía no jurisdiccional, por cuanto el art. 89.9 LOPJ excluye de los MASC los procesos derivados de crisis familiares en casos de violencia sobre la mujer [NOTA DE REVISIÓN: Fundamento erróneo en un mutuo acuerdo sin violencia: el art. 89.9 LOPJ solo veda los MASC en los asuntos de violencia sobre la mujer (art. 89.7). Mejor justificar el requisito como cumplido por la negociación directa plasmada en el convenio (arts. 5.1 y 10.2 LO 1/2025). Fuente: LOPJ art. 89.7 y 89.9 (redacc. LO 1/2025) y LO 1/2025 arts. 5.1 y 10.2.].

QUINTO.- Efectos derivados o medidas.

Artículo 233-2 del Código Civil de Cataluña. En cumplimiento de dicho precepto se acompaña convenio regulador que recoge el contenido mínimo fijado en dicho precepto, incluyendo plan de parentalidad, de acuerdo con lo establecido en el artículo 233-9.

SEXTO.- Audiencia de los menores e intervención del Ministerio Fiscal.

Artículos 749. 2 y 777.5 de la L.E.C.

SÉPTIMO.- División de bienes en comunidad ordinaria indivisa.

Artículo 233-2, apartado 5, del Código Civil de Cataluña, en relación con el art. 437.4.4ª de la LEC, en cuanto a la división del inmueble propiedad pro indiviso de ambos cónyuges.

En su virtud

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos acompañados y lo admita; por promovido por el Procurador que suscribe, con quien se entiendan las sucesivas diligencias, en nombre y representación de Don [COMPLETAR] y Doña [COMPLETAR], con devolución de la escritura de poderes acompañada una vez quede testimonio en autos, petición de DISOLUCIÓN MATRIMONIAL POR DIVORCIO DE MUTUO ACUERDO; y, por los trámites procesales pertinentes, previa ratificación de las partes por separado, audiencia de los menores y con intervención del Ministerio Fiscal, dicte sentencia por la que, dando lugar a la disolución, determine como efectos derivados de la misma los contenidos en la propuesta de convenio regulador aportado como documento núm. cinco, el cual sea íntegramente aprobado.

Es justicia que insto en [LUGAR], a [FECHA].

Firma de Abogado y Procurador.
