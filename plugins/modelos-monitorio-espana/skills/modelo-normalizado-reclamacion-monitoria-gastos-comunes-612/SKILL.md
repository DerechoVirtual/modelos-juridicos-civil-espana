---
name: modelo-normalizado-reclamacion-monitoria-gastos-comunes-612
description: "Redacta el escrito «Modelo normalizado de reclamación monitoria de gastos comunes de comunidad» (formulario 612 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Modelo normalizado de reclamación monitoria de gastos comunes de comunidad

> Formulario 0612 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Escrito inicial sin referencia al requisito de procedibilidad: añadir la nota MASC (el art. 5.2 LO 1/2025 alcanza a los procesos del libro IV LEC, incluido el monitorio).
- REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] NIF (4 veces)
- [ ] CALLE (8 veces)
- [ ] NÚMERO (11 veces)
- [ ] TELÉFONO (5 veces)
- [ ] CORREO ELECTRÓNICO
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] IMPORTE (3 veces)
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 16 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…mente por la Instrucción 1/2002 del CGPJ»; «…, número [NÚMERO], piso»; «…, piso [COMPLETAR], de la localidad de»; «…, número [NÚMERO], piso»; «…, piso [COMPLETAR], de la localidad de»; «…con número de teléfono [TELÉFONO], fax»; «…de la calle [CALLE], de la localidad de»; «…, número [NÚMERO], de la localidad de»; «…, número [NÚMERO], de la localidad de»; «…, número [NÚMERO], de la localidad de»; «…a»; «…. (2) SEGUNDO. Los/as demandados/as son»; …

## Elecciones que hay que hacer

- Presidente / Presidenta / Administrador / Administradora
- la vivienda / el local
- la vivienda / local
- Presidente/a / Administrador/a

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS

## Párrafos opcionales (4)

Inclúyelos solo si encajan en los hechos:

- En caso de que el anterior propietario/a de [ELEGIR: la vivienda / local] no hubiera comunicado la venta o tra…
- Si la persona o personas que figuran como propietarios/as de [ELEGIR: la vivienda / el local] en el Registro d…
- QUINTO. En su caso, con carácter previo a la presentación de esta petición, se ha requerido previamente de pag…
- Y para el caso de oposición solicito el embargo preventivo de bienes suficientes de la persona deudora, para h…

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

### Formulario 0612 · Modelo normalizado de reclamación monitoria de gastos comunes de comunidad

- Año del modelo: 2016
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (2); 7 desplegables convertidos en elección en blanco; 1 bloques de alternativas señalados; 4 párrafos opcionales señalados; 57 campos de relleno marcados en blanco
- Avisos de la revisión: Escrito inicial sin referencia al requisito de procedibilidad: añadir la nota MASC (el art. 5.2 LO 1/2025 alcanza a los procesos del libro IV LEC, incluido el monitorio). · REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo normalizado de petición en proceso monitorio aprobado por Acuerdo CGPJ publicado en BOE 28-1-2016. Actualiza a las últimas reformas el aprobado anteriormente por la Instrucción 1/2002 del CGPJ [COMPLETAR].

Formulario adaptado a la reforma procesal de la LO 1/2025.

AL TRIBUNAL

D./Dña. [NOMBRE Y APELLIDOS] con DNI y NIF/CIF número [NIF], domiciliado/a en la calle [CALLE], número [NÚMERO], piso [COMPLETAR], de la localidad de [COMPLETAR], con número de teléfono [TELÉFONO] y domicilio laboral en la calle [CALLE], número [NÚMERO], piso [COMPLETAR], de la localidad de [COMPLETAR] con número de teléfono [TELÉFONO], fax [COMPLETAR] y dirección de correo electrónico [CORREO ELECTRÓNICO] (1)., como [ELEGIR: Presidente / Presidenta / Administrador / Administradora] DE LA COMUNIDAD DE PROPIETARIOS de la casa número [NÚMERO] de la calle [CALLE], de la localidad de [COMPLETAR],

FORMULO PETICION INICIAL DE PROCESO MONITORIO en reclamación de correspondiente a la liquidación de la deuda y, en su caso, a los gastos del requerimiento del pago, contra

D./Dña. [NOMBRE Y APELLIDOS], con DNI y NIF número [NIF] con domicilio en la calle [CALLE], número [NÚMERO], de la localidad de [COMPLETAR], con número de teléfono [TELÉFONO], fax número [NÚMERO], como propietario de [ELEGIR: la vivienda / el local]. Actualmente puede/n ser localizado/s también en la calle [CALLE], número [NÚMERO].

[OPCIONAL — incluir si procede]

En caso de que el anterior propietario/a de [ELEGIR: la vivienda / local] no hubiera comunicado la venta o transmisión a la Comunidad, podrá también demandarse al anterior propietario/a, indicando los mismos datos personales.

