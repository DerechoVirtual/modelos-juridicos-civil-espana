---
name: laudo-final-arbitraje-institucional-derecho-258
description: "Redacta el escrito «Laudo final en arbitraje institucional de derecho» (formulario 258 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Laudo final en arbitraje institucional de derecho

> Formulario 0258 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] IMPORTE (7 veces)
- [ ] LUGAR (2 veces)
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] Nº (5 veces)
- [ ] PROFESIÓN
- [ ] COLEGIO (3 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] NIF (2 veces)
- [ ] DOMICILIO A EFECTOS DE NOTIFICACIONES
- [ ] ACTO O RESOLUCIÓN (3 veces)
- [ ] FECHA (2 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] ÓRGANO
- [ ] DESCRIBIR
- [ ] ÓRGANO O PERSONA
- [ ] Otros 78 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ARBITRAL Logo de la Institución Arbitral»; «…, mayor de edad, vecino/a de»; «…rofesional a efecto de notificaciones en»; «…, nombrado árbitro por la Institución de»; «…a registrada con el número de expediente»; «…planteada como demandante por el letrado»; «…, con número de colegiado»; «…on número DNI/CIF [NIF], y con domicilio»; «…liado a los efectos de notificaciones en»; «… LAUDO según lo dispuesto en el artículo»; «…del Reglamento de Arbitraje de»; «…, con base en la Cláusula»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 37 de la Ley 60/2003

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

### Formulario 0258 · Laudo final en arbitraje institucional de derecho

