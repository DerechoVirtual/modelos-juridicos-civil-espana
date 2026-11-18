---
name: interponer-recurso-casacion-878
description: "Redacta el escrito «Interponer el recurso de casación» (formulario 878 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Interponer el recurso de casación

> Formulario 0878 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- Estructura de acceso a casación anterior al RDL 5/2023 (derecho fundamental / cuantía > 600.000 € / interés casacional): adaptar al art. 477 vigente (477.1 resoluciones; 477.2-4 interés casacional; 477.2 segundo inciso, derechos fundamentales) y al art. 481.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LOCALIDAD (2 veces)
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] NÚMERO (6 veces)
- [ ] FECHA (5 veces)
- [ ] Nº
- [ ] SEDE (2 veces)
- [ ] ÓRGANO O PERSONA
- [ ] DESCRIBIR (3 veces)
- [ ] LUGAR (2 veces)
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 20 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…a procesal de la LO 1/2025. A LA SECCIÓN»; «…, deriva del juicio»; «…con n.º [Nº] de autos»; «…numeración del juzgado de procedencia).]»; «…claraba que La sentencia ahora recurrida»; «…y declara que»; «…de la sentencia impugnada como documento»; «…a judicial civil del derecho fundamental»; «…omunidad y estar previsto en el artículo»; «…del Estatuto de Autonomía de»; «…ión por aplicación indebida del artículo»; «…de»; …

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS
- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS

## Párrafos opcionales (7)

Inclúyelos solo si encajan en los hechos:

- 1.º Estimar las pretensiones de esta parte declarando haber lugar a [COMPLETAR]…
- 2.º Declarando la vulneración del derecho constitucional de [COMPLETAR] y, en consecuencia, [COMPLETAR]…
- 3.º Declarar haber lugar a nuestra pretensión y, en consecuencia [COMPLETAR], declarando doctrina jurisprudenc…
- E imponer las costas de las anteriores instancias a la otra parte.…
- OTROSÍ DIGO: Que apareciendo así como conveniente para mejor impartir la justicia impetrada, intereso la celeb…
- OTROSÍ DIGO: Que según permite el artículo 482.2 de la LEC la Sala deberá requerir al Letrado de la Administra…
- NUEVAMENTE SUPLICO A LA SALA PRIMERA DEL TRIBUNAL SUPREMO: Tenga por solicitada la celebración de vista, acuer…

## Correcciones de la revisión (5)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 479 de la LEC
- art. 481.2 de la LEC
- artículo 477.1 de la LEC
- artículo 477 de la LEC
- art. 479.1 de la LEC
- art. 478 de la LEC
- art. 56.1 de la LOPJ
- art. 73.1.a) de la LOPJ
- art. 448.1 de la LEC
- artículo 24 de la Constitución
- artículo 481 de la LEC
- artículo 477.3 de la LEC
- art. 398 de la LEC
- artículo 482.2 de la LEC

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

### Formulario 0878 · Interponer el recurso de casación

- Año del modelo: 2013
- Revisión 17-11-2026: 5 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 2 bloques de alternativas señalados; 7 párrafos opcionales señalados; 42 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, SEDE)
- Avisos de la revisión: Estructura de acceso a casación anterior al RDL 5/2023 (derecho fundamental / cuantía > 600.000 € / interés casacional): adaptar al art. 477 vigente (477.1 resoluciones; 477.2-4 interés casacional; 477.2 segundo inciso, derechos fundamentales) y al art. 481.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN [COMPLETAR] DE LA AUDIENCIA PROVINCIAL DE [LOCALIDAD] PARA ANTE LA SALA PRIMERA DEL TRIBUNAL SUPREMO

[NOTA DE REVISIÓN: Errata. La Audiencia Provincial no cambia de denominación. Fuente: LOPJ arts. 80 y 82 (Audiencia Provincial, sin cambio de denominación).]

