---
name: plan-relaciones-familiares-aragon-349
description: "Redacta el escrito «Plan de relaciones familiares (Aragón)» (formulario 349 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Plan de relaciones familiares (Aragón)

> Formulario 0349 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] Nº DE DOCUMENTO
- [ ] NOMBRE Y APELLIDOS (10 veces)
- [ ] IMPORTE (3 veces)
- [ ] Nº
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…men económico matrimonial. Que Don /Doña»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS

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

### Formulario 0349 · Plan de relaciones familiares (Aragón)

- Año del modelo: 2019
- Revisión 17-11-2026: 1 bloques de alternativas señalados; 14 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Plan de relaciones familiares del Derecho foral de Aragón que regula el régimen de convivencia y de visitas con los hijos, la relación de los menores con sus parientes, el destino de la vivienda y ajuar familiar, participación en los gastos de los hijos y la liquidación del régimen económico matrimonial.

Que Don /Doña [COMPLETAR], en cumplimiento de lo exigido por el apartado 3 de la Disposición Adicional Segunda/la Disposición Adicional Tercera del Código del Derecho Foral de Aragón, adjunta a la presente demanda de separación/divorcio/adopción de medidas reguladoras de las relaciones familiares tras la ruptura de la convivencia de los padres, como documento nº [Nº DE DOCUMENTO], conteniendo un Plan de relaciones familiares en el que la parte demandante/demandada propone las normas que han de regir dichas relaciones familiares en lo sucesivo.

I. AUTORIDAD FAMILIAR

La ruptura de la convivencia de los progenitores no afecta a los derechos y obligaciones propios de la autoridad familiar. Toda decisión, resolución o medida que afecte a los hijos menores de edad se adoptará en atención al beneficio e interés de los mismos.

II. GUARDA Y CUSTODIA DE LOS HIJOS

Se solicita la atribución de la guarda y custodia individual de los menores a favor de la parte demandante/demandada.

III. RÉGIMEN DE COMUNICACIONES Y ESTANCIAS

III.1. Don/Doña [NOMBRE Y APELLIDOS], como progenitor con quien no estarán los hijos, dispondrá de un derecho de visitas ordinario, de modo que podrá tener en su compañía al/a los hijo/s común/nes de la manera siguiente:

a) Semanal: El padre podrá tener consigo a los hijos un fin de semana de cada dos, de sábado por la mañana a domingo por la tarde, recogiéndolos y devolviéndolos en el domicilio de la madre, en horas que respeten el horario habitual de los niños.

Podrá igualmente tener consigo a los hijos una tarde entre semana, entre martes o jueves, a convenir entre los padres, recogiéndolos en el colegio, y depositándolos en el domicilio de la madre.

b) Periodos de vacaciones: Por Navidad, los hijos pasarán la mitad de sus vacaciones escolares con el padre y la mitad con la madre, rotando éstos anualmente el período que pasarán con cada uno, empezando este año con la primera porción con la madre y la segunda con el padre, sin perjuicio de intercambiarse el turno por acuerdo de los padres.

En Semana Santa, los hijos pasarán un año con el padre y otro con la madre en años alternos.

Durante el período de vacaciones de verano escolares, correspondiente a los meses de julio y agosto, pasarán los hijos un mes con el padre y otro con la madre, a convenir entre éstos con la suficiente antelación, y caso de desacuerdo, la madre elegirá los años pares y el padre los impares.

III.2. Como régimen de visitas a favor de los abuelos se establece el siguiente:

c) En general: En los fines de semana y periodos vacacionales en que al padre corresponda tener consigo a los hijos, si el mismo estuviera fuera de la localidad, como ocurre por motivos laborales, podrán encargarse de tener consigo a aquéllos los abuelos paternos, D. y D.ª [NOMBRE Y APELLIDOS], quienes les recogerán y devolverán en el domicilio de la madre, como sea de costumbre, pudiendo pasar estos periodos los menores en el domicilio, bien del padre, bien en el de los abuelos.
d) Semanal: Una tarde de la semana, de martes a jueves, aparte de la que haya elegido el padre por corresponderle, los abuelos paternos podrán tener en su compañía a los hijos, tomándolos a la salida del colegio y devolviéndolos antes de las 22.00 horas al domicilio de la madre.