- Año del modelo: 2020
- Revisión 17-11-2026: 106 campos de relleno marcados en blanco; 6 huecos del original que se habían perdido sin marca, marcados (IMPORTE, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Véase MEDIACIÓN Y ARBITRAJE: Requisitos formales de un laudo dictado en un arbitraje institucional

LAUDO ARBITRAL

Logo de la Institución Arbitral [COMPLETAR]

Demandante:

Demandado:

Objeto:

Cuantía: [IMPORTE] €

Demanda reconvencional:

Cuantía: [IMPORTE] €

Notificación:

I.En [LUGAR], a [DÍA] de [MES] de [AÑO]., emite el presente Laudo el árbitro D./Dª. [NOMBRE Y APELLIDOS], mayor de edad, vecino/a de [COMPLETAR], provisto de DNI núm. [Nº], con domicilio profesional a efecto de notificaciones en [COMPLETAR], con profesión [PROFESIÓN], ejerciente del Ilustre Colegio de Abogados de [COLEGIO], nombrado árbitro por la Institución de [COMPLETAR], para resolver mediante Arbitraje de Derecho la cuestión litigiosa registrada con el número de expediente [COMPLETAR], planteada como demandante por el letrado [COMPLETAR], ejerciente del Ilustre Colegio de Abogados de [COLEGIO], con número de colegiado [COMPLETAR], que actúa en nombre y representación de [NOMBRE DEL REPRESENTADO/A] con número DNI/CIF [NIF], y domicilio a efectos de notificaciones en [DOMICILIO A EFECTOS DE NOTIFICACIONES], frente a [ACTO O RESOLUCIÓN], con número DNI/CIF [NIF], y con domicilio [COMPLETAR], y su representante legal D./Dª. [NOMBRE Y APELLIDOS], abogado/a ejerciente del Ilustre Colegio de Abogados de [COLEGIO], domiciliado a los efectos de notificaciones en [COMPLETAR].

Después del estudio y adecuada ponderación de las alegaciones de las partes, y de las pruebas practicadas, dicta el presente LAUDO según lo dispuesto en el artículo [COMPLETAR] del Reglamento de Arbitraje de [COMPLETAR], con el artículo 37 de la Ley 60/2003, de 23 de diciembre, de Arbitraje (en adelante Ley de Arbitraje) con base en los siguientes

ANTECEDENTES

Primero

II.Mediante escrito de [FECHA], con base en la Cláusula [COMPLETAR] del [COMPLETAR], de [COMPLETAR], entre [COMPLETAR], presenta en la Institución [COMPLETAR] una SOLICITUD DE ARBITRAJE institucional de Derecho con árbitros, a efectuarse en la ciudad de [COMPLETAR], en idioma [COMPLETAR]; a la que acompaña los documentos en que fundamenta su derecho y en el que suplica que [COMPLETAR] y que se condene a [COMPLETAR] a [COMPLETAR], así como entregar [COMPLETAR] en concepto de [COMPLETAR].

III.La demanda cumple los requisitos procedimentales y documentales del artículo [COMPLETAR] del Reglamento de Arbitraje de [COMPLETAR] y del artículo 29 de la Ley de Arbitraje, en la medida que el Acuerdo [COMPLETAR] dispone expresamente “”.

Segundo

IV. El [COMPLETAR] el Tribunal de [LOCALIDAD] da traslado de la demanda de arbitraje a [COMPLETAR] mediante [ÓRGANO].

Tercero

V.El [COMPLETAR], dentro del plazo reglamentario, por [COMPLETAR], se emite escrito de contestación a la demanda, en el que tras alegar los hechos y fundamentos que estimó de aplicación solicita que [COMPLETAR], y que la demandante le abone las siguientes cantidades: [IMPORTE] €, y [IMPORTE] € en concepto de indemnización por [COMPLETAR].

Cuarto

VI.El Tribunal de [LOCALIDAD] mediante acuerdo fundamentado de [LOCALIDAD], aceptó el encargo arbitral y, de conformidad con su reglamento, procedió a designar al Árbitro que suscribe.

Quinto

VII.Registrado el escrito de contestación a la demanda el [COMPLETAR], con esta fecha se dicta la resolución por la que se requiere a [COMPLETAR] para que en el plazo de [Nº] días manifieste expresamente si su escrito de contestación contiene una reconvención o no (en su caso, incluir este apartado).

VIII.El [COMPLETAR] se reitera íntegramente en su escrito de contestación y formula demanda reconvencional frente a [ACTO O RESOLUCIÓN] para que [COMPLETAR], y que abone las siguientes cantidades: [COMPLETAR], y en concepto de indemnización por el perjuicio económico y el lucro cesante por los daños ocasionados por el incumplimiento del convenio [COMPLETAR].

Sexto

IX.Recibida la demanda reconvencional, según lo dispuesto en los artículos [COMPLETAR] del Reglamento de Arbitraje, en relación con los artículos 4, 5 y 14 de la Ley de Arbitraje, el [COMPLETAR] se dio traslado de los escritos de contestación a la demanda y demanda reconvencional (en su caso, escoger lo que corresponda) a [COMPLETAR] y realizado el emplazamiento de la demandante-demandada reconvenida, presentó contestación a la reconvención el [COMPLETAR], en el que después de exponer los hechos requiere que [COMPLETAR] y solicita la apertura del período de prueba.

Séptimo

X.Por resolución de se declara la conclusión de la fase de alegaciones e inicio del período de prueba, para que en el plazo común de [Nº] días, las partes propongan los medios de prueba que a su derecho corresponda.

XI. Tras la presentación de los escritos de proposición de prueba por las partes, por resolución de se acuerda dar traslado a las partes de los medios de proposición de prueba admitidos para la práctica de [COMPLETAR], el [COMPLETAR], a las [Nº] horas, en [COMPLETAR], autorizando a participar en dicha Audiencia a [COMPLETAR].

Octavo

XII.El resultado de la Audiencia obra en el expediente y cuyo contenido quedó reflejado en el acta de comparecencia y en [COMPLETAR] celebrada el [COMPLETAR]), y cuyas copias fueros remitidas a las partes en cumplimiento de la resolución de igual fecha, a fin de que en el plazo de [Nº] días, según lo dispuesto en el artículo [COMPLETAR] del Reglamento de Arbitraje en relación con el artículo 30 de la Ley del Arbitraje, las partes examinen, valoren las pruebas practicadas y presenten sus escritos de conclusiones.

Noveno

XIII.En cumplimiento del trámite conferido se presentan los escritos de conclusiones los días [COMPLETAR], respectivamente, por [COMPLETAR] y que quedan unidos al expediente, en los que cada una hace constar las que estima conveniente a su derecho.

