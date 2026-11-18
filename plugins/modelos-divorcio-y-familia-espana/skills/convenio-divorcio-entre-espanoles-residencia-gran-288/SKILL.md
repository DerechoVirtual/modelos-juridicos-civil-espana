---
name: convenio-divorcio-entre-espanoles-residencia-gran-288
description: "Redacta el escrito «Convenio de divorcio entre españoles con residencia en Gran Bretaña tras el traslado de uno a España» (formulario 288 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Convenio de divorcio entre españoles con residencia en Gran Bretaña tras el traslado de uno a España

> Formulario 0288 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] FECHA (3 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NÚMERO
- [ ] LOCALIDAD
- [ ] DESCRIBIR
- [ ] IMPORTE
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…. MANIFESTACIONES I.- Matrimonio: Dª»; «…y D. contrajeron matrimonio canónico en»; «…, el»; «…imonio ha nacido y vive una hija llamada»; «… en el Registro Civil de al Tomo, página»; «…res (Inglaterra, Reino Unido), domicilio»; «…ritura. que se otorgó ante el Notario de»; «…n su hija. 3.2.2.- VACACIONES DE NAVIDAD»; «…pués de leerla cada uno por sí mismo, en»; «…folios de papel timbrado números»; «…a»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 90.2 del Código Civil
- art. 154 del Código Civil
- artículo 156 del Código Civil
- Ley 8/2021
- Ley Orgánica 8/2021

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

### Formulario 0288 · Convenio de divorcio entre españoles con residencia en Gran Bretaña tras el traslado de uno a España

- Año del modelo: 2020
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 17 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (FECHA, NOMBRE Y APELLIDOS)
- Avisos de la revisión: Modelo de convenio regulador sin cláusula sobre animales de compañía: el art. 90.1.b) bis CC (Ley 17/2021, BOE-A-2021-20727) la exige cuando existan.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma de la LO 1/2025.

PROPUESTA DE CONVENIO REGULADOR

DE DIVORCIO

Lugar de firma y fecha [FECHA].

MANIFESTACIONES

I.- Matrimonio: Dª [COMPLETAR] y D. contrajeron matrimonio canónico en [COMPLETAR], el [COMPLETAR] según consta en el Registro Civil de dicha localidad al Tomo, página

II.- Hijos comunes: Fruto de ese matrimonio ha nacido y vive una hija llamada [COMPLETAR], nacida en el día [FECHA], tal y como consta en el Registro Civil de al Tomo, página [COMPLETAR].

III.- Domicilio: Que el domicilio conyugal hasta el momento de la separación de hecho ha estado sito en la localidad de Londres (Inglaterra, Reino Unido), domicilio [COMPLETAR], teniendo actualmente ambos progenitores sus respectivas residencias independientes y separadas entre sí, y ocupando D. la misma en solitario.

IV.- Régimen matrimonial: Que al momento presente el régimen matrimonial es de separación absoluta de bienes, en virtud de la escritura de capitulaciones matrimoniales de fecha [FECHA] de la escritura. que se otorgó ante el Notario de [COMPLETAR], D. [NOMBRE Y APELLIDOS], al número [NÚMERO] de su protocolo.

V.- Que es interés de ambos intervinientes corroborar la solicitud de DIVORCIO para lo cual han procedido a regular sus bases, motivo por el cual con arreglo al art. 90.2 del Código Civil por remisión del artículo 86, y art. 777 de la Ley de Enjuiciamiento Civil en la nueva redacción dada por la Ley 8/2021 de 2 de junio, [NOTA DE REVISIÓN: El art. 90 CC está hoy en la redacción de la Ley 17/2021 (animales de compañía: art. 90.1.b bis y 90.2 párr. 2.º); el art. 777 LEC sí en la de la Ley 8/2021. Añadir al convenio la cláusula sobre animales de compañía si los hay. Fuente: Código Civil (BOE-A-1889-4763) art. 90 (redacción Ley 17/2021 (BOE-A-2021-20727)); LEC 1/2000 (BOE-A-2000-323) art. 777 (redacción Ley 8/2021 (BOE-A-2021-9233)).] aportan el presente CONVENIO REGULADOR, el cual en un futuro regirá sus relaciones personales, comprometiéndose a presentarlo en el Tribunal de [LOCALIDAD] que por turno corresponda para proseguir por los trámites conforme a Derecho, ofreciendo desde ahora la ratificación de su contenido ante la Autoridad Judicial competente y con arreglo a las siguientes.

