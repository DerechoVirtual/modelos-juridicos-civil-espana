---
name: contestacion-demanda-vicios-constructivos-531
description: "Redacta el escrito «Contestación a la demanda por vicios constructivos» (formulario 531 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a la demanda por vicios constructivos

> Formulario 0531 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] Nº DE DOCUMENTO
- [ ] LOCALIDAD (2 veces)
- [ ] NÚMERO (3 veces)
- [ ] COLEGIO
- [ ] FECHA (5 veces)
- [ ] Nº (2 veces)
- [ ] ÓRGANO O PERSONA
- [ ] LUGAR (2 veces)
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… contra por la Comunidad de Propietarios»; «…, desarrollada entre los meses de»; «…y»; «…de mi representado aparecieron en el año»; «…e recepción de las obras contratadas, el»; «…l certificado de fin de obra se firma en»

## Elecciones que hay que hacer

- Procurador/a / Procurador/a a
- Doña / la mercantil
- DNI / CIF
- Letrado / de la Letrada

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 248 y 249.2 LEC
- art. 17.6 de la Ley 38/1999
- art. 394 LEC
- arts. 335 y 336.1 LEC
- art. 337.2 LEC

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

### Formulario 0531 · Contestación a la demanda por vicios constructivos

- Año del modelo: 2016
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 4 desplegables convertidos en elección en blanco; 28 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Contestación a demanda de juicio ordinario sobre responsabilidad por vicios constructivos formulada por el constructor.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], [ELEGIR: Procurador/a / Procurador/a a] de los Tribunales, que actúa en nombre y representación de [NOMBRE DEL REPRESENTADO/A]
D./Dña. [ELEGIR: Doña / la mercantil], con [ELEGIR: DNI / CIF], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], bajo dirección del [ELEGIR: Letrado / de la Letrada] D./Dña. [NOMBRE Y APELLIDOS], con despacho profesional abierto en [LOCALIDAD], y colegiado n.º [NÚMERO] del Iltre. Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco y como mejor proceda en Derecho, DIGO:

Que en nombre de mi mandante vengo a personarme y CONTESTAR a la demanda de juicio declarativo ordinario, seguido ante ese Tribunal bajo el número [NÚMERO], interpuesta en mi contra por la Comunidad de Propietarios [COMPLETAR], tomando como base los siguientes:

HECHOS

PRELIMINAR.-

Con carácter previo esta parte se opone a todos cuantos hechos aducidos en la demanda a la que se contesta no sean expresamente reconocidos en los ordinales siguientes.

PRIMERO.- Efectivamente, mi mandante intervino, como constructor, en la construcción del edificio sito en [LOCALIDAD], desarrollada entre los meses de [COMPLETAR] y [COMPLETAR], habiendo concluido las obras con fecha [FECHA].

SEGUNDO.- Igualmente conformes con el contenido del correlativo de la demanda.

TERCERO.- Disconformes con el correlativo. Se niega que la construcción de dicha edificación fuera defectuosa, la misma se efectuó correctamente, ajustándose al proyecto e instrucciones del Arquitecto director, sin que quepa responsabilizar a mi mandante del deterioro de la cubierta del edificio; más al contrario, sólo hay un defecto de mantenimiento, que no debe acarrear condena alguna a esta parte.

CUARTO.- Incierto. El mal estado de la cubierta se debe exclusivamente a no haberse llevado a cabo durante años las operaciones de conservación y mantenimiento ordinarias, por lo que no estaríamos ante vicios constructivos sino ante falta de mantenimiento.

QUINTO a SÉPTIMO.-

Absolutamente incierto. El demandante alega en su escrito que los vicios constructivos por los que se reclama la responsabilidad de mi representado aparecieron en el año [COMPLETAR]. Sin embargo, según se desprende del relato fáctico de la propia demanda, no consta ninguna Junta de la Comunidad aludiendo al problema hasta el acta de fecha [FECHA], cuando el fin de la obra había acontecido en fecha [FECHA], y en consecuencia, el plazo de garantía con respecto a mi mandante había transcurrido.

