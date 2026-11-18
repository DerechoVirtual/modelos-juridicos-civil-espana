---
name: clausula-no-vulnerabilidad-economica-arrendatario-62
description: "Redacta el escrito «Cláusula de no vulnerabilidad económica del arrendatario» (formulario 62 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Cláusula de no vulnerabilidad económica del arrendatario

> Formulario 0062 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Planteamiento superado: los arts. 439.6.c) y 439.7 LEC fueron anulados (STC 26/2025, BOE-A-2025-4079) y la vulnerabilidad se aprecia en el proceso (arts. 441.5-7 y 22.6 LEC, art. 2 RDL 29/2026); eficacia de la cláusula dudosa.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…simismo, se autoriza por el arrendatario»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 439.6 y 7 LEC
- arts. 439.6 y 7 y 441.5, 6 y 7 LEC
- Ley 12/2023

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

### Formulario 0062 · Cláusula de no vulnerabilidad económica del arrendatario

- Año del modelo: 2023
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; 1 llamadas a nota sin texto retiradas; 1 campos de relleno marcados en blanco
- Avisos de la revisión: Planteamiento superado: los arts. 439.6.c) y 439.7 LEC fueron anulados (STC 26/2025, BOE-A-2025-4079) y la vulnerabilidad se aprecia en el proceso (arts. 441.5-7 y 22.6 LEC, art. 2 RDL 29/2026); eficacia de la cláusula dudosa.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Cláusula contractual haciendo constar en el contrato de arrendamiento de vivienda que el arrendatario y su unidad familiar no son vulnerables a los efectos de eludir lo dispuesto en los arts. 439.6 y 7 LEC [NOTA DE REVISIÓN (comprobar): El art. 439.6.c) y el 439.7 LEC fueron anulados (STC 26/2025). La cláusula no puede impedir que el tribunal valore la vulnerabilidad en el proceso (arts. 441.5-7 y 22.6 LEC; art. 2 RDL 29/2026). Fuente: LEC (Ley 1/2000), BOE-A-2000-323, art. 439.6-7; STC 26/2025, BOE-A-2025-4079; LEC (Ley 1/2000), BOE-A-2000-323, arts. 22.6 y 441; RDL 29/2026, BOE-A-2026-20823 (convalidado: BOE-A-2026-23755), art. 2.] (en el caso del gran tenedor) y 441.5, 6 y 7 LEC (cuando se trate de no gran tenedor).

Ambas partes convienen en que ni el arrendatario ni la unidad familiar son vulnerables a los efectos previstos en los arts. 439.6 y 7 y 441.5, 6 y 7 LEC no siendo preciso en el caso de incumplimiento por el arrendatario firmante de este contrato de sus obligaciones la averiguación de la situación de vulnerabilidad del arrendatario, habida cuenta el reconocimiento de su no concurrencia, eximiendo de su constatación en el procedimiento judicial que se desee incoar, o que se haya incoado (según sea gran tenedor o no el actor).

Asimismo, se autoriza por el arrendatario [COMPLETAR] en el presente contrato a usar los documentos que acreditan la no vulnerabilidad ante la Administración que corresponda en caso de incumplimiento por el arrendatario de sus obligaciones.

Para evitar situaciones de retraso en la tramitación de procedimientos en supuestos de inquiokupación VICENTE MAGRO SERVET propone en su artículo titulado: Remedio ante la Ley 12/2023, de 24 de mayo de vivienda: la constancia en el contrato de arrendamiento de la no vulnerabilidad del arrendatario (2023) dejar constancia en el contrato de arrendamiento de una cláusula semejante a la que recoge el modelo.
