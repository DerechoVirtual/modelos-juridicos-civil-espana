---
name: constitucion-agrupacion-comunidades-propietarios-1433
description: "Redacta el escrito «Constitución en agrupación de comunidades de propietarios» (formulario 1433 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Constitución en agrupación de comunidades de propietarios

> Formulario 1433 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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

- [ ] CALLE
- [ ] Otros 24 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…parada del siguiente edificio situado en»; «…. Ocupa una superficie de»; «… lo que afecta a este edificio comprende»; «…carboneras numeradas del»; «…carboneras numeradas del [COMPLETAR] al»; «…y plazas de aparcamiento numeradas del»; «…al»; «…ras de acceso a las plantas superiores y»; «…ales. Planta primera: está compuesta por»; «…ndas. Planta segunda: está compuesta por»; «…viviendas.»; «…, derecha»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Ley 49/1960

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

### Formulario 1433 · Constitución en agrupación de comunidades de propietarios

- Año del modelo: 2013
- Revisión 17-11-2026: 25 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

La finca/s descrita/s forma/n parte separada del siguiente edificio situado en [COMPLETAR]. Ocupa una superficie de [COMPLETAR] metros cuadrados y está compuesto por:

Planta sótano: con acceso para vehículos a través de la rampa de bajada general para todo el complejo inmobiliario que después se describirá y de peatones a través del portal de este edificio. En lo que afecta a este edificio comprende [COMPLETAR] carboneras numeradas del [COMPLETAR] al [COMPLETAR] y plazas de aparcamiento numeradas del [COMPLETAR] al [COMPLETAR], ambas anejas a las viviendas.

Planta baja: donde se ubica el portal y caja de escaleras de acceso a las plantas superiores y [COMPLETAR] locales comerciales.

Planta primera: está compuesta por [COMPLETAR] viviendas.

Planta segunda: está compuesta por [COMPLETAR] viviendas.

[COMPLETAR]

Linda este edificio mirándolo desde la C/ [CALLE], derecha [COMPLETAR], izquierda [COMPLETAR], fondo [COMPLETAR], frente [COMPLETAR].

El edificio a su vez forma parte del complejo inmobiliario que se constituye en este acto formado por [COMPLETAR] edificios situados [COMPLETAR] y que se describen de la siguiente manera [COMPLETAR].

ESPECIALIDADES

Las viviendas y locales con sus anejos integrados en cada uno de los edificios descritos constituirán una agrupación de comunidades de propietarios que se regirá por el siguiente régimen de propiedad horizontal:

La agrupación de comunidades en la que se integran los edificios descritos que componen ese conjunto y los demás elementos que configuran el inmueble en el que se ubica se regirán por la Ley 49/1960, de 21 de julio, de Propiedad Horizontal con las siguientes especialidades:

Cada edificio constituye una comunidad de propietarios que se regirá por sus propias reglas, sin perjuicio de procurar que éstas tengan el mismo contenido y forma en cada uno de ellos.

Son elementos comunes de todo el complejo los que se destinen o puedan destinarse al uso y disfrute común de sus ocupantes y que se comprenden en todo el contenido del perímetro definido por la valla de delimitación de la urbanización denominada [COMPLETAR], que incluye: jardines, piscinas, caminos de comunicación entre todos los portales hasta el acceso a éstos que es elemento común de cada comunidad, camino de acceso a la urbanización, garita del conserje, instalaciones de calefacción, etc.

La Junta de Propietarios de la agrupación se compone por los presidentes de cada una de las comunidades de la agrupación y ostenta la representación de todos los comuneros de su comunidad dentro del conjunto.

La competencia de esta Junta se limita únicamente a los elementos comunes a la agrupación y no se extiende a las facultades de cada comunidad, en cuyo ámbito de competencias no podrá inmiscuirse, salvo delegación de competencias por todas ellas.

La adopción de acuerdos para los que se exijan mayorías cualificadas exigirá la previa obtención de estas mayoría en cada Junta de Propietarios de las que componen la agrupación inmobiliaria.

Esta Junta elegirá anualmente un presidente de la agrupación por mayoría simple con las siguientes funciones:

—convocar y presidir las juntas de gobierno.

—representar a la agrupación frente a terceros y en actuaciones judiciales.

—

Constituyen servicios comunes de la agrupación los siguientes: [COMPLETAR].

Para la contribución a los gastos comunes se asigna la siguiente cuota de participación a cada comunidad:

Edificio [COMPLETAR]: %.

Edificio [COMPLETAR]: %.

Edificio [COMPLETAR]: %.

Edificio [COMPLETAR]: %.

========================================================================
