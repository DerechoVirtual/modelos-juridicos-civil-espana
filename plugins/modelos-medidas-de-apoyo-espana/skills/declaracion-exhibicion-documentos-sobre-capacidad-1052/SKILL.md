---
name: declaracion-exhibicion-documentos-sobre-capacidad-1052
description: "Redacta el escrito «Declaración o exhibición de documentos sobre capacidad, representación o legitimación» (formulario 1052 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Declaración o exhibición de documentos sobre capacidad, representación o legitimación

> Formulario 1052 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] Nº DE DOCUMENTO
- [ ] COLEGIO
- [ ] DESCRIBIR (3 veces)
- [ ] TELÉFONO
- [ ] ACTO O RESOLUCIÓN
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] IMPORTE
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, con DIN»; «…, con DIN [COMPLETAR], domiciliado en»; «…y número de fax»; «…o tiene intención de promover demanda de»; «…en el ejercicio de la acción de»; «…bjeto concreto de la demanda consiste en»; «…que afecta a la»; «…obre el que se pide declaración debido a»; «…nar interesada por las circunstancias de»; «…258 de la LEC radican en su condición de»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 263 de la LEC
- artículo 258 de la LEC

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

### Formulario 1052 · Declaración o exhibición de documentos sobre capacidad, representación o legitimación

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 24 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en nombre y representación de D./ Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], ante el Tribunal comparezco bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], colegiado núm.del Iltre. Colegio de Abogados de [COLEGIO], y como mejor proceda en derecho DIGO:

Que mediante el presente escrito, en nombre de mi representado y al amparo de lo dispuesto en el artículo 256.1.1.º de la LEC, promuevo DILIGENCIA PRELIMINAR de declaración bajo juramento o promesa de decir verdad sobre [DESCRIBIR] (capacidad, representación o legitimación) frente a D./Dña. [NOMBRE Y APELLIDOS], con

DIN [COMPLETAR], domiciliado en [COMPLETAR] y provisto de número de teléfono [TELÉFONO] y número de fax [COMPLETAR], basándome en los siguientes

ANTECEDENTES

Mi representado tiene intención de promover demanda de [COMPLETAR] en el ejercicio de la acción de [COMPLETAR] frente a [ACTO O RESOLUCIÓN]

El objeto concreto de la demanda consiste en [COMPLETAR] (detallar).

Para plantear adecuadamente dicha demanda precisa mi poderdante conocer el dato relativo a [DESCRIBIR] que afecta a la [COMPLETAR] (determinar si la circunstancia sobre la que se pretende la declaración hace referencia a capacidad, representación o legitimación).

Resulta necesario a mi mandante conocer el dato sobre el que se pide declaración debido a [COMPLETAR] (justificar la necesidad de la diligencia preliminar solicitada).

Resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

Es competente el Tribunal al que me dirijo en virtud de lo dispuesto en el artículo 257 de la Ley de Enjuiciamiento Civil (LEC), en relación con en el art. 85.1º LOPJ.

Procedimiento

La solicitud se tramitará por el cauce establecido en las artículos 258 y siguientes de la LEC.

Caución

El artículo 263 de la LEC exige el ofrecimiento de prestación de caución para responder de eventuales gastos y daños y perjuicios que se pudieran irrogar a la parte frente a la que se promueven estas diligencias. Realizo dicho ofrecimiento mediante otrosí.

Fondo

El artículo 256.1.1.º de la LEC habilita la preparación del juicio mediante la petición a la persona a que se pretende demandar de que «declare, bajo juramento o promesa de decir verdad, sobre algún hecho relativo a su capacidad, representación o legitimación, cuyo conocimiento sea necesario para el pleito, o exhiba los documentos en los que conste dicha capacidad, representación o legitimación».

En el presente caso se justifican la pertinencia y proporcionalidad de la diligencia preliminar interesada por las circunstancias de [COMPLETAR] (justificar mediante la alegación de las circunstancias concurrentes).

La justa causa y el interés legítimo de mi mandante que exige el artículo 258 de la LEC radican en su condición de [COMPLETAR] (detallar justificación).

 (desarrollar cuantas razones contribuyan a plantear la diligencia como adecuada a la finalidad perseguida y acreditar que la medida guarda proporcionalidad con dicho fin).

Por todo lo expuesto,

SUPLICO AL TRIBUNAL que tenga por presentado este escrito, con el poder y los documentos que se acompañan y sus preceptivas copias, se sirva admitirlo, teniendo por promovida la diligencia preliminar solicitada, y en su virtud requiera a D./Dña. [NOMBRE Y APELLIDOS] para que comparezca ante el tribunal a fin de declarar bajo juramento o promesa de decir verdad sobre [DESCRIBIR] (detallar objeto de la diligencia) contestando en el modo previsto para el interrogatorio de la parte a las preguntas que se le formulen, bajo apercibimiento de que si no comparece ni formula oposición se podrán tener por respondidas afirmativamente las preguntas que esta parte pretendiera formularle, teniendo por admitidos los hechos correspondientes a efectos del juicio posterior, todo ello con los demás pronunciamientos procedentes en derecho, y, una vez practicada la diligencia interesada, se me expida testimonio de su resultado.

Es Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

OTROSÍ DIGO: que a los efectos previstos en los artículos 256.3 y 258.3, y aun cuando esta parte entiende que la diligencia solicitada no la precisaría, ofrecemos prestar, en la forma y plazos legalmente establecidos, la caución de [IMPORTE] euros, o, subsidiariamente, la que fije el Tribunal, comprometiéndonos a constituir la caución que se señale.

NUEVAMENTE SUPLICO AL TRIBUNAL: tenga por hecho el anterior ofrecimiento de caución a los efectos legales oportunos.

Es Justicia que reitero en igual lugar y fecha.

========================================================================
