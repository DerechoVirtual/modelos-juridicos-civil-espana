---
name: demanda-contenciosa-modificacion-medidas-931
description: "Redacta el escrito «Demanda contenciosa de modificación de medidas» (formulario 931 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda contenciosa de modificación de medidas

> Formulario 0931 del plugin **Familia** · revisado el 17-11-2026.

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

- Paráfrasis del art. 96 CC anterior: desde la Ley 8/2021 el uso de la vivienda, sin acuerdo, corresponde a los hijos menores y al progenitor custodio hasta la mayoría de edad de todos ellos (con regla especial para hijos con discapacidad).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NÚMERO (10 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] SEDE (5 veces)
- [ ] NOMBRE Y APELLIDOS (17 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] DESCRIBIR (3 veces)
- [ ] FECHA (6 veces)
- [ ] DNI/NIE
- [ ] IMPORTE (7 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 20 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…) acordaba como medidas definitivas a la»; «…s cuya modificación se pretende para que»; «…para sus hijos»; «…y custodia conjunta de los hijos menores»; «…y»; «… siguiente manera: mediante estancias de»; «…cial emitido por el perito con título en»; «…io conyugal. En efecto en estos momentos»; «…trabajo de los que carecía al momento de»; «…rcio—, ...) Adjunto como documentos n.os»; «…o unos ingresos mensuales aproximados de»; «…ica que esta persona tenía al momento de»; …

## Correcciones de la revisión (5)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 36 y 769 de la LEC
- art. 46 de la LEC
- art. 775.1 LEC
- art. 775 de la LEC
- art. 770 de la LEC
- arts. 10 y 775.1 de la LEC
- art. 749.2 de la LEC
- art. 750 de la LEC
- art. 437.1 LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 92.8 del CC
- art. 96 del CC
- art. 100 del CC
- art. 93 del CC
- art. 91 del Código Civil
- art. 394 de la LEC

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

### Formulario 0931 · Demanda contenciosa de modificación de medidas

- Año del modelo: 2013
- Revisión 17-11-2026: 5 citas normativas corregidas tras comprobarlas en el BOE; 74 campos de relleno marcados en blanco
- Avisos de la revisión: Paráfrasis del art. 96 CC anterior: desde la Ley 8/2021 el uso de la vivienda, sin acuerdo, corresponde a los hijos menores y al progenitor custodio hasta la mayoría de edad de todos ellos (con regla especial para hijos con discapacidad).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modificación de medidas

 (Separación o Divorcio) n.º [NÚMERO] de la Sección de Familia, Infancia y Capacidad del Tribunal [NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).] de Instancia de [LOCALIDAD]

A LA SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que mediante el presente escrito formulo demanda en solicitud de MODIFICACIÓN DE MEDIDAS DEFINITIVAS relativas a [DESCRIBIR] (la cuantía de los alimentos de los hijos, la existencia de pensión compensatoria, la guarda y custodia de los hijos menores del matrimonio, la atribución del uso del domicilio conyugal, ...) acordadas en sentencia de [FECHA] (separación o divorcio) n.º [NÚMERO] de fecha [FECHA], dictada en autos n.º [NÚMERO] tramitados ante el Tribunal de Instancia de [SEDE], en el sentido que se especificará en el suplico de esta demanda, frente a D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD] y DNI n.º [DNI/NIE] Basamos esta pretensión en los siguientes:

HECHOS

Se presenta listado de documentos que acompañan a la demanda.

La sentencia n.º [NÚMERO] de fecha [FECHA] dictada por el Tribunal de Instancia de [SEDE] (doc. n.º [NÚMERO]) acordaba como medidas definitivas a la [COMPLETAR] (separación o el divorcio), entre otras, las siguientes:

Estas son las medidas cuya modificación se pretende para que [COMPLETAR] (se acuerde la guarda y custodia de los hijos menores compartida, se deje sin efecto la atribución del uso del domicilio conyugal, se extinga la obligación de abono de pensión compensatoria, se modifique la cuantía de los alimentos que corresponde entregar a D./Dña. [NOMBRE Y APELLIDOS] para sus hijos [COMPLETAR])

Los hechos que a continuación se relatan han producido una modificación de circunstancias que deben determinar también una modificación de la regulación de las relaciones entre las partes recogidas en la sentencia de [FECHA] (separación o divorcio).

En concreto:

(Opciones):

1.º La actual regulación de la guarda y custodia recogida en el Código Civil permite que se fije una custodia compartida de los hijos. Mi representado siempre pretendió que se le atribuyera la guarda de los hijos o, subsidiariamente que esta labor se compartiera por ambos progenitores. La reforma del Código Civil en esta materia permite ahora hacer realidad este deseo. Por supuesto que a esto hay que añadir la existencia de unas circunstancias que consideramos propicias para materializar este cambio. Nos referimos al tipo de trabajo que realiza cada uno de los padres, a la proximidad de las viviendas de ambos, la buena relación que padre y madre mantienen con su hijos,

