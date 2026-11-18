---
name: separacion-mutuo-acuerdo-sin-hijos-demanda-682
description: "Redacta el escrito «Separación de mutuo acuerdo sin hijos: demanda» (formulario 682 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Separación de mutuo acuerdo sin hijos: demanda

> Formulario 0682 del plugin **Familia** · revisado el 17-11-2026.

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

- Contiene la nota «las referencias a Juzgados se entenderán sustituidas por Tribunales de Instancia cuando estos se constituyan»: la DT 1.ª LO 1/2025 terminó la transformación el 31-12-2025; suprimir la nota y usar la denominación de Sección.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Nº
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… HECHOS D. y Dña. contrajeron matrimonio»; «…, en»; «…, en [COMPLETAR] con fecha de»; «…con fecha de [COMPLETAR] de»; «…n fecha de [COMPLETAR] de [COMPLETAR] de»; «…, de la ciudad de»; «…, de la ciudad de [COMPLETAR], al tomo»; «…l régimen económico matrimonial es el de»; «…de la ciudad de»; «…ción del matrimonio existente entre doña»; «…y don»; «… a [DÍA] de [MES] de [AÑO]. Fdo. Letrado»; …

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 82 del Código Civil
- art. 82 del Código Civil
- art. 769.2 y 777 de la LEC
- art. 777 LEC
- art. 777 de la LEC
- art. 82.1 del Código Civil
- art. 90 del Código Civil
- Ley 8/2021
- Ley 15/2015

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

### Formulario 0682 · Separación de mutuo acuerdo sin hijos: demanda

- Año del modelo: 2015
- Revisión 17-11-2026: 6 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 20 campos de relleno marcados en blanco; 4 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº)
- Avisos de la revisión: Contiene la nota «las referencias a Juzgados se entenderán sustituidas por Tribunales de Instancia cuando estos se constituyan»: la DT 1.ª LO 1/2025 terminó la transformación el 31-12-2025; suprimir la nota y usar la denominación de Sección.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario en proceso de revisión por LO 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia

Todas las referencias a Juzgados contenidas en este documento se entenderán sustituidas por Tribunales de Instancia cuando estos se constituyan [NOTA DE REVISIÓN: Nota desfasada: la DT 1.ª LO 1/2025 fijó la última transformación de juzgados en Secciones el 31-12-2025; hoy todos los TI están constituidos. Suprimir la nota y usar directamente la denominación de Sección. Fuente: LO 1/2025 DT 1.ª (BOE-A-2025-76).], conforme al régimen transitorio que prevé la DT 1ª LO 1/2025

Véase el formulario Supuesto de cumplimiento de requisito de procedibilidad (MASC)

A LA SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Si en el partido no hay Sección de Familia, Infancia y Capacidad, dirigir a la Sección Civil (o Única) (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76); LO 1/2025 DA 1.ª (referencias a Juzgados = Secciones del TI) (BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS] Procurador de los Tribunales en representación de Dña. [NOMBRE Y APELLIDOS] y de D. [NOMBRE Y APELLIDOS], según acredito mediante copia de escritura de poder que debidamente bastanteada acompaño en forma, ante el Tribunal comparezco y

DIGO:

Que en la representación que ostento deduzco demanda de SEPARACIÓN MATRIMONIAL DE MUTUO ACUERDO de los cónyuges D. y Dña. [NOMBRE Y APELLIDOS], ejercitando la acción prevista en el artículo 82 del Código Civil, en base a los siguientes

HECHOS

D. y Dña. contrajeron matrimonio [COMPLETAR], en [COMPLETAR] con fecha de [COMPLETAR] de [COMPLETAR] de [COMPLETAR], según acredito mediante la certificación de la inscripción de matrimonio que se acompaña con documento número [Nº DE DOCUMENTO], inscrito en el Registro Civil de [LOCALIDAD], de la ciudad de [COMPLETAR], al tomo [COMPLETAR], página

El régimen económico matrimonial es el de [COMPLETAR]

El matrimonio no ha tenido hijos.

