---
name: casacion-e-infraccion-procesal-conjuntas-simultaneas-1127
description: "Redacta el escrito «Casación e infracción procesal conjuntas y simultáneas, previo al RDL 5/2023 (general)» (formulario 1127 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Casación e infracción procesal conjuntas y simultáneas, previo al RDL 5/2023 (general)

> Formulario 1127 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Interposición conjunta de infracción procesal y casación (DF 16.ª, art. 469 y antiguo 477.2.1.º-3.º LEC): régimen derogado por RDL 5/2023 y RDL 6/2023; rehacer como casación única (arts. 477 y 481 LEC).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NÚMERO (11 veces)
- [ ] LOCALIDAD (9 veces)
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] FECHA (8 veces)
- [ ] SEDE (5 veces)
- [ ] IMPORTE (3 veces)
- [ ] DESCRIBIR (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 58 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, SECCIÓN»; «…, proveniente del juicio»; «…stiman sus pretensiones, se le condena a»; «…curso, según acredito documentalmente, a»; «…o. SÉPTIMO.— Acompañamos como documentos»; «…sal. Esta parte entiende que ha existido»; «…tencia objetiva o funcional, en concreto»; «…reguladoras de la sentencia, en concreto»; «…cias oportunas. Constan en autos, folios»; «…en que se ha denunciado la infracción de»; «…y se solicitó la subsanación de»; «…n este caso se recurre una sentencia que»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 470 y 479 de la LEC
- artículos 470.1 y 479.1 de la LEC
- artículos 469 y 477 de la LEC
- artículo 448 LEC
- artículo 449 de la LEC
- artículo 469.1 de la LEC
- artículos 469.2 y 470.2 de la LEC
- artículo 24 de la Constitución
- artículo 469 de la LEC
- artículo 477 de la LEC
- art. 469.1 de la LEC
- art. 469.2 y 470.2 de la LEC
- art. 477.2 de la LEC
- art. 471 de la LEC
- art. 398 de la LEC
- arts. 471 y 481 de la LEC

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

### Formulario 1127 · Casación e infracción procesal conjuntas y simultáneas, previo al RDL 5/2023 (general)

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 100 campos de relleno marcados en blanco
- Avisos de la revisión: Interposición conjunta de infracción procesal y casación (DF 16.ª, art. 469 y antiguo 477.2.1.º-3.º LEC): régimen derogado por RDL 5/2023 y RDL 6/2023; rehacer como casación única (arts. 477 y 481 LEC).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Rollo de apelación n.º [NÚMERO].

A LA AUDIENCIA PROVINCIAL DE [LOCALIDAD], SECCIÓN [COMPLETAR].

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según tengo debidamente acreditado en el procedimiento referenciado, ante la Sala comparezco y como mejor proceda en derecho DIGO:

Que mediante el presente escrito según permiten la DF decimosexta de la LEC en relación con los arts. 470 y 479 de la LEC INTERPONEMOS de forma conjunta RECURSO EXTRAORDINARIO POR INFRACCIÓN PROCESAL y RECURSO DE CASACIÓN contra la sentencia n.º [NÚMERO] de fecha [FECHA] dictada en el presente recurso, en atención a los siguientes

PRESUPUESTOS Y REQUISITOS

A) GENERALES:

PRIMERO.— Se interpone este recurso contra la sentencia n.º [NÚMERO] de fecha [FECHA] dictada en el rollo de apelación n.º [NÚMERO], proveniente del juicio [COMPLETAR] n.º [NÚMERO] del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]ntro del plazo legalmente establecido de veinte días en los artículos 470.1 y 479.1 de la LEC.

Acompañamos certificación de la sentencia según exige el art. 481.2 para el recurso de casación.

SEGUNDO.— Ambos recursos se preparan en un mismo escrito tal como exige la disposición final decimosexta, 1.3.ª de la LEC, presentándose ante el Tribunal que dictó la sentencia que se pretende recurrir.

TERCERO.— La resolución es susceptible de ser recurrida por infracción procesal y en casación en atención a los artículos 469 y 477 de la LEC, ya que nos encontramos ante una sentencia dictada por la Audiencia Provincial que pone fin a la segunda instancia.

CUARTO.— Mi representado está legitimado para recurrir por haber sido parte en el proceso y por afectarle desfavorablemente la resolución impugnada (artículo 448 LEC), puesto que en el fallo de la sentencia (se desestiman sus pretensiones, se le condena a [COMPLETAR]).

QUINTO.— Será competente para conocer de estos recursos, según indican la disposición final decimosexta 1.1.ª de la LEC la Sala I del Tribunal Supremo.

SEXTO.— (En su caso) A los efectos previstos en el apartado 1 del artículo 449 de la LEC, manifiesto y acredito documentalmente n.º [NÚMERO] que mi poderdante ha procedido con anterioridad a la presentación de este recurso, según acredito documentalmente, a [COMPLETAR] (opciones):

