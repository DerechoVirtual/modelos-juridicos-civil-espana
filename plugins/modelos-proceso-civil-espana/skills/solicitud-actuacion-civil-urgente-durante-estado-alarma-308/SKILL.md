---
name: solicitud-actuacion-civil-urgente-durante-estado-alarma-308
description: "Redacta el escrito «Solicitud de actuación civil urgente durante el estado de alarma por coronavirus» (formulario 308 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Solicitud de actuación civil urgente durante el estado de alarma por coronavirus

> Formulario 0308 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- Solicitud ligada al estado de alarma de 2020 (COVID): sin vigencia; revisar si el formulario debe mantenerse.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS
- [ ] Nº
- [ ] AÑO (2 veces)
- [ ] NIF
- [ ] DOMICILIO A EFECTOS DE NOTIFICACIONES
- [ ] FECHA
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…dor de los Tribunales, en nombre de Doña»; «…stableció la guarda y custodia del menor»; «…a se hubiere expedido; en relación a Don»; «… las siguientes, ALEGACIONES 1ª) Que Don»; «…jante a la de los casados entre los años»; «…, fruto de cuya unión nació el menor»; «…que se atribuía la misma a la madre Doña»; «…a tenido conocimiento fundado de que Don»; «…njero, concretamente a su país de origen»; «…ene el lógico y fundado temor de que Don»; «…s de origen y pretende llevarse al menor»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 763 de la LEC
- articulo 158 CC
- articulo 52 CC
- art. 158 CCiv
- Real Decreto 463/2020

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

### Formulario 0308 · Solicitud de actuación civil urgente durante el estado de alarma por coronavirus

- Año del modelo: 2020
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 20 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)
- Avisos de la revisión: Solicitud ligada al estado de alarma de 2020 (COVID): sin vigencia; revisar si el formulario debe mantenerse.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito solicitando al Tribunal de Instancia la práctica de una actuación urgente, como la prohibición de salida de un menor al extranjero, expedición de pasaporte, a pesar de la suspensión de las actuaciones judiciales conforme a la DA 2ª del RD 463/2020, de 14 de marzo, que declara el estado de alarma por coronavirus.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D/Dña [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre de Doña [COMPLETAR], cuyas circunstancias y representación ya constan en autos de procedimiento sobre Guarda y Custodia de hijos menores, en el que se estableció la guarda y custodia del menor [COMPLETAR] en favor de la madre y un régimen de visitas en favor del padre, seguidos por este Tribunal con el nº [Nº]/[AÑO], ante el mismo comparezco y como mejor proceda en derecho, DIGO:

Que, por medio del presente escrito, y en razón a la situación de pandemia señalada por la OMS, venimos a solicitar, de conformidad con la DA 2ª del Real Decreto 463/2020, de 14 de marzo, por el que se declara el estado de alarma para la gestión de la situación de crisis sanitaria ocasionada por el COVID-19, la práctica de una actuación inaplazable, a la vista del Acuerdo la Comisión Permanente del CGPJ de fecha 14 de marzo de 2020, consistente en que:

"Se suspenden todas las actuaciones judiciales programadas y los plazos procesales que tal decisión conlleva, salvo en los supuestos de servicios especiales".

Estos servicios esenciales son los que figuran en el Acuerdo 11-1 de la Comisión Permanente del CGPJ en fecha 13 de marzo de 2020 y que son las siguientes:

"1. Cualquier actuación judicial que, de no practicarse, pudiera causar perjuicio irreparable.
2. Internamientos urgentes del artículo 763 de la LEC.
3. La adopción de medidas cautelares u otras actuaciones inaplazables, como las medidas de protección de menores del articulo 158 CC.
4. Los juzgados de violencia sobre la mujer realizarán los servicios de guardia que les correspondan. En particular deberán asegurar el dictado de las órdenes de protección y cualquier medida cautelar en materia de violencia sobre la mujer y menores.
5. El Registro Civil prestará atención permanente durante las horas de audiencia. En particular, deberán asegurar la expedición de licencias de enterramiento, las inscripciones de nacimiento en plazo perentorio y la celebración de matrimonios del articulo 52 CC.
6. Las actuaciones con detenido y otras que resulten inaplazables, como adopción de medidas cautelares urgentes, levantamientos de cadáver, entradas y registros, etc.
7. Cualquier actuación en causa con presos o detenidos.
8. Actuaciones urgentes en materia de vigilancia penitenciaria."

Con ello, y a pesar de la existencia de la crisis por pandemia, y por estar en uno de los supuestos de "actuaciones urgentes" que se pueden llevar a cabo para evitar un perjuicio irreparable, se solicita la práctica de una actuación urgente consistente en a) prohibición de salida del territorio nacional, salvo autorización judicial previa, y b) prohibición de expedición del pasaporte al menor o retirada del mismo si ya se hubiere expedido; en relación a Don [COMPLETAR] con DNI/NIF [NIF] y domicilio a efectos de notificaciones en [DOMICILIO A EFECTOS DE NOTIFICACIONES], con base en las siguientes,

ALEGACIONES

1ª) Que Don [COMPLETAR] y mi patrocinada mantuvieron una relación de pareja semejante a la de los casados entre los años [COMPLETAR], fruto de cuya unión nació el menor [COMPLETAR], hasta que convinieron en separarse de hecho, siguiéndose proceso civil sobre guarda y custodia en el que se dictó sentencia de fecha [FECHA] en la que se atribuía la misma a la madre Doña [COMPLETAR], fijándose un régimen de visitas a favor del padre.

Se acompaña copia de la sentencia como documento nº [Nº DE DOCUMENTO]

2ª) Que mi representada ha tenido conocimiento fundado de que Don [COMPLETAR] ha decidido trasladarse a vivir al extranjero, concretamente a su país de origen [COMPLETAR], por lo que tiene el lógico y fundado temor de que Don [COMPLETAR] abandone España llevando consigo a su hijo al citado país y sustraerla de su custodia.

Según hemos podido saber, al parecer el padre biológico tiene otra familia en su país de origen y pretende llevarse al menor [COMPLETAR] a vivir con él, habiendo manifestado a algunos conocidos y ante el propio menor que no le volverían a ver más ni su madre ni el resto de la familia de mi mandante.

3ª) Que a fin de evitar la sustracción del citado menor por su progenitor paterno o por terceras personas es interés de mi mandante la adopción urgente de medidas de protección de menores establecidas en el art. 158 CCiv y, en particular, las siguientes: a) Prohibición de salida del territorio nacional, salvo autorización judicial previa; y b) Prohibición de expedición del pasaporte al menor o retirada del mismo si ya se hubiere expedido.

Es por ello, por lo que:

SUPLICO AL TRIBUNAL: Que dicte resolución en forma de auto en la que se acuerde la prohibición expresa de salida del menor [COMPLETAR] del territorio nacional, salvo autorización judicial previa, así como la prohibición de expedición de pasaporte a la menor o la retirada del mismo si ya se hubiera expedido.

Es justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

	Firma de Procurador/a
