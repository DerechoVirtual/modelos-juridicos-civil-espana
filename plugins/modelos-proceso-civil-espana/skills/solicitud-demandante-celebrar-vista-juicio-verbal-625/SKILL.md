---
name: solicitud-demandante-celebrar-vista-juicio-verbal-625
description: "Redacta el escrito «Solicitud del demandante para celebrar vista en juicio verbal» (formulario 625 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Solicitud del demandante para celebrar vista en juicio verbal

> Formulario 0625 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Escrito construido sobre el trámite del art. 438.4 LEC en la redacción de la Ley 42/2015 (pedir o renunciar a la vista en 3 días): suprimido por la LO 1/2025. Hoy: prueba en 5 días (art. 438.8), impugnaciones en 3 días (438.9) y auto del tribunal sobre la vista (438.10).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LOCALIDAD
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] DESCRIBIR
- [ ] NÚMERO
- [ ] COLEGIO
- [ ] LUGAR
- [ ] FECHA
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «… SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 438.4 LEC
- Ley 42/2015

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

### Formulario 0625 · Solicitud del demandante para celebrar vista en juicio verbal

- Año del modelo: 2016
- Revisión 17-11-2026: 2 puntualizaciones normativas añadidas en el texto; 11 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)
- Avisos de la revisión: Escrito construido sobre el trámite del art. 438.4 LEC en la redacción de la Ley 42/2015 (pedir o renunciar a la vista en 3 días): suprimido por la LO 1/2025. Hoy: prueba en 5 días (art. 438.8), impugnaciones en 3 días (438.9) y auto del tribunal sobre la vista (438.10).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito del demandante que procediendo a evacuar el trámite conferido con el traslado de la contestación a la demanda sobre la procedencia de la vista, considera necesaria su celebración.

Hasta la reforma operada por LO 1/2025 -esto es, en procesos incoados antes del 3 de abril de 2025-, la decisión de la celebración de la vista, le correspondía a las partes o al juez, de tal modo que la vista se celebrará cuando alguna de las partes lo solicite, en cuyo caso el Letrado de la Administración de Justicia señalará día y hora para la misma, o cuando el tribunal considere procedente su celebración a pesar de no haber sido instada por alguna de las partes.

A tal efecto, el art. 438.4 LEC reformado por la Ley 42/2015, de 5 de octubre, expresamente prevé [NOTA DE REVISIÓN: Régimen derogado: la LO 1/2025 suprimió el trámite de 3 días para pedir vista; ahora prueba en 5 días (art. 438.8) y auto sobre la vista (art. 438.10). Fuente: LEC art. 438.8-10 (redacc. LO 1/2025, BOE-A-2025-76).] que la parte demandada en la contestación de la demanda debe de pronunciarse sobre si quiere o no la celebración de la vista, debiendo el demandante pronunciarse sobre ello en el plazo de tres días desde el traslado del escrito de contestación a la demanda.

Por lo tanto, en las partes recae la carga de pronunciarse sobre la pertinencia de la celebración de la vista. Con carácter general, el demandante se manifestará al respecto en el plazo de tres días desde el traslado del escrito de contestación, y el demandado lo hará en su escrito de contestación. Es decir, el demandado es al que corresponde, en primer lugar, manifestarse sobre dicha pertinencia. En segundo lugar, una vez recibida la contestación en la que constará o no dicha manifestación, corresponderá al demandante.

Desde la modificación operada por LO 1/2025 -aplicable a los procedimientos iniciados a partir del 3 de abril de 2025-, la decisión sobre la celebración de la vista queda fuera del ámbito de decisión de las partes, pudiendo el juez acordar que no se celebre, facultad que permite evitar celebración de vistas innecesarias si no hay prueba admitida o toda es documental (art. 438.10 III LEC).

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA [COMPLETAR] DE [LOCALIDAD]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según tengo acreditado en los autos del juicio verbal n.º [Nº DE PROCEDIMIENTO]/[AÑO], sobre [DESCRIBIR], asistido del Letrado D./Dña. [NOMBRE Y APELLIDOS], ejerciente n.º [NÚMERO] del Iltre. Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco y, como mejor proceda en Derecho, DIGO:

PRIMERO

Que el pasado día D./Dña. [NOMBRE Y APELLIDOS] he recibido traslado del escrito de contestación a la demanda formulado por la representación de D./Dña. [NOMBRE Y APELLIDOS], en el cual se manifiesta no considerar necesaria la celebración de vista en este juicio.

SEGUNDO

Que de conformidad con lo dispuesto en el art. 438.4 LEC en la redacción dada por la Ley 42/2015, de 5 de octubre, y dentro del plazo de tres días allí establecido, esta parte interesa la celebración de vista al entender que resulta pertinente por tratarse la controversia de una clara cuestión fáctica que requiere de la práctica de prueba.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito acuerde la celebración de vista en este juicio verbal, señalando el Letrado de la Administración de Justicia día y hora para la misma.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

========================================================================
