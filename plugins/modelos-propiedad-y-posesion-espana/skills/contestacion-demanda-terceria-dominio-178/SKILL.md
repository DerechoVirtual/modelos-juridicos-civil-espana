---
name: contestacion-demanda-terceria-dominio-178
description: "Redacta el escrito «Contestación a la demanda de tercería de dominio» (formulario 178 de propiedad y derechos reales, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a la demanda de tercería de dominio

> Formulario 0178 del plugin **Propiedad y derechos reales** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] Nº (2 veces)
- [ ] AÑO (3 veces)
- [ ] FECHA (3 veces)
- [ ] NÚMERO (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…rtenece realmente al ejecutado, dado que»; «…constante en el tiempo del ejecutado Don»; «…scrito en el Registro de la Propiedad de»; «…e tiene constituida con el ejecutado Don»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 255.1 LEC
- art. 596.2 LEC
- arts. 418.2 y 438.10 LEC
- art. 394.1 LEC

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

### Formulario 0178 · Contestación a la demanda de tercería de dominio

- Año del modelo: 2021
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 15 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de contestación a demanda de tercería de dominio con fundamento en que el bien embargado pertenece realmente al ejecutado.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, que actúa en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según tengo acreditado mediante copia de la escritura de poder que se acompañó y cuya copia está testimoniada en los autos principales de Ejecución de título judicial nº [Nº]/[AÑO], seguidos a mi instancia contra D./Dña. [NOMBRE Y APELLIDOS] y otros, en la pieza de Tercería de Dominio nº [Nº]/[AÑO], ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que mediante el presente escrito y dentro del término conferido por decreto de fecha [FECHA], paso a contestar la demanda de tercería de dominio formulada de adverso, oponiéndome a la misma en base a los siguientes:

HECHOS

PRIMERO.- Se acepta el correlativo de la demanda, en cuanto refiere el hecho del embargo acordado por el Tribunal al que me dirijo en el procedimiento arriba referenciado, sobre el bien que en el mismo se menciona.

No se aceptan, por no ajustarse a la realidad, los demás hechos en los que funda el actor la pretensión de alzamiento del embargo, en cuanto se oponen a lo que posteriormente se dirá.

SEGUNDO.- El bien embargado con fecha [FECHA] pertenece realmente al ejecutado, dado que [COMPLETAR]

TERCERO.- El dominio del bien objeto de embargo es constante en el tiempo del ejecutado Don [COMPLETAR] desde fecha [FECHA], momento en el que lo adquirió mediante contrato de compraventa elevado a público y debidamente inscrito en el Registro de la Propiedad de [COMPLETAR], sin que con posterioridad haya realizado transmisión alguna, careciendo de toda credibilidad y validez el documento privado que aporta la adversa pues hay indicios racionales para considerar que se ha realizado dicho documento privado con posterioridad para enmascarar la realidad, pues el documento que se acompaña a la demanda con el nº [NÚMERO], consiste en un simple escrito redactado por el actor en el que se describen las circunstancias de la supuesta adquisición por el mismo del bien embargado. Se trata de un documento elaborado unilateralmente por el propio demandante con el único objeto de presentarlo en este procedimiento y que, por ello mismo, no puede merecer la conceptuación de «principio de prueba por escrito».

CUARTO.- Aparte de no haberse acreditado inicialmente la legitimación del demandante, ya que el documento aportado por el mismo carece de toda fiabilidad, dicho señor no tiene la condición de tercero en el proceso de ejecución en el que se acordó el embargo del bien que dice pertenecerle.

En el caso de ser cierto cuanto se expresa en el citado documento, el bien que dice haber adquirido lo habría sido para la comunidad de bienes que tiene constituida con el ejecutado Don [COMPLETAR] para la explotación de la actividad comercial en la que se generó, precisamente, la deuda cuyo impago ha dado lugar al título que se ejecuta en los autos

A estos hechos le son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA Y PROCEDIMIENTO.

Debe mostrarse conformidad con la competencia, genérica y objetiva del Tribunal a que se ha dirigido la entidad actora, y asimismo con que el proceso adecuado es el juicio verbal, señalado por la actora en el correlativo de la demanda.

II.- LEGITIMACIÓN.

Se denuncia la falta de legitimación del demandante.

El demandante Sr. carece de legitimación para promover la presente tercería al no tener la condición de tercero, de conformidad con lo dispuesto en el art. 595.1 en relación con el 538.2 LEC.

III.- CUANTÍA.

Nada que oponer a la cuantificación que hace la demanda del interés litigioso, conforme al valor catastral del año pasado que tiene fijada la Hacienda, dado que el art. 255.1 LEC, sólo habilita para impugnar la cuantía cuando la determinación inadecuada provocara la elección indebida del cauce procesal, o viabiliza la recurribilidad en apelación, ninguna de las dos cosas que ocurre.

IV.- PROCEDIBILIDAD.

Al no acompañarse con la demanda un documento que constituya propiamente un «principio de prueba», la misma no debió ser admitida a trámite por el Tribunal (art. 596.2 LEC). Si bien, en el caso de que se considere que se trata de un defecto subsanable, podría concedérsele al actor, en su momento, un plazo para que lo intentara, acordando, si no lo hiciere, el sobreseimiento del proceso conforme a lo establecido en el art. 425 en relación con los arts. 418.2 y 438.10 LEC.

V.- FONDO DE LA RECLAMACIÓN.

Son de aplicación los fundamentos alegados de adverso, si bien en su correcta interpretación, de donde resulta la improcedencia de la pretensión sostenida de contrario.

Como se desprende de los hechos expuestos en la presente contestación y se acreditará, en su momento, mediante la articulación de la prueba testifical que a tal fin será propuesta, el bien embargado en el proceso de ejecución que el Tribunal tramita con el nº [NÚMERO] lo fue correctamente, por ser en aquella fecha de la pertenencia del ejecutado.

VI.- COSTAS.

Las costas procesales deberán ser impuestas a la entidad demandante, conforme al criterio cuasiobjetivo del art. 394.1 LEC, como procede según remisión por el art. 603 II LEC.

En su virtud,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito con sus documentos y copias, se sirva admitir uno y otros, y se tenga a mi representado por opuesto a la tercería de dominio, y por contestada la demanda y, seguido el proceso por todos sus trámites, se venga a dictar auto íntegramente desestimatorio de los pedimentos deducidos en la demanda, manteniendo la traba y prosiguiendo el proceso de ejecución, con expresa imposición de costas a la parte actora.

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del Abogado	Firma del Procurador