Décimo

XIV.Finalizado el plazo de conclusiones queda pendiente dictar el Laudo Arbitral en Derecho, que se emite en fecha de hoy con base a los siguientes

FUNDAMENTOS JURÍDICOS

Primero. Principal objeto de la controversia.

[COMPLETAR]

XV.El litigio que ha de dirimirse en este laudo tiene por objeto principal [COMPLETAR], y aportado por la demandante como Documento número 1. Una vez establecido si el comportamiento de las partes se desvió de lo prometido en aquel, habrá de concretarse, en su caso, la pertinencia de su resolución o condena al cumplimiento, así las consecuencias económicas exigidas por cada una de las ellas en sus escritos de demanda y reconvención.

XVI.El contenido contractual del Convenio [COMPLETAR] se desarrolla en [COMPLETAR], bajo las rúbricas [COMPLETAR].

XVII.El objeto del contrato (Acuerdo primero) constituye la “”.

XVIII.El contenido obligacional del contrato, que en parte se contiene en el tenor literal del transcrito Acuerdo Primero, se desarrolla en los Acuerdos [COMPLETAR]. A la vista del tenor de ambos, las rúbricas [COMPLETAR].

Segundo Las pretensiones de las partes.

XIX.Ambas partes, en sus escritos de demanda y reconvención se acusan mutuamente de incumplimiento grave de las obligaciones que les corresponden, en los términos que han sido transcritos en los antecedentes y que, resumidos, se señalan a continuación.

XX.La demanda de [COMPLETAR] solicita que se declare:

[COMPLETAR]

XXI.En su escrito de conclusiones, la demandante y reconvenida (escoger dependiendo de las circunstancias), además de reiterar su petición inicial, cuantifica las cantidades debidas en [IMPORTE] euros.

XXII.La demandada formula reconvención (o no, dependiendo del caso) en la que se solicita se declare:

[COMPLETAR]

XXIII.En su escrito de conclusiones, la demandada y reconviniente, además de reiterar su petición inicial, cuantifica las cantidades debidas en [IMPORTE] euros.

XXIV.Por toda fundamentación jurídica, ambas partes invocan los artículos [COMPLETAR], relativos a [DESCRIBIR], aun sin realizar consideración jurídica alguna sobre su concreta aplicación a los hechos alegados. Citan también los artículos [COMPLETAR], de cuyo contenido se limitan a dar noticia [COMPLETAR].

Tercero. Relación cronológica de hechos probados.

XXV..

Cuarto. Derecho alegado por partes en sus escritos.

XXVI.Las dos partes en litigio invocan como fundamento de sus respectivas pretensiones la aplicación de los artículos [COMPLETAR].

Quinto. Estimaciones oportunas de la demanda.

Sexto. Estimaciones parciales de la demanda.

Séptimo. Causa del conflicto.

[COMPLETAR]

Octavo. Pretensiones de las partes.

[COMPLETAR]

Noveno. Costas del arbitraje.

XXVII.Conforme a lo establecido en el art. del Reglamento de la Institución de Arbitraje, “” las costas del arbitraje deberán ser abonadas de la siguiente forma:

a)Honorarios y gastos de los árbitros.

b)Honorarios de abogados.

c)El coste del servicio prestado por la institución administradora del arbitraje.

d)Dictámenes periciales.

e).

Criterio seguido, análisis y motivación: [COMPLETAR].

PARTE DISPOSITIVA

XXVIII.Estimando [COMPLETAR] la demanda presentada por [ÓRGANO O PERSONA] contra [ACTO O RESOLUCIÓN]:

1.Se declara [COMPLETAR].

2.Se declara que [COMPLETAR] debe abonar a la [COMPLETAR] la cantidad de [IMPORTE] euros en favor de [COMPLETAR]

3.Se declara no haber lugar a [COMPLETAR]

XXIX.Queda [COMPLETAR] la reconvención.

XXX.Se imponen las costas del arbitraje relativas a la reconvención a [COMPLETAR] y sin pronunciamiento en las correspondientes a [COMPLETAR].

En [LUGAR], a [FECHA].

Lo acuerda, manda y firma

()