D./Dña. [NOMBRE Y APELLIDOS], con DNI y NIF número [NIF] con domicilio en la calle [CALLE], número [NÚMERO], de la localidad de [COMPLETAR], con número de teléfono [TELÉFONO], fax número [NÚMERO], como anteriores propietarios/as de la vivienda o local. Actualmente puede/n ser localizado/s también en la calle [CALLE], número [NÚMERO].

[OPCIONAL — incluir si procede]

Si la persona o personas que figuran como propietarios/as de [ELEGIR: la vivienda / el local] en el Registro de la Propiedad no coinciden con el vecino moroso/a también podrán ser demandados.

D./Dña. [NOMBRE Y APELLIDOS], con DNI y NIF número [NIF] con domicilio en la calle [CALLE], número [NÚMERO], de la localidad de [COMPLETAR], con número de teléfono [TELÉFONO], fax número [NÚMERO], como titulares registrales de la vivienda o local.

HECHOS

PRIMERO. Que soy [ELEGIR: Presidente / Presidenta / Administrador / Administradora] a [COMPLETAR] de la Comunidad de Propietarios arriba expresada, en virtud de acuerdo adoptado por la Junta, y estoy debidamente autorizado para formular esta reclamación. Se acompaña copia del/las acta/s como documento número [Nº DE DOCUMENTO]. (2)

SEGUNDO. Los/as demandados/as son [COMPLETAR]
propietarios
propietarias
[NOMBRE Y APELLIDOS], de [ELEGIR: la vivienda / el local] de la escalera [COMPLETAR] planta [COMPLETAR], letra [COMPLETAR], de la casa que forma la Comunidad demandante.

TERCERO. La Junta de Propietarios aprobó la liquidación de la deuda, ante el incumplimiento por parte del deudor/a de sus obligaciones de pago frente a la Comunidad, por importe de [IMPORTE]. Se acompaña como documento número [Nº DE DOCUMENTO] certificación del acuerdo aprobando la liquidación.

CUARTO. El importe de la deuda se comunicó al deudor/a:

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

en su domicilio.

en el específicamente designado por el propietario/a.

en el tablón de anuncios u otro lugar visible de uso general.

Se acompaña como documento número tres el documento acreditativo de la notificación.

[OPCIONAL — incluir si procede]

QUINTO. En su caso, con carácter previo a la presentación de esta petición, se ha requerido previamente de pago a la/s persona/s deudor/a, lo que ha ocasionado a esta Comunidad unos gastos de [COMPLETAR].

Se acompañan como documento número cuatro los justificantes de dichos gastos.

En atención a lo expuesto

PIDO AL TRIBUNAL:

1.º Que se requiera a la/s persona/s deudor/as para que en el plazo de veinte días, pague/n a la Comunidad la cantidad de [IMPORTE], así como, en su caso, el importe de [IMPORTE] correspondiente a los gastos de previo requerimiento de pago, y para el caso de que no pague/n la suma reclamada ni comparezca/n alegando razones de la negativa de pago, se dicte decreto dando por terminado el proceso monitorio y se me dé traslado del mismo para que pueda instar el despacho de ejecución.
2.º Que si la persona/s deudora/s se opone/n por escrito alegando razones para negarse total o parcialmente al pago, se dé por terminado el monitorio y se acuerde seguir por los trámites del juicio verbal, dándome traslado de la oposición para poder impugnarla por escrito en diez días.

[OPCIONAL — incluir si procede]

Y para el caso de oposición solicito el embargo preventivo de bienes suficientes de la persona deudora, para hacer frente a la cantidad reclamada, los intereses y las costas, sin necesidad de prestar caución.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma por el [ELEGIR: Presidente/a / Administrador/a] de la Comunidad de Propietarios

NOTAS DEL FORMULARIO

(1) Modelo aprobado por Acuerdo de 22 de diciembre de 2015, de la Comisión Permanente del Consejo General del Poder Judicial (BOE 28-1-2016).

En la Instrucción 1/2002, de 5 de noviembre de 2002 del CGPJ se aprobaron para su publicación en el BOE los modelos normalizados de demanda y petición inicial de procedimientos monitorios, que nacieron con carácter de material informativo y a efectos orientativos y con la previsión de que las Presidencias y Salas de Gobierno de los Tribunales Superiores de Justicia dispusieran lo necesario a estos fines, bien directamente o bien, en los casos de Administraciones Públicas con competencias en la materia, a través de los correspondientes órganos de coordinación, en especial en aquellos territorios D./Dña. [NOMBRE Y APELLIDOS] de el estatuto de cooficialidad lingüística requiera que sean facilitados en versión bilingüe. Y, tras las reformas legislativas últimas se estima necesaria igualmente la actualización de los referidos modelos normalizados mencionados anteriormente.

(2) Relación de documentos adjuntos: ...

========================================================================