Es en ese momento cuando la Comunidad de Propietarios solicita el dictamen que se acompaña al escrito de demanda y reclama a los codemandados.

Lógicamente el informe pericial resulta teórico y genérico, sin detallar y menos cuantificar las distintas y posibles responsabilidades, y con absoluta falta de verdad, puesto que el facultativo que lo elabora toma en consideración el estado actual de la cubierta, cuando han transcurrido más de [Nº] años de la finalización de las obras en que intervino mi mandante.

De ahí que se impugne expresamente el dictamen pericial emitido por [ÓRGANO O PERSONA], que se documenta y acompaña con la demanda, presentándose por esta parte, dictamen del Arquitecto D./Dña. [NOMBRE Y APELLIDOS], como documento n.º [NÚMERO].

A los anteriores hechos les son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA Y PROCEDIMIENTO.

Esta parte reconoce y hace suyos la totalidad de los razonamientos y fundamentos legales invocados de contrario, en punto a la competencia, objetiva y territorial, el procedimiento adecuado para la tramitación de esta litis que, en atención a la cantidad reclamada, no puede ser otro que el juicio declarativo ordinario, de conformidad con lo establecido en los arts. 248 y 249.2 LEC.

II.- LEGITIMACIÓN ACTIVA Y PASIVA.

A los puros efectos formales, de acuerdo con la legitimación de la parte actora, a la hora de ejercitar una acción como la que aquí se plantea, concurriendo la previa autorización de la junta de propietarios. Asimismo, se acepta, a los mismos efectos formales, la legitimación pasiva de mi cliente, como interviniente en el proceso de edificación en calidad de constructor. Y ello, sin perjuicio de oponernos de manera frontal a la demanda, y negar tajantemente los hechos aducidos en la demanda.

III.- FONDO DEL ASUNTO

a) Caducidad de acción

Conforme al art. 17.6 de la Ley 38/1999, de 5 de noviembre, de Ordenación de la Edificación (en adelante LOE), el constructor responderá directamente de los daños materiales causados en el edificio por vicios o defectos derivados de la impericia, falta de capacidad profesional o técnica, negligencia o incumplimiento de las obligaciones atribuidas al jefe de obra y demás personas físicas o jurídicas que de él dependan.

Dicha Ley, en cuanto a la responsabilidad de los agentes intervinientes en el proceso constructivo, entre los que se encuentra el constructor, diferencia entre los plazos de garantía, en el art. 17, y los de prescripción, en el art. 18, debiendo entenderse los primeros como de caducidad, no así los segundos, que por tanto serán susceptibles de interrupción.

Conforme al art. 17.1 LOE los plazos de garantía son de diez, tres y un año a partir de la recepción de la obra sin reservas, o de su subsanación, en función del tenor de los defectos, si afectan a elementos estructurales, a la habitabilidad o simples remates.

Conforme al art. 18 LOE las acciones para exigir la responsabilidad prevista en el artículo anterior por daños materiales dimanantes de los vicios o defectos, prescribirán en el plazo de dos años a contar desde que se produzcan dichos daños.

Pues bien, en cualquier caso, en el caso enjuiciado, habiéndose suscrito el acta de recepción de las obras contratadas, el [COMPLETAR], sea cual fuere el origen del defecto, cuando se reclamó lo cierto es que habría transcurrido el plazo de garantía con respecto a la constructora, de ahí su exoneración.

b) Falta de presupuesto normativo

Ejercitada frente a mi representado acción de responsabilidad por vicios constructivos, de naturaleza legal, que actualmente está conformada por el régimen de la LOE, aun si se estimara que la acción no está caducada, por transcurso del plazo de garantía del art. 17 LOE, subsidiariamente, en ningún caso daría lugar a responsabilidad de mi mandante, por falta de presupuesto normativo, pues el deterioro producido en el edificio, que es lo que realmente se ha producido, no es imputable a mi mandante, que en la construcción del edificio actuó con la más absoluta diligencia ajustándose en todo caso al proyecto redactado, sino a la falta de diligencia, como ya se ha puesto de manifiesto, en la conservación y mantenimiento del mismo.

