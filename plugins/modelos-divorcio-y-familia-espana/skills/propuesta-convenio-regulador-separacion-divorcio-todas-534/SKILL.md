---
name: propuesta-convenio-regulador-separacion-divorcio-todas-534
description: "Redacta el escrito «Propuesta de convenio regulador de separación o divorcio con todas las opciones» (formulario 534 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Propuesta de convenio regulador de separación o divorcio con todas las opciones

> Formulario 0534 del plugin **Familia** · revisado el 17-11-2026.

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

- Modelo de convenio regulador sin cláusula sobre animales de compañía: el art. 90.1.b) bis CC (Ley 17/2021, BOE-A-2021-20727) la exige cuando existan.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LUGAR (2 veces)
- [ ] FECHA (5 veces)
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO DE LA CALLE (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] LOCALIDAD (5 veces)
- [ ] IMPORTE
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «…de»; «…, en la ciudad de»; «…, al tomo»; «…, al tomo [COMPLETAR], folio»; «…l régimen económico matrimonial es el de»; «…igo a aquéllos los abuelos paternos, Don»; «…y Doña»; «… hermano menor de la abuela paterna, Don»; «…osa, así como con la abuela materna Doña»

## Elecciones que hay que hacer

- vecino / vecina
- documento nacional de identidad / pasaporte
- civil / canónico
- separación / divorcio

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Con hijos menores de edad / Con hijos mayores de edad / Con hijos mayores y menores de edad / Sin hijos — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de separación / En caso de divorcio — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Hijos menores de edad / Hijos mayores de edad / Hijos mayores de edad convivientes en el hogar familiar / Sin hijos — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Guarda y custodia monoparental / Guarda y custodia compartida — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Con hijos menores de edad / Con hijos mayores de edad — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Guarda y custodia compartida / Guarda y custodia monoparental (o compartida en que así se acuerde — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: No se fija pensión compensatoria / Se fija pensión compensatoria / Se fija pensión compensatoria con carácter temporal — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Separación de bienes / Sociedad de gananciales con liquidación / Sociedad de gananciales sin liquidación / Sociedad de gananciales con liquidación diferida — el texto de cada opción no venía en el formulario original

## Párrafos opcionales (6)

Inclúyelos solo si encajan en los hechos:

- En caso de custodia monoparental…
- III.- RÉGIMEN DE VISITAS…
- IV.- ATRIBUCIÓN DEL USO DE LA VIVIENDA FAMILIAR…
- V.- PENSIÓN ALIMENTICIA Y GASTOS EXTRAORDINARIOS DE LOS HIJOS MENORES…
- VI.- PENSIÓN ALIMENTICIA Y GASTOS EXTRAORDINARIOS DE LOS HIJOS MAYORES…
- El presente convenio plasma el acuerdo de mediación incorporado como ANEXO I y resuelve todas las diferencias …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 90 del Código Civil

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

### Formulario 0534 · Propuesta de convenio regulador de separación o divorcio con todas las opciones

- Año del modelo: 2016
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (3); 7 desplegables convertidos en elección en blanco; 8 bloques de opciones sin texto dejados en blanco con sus rótulos; 6 párrafos opcionales señalados; 30 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NÚMERO DE LA CALLE)
- Avisos de la revisión: Modelo de convenio regulador sin cláusula sobre animales de compañía: el art. 90.1.b) bis CC (Ley 17/2021, BOE-A-2021-20727) la exige cuando existan.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Propuesta de convenio suscrito por los cónyuges para regular las consecuencias de su separación o divorcio, en los términos establecidos en el artículo 90 del Código Civil, adaptable a lo que resulte procedente en cada caso concreto, respecto a la patria potestad, guarda y custodia, régimen de comunicación y estancias, pensión de alimentos, gastos extraordinarios de los hijos menores, uso del domicilio, pensión compensatoria, alimentos de los hijos mayores de edad, liquidación de la sociedad conyugal, etc.

Formulario adaptado a la reforma de la LO 1/2025.

En [LUGAR], a [FECHA].

