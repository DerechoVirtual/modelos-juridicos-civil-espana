---
name: revocar-unilateralmente-testamento-mancomunado-544
description: "Redacta el escrito «Revocar unilateralmente el testamento mancomunado correspectivo (Galicia)» (formulario 544 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Revocar unilateralmente el testamento mancomunado correspectivo (Galicia)

> Formulario 0544 del plugin **Sucesiones** · revisado el 17-11-2026.

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

- [ ] NÚMERO (3 veces)
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] FECHA
- [ ] LOCALIDAD
- [ ] DESCRIBIR
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…En»; «… Notario del Ilustre Colegio Notarial de»; «…de»; «…de [COMPLETAR] de»; «…otorgó junto con su cónyuge, Don»; «…testamento mancomunado en»; «…, ante el Notario Don»; «… mancomunado otorgado con su cónyuge Don»; «…ante el Notario Don»; «… para documentos notariales, de la serie»; «…, números»

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

### Formulario 0544 · Revocar unilateralmente el testamento mancomunado correspectivo (Galicia)

- Año del modelo: 2016
- Revisión 17-11-2026: restos de formato retirados; 6 llamadas a nota sin texto retiradas; 18 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

NÚMERO [NÚMERO]

En [COMPLETAR], mi residencia, a [DÍA] de [MES] de [AÑO]

Ante mí, Notario del Ilustre Colegio Notarial de [COMPLETAR]

COMPARECE

Interviene en su propio nombre y derecho y tiene, a mi juicio, la capacidad legal necesaria para formalizar esta escritura de REVOCACIÓN DE TESTAMENTO MANCOMUNADO, a cuyo efecto

EXPONE

Que con fecha [FECHA] de [COMPLETAR] de [COMPLETAR] otorgó junto con su cónyuge, Don [COMPLETAR] testamento mancomunado en [COMPLETAR], ante el Notario Don [COMPLETAR], bajo el número [NÚMERO] de su protocolo.

Que es su voluntad revocar dicho testamento y al efecto,

OTORGA

Revoca el testamento mancomunado otorgado con su cónyuge Don [COMPLETAR] ante el Notario Don [COMPLETAR], bajo el número [NÚMERO] de su protocolo e interesa, asimismo, que se notifique la revocación del mencionado testamento a su cónyuge, en el domicilio sito en [LOCALIDAD].

Acepto el requerimiento que practicaré por diligencia por separado.

Leo por mí íntegramente y en alta voz esta escritura a la compareciente, por su opción, y enterada de su contenido, la encuentra conforme con su voluntad, presta su consentimiento, y la firma conmigo.

Yo, el Notario, doy fe de haber identificado a la compareciente por medio de su reseñado documento de identidad, de haberse observado en este otorgamiento las solemnidades legales y de cuanto se consigna en este original, extendido sobre [DESCRIBIR] folios de papel exclusivo para documentos notariales, de la serie [COMPLETAR], números [COMPLETAR] y los siguientes correlativos.

Debe tenerse presente que la revocación unilateral de una disposición correspectiva producirá la ineficacia de todas las recíprocamente condicionadas, mas la revocación en cuestión, si el revocante la circunscribe únicamente a las disposiciones correspectivas, no tiene por qué afectar a la eficacia de aquellas otras disposiciones que no tengan dicha naturaleza.

La notificación se practicará en el domicilio que figure en el testamento mancomunado que se revoca, sin perjuicio de que pueda realizarse, también, en el domicilio indicado por el revocante.

La notificación será realizada en los treinta días hábiles siguientes por el notario que la autorizó y producirá efectos revocatorios aunque no se encuentre al cónyuge en ninguno de los domicilios señalados.

========================================================================
