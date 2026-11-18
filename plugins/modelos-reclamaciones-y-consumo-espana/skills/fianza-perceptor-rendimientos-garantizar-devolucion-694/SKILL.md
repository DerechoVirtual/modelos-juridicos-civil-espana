---
name: fianza-perceptor-rendimientos-garantizar-devolucion-694
description: "Redacta el escrito «Fianza del perceptor de rendimientos para garantizar su devolución» (formulario 694 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Fianza del perceptor de rendimientos para garantizar su devolución

> Formulario 0694 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] FECHA (6 veces)
- [ ] Nº DE EXPEDIENTE
- [ ] IMPORTE (3 veces)
- [ ] LUGAR
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…on lo ordenado por el decreto dictado el»; «… Hechos y consideraciones jurídicas: 1.ª»; «…rización para cobrar rendimientos de los»; «…o de renta fija, emitidos por la entidad»; «…SA, con número de serie»; «…, y que se encuentran numerados del»; «…al»; «…ido sustraídos de la entidad depositaria»; «…/»; «…para la ratificación de la misma. 2.ª»; «…ratificación mediante decreto dictado el»; «…, la devolución de los rendimientos. 3.ª»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 135.7 de la Ley 15/2015
- art. 135.7 LJV
- art. 3.2 LJV
- art. 133.3 LJV

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

### Formulario 0694 · Fianza del perceptor de rendimientos para garantizar su devolución

- Año del modelo: 2015
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 26 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Presentación de aval bancario para cobrar rendimientos de valores mobiliarios sustraídos

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, como mejor proceda en derecho comparezco y DIGO: (1)

Que por medio del presente escrito, y de conformidad con lo ordenado por el decreto dictado el [COMPLETAR] por el Letrado de la Administración de Justicia del órgano al cual tengo el honor de dirigirme, presto aval bancario para cobrar rendimientos de valores mobiliarios sustraídos. Todo ello, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª [COMPLETAR])

El pasado [FECHA] mi mandante solicitó autorización para cobrar rendimientos de los [COMPLETAR] valores admitidos a cotización oficial en el mercado de renta fija, emitidos por la entidad [COMPLETAR] SA, con número de serie [COMPLETAR], y que se encuentran numerados del [COMPLETAR] al [COMPLETAR]. Los mismos habían sido sustraídos de la entidad depositaria [COMPLETAR] SA, extremo que se denunció ante la Sociedad Rectora del Mercado de Renta Fija mediante escrito presentado en fecha [FECHA]. Lo que llevó a que se acordara por dicha sociedad la prohibición de negociación y transmisión de los mismos con carácter provisional, y que se incoara el expediente de jurisdicción voluntaria con nº [Nº DE EXPEDIENTE] / [COMPLETAR] para la ratificación de la misma.

2.ª [COMPLETAR])

Tras la concesión de tal ratificación mediante decreto dictado el [COMPLETAR], y el transcurso de los seis meses indicado en el art. 135.7 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), el pasado [FECHA] se solicitó autorización para cobrar los rendimientos de los referidos valores mobiliarios, que se calculaban aproximadamente en la cantidad de [IMPORTE] euros. Extremo que se concedió por decreto dictado por el Letrado de la Administración de Justicia el pasado [FECHA], en el cual se exigió a mi mandante una fianza por importe de [IMPORTE] euros que garantizara, en su caso, la devolución de los rendimientos.

3.ª [COMPLETAR])

En consecuencia, se acompaña aval bancario constituido ante la entidad financiera [COMPLETAR] SA por la cantidad de [IMPORTE] euros, en cumplimiento de la condición prefijada,

Por todo lo expuesto, al amparo de lo dispuesto en el art. 135.7 LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito, y la documentación que se acompaña se tenga por prestada fianza en garantía de los rendimientos a percibir, en cumplimiento de lo ordenado en el decreto de fecha [FECHA].

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito, el art. 133.3 LJV establece como preceptiva la intervención de Abogado y Procurador para la solicitud en análisis.

========================================================================
