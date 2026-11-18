---
name: constitucion-comunidad-propietarios-complejo-825
description: "Redacta el escrito «Constitución en comunidad de propietarios de un complejo inmobiliario privado» (formulario 825 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Constitución en comunidad de propietarios de un complejo inmobiliario privado

> Formulario 0825 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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
- [ ] DESCRIBIR
- [ ] Otros 35 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…parada del siguiente edificio situado en»; «…Ocupa una superficie de»; «… lo que afecta a este edificio comprende»; «…carboneras numeradas del»; «…carboneras numeradas del [COMPLETAR] al»; «…al [COMPLETAR] y»; «…plazas de aparcamiento numeradas del»; «…al»; «…ras de acceso a las plantas superiores y»; «…ales. Planta primera: está compuesta por»; «…endas Planta segunda: está compuesta por»; «…, derecha»; …

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

### Formulario 0825 · Constitución en comunidad de propietarios de un complejo inmobiliario privado

- Año del modelo: 2015
- Revisión 17-11-2026: 37 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

(Incluido en la escritura de división horizontal y en la de adquisición de cada uno de los pisos o locales)

La/s finca/s descrita/s forma/n parte separada del siguiente edificio situado en [COMPLETAR] Ocupa una superficie de [COMPLETAR] metros cuadrados y está compuesto por:

Planta sótano: con acceso para vehículos a través de la rampa de bajada general para todo el complejo inmobiliario que después se describirá y de peatones a través del portal de este edificio. En lo que afecta a este edificio comprende [COMPLETAR] carboneras numeradas del [COMPLETAR] al [COMPLETAR] y [COMPLETAR] plazas de aparcamiento numeradas del [COMPLETAR] al [COMPLETAR], ambas anejas a las viviendas.

Planta baja: donde se ubica el portal y caja de escaleras de acceso a las plantas superiores y [COMPLETAR] locales comerciales.

Planta primera: está compuesta por [COMPLETAR] viviendas

Planta segunda: está compuesta por [COMPLETAR] viviendas

Linda este edificio mirándolo desde la C/ [CALLE], derecha [COMPLETAR], izquierda [COMPLETAR], fondo [COMPLETAR], frente [COMPLETAR]

Este edificio está construido dentro de la urbanización [COMPLETAR] que se constituye en este acto como una Comunidad de Propietarios formada por [COMPLETAR] edificios situados [COMPLETAR] y que se describen de la siguiente manera

Las viviendas y locales con sus anejos integrados en cada uno de los edificios descritos constituirán una sola comunidad de propietarios que se regirá por el siguiente régimen de comunidad:

La Comunidad de Propietarios en la que se integran los pisos o locales objeto de esta escritura y los demás elementos que componen el inmueble en el que se ubica se regirá por la Ley 49/1960, de 21 de julio, de Propiedad Horizontal, por el Código Civil por la Ley Hipotecaria y por las reglas siguientes:

Primera.— Son elementos comunes de todo el complejo los que se destinen o puedan destinarse al uso y disfrute común de sus ocupantes tales como suelo, vuelo, cimentaciones, pasos, pasillo, portal, escaleras, fachadas, patios de luces, cubiertas, conducciones de agua, luz, energía eléctrica, comunicaciones telefónicas o telemáticas, hasta la entrada en elementos independientes, así como todo el contenido del perímetro definido por la valla de delimitación de la urbanización denominada [COMPLETAR], que comprende: jardines, piscinas, caminos de comunicación entre todos los portales y de éstos con la entrada común, garita del conserje, instalaciones de calefacción, ..., y son elementos propios los que sirven únicamente a la finca de que se trata tales como puertas, tabiques interiores, suelo, cielo raso, etc.

(En su caso) Constituyen elementos comunes de uso privativo [COMPLETAR] (la terraza situada en [COMPLETAR] o el patio de [COMPLETAR]).

Segunda.— La cuota de participación asignada a cada piso o local del inmueble servirá para fijar la contribución de cada titular a los gastos comunes y a todos los beneficios o cargas que se asuman, [COMPLETAR] (En su caso) con las siguientes excepciones:

1.º Los dueños de los locales quedan excluidos de contribución a los gastos de [COMPLETAR] Cuando existan estos gastos la contribución del resto de los titulares se hará [COMPLETAR] (por partes iguales entre todos ellos; calculando la contribución al importe total en la misma proporción que mantiene sobre la contribución al resto de los gastos, etc.).

2.º Cuando se aprueben gastos relativos a [DESCRIBIR], la cuota de participación será de [COMPLETAR]

(En su caso, si la cuota de participación de cada elemento se ha asignado por edificio

y no por el total del conjunto) La cuota de participación de cada elemento en el conjunto inmobiliario se calcula teniendo en cuenta que el complejo inmobiliario está compuesto por [COMPLETAR] edificios y que a cada uno de ellos le corresponde una participación de [COMPLETAR] por ciento en el total de los votos, de manera que pisos y locales de cada edificio ajustarán su cuota en el conjunto en la misma proporción que les corresponda dentro de su edificio y a éste en el conjunto, es decir, al piso [COMPLETAR] del edificio [COMPLETAR] le corresponde en ese edificio una cuota de [COMPLETAR] por ciento. Al edificio le corresponde en el complejo una cuota del [COMPLETAR] por ciento, por tanto al piso le corresponde en el complejo una cuota del [COMPLETAR] por ciento.

La adopción de acuerdos por la Junta de Propietarios seguirá las reglas de mayorías reguladas en la Ley de Propiedad Horizontal.

Tercera.— Los titulares de elementos independientes podrán por sí solos realizar operaciones de agrupación, agregación, segregación, división y subdivisión permitidas por la ley y con los permisos y licencias administrativos correspondientes, sin que ello altere la estructura externa del edificio ni disminuya su seguridad. En estos casos la cuota de participación del elemento o los elementos resultantes se fijará por suma o distribución de los que tenían asignados.

Cuarta.— Los comuneros podrán realizar obras en su parte privativa siempre que no afecten al resto del inmueble.

Se requerirá el consentimiento previo de la comunidad para la ejecución de obras que afecten o puedan afectar a [COMPLETAR] (la estética del edificio, las galerías de cada vivienda, etc.).

En concreto, en los locales de negocio, sin necesidad de aprobación por la Comunidad de Propietarios, se podrán realizar las obras siguientes:

Quinta.— En las plazas de garaje [COMPLETAR] (sí o no) se permite el cerramiento por cada uno de sus titulares.

Sexta.— La Junta de Propietarios estará compuesta por todos los propietarios de los distintos elementos que comprende cada uno de los edificios de la comunidad.

Séptima.— La presidencia se asumirá anualmente por un comunero de edificio distinto al del año anterior, al igual que la secretaría, no pudiendo coincidir en estos cargos propietarios de un mismo edificio.

Octava.—

========================================================================
