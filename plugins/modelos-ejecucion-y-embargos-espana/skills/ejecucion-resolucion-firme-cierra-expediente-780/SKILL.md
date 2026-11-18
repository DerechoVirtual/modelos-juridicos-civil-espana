---
name: ejecucion-resolucion-firme-cierra-expediente-780
description: "Redacta el escrito «Ejecución de la resolución firme que cierra el expediente de jurisdicción voluntaria» (formulario 780 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Ejecución de la resolución firme que cierra el expediente de jurisdicción voluntaria

> Formulario 0780 del plugin **Ejecución civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.
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
- [ ] NOMBRE Y APELLIDOS (13 veces)
- [ ] FECHA (2 veces)
- [ ] PLAZO (2 veces)
- [ ] LUGAR
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…engo acreditada en los autos de juicio /»; «…, administrador/a social de la entidad»; «…SA»; «…onforme a lo ordenado en auto dictado el»; «…días desde la comparecencia celebrada el»; «… al administrador/a social de la entidad»; «… examinados, relativos a las operaciones»; «…omo administrador/a social de la entidad»; «…omo administrador/a social de la entidad»; «… examinados, relativos a las operaciones»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 545.1 de la Ley 1/2000
- art. 22.1 LJV
- art. 538 LEC
- art. 539.1 LEC
- art. 113.2 LJV
- art. 548 LEC
- art. 518 LEC
- art. 549 LEC
- art. 550 LEC
- artículo 705 LEC
- arts. 114.2 y 115.2 LJV
- art. 115.1 LJV
- art. 116 LJV
- art. 539.2 LEC
- art. 583 LEC
- art. 539 LEC
- Ley 15/2015

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

### Formulario 0780 · Ejecución de la resolución firme que cierra el expediente de jurisdicción voluntaria

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; restos de formato retirados; notas del formulario agrupadas al final (1); 29 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda ejecutiva a fin de que se lleve a cabo la resolución firme que pone fin al expediente de jurisdicción voluntaria frente al administrador social, requiriéndole que entregue al Letrado de la Administración de Justicia el libro diario, el libro de cuentas y el libro registro en soporte informático.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], cuya representación tengo acreditada en los autos de juicio / [COMPLETAR], seguido contra D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco y como mejor proceda en derecho DIGO: (1)

Que mediante el presente escrito formulo demanda ejecutiva contra D./Dña. [NOMBRE Y APELLIDOS], administrador/a social de la entidad [COMPLETAR] SA [COMPLETAR], a fin de que se proceda a exhibir los libros de la misma conforme a lo ordenado en auto dictado el [COMPLETAR]. Todo ello según resulta de los siguientes

HECHOS

PRIMERO.- El pasado día [FECHA] por el órgano judicial al que me dirijo se dictó auto que puso fin al expediente de jurisdicción voluntaria tramitada conforme a los arts. 112 y ss. de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), dentro del plazo de cinco días desde la comparecencia celebrada el [COMPLETAR]. En su parte dispositiva se ordenaba al administrador/a social de la entidad [COMPLETAR] SA, D./Dña. [NOMBRE Y APELLIDOS] que aportara al Tribunal, ante el Letrado de la Administración de Justicia: el libro diario, el libro de cuentas y ganancias y el libro registro de socios en soporte informático especificando los asientos que debían ser examinados, relativos a las operaciones [COMPLETAR], y las relaciones con los socios siguientes: D./Dña. [NOMBRE Y APELLIDOS], D./Dña. [NOMBRE Y APELLIDOS], D./Dña. [NOMBRE Y APELLIDOS].

SEGUNDO.- Dicho auto al no ser recurrido adquirió el carácter de firme, habiendo transcurrido más de veinte días desde que se notificó la resolución de condena al demandado.

TERCERO.- Dado que hasta la fecha no se han aportado los soportes informáticos que se aluden en la sentencia dictada en las presentes actuaciones, me veo en la necesidad de formular la presente demanda ejecutiva.

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA

Según el art. 545.1 de la Ley 1/2000, de 7 de enero, de Enjuiciamiento Civil (en lo sucesivo, LEC), al cual se remite el art. 22.1 LJV, será competente para la ejecución de resoluciones judiciales y de transacciones y acuerdos judicialmente homologados o aprobados, el tribunal que conoció del asunto en primera instancia o el que homologó o aprobó la transacción o el acuerdo.

Por eso se presenta esta demanda ante el Tribunal al que gustosamente me dirijo, ya que fue quien dictó el auto que sirve de título para la presente ejecución.

II.- LEGITIMACIÓN

El art. 538 LEC regula que es parte en el proceso de ejecución la persona o personas que piden y obtienen el despacho de la ejecución y la persona o personas frente a las que ésta se despacha, añadiendo que sólo podrá despacharse ejecución a instancia de quien aparezca como acreedor en el título ejecutivo, entre otros, frente a quien aparezca como deudor en el mismo título.

Tratándose de la ejecución de auto firme de condena a un hacer no personalísimo, es obvio que mi mandante es el acreedor, quien solicitó la exhibición que se pretende, y el demandado es el deudor, obligado a la misma, tal y como concluye la parte dispositiva del auto de expediente de jurisdicción voluntaria del que dimana esta demanda ejecutiva.

III.- POSTULACIÓN

Conforme a lo dispuesto en el art. 539.1 LEC, la demanda viene firmada por abogado y procurador, ya que estamos ante la ejecución de una resolución dictada en un proceso en que es preceptiva la intervención de dichos profesionales, tal y como se exige en el art. 113.2 LJV.

