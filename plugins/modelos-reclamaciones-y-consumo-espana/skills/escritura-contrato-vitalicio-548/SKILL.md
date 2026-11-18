---
name: escritura-contrato-vitalicio-548
description: "Redacta el escrito «Escritura de contrato de vitalicio» (formulario 548 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Escritura de contrato de vitalicio

> Formulario 0548 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (10 veces)
- [ ] en su caso, rústicos
- [ ] Nº (8 veces)
- [ ] CALLE
- [ ] DATO REGISTRAL (5 veces)
- [ ] IMPORTE (3 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] FECHA
- [ ] AÑO
- [ ] Otros 28 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, mi residencia, a .de»; «…, mi residencia, a .de [COMPLETAR]. de»; «…. de [COMPLETAR]. Ante mí»; «… como sigue: 1.- TÉRMINO MUNICIPAL DE DE»; «….- Vivienda sita en la planta»; «…, sita en la calle [CALLE].,»; «…. Ocupa la superficie útil aproximada de»; «… fachada principal del inmueble: frente,»; «…; derecha entrando,»; «…alada en el citado plano con los números»; «…. Cuota:»; «…sponde el número de referencia catastral»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Ley 2/2006
- Ley 8/1989
- Ley Orgánica 3/2018

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

### Formulario 0548 · Escritura de contrato de vitalicio

