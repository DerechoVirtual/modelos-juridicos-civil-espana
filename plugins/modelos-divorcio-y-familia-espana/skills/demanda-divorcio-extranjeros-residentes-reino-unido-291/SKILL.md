---
name: demanda-divorcio-extranjeros-residentes-reino-unido-291
description: "Redacta el escrito «Demanda de divorcio de extranjeros residentes en Reino Unido y España, con alimentos y compensatoria» (formulario 291 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de divorcio de extranjeros residentes en Reino Unido y España, con alimentos y compensatoria

> Formulario 0291 del plugin **Familia** · revisado el 17-11-2026.

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

- REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] DNI/NIE
- [ ] Nº DE DOCUMENTO (11 veces)
- [ ] Nº (8 veces)
- [ ] FECHA (2 veces)
- [ ] IMPORTE (11 veces)
- [ ] NÚMERO
- [ ] Otros 41 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…dad, de nacionalidad francesa, vecina de»; «…matrimonio canónico en Lyon (Francia) el»; «…egistro Civil de dicha localidad al Tomo»; «…, página»; «…n nacido y viven dos hijos llamados: 1.-»; «…años de edad, nacido en Lyon, el día de»; «…egistro Civil de dicha localidad al Tomo»; «…, página»; «…s tiene un trabajo estable en la empresa»; «…y vive en la localidad de»; «…a en el Registro Civil de Madrid al Tomo»; «…, página»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 23 y 31 de la LEC
- art. 437.1 LEC
- art. 5 de la Ley Orgánica 1/2025
- artículo 85 del Código Civil
- artículo 97 CC
- artículo 99 CC
- Ley 15/2005
- Ley 8/2021

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

### Formulario 0291 · Demanda de divorcio de extranjeros residentes en Reino Unido y España, con alimentos y compensatoria

- Año del modelo: 2020
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 76 campos de relleno marcados en blanco; 6 huecos del original que se habían perdido sin marca, marcados (IMPORTE, NOMBRE Y APELLIDOS)
- Avisos de la revisión: REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD DEL TRIBUNAL DE INSTANCIA DE [SEDE] QUE POR TURNO CORRESPONDA

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

D.. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de Dª., mayor de edad, de nacionalidad francesa, vecina de [COMPLETAR], con domicilio en [LOCALIDAD], y provista de NIE [DNI/NIE], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], ante el Tribunal con el mayor respeto comparezco bajo la dirección letrada de D. [NOMBRE Y APELLIDOS] y como mejor proceda en Derecho DIGO:

Que a medio del presente escrito, en la representación enunciada y al amparo de lo dispuesto en los arts. 85 y ss. del Código Civil, venimos a interponer DEMANDA DE DIVORCIO CONTENCIOSO contra el esposo de mi mandante D. [NOMBRE Y APELLIDOS], mayor de edad, de nacionalidad británica, con domicilio en [LOCALIDAD] y provisto de N.I.E., demanda que se basa en los siguientes

HECHOS

PRIMERO.- Del matrimonio:

Nuestra mandante contrajo matrimonio canónico en Lyon (Francia) el [COMPLETAR], según consta en el Registro Civil de dicha localidad al Tomo [COMPLETAR], página [COMPLETAR], cuya certificación aportamos como documento nº [Nº DE DOCUMENTO].

SEGUNDO.- De los hijos comunes:

Fruto de ese matrimonio han nacido y viven dos hijos llamados:

1.- [COMPLETAR], actualmente con [Nº] años de edad, nacido en Lyon, el día de [COMPLETAR], tal y como consta en el Registro Civil de dicha localidad al Tomo [COMPLETAR], página [COMPLETAR], cuya certificación aportamos como documento nº [Nº DE DOCUMENTO].

Este hijo común se encuentra totalmente independizado pues tiene un trabajo estable en la empresa [COMPLETAR] y vive en la localidad de [COMPLETAR].

