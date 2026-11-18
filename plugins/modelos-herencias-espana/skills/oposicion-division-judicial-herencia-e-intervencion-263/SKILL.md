---
name: oposicion-division-judicial-herencia-e-intervencion-263
description: "Redacta el escrito «Oposición a la división judicial de la herencia e intervención del caudal» (formulario 263 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición a la división judicial de la herencia e intervención del caudal

> Formulario 0263 del plugin **Sucesiones** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS
- [ ] Nº
- [ ] Nº DE PROCEDIMIENTO
- [ ] FECHA (3 veces)
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…D.»; «…, Procurador de los Tribunales y de D.»; «…, perteneciente al ICA de»; «…con el nº [Nº] de colegiada»; «…, Don»; «… división judicial de la herencia de Don»; «… DIVISIÓN JUDICIAL DE LA HERENCIA de Don»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 792 LEC
- art. 782 LEC
- art. 792.2 LEC

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

### Formulario 0263 · Oposición a la división judicial de la herencia e intervención del caudal

- Año del modelo: 2020
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 16 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de oposición a la división judicial de la herencia, y solicitud de intervención del caudal hereditario por los acreedores reconocidos como tales en el testamento o por los coherederos y los que tengan su derecho documentado en un título ejecutivo.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D. [COMPLETAR], Procurador de los Tribunales y de D. [COMPLETAR], según acredito mediante escritura de poder que acompaño a la presente, bajo la dirección letrada de D.ª [NOMBRE Y APELLIDOS], perteneciente al ICA de [COMPLETAR] con el nº [Nº] de colegiada [COMPLETAR], ante este Tribunal comparezco y como mejor proceda, DIGO:

Que a medio del presente escrito, en la representación enunciada y de acuerdo con lo dispuesto en el art. 792 LEC, vengo a formular ESCRITO DE OPOSICIÓN A LA DIVISIÓN JUDICIAL DE LA HERENCIA, Y SOLICITUD DE INTERVENCIÓN DEL CAUDAL HEREDITARIO, seguido en Autos nº [Nº DE PROCEDIMIENTO], todo ello sobre la base de las siguientes:

ALEGACIONES

PRIMERA.- Mediante escrito de fecha [FECHA], Don [COMPLETAR] solicitó, al amparo del art. 782 LEC, la división judicial de la herencia de Don [COMPLETAR], de la que fue instituido como coheredero, en virtud del testamento abierto otorgado por el causante con fecha

SEGUNDA.- Por Decreto de fecha [FECHA], el Tribunal tuvo por interesada la división judicial de la herencia, y convocó a los coherederos y al Ministerio Fiscal a la Junta, a celebrar el día [FECHA], que tendrá por objeto el nombramiento de contador, y en su caso, peritos, para practicar las operaciones divisorias.

TERCERA.- Mi mandante es acreedor reconocido por el causante en su testamento, ya que ostenta un crédito contra el caudal relicto consistente en [DESCRIBIR]; y ha llegado a su conocimiento que los coherederos han instado la división judicial de la herencia.

CUARTA.- En este momento, y según los datos de los que dispone mi representado, no ha tenido lugar la entrega de los bienes adjudicados a cada heredero, por lo que concurren todos los requisitos exigidos legalmente para la interposición de esta oposición.

QUINTA.- Asimismo, mi mandante está legitimado, como acreedor reconocido como tal en el testamento, de acuerdo con el art. 792.2 LEC, para instar la práctica de las actuaciones judiciales previstas en el art. 793.1 del mismo cuerpo legal, entre las que se encuentran la ocupación de los libros, papeles y correspondencia del difunto, la formación de inventario y depósito de bienes y el nombramiento de persona que efectúe y garantice el inventario y su depósito.

Por lo expuesto,

SUPLICO AL TRIBUNAL:

que teniendo por presentado este escrito, con los documentos y copias que acompaño de los mismos, se sirva admitirlo y a mí por comparecido en nombre de mi mandante, por propuesto este escrito de OPOSICIÓN A LA DIVISIÓN JUDICIAL DE LA HERENCIA de Don [COMPLETAR], hasta que se pague o afiance el crédito del que soy titular.

OTROSÍ DIGO:

que, como acreedor reconocido en testamento, interesa a mi mandante la INTERVENCIÓN JUDICIAL DE LA HERENCIA, por lo que

SUPLICO AL TRIBUNAL:

Se sirva acordar:

- La intervención del caudal hereditario
- La ocupación de los libros, papeles y correspondencia del difunto
- La formación de Inventario y Depósito de bienes
- El nombramiento de persona que efectúe y garantice el inventario y su depósito.

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado

	Firma de Procurador
