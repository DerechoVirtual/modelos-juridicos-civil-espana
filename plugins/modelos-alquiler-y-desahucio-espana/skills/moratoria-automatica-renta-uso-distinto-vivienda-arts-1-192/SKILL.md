---
name: moratoria-automatica-renta-uso-distinto-vivienda-arts-1-192
description: "Redacta el escrito «Moratoria automática de renta en uso distinto de vivienda (arts. 1 y 2 RDL 35/2020)» (formulario 192 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Moratoria automática de renta en uso distinto de vivienda (arts. 1 y 2 RDL 35/2020)

> Formulario 0192 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

- Moratoria COVID para uso distinto (RDL 35/2020): medida temporal de 2020-2021 ya agotada; plazo exacto NO VERIFICADO en el BOE.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] FECHA (2 veces)
- [ ] LOCALIDAD
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] LUGAR
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Calle [CALLE] nº [NÚMERO], piso»; «…Calle [CALLE] nº [NÚMERO], piso»; «…ocal arrendado desempeño mi actividad de»; «…lta de forma ininterrumpida desde el año»; «…accionamiento aplazado de su pago en las»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 2 del RDL 35/2020
- art. 1 del RDL 35/2020
- art. 1.3 del RDL 35/2020
- Real Decreto-ley 35/2020

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

### Formulario 0192 · Moratoria automática de renta en uso distinto de vivienda (arts. 1 y 2 RDL 35/2020)

- Año del modelo: 2021
- Revisión 17-11-2026: 15 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)
- Avisos de la revisión: Moratoria COVID para uso distinto (RDL 35/2020): medida temporal de 2020-2021 ya agotada; plazo exacto NO VERIFICADO en el BOE.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Carta-tipo solicitando moratoria sobre deuda arrendaticia en arrendamiento para uso distinto al de vivienda al amparo del Real Decreto-ley 35/2020, de 22 de diciembre, de medidas urgentes de apoyo al sector turístico, la hostelería y el comercio y en materia tributaria.

D./Dña. [NOMBRE Y APELLIDOS]

Calle [CALLE] nº [NÚMERO], piso [COMPLETAR]

A D./Dña. [NOMBRE Y APELLIDOS]

Calle [CALLE] nº [NÚMERO], piso [COMPLETAR]

Estimado Sr/a.:

Le dirijo la presente en su calidad de arrendador en el contrato de arrendamiento urbano celebrado el día [FECHA] sobre el local sito en [LOCALIDAD], a fin de solicitar, de conformidad con lo dispuesto en el art. 2(o en caso de gran tenedor o entidad pública del 1 del RDL 35/2020) una MORATORIA AUTOMÁTICA de la renta arrendaticia adeudada entre el día 24 de diciembre de 2020 y hasta que finalice el periodo de alarma y sus prórrogas, cuya ampliación solicitaría con posterioridad a la finalización de ese periodo en caso de mantenerse mi situación de vulnerabilidad, hasta el máximo legal de cuatro meses.

Como Vd. conoce en el local arrendado desempeño mi actividad de [COMPLETAR], la cual se ha visto muy gravemente afectada por las medidas adoptadas como consecuencia de la situación de emergencia sanitaria, con pérdida sustancial de ingresos, que me dejan en una complicada situación económica al constituir dicho negocio mi único medio de ingresos.

Por ello, solicito esta moratoria al amparo del citado art. 2 del RDL 35/2020 (o, en su caso, al amparo del citado art. 1 del RDL 35/2020, al ser conocedor que Vd. es titular de más de diez inmuebles en alquiler, al ser el arrendador de todos los pisos y locales de la finca en la que tengo mi negocio), y dada mi situación de vulnerabilidad económica a consecuencia de la emergencia sanitaria ocasionada por el COVID-19, al haberse reducido mi facturación en más de un 75% en el mes de diciembre de 2020 en relación a la media mensual del primer trimestre del año 2019.

El negocio que desarrollo en el local arrendado es mi único medio de vida como autónomo, estando en situación de alta de forma ininterrumpida desde el año [COMPLETAR], acreditando esta circunstancia y la de crisis derivada del COVID-19 con la siguiente documentación que adjunto:

Documento nº [Nº DE DOCUMENTO]: Certificado expedido por la Seguridad Social de alta en el RETA.

Documento nº [Nº DE DOCUMENTO]: Declaración responsable de reducción de más del 75 % de la facturación en base a la información contable de ingresos y gastos, aportando copia de los apuntes contables y declaraciones tributarias en soporte electrónico.

Sin perjuicio de que Vd. puede elegir la alternativa más adecuada a sus intereses, le manifiesto que sería suficiente un aplazamiento temporal de la deuda con fraccionamiento aplazado de su pago en las [COMPLETAR] mensualidades siguientes a la de finalización del aplazamiento, si Vd. lo considerara oportuno.

En caso de que Vd. tuviera la intención de buscar otra solución de consuno, quedo a su disposición a fin de negociar un acuerdo.

En otro caso, solicito de Vd. la comunicación expresa de su decisión en el plazo de siete días laborables fijado en el art. 1.3 del RDL 35/2020.

Lo que se hace constar a los efectos oportunos en [LUGAR], a [FECHA].

Firma del arrendatario