REUNIDOS

DE UNA PARTE:

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, [ELEGIR: vecino / vecina] de [COMPLETAR], calle [CALLE], núm. [NÚMERO DE LA CALLE] y [ELEGIR: documento nacional de identidad / pasaporte] número [NÚMERO].

Y DE OTRA:

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, [ELEGIR: vecino / vecina] de [COMPLETAR], calle [CALLE], núm. [NÚMERO DE LA CALLE] y [ELEGIR: documento nacional de identidad / pasaporte] número [NÚMERO].

Ambas partes intervienen en su propio nombre y derecho, y se reconocen recíprocamente la suficiente capacidad legal y legitimación para otorgar la presente PROPUESTA DE CONVENIO REGULADOR, de conformidad con lo establecido en el artículo 90 del Código Civil.

EXPONEN

1. Que los comparecientes contrajeron matrimonio [ELEGIR: civil / canónico], en la ciudad de [COMPLETAR], el día [FECHA], figurando dicho matrimonio inscrito en el Registro Civil de [LOCALIDAD], al tomo [COMPLETAR], folio [COMPLETAR].

[ELEGIR UNA OPCIÓN Y REDACTARLA: Con hijos menores de edad / Con hijos mayores de edad / Con hijos mayores y menores de edad / Sin hijos — el texto de cada opción no venía en el formulario original]

3. Debido a la situación de quiebra en la convivencia conyugal, ambos esposos acordaron suspender la misma con fecha [FECHA].

4. El régimen económico matrimonial es el de [COMPLETAR].

[ELEGIR UNA OPCIÓN Y REDACTARLA: En caso de separación / En caso de divorcio — el texto de cada opción no venía en el formulario original]

ACUERDAN

I.- PATRIA POTESTAD Y RELACIONES PATERNO-FILIALES

[ELEGIR UNA OPCIÓN Y REDACTARLA: Hijos menores de edad / Hijos mayores de edad / Hijos mayores de edad convivientes en el hogar familiar / Sin hijos — el texto de cada opción no venía en el formulario original]

En caso de hijos menores de edad

II.- GUARDA Y CUSTODIA DE LOS HIJOS

[ELEGIR UNA OPCIÓN Y REDACTARLA: Guarda y custodia monoparental / Guarda y custodia compartida — el texto de cada opción no venía en el formulario original]

[OPCIONAL — incluir si procede]

En caso de custodia monoparental

[OPCIONAL — incluir si procede]

III.- RÉGIMEN DE VISITAS

III. 1. El padre disfrutará del siguiente régimen de visitas y comunicaciones con sus hijos:

a) Semanal: El padre podrá tener consigo a los hijos un fin de semana de cada dos, de sábado por la mañana a domingo por la tarde, recogiéndolos y devolviéndolos en el domicilio de la madre, en horas que respeten el horario habitual de los niños.

Podrá igualmente tener consigo a los hijos una tarde entre semana, entre martes o jueves, a convenir entre los padres, recogiéndolos en el colegio, y depositándolos en el domicilio de la madre.

b) Periodos de vacaciones: Por Navidad, los hijos pasarán la mitad de sus vacaciones escolares con el padre y la mitad con la madre, rotando éstos anualmente el período que pasarán con cada uno, empezando este año con la primera porción con la madre y la segunda con el padre, sin perjuicio de intercambiarse el turno por acuerdo de los padres.

En Semana Santa, los hijos pasarán un año con el padre y otro con la madre en años alternos.

Durante el período de vacaciones de verano escolares, correspondiente a los meses de julio y agosto, pasarán los hijos un mes con el padre y otro con la madre, a convenir entre éstos con la suficiente antelación, y caso de desacuerdo, la madre elegirá los años pares y el padre los impares.

III. 2. Como régimen de visitas a favor de los abuelos se establece el siguiente:

