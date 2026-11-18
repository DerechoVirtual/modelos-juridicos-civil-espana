---
name: contestacion-propietario-comunidad-abuso-derecho-1143
description: "Redacta el escrito «Contestación del propietario a la comunidad: abuso de derecho» (formulario 1143 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación del propietario a la comunidad: abuso de derecho

> Formulario 1143 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] NÚMERO (11 veces)
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] CALLE (5 veces)
- [ ] Nº
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…n.º [NÚMERO] de»; «…de la C/ [CALLE] de la ciudad de»; «…arreras, en concreto a lo establecido en»; «…, con título de»; «…El cumplimiento de la»; «…tas negativas. Ajuntamos como documentos»; «… mayoría de cuotas de participación. 4.º»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 416.1 de la LEC
- art. 6.5 de la LEC
- art. 13.3 de la LPH
- art. 19 de la LPH
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

### Formulario 1143 · Contestación del propietario a la comunidad: abuso de derecho

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 33 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

P. Ordinario n.º [NÚMERO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante poder notarial que acompaño, ante el Tribunal comparezco con la asistencia letrada de D./Dña. [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO.

Que mediante el presente escrito procedo a CONTESTAR a la demanda promovida por la Comunidad de Propietarios de la C/ [CALLE] n.º [NÚMERO] de [COMPLETAR] en el sentido de OPONERME a la misma en atención a las siguientes consideraciones:

PREVIA.—CUESTIONES PROCESALES

1.º—Falta de capacidad de los litigantes o de representación en sus diversas clases, art. 416.1 de la LEC.

La entidad demandante, según consta en la demanda, es la Comunidad de Propietarios de la C/ [CALLE] y en su nombre, en su calidad de Presidente, comparece D./Dña. [NOMBRE Y APELLIDOS], según consta en el apoderamiento apud acta.

– Respecto a la capacidad de la parte demandante para comparecer en juicio la actora dice en el hecho primero que su “mandante es la Comunidad de Propietarios de los n.º [NÚMERO] de la C/ [CALLE] de la ciudad de [COMPLETAR] Se acompaña con la demanda y como documento n.º [NÚMERO], declaración de obra nueva y división horizontal de la citada edificación”. Pues bien, en dicha escritura se hace referencia constantemente a los n.º [NÚMERO] de la C/ [CALLE] como los que son objeto de la obra nueva y de la división horizontal. No se acredita que exista identidad entre los antiguos n.º [NÚMERO] y la actual comunidad demandante que se ciñe a los n.º [Nº]

– Respecto a la falta de representación: El art. 6.5 de la LEC reconoce capacidad para ser parte a las entidades sin personalidad jurídica a las que la ley reconozca capacidad para ser parte, debiendo comparecer por ésta, art. 7.6 de la misma norma, las personas a quienes la ley atribuya su representación en juicio.

Según el art. 13.3 de la LPH el presidente ostenta legalmente la representación de la Comunidad en juicio y fuera de él.

En los documentos n.º [NÚMERO] que acompañan a la demanda consta que el presidente era D./Dña. [NOMBRE Y APELLIDOS], mientras que en los documentos n.º [NÚMERO], actúa como presidente otra persona, D./Dña. [NOMBRE Y APELLIDOS], que es quien otorga el apoderamiento apud acta. Pero lo cierto es que en ningún momento ha acreditado su condición mediante el documento en el que conste su nombramiento. La resolución de la DGRN de 25 de mayo de 2005 dice que “la acreditación de los cargos en la propiedad horizontal puede verificarse por una doble vía: testimonio notarial del contenido del libro de actas, o bien por certificación expedida por el órgano de la Comunidad que tenga facultad certificante, con aseveración notarial, con referencia al libro de actas, de que el autor de la certificación se halla en el ejercicio de su cargo, constituyendo por tanto defecto que no se acredite el cargo de Presidente en ninguna de dichas formas”. De hecho en los poderes notariales para pleitos que otorgan los Presidentes de las Comunidades de Propietarios consta el reconocimiento por alguno de estos medios del fedatario público de la condición de presidente. Es evidente que quien dice ostentar la condición de representante de una entidad tenga que acreditarlo, y con el apoderamiento apud acta no se presentó ninguno de los documentos indicados para realizarlo, por eso consideramos que existe falta de representación.

De no estimarse las cuestiones procesales que presentamos deberá entrarse a conocer del fondo del asunto.

HECHOS

Se presenta listado de documentos que acompañan a la contestación a la demanda.

Sobre la legitimación de la parte actora nos remitimos a las cuestiones procesales alegadas en el apartado precedente. Y sobre la legitimación ad procesum del demandado estamos conformes pues el local es propiedad de mi representado.

La actuación de la Junta de Propietarios constituyó un abuso de derecho sin existencia de causa para ello por dos razones:

A) La mayoría de los propietarios de las viviendas han procedido a cerrar sus balcones anexionando de esta forma el espacio abierto a las dependencias del hogar y aumentado de esa manera la edificabilidad.

B) La obra en el local resultaba necesaria para adecuarse a la normativa de accesibilidad y supresión de barreras, en concreto a lo establecido en [COMPLETAR] (norma aplicable al supuesto concreto).

Procedemos a desarrollar cada uno de estos motivos:

A) Actuaciones previas de alteración de la fachada como elemento común sin contar con el consentimiento de la Junta de Propietarios o sin licencia municipal.

