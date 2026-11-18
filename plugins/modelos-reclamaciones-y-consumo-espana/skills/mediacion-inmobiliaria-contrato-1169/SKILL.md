---
name: mediacion-inmobiliaria-contrato-1169
description: "Redacta el escrito «Mediación inmobiliaria: contrato» (formulario 1169 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Mediación inmobiliaria: contrato

> Formulario 1169 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] FECHA (6 veces)
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] DNI/NIE (2 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] LOCALIDAD (2 veces)
- [ ] NIF
- [ ] NÚMERO (3 veces)
- [ ] Nº (6 veces)
- [ ] IMPORTE (14 veces)
- [ ] CALLE (2 veces)
- [ ] PLAZO
- [ ] Otros 27 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, mayor de edad, vecino/a de»; «…, mayor de edad, vecino/a»; «…, Notario de»; «…, Notario de [COMPLETAR], el»; «… entre otras, las siguientes facultades:»; «…, válido hasta»; «…les a partir del día uno del próximo mes»; «…del corriente año»; «…euros. —»; «…rgante/s recibirán totalmente terminados»; «…os/ — El/la los/as Otorgante/s recibirán»; «…viviendas de»; …

## Elecciones que hay que hacer

- vender / permutar / arrendar / constituir un derecho de superficie sobre / constituir un derecho de habitación sobre / edificar / urbanizar / traspasar
- comprar / vender / arrendar / arrendar mediante traspaso / construir el solar y abonar el precio mediante permuta
- del otorgamiento de la escritura pública / del otorgamiento de las arras / de la firma del contrato de arrendamiento / de la firma del documento privado de venta / de la permuta / del traspaso
- el traspaso / la aportación / el precio de venta / la renta anual
- para que proceda a firmar el correspondiente contrato / pudiendo el Mediador firmar el correspondiente documento de arras/paga/señal

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS

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

### Formulario 1169 · Mediación inmobiliaria: contrato

- Año del modelo: 2015
- Revisión 17-11-2026: 5 desplegables convertidos en elección en blanco; 1 bloques de alternativas señalados; 70 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (FECHA)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [FECHA].

REUNIDOS

DE UNA PARTE, D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, vecino/a de [COMPLETAR], con DNI n.º [DNI/NIE], en lo sucesivo denominado EL OTORGANTE.

Y DE OTRA PARTE, D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, vecino/a [COMPLETAR], con DNI n.º [DNI/NIE], en lo sucesivo EL MEDIADOR.

INTERVIENEN

EL OTORGANTE en su propio nombre y derecho.

EL MEDIADOR, en representación de la mercantil [NOMBRE DEL REPRESENTADO/A], con domicilio en [LOCALIDAD] y NIF número [NIF] en uso del poder otorgado ante D./Dña. [NOMBRE Y APELLIDOS], Notario de [COMPLETAR], el [COMPLETAR], bajo el número [NÚMERO] de los de su protocolo, y por medio del cual se halla facultado para ejercitar, entre otras, las siguientes facultades: [COMPLETAR].

Se reconocen mutuamente con capacidad suficiente para otorgar el presente contrato de MEDIACIÓN INMOBILIARIA y a tal fin,

EXPONEN

I.- EL OTORGANTE

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

es propietario de la siguiente finca que se reseña a continuación:

es arrendatario según contrato de fecha [FECHA], de [Nº] años de duración y con una renta mensual de [IMPORTE] euros del siguiente inmueble:

es arrendatario según contrato de fecha [FECHA], con prórroga forzosa y una renta mensual de [IMPORTE] euros del siguiente inmueble:

es arrendatario según contrato de fecha [FECHA], válido hasta [COMPLETAR] y una renta mensual de [IMPORTE] euros del siguiente inmueble:

es arrendatario según contrato de fecha [FECHA], con derecho de traspaso y una renta mensual de [IMPORTE] euros del siguiente inmueble:

está interesado en comprar el siguiente inmueble:

está interesado en arrendar mediante traspaso el siguiente inmueble:

está interesado en adquirir por permuta el siguiente inmueble:

está interesado en promover la edificación de un edificio en:

II.- EL OTORGANTE desea [ELEGIR: vender / permutar / arrendar / constituir un derecho de superficie sobre / constituir un derecho de habitación sobre / edificar / urbanizar / traspasar] el inmueble descrito en el expositivo I y para que el Mediador encuentre la persona física o jurídica interesada en [ELEGIR: comprar / vender / arrendar / arrendar mediante traspaso / construir el solar y abonar el precio mediante permuta], convienen el presente contrato en base a las siguientes

ESTIPULACIONES

Primera.- EL OTORGANTE conviene con EL MEDIADOR un contrato de mediación inmobiliaria o corretaje, con el fin de que gestione y proporcione un cliente interesado en el negocio que se especifica en la estipulación TERCERA.

Segunda.- El presente contrato de mediación tendrá la duración de [Nº] meses, computables a partir del día uno del próximo mes [COMPLETAR] del corriente año [COMPLETAR], pero se entenderá prorrogado por periodos sucesivos de un mes, salvo preaviso fehaciente de alguna de las partes con 10 días de antelación a la terminación de cada uno de dichos meses.

El presente contrato de mediación quedará extinguido por la consecución de su fin.

Tercera.- Objeto

a) Las condiciones en que la parte Otorgante está interesada en suscribir la compraventa son:

— Precio [IMPORTE] euros.
— Plazo de pago contado/ meses/ años.
— El comprador no/se subrogará en la hipoteca.
— Las arras serán de un mínimo de [IMPORTE] euros.
— [COMPLETAR]