III.3. Normas generales.

e) Se favorecerán las relaciones de los hijos, no sólo con los abuelos paternos, como se regula, sino con los parientes del padre, en especial, el hermano menor de la abuela paterna, D. [NOMBRE Y APELLIDOS] y su esposa, así como con la abuela materna D.ª [NOMBRE Y APELLIDOS]
f) Las visitas pactadas como semanales ordinarias se suspenderán durante los periodos de vacaciones.
g) El padre o abuelo que se encuentre con los hijos permitirá y facilitará en todo momento la comunicación con cualquiera de los progenitores, otros abuelos, parientes y allegados de la familia, siempre que ésta no se produzca de forma caprichosa, injustificada o fuera de las horas normales para ello.
h) Cualquiera de los padres o abuelos que traslade a los menores de un lugar conocido a otro desconocido, lo comunicará a los demás, y dará también el nuevo teléfono, si lo hubiere.
i) En caso de enfermedad de los hijos, cualquiera de los progenitores deberá comunicárselo al otro, y en caso de estancia con los abuelos, comunicárselo a los dos padres, permitiendo la visita en el domicilio al padre o abuelo que lo interese y, en todo caso, deberá considerarse la opinión de padres y abuelos en lo relativo a médicos, tratamientos, hospitales, etc.

IV. ATRIBUCIÓN DEL USO DE LA VIVIENDA Y DEL AJUAR FAMILIAR

Se solicita la atribución del uso de la vivienda familiar a D./Dª [NOMBRE Y APELLIDOS] como progenitor que ostenta la guarda y custodia, así como el uso del ajuar familiar en ella existente, estableciéndose una limitación temporal de

Los gastos derivados del uso de la vivienda serán a cargo del/de la usuaria.

V. GASTOS DE ASISTENCIA A LOS HIJOS MENORES.

Se estará a las siguientes reglas según sean gastos ordinarios, extraordinarios necesarios o extraordinarios no necesarios:

V.1. Gastos ordinarios:

D./Dª [NOMBRE Y APELLIDOS] abonará, en concepto de pensión de alimentos, la cantidad de [IMPORTE] euros mensuales para el/cada uno de los hijo/hijos menor/es.

Dicha cantidad deberá ser ingresada en los cinco primeros días de cada mes, en la entidad y en la cuenta bancaria que designe D./Dª [NOMBRE Y APELLIDOS]

La cantidad abonada en concepto de alimentos, será actualizada anualmente a tenor de las variaciones porcentuales experimentadas por el IPC, a nivel nacional, según conste en el certificado que a tal efecto expida el INE o el organismo que pueda sustituirlo en sus funciones.

V.2. Gastos extraordinarios necesarios:

Los gastos extraordinarios de los hijos que sean necesarios, serán sufragados, previo acuerdo de los progenitores, al 50 por ciento. Se consideran expresamente gastos extraordinarios necesarios los siguientes:

V.3. Gastos extraordinarios no necesarios:

Los gastos extraordinarios no necesarios se abonarán en función de los acuerdos a los que lleguen los progenitores en cada caso y, en defecto de acuerdo, los abonará el progenitor que haya decidido la realización del gasto.

VI. ASIGNACIÓN COMPENSATORIA.

Se solicita una asignación compensatoria que deberá abonar D./Dª [NOMBRE Y APELLIDOS] a D./Dª [NOMBRE Y APELLIDOS]

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

Dicha asignación consistirá en un pago único de [IMPORTE] euros.

Dicha asignación consistirá en un pago mensual de [IMPORTE] euros, que tendrá una duración de [Nº] años y no será actualizable/será actualizable anualmente conforma a las variaciones porcentuales experimentadas por el IPC, a nivel nacional, según conste en el certificado que a tal efecto expida el INE o el organismo que pueda sustituirlo en sus funciones.

Dicha cantidad deberá ser ingresada en los cinco primeros días de cada mes, en la entidad y en la cuenta bancaria que designe D./Dª [NOMBRE Y APELLIDOS]
