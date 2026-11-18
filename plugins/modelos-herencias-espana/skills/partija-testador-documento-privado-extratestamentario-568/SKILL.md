---
name: partija-testador-documento-privado-extratestamentario-568
description: "Redacta el escrito «Partija del testador en documento privado extratestamentario (Galicia)» (formulario 568 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Partija del testador en documento privado extratestamentario (Galicia)

> Formulario 0568 del plugin **Sucesiones** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] DNI/NIE
- [ ] FECHA (2 veces)
- [ ] NÚMERO (5 veces)
- [ ] CALLE
- [ ] Otros 47 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ayor de edad, viudo, jubilado, vecino de»; «…con domicilio en la»; «…ué testamento abierto ante el Notario de»; «…,»; «…iversales de mi herencia a mis hijos Don»; «…, Don»; «…, Don [COMPLETAR], Don»; «… Don [COMPLETAR], Don [COMPLETAR] y Doña»; «…que pueda existir en la cuenta corriente»; «…en la entidad bancaria»; «…ibe a continuación. 3. La vivienda de la»; «…e, según el Registro de la Propiedad, de»; …

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 0568 · Partija del testador en documento privado extratestamentario (Galicia)

- Año del modelo: 2016
- Revisión 17-11-2026: 57 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

PARTIJA POR TESTADOR EN DOCUMENTO PRIVADO EXTRATESTAMENTARIO

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Yo, mayor de edad, viudo, jubilado, vecino de [COMPLETAR] con domicilio en la [COMPLETAR], DNI [DNI/NIE], deseo realizar la PARTICIÓN de los bienes de mi herencia por medio del presente documento. A tal efecto hago constar:

I. Que el día [FECHA] otorgué testamento abierto ante el Notario de [COMPLETAR], [COMPLETAR].

II. Que en dicho testamento instituí herederos universales de mi herencia a mis hijos Don [COMPLETAR], Don [COMPLETAR], Don [COMPLETAR] y Doña [COMPLETAR]. Además establecí dos legados.

III. Que las previsiones de esta partición se ajustan a las disposiciones contenidas en el referido testamento. En caso de que hubiese discordancia, es mi deseo que, de acuerdo con la Ley de Derecho civil de Galicia, prevalezca la atribución de bienes que a continuación se efectúa siempre que estén respetadas las legítimas.

IV. Que esta partición engloba todos los bienes de que a día de hoy soy titular en pleno dominio, no constando ningún otro fuera de la relación que ahora se efectúa.

V. Que en caso de que uno de los instituidos me premuera y fallezca sin sustituto, si no he modificado en vida mi testamento o esta partición, deseo que los bienes a que se contrae la cuota del premuerto en esta partición sean repartidos entre sí por el resto de coherederos vivos.

VI. Los bienes que abarca esta partición son los siguientes: (al tratarse de una partija efectuada por el testador no es imprescindible que los bienes figuren con todos los datos identificativos que a continuación se recogen, aunque, lógicamente, resulta muy conveniente que así sea para evitar posibles errores)

1. El saldo que pueda existir en la cuenta corriente [COMPLETAR] en la entidad bancaria [COMPLETAR].

2. Los muebles, ropas y ajuar de casa, que se encuentran en la vivienda que habito, que se describe a continuación.

3. La vivienda de la [COMPLETAR], que se compone de un piso con una superficie, según el Registro de la Propiedad, de [COMPLETAR] metros cuadrados.

Título. La adquirí por compra, mediante escritura autorizada por el Notario de [COMPLETAR], el [COMPLETAR] de [COMPLETAR] de [COMPLETAR], número [NÚMERO] de protocolo e inscrita en el Registro de la Propiedad.

Inscripción. Registro de la Propiedad de [COMPLETAR] tomo [COMPLETAR], libro [COMPLETAR], folio [COMPLETAR], finca [COMPLETAR].

Referencia catastral. Tiene asignada la referencia catastral número [NÚMERO].

Cargas. No tiene carga alguna.

4. Finca número [NÚMERO] del Plano de la Zona de Concentración Parcelaria de [COMPLETAR], al sitio de [COMPLETAR], a monte, de una superficie de [COMPLETAR] áreas y [COMPLETAR] centiáreas.

Linda: al Norte con [COMPLETAR] y camino; al Sur con [COMPLETAR]; al Este con camino [COMPLETAR] y al Oeste con [COMPLETAR].

Inscripción. Registro de la Propiedad de [COMPLETAR], tomo [COMPLETAR], libro [COMPLETAR], folio [COMPLETAR], finca [COMPLETAR].

Referencia catastral. Tiene asignada referencia catastral número [NÚMERO].

Título. Acta de reorganización de concentración parcelaria, autorizada por el Notario de [COMPLETAR], don [COMPLETAR], el día [FECHA] de [COMPLETAR] de [COMPLETAR], número [NÚMERO] de protocolo.

Cargas. La finca anteriormente descrita se dividirá materialmente en dos partes iguales en extensión e iguales en valor dada la calidad del terreno, previa licencia reglamentaria que habrán de solicitar los adjudicatarios. Caso de resultar la finca indivisible, se entenderá adjudicada por mitad y proindiviso a los dos adjudicatarios en ella interesados.

VII. Que es mi voluntad partir los bienes mencionados entre mis hijos de la siguiente manera: (resulta conveniente repetir, aunque sea de manera sintética, la descripción de los bienes que se adjudican a fin de evitar eventuales errores en la remisión a los enumerados en el inventario)

Adjudicación a Doña [COMPLETAR]

1. Los muebles, ropas y ajuar de casa que se mencionan en el número 2 del inventario, a excepción de los relativos a los dos legados que a continuación se describen.

2. La vivienda de la calle [CALLE] que se describe en el número 3 del inventario, en pleno dominio.

Adjudicación a Don [COMPLETAR]

1. El pleno dominio de una de las dos mitades de la finca anteriormente descrita en el número 4 del inventario. Le corresponderá la mitad que linda con la finca de [COMPLETAR].

Adjudicación a Don [COMPLETAR]

1. El pleno dominio de la otra mitad de la finca anteriormente descrita en el número 4 del inventario.

Adjudicación a Don [COMPLETAR]

1. El saldo que exista en la cuenta corriente que se incluye en el número 1 del inventario.

Lego a Doña [COMPLETAR] el mueble [COMPLETAR] que actualmente está en la casa incluida en el número 3 del inventario.

Lego a Don [COMPLETAR] la colección de [COMPLETAR] que actualmente está en la casa incluida en el número 3 del inventario.

Esta partición y adjudicación en nada perjudica la legítima de mis herederos.

Firma del testador

========================================================================
