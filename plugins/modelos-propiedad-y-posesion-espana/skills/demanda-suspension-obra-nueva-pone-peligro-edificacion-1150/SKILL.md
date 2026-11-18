---
name: demanda-suspension-obra-nueva-pone-peligro-edificacion-1150
description: "Redacta el escrito «Demanda de suspensión de obra nueva que pone en peligro la edificación del demandante» (formulario 1150 de propiedad y derechos reales, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de suspensión de obra nueva que pone en peligro la edificación del demandante

> Formulario 1150 del plugin **Propiedad y derechos reales** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (3 veces)
- [ ] Nº DE DOCUMENTO
- [ ] IMPORTE
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…n de suspensión de obra nueva situada en»; «…que se está realizando por la mercantil»; «…o adquirido recientemente por la empresa»; «…presento informe del perito en»; «…tuación los representantes de la empresa»; «…rajudicial. En este sentido, se acudió a»; «… por el Tribunal dirigiendo al demandado»; «…inmediata orden de suspensión de la obra»; «…los trabajos de la obra que la mercantil»; «…está realizando en»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 21 y 22 de la LOPJ
- art. 85 de la LOPJ
- art. 45 de la LEC
- art. 441.2 de la LEC
- art. 10 de la LEC
- arts. 23 y 31 de la LEC
- art. 437.1 LEC
- art. 5 de la Ley Orgánica 1/2025
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

### Formulario 1150 · Demanda de suspensión de obra nueva que pone en peligro la edificación del demandante

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 30 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda:

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante poder notarial que acompaño, en el que constan las circunstancias personales de mi mandante ante el Tribunal comparezco bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO:

Que mediante el presente escrito y conforme permite el art. 250.1.5.º de la LEC formulo demanda a tramitar por el cauce del juicio verbal ejercitando acción de suspensión de obra nueva situada en [COMPLETAR] que se está realizando por la mercantil [COMPLETAR], con domicilio social en [LOCALIDAD] (ciudad), c/ [CALLE] Basamos nuestra pretensión en los siguientes:

HECHOS

Se presenta listado de documentos que acompañan a la demanda.

D./Dña. [NOMBRE Y APELLIDOS] es propietario de la finca urbana de la c/ [CALLE] de esta ciudad, según acredito con nota simple del Registro de la Propiedad que presento como doc. n.º [NÚMERO] de la prueba.

El inmueble colindante ha sido adquirido recientemente por la empresa [COMPLETAR] (demandada), tal como consta en la certificación del Registro de la Propiedad que acompaño como doc. n.º [NÚMERO] Inmediatamente los propietarios han comenzado unas obras de reparación en el inmueble colocando andamios que apoyan en el lateral del dominio de mi representado y que ponen en peligro la integridad de esta edificación. A esto hay que añadir que no se ha solicitado permiso alguno al actor para obrar de esta forma.

(Opciones):

1.º Con el n.º [NÚMERO] presento informe del perito en [COMPLETAR] D./Dña. [NOMBRE Y APELLIDOS] sobre el estado actual de la obra y sobre la incidencia en la propiedad del actor. En este estudio se incluyen fotografías que ayudan a entender lo expuesto por el especialista.

2.º Intereso que se nombre perito por el Tribunal con el título de [LOCALIDAD] a fin de que antes de la celebración de la vista se emita informe sobre el estado de realización de la obra nueva y su incidencia en la propiedad de D./Dña. [NOMBRE Y APELLIDOS]

3.º Entiende esta parte que puede resultar oportuno el reconocimiento judicial de la obra y su incidencia en la propiedad de mi representado, motivo por el cual solicitamos que antes de la celebración de la vista se proceda a la práctica de este medio de prueba.

4.º Intereso que se nombre perito por el Tribunal con el título de [LOCALIDAD] a fin de que antes de la celebración de la vista se emita informe sobre el estado de realización de la obra nueva y su incidencia en la propiedad de D./Dña. [NOMBRE Y APELLIDOS] y que la inspección de este perito se realice de forma conjunta con el reconocimiento judicial de la obra y su incidencia en el dominio colindante, cuya práctica también interesamos con carácter previo.

Requerido para que modifique esta situación los representantes de la empresa [COMPLETAR] se han negado sin dar explicación alguna, motivo por el que nos vemos obligados a interponer esta acción.

(Para personas jurídicas y cuantía superior a 2.000 euros). Acompañamos como documento modelo 696 de liquidación de la tasa judicial.

Previamente a la interposición de la presente demanda, se han llevado a cabo diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

Jurisdicción y competencia

Los arts. 21 y 22 de la LOPJ atribuyen a la jurisdicción española y al orden civil el conocimiento de estas materias, y el art. 85 de la LOPJ y art. 45 de la LEC designan a los Tribunales de Instancia como los encargados de conocer estas pretensiones.

La competencia territorial viene determinada por el art. 52.1.1.º de la LEC.

Tramitación y actuaciones previas a la vista

PRIMERO.— El art. 250.1.5.º de la LEC remite al cauce del juicio verbal las demandas que pretendan que el Tribunal resuelva, con carácter sumario, la suspensión de una obra nueva.

La cuantía se fija en [IMPORTE] euros en atención a lo establecido en el art. 251.3.ª.5.º de la LEC.

SEGUNDO.— En aplicación de lo establecido en el art. 441.2 de la LEC interesamos que antes del traslado para la contestación de esta demanda se dirija inmediata orden de suspensión al dueño o encargado de la obra.

Legitimación y postulación

El art. 10 de la LEC, según el cual están legitimadas ambas partes por ser titulares del objeto de este proceso.

Los arts. 23 y 31 de la LEC exigen la firma de la demanda por procurador y letrado cuando la cuantía de la demanda exceda los 2.000 euros.

Cumplimiento de los requisitos de procedibilidad

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC en relación con el art. 437.1 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Fondo del asunto

PRIMERO.— El art. 250.1.5.º de la LEC permite solicitar la tutela sumaria de la posesión mediante la solicitud de suspensión de una obra nueva que perturbe o pueda causar perjuicios a quien solicita el auxilio judicial.

SEGUNDO.— De la redacción del art. 441.2 de la LEC se puede desprender que uno de los requisitos que se exige para poder valerse de esta acción consiste en que la obra se esté realizando y no haya concluido. En este caso se puede apreciar por el informe y las fotografías que aportamos que nos encontramos dentro de ese supuesto, ya que se están realizando las labores preliminares de la construcción.

TERCERO.— Art. 446 del CC, todo poseedor tiene derecho a ser respetado en su posesión y si fuere inquietado en ella debe ser amparado o restituido.

Costas

En aplicación del art. 394 de la LEC deberán imponerse al demandado al desestimarse sus pretensiones.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño, lo admita y,

1.º (En su caso) Se practiquen los medios de prueba interesados con carácter previo a la celebración de la vista.

2.º Con carácter previo al traslado para contestar la demanda, una vez admitida a trámite, se dicte resolución por el Tribunal dirigiendo al demandado [COMPLETAR] (nombre) inmediata orden de suspensión de la obra [COMPLETAR] (en su caso) y que se practiquen los medios de prueba interesados con carácter previo.

3.º Así como que en su día siguiendo el trámite del juicio verbal se dicte en su día sentencia por la que se acuerde la definitiva suspensión de los trabajos de la obra que la mercantil [COMPLETAR] está realizando en [COMPLETAR] consistentes en [DESCRIBIR] (en su caso), así como que se repongan las cosas al estado anterior.

4.º Que se condene en costas al demandado.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
