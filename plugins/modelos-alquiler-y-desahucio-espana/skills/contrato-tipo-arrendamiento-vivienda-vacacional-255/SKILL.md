---
name: contrato-tipo-arrendamiento-vivienda-vacacional-255
description: "Redacta el escrito «Contrato tipo de arrendamiento de vivienda vacacional» (formulario 255 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contrato tipo de arrendamiento de vivienda vacacional

> Formulario 0255 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Desde el 8-10-2026 el «arrendamiento de temporada» de vivienda es «arrendamiento de vivienda temporal» (arts. 2.3, 7.2 y 9 bis LAU): causa de desplazamiento expresa y acreditable, más de 31 días, máximo 12 meses salvo causa; si no, se convierte en vivienda habitual. Los anteriores conservan su régimen hasta el plazo pactado (DT 8.ª).
- Si es cesión turística (art. 5.e LAU, máximo 31 días) queda fuera de la LAU y, en propiedad horizontal, requiere aprobación previa de la comunidad (art. 7.3 y 17.12 LPH).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] CALLE (3 veces)
- [ ] IMPORTE
- [ ] ÓRGANO
- [ ] LOCALIDAD
- [ ] Otros 20 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…En la»; «…a»; «…, mayor de edad, vecino/a de»; «…, mayor de edad, vecino/a de»; «…al: Vivienda con una superficie total de»; «…, perteneciente al inmueble sito en la»; «…, de la localidad de»; «…referencia catastral»; «…scrita en el Registro de la Propiedad de»; «…Tomo»; «…Tomo [COMPLETAR] Folio»; «…de la localidad de»; …

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 31 de la Ley 29/1994

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

### Formulario 0255 · Contrato tipo de arrendamiento de vivienda vacacional

- Año del modelo: 2020
- Revisión 17-11-2026: 3 puntualizaciones normativas añadidas en el texto; 29 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)
- Avisos de la revisión: Desde el 8-10-2026 el «arrendamiento de temporada» de vivienda es «arrendamiento de vivienda temporal» (arts. 2.3, 7.2 y 9 bis LAU): causa de desplazamiento expresa y acreditable, más de 31 días, máximo 12 meses salvo causa; si no, se convierte en vivienda habitual. Los anteriores conservan su régimen hasta el plazo pactado (DT 8.ª). · Si es cesión turística (art. 5.e LAU, máximo 31 días) queda fuera de la LAU y, en propiedad horizontal, requiere aprobación previa de la comunidad (art. 7.3 y 17.12 LPH).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En la [COMPLETAR] a [COMPLETAR]

REUNIDOS

De una parte,

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, vecino/a de [COMPLETAR], con domicilio en la calle [CALLE], provisto/a del N.I.F., en adelante PARTE ARRENDADORA;

Y de otra parte,

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, vecino/a de [COMPLETAR] con domicilio en la calle [CALLE] provisto del N.I.F. en adelante PARTE ARRENDATARIA;

MANIFIESTAN

Que con el carácter que respectivamente intervienen, se reconocen mutua y plena capacidad legal de obrar y de obligarse para este acto, otorgando de forma libre y espontánea y a su tenor el presente CONTRATO DE ARRENDAMIENTO VIVIENDA DE TEMPORADA PARA USO VACACIONAL, asumiendo la responsabilidad que corresponda en función de la veracidad de sus manifestaciones, y, de mutuo acuerdo,

Exponen

I. Que la parte arrendadora es propietaria de la finca urbana que a continuación se describe y que constituye el objeto del presente contrato de arrendamiento de vivienda de temporada para uso vacacional:

Vivienda con una superficie total de [COMPLETAR], perteneciente al inmueble sito en la [COMPLETAR], de la localidad de [COMPLETAR] referencia catastral [COMPLETAR] inscrita en el Registro de la Propiedad de [COMPLETAR] Tomo [COMPLETAR] Folio [COMPLETAR].

II. Que la parte arrendadora es propietaria de la finca anteriormente descrita, por lo que ostenta facultades legales para su arrendamiento.

La parte arrendadora manifiesta que el inmueble no tiene la consideración de vivienda de uso turístico según la definición de la legislación sectorial.

Asimismo, manifiesta la parte arrendadora que la finca se encuentra libre de toda carga, gravámenes y libre de arrendamientos, así como que se haya al corriente de todos sus pagos.

III. La parte arrendataria tiene interés en el arrendamiento de temporada de la citada vivienda para uso vacacional.