a) pagar o consignar a favor del arrendador D./Dña. [NOMBRE Y APELLIDOS] las cantidades que en concepto de rentas vencidas y (en su caso) adelantadas debía pagar con arreglo al contrato de arrendamiento suscrito entre las partes objeto de esta pugna, por importe de [IMPORTE] €.

b) consignar o depositar en la cuenta del tribunal (o avalar) la cantidad total por principal e intereses, que asciende a [IMPORTE] €, a cuyo pago ha sido condenado en la sentencia de indemnización por daños y perjuicios causados en accidente de circulación contra la que se prepara este recurso.

c)pagar o consignar a favor de la Comunidad de Propietarios demandante la cantidad de [IMPORTE] € a cuyo pago ha sido condenado en la sentencia contra la que se prepara este recurso.

SÉPTIMO.— Acompañamos como documentos [COMPLETAR] resguardo de ingreso de los depósitos para recurrir según exige la DA 15.ª de la LOPJ (para personas jurídicas) así como justificante de liquidación de la tasa por el ejercicio de la potestad jurisdiccional, mediante el modelo 696.

B) DEL RECURSO POR INFRACCIÓN PROCESAL

PRIMERO.— El artículo 469.1 de la LEC tasa los motivos del recurso por infracción procesal. Esta parte entiende que ha existido [COMPLETAR]:

(Opciones):

1.º—Infracción de las normas sobre jurisdicción y/o competencia objetiva o funcional, en concreto [COMPLETAR].

2.º—Infracción de las normas procesales reguladoras de la sentencia, en concreto [COMPLETAR].

3.º—Infracción de las normas legales que rigen los actos y garantías del proceso cuando la infracción determinare la nulidad conforme a la ley o haya podido producir indefensión.

SEGUNDO.— Según exigen los artículos 469.2 y 470.2 de la LEC, para que prospere este recurso, la infracción procesal debe haberse denunciado en la instancia y, si la vulneración se produjo en la primera, también en la segunda instancia. Si se vulneró el artículo 24 de la Constitución produciéndose falta o derecho subsanable también debe haberse pedido la subsanación en la instancia o instancias oportunas.

Constan en autos, folios [COMPLETAR], los escritos o momentos en que se ha denunciado la infracción de [COMPLETAR] y se solicitó la subsanación de [COMPLETAR] así como las decisiones que adoptaron el Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO] y la Audiencia Provincial de [LOCALIDAD].

TERCERO.— Hay que tener en cuenta lo indicado en el n.º 1 de la disposición final decimosexta de la LEC según el cual, en tanto no se confiera a los TSJ la competencia para conocer del recurso extraordinario por infracción procesal, este recurso sólo procederá por el motivo indicado, permitido por el artículo 469 de la LEC, pero solo frente a resoluciones que, a su vez, sean susceptibles de recurso de casación según el artículo 477 de la misma norma.

C) DEL RECURSO DE CASACIÓN

PRIMERO.— Los motivos del recurso de casación se recogen en el artículo 477 de la LEC. En este caso se recurre una sentencia que [COMPLETAR] (opciones).

1.º—se ha dictado para la tutela del derecho fundamental de [COMPLETAR]. La vulneración en esencia ha consistido en [COMPLETAR].

2.º—se ha dictado en un proceso cuya cuantía supera los 600.000 € y en la que se han cometido las siguientes infracciones legales [COMPLETAR] relativas a los siguientes preceptos [COMPLETAR].

3.º—se recurre porque la resolución de este recurso presenta interés casacional por [COMPLETAR] (oponerse a la doctrina jurisprudencial del Tribunal Supremo en materia de [LOCALIDAD]; resolver la cuestión de [LOCALIDAD] sobre la que la Audiencia Provincial de [LOCALIDAD] se ha pronunciado en sentido contrario al indicar que [COMPLETAR]; haber aplicado una norma que lleva en vigor menos de cinco años, en concreto la Ley [COMPLETAR] que entró en vigor el día [FECHA] sin que exista doctrina jurisprudencial del Tribunal Supremo sobre normas de anteriores que hubieran podido tener contenido similar; oponerse a la doctrina de nuestro TSJ en materia de derecho autonómico relativo a [DESCRIBIR]; por no haberse pronunciado el TSJ de [COMPLETAR] respecto a la norma autonómica de [COMPLETAR])

ANTECEDENTES

En fecha [FECHA] se presentó demanda en cuyo suplico se interesaba [COMPLETAR]. La parte demandada se opuso a estas pretensiones interesando la desestimación íntegra de la demanda.

En [COMPLETAR] (la audiencia previa, el juicio, [COMPLETAR]) se [COMPLETAR] (procedió a la denuncia de la infracción del art. por producir indefensión, interesó la subsanación del defecto de [COMPLETAR]), según consta en los folios [COMPLETAR]. Frente a esta pretensión por el Tribunal de Instancia de [SEDE] se resolvió lo siguiente [COMPLETAR].

En sentencia de fecha [FECHA] el Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO] acordó [COMPLETAR].

Y respecto a la infracción procesal alegada afirmaba que [COMPLETAR].

