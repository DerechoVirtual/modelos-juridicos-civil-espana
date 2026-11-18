---
name: solicitud-mediacion-previa-demanda-masc-10
description: "Redacta el escrito «Solicitud de mediación previa a la demanda (MASC)» (formulario 10 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Solicitud de mediación previa a la demanda (MASC)

> Formulario 0010 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] DNI/NIE (2 veces)
- [ ] C.P. (2 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] TELÉFONO (2 veces)
- [ ] FECHA
- [ ] IMPORTE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 15 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…25). A LA INSTITUCIÓN DE MEDIACIÓN DE D.»; «…, y domiciliado en»; «…, calle [CALLE], núm. [NÚMERO], piso»; «…, núm. [NÚMERO], piso [COMPLETAR], letra»; «…letra [COMPLETAR], dirección electrónica»; «…, en su propio nombre, EXPONE:1)»; «…ión ante esa Institución, respecto de D.»; «…, y domiciliado en»; «…, calle [CALLE], núm. [NÚMERO], piso»; «…, núm. [NÚMERO], piso [COMPLETAR], letra»; «…letra [COMPLETAR], dirección electrónica»; «…aña por copia a la presente solicitud.2)»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 5.1 y 14.2 LO 1/2025
- art. 16 Ley 5/2012
- artículo 403.2 de la LEC

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

### Formulario 0010 · Solicitud de mediación previa a la demanda (MASC)

- Año del modelo: 2025
- Revisión 17-11-2026: saltos de párrafo recuperados (texto venía pegado); 28 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de solicitud de mediación a los efectos de cumplir el requisito de procedibilidad para la iniciación de la vía jurisdiccional, conforme a los arts. 5.1 y 14.2 LO 1/2025, y art. 16 Ley 5/2012 (aplicable a procesos incoados desde el 3 de abril de 2025). A LA INSTITUCIÓN DE MEDIACIÓN DE D. [COMPLETAR], mayor de edad, con DNI [DNI/NIE], y domiciliado en [COMPLETAR], C.P. [C.P.], calle [CALLE], núm. [NÚMERO], piso [COMPLETAR], letra [COMPLETAR], dirección electrónica [COMPLETAR], y teléfono [TELÉFONO], en su propio nombre, EXPONE:1) [COMPLETAR] Que solicito la iniciación del procedimiento de mediación ante esa Institución, respecto de D. [COMPLETAR], mayor de edad, con DNI [DNI/NIE], y domiciliado en [COMPLETAR], C.P. [C.P.], calle [CALLE], núm. [NÚMERO], piso [COMPLETAR], letra [COMPLETAR], dirección electrónica [COMPLETAR], y teléfono [TELÉFONO], a fin de solucionar la controversia que se expone a continuación en relación al contrato de arrendamiento de fecha [FECHA] suscrito por ambas partes que se acompaña por copia a la presente solicitud.2) [COMPLETAR] Que esta solicitud se formula al amparo de lo dispuesto en el art. 16.1.c) de la Ley de Mediación, con carácter previo al ejercicio de acciones judiciales y en cumplimiento del requisito de procedibilidad previsto en el artículo 403.2 de la LEC. No existe pacto de mediación entre las partes y no se ha iniciado ninguna actuación en vía judicial por la controversia que paso a exponer.3) [COMPLETAR] El objeto de la controversia es determinar quién debe asumir el coste de las obras de reparación del inmueble arrendado, realizadas en las fechas [COMPLETAR] y consistentes en El importe de las obras asciende a [IMPORTE] euros, según detalle que se recoge en la relación y facturas que acompaño, las cuales han sido abonadas por el arrendatario solicitante, pero que, según contrato, entiendo que debería abonar el arrendador, quien se ha negado a su pago, por lo que me veo en la obligación de acudir a la vía de la mediación para intentar la solución de la controversia.4) [COMPLETAR] Que de conformidad con lo dispuesto en el art. 16 de la Ley de Mediación esta parte acepta las prescripciones de procedimiento recogidas en los estatutos de la institución.

En virtud de lo expuesto,

SOLICITO DE LA INSTITUCIÓN, que tenga por formulada la presente y en su virtud, proceda a la iniciación del procedimiento de mediación, designando mediador y citando a las partes a la sesión inicial, continuando el procedimiento conforme a las reglas de la institución, y a fin de resolver la controversia que dejo expuesta.

En [LUGAR], a [DÍA] de [MES] de [AÑO].Firma del solicitante
