---
name: acta-notoriedad-ausencia-no-declarada-galicia-538
description: "Redacta el escrito «Acta de notoriedad de ausencia no declarada (Galicia)» (formulario 538 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acta de notoriedad de ausencia no declarada (Galicia)

> Formulario 0538 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] FECHA (2 veces)
- [ ] COLEGIO
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, con residencia en»; «…, mayor de edad, vecino/a de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 48 de la Ley 2/2006

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

### Formulario 0538 · Acta de notoriedad de ausencia no declarada (Galicia)

- Año del modelo: 2016
- Revisión 17-11-2026: 8 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [FECHA].

ANTE MI, Notario del Ilustre Colegio de [COLEGIO], con residencia en [COMPLETAR],

COMPARECE

D/Dña. [NOMBRE Y APELLIDOS], mayor de edad, vecino/a de [COMPLETAR], con domicilio en Exhibe DNI/NIF

Sujeto/a al Derecho civil de Galicia.

Intervienen en su propio nombre y derecho.

Juicio Notarial: Tiene a mi juicio capacidad e interés legítimo para este requerimiento.

Objeto: El compareciente me requiere a mí, el Notario, para acreditar por notoriedad la situación de ausencia no declarada de su cónyuge, Dña/D

EXPONE

Que Dña/D, se encuentra en paradero desconocido desde el [FECHA], siendo que no puede localizarse de ninguna manera (breve exposición del modo de la desaparición/y de los intentos de localización de la persona).

Que el/la compareciente, D./Dña. [NOMBRE Y APELLIDOS] es el cónyuge no separado legalmente o de hecho (o el descendiente mayor de edad y al ascendientes, por este orden) en la fecha de desaparición.

Que el ausente no ha previsto nada para esta situación, ni ha dejado nombrado representante ni firmado poder, y existen actos y negocios jurídicos de administración ordinaria que no puedan demorarse.

Que en atención al art. 48 de la Ley 2/2006, de 14 de junio, de Derecho civil de Galicia corresponde al cónyuge no separado legalmente o de hecho (o a los descendientes mayores de edad y a los ascendientes, por este orden) la representación del ausente de hecho en todos los actos y negocios jurídicos de administración ordinaria que no puedan demorarse y la obligación de velar por los intereses de éste.

Siendo lícito el objeto y fin de este requerimiento es aceptado por mí, el Notario, que cumplo en este mismo acto.

Prueba de confesión: Propone con tal carácter la exposición que antecede.

Prueba documental: Certificado de matrimonio del requirente.

Numero

ACTA DE NOTORIEDAD. CONCLUSIÓN

Yo, Notario hago constar:

Que en acta autorizada por mí el, número, se me requirió para lo que consta en la misma.

Que en el instrumento de referencia se practicaron las pruebas pertinentes.

Declaración de Notoriedad: Practicadas las pruebas referidas y siendo, a mi juicio, suficientes y satisfactorias, yo, el Notario, declaro por notoriedad el hecho de que D/Dña. [NOMBRE Y APELLIDOS] está en situación de ausencia no declarada, siendo que Dña./D será su representante a los efectos del art. 48 de la LDCG.

Dejo nota en la matriz referenciada de haberse concluido positivamente lo requerido.

========================================================================
