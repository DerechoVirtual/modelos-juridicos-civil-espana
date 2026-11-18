---
name: demanda-ordinaria-accion-derivada-relaciones-vecindad-1164
description: "Redacta el escrito «Demanda ordinaria por acción derivada de relaciones de vecindad» (formulario 1164 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda ordinaria por acción derivada de relaciones de vecindad

> Formulario 1164 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] FECHA (3 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 23 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…do/a de la Administración de Justicia de»; «…que acompaño»; «…nes de vecindad, la cual dirijo contra D»; «…es titular de la finca urbana situada en»; «…El demandado D»; «…as fincas son colindantes por el lindero»; «…a del demandado existe una plantación de»; «…árboles, de una altura de»; «…, los cuales están a una distancia de»; «…s, y además se ubican a una distancia de»; «…os acreditativos acompaño como documento»; «…informe pericial elaborado por D»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 591 del Código Civil
- artículos 591 y 592 del Código Civil
- art. 5 de la Ley Orgánica 1/2025
- art. 592 del Código Civil
- artículo 394 LEC
- art. 251 de la LEC

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

### Formulario 1164 · Demanda ordinaria por acción derivada de relaciones de vecindad

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 31 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D. [NOMBRE Y APELLIDOS] Procurador de los Tribunales en representación de D/Dña. [NOMBRE Y APELLIDOS], según acredito por certificación del registro electrónico de apoderamientos judiciales que acompaño o mediante designación apud acta otorgado ante el Letrado/a de la Administración de Justicia de [COMPLETAR] que acompaño [COMPLETAR] por medio de la presente formulo demanda de juicio ordinario en ejercicio de acción derivada de las relaciones de vecindad, la cual dirijo contra D [COMPLETAR], con domicilio en en base a los siguientes:

HECHOS

Mi representado es titular de la finca urbana situada en [COMPLETAR] tal y como resulta de la certificación de la inscripción obrante en el Registro de la Propiedad que se adjunta como documento núm. [Nº DE DOCUMENTO]

El demandado D [COMPLETAR] es por su parte titular de la finca urbana colindante sita en [LOCALIDAD] tal y como resulta de la certificación de la inscripción obrante en el Registro de la Propiedad que se adjunta como documento núm

Las citadas fincas son colindantes por el lindero [COMPLETAR], hallándose separadas por una pared que discurre a lo largo de todo el lindero, tal como se acredita por el plano y fotografías que se acompañan como documentos núm

Se ejercita la presente acción derivada de las relaciones de vecindad por cuanto que en la finca del demandado existe una plantación de [COMPLETAR] árboles, de una altura de [COMPLETAR], los cuales están a una distancia de [COMPLETAR] respecto de la pared divisoria. Por tanto, se trata de árboles altos que se han plantado a una distancia inferior a dos metros de la línea divisoria.

Tal como se aprecia en las fotografías acompañadas, las ramas de estos árboles están tocando la pared de la edificación de mi representado, privándole de luces y vistas, y además se ubican a una distancia de [COMPLETAR] sobre la línea del tejado de la edificación, impidiendo el vertido de aguas.

A efectos acreditativos acompaño como documento [COMPLETAR] informe pericial elaborado por D [COMPLETAR], ingenieros técnico agrícolas, donde se recoge la medición de la distancia entre árboles y pared divisoria, mediación de la altura, distancia entre árboles y edificación y efectos sobre la finca de representado, vistas y vertido de aguas.

Con fundamento en estos hechos, se solicita que se condene al demandado a arrancar los árboles descritos por no respetar la distancia mínima de dos metros establecida en el art. 591 del Código Civil, además de extenderse las ramas hacia la edificación colindante con grave perjuicio para la finca de mi representado.

Esta pretensión tiene amparo en la pacífica interpretación jurisprudencial que viene reiterando que la prohibición de plantar árboles a menor distancia de la establecida en el artículo 591 del Código civil [COMPLETAR], tiene la finalidad de regular pacíficamente la convivencia entre vecinos a través del respeto a la integridad y libertad de uso de los fundos, siendo una limitación recíproca que favorece igualmente a las dos fincas colindantes, naciendo un derecho a que se arranquen los árboles y plantados con infracción de las distancias previstas desde el mismo momento de la plantación y persistiendo durante toda la vida del árbol. La razón de ser de estos límites recíprocos estriba en que las raíces no se aprovechen del suelo ajeno y en evitar que las ramas priven al fundo vecino de aire y luz, y deben regir para todos aquellos supuestos en que pueda quedar perjudicado el fundo vecino por la proximidad de un árbol, como sucede en el caso de la finca de mi representado según ha quedado expuesto en el anterior fundamento.

Mi representado ha intentado solucionar el asunto antes de iniciar el ejercicio de la acción judicial, habiendo remitido requerimiento al demandado en fecha [FECHA] de [COMPLETAR] de [COMPLETAR] a los efectos de que arrancara los árboles, sin que éste haya atendido dicho requerimiento (acompaño como documento [COMPLETAR] requerimiento notarial de fecha [FECHA] de [COMPLETAR] de [COMPLETAR]).

Finalmente, en fecha [FECHA], se acudió a [COMPLETAR], con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial, no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

Competencia

Corresponde a los Tribunales de [LOCALIDAD] al ser el lugar al ser el lugar en el que se ubican las fincas (art. 52.1.1.ª LEC).

Legitimación

La legitimación corresponde a esta parte ante su condición de titular del predio sobre el que se está produciendo la perturbación, en tanto que la legitimación pasiva corresponde al demandado, conforme a lo que disponen los artículos 591 y 592 del Código Civil.

Procedimiento

Es el juicio ordinario con fundamento en el artículo 249.2º LEC al exceder la cuantía de este proceso de 15.000 euros.

Cumplimiento de los requisitos de procedibilidad.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Acción ejercitada

La derivada de las relaciones de vecindad contemplada en los artículos 591 y 592 del Código Civil. El artículo 591 dispone que "No se podrá plantar árboles cerca de una heredad ajena sino a la distancia autorizada por las ordenanzas o la costumbre del lugar, y en su defecto, a la de dos metros de la línea divisoria de las heredades si la plantación se hace de árboles altos, y a la de 50 centímetros si la plantación es de arbustos o árboles bajos. Todo propietario tiene derecho a pedir que se arranquen los árboles que en adelante se plantaren a menor distancia de su heredad”. El art. 592 del Código Civil añade que "Si las ramas de algunos árboles se extendieren sobre una heredad, jardines o patios vecinos, tendrá el dueño de éstos derecho a reclamar que se corten en cuanto se extiendan sobre su propiedad, y si fueren las raíces de los árboles vecinos las que se extendiesen en suelo de otro, el dueño del suelo en que se introduzcan podrá cortarlas por sí mismo dentro de su heredad”.

Pretensiones

La pretensión de esta parte es la de que se arranquen los árboles y ramas que se han descrito, amparada en los preceptos antes invocados. Es criterio jurisprudencial que la prohibición recogida en el art. 591 del Código Civil [COMPLETAR], ya se le catalogue como una propia servidumbre predial, ya como una mera limitación de dominio, ya como una imposición derivada de las denominadas relaciones de vecindad [COMPLETAR], viene a establecer el que las plantaciones no pueden hacerse libremente dentro de las fincas sino guardando las distancias debidas por así exigirlo elementales normas de pacífica convivencia y respeto a la integridad y libertad de uso de los predios, concediendo dicho precepto al propietario de la finca colindante afectada el derecho a solicitar que se arranquen los árboles plantados con infracción de las distancias debidas desde el mismo momento de la plantación y sin necesidad de demostración de concretos y efectivos perjuicios pues la norma no tiene un sentido reparador sino de ordenación de la convivencia y de preservación del libre uso y disfrute de las fincas [COMPLETAR]. Esta regla de vecindad es de aplicación en otros ámbitos como el de las urbanizaciones privadas, o incluso en el urbano (jardines o patios de un inmueble), como ponen de relieve las sentencias del Tribunal Supremo de 28 de mayo de 1986 y 19 de mayo de 1989, tratándose de restricción del derecho de propiedad basado en el principio jurisprudencial reconocido de que la propiedad no puede llegar más allá de lo que el respeto al vecino determina (sentencia del Tribunal Supremo de 17 de febrero de 1968 ).

En este caso, tal como ha quedado expuesto, se infringen las reglas de distancia y las ramas están privando a la finca de mi representado de aire y luz, por lo que debe condenarse al demandado a que proceda a arrancar los árboles plantados en su finca que han quedado identificados anteriormente.

En materia de costas, es de aplicación el artículo 394 LEC debiendo imponerse a la parte demandada.

En base a lo anterior,

SUPLICO AL TRIBUNAL que tenga por presentada la presente demanda con los documentos a ella adjuntos y por parte en la representación que ostento se tenga por formulada demanda de acción derivada de las relaciones de vecindad frente a D [COMPLETAR] y en su virtud se dicte sentencia por la que condene al demandado a arrancar los árboles descritos en esta demanda que no guardan la distancia mínima respecto de la línea divisoria, todo ello con imposición de costas a la parte demandada.

OTROSÍ DIGO I que, de conformidad con lo dispuesto en el art. 251 de la LEC se fija la cuantía del presente proceso en ….. euros.

En virtud de lo anterior,

SUPLICO AL TRIBUNAL que tenga por hechas las anteriores manifestaciones a los efectos pertinentes y por acompañado el documento justificativo del abono de la tasa.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma Abogado y Procurador

========================================================================
