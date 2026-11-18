---
name: oposicion-interesados-paso-contencioso-plazo-cumplir-764
description: "Redacta el escrito «Oposición de los interesados con paso a contencioso (plazo para cumplir una obligación)» (formulario 764 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición de los interesados con paso a contencioso (plazo para cumplir una obligación)

> Formulario 0764 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] LOCALIDAD
- [ ] CALLE (3 veces)
- [ ] NÚMERO (3 veces)
- [ ] FECHA (5 veces)
- [ ] Nº DE EXPEDIENTE
- [ ] LUGAR
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ración del correspondiente juicio verbal»; «…, PLAZA N.º»; «…de la calle [CALLE] de»; «…celebrado con la entidad que represento,»; «…/»; «…de la calle [CALLE] de»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 17.3 de la Ley 15/2015
- art. 96 LJV
- art. 1.128 del Código Civil
- arts. 17.3 y 97.3 LJV
- art. 17.3 LJV
- art. 97.2 LJV

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

### Formulario 0764 · Oposición de los interesados con paso a contencioso (plazo para cumplir una obligación)

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 26 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de oposición a la fijación de plazo solicitada por la parte contraria para la construcción de las viviendas integrantes del complejo urbanístico en cuestión, a fin de que se resuelva convertir el expediente en contencioso, con citación de las partes a la celebración del correspondiente juicio verbal [COMPLETAR].

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

Que por medio del presente escrito, y al amparo de lo dispuesto en el art. 17.3 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), procedo a mostrar mi OPOSICIÓN a la fijación de plazo solicitada de adverso, con arreglo a las siguientes

ALEGACIONES

PRIMERA.- Que el pasado [FECHA], D./Dña. [NOMBRE Y APELLIDOS] instó ante el órgano judicial al cual tengo el honor de dirigirme, la fijación de plazo para la construcción de las viviendas integrantes del complejo urbanístico sito en el nº [NÚMERO] de la calle [CALLE] de [COMPLETAR], en relación al contrato celebrado con la entidad que represento, [COMPLETAR] SL, en fecha [FECHA]. Mediante diligencia de ordenación de fecha [FECHA], se incoó el presente expediente con nº [Nº DE EXPEDIENTE] / [COMPLETAR], y se me dio traslado para realizar alegaciones, de conformidad con lo ordenado en el art. 96 LJV, y las normas comunes del mismo texto legal, a las que tal precepto se remite, contenidas en sus arts. 16 y ss LJV.

SEGUNDO.- El solicitante acude al expediente de jurisdicción voluntaria previsto en los arts. 96 y ss. de la Ley de Jurisdicción Voluntaria en relación con la previsión legal contenida en el art. 1.128 del Código Civil, en orden a fijar el plazo determinado dentro de un contrato de promoción y construcción de viviendas en un complejo urbanístico. Si bien, peticiona la fijación de un plazo de seis meses a partir del dictado de la resolución que ponga fin a este expediente, que no se corresponde al verdadero acuerdo de voluntades que fructificó en la consecución del contrato en cuestión, ni con la realidad del sector en el que la mercantil que administro se mueve.

Así, es imposible que en dicho plazo las viviendas, todavía no iniciadas, puedan estar terminadas en condiciones de ser entregadas al solicitante, cumpliendo con el contrato en cuestión. En este sentido, tal y como se recogía en el propio contrato, el inicio de las obras estaba supeditado a la concesión de las correspondientes licencias administrativas habilitantes de las mismas, a su vez, supeditadas, a la aprobación del plan urbanístico municipal que pudiera recalificar la naturaleza de los terrenos y atribuirles carácter urbanizables. El Plan se aprobó definitivamente hace poco más tres semanas, y, a día de hoy, las licencias no han sido otorgadas, aunque ha llegado a nuestro conocimiento que se encuentran en pleno proceso de tramitación, siendo muy probable que en breve se pueda disponer de ellas. En todo caso, y siguiendo el criterio técnico del arquitecto D./Dña. [NOMBRE Y APELLIDOS], contratado para realizar el proyecto y la dirección de obra, será necesario un mínimo de quince meses para terminar la vivienda, desde el momento en que se otorguen aquellas, y se pueda, en definitiva, iniciar las labores de construcción necesarias.

TERCERO.- En atención a las razones expuestas se formula el presente escrito de oposición, dentro de los cinco días posteriores a la citación recibida, en virtud de los arts. 17.3 y 97.3 LJV. Procedería, en consecuencia, convertir el expediente en contencioso, citando el Letrado de la Administración de Justicia a las partes a una vista, conforme a los trámites del juicio verbal previsto en los arts. 440 y ss. LEC; de manera que se pueda practicar la prueba correspondiente a fin de que por el Juez de Primera Instancia se fije el plazo adecuado a la obligación que nos ocupa.

CUARTO.- Que acompaño a este escrito copia de los estatutos sociales donde se acredita mi condición de administrador social único, y representante legal de la mercantil indicada; informe del arquitecto D./Dña. [NOMBRE Y APELLIDOS] en el cual aconseja el plazo propuesto por esta parte; y reportaje fotográfico de los terrenos en el cual se puede observar que las obras no han sido iniciadas a fecha actual.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito y por opuesta esta parte a la fijación de plazo para la construcción de las viviendas integrantes del complejo urbanístico sito en el nº [NÚMERO] de la calle [CALLE] de [COMPLETAR], en relación al contrato en fecha [FECHA], de conformidad con el art. 17.3 LJV; se resuelva convertir el expediente en contencioso, con citación de las partes a la celebración del correspondiente juicio verbal.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) No resulta exigible ser asistido por abogado y representado por procurador en el expediente, conforme art. 97.2 LJV.

========================================================================