[NOTA DE REVISIÓN: Errata. Fuente: LOPJ arts. 80 y 82 (Audiencia Provincial, sin cambio de denominación).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según tengo debidamente acreditado en los autos del rollo de apelación n.º [NÚMERO], ante la Sala comparezco y como mejor proceda en Derecho DIGO:

Que mediante el presente escrito, y según permite el artículo 479 de la LEC, interpongo el recurso de casación contra la sentencia n.º [NÚMERO] de fecha [FECHA], dictada en el presente procedimiento, señalando con carácter previo al desarrollo de los motivos en que se fundan, los siguientes

Antecedentes

I. El recurso de casación se interpone contra la sentencia n.º [NÚMERO] de fecha [FECHA], recaída en los presentes autos dentro del plazo legal de veinte días hábiles siguientes a la notificación de la resolución impugnada previsto en el artículo 479 de la LEC.

La sentencia dictada en rollo de apelación n.º [NÚMERO], deriva del juicio [COMPLETAR] con n.º [Nº] de autos [COMPLETAR], seguido ante la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], en el que se dictó la sentencia n.º [NÚMERO] de fecha [FECHA], en cuyo fallo se declaraba que

La sentencia ahora recurrida [COMPLETAR] (estima o desestima) el recurso de apelación interpuesto por [ÓRGANO O PERSONA] y declara que [COMPLETAR] Acompañamos certificación de la sentencia impugnada como documento [COMPLETAR] tal como requiere el art. 481.2 de la LEC.

II. La resolución impugnada es susceptible de recurso de casación por tratarse de sentencia dictada por una Audiencia Provincial mediante la que se pone fin a la segunda instancia –artículo 477.1 de la LEC– [NOTA DE REVISIÓN: Las resoluciones recurribles están hoy en el art. 477.1 LEC. Fuente: LEC arts. 477.1-3 (redacc. RDL 5/2023, BOE-A-2023-15135; apdo. 1 también RDL 6/2023).] y adecuarse al caso previsto legalmente:

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

a) se ha dictado en un proceso para la tutela judicial civil del derecho fundamental [COMPLETAR] (detallar; p.ej.: tutela del derecho al honor, a la intimidad y a la propia imagen, ...).

b) La cuantía del asunto excede de seiscientos mil euros (artículo 477, inciso 2.2.º de la LEC).

c) La resolución del recurso presenta interés casacional, según desarrollaremos, permitiendo el apartado 3 del artículo 477 de la LEC en este caso interponer este recurso aunque la cuantía del pleito no alcance los seiscientos mil euros o éste se haya tramitado en atención a la materia. Desde este momento indicamos que, según requiere el art. 481.2 de la LEC presentamos el texto de las sentencias que fundamentan el interés casacional.

III. Este recurso se presenta ante la Audiencia que dictó la resolución recurrida, art. 479.1 de la LEC, siendo competente para resolver según el art. 478 de la LEC (opciones):

– La Sala de lo Civil del Tribunal Supremo por aplicación del art. 56.1 de la LOPJ.
– La Sala de lo Civil del Tribunal Superior de Justicia de Castilla y León por aplicación del art. 73.1.a) de la LOPJ, fundarse el recurso en infracción de normas de derecho civil, foral o especial, propio de la Comunidad y estar previsto en el artículo [COMPLETAR] del Estatuto de Autonomía de [COMPLETAR] esta atribución.

IV. Mi representado está legitimado para interponer el recurso por ser parte en el proceso y permitirlo el art. 448.1 de la LEC.

V. El motivo concreto de la casación que debe indicarse según exige el art 477 de la LEC es (opciones):

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

1. (Cuando se pretenda impugnar sentencia dictada para la tutela judicial civil de derechos fundamentales –excepto los reconocidos en el artículo 24 de la Constitución– se expondrá la vulneración de derecho fundamental que se considera cometida).

2. (Cuando se pretenda recurrir sentencia en asunto cuya cuantía exceda de 600.000 euros se indicará la INFRACCIÓN LEGAL que se considera cometida). [NOTA DE REVISIÓN: Suprimir: el acceso a casación por cuantía superior a 600.000 € no existe desde el RDL 5/2023; solo interés casacional (art. 477.2-4) o tutela de derechos fundamentales (art. 477.2, segundo inciso). Fuente: LEC arts. 477.1-3 (redacc. RDL 5/2023, BOE-A-2023-15135; apdo. 1 también RDL 6/2023).]

3. (Cuando se pretenda recurrir sentencia basándose en interés casacional se indicarán, además de la infracción legal que se considera cometida, las sentencias, al menos dos, que pongan de manifiesto la doctrina jurisprudencial o jurisprudencia contradictoria, al menos dos en cada sentido contradictorio, en que se funde el interés casacional alegado)].

VI. Según acredito, esta parte ha procedido por esta parte a consignar el depósito para recurrir y, (para personas jurídicas), liquidar la tasa por el ejercicio de la potestad jurisdiccional, según el modelo 696.

