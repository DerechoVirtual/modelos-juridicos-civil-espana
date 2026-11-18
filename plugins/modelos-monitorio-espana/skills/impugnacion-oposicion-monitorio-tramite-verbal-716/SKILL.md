---
name: impugnacion-oposicion-monitorio-tramite-verbal-716
description: "Redacta el escrito «Impugnación de la oposición al monitorio por el trámite del verbal» (formulario 716 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Impugnación de la oposición al monitorio por el trámite del verbal

> Formulario 0716 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] Nº (3 veces)
- [ ] FECHA (3 veces)
- [ ] Nº DE DOCUMENTO
- [ ] IMPORTE (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…represento, que acompaño como documentos»; «…aportó con la solicitud, como documentos»; «…A LA OPOSICIÓN deducida por el demandado»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 818.2 de la LEC
- artículo 394 LEC

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

### Formulario 0716 · Impugnación de la oposición al monitorio por el trámite del verbal

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 15 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D. [NOMBRE Y APELLIDOS] Procurador de los Tribunales, actuando en representación de [NOMBRE DEL REPRESENTADO/A], parte actora en el procedimiento monitorio arriba expresado, transformado en el proceso declarativo verbal núm. [Nº], comparezco y, como mejor proceda en Derecho, DIGO:

Que habiéndose dado traslado a esta parte del decreto y de la oposición deducida por D. [NOMBRE Y APELLIDOS] en el procedimiento monitorio núm. [Nº], de conformidad a lo que dispone el art. 818.2 de la LEC, paso a formular escrito de IMPUGNACIÓN A LA OPOSICIÓN, la cual baso en los siguientes

HECHOS

Negamos los hechos relatados en la oposición del demandado

En primer lugar, el demandado niega que contratara con mi representada, cuando en nuestra solicitud de procedimiento monitorio se explica suficientemente, además de ser un hecho notorio, que la entidad que representado había procedido el día [FECHA] a fusionarse como sociedad absorbente con la entidad, como sociedad absorbida, adjuntándose la correspondiente escritura de fusión de sociedades como documento núm. [Nº DE DOCUMENTO].

Pero es más, el demandado conocía perfectamente esta situación, puesto que se le han remitido varios recibos de liquidación en su cuenta corriente por parte de la entidad que represento, que acompaño como documentos [COMPLETAR], lo que demuestra que conocía que había contratado con mi representada.

El demandado se opone asimismo al entender que la liquidación practicada no se corresponde con disposiciones realizadas en la cuenta, cuando ya se aportó con la solicitud, como documentos [COMPLETAR], la certificación del saldo deudor de [IMPORTE] euros, así como el detalle de operaciones realizadas por el demandado.

Todo ello le fue comunicado en fecha [FECHA] por burofax que se aporta como documento núm. [Nº], figurando en los detalles de liquidación las distintas operaciones efectuadas en la cuenta, sin que el demandado opusiera objeción alguna a dicha liquidación en ningún momento.

Como se puede comprobar, el seguimiento de los detalles de liquidación permitía al demandado impugnar aquellas operaciones que considerara no habían sido realizadas, cosa que no ha hecho en ningún momento, limitándose a negar genéricamente la deuda en el escrito de oposición que impugnamos.

Por todo ello, la oposición debe ser desestimada, debiendo condenarse al demandado en los términos interesados en nuestra petición inicial.

FUNDAMENTOS DE DERECHO

En cuanto al procedimiento, el art. 818.2 de la LEC establece que, cuando la cuantía de la pretensión no excediera de la propia del juicio verbal, el letrado o la letrada de la Administración de Justicia dictará decreto dando por terminado el proceso monitorio y acordando seguir la tramitación conforme a lo previsto para este tipo de juicio, dando traslado de la oposición al actor, quien podrá impugnarla por escrito en el plazo de diez días. Presentado el escrito de impugnación o transcurrido el plazo sin haberse efectuado, se dictará diligencia de ordenación acordando conceder a ambas partes el plazo de cinco días a fin de que propongan la prueba que quieran practicar, debiendo, igualmente, indicar las personas que, por no poderlas presentar ellas mismas, han de ser citadas por el letrado o la letrada de la Administración de Justicia a la vista para que declaren en calidad de parte, testigos o peritos. A tal fin, facilitarán todos los datos y circunstancias precisos para llevar a cabo la citación y podrán pedir respuestas escritas a cargo de personas jurídicas o entidades públicas, por los trámites establecidos en el artículo 381, continuando el procedimiento por los trámites del artículo 438.9 y siguiente LEC.

En cuanto al fondo de la reclamación, son de aplicación los preceptos invocados en nuestra solicitud, en especial los arts. 1101 y concordantes del Código Civil al existir un incumplimiento contractual por parte del demandado.

Las costas deben imponerse al demandado, de conformidad con lo dispuesto en el artículo 394 LEC.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL: que teniendo por presentado este escrito, con sus documentos, y copias de todo ello, se sirva admitirlo, y tenga por formulada IMPUGNACIÓN A LA OPOSICIÓN deducida por el demandado [COMPLETAR] y, tras los trámites legales, dicte Sentencia condenado al demandado a que indemnice a mi representada en la cantidad de [IMPORTE] euros, con más los intereses de demora al % desde el día [FECHA], todo ello con expresa imposición de costas al citado demandado.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado / Firma de Procurador

========================================================================
