---
name: defensor-judicial-como-cautelar-junto-demanda-medidas-364
description: "Redacta el escrito «Defensor judicial como cautelar junto a la demanda de medidas de apoyo» (formulario 364 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Defensor judicial como cautelar junto a la demanda de medidas de apoyo

> Formulario 0364 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…y certificado expedido por la residencia»; «…donde se encuentra ingresado»; «… índole judicial amparen los derechos de»; «…Que la autorización judicial en favor de»; «…das ESPECIALES URGENTES Y CONCRETAS para»; «…miento de defensor judicial a fin de que»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 762 LEC
- art. 723.1 LEC
- Ley 15/2015

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

### Formulario 0364 · Defensor judicial como cautelar junto a la demanda de medidas de apoyo

- Año del modelo: 2019
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 12 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Otrosí solicitando el nombramiento de defensor judicial por no haberse constituido aún la curatela, siendo ésta necesaria para la administración de bienes de la persona con discapacidad. [NOTA DE REVISIÓN: Base sustantiva vigente: art. 295.4.º CC; procesal: art. 762 LEC. Fuente: Código Civil (BOE-A-1889-4763) art. 295.4.º; LEC 1/2000 (BOE-A-2000-323) art. 762, redacción Ley 8/2021 (BOE-A-2021-9233).]

Formulario adaptado a la reforma procesal de la LO 1/2025.

OTROSÍ DIGO que interesa al derecho de esta parte instar la tutela cautelar, con base en los siguientes datos y consideraciones jurídicas:

Primero.- Por reproducidos los hechos y las valoraciones sobre los mismos que se han dejado expresados en el cuerpo de la demanda principal, se insiste en la conveniencia a los intereses de la persona con discapacidad, que debe protegerse la situación jurídica de sus bienes

Concretamente, tiene un importante patrimonio, relacionado en el anexo acompañado a la presente solicitud, parte del cual consiste en una serie de activos mobiliarios sobre los que hay que tomar decisiones de manera periódica (en cada caso, alegar la situación, la urgencia y la causa de necesidad de las medidas concretas: firmar contrato, administrar fincas, realizar pagos, aceptar herencias, obras en inmuebles requeridas por ayuntamiento ...).

Se acompañan a este escrito certificado médico sobre el estado de salud de D./Dña. [NOMBRE Y APELLIDOS], relación de bienes propiedad de aquel, y certificado expedido por la residencia [COMPLETAR] donde se encuentra ingresado [COMPLETAR].

Segundo.- Que ante la imposibilidad de D./Dña. [NOMBRE Y APELLIDOS], debido a su estado físico y mental, esta representación considera necesaria una autorización judicial a favor de D./Dña. [NOMBRE Y APELLIDOS], a fin de que pueda ejercitar cuantas acciones legales, incluidas las de índole judicial amparen los derechos de [COMPLETAR]. Todas ellas encaminadas, exclusivamente a

Que la autorización judicial en favor de [COMPLETAR] tendrá la duración de la sustantación del presente procedimiento y en tanto no se nombre curador.

Tercero.- Que de todo lo expuesto -no habiéndose constituido aún la curatela, siendo está necesaria- y debido a que se precisan medidas ESPECIALES URGENTES Y CONCRETAS para [COMPLETAR], resulta de aplicación el art. 762 LEC.

Procesalmente, y siendo de aplicación las normas del proceso cautelar, en relación con los arts. 735 y concordantes LEC, consideramos que el Tribunal debe considerar que concurren todos los requisitos establecidos y acreditados, para acceder a la presente solicitud de medidas, fijando con toda precisión la medida que se acuerda y precisando el régimen a que ha de estar sometida.

Cuarto.- Que sin perjuicio del superior criterio juzgador, entiende esta parte que la medida redunda en beneficio de la propia demandada y presunta discapacitada, lo que impide establecer una caución a cargo del solicitante.

En consecuencia se acude al expediente regulado en los arts. 27 y ss. de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), para solicitar el nombramiento de un defensor judicial que administre los bienes. Todo lo cual tiene encaje en el art. 42 bis).a.4 LJV, en la medida en que no resulta previsible que D./Dña. [NOMBRE Y APELLIDOS] proceda a realizar por sí misma la designación de su defensa y representación, y deben adoptarse medidas urgentes para la administración de sus activos mobiliarios. En este sentido, me postulo para tal cargo, sin perjuicio de mostrar mi consentimiento con el defensor judicial que finalmente se tenga a bien designar.

Quinto.- Que conforme al art. 723.1 LEC corresponde resolver esta petición a la Sección Civil del Tribunal de Instancia a la que me dirijo, puesto que el proceso cautelar que se inicia con la demanda del proceso del que resulta instrumental es competencia funcional del órgano competente para conocer de tal proceso principal, como se ha razonado lo es.

En consecuencia con lo expuesto,

SUPLICO AL TRIBUNAL

que, teniendo por recibida esta solicitud de medidas cautelares, se digne admitirla y convocándose a la vista por el Letrado/a de la Administración de Justicia a las partes, seguido que sea el oportuno trámite, y practicándose la prueba documental que se propone, dicte auto por el que se acuerde la medida solicitada procediendo al nombramiento de defensor judicial a fin de que [COMPLETAR], en todo caso sin imposición de caución a esta parte por redundar la medida en beneficio de D./Dña. [NOMBRE Y APELLIDOS]

Todo ello con imposición de las costas del proceso cautelar a la parte contraria, si se resistiere a la adopción de la medida.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a
