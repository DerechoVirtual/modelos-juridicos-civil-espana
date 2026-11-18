---
name: contestacion-usuario-demanda-cesacion-actividades-1403
description: "Redacta el escrito «Contestación del usuario a demanda de cesación de actividades prohibidas» (formulario 1403 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación del usuario a demanda de cesación de actividades prohibidas

> Formulario 1403 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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
- [ ] Nº (3 veces)
- [ ] Nº DE DOCUMENTO
- [ ] NOMBRE Y APELLIDOS
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, presentamos informe del»; «…conocimiento de los vecinos, en Junta de»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Almacén / Actividad lícita / Continuación actividad / Representado — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Ausencia solicitud / Solicitud posterior a la apertura — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Propietario / Arrendatario — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 9.1 de la LPH
- artículo 394 de la LEC

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

### Formulario 1403 · Contestación del usuario a demanda de cesación de actividades prohibidas

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 3 bloques de opciones sin texto dejados en blanco con sus rótulos; 7 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio ordinario/

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [Nº]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

Que mediante el presente escrito procedo a contestar a la demanda en ejercicio de las acciones de cesación de actividad y reclamación de indemnización interpuesta por la Comunidad de Propietarios de la C/, n.º [Nº], en el sentido de oponerme a ella con base en los siguientes Propietarios:

HECHOS

 Acompañamos índice numerado de los documentos que se presentan con la contestación a la demanda.

Conforme con el correlativo respecto a la titularidad del inmueble.

 Igualmente es cierto que desde el inmueble se alquiló a mi representado, según se acredita mediante el contrato de arrendamiento que acompañamos como documento n.º [Nº DE DOCUMENTO].

No es cierto que se esté realizando actividad prohibida en.

[ELEGIR UNA OPCIÓN Y REDACTARLA: Almacén / Actividad lícita / Continuación actividad / Representado — el texto de cada opción no venía en el formulario original]

En cuanto a la inexistencia de licencias urbanísticas para el ejercicio de:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Ausencia solicitud / Solicitud posterior a la apertura — el texto de cada opción no venía en el formulario original]

Incierto el correlativo. Los estatutos de la Comunidad prohíben de modo genérico realizar actividades molestas. Mi representado se dedica a, actividad perfectamente legal y que puede llevarse a cabo sin menoscabo alguno del bienestar de los vecinos.

Como documento n.º [Nº], presentamos informe del [COMPLETAR], en el que se acredita que la instalación se ha montado con las debidas garantías y cumpliendo los requisitos necesarios. Igualmente manifiesta que se encuentra en buen estado de conservación y que su funcionamiento es correcto.

Cuando se requirió a mi representado por el Presidente de la Comunidad para que cesara en su actividad, D./Dña. [NOMBRE Y APELLIDOS] le recordó que cuando empezó a funcionar su negocio, hace ya, lo puso en conocimiento de los vecinos, en Junta de [COMPLETAR], y nadie puso objeción alguna.

Dejamos acotados los archivos de la Comunidad de Propietarios a efectos probatorios.

Por este motivo esta parte no ha realizado ninguna gestión, ya que se considera debidamente autorizado por los vecinos, y entiende que en estos momentos son problemas personales los que están llevando a la nueva dirección de la Comunidad a tomar esta decisión, a nuestro modo de ver errónea.

No es cierto que se haya causado daño a elementos comunes de la Comunidad. No existen ni siquiera las molestias que se alegan. El mismo informe ya citado explica respecto a este punto que es imposible que de un correcto funcionamiento del negocio de mi representado se deriven daños a terceros valorables económicamente.

Esta parte ha intentado convencer a los actores de que su pretensión es infundada, lo mismo que lo es su temor ante las instalaciones que existen en el interior del inmueble del demandado, pero también sus explicaciones han resultado infructuosas.

FUNDAMENTOS DE DERECHO

Nada que oponer a los fundamentos alegados de contrario.

Conforme con el correlativo y con la cuantía de la demanda.

Conforme con la legitimación formal, aunque negamos el fondo del asunto.

Esta parte también comparece representada por Procurador y asistida por Letrado por prescripción legal.

Con carácter general negamos todos los Fundamentos de Derecho alegados de contrario en lo que se opongan o contradigan nuestras pretensiones.

Primero.—

[ELEGIR UNA OPCIÓN Y REDACTARLA: Propietario / Arrendatario — el texto de cada opción no venía en el formulario original]

Segundo.— El artículo 9.1 de la LPH obliga al propietario a hacer un adecuado uso de las instalaciones generales y a mantener en buen estado de conservación el propio inmueble.

En el informe que se acompaña con esta contestación se acredita que se cumplen estos deberes.

Tercero.— El artículo 6, apartado a) del Real Decreto legislativo 7/2015, de 30 de octubre, por el que se aprueba el Texto Refundido de la Ley del Suelo y Ordenación Urbana, permite la realización de este tipo de actividades si se sujetan a la legislación vigente y se emplean en cada momento las mejoras técnicas disponibles según la normativa aplicable.

Cuarto.— El artículo 7.2 de la Ley de Propiedad Horizontal establece un derecho de indemnización a favor de la Comunidad cuando ésta se haya visto perjudicada. En este caso concreto se presenta por la demandante un informe de daños en bienes de titularidad de uno de los vecinos. Además de negar que la actividad de mi representado sea la causa directa de los desperfectos descritos, hemos de añadir que la Comunidad no se encuentra legitimada para reclamar indemnizaciones que en su caso corresponderían en exclusividad a un propietario.

Quinto.— La ordenanza municipal sobre permite la realización de esta actividad sin el otorgamiento de la licencia que exige la Comunidad.

En aplicación del artículo 394 de la LEC deberán imponerse al actor.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y copia de todo ello así como por evacuado el trámite de contestación a la demanda, lo admita y, previos los trámites legales oportunos, dicte en su día sentencia:

1.º Desestimando íntegramente las pretensiones de la actora.

2.º Absolviendo a esta parte de todos los pedimentos planteados por aquélla.

3.º Condenando en costas a la demandante.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

(Firma de Abogado y Procurador)

========================================================================
