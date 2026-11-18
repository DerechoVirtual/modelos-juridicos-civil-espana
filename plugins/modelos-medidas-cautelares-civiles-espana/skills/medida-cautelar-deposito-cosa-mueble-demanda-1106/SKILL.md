---
name: medida-cautelar-deposito-cosa-mueble-demanda-1106
description: "Redacta el escrito «Medida cautelar de depósito de cosa mueble con la demanda» (formulario 1106 de medidas cautelares y diligencias preliminares, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Medida cautelar de depósito de cosa mueble con la demanda

> Formulario 1106 del plugin **Medidas cautelares y diligencias preliminares** · revisado el 17-11-2026.

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

- [ ] Nº
- [ ] NOMBRE Y APELLIDOS
- [ ] LOCALIDAD
- [ ] IMPORTE
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…da en los formularios precedentes), para»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 734 de la LEC
- artículo 732.2 de la LEC

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

### Formulario 1106 · Medida cautelar de depósito de cosa mueble con la demanda

- Año del modelo: 2013
- Revisión 17-11-2026: 4 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Otrosí digo: Que al amparo de lo dispuesto en el artículo 721 en relación con el 730, ambos de la LEC (en caso de que se solicitase sin audiencia de la otra parte: al amparo de lo dispuesto en el artículo 733.2 en relación con el artículo 727.1.º, ambos de la LEC) solicito la adopción (en su caso: sin audiencia del demandado) de la medida cautelar de DEPÓSITO DE COSA MUEBLE. La solicitud de esta medida se asienta sobre los siguientes

ANTECEDENTES Y PRESUPUESTOS

Entre las acciones que se ejercitan en la demanda se encuentra la reivindicatoria de (determinar objeto reivindicado).

Se dirige la solicitud de esta medida cautelar a obtener la puesta a disposición del demandante de dicho bien, que siendo propiedad del actor, permanece desde hace [Nº] días en poder del demandado, habiéndose negado éste a restituirlo a su propietario alegando haberlo adquirido de un tercero que manifestó tener poder de disposición sobre él.

Las razones expuestas al desarrollar la petición de la medida anterior sirven para justificar la conveniencia de la adopción de esta medida. Si el demandado, que ha declarado públicamente su intención de vender todo su patrimonio y trasladarse a vivir al extranjero, lleva a efecto su propósito, va a resultar de muy dificultosa ejecución la restitución del derecho de mi poderdante.

Se aporta con la demanda (reseñar documentos), que acreditan la libre y completa titularidad de mi representado sobre el bien reivindicado, lo que constituye un eficaz principio de prueba que permiten al juzgador formar un juicio provisional e indiciario favorable sobre el fundamento de la pretensión deducida con la demanda.

Solicito que se nombre depositario del bien a D. [NOMBRE Y APELLIDOS], industrial de reconocida solvencia, que podrá custodiarlo en el local de su propiedad sito en [LOCALIDAD]

También intereso que una vez acordado tal nombramiento, se le cite para aceptación del cargo y se disponga lo necesario para la formal entrega del bien depositado.

Ofrezco la prestación de caución mediante aval solidario, indefinido y de primera reclamación por la suma de [IMPORTE] euros. Esta cantidad se estima suficiente y proporcionada a la finalidad que persigue, toda vez que (desarrollar la argumentación adecuada al caso).

Las costas deberán ser impuestas al demandado si se opusiere a la adopción de la medida cautelar propuesta.

La tramitación se ajustará a lo dispuesto en los artículos 730 y ss. de la LEC. Se deberá citar a las partes a la comparecencia para vista que establece el artículo 734 de la LEC.

(En caso de que se solicite inaudita parte: La tramitación se ajustará a lo dispuesto en los artículos de la LEC. Ya se ha manifestado que los efectos del señalamiento de la comparecencia prevista en el artículo 734 de la LEC para substanciar la tramitación de la medida interesada impedirían, con toda probabilidad, la eficacia de la medida, dadas las razones de urgencia ya expresadas en el relato fáctico. Procede, en consecuencia, la adopción inaudita altera parte de las medidas interesadas, sin perjuicio de la facultad de éste de formalizar, si lo estima conveniente, la oposición prevista en los artículos 739 y ss. de la LEC).

Al amparo de lo dispuesto en el artículo 732.2 de la LEC, y para acreditar la concurrencia de los supuestos que autorizan la adopción de las medidas cautelares propuestas, propongo la práctica de la siguiente

1.(proponer la que proceda).

Nuevamente suplico al Tribunal que tenga por formulada petición de adopción de la MEDIDA CAUTELAR de depósito de cosa mueble que se deja solicitada mediante (determinar el modo en que se solicita que se realice el depósito), por ofrecida la caución que se deja indicada y por propuesta la prueba antecedente, impulsando en debida forma el trámite para su adopción (adecuar la petición a la modalidad: con o sin audiencia del demandado en la forma desarrollada en los formularios precedentes), para [COMPLETAR], en definitiva, dictar auto mediante el que se acuerde su adopción con los demás pronunciamientos legalmente previstos, y en concreto el de imposición de costas al demandado si se pusiere a la adopción de las medidas cautelares propuestas.

Por ser Justicia que reitero en igual lugar y fecha.

========================================================================
