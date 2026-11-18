---
name: demanda-art-158-cc-incumplimiento-regimen-visitas-312
description: "Redacta el escrito «Demanda del art. 158 CC por incumplimiento del régimen de visitas amparado en el estado de alarma» (formulario 312 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda del art. 158 CC por incumplimiento del régimen de visitas amparado en el estado de alarma

> Formulario 0312 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] Nº
- [ ] FECHA (4 veces)
- [ ] SEDE
- [ ] NÚMERO
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…QUE POR TURNO CORRESPONDA DE»; «…, domiciliada»; «…, a los Autos de»; «…us hijos: fines de semana alternos desde»; «… semana que a falta de acuerdo serán los»; «…demanda. Por ser de Justicia que pido en»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (4)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 51 de la LEC
- arts. 23 y 31 de la LEC
- art. 5.2 de la Ley Orgánica 1/2025
- artículo 158 del Código Civil
- artículos 92, 93 y 94 CC

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

### Formulario 0312 · Demanda del art. 158 CC por incumplimiento del régimen de visitas amparado en el estado de alarma

- Año del modelo: 2020
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 12 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 1 huecos del original que se habían perdido sin marca, marcados (FECHA)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

QUE POR TURNO CORRESPONDA

DE [COMPLETAR]

Que a medio del presente escrito y en la representación enunciada interpongo DEMANDA DE MEDIDA DEL ARTÍCULO 158 DEL CÓDIGO CIVIL contra Dª., provista de DNI núm. [Nº], domiciliada [COMPLETAR], sobre la base de los siguientes

Hechos

Primero.- Que con fecha [FECHA], a los Autos de [COMPLETAR] el Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO], dictó [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] Sentencia/Auto cuya parte dispositiva era del siguiente tenor literal:

“ 2..- La guarda y custodia del hijo/a menor de ambos, se atribuye a la madre. Si bien ambos progenitores tienen la patria potestad compartida…

3.-En defecto de acuerdo.. el padre de podrá estar con sus hijos: fines de semana alternos desde [COMPLETAR]. Los puentes se disfrutarán por aquel progenitor a quien corresponda el fin de semana respectivo.

Podrá estar con ellos también dos tardes entre semana que a falta de acuerdo serán los [COMPLETAR] desde la salida del colegio hasta las ….

Durante las vacaciones de semana santa, se distribuirán las mismas por mitad entre ambos progenitores.

La vacaciones escolares de navidad se distribuirán por mitad entre ambos en dos periodos: el primero abarcará desdel último día lectivo a la salida del colegio hasta el 30 de diciembre a las 20 horas; y el segundo desde la finalización del anterior hasta el día inmediatamente anterior al comienzo de las clases.

Y las vacaciones escolares de verano se distribuirán por mitad,

Aportamos como documento número 1 la.

Segundo Desde que se dictó la Resolución antes referida de fecha [FECHA], se ha venido cumpliendo el régimen de visitas sin problema, hasta el pasado día 16 de marzo en el que la progenitora custodia comunicó por whatsapp a nuestro mandante la siguiente decisión unilateral que transcribimos a continuación:

“Debido al estado de alarma decretado por el Gobierno de España, te comunico que se suspenden las visitas hasta que el Gobierno comunique la finalización del mismo ”.

Aportamos como documento número 2 la captura de pantalla con dicha comunicación.

Tercero Nuestro mandante remitió a la progenitora custodia un whatsapp en el que mostraba su disconformidad y le alegaba razones suficientes para entender que no existe ningún fundamento legal para proceder unilateralmente.

Aportamos como documento número 3 la captura de pantalla con dicha comunicación.

Cuarto Que habiendo intentando resolver este asunto sin que el resultado haya dado frutos, nos vemos abocados a solicitar el auxilio judicial

Fundamentos de Derecho

I.- Competencia.

Es competente este tribunal en virtud del artículo 51 de la LEC por ser el tribunal donde tiene su domicilio la demandada.

