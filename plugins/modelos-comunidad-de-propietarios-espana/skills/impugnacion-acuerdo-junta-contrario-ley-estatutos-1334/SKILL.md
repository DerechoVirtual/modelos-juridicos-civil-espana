---
name: impugnacion-acuerdo-junta-contrario-ley-estatutos-1334
description: "Redacta el escrito «Impugnación de acuerdo de junta contrario a la ley o a los estatutos» (formulario 1334 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Impugnación de acuerdo de junta contrario a la ley o a los estatutos

> Formulario 1334 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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
- [ ] Nº (4 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] FECHA (2 veces)
- [ ] HORA (2 veces)
- [ ] IMPORTE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ustifica con los recibos de los meses de»; «…a Ley de Propiedad Horizontal. Primero.—»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Contrario a estatutos / Contrario a la ley — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Elementos comunes / Propiedad privada — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Servidumbre / Instalaciones generales — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 85 de la LOPJ
- artículo 10 de la LEC
- artículos 23 y 31 de la LEC
- artículo 18 de la LPH
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

### Formulario 1334 · Impugnación de acuerdo de junta contrario a la ley o a los estatutos

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 3 bloques de opciones sin texto dejados en blanco con sus rótulos; 9 campos de relleno marcados en blanco; 7 huecos del original que se habían perdido sin marca, marcados (FECHA, HORA, IMPORTE, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Impugnación de acuerdo de Junta de Propietarios

Demanda. Juicio ordinario

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: No existe «Tribunal de Instancia Decano» (DT 3.ª LO 1/2025). Si el asunto es de familia, Sección de Familia, Infancia y Capacidad; en partidos sin Sección Civil separada, Sección Única, de Civil y de Instrucción. Fuente: LO 1/2025 DT 3.ª (los jueces decanos pasan a la Presidencia del TI) y LOPJ arts. 84.1, 84.3 y 166 (BOE-A-2025-76).]

Que mediante el presente escrito ejercito acción de impugnación del acuerdo de fecha de la Junta de Propietarios de la C/, n.º [Nº] de esta ciudad al resultar contrario a, que se tramitará por el cauce del juicio declarativo ordinario frente a la Comunidad de Propietarios de la C/, n.º [Nº] de esta ciudad con base en los siguientes

HECHOS

 Acompañamos índice numerado de los documentos que se presentan como prueba con la demanda.

D./Dña. [NOMBRE Y APELLIDOS] es propietario del piso sito en la C/ n.º [Nº] de esta ciudad, según acredito mediante escritura pública que acompaño como documento n.º [Nº DE DOCUMENTO].

Se encuentra al corriente del pago de las cuotas de Comunidad, tal como se justifica con los recibos de los meses de [COMPLETAR], que adjuntamos a este escrito como documentos n.º [Nº DE DOCUMENTO].

Al parecer, el Presidente de la Comunidad de Propietarios convocó a Junta a celebrar en el día [FECHA] a las [HORA] horas en primera convocatoria y a las [HORA] horas en segunda convocatoria.

De esta convocatoria no tuvo conocimiento mi representado por residir fuera de este inmueble y no haber sido citado en persona para acudir a ella.

El orden del día que se acordó era el siguiente.

Días más tarde un vecino comentó a D./Dña. [NOMBRE Y APELLIDOS] el acuerdo al que se había llegado. Dicho acuerdo no había sido comunicado a mi poderdante.

Por este motivo solicitó al Presidente que le diera una copia del acta de aquella reunión.

Acompaño como documentos n.º copia de la solicitud y del acta.

Esta parte considera que el acuerdo adoptado resulta:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Contrario a estatutos / Contrario a la ley — el texto de cada opción no venía en el formulario original]

Tales irregularidades suponen una vulneración de las normas estatutarias y legales, pero además hay que tener en cuenta que el acuerdo que se adopta también vulnera la normativa vigente sobre porque.

El presupuesto presentado por el Presidente en la Junta de Vecinos donde se discutió se valoró en [IMPORTE] euros, cifra que damos por válida y que tenemos en cuenta para determinar la cuantía del procedimiento.

FUNDAMENTOS DE DERECHO

Los artículos 21 y 22 de la Ley Orgánica del Poder Judicial (LOPJ) y 36 de la Ley de Enjuiciamiento Civil (LEC) atribuyen con carácter general a la jurisdicción española y al orden civil el conocimiento de esta materia. Los artículos 85 de la LOPJ y 45 de la LEC designan a los Tribunales de Instancia como los órganos que específicamente resolverán estos pleitos. Finalmente el artículo 52.1.8.º de la LEC dice que en los juicios en materia de propiedad horizontal será competente el Tribunal del lugar en que radique la finca.

El artículo 249.1.8.º de la LEC remite la tramitación de estos pleitos al cauce del juicio ordinario.

Se fija la cuantía de este procedimiento como indeterminada.

El artículo 10 de la LEC legitima para comparecer y actuar en juicio a los titulares de la relación jurídica o del objeto litigioso. La propia LPH faculta al propietario para impugnar los acuerdos de la Comunidad que resulten lesivos o perjudiciales.

En aplicación de los artículos 23 y 31 de la LEC las partes deberán comparecer representadas por Procurador y asistidas por Letrado.

La presente demanda no está sujeta al previo intento de resolución de controversias en vía no jurisdiccional, por tratarse de la impugnación judicial de un acuerdo de la comunidad de propietarios, habiendo determinado la doctrina de apelación que la propia junta equivale a una actividad negociadora y no son exigibles los MASC de la LO 1/2025 para la Ley de Propiedad Horizontal.

Primero.— [COMPLETAR]

[ELEGIR UNA OPCIÓN Y REDACTARLA: Elementos comunes / Propiedad privada — el texto de cada opción no venía en el formulario original]

Segundo.— El artículo 18 de la LPH permite impugnar los acuerdos contrarios a la ley o los estatutos de la Comunidad de Propietarios. Se exige como condición que el demandante esté al corriente en el pago de las deudas vencidas de la Comunidad o que haya consignado judicialmente esta cantidad.

Tercero.— El artículo 9.º de la LPH regula las obligaciones de los propietarios entre las cuales se encuentra la de:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Servidumbre / Instalaciones generales — el texto de cada opción no venía en el formulario original]

Cuarto.— Artículo 18.4 de la LPH. La acción de impugnación de los acuerdos contrarios a la ley o a los estatutos caduca al año de haberse adoptado. En este caso han transcurrido meses.

En aplicación del artículo 394 de la LEC deberán imponerse al demandado.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y copia de todo ello, lo admita a trámite el Letrado de la Administración de Justicia dictando al efecto el oportuno decreto teniendo por interpuesta demanda de juicio declarativo ordinario contra la Comunidad de Propietarios de la C/, n.º [Nº], a fin de que en su día, previa la tramitación oportuna, se dicte Sentencia mediante la que se deje sin efecto el acuerdo de la Junta de Propietarios de fecha [FECHA] por el que se acordó al declararlo, todo ello con expresa imposición de costas al demandado.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de abogado y procurador

========================================================================
