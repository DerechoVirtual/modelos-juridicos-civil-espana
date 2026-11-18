---
name: honorarios-abogado-contra-herencia-yacente-reclamacion-462
description: "Redacta el escrito «Honorarios de abogado contra herencia yacente: reclamación» (formulario 462 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Honorarios de abogado contra herencia yacente: reclamación

> Formulario 0462 del plugin **Sucesiones** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Inmuebles** (referencia catastral, superficie, uso) → `consultar_catastro` (y `callejero_catastro` para localizar la dirección).

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
- [ ] NOMBRE Y APELLIDOS (13 veces)
- [ ] COLEGIO
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE
- [ ] NÚMERO (2 veces)
- [ ] Nº DE PROCEDIMIENTO (2 veces)
- [ ] AÑO (2 veces)
- [ ] FECHA (4 veces)
- [ ] SSTS de 21 de mayo de 1991 o 366/1992, de 7 de abril
- [ ] IMPORTE (2 veces)
- [ ] LUGAR
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, acaecido en»; «…ovisional que supone la herencia yacente»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 35 LEC
- art. 1.544 CCiv
- art. 35.1 LEC
- art. 35 LEC
- arts. 155 y 156 LEC
- art. 156.4 LEC
- Real Decreto 135/2021

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

### Formulario 0462 · Honorarios de abogado contra herencia yacente: reclamación

- Año del modelo: 2017
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 28 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito del Abogado por el que reclama a los herederos de su cliente fallecido la minuta de honorarios profesionales devengados en el proceso y que le son debidos y no satisfechos.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Letrado en ejercicio del Iltre. Colegio de Abogados de [COLEGIO], con despacho abierto en [LOCALIDAD], calle [CALLE], n.º [NÚMERO], ante el Tribunal comparezco en autos de Juicio Verbal n.º [Nº DE PROCEDIMIENTO]/[AÑO], y como sea procedente, respetuosamente, DIGO:

Que por medio del presente escrito promuevo reclamación de honorarios, de conformidad con los arts. 35 LEC y 25 del Estatuto General de la Abogacía, contra la HERENCIA YACENTE –o, en su caso, IGNORADOS HEREDEROS- de D./Dña. [NOMBRE Y APELLIDOS], pudiendo ser requerida en el domicilio de la viuda del causante, D./Dña. [NOMBRE Y APELLIDOS], y de sus hijos D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS], sito en [LOCALIDAD], con base en los siguientes:

HECHOS

PRIMERO

D./Dña. [NOMBRE Y APELLIDOS] interesó los servicios profesionales del que suscribe para el estudio y posterior interposición de demanda de Juicio Verbal, en reclamación de desahucio por extinción del plazo del arriendo, lo que determinó el otorgamiento del poder para pleitos "apud acta" a favor de la Procurador/a de los Tribunales D./Dña. [NOMBRE Y APELLIDOS], y la interposición de la misma en fecha [FECHA], redactada y firmada por el que comparece, que dió lugar al Juicio Verbal n.º [Nº DE PROCEDIMIENTO]/[AÑO], en cuya vista fue asistido el demandante, y habiéndose dictado sentencia íntegramente estimatoria por el Tribunal a que me honro en dirigirme, que es firme.

SEGUNDO

Si bien D./Dña. [NOMBRE Y APELLIDOS] entregó una pequeña cifra de dinero a la Procurador/a indicada para los gastos que debiera anticipar, cuando le ha enterado el suscrito que debía satisfacer la minuta de honorarios, en repetidas ocasiones se ha negado, al socaire de que la sentencia condenaba en costas al demandado del juicio, por lo que me veo forzado a manifestar formalmente que los honorarios que se consignan en minuta detallada que acompaño me son debidos y no me han sido abonados, deduciendo la pretensión de cobro en este procedimiento.

TERCERO

