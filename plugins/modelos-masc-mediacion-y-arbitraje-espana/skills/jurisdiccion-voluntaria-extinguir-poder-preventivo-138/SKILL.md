---
name: jurisdiccion-voluntaria-extinguir-poder-preventivo-138
description: "Redacta el escrito «Jurisdicción voluntaria para extinguir un poder preventivo» (formulario 138 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Jurisdicción voluntaria para extinguir un poder preventivo

> Formulario 0138 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD (2 veces)
- [ ] FECHA
- [ ] IMPORTE (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Procurador/a de los Tribunales y de Don»; «…s: 1º) Mi representado es hermano de Don»; «…, otorgó poder preventivo a favor de Don»; «…que se acompañan como documentos números»; «…al presente escrito. 2º) En el año»; «…ación de discapacidad del poderdante Don»; «…ntivo otorgado a favor de su hermano Don»; «…el mismo se expresaba la voluntad de Don»; «…ÓN DEL PODER PREVENTIVO OTORGADO POR DON»; «…, A FAVOR DEL APODERADO DON»; «…, con domicilio respectivamente en»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 258 y 278 CCiv
- art. 14.2 LJV
- art. 43.1 LJV
- art. 51 bis.1 LJV
- art. 43.3 LJV
- art. 3.2 LJV

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

### Formulario 0138 · Jurisdicción voluntaria para extinguir un poder preventivo

- Año del modelo: 2021
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 26 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de solicitud de expediente de extinción de poderes preventivos del art. 51 bis) LJV.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales y de Don [COMPLETAR], a quien asiste el Letrado/a en ejercicio D./Dña. [NOMBRE Y APELLIDOS], colegiado/a nº [Nº DE COLEGIADO/A] del Iltre. Colegio de Abogados de [COLEGIO], con despacho abierto en esta localidad, calle [CALLE], ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que por el presente escrito, en la representación que acredito y siguiendo instrucciones de mi mandante, al amparo de lo dispuesto en los art. 51 bis) LJV promuevo EXPEDIENTE DE JURISDICCIÓN VOLUNTARIA PARA LA EXTINCIÓN DEL PODER PREVENTIVO OTORGADO POR DON, A FAVOR DEL APODERADO DON con domicilio en [LOCALIDAD], por escritura pública de fecha [FECHA], y en base a los siguientes:

Hechos y consideraciones jurídicas:

1º) Mi representado es hermano de Don [COMPLETAR], quien en previsión de su futura falta de capacidad al estar afecto de una enfermedad degenerativa, otorgó poder preventivo a favor de Don [COMPLETAR], asimismo hermano del solicitante y de la persona con discapacidad, en previsión de precisar apoyo para el ejercicio de su capacidad jurídica, apoderándole de la forma más amplia para el cuidado de su persona y administración de sus bienes, como acredito mediante la aportación de certificado del Registro Civil y copia autorizada de la escritura pública de apoderamiento, que se acompañan como documentos números [COMPLETAR] al presente escrito.

2º) En el año [COMPLETAR], ante la situación de discapacidad del poderdante Don [COMPLETAR] que no le permitía valerse por sí mismo, según las previsiones del poder preventivo otorgado a favor de su hermano Don [COMPLETAR], éste debió pasar a residir con el apoderado, quien además se debía hacer cargo de la administración de sus bienes de acuerdo a la voluntad del poderdante expresada en el mencionado poder preventivo, puesto que en el mismo se expresaba la voluntad de Don [COMPLETAR] de convivir en el mismo domicilio con su hermano.

No obstante, desde el momento en que el apoderado se hizo cargo de la gestión del patrimonio de su hermano incumplió gravemente los deberes establecidos en el apoderamiento, puesto que en ningún momento ha existido dicha convivencia efectiva por la negativa del apoderado, siendo que el apoderado no es quien cuida de su hermano, sino que lo hace mi representado, con quien convive el poderdante junto a su familia y mantiene estrechos vínculos personales y afectivos, y el apoderado solo abona una pequeña cantidad de [IMPORTE] euros para la manutención de su hermano, con cargo a la cuenta del poderdante

3º) Esta situación ha desembocado en un grave conflicto personal y económico con el poderdante, que se ha visto agravado por la aplicación por el apoderado de cantidades recibidas del poderdante a usos propios, en cuantía aproximada de [IMPORTE] euros.

Por tanto, de conformidad a lo dispuesto en los arts. 258 y 278 CCiv y en razón a la falta de cumplimiento de las obligaciones para las que fue designado, y a la existencia de problemas de convivencia, graves y continuados, debe decretarse la extinción de los poderes preventivos otorgados en su día, que se solicita en este escrito.

