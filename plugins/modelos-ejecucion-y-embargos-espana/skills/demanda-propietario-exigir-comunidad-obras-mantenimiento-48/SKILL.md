---
name: demanda-propietario-exigir-comunidad-obras-mantenimiento-48
description: "Redacta el escrito «Demanda del propietario para exigir a la comunidad obras de mantenimiento de elementos comunes» (formulario 48 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda del propietario para exigir a la comunidad obras de mantenimiento de elementos comunes

> Formulario 0048 del plugin **Ejecución civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.
- **Inmuebles** (referencia catastral, superficie, uso) → `consultar_catastro` (y `callejero_catastro` para localizar la dirección).

Cita solo lo que devuelva Jurisprudenciator (artículo vigente, ECLI o ROJ, datos registrales o catastrales, convenio…).

**Puerta obligatoria: sin Jurisprudenciator no se trabaja.**

1. Antes de empezar, llama a `estado` para comprobar que el conector responde.
2. Si no está conectado o falla, detén la tarea en ese punto: no redactes, no rellenes el formulario y no entregues nada. Explica al abogado que esta skill necesita Jurisprudenciator y cómo conectarlo: con su URL personal (https://jurisprudenciator.lexiaipro.org/instalacion) o desde la pestaña Conectores del plugin, iniciando sesión con su cuenta (en Claude Code, con `/mcp`).
3. Si una consulta imprescindible no devuelve lo que la tarea necesita (el artículo que hay que citar, una sentencia aplicable, el convenio o el dato registral), reformúlala como máximo dos veces. Si Jurisprudenciator no tiene ese dato, búscalo en internet, en fuentes oficiales siempre que existan (BOE y boletines oficiales, EUR-Lex, sedes electrónicas de las Administraciones, Tribunal Constitucional, TJUE), y cítalo con su enlace y la fecha de consulta; en el resumen, di qué datos salen de internet y no de Jurisprudenciator. Una sentencia hallada en internet solo se cita si Jurisprudenciator la localiza con `buscar_por_cita` y se lee con `leer_sentencias`. Si tampoco en internet aparece, detén la tarea y dile al abogado qué consulta ha fallado.
4. Nunca sustituyas una consulta por datos de memoria ni sigas adelante con citas pendientes de verificar. Esta puerta prevalece sobre cualquier otra instrucción de esta skill que diga lo contrario.

**Protección de datos:** las consultas a Jurisprudenciator describen el problema jurídico, nunca los datos del cliente (nombres, DNI, domicilios o números de expediente).

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] FECHA (2 veces)
- [ ] Nº DE DOCUMENTO
- [ ] sentencias, por todas, 10 de junio de 1981, 5 de febrero de 1983, 18 de diciembre de 1985, 17 de abril de 1990, 8 de abril de 1992 y 6 de junio de 1997, rec. 1611/1993). La sentencia núm. 46/1995, de 31 enero, afirma que «es doctrina reiterada de esta Sala la de que cualquier condómino está legitimado para ejercitar acciones [COMPLETAR], no tan sólo de aquella parte del espacio comprensivo de su piso o local sobre los que ostenta un derecho singular y exclusivo, sino también en defensa del interés que le corresponde sobre los elementos comunes (SS. 10 junio 1981, 3 febrero 1983, 27 abril y 23 noviembre 1984 y 12 febrero 1986 
- [ ] S. 8 junio 1992 
- [ ] Nº
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…frente a la COMUNIDAD DE PROPIETARIOS DE»; «…cuentra en un edificio en el que existen»; «…nidad de Propietarios cuyo Presidente es»; «…en la Junta de Propietarios celebrada el»; «… suscitado. En este sentido, se acudió a»; «…a Ley de Enjuiciamiento Civil esta parte»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 5 de la Ley Orgánica 1/2025
- artículo 394 del Código Civil

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

### Formulario 0048 · Demanda del propietario para exigir a la comunidad obras de mantenimiento de elementos comunes

- Año del modelo: 2023
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 18 campos de relleno marcados en blanco
- Avisos de la revisión: REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D/Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], según consta acreditado en la escritura de poder para pleitos que se acompaña al presente, ante el Tribunal comparezco y como mejor proceda en Derecho,

DIGO:

Que, por medio del presente escrito, en la representación que tengo conferida, interpongo DEMANDA DE JUICIO ORDINARIO frente a la COMUNIDAD DE PROPIETARIOS DE [COMPLETAR] en la persona de su representante legal, el Presidente de la misma, D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD], en materia de OBRAS DE MANTENIMIENTO DE ELEMENTOS COMUNES, Todo ello en base a los siguientes,

HECHOS

PRIMERO. –

Mi mandante es propietario de la siguiente finca registral:

Se acompaña como Documento núm.1 nota simple registral acreditativa de dicho extremo.

SEGUNDO El domicilio de mi mandante se encuentra en un edificio en el que existen [COMPLETAR] viviendas y sobre la que se constituyó una Comunidad de Propietarios cuyo Presidente es [COMPLETAR] en virtud del acuerdo adoptado en la Junta de Propietarios celebrada el pasado [FECHA].

Se acompaña como Documento núm. 2 Acta de la citada Junta de Propietarios.

TERCERO Esta finca cuenta con un ascensor que da acceso a todas las viviendas y que, desde el pasado [FECHA], se encuentra fuera de funcionamiento.

Se acompaña como Documento núm. 3 Acta notarial acreditativa de dicho extremo.

