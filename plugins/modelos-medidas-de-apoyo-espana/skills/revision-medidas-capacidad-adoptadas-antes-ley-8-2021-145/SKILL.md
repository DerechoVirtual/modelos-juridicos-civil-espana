---
name: revision-medidas-capacidad-adoptadas-antes-ley-8-2021-145
description: "Redacta el escrito «Revisión de medidas de capacidad adoptadas antes de la Ley 8/2021: solicitud» (formulario 145 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Revisión de medidas de capacidad adoptadas antes de la Ley 8/2021: solicitud

> Formulario 0145 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

- Cita la DT 5.ª Ley 8/2021: su párrafo 2.º fue modificado por la LO 5/2024 (BOE-A-2024-23630), que amplía a seis años el plazo de revisión de oficio; el párrafo citado (revisión a instancia, un año) sigue vigente.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] COLEGIO
- [ ] CALLE
- [ ] LOCALIDAD
- [ ] NÚMERO
- [ ] FECHA (2 veces)
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Procurador/a de los Tribunales y de Don»; «…adoptadas respecto de mi representado D.»; «…e sanidad y asuntos sociales de la CA de»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 249 CCiv
- art. 269 CCiv
- Ley 8/2021

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

### Formulario 0145 · Revisión de medidas de capacidad adoptadas antes de la Ley 8/2021: solicitud

- Año del modelo: 2021
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 14 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 1 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO)
- Avisos de la revisión: Cita la DT 5.ª Ley 8/2021: su párrafo 2.º fue modificado por la LO 5/2024 (BOE-A-2024-23630), que amplía a seis años el plazo de revisión de oficio; el párrafo citado (revisión a instancia, un año) sigue vigente.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito solicitando la revisión de medidas adoptadas en proceso de modificación de capacidad con anterioridad a la Ley 8/2021. Régimen transitorio.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales y de Don [COMPLETAR], a quien asiste el Letrado/a en ejercicio D./Dña. [NOMBRE Y APELLIDOS], colegiado/a nº [Nº DE COLEGIADO/A] del Iltre. Colegio de Abogados de [COLEGIO], con despacho abierto en esta localidad, calle [CALLE], ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que en la indicada representación, al amparo de la disposición transitoria quinta de la Ley 8/2021, de 2 de junio, solicito la REVISIÓN de las medidas adoptadas respecto de mi representado D. [COMPLETAR], con domicilio en [LOCALIDAD], en proceso de modificación de capacidad nº [NÚMERO] seguido ante el Tribunal al que me dirijo, todo ello en base a los siguientes:

Hechos y consideraciones jurídicas

I) En virtud de sentencia firme de fecha [FECHA] dictada en los autos seguidos ante ese Tribunal se declaró que mi representado D. padecía síndrome de Diógenes con posible trastorno de la personalidad, declarándose la modificación de capacidad del mismo y la constitución de tutela, adoptándose una medida de apoyo consistente en la asistencia para el orden y la limpieza de su domicilio con designación como tutora a la Comunidad Autónoma competente.

II) La Ley 8/2021, de 2 de junio, constituye una profunda reforma del tratamiento civil y procesal de la capacidad de las personas, que pretende incorporar las exigencias del art. 12 de la Convención de Nueva York, de 13 de diciembre de 2006. La reforma suprime la declaración de incapacidad y se centra en la provisión de los apoyos necesarios que una persona con discapacidad pueda precisar «para el adecuado ejercicio de su capacidad jurídica», con la «finalidad (de) permitir el desarrollo pleno de su personalidad y su desenvolvimiento jurídico en condiciones de igualdad» (art. 249 CCiv). Sin perjuicio de la adopción de las salvaguardas oportunas para asegurar que el ejercicio de las medidas de apoyo se acomoda a los criterios legales, y en particular, que atienda a la voluntad, deseos y preferencias de la persona que las requiera.

III) La provisión de apoyos judiciales deja de tener un carácter preferente y se supedita a la ausencia o insuficiencia de las medidas previstas por el propio interesado. Y, en cualquier caso, como dispone el art. 269 CCiv, "las medidas tomadas por la autoridad judicial en el procedimiento de provisión de apoyos serán proporcionadas a las necesidades de la persona que las precise, respetarán siempre la máxima autonomía de esta en el ejercicio de su capacidad jurídica y atenderán en todo caso a su voluntad, deseos y preferencias".

