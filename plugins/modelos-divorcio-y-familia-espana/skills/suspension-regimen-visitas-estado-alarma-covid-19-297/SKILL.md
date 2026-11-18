---
name: suspension-regimen-visitas-estado-alarma-covid-19-297
description: "Redacta el escrito «Suspensión del régimen de visitas por el estado de alarma del COVID-19» (formulario 297 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Suspensión del régimen de visitas por el estado de alarma del COVID-19

> Formulario 0297 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] Nº DE DOCUMENTO
- [ ] Nº DE COLEGIADO/A
- [ ] COLEGIO
- [ ] DNI/NIE
- [ ] DOMICILIO A EFECTOS DE NOTIFICACIONES
- [ ] NÚMERO
- [ ] FECHA
- [ ] Nº
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…, Hechos y consideraciones jurídicas: 1ª»; «…la guarda y custodia de los hijos de Don»; «…y Doña»; «…y Doña [COMPLETAR], cuyos nombres son»; «…, cuyos nombres son [COMPLETAR] y»; «…, y que tienen en la actualidad»; «…. 2ª»; «… la residencia actual de los menores. 3ª»; «…anto a su tramitación al art. 85 LJV. 4ª»; «…es uno de los progenitores del menor. 5ª»; «…ado en ejercicio que redacta y firma. 6ª»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 158 del Código Civil
- art. 87.1.a) de la Ley 15/2015
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

### Formulario 0297 · Suspensión del régimen de visitas por el estado de alarma del COVID-19

- Año del modelo: 2020
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 29 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Solicitud de expediente de jurisdicción voluntaria sobre suspensión del régimen de visitas al amparo del art. 158 del Código Civil como consecuencia del estado de alarma decretado por la crisis sanitaria del COVID-19.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], asistida por el/la Letrado/a D./Dña. [NOMBRE Y APELLIDOS], colegiado/a nº [Nº DE COLEGIADO/A] del Ilustre Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco y, como mejor proceda en Derecho, DIGO:

Que por medio del presente escrito, y de conformidad con lo previsto en el art. 87.1.a) de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo EXPEDIENTE EN SOLICITUD DE ADOPCIÓN DE MEDIDAS DE PROTECCIÓN DE LOS MENORES; en relación a D./Dña. [NOMBRE Y APELLIDOS] con DNI nº [DNI/NIE] y domicilio a efectos de notificaciones en [DOMICILIO A EFECTOS DE NOTIFICACIONES], con base en los siguientes,

Hechos y consideraciones jurídicas:

1ª [COMPLETAR])

Que, en virtud de sentencia de separación/divorcio/adopción de medidas paterno-filiales número [NÚMERO] de fecha [FECHA] dictada por ese Tribunal, se acordó que la guarda y custodia de los hijos de Don [COMPLETAR] y Doña [COMPLETAR], cuyos nombres son [COMPLETAR] y [COMPLETAR], y que tienen en la actualidad [COMPLETAR] y [Nº], años, respectivamente, se atribuyese a la madre/padre, fijándose un régimen de visitas a favor del padre/madre, consistente en [DESCRIBIR].

2ª [COMPLETAR])

Que el Decreto 463/2020, de 14 de marzo, por el que se declara el estado de alarma para la gestión de la situación de crisis sanitaria ocasionada por el COVID-19, ha limitado la libertad de circulación de las personas durante la vigencia del estado de alarma y si bien se contempla que las personas podrán circular por las vías de uso público para la asistencia y cuidado de menores (art. 7.1.e), en el presente caso, constituye un riesgo para la salud de los menores y de los propios progenitores, que aconseja evitar el desplazamiento a un domicilio manifiestamente alejado de la residencia actual de los menores.

3ª [COMPLETAR])

Que, a la vista de las circunstancias expuestas, la protección del interés superior de los menores aconseja que los menores permanezcan en el domicilio del progenitor custodio y que se suspenda el régimen de visitas concedido al padre/madre en la sentencia. Se solicita, por ello, la incoación del expediente previsto en el art. 87.1.a) LJV, que se remite en cuanto a su tramitación al art. 85 LJV.

4ª [COMPLETAR])

Que mi representada está legitimada activamente para el ejercicio de la solicitud efectuada en petición de adopción de tales medidas, conforme a lo dispuesto en los arts. 158 CCiv y 87.3 LJV, por cuanto es uno de los progenitores del menor.

5ª [COMPLETAR])

Que no obstante no ser preceptiva la intervención de Procurador y Abogado, conforme a lo dispuesto en los arts. 3.2 y 85.3 LJV, se presenta por medio de Procurador legalmente habilitado para actuar ante los tribunales de este partido, y bajo la dirección de Letrado en ejercicio que redacta y firma.

6ª [COMPLETAR])

Que es competente el Tribunal de Instancia al que me dirijo conforme al art. 87.2 LJV, al haber conocido del procedimiento en el que se estableció la guarda y custodia en favor del/a padre/madre y un régimen de visitas en favor del/a padre/madre.

Por todo lo expuesto, al amparo del art. 158.6º CCiv, y de los arts. 87 y ss. LJV,

SUPLICO AL TRIBUNAL:

Que tenga por presentado este escrito, lo admita, y por promovido expediente de jurisdicción voluntaria para la adopción de medidas de protección en relación a los menores [COMPLETAR] y [COMPLETAR], y practicadas las diligencias oportunas, dicte resolución en forma de auto en la que se acuerde la adopción de la medida consistente en suspender el régimen de visitas de los menores con su padre/madre mientras subsista el estado de alarma declarado para la gestión de la situación de crisis sanitaria ocasionada por el COVID-19.

Es justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

	Firma de Procurador/a
