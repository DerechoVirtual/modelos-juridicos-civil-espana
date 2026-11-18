---
name: otrosi-cesacion-inmediata-actividad-1345
description: "Redacta el escrito «Otrosí: cesación inmediata de la actividad» (formulario 1345 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Otrosí: cesación inmediata de la actividad

> Formulario 1345 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] IMPORTE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de inmediata cesación de la actividad de»; «…emanda se han desarrollado las causas de»; «…n este apartado y que, en síntesis, son:»; «…creditan la existencia de la actuación y»; «…nto en la realización de la actividad de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 726 de la LEC
- art. 728 de la LEC
- art. 737 de la LEC

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

### Formulario 1345 · Otrosí: cesación inmediata de la actividad

- Año del modelo: 2013
- Revisión 17-11-2026: 10 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

OTROSÍ DIGO: Que según permiten los artículos 721, 727.7.ª y 730 de la LEC y artículo 7.2 de la Ley de Propiedad Horizontal interesamos que se acuerde desde este momento la medida cautelar de inmediata cesación de la actividad de [COMPLETAR], objeto de esta demanda, por parte del demandado D./Dña. [NOMBRE Y APELLIDOS], con expreso apercibimiento de incurrir en delito de desobediencia en caso de no actuar conforme se le requerirá.

Primero.- En el relato fáctico de esta demanda se han desarrollado las causas de [COMPLETAR] de la actuación de D./Dña. [NOMBRE Y APELLIDOS], que damos por reproducidas en este apartado y que, en síntesis, son: [COMPLETAR].

Según exige el art. 726 de la LEC, existe apariencia de buen derecho en nuestra pretensión, puesto que los documentos que presentamos acreditan la existencia de la actuación y [COMPLETAR] que causa a la Comunidad.

 Según se ha indicado en la demanda principal se aporta como documento nº 1 índice numerado de los documentos que se presentan tanto con la demanda como con esta pretensión de medida cautelar.

La dilación que supone toda actuación procesal puede impedir o dificultar los efectos que una más que posible sentencia estimatoria de nuestras pretensiones pueda ocasionar. Por esa razón, el art. 728 de la LEC permite la adopción de las medidas necesarias para conseguir la efectividad de la resolución que se pudiera dictar.

De no adoptarse esta medida con carácter previo a la resolución del pleito, se podría ocasionar a la Comunidad un grave perjuicio.

Segundo.- Según exige el art. 737 de la LEC, desde este momento ofrecemos caución en metálico para ingresar en la cuenta de consignación del Tribunal por importe de [IMPORTE].

NUEVAMENTE SUPLICO: Que se tenga por hecha la anterior petición a fin de que se cite a las partes a comparecencia de medidas cautelares con el fin de que se dicte orden de cesación de actividad, acordando requerir personalmente a D./Dña. [NOMBRE Y APELLIDOS] para que cese desde el mismo momento en la realización de la actividad de [COMPLETAR], así como que acredite esta paralización ante el Tribunal, todo ello con expreso apercibimiento de incurrir en delito de desobediencia en caso contrario.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
