---
name: ejecucion-acto-conciliacion-avenencia-668
description: "Redacta el escrito «Ejecución de acto de conciliación con avenencia» (formulario 668 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Ejecución de acto de conciliación con avenencia

> Formulario 0668 del plugin **Ejecución civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.
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
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (6 veces)
- [ ] IMPORTE (6 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 21 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…D»; «…de»; «…de [COMPLETAR] de»; «…seguido ante el Juez de Paz de»; «…de»; «…de [COMPLETAR] de»; «…cución y costas, la cual dirijo contra D»; «…de»; «…de [COMPLETAR] de»; «…sentado se instó, ante el Juez de Paz de»; «…to de conciliación contra el ejecutado D»; «…de»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 548 de la LEC
- art. 147.2 LJV
- art. 50 de la LEC
- art. 147.3 LJV
- arts. 548 a 554 de la LEC
- artículo 590 LEC

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

### Formulario 0668 · Ejecución de acto de conciliación con avenencia

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 38 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D [COMPLETAR] Procurador de los Tribunales, en nombre y representación de [NOMBRE DEL REPRESENTADO/A], parte ejecutada en el procedimiento de ejecución arriba referenciado, según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, ante el Tribunal comparezco y como mejor proceda en Derecho

DIGO:

Que por medio de la presente demanda y en la meritada representación solicito la ejecución de lo convenido en acto de conciliación en fecha [FECHA] de [COMPLETAR] de [COMPLETAR] seguido ante el Juez de Paz de [COMPLETAR], la cual consta en el auto aprobatorio de fecha [FECHA] de [COMPLETAR] de [COMPLETAR], en reclamación de la suma pactada de [IMPORTE] euros, con más la cantidad de [IMPORTE] euros, que se presupuesta en concepto de intereses que se pueden devengar en la presente ejecución y costas, la cual dirijo contra D [COMPLETAR], con domicilio en [LOCALIDAD], con base en los siguientes:

HECHOS

En fecha [FECHA] de [COMPLETAR] de [COMPLETAR] por mi representado se instó, ante el Juez de Paz de [COMPLETAR], acto de conciliación contra el ejecutado D [COMPLETAR] en reclamación de [IMPORTE] euros como consecuencia de una deuda de

Admitida a trámite la solicitud, se celebró la comparecencia en fecha [FECHA] de [COMPLETAR] de [COMPLETAR], aviniéndose el demandado a indemnizar a mi representado en la cantidad de [IMPORTE] euros, tal como consta en el acta y resolución que se acompañan.

(Se acompaña como documentos núm. testimonio del acta de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] y del auto del Juez de Paz de [COMPLETAR] haciendo constar la avenencia de fecha [FECHA] de [COMPLETAR] de [COMPLETAR]).

Que habiendo transcurrido el plazo prevenido en el artículo 548 de la LEC sin que se haya hecho efectiva la deuda por la parte condenada al pago, es por lo que se interesa su ejecución.

FUNDAMENTOS DE DERECHO

Competencia

El art. 147.2 LJV dispone que será competente para la ejecución el mismo Tribunal que tramitó la conciliación cuando se trate de asuntos de la competencia del propio Tribunal; en los demás casos será competente para la ejecución la Sección Civil del Tribunal de Instancia a quien hubiere correspondido conocer de la demanda. En este caso, al exceder de la competencia del Juez de Paz, es competente el Tribunal al que me dirijo al tratarse de una acción personal, según dispone el art. 50 de la LEC.

Procedimiento

El art. 147.3 LJV establece que la ejecución se llevará a cabo conforme a lo establecido en la Ley de Enjuiciamiento Civil para la ejecución de sentencias y convenios judicialmente aprobados, por lo que son de aplicación los arts. 548 a 554 de la LEC.

Título ejecutivo

Artículo 517.2.9 en relación con el artículo 147.1 de la Ley de Jurisdicción Voluntaria, acompañándose el testimonio del acta junto con el auto del Juez de Paz (o decreto del Letrado de la Administración de Justicia) haciendo constar la avenencia de las partes en el acto de conciliación.

Pretensión

Se pretende la ejecución de la obligación de pago alcanzada en avenencia, por lo que es de aplicación lo dispuesto en los artículos 571 y ss. para la ejecución dineraria.

Costas

Artículo 539.2 LEC.

Por todo ello,

SUPLICO AL TRIBUNAL: Que teniendo por presentado este escrito con los documentos que lo acompañan y sus copias, se acuerde, sin necesidad de previo requerimiento al deudor, se dicte auto conteniendo la orden general de ejecución y despachando la misma, en el que conforme al artículo 551.2.3º LEC fije la cantidad reclamada conforme a lo solicitado en la cantidad de [IMPORTE] euros en concepto de principal, más la cantidad de [IMPORTE] euros en concepto de intereses, gastos y costas.

OTROSÍ DIGO: Que, una vez dictado el auto general de ejecución y de conformidad con el art. 551.3.1º de la LEC, se solicita que por el Letrado de la Administración de Justicia responsable de la misma se dicte decreto procediéndose al embargo, sin previo requerimiento de pago del ejecutado por la cantidad indicada, de los siguientes bienes que se estiman suficientes para cubrir las indicadas responsabilidades en su totalidad:

Por lo que, SUPLICO que se dicte decreto en el que se contengan las medidas que dejo interesadas.

OTROSÍ DIGO II: Que desconociendo esta parte bienes que puedan ser objeto de embargo por parte de este Tribunal, al amparo de lo dispuesto en el artículo 590 LEC, esta parte solicita que, una vez dictado el auto general de ejecución y de conformidad con el art. 551.3.2º de la LEC, el Tribunal proceda a dirigirse a los efectos de determinación de la relación de bienes muebles e inmuebles, así como depósitos o imposiciones a plazo fijo que el ejecutado pueda tener a su nombre a los siguientes organismos:

1. Gerencia Territorial del Catastro de [COMPLETAR]

2. Delegación Territorial de la Agencia Tributaria de [COMPLETAR]

3. Registro de la Propiedad núm. De

4. Jefatura Provincial de Tráfico de [LOCALIDAD]

5. Caja de Ahorros Provincial de [COMPLETAR]

Por lo que, SUPLICO que se dicte decreto procediéndose a adoptar las medidas de localización y averiguación de bienes solicitadas.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

(Firma Abogado y Procurador)

========================================================================
