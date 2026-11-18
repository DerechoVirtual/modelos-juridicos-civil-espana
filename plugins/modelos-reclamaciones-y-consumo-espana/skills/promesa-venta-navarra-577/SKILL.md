---
name: promesa-venta-navarra-577
description: "Redacta el escrito «Promesa de venta (Navarra)» (formulario 577 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Promesa de venta (Navarra)

> Formulario 0577 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE
- [ ] FECHA (4 veces)
- [ ] NÚMERO (3 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] IMPORTE (5 veces)
- [ ] Otros 25 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…reforma del RDL 29/2026. En la ciudad de»; «…, a [DÍA] de [MES] de [AÑO] EXPONE Que»; «…, calle [CALLE], piso»; «…, calle [CALLE], piso [COMPLETAR], letra»; «…. TÍTULO. Pertenece a Don»; «…por compra a Don»; «…de»; «…de [COMPLETAR] de»; «…de [COMPLETAR] ante el Notario de»; «…ante el Notario de [COMPLETAR], Don»; «…de»; «…de [COMPLETAR], tomo»; …

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 0577 · Promesa de venta (Navarra)

- Año del modelo: 2016
- Revisión 17-11-2026: 40 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (IMPORTE, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma del RDL 29/2026.

En la ciudad de [COMPLETAR], a [DÍA] de [MES] de [AÑO]

EXPONE

Que [COMPLETAR] es propietario en pleno dominio de la siguiente finca:

DESCRIPCIÓN: Vivienda sita en [LOCALIDAD], calle [CALLE], piso [COMPLETAR], letra [COMPLETAR].

TÍTULO. Pertenece a Don [COMPLETAR] por compra a Don [COMPLETAR], según escritura pública otorgada el día [FECHA] de [COMPLETAR] de [COMPLETAR] ante el Notario de [COMPLETAR], Don [COMPLETAR], bajo el número [NÚMERO] de su protocolo.

INSCRIPCIÓN. Se halla inscrita a su favor en el Registro de la Propiedad número [NÚMERO] de [COMPLETAR], tomo [COMPLETAR], libro [COMPLETAR], folio [COMPLETAR], finca número [NÚMERO], inscripción [COMPLETAR].

CARGAS Y SITUACIÓN POSESORIA. Se encuentra libre de cargas y gravámenes según manifiesta expresamente la sociedad propietaria de la finca así como libre de arrendatarios y ocupantes.

ANTIGÜEDAD DE LA CONSTRUCCIÓN. Fue declarada la obra nueva mediante escritura otorgada ante el Notario de [COMPLETAR], el día [FECHA] de [COMPLETAR] de [COMPLETAR], número de protocolo [COMPLETAR].

REFERENCIA CATASTRAL:

Que Don [COMPLETAR] está interesado en la venta y Don [COMPLETAR] en la compra de la finca descrita en el expositivo, por lo que Don [COMPLETAR] otorga promesa de venta de la referida finca de acuerdo con las siguientes:

ESTIPULACIONES

Don [COMPLETAR] se compromete a vender a Don [NOMBRE Y APELLIDOS], la vivienda descrita en el apartado Primero de la parte expositiva de este contrato, con cuantos usos, derechos y servidumbres le correspondan, libre de cargas, gravámenes y de arrendatarios.

El precio de la futura compraventa ha sido establecido en [IMPORTE] euros, cuyo pago realizará la parte compradora de la siguiente forma:

- [IMPORTE] euros (en número, [IMPORTE] euros) a la firma del contrato privado de compraventa que se celebrará el día [FECHA], sirviendo el mismo como recibo y la más eficaz carta de pago. Dicha cantidad será entregada a cuenta del total del precio y en concepto de arras o paga y señal.

- Y la cantidad de [IMPORTE] euros (en número.- euros) a la firma de la escritura de compraventa que deberá otorgarse antes del día [FECHA] de [COMPLETAR].

La posesión será entregada por el vendedor al comprador el día de la firma de la escritura de compraventa

A partir de tal momento, serán de cargo y cuenta del comprador las contribuciones, tasas o impuestos que lo graven, siendo igualmente de su cargo los servicios y suministros del inmueble y los gastos, derramas o cuotas que deriven del régimen de propiedad horizontal.

Además de la plena propiedad del piso, la parte compradora adquirirá una porción o cuota proindiviso inseparable con la anterior, en las partes y elementos comunes del edificio en que se encuentra la vivienda objeto del presente contrato.

La escritura pública solemnizadora del contrato de compraventa se otorgará ante el Notario de elección del comprador, siendo de cuenta del mismo los gastos notariales que de dicha elevación se deriven así como por su inscripción en el Registro de la Propiedad y por el Impuesto de Transmisiones Patrimoniales aplicable. El impuesto municipal sobre el Incremento del Valor de los Terrenos de Naturaleza Urbana o Plusvalía, será de cuenta del vendedor.

La presente promesa de venta tiene un plazo de duración de [COMPLETAR], una vez transcurrido el mismo, se extinguirá la obligación que mediante el presente contrae el otorgante. La exigencia por parte de Don de que se lleve a efecto la promesa deberá ejercitarse de modo fehaciente dentro del indicado plazo, una vez transcurrido la promesa quedará sin efecto de modo automático, sin necesidad de acto o formalidad alguna ni notificación.

El incumplimiento por parte del promitente de la promesa de contrato de compraventa dará lugar a una indemnización a favor de Don por importe de [IMPORTE].

El enjuiciamiento de cualquier controversia que se suscite en la interpretación o cumplimiento del presente compromiso se somete a los Tribunales de [LOCALIDAD].

Y en prueba de conformidad con todo el contenido de este documento, lo firma el otorgante por duplicado ejemplar, en el lugar y fecha indicados en el encabezamiento.

Firmado: Don [NOMBRE Y APELLIDOS]

========================================================================