2.- actualmente con [Nº] años de edad, nació en Madrid el día [FECHA], tal y como consta en el Registro Civil de Madrid al Tomo [COMPLETAR], página [COMPLETAR]. Aportamos la certificación de nacimiento como documento número [Nº DE DOCUMENTO].

Esta segunda hija se encuentra escolarizada en el Centro [COMPLETAR] de Madrid y vive actualmente en Madrid con su madre.

TERCERO.- Del domicilio conyugal:

Que el domicilio conyugal hasta hace escasamente dos meses ha sido Madrid, teniendo actualmente ambos cónyuges residencias separadas: mientras que la progenitora permanece en el que ha sido el domicilio familiar, el esposo reside actualmente en la localidad galesa de [COMPLETAR].

CUARTO.- De las circunstancias económicas del esposo

: Que el ahora demandado es de profesión y en la actualidad se encuentra trabajando en la empresa [COMPLETAR] desde hace aproximadamente [Nº] años, desarrollando su puesto de trabajo en la localidad galesa de

Sus ingresos en el ejercicio 2017 han sido de más otros [COMPLETAR] por objetivos, lo que totaliza un total neto anual de [IMPORTE] €; y durante 2018 ha percibido unos ingresos netos de [IMPORTE] €.

Dejamos expresamente designados los archivos de la Agencia Tributaria Española y de la empresa [COMPLETAR] a efectos de prueba

Aportamos las declaraciones del IRPF de 2017 y 2018 como documentos 4 y 5 respectivamente.

QUINTO.- De las circunstancias económicas de la esposa:

Por su parte, nuestra representada, que cuenta con [Nº] años de edad actualmente está desempleada y nunca ha trabajado desde que contrajo matrimonio.

Posee una titulación académica de [COMPLETAR], lo que le permitió desarrollar durante [Nº] años el puesto de [COMPLETAR] en la/s empresa/s [COMPLETAR].

Como consecuencia del nacimiento de su primer hijo, ambos esposos convinieron que se dedicara en exclusiva al cuidado y atención de la familia, habida cuenta de que ambos residían en España, y ningún miembro de sus respectivas familias se encuentra en este país, por lo que carecían de ayuda y apoyo familiar. Por tanto, Dª. ha permanecido desligada del mercado laboral desde el año [COMPLETAR] hasta la actualidad.

Como decíamos, nuestra mandante antes del matrimonio ha trabajado en los siguientes períodos:

De a [COMPLETAR] como [COMPLETAR].

De [COMPLETAR] a [COMPLETAR] como monitora de [COMPLETAR] en el Centro de [COMPLETAR].

La crianza de los hijos, pues, le ha impedido a la esposa trabajar durante unos años, así como obtener sus propios ingresos, sus cotizaciones para futuras pensiones, así como formación académica complementaria.

El currículum de la demandada sí demuestra buenas aptitudes académicas, pero el hecho de haber estado desligada del mercado laboral, su edad, la carga familiar que representa su hija menor, etc, hacen muy difícil que pueda acceder con cierta rapidez al mercado laboral, lo que permite pronosticar que la esposa no va a poder obtener recursos por este cauce como los ha percibido antes del matrimonio.

Aportamos certificado de vida laboral como documento nº [Nº DE DOCUMENTO].

Nos remitimos expresamente a los archivos de la TGSS, Centro y Centro de [COMPLETAR] por si preciso fuere a efectos de prueba y estos hechos fueren negados de adverso.

SEXTO.- De las necesidades de la familia:

La vivienda que constituye el domicilio conyugal se encuentra alquilada, habiendo comunicado los cónyuges la subrogación por parte de la esposa a los arrendadores, tal y como se acredita como documento nº [Nº DE DOCUMENTO].

Actualmente, nuestra mandante está sufragando los gastos del alquiler, más los de los suministros, que totalizan un total mensual de [COMPLETAR] tal y como acreditamos con el contrato de alquiler y las facturas que aportamos como documentos nº [Nº DE DOCUMENTO] a [COMPLETAR].

