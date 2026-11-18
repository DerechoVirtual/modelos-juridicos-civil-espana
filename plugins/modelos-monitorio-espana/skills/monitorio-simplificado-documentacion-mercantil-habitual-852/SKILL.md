---
name: monitorio-simplificado-documentacion-mercantil-habitual-852
description: "Redacta el escrito «Monitorio simplificado con documentación mercantil habitual» (formulario 852 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Monitorio simplificado con documentación mercantil habitual

> Formulario 0852 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Escrito inicial sin referencia al requisito de procedibilidad: añadir la nota MASC (el art. 5.2 LO 1/2025 alcanza a los procesos del libro IV LEC, incluido el monitorio).
- REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] DNI/NIE (2 veces)
- [ ] PROFESIÓN (2 veces)
- [ ] CALLE
- [ ] NÚMERO (7 veces)
- [ ] Nº
- [ ] TELÉFONO
- [ ] IMPORTE (6 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…n.º [NÚMERO] de»; «…, domiciliado en C/ n.º [NÚMERO] de»; «…erto al público bajo el nombre comercial»; «…sito en la C/ n.º [NÚMERO] de»; «…de teléfono [TELÉFONO] y de fax»; «…iguiente ANTECEDENTE ÚNICO.—Con fecha de»; «…mi establecimiento fabril, concretamente»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 2 de la Ley 10/2012

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

### Formulario 0852 · Monitorio simplificado con documentación mercantil habitual

- Año del modelo: 2013
- Revisión 17-11-2026: 36 campos de relleno marcados en blanco
- Avisos de la revisión: Escrito inicial sin referencia al requisito de procedibilidad: añadir la nota MASC (el art. 5.2 LO 1/2025 alcanza a los procesos del libro IV LEC, incluido el monitorio). · REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

AL SERVICIO COMÚN DE REGISTRO Y REPARTO DEL TRIBUNAL DE INSTANCIA DE [SEDE]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, soltero, provisto de DNI [DNI/NIE], de profesión [PROFESIÓN] y domiciliado en C/ [CALLE] n.º [NÚMERO] de [COMPLETAR] ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que mediante el presente escrito formulo PETICIÓN INICIAL mediante la que insto PROCESO MONITORIO frente a D./Dña. [NOMBRE Y APELLIDOS] (deudor), mayor de edad, soltero, de profesión [PROFESIÓN], provisto de DNI [DNI/NIE], domiciliado en C/ n.º [NÚMERO] de [COMPLETAR], quien también podrá ser citado en su establecimiento comercial abierto al público bajo el nombre comercial [COMPLETAR] sito en la C/ n.º [NÚMERO] de [COMPLETAR] provisto de n.º [Nº] de teléfono [TELÉFONO] y de fax [COMPLETAR], con objeto de que se requiera a dicho deudor para que me haga efectiva la cantidad de [IMPORTE] euros que me adeuda, según el siguiente

ANTECEDENTE

ÚNICO.—Con fecha de [COMPLETAR] vendí a D./Dña. [NOMBRE Y APELLIDOS] géneros de los que habitualmente produzco en mi establecimiento fabril, concretamente [COMPLETAR]. Tales géneros fueron entregados a D./Dña. [NOMBRE Y APELLIDOS] en la expresada fecha, firmando éste, en señal de conformidad con la recepción de los mismos, el albarán de entrega que acompaño reseñado como documento n.º [NÚMERO]. El precio de la compraventa ascendió a [IMPORTE] euros, como consta en la factura que entregué al deudor y cuyo duplicado acompaño reseñada como documento n.º [NÚMERO]. Convine con el comprador la puesta en circulación de un recibo para el pago de los géneros por aquél adquiridos, que a su presentación al cobro resultó desatendido e impagado. Como documento n.º [NÚMERO] acompaño ejemplar original del mencionado recibo impagado. La devolución del recibo me ha ocasionado gastos por [IMPORTE] euros, como acredito con el justificante bancario de gastos de devolución que acompaño como documento n.º [NÚMERO] Resulta de todo ello que D./Dña. [NOMBRE Y APELLIDOS] me adeuda la suma conjunta de [IMPORTE] euros, correspondiente a principal de la factura que acompaño y gastos de devolución del recibo puesto en circulación para su pago.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL que tenga por presentado este escrito, documentos adjuntos y copias de todo ello, lo admita y tenga por formulada PETICIÓN INICIAL de promoción de PROCESO MONITORIO contra D./Dña. [NOMBRE Y APELLIDOS] y en su virtud requiera el Letrado de la Administración de Justicia a dicho deudor para que haga efectivo en el plazo de veinte días el importe de [IMPORTE] euros, bajo apercibimiento de que de no hacerlo se despachará ejecución por la cantidad adeudada más los intereses de mora procesal pertinentes y costas de la ejecución, acordando además lo siguiente:

1.º Para el supuesto de que el deudor no pagare la suma reclamada y no formulare oposición en debida forma, se dicte el decreto dando por terminado el procedimiento monitorio y dándonos traslado para formular despacho de ejecución.

2.º OPCIONES:

a) (En asuntos cuya cuantía no supere 15.000 euros) Para el supuesto de que el deudor presentase escrito de oposición en debida forma y plazo legal, dicte decreto el Letrado de la Administración de Justicia dando por terminado este proceso y acordando seguir los trámites del juicio verbal dando traslado a esta parte para su contestación a fin de que en su día se dicte sentencia condenando a D./Dña. [NOMBRE Y APELLIDOS] a pagarme la suma reclamada de [IMPORTE] euros más los intereses legales e imponiéndole las costas del proceso.

b) (En asuntos cuya cuantía supere 15.000 euros) Para el supuesto de que el deudor presentase escrito de oposición en plazo legal y debida forma, acuerde darme traslado del mismo para formular demanda en el plazo de un mes legalmente previsto.

Por ser Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

(Para personas jurídicas y cuantía superior a 2.000 euros) OTROSÍ DIGO: Que acompaño modelo 696 de autoliquidación de la tasa judicial, según exigen el artículo 2 de la Ley 10/2012, de 20 de noviembre, y la Orden que regula los modelos de autoliquidación.

NUEVAMENTE SUPLICO: Que se tenga por cumplimentado este trámite por ser justicia que pido en mismo lugar y fecha.

========================================================================
