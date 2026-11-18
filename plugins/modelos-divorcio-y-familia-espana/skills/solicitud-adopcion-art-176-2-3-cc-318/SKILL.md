---
name: solicitud-adopcion-art-176-2-3-cc-318
description: "Redacta el escrito «Solicitud de adopción (art. 176.2.3.ª CC)» (formulario 318 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Solicitud de adopción (art. 176.2.3.ª CC)

> Formulario 0318 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] Nº DE DOCUMENTO (6 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] COLEGIO
- [ ] CALLE
- [ ] FECHA (5 veces)
- [ ] LOCALIDAD (4 veces)
- [ ] PROFESIÓN
- [ ] IMPORTE
- [ ] Nº (4 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 32 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Procurador/a de los Tribunales, y de Don»; «…y Doña»; «…nes jurídicas: 1º) Mis representados Don»; «…y Doña»; «…y Doña [COMPLETAR], nacieron en»; «…contrajeron matrimonio civil/canónico en»; «…compañan como documentos números 2º) Don»; «…y Doña»; «…, son de profesión [PROFESIÓN] y»; «…ualmente prestan servicios el primero en»; «…, y la segunda en»; «…euros. El adoptando nació en»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 176 CCiv
- arts. 35.3 y 4 LJV
- art. 37 LJV
- art. 177 CCiv
- art. 38 LJV
- art. 109 CCiv
- arts. 2 y 33 LJV
- arts. 3 y 34.2 LJV
- art. 175 CCiv
- arts. 4 y 34.1 LJV
- art. 39.5 LJV
- Ley 26/2015

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

### Formulario 0318 · Solicitud de adopción (art. 176.2.3.ª CC)

- Año del modelo: 2020
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 60 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de solicitud del adoptante interesando el inicio de expediente de jurisdicción voluntaria de adopción de un menor en guarda con fines de adopción (o acogido) durante más de un año.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales, y de Don [COMPLETAR] y Doña [COMPLETAR], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], a quien asiste el Letrado/a en ejercicio D./Dña. [NOMBRE Y APELLIDOS], colegiado/a nº [Nº DE COLEGIADO/A] del Iltre. Colegio de Abogados de [COLEGIO], con despacho abierto en esta localidad, calle [CALLE], ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que por el presente escrito, en la representación que acredito y siguiendo instrucciones de mi mandante promuevo EXPEDIENTE DE JURISDICCIÓN VOLUNTARIA EN SOLICITUD DE CONSTITUCIÓN DE ADOPCIÓN del menor, todo ello de conformidad con lo previsto en los arts. 176 CCiv y 33 y ss. LJV y en base a los siguientes:

Hechos y consideraciones jurídicas:

1º) Mis representados Don [COMPLETAR] y Doña [COMPLETAR], nacieron en [COMPLETAR], el día [FECHA] y el día [FECHA], respectivamente, y contrajeron matrimonio civil/canónico en [COMPLETAR] con fecha [FECHA], como se acreditan con las certificaciones de nacimiento y literal de matrimonio expedidas por el Registro civil de [LOCALIDAD] que se acompañan como documentos números

2º) Don [COMPLETAR] y Doña [COMPLETAR], son de profesión [PROFESIÓN] y [COMPLETAR], respectivamente y actualmente prestan servicios el primero en [COMPLETAR], y la segunda en [COMPLETAR], obteniendo unos ingresos anuales de [IMPORTE] euros.

El adoptando nació en [COMPLETAR] el [COMPLETAR] de [COMPLETAR] de [COMPLETAR], por lo que tiene en la actualidad [Nº] años de edad. Se acompaña como documento nº [Nº DE DOCUMENTO] certificación literal de nacimiento del menor expedido por el encargado del Registro Civil de

Según se acredita mediante certificación librada por la Entidad pública de Protección de Menores [COMPLETAR] (documento nº [Nº DE DOCUMENTO]), consta en el expediente nº [Nº DE PROCEDIMIENTO]/[AÑO] del año [COMPLETAR], que dicho menor resulta ser hijo de Don [COMPLETAR] y Doña [NOMBRE Y APELLIDOS]

El padre biológico del menor cuya adopción se promueve falleció en fecha [FECHA], cuando éste contaba tan sólo con [Nº] meses de edad.

