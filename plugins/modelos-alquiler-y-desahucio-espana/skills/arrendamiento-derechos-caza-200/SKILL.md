---
name: arrendamiento-derechos-caza-200
description: "Redacta el escrito «Arrendamiento de derechos de caza» (formulario 200 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Arrendamiento de derechos de caza

> Formulario 0200 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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
- [ ] FECHA (2 veces)
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] LOCALIDAD (6 veces)
- [ ] DNI/NIE (2 veces)
- [ ] NIF
- [ ] NÚMERO
- [ ] Nº
- [ ] IMPORTE
- [ ] Otros 16 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, en representación del Club»; «…, en su condición de presidente»; «…montes, caza y pesca de la Consejería de»; «…OR es propietario de la finca denominada»; «…, sita en el municipio de»; «…, con una superficie de»; «…scrita en el registro de la Propiedad de»; «…, de acuerdo con el artículo»; «…, de la Ley»; «…l pago habrá de realizarse dentro de los»; «…, primeros días del mes de»; «…NDATARIO establecerá un número mínimo de»; …

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

### Formulario 0200 · Arrendamiento de derechos de caza

- Año del modelo: 2020
- Revisión 17-11-2026: 36 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Contrato de arrendamiento de unos terrenos de propiedad privada, que han sido catalogados como cinegéticos, y por ende, aptos para establecer en ellos un coto de caza. Téngase en cuenta que cada CCAA dispone de legislación propia respecto a este tipo de contratos de aprovechamiento cinegético.

En [LUGAR], a [FECHA].

REUNIDOS

De una parte D./Dª [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], y provisto de DNI nº [DNI/NIE], en adelante EL ARRENDADOR.

Y de otra D./Dª [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], y provisto de DNI nº [DNI/NIE], en adelante EL ARRENDATARIO.

INTERVIENEN

D./Dª [NOMBRE Y APELLIDOS], en nombre y representación propio.

D/Dª [NOMBRE Y APELLIDOS], en representación del Club [COMPLETAR], con CIF nº [NIF], y domicilio en [LOCALIDAD], en su condición de presidente [COMPLETAR], de dicha asociación que se encuentra inscrita, con matrícula vigente en el servicio de montes, caza y pesca de la Consejería de [COMPLETAR], de la Comunidad Autónoma de [LOCALIDAD].

Ambas partes se reconocen mutua y recíproca capacidad para comparecer y obligarse por este contrato y, en tal condición,

EXPONEN

I.- Que EL ARRENDADOR es propietario de la finca denominada [COMPLETAR], sita en el municipio de [COMPLETAR], con una superficie de [COMPLETAR], hectáreas, inscrita en el registro de la Propiedad de [COMPLETAR], como finca registral nº [NÚMERO]., catalogada como terreno cinegético por la Comunidad Autónoma de [LOCALIDAD], de acuerdo con el artículo [COMPLETAR], de la Ley [COMPLETAR]., de la comunidad, cuyo aprovechamiento le corresponde en exclusiva.

Se aporta como documento nº 1, a fin de acreditar el anterior extremo, copia simple del Registro de la Propiedad.

II.- Que EL ARRENDATARIO desea adquirir el arriendo de los aprovechamientos cinegéticos de la misma, por lo que formalizan el presente CONTRATO DE ARRENDAMIENTO DE DERECHOS CINEGÉTICOS de conformidad con las siguientes,

CLÁUSULAS

Primera.– Objeto del contrato

EL ARRENDADOR cede en arrendamiento toda clase de caza existente en la finca descrita en el expositivo I anterior, al ARRENDATARIO, quien la adquiere para su aprovechamiento cinegético, extendiéndose a todos derechos normales de la caza y obligándose el ARRENDATARIO a practicarla con arreglo a lo dispuesto en la vigente Ley de Caza de

Segunda.– Duración

La duración del presente contrato es de [Nº] años, a contar desde el día de su firma, y concluirá al finalizar la temporada de caza correspondiente al ejercicio cinegético /.

Tercera.- Precio