c) En general: En los fines de semana y periodos vacacionales en que al padre corresponda tener consigo a los hijos, si el mismo estuviera fuera de la localidad, como ocurre por motivos laborales, podrán encargarse de tener consigo a aquéllos los abuelos paternos, Don [COMPLETAR] y Doña [COMPLETAR], quienes les recogerán y devolverán en el domicilio de la madre, como sea de costumbre, pudiendo pasar estos periodos los menores en el domicilio, bien del padre, bien en el de los abuelos.
d) Semanal: Una tarde de la semana, de martes a jueves, aparte de la que haya elegido el padre por corresponderle, los abuelos paternos podrán tener en su compañía a los hijos, tomándolos a la salida del colegio y devolviéndolos antes de las 22.00 horas al domicilio de la madre.

III. 3. Normas generales.

e) Se favorecerán las relaciones de los hijos, no sólo con los abuelos paternos, como se regula, sino con los parientes del padre, en especial, el hermano menor de la abuela paterna, Don [COMPLETAR] y su esposa, así como con la abuela materna Doña [COMPLETAR].

f) Las visitas pactadas como semanales ordinarias se suspenderán durante los periodos de vacaciones.

g) El padre o abuelo que se encuentre con los hijos permitirá y facilitará en todo momento la comunicación con cualquiera de los progenitores, otros abuelos, parientes y allegados de la familia, siempre que ésta no se produzca de forma caprichosa, injustificada o fuera de las horas normales para ello.

h) Cualquiera de los padres o abuelos que traslade a los menores de un lugar conocido a otro desconocido, lo comunicará a los demás, y dará también el nuevo teléfono, si lo hubiere.

i) En caso de enfermedad de los hijos, cualquiera de los progenitores deberá comunicárselo al otro, y en caso de estancia con los abuelos, comunicárselo a los dos padres, permitiendo la visita en el domicilio al padre o abuelo que lo interese y, en todo caso, deberá considerarse la opinión de padres y abuelos en lo relativo a médicos, tratamientos, hospitales, etc.

j) Los progenitores se comprometen a interpretar este convenio tomando siempre en consideración el interés y protección de los menores, y a evitar cualquier actitud que afecte el cariño y respeto de los hijos hacia ambos padres, y hacia cualquiera de sus abuelos.

[OPCIONAL — incluir si procede]

IV.- ATRIBUCIÓN DEL USO DE LA VIVIENDA FAMILIAR

[ELEGIR UNA OPCIÓN Y REDACTARLA: Con hijos menores de edad / Con hijos mayores de edad — el texto de cada opción no venía en el formulario original]

En caso de hijos menores

[OPCIONAL — incluir si procede]

V.- PENSIÓN ALIMENTICIA Y GASTOS EXTRAORDINARIOS DE LOS HIJOS MENORES

[ELEGIR UNA OPCIÓN Y REDACTARLA: Guarda y custodia compartida / Guarda y custodia monoparental (o compartida en que así se acuerde — el texto de cada opción no venía en el formulario original]

En caso de hijos mayores

[OPCIONAL — incluir si procede]

VI.- PENSIÓN ALIMENTICIA Y GASTOS EXTRAORDINARIOS DE LOS HIJOS MAYORES

Dado que los hijos mayores de edad no tienen independencia económica, se acuerda que D./Dña. [NOMBRE Y APELLIDOS] abone a cada uno de sus hijos mayores la cantidad de [IMPORTE] euros mensuales, en concepto de pensión alimenticia, en la entidad y cuenta bancaria de la que los hijos sean titulares y que designen al efecto, mientras los mismos continúen realizando sus estudios o no tengan recursos económicos propios que les permitan emanciparse.

La cantidad abonada en concepto de alimentos será actualizada anualmente a tenor de las variaciones porcentuales experimentadas por el IPC, a nivel nacional, según conste en el certificado que a tal efecto expida el INE o el organismo que pueda sustituirlo en sus funciones. La primera actualización se realizará el día [FECHA].

Los gastos extraordinarios de los hijos que sean necesarios, serán sufragados por los progenitores por mitad, decidiendo la autoridad judicial en caso de desacuerdo. En concreto, se fijan como gastos extraordinarios los siguientes:

VII.- COMPENSACIÓN POR DESEQUILIBRIO

[ELEGIR UNA OPCIÓN Y REDACTARLA: No se fija pensión compensatoria / Se fija pensión compensatoria / Se fija pensión compensatoria con carácter temporal — el texto de cada opción no venía en el formulario original]

VIII.- RÉGIMEN ECONÓMICO MATRIMONIAL

[ELEGIR UNA OPCIÓN Y REDACTARLA: Separación de bienes / Sociedad de gananciales con liquidación / Sociedad de gananciales sin liquidación / Sociedad de gananciales con liquidación diferida — el texto de cada opción no venía en el formulario original]

IX.- DIVISIÓN DE BIENES EN COMUNIDAD ORDINARIA INDIVISA

Los cónyuges reconocen que se casaron bajo el régimen de separación de bienes, sin haber otorgado capitulaciones matrimoniales.

No obstante, ambos cónyuges son cotitulares en mitades y proindiviso de los inmuebles que se especificarán a continuación, y acuerdan extinguir, en la forma que se dirá, la comunidad indivisa existente hasta ahora:

1) Piso sito en [LOCALIDAD]
2) Piso sito en [LOCALIDAD]

