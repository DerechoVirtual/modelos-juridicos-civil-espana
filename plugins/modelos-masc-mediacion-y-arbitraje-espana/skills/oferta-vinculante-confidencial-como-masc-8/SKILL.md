---
name: oferta-vinculante-confidencial-como-masc-8
description: "Redacta el escrito «Oferta vinculante confidencial como MASC» (formulario 8 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oferta vinculante confidencial como MASC

> Formulario 0008 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] LUGAR
- [ ] FECHA
- [ ] COLEGIO
- [ ] LOCALIDAD (2 veces)
- [ ] DESCRIBIR
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…: Asunto: Oferta Vinculante Confidencial»; «…, con número de colegiado/a»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 5.1 y 17 LO 1/2025
- artículo 9 de la Ley Orgánica 1/2025
- artículos 5.1 y 17 de la Ley Orgánica 1/2025
- art. 17 LO 1/2025
- art. 6.2 LO 1/2025
- art. 17.4 LO 1/2025
- art. 245.5 LEC
- art. 245 bis LEC

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

### Formulario 0008 · Oferta vinculante confidencial como MASC

- Año del modelo: 2025
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 10 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Propuesta de solución dirigida a la otra parte a los efectos de cumplir el requisito de procedibilidad para la iniciación de la vía jurisdiccional, conforme a los arts. 5.1 y 17 LO 1/2025.

Formulario adaptado a la reforma procesal de la LO 1/2025.

Oferente: D/Dª [NOMBRE Y APELLIDOS]

Domicilio:

Correo electrónico:

Destinatario: D/Dª [NOMBRE Y APELLIDOS]:

Domicilio:

Correo electrónico:

Asunto: Oferta Vinculante Confidencial [COMPLETAR]

En [LUGAR], a [FECHA].

Estimado Sr./Sra. [NOMBRE Y APELLIDOS]:

Don/Doña [NOMBRE Y APELLIDOS], con número de colegiado/a [COMPLETAR] del Ilustre Colegio de Abogados de [COLEGIO] y despacho abierto en [LOCALIDAD], emito oferta vinculante en nombre y representación de Don/Doña [NOMBRE Y APELLIDOS] mayor de edad, con domicilio en [LOCALIDAD], con el objetivo de resolver la controversia existente en relación con [DESCRIBIR].

1. Antecedentes

2. Términos de la oferta

3. Confidencialidad

Esta oferta tiene carácter confidencial, por lo que su contenido no podrá ser divulgado a terceros, de conformidad con lo dispuesto en el artículo 9 de la Ley Orgánica 1/2025.

4. Aceptación

La aceptación de esta oferta deberá ser expresa e irrevocable, y deberá ser comunicada por escrito a esta parte en el plazo indicado en el punto 2. La forma de remisión de la aceptación deberá permitir dejar constancia de la identidad del aceptante, de su recepción efectiva por nuestra parte y de la fecha en que se produce dicha recepción, así como de su contenido.

5. Decaimiento de la oferta

En caso de que esta oferta sea rechazada, o no sea aceptada expresamente en el plazo indicado, decaerá automáticamente, quedando mi cliente en libertad para ejercitar las acciones que le correspondan ante el tribunal competente (o continuar con las ya iniciadas), habiendo cumplido, en su caso, el requisito de procedibilidad para la interposición de la correspondiente demanda en vía jurisdiccional de conformidad a lo dispuesto en los artículos 5.1 y 17 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia

Atentamente,

Firma del oferente

NOTAS DEL FORMULARIO

(1) Bajo esta denominación regula el art. 17 LO 1/2025 un instrumento que puede definirse como la actividad o, si se prefiere, la actuación llevada a cabo por uno de los sujetos implicados en un conflicto jurídico, consistente en dirigir al sujeto que ocupa el otro lado de la controversia, una propuesta de solución que, tras ser ofrecida y una vez aceptada, resulta inmodificable y de obligado cumplimiento para el oferente; una propuesta u oferta –conforme revela su denominación– planteada de forma confidencial o privada, con el límite que representa la necesidad de dejar constancia acreditativa de su formulación; algo, por otra parte lógico, en la medida en que, fructifique o no en acuerdo, la sola propuesta en las condiciones que legalmente se determinan, permite entender agotada la "actividad negocial previa" que da acceso a la vía judicial y, con ella, a la solución a través del proceso.

Conforme señala el art. 17.2 LMEP la forma de remisión tanto de la oferta como de la aceptación –que, puesto que no se explicita, podría ser cualquiera siempre que observe la exigencia que seguidamente se menciona– tendrá que dar constancia "de la identidad del oferente, de su recepción efectiva por la otra parte y de la fecha en la que se produce dicha recepción, así como de su contenido".

En todo caso, según se desprende de lo dispuesto por el art. 6.2 LO 1/2025, si se acude a la formulación de una oferta vinculante "ya sea con el objeto de cumplir el requisito de procedibilidad o (se esté) ante un supuesto de derivación judicial" será preceptiva la asistencia letrada a las partes, excepción hecha del supuesto en que la cuantía del asunto controvertido no supere los 2.000 euros o una ley lo exceptúe expresamente.

Es importante mencionar que la oferta vinculante tiene carácter confidencial, y la aceptación de la misma tiene efectos irrevocables. Esto quiere decir que tal oferta no podrá ser aportada en el proceso (o debe ser inadmitida, en caso de aportarse) así como que una vez aceptada, obliga a ambas partes a ser cumplida.

Salvo que la parte requirente establezca otro plazo mayor, el art. 17.4 LO 1/2025 estipula el plazo de 1 mes desde la recepción de la oferta para que la contraparte acepte o rechace la misma. En caso de que la oferta sea rechazada expresamente o no aceptada dentro del plazo legalmente estipulado, podrá el oferente ejercitar las correspondientes acciones legales ante el tribunal, puesto que el oferente ha cumplido con el requisito de procedibilidad que exige la LO 1/2025.

Importante destacar que el art. 245.5 LEC reformado por LO 1/2025 recoge en relación a la oferta vinculante confidencial, un supuesto concreto de tratamiento de las costas procesales. En concreto, cuando la oferta no haya sido aceptada por la otra parte y la resolución judicial dictada sea sustancialmente similar al contenido de la oferta que no fue aceptada, podrá solicitar el oferente la exoneración de su pago o la moderación de su cuantía, presentando para ello, en la pieza de la tasación de costas, la documentación –confidencial- relacionada con la oferta (vid. nuevo art. 245 bis LEC introducido por LO 1/2025).