Con fecha [FECHA] el que suscribe ha tenido conocimiento del fallecimiento de D./Dña. [NOMBRE Y APELLIDOS], acaecido en [COMPLETAR] el día [FECHA], tal y como se desprende del certificado de defunción que se aporta como documento n.º [NÚMERO].

Por lo tanto, el procedimiento se dirige contra los ignorados herederos o herencia yacente de quien contrató los servicios profesionales del letrado que jura la cuenta, al desconocer el que suscribe la posible identidad o existencia de herederos.

FUNDAMENTOS DE DERECHO

I.- El art. 1.544 CCiv establece que, en el arrendamiento de obras o servicios, cuya calificación es aplicable a los prestados por los Abogados según reiterada jurisprudencia, una de las partes se obliga a ejecutar una obra o a prestar la otra un servicio por precio cierto, y de conformidad con lo previsto en el art. 25 del Estatuto General de la Abogacía aprobado por el Real Decreto 135/2021, de 2 de marzo, el Abogado tiene derecho a una compensación económica adecuada por los servicios prestados, así como al reintegro de los gastos que se le hayan causado. La cuantía de los honorarios será libremente convenida entre el cliente y el abogado, con respeto a las normas deontológicas y sobre competencia desleal. A falta de pacto expreso en contrario, para la fijación de los honorarios se podrán tener en cuenta, como referencia, los baremos orientadores del Colegio en cuyo ámbito actúe, aplicados conforme a las reglas, usos y costumbres del mismo, normas que en todo caso tendrán carácter supletorio de lo convenido y que se aplicarán en los casos de condena en costas a la parte contraria.

II.- Dispone el art. 35.1 LEC que los abogados podrán reclamar frente a la parte a la que defiendan el pago de los honorarios que hubieren devengado en el asunto, presentando minuta detallada y manifestando formalmente que esos honorarios les son debidos y no han sido satisfechos. Igual derecho que los abogados tendrán sus herederos respecto a los créditos de esta naturaleza que aquéllos les dejaren. No será preceptiva la intervención de abogado ni Procurador/a y de conformidad con el art. 35.2 presentada esta reclamación, el Letrado de la Administración de Justicia requerirá al deudor para que pague dicha suma o impugne la cuenta, en el plazo de diez días, bajo apercibimiento de apremio si no pagare ni formulare impugnación. Si, dentro del citado plazo, los honorarios se impugnaren por indebidos, se estará a lo dispuesto en los párrafos segundo y tercero del apartado 2 del artículo anterior. Si se impugnaran los honorarios por excesivos, el Letrado de la Administración de Justicia dará traslado al abogado por tres días para que se pronuncie sobre la impugnación. Si no se aceptara la reducción de honorarios que se le reclama, el Letrado de la Administración de Justicia procederá previamente a su regulación conforme a lo previsto en los arts. 241 y siguientes, salvo que el abogado acredite la existencia de presupuesto previo en escrito aceptado por el impugnante, y dictará decreto fijando la cantidad debida, bajo apercibimiento de apremio si no se pagase dentro de los cinco días siguientes a la notificación. Dicho decreto no será susceptible de recurso, pero no prejuzgará, ni siquiera parcialmente, la sentencia que pudiere recaer en juicio ordinario ulterior.

III.- El presente procedimiento de jura de cuentas se promueve contra la herencia yacente del finado, D./Dña. [NOMBRE Y APELLIDOS], o sus ignorados herederos, al desconocer el que suscribe la posible identidad o existencia de herederos, posibilidad reconocida por la jurisprudencia [SSTS de 21 de mayo de 1991 o 366/1992, de 7 de abril], y recogida legalmente en el art. 6.1.4.º LEC, que incluye dentro de los que pueden ser parte en el procedimiento civil a "las masas patrimoniales o los patrimonios separados que carezcan transitoriamente de titular". Dentro de esta expresión tiene cabida la herencia yacente, que transitoriamente carece de titular definido en tanto no sean llamados a la sucesión y acepten la herencia sus herederos.

