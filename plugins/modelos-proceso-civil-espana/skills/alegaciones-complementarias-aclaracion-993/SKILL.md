---
name: alegaciones-complementarias-aclaracion-993
description: "Redacta el escrito «Alegaciones complementarias y de aclaración» (formulario 993 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones complementarias y de aclaración

> Formulario 0993 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.

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

- [ ] NOMBRE Y APELLIDOS
- [ ] LOCALIDAD
- [ ] DESCRIBIR (3 veces)
- [ ] ÓRGANO
- [ ] NÚMERO
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…n a la demanda en el fundamento de hecho»; «…el cual mi representado se comprometía a»; «…ar cualquier labor agrícola. Como prueba»; «…arte reclama la propiedad de la finca de»; «…derecho dominical sobre una extensión de»; «…m2, y cuyos lindes son»; «…a reclamación la construcción situada en»; «…y en atención a la alegación de la parte»; «…con respecto a»; «…con respecto a [COMPLETAR] presentamos»; «…araciones que se le interesan respecto a»; «…(la afirmación contenida en el hecho»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 426.1 de la LEC
- art. 339.3 de la LEC
- arts. 412 y 426.3 de la LEC
- art. 426.5 de la LEC

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

### Formulario 0993 · Alegaciones complementarias y de aclaración

- Año del modelo: 2013
- Revisión 17-11-2026: 19 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Con la venia: (Opciones):— Tal como permite el art. 426.1 de la LEC la parte actora desea realizar una aclaración complementa- ria en relación con lo expuesto por el demandado en la contestación a la demanda en el fundamento de hecho [COMPLETAR], ya que si bien es cierto, y así lo expusimos en la demanda, que se firmó un contrato entre las partes según el cual mi representado se comprometía a [COMPLETAR], el contrario olvida mencionar que esta tarea resultó imposible porque la lluvia que cayó esos días impidió realizar cualquier labor agrícola. Como prueba [COMPLETAR] (acompañamos a efectos probatorios informe del perito D. [NOMBRE Y APELLIDOS], que acredita estos extremos, o presentaremos antes del juicio informe pericial del que se deberá dar traslado al contrario o interesamos que en aplicación del art. 339.3 de la LEC por el Tribunal se designe un perito con el título de [LOCALIDAD] para que dictamine sobre [DESCRIBIR])— Cuando esta parte reclama la propiedad de la finca de [COMPLETAR] está solicitando que se le declare el derecho dominical sobre una extensión de [COMPLETAR] m2, y cuyos lindes son [COMPLETAR] No incluye, por tanto, la reclamación la construcción situada en [COMPLETAR] porque la misma se encuentra fuera de los límites citados, tal y como se acredita con los planos que presentamos en este momento.— El actor, en aplicación de los arts. 412 y 426.3 de la LEC interesa añadir una petición accesoria a la ya manifestada en el suplico de la demanda consistente en que la condena de hacer del actor incluya también la contratación del seguro de daños materiales o seguro de caución exigido por el art. 19 de la Ley de ordenación de la edificación, a fin de garantizar la calidad y durabilidad de la obra que ha de realizar.— Después de contestar a la demanda, la parte demandada ha recibido notificación de la contesta- ción a la solicitud presentada ante [ÓRGANO] Tal y como se puede apreciar en este documento que ahora presentamos, se confirma lo que alegamos en el hecho n.º [NÚMERO] del citado escrito.— Tal y como permite el art. 426.5 de la LEC y en atención a la alegación de la parte [COMPLETAR] con respecto a [COMPLETAR] presentamos [COMPLETAR] (el documento sobre [DESCRIBIR] o el dictamen elaborado por D. relativo a [DESCRIBIR]) dirigido a rebatir lo alegado de contrario.— A instancia del Tribunal esta parte procede a realzar las aclaraciones que se le interesan respecto a [COMPLETAR] (la afirmación contenida en el hecho [COMPLETAR] o la aplicación del precepto [COMPLETAR] a este caso concreto). (razonar).

========================================================================
