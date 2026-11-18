---
name: arrendamiento-uso-distinto-vivienda-garantias-1217
description: "Redacta el escrito «Arrendamiento para uso distinto de vivienda con garantías» (formulario 1217 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Arrendamiento para uso distinto de vivienda con garantías

> Formulario 1217 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] CALLE (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] FECHA
- [ ] IMPORTE (3 veces)
- [ ] Nº
- [ ] LOCALIDAD
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] Otros 21 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Que el arrendador es propietario de»; «…situado en la C/ [CALLE] de»; «…de»; «…de [COMPLETAR] al Tomo»; «…e [COMPLETAR] al Tomo [COMPLETAR], Folio»; «…, Folio [COMPLETAR], Finca»; «…de»; «…o del presente contrato será destinada a»; «…de uso. La duración del contrato será de»; «…esistir del contrato una vez cumplido el»; «… arrendador con una antelación mínima de»; «…rato se dejara sin efecto de esta manera»; …

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: En nombre / En nombre propio y derecho / En nombre y representación — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: En nombre / En nombre propio y derecho / En nombre y representación — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Medio / Domicilio arrendador / Inmueble alquilado / Ingreso/Transferencia — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Aval bancario / Aval bancario / Letras de cambio / Avalista — el texto de cada opción no venía en el formulario original

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 1124 del Código Civil
- Real Decreto 390/2021

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

### Formulario 1217 · Arrendamiento para uso distinto de vivienda con garantías

- Año del modelo: 2013
- Revisión 17-11-2026: 4 bloques de opciones sin texto dejados en blanco con sus rótulos; 34 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [DÍA] de [MES] de [AÑO].

EXPONEN

Que el primero, en adelante el arrendador, comparece:

[ELEGIR UNA OPCIÓN Y REDACTARLA: En nombre / En nombre propio y derecho / En nombre y representación — el texto de cada opción no venía en el formulario original]

Que el segundo en adelante el arrendatario, comparece:

[ELEGIR UNA OPCIÓN Y REDACTARLA: En nombre / En nombre propio y derecho / En nombre y representación — el texto de cada opción no venía en el formulario original]

Que el arrendador es propietario de [COMPLETAR] situado en la C/ [CALLE] de [COMPLETAR], según consta en el Registro de la Propiedad n.º [NÚMERO] de [COMPLETAR] al Tomo [COMPLETAR], Folio [COMPLETAR], Finca [COMPLETAR] que se describe de la forma que sigue:

Su referencia catastral es la n.º [NÚMERO]

La finca descrita goza del certificado de eficiencia energética regulado en el Real Decreto 390/2021, de 1 de junio. Se entrega al arrendatario la firma de este contrato una copia de dicho documento en virtud de lo exigido en el artículo único de la citada norma.

Que ambas partes se reconocen mutua y recíprocamente capacidad suficiente para suscribir el presente contrato de arrendamiento para uso distinto de vivienda conforme a las siguientes

El objeto del presente contrato es la finca urbana situada en la C/ [CALLE] de [COMPLETAR] descrita en el apartado III del epígrafe «exponen».

La finca objeto del presente contrato será destinada a [COMPLETAR], no pudiendo variar dicho destino sin conocimiento y consentimiento expreso del arrendador.

El arrendatario recibe en este acto las llaves de la finca arrendada, toma posesión de la misma y declara haberla examinado y encontrarla a su total y entera satisfacción, reconociendo que se encuentra en estado de servir para el uso a que se destina. A la extinción del contrato deberá devolverla en este estado, salvo el desgaste ordinario de uso.

La duración del contrato será de [COMPLETAR] año/s contados a partir de la fecha de este documento. Finalizará su vigencia, por tanto el día [FECHA].

No obstante, podrá la parte arrendataria desistir del contrato una vez cumplido el [COMPLETAR] año de vigencia previo aviso fehaciente al arrendador con una antelación mínima de [COMPLETAR].

Si el contrato se dejara sin efecto de esta manera [COMPLETAR]:

Si el arrendatario desistiera antes del plazo mínimo señalado deberá abonar todas las rentas que hubiera debido hacer efectivas hasta cubrir dicho plazo.

La renta mensual será de [IMPORTE] euros más el correspondiente IVA, que se abonará por mensualidades anticipadas en los cinco primeros días del mes. Mensualmente se practicará también por el arrendatario la retención a cuenta del impuesto [COMPLETAR] que se obliga a ingresar con la periodicidad que corresponda en la Hacienda Pública. Todos los gastos, perjuicios y pagos que se vea obligado a realizar la parte arrendadora como consecuencia del incumplimiento de esta obligación podrán ser reclamados por ésta al arrendatario.

