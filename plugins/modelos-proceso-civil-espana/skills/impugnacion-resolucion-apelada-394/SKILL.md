---
name: impugnacion-resolucion-apelada-394
description: "Redacta el escrito «Impugnación de la resolución apelada» (formulario 394 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Impugnación de la resolución apelada

> Formulario 0394 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (6 veces)
- [ ] LUGAR (2 veces)
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…l de la LO 1/2025. A LA SALA Don D./Doña»; «…ictada por el órgano "a quo" dispone que»; «…rueba practicada en autos, en relación a»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 461 LEC
- art. 455 LEC
- art. 460.2 LEC

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

### Formulario 0394 · Impugnación de la resolución apelada

- Año del modelo: 2019
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 10 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de impugnación al recurso de apelación conforme a lo previsto en el art. 461 LEC.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SALA

Don D./Doña [COMPLETAR], Procurador de los Tribunales, actuando en nombre y representación de [NOMBRE DEL REPRESENTADO/A], según tengo acreditado en los autos ante el Tribunal comparezco y como mejor en derecho proceda DIGO:

Que habiéndoseme notificado con fecha [FECHA], diligencia de Ordenación por la que se da traslado a esta parte del recurso de apelación interpuesto de contrario, dentro del plazo de diez días concedido al efecto, por medio del presente escrito, en tiempo y forma, conforme a lo previsto en el art. 461 LEC, formulo IMPUGNACIÓN AL RECURSO DE APELACIÓN, en base a las siguientes:

ALEGACIONES

PRIMERA

La resolución recurrida es la de fecha [FECHA], que conforme a lo previsto en el art. 455 LEC es susceptible de recurso de apelación.

SEGUNDA

La referida resolución es desfavorable a mi mandante en relación a los siguientes pronunciamientos que se impugnan a través del presente escrito, sobre los cuales formularemos separadamente las correspondientes alegaciones.

TERCERA

En cuanto al primer pronunciamiento que se recurre la resolución dictada por el órgano "a quo" dispone que [COMPLETAR]

El Tribunal de instancia ha incurrido en error en la valoración de la prueba practicada en autos, en relación a [COMPLETAR]

CUARTA.- (1)

Por todo lo expuesto,

SUPLICO A LA SALA

Tenga por presentado este escrito, con sus copias, y por hechas las manifestaciones que contiene, se sirva admitirlo, y en su consecuencia, tener por presentado ESCRITO DE IMPUGNACIÓN AL RECURSO DE APELACIÓN contra la resolución de fecha [FECHA], y en su día se dicte resolución por la que se revoque la resolución de instancia de fecha [FECHA] y se dicte otra por la que se estimen las pretensiones de esta parte conforme a los pedimentos contenidos en el cuerpo de este escrito, con condena en costas a la parte contraria, por ser de justicia que pido en [LUGAR], a [FECHA].

OTROSÍ PRIMERO DIGO. Que esta parte solicita la práctica de prueba en segunda instancia, conforme a lo dispuesto en el art. 460.2 LEC, a cuyo fin se propone la siguiente:

Por ello nuevamente,

SUPLICO A LA SALA

Tenga por hecha la anterior manifestación a los oportunos efectos, se admita la prueba solicitada y se acuerde su práctica, para lo cual se solicita igualmente la celebración de vista ante el tribunal "ad quem", por lo que reitero nuevamente justicia en el lugar y fecha antes indicado.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) Se irán haciendo las alegaciones en párrafos separados y numerados.