Del simple examen de las fotografías que se incorporan al informe del perito Sr./a. se aprecia que las mismas son simples humedades en zonas concretas; y ello en un edificio en el que el certificado de fin de obra se firma en [COMPLETAR]. En todo este tiempo, la persistencia de las humedades hubieran hecho a las viviendas inhabitables (olor, moho, sensación persistente de humedad), y ello no se denuncia como ocurrido. Tampoco se habla de una situación permanente, por lo que debe predicarse su ocasionalidad, como lo prueba el hecho de que dos de las viviendas se hayan pintado y no conste de nuevo la existencia del defecto. De ser cierta la situación permanente de la "mala solución constructiva" o de "defectuosa colocación de las tejas" desde un principio, [Nº] años más tarde, la situación sería totalmente insostenible y no se habría esperado tantos años para presentar la demanda, que se habría intentado con absoluta premura e inmediación por las razones de inhabitabilidad expresadas. Nos encontramos, en definitiva, con una falta de mantenimiento, o que el mismo se hubiera realizado en forma no adecuada por la propiedad. No consta y no se prueba más allá de las manifestaciones del perito de la parte actora, que se haya efectuado algún tipo de mantenimiento, o que el mismo, de existir, haya sido eficaz. La habilidad y carga probatoria le corresponde, al respecto, a la parte actora, y su defecto de prueba le perjudica; y lo es más allá de la responsabilidad que se imputa del arquitecto superior, sino que al tratarse de defecto de mantenimiento, también beneficia al constructor. No se trata, por tanto, de un vicio ruinógeno, en sentido amplio o estricto, del que se generaría responsabilidad para el técnico, sino de unos perjuicios que se producen por falta de mantenimiento del edificio, que no es imputable a los codemandados.

IV.- COSTAS.

Las costas de la primera instancia deberán imponerse a la parte cuyas pretensiones resultaran totalmente desestimadas, es decir, a la actora si, como esta parte espera, la sentencia que, en su día, se dicte, resultara íntegramente absolutoria con plena desestimación de la acción ejercitada de contrario; todo ello, de conformidad con lo establecido en el art. 394 LEC.

En su virtud,

SUPLICO AL TRIBUNAL:

Que teniendo por recibido este escrito se sirva admitirlo y por él se tenga por contestada la demanda y, seguido que sea el procedimiento por sus trámites, se venga en su día a dictar sentencia que, con íntegra desestimación de dicha demanda:

1.- Absuelva en la instancia al actor de cuantos pedimentos se contienen en el escrito de demanda, por estar caducada la acción ejercitada, o
2.- En su caso, se absuelva libremente al actor por inexistente la responsabilidad que se postula frente al mismo.
3.- Todo ello con expresa imposición de las costas de este pleito a la parte actora.

Es justicia que pido en [LUGAR], a [FECHA].

OTROSÍ DIGO: Que conforme a los arts. 335 y 336.1 LEC aporto con este escrito de contestación DICTAMEN PERICIAL emitido por el Arquitecto D./Dña. [NOMBRE Y APELLIDOS]. De acuerdo con lo dispuesto en el art. 337.2 LEC, el perito deberá comparecer en el acto del juicio oral al objeto de ratificar el informe, exponer y explicar el dictamen que acompaño, así como responder a las preguntas que esta parte le pueda formular en el acto de Juicio Oral.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por hechas las afirmaciones anteriores, tenga por acompañado DICTAMEN PERICIAL, por anunciada la proposición de prueba PERICIAL del Técnico, D./Dña. [NOMBRE Y APELLIDOS], y cite al mismo al acto del juicio oral a los efectos previstos en el art. 337.2 LEC.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado	Firma del Procurador/a

========================================================================
