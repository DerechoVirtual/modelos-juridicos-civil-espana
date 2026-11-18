---
name: alegaciones-solicitante-frente-posible-falta-competencia-740
description: "Redacta el escrito «Alegaciones del solicitante frente a la posible falta de competencia objetiva del Juez» (formulario 740 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones del solicitante frente a la posible falta de competencia objetiva del Juez

> Formulario 0740 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] FECHA (3 veces)
- [ ] Nº DE EXPEDIENTE
- [ ] LUGAR
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «… la disolución judicial de la Asociación»; «…de la cual soy asociado fundador desde»; «…/»; «…l al órgano de gobierno de la Asociación»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 16.2 de la Ley 15/2015
- art. 16.2 LJV
- art. 17 de la Ley Orgánica 1/2002
- art. 39 del Código Civil
- arts. 126.1 y 128 LJV
- art. 86 bis.1 LOPJ
- art. 127 LJV
- art. 126.3 LJV

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

### Formulario 0740 · Alegaciones del solicitante frente a la posible falta de competencia objetiva del Juez

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; restos de formato retirados; notas del formulario agrupadas al final (1); 12 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de alegaciones en relación al traslado recibido sobre posible falta de competencia objetiva del juez, se resuelva continuar con el expediente dando traslado de la solicitud inicial al órgano de gobierno de la Asociación y se convocando la comparecencia prevista en la ley.

Formulario adaptado a la reforma orgánica y procesal de la LO 1/2025.

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

Que por medio del presente escrito, y al amparo de lo dispuesto en el art. 16.2 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), formulo ALEGACIONES en relación al traslado recibido sobre posible falta de competencia objetiva del juez, en base a las siguientes

ALEGACIONES

PRIMERA.- Que el pasado [FECHA], insté ante el órgano judicial al cual tengo el honor de dirigirme, la disolución judicial de la Asociación [COMPLETAR] de la cual soy asociado fundador desde [COMPLETAR]. Mediante diligencia de ordenación de fecha [FECHA] se incoó el presente expediente con nº [Nº DE EXPEDIENTE] / [COMPLETAR], y se me dio traslado, al igual que al Ministerio Fiscal, para que realizáramos alegaciones en relación a una posible falta de competencia objetiva del juez de lo mercantil que debe resolver el presente expediente, de conformidad con lo dispuesto en el art. 16.2 LJV.

SEGUNDO.- En este sentido, y tal y como se hacía constar en la solicitud inicial, el único procedimiento específico, no contencioso, establecido en nuestra legislación para instar la disolución de personas jurídicas que se encuentran en tal situación legal de disolución, pero que sufren una situación de bloqueo que impide iniciar la misma; es el de disolución judicial de sociedades previsto en los arts. 125 y ss. LJV.

Así, el art. 17 de la Ley Orgánica 1/2002, de 22 de marzo, reguladora del Derecho de Asociación, establece, como causa de disolución las previstas en los estatutos, en la voluntad de los asociados, la sentencia judicial firme que así lo declare, y las causas recogidas en el art. 39 del Código Civil. Asimismo, este último precepto legal contempla le expiración del plazo durante el cual funcionaban legalmente, la realización del fin para el cual se constituyeron, y la imposibilidad de aplicar a tal fin la actividad y los medios de los que disponían. Como ya se hizo constar en la solicitud inicial, en el presente caso concurre esta última causa, al encontrarse la asociación paralizada desde hace tres años, sin que los órganos de gobierno de la misma adopten acuerdo alguno, habida cuenta del profundo desacuerdo existente entre los asociados, divididos en dos bloques al 50%, que imposibilitan la toma de decisión alguna.

TERCERO.- Y, de esta forma, el procedimiento de disolución, a todas luces, necesario y procedente legalmente, ni siquiera se puede poner en marcha por la propia Asociación, sin que los bienes de la misma se puedan aplicar a los fines previstos en los estatutos, tal y como ordena el citado art. 39 del Código Civil. Por ello, procede la puesta en marcha de este expediente de jurisdicción voluntaria para cuya resolución es competente el juez mercantil, en virtud de lo dispuesto en los arts. 126.1 y 128 LJV; con encaje en la competencia específica prevista en el art. 86 bis.1 LOPJ.

Procede, en consecuencia, continuar con los trámites legales, de manera que, a partir de lo prevenido en el art. 127 LJV, el Letrado de la Administración de Justicia dé traslado de la solicitud inicial al órgano de gobierno de la Asociación (al no haber promovido el mismo la disolución interesada), y convoque la comparecencia prevista en tal precepto, para que se resuelva posteriormente al respecto por el Juez de la Sección de lo Mercantil del TI.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito y los documentos que se acompañan, y por deducidas alegaciones en relación a la competencia objetiva del órgano judicial al cual tengo el honor de dirigirme, de conformidad con el art. 16.2 LJV, se resuelva continuar con el expediente, dando traslado de la solicitud inicial al órgano de gobierno de la Asociación [COMPLETAR], y convocando la comparecencia prevista en el art. 127 LJV.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) Exigible en este expediente expresamente, conforme art. 126.3 LJV.

========================================================================
