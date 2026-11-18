---
name: impugnacion-acuerdo-junta-lesivo-perjudicial-1289
description: "Redacta el escrito «Impugnación de acuerdo de junta lesivo o perjudicial» (formulario 1289 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Impugnación de acuerdo de junta lesivo o perjudicial

> Formulario 1289 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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
- [ ] Nº (5 veces)
- [ ] FECHA (2 veces)
- [ ] HORA (2 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] IMPORTE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Acompaño también informe técnico del»; «… que tal medida resulta perjudicial para»; «…nario. La cuantía de este pleito se fija»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Lesivo para la comunidad / Perjuicio particular — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Elementos comunes / Propiedad — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Servidumbres / Respetar las instalaciones — el texto de cada opción no venía en el formulario original

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 85 de la LOPJ
- artículo 10 de la LEC
- artículos 23 y 31 de la LEC
- artículo 18 de la LPH
- artículo 18.4 de la LPH
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

### Formulario 1289 · Impugnación de acuerdo de junta lesivo o perjudicial

- Año del modelo: 2013
- Revisión 17-11-2026: 3 bloques de opciones sin texto dejados en blanco con sus rótulos; 11 campos de relleno marcados en blanco; 8 huecos del original que se habían perdido sin marca, marcados (FECHA, HORA, IMPORTE, NOMBRE Y APELLIDOS, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Impugnación de acuerdo de Junta de Propietarios

Demanda. Juicio ordinario

AL SERVICIO COMÚN DE REGISTRO Y REPARTO DEL TRIBUNAL DE INSTANCIA DE [SEDE]

Que mediante el presente escrito ejercito acción de impugnación del acuerdo de fecha de la Junta de Propietarios de la C/, n.º [Nº] de esta ciudad por su carácter que se tramitará por el cauce del juicio declarativo ordinario contra la Comunidad de Propietarios de la C/, n.º [Nº] de esta ciudad con base en los siguientes

HECHOS

 Acompañamos índice numerado de los documentos que se presentan como prueba con la demanda.

El Presidente de la Comunidad de Propietarios convocó a Junta a celebrar en el día [FECHA] a las [HORA] horas en primera convocatoria y a las [HORA] horas en segunda convocatoria.

A tal reunión fueron debidamente convocados los vecinos mediante.

Acompaño copia de la citación como documento n.º [Nº DE DOCUMENTO].

El orden del día que se acordó era el siguiente.

Cuando se pasó a discutir el punto n.º relativo a hubo una larga polémica sobre la necesidad o no para la Comunidad de lo que se proponía.

Los que estaban a favor mantenían que, mientras que los que se oponían consideraban que.

Finalmente se procedió a la votación siendo el resultado de votos a favor y votos en contra.

Adjunto como documento n.º copia del acta de la reunión.

Esta parte considera que el acuerdo adoptado resulta:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Lesivo para la comunidad / Perjuicio particular — el texto de cada opción no venía en el formulario original]

Tal como se puede apreciar con el plano del edificio que presentamos como documento n.º [Nº], tal instalación tiene cabida en zonas comunes sin tener que limitar el disfrute de la propiedad de D./Dña. [NOMBRE Y APELLIDOS]

Acompaño también informe técnico del [COMPLETAR], D./Dña. [NOMBRE Y APELLIDOS] en el mismo sentido:.

El actor es propietario de la vivienda que habita, según acredito mediante nota simple del Registro de la Propiedad que acompaño como documento n.º [Nº], y se encuentra al corriente del pago de las cuotas de la Comunidad, según justifico con copia de los recibos de pago de las últimas mensualidades, documentos n.º [Nº DE DOCUMENTO].

En la reunión de los vecinos a que nos hemos referido, mi representado votó en contra de la adopción de ese acuerdo, tal como se plasmó en el acta que acompaño.

Al seguir convencido de que tal medida resulta perjudicial para [COMPLETAR], nos vemos obligados a acudir a esta vía para solventar la cuestión.

El presupuesto presentado por el Presidente en la Junta de Propietarios donde se discutió valoró ésta en [IMPORTE] euros, cifra que damos por válida y que tenemos en cuenta para determinar la cuantía del procedimiento.

FUNDAMENTOS DE DERECHO

Los artículos 21 y 22 de la Ley Orgánica del Poder Judicial (LOPJ) y 36 de la Ley de Enjuiciamiento Civil (LEC) atribuyen con carácter general a la jurisdicción española y al orden civil el conocimiento de esta materia. Los artículos 85 de la LOPJ y 45 de la LEC designan a los Tribunales de Instancia como los órganos que específicamente resolverán estos pleitos. Finalmente el artículo 52.1.8.º de la LEC dice que en los juicios en materia de propiedad horizontal será competente el Tribunal del lugar en que radique la finca.

El artículo 249.1.8.º de la LEC remite la tramitación de estos pleitos al cauce del juicio ordinario.

La cuantía de este pleito se fija [COMPLETAR].

El artículo 10 de la LEC legitima para comparecer y actuar en juicio a los titulares de la relación jurídica o del objeto litigioso. La propia LPH faculta al propietario para impugnar los acuerdos de la Comunidad que resulten lesivos o perjudiciales.

En aplicación de los artículos 23 y 31 de la LEC las partes deberán comparecer representadas por Procurador y asistidas por Letrado.

La presente demanda no está sujeta al previo intento de resolución de controversias en vía no jurisdiccional, por tratarse de la impugnación judicial de un acuerdo de la comunidad de propietarios, habiendo determinado la doctrina de apelación que la propia junta equivale a una actividad negociadora y no son exigibles los MASC de la LO 1/2025 para la Ley de Propiedad Horizontal.

[ELEGIR UNA OPCIÓN Y REDACTARLA: Elementos comunes / Propiedad — el texto de cada opción no venía en el formulario original]

Segundo.— El artículo 18 de la LPH permite impugnar los acuerdos.

Tercero.— Según exige el n.º 2 del artículo 18 de la LPH esta parte.

Cuarto.— La acción caduca a los tres meses desde la adopción del acuerdo, artículo 18.4 de la LPH.

Quinto.— El artículo 9.º de la LPH regula las obligaciones de los propietarios entre las cuales se encuentra la de:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Servidumbres / Respetar las instalaciones — el texto de cada opción no venía en el formulario original]

En aplicación del artículo 394 de la LEC deberán imponerse al demandado.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño se admita a trámite por el Letrado de la Administración de Justicia mediante el oportuno decreto teniendo por interpuesta demanda de juicio declarativo ordinario contra la Comunidad de Propietarios de la C/, n.º [Nº], a fin de que en su día y, previos los trámites oportunos, se dicte sentencia mediante la que se deje sin efecto el acuerdo de la Junta de Propietarios de fecha [FECHA] por el que se acordó al declararlo, todo ello con expresa imposición de costas al demandado.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado y Procurador

========================================================================
