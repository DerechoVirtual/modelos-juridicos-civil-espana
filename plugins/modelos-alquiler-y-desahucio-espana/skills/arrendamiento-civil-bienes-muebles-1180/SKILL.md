---
name: arrendamiento-civil-bienes-muebles-1180
description: "Redacta el escrito «Arrendamiento civil de bienes muebles» (formulario 1180 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Arrendamiento civil de bienes muebles

> Formulario 1180 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (2 veces)
- [ ] NIF (2 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] IMPORTE (3 veces)
- [ ] ÓRGANO
- [ ] CALLE (2 veces)
- [ ] Nº (2 veces)
- [ ] PROVINCIA (2 veces)
- [ ] Otros 20 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…En la localidad/ciudad de»; «…, a»; «…, a [COMPLETAR], de»; «…, a [COMPLETAR], de [COMPLETAR], del año»; «…REUNIDOS De una parte, D»; «…, en calidad de ARRENDADOR; Y de otra, D»; «…ánea y de mutuo acuerdo EXPONEN I. Que D»; «…ación El contrato tendrá una duración de»; «…euros (- €) cada una.»; «…, núm. [Nº], piso»; «…, núm. [Nº], piso [COMPLETAR], puerta»; «…, de la localidad/ciudad de»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Ley 5/2012

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

### Formulario 1180 · Arrendamiento civil de bienes muebles

- Año del modelo: 2015
- Revisión 17-11-2026: 34 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En la localidad/ciudad de [COMPLETAR], a [COMPLETAR], de [COMPLETAR], del año [COMPLETAR]

REUNIDOS

De una parte, D [COMPLETAR], mayor de edad, con domicilio en [LOCALIDAD] y titular del NIF [NIF], en calidad de ARRENDADOR;

Y de otra, D [COMPLETAR], mayor de edad, con domicilio en [LOCALIDAD] y titular del NIF [NIF], en calidad de ARRENDATARIO;

MANIFIESTAN

Que reconociéndose mutuamente las partes la capacidad legal necesaria a los efectos de este CONTRATO DE ARRENDAMIENTO DE BIENES MUEBLES, interviniendo en nombre y derecho propio, siendo responsables de la veracidad de sus manifestaciones, y de forma libre, espontánea y de mutuo acuerdo

EXPONEN

I. Que D [COMPLETAR] es dueño en pleno dominio del siguiente bien mueble no fungible:

(se describiría)

II. Que estando interesados D. [NOMBRE Y APELLIDOS] como parte arrendadora, y D. [NOMBRE Y APELLIDOS] como parte arrendataria en formalizar el arrendamiento del bien mueble indicado es por lo que celebran el presente CONTRATO DE ARRENDAMIENTO DE BIEN MUEBLE de acuerdo con las siguientes

CLÁUSULAS

Objeto y destino

El ARRENDADOR, por medio de este Contrato arrienda el bien mueble no fungible descrito en el Expositivo I, al ARRENDATARIO, que declara que el bien se encuentra en perfecto estado de conservación y lo encuentra apto para el fin a que va a destinarlo.

En este acto, el ARRENDADOR entrega al ARRENDATARIO dicho bien en perfecto estado de funcionamiento y mantenimiento, externa e internamente.

El ARRENDATARIO destinará el bien que alquila a su uso propio, de tal manera no lo podrá subarrendar, ni permitir que terceros lo utilicen.

(cláusulas opcionales El ARRENDATARIO será el único que podrá conducir el vehículo, utilizar el ordenador, utilizar la maquinaria, etc.).

Duración

El contrato tendrá una duración de [COMPLETAR], a contar desde la fecha de este contrato.

El contrato podrá ser prorrogado de mutuo acuerdo por las partes, antes del vencimiento del mismo.

Precio y actualización

La renta de este contrato se fija en la cantidad de [IMPORTE] euros anuales (- €), pagaderos por mensualidades anticipadas de [IMPORTE] euros (- €) cada una. [COMPLETAR].

Se verificarán los pagos por meses anticipados y dentro de los cinco primeros días de cada mes, mediante [ÓRGANO]

(en su caso) El precio convenido incluye/no incluye el pago del transporte encargado de realizar la entrega y la posterior retirada de los muebles y demás accesorios, el cual deberá ser soportado exclusivamente a costa de

