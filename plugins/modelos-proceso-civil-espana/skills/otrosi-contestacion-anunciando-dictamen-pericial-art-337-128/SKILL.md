---
name: otrosi-contestacion-anunciando-dictamen-pericial-art-337-128
description: "Redacta el escrito «Otrosí de contestación anunciando dictamen pericial (art. 337 LEC)» (formulario 128 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Otrosí de contestación anunciando dictamen pericial (art. 337 LEC)

> Formulario 0128 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] NÚMERO
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, el cual será elaborado por el perito D»; «…, con titulación»; «… anunciado debe emitirse por el perito D»; «…, con titulación»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 337.1 de la LEC

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

### Formulario 0128 · Otrosí de contestación anunciando dictamen pericial (art. 337 LEC)

- Año del modelo: 2022
- Revisión 17-11-2026: 5 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Documento adaptado a la reforma orgánica de la LO 1/2025

OTROSÍ DIGO: Que no habiendo sido posible la aportación del dictamen pericial que pretende aportar esta parte, el cual será elaborado por el perito D [COMPLETAR], con titulación [COMPLETAR], al que se ha hecho referencia en el hecho número [NÚMERO] de esta contestación a la demanda, por medio de este otrosí se anuncia su aportación tan pronto el mismo esté finalizado y en todo caso antes del término establecido en el artículo 337.1 de la LEC.

El dictamen pericial encargado por esta parte no ha podido ser aportado por falta de tiempo material para su elaboración por parte del perito, dada su complejidad y el corto término de emplazamiento, así como por la necesidad de acceso al inmueble para el reconocimiento pericial, al ser imprescindible examinar su estado para la elaboración del dictamen por el perito, pues el mismo tiene por objeto dictaminar la inexistencia de vicios constructivos en la vivienda de la actora objeto del contrato de compraventa y la posibilidad de que existan otras causas de deterioro no imputables a esta parte, a las que se ha hecho referencia en esta contestación, y más concretamente en los hechos número

El dictamen anunciado debe emitirse por el perito D [COMPLETAR], con titulación [COMPLETAR], que versará concretamente sobre los siguientes extremos:

Fundamos nuestra pretensión en la reiterada jurisprudencia que admite la denominada "entrega aplazada" del dictamen pericial, aludida tanto en el artículo 265.1.4º de la LEC, como en el 336.1 de la misma Ley procesal, siempre que se anuncie oportunamente en el escrito de contestación conforme a lo establecido en el artículo 337.1 de la LEC, tal como expresan, entre otras muchas, las SSTS 872/2010, de 27 diciembre y 485/2012 de 18 julio, habiendo afirmado la jurisprudencia que la exigencia de justificación ha de ser más flexible para los demandados, toda vez que no han elegido el tiempo para poder obtener ese dictamen, al estar sujeto al plazo para contestar a la demanda, por lo que es más lógico que no lo tengan a tiempo. En consecuencia, solicitamos que se tenga por anunciado la aportación de este informe de relevancia sustancial para la pretensión de esta parte sobre los hechos alegados en la contestación, al amparo de los artículos 265.1.4.º, 336.1 y 337.1 LEC, por la imposibilidad de su aportación en el momento de presentar este escrito de contestación a la demanda.

Al tiempo, solicitamos al Tribunal que autorice al perito el reconocimiento de la vivienda litigiosa, a fin de que pueda elaborar su dictamen, requiriendo a la parte actora que facilite el acceso el día y hora que se acuerde por el Tribunal.

En base a lo anterior,

SUPLICO al Tribunal que tenga por anunciada la aportación del dictamen pericial expresado en este otrosí tan pronto disponga del mismo esta parte, en el momento procesal oportuno, acordando requerir a la actora para que facilite el acceso a la vivienda litigiosa a efectos de reconocimiento por el perito, en el día y hora que se fije por el Tribunal.
