---
name: oposicion-provision-medidas-judiciales-apoyo-146
description: "Redacta el escrito «Oposición a la provisión de medidas judiciales de apoyo» (formulario 146 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición a la provisión de medidas judiciales de apoyo

> Formulario 0146 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] COLEGIO
- [ ] CALLE
- [ ] FECHA
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Procurador/a de los Tribunales y de Don»; «…e de jurisdicción voluntaria instado por»; «…, fallecida el»; «…, certificado médico expedido por el Dr.»; «…l centro de rehabilitación de la Clínica»; «…para»; «…chos básicos de nuestro patrocinado para»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 275 y 276 CCiv
- art. 41 CE
- art. 268 CCiv

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

### Formulario 0146 · Oposición a la provisión de medidas judiciales de apoyo

- Año del modelo: 2021
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 19 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de oposición en un expediente de jurisdicción voluntaria sobre provisión de medidas judiciales de apoyo a personas con discapacidad.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales y de Don [COMPLETAR], a quien asiste el Letrado/a en ejercicio D./Dña. [NOMBRE Y APELLIDOS], colegiado/a nº [Nº DE COLEGIADO/A] del Iltre. Colegio de Abogados de [COLEGIO], con despacho abierto en esta localidad, calle [CALLE], ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que el pasado día [FECHA], mi representado ha sido citado a la comparecencia que debe celebrarse en el expediente de jurisdicción voluntaria instado por [COMPLETAR] sobre adopción de medidas judiciales de apoyo a personas con discapacidad respecto a su persona.

Que, de conformidad con lo dispuesto en los arts. 17.3 II y 42 bis b).5 LJV, mediante el presente escrito formulo OPOSICIÓN a la solicitud de la promotora del expediente, en base a los siguientes:

HECHOS

PRIMERO.- Se insta por la promotora expediente de provisión de medidas judiciales de apoyo estable respecto de mi representado en base a una supuesta discapacidad, alegándose que padece síndrome de Guillain-Barré, solicitando la constitución de la curatela para actos patrimoniales y que se nombre curadora a la promotora del expediente, hija de mi representado.

Efectivamente la promotora del expediente es hija de mi representado; por otro lado, hija única del matrimonio habido con Dña. [NOMBRE Y APELLIDOS], fallecida el [COMPLETAR] según se desprende de la fotocopia del Libro de Familia que ha aportado la parte actora.

No obstante, esta parte niega la existencia de cualquier tipo de discapacidad en mi representado, tal como se expondrá a continuación, y que sea necesaria la adopción de cualquier tipo de medida de apoyo para el mismo.

SEGUNDO.- Nada se objeta sobre que mi representado padece la enfermedad diagnosticada, ni sobre que se haya venido agravando desde su aparición, como pertenece a la naturaleza de la misma, crónica y progresiva, y es verdad que requiere el afectado ser atendido permanentemente por una enfermera.

Lo que no se admite es esa afirmación adversa de que le es imposible atender a sus más elementales necesidades como persona por sí mismo, ya que no es lo que exactamente pone el certificado médico acompañado de contrario, ni es lo cierto.

Pues bien, nuestro representado, pese a la carga que supone para sí mismo estar impedido en cama, es una persona con autonomía y pleno dominio de sus actos.

TERCERO.- En efecto, nuestro mandante se encuentra postrado en cama, lo cual, en modo alguno, supone que concurran en el mismo circunstancias que determinen la necesidad de medidas de apoyo para el ejercicio de su capacidad jurídica, puesto que D. no está impedido de gobernar su persona.

Se acompaña, señalado como documento nº [Nº DE DOCUMENTO], certificado médico expedido por el Dr. [COMPLETAR], del centro de rehabilitación de la Clínica [COMPLETAR], especialista que sigue a nuestro mandante, y que acredita que las capacidades psíquicas de nuestro representado no sufren ningún deterioro; es más, posee una memoria muy superior a la media de las personas de su edad, lo que unido a que tiene un importante patrimonio que administra y mantiene un actividad rentable domiciliaria, determina que, en modo alguno, pueda pensarse que nos hallemos ante una persona en situación de discapacidad, por mucho que no pueda hacer una vida normal.

En cualquier caso, y de constatarse que mi representado precisa alguna medida de apoyo, debe manifestarse desde momento su rotunda oposición a que sea designada curadora la promotora, siendo su voluntad que en su caso sea designada su pareja Dña. [NOMBRE Y APELLIDOS], quien se encuentra en una situación de hecho asimilable a la conyugal y convive con mi representado, conforme a lo prevenido en los arts. 275 y 276 CCiv.

CUARTO.- De todo ello se desprende claramente que son improcedentes las medidas judiciales de apoyo solicitadas, al encontrarse mi representado en situación de plena capacidad para gobernar su persona y bienes por sí mismo, por lo que nos oponemos totalmente a la solicitud, de manera que, conforme a lo que dispone el art. 42 bis b).5 LJV, solicitamos que se ponga fin al expediente decretando su archivo, siendo improcedente la aplicación de cualquier medida provisional dada la plena capacidad de mi representado y la inexistencia de presupuestos para su adopción.

