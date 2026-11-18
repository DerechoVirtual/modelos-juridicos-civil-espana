---
name: alegaciones-conformidad-causa-inadmision-recurso-1073
description: "Redacta el escrito «Alegaciones de conformidad con la causa de inadmisión del recurso» (formulario 1073 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones de conformidad con la causa de inadmisión del recurso

> Formulario 1073 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] NÚMERO (2 veces)
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] FECHA (3 veces)
- [ ] DESCRIBIR (2 veces)
- [ ] IMPORTE (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Sección»; «… inadmisión apreciada por la Sala porque»; «…n permite el art. 483.2 de la LEC porque»; «… debería haberse admitido por carecer de»; «…a se limita el objeto del recurso porque»; «… LEC. — No existe interés casacional por»; «…es unánime en el sentido de entender que»; «…en la que se declara que»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 483.2 de la LEC
- art. 477 de la LEC
- art. 398 de la LEC

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

### Formulario 1073 · Alegaciones de conformidad con la causa de inadmisión del recurso

- Año del modelo: 2013
- Revisión 17-11-2026: 21 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Recurso n.º [NÚMERO]

Sección [COMPLETAR]

A LA SALA PRIMERA DEL TRIBUNAL SUPREMO

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según tengo debidamente acreditado en el recurso n.º [NÚMERO], ante la Sala comparezco y como mejor proceda en derecho DIGO:

Que se ha notificado a esta parte con fecha [FECHA] providencia de fecha [FECHA] mediante la que se pone de manifiesto a las partes una posible causa de inadmisión del recurso consistente en [DESCRIBIR], y por la que se abre plazo para manifestar lo que a nuestro derecho convenga, trámite que procedemos a evacuar mostrando desde este momento la conformidad con la inadmisión del recurso en atención a las siguientes

ALEGACIONES

Esta parte entiende que en efecto concurre en el presente caso la causa de inadmisión apreciada por la Sala porque [COMPLETAR]

(Opciones):

— Se considera improcedente el recurso y por tanto acertada la inadmisión a trámite, según permite el art. 483.2 de la LEC porque [COMPLETAR]

— Se ha incurrido por la parte recurrente al momento de interponer el recurso en defecto de forma consistente en [DESCRIBIR] que en estos momentos ya no se puede subsanar. El art. 483.2.1.º de la LEC determina que en estos casos procede la inadmisión del recurso.

— La sentencia no es recurrible por no poderse incluir en ninguno de los supuestos recogidos en el art. 477 de la LEC y por tanto debe declararse la inadmisión del recurso en aplicación del art. 483.2.1.º de la LEC.

— De hecho el escrito de interposición no debería haberse admitido por carecer de [COMPLETAR] en aplicación del art. 483.2.2.º de la LEC.

— La cuantía del presente recurso no es la de [IMPORTE] euros como se afirma de contrario sino la de [IMPORTE] euros, ya que a esta última cifra se limita el objeto del recurso porque [COMPLETAR] Así las cosas deberá declararse la inadmisión en aplicación del art. 483.2.3.º de la LEC.

— No existe interés casacional por [COMPLETAR] Debe declararse la inadmisión del recurso conforme al art. 483.2.3º de la LEC.

— (En caso de recurso presentado ante el TSJ): La doctrina de este Tribunal sobre la norma discutida es unánime en el sentido de entender que [COMPLETAR] Por todas citaremos la sentencia del TSJ, sala de lo civil, de fecha [FECHA] en la que se declara que [COMPLETAR] Según lo establecido en el art. 483.2 final de la LEC debe declararse la inadmisión del recurso.

En aplicación del art. 398 de la LEC las costas devengadas deberán ser impuestas a la parte recurrente.

Por lo expuesto,

SUPLICO A LA SALA: Que tenga por presentado este escrito con sus copias, lo admita y, previos los trámites oportunos, acuerde mantener la inadmisión del recurso de casación interpuesto por la representa- ción procesal de D./Dña. [NOMBRE Y APELLIDOS], todo ello con expresa imposición de costas a la parte recurrente.

Por ser justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