Por esa razón se considera adecuado que se acuerde la guarda y custodia conjunta de los hijos menores [COMPLETAR] y [COMPLETAR] que se llevará a cabo de la siguiente manera: mediante estancias de [COMPLETAR] (quince días, un mes, medio año, ...) en el domicilio de cada uno de los progenitores.

(En su caso) La duración de las estancias hace necesario establecer además un régimen de comunicación con el progenitor que no esté en ese momento con sus hijos consistente en

Adjunto con el n.º [NÚMERO] informe pericial emitido por el perito con título en [COMPLETAR], D./Dña. [NOMBRE Y APELLIDOS] en el que se asegura que el régimen propuesto no sólo es posible sino recomendable para el bienestar de los menores.

2.º Ha desaparecido el interés más necesitado de protección que determinó la atribución a D./Dña. [NOMBRE Y APELLIDOS] de uso del domicilio conyugal. En efecto en estos momentos [COMPLETAR] (ninguno de los hijos vive ya en ese domicilio, D./Dña. [NOMBRE Y APELLIDOS] tiene ahora unos ingresos por su trabajo de los que carecía al momento de [COMPLETAR] —la separación o el divorcio—, ...)

Adjunto como documentos n.os [COMPLETAR], consistentes en [DESCRIBIR] para acreditar lo expuesto.

Así las cosas deberá declararse extinguido, la atribución del uso del domicilio y ajuar conyugal a favor de D./Dña. [NOMBRE Y APELLIDOS] dejando la vivienda libre.

3.º D./Dña. [NOMBRE Y APELLIDOS] ha accedido al mercado laboral en fecha [FECHA] (doc. n.º [NÚMERO]) percibiendo unos ingresos mensuales aproximados de [COMPLETAR] Por tanto ha cambiando la situación económica que esta persona tenía al momento de [COMPLETAR] (la separación o el divorcio) porque entonces carecía de ingresos propios. Se elimina de esta manera el desequilibrio que determinó la obligación de mi representado/a de abonar una pensión compensatoria mensual de [IMPORTE] euros.

Por tanto interesamos que se deje sin efecto la obligación de D./Dña. [NOMBRE Y APELLIDOS] de abonar a D./Dña. [NOMBRE Y APELLIDOS] una pensión compensatoria de [IMPORTE] euros ( euros actuales tras las sucesivas actualizaciones), que se abonaría por anticipado dentro de los primeros cinco días de cada mes y que sería actualizada todos los años aplicando el IPC elaborado por el INE o índice que lo sustituyera a la cifra en cada momento en vigor.

Dejamos acotados los archivos de la TGSS a efectos probatorios.

4.º Debe procederse a un incremento de la cuantía con la que participa D./Dña. [NOMBRE Y APELLIDOS] en los alimentos de los hijos comunes tanto por la subida de sus ingresos como por el incremento de las necesidades de sus descendientes. En efecto [COMPLETAR] (Docs. n.os [COMPLETAR])

D./Dña. [NOMBRE Y APELLIDOS] contribuirá a los alimentos de los hijos comunes entregando por anticipado dentro de los primeros cinco días de cada mes la cantidad de [IMPORTE] euros por cada hijo, es decir, [IMPORTE] euros en total. Esta cantidad será actualizada todos los años aplicando el IPC elaborado por el INE o índice que lo sustituya a la cifra en cada momento en vigor.

Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

Jurisdicción y competencia

Los arts. 21, 22 y 86.5.a) de la LOPJ y arts. 36 y 769 de la LEC atribuyen a la jurisdicción española y a las Secciones de Familia, Infancia y Capacidad de los Tribunales de Instancia el conocimiento de esta materia. El art. 46 de la LEC dice que en los lugares donde exista sección especializada de familia será éste el competente.

La competencia territorial se fija en atención al último domicilio conyugal, y si residen en distintos partidos judiciales decide el demandante entre el del último domicilio del matrimonio o el de residencia del demandado. El art. 775.1 LEC expresamente hace constar que conocerá de la modificación el mismo Tribunal que adoptó las medidas definitivas, en este caso el Tribunal de Instancia de [SEDE].

Tramitación

El art. 775 de la LEC permite solicitar la modificación de las medidas definitivas acordadas en sentencia de separación o divorcio cuando hayan variado sustancialmente las circunstancias que se tuvieron en cuenta para aprobarlas o acordarlas.