ESTIPULACIONES

Primera.- Poderes mutuos: Revocación de poderes y consentimientos entre los cónyuges.

Segunda.- PATRIA POTESTAD.

La patria potestad sobre [DESCRIBIR] se ejercerá por ambos progenitores conforme establece el art. 154 del Código Civil en la nueva redacción dada por la Ley Orgánica 8/2021 de 4 de junio.

Este ejercicio conjunto supone que las decisiones importantes relativas a dicha menor serán adoptadas por ambos progenitores de mutuo acuerdo, y en caso de discrepancia resolverá el tribunal conforme al trámite previsto en el artículo 156 del Código Civil. A título indicativo y no excluyente son decisiones incluidas en el ámbito de la patria potestad las relativas a las siguientes cuestiones:

a) Cambio de domicilio de la menor fuera del municipio de residencia habitual y traslado al extranjero, salvo viajes vacacionales.

b) Elección inicial o cambio de centro escolar.

c) Actos médicos no urgentes que supongan intervención quirúrgica o tratamiento médico de larga duración o psicológicos o de carácter no necesario.

d) Celebraciones religiosas o similares.

Ambos intervinientes consienten y consideran beneficioso que su hija traslade su residencia de forma permanente a España, quien residirá allí en compañía de su madre. Por ello, el padre presta su total consentimiento a que la menor traslade su residencia, comprometiéndose a suscribir ante Notario dicho consentimiento por ser una de las facultades inherentes a la patria potestad.

Ambos progenitores tienen derecho a conocer la información sobre la evolución escolar de su hija, así como toda la relacionada con su salud, de manera que ambos podrán acceder a esa información en iguales condiciones o será proporcionada al otro progenitor por quien tiene la custodia.

Las decisiones ordinarias sobre las necesidades de la hija se adoptarán por el progenitor con quien esté la menor en cada momento.

TERCERA.- GUARDA Y CUSTODIA DE LA HIJA MENOR. RÉGIMEN DE VISITAS y COMUNICACIONES:

La guarda y custodia de la menor se atribuye a la madre, Dña. [NOMBRE Y APELLIDOS]

Se establece a favor del padre, D. el régimen de visitas siguiente:

3.1.- VISITAS EN PERÍODO ORDINARIO:

Debido a que el progenitor paterno no traslada su residencia a España, sino que continúa residiendo en Londres, se pacta un régimen de visitas favorable a estancias largas por cuanto se hace necesario el uso de avión.

Los puentes escolares se unirán al fin de semana más próximo, respetando escrupulosamente el régimen anterior.

El período ordinario comprende todo el año a excepción de los períodos extraordinarios, que por razones de distancia geográfica queda en suspenso, sin perjuicio de que el padre pueda visitar en España a su hija las veces que desee, bien en fin de semana o bien en puente escolar, preavisando con antelación mínima de quince días, y corriendo con los gastos de su desplazamiento. Se garantiza a favor del padre un fin de semana al mes como mínimo.

3.2.- PERÍODOS EXTRAORDINARIOS:

3.2.1.- Las VACACIONES DE VERANO comprenden seis subperíodos: período no lectivo de junio, período no lectivo de septiembre, primeras quincenas de los meses de julio y agosto, y segundas quincenas de julio y gasto.

La menor estará en compañía del padre de forma ininterrumpida: el período no lectivo de junio y las dos segundas quincenas de julio y agosto, quedando al mutuo acuerdo de los padres adjudicar las quincenas y la semana; en caso de discrepancia o desacuerdo, se resolverá los años pares eligiendo el padre y los impares la madre.

Todas las quincenas comenzarán los días 1 y 16 de cada mes a las 10 horas y terminarán los días 15 y 31 a las 22horas respectivamente. Durante este período, el progenitor no custodio podrá comunicarse diariamente con su hija.

3.2.2.- VACACIONES DE NAVIDAD [COMPLETAR]: se distribuye por mitad el periodo Navideño, comenzando el primero de ellos el primer día de vacaciones escolares y culminando el 30 del mismo mes y año; el segundo período comenzará el día 30 de diciembre hasta el último día de las vacaciones escolares. Cada período comienza a las 10 horas y terminará a las 21 horas.

