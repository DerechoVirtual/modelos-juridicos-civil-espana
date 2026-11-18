---
name: declarar-ilicito-traslado-retencion-menor-otro-estado-642
description: "Redacta el escrito «Declarar ilícito el traslado o retención de un menor en otro Estado» (formulario 642 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Declarar ilícito el traslado o retención de un menor en otro Estado

> Formulario 0642 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] SEDE (2 veces)
- [ ] FECHA (5 veces)
- [ ] NÚMERO
- [ ] Nº
- [ ] Nº DE PROCEDIMIENTO
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 32 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Don»; «…en la representación que ostento de Doña»; «…rado de la Administración de Justicia de»; «…, y bajo la dirección Letrada de Don»; «…clare la ilicitud del traslado del menor»; «…, nacido el día [FECHA] de»; «… nacido el día [FECHA] de [COMPLETAR] de»; «…de [COMPLETAR], al Estado de»; «… al Estado de [COMPLETAR] por parte de D»; «…, con último domicilio en España, en»; «… al parecer se encuentra en el Estado de»; «…en el siguiente domicilio»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (6)

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

### Formulario 0642 · Declarar ilícito el traslado o retención de un menor en otro Estado

- Año del modelo: 2015
- Revisión 17-11-2026: 4 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 42 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 2 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

Don [COMPLETAR], Procurador de los Tribunales, en la representación que ostento de Doña [COMPLETAR], según acredito mediante designación apud-acta otorgada ante el Letrado de la Administración de Justicia de [COMPLETAR], y bajo la dirección Letrada de Don [COMPLETAR] ante la Sección Civil del Tribunal de Instancia de [NOTA DE REVISIÓN: Un solo TI por partido judicial (art. 84.1 LOPJ): sobra «de los de». Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] que por turno de reparto corresponda (o Sección de Familia, Infancia y Capacidad) [NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).] comparezco y como mejor proceda en Derecho,

DIGO:

Que por medio del presente escrito, al amparo de lo dispuesto en el art. 778 quáter de la Ley de Enjuiciamiento Civil, solicito que se declare la ilicitud del traslado del menor [COMPLETAR], nacido el día [FECHA] de [COMPLETAR] de [COMPLETAR], al Estado de [COMPLETAR] por parte de D [COMPLETAR], con último domicilio en España, en [COMPLETAR], y que actualmente al parecer se encuentra en el Estado de [COMPLETAR] en el siguiente domicilio [COMPLETAR], solicitud que fundo en los siguientes

HECHOS

Mi representada y D [COMPLETAR] formaban una unión estable de pareja hasta que se produjo su ruptura en el año [COMPLETAR] De dicha unión es el menor [COMPLETAR], nacido el día [FECHA], del mes de [COMPLETAR], del año [COMPLETAR], según acredito mediante certificación del Registro Civil que acompaño como documento número

Como consecuencia de la ruptura de la relación se siguió proceso de guarda y custodia del menor ante el Tribunal de Instancia, plaza n.º [NÚMERO], de esa [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] localidad, autos núm. [Nº], en el cual recayó sentencia de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] en la que se atribuía la guarda y custodia del menor de forma compartida a ambos progenitores, tal como se acredita por testimonio que acompaño como documento núm. con expresión de su firmeza.

Mi representada y su hijo residían desde esa fecha en el domicilio de [COMPLETAR] de la localidad de [COMPLETAR]

Pese a lo establecido en la sentencia, lo cierto es que, tras la ruptura de la unión, el padre en ningún momento se ocupó del hijo, ni contribuyó en ninguna cantidad económica, ejerciendo mi representada la custodia efectiva en solitario.

Ante el incumplimiento de las obligaciones parentales, mi representada se vio obligada a formular denuncia estando actualmente en tramitación las diligencias previas núm. [Nº DE PROCEDIMIENTO] ante la Sección de Instrucción del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], tal como acredito por testimonio de la denuncia y auto de incoación que aporto como documentos núm. [Nº DE DOCUMENTO]

El pasado día [FECHA], el padre [COMPLETAR], aprovechando una de las visitas que realizaba de forma esporádica, sin conocimiento ni consentimiento de mi representada, se llevó al menor a su Estado de origen [COMPLETAR], donde residen sus padres en el domicilio arriba expresado, donde al parecer se encuentra en la actualidad el menor desde esa fecha.

Al cabo de unos días, mi representada recibió una llamada telefónica del padre comunicando esta circunstancia y diciéndole textualmente “que el niño se quedaba a vivir con él para siempre”.

Mi representada interpuso denuncia ante la Policía en fecha [FECHA] de [COMPLETAR] de [COMPLETAR] por la sustracción del menor, y se dirigió a la autoridad central (Ministerio de Justicia), tal como se acredita por los documentos núms. que se acompañan.

A la vista de los anteriores hechos se insta este procedimiento para que se declare la ilicitud del traslado del menor al Estado [COMPLETAR] al darse los requisitos establecidos en la norma internacional aplicable (en cada caso se haría constar) que en este caso es el art. 2.2.11 del Reglamento de Bruselas II ter por cuanto: a) hay una clara infracción del derecho de custodia establecido judicialmente por parte del padre; b) el menor residía habitualmente con su madre; c) el derecho de custodia se ejercía de forma efectiva- y exclusiva- por parte de la madre; y d) el padre en modo alguno estaba autorizado a modificar el domicilio del menor sin el consentimiento de la madre.

A los anteriores hechos les son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia y procedimiento

Artículo 778 quáter en relación con el art. 769 de la Ley de Enjuiciamiento Civil, al ser el Tribunal al que me dirijo el competente para conocer del fondo del asunto, debiendo seguir los trámites de los arts. 771 y ss de la LEC.

Legitimación e intervención del Ministerio Fiscal

Esta parte ostenta legitimación conforme al art. 778 quáter LEC, debiendo intervenir el Ministerio Fiscal según dispone el art. 749 de la LEC.

Declaración de ilicitud del traslado del menor

Es de aplicación lo establecido en el art. 2.11 del Reglamento de Bruselas II, al tratarse del traslado al Estado de [COMPLETAR], perteneciente a la Unión Europea, que define el traslado como ilícito cuando: a) se haya producido con infracción de un derecho de custodia adquirido por resolución judicial, por ministerio de la ley o por un acuerdo con efectos jurídicos de conformidad con la legislación del Estado miembro en donde el menor tenía su residencia habitual inmediatamente antes de su traslado o retención, y b) este derecho se ejercía, en el momento del traslado o de la retención, de forma efectiva, separada o conjuntamente, o se habría ejercido de no haberse producido dicho traslado o retención. Se considera que la custodia es ejercida de manera conjunta cuando, en virtud de una resolución judicial o por ministerio de la ley, uno de los titulares de la responsabilidad parental no pueda decidir sin el consentimiento del otro titular sobre el lugar de residencia del menor.

En su virtud,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos acompañados y sus copias; por interpuesta por el Procurador que suscribe, con quien se entiendan las sucesivas diligencias, en nombre y representación de Doña [COMPLETAR], solicitud de declaración de ilicitud del traslado del hijo menor [COMPLETAR] al Estado de [COMPLETAR] por parte de D [COMPLETAR]; y previos los trámites pertinentes y con intervención del Ministerio Fiscal, dicte resolución que especifique que dicho traslado ha sido ilícito, con las consecuencias inherentes.

Es justicia que insto en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firmas de Letrado y Procurador

========================================================================
