---
name: diligencias-preliminares-propiedad-horizontal-exhibir-1373
description: "Redacta el escrito «Diligencias preliminares de propiedad horizontal para exhibir documentos de la comunidad» (formulario 1373 de medidas cautelares y diligencias preliminares, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Diligencias preliminares de propiedad horizontal para exhibir documentos de la comunidad

> Formulario 1373 del plugin **Medidas cautelares y diligencias preliminares** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] CALLE (3 veces)
- [ ] NÚMERO (3 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] IMPORTE
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…eliminares consistentes en la exhibición»; «…nº [NÚMERO] de»; «…nº [NÚMERO] de»; «…es propietario de»; «…este acto se demanda, según acredito con»; «…nº [NÚMERO] por»; «…presentarla se hace necesario conocer su»; «…, con el fin de»; «…sde este momento dejamos interesado que,»; «…que presentar el documento, en este caso»; «…o de la demanda principal recordemos que»; «…con la Comunidad de Propietarios de»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Libro de actas / Contrato / Libro de cuentas / Cuentas anuales / Contrato de seguro / Otros... — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Se ordene entrada y registro y disposición en sede tribunal. / Documentos contables — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Libro de actas / Cuentas y presupuestos — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 257 de la LEC
- art. 10 de la LEC
- art. 256 de la LEC
- art. 6.5 de la LEC
- art. 256.3 de la LEC
- art. 260.3 de la LEC

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

### Formulario 1373 · Diligencias preliminares de propiedad horizontal para exhibir documentos de la comunidad

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 3 bloques de opciones sin texto dejados en blanco con sus rótulos; 29 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D/Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante poder notarial que acompaño, rogando me sea devuelto una vez testimoniado en autos, ante el Tribunal comparezco con la asistencia letrada de D./Dña. [NOMBRE Y APELLIDOS] y como mejor proceda en derecho, digo:

Que mediante el presente escrito y según permite el art. 256.1.4º de la LEC intereso la práctica de diligencias preliminares consistentes en la exhibición [COMPLETAR] de la Comunidad de Propietarios de la C/ [CALLE] nº [NÚMERO] de [COMPLETAR]. Esta diligencia se practicará con el representante legal de la Comunidad, su Presidente D./Dña. [NOMBRE Y APELLIDOS], con domicilio en la C/ [CALLE] nº [NÚMERO] de [COMPLETAR]. Basamos esta solicitud en los siguientes

HECHOS

El demandante D./Dña. [NOMBRE Y APELLIDOS] es propietario de [COMPLETAR], perteneciente a la Comunidad de Propietarios cuya documentación en este acto se demanda, según acredito con [COMPLETAR], que acompaño como documento nº [Nº DE DOCUMENTO].

Mi representado pretende formular demanda contra la Comunidad de Propietarios de la C/ [CALLE] nº [NÚMERO] por [COMPLETAR], pero antes de presentarla se hace necesario conocer su [COMPLETAR], con el fin de [COMPLETAR].

El conocimiento de estos datos resulta imprescindible para formular de forma adecuada la demanda y, a pesar de los intentos por conseguir el acceso a ellos, según se acredita con la copia de cartas remitidas al Presidente, que adjuntamos como documentos nº [Nº DE DOCUMENTO], no se ha contestado a esta pretensión. Por esta razón, nos vemos obligados a acudir a la vía judicial.

En concreto esta parte interesa la exhibición de los siguientes documentos:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Libro de actas / Contrato / Libro de cuentas / Cuentas anuales / Contrato de seguro / Otros... — el texto de cada opción no venía en el formulario original]

En caso de que por parte de la Comunidad no se proceda a atender al requerimiento que se le efectúe ni formule oposición, desde este momento dejamos interesado que, [COMPLETAR]:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Se ordene entrada y registro y disposición en sede tribunal. / Documentos contables — el texto de cada opción no venía en el formulario original]

FUNDAMENTOS DE DERECHO

En aplicación del art. 257 de la LEC, será competente la Sección Civil del Tribunal de Instancia del domicilio de la persona que tenga que presentar el documento, en este caso [COMPLETAR].

Los arts. 259 y siguientes de la LEC determinan el procedimiento a seguir, que comienza citando a los interesados a una comparecencia para llevar a cabo la diligencia de exhibición e indicando a los requeridos su facultad de oponerse, en cuyo caso se citará a las partes a una vista que se tramitará por el cauce del juicio verbal.

El art. 10 de la LEC legitima a los titulares de la relación jurídica u objeto litigioso para ser parte en el proceso. En este caso, el art. 256 de la LEC permite preparar el juicio que pretenda entablarse con la diligencia que aquí interesamos.

Finalmente, el art. 6.5 de la LEC reconoce la capacidad para ser parte a determinadas entidades jurídicas, como es una Comunidad de Propietarios.

Sin entrar a estudiar el objeto de la demanda principal recordemos que [COMPLETAR].

PRIMERO

[ELEGIR UNA OPCIÓN Y REDACTARLA: Libro de actas / Cuentas y presupuestos — el texto de cada opción no venía en el formulario original]

SEGUNDO. CAUCIÓN.—Según indica el art. 256.3 de la LEC esta parte ofrece caución en la cuantía de [IMPORTE] €, o en la que estime adecuada el Juzgador que no supere esa cifra, para responder de los posibles gastos o perjuicios que debidamente acredite la parte requerida que se le han producido.

Las costas de estas diligencias deberán ser impuestas a la parte requerida, al haberse negado a facilitar voluntariamente a mi representado la documentación solicitada en aplicación del art. 260.3 de la LEC.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y copia de todo ello, lo admita y acuerde la práctica de las diligencias preliminares consistentes en [DESCRIBIR] con la Comunidad de Propietarios de [COMPLETAR] mediante la persona física de su Presidente.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