La forma de pago será mediante abono de la cantidad [IMPORTE]:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Medio / Domicilio arrendador / Inmueble alquilado / Ingreso/Transferencia — el texto de cada opción no venía en el formulario original]

Todos los gastos de uso, consumo y suministros propios de la finca correrán por cuenta del arrendatario, al igual que los correspondientes a las cuotas ordinarias de la Comunidad de Propietarios donde se encuentra. A este efecto el arrendatario procederá a liquidar directamente esta cuota en la forma que se le indique por el Presidente de la Comunidad, ya sea mediante pago directo o mediante ingreso en cuenta bancaria.

El arrendatario se obliga a abonar todos los gastos, tasas e impuestos que se devenguen con ocasión del otorgamiento del presente contrato. También deberá abonar el impuesto sobre bienes inmuebles (IBI) de una sola vez junto con la mensualidad siguiente a la fecha en que reciba copia del recibo pagado por el arrendador.

Tal y como se ha indicado, el arrendatario se obliga también a abonar el correspondiente IVA y a practicar las retenciones a cuenta sobre el impuesto [COMPLETAR] legalmente exigibles sobre la renta que se abone en cada momento.

Se autoriza al arrendatario a realizar las obras necesarias para la instalación del negocio de [COMPLETAR] y adecuación del inmueble a tal fin.

Aparte de estas obras el arrendatario [COMPLETAR] podrá efectuar obras en la finca sin el consentimiento expreso y por escrito de la propiedad. Las obras o mejoras así ejecutadas que no puedan separarse del inmueble sin daño quedarán en poder de la propiedad al término del arrendamiento sin que ello dé derecho al arrendatario a indemnización o compensación.

El arrendatario está obligado a reparar y reponer los siguientes elementos de la finca que se deterioren dejando de servir para su uso, debiendo, no obstante, poner en conocimiento de la propiedad la ejecución de las obras. También corre por cuenta del arrendatario la realización de las revisiones e inspecciones de las instalaciones individuales de suministros o servicios.

En caso de transmisión de la vivienda el arrendador se obliga a notificar dicha transmisión a la parte arrendataria y ésta, si fuera necesario, a otorgar los documentos necesarios para regularizar la nueva situación. Los derechos de tanteo y retracto se regulan según lo previsto en los artículos 25 y 31 de la Ley de Arrendamientos Urbanos.

Se [COMPLETAR] la cesión del presente contrato y el subarriendo total o parcial de la finca.

El arrendatario entrega en este acto la cantidad de [IMPORTE] euros, equivalente a dos mensualidades de renta, en concepto de fianza, a la que se dará el destino legal oportuno. Se autoriza expresamente al arrendador a hacerla suya si al finalizar el contrato hubiera que realizar reparaciones por desperfectos causados por el arrendatario o quedara alguna renta pendiente de abonar, sin perjuicio de ulterior reclamación por la cantidad que reste de abonar.

 La fianza señalada será actualizada a partir del [COMPLETAR] año de vigencia del contrato en el mismo porcentaje y forma estipulados para la actualización de la renta.

[ELEGIR UNA OPCIÓN Y REDACTARLA: Aval bancario / Aval bancario / Letras de cambio / Avalista — el texto de cada opción no venía en el formulario original]

El incumplimiento por cualquiera de las partes de las obligaciones de este contrato dará derecho a la parte que hubiera cumplido las suyas a exigir el cumplimiento de la obligación o a promover la resolución del contrato de acuerdo con lo dispuesto en el artículo 1124 del Código Civil.

El incumplimiento de las obligaciones pecuniarias del arrendatario dará derecho al arrendador a exigir al arrendatario un interés anual sobre la cifra impagada de [Nº] puntos por encima del interés legal del dinero hasta su pago, y a reclamarle, si hubiere de procederse judicialmente para su reclamación o resolución del contrato, todos los gastos, incluso los honorarios del Letrado y Procurador, aunque su utilización no sea preceptiva.

Serán de cuenta y cargo de la parte que incumpliere el presente contrato todos los gastos derivados del incumplimiento, costas procesales, inclusive tasa fiscal y honorarios de Abogado y Procurador, incluso si no fuera preceptiva su intervención.

Las partes acuerdan someterse a los Tribunales de [LOCALIDAD] para dilucidar cualquier tipo de cuestión litigiosa a que pudiera dar lugar la interpretación y cumplimiento del presente documento.

Y para que conste y surta efecto suscriben las partes [COMPLETAR] este documento que consta de [COMPLETAR] folios en cada uno de ellos de los [COMPLETAR] ejemplares, en el lugar y fecha indicados en el encabezamiento.

Fdo.: D./Dña. [NOMBRE Y APELLIDOS] Fdo.: D./Dña. [NOMBRE Y APELLIDOS]

========================================================================