IV. Que los comparecientes han convenido el arrendamiento para uso distinto del de vivienda [NOTA DE REVISIÓN: Desde el 8-10-2026 el art. 3.2 LAU excluye del uso distinto el alojamiento u hospedaje; el arrendamiento por temporada que cubre la necesidad de vivienda de quien está temporalmente desplazado es «arrendamiento de vivienda temporal» (arts. 2.3, 7.2 y 9 bis: causa expresa y acreditable, más de 31 días y, por regla general, no más de 12 meses). Los contratos de temporada anteriores conservan su régimen hasta el plazo pactado y se extinguen sin prórroga (DT 8.ª LAU). Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, arts. 2.3, 3.2, 7.2, 9 bis y DT 8.ª (redacción RDL 29/2026, BOE-A-2026-20823 (convalidado: BOE-A-2026-23755)).], suscriben el presente CONTRATO DE ARRENDAMIENTO VIVIENDA DE TEMPORADA PARA USO VACACIONAL, que se regirá de acuerdo con las siguientes:

Cláusulas

Primera.– Objeto

D./Dña. [NOMBRE Y APELLIDOS] PARTE ARRENDADORA, cede en arrendamiento de temporada para uso vacacional la vivienda de su propiedad, perteneciente al inmueble sito en la calle [CALLE] de la localidad de [COMPLETAR] referencia catastral [COMPLETAR] inscrita en el Registro de la Propiedad de [COMPLETAR] Tomo [COMPLETAR] Folio [COMPLETAR], que cuenta con una superficie total de [COMPLETAR].

Al mismo tiempo cede en arrendamiento los muebles y enseres que contiene y que se detallan en el ANEXO de inventario y fotografías unido a este contrato, considerándose a todos los efectos que éstos forman parte de aquélla y rigiéndose todo ello, en global, por las estipulaciones del presente contrato.

Ambas partes manifiestan que, tanto el apartamento como el mobiliario y enseres que en el ANEXO se relacionan se encuentran en perfecto estado para su uso.

La PARTE ARRENDATARIA manifiesta tener su domicilio habitual en el inmueble expresado en el encabezamiento, manifestando que arrienda la vivienda por motivo de uso vacacional.

Segunda.– Legislación aplicable

El presente contrato de arrendamiento de temporada para uso vacacional es otorgado de conformidad con la Ley 29/1994, de 24 de noviembre, de Arrendamientos Urbanos, rigiéndose, de conformidad con lo dispuesto en el apartado 3 de su artículo 4, en primer lugar, por lo expresamente pactado por las partes en el presente contrato.

En defecto de pacto expreso el presente contrato se regirá por lo dispuesto en el Título III de la referida Ley de Arrendamientos Urbanos, y supletoriamente, por las disposiciones del Código Civil.

Tercera.– Duración

El presente contrato de arrendamiento de temporada para uso vacacional tendrá una duración total de [COMPLETAR]. Dicha temporada quedará comprendida entre el [COMPLETAR] y [COMPLETAR].

Llegada dicha fecha de vencimiento del término del contrato, la PARTE ARRENDATARIA deberá dejar la libre y a disposición plena del/la ARRENDADOR/A el apartamento objeto del presente contrato, bajo apercibimiento de ejercicio de las acciones legales en caso contrario.

Cuarta.– Renta

Se pacta una renta de [IMPORTE] euros ( €). El pago de la renta se efectuará en los cinco primeros días de cada mes, mediante [ÓRGANO].

Quinta.– Fianza

Junto con la primera mensualidad de renta, y en concepto de fianza, a fin de responder del cumplimiento de la normativa vigente y del cumplimiento de este contrato y hasta donde lleguen los daños y perjuicios que pudiera causar en el inmueble, la PARTE ARRENDATARIA entrega en este acto la suma de .... euros en dicho concepto de fianza, que serán depositadas por la PARTE ARRENDADORA de acuerdo a lo dispuesto en la normativa aplicable.

Sexta.– Gastos/consumos/suministros

Será a cargo de la PARTE ARRENDATARIA la obligación de pago de los importes correspondientes a los consumos de luz, agua y demás suministros de que esté dotada la vivienda objeto del presente contrato. En garantía del cumplimiento de esta obligación se entrega, por parte de la PARTE ARRENDATARIA, la fianza a que se ha hecho referencia en la cláusula anterior.

