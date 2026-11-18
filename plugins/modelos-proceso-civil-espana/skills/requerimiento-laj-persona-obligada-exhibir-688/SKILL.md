---
name: requerimiento-laj-persona-obligada-exhibir-688
description: "Redacta el escrito «Requerimiento del LAJ a la persona obligada a exhibir» (formulario 688 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Requerimiento del LAJ a la persona obligada a exhibir

> Formulario 0688 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…en nombre y representación de la entidad»; «…SL»; «…s Hechos y consideraciones jurídicas: 1ª»; «…o con número terminó con auto dictado el»; «…ales correspondiente a los ejercicios de»; «…y»; «…currida, deviniendo, por ello, firme. 2ª»; «…ales correspondiente a los ejercicios de»; «…y»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 116 de la Ley 15/2015
- art. 115.1 LJV
- art. 116 LJV
- art. 3.2 LJV
- art. 113.2 LJV

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

### Formulario 0688 · Requerimiento del LAJ a la persona obligada a exhibir

- Año del modelo: 2015
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 15 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito del solicitante para que se requiera por el Letrado de la Administración de Justicia a la persona obligada a la exhibición

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de la entidad [COMPLETAR] SL [COMPLETAR], según acredito mediante copia fehaciente de la escritura de poderes, que acompaño para su unión a los autos por copia testimoniada con devolución de aquélla, como mejor proceda en derecho comparezco y DIGO: (1)

Que por medio del presente escrito, y de conformidad con el art. 116 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), solicito requerimiento del Letrado de la Administración de Justicia en relación a D./Dña. [NOMBRE Y APELLIDOS]. Todo ello, en base a los siguientes

Hechos y consideraciones jurídicas:

1ª [COMPLETAR])

Que mi mandante planteó ante el Tribunal al cual tengo el honor de dirigirme expediente de jurisdicción voluntaria, en solicitud de exhibición de libros contables por parte de D./Dña. El expediente tramitado con número terminó con auto dictado el [COMPLETAR] en el cual se le ordenaba la presentación en el Tribunal, en el plazo de diez días, del soporte informático relativo al libro de inventario y cuentas anuales correspondiente a los ejercicios de [COMPLETAR] y [COMPLETAR]. Dicha resolución judicial no fue recurrida, deviniendo, por ello, firme.

2ª [COMPLETAR])

Que transcurrido el plazo ordenado para ello, donde ha cumplido con la orden dada, y no ha presentado ante el órgano judicial soporte informático alguno, incumpliendo el deber de colaboración exigido en el art. 115.1 LJV.

3º) En consecuencia, y en virtud de lo dispuesto en el art. 116 LJV, solicito que por el Letrado de la Administración de Justicia se proceda a requerir al citado comerciante para que aporte la documentación señalada, absteniéndose de reiterar el quebrantamiento, con apercibimiento de imposición de multa y de incurrir en un delito de desobediencia a la autoridad judicial. Y para el caso, de que persista en tal incumplimiento se impongan multas coercitivas en el importe que se estime conveniente, en atención a las circunstancias del hecho y los graves perjuicios que se puedan ocasionar a mi mandante.

Por todo lo expuesto, al amparo del art. 116 LJV,

SOLICITO AL TRIBUNAL

Que teniendo por presentado este escrito, se proceda por el Letrado de la Administración de Justicia a requerir a D./Dña. [NOMBRE Y APELLIDOS] para que aporte de manera inmediata soporte informático relativo al libro de inventario y cuentas anuales correspondiente a los ejercicios de [COMPLETAR] y [COMPLETAR], ordenado en auto dictado en fecha [FECHA], absteniéndose de reiterar el quebrantamiento, con apercibimiento de imposición de multa y de incurrir en un delito de desobediencia a la autoridad judicial. Y para el caso, de que persista en tal incumplimiento se impongan multas coercitivas en el importe que se estime conveniente, en atención a las circunstancias del hecho y los graves perjuicios que se puedan ocasionar a mi mandante.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 113.2 LJV exige de manera preceptiva la intervención de Abogado y Procurador para la solicitud en análisis.

========================================================================