b) Las condiciones en que se pactará la permuta son:

— Plazo de ejecución de la obra [Nº] meses/años y la entrega de los locales/viviendas a los interesados será de [Nº] meses/años. Ambas fechas a partir del día de hoy.
— El/la los/as Otorgante/s recibirán totalmente terminados [COMPLETAR] m² de locales en planta baja, diáfanos/con servicios/con tabiquería/enyesados/
— El/la los/as Otorgante/s recibirán [COMPLETAR] viviendas de [COMPLETAR] m² de superficie útil/ construida, sitas en la planta / en la planta / [COMPLETAR] en la planta /con cédula de habitabilidad y licencia de primera ocupación/
— El arquitecto y aparejador será designado por el/la lo/as Otorgante/s/ por los constructores permutantes/por [COMPLETAR]
— Las calidades mínimas de las viviendas serán [COMPLETAR]

c) Las condiciones en las que está interesado en arrendar como arrendatario son:

— Local de entre [COMPLETAR] y [COMPLETAR] metros.
— Destinado a oficina/ vivienda/ industria
— En el área [COMPLETAR] de la ciudad de [COMPLETAR]
— Renta mensual total entre [COMPLETAR] y [IMPORTE] euros.
— Plazo máximo/mínimo de duración V
— Todos los gastos de gestión y redacción del contrato serán de cargo del arrendatario/arrendador.

d) Las condiciones en que se arrendará el local/ vivienda/ oficina/ nave industrial/ son:

— Renta mensual [IMPORTE] euros, IVA, si procede, aparte.
— Plazo de duración [Nº] años.
— No/se autorizarán obras en la finca.
— Podrán desarrollarse en el local/nave las actividades de - Todos los gastos de gestión y redacción del contrato serán de cargo del arrendatario/arrendador.

e) El Otorgante desea traspasar el local sobre la base de:

— Obtener un importe por traspaso de [IMPORTE] euros.
— No/quedará incluida en el traspaso/la instalación existente/el mobiliario/existencias por importe de [IMPORTE] euros, que/no se incluyen en el precio fijado.
— Los gastos de gestión y redacción serán de cargo de [COMPLETAR]

f) El Otorgante desea adquirir terrenos a cambio de ejecutar la urbanización:

— Con una proporción mínima de que se le adjudique un [COMPLETAR] tanto por 100 de los derechos de edificación que se pueda realizar en los terrenos que se urbanicen.
— Los terrenos serán aptos para la edificación de/viviendas unifamiliares/plurifamiliares/naves industriales/locales comerciales

g) El Otorgante desea adquirir en traspaso un local:

— En la calle [CALLE] número [NÚMERO]
— Por un importe máximo de [IMPORTE] euros, a pagar por derechos de traspaso.
— Con un mínimo de [Nº] años de vigencia de contrato.
— Con una renta mensual de [IMPORTE] euros.
— El local estará en planta baja/primer piso/
— Tendrá una superficie mínima de [COMPLETAR] m² y máxima de [COMPLETAR] m².

h) El Otorgante encarga al Mediador que contacte con capitalistas que deseen colaborar como inversores en la ejecución de un edificio en la calle/plaza/avenida [CALLE], número [NÚMERO], de [COMPLETAR], admitiéndose aportaciones de entre [IMPORTE] euros y [IMPORTE] euros, a aportar en un plazo de [PLAZO], según el proyecto del arquitecto D./Dña. [NOMBRE Y APELLIDOS] habiéndose obtenido licencia del Ayuntamiento el día [FECHA]

Cuarta.- Si el Mediador hace uso o colaboración de otros profesionales, cualquiera que sea su trabajo de publicidad u otros medios, correrán de cargo del mismo cuantos honorarios y gastos devenguen, salvo pacto expreso y escrito.

Quinta.- En concepto de honorarios o corretaje el Mediador recibirá en el momento [ELEGIR: del otorgamiento de la escritura pública / del otorgamiento de las arras / de la firma del contrato de arrendamiento / de la firma del documento privado de venta / de la permuta / del traspaso], en las condiciones de la ESTIPULACIÓN TERCERA, un% sobre el valor o precio fijado en el [ELEGIR: el traspaso / la aportación / el precio de venta / la renta anual]

Sexta.- Los impuestos y gastos, tanto del presente contrato como de los contratos que se deriven del mismo o que resulten de la mediación, salvo pacto expreso y escrito entre las partes que intervengan, correrán de cargo de quien corresponda según ley y en especial estarán sujetos los honorarios, comisión o corretaje al Impuesto Sobre el Valor Añadido, entregando en su momento el Otorgante la correspondiente factura.

Séptima.- Cuando el Mediador encuentre la persona física o jurídica que esté interesada en el contrato de [COMPLETAR] notificará por escrito mediante telegrama, burofax o cualquier otro medio del que quede constancia al Otorgante [ELEGIR: para que proceda a firmar el correspondiente contrato / pudiendo el Mediador firmar el correspondiente documento de arras/paga/señal] con un pago a disposición del Otorgante y por cuenta del mismo de [COMPLETAR] por 100 del precio.

Octava.- Las partes con renuncia a su fuero propio, si lo tuvieran, se someten a los Tribunales de [LOCALIDAD]

Y en prueba de conformidad, firman el presente por duplicado ejemplar y a un solo fin, en el lugar y fecha indicados al principio.

EL OTORGANTE

EL MEDIADOR

Firmado: D./Dña. [NOMBRE Y APELLIDOS] 	Firmado: D./Dña. [NOMBRE Y APELLIDOS]

========================================================================
