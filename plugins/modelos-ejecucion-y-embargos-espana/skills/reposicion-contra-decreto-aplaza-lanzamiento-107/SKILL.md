---
name: reposicion-contra-decreto-aplaza-lanzamiento-107
description: "Redacta el escrito «Reposición contra el decreto que aplaza un lanzamiento» (formulario 107 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición contra el decreto que aplaza un lanzamiento

> Formulario 0107 del plugin **Ejecución civil** · revisado el 17-11-2026.

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
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (2 veces)
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…D»; «…por la que (se expresa el contenido..)»; «…ordenación (se expresan las infracciones»; «…ose en un plazo no superior a un mes. En»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 24 CE
- art. 661 y 675 de la LEC
- arts. 549 y 704 de la LEC
- art. 24 de la CE

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

### Formulario 0107 · Reposición contra el decreto que aplaza un lanzamiento

- Año del modelo: 2022
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 9 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (COMPLETAR)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Juicio de desahucio por falta de pago número [NÚMERO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D [COMPLETAR], Procurador de los Tribunales y de [NOMBRE DEL REPRESENTADO/A] parte demandante en los autos de proceso ordinario arriba referenciados, ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que habiendo sido notificada a esta representación diligencia de ordenación de fecha [FECHA] por la que (se expresa el contenido..) [COMPLETAR], mediante el presente escrito, al amparo del art. 563, en relación con los arts. 451 y 452 de la LECiv, interpongo RECURSO DE REPOSICIÓN contra la mencionada diligencia de ordenación (se expresan las infracciones [COMPLETAR]) citando como infringidos el art. 24 CE, el art. 549 y 704 de la LECiv, por inaplicación, y el art. 661 y 675 de la LEC, por indebida aplicación, en base a los siguientes MOTIVOS:

MOTIVOS

PRIMERO.- La diligencia de ordenación infringe lo dispuesto en los arts. 549 y 704 de la LEC, a la vez que aplica indebidamente los arts. 661 y 675 del mismo texto legal, dicho sea en términos de defensa, al aplicar la normativa procesal sobre entrega de inmuebles a los adjudicatarios de las subastas, cuando estamos en un proceso de ejecución de título judicial firme, de entrega de cosas inmuebles por impago de la renta, donde resultan de aplicación los arts. 549 y 704 de la LECiv.

El art. 704.2 de la LECiv establece: “si el inmueble a cuya entrega obliga el título ejecutivo estuviera ocupado por terceras personas distintas del ejecutado y de quienes con él compartan la utilización de aquél, el Letrado de la Administración de Justicia responsable de la ejecución, tan pronto como conozca su existencia, les notificará el despacho de la ejecución o la pendencia de ésta, para que, en el plazo de diez días, presenten los títulos que justifiquen su situación.

El ejecutante podrá pedir al tribunal el lanzamiento de quienes considere ocupantes de mero hecho o sin título suficiente. De esta petición se dará traslado a las personas designadas por el ejecutante, prosiguiendo las actuaciones conforme a lo previsto en los apartados 3 y 4 del artículo 675”.

Los tribunales civiles vienen interpretando uniformemente que el citado art. 704 regula dos situaciones distintas: (i) el caso de los ocupantes que no presentan título que justifique su situación, en cuyo caso debe continuar el lanzamiento; y (ii) el caso de los ocupantes que presentan título, en cuyo caso se abre el trámite establecido en los apartados 3 y 4 del art. 675 de la LECiv, a instancia del ejecutante.

La diligencia de ordenación recurrida infringe dicho precepto, por cuanto que se ha procedido a aplicar directamente el trámite del art. 675.3 de la LECiv cuando los ocupantes no habían presentado ningún título que justificase su situación, por lo que es procedente continuar el lanzamiento sin más trámite como ordena el art. 549 de la LECiv.

La aplicación del art. 661.2 de la LECiv es totalmente errónea, dicho sea en términos de defensa, puesto que regula los supuestos de enajenación forzosa de inmuebles, no resultando aplicable a este caso, donde existe un título judicial firme que acuerda el lanzamiento, y que debe seguir las reglas de la ejecución de entrega de cosas establecidas en el art. 704 de la LECiv.

Por este motivo solicitamos que se reponga la resolución recurrida, dejándola sin efecto, y acordando continuar el lanzamiento sin más trámites.

SEGUNDO.- La diligencia de ordenación infringe el art. 24 de la CE, derecho a la tutela efectiva y a un proceso sin dilaciones indebidas, puesto que dilata injustificadamente la ejecución de una resolución judicial firme, dicho sea en términos de defensa, fijando a nuestro juicio un plazo a todas luces excesivo en el que se mantiene durante más de seis meses la injusta situación de privación de un inmueble al arrendador cuando no se está pagando ninguna renta.

Debemos subrayar lo injusto de esta situación, cuando después de haber seguido un proceso verbal ante el impago de la renta, donde se prolonga y mantiene la ocupación del inmueble de personas que no presentan ningún título durante más de seis meses, con nulas expectativas de percibir ningún tipo de renta y provocando gravísimos daños y perjuicios a esta parte, que lesiona el derecho a un proceso sin dilaciones indebidas, a la vez de constituir un supuesto de un supuesto de anormal funcionamiento de la Administración de Justicia, que genera graves daños y perjuicios al justiciable, reservándose esta parte las acciones de responsabilidad que pudieran corresponderle en su caso.

Por este motivo, con invocación del art. 24 CE, solicitamos subsidiariamente que, en el caso que se desestime la pretensión principal de continuar el lanzamiento, éste se señale el lanzamiento a la mayor brevedad tras la celebración de la vista, en un plazo no superior a un mes en todo caso.

En su virtud,

SUPLICO AL TRIBUNAL que teniendo por presentado este escrito, con justificante de traslado, se sirva admitirlo, tener por interpuesto recurso de reposición contra la diligencia ordenación de fecha [FECHA] y, en su virtud, se reponga la misma, acordando señalar el lanzamiento sin más trámites de forma inmediata o, subsidiariamente, señalándose en un plazo no superior a un mes.

En [COMPLETAR]

(Firma Procurador y Abogado)
