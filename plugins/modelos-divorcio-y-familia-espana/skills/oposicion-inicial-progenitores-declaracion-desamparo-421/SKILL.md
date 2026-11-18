---
name: oposicion-inicial-progenitores-declaracion-desamparo-421
description: "Redacta el escrito «Oposición inicial de los progenitores a la declaración de desamparo» (formulario 421 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición inicial de los progenitores a la declaración de desamparo

> Formulario 0421 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] FECHA DE LA RESOLUCIÓN
- [ ] ÓRGANO O PERSONA
- [ ] LOCALIDAD
- [ ] FECHA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ocedimientos relativos al menor Por ello»; «…PLICO: Tenga por presentado este escrito»; «…, lo admita»; «…de [AÑO]. Firma de Abogado y Procurador»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 780.2 de la LEC

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

### Formulario 0421 · Oposición inicial de los progenitores a la declaración de desamparo

- Año del modelo: 2018
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 12 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 2 huecos del original que se habían perdido sin marca, marcados (FECHA, FECHA DE LA RESOLUCIÓN)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

ESCRITO INICIAL DE OPOSICIÓN A LA DECLARACIÓN DE DESAMPARO DE UN MENOR INTERPUESTO POR LOS PROGENITORES

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D/Dª [NOMBRE Y APELLIDOS] Procurador de los Tribunales, en nombre y representación de D/Dª [NOMBRE Y APELLIDOS] y de D/Dª [NOMBRE Y APELLIDOS], según acredito mediante designación “apud acta” otorgada ante el Letrado de la Administración de Justicia de que se acompaña, ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

HECHOS

PRIMERO.- Que se ha notificado a esta parte la resolución administrativa de fecha [FECHA DE LA RESOLUCIÓN]

dictada por [ÓRGANO O PERSONA], notificada el día, cuya copia se aporta como documento número 1 por la que se acuerda declarar en situación de desamparo al menor, hijo de mis mandantes, oponiéndose mi representado a dicha medida por no encontrarse acreditado en ningún caso dicho desamparo, no siendo pertinente la adopción de medida de ningún tipo.

SEGUNDO.- El art. 780.2 de la LEC establece que el proceso de oposición a una resolución administrativa en materia de protección de menores se iniciará mediante la presentación de un escrito inicial en el que el actor sucintamente expresará la pretensión y la resolución a que se opone. En el escrito consignará expresamente la fecha de notificación de la resolución administrativa y manifestará si existen procedimientos relativos a ese menor.

TERCERO.- Mis representados pretenden que se deje sin efecto la citada resolución de la entidad de protección de menores de la Comunidad Autónoma de [LOCALIDAD]

[NOMBRE Y APELLIDOS], por la que declaró la situación legal de desamparo del hijo de mis representados, antes citado, con asunción de su tutela legal, al existir una evolución favorable en la convivencia del menor en el entorno personal y social de su familia biológica, según consta en los diferentes informes obrantes en el expediente, donde consta asimismo la superación de las adicciones por parte del padre y la actividad laboral de ambos progenitores, así como la conveniencia e interés del menor de mantener la convivencia con sus padres y hermanos y demás familia extensa.

CUARTO.- Tal como ha quedado expresado, la fecha de notificación de la resolución administrativa fue el día [FECHA], tal como se acredita por el acuse de recibo que se acompaña como documento número 2.

QUINTO.- No consta a esta parte la existencia de otros procedimientos relativos al menor

Por ello [COMPLETAR],

AL TRIBUNAL SUPLICO: Tenga por presentado este escrito [COMPLETAR], lo admita [COMPLETAR], tenga por interpuesta oposición a la resolución administrativa en materia de protección de menores y que por el Letrado de la Administración de Justicia se reclame a la entidad administrativa un testimonio completo del expediente, que deberá ser aportado en el plazo de veinte días, a fin de ser emplazada esta parte para la presentación de la demanda.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado y Procurador [COMPLETAR].

========================================================================
