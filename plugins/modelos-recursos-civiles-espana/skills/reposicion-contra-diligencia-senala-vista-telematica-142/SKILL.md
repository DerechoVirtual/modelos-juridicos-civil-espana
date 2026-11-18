---
name: reposicion-contra-diligencia-senala-vista-telematica-142
description: "Redacta el escrito «Reposición contra la diligencia que señala vista telemática» (formulario 142 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reposición contra la diligencia que señala vista telemática

> Formulario 0142 del plugin **Recursos civiles** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] COLEGIO
- [ ] FECHA (4 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…nte acreditado en autos de procedimiento»; «…con número de colegiado»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 452 LEC
- art. 451.1 LEC
- art. 137.1 LEC
- art. 137 LEC
- arts. 238.3 y 240 LOPJ
- art. 24 CE
- art. 229 LOPJ
- Ley 1/2000
- Ley 3/2020

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

### Formulario 0142 · Reposición contra la diligencia que señala vista telemática

- Año del modelo: 2021
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 12 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Recurso de reposición contra el señalamiento de vista telemática.

Formulario adaptado a la reforma procesal de la LO 1/2025.

AL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [Nº]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según tengo debidamente acreditado en autos de procedimiento [COMPLETAR], dirigido por el Letrado D./Dña. [NOMBRE Y APELLIDOS], abogado en ejercicio del Colegio de Abogados de [COLEGIO] con número de colegiado [COMPLETAR], ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que el pasado día [FECHA] se me ha notificado diligencia de ordenación de fecha [FECHA], por la que acuerda la celebración de forma telemática del próximo señalamiento de vista el día [FECHA], y estimando la misma lesiva para los intereses de mi mandante, dicho sea en términos de defensa, dentro del plazo de cinco días legalmente establecido en el art. 452 LEC, interpongo contra la misma recurso de reposición fundamentándolo en las siguientes:

ALEGACIONES

Primera.- La resolución contra la que formulo este recurso es susceptible de recurso de reposición, en virtud de lo establecido por el art. 451.1 LEC, por tratarse de una diligencia de ordenación dictada por el Letrado de la Administración de Justicia.

Se interpone el recurso de reposición dentro del plazo de cinco días previsto en el art. 452 LEC, a contar desde el siguiente al de la notificación de la resolución recurrida.

Citamos como precepto infringido a efectos del presente recurso de reposición y conforme a lo previsto en el citado art. 452 LEC, el art. 137.1 LEC a cuyo tenor, los Jueces y los Magistrados miembros del Tribunal que esté conociendo de un asunto presenciarán las declaraciones de las partes y de testigos, los careos, las exposiciones, explicaciones y respuestas que hayan de ofrecer los peritos, así como la crítica oral de su dictamen y cualquier otro acto de prueba que, conforme a lo dispuesto en esta Ley, deba llevarse a cabo contradictoria y públicamente. a cuyo tenor y, respectivamente, los Jueces y los Magistrados miembros del Tribunal que esté conociendo de un asunto presenciarán las declaraciones de las partes y de testigos, los careos, las exposiciones, explicaciones y respuestas que hayan de ofrecer los peritos, así como la crítica oral de su dictamen y cualquier otro acto de prueba que, conforme a lo dispuesto en esta Ley, deba llevarse a cabo contradictoria y públicamente.

Ello supone una vulneración del principio de inmediación, que necesariamente debe ser observado bajo sanción de nulidad, conforme expresamente establece el art. 137 LEC y también por aplicación de los arts. 238.3 y 240 LOPJ. El principio de inmediación se consagra en la Ley 1/2000, de 7 de enero, de Enjuiciamiento Civil, vigente en la tramitación del procedimiento en la primera instancia, como un principio procesal de obligada observancia bajo sanción de nulidad de pleno derecho, y el respeto y observancia del mismo supone la práctica de las pruebas a presencia del Juez, con contacto directo con las partes e intervención en la práctica de las pruebas, lo que le sitúa en condiciones de valorar las pruebas con las ventajas de la inmediación. La celebración del acto de la vista oral en forma telemática no puede equipararse a la inmediación a efecto de formar la convicción judicial sobre las afirmaciones de hechos de las partes a la hora de valorar las pruebas para dictar sentencia, porque no se percibe directamente lo que dice el testigo o la parte en el interrogatorio, y no se captan igual todos sus gestos y matices de su voz que hacen posible valorar si transmite seguridad en sus manifestaciones, ni es posible ya la intervención en la práctica de las pruebas. Estimamos que la inmediación es esencial cuando los actos de prueba tienen lugar en un juicio en el que rige el principio de oralidad, como sucede con el juicio verbal, que es el trámite seguido en este caso.

Apoyan esta argumentación los fundamentos legales y jurisprudenciales que a continuación se exponen.

Segunda.- La Ley 3/2020, de 18 de septiembre, de medidas procesales y organizativas para hacer frente al COVID-19 en el ámbito de la Administración de Justicia establece en su preámbulo que:

Una vez superado el estado de alarma, la Administración de Justicia debe adaptarse durante los próximos meses a la nueva normalidad, tomando en consideración los derechos y las necesidades de la ciudadanía como usuaria del servicio público de la Justicia en ejercicio del derecho a la tutela judicial efectiva, y garantizar el derecho a la salud tanto de esta como del conjunto del personal y profesionales del sector de la Justicia. Junto a ello, y en relación con el aumento de litigiosidad previsto, la Administración de Justicia debe prepararse no solo para dar respuesta a la misma, sino para erigirse en factor determinante en el proceso de recuperación económica.

Dicho cuerpo legal tiene como finalidad garantizar la salud de las personas y adaptar la Administración de Justicia a la situación que ha surgido una vez finalizado el estado de emergencia sanitaria de nuestro país, sin vulnerar nunca los principios constitucionales de nuestro ordenamiento jurídico, siendo lo cierto que es una actitud generalizada en los Tribunales de nuestro ámbito territorial la celebración presencial de la mayoría de los juicios y vistas, salvo casos de fuerza mayor, y ello precisamente para garantizar el principio constitucional de tutela judicial efectiva del art. 24 CE, y garantizar asimismo los principios de inmediación, oralidad y contradicción, que conforman el concepto de juicio justo.

Tercera.- La salud de los intervinientes en un juicio, Jueces y Magistrados, Letrados de la Administración de Justicia, Fiscales, Abogados y Procuradores, así como de los justiciables, está en la actualidad plenamente preservada en los Tribunales con las medidas adoptadas de uso obligatorio de mascarillas y utilización de geles desinfectantes, mantenimiento de distancia de seguridad, dispensa de utilización de togas y desinfección de la sala de vistas entre un juicio y otro.

Cuarta.- En cualquier caso, lo que no puede obviarse es que la presencialidad e intervención directa ante el Tribunal permite al Juzgador unas ventajas visuales y perceptivas que no se aprecian a través de medios telemáticos.

En este sentido, la STS de 17 de marzo de 2015, rec. 1828/2014, dice textualmente que:

El ritmo al que se suceden los avances tecnológicos obliga a no descartar que en un futuro no muy lejano la opción entre el examen presencial de los testigos/peritos y su interrogatorio mediante videoconferencia, sea una cuestión que no se plantee en términos de principalidad y subsidiariedad. Sin embargo, en el actual estado de cosas, el entendimiento histórico-convencional del principio de inmediación sigue siendo considerado un valor que preservar, sólo sacrificable cuando concurran razones que, debidamente ponderadas por el órgano jurisdiccional, puedan prevalecer sobre las ventajas de la proximidad física y personal entre las fuentes de prueba y el Tribunal que ha de valorarlas.

En suma, si bien es cierto que el art. 229 LOPJ establece que las actuaciones judiciales serán predominantemente orales y ello tiene su razón de ser en que el juicio se rige por los principios de inmediación, oralidad y publicidad, no es menos cierto que la Ley admite, con determinadas garantías, la celebración del juicio por videoconferencia; pero no se acierta a comprender que en este caso concurra causa alguna que autorice justificadamente la exclusión singular del principio de inmediación.

Debiéndose tener en cuenta, además, que el CGAE ha recomendado a todos los colegiados que para garantizar los derechos de defensa de nuestros clientes y ejercitar una defensa íntegra y completa los abogados debemos asistir presencialmente a las vistas, máxime cuando se está volviendo a la presencialidad en el resto de colectivos (sanitarios, profesores, funcionarios), de modo que vuelven a realizar sus actividades laborales de manera presencial, eso sí, adoptando las precauciones que resulten necesarias, pero con presencialidad.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL:

Que tenga por presentado este escrito, se sirva admitirlo, teniendo por formulado en tiempo y forma RECURSO DE REPOSICIÓN contra la diligencia de ordenación de fecha [FECHA] a fin de que, previa la tramitación oportuna, estime este recurso, acordando reponer la resolución recurrida, dictando decreto mediante el que se acuerde la celebración de juicio presencial.

OTROSÍ DIGO:

Que según exige la disposición adicional decimoquinta de la LOPJ, se ha procedido a consignar en la cuenta del Tribunal la cantidad de 25 euros como depósito para recurrir, según se acredita con justificante que acompaño.

Por lo que,

NUEVAMENTE SUPLICO: Que se tenga por hecha esta actuación a los efectos oportunos, por ser justicia que pido en mismo lugar y fecha.

Es justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

	Firma de Procurador/a
