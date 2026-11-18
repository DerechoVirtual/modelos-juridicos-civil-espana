---
name: supuesto-excluido-requisito-procedibilidad-demandas-13
description: "Redacta el escrito «Supuesto excluido del requisito de procedibilidad en demandas civiles (MASC)» (formulario 13 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Supuesto excluido del requisito de procedibilidad en demandas civiles (MASC)

> Formulario 0013 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.

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

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 5.2 de la Ley Orgánica 1/2025
- art. 5 LO 1/2025
- art. 399 y 264 de la LEC
- art. 403 de la LEC
- art. 5.2 de la LO 1/2025
- artículo 158 del Código Civil
- art. 89.9 LOPJ

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

### Formulario 0013 · Supuesto excluido del requisito de procedibilidad en demandas civiles (MASC)

- Año del modelo: 2025
- Revisión 17-11-2026: restos de formato retirados; 2 llamadas a nota sin texto retiradas

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Mención que debe constar en los escritos de demanda de proceso declarativo, cuando no sea necesario acudir a un MASC antes de ejercitar acciones civiles. La mención deberá ir normalmente en los Fundamentos de Derecho; y si se diferencia fundamentos procesales de los materiales, irá al final de los procesales, como formal, después de la cuantía y clase de juicio.

En el escrito de demanda deberá consignarse:

CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda no está sujeta al previo intento de resolución de controversias en vía no jurisdiccional por tratarse de materias excluidas del requisito de procedibilidad de acuerdo con el art. 5.2 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

El art. 5 LO 1/2025 establece, con carácter general, que, en el orden jurisdiccional civil, para que sea admisible la demanda se considerará requisito de procedibilidad acudir previamente a algún medio adecuado de solución de controversias de los previstos en el art. 2, lo cual tiene concordancia con lo dispuesto en el art. 399 y 264 de la LEC, en cuanto a que debe constar en la demanda la descripción del proceso negociador, o la imposibilidad del mismo, en los casos en que sea preceptivo, acompañando el documento justificativo, o la declaración responsable de que no se ha podido llevar a cabo. Asimismo, el art. 403 de la LEC establece la inadmisión de la demanda por falta del requisito de procedibilidad.

Por otro lado, el art. 5.2 de la LO 1/2025 establece que se exigirá actividad negociadora previa a la vía jurisdiccional como requisito de procedibilidad en todos los procesos declarativos del Libro II y en los procesos especiales del Libro IV de la LEC, con excepción de los que tengan por objeto las siguientes materias: a) la tutela judicial civil de derechos fundamentales; b) la adopción de las medidas previstas en el artículo 158 del Código Civil; c) la adopción de medidas judiciales de apoyo a las personas con discapacidad; d) la filiación, paternidad y maternidad; e) la tutela sumaria de la tenencia o de la posesión de una cosa o derecho por quien haya sido despojado de ellas o perturbado en su disfrute; f) la pretensión de que el tribunal resuelva, con carácter sumario, la demolición o derribo de obra, edificio, árbol, columna o cualquier otro objeto análogo en estado de ruina y que amenace causar daños a quien demande; g) el ingreso de menores con problemas de conducta en centros de protección específicos, la entrada en domicilios y restantes lugares para la ejecución forzosa de medidas de protección de menores o la restitución o retorno de menores en los supuestos de sustracción internacional; h) el juicio cambiario.

Fuera de los supuestos excluidos, es importante señalar que en los procesos derivados de crisis familiares (separación, divorcio...) con elemento de violencia de género, está vedada la utilización de los MASC previo a la demanda judicial, por aplicación de lo dispuesto en el art. 89.9 LOPJ, ya que estos mecanismos no son adecuados y se prioriza el cauce penal y la protección de la víctima, en cuyo caso se expresará: "La presente demanda no está sujeta al previo intento de resolución de controversias en vía no jurisdiccional, por cuanto el art. 89.9 LOPJ excluye de los MASC los procesos derivados de crisis familiares en casos de violencia sobre la mujer".