Según acreditamos con el documento n.º [NÚMERO], informe pericial emitido por D./Dña. [NOMBRE Y APELLIDOS], con título de [COMPLETAR], se comprueba que el edificio de la C/ [CALLE] ha sufrido importantes modificaciones en su estética exterior. Estas modificaciones han alterado la imagen inicialmente proyectada por el arquitecto y aumentan las cargas sobre la estructura del inmueble.

Esta situación afecta no sólo a la superficie edificable sino que también, al aumentar la superficie útil de las viviendas en distintas medidas, altera el coeficiente de participación. Esto es así porque en la medida que se incrementa la superficie de las viviendas a computar para establecer el cálculo de su coeficiente de participación, disminuye el de los locales.

De lo expuesto se deduce que los propietarios de viviendas, por constituir mayoría, imponen sus decisiones a los titulares de los locales y obran en su propio beneficio, incluso vulnerando la legalidad urbanística: para ellos no ha resultado necesario ni siquiera plantear en Junta de Propietarios el cerramiento de las terrazas y a los locales se les niega cualquier reforma técnica, aunque sea necesaria.

B) Necesariedad de la obra.

Según se acredita con el informe de la arquitecto que adjuntamos como documento n.º [NÚMERO] El cumplimiento de la [COMPLETAR] (norma aplicable al supuesto concreto) hace necesaria la obra de

La Comunidad no resultaba perjudicada en modo alguno y tampoco se beneficia con el cierre de la puerta que sí produce un agravio evidente al dueño del local. Tampoco se dan razones para justificar la negativa que se constituye de esta manera en un ejercicio abusivo de los derechos de la mayoría de propietarios de viviendas sobre los de los locales.

La puerta se abrió porque la licencia de obras, según se comprueba, era anterior a estas negativas. Ajuntamos como documentos [COMPLETAR] licencia de obras y proyecto básico de ejecución.

Respecto a los llamados acuerdos de la Comunidad y los requerimientos hemos de hacer las siguientes consideraciones:

1.º No consta que quien firma el burofax que se adjunta como documento n.º [NÚMERO] de la demanda tuviera la calidad de Presidente, ni que en ese momento contara con la autorización de la Junta para formular ese requerimiento.

2.º No se acompaña convocatoria de las Juntas para saber si se constituyeron válidamente y no consta el orden del día.

3.º Tampoco figura en las denominadas actas el coeficiente de participación de cada uno de los propietarios y de esta manera no consta si las mayorías de votos de los comuneros constituyen también mayoría de cuotas de participación.

4.º [COMPLETAR]

Todos estos defectos formales unidos al abuso de derecho deben determinar la inadmisión de la pretensión de la demanda.

FUNDAMENTOS DE DERECHO

I. COMPETENCIA.—Conforme con el correlativo.

II, III y V. TRAMITACIÓN y LEGITIMACIÓN.—

(Opciones:)

– Conforme con los correlativos.

– Disconformes en atención a las cuestiones procesales planteadas en el encabezamiento de esta contestación que damos por reproducidas en este apartado.

IV. FONDO DEL ASUNTO.—

Con carácter general negamos los alegados de contrario en cuanto sean contrarios a nuestros intereses.

1.º Art. 7 del CC, según el cual los derechos deberán ejercitarse conforme a las exigencias de la buena fe. La ley no ampara el abuso de derecho.

La Comunidad ha consentido a los propietarios de vivienda realizar obras que afectan en mayor medida a la estructura del edificio, como son el cerramiento de la terrazas, mientras que se oponen sin ninguna justificación a la apertura de la puerta del local que no le supone ningún perjuicio.

2.º Vulneración del art. 19 de la LPH sobre la forma de redactar las actas, impugnamos la validez de las dos que se presentan por defectos de forma insubsanables al no recoger el carácter de la misma, la falta de indicación de las cuotas de participación, la falta de acreditación de la representación de uno de los vecinos, el orden del día, las cuotas de participación que votaron a favor o en contra de los acuerdos

3.º Vulneración del art. 13.3 de la LPH sobre la falta de acreditación de la presidencia.

4.º Art. 7 de la LPH el propietario podrá modificar elementos cuando no altere la estructura del edificio.

En el caso presente ya está alterada la estructura por las obras anteriores.

5.º Art. 17 de la LPH sobre la adopción de acuerdos. Según se ha indicado se han alterado los coeficientes de participación por las obras que se han realizado en el edificio por eso las votaciones no podrán ser válidas mientras no se adecuen los coeficientes a la nueva realidad.

I. COSTAS: en aplicación del art. 394 de la LEC se impondrán a la parte actora por la mala fe en la presentación de esta demanda.

Por lo expuesto,

SUPLICO AL TRIBUNAL: que tenga por presentado este escrito con los documentos que acompaño, lo admita a trámite y tenga por formulada CONTESTACIÓN a la demanda en el sentido de OPONERME a ella solicitando (en su caso) que se estimen las cuestiones procesales planteadas procediéndose al archivo del procedimiento ante la falta de acreditación de la legitimación y la representación o, de inadmitirse o subsanarse ésta, que en su día, se dicte sentencia por la que se desestime íntegramente la demanda con expresa imposición de costas a la parte actora.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

NORMATIVA APLICABLE

Artículo 405 de la Ley de Enjuiciamiento Civil.

Artículo 7, 13, 17 y 19 de la Ley de Propiedad Horizontal.

NOTAS ACLARATORIAS

En la contestación a la demanda se plantearán las excepciones procesales que en su caso existan así como las cuestiones de fondo.

Por lo expuesto,

========================================================================
