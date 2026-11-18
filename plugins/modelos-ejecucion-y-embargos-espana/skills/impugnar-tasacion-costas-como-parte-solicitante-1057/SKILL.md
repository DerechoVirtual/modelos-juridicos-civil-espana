---
name: impugnar-tasacion-costas-como-parte-solicitante-1057
description: "Redacta el escrito «Impugnar la tasación de costas como parte solicitante» (formulario 1057 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Impugnar la tasación de costas como parte solicitante

> Formulario 1057 del plugin **Ejecución civil** · revisado el 17-11-2026.

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

- [ ] NÚMERO
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] FECHA (2 veces)
- [ ] IMPORTE (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Juicio»; «…n.º [NÚMERO] /»; «…, PLAZA N.º»; «…cticada, por no haberse incluido en ella»; «… original: No se ha tenido en cuenta que»; «…en el presente supuesto la circunstancia»; «…nclusión de la partida correspondiente a»; «…n las partidas concretas que se impugnan»; «…y forma la tasación de costas practicada»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 245.3 de la LEC
- art. 245 de la LEC

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

### Formulario 1057 · Impugnar la tasación de costas como parte solicitante

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 18 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio [COMPLETAR] n.º [NÚMERO] / [COMPLETAR]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

PARA EL LETRADO DE LA ADMINISTRACIÓN DE JUSTICIA

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], según tengo acreditado en los autos referenciados ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que con fecha [FECHA] se ha dado traslado a esta parte de la tasación de costas practicada en el presente procedimiento. Dentro del plazo legal de diez días previsto en el art. 245 en relación con el art. 244 de la Ley de Enjuiciamiento Civil, y mediante el presente escrito, IMPUGNO la tasación practicada, por no haberse incluido en ella [COMPLETAR] (gastos justificados, la totalidad de la minuta del abogado, correctamente los derechos del Procurador) sentando como base de mi pretensión los siguientes

ANTECEDENTES

Mediante escrito de fecha [FECHA] esta parte demandante solicitó la tasación de las costas causadas en este procedimiento, detallando como conceptos que debían formar parte de la misma los siguientes:

Sin embargo, el Sr. Letrado de la Administración de Justicia ha practicado la tasación que se nos traslada, en la que se excluyen algunos de los conceptos detallados en la solicitud formulada por la parte actora, y que a juicio de esta parte deben formar parte de la tasación que finalmente haya de aprobarse. Concretamente, han quedado excluidos de la tasación inicial practicada los siguientes capítulos de nuestra solicitud original:

No se ha tenido en cuenta que [COMPLETAR] (desarrollar los hechos que sirvan de base a la impugnación).

Resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Art. 241 de la LEC, que relaciona pormenorizadamente los conceptos que integran la tasación de costas.

Concurre en el presente supuesto la circunstancia [COMPLETAR] que determina la inclusión de la partida correspondiente a [COMPLETAR] de la tasación de costas por importe de [IMPORTE] euros (desarrollar argumentación mediante la que se pretende defender la procedencia de la inclusión de cada concepto en la tasación de costas o la inclusión de determinados conceptos en la misma).

Procede, en consecuencia, aprobar la tasación de costas en los términos y por los conceptos que dejamos detallados en nuestro escrito de solicitud de tasación, es decir:

1. euros.

2. euros.

TOTAL [IMPORTE] euros.

El art. 245.3 de la LEC permite a la parte favorecida por la condena en costas impugnar en el plazo legal señalado en el art. 244 del mismo texto legal la tasación practicada.

Conforme a la exigencia del apartado 4 del art. 245 de la LEC, se detallan las partidas concretas que se impugnan [COMPLETAR] (por exclusión o por excesiva) y las razones de la impugnación.

El art. 246 del precitado texto legal procedimental establece el procedimiento a seguir para dirimir la impugnación.

Por lo expuesto,

SUPLICO: Que tenga por presentado este escrito con su copia preceptiva, se sirva admitirlo, teniendo por impugnada en tiempo y forma la tasación de costas practicada [COMPLETAR] (por indebida o por excesiva) y tras el trámite procesal oportuno dicte el Letrado de la Administración de Justicia decreto mediante el que se acuerde aprobar la tasación de costas en los términos que esta parte actora dejó interesados en su escrito original de solicitud de tasación y que se reproducen en el cuerpo del presente escrito.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
