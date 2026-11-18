---
name: medidas-ejercicio-inadecuado-guarda-administracion-474
description: "Redacta el escrito «Medidas por ejercicio inadecuado de la guarda o administración de bienes (art. 158 CC)» (formulario 474 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Medidas por ejercicio inadecuado de la guarda o administración de bienes (art. 158 CC)

> Formulario 0474 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] Nº
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] NÚMERO
- [ ] COLEGIO
- [ ] NIF
- [ ] DOMICILIO A EFECTOS DE NOTIFICACIONES
- [ ] FECHA (2 veces)
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] LOCALIDAD (2 veces)
- [ ] Otros 15 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Procurador/a de los Tribunales y de Doña»; «…a se hubiere expedido; en relación a Don»; «… consideraciones jurídicas: 1.ª) Que Don»; «…jante a la de los casados entre los años»; «…, fruto de cuya unión nació el menor»; «…que se atribuía la misma a la madre Doña»; «…a tenido conocimiento fundado de que Don»; «…njero, concretamente a su país de origen»; «…s de origen y pretende llevarse al menor»; «…remos, interesamos que sea oído el menor»; «…, que en la actualidad cuenta con»; «…didas de protección en relación al menor»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 87.1.a) de la Ley 15/2015
- art. 158 CCiv
- art. 87.1.a) LJV
- art. 85 LJV
- arts. 158 CCiv
- arts. 3.2 y 85.3 LJV
- art. 87.2 LJV

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

### Formulario 0474 · Medidas por ejercicio inadecuado de la guarda o administración de bienes (art. 158 CC)

- Año del modelo: 2017
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 29 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de solicitud de prohibición de salida de un menor al extranjero, expedición de pasaporte, y sometimiento a autorización judicial previa de cualquier cambio de domicilio.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [Nº]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de Doña [COMPLETAR], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, asistida por el/la Letrado/a D./Dña. [NOMBRE Y APELLIDOS], colegiado/a n.º [NÚMERO] del Ilustre Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco y, como mejor proceda en Derecho, DIGO:

Que por medio del presente escrito, y de conformidad con lo previsto en el art. 87.1.a) de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo EXPEDIENTE EN SOLICITUD DE ADOPCIÓN DE MEDIDAS DE PROTECCIÓN DEL MENOR relativas a: a) prohibición de salida del territorio nacional, salvo autorización judicial previa, y b) prohibición de expedición del pasaporte al menor o retirada del mismo si ya se hubiere expedido; en relación a Don [COMPLETAR] con DNI/NIF [NIF] y domicilio a efectos de notificaciones en [DOMICILIO A EFECTOS DE NOTIFICACIONES], con base en los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que Don [COMPLETAR] y mi patrocinada mantuvieron una relación de pareja semejante a la de los casados entre los años [COMPLETAR], fruto de cuya unión nació el menor [COMPLETAR], hasta que convinieron en separarse de hecho, siguiéndose proceso civil sobre guarda y custodia en el que se dictó sentencia de fecha [FECHA] en la que se atribuía la misma a la madre Doña [COMPLETAR], fijándose un régimen de visitas a favor del padre.

Se acompaña copia de la sentencia como documento número [Nº DE DOCUMENTO].

2.ª) Que mi representada ha tenido conocimiento fundado de que Don [COMPLETAR] ha decidido trasladarse a vivir al extranjero, concretamente a su país de origen [COMPLETAR], por lo que tiene el lógico y fundado temor de que el demandado utilice alguno de los fines de semana que tiene consigo a su hijo para llevarlo consigo al citado país y sustraerla de su custodia.

Según hemos podido saber, al parecer el padre biológico tiene otra familia en su país de origen y pretende llevarse al menor [COMPLETAR] a vivir con él, habiendo manifestado a algunos conocidos y ante el propio menor que no le volverían a ver más ni su madre ni el resto de la familia de mi mandante.

A fin de acreditar estos extremos, interesamos que sea oído el menor [COMPLETAR], que en la actualidad cuenta con [COMPLETAR] de edad, y ofrecemos información testifical de las personas que indicamos en el otrosí, quienes conocen perfectamente la situación personal, familiar y social del menor.

3.ª) Que a fin de evitar la sustracción del citado menor por su progenitor paterno o por terceras personas es interés de mi mandante la adopción urgente de medidas de protección de menores establecidas en el art. 158 CCiv y, en particular, las siguientes: a) Prohibición de salida del territorio nacional, salvo autorización judicial previa; y b) Prohibición de expedición del pasaporte al menor o retirada del mismo si ya se hubiere expedido. Se solicita, por ello, la incoación del expediente previsto en el art. 87.1.a) LJV, que se remite en cuanto a su tramitación al art. 85 LJV.

4.ª) Que mi representada está legitimada activamente para el ejercicio de la solicitud efectuada en petición de adopción de tales medidas, conforme a lo dispuesto en los arts. 158 CCiv y 87.3 LJV, por cuanto es uno de los progenitores del menor.

5.ª) Que no obstante no ser preceptiva la intervención de Procurador y Abogado, conforme a lo dispuesto en los arts. 3.2 y 85.3 LJV, se presenta por medio de Procurador legalmente habilitado para actuar ante los tribunales de este partido, y bajo la dirección de Letrado en ejercicio que redacta y firma

6.ª) Que es competente la Sección Civil del Tribunal de Instancia al que me dirijo conforme al art. 87.2 LJV, en relación con lo dispuesto en el art. 85.1º LOPJ, al haber conocido del procedimiento en el que se estableció la guarda y custodia en favor de la madre y un régimen de visitas en favor del padre.

Por todo lo expuesto, al amparo del art. 158.3.º CCiv, y de los arts. 87 y ss. LJV,

SUPLICO AL TRIBUNAL:

Que tenga por presentado este escrito, y documentos que lo acompañan, lo admita, y por promovido expediente de jurisdicción voluntaria de medidas de protección en relación al menor [COMPLETAR], y practicadas las diligencias oportunas, con audiencia del menor, práctica de la información testifical interesada y con intervención del Ministerio Fiscal, y previos los demás trámites con arreglo a Derecho dicte resolución en forma de auto en la que se acuerde la prohibición expresa de salida del menor [COMPLETAR] del territorio nacional, salvo autorización judicial previa, así como la prohibición de expedición de pasaporte a la menor o la retirada del mismo si ya se hubiera expedido.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

OTROSÍ PRIMERO DIGO: Que para los fines expuestos se interesa de este Tribunal que por el Letrado de la Administración de Justicia se libre oficio al Ministerio del Interior, Dirección General de la Policía, informándole de la prohibición de salida del territorio nacional, salvo autorización judicial previa, del menor [COMPLETAR]; así como de la prohibición de expedición de pasaporte al niño o retirada de éste si ya se hubiese expedido.

SUPLICO AL TRIBUNAL que tenga por realizadas las anteriores manifestaciones.

OTROSÍ SEGUNDO DIGO: Que para acreditar la certeza de los hechos relatados, solicito que sea oído el menor [COMPLETAR] y ofrezco los siguientes testigos que, por razón de su conocimiento de los hechos, pueden declarar sobre la situación de la menor y el riesgo de sustracción por parte de su padre biológico:

- D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD].
- D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD].

SUPLICO AL TRIBUNAL que tenga por propuestos a los testigos indicados, admitiendo la testifical ofrecida, comprometiéndose esta parte a que comparezcan en el día y hora que se señale.

Es Justicia que reitero en lugar y fecha indicados ut supra.

Firma de Abogado/a	Firma de Procurador/a

========================================================================
