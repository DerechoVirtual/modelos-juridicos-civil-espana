---
name: compraventa-bien-tronquero-llamamiento-previo-pais-vasco-584
description: "Redacta el escrito «Compraventa de bien tronquero con llamamiento previo (País Vasco)» (formulario 584 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Compraventa de bien tronquero con llamamiento previo (País Vasco)

> Formulario 0584 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] FECHA
- [ ] NÚMERO (4 veces)
- [ ] IMPORTE (2 veces)
- [ ] Nº (2 veces)
- [ ] DESCRIBIR
- [ ] Otros 30 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…otario del Ilustre Colegio y Distrito de»; «…, con residencia en»; «…RAVENTA, y al efecto, EXPONEN I. Que Don»; «…ular de la siguiente finca: -Descripción»; «…(superficie de»; «…ra en régimen de propiedad horizontal de»; «…. - Título: Pertenece Don»; «…por compra a Don»; «…de»; «…de [COMPLETAR] de»; «…de [COMPLETAR] ante el Notario de»; «…ante el Notario de [COMPLETAR], Don»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 76 de la Ley 5/2015

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

### Formulario 0584 · Compraventa de bien tronquero con llamamiento previo (País Vasco)

- Año del modelo: 2016
- Revisión 17-11-2026: 40 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Ante mí, Notario del Ilustre Colegio y Distrito de [COMPLETAR], con residencia en [COMPLETAR].

INTERVIENEN

A) El primero en su propio nombre y derecho, denominado en lo sucesivo el VENDEDOR.

B) El segundo en su propio nombre y derecho, denominado en lo sucesivo el COMPRADOR.

Les conozco, y tienen, a mi juicio, como intervienen, la capacidad legal necesaria para formalizar la presente ESCRITURA DE COMPRAVENTA, y al efecto,

EXPONEN

I. Que Don [COMPLETAR] es titular de la siguiente finca:

-Descripción [COMPLETAR] (superficie de [COMPLETAR]. Con una cuota de participación en el conjunto del inmueble en el que se integra en régimen de propiedad horizontal de [COMPLETAR].

- Título: Pertenece Don [COMPLETAR] por compra a Don [COMPLETAR], según escritura pública otorgada el día [FECHA] de [COMPLETAR] de [COMPLETAR] ante el Notario de [COMPLETAR], Don [COMPLETAR], bajo el número [NÚMERO] de su protocolo.

-Cargas y gravámenes: Según nota simple informativa del Registro de la Propiedad correspondiente, obtenida por medio de telefax, en la fecha que figura en la misma, de la que deduzco copia que incorpora a esta matriz, de conformidad con lo previsto en el apartado primero del artículo 175 del Reglamento Notarial, y según manifestaciones de la parte propietaria, la finca descrita se halla libre de cargas y de gravámenes.

Manifiesta igualmente la parte vendedora que la finca descrita se halla asimismo libre de ocupantes, inquilinos y precaristas y al corriente en el pago de contribuciones, impuestos y gastos generales de la comunidad de propietarios que justifica mediante certificación expedida en los términos previstos la Ley de Propiedad Horizontal.

- Inscripción: Se halla inscrita a su favor en el Registro de la Propiedad número [NÚMERO] de [COMPLETAR], tomo [COMPLETAR], libro [COMPLETAR], folio [COMPLETAR], finca número [NÚMERO], inscripción [COMPLETAR].

Advierto que sobre la expresada información prevalecerá la situación registral preexistente a la presentación en el Registro de la copia autorizada de este instrumento.

II. Que tienen convenida la enajenación de la finca descrita en el anterior expositivo I de esta escritura, lo que formalizan con arreglo a las siguientes

III.- Que ha sido realizado el llamamiento a los parientes tranqueros previsto en el artículo 76 de la Ley 5/2015 de Derecho Civil Foral del País Vasco mediante acta autoriza por mí el [COMPLETAR] con el número [NÚMERO] de protocolo sin que ningún pariente tranquero haya ejercitado su derecho de adquisición preferente.

ESTIPULACIONES

Don [COMPLETAR] vende el pleno dominio de la finca urbana descrita en el apartado primero de la exposición a Don [COMPLETAR], que la compra y recibe para su sociedad conyugal y libre de cargas.

El precio de esta venta es de [IMPORTE] EUROS ( €), de las que los compradores entregan en el acto la cantidad de [IMPORTE] EUROS ( €) mediante cheque bancario núm. [Nº], fechado [COMPLETAR] y expedido por la entidad financiera [COMPLETAR], sucursal de [COMPLETAR].

El resto por una cuantía igual de [COMPLETAR] se pagará en [COMPLETAR] plazos mensuales, mediante el ingreso los [Nº] días primeros de cada mes.

La falta de pago de cualquiera de las fracciones del precio aplazado actuará como condición resolutoria explícita de la presente compraventa, que operará de forma automática una vez efectuado requerimiento notarial fehaciente a la compradora y poniendo a disposición de la misma, las cantidades entregadas a cuenta del precio de venta, con deducción de un [COMPLETAR] por ciento de las cantidades entregadas, en concepto de indemnización por daños y perjuicios.

Todos los gastos e impuestos que se deriven del otorgamiento del presente contrato serán satisfechos por la parte [COMPLETAR], al igual que los que deriven de la inscripción en el Registro de la Propiedad, impuestos sobre transmisiones patrimoniales y actos jurídicos documentados e impuesto municipal sobre el incremento de valor de los terrenos.

OTORGAMIENTO

Hago las reservas y advertencias legales, entre ellas las fiscales y advierto a las partes de la necesidad de presentar esta escritura a autoliquidación y de las consecuencias que se derivarían de la inexactitud de sus declaraciones.

Les leo el contenido de esta escritura a los comparecientes, previa advertencia y renuncia al derecho que tienen para hacerlo por sí, del que les enteros y hallándola conforme, se ratifican y firman conmigo. Doy fe de su identidad a través de la exhibición de sus DNI y demás documentos aportados, así como del contenido total de este instrumento público que queda extendido sobre [DESCRIBIR] folios de clase [COMPLETAR], de la Serie [COMPLETAR], números [COMPLETAR] y el presente.

El vendedor	El comprador
Fdo.:	Fdo.:

========================================================================