IV.- TÍTULO DE EJECUCIÓN

El art. 517.2.9º LEC enumera como uno de los títulos que lleva aparejada ejecución las demás resoluciones que conforme a ley, en este caso, el art. 22.1 LJV, lleven aparejado ejecución. En el presente caso, el auto dictado conforme al art. 114 de dicho texto legal, que sirve de fundamento a esta demanda.

V.- REQUISITOS TEMPORALES

La resolución de condena se ha notificado al ejecutado hace más de veinte días (art. 548 LEC) y la demanda ejecutiva se ha interpuesto sin que hayan transcurrido los cinco años siguientes a la firmeza de la sentencia, que el art. 518 LEC fija como de caducidad de la acción ejecutiva.

VI.- REQUISITOS FORMALES

La presente demanda contiene todos los requisitos enumerados en el art. 549 LEC, ya que se ha indicado cual es el título en que se funda, la tutela ejecutiva que se pretende y la persona frente a la que se interesa el despacho de la ejecución. Por último se acompaña a la demanda ejecutiva la documentación necesaria de la contemplada en el art. 550 LEC.

VII.- EJECUCIÓN DE CONDENA DE HACER NO PERSONALISIMO

El artículo 705 LEC, dispone que si el título ejecutivo obliga a hacer alguna cosa, el tribunal requerirá al deudor para que la haga dentro de un plazo que fijará según la naturaleza del hacer y las circunstancias que concurran. En esta misma línea los arts. 114.2 y 115.2 LJV permiten que se reclame, tal y como se contiene en el título ejecutivo cuya ejecución se pretende, los libros en cuestión, en soporte informático.

Asimismo, el art. 115.1 LJV obliga al ejecutado, en este caso al administrador social, a colaborar y facilitar el acceso a la documentación requerida. El art. 116 LJV añade que si se negara, obstaculizara, o quebrantara tal deber, de manera injustificada, será requerido por el Letrado de la Administración de Justicia para que lo haga y se abstenga de reiterar el quebrantamiento, con apercibimiento de la imposición de multa y de incurrir en un delito de desobediencia a la autoridad judicial. Las multas podrán ser de hasta 300 euros al día, teniendo en cuenta las circunstancias del hecho de que se trate y de los perjuicios que pudieran causar; y se ingresarán en el Tesoro Público.

En atención a los preceptos legales citados, y dado que hasta la fecha no se ha facilitado lo ordenado, se solicita que se despache ejecución frente a D./Dña. [NOMBRE Y APELLIDOS] como administrador/a social de la entidad [COMPLETAR] SA, requiriéndole por el Letrado de la Administración de Justicia para que en el plazo de [PLAZO] entregue en soporte informático los libros requeridos, bajo apercibimiento de imposición de una multa de 150 euros diarios, y de incurrir en un delito de desobediencia a la autoridad judicial. Se solicita la fijación de dicha cuantía, en su extensión media en atención a las circunstancias del caso y a los perjuicios que se pueden ocasionar. Recuérdese que la solicitud de exhibición se hacía en el marco de una entidad mercantil de gran importancia en la cual mi mandante, como socio minoritario, tiene vedado el acceso a la documentación a la que tiene derecho para poder instar una junta en la que se pueda cesar a los administradores sociales por falta de diligencia en el ejercicio de su función. Extremos que sólo se pueden comprobar a partir del análisis de la documentación requerida.

VIII.- COSTAS

En virtud de lo dispuesto en el art. 539.2 LEC en relación con el art. 583 LEC, las costas de esta ejecución deberán ser impuestas al ejecutado, ya que ha sido quien ha originado la necesidad de este procedimiento al no haber cumplido con lo establecido en el auto recaída en las presentes actuaciones.

De conformidad con lo anteriormente expuesto se formula al Tribunal la siguiente

PETICION

Que teniendo por presentado este escrito con los documentos acompañados y copia de todo ello, se sirva admitirlo, ordenando se entiendan conmigo las sucesivas diligencias y en nombre de mi patrocinado se tenga por presentada demanda ejecutiva para que, una vez examinados los requisitos y presupuestos procesales, el título ejecutivo y los actos de ejecución que se solicitan, así como la propia competencia, se despache ejecución frente a D./Dña. [NOMBRE Y APELLIDOS] como administrador/a social de la entidad [COMPLETAR] SA, requiriéndole por el Letrado de la Administración de Justicia para que en el plazo de [PLAZO] entregue en soporte informático el libro diario, el libro de cuentas y ganancias y el libro registro de socios en soporte informático especificando los asientos que debían ser examinados, relativos a las operaciones [COMPLETAR], y las relaciones con los socios siguientes: D./Dña. [NOMBRE Y APELLIDOS], D./Dña. [NOMBRE Y APELLIDOS], D./Dña. [NOMBRE Y APELLIDOS]. Todo ello, bajo apercibimiento de imposición de una multa de 150 euros diarios, y de incurrir en un delito de desobediencia a la autoridad judicial, con imposición de las costas derivadas de esta ejecución al mismo.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para presentar demanda de ejecución variará, según el art 3.2 LJV, y el art. 539 LEC, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico de la presente demanda el art. 113.2 LJV, exige dichos requisitos para la tramitación de la fase declarativa; lo que, en aplicación de los preceptos antes citados, se extiende a la ejecución.

========================================================================