A los anteriores hechos de aplicación los siguientes

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA.

Nada que oponer a la competencia del Tribunal de Instancia al que me dirijo conforme a lo dispuesto en el art. 42 bis a).2 LJV, en relación con lo dispuesto en el art. 85.1º LOPJ.

II.- REQUISITOS DE LA OPOSICIÓN.

Se cumplen los requisitos para la oposición de los arts. 17.3 y 42 bis b).5 LJV, habiéndose formulado la oposición en tiempo y forma por el propio interesado, fundada en que mi representado tiene plena capacidad para gobernarse por sí mismo sin necesidad de medida de apoyo alguna.

III.- TRÁMITE

Al haberse formulado oposición es de aplicación lo dispuesto en el art. 42 bis b).5 LJV, debiendo acordarse el archivo del expediente, sin que sea procedente la adopción de medida provisional alguna.

IV.- EFECTOS

Dispone el art. 42 bis b).5 LJV que "la oposición de la persona con discapacidad a cualquier tipo de apoyo, la oposición del Ministerio Fiscal o la oposición de cualquiera de los interesados en la adopción de las medidas de apoyo solicitadas pondrá fin al expediente, sin perjuicio de que la autoridad judicial pueda adoptar provisionalmente las medidas de apoyo de aquella o de su patrimonio que considere convenientes. Dichas medidas podrán mantenerse por un plazo máximo de treinta días, siempre que con anterioridad no se haya presentado la correspondiente demanda de adopción de medidas de apoyo en juicio contencioso. No se considerará oposición a los efectos señalados en el párrafo anterior la relativa únicamente a la designación como curador de una persona concreta".

V.- FUNDAMENTOS JURÍDICO-MATERIALES.

Nuestro representado, pese a la carga que supone para sí mismo estar impedido en cama, es una persona con autonomía y pleno dominio de sus actos.

Pretende la hija demandante, que no se resigna a esperar resultar heredera, ser nombrada curadora del mismo, [NOTA DE REVISIÓN: Para mayores de edad no cabe tutela. Fuente: Código Civil (BOE-A-1889-4763) arts. 199 y 250, redacción Ley 8/2021 (BOE-A-2021-9233).] para [COMPLETAR], de esta manera, controlar el cuantioso patrimonio de su padre, mi representado. Pero silencia en su escrito de demanda que nuestro representado, aunque de avanzada edad, carece de cualquier déficit de conocimiento o voluntad, y no sólo detenta una vida económicamente desahogada, que le permite contar con servicio, incluida enfermera a tiempo completo, que le auxilia en su enfermedad degenerativa, como se ha indicado, sino que sigue llevando a cabo una tarea profesional bien remunerada desde casa, lo que le permite obtener cuantiosos ingresos, como hasta la aparición de dicha enfermedad hiciera, como intérprete traductor jurado de idioma árabe, utilizando los avances de la informática.

Siendo el objeto del expediente la provisión de apoyos a personas en situación de discapacidad sólo puede conducir a una resolución judicial que determine los actos para los que la persona con discapacidad requiera el apoyo, insusceptible de ser interpretada de una manera extensiva en la concurrencia o no de los requisitos necesarios para que una resolución de tal calibre se produzca.

Pretender, con la única base de unas ciertas limitaciones físicas, que concurren las exigencias necesarias para adoptar judicialmente la provisión de medidas de apoyo de una persona, es tanto como admitir que únicamente las personas sanas, físicamente íntegras y válidas, son dignas de ser consideradas capaces, lo que choca con los más elementales principios de nuestro ordenamiento y el art. 41 CE.

Se trata de una estrategia de la hija única de una persona viuda con pingüe patrimonio encaminada a hurtar los derechos básicos de nuestro patrocinado para [COMPLETAR], de esta manera, no depender de unos derechos legitimarios, y controlar los bienes de nuestro representado.

El régimen de apoyo formal es subsidiario del voluntario y se establece por la autoridad judicial en un procedimiento de provisión de apoyos, los cuales deben ser proporcionados a las necesidades de la persona que los precise, respetando siempre la máxima autonomía de ésta en el ejercicio de su capacidad jurídica y atendiendo en todo caso a su voluntad, deseos y preferencias.

El art. 268 CCiv configura así las medidas de apoyo de manera individualizada, las cuales se establecen principalmente a través de la institución de la curatela, definiéndose el alcance y extensión de la curatela de forma individualizada, de manera que es la autoridad judicial quien determina los actos para los que la persona requiere asistencia del curador en el ejercicio de su capacidad jurídica atendiendo a sus concretas necesidades de apoyo. Circunstancias que en modo alguno concurren en el presente caso, como ha quedado expuesto.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL

que por presentado este escrito, con sus documentos y copias de todo, así como con el resguardo acreditativo de haber dado traslado de copia al mandatario procesal de la contraparte, se tenga por formulada oposición al expediente instado por Dña. [NOMBRE Y APELLIDOS], y, en su virtud, acuerde el archivo del expediente sin más trámite.

Es justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

	Firma de Procurador/a
