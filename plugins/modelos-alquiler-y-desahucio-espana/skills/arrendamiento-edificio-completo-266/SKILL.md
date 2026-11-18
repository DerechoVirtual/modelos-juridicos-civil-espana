---
name: arrendamiento-edificio-completo-266
description: "Redacta el escrito «Arrendamiento de un edificio completo» (formulario 266 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Arrendamiento de un edificio completo

> Formulario 0266 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (9 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] DNI/NIE (2 veces)
- [ ] NÚMERO (3 veces)
- [ ] CALLE (5 veces)
- [ ] FECHA (2 veces)
- [ ] IMPORTE (3 veces)
- [ ] Otros 21 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…enda y local de negocio. En la ciudad de»; «…, a»; «…URBANA. Casa con su patio en la calle de»; «…esquina a calle [CALLE], de la ciudad de»; «…, formando todo una sola finca urbana de»; «…; y Fondo, Espalda u Oeste, edificio»; «…scrita en el Registro de la Propiedad de»; «…, al»; «…- El destino del edificio arrendado será»; «…rta.- El contrato tendrá una duración de»; «… finalizando el día [FECHA]. A partir de»; «…euros pagaderos»; …

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

### Formulario 0266 · Arrendamiento de un edificio completo

- Año del modelo: 2020
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 47 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Contrato de arrendamiento mixto de arrendamiento de vivienda y local de negocio.

En la ciudad de [COMPLETAR], a [COMPLETAR].

REUNIDOS

De una parte, Don/Doña [NOMBRE Y APELLIDOS] con domicilio en [LOCALIDAD], que deja designado a efectos de notificaciones y avisos en relación con el presente contrato, y DNI [DNI/NIE], en concepto de ARRENDADOR y

De otra parte, Don/Doña [NOMBRE Y APELLIDOS] con domicilio en [LOCALIDAD], que deja designado a efectos de notificaciones y avisos en relación con el presente contrato, y DNI [DNI/NIE], en concepto de ARRENDATARIO

INTERVIENEN

Ambos en su propio nombre y derecho.

Recíprocamente se reconocen, en los conceptos de su respectiva intervención, la capacidad necesaria para otorgar el presente contrato, y a tales efectos,

EXPONEN

I.- Que Don/Doña [NOMBRE Y APELLIDOS] es propietario, en pleno dominio, de la siguiente finca:

URBANA. Casa con su patio en la calle de [COMPLETAR], número [NÚMERO], esquina a calle [CALLE], de la ciudad de [COMPLETAR] Consta de planta baja y tres plantas; la planta baja con local comercial y almacén, las plantas primera y segunda con tres pisos cada una y la planta tercera con dos pisos. En su fachada derecha entrando existe una franja de terreno o patio pegante a toda la longitud de la misma, formando todo una sola finca urbana de [COMPLETAR] metros cuadrados. Linda: Frente o Este, calle [CALLE]; Derecha Entrando o Norte, edificio número [NÚMERO] de la calle [CALLE], de diversos propietarios; Izquierda o Sur, calle [CALLE]; y Fondo, Espalda u Oeste, edificio [COMPLETAR] de la calle [CALLE] Consta inscrita en el Registro de la Propiedad de [COMPLETAR], al [COMPLETAR].

II.- Que el edificio descrito se encuentra sujeto al régimen de propiedad horizontal.

III.- Que las distintas viviendas y locales del referido inmueble están libres de arrendamientos.

IV.- Que Don/Doña [NOMBRE Y APELLIDOS] está interesado en adquirir el uso del referido edificio completo en arrendamiento, como un conjunto unitario en su realidad física (extensión, ubicación y linderos) y en su realidad jurídica (como única finca registral), estando Don/Doña [NOMBRE Y APELLIDOS] interesado en su cesión en arriendo.

V.- Que ambas partes están conformes en llevar a cabo el presente CONTRATO DE ARRENDAMIENTO DE EDIFICIO, que se regirá por las siguientes

ESTIPULACIONES

Primera.- Don/Doña [NOMBRE Y APELLIDOS] cede en arrendamiento a Don/Doña [NOMBRE Y APELLIDOS], el edificio descrito en el expositivo I.

Segunda.- El presente contrato se regirá por lo dispuesto en el mismo y, supletoriamente por las reglas del Código civil.

Tercera.- El destino del edificio arrendado será [COMPLETAR] (1). En caso de que el arrendatario destine el edificio a un uso diferente, el arrendador podrá resolver el contrato de arrendamiento, antes de la finalización del plazo pactado, y exigir la correspondiente indemnización de daños y perjuicios.

Cuarta.- El contrato tendrá una duración de [COMPLETAR], dando comienzo el día [FECHA] y finalizando el día [FECHA].

A partir de [COMPLETAR], ambas partes podrán desistir del mismo preavisando fehacientemente a la otra con un mes de antelación. Si, una vez notificado por el arrendador el deseo de finalizar el arriendo a la expiración del plazo contractual o de cualquiera de las prórrogas, el arrendatario continuase en el uso de la cosa, tras dicho vencimiento, deberá abonar al arrendador la cantidad de [IMPORTE] euros, por día de retraso en la devolución del edificio.

Si, una vez haya expirado el plazo contractual, ninguna de las partes manifiesta su voluntad de finalizar el arriendo, el contrato se prorrogará automáticamente por un plazo contractual igual al inicialmente pactado, plazo durante el cual seguirá siendo de aplicación al arriendo lo pactado en este contrato.

Quinta.- Ambas partes estipulan una renta anual de [IMPORTE] euros pagaderos [COMPLETAR].