Frente a dicha sentencia la parte [COMPLETAR] (demandante, demandada) interpuso recurso de apelación que, sustanciado en forma, se resolvió por la Audiencia Provincial de [LOCALIDAD] mediante sentencia de fecha [FECHA], cuyo fallo establecía que [COMPLETAR].

En esa fase del procedimiento se alegó la siguiente vulneración de [COMPLETAR] (normativa procesal, derecho fundamental, [COMPLETAR]), cuestión que se resolvió por el órgano colegiado de la siguiente manera [COMPLETAR].

MOTIVOS DEL RECURSO POR INFRACCIÓN PROCESAL

Basándonos en la regulación del art. 469.1 de la LEC alegamos:

(Opciones)

1.º—Infracción de las normas sobre jurisdicción y/o competencia objetiva o funcional, en concreto [COMPLETAR].

2.º—Infracción de las normas procesales reguladoras de la sentencia, en concreto [COMPLETAR].

3.º—Infracción de las normas legales que rigen los actos y garantías del proceso cuando la infracción determinare la nulidad conforme a la ley o haya podido producir indefensión.

Se hace constar, según exigen los art. 469.2 y 470.2 de la LEC, que la infracción procesal se denunció en su momento.

Consta en autos, folios [COMPLETAR], los escritos o momentos en que se ha denunciado la infracción de [COMPLETAR] y se solicitó la subsanación de [COMPLETAR] así como las decisiones que adoptaron el Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO] y la Audiencia Provincial de [LOCALIDAD].

DEL RECURSO DE CASACIÓN

PRIMERO.—En aplicación del art. 477.2 de la LEC la sentencia es recurrible en casación. Esta resolución [COMPLETAR] (opciones)

1.º—se dictó para la tutela del derecho fundamental de [COMPLETAR]. La vulneración en esencia ha consistido en [COMPLETAR].

2.º—se dictó en un proceso cuya cuantía supera los 600.000€ y en la que se han cometido las siguientes infracciones legales [COMPLETAR]. Relativas a los siguientes preceptos [COMPLETAR].

3.º—se recurre porque la resolución de este recurso presenta interés casacional por [COMPLETAR] (oponerse a la doctrina jurisprudencia del Tribunal Supremo en materia de [LOCALIDAD], resolver la cuestión de [COMPLETAR] sobre la que la Audiencia Provincial de [LOCALIDAD] se ha pronunciado en sentido contrario al indicar que [COMPLETAR]; haber aplicado una norma que lleva en vigor menos de cinco años, en concreto la Ley [COMPLETAR] que entró en vigor el día [FECHA] sin que exista doctrina jurisprudencial del Tribunal Supremo sobre normas anteriores que hubieran podido tener contenido similar; oponerse a la doctrina de nuestro TSJ en materia de derecho autonómico relativo a [DESCRIBIR]; por no haberse pronunciado el TSJ de [COMPLETAR] respecto a la norma autonómica de [COMPLETAR])

FUNDAMENTOS DEL RECURSO POR INFRACCIÓN PROCESAL

(desarrollar en atención a los motivos alegados)

(En su caso) Según permite el art. 471 de la LEC esta parte interesa la práctica de la siguiente prueba cuya finalidad es acreditar [COMPLETAR] (la infracción o vulneración producida)

DEL RECURSO DE CASACIÓN

(desarrollar en atención a los motivos alegados)

Costas

Será de aplicación lo establecido en el art. 398 de la LEC, pero deberán imponerse las costas de las instancias anteriores a la otra parte.

Por lo expuesto,

SUPLICO A LA SALA: Que tenga por presentado este escrito con el documento que acompaño, lo admita y tenga por interpuesto en tiempo y forma recurso extraordinario por infracción procesal y recurso de casación contra la sentencia n.º [NÚMERO] de fecha [FECHA] dictada en el rollo de apelación n.º [NÚMERO], a fin de que en su día y previos los trámites oportunos se acuerde la remisión de los autos a la Sala de lo Civil del Tribunal Supremo para que por ésta se dicte finalmente sentencia por la que:

1.º—Estime el recurso extraordinario por infracción procesal acordando [COMPLETAR] (dictar nueva sentencia resolviendo el contencioso por la que se declare que [COMPLETAR]; o, en consecuencia, anular la sentencia impugnada así como las actuaciones desde el trámite de [COMPLETAR], ordenando reponerlas a ese momento procesal, y declarando expresamente que se ha producido una vulneración del derecho de [COMPLETAR] en esa fase).

2.º—De forma principal o subsidiaria, para el caso de no apreciar el recurso anterior, que se admita el recurso de casación, dejando sin efecto la sentencia recurrida, declarando que [COMPLETAR], e imponiendo las costas de primera y segunda instancia a la parte contraria.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

OTROSÍ DIGO: Que según permiten los arts. 471 y 481 de la LEC intereso la celebración de vista por entender que resulta necesario [COMPLETAR].

NUEVAMENTE SUPLICO: Que se acuerde la celebración de vista en los presentes recursos, por ser justicia que pido en mismo lugar y fecha.

========================================================================
