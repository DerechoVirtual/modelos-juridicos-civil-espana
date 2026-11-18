---
name: monitorio-peticion-1254
description: "Redacta el escrito «Monitorio: petición» (formulario 1254 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Monitorio: petición

> Formulario 1254 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] Nº DE DOCUMENTO
- [ ] LOCALIDAD
- [ ] DNI/NIE
- [ ] FECHA (2 veces)
- [ ] NÚMERO (4 veces)
- [ ] IMPORTE (6 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…es propietario de la vivienda situada en»; «…uros. Además, estaba obligado al pago de»; «…a última cantidad ingresada en el mes de»; «…oco ha cumplido su obligación de pago de»; «…iembre, la presentación de esta petición»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 814 de la LEC
- artículo 813 de la LEC
- artículos 155.3 y 814 de la LEC
- artículos 812 y 814 de la LEC
- artículos 17 y 20 de la LAU
- artículos 2 y 4 de la Ley 10/2012

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

### Formulario 1254 · Monitorio: petición

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 29 campos de relleno marcados en blanco
- Avisos de la revisión: Escrito inicial sin referencia al requisito de procedibilidad: añadir la nota MASC (el art. 5.2 LO 1/2025 alcanza a los procesos del libro IV LEC, incluido el monitorio). · REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: No existe «Tribunal de Instancia Decano»: hay un solo TI por partido y el decanato pasó a la Presidencia del TI. La demanda se dirige a la Sección (reparto interno). Fuente: LO 1/2025 DT 3.ª (los jueces decanos pasan a la Presidencia del TI) y LOPJ arts. 84.1, 84.3 y 166 (BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], ante el Tribunal comparezco con la asistencia letrada de D./Dña [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO:

Que mediante el presente escrito y según permite el artículo 814 de la LEC formulo petición inicial promoviendo proceso monitorio frente a D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD] y DNI n.º [DNI/NIE], en atención a los siguientes

HECHOS

Se presenta listado de documentos que acompañan a la petición.

Mi representado es propietario de la vivienda situada en [COMPLETAR], que tiene cedida en alquiler a D./Dña. [NOMBRE Y APELLIDOS] en virtud de contrato de fecha [FECHA], que adjuntamos como documento n.º [NÚMERO].

La renta mensual pactada era de [IMPORTE] euros. Además, estaba obligado al pago de [COMPLETAR]. Tras las actualizaciones anuales la renta ha alcanzado un valor de [IMPORTE] euros. Desde el mes del arrendatario ha dejado de abonar las mensualidades de renta, razón por la que en este momento adeuda la cifra de [IMPORTE] euros por ese concepto.

Adjunto extracto bancario de fecha [FECHA] en el que figura la última cantidad ingresada en el mes de [COMPLETAR], como documento n.º [NÚMERO].

Tampoco ha cumplido su obligación de pago de [COMPLETAR]

Acompaño documentos que acreditan esta deuda con los n.º [NÚMERO].

La deuda generada hasta este momento asciende, en consecuencia, a [IMPORTE] euros, que es la cifra que se reclama en este procedimiento.

Los requerimientos de pago que acompaño como documento n.º [NÚMERO] no han surtido efecto.

FUNDAMENTOS DE DERECHO

Según lo establecido en el artículo 813 de la LEC, en relación con lo dispuesto en el art. 85.1º LOPJ, corresponde conocer esta petición al Tribunal del domicilio del deudor:

. En todo caso, esta parte ha indicado otros posibles lugares donde puede ser encontrado según permiten los artículos 155.3 y 814 de la LEC.

Se seguirá el cauce establecido en los artículos 814 y siguientes de la LEC, debiendo, en definitiva, citar a las partes a juicio verbal si se formulara oposición en tiempo y forma.

Los artículos 812 y 814 de la LEC exigen que se acompañe acreditación documental de la deuda. Dicha deuda proviene de la obligación de pago de la renta y otros gastos que se recoge en los artículos 17 y 20 de la LAU.

 En aplicación de los artículos 2 y 4 de la Ley 10/2012, de 20 de noviembre y la Orden HAP/2662/2012, de 13 de diciembre, la presentación de esta petición [COMPLETAR] está sujeta a la liquidación de tasa jurisdiccional..

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y copia de todo ello, lo admita el Letrado de la Administración de Justicia y tenga por formulada petición inicial de proceso monitorio, a fin de que requiera a D./Dña. [NOMBRE Y APELLIDOS] para que pague en el plazo legalmente establecido la cantidad de [IMPORTE] euros que adeuda bajo apercibimiento de que, de no hacerlo, se despachará ejecución por la cantidad adeudada más intereses y costas, debiéndose acordar, además, lo siguiente:

1.º Para el supuesto de que el deudor no pague ni se oponga en debida forma, el Letrado de la Administración de Justicia dicte decreto dando por terminado este proceso y dándonos traslado para que instemos el despacho de ejecución.

2.º Para el supuesto de que el deudor presentase oposición en tiempo y forma, acuerde el Letrado de la Administración de Justicia mediante decreto la terminación de este proceso acordando seguir los trámites de juicio verbal con traslado al actor para que pueda impugnar esta oposición, si lo considera oportuno, en el plazo de diez días, a fin de que en su día se dicte sentencia por la que se condene a D./Dña. [NOMBRE Y APELLIDOS] al pago a mi representado de la cantidad de [IMPORTE] euros, más intereses y costas.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