Tal herencia yacente es el patrimonio relicto mientras se mantiene interinamente sin titular, por lo que carece de personalidad jurídica, pero para determinados fines, se le otorga transitoriamente una consideración y tratamiento unitarios. Cuando la deuda con el acreedor nace con el causante, fallecido éste, el acreedor no puede saber todos los herederos ni si dicha herencia ha sido aceptada, razón por la que se confiere legitimación pasiva a dicha herencia yacente.

Como se reitera en la interpretación de nuestros tribunales, esta situación interina y provisional que supone la herencia yacente [COMPLETAR], es decir, la existencia de un patrimonio cuyo titular ha fallecido y aún no se han realizado todas las operaciones para adjudicarlo a los herederos, no impide que los procesos que se sigan con el fallecido se paralicen, o no puedan iniciarse, porque se permite dirigir las actuaciones contra la herencia yacente, en la persona de sus herederos, y estos pueden iniciar los procesos necesarios en defensa de la misma.

Por tanto, debe admitirse la posibilidad de que el procedimiento de jura de cuentas (y el requerimiento de pago al deudor que del mismo habrá de derivarse, ex art. 35 LEC) se dirija contra la herencia yacente o ignorados herederos del deudor de cuyo fallecimiento se aporta acreditación documental, y ello sin perjuicio de que a efectos de notificaciones y demás actos de comunicación, si se manifiesta la imposibilidad de designar el domicilio o residencia de los hipotéticos herederos o de la persona designada como administrador, haya de acudirse a los medios de averiguación del domicilio a que se refieren los arts. 155 y 156 LEC y, en último término, de resultar infructuosas tales averiguaciones, las comunicaciones se llevarán a cabo mediante edictos, tal como establece el art. 156.4 LEC (Auto de la Audiencia Provincial de Lleida, Sección 2ª, 36/2004 de 8 Abr. 2004, Rec. 413/2003; Auto de la Audiencia Provincial de A Coruña, Sección 5ª, 59/2006 de 30 May. 2006, Rec. 551/2005).

En definitiva, no cabe desconocer al respecto la doctrina jurisprudencial (Sentencia del Tribunal Supremo, Sala Primera, de lo Civil, 530/2005 de 7 Jul. 2005, Rec. 166/1999 y Sentencia del Tribunal Supremo, Sala Primera, de lo Civil, 540/2008 de 12 Jun. 2008, Rec. 2996/2001), en la que se admite el emplazamiento de la herencia yacente a través de un posible interesado, aunque no se haya acreditado su condición de heredero ni por supuesto su aceptación.

Por tanto, se dirige la acción contra la herencia yacente o ignorados herederos de D./Dña. [NOMBRE Y APELLIDOS], de cuyo fallecimiento se aporta acreditación documental, designándose, a efectos del requerimiento que permita tomar conocimiento de la deuda a la herencia yacente, el domicilio que consta al que suscribe D./Dña. [NOMBRE Y APELLIDOS], donde viven sus familiares más cercanos –cónyuge e hijos-, quienes lógicamente parece que pueden estar llamados a la herencia o más directamente interesados en el asunto.

Por todo lo expuesto.

SUPLICO AL TRIBUNAL:

Que teniendo por presentado este escrito junto con sus documentos y copias de todo ello, se sirva admitirlo y tener por formulada petición de reclamación de la minuta de honorarios profesionales detallada contra HERENCIA YACENTE -O IGNORADOS HEREDEROS- de D./Dña. [NOMBRE Y APELLIDOS] en la cuantía de [IMPORTE] euros de principal y [IMPORTE] euros más para intereses y costas prudencialmente calculados y, previo los trámites legales de rigor, dicte el/la Letrado/a de la Administración de Justicia resolución por la que acuerde requerir al mismo para que en el plazo de diez días pague dicha suma, o impugne la cuenta, bajo apercibimiento de apremio si no pagare ni formulare impugnación.

Es justicia de hacerse en [LUGAR], a [FECHA].

Firma del Abogado

========================================================================
