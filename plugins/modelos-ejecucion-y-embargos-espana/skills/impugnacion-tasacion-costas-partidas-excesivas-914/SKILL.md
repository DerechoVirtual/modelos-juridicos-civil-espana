---
name: impugnacion-tasacion-costas-partidas-excesivas-914
description: "Redacta el escrito «Impugnación de la tasación de costas por partidas excesivas o superfluas» (formulario 914 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Impugnación de la tasación de costas por partidas excesivas o superfluas

> Formulario 0914 del plugin **Ejecución civil** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] FECHA (2 veces)
- [ ] IMPORTE (4 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Juicio»; «…n.º [NÚMERO] /»; «…, PLAZA N.º»; «…ptos que debían formar parte de la misma»; «…in embargo no se ha tenido en cuenta que»; «… por lo que la partida correspondiente a»; «…euros la partida de»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 246.1 de la LEC
- art. 245 LEC
- art. 246.3 de la LEC

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

### Formulario 0914 · Impugnación de la tasación de costas por partidas excesivas o superfluas

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 19 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio [COMPLETAR] n.º [NÚMERO] / [COMPLETAR]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

PARA EL LETRADO DE LA ADMINISTRACIÓN DE JUSTICIA

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], según tengo acreditado en los autos referenciados, ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que con fecha [FECHA] se ha dado traslado a esta parte de la tasación de costas practicada en el presente procedimiento a instancia de parte contraria. Dentro del plazo legal de diez días previsto en el art. 245 en relación con el art. 244 de la Ley de Enjuiciamiento Civil, y mediante el presente escrito, IMPUGNO por excesiva la tasación practicada, sentando como base de mi pretensión los siguientes

ANTECEDENTES

Por la representación procesal del demandante D./Dña. [NOMBRE Y APELLIDOS] se presentó escrito de fecha [FECHA] en el que se solicitaba la tasación de costas, detallando como conceptos que debían formar parte de la misma [COMPLETAR] (detallar los que hayan de ser objeto de impugnación).

Consecuentemente a tal petición por el Sr. Letrado de la Administración de Justicia se practicó la tasación que se nos traslada, en la que se incluyen todos los conceptos detallados en la solicitud formulada por la parte actora y por las cuantías detalladas en la solicitud.

Sin embargo no se ha tenido en cuenta que [COMPLETAR] (desarrollar los hechos que sirvan de base a la impugnación), por lo que la partida correspondiente a [COMPLETAR] debe quedar fijada en la suma de [IMPORTE] euros.

Resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

El art. 246.1 de la LEC permite a las partes impugnar en el plazo legal señalado en el art. 244 del mismo texto legal la tasación practicada.

El art. 246.1 del precitado texto legal procedimental establece el procedimiento a seguir para dirimir la impugnación.

Conforme a la exigencia del apartado 4 del art. 245 LEC, se detallan las partidas concretas que se impugnan y las razones de la impugnación. (Desarrollar la fundamentación que sirve de base a la consideración de excesiva de alguna de las partidas incluidas en la tasación o hacer referencia a la vulneración de las normas orientadoras de honorarios aprobadas por los Colegios Profesionales).

Procede, en consecuencia, fijar en la suma de [IMPORTE] euros la partida de [COMPLETAR] impugnada por excesiva, según el siguiente detalle de conceptos:

1. euros.

2. euros.

TOTAL [IMPORTE] euros.

El art. 246.3 de la LEC permite imponer las costas al impugnante cuyas pretensiones son desestimadas.

Por lo expuesto,

SUPLICO: Que tenga por presentado este escrito (en su caso, con su copia preceptiva), se sirva admitirlo, teniendo por impugnada por excesiva en tiempo y forma la tasación de costas practicada, relativa a la minuta de letrado y siga el trámite procesal oportuno de traslado al letrado contrario a fin de que acepte la reducción de honorarios propuesta o, en caso contrario, se requiera al Colegio de Abogados para que emita informe tras el cual el Letrado de la Administración de Justicia dictará decreto mediante el que se acuerde aprobar la tasación de costas procedente por la suma total de [IMPORTE] euros en los términos que se dejan interesados en el cuerpo del presente escrito, con imposición de costas al impugnante.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