En los casos de reclamación contenciosa el indicado precepto remite a la tramitación recogida en el art. 770 de la LEC, que, a su vez, remite al cauce del juicio verbal con determinadas especialidades como son, por ejemplo, la contestación por escrito a la demanda.

Legitimación

Según los arts. 10 y 775.1 de la LEC están legitimados de forma activa y pasiva los cónyuges y en aplicación del art. 749.2 de la LEC deberá intervenir el Ministerio Fiscal cuando estén afectados por este pleito menores o personas con discapacidad (que incluso [NOTA DE REVISIÓN: El art. 749.2 LEC ya no habla de «incapacitados». Fuente: LEC 1/2000 (BOE-A-2000-323) art. 749.2, redacción Ley 8/2021 (BOE-A-2021-9233): «sea menor, persona con discapacidad o esté en situación de ausencia legal».] está legitimado para demandar).

Postulación

En atención a lo establecido en el art. 750 de la LEC, las partes deberán com- parecer representadas por procurador y asistidas de letrado.

Cumplimiento de los requisitos de procedibilidad.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC en relación con el art. 437.1 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Fondo del asunto

PRIMERO.— El art. 775 de la LEC permite solicitar del Tribunal la modificación de medidas definitivas acordadas o adoptadas en las sentencias de separación o divorcio cuando hayan variado sustancialmente las circunstancias que determinaron su adopción.

SEGUNDO.— (Opciones):

1.º El art. 92.8 del CC permite la declaración por el Tribunal de la guarda y custodia conjunta.

2.º El art. 96 del CC atribuye, en defecto de acuerdo, el uso de la vivienda familiar a los hijos comunes menores y al cónyuge en cuya compañía queden, hasta que todos ellos alcancen la mayoría de edad; no habiendo hijos, puede atribuirse al cónyuge no titular cuyo interés sea el más necesitado de protección, por el tiempo que prudencialmente se fije. [NOTA DE REVISIÓN: Paráfrasis del art. 96 CC anterior a la Ley 8/2021. Fuente: Código Civil (BOE-A-1889-4763) art. 96.1 y 96.2, redacción Ley 8/2021 (BOE-A-2021-9233).] Ya hemos indicado que las circunstancias han cambiado porque

3.º El art. 100 del CC permite la modificación o supresión de la pensión compensatoria por alteracio- nes sustanciales de la fortuna de uno u otro cónyuge. En este caso

4.º El art. 93 del CC regula los alimentos de los hijos.

TERCERO.— El art. 91 del Código Civil permite modificar las medidas acordadas en separación o divorcio cuando se alteren sustancialmente las circunstancias.

Costas

El art. 394 de la LEC dice que se impondrán a aquellos cuya pretensión se desestimara.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y copia de todo ello, lo admita y acuerde en su día, previos los trámites legales oportunos, modificar las medidas n.º [NÚMERO] recogidas en el fallo de la sentencia n.º [NÚMERO] de fecha [FECHA] dictada por el Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] en juicio de [COMPLETAR] n.º [NÚMERO], relativas a [DESCRIBIR] para ser sustituidas por las que a continuación se indican, todo ello con expresa imposición de costas a la parte demandada:

(Opciones):

1.º La guarda y custodia conjunta de los hijos menores [COMPLETAR] y [COMPLETAR] se llevará a cabo de la siguiente manera: mediante estancias de [COMPLETAR] (quince días, un mes, medio año, ...) en el domicilio de cada uno de los progenitores.

(En su caso) La duración de las estancias hace necesario establecer además un régimen de comunicación con el progenitor que no esté en ese momento con sus hijos consistente en

2.º Declararse extinguido la atribución del uso del domicilio y ajuar conyugal a favor de D./Dña. [NOMBRE Y APELLIDOS] dejando la vivienda libre.

3.º Que se deje sin efecto la obligación de D./Dña. [NOMBRE Y APELLIDOS] de abonar a D./Dña. [NOMBRE Y APELLIDOS] una pensión compensatoria de [IMPORTE] euros ( euros actuales tras las sucesivas actualizaciones), que se abona por anticipado dentro de los primeros cinco días de cada mes y que es actualizada todos los años aplicando el IPC elaborado por el INE o índice que lo sustituya a la cifra en cada momento en vigor.

4.º D./Dña. [NOMBRE Y APELLIDOS] contribuirá a los alimentos de los hijos comunes entregando por anticipado dentro de los primeros cinco días de cada mes la cantidad de [IMPORTE] euros por cada hijo, es decir, [IMPORTE] euros en total. Esta cantidad será actualizada todos los años aplicando el IPC elaborado por el INE o índice que lo sustituya a la cifra en cada momento en vigor.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
