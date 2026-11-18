---
name: escrito-conclusiones-modelo-general-926
description: "Redacta el escrito «Escrito de conclusiones: modelo general» (formulario 926 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Escrito de conclusiones: modelo general

> Formulario 0926 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] FECHA (3 veces)
- [ ] NÚMERO (3 veces)
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] DESCRIBIR
- [ ] Otros 17 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… en el momento procesal oportuno. Así el»; «…, que»; «…eguntas del Órgano judicial contestó que»; «…, con los números»; «…, acreditan que»; «…acreditaba que»; «…, especialista en»; «…el juicio, confirman su dictamen, ya que»; «…o en sentido afirmativo a la pregunta de»; «…e no ha sido impugnado de contrario. 2.–»; «…. 3.– Hechos alegados por»; «…rtos la otra parte, salvo los de los nos»; …

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

### Formulario 0926 · Escrito de conclusiones: modelo general

- Año del modelo: 2013
- Revisión 17-11-2026: 24 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Con la venia

Esta parte procede a formular sus conclusiones en los siguientes:

Términos

1.– Hechos alegados por esta parte y prueba: nos afirmamos y ratificamos en todos y cada uno de los hechos que alegamos en nuestro escrito de [FECHA], que han quedado debidamente acreditados con la prueba que en su momento propusimos y que se ha llevado a efecto en el momento procesal oportuno. Así el [COMPLETAR], ha reconocido al contestar a nuestra pregunta n.º [NÚMERO], que [COMPLETAR], e igualmente, a preguntas del Órgano judicial contestó que [COMPLETAR], según acabamos de oír.

Por otro lado los documentos presentados con nuestro escrito de [FECHA], con los números [COMPLETAR], acreditan que [COMPLETAR].

El informe pericial presentado con el n.º [NÚMERO] acreditaba que [COMPLETAR], y las aclaraciones presentadas por D. [NOMBRE Y APELLIDOS], especialista en [COMPLETAR], en este acto del juicio, confirman su dictamen, ya que [COMPLETAR].

El testigo propuesto por esta parte, D. [NOMBRE Y APELLIDOS], ha contestado en sentido afirmativo a la pregunta de [COMPLETAR], confirmando así el hecho n.º [NÚMERO] referido a [DESCRIBIR].

Por último hay que hacer constar que debe admitirse la presunción legal de convivencia de los cónyuges al haber presentado esta parte contrato de arrendamiento de vivienda para el matrimonio, que no ha sido impugnado de contrario.

2.– [COMPLETAR].

3.– Hechos alegados por [COMPLETAR] y su prueba: reiteramos nuestra oposición a los hechos que da como ciertos la otra parte, salvo los de los nos [COMPLETAR], que ya reconocimos como ciertos en el acto de la audiencia previa.

Su prueba no ha conseguido ni desvirtuar nuestras alegaciones ni acreditar las suyas.

Mi representado en confesión judicial no ha reconocido, a preguntas de mi compañero que [COMPLETAR]. Insistiendo en aclaraciones el propio Tribunal, ha mantenido en todo momento su negativa, según acabamos de oír.

En cuanto a los documentos que presentó con su [COMPLETAR], dimos por válidos en la audiencia previa los nos [COMPLETAR] y se impugnaron los nos [COMPLETAR]. Practicada prueba pericial caligráfica con relación al último de los citados, se afirmó la autenticidad de la firma de mi representado, a pesar de lo cual seguimos manteniendo que existe una falsedad ideológica en el mismo puesto que su contenido se cumplimentó después de llevarse a cabo dicha rúbrica.

Los testigos D. y D. [NOMBRE Y APELLIDOS], que han declarado en este acto, presentan respuestas confusas y que no arrojan ningún dato nuevo sobre los hechos. En todo caso no hay que olvidar que esta parte ha presentado tacha con respecto al primero de ellos para que no se valore su declaración por el Tribunal.

4.– Reiteramos nuestra argumentación jurídica, que en síntesis se basa en [COMPLETAR], y negamos la del contrario en lo que se oponga o contradiga a nuestras pretensiones.

5.– Finalmente acabamos interesando que se dicte sentencia conforme interesamos en el suplico de nuestro escrito de [FECHA].

========================================================================
