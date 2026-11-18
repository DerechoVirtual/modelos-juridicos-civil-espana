---
name: planteamiento-cuestion-prejudicial-ante-tjue-440
description: "Redacta el escrito «Planteamiento de cuestión prejudicial ante el TJUE» (formulario 440 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Planteamiento de cuestión prejudicial ante el TJUE

> Formulario 0440 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

El formulario no tiene campos marcados: revisa el texto por si hay datos implícitos.

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

### Formulario 0440 · Planteamiento de cuestión prejudicial ante el TJUE

- Año del modelo: 2018
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Otrosí de demanda en proceso declarativo interesando al Tribunal el planteamiento de cuestión prejudicial de derecho comunitario.

Formulario adaptado a la reforma procesal de la LO 1/2025.

OTROSÍ DIGO que, al amparo de lo dispuesto en el art. 267 del Tratado de Funcionamiento de las Comunidades Europeas, en relación con el art. 43 de la Ley de Enjuiciamiento Civil, interesa a esta parte el planteamiento de la siguiente cuestión prejudicial de derecho comunitario (1):

Por lo que,

SUPLICO AL TRIBUNAL

que tenga por solicitado, si lo considera necesario, el planteamiento de cuestión prejudicial de Derecho Comunitario respecto del extremo referido, dando traslado a la otra parte para oírla y dictar resolución por la que acuerde la suspensión del curso de las actuaciones, en el estado en que se hallen, hasta que se resuelva la cuestión prejudicial, a cuyo fin deberá plantearla ante el ante el Tribunal de Justicia de la Unión Europea en la forma que a tal fin se establece en el precitado art. 267 del Tratado de Funcionamiento de las Comunidades Europeas.

Firma:

NOTAS DEL FORMULARIO

(1) Conforme al art. 267 TFUE el planteamiento de una cuestión prejudicial sobre Derecho comunitario europeo ante el Tribunal de Justicia de la Unión Europea —TJUE— suspende el proceso en el que surge. La sentencia que dicte el TJUE no resuelve el objeto del litigio en el que se suscitó pero es vinculante para el tribunal que planteó la cuestión.

La competencia del TJUE para pronunciarse con carácter prejudicial se limita a dos clases de asuntos:

— Interpretación de los Tratados.
— Validez e interpretación de los actos adoptados por las instituciones, órganos u organismos de la Unión.

La legitimación para promover la cuestión prejudicial comunitaria la ostenta el órgano jurisdiccional nacional, que puede o, en su caso, debe plantear la misma al Tribunal de Justicia de las Comunidades Europeas.

Así, el planteamiento resulta facultativo u obligatorio para el órgano judicial nacional, según que exista posibilidad de interponer recurso en el Derecho nacional interno:

— Si se plantea una cuestión ante un órgano judicial de uno de los estados miembros, dicho órgano podrá pedir al Tribunal que se pronuncie sobre la misma, si estima necesaria una decisión al respecto para poder emitir su fallo.
— Si se plantea en un asunto pendiente ante un órgano judicial nacional cuyas decisiones no son susceptibles de ulterior recurso judicial en el Derecho interno, dicho órgano estará obligado a someter la cuestión al Tribunal.

Las partes o el Fiscal sólo pueden solicitar a la jurisdicción nacional el planteamiento de la cuestión sin que ello suponga obligación alguna por parte del órgano jurisdiccional.]

========================================================================