Correrán por cuenta de la PARTE ARRENDADORA los gastos generales y de servicios individuales relativos al sostenimiento del inmueble, servicios, tributos, cargas, seguro general del inmueble, responsabilidades no individualizables, etc., que corresponda al mismo según cuota de participación en edificios que se encuentren en régimen de propiedad horizontal.

Séptima.– Obras de conservación

Serán de cargo y cuenta de la PARTE ARRENDATARIA todas aquellas obras que sean necesarias para la conservación de la vivienda, así como del mobiliario y enseres, en el estado en el que se alquilaron, siendo responsable de los posibles deterioros que pudieran originarse. Dicha responsabilidad alcanzará no sólo a los posibles deterioros causados por la persona del/la ARRENDATARIO/A, sino también a los posibles perjuicios y deterioros que pudieran causar el resto de ocupantes de la vivienda.

Octava.– Derecho de adquisición preferente

LA PARTE ARRENDATARIA renuncia expresa y formalmente, durante la vigencia del presente contrato al derecho reconocido en el artículo 31 [NOTA DE REVISIÓN (comprobar): Si el contrato es «vivienda temporal» (desde el 8-10-2026), se rige por el Título II y el art. 25.8 LAU impide pactar la renuncia al derecho de adquisición preferente. Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, arts. 2.3 y 25.8 (redacción RDL 29/2026, BOE-A-2026-20823 (convalidado: BOE-A-2026-23755)).] de la Ley 29/1994, de 24 de noviembre, de Arrendamientos Urbanos, de adquisición preferente sobre la vivienda arrendada en caso de que se produzca su venta.

Novena.– Cesión y subarriendo

La PARTE ARRENDATARIA no podrá subarrendar, total ni parcialmente, ni tampoco ceder la finca arrendada, salvo que conste para ello, el consentimiento expreso y escrito de la PARTE ARRENDADORA.

El incumplimiento de lo dispuesto en esta cláusula será causa válida para que la PARTE ARRENDADORA resuelva, de pleno derecho, el presente contrato de arrendamiento de temporada para uso vacacional.

Décima.– Finalización del arrendamiento

Llegada la fecha de vencimiento del contrato, éste quedará resuelto de forma automática, sin que haya necesidad de preaviso ni denuncia por ninguna de las partes.

Llegado dicho vencimiento la PARTE ARRENDATARIA deberá entregar las llaves a la PARTE ARRENDADORA.

Undécima.– Desistimiento unilateral de la parte arrendataria

En el supuesto de que, con carácter previo a que se produzca la finalización del contrato de arrendamiento por temporada por vencimiento de su término, la PARTE ARRENDATARIA abandonara la vivienda, desistiendo así del contrato, vendrá éste obligado a satisfacer a la PARTE ARRENDADORA el pago del importe total de la renta que se hubiera convenido [NOTA DE REVISIÓN (comprobar): En arrendamiento de vivienda temporal el arrendatario puede desistir pasado un mes con 10 días de preaviso sin indemnización (art. 11.2-3 LAU); depende de que el contrato encaje en esa figura (más de 31 días y causa de temporalidad). Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, art. 11 (redacción RDL 29/2026, BOE-A-2026-20823 (convalidado: BOE-A-2026-23755)).], en iguales condiciones y con las mismas características que si dicho desistimiento no se hubiera producido. Ello al objeto de paliar los posibles perjuicios que dicho abandono pudiere causar a la PARTE ARRENDADORA

Duodécima.– Resolución del contrato

Además de las causas de finalización del contrato de las cláusulas anteriores, será causas en virtud de las cuales la PARTE ARRENDADORA estará facultado para resolver de pleno derecho el contrato de arrendamiento por temporada, el impago de la renta pactada, de la fianza o de cualquiera del resto de cantidades cuyo pago se ha pactado a su cargo.

Decimotercera.– Jurisdicción

Las partes se someten a la Jurisdicción y Tribunales de [LOCALIDAD] para cuantas incidencias puedan surgir en la interpretación o cumplimiento de este contrato, por ser este el lugar donde se encuentra sita la finca, de conformidad con lo establecido en la vigente Ley de Enjuiciamiento Civil.

Y por todo ello los comparecientes, de plena conformidad, firman y rubrican el presente documento en todas sus hojas, por duplicado ejemplar y a un sólo efecto, en la ciudad y fecha que figura en el encabezamiento.

Arrendador/a	Arrendatario/a

Fdo. D./Dña. [NOMBRE Y APELLIDOS]: 	Fdo. D./Dña. [NOMBRE Y APELLIDOS]:
