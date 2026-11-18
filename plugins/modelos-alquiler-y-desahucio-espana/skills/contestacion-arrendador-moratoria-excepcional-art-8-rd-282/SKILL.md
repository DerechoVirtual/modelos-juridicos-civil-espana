---
name: contestacion-arrendador-moratoria-excepcional-art-8-rd-282
description: "Redacta el escrito «Contestación del arrendador a la moratoria excepcional del art. 8 RD 15/2020» (formulario 282 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación del arrendador a la moratoria excepcional del art. 8 RD 15/2020

> Formulario 0282 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

- Moratoria COVID de 2020 (art. 8 «RD 15/2020»): medida temporal ya agotada; plazo exacto NO VERIFICADO en el BOE.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 2 del RD 15/2020
- art. 2.2 del RDL 15/2020

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

### Formulario 0282 · Contestación del arrendador a la moratoria excepcional del art. 8 RD 15/2020

- Año del modelo: 2020
- Revisión 17-11-2026: 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)
- Avisos de la revisión: Moratoria COVID de 2020 (art. 8 «RD 15/2020»): medida temporal ya agotada; plazo exacto NO VERIFICADO en el BOE.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Sr. D. ………….… (arrendador),

calle ………………, núm. …, piso …, puerta ….,

de la localidad/ciudad de …….., provincia ……..

Al Sr. D. …………… (arrendatario),

calle ………………, núm. …, piso …, puerta ….,

de la localidad/ciudad de …….., provincia ……..

Estimado Sr. [NOMBRE Y APELLIDOS]:

Le dirijo la presente en su calidad de arrendatario en el contrato de arrendamiento urbano celebrado el día … sobre el local de negocio sito en ….., a fin de respuesta a su solicitud de aplazamiento temporal y extraordinario en el pago de la renta, recibida el pasado día……….., de conformidad con lo dispuesto en el art. 2 del RD 15/2020.

A la vista de la situación excepcional que estamos viviendo, estoy en disposición de acceder al aplazamiento de la renta mediante el fraccionamiento en seis mensualidades de la que se devengue entre el mes de abril de 2020 y la mensualidad siguiente a la finalización del estado de alarma, que les serían prorrateadas en los correspondientes recibos de renta vencidos posteriormente, sin que pueda superarse en ningún caso los cuatro meses de renta aplazada.

No puedo acceder al resto de condiciones que me propone puesto que, si bien me hago cargo de su situación, en mi caso me he visto seriamente afectado como consecuencia del impacto económico y social del COVID-19, lo cual me ha producido una sustancial pérdida de ingresos, de ahí que me resulte extraordinariamente gravoso conceder un aplazamiento más allá del que le propongo como alternativa.

En cualquier caso, como segunda alternativa, le propongo la posibilidad de pagar las rentas de los meses de abril y mayo de 2020 con cargo a la fianza arrendaticia que tiene Vd. constituida, en las condiciones establecidas en el art. 2.2 del RDL 15/2020, y aplazar el fraccionamiento de las rentas adeudadas posteriormente a la mensualidad siguiente a la de los dos meses de finalización del estado de alarma.

En caso de que Vd. no estuviera de acuerdo con esta solución, quedo a su disposición a fin de negociar un acuerdo.

En otro caso, solicito de Vd. la comunicación expresa de su decisión sobre las alternativas que le propongo que son: 1) aplazamiento fraccionado de la renta devengada en seis mensualidades, sin que en ningún caso pueda superar los cuatro meses; y 2) pago de las rentas de abril y mayo de 2020 con cargo a la fianza arrendaticia, y aplazamiento fraccionado en los términos expuestos a partir de la mensualidad siguiente a los dos meses de finalización del periodo de alarma, sin que en ningún caso pueda superar los cuatro meses contado desde junio de 2020.

Atentamente,

En la localidad/ciudad de ……., a … de … del año ...

Fdo.: ………………… (El arrendador)