La distribución de períodos se hará de mutuo acuerdo y en caso de discrepancia o desacuerdo, se resolverá los años pares eligiendo el padre y los impares la madre.

3.2.3.- SEMANA SANTA o Semana análoga: Se entiende como tal la que se corresponda con vacaciones escolares y durante el mismo se considera conveniente establecer que ambos progenitores se repartan las vacaciones cada año, de manera que corresponderá este período a la madre en años impares, y al padre los pares, y así sucesivamente.

Notas comunes a la custodia y al régimen de visitas:

Tanto las entregas como las recogidas de la menor, tanto en el período ordinario como los extraordinarios, se harán en el domicilio de la madre, y se le reintegrará cenado, habida cuenta de la hora.

Si cualquier fin de semana del período ordinario coincide con los puentes festivos, se ampliará éste a todo el puente.

Todas las referencias al calendario escolar se referirán al que afecte a la menor en cada momento, de manera que la madre hará entrega al padre del calendario definitivo con los períodos vacacionales del año en curso.

La madre custodia avisará al padre con al menos tres días de antelación de cualquier incidente que impida el desarrollo de las visitas, como pueda ser enfermedad de la hija o de la madre, así como del momento elegido para sustituir esa concreta visita que se cancela por causa justificada.

En caso de enfermedad de la menor, deberá ponerse este hecho en conocimiento inmediatamente del otro progenitor.

CUARTA.- PENSIÓN DE ALIMENTOS:

El padre contribuirá a los alimentos de la hija con la cantidad de [IMPORTE] € al mes. Esta cantidad se abonará por anticipado dentro de los cinco primeros días de cada mes en la cuenta que la madre designe al efecto y su importe se actualizará anualmente, sólo si es al alza, aplicando a la cifra que cada año esté en vigor el IPC elaborado por el INE de los doce meses anteriores desde el mes en que se dicte la sentencia aprobando este convenio.

Los gastos extraordinarios, los gastos de logopedia y necesidades educativas especiales que pudiere tener la menor serán por mitad por ambos progenitores. Se entiende por gastos extraordinarios: los de tratamiento médico con prescripción facultativa, ortopédicos, oftalmológicos, odontológicos, farmacológicos, no cubiertos por el sistema público de salud o cuyo importe exceda la bonificación pública, las clases que deban recibir para refuerzo o apoyo escolar recomendadas o prescritas por el centro educativo por problemas de aprendizaje o deficiente rendimiento académico, libros de texto, matrícula de centros educativos etc…

Cuando se plantee la necesidad de estos gastos, deberá comunicarse de forma que deje constancia al otro progenitor la necesidad de realizar el gasto. Se fija como medio de notificación el whatsapp de ambos. En esta comunicación se deberá detallar cuál es el gasto concreto que precise la hija, adjuntando presupuesto o factura/recibo si se ha tenido que abonar por motivos de urgencia, donde figure el nombre del profesional que lo expide.

QUINTA .- USO DE LA VIVIENDA FAMILIAR Y AJUAR: Se atribuirá definitivamente el uso de la vivienda familiar y del ajuar doméstico al padre por ser la persona que permanecerá en Reino Unido, habida cuenta del traslado de madre e hija a España. La madre retirará de la vivienda los enseres y efectos personales, tanto propios como de la menor.

SEXTA .- PENSIÓN COMPENSATORIA: No hay causa legal para el establecimiento de una pensión por el concepto de indemnización por desequilibrio ni pensión compensatoria, al tener cada uno de ellos capacidad económica suficiente y no suponer a ninguno de ellos desequilibrio económico el presente divorcio.

SÉPTIMA .- Régimen económico matrimonial: No procede disolver ni liquidar la sociedad de gananciales por regirse el matrimonio por el régimen de separación absoluta de bienes, manifestando que no existen créditos mutuamente reconocidos.

Y para que así conste, otorgan esta propuesta, firmándola los comparecientes en prueba de conformidad, después de leerla cada uno por sí mismo, en [COMPLETAR] folios de papel timbrado números [COMPLETAR] a [COMPLETAR] en el lugar y fecha de encabezamiento.

Fdo. ( Fdo.
