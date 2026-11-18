---
name: comunidad-agrupada-estatutos-1235
description: "Redacta el escrito «Comunidad agrupada: estatutos» (formulario 1235 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Comunidad agrupada: estatutos

> Formulario 1235 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LOCALIDAD
- [ ] DESCRIBIR
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…spectivas Comunidades de Propietarios de»; «…nchas de tenis, las zonas ajardinadas de»; «…las comunidades integradas: Comunidad de»; «…,%. Comunidad de»; «…,%. Comunidad de»; «…,%. Comunidad de»; «…ragados en exclusiva por las Comunidades»; «…contratado por la Junta de Propietarios.»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Junta y Tribunales / Mediación civil y Tribunales — el texto de cada opción no venía en el formulario original

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Ley 49/1960

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

### Formulario 1235 · Comunidad agrupada: estatutos

- Año del modelo: 2013
- Revisión 17-11-2026: 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 10 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

La Agrupación de Comunidades denominada, constituida por título y formada por las siguientes fincas y las respectivas Comunidades de Propietarios de [COMPLETAR], se regirá por las siguientes reglas aprobadas por Junta constituyente de fecha tras refrendo de cada una de las Comunidades agrupadas:

Son elementos comunes de la Agrupación de Comunidades: la garita de acceso a la urbanización, los viales descritos como, las instalaciones deportivas situadas en y consistentes en dos piscinas y cuatro canchas de tenis, las zonas ajardinadas de [COMPLETAR], dos salas situadas en [LOCALIDAD], accesos a garaje.

Son SERVICIOS COMUNES:.

De cada una de las comunidades integradas:

Comunidad de [COMPLETAR],%.

Comunidad de [COMPLETAR],%.

Comunidad de [COMPLETAR],%.

Comunidad de [COMPLETAR],%.

Todos los gastos de esta Agrupación se distribuirán según el criterio de las cuotas de participación de cada una de las Comunidades, fijadas en el punto anterior.

Los gastos relativos a [DESCRIBIR] serán sufragados en exclusiva por las Comunidades [COMPLETAR]

Cada Comunidad de Propietarios contribuirá mensualmente con la cifra que se apruebe cada año al mantenimiento de los elementos y servicios comunes, y que para este año se cifra en.

Cada Comunidad de Propietarios deberá contar con su preceptivo fondo de reserva.

Serán los descritos en cada uno de los Estatutos de su propia Comunidad. Respecto a los elementos comunes de la Agrupación ostentan el derecho a usarlos y disfrutar de ellos de forma adecuada y según las características de cada uno y tienen la obligación de conservarlos y evitar causar daños o desperfectos.

1.º Junta de Propietarios: estará compuesta por los presidentes de las Comunidades integradas en esta Agrupación, que ostentan la representación del conjunto de comuneros de su Comunidad. Esta Junta tendrá competencia para adoptar decisiones que afecten exclusivamente a los elementos y servicios comunes descritos en el punto primero.

2.º Presidente de la Junta: Que será elegido anualmente por la Junta de Propietarios y representa a la Agrupación.

3.º Secretario–Administrador: este cargo será ejercido por personal cualificado contratado por la Junta de Propietarios.

[COMPLETAR]

Para la adopción de acuerdos se seguirá el criterio establecido en el artículo 17 de la Ley de Propiedad Horizontal con la especialidad de que la referencia a propietarios deberá entenderse hecha para la Agrupación de Presidentes de Comunidad.

La adopción de acuerdos en los que se requieran mayorías cualificadas requerirá el previo acuerdo o refrendo por la mayoría, que en cada caso se exija, de cada Junta de Propietarios de las que integran la Agrupación.

En todo lo no regulado en estos estatutos será de aplicación lo establecido en el capítulo III de la Ley 49/1960, de 21 de julio, de Propiedad Horizontal

[ELEGIR UNA OPCIÓN Y REDACTARLA: Junta y Tribunales / Mediación civil y Tribunales — el texto de cada opción no venía en el formulario original]

========================================================================
