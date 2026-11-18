---
name: declaracion-ausencia-751
description: "Redacta el escrito «Declaración de ausencia» (formulario 751 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Declaración de ausencia

> Formulario 0751 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] LOCALIDAD
- [ ] CALLE (4 veces)
- [ ] NÚMERO
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ciones jurídicas: 1.ª) Que mi marido, D.»; «…más próximos de mi marido: su hermano D.»; «…, con domicilio en la calle [CALLE] de»; «…, con domicilio en la calle [CALLE] de»; «…rtido judicial el último domicilio de D.»; «…, sito en la calle [CALLE] de»; «… declarando legalmente la ausencia de D.»

## Elecciones que hay que hacer

- Firma del solicitante

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 70.1 LJV
- art. 70.2 LJV
- art. 71.1 LJV
- art. 70 LJV
- art. 68.1 LJV
- art. 182 del Código Civil
- art. 3.2 LJV
- art. 68.4 LJV
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

### Formulario 0751 · Declaración de ausencia

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 1 bloques de alternativas señalados; 24 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito por el que se promueve el expediente en solicitud de declaración de ausencia.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que por medio del presente escrito, y de conformidad con los arts. 67 y ss. de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud de declaración de ausencia, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que mi marido, D. [COMPLETAR], desapareció de su domicilio el pasado [FECHA] sin dejar rastro de su paradero, y sin haber dejado persona alguna encargada de sus asuntos. A pesar de la denuncia presentada ante el Cuerpo Nacional de Policía, y las diversas pesquisas llevadas a cabo en su búsqueda, no se ha podido obtener hasta la fecha noticia alguna de su persona, habiendo transcurrido más de año y medio desde la referida desaparición. Concurren, en consecuencia, los presupuestos legales previstos en el art. 183.1º del Código Civil para la declaración de ausencia, al exceder en más de un año las últimas noticias del ausente, sin que el mismo haya dejado apoderado con facultades de administración de sus bienes.

2.ª) Que en el momento de la desaparición D. [NOMBRE Y APELLIDOS] y yo estábamos casados en régimen de gananciales, y vivíamos junto a nuestras dos hijas Dña. y Dña. [NOMBRE Y APELLIDOS]. Me encuentro, por ello, legitimada para instar su declaración de ausencia, de conformidad con lo dispuesto en el art. 182.1º del Código Civil y el art. 70.1 LJV, al ser su cónyuge, y no encontrarnos separados legalmente.

3.ª) Que, concurriendo los presupuestos legales, es necesario legalizar la situación de ausencia de mi marido a través de los trámites legales previstos en el art. 70.2 LJV. Asimismo, procede, en virtud de lo ordenado por el art. 184.1º del Código Civil y el art. 71.1 LJV, mi nombramiento como su representante, con objeto de ocuparme de sus asuntos, mantener la pesquisa de su persona, la protección y administración de sus bienes y el cumplimiento de sus obligaciones. En este sentido, no existe motivo grave alguno que permita alterar el orden previsto en el primero de los preceptos legales citados, y que prima mi nombramiento al ser su esposa no separada en el momento de su desaparición.

4.ª) Que, en atención a lo preceptuado por el art. 70 LJV, se relacionan como parientes más próximos de mi marido: su hermano D. [COMPLETAR], con domicilio en la calle [CALLE] de [COMPLETAR], y su hermana Dña. [NOMBRE Y APELLIDOS], con domicilio en la calle [CALLE] de [COMPLETAR], y mis hijas mayores de edad Dña. y Dña. [NOMBRE Y APELLIDOS], quienes residen en mi mismo domicilio.

5.ª) Que es competente el Tribunal de Instancia al que me dirijo conforme al art. 68.1 LJV en relación con lo dispuesto en el art. 85.1º LOPJ, al encontrarse en su partido judicial el último domicilio de D. [COMPLETAR], sito en la calle [CALLE] de [COMPLETAR].

6.ª) Se acompañan a este escrito copia de la denuncia presentada ante el Cuerpo Nacional de Policía, copia del libro de familia y certificados de nacimiento de mis hijas.

Por todo lo expuesto, al amparo del art. 182 del Código Civil, y de los arts. 67 y ss. LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria; se admita a trámite por el Letrado de la Administración de Justicia la solicitud y se fije hora para la comparecencia prevista en el art. 70.2 LJV; se publique tal resolución dos veces, mediante edictos, con intervalo mínimo de ocho días, en la forma establecida en la Ley de Enjuiciamiento Civil en el Boletín Oficial del Estado y en el tablón de anuncios del ayuntamiento de Madrid haciendo constar que cualquier interesado pueda intervenir en la comparecencia; se cite para la misma al Ministerio Fiscal, a los testigos propuestos y a quien se considere interesado; y, previa las medidas de averiguación, investigación, y protección que se estimen procedentes; se dicte decreto por el Letrado de la Administración de Justicia declarando legalmente la ausencia de D. [COMPLETAR], nombrándome como representante, a quien le corresponderá la pesquisa de la persona del ausente, la protección y administración de sus bienes y el cumplimiento de sus obligaciones.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

[ELEGIR: Firma del solicitante]

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 68.4 LJV, no exige requisito alguno de postulación.

========================================================================
