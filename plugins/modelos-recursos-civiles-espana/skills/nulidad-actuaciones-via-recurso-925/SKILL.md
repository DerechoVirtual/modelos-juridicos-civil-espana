---
name: nulidad-actuaciones-via-recurso-925
description: "Redacta el escrito «Nulidad de actuaciones por vía de recurso» (formulario 925 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Nulidad de actuaciones por vía de recurso

> Formulario 0925 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] NÚMERO (2 veces)
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (2 veces)
- [ ] DESCRIBIR
- [ ] ACTO O RESOLUCIÓN
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Juicio»; «…, PLAZA N.º»; «…roceda en derecho DIGO: Que con fecha de»; «…rmulo contra dicha resolución RECURSO DE»; «…7.1 del CC, la nulidad de actuaciones de»; «…nulidad a través del presente Recurso de»; «… presente caso concurre la circunstancia»; «… el resto de las alegaciones del recurso»; «… ajusta a las pruebas practicadas porque»; «… forma solicitud de nulidad y RECURSO DE»; «…mediante la que se acuerda»; «…diante la que, estimando este Recurso de»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 227.1 del CC
- arts. 240 de la LOPJ
- arts. 238 de la LOPJ

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

### Formulario 0925 · Nulidad de actuaciones por vía de recurso

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 25 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio [COMPLETAR] n.º [NÚMERO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS] Procuradora de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], n.º [NÚMERO], según tengo debidamente acreditado en el procedimiento referenciado, ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que con fecha de [COMPLETAR] se ha notificado a mi mandante [NOMBRE DEL REPRESENTADO/A] (indicar resolución procesal notificada) de fecha [FECHA], dictada en el presente procedimiento. Mediante el presente escrito y en aplicación del art. formulo contra dicha resolución RECURSO DE [COMPLETAR] (reposición, revisión, apelación...), interesando igualmente, y según permite el art. 227.1 del CC, la nulidad de actuaciones de [COMPLETAR] en atención a las siguientes

ALEGACIONES

PREVIA.—I. Formulo la solicitud de declaración de nulidad a través del presente Recurso de [COMPLETAR], tal y como determinan los arts. 240 de la LOPJ y 227 de la LEC, que establecen que la nulidad de pleno derecho, en todo caso, y los defectos de forma en los actos procesales que impliquen ausencia de los requisitos indispensables para alcanzar su fin o determinen efectiva indefensión, se harán valer por los recursos establecidos en la ley contra la resolución de que se trate

II. Los arts. 238 de la LOPJ y 225 de la LEC determinan en qué supuestos los actos procesales serán nulos de pleno derecho.

III. En el presente caso concurre la circunstancia [COMPLETAR] (desarrollar y justificar encaje en alguna de las anteriores previsiones legales).

De no estimarse el motivo de nulidad pasamos a formular el resto de las alegaciones del recurso [COMPLETAR] que interponemos.

PRIMERA.— Se ha vulnerado el art. relativo a [DESCRIBIR]

SEGUNDA.— En cuanto a la valoración de los hechos que incluye la resolución recurrida no se ajusta a las pruebas practicadas porque [COMPLETAR]

Por lo expuesto,

SUPLICO AL TRIBUNAL: Tenga por presentado este escrito y su copia preceptiva, se sirva admitirlo, y en su virtud tenga por formulado en tiempo y forma solicitud de nulidad y RECURSO DE [COMPLETAR] contra [ACTO O RESOLUCIÓN] (resolución judicial) de fecha [FECHA] mediante la que se acuerda [COMPLETAR], a fin de que en su día se dicte resolución mediante la que, estimando este Recurso de [COMPLETAR] acuerde [COMPLETAR] (pedimento principal del recurso) así como declarar la nulidad de las actuaciones [COMPLETAR] (detallar).

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