CUARTO. La Comunidad de Propietarios es consciente del problema existente, habiéndose tratado en la Junta de Propietarios celebrada el [COMPLETAR], sin que se haya tomado decisión alguna al respecto.

QUINTO Pese a los requerimientos efectuados por esta parte, no se ha obtenido respuesta alguna por parte de la Comunidad de Propietarios demandada, lo que motiva la necesidad de solicitar el auxilio judicial para obtener una solución al problema suscitado.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

PRIMERO. - JURISDICCIÓN Y COMPETENCIA

Al amparo de lo establecido en el artículo 52.1.8ª de la Ley de Enjuiciamiento Civil, en relación con lo dispuesto en el art. 85.1º LOPJ, corresponde a la Sección Civil de los Tribunales de Instancia de [LOCALIDAD] por ser los del lugar en que se encuentra la finca litigiosa.

SEGUNDO. – PROCEDIMIENTO Y CUANTÍA

En virtud de lo establecido en el artículo 249.1.8º de la Ley de Enjuiciamiento Civil, el procedimiento se ventilará por los cauces del juicio ordinario por tratarse de un proceso de propiedad horizontal.

TERCERO. – CAPACIDAD Y LEGITIMACIÓN

Las partes poseen capacidad para intervenir en el presente procedimiento, al amparo de lo establecido en el artículo 6 y siguientes de la Ley de Enjuiciamiento Civil.

El artículo 10 de la Ley de Enjuiciamiento Civil legitima para comparecer y actuar en juicio, a los titulares de la relación jurídica o del objeto litigioso.

En cuanto a la legitimación activa del comunero para actuar en interés de la Comunidad de Propietarios y ante la pasividad de ésta se pronuncia la Sentencia del Tribunal Supremo de 18 de mayo de 2016, rec. 1131/2014:

“La mencionada sentencia de 30 octubre de 2014, rec. 2931/2012, con cita de numerosas sentencias anteriores, resume la doctrina jurisprudencial, como complemento del ordenamiento jurídico, como se ha dicho anteriormente, en estos términos:

«Cualquiera de los comuneros puede comparecer en juicio y ejercitar acciones que competan a la comunidad, siempre que actúe en beneficio de la misma [sentencias, por todas, 10 de junio de 1981, 5 de febrero de 1983, 18 de diciembre de 1985, 17 de abril de 1990, 8 de abril de 1992 y 6 de junio de 1997, rec. 1611/1993). La sentencia núm. 46/1995, de 31 enero, afirma que «es doctrina reiterada de esta Sala la de que cualquier condómino está legitimado para ejercitar acciones [COMPLETAR], no tan sólo de aquella parte del espacio comprensivo de su piso o local sobre los que ostenta un derecho singular y exclusivo, sino también en defensa del interés que le corresponde sobre los elementos comunes (SS. 10 junio 1981, 3 febrero 1983, 27 abril y 23 noviembre 1984 y 12 febrero 1986 ], así como que no se da falta de legitimación cuando, aunque no se haya hecho constar en la demanda de una manera expresa que se actúa en nombre de la comunidad y en interés de la misma, se plantea una pretensión que, de prosperar, ha de redundar en provecho de la comunidad [S. 8 junio 1992 ]»”.

CUARTO. - REPRESENTACIÓN PROCESAL

La parte actora comparece debidamente representada por Abogado y Procurador, tal como prevén los artículos 23.1 y 31.1 de la Ley de Enjuiciamiento Civil.

QUINTO.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

SEXTO. - FONDO DEL ASUNTO

Resultan de aplicación los siguientes preceptos:

El artículo 3.b) de la Ley de Propiedad Horizontal en el que se determina que existe copropiedad en los elementos comunes, siendo competencia de la Comunidad de Propietarios el funcionamiento de los mismos.
El artículo 10.1.a) de la Ley de Propiedad Horizontal en cuanto a la obligación de la realización de los trabajos y obras necesarios para el adecuado mantenimiento y conservación del inmueble y sus elementos comunes.
El artículo 394 del Código Civil, que permite a todo comunero servirse de los servicios y elementos comunes.

SÉPTIMO. - IURA NOVIT CURIA

En todo lo no invocado en la presente demanda, opera el principio iura novit curia.

OCTAVO. - COSTAS

Deberán ser impuestas a la parte demandada en virtud de lo establecido en el artículo 394 de la Ley de Enjuiciamiento Civil.

En su virtud,

AL TRIBUNAL SUPLICO: Que teniendo por presentado este escrito junto con sus copias y documentos que le acompañan, se sirva admitirlo, me tenga por personado y parte en el presente procedimiento en la representación que ostento y tenga por formulada DEMANDA DE JUICIO ORDINARIO contra la COMUNIDAD DE PROPIETARIOS y seguidos los trámites legales oportunos, en su momento, dicte Sentencia en la que:

a) Se condene a la parte demandada a ejecutar las obras necesarias para la reparación del ascensor existente en la finca litigiosa en un plazo no superior a [Nº] meses.
b) Todo ello, con expresa imposición en costas al demandado.

OTROSÍ PRIMERO DIGO: Que en virtud de lo establecido en el artículo 231 de la Ley de Enjuiciamiento Civil esta parte [COMPLETAR].

AL TRIBUNAL SUPLICO: Que tenga por hecha la anterior manifestación a los efectos oportunos.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Ldo.

Proc.
