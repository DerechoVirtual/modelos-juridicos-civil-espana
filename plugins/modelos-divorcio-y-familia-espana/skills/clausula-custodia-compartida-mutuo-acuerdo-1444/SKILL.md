---
name: clausula-custodia-compartida-mutuo-acuerdo-1444
description: "Redacta el escrito «Cláusula de custodia compartida de mutuo acuerdo» (formulario 1444 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Cláusula de custodia compartida de mutuo acuerdo

> Formulario 1444 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] Nº
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… en que los hijos menores del matrimonio»; «…odia de forma compartida por períodos de»; «….»; «…ienen en que dada la edad de los menores»; «…cuanto, el domicilio del padre radica en»; «… tanto que la madre se ha domiciliado en»; «…es y extraescolares. El padre trabaja en»; «…siendo su horario laboral de»; «…es del colegio. Por su parte la madre es»

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 1444 · Cláusula de custodia compartida de mutuo acuerdo

- Año del modelo: 2008
- Revisión 17-11-2026: restos de formato retirados; 2 llamadas a nota sin texto retiradas; 10 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Cláusula de convenio regulador de la separación o del divorcio, en la que se acuerda la guarda y custodia de los hijos menores de forma compartida.

Ambos cónyuges convienen de común acuerdo en que los hijos menores del matrimonio [COMPLETAR] quedan bajo el cuidado de ambos progenitores que ejercerán la guarda y custodia de forma compartida por períodos de [COMPLETAR]. [COMPLETAR].

Ambos progenitores convienen en que dada la edad de los menores [COMPLETAR] y que los mismos ya tienen la suficiente madurez, la medida acordada resulta ser la que mejor protege su interés.

Y ello, por cuanto, el domicilio del padre radica en [COMPLETAR] en tanto que la madre se ha domiciliado en [COMPLETAR] lo que implica una cercanía tal que permite que los niños mantengan la misma ruta escolar, así como todos los aspectos sociales y culturales de su vida como estudios y actividades extraescolares, diversión y trato con amigos.

Así mismo, ambas viviendas cuentan con una disposición tal que permite que cada uno de los menores disponga de su propia habitación en cada una de ellas y demás instrumentos necesarios para desarrollar plenamente sus actividades escolares y extraescolares.

El padre trabaja en [COMPLETAR] siendo su horario laboral de [COMPLETAR] teniendo de tal manera plena disponibilidad para llevar y recoger a los menores del colegio. Por su parte la madre es [COMPLETAR] y su horario de trabajo matinal le permite la mayor parte de las intervenciones precisas para atender a los menores fuera de sus actividades escolares y extraescolares disponiendo de todas las tardes para ello.

Las anteriores circunstancias de hecho, se ven complementadas con la demostrada capacidad de ambos progenitores para asumir de forma compartida el cuidado de sus hijos y para llegar a soluciones consensuadas en su educación y cuidado. Y así lo corrobora el informe psicológico que se acompaña al presente convenio regulador.

En cualquier caso, ambos progenitores se comprometen, a fin de proteger dicho interés de los menores, a mantener, en todo momento, la necesaria fluidez en su comunicación para lograr criterios de actuación coherentes, así como una organización semejante que permita que los menores tengan la necesaria estabilidad.

(A continuación se describirá detalladamente las visitas y estancias para el progenitor que no ostente en ese momento su cuidado diario, sin perjuicio de lo muy conveniente que resultaría describir la intervención diaria de cada uno de los progenitores con los hijos no obstante permanecer y pernoctar en el domicilio de uno de ellos: así se distribuirá el día de un modo que puede ser el que sigue:

En los períodos en que los menores permanezcan con el padre, la madre acudirá diariamente a buscarlos a la salida del colegio o de la actividad extraescolar en que se encontraran y pasará con ellos el resto de la tarde reintegrándolos al domicilio paterno. En estos casos los menores comerán con su madre los miércoles.

Por su parte, en los períodos en que los menores permanezcan con la madre, el padre llevará a los mismos todas las mañanas al colegio, recogiéndolos a las [Nº] horas en el domicilio materno. Así mismo los recogerá del centro escolar o del lugar donde los menores desarrollen sus actividades extraescolares los martes, miércoles y jueves permaneciendo con ellos el resto de la tarde.

El presente modelo sirve tanto para un convenio regulador como para una petición en demanda en principio contenciosa por otras cuestiones derivadas directamente de la separación. Ello tendrá también su incidencia en la pensión de alimentos habida cuenta que se tendrá que fijar la pensión a abonar por cada uno de los progenitores con independencia de quien ostente la guarda y custodia en cada momento (en relación a esta cuestión véase Comentario y Jurisprudencia relacionada en "Guarda y custodia compartida y pensión alimenticia").

========================================================================
