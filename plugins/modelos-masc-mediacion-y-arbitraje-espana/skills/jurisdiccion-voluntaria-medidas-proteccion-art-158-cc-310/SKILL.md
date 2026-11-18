---
name: jurisdiccion-voluntaria-medidas-proteccion-art-158-cc-310
description: "Redacta el escrito «Jurisdicción voluntaria de medidas de protección del art. 158 CC» (formulario 310 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Jurisdicción voluntaria de medidas de protección del art. 158 CC

> Formulario 0310 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] LOCALIDAD
- [ ] FECHA
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, vecino/a de»; «…nació»; «…, hijo de ambos, el día [FECHA] de»; «…de [COMPLETAR] de»; «…de [COMPLETAR], en la ciudad de»; «…nor que actualmente tiene 2 años de edad»; «…l Registro civil de dicha ciudad al Tomo»; «…, libro»; «…, libro [COMPLETAR], página»; «…a desarrollando en relación con su hijo.»; «…la representación que, otorgada por Doña»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 158 del Código Civil
- art. 158 del Código Civil

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

### Formulario 0310 · Jurisdicción voluntaria de medidas de protección del art. 158 CC

- Año del modelo: 2020
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 20 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dª [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre de D./Dª [NOMBRE Y APELLIDOS], representación que acredito mediante copia digitalizada de de poder que acompaño, ante el Tribunal comparezco y como mejor proceda en Derecho, DIGO:

Que mediante el presente escrito, al amparo del artículo 87 de la Ley de Jurisdicción Voluntaria y artículo 158 del Código Civil, promuevo expediente de jurisdicción voluntaria solicitando que se suspenda cautelarmente el régimen de visitas al que haremos mención, debiendo emplazarse para que comparezca en el mismo a D./Dª [NOMBRE Y APELLIDOS], vecino/a de [COMPLETAR], con domicilio en [LOCALIDAD], con base en los siguientes HECHOS

Hechos

PRIMERO.- Fruto de las relaciones sentimentales habidas entre mi mandante y D./Dª [NOMBRE Y APELLIDOS] nació [COMPLETAR], hijo de ambos, el día [FECHA] de [COMPLETAR] de [COMPLETAR], en la ciudad de [COMPLETAR]. El nacimiento del/la menor que actualmente tiene 2 años de edad [COMPLETAR], figura inscrito en el Registro civil de dicha ciudad al Tomo [COMPLETAR], libro [COMPLETAR], página [COMPLETAR].

Adjunto acompañamos como DOCUMENTO NÚM. UNO certificación literal de nacimiento.

SEGUNDO.- Desde el nacimiento del menor, por acuerdo de ambos progenitores, asumió de hecho la guarda y custodia del mismo la madre, mi representada.

D. [NOMBRE Y APELLIDOS], progenitor no custodio, viene recogiendo a su hijo/a los fines de semana alternos, el viernes al finalizar el horario de la guardería, acompañando al/la menor a dicho centro el lunes por la mañana.

Dada la fluidez de las relaciones entre los progenitores, no han considerado hasta la fecha la necesidad de regular judicialmente sus relaciones parentales, no obstante, en la guardería a la que llevan al menor tenían instrucciones expresas en el sentido de que el padre recogerá al niño los viernes alternos.

TERCERO.- El progenitor no custodio perdió hace dos meses su puesto de trabajo, como consecuencia de un ERE que tuvo lugar en la empresa en la que trabajaba, lo que, al parecer, le ha sumido en una depresión profunda que conlleva una gran apatía en lo que al cuidado y atención del menor se refiere.

De hecho en dos ocasiones mi mandante se ha visto obligada a ir a recoger a su hijo, previo aviso de los vecinos, al haber observado al mismo desamparado, llorando, mientras su padre se encontraba en evidente estado de ebriedad.

La situación está poniendo al menor en grave riesgo, puesto que la última de las ocasiones fue recogido en el portal del domicilio por parte de su madre, tal como consta en el atestado policial que se acompaña como documento núm [Nº DE DOCUMENTO], estando el menor totalmente abandonado y desnutrido.

A los anteriores hechos les son de aplicación los siguientes FUNDAMENTOS DE DERECHO

Fundamentos de Derecho

PRIMERO.- COMPETENCIA. Son competentes los Tribunales de Instancia de esta ciudad, por ser la del domicilio del hijo, conforme a lo dispuesto en el art. 87.2 de la Ley de Jurisdicción Voluntaria en relación con lo dispuesto en el art. 85.1º LOPJ.

SEGUNDO.- PROCEDIMIENTO. Debe seguirse el procedimiento de jurisdicción voluntaria regulado en los artículos 87 y siguientes de la Ley de Jurisdicción Voluntaria.

TERCERO.- LEGITIMACIÓN. Esta parte está legitimada conforme a lo dispuesto en el art. 158 del Código Civil y art. 87.1 de la Ley de Jurisdicción Voluntaria.

CUARTO.- FUNDAMENTOS DE FONDO. El art. 158.6º del Código Civil dispone que la autoridad judicial puede acordar la suspensión cautelar en el ejercicio de la patria potestad y/o en el ejercicio de la guarda y custodia, la suspensión cautelar del régimen de visitas y comunicaciones establecidos en resolución judicial o convenio judicialmente aprobado y, en general, las demás disposiciones que considere oportunas, a fin de apartar al menor de un peligro o de evitarle perjuicios en su entorno familiar o frente a terceras personas. En este caso, y en tanto subsista la situación emocional del padre, las visitas están poniendo en grave riesgo la integridad de un niño de tan corta edad, tal como queda constatado por los episodios relatados, por lo que debe acordarse la suspensión de las visitas que el progenitor no custodio venía desarrollando en relación con su hijo.

[COMPLETAR]

Por lo expuesto:

SUPLICO AL TRIBUNAL tenga por presentado este escrito, me tenga por parte en la representación que, otorgada por Doña [COMPLETAR], asumo, entendiéndose conmigo las sucesivas actuaciones, por promovido y se incoe el oportuno expediente de jurisdicción voluntaria, y una vez oído el progenitor no custodio y el Ministerio fiscal, y practicadas cuantas actuaciones se consideren necesarias, se dicte en su día auto por el que se acuerde, como medida de protección del menor, la suspensión de las visitas que venía desarrollando el padre del menor.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del Abogado y Procurador.