A causa de divergencias nacidas por motivos personales e íntimos que por su naturaleza no se considera necesario relatar, la continuación de la vida en común se ha hecho imposible así como la vida matrimonial y familiar.

El último domicilio conyugal estuvo situado en la casa núm. calle [CALLE] de la ciudad de [COMPLETAR]

Los cónyuges han decido de común acuerdo solicitar la separación matrimonial, adjuntando el oportuno CONVENIO REGULADOR, que se acompaña como documento número [Nº DE DOCUMENTO], donde se establecen las cláusulas por las que van a regirse los efectos de la separación.

A los anteriores hechos le son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

Es competente el Letrado de la Administración de Justicia del Tribunal de Instancia a quien por turno corresponda, al amparo del art. 82 del Código Civil en relación con el art. 769.2 y 777 de la LEC, al ser competente el Tribunal de Instancia del último domicilio común o el del domicilio de cualquiera de los solicitantes (el art. 777 LEC, en la redacción dada por la Ley 8/2021, de 2 de junio). [NOTA DE REVISIÓN (comprobar): El art. 769 LEC conserva la redacción de la Ley 15/2015; el art. 777 sí fue modificado por la Ley 8/2021 (apartados 5, 8 y 10). Revisar que la frase siga leyendo bien. Fuente: LEC 1/2000 (BOE-A-2000-323) art. 769 (redacción Ley 15/2015) y art. 777 (redacción Ley 8/2021 (BOE-A-2021-9233)).]

Procedimiento

Debe seguirse el procedimiento de mutuo acuerdo regulado en el art. 777 de la LEC, en especial los apartados 4 y 10 del citado precepto, al ser competencia del Letrado de la Administración de Justicia.

Legitimación

Los cónyuges están legitimados activamente para ejercitar la acción personal de separación matrimonial.

Separación matrimonial

El art. 82.1 del Código Civil, redactado por Ley 15/2015 y modificado por la Ley 8/2021 de 2 de junio, dispone que:

“1.- Los cónyuges podrán acordar su separación de mutuo acuerdo transcurridos tres meses desde la celebración del matrimonio mediante la formulación de un convenio regulador ante el letrado de la Administración de Justicia o en escritura pública ante Notario, en el que, junto a la voluntad inequívoca de separarse, determinarán las medidas que hayan de regular los efectos derivados de la separación en los términos establecidos en el artículo 90. Los funcionarios diplomáticos o consulares, en ejercicio de las funciones notariales que tienen atribuidas, no podrán autorizar la escritura pública de separación. Los cónyuges deberán intervenir en el otorgamiento de modo personal, sin perjuicio de que deban estar asistidos por letrado en ejercicio, prestando su consentimiento ante el letrado de la Administración de Justicia o notario. Igualmente los hijos mayores o menores emancipados deberán otorgar el consentimiento ante el letrado de la Administración de Justicia o Notario respecto de las medidas que les afecten por carecer de ingresos propios y convivir en el domicilio familiar.

2. No será de aplicación lo dispuesto en este artículo cuando existan hijos en la situación a la que se refiere el artículo anterior”.

En el caso, se dan los requisitos para la separación al haber transcurrido en exceso los tres meses desde la celebración del matrimonio y acompañarse convenio regulador con las menciones exigidas en el art. 90 del Código Civil.

Por todo lo cual,

SUPLICO AL TRIBUNAL: que, teniendo por presentado este escrito inicial, con los documentos y copias que se acompañan, y por instada de común acuerdo la separación del matrimonio existente entre doña [COMPLETAR] y don [COMPLETAR], se sirva admitirlo, seguir el trámite establecido en el artículo 777 LECiv, acordar que los interesados presten su consentimiento de forma personal en la separación y en el convenio que se presenta, y dictar decreto por el que se acuerde la separación del matrimonio formado por los solicitantes, y aprobando el Convenio regulador que se acompaña.

Es justicia que pido, en [LUGAR], a [DÍA] de [MES] de [AÑO].

Fdo. Letrado [COMPLETAR] Fdo. Procurador [COMPLETAR]

Coleg. núm. Coleg. núm. [Nº]

========================================================================
