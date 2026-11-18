---
name: comunicacion-propietario-discrepante-acuerdo-junta-305
description: "Redacta el escrito «Comunicación del propietario discrepante de un acuerdo de la junta» (formulario 305 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Comunicación del propietario discrepante de un acuerdo de la junta

> Formulario 0305 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS
- [ ] NÚMERO
- [ ] DOMICILIO A EFECTOS DE NOTIFICACIONES
- [ ] FECHA (2 veces)
- [ ] Nº
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…CRETARIO DE LA COMUNIDAD DE PROPIETARIOS»; «…a de la vivienda/local identificada como»; «…inaria/Extraordinaria, que tuvo lugar en»; «…a las [Nº] horas, en relación a»; «… y representados/aprobado por mayoría de»; «…on el mismo, por los siguientes motivos:»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 17.8 LPH

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

### Formulario 0305 · Comunicación del propietario discrepante de un acuerdo de la junta

- Año del modelo: 2020
- Revisión 17-11-2026: 13 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de propietario al Secretario de la comunidad oponiéndose a acuerdo.

AL SR. SECRETARIO DE LA COMUNIDAD DE PROPIETARIOS [COMPLETAR]

D./Dª. [NOMBRE Y APELLIDOS], con D.N.I. nº [NÚMERO], con domicilio a efectos de notificaciones en [DOMICILIO A EFECTOS DE NOTIFICACIONES], ante el Sr. Secretario de esta Comunidad comparezco y DIGO:

Que, soy propietario/a de la vivienda/local identificada como [COMPLETAR] en la Comunidad anteriormente mencionada.

Que, en fecha [FECHA] me ha sido notificado Acta en el que se recoge el acuerdo adoptado por la Junta General Ordinaria/Extraordinaria, que tuvo lugar en [COMPLETAR], el día [FECHA] a las [Nº] horas, en relación a [COMPLETAR]; por unanimidad de los presentes y representados/aprobado por mayoría de [COMPLETAR], en la que no participé por estar ausente.

Que, tal y como dispone el art. 17.8 LPH, los acuerdos de la Junta de propietarios se sujetarán, entre otras, a la siguiente regla: «Salvo en los supuestos expresamente previstos en los que no se pueda repercutir el coste de los servicios a aquellos propietarios que no hubieren votado expresamente en la Junta a favor del acuerdo, o en los casos en los que la modificación o reforma se haga para aprovechamiento privativo, se computarán como votos favorables los de aquellos propietarios ausentes de la Junta, debidamente citados, quienes una vez informados del acuerdo adoptado por los presentes, conforme al procedimiento establecido en el artículo 9,no manifiesten su discrepancia mediante comunicación a quien ejerza las funciones de secretario de la comunidad en el plazo de 30 días naturales, por cualquier medio que permita tener constancia de la recepción».

En base a lo anteriormente expuesto, y en virtud del derecho que me confiere el citado artículo 17.8 de la Ley de Propiedad Horizontal, y no estando conforme con el referido acuerdo; vengo a manifestarle en plazo legal mi discrepancia con el mismo, por los siguientes motivos: [COMPLETAR].

Por todo ello, SOLICITO que se tenga por presentado el presente escrito, se sirva admitirlo y se tenga por realizada mi oposición, reservándome el derecho a impugnar judicialmente dicho acuerdo.

Atentamente en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del/a propietario/a