La renta se revisará anualmente a partir de la fecha de este documento por aplicación de las variaciones que experimente el Índice General de Precios al Consumo, Conjunto Nacional, que elabore el Instituto Nacional de Estadística u Organismo que, en su caso, lo sustituya, en los doce meses anteriores a la fecha de efectos de cada actualización, y se aplicará sobre la Renta vigente que corresponda al mes anterior a aquél en que se deba realizar la actualización.

Obligaciones del arrendador

El ARRENDADOR garantiza la posesión legal y pacífica del bien arrendado, respondiendo en virtud del saneamiento en los términos establecidos en el Código Civil.

Obligaciones del arrendatario

El ARRENDATARIO se obliga y asume todas las responsabilidades que tal condición implica, hasta proceda la devolución del artículo al ARRENDADOR, en especial las siguientes:

– El ARRENDATARIO queda obligado a satisfacer puntualmente la renta y a poner toda diligencia en la conservación de las cosas y muebles alquilados, asumiendo la entera y absoluta responsabilidad de todo deterioro que éstas sufran, ya sea por su culpa o la de terceros, así como ante los supuestos de accidente, caso fortuito o fuerza mayor.

– En caso de que los muebles arrendados hayan sufrido desperfecto alguno durante el transcurso del arriendo el ARRENDATARIO deberá abonar el importe necesario para su reparación. Si son necesarias reparaciones sobre el bien alquilado, deberá informar previamente al ARRENDADOR, quien podrá oponerse respecto a la forma de realizarse la reparación.

– Al finalizar el arriendo, la devolución de los muebles arrendados deberá efectuarse en el mismo estado de conservación en que fueron recibidos y en el mismo lugar de la entrega

El incumplimiento de cualquiera de las obligaciones descritas en este contrato, da derecho al ARRENDADOR a declarar rescindido este contrato de alquiler.

Fianza

El ARRENDATARIO entrega en este acto al ARRENDADOR en concepto de fianza la cantidad de [IMPORTE] euros.

La fianza se constituye con carácter de garantía por el buen uso y conservación de los muebles arrendados, y se devolverá por el ARRENDADOR al finalizar el arriendo siempre y cuando se devuelva el bien en el mismo estado en que fue entregado, salvo el desgaste natural por su uso.

Designación de domicilio

A efectos de notificaciones o emplazamientos judiciales, y en general, toda comunicación o requerimiento que hayan de oír las partes en relación con el presente contrato, se tomará como domicilio del arrendador el señalado al inicio del presente contrato, es decir, calle [CALLE], núm. [Nº], piso [COMPLETAR], puerta [COMPLETAR], de la localidad/ciudad de [COMPLETAR], provincia de [PROVINCIA], y como domicilio del arrendatario el de la calle [CALLE], núm. [Nº], piso [COMPLETAR], puerta [COMPLETAR], de la localidad/ciudad de [COMPLETAR], provincia de [PROVINCIA].

Cualquier cambio de domicilio de una de las partes deberá ser notificado a la otra de forma inmediata, y por un medio que garantice la recepción del mensaje.

Cláusula de sumisión

(en su caso.. [COMPLETAR]) Las partes contratantes acuerdan libre y voluntariamente que todas las desavenencias, divergencias o cuestiones litigiosas que deriven de este contrato, se resolverán a través de la Mediación (en su caso se citará la institución) de [COMPLETAR], antes de acudir a la jurisdicción o a otra solución extrajudicial de conflictos, sometiéndose a la regulación establecida en la Ley 5/2012, de 6 de julio, y (caso de fijar un plazo máximo) fijando un plazo máximo de duración del procedimiento de sesenta días desde la solicitud de iniciación por cualquiera de las partes.

(caso de pacto sucesivo de arbitraje) A falta de resolución de la controversia en el procedimiento de mediación, la misma será definitivamente resuelta mediante Arbitraje de la Corte de [COMPLETAR], a la que se encomienda la administración del arbitraje y la designación de los árbitros, de acuerdo con su reglamento.

(pacto de sumisión expresa) Las partes, con renuncia expresa al fuero que pudiera corresponderles, se someten para todas las cuestiones dimanantes del presente contrato a los Tribunales de la localidad de

Y en prueba de conformidad con cuanto antecede, ambas partes firman este contrato por duplicado y a un solo efecto en el lugar y fecha indicados en el encabezamiento.

Fdo.: Don [COMPLETAR]

-Arrendador

Fdo.: Don [COMPLETAR]

-Arrendatario-

========================================================================