Sentados estos antecedentes pasamos al desarrollo de los motivos del recurso

Motivos del recurso

De conformidad con lo dispuesto en el artículo 481 de la LEC, desarrollo, para impugnar la resolución recurrida, los siguientes MOTIVOS:

Motivo primero.–

Se denuncia la infracción por aplicación indebida del artículo [COMPLETAR] de [COMPLETAR] (norma que se considera infringida) en relación con [DESCRIBIR]

La sentencia recurrida declara probados los siguientes hechos [COMPLETAR]

La cuestión central del debate litigioso se resuelve mediante la aplicación de [COMPLETAR] (citar preceptos que sirven de base a la sentencia recurrida). Sin embargo, el art. de (norma que se considera infringida) en relación con [DESCRIBIR] establece

(Exponer, con la «necesaria extensión» que exige el artículo 481 de la LEC, los fundamentos del motivo:

– detallando los antecedentes que se refieren a la infracción legal que se considera cometida,
– justificando de qué manera dicha infracción ha influido en el resultado del proceso,
– invocando los fundamentos de derecho aplicables, vigencia de la norma e inexistencia de doctrina jurisprudencia sobre la norma que se considere infringida.
– proponiendo el resultado a que debía haber conducido la correcta interpretación y aplicación de la norma.

Motivo segundo.–

En el caso de interés casacional se desarrollará, sobre el texto de las sentencias aportadas, el contenido de la contradicción jurisprudencial, y en el supuesto previsto en el artículo 477.3 de la LEC se desarrollará expresa y razonadamente cuanto haga referencia a la contradicción entre las sentencias cuyo texto se acompaña.

/

COSTAS: Será de aplicación el art. 398 de la LEC, debiéndose condenar a la otra parte a las costas de las instancias anteriores.

Por lo expuesto,

SUPLICO A LA SECCIÓN [COMPLETAR] DE LA AUDIENCIA PROVINCIAL DE [LOCALIDAD]: que tenga por presentado este escrito con la certificación de la sentencia impugnada y demás documentos que se aportan, así como copia de todo ello, se sirva admitirlo y, en su virtud tenga por interpuesto en tiempo y forma RECURSO DE CASACIÓN contra la sentencia de esta Audiencia n.º [NÚMERO] de fecha [FECHA], acordando remitir todos los autos originales a la Sala Primera del Tribunal Supremo como tribunal competente para resolver este recurso, y

SUPLICO A LA SALA PRIMERA DEL TRIBUNAL SUPREMO: que admitiendo a trámite el recurso de casación interpuesto contra la sentencia de que se ha hecho mérito, y previa la tramitación oportuna se dicte sentencia mediante la que, estimando íntegramente este recurso, case la sentencia recurrida y, en consecuencia, acuerde:

[OPCIONAL — incluir si procede]

1.º Estimar las pretensiones de esta parte declarando haber lugar a [COMPLETAR]

[OPCIONAL — incluir si procede]

2.º Declarando la vulneración del derecho constitucional de [COMPLETAR] y, en consecuencia, [COMPLETAR]

[OPCIONAL — incluir si procede]

3.º Declarar haber lugar a nuestra pretensión y, en consecuencia [COMPLETAR], declarando doctrina jurisprudencial sobre [DESCRIBIR] en el sentido de [COMPLETAR]

[OPCIONAL — incluir si procede]

E imponer las costas de las anteriores instancias a la otra parte.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

[OPCIONAL — incluir si procede]

OTROSÍ DIGO: Que apareciendo así como conveniente para mejor impartir la justicia impetrada, intereso la celebración de vista.

[OPCIONAL — incluir si procede]

OTROSÍ DIGO: Que según permite el artículo 482.2 de la LEC la Sala deberá requerir al Letrado de la Administración de Justicia de la Audiencia Provincial de [SEDE] para que remita la certificación de la sentencia recurrida pues, tal como acreditamos, fue solicitada en su momento sin que se nos entregara.

[OPCIONAL — incluir si procede]

NUEVAMENTE SUPLICO A LA SALA PRIMERA DEL TRIBUNAL SUPREMO: Tenga por solicitada la celebración de vista, acuerde su celebración y disponga lo necesario para su efectividad.

Por ser justicia que reitero en [LUGAR], a [FECHA].

Abogado/a	Procurador/a

Fdo. D./Dña. [NOMBRE Y APELLIDOS]: 	Fdo. D./Dña. [NOMBRE Y APELLIDOS]:

========================================================================