Consiguientemente, el anterior régimen de guarda legal (tutela y la curatela), para quienes precisan el apoyo de modo continuado, ha sido reemplazado por la curatela, cuyo contenido y extensión debe ser precisado por la resolución judicial que la acuerde «en armonía con la situación y circunstancias de la persona con discapacidad y con sus necesidades de apoyo» (art. 250 V CCiv).

IV) La Ley 8/2021, de 2 de junio, en coherencia con la naturaleza de la materia reformada y la finalidad perseguida, ha establecido unas reglas de aplicación transitoria especiales.

En concreto, la disposición transitoria quinta de la Ley 8/2021 establece: "las personas con capacidad modificada judicialmente, los declarados pródigos, los progenitores que ostenten la patria potestad prorrogada o rehabilitada, los tutores, los curadores, los defensores judiciales y los apoderados preventivos podrán solicitar en cualquier momento de la autoridad judicial la revisión de las medidas que se hubiesen establecido con anterioridad a la entrada en vigor de la presente Ley, para adaptarlas a esta. La revisión de las medidas deberá producirse en el plazo máximo de un año desde dicha solicitud".

V) De la propia regulación legal, contenida en los arts. 249 y ss. CCiv, así como del reseñado art. 12 de la Convención, se extraen los elementos caracterizadores del nuevo régimen legal de provisión de apoyos: i) es aplicable a personas mayores de edad o menores emancipadas que precisen una medida de apoyo para el adecuado ejercicio de su capacidad jurídica; ii) la finalidad de estas medidas de apoyo es "permitir el desarrollo pleno de su personalidad y su desenvolvimiento jurídico en condiciones de igualdad" y han de estar "inspiradas en el respeto a la dignidad de la persona y en la tutela de sus derechos fundamentales"; iii) las medidas judiciales de apoyo tienen un carácter subsidiario respecto de las medidas voluntarias de apoyo, por lo que sólo se acordaran en defecto o insuficiencia de estas últimas; iv) no se precisa ningún previo pronunciamiento sobre la capacidad de la persona; y v) la provisión judicial de apoyos debe ajustarse a los principios de necesidad y proporcionalidad, ha de respetar la máxima autonomía de la persona con discapacidad en el ejercicio de su capacidad jurídica y debe atenderse en todo caso a su voluntad, deseos y preferencias.

La reforma ha suprimido la tutela y concentra en la curatela todas las medidas judiciales de apoyo continuado. En sí mismo y más allá de la aplicación de la regulación legal sobre su provisión, del nombramiento de la(s) persona(s) designada(s) curador(es), del ejercicio y la extinción, la denominación «curatela» no aporta información precisa sobre el contenido de las medidas de apoyo y su alcance. El contenido de la curatela puede llegar a ser muy amplio, desde la simple y puntual asistencia para una actividad diaria, hasta la representación, en supuestos excepcionales. Es el juez quien debe precisar este contenido en la resolución que acuerde o modifique las medidas.

VI) En el tiempo transcurrido desde la constitución del órgano tutelar, mi representado ha recibido terapia cognitivo-conductual, combinada con tratamiento farmacológico en centro asistencial oficial dependiente de la consejería de sanidad y asuntos sociales de la CA de [COMPLETAR].

Dicho tratamiento que se ha prolongado durante año y medio con supervisión médica y psiquiátrica, habiendo seguido mi representado la totalidad del tratamiento con éxito, encontrándose a la fecha de la interposición de la presente solicitud totalmente rehabilitado de su enfermedad.

Así, en la actualidad, D. es una persona orientada, sin alteraciones sensoperceptivas ni deterioro cognitivo, según consta en el informe expedido por el informe del psiquiatra adscrito al centro que se acompaña como documento nº [Nº DE DOCUMENTO]

VII) Esta nueva regulación de las medidas de apoyo y la mejora significativa de la situación de mi representado determinan que se solicite la revisión de las mismas a fin de que se deje sin efecto la declaración de modificación de capacidad procediéndose a extinguir la tutela constituida y dejando sin efecto la medida de apoyo adoptada.

En su virtud,

SUPLICO AL TRIBUNAL:

Que tenga por presentado este escrito con los documentos acompañados y sus copias; admita todo ello; y se tenga por solicitada la REVISIÓN de las medidas adoptadas en la sentencia de fecha [FECHA] dictada por ese Tribunal, procediéndose a extinguir la tutela constituida y dejando sin efecto la medida de apoyo adoptada, inscribiendo la resolución en el Registro Civil correspondiente.

Es justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

	Firma de Procurador/a