Por su parte, los gastos extraescolares de la menor son los siguientes, y ascienden a la cantidad que se indica a continuación:

1.- Gastos del colegio al que acude la menor, [IMPORTE] € mensuales

2.- Gastos del club de [IMPORTE], € anuales.

3.- Actividades deportivas [IMPORTE] € mensuales.

4.- Idiomas: clases de apoyo en centro de estudios [IMPORTE], [IMPORTE] € mensuales, más academia € mensuales.

5.- Odontólogo y ortodoncista: [IMPORTE] € mensuales.

Aportamos las facturas de los últimos [Nº] meses de estas partidas como documentos nº [Nº DE DOCUMENTO].

El esposo hasta ahora viene contribuyendo al pago de las necesidades de la familia mediante el ingreso voluntario y unilateralmente decidido de [IMPORTE] € de pensión alimenticia. Aportamos el extracto de los últimos seis meses de la cuenta donde se ingresa la nómina del esposo y se giran los gastos referenciados como documentos nº [Nº DE DOCUMENTO].

SÉPTIMO.- Del régimen económico familiar:

El matrimonio se contrajo bajo el régimen de separación de bienes en virtud de las Capitulaciones Matrimoniales de Separación de Bienes otorgadas en [COMPLETAR] en fecha [FECHA] ante el Notario [COMPLETAR], número de protocolo [COMPLETAR], que aportamos como documento nº [Nº DE DOCUMENTO].

Por lo que no ha de procederse a la disolución y liquidación de la ninguna sociedad de gananciales.

En la escritura de Capitulaciones referida, se contiene expresamente en la cláusula número [NÚMERO] que los futuros cónyuges y los efectos de su matrimonio, se regirán, a falta de ley común por razón de su nacionalidad, por la ley del país del último domicilio común.

OCTAVO Proceso de negociación previo y medios de solución de controversias de manera amistosa y extrajudicial:

Habiendo agotado esta parte todos los intentos de acuerdo extrajudicial, proceso que ha resultado totalmente infructuoso, como se acredita con los documentos acompañados a la presente con los números [COMPLETAR], nos vemos obligados a interponer la presente demanda, que se basa en los siguientes

FUNDAMENTOS DE DERECHO

I.- Competencia: Es competente el Tribunal al que me dirijo por cuanto aunque se trate de un matrimonio con diferente nacionalidad cada uno de los cónyuges, en nuestro caso británica y francesa, se debe aplicar lo dispuesto en el artículo 9.2 de nuestro Código Civil:

.-por la ley personal o de la residencia habitual de cualquiera de ellos, elegida por ambos en documento auténtico otorgado antes de la celebración del matrimonio;

.-a falta de elección, por la ley de la residencia habitual común inmediatamente posterior a la celebración;

.-y a falta de dicha residencia, por la ley del lugar de celebración del matrimonio.

Como hemos acreditado, los cónyuges establecieron en la escritura de Capitulaciones matrimoniales aportada al documento nº [Nº DE DOCUMENTO] de esta demanda, expresamente en la cláusula [COMPLETAR] que “los futuros cónyuges y los efectos de su matrimonio, se regirán, a falta de ley común por razón de su nacionalidad, por la ley del país del último domicilio común”.

Por tanto, es objetiva y territorialmente competente este Tribunal tanto por razón del último domicilio conyugal como por haberlo pactado expresamente ambos cónyuges en documento público.

(Esto enlaza con los artículos 39 y 63 y siguientes, todos ellos de la LEC: el demandado podrá oponerse mediante declinatoria a la competencia internacional).

II.- Legitimación y Postulación: Está legitimada activamente la demandante en tanto ostenta la cualidad de cónyuge, y pasivamente el demandado por ser su esposo.

En virtud de lo dispuesto en los arts. 23 y 31 de la LEC el demandante comparece representado por procurador y asistido de letrado.

Resulta preceptiva la intervención del Ministerio Fiscal al existir una menor de edad.

