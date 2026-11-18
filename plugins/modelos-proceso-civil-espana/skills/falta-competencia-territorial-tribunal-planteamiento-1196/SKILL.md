---
name: falta-competencia-territorial-tribunal-planteamiento-1196
description: "Redacta el escrito «Falta de competencia territorial del Tribunal: planteamiento» (formulario 1196 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Falta de competencia territorial del Tribunal: planteamiento

> Formulario 1196 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Argumentación construida sobre «incapaz/incapacitado» y la LEC de 1881: actualizar a la persona con discapacidad y al fuero del art. 52.1.5.º LEC y del art. 62.1 LJV.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] FECHA (4 veces)
- [ ] LUGAR
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…tado en autos de jurisdicción voluntaria»; «…fue trasladada al Centro de Salud de»; «…, en la localidad de»; «…a fecha de hoy en el partido judicial de»; «…y sí en el de»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 411 LEC
- art. 24.1 CE
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

### Formulario 1196 · Falta de competencia territorial del Tribunal: planteamiento

- Año del modelo: 2014
- Revisión 17-11-2026: 8 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 15 campos de relleno marcados en blanco
- Avisos de la revisión: Argumentación construida sobre «incapaz/incapacitado» y la LEC de 1881: actualizar a la persona con discapacidad y al fuero del art. 52.1.5.º LEC y del art. 62.1 LJV.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, actuando en representación de D./Dña. [NOMBRE Y APELLIDOS], según tengo acreditado en autos de jurisdicción voluntaria [COMPLETAR], comparezco y como proceda en Derecho DIGO:

Que mediante el presente escrito pongo en conocimiento del Tribunal la pérdida de competencia territorial para seguir conociendo del procedimiento, de acuerdo a las siguientes:

ALEGACIONES

PRIMERA

El presente procedimiento en solicitud de autorización judicial para enajenación de bienes de D./Dña. [NOMBRE Y APELLIDOS], se inició con fecha [FECHA] a instancias de mi representado, habiéndose dictado en fecha [FECHA], auto autorizando la venta.

SEGUNDA

Con fecha [FECHA], D./Dña. [NOMBRE Y APELLIDOS] fue trasladada al Centro de Salud de [COMPLETAR], en la localidad de [COMPLETAR], para ser debidamente atendida, conforme consta en el informe médico que se acompaña a este escrito, fijando desde entonces su residencia con carácter permanente en dicha localidad.

TERCERA

El TS tiene declarado en diversas resoluciones que el cambio de residencia de la persona con discapacidad no determina la pérdida de competencia del Tribunal para seguir conociendo los incidentes posteriores que puedan suscitarse respecto de la persona con discapacidad, por lo que resulta aplicable el art. 411 LEC, en cuanto garantiza la perpetuación de la jurisdicción, en su versión de competencia, pero no es menos cierto que en sede de autorizaciones para la venta de bienes de menores o personas con discapacidad y en aplicación de la regla 23.ª del art. 63 LECiv 1881, vigente por aplicación de la Disposición Derogatoria Única 1-1.ª LEC, hasta la promulgación de la actual Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria, cuyo art. 62.1 recoge el contenido de la regla anterior, se ha tenido en cuenta la prevalencia del fuero de la localidad en que reside la persona con discapacidad, fuero correspondiente al lugar de su residencia que también es aplicable a los supuestos de representación y asistencia de las personas con discapacidad con medidas judiciales de apoyo (art. 52.1.5.º LEC), [NOTA DE REVISIÓN: El art. 52.1.5.º LEC vigente se refiere a las acciones relativas a medidas judiciales de apoyo; no hay ya incapacitados ni pródigos. Fuente: LEC 1/2000 (BOE-A-2000-323) art. 52.1.5.º (medidas judiciales de apoyo de personas con discapacidad) y Ley 15/2015 de la Jurisdicción Voluntaria (BOE-A-2015-7391) art. 62.1.] preceptos éstos últimos que excluirían la aplicación al presente procedimiento del principio de la "perpetuatio iurisdictionis" consagrado en el art. 411 LEC. Tal criterio competencial es más acorde al principio de protección de la persona con discapacidad en relación con razones de inmediación, eficacia y la efectividad de la tutela judicial exigida por el art. 24.1 CE, que será más efectiva bajo el control del Tribunal de su residencia, y además posibilita su acceso efectivo a la Justicia, de conformidad con el art. 13 de la Convención sobre los derechos de las personas con discapacidad, habiéndose producido, con el paso del tiempo, un cambio en las circunstancias que en su día llevaron a declarar la competencia funcional de este Tribunal, sin que deba darse al presente procedimiento una mayor dilación, pues parece claro que el interés de la persona con discapacidad está mejor protegido y el acceso a la justicia más adecuado a través de la Sección Civil del Tribunal de Instancia del domicilio en el que actualmente reside.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que tenga por presentado este escrito con los documentos que se acompañan, y previos los trámites legales, dicte auto declarando la falta de competencia territorial del Tribunal al que respetuosamente me dirijo para conocer de este procedimiento en solicitud de autorización judicial para enajenación de bienes de D./Dña. [NOMBRE Y APELLIDOS], por no residir ésta con carácter permanente a fecha de hoy en el partido judicial de [COMPLETAR] y sí en el de [COMPLETAR], remitiendo los autos en el estado en que se encuentran al Tribunal de Instancia de dicho partido judicial para su reparto a la plaza que por turno corresponda para el enjuiciamiento de este procedimiento.

Es justicia de hacerse en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

========================================================================