El precio en que se estipula el arrendamiento objeto del presente contrato, es de [IMPORTE] euros al año, más el IVA correspondiente.

Dicha cifra se actualizará cada año de conformidad con el IPC o índice que lo sustituya.

El pago habrá de realizarse dentro de los [COMPLETAR], primeros días del mes de [COMPLETAR], de cada año.

Cuarta.– Impuestos

Serán a cuenta del ARRENDATARIO los impuestos que por coto de caza se fijen por el Ministerio de Hacienda, los gastos que se deriven del coto tales como placas, tablillas, etc., el Impuesto de Transmisiones Patrimoniales o Derechos Reales que en su caso pudiera exigir y cuantos otros impuestos puedan crearse en el futuro para gravar el disfrute de los cotos de caza, aun cuando los mismos se libren por la Administración a nombre del ARRENDADOR.

Por lo tanto, el ARRENDADOR de la finca queda liberado de cualquier pago exigible por la existencia en ella del coto de caza. Ello no obstante si durante el plazo de vigencia del presente contrato, por la Administración competente se fijara un impuesto sobre los cotos de caza que a juicio de ambas partes comparecientes en este documento, revistiera un carácter desorbitado, se pacta expresamente que ARRENDADOR y ARRENDATARIO procederán a revisar las condiciones del arriendo.

Quinta.- Guardería

El ARRENDATARIO establecerá un número mínimo de [COMPLETAR], guardas a tiempo completo durante la vigencia del contrato. Siendo obligación del ARRENDATARIO su contratación, su remuneración, así como cualquier actividad que genere la guardería, tanto de personal, como de cualquier elemento de servicio, siendo de cargo exclusivo de dicha parte arrendataria todos los gastos de cualquier tipo que se generen como consecuencia de este servicio.

Es obligación de la guardería el vigilar todos los tipos de animales de caza, así como las fincas, productos y enseres que se encuentren dentro del Coto, asumiendo la obligación de informar al ARRENDADOR y ARRENDATARIO, de los daños ocasionados a las cosechas, espantando la misma, y además dando cuenta a la Administración competente, de las posibles incidencias que puedan afectar a normal cumplimiento de este contrato, y que observen en el desempeño de su función.

Sexta.– Desarrollo de las cacerías

La ARRENDATARIA deberá cumplir y actuar para el correcto aprovechamiento se la Caza objeto de este contrato, de conformidad con los siguientes criterios:

— Deberá señalizar el "coto" en la forma y con los elementos establecidos reglamentariamente para poder ejercitar el derecho de caza.
— El número de cacerías a realizar por temporada está subordinado al Plan de Ordenación Cinegética. La ARRENDATARIA se obliga a llevar a cabo la mitad de las cacerías de cada temporada, antes del día [FECHA], del mes de [COMPLETAR]., de cada año, siempre que las inclemencias del tiempo, o causas de fuerza mayor debidamente justificadas no lo pidan.
— En la medida de lo posible, tanto el personal como los vehículos que se contraten para auxiliar en las cacerías serán de la localidad de [COMPLETAR].
— La caza se realizará en la modalidad de [COMPLETAR], bajo la autorización y supervisión de la Junta de Caza de [COMPLETAR] La ARRENDATARIA se compromete a tomar las medidas para que los cazadores no causen desperfectos ni daños en el coto ni en las fincas colindantes.

Séptima.– Sumisión a arbitraje

Opción b) Para la solución de cualquier conflicto o cuestión litigiosa derivada de este contrato, las partes se someten al arbitraje del Tribunal Arbitral de [LOCALIDAD], a quien se encomienda la designación del árbitro y la administración del arbitraje de acuerdo con su Reglamento vigente al inicio del arbitraje.

Y en prueba de su conformidad, firman las partes el presente contrato por duplicado ejemplar y a un solo efecto en el lugar y fecha indicados al principio.

Firma del arrendador

	Firma del arrendatario
D./Dña. [NOMBRE Y APELLIDOS] 	D./Dña. [NOMBRE Y APELLIDOS]