III.- Cuantía: La cuantía es indeterminada.

IV.- Cumplimiento de los requisitos de procedibilidad: La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC en relación con el art. 437.1 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

V.- A tenor de lo dispuesto en el artículo 85 del Código Civil en su nueva redacción de la Ley 15/2005, la acción que se ejercita es la de DIVORCIO.

Corresponde la misma en tanto los cónyuges llevan más de tres meses casados, dando cumplimiento a lo dispuesto en el artículo 86 por remisión al 81.2º, ambos del Código Civil (el art. 81, en la redacción dada por la Ley 8/2021, de 2 de junio). [NOTA DE REVISIÓN: El art. 86 CC no fue modificado por la Ley 8/2021: su redacción vigente procede de la Ley 15/2005 (BOE-A-2005-11864). Fuente: Código Civil (BOE-A-1889-4763) art. 86 (redacción Ley 15/2005, BOE-A-2005-11864) y art. 81 (redacción Ley 8/2021 (BOE-A-2021-9233)).]

VI.- Procedimiento [COMPLETAR]: El cauce procedimental será el del juicio verbal previsto en el artículo 770 del mismo cuerpo legal.

VII. Medidas solicitadas con relación al matrimonio:

VII.1.- Se atribuye la PATRIA POTESTAD de la hija menor a ambos progenitores.

El traslado de residencia de la menor así como la salida al extranjero requerirá consentimiento de ambos cónyuges.

Conforme disponen los artículos 1.319 y 144 ambos del Código Civil, persistirá la potestad doméstica.

VII.2.- Guarda, custodia y visitas a favor del progenitor no custodio.

VII.2.1.-En primer lugar, la GUARDIA Y CUSTODIA de la menor se atribuirá a su madre, Dª [COMPLETAR].

Habida cuenta de la residencia de los progenitores en distintos estados, no se establece ningún régimen ordinario a favor del progenitor no custodio, quien gozará del siguiente sistema de comunicación y estancia con la menor:

VII.2.2.-Vacaciones de Navidad [COMPLETAR]: se dividirá en dos períodos iguales:

Desde las 20h del último día lectivo hasta el 30 de diciembre a las 20h., acudiendo a recoger a la menor el progenitor entrante.

Y desde las 20h. del 30 de diciembre hasta el último día vacacional a las 20h., acudiendo a recoger a la menor el progenitor entrante.

VII.2.3.-Vacaciones de Semana Santa:

Se otorgará completo al padre, quien acudirá a recoger a su hija el primer día de vacaciones a las 10h en el domicilio familiar y le reintegrará a las 20h del día inmediatamente anterior al comienzo de las clases.

VII.2.4.-Vacaciones de verano [COMPLETAR]: este período abarca solamente los meses de julio y agosto, de manera que se atribuirá un mes completo a cada progenitor. A falta de acuerdo entre los progenitores, la madre elegirá turno en los años pares; y el padre los años impares, y así sucesiva y alternativamente.

Durante los periodos de vacaciones, los progenitores facilitarán la comunicación de su hija con aquél con el que no se encuentre, que por su parte buscará no alterar las rutinas de la menor en el núcleo familiar en que se halle, entendiendo una comunicación prudente y adecuada la de una vez cada cinco días como máximo, y preferiblemente a las 20.30 h.

VII.2.5.-El padre dispondrá a mayores de otra semana completa para estar con su hija, a su elección, siempre que coincida con períodos no lectivos de la menor, y que no impliquen privar a la madre de su turno de verano ni de Navidades. El padre deberá preavisar con un mes de antelación de la semana elegida.

VII.2.6.-Habida cuenta de la edad de la menor, [Nº] años, debe autorizarse que la misma pueda viajar en avión en solitario para que el padre pueda desarrollar el régimen de visitas y estancia en su domicilio de Reino Unido, debiendo éste sufragar los gastos de transporte que precise la menor.

VII.3.- Pensión de alimentos:

Habida cuenta de que sólo el ahora demandado tiene ingresos derivados de su trabajo por cuenta ajena, el padre deberá contribuir en la cuantía de [IMPORTE] EUROS mensuales para su hija, y por doce mensualidades, para su mantenimiento y alimentación. Dicha pensión será anualmente actualizable conforme al sistema que aplique el gobierno para la actualización de pensiones, que podrá coincidir o no con el I.P.C., y deberá ser ingresada antes del día cinco de cada mes, por meses adelantados, en la cuenta bancaria que designe la madre a tal efecto.

Se establece de común acuerdo entre los esposos, que los gastos derivados de servicios médicos privados, odontólogos, farmacológicos, ortopédicos y sanitarios que no estén bonificados o cuya cuantía exceda de la bonificación del sistema público de salud, y las actividades extraescolares y/o extra educativas, así como otros de semejante naturaleza como campamentos, gastos del club [COMPLETAR] al que pertenece, etc., serán abonados por los padres por mitad.

Los padres deberán de notificarse previamente el hecho que los motiva y el importe del mismo para su aprobación.

VII.4.- Pensión compensatoria por desequilibrio:

Tras la reforma del artículo 97 CC por Ley 15/2005, de 8 de julio, las modalidades de pago de dicha compensación no se reducen ya a unas prestaciones periódicas, sustituibles conforme a lo establecido en el artículo 99 CC, o a una prestación única, sino que se establece la posibilidad -ya reconocida por la jurisprudencia- de conceder prestaciones periódicas sometidas a término. Se trata, en todo caso, de compensar el descenso que la nueva situación produce respecto del nivel de vida que se mantenía durante la convivencia; lo que, en consecuencia, se produce con independencia de la situación de necesidad, mayor o menor, del acreedor, no debiendo entenderse como un derecho de nivelación o de indiscriminada igualación.

El artículo 97 exige que el juzgador tenga en cuenta las siguientes: circunstancias:

1º.- Los acuerdos de los cónyuges: en nuestro caso concreto, no existen pues nada se previó en las capitulaciones matrimoniales ni en documento posterior alguno.

2º.- La edad y estado de salud: la esposa cuenta con [Nº] años, tiene como carga familiar la de su hija de 12 años, que le obligará a ajustar su jornada de trabajo por la necesidad de dedicar parte de su tiempo al cuidado de hijos menores. Estas circunstancias redundan en contra de unas posibilidades reales de obtención de un trabajo a corto/medio plazo.

3º.- la cualificación profesional de nuestra representada choca frontalmente con el hecho de haber estado desligada del mercado laboral y de la actualización de conocimientos académicos desde la celebración del matrimonio, restando por tanto posibilidades de acceso a un empleo.

Circunstancias fácticas que conllevan el establecimiento de una pensión compensatoria indefinida a favor de nuestra representada de [IMPORTE] EUROS mensuales.

VII.5.- Uso del domicilio conyugal:

Solicitamos como medida la atribución exclusiva del uso de la vivienda a la esposa, si bien los cónyuges ya han comunicado a los arrendadores la subrogación de la esposa en la posición de arrendataria como consecuencia de la separación de hecho llevada a cabo por ambos.

Por todo lo cual,

AL TRIBUNAL SUPLICO tenga por presentado este escrito, sus documentos y copias. Me sea devuelto el poder por ser general y necesitarlo para otros usos. Lo admita y dé el trámite legal que corresponda. Tenga por interpuesta DEMANDA en juicio de DIVORCIO CONTENCIOSO en nombre de Dª. contra D. [NOMBRE Y APELLIDOS]. Y tras los demás trámites, y previo el recibimiento del juicio a prueba, tenga a bien dictar Sentencia por la que se decrete lo siguiente:

1ª.- La disolución del matrimonio por divorcio.

2º.- La íntegra estimación de las Medidas contenidas en el Fundamento de Derecho VI, que se dan por reproducidas.

Es Justicia que pido en [COMPLETAR]

Fdo. Letrado Fdo. Procurador