4º) A los efectos del art. 14.2 LJV, debo hacer constar que, al margen del solicitante y del apoderado, los parientes más próximos del poderdante, que pueden estar interesados en el expediente, son sus otros dos hermanos, cuya testifical se propone por medio de otrosí.

5º) Que es competente la Sección Civil del Tribunal de Instancia al que me dirijo a tenor de lo previsto en el art. 43.1 LJV, por ser el del lugar de residencia de la persona con discapacidad.

6º) Que mi representado está legitimado activamente para promover el presente expediente, conforme a lo dispuesto en el art. 51 bis.1 LJV, por ser hermano del poderdante y persona que está cuidando del mismo de forma continuada.

7º) Que conforme a lo dispuesto en el art. 43.3 LJV la solicitud está firmada por abogado, por ser preceptiva su intervención en el caso de autos.

Esta parte actúa representada por Procurador, pese a que su intervención no es preceptiva en el caso de autos, por permitirlo así el art. 3.2 LJV.

8º) Que la presente solicitud deberá ser tramitada por las normas establecidas para la jurisdicción voluntaria en el art. 51 bis).2 LJV, conforme al que, admitida la solicitud, se citará a la comparecencia al solicitante, al apoderado, a la persona con discapacidad que precise apoyo y al Ministerio Fiscal. Si se suscitare oposición, el expediente se hará contencioso y el letrado de la Administración de Justicia citará a los interesados a una vista, continuando la tramitación con arreglo a lo previsto en el juicio verbal.

9º) Que el testimonio de la resolución firme dictada en el presente procedimiento deberá remitirse al Registro Civil para que se practique su inscripción, conforme al art. 4.11º LRC.

10º) Que el art. 258 IV CCiv establece que "Cualquier persona legitimada para instar el procedimiento de provisión de apoyos y el curador, si lo hubiere, podrán solicitar judicialmente la extinción de los poderes preventivos, si en el apoderado concurre alguna de las causas previstas para la remoción del curador, salvo que el poderdante hubiera previsto otra cosa", en tanto que el art. 278 del mismo texto legal establece que "serán removidos de la curatela los que, después del nombramiento, incurran en una causa legal de inhabilidad, o se conduzcan mal en su desempeño por incumplimiento de los deberes propios del cargo, por notoria ineptitud de su ejercicio o cuando, en su caso, surgieran problemas de convivencia graves y continuados con la persona a la que prestan apoyo"; circunstancias que concurren en el presente caso, lo que determina la procedencia de las pretensiones sostenidas en esta solicitud.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL:

que teniendo por presentado este escrito con los documentos y copias que se acompañan, se inicie EXPEDIENTE DE JURISDICCIÓN VOLUNTARIA PARA LA EXTINCIÓN DEL PODER PREVENTIVO OTORGADO POR DON [COMPLETAR], A FAVOR DEL APODERADO DON [COMPLETAR], y practicadas las diligencias oportunas con intervención del Ministerio Fiscal, y previos los demás trámites con arreglo a Derecho dicte resolución en la que se acuerde la extinción de los poderes preventivos otorgados a favor del apoderado D/Dª [NOMBRE Y APELLIDOS], acordando remitir la correspondiente comunicación al Registro Civil de [LOCALIDAD].

OTROSI PRIMERO DIGO:

que se acompaña en anexo relación de documentos presentados, debidamente foliados y con índice electrónico, para su debida localización y consulta.

Por lo que,

SUPLICO AL TRIBUNAL tenga hecha esta manifestación a los efectos oportunos y por aportados los documentos relacionados en el anexo.

OTROSI SEGUNDO DIGO:

que sin perjuicio de la preceptiva entrevista al poderdante, así como al apoderado, de conformidad a lo dispuesto en el art. 51 bis).2 LJV, PROPONGO la siguiente PRUEBA para su práctica en la comparecencia:

— DOCUMENTAL, de los documentos acompañados a esta demanda relacionados en el anexo.
TESTIFICAL de D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS], con domicilio respectivamente en [COMPLETAR], hermanos de mi representado y de la persona con discapacidad, cuidando el solicitante de la comparecencia voluntaria de los testigos. el día y hora que se señale para la comparecencia (o, en su caso, solicitando que sean citados judicialmente para la práctica de la diligencia).

Por lo que nuevamente,

SUPLICO AL TRIBUNAL tenga por propuesta la prueba, admitiéndola y acordando su práctica.

Es justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

	Firma de Procurador/a