El pago se hará efectivo por el arrendatario mediante ingreso en la cuenta del arrendador n.° [NÚMERO] de la entidad [COMPLETAR], durante los cinco primeros días del [COMPLETAR].

La renta se actualizará de la siguiente forma: [COMPLETAR].

Sexta.- El arrendatario recibe el edificio en perfecto estado para servir al uso al que se destina. Serán de cuenta del arrendador las reparaciones que sean necesarias, para que la cosa siga sirviendo al uso pactado, siempre que las mismas sean debidas al uso normal de la cosa. Serán de cuenta del arrendatario las reparaciones debidas al uso indebido o a la falta de diligencia o dolo por parte del arrendatario. Si la cosa sufre deterioro por este motivo, podrá el arrendador resolver el contrato, con la consiguiente indemnización de daños y perjuicios.

El arrendador deberá ser informado inmediatamente de toda perturbación que sufra el arrendatario, o de cualquier deterioro que se haya producido en el bien arrendado.

Séptima.- El arrendatario (no) tendrá derecho de adquisición preferente en el caso de que el arrendador vendiese el edificio o alguna de las viviendas que lo integran, si bien el adquirente se subrogará en la posición del arrendador, hasta la fecha de conclusión del contrato.

Octava.- Las partes acuerdan elevar el presente contrato a escritura pública, así como proceder a su inscripción en el Registro de la Propiedad, siendo los gastos derivados de ambos conceptos a cuenta del arrendador/arrendatario.

Novena.- Ambas partes pactan la entrega al arrendador de [IMPORTE] euros en concepto de fianza, sirviendo el presente contrato de recibo, y debiendo devolver dicha cantidad el arrendador a la finalización del contrato.

Durante los [COMPLETAR] primeros años de vigencia del contrato, la fianza no estará sujeta a actualización. A partir del [COMPLETAR] año, si el arrendamiento se prorroga, el arrendador podrá exigir que la fianza sea incrementada, o el arrendatario que disminuya, hasta hacerse igual a una mensualidad de la renta vigente, al tiempo de la prórroga.

El arrendador podrá aplicar la fianza a posibles impagos en que hubiera incurrido el arrendatario, así como a la reparación de posibles daños que éste hubiera causado en la vivienda arrendada. El saldo resultante de la fianza será devuelto al arrendatario, previa la constatación por parte del arrendador de que la finca se haya en perfecto estado de conservación. Este saldo final devengará el interés legal del dinero a partir del transcurso de un mes desde la entrega de las llaves por el arrendatario, sin que se le hubiera hecho efectiva la restitución.

Décima.- El incumplimiento de las obligaciones establecidas en el presente contrato dará derecho a la parte que esté al corriente en el cumplimiento de las suyas a resolver la relación y (alternativa o cumulativamente) ejecutar las garantía adicional que se establece en la cláusula siguiente.

Undécima.- Sin perjuicio de lo dispuesto en la cláusula anterior, el arrendatario constituirá en el plazo de un mes a contar desde la fecha celebración del presente contrato, aval bancario garantizando el cumplimiento de las obligaciones derivadas del mismo.

Duodécima.- Las partes contratantes acuerdan libre y voluntariamente que todas las desavenencias, divergencias o cuestiones litigiosas que deriven de este contrato, incluso cuando la controversia verse sobre la validez o existencia del presente contrato, se resolverán a través de la Mediación de [COMPLETAR], antes de acudir a la jurisdicción o a otra solución extrajudicial de conflictos, sometiéndose a la regulación establecida en la Ley 5/2012, de 6 de julio, y fijando un plazo máximo de duración del procedimiento de sesenta días desde la solicitud de iniciación por cualquiera de las partes.

A falta de resolución de la controversia en el procedimiento de mediación, la misma será definitivamente resuelta mediante Arbitraje de la Corte de [COMPLETAR], a la que se encomienda la administración del arbitraje y la designación de los árbitros, de acuerdo con su reglamento.

El conocimiento de los litigios relativos a que diera lugar la interpretación y/o ejecución del presente contrato corresponderá al Juez de Primera Instancia del lugar en que se halle la finca.

Decimotercera.- A efectos de notificaciones o emplazamientos judiciales, y en general, toda comunicación o requerimiento que hayan de oír las partes en relación con el presente contrato se tomará como domicilio del arrendador el señalado al inicio del presente contrato, es decir [COMPLETAR], y como domicilio del arrendatario [COMPLETAR].

Cualquier cambio de domicilio de una de las partes deberá ser notificado a la otra de forma inmediata y por un medio que garantice la recepción del mensaje.

Y para que así conste, las partes firman el presente contrato, por duplicado y a un solo efecto, en el lugar y fecha indicados.

Firma del arrendador

	Firma del arrendatario
D./Dña. [NOMBRE Y APELLIDOS] 	D./Dña. [NOMBRE Y APELLIDOS]

NOTAS DEL FORMULARIO

(1) Nada hay específicamente regulado sobre el contrato de arrendamiento mixto de arrendamiento de vivienda y local de negocio.

De acuerdo con reiterada doctrina jurisprudencial, dictada antes y a partir de la LAU de 1964, el régimen jurídico de los arrendamientos mixtos queda determinado por el que corresponde al elemento objetivo predominante al decir (SSTS de 21 de marzo de 1949, 18 de abril de 1950, 28 de junio de 1975 y 30 de junio de 1979), que el arrendamiento mixto ha de regirse por una única normativa, que tiene que ser la del elemento objetivo principal o preponderante en atención al principio jurídico de la accesoriedad, y ello con la finalidad de mantener la integridad del contrato tal y como lo idearon los interesados y para esa determinación debe acudirse a la intención de los contratantes (factores subjetivos) y a la mayor importancia de uno u otro destino (factores objetivos).
