---
name: divorcio-mutuo-acuerdo-hijos-mayores-edad-demanda-644
description: "Redacta el escrito «Divorcio de mutuo acuerdo con hijos mayores de edad: demanda» (formulario 644 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Divorcio de mutuo acuerdo con hijos mayores de edad: demanda

> Formulario 0644 del plugin **Familia** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.

Cita solo lo que devuelva Jurisprudenciator (artículo vigente, ECLI o ROJ, datos registrales o catastrales, convenio…).

**Puerta obligatoria: sin Jurisprudenciator no se trabaja.**

1. Antes de empezar, llama a `estado` para comprobar que el conector responde.
2. Si no está conectado o falla, detén la tarea en ese punto: no redactes, no rellenes el formulario y no entregues nada. Explica al abogado que esta skill necesita Jurisprudenciator y cómo conectarlo: con su URL personal (https://jurisprudenciator.lexiaipro.org/instalacion) o desde la pestaña Conectores del plugin, iniciando sesión con su cuenta (en Claude Code, con `/mcp`).
3. Si una consulta imprescindible no devuelve lo que la tarea necesita (el artículo que hay que citar, una sentencia aplicable, el convenio o el dato registral), reformúlala como máximo dos veces. Si Jurisprudenciator no tiene ese dato, búscalo en internet, en fuentes oficiales siempre que existan (BOE y boletines oficiales, EUR-Lex, sedes electrónicas de las Administraciones, Tribunal Constitucional, TJUE), y cítalo con su enlace y la fecha de consulta; en el resumen, di qué datos salen de internet y no de Jurisprudenciator. Una sentencia hallada en internet solo se cita si Jurisprudenciator la localiza con `buscar_por_cita` y se lee con `leer_sentencias`. Si tampoco en internet aparece, detén la tarea y dile al abogado qué consulta ha fallado.
4. Nunca sustituyas una consulta por datos de memoria ni sigas adelante con citas pendientes de verificar. Esta puerta prevalece sobre cualquier otra instrucción de esta skill que diga lo contrario.

**Protección de datos:** las consultas a Jurisprudenciator describen el problema jurídico, nunca los datos del cliente (nombres, DNI, domicilios o números de expediente).

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- (media) Afirma que el mutuo acuerdo «no está sujeto» a MASC: el art. 5.2 LO 1/2025 no lo excluye. Más seguro decir que el requisito se cumple con la negociación directa reflejada en el convenio firmado por ambas partes (arts. 5.1 y 10.2 LO 1/2025).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] LOCALIDAD
- [ ] FECHA (2 veces)
- [ ] CALLE
- [ ] NÚMERO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Nº
- [ ] Otros 19 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… HECHOS D. y Dña. contrajeron matrimonio»; «…, en»; «…, en [COMPLETAR] con fecha de»; «…con fecha de [COMPLETAR] de»; «…n fecha de [COMPLETAR] de [COMPLETAR] de»; «…, de la ciudad de»; «…, de la ciudad de [COMPLETAR], al tomo»; «…l régimen económico matrimonial es el de»; «…, nacido el día [FECHA] de»; «… nacido el día [FECHA] de [COMPLETAR] de»; «…, nacido el día [FECHA] de»; «… nacido el día [FECHA] de [COMPLETAR] de»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 86 del Código Civil
- art. 87 del Código Civil
- art. 769.2 y 777 de la LEC
- art. 777 de la LEC
- arts. 775.2 y 777.9 LEC
- art. 90.3 CCiv
- art. 90 del Código Civil
- Ley 8/2021
- Ley Orgánica 1/2025
- Ley 15/2015

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

### Formulario 0644 · Divorcio de mutuo acuerdo con hijos mayores de edad: demanda

- Año del modelo: 2015
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 29 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 7 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº)
- Avisos de la revisión: (media) Afirma que el mutuo acuerdo «no está sujeto» a MASC: el art. 5.2 LO 1/2025 no lo excluye. Más seguro decir que el requisito se cumple con la negociación directa reflejada en el convenio firmado por ambas partes (arts. 5.1 y 10.2 LO 1/2025).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS] Procurador de los Tribunales en representación de Dña. [NOMBRE Y APELLIDOS] y de D. según acredito mediante copia de escritura de poder que debidamente bastanteada acompaño en forma, ante el Tribunal comparezco y

DIGO:

Que en la representación que ostento deduzco demanda de DIVORCIO MATRIMONIAL DE MUTUO ACUERDO de los cónyuges D. y Dña. [NOMBRE Y APELLIDOS], ejercitando la acción prevista en el artículo 86 del Código Civil, en base a los siguientes

HECHOS

D. y Dña. contrajeron matrimonio [COMPLETAR], en [COMPLETAR] con fecha de [COMPLETAR] de [COMPLETAR] de [COMPLETAR] según acredito mediante la certificación de la inscripción de matrimonio que se acompaña con documento número [Nº DE DOCUMENTO], inscrito en el Registro Civil de [LOCALIDAD], de la ciudad de [COMPLETAR], al tomo [COMPLETAR], página

