---
name: medidas-cautelares-general-1040
description: "Redacta el escrito «Medidas cautelares (general)» (formulario 1040 de medidas cautelares y diligencias preliminares, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Medidas cautelares (general)

> Formulario 1040 del plugin **Medidas cautelares y diligencias preliminares** · revisado el 17-11-2026.

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

- Medida cautelar de administración judicial de bienes del «presunto incapaz» por el art. 727.2.ª LEC: en el proceso de apoyos la vía específica es el art. 762 LEC (y el defensor judicial del art. 295.4.º CC).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] Nº DE DOCUMENTO
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…nte este Tribunal y bajo número de autos»; «…rma continua de su producción y recursos»; «…o de muebles, efectivo, títulos valores,»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 762.3 de la LEC
- arts. 734 a 736 de la LEC

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

### Formulario 1040 · Medidas cautelares (general)

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 1 rangos de artículos despegados («25 a31» → «25 a 31»); 14 campos de relleno marcados en blanco
- Avisos de la revisión: Medida cautelar de administración judicial de bienes del «presunto incapaz» por el art. 727.2.ª LEC: en el proceso de apoyos la vía específica es el art. 762 LEC (y el defensor judicial del art. 295.4.º CC).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales, en nombre y representación de [NOMBRE DEL REPRESENTADO/A]

D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], ante el Tribunal comparezco con asistencia letrada de D./Dña. [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO:

Opciones:

S Que ante este Tribunal y bajo número de autos [COMPLETAR] viene tramitándose, a instancia de mi mandante proceso sobre la adopción de medidas judiciales de apoyo a personas con discapacidad de D./Dña. Mediante el presente escrito solicito la adopción de las MEDIDAS CAUTELARES que se detallan en el cuerpo del presente escrito.

S Que mediante el presente escrito y existiendo una posible situación de discapacidad que afecta a D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD], mediante el presente escrito intereso la adopción de las medidas cautelares que se concretarán en el suplico de este escrito en atención a los siguientes

PRESUPUESTOS

PRIMERO.— Los apartados 1 y 2 del art. 762 de la LECiv contemplan la adopción de medidas cautelares tan pronto se tenga conocimiento de la existencia de una persona en una situación de discapacidad que requiera medidas de apoyo a fin de proteger adecuadamente a la persona o a su patrimonio, antes del inicio del procedimiento o en cualquier estado del mismo.

SEGUNDO.— Mi representada ha tenido conocimiento de que, desde que se planteó la situación de discapacidad, el patrimonio de la persona afectada está siendo objeto de una administración que ocasiona una merma continua de su producción y recursos [COMPLETAR] (desarrollar circunstancias que así lo indiquen y aportar la documentación acreditativa).

TERCERO.— Según lo dispuesto en el art. 762.3 de la LEC, la presente solicitud se tramitará por el cauce previsto en los arts. 734 a 736 de la LEC, con la convocatoria de las partes a vista.

CUARTO.— Las medidas cautelares cuya adopción se solicita son las siguientes:

I.ADMINISTRACIÓN JUDICIAL DE LOS BIENES productivos de la persona respecto de la que se ha solicitado la provisión de medidas de apoyo D./Dña. [NOMBRE Y APELLIDOS] [NOTA DE REVISIÓN (comprobar): En el proceso de apoyos las medidas cautelares se rigen por el art. 762 LEC (y el defensor judicial administrador por el art. 295.4.º CC). Fuente: LEC 1/2000 (BOE-A-2000-323) art. 762, redacción Ley 8/2021 (BOE-A-2021-9233).]

Como ha quedado apuntado, se justifica la necesidad de esta medida, prevista específicamente en el art. 727.2.ª de la LEC, por la necesidad de salvaguardar el patrimonio de D./Dña. [NOMBRE Y APELLIDOS] en tanto se substancia este procedimiento de su incapacitación.

II. (Se plantearán las demás medidas cautelares que resulten pertinentes al caso y compatibles entre sí. Entre las más usuales: 1. Formación de inventario de bienes. 2. Depósito de muebles, efectivo, títulos valores, [COMPLETAR] 3. Anotación preventiva de demanda. 4. Otras anotaciones registrales. 5. Órdenes judiciales conminatorias).

Por todo lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño, teniendo por formulada solicitud de adopción de las medidas cautelares propuestas para la salvaguarda del patrimonio de D./Dña. [NOMBRE Y APELLIDOS], y previa la tramitación pertinente, se dicte resolución por la que se acuerde la adopción de las medidas cautelares que se dejan solicitadas.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
