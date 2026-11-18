---
name: arrendamiento-cuarto-trastero-navarra-578
description: "Redacta el escrito «Arrendamiento de cuarto trastero (Navarra)» (formulario 578 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Arrendamiento de cuarto trastero (Navarra)

> Formulario 0578 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] NÚMERO (4 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE
- [ ] Nº
- [ ] FECHA
- [ ] IMPORTE (2 veces)
- [ ] Otros 20 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…comparece»; «…de»; «…de [COMPLETAR], al Tomo»; «… [COMPLETAR], al Tomo [COMPLETAR], Libro»; «…, Libro [COMPLETAR], Folio»; «…, Folio [COMPLETAR], Finca»; «…:»; «…presente contrato tendrá una duración de»; «…de»; «…de [COMPLETAR] de»; «…. Finalizada la duración pactada»; «…e realizará por anticipado dentro de los»; …

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

### Formulario 0578 · Arrendamiento de cuarto trastero (Navarra)

- Año del modelo: 2016
- Revisión 17-11-2026: 37 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [DÍA] de [MES] de [AÑO].

MANIFIESTAN

Que D./Dña. [NOMBRE Y APELLIDOS] comparece [COMPLETAR], y tiene capacidad legal para disponer del cuarto trastero nº [NÚMERO], de la planta n.º [NÚMERO] del inmueble sito en [LOCALIDAD], C/ [CALLE], n.º [NÚMERO], que aparece inscrita en el Registro de la Propiedad n.º [NÚMERO] de [COMPLETAR], al Tomo [COMPLETAR], Libro [COMPLETAR], Folio [COMPLETAR], Finca [COMPLETAR], descrita como sigue:

Referencia catastral n.º [Nº]: [COMPLETAR].

Que D./Dña. [NOMBRE Y APELLIDOS] comparece en nombre propio.

Que ambas partes se reconocen mutuamente la capacidad necesaria para otorgar el presente contrato de arrendamiento de cuarto trastero que pactan libremente con arreglo a las siguientes

CLÁUSULAS

D./Dña. [NOMBRE Y APELLIDOS] cede en uso a D./Dña. [NOMBRE Y APELLIDOS] del cuarto trastero descrito en el punto I libre de cargas y ocupantes.

El arrendatario utilizará el inmueble arrendado exclusivamente para el almacenamiento de objetos muebles de su propiedad quedando prohibido el almacenamiento de bienes nocivos o peligrosos como gases inflamables, combustibles, etc.

Deberá cumplir las obligaciones que los Estatutos de la Comunidad de Vecinos y las Ordenanzas Municipales establezcan en la materia.

El presente contrato tendrá una duración de [COMPLETAR] a contar desde la fecha de este escrito.

Llegada la fecha de vencimiento del contrato, el día [FECHA] de [COMPLETAR] de [COMPLETAR].

Finalizada la duración pactada [COMPLETAR] el arrendatario deberá dejar el cuarto trastero en buen estado de uso, salvo el desgaste habitual.

El arrendatario abonará al arrendador en concepto de renta la cantidad de [IMPORTE] euros mensuales.

El pago se realizará por anticipado dentro de los [COMPLETAR] primeros días de cada mes en [COMPLETAR] y se efectuará [COMPLETAR]

Al cumplimiento de cada año de vigencia del contrato la renta será actualizada [COMPLETAR]. El índice actualizador consistirá en aplicar a la renta correspondiente a la anualidad anterior [COMPLETAR].

Correrán por cuenta del [COMPLETAR] los gastos generales [COMPLETAR].

El arrendador declara en este momento haber recibido en concepto de fianza [IMPORTE] euros en metálico, cantidad equivalente a [COMPLETAR] mensualidades de renta.

El arrendatario declara recibir el bien en perfecto estado de utilidad.

El arrendatario debe pagar las reparaciones que exija el desgaste por el uso ordinario de la cosa.

El arrendatario no podrá realizar obras ni mejoras en la cosa arrendada.

El subarriendo y la cesión del contrato de arrendamiento están permitidos, sin embargo, la cesión requerirá el consentimiento del arrendador.

En todo lo no expresamente regulado en este contrato será de aplicación el Título XV del Libro III de la Compilación del Derecho Civil Foral de Navarro y legislación supletoria.

Para todos los conflictos que puedan surgir en la interpretación, aplicación, efectos e incumplimiento del contrato por las partes se someten expresamente los contratantes a la Jurisdicción de los Tribunales de [LOCALIDAD], renunciando a cualquier otro fuero que pudiera corresponderles.

Y para que conste y surta los efectos oportunos, firman arrendador y arrendatario el presente contrato que consta de [COMPLETAR] folios, y que se suscribe en cada hoja de los dos ejemplares idénticos que se otorgan mutuamente, en el lugar y fecha del encabezamiento.

Fdo.: D./Dña. [NOMBRE Y APELLIDOS] Fdo.: D./Dña. [NOMBRE Y APELLIDOS]

========================================================================