- Año del modelo: 2016
- Revisión 17-11-2026: 1 rangos de artículos despegados («25 a31» → «25 a 31»); 3 campos de relleno marcados en blanco; 56 huecos del original que se habían perdido sin marca, marcados (CALLE, COMPLETAR, DATO REGISTRAL, FECHA, IMPORTE, LOCALIDAD, LUGAR, NOMBRE Y APELLIDOS, Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

NÚMERO

En [LUGAR], mi residencia, a .de [COMPLETAR]. de [COMPLETAR].

Ante mí [COMPLETAR], Notario del Ilustre Colegio de Galicia,

COMPARECEN

INTERVIENEN, todos los comparecientes en su propio nombre y derecho (o, en su caso, en representación de [NOMBRE Y APELLIDOS]); siendo su vecindad civil la gallega, conforme manifiestan.

DECLARAN: Que, en el momento de otorgamiento de la presente escritura pública, ambos comparecientes tienen la vecindad civil gallega.

Los comparecientes, en las representaciones en las que intervienen, tienen, a mi juicio, la capacidad legal y la legitimación necesarias para obligarse y, por tanto, para formalizar el presente CONTRATO DE VITALICIO y, a tal efecto MANIFIESTAN:

EXPONEN

Que Don/Doña [NOMBRE Y APELLIDOS] es propietario de los dos inmuebles urbanos [en su caso, rústicos] que se identifica como sigue:

1.- TÉRMINO MUNICIPAL DE DE [COMPLETAR].- Vivienda sita en la planta [COMPLETAR], de la casa número [Nº], sita en la calle [CALLE]., [COMPLETAR]. Ocupa la superficie útil aproximada de [COMPLETAR], siéndole inherente un derecho conjunto de copropiedad con las demás plantas del edificio sobre los elementos comunes necesarios para su adecuado uso y disfrute. Linda, tomando referencia la fachada principal del inmueble: frente, [COMPLETAR]; derecha entrando, [COMPLETAR], y en parte la referida rampa de acceso; izquierda, el solar número [Nº]; y espalda, finca de Don [NOMBRE Y APELLIDOS], señalada en el citado plano con los números [COMPLETAR].

Cuota: [COMPLETAR] centésimas.

Inscripción: Registro de la Propiedad número [Nº] en el Libro [DATO REGISTRAL], Folio [DATO REGISTRAL], finca número [Nº], inscripción [DATO REGISTRAL].

Datos Catastrales: Le corresponde el número de referencia catastral [COMPLETAR].

Cargas y arrendamientos: Libres de cargas y sin arrendar.

Valor.- Este piso se valora en la suma de [IMPORTE] EUROS Y [COMPLETAR] CÉNTIMOS ( €).

2º.- TÉRMINO MUNICIPAL DE [COMPLETAR].- Local destinado a plaza de garaje y trastero, en la plaza de sótano de un edificio radicante en la parcela [COMPLETAR], de [COMPLETAR], municipio de [LOCALIDAD], de dieciocho metros y noventa decímetros cuadrados de superficie. Linda, viendo el local desde su frente: Frente-Norte, [COMPLETAR]; derecha entrando-Oeste, plaza de garaje número [Nº]; izquierda-Este, plaza de garaje número [Nº]; y fondo-Sur, muro que separa del subsuelo de la parcela [COMPLETAR].

Es la plaza de garaje número [Nº] de la Escalera [COMPLETAR], Bloque [COMPLETAR].

Cuota de participación en los elementos comunes del inmueble: [COMPLETAR] centésimas.

Referencia catastral.- Catastrada bajo la referencia catastral [COMPLETAR], según resulta de certificación catastral descriptiva y gráfica, que yo, el Notario, doy fe de haber solicitado a efectos del presente otorgamiento y obtenido por los procedimientos telemáticos seguros habilitados (de conformidad con la resolución de 24 de noviembre de 2008, de la Dirección General del Catastro), que incorporo a esta matriz.

Inscripción.- Registro de la Propiedad de [LOCALIDAD], Libro [DATO REGISTRAL] de [COMPLETAR], folio [COMPLETAR], finca número [Nº].

Título.- Le corresponde en virtud de compraventa otorgada por los cónyuges Don [NOMBRE Y APELLIDOS] y Dñª [COMPLETAR], formalizada en escritura pública autorizada por el Notario del Ilustre Colegio de Galicia Don [NOMBRE Y APELLIDOS] en fecha [FECHA] de [COMPLETAR] de [AÑO], bajo el número de su protocolo [DATO REGISTRAL].

Cargas y gravámenes.- La finca se encuentra libre de cargas y gravámenes, así como de inquilinos y ocupantes y con todos los derechos a la misma que son inherentes al derecho de propiedad.

Valor.- Esta plaza de garaje se valora en la suma de [IMPORTE] EUROS Y CINCUENTA Y [COMPLETAR] CÉNTIMOS ( €).

Expuesto lo que antecede:

OTORGAN

Don / Doña [NOMBRE Y APELLIDOS] cede a los cónyuges Don / Doña [NOMBRE Y APELLIDOS] y Don / Doña [NOMBRE Y APELLIDOS], los dos bienes inmuebles descritos e identificados en el Expositivo I de esta escritura pública, que los adquieren para su sociedad legal de gananciales, valorándose ambos en la suma de [IMPORTE] €.

Como contraprestación de la cesión referida, los cónyuges Don / Doña [NOMBRE Y APELLIDOS] y Don / Doña [NOMBRE Y APELLIDOS], contraen la obligación solidaria, respecto de la parte cedente, de proporcionarle alimentos (incluyendo alimentación, vestimenta y residencia) y todos los cuidados personales que le resulten necesarios, teniéndolo en su compañía, si ésta fuese su voluntad, así como satisfaciendo los gastos médicos y paramédicos (en especial, medicamentos) que precise, así como todos los cuidados y afectos que resulten adecuados a la situación personal y de salud del cedente en cada momento y hasta la fecha de su fallecimiento. Asimismo, los cesionarios asumen la obligación, de carácter solidario, de satisfacer los gastos de sepelio y funeral que fuesen precisos y conformes con la posición económica y social del cedente.

El incumplimiento de la obligación establecida en la cláusula precedente, siempre que resulte imputable a los cesionarios o a sus herederos, dará lugar a la resolución del presente contrato de vitalicio, quedando en poder del cedente los alimentos y la asistencia recibida, cualquiera que fuese la duración y la cuantía de ésta.

Todos los gastos e impuestos derivados de esta escritura pública, así como, en su caso, los derivados del incumplimiento de lo pactado, tanto judiciales como extrajudiciales, incluidos los honorarios de abogado y los derechos y suplidos del procurador, serán de cargo de los cesionarios.

En todo lo no previsto en la presente escritura pública, resultará de aplicación lo dispuesto en los artículos 147 a 156, ambos incluidos, de la Ley 2/2006, de 14 de junio, de Derecho Civil de Galicia.

Hago las reservas y advertencias legales y, a efectos fiscales, las relativas a las obligaciones y responsabilidades que incumben a las partes en su aspecto material, formal y sancionador, y a las consecuencias de toda índole que se derivarían de la inexactitud de sus declaraciones. Advierto, en especial de las obligación relativa al plazo de presentación de esta escritura a liquidación de los Impuestos sobre Transmisiones Patrimoniales y de Actos Jurídicos Documentados y sobre la afección de los bienes al pago del primero de dichos Impuestos y de las responsabilidades en caso de no presentación, así como de los efectos de la Ley 8/1989.

Respecto a los datos personales recogidos en el presente documento, debe tenerse en cuenta que el tratamiento de los mismos se ajustará a la LO 3/2018, de 5 de diciembre, de Protección de Datos de Carácter Personal y Garantía de los Derechos Digitales, en desarrollo y aplicación del Reglamento UE 2016/679, de 27 de abril, y que el interesado podrá ejercitar sus derechos de acceso, rectificación, cancelación, supresión (derecho al olvido), portabilidad, oposición y limitación del tratamiento de los datos (ARCO-POL) en los términos establecidos en los arts. 12 a 23 y 12 a 18 de los citados Reglamento y Ley Orgánica, respectivamente.

De conformidad con el art. 6º de la Ley Orgánica 3/2018, de 5 de diciembre, de Protección de Datos Personales y garantía de los derechos digitales, se entiende por consentimiento del afectado toda manifestación de voluntad libre, específica, informada e inequívoca por la que éste acepta, ya sea mediante una declaración o una clara acción afirmativa, el tratamiento de datos personales que le conciernen. Cuando se pretenda fundar el tratamiento de los datos en el consentimiento del afectado para una pluralidad de finalidades será preciso que conste de manera específica e inequívoca que dicho consentimiento se otorga para todas ellas. No podrá supeditarse la ejecución del contrato a que el afectado consienta el tratamiento de los datos personales para finalidades que no guarden relación con el mantenimiento, desarrollo o control de la relación contractual.

Leo esta escritura a los comparecientes, por su elección, previa advertencia y renuncia de la interesada a su derecho a leerlo por sí mismas y, enterados de su contenido, la aprueban y firman conmigo, el Notario, que doy fe de que el consentimiento ha sido libremente prestado, de que se adecua a la voluntad debidamente informada de los otorgantes y de haberse observado todas las formalidades legales anteriormente expresadas, de todo lo demás contenido en folios de clase Notarial, números [COMPLETAR], y de ser las

========================================================================
