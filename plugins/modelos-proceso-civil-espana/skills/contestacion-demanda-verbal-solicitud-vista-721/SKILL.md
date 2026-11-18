---
name: contestacion-demanda-verbal-solicitud-vista-721
description: "Redacta el escrito «Contestación a la demanda verbal con solicitud de vista» (formulario 721 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a la demanda verbal con solicitud de vista

> Formulario 0721 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] NOMBRE DEL REPRESENTADO/A (2 veces)
- [ ] SEDE (2 veces)
- [ ] NÚMERO
- [ ] FECHA (2 veces)
- [ ] CALLE (2 veces)
- [ ] LUGAR
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ales, y bajo la dirección Letrada de Don»; «…numeración del juzgado de procedencia).]»; «…rado de la Administración de Justicia de»; «…paño, y bajo la dirección Letrada de Don»; «…esta parte de la demanda formulada por D»; «…en reclamación de»; «…cía Local que se acompaña como documento»; «…, habiendo sido testigos del accidente D»; «…y D»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS

## Párrafos opcionales (1)

Inclúyelos solo si encajan en los hechos:

- OTROSÍ DIGO que se acompaña en anexo relación de documentos, debidamente foliados y con índice electrónico, pa…

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 1902 del Código Civil
- artículo 394 LEC
- Real Decreto Legislativo 8/2004

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

### Formulario 0721 · Contestación a la demanda verbal con solicitud de vista

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 bloques de alternativas señalados; 1 párrafos opcionales señalados; 22 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

D/Dª [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales, actuando en representación de [NOMBRE DEL REPRESENTADO/A], según se acredita mediante certificación del registro electrónico de apoderamientos judiciales, y bajo la dirección Letrada de Don [COMPLETAR] ante la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. «De los de» es residuo de los varios juzgados de una plaza. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] en el proceso declarativo verbal arriba expresado comparezco y, como mejor proceda en Derecho,

D/Dª [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales, actuando en representación de [NOMBRE DEL REPRESENTADO/A], según se acredita en virtud de apoderamiento apud acta otorgado ante el Letrado de la Administración de Justicia de [COMPLETAR] que acompaño, y bajo la dirección Letrada de Don [COMPLETAR] ante la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO] en el proceso declarativo verbal arriba expresado comparezco y, como mejor proceda en Derecho,

DIGO:

Que habiéndose dado traslado a esta parte de la demanda formulada por D [COMPLETAR] en reclamación de [COMPLETAR], siguiendo instrucciones de mi poderdante por medio del presente escrito y en nombre del mismo formulo en tiempo y forma CONTESTACIÓN A LA DEMANDA, la cual baso en los siguientes

Hechos

Negamos los hechos relatados en el escrito de demanda, salvo aquellos que sean expresamente aceptados a lo largo de este escrito.

Se acepta la titularidad del vehículo y el accidente ocurrido el día [FECHA], pero se niega totalmente que el accidente se produjera en la forma relatada en la demanda, tal como se expresa seguidamente.

Se niegan totalmente los hechos segundo y tercero de la demanda, por cuanto que el accidente se produjo estando detenido el vehículo conducido por mi representado en el ceda el paso de la calle [CALLE], por lo que en modo alguno rebasó el citado ceda el paso como se hace constar en la demanda.

En efecto, mi representado, al llegar a la altura del cruce con la calle [CALLE], detuvo el vehículo en el ceda el paso que existe en el citado cruce al percatarse que venía el vehículo del demandante por la calle principal.

Fue el vehículo del demandante que, al llegar a la altura del cruce, se desvió inopinadamente hacia la izquierda, colisionando con una farola, lo cual es imputable exclusivamente a su propia impericia.

Así consta en el atestado que realizó la Policía Local que se acompaña como documento [COMPLETAR], habiendo sido testigos del accidente D [COMPLETAR] y D [COMPLETAR]

No niega esta parte que el vehículo del actor sufriera los daños que refiere, si bien la responsabilidad en el siniestro es exclusivamente suya, sin que concurra negligencia alguna en mi representado.

Por todo ello, la demanda debe ser desestimada.

Fundamentos de derecho

Conformes con la competencia objetiva y territorial del Tribunal, y el procedimiento verbal, aceptando la cuantía, compareciendo esta parte con la debida representación técnica y asistencia letrada.

En cuanto al fondo de la reclamación, no es acceder a la misma por no ser aplicables los preceptos invocados de contrario, el artículo 1902 del Código Civil y el art. 1 del Texto Refundido de la Ley sobre responsabilidad civil y seguro en la circulación de vehículos a motor aprobado por Real Decreto Legislativo 8/2004, de 29 de octubre, al producirse el siniestro por culpa exclusiva del demandante.

Las costas deben imponerse a la actora, de conformidad con lo dispuesto en el artículo 394 LEC.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL: que teniendo por presentado este escrito, con sus documentos, y copias de todo ello, se sirva admitirlo, y tenga por formulada CONTESTACIÓN A LA DEMANDA y, tras los trámites legales, incluida la celebración de vista que interesamos por otrosí, dicte Sentencia desestimatoria de la pretensión formulada de contrario, todo ello con expresa imposición de costas a la parte actora.

[OPCIONAL — incluir si procede]

OTROSÍ DIGO que se acompaña en anexo relación de documentos, debidamente foliados y con índice electrónico, para su debida localización y consulta.

SUPLICO AL TRIBUNAL tenga hecha esta manifestación a los efectos oportunos y por aportados los documentos e informe pericial relacionados en el anexo.

Es justicia que pido en [LUGAR], a [FECHA].

Abogado/a	Procurador/a

Fdo. D./Dña. [NOMBRE Y APELLIDOS] D. [NOMBRE Y APELLIDOS]: 	Fdo. D./Dña. [NOMBRE Y APELLIDOS] D. [NOMBRE Y APELLIDOS]:

========================================================================
