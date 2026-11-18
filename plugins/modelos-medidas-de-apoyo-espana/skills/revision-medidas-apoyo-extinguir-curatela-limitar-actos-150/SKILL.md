---
name: revision-medidas-apoyo-extinguir-curatela-limitar-actos-150
description: "Redacta el escrito «Revisión de medidas de apoyo: extinguir la curatela o limitar los actos asistidos» (formulario 150 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Revisión de medidas de apoyo: extinguir la curatela o limitar los actos asistidos

> Formulario 0150 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

- [ ] SEDE (2 veces)
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] Nº DE COLEGIADO
- [ ] COLEGIO
- [ ] FECHA (5 veces)
- [ ] Nº DE EXPEDIENTE
- [ ] LOCALIDAD
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…D»; «…rado de la Administración de Justicia de»; «…dictado en los autos»; «…numeración del juzgado de procedencia).]»; «…a D»; «… el centro de desintoxicación homologado»; «…resente. Se emitió informe por el Doctor»; «…exo. Por ser de justicia que solicito en»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (4)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 42 bis c) de la LJV
- art. 268 del CC
- art. 291 CC

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

### Formulario 0150 · Revisión de medidas de apoyo: extinguir la curatela o limitar los actos asistidos

- Año del modelo: 2021
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 25 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE COLEGIADO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D [COMPLETAR], Procurador de los Tribunales en nombre y representación de D. [NOMBRE Y APELLIDOS], tal y como acredito por apoderamiento apud-acta otorgado ante el Letrado de la Administración de Justicia de [COMPLETAR], bajo la dirección letrada del Letrado D. [NOMBRE Y APELLIDOS], colegiado núm. [Nº DE COLEGIADO] del Ilustre Colegio de Abogados de [COLEGIO] ante el Tribunal comparezco y como mejor proceda en Derecho, DIGO:

Que mediante en la representación que ostento, al amparo de lo dispuesto en el art. 42 bis c) de la Ley de Jurisdicción Voluntaria, promuevo EXPEDIENTE DE JURISDICCIÓN VOLUNTARIA para la REVISIÓN DE MEDIDAS JUDICIALES DE APOYO decretadas en el auto de fecha [FECHA] dictado en expediente de jurisdicción voluntaria número [Nº DE EXPEDIENTE], respecto de mi representado D/Dª [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], en base a los siguientes,

HECHOS

PRIMERO.- En virtud de auto firme de fecha [FECHA] dictado en los autos [COMPLETAR] seguidos ante la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] se declaró que D/Dª [NOMBRE Y APELLIDOS], padecía un enolismo de larga evolución, señalándose que la dependencia alcohólica había derivado en una psicosis paranoide toxicofílica acordándose la provisión de medidas judiciales de apoyo, constituyéndose la curatela y nombrándose curador [NOTA DE REVISIÓN (comprobar): Desde la Ley 8/2021 no se declara la «incapacidad»; la resolución provee apoyos. Fuente: Código Civil (BOE-A-1889-4763) arts. 250 y 269, redacción Ley 8/2021 (BOE-A-2021-9233).] a D [COMPLETAR], quien asumía facultades plenas de representación de la persona con discapacidad para todos los actos de gestión, administración y disposición de su patrimonio.

En el citado auto se fijaba un plazo de tres años para la revisión de las medidas.

(Acompaño como documento número [Nº DE DOCUMENTO] testimonio del auto con expresión de su firmeza).

SEGUNDO.- Desde la constitución de la curatela hasta la fecha de interposición de la presente solicitud las circunstancias concurrentes han variado ostensiblemente, de manera que aun no habiendo transcurrido el plazo de revisión de las medidas de apoyo, se está en el caso de solicitar su revisión conforme a lo establecido en el art. 268.III CC y en el art. 42 bis c), apartado 1, de la LJV.

En fecha [FECHA] mi representado ingresó en el centro de desintoxicación homologado [COMPLETAR] dependiente del Ministerio de Sanidad al objeto de iniciar el correspondiente tratamiento de desintoxicación. Dicho tratamiento que se ha prolongado durante año y medio ha sido en régimen cerrado con supervisión médica y psiquiátrica.

Mi representado ha seguido la totalidad del tratamiento con gran éxito encontrándose a fecha de la interposición de la presente solicitud totalmente desintoxicado. Se aporta como documento número [Nº DE DOCUMENTO] informe expedido por la dirección facultativa de dicho centro en que se certifica dicha afirmación.