Se acompaña, como documento nº [Nº DE DOCUMENTO], certificación literal de la inscripción de defunción del padre biológico del menor, expedida por el Encargado del Registro Civil de

3º) La madre del menor, que se veía incapaz de atender a su hijo y deseaba llevar una vida libre de ataduras, abandonó el domicilio familiar hace ahora [Nº] meses, y, con ello, los más elementales cuidados del pequeño encontrándose desde entonces en paradero desconocido, sin que se hayan tenido noticias suyas en su entorno familiar.

Por estos motivos, tuvieron que intervenir los Servicios Sociales, a fin de prestar al menor los cuidados que por su edad necesitaba y, viendo que la situación de abandono del menor era irreversible, por cuanto [COMPLETAR], la citada Entidad pública lo declaró en situación de desamparo, asumiendo su tutela y procediendo seguidamente a su internamiento en el Centro

4º) Como resulta también de la certificación a que se refiere el hecho 2º, el menor fue tomado en guarda con fines de adopción (1) por mis representados, en fecha

Dicha medida fue tomada por la Entidad Pública por el peligro que un internamiento continuado podría producir en el menor. Desde entonces, el menor permanece totalmente integrado en el núcleo familiar de mis mandantes, hasta el extremo de ser tenido como hijo propio.

Se acompaña como documento nº [Nº DE DOCUMENTO], certificación de la declaración de desamparo del menor y su guarda mediante acogimiento familiar por los solicitantes de la adopción, guarda con fines de adopción que se inició en fecha [FECHA], hace por tanto [Nº] años.

5º) Desde entonces, el adoptando ha convivido como un miembro más de la familia de Don [COMPLETAR] y Doña [COMPLETAR], por lo que es del deseo de todo el núcleo familiar que esta situación se formalice pasando a ser miembro de pleno derecho de ésta.

6º) Que mis representados son mayores de veinticinco años y tienen una diferencia de edad con el adoptando superior a dieciséis años, tal como se acredita por los certificados de nacimiento acompañados como documentos números

Las relaciones hasta la fecha y durante el tiempo que ha durado el acogimiento entre los adoptantes y el adoptado han sido muy buenas, habiéndose integrado el menor de manera plena en la vida familiar de mis representantes, acude al Colegio [COMPLETAR] sito en [LOCALIDAD], siendo el resultado en los estudios favorables. Se acredita este extremo con el informe que emite la dirección del Colegio y el Psicólogo adscrito al mismo.

7º) Que en relación a la indicación de las condiciones personales, familiares y sociales y los medios de vida de los adoptantes y sus relaciones con el adoptando, la capacidad de los solicitantes para asumir las obligaciones que les corresponden como padres adoptivos está más que probada, por cuanto además de contar con suficientes recursos económicos (se aportan las certificaciones expedidas por las empresas donde prestan servicios mis representados y las declaraciones de IRPF correspondientes a los cinco últimos años), ya se ha hecho mención expresa a que el menor [COMPLETAR] reside desde [COMPLETAR] con mi mandantes y sus hijos habidos del matrimonio, en el domicilio sito en [LOCALIDAD] según se justifica con el certificado de empadronamiento, estando el menor matriculado en el mismo colegio al que acuden los hijos de mi mandante y realizando vida conjunta con todos ellos desde el primer momento, tanto a nivel personal, familiar y escolar según se acredita con el informe del colegio al que acude el menor y las notas de éste, a través de las que se advierte su plena integración escolar.

Se acompañan adjuntos documentos números [COMPLETAR] a [COMPLETAR], ofrecimiento por escrito para la adopción por parte de los adoptantes e informes y documentos de interés en prueba de lo anterior, conforme a los arts. 35.3 y 4 LJV.

Dicha relación se constata también en el expediente abierto por la entidad [COMPLETAR], que promovió en su día el acogimiento del menor a favor de mis representados, y que ha venido haciendo el seguimiento pertinente durante el tiempo que viene durando dicho acogimiento. Se dejan citados a efectos probatorios los archivos de la entidad

En particular, se acompaña como documento nº [Nº DE DOCUMENTO] la declaración previa de idoneidad de mis mandantes para el ejercicio de la patria potestad emitida por la Entidad Pública.

