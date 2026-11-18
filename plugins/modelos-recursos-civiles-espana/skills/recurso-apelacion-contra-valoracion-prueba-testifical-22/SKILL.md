---
name: recurso-apelacion-contra-valoracion-prueba-testifical-22
description: "Redacta el escrito «Recurso de apelación contra la valoración de la prueba testifical» (formulario 22 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Recurso de apelación contra la valoración de la prueba testifical

> Formulario 0022 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] SEDE (3 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (4 veces)
- [ ] ÓRGANO O PERSONA
- [ ] LUGAR
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…5. Antecedentes: Procedimiento Ordinario»; «… Sentencia en el procedimiento ordinario»; «…, absolviendo a»; «…En el Fundamento»; «…, empleado de la entidad»; «…, se desprende que»; «…de»; «…de [COMPLETAR] de»

## Párrafos opcionales (1)

Inclúyelos solo si encajan en los hechos:

- OTROSÍ PRIMERO DIGO: que al amparo de lo establecido en el artículo 231 de la Ley de Enjuiciamiento Civil, est…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 376 de la LEC

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

### Formulario 0022 · Recurso de apelación contra la valoración de la prueba testifical

- Año del modelo: 2024
- Revisión 17-11-2026: 1 párrafos opcionales señalados; 22 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Antecedentes:

Procedimiento Ordinario [COMPLETAR]

Tribunal de Instancia [SEDE] de [LOCALIDAD]

A LA ILMA. AUDIENCIA PROVINCIAL DE [LOCALIDAD]

D./Dña. [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales y de [NOMBRE DEL REPRESENTADO/A], representación que tengo acreditada en los presentes autos, ante el la Ilma. Sala comparezco y como mejor proceda en Derecho,

DIGO:

Que, en virtud de lo establecido en los artículos 455 y siguientes de la Ley de Enjuiciamiento Civil (en adelante, "LEC), dentro del plazo legal de 20 días concedido a esta parte a tal efecto, por medio del presente escrito interpongo RECURSO DE APELACIÓN contra la Sentencia de fecha [FECHA] dictada en los presentes autos, en atención a las siguientes,

Alegaciones

Primera.– En fecha [FECHA] se dictó Sentencia en el procedimiento ordinario [COMPLETAR] seguido ante la Sección Civil del Tribunal de Instancia [SEDE] de [SEDE], cuya parte dispositiva acuerda desestimar la demanda interpuesta por [ÓRGANO O PERSONA], absolviendo a [COMPLETAR] de todas las peticiones, con expresa imposición en costas a mi mandante.

Segunda.– Que no estando conforme esta parte con dicha resolución, dicho sea con los debidos respetos y en estrictos términos de defensa, por medio del presente escrito, se impugnará el error en la valoración probatoria de la Sentencia en lo que a la prueba testifical se refiere.

Tercera.– A juicio de esta parte, se ha producido una defectuosa valoración de la prueba testifical, infringiendo lo dispuesto en el artículo 376 de la LEC, al no apreciarse la absoluta falta de imparcialidad del testigo D. [NOMBRE Y APELLIDOS]

En el Fundamento [COMPLETAR] de la Sentencia se afirma que, de la testifical de D. [NOMBRE Y APELLIDOS], empleado de la entidad [COMPLETAR], se desprende que [COMPLETAR]

Esta parte se muestra disconforme con dicha afirmación, siendo preciso advertir que el testigo que prestó declaración en el acto de juicio no es un tercero ajeno al procedimiento, sino que presenta un claro interés y directo en el resultado del mismo habida cuenta que es empleado de la entidad demandada.

El artículo 376 de la LEC determina que las pruebas testificales serán valoradas conforme a las reglas de la sana crítica, debiendo analizarse las circunstancia que concurran en los testigos a tal efecto.

Como advertimos, la valoración efectuada en la Sentencia impugnada no se corresponde con dicho principio, careciendo la deposición del testigo de la más absoluta credibilidad dados los estrechos vínculos laborales que presenta con la entidad demandada, que redundan en la existencia de un interés directo en que el pleito se resuelva a favor de su empleados.

Ese interés ha sido reconocido por la jurisprudencia, citándose a meros efectos ilustrativos, la Sentencia de la Audiencia Provincial de Barcelona núm. 214/2017 de 30 de marzo, que razona:

«Tampoco la prueba testifical contradice lo anterior pues las reglas de la sana crítica llevan a considerar, el testimonio de empleados o exempleados de la demandada, la escasa relevancia de los mismos en esta clase de situaciones como la que nos ocupa».

En consecuencia, la correcta valoración de la prueba testifical conduce a la estimación de la demanda interpuesta por esta parte.

Cuarta.– Al estimarse el presente recurso, la Sentencia impugnada debe ser revocada y, en consecuencia, deben imponerse las costas a la adversa.

Por lo expuesto,

A LA SALA SUPLICO: Que tenga por presentado el presente RECURSO DE APELACIÓN, se sirva admitirlo y, en su virtud, previos los trámites legales oportunos, en su día, dicte Sentencia por la que, tras la estimación del mismo, revoque la Sentencia de [FECHA] de [COMPLETAR] de [COMPLETAR], y, acuerde estimar la demanda interpuesta por esta parte con expresa imposición en costas a la adversa.

[OPCIONAL — incluir si procede]

OTROSÍ PRIMERO DIGO: que al amparo de lo establecido en el artículo 231 de la Ley de Enjuiciamiento Civil, esta parte manifiesta expresamente su voluntad de dar el estricto cumplimiento a cuantos requisitos le resulten legalmente exigibles en el curso del presente procedimiento, en todas sus instancias e incidentes, subsanando cualquier eventual defecto en que pueda incurrir en sus actos procesales.

A LA SALA SUPLICO, que tenga por efectuada la anterior manifestación a los efectos legales oportunos.

Es justicia que pido en [LUGAR], a [FECHA].

Procurador/a	Abogado/a

Fdo. D./Dña. [NOMBRE Y APELLIDOS] 	Fdo. D./Dña. [NOMBRE Y APELLIDOS]