A) D./Dña. [NOMBRE Y APELLIDOS], recibe la mitad indivisa, propiedad de su consorte, del piso sito en [LOCALIDAD], con la siguiente descripción registral:

B) D./Dña. [NOMBRE Y APELLIDOS], recibe la mitad indivisa, propiedad de su consorte, del piso sito en [LOCALIDAD], con la siguiente descripción registral:

El presente convenio implica tradición de los mencionados condominios, sin que sea necesario proceder a posterior transferencia física a favor de los respectivos adquirentes en cuanto a la mitad indivisa propiedad del cedente en concepto de condueño, por cuanto aquéllos ya se hallaban en posesión y disfrute del bien, y a partir de este momento y conforme a lo aquí convenido, consolidan el pleno dominio de dichos bienes, por lo que ambas partes solicitan al Registrador de la Propiedad que en cada caso corresponda la inscripción de los presentes títulos, en cuanto implica la transmisión de la mitad indivisa de los bienes pertinentes al otro cónyuge.

X.- DISPOSICIÓN FINAL

[OPCIONAL — incluir si procede]

El presente convenio plasma el acuerdo de mediación incorporado como ANEXO I y resuelve todas las diferencias existentes entre los cónyuges e implica transacción de todas las cuestiones planteadas entre los mismos, por lo que ambos se comprometen a solicitar su [ELEGIR: separación / divorcio] de mutuo acuerdo, constituyendo el presente documento como PROPUESTA DEL CONVENIO REGULADOR de todos sus efectos, conforme a lo previsto en el artículo 90 del Código Civil.

En prueba de conformidad con todo lo acordado, firman los comparecientes el presente documento por triplicado y en todas sus hojas, en el lugar y fecha al principio indicados, quedando un ejemplar para cada cónyuge, y otro a los efectos de su aportación al Tribunal, junto con la demanda de [ELEGIR: separación / divorcio].

Es justicia que pido en [LUGAR], a [FECHA].

Firma	Firma

NOTAS DEL FORMULARIO

(1) Los períodos podrán variar sin que necesariamente tengan que suponer un reparto del año al 50%, si bien, resulta conveniente, a fin de evitar perjuicios de estabilidad a los menores, que los períodos no sean restringidos sino amplios en el tiempo y, en cualquier caso, que se excluyan las periodificaciones por días.

(2) Éstos no deben ser demasiado pequeños porque en tal caso no suele resultar beneficiosa tal medida.

(3) Sin perjuicio de regular el régimen de estancias con uno y otro progenitor resulta muy conveniente describir la intervención diaria de cada uno de los mismos con los hijos no obstante permanecer y pernoctar en el domicilio de uno de ellos. Así, se distribuirá el día de un modo que puede ser el que aquí se señala como ejemplo.

========================================================================