8º) Que en relación a los consentimientos, asentimientos y audiencias que son preceptivas para la válida constitución de la adopción, a los efectos de lo establecido por el art. 37 LJV en relación al art. 177 CCiv, el adoptando deberá consentir la adopción por ser mayor de 12 años/deberá ser oído al tener menos de 12 años/no debe ser citado debido a su corta edad. Mis representados deberán de comparecer ante el Juez para consentir en la adopción, en su calidad de adoptantes, debiendo ser citados judicialmente en su domicilio sito en

Asimismo, deberá ser citada la madre biológica para ser oída, al no ser necesario su asentimiento, conforme al art. 177.3.1º CCiv. Con carácter previo, y ya que se desconoce su último domicilio, será necesario proceder conforme al art. 38 LJV.

Estando actualmente el menor sujeto a la tutela de la Entidad pública, también será necesaria la audiencia de la misma, a cuyo fin se le dará traslado de la presente solicitud.

9º) Una vez constituida la adopción, el adoptado ostentará por apellidos los siguientes: [COMPLETAR], conforme a lo dispuesto en el art. 109 CCiv.

10º) Que es competente el Tribunal de Instancia al que me dirijo a tenor de lo previsto en los arts. 2 y 33 LJV en relación con lo dispuesto en el art. 85.1º LOPJ, por ser el del domicilio de la Entidad Pública que tiene encomendada la protección del adoptando.

11º) Que mis representados están legitimados activamente para el ejercicio de la solicitud efectuada en petición de adopción, conforme a lo dispuesto en los arts. 176.2.3ª CCiv y 35.3 LJV, por cuanto concurre la circunstancia de llevar el adoptando más de un año en situación de guarda con fines de adopción respecto a mis mandantes, no siendo necesario entonces la propuesta previa de la entidad pública.

12º) Que conforme a lo dispuesto en los arts. 3 y 34.2 LJV la solicitud está firmada por abogado y procurador, pese a que su intervención no es preceptiva en el caso de autos.

13º) Que la presente solicitud deberá ser tramitada por las normas establecidas para la jurisdicción voluntaria en los arts. 17 a 20 y 33 y ss. LJV.

14º) Que se cumplen todos los requisitos legales establecidos en el art. 175 CCiv para la adopción, en cuanto a las edades de adoptantes y de adoptando, diferencias de edad entre los mismos, y no hallarse incurso en ninguna de las prohibiciones establecidas en el precepto.

15º) Que conforme a los arts. 4 y 34.1 LJV la tramitación del expediente de adopción se practicará con intervención del Ministerio Fiscal.

16º) Que el testimonio de la resolución firme en que se acuerde la adopción deberá remitirse al Registro Civil para que se practique su inscripción, conforme al art. 39.5 LJV.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL:

que teniendo por presentado este escrito con los documentos y copias que se acompañan, se inicie EXPEDIENTE DE JURISDICCIÓN VOLUNTARIA EN SOLICITUD DE CONSTITUCIÓN DE ADOPCIÓN por Don [COMPLETAR] y Doña [COMPLETAR] del menor [COMPLETAR] y, tras recabar todos los consentimientos y asentimientos requeridos al efecto, todo ello con intervención del Ministerio Fiscal, en interés del menor, se sirva dicte Auto constituyendo la adopción solicitada, con todos los efectos legales inherentes al respecto, designando como adoptantes a mis representados, acordando igualmente que en adelante el adoptado pase a llamarse [COMPLETAR], librándose, una vez firme la resolución, testimonio de la misma para su inscripción en el Registro Civil de [LOCALIDAD], junto a lo demás que en Derecho proceda.

OTROSI DIGO:

que dado que el domicilio de la madre del adoptado es desconocido deberá por el Tribunal practicarse las diligencia prevenidas por el art. 38 LJV.

Por lo que nuevamente,

SUPLICO AL TRIBUNAL, acuerde la práctica de las diligencias interesadas.

Es justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) Téngase en cuenta también que la DA 6ª de la Ley 26/2015 de 28 de julio, de modificación del sistema de protección a la infancia y a la adolescencia, establece que, a los efectos de las normas y leyes existentes con anterioridad a la presente ley y de las legislaciones correspondientes de las Comunidades Autónomas con Código Civil propio o con leyes civiles que lo regulen, se equipara la situación de acogimiento familiar temporal con acogimiento familiar simple, y la situación de guarda con fines de adopción con el acogimiento preadoptivo.