TERCERO.- Por otro lado, teniendo en cuenta que la dependencia alcohólica había generado una psicosis paranoide toxicofílica, mi representado ha recabado informe del psiquiatra adscrito al centro de desintoxicación al efecto de que determine cuál es el estado de dicha afección al momento presente.

Se emitió informe por el Doctor [COMPLETAR], de fecha [FECHA], que se aporta como documento número [Nº DE DOCUMENTO], en virtud del cual se pone de manifiesto que «si bien el consumo de alcohol prolongado produce desarrollo de trastornos de tipo paranoide, fundamentalmente de tipo celotípicos que afectan muy gravemente a las facultades volitivas e intelectivas de quien las sufre, en el caso presente D/Dª [NOMBRE Y APELLIDOS], habiendo superado con notable éxito y tratamiento intensivo su adicción al alcohol no puede decirse que en la actualidad sufra trastorno paranoide de ninguna índole, siendo su diagnóstico psiquiátrico de absoluta normalidad».

CUARTO.- Atendido lo anterior, mi representado se encuentra en situación de gobernarse por sí mismo, sin necesidad de medidas de apoyo, por lo que se solicita la extinción de la curatela o, subsidiariamente, que el apoyo se limite estrictamente a lo que son actos de disposición patrimonial.

A los anteriores hechos les son de aplicación los siguientes,

FUNDAMENTOS DE DERECHO

PRIMERO.- COMPETENCIA. El art. 42 bis c), apartado 2, LJV establece que el Tribunal que dictó las medidas será también competente para conocer de la citada revisión, siempre que la persona con discapacidad permanezca residiendo en la misma circunscripción. En caso contrario, el Tribunal de la nueva residencia habrá de pedir un testimonio completo del expediente al Tribunal que anteriormente conoció del mismo, que lo remitirá en los diez días siguientes a la solicitud.

SEGUNDO.- PROCEDIMIENTO El procedimiento a seguir en el presente supuesto es el de jurisdicción voluntaria, regulado en el artículo 42 bis c) de la LJV, debiendo darse traslado a quien ejerza las funciones de apoyo, al Ministerio Fiscal y a los interesados personados en el expediente previo.

TERCERO.- LEGITIMACIÓN Está legitimado activamente el promotor del expediente conforme a lo establecido en el art. 42 bis c), apartado 1, cuando dispone: “cualquiera de las personas mencionadas en el apartado 3 del artículo 42 bis a), así como quien ejerza el apoyo, podrá solicitar la revisión de las medidas antes de que transcurra el plazo previsto en el auto”. Por su parte, el artículo 42 bis a), apartado 3, de la LJV:" Podrá promover este expediente el Ministerio Fiscal, la propia persona con discapacidad, su cónyuge no separado de hecho o legalmente o quien se encuentre en una situación de hecho asimilable y sus descendientes, ascendientes o hermanos”.

CUARTO.- REVISIÓN DE LAS MEDIDAS JUDICIALES DE APOYO. El art. 268 del CC establece que las medidas tomadas por la autoridad judicial en el procedimiento de provisión de apoyos serán proporcionadas a las necesidades de la persona que las precise, respetarán siempre la máxima autonomía de esta en el ejercicio de su capacidad jurídica y atenderán en todo caso a su voluntad, deseos y preferencias y que se revisarán, en todo caso, ante cualquier cambio en la situación de la persona que pueda requerir una modificación de dichas medidas. Por su parte, el art. 291 CC establece que la curatela se extingue por resolución judicial cuando ya no sea precisa esta medida de apoyo o cuando se adopte una forma de apoyo más adecuada para la persona sometida a curatela

Por lo expuesto,

SUPLICO AL TRIBUNAL que tenga por presentado este escrito con los documentos acompañados y sus copias, se inicie expediente de JURISDICCIÓN VOLUNTARIA DE REVISIÓN DE MEDIDAS JUDICIALES DE APOYO de mi representado D/Dª [NOMBRE Y APELLIDOS] y, tras los trámites legales una vez recabados los informes que V.I. estime oportunos, acuerde la revisión de las medidas decretadas en auto de fecha [FECHA], disponiendo la extinción de la curatela o, subsidiariamente, la limitación de los actos sujetos a asistencia del curador, junto a lo demás que en Derecho proceda.

OTROSÍ PRIMERO DIGO que se acompaña en anexo relación de documentos e informes presentados, debidamente foliados y con índice electrónico, para su debida localización y consulta.

SUPLICO AL TRIBUNAL tenga hecha esta manifestación a los efectos oportunos y por aportados los documentos e informe pericial relacionados en el anexo.

Por ser de justicia que solicito en [COMPLETAR]

Fdo. Abogado Fdo. Procurador
