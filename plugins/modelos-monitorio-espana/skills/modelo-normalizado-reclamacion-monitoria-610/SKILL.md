---
name: modelo-normalizado-reclamacion-monitoria-610
description: "Redacta el escrito «Modelo normalizado de reclamación monitoria» (formulario 610 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Modelo normalizado de reclamación monitoria

> Formulario 0610 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NIF (2 veces)
- [ ] CORREO ELECTRÓNICO (3 veces)
- [ ] CALLE (3 veces)
- [ ] NÚMERO (3 veces)
- [ ] TELÉFONO (2 veces)
- [ ] Nº
- [ ] IMPORTE
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…,»; «…como representante de la entidad»; «…, número [NÚMERO], piso»; «…, piso [COMPLETAR], de la ciudad de»; «…, número [NÚMERO], piso»; «…, piso [COMPLETAR], de la localidad de»; «…L DE PROCESO MONITORIO EN RECLAMACIÓN DE»; «…, número [NÚMERO], de la ciudad de»; «…, n.º [Nº] de fax»; «…,»

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

### Formulario 0610 · Modelo normalizado de reclamación monitoria

- Año del modelo: 2016
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (2); 28 campos de relleno marcados en blanco
- Avisos de la revisión: Escrito inicial sin referencia al requisito de procedibilidad: añadir la nota MASC (el art. 5.2 LO 1/2025 alcanza a los procesos del libro IV LEC, incluido el monitorio). · REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de petición en proceso monitorio aprobado por Acuerdo CGPJ publicado en BOE 28-1-2016. Actualiza a las últimas reformas el aprobado anteriormente por la Instrucción 1/2002 del CGPJ.

Formulario adaptado a la reforma orgánica y procesal de la LO 1/2025.

AL TRIBUNAL

D./Dña. [NOMBRE Y APELLIDOS], [COMPLETAR] como representante de la entidad [COMPLETAR], con DNI y NIF/CIF número [NIF], dirección de correo electrónico [CORREO ELECTRÓNICO], domiciliado/a en la calle [CALLE], número [NÚMERO], piso [COMPLETAR], de la ciudad de [COMPLETAR], con número de teléfono [TELÉFONO] y domicilio laboral en la calle [CALLE], número [NÚMERO], piso [COMPLETAR], de la localidad de [COMPLETAR], fax n.º < y dirección de correo electrónico [CORREO ELECTRÓNICO] (1)

FORMULO PETICION INICIAL DE PROCESO MONITORIO EN RECLAMACIÓN DE [COMPLETAR] contra:

D./Dña. [NOMBRE Y APELLIDOS] con DNI NIF/CIF [NIF], domiciliado/a en la calle [CALLE], número [NÚMERO], de la ciudad de [COMPLETAR], número de teléfono [TELÉFONO], n.º [Nº] de fax [COMPLETAR] y dirección de correo electrónico [CORREO ELECTRÓNICO], [COMPLETAR].

La cantidad reclamada tiene origen en las relaciones mantenidas entre las partes y, concretamente: (2)

En atención a lo expuesto,

PIDO AL TRIBUNAL:

1.º Que se requiera a la/s persona/s deudora/s para que en el plazo de veinte días, pague/n la cantidad de [IMPORTE], y para el caso de que en dicho plazo no atienda/n el requerimiento o no comparezca/n alegando razones de la negativa de pago, se dicte decreto dando por terminado el proceso monitorio y se me dé traslado del mismo para que pueda instar el despacho de ejecución
2.º Que si la persona/s deudora/s se opone/n por escrito alegando razones para negarse total o parcialmente al pago, se dé por terminado el monitorio y se acuerde seguir por los trámites del juicio verbal, dándome traslado de la oposición para poder impugnarla por escrito en diez días.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) Modelo aprobado por Acuerdo de 22 de diciembre de 2015, de la Comisión Permanente del Consejo General del Poder Judicial (BOE 28-1-2016).

En la Instrucción 1/2002 del CGPJ se aprobaron para su publicación en el BOE los modelos normalizados de demanda y petición inicial de procedimientos monitorios, que nacieron con carácter de material informativo y a efectos orientativos y con la previsión de que las Presidencias y Salas de Gobierno de los Tribunales Superiores de Justicia dispusieran lo necesario a estos fines, bien directamente o bien, en los casos de Administraciones Públicas con competencias en la materia, a través de los correspondientes órganos de coordinación, en especial en aquellos territorios donde el estatuto de cooficialidad lingüística requiera que sean facilitados en versión bilingüe. Y, tras las reformas legislativas últimas se estima necesaria igualmente la actualización de los referidos modelos normalizados mencionados anteriormente.

(2) Relación de documentos adjuntos: ....

========================================================================