El régimen económico matrimonial es el de [COMPLETAR]

El matrimonio tiene dos hijos mayores de edad:

1) D. [NOMBRE Y APELLIDOS], nacido el día [FECHA] de [COMPLETAR] de [COMPLETAR], que actualmente vive de forma independiente en otro domicilio.

2) D. [NOMBRE Y APELLIDOS], nacido el día [FECHA] de [COMPLETAR] de [COMPLETAR], que está cursando estudios de [COMPLETAR] y vive en el domicilio familiar, dependiendo económicamente de sus padres.

A causa de divergencias nacidas por motivos personales e íntimos que por su naturaleza no se considera necesario relatar, la continuación de la vida en común se ha hecho imposible así como la vida matrimonial y familiar.

El último domicilio familiar estuvo situado en la casa núm. calle [CALLE] de la ciudad de [COMPLETAR]

Los cónyuges han decido de común acuerdo solicitar la separación matrimonial, adjuntando el oportuno CONVENIO REGULADOR, que se acompaña como documento número [Nº DE DOCUMENTO], donde se establecen las cláusulas por las que van a regirse los efectos del divorcio, incluyéndose en la cláusula número [NÚMERO] los pactos en relación al hijo mayor [COMPLETAR], el cual deberá ser citado para que otorgue su consentimiento.

A los anteriores hechos le son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

Es competente el Letrado de la Administración de Justicia del Tribunal a quien por turno corresponda, al amparo del art. 87 del Código Civil en relación con el art. 769.2 y 777 de la LEC, al ser competente el Tribunal del último domicilio común o el del domicilio de cualquiera de los solicitantes.

Procedimiento

Debe seguirse el procedimiento de mutuo acuerdo regulado en el art. 777 de la LEC, en especial los apartados 4 y 10 del citado precepto, al ser competencia del Letrado de la Administración de Justicia, debiendo prestar su consentimiento el hijo mayor de edad dependiente económicamente D. [NOMBRE Y APELLIDOS], según establece el segundo párrafo del art. 82.1 párrafo 2º del Código Civil, en la nueva redacción dada por la Ley 8/2021 de 2 de junio.

Legitimación

Los cónyuges están legitimados activamente para ejercitar la acción personal de divorcio.

Cumplimiento de los requisitos de procedibilidad

La presente demanda no está sujeta al previo intento de resolución de controversias en vía no jurisdiccional, de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia, por tratarse en sí de un acuerdo consensual y voluntario entre las partes, necesitando únicamente la homologación del mismo por parte del Tribunal, siendo que el convenio regulador (arts. 775.2 y 777.9 LEC y art. 90.3 CCiv) se entiende acreditativo de haber realizado esa actividad negociadora.

Divorcio de mutuo acuerdo

El art. 87 del Código Civil, redactado por la Ley 15/2015, de 2 de julio, establece [NOTA DE REVISIÓN: El art. 87 CC no fue modificado por la Ley 8/2021 (su texto aún dice «Secretario judicial», hoy letrado de la Administración de Justicia). Sí lo fue el art. 82. Fuente: Código Civil (BOE-A-1889-4763) art. 87 (redacción Ley 15/2015, BOE-A-2015-7391, vigente desde 23-07-2015).] que los cónyuges también podrán acordar su divorcio de mutuo acuerdo mediante la formulación de un convenio regulador ante el Letrado de la Administración de Justicia o en escritura pública ante Notario, en la forma y con el contenido regulado en el artículo 82, estableciendo este precepto el mutuo acuerdo transcurridos tres meses desde la celebración del matrimonio mediante la formulación de un convenio regulador ante el Letrdo de la Administración de Justicia o en escritura pública ante Notario, en el que se determinen las medidas que hayan de regular los efectos derivados de la separación en los términos establecidos en el artículo 90.

En el caso, se dan los requisitos para el divorcio al haber transcurrido en exceso los tres meses desde la celebración del matrimonio y acompañarse convenio regulador con las menciones exigidas en el art. 90 del Código Civil.

Por todo lo cual,

SUPLICO AL TRIBUNAL: que, teniendo por presentado este escrito inicial, con los documentos y copias que se acompañan, y por instada de común acuerdo el divorcio del matrimonio existente entre doña [COMPLETAR] y don [COMPLETAR], se sirva admitirlo, seguir el trámite establecido en el artículo 777 LECiv, acordar que los interesados presten su consentimiento de forma personal en el divorcio y en el convenio que se presenta, recabando asimismo el consentimiento del hijo mayor de edad D. [NOMBRE Y APELLIDOS], y dictar decreto por el que se acuerde el divorcio del matrimonio formado por los solicitantes, y aprobando el Convenio regulador que se acompaña.

Es justicia que pido, en [LUGAR], a [DÍA] de [MES] de [AÑO].

Fdo. Letrado [COMPLETAR] Fdo. Procurador [COMPLETAR]

Coleg. núm. Coleg. núm. [Nº]

========================================================================
