---
name: demanda-sucinta-juicio-verbal-611
description: "Redacta el escrito «Demanda sucinta en juicio verbal» (formulario 611 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda sucinta en juicio verbal

> Formulario 0611 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NIF
- [ ] CALLE (3 veces)
- [ ] NÚMERO (3 veces)
- [ ] TELÉFONO (3 veces)
- [ ] CORREO ELECTRÓNICO (2 veces)
- [ ] IMPORTE
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, número [NÚMERO], piso»; «…, piso [COMPLETAR], de la localidad de»; «…, número [NÚMERO], piso»; «…, piso [COMPLETAR], de la localidad de»; «…con número de teléfono [TELÉFONO], fax»; «…CINTA DE JUICIO VERBAL en reclamación de»; «…, número [NÚMERO], piso»; «…, piso [COMPLETAR], de la localidad de»; «…, con número de teléfono [TELÉFONO], fax»; «…,»; «…, [COMPLETAR]. Por:»

## Elecciones que hay que hacer

- Marque una de las siguientes opciones:)
- el interés legal / el interés pactado si fuera mayor

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 438 de la LEC
- Ley 42/2015

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

### Formulario 0611 · Demanda sucinta en juicio verbal

- Año del modelo: 2016
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (4); 1 desplegables convertidos en elección en blanco; 2 bloques de opciones sin texto dejados en blanco con sus rótulos; 27 campos de relleno marcados en blanco
- Avisos de la revisión: REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma orgánica y procesal de la LO 1/2025

AL TRIBUNAL

D./Dña. [NOMBRE Y APELLIDOS] con DNI y NIF/CIF número [NIF], domiciliado/a en la calle [CALLE], número [NÚMERO], piso [COMPLETAR], de la localidad de [COMPLETAR], con número de teléfono [TELÉFONO] y domicilio laboral en la calle [CALLE], número [NÚMERO], piso [COMPLETAR], de la localidad de [COMPLETAR] con número de teléfono [TELÉFONO], fax [COMPLETAR] y dirección de correo electrónico [CORREO ELECTRÓNICO] (1) (2).

FORMULO DEMANDA SUCINTA DE JUICIO VERBAL en reclamación de [COMPLETAR] más intereses y costas contra:

-
+
Añadir más párrafos iguales

D./Dña. [NOMBRE Y APELLIDOS] con DNI Y NIF/CIF, domiciliado/a en la calle [CALLE], número [NÚMERO], piso [COMPLETAR], de la localidad de [COMPLETAR], con número de teléfono [TELÉFONO], fax [COMPLETAR] y dirección de correo electrónico [CORREO ELECTRÓNICO], [COMPLETAR].

Por: [COMPLETAR].

[ELEGIR: Marque una de las siguientes opciones:)]

No presento documentos y/o dictámenes periciales relativos a los hechos en que baso la (contestación de la) demanda.

[ELEGIR: Marque una de las siguientes opciones:)]

No estimo pertinente la celebración de vista, solicitando que se dicte sentencia sin más trámite.

En atención a lo expuesto,

PIDO AL TRIBUNAL:

Que se condene a la parte demandada a pagarme la cantidad de [IMPORTE] más [ELEGIR: el interés legal / el interés pactado si fuera mayor], desde la interpelación judicial o requerimiento extrajudicial, así como al abono de las costas procesales.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

NOTAS DEL FORMULARIO

(1) Modelo aprobado por Acuerdo de 22 de diciembre de 2015, de la Comisión Permanente del Consejo General del Poder Judicial (BOE 28-1-2016), adaptado a la reforma orgánica y procesal de la LO 1/2025.

La Ley 42/2015, de 5 de octubre, de reforma de la Ley de Enjuiciamiento Civil, ha introducido en el artículo 438 de la LEC la previsión de que existan a disposición de los demandados, en los casos de juicios verbales en los que sea posible actuar sin abogado ni procurador, impresos normalizados para contestar a la demanda. Dichos impresos deben estar en el Tribunal a disposición de los demandados y en el Decreto de admisión se les debe comunicar esa disponibilidad.

(2) Importante: Antes de redactar el escrito de demanda de la demanda, lea con atención la guía que han de facilitarle con este modelo.

(3) Importante: Deberá presentar con la demanda todos los documentos y/o dictámenes periciales de que disponga relativos a los hechos alegados en el escrito-modelo de demanda.

(4) Documentación que se adjunta (en su caso): ...

========================================================================