II.- Procedimiento y acción.

Este procedimiento de modificación se tramitará por las reglas del artículo 770 del mismo cuerpo legal.

III.- Legitimación:

Se encuentran legitimados activa y pasivamente las partes litigantes por su condición de progenitores de los hijos menores.

IV.- Postulación:

En virtud de lo dispuesto en los arts. 23 y 31 de la LEC el demandante comparece representado por procurador y asistido de letrado.

Resulta preceptiva la intervención del Ministerio Fiscal al haber intereses de unos menores.

V.- Cumplimiento de los requisitos de procedibilidad:

La presente demanda no está sujeta al previo intento de resolución de controversias en vía no jurisdiccional por tratarse de materias excluidas del requisito de procedibilidad de acuerdo con el art. 5.2 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VI.- Fondo del asunto:

Dispone el artículo 158 del Código Civil en la nueva redacción dada por la L.O. 8/2021 de 4 de junio, que “El juez de oficio, o a instancia del propio hijo, de cualquier pariente o del Ministerio Fiscal, dictará:

6.º La suspensión cautelar en el ejercicio de la patria potestad y/o en el ejercicio de la guarda y custodia, la suspensión cautelar del régimen de visitas y comunicaciones establecidos en resolución judicial o convenio judicialmente aprobado y, en general, las demás disposiciones que considere oportunas, a fin de apartar al menor de un peligro o de evitarle perjuicios en su entorno familiar o frente a terceras personas.

Ésta es una materia en la que es criterio primordial el del "favor filii" contenido en los artículos 92, 93 y 94 CC, [NOTA DE REVISIÓN: Redacciones vigentes: art. 92 por Ley 16/2022 (texto de la LO 8/2021); art. 93 por Ley 11/1990; art. 94 por Ley 8/2021. Fuente: Código Civil (BOE-A-1889-4763) arts. 92-94 (BOE consolidado).] que obliga a atemperar el contenido de la patria potestad en interés de los hijos, por ello los Tribunales deben tratar de indagar cuál es el verdadero interés del menor, aquello que le resultará más beneficioso, no sólo a corto plazo sino en el futuro, que le permita ver constantemente a su padre y a su madre, lo cual no es en absoluto incompatible con la atribución a uno solo de los progenitores de la guarda y custodia. De esta forma el menor puede disfrutar de ambos progenitores en la medida más parecida a la que fue anterior a la ruptura del matrimonio o de la pareja.

Que la tutela que se pretende de este es ejecutiva, de obligación de hacer, en el Tribunal es el de requerir a Dª.que proceda a dar inmediato, íntegro y estricto cumplimiento al régimen de visitas acordado en la/el Sentencia/Auto de [FECHA], con los apercibimientos legales, especialmente las del artículo 776.3º de la Ley de Enjuiciamiento Civil, así como se determine los días de visita a favor de mi mandante en concepto de compensación a la privación del derecho a las visitas.

Por todo lo cual,

AL TRIBUNAL SUPLICO tenga por presentado este escrito, sus documentos y copias. Lo admita y dé el trámite legal que corresponda. Tenga por interpuesta DEMANDA DEL ARTÍCULO 158 del Código Civil en nombre de D.contra Dª. Y tras los demás trámites, y previo el recibimiento del juicio a prueba, tenga a bien dictar Auto por la que se estime íntegramente la medida solicitada, y en concreto requerir a Dª.que proceda a dar inmediato, íntegro y estricto cumplimiento al régimen de visitas acordado en la/el Sentencia/Auto de [FECHA], con los apercibimientos legales, especialmente las del artículo 776.3º de la Ley de Enjuiciamiento Civil, así como se determine los días de visita a favor de mi mandante en concepto de compensación a la privación del derecho a las visitas.

Y todo ello con imposición de costas a la parte demandada en caso de que se oponga temerariamente a esta demanda. Por ser de Justicia que pido en [COMPLETAR]

Fdo. Ldo. Fdo. Procurador
