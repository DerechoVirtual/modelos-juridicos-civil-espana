---
name: demanda-cantidad-venta-acciones-sin-consentimiento-todos-416
description: "Redacta el escrito «Demanda de cantidad por venta de acciones sin el consentimiento de todos los coherederos» (formulario 416 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de cantidad por venta de acciones sin el consentimiento de todos los coherederos

> Formulario 0416 del plugin **Sucesiones** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (12 veces)
- [ ] NÚMERO (2 veces)
- [ ] Nº DE DOCUMENTO (8 veces)
- [ ] LOCALIDAD
- [ ] CALLE (5 veces)
- [ ] Nº (4 veces)
- [ ] FECHA (6 veces)
- [ ] IMPORTE (13 veces)
- [ ] Sentencia del Tribunal Supremo, Sala Primera, de lo Civil, Sentencia de 3 Feb. 1982 y Sentencia del TS de 27 de mayo de 1982, 3 de junio de 1989, 5 de marzo de 1991, etc.
- [ ] LUGAR
- [ ] Otros 24 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…da de juicio ordinario contra la entidad»; «…de»; «… su titularidad en la entidad financiera»; «…de la localidad de»; «… en su domicilio sito en la localidad de»; «…ie de acciones, entre las que destacaban»; «…acciones de la entidad»; «…stamentarias decididas en su momento por»; «…ron, además de otros bienes, un total de»; «…acciones de la entidad»; «…uros. CUARTO.- Mi representada acudió el»; «…os cada una, ascendiendo el total de las»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 85.1 LOPJ
- art. 45 LEC
- art. 51.1 LEC
- art. 7.4 LEC
- art. 253 LEC
- art. 249.2 LEC
- arts. 23 y 31 LEC
- art. 399 LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 397 CCiv
- art. 1.108 CCiv
- art. 394.1 LEC
- art. 231 LEC

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

### Formulario 0416 · Demanda de cantidad por venta de acciones sin el consentimiento de todos los coherederos

- Año del modelo: 2018
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 71 campos de relleno marcados en blanco; 5 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda de juicio ordinario sobre acción de reclamación de cantidad por incumplimiento contractual contra entidad financiera por venta de acciones sin consentimiento de todos los coherederos.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], a cuya justificación aporto escritura de poder inscrito en el Registro Electrónico de Apoderamientos Judiciales con el nº [NÚMERO] y que se puede acreditar mediante consulta automatizada orientada al dato, por parte del órgano judicial al cual tengo el honor de dirigirme, acompañándose certificación electrónica del Registro Electrónico de Apoderamientos Judiciales como Documento nº [Nº DE DOCUMENTO] por si no fuera posible la consulta automatizada; bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], abogada ejerciente, n.º [NÚMERO] del Iltre. Colegio de Madrid, con despacho abierto en [LOCALIDAD], calle [CALLE], ante el Tribunal comparezco y como mejor proceda en Derecho, DIGO:

Que por medio del presente escrito paso a interponer demanda de juicio ordinario contra la entidad [COMPLETAR], con sucursal abierta en la calle [CALLE] de [COMPLETAR], ejercitando acción de reclamación de cantidad por incumplimiento contractual, todo ello de acuerdo con los siguientes hechos y consideraciones de derecho:

HECHOS

PRIMERO.- El padre de mi mandante, mantuvo en depósito diversos paquetes de acciones de su titularidad en la entidad financiera [COMPLETAR], desde 1980, en la modalidad de contrato de depósito y administración de valores. Se aporta copia del contrato en cuestión, como documento nº [Nº], gestionado en la sucursal sita en la calle [CALLE] de la localidad de [COMPLETAR]. Durante la vigencia de dicho relación contractual, han sido innumerables las órdenes de venta emitidas por D./Dña. [NOMBRE Y APELLIDOS], que siempre fueron oportunamente cumplimentadas por la entidad aquí demandada.

SEGUNDO.- El pasado [FECHA] falleció después de una larga enfermedad en su domicilio sito en la localidad de [COMPLETAR]. Se adjunta copia del certificado de defunción como documento nº [Nº DE DOCUMENTO]. En el día de su muerte, el fallecido era titular de una serie de acciones, entre las que destacaban [COMPLETAR] acciones de la entidad [COMPLETAR] que cotiza en el IBEX-35. Así se desprende de la escritura de partición de herencia que se firmó el día [FECHA], en la Notaría de D./Dña. [NOMBRE Y APELLIDOS], cuya copia de acompaña como documento nº [Nº DE DOCUMENTO]. En la misma se puede comprobar la existencia de las citadas acciones, con un valor nominal de [IMPORTE] euros cada una, que asciende a un total de [IMPORTE] euros. Se aporta también el estado de posición a dicha fecha, facilitado por la propia demandada para realizar la partición de la herencia, como documento nº [Nº DE DOCUMENTO].

TERCERO.- A tal partición, y cumpliendo con las disposiciones testamentarias decididas en su momento por [COMPLETAR], mi mandante concurrió con sus dos hermanos, D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS]. De esta forma, siendo heredera en una tercera parte del patrimonio de su padre, se le adjudicaron, además de otros bienes, un total de [COMPLETAR] acciones de la entidad [COMPLETAR], por un valor total de [IMPORTE] euros.

CUARTO.- Mi representada acudió el [COMPLETAR] a la sucursal que gestionaba el contrato de depósito para materializar la adjudicación de las acciones que le correspondían. En dicho momento descubrió que las mismas se habían vendido el pasado [FECHA], tres semanas después del fallecimiento de su padre, sin que tuviera ningún conocimiento de dicha transmisión, ni, desde luego, la hubiera aprobado en modo alguno, expreso o tácito. Tras reclamar insistentemente una copia de la eventual orden de venta, se le entregó la misma, la cual se aporta como documento nº [Nº], pudiendo comprobar como aquella estaba firmada únicamente por su hermano D./Dña. [NOMBRE Y APELLIDOS]. El día de la venta las acciones tenían un valor de [IMPORTE] euros cada una, ascendiendo el total de las [COMPLETAR] acciones que corresponden a mi cliente a la cantidad de [IMPORTE] euros, que, tras deducir los correspondientes impuestos, han sido ingresadas en cuenta corriente de su titularidad en cantidad de [IMPORTE] euros. Se aporta el certificado de venta como documento nº [Nº DE DOCUMENTO].

QUINTO.- Desde la fecha de venta de las acciones, el día [FECHA], hasta el momento en que mi mandante trató de adjudicarse efectivamente las que le correspondían, el valor nominal de cada una ascendió un [COMPLETAR] %. Concretamente, pasaron de un valor de [IMPORTE] euros hasta los [IMPORTE] euros fijados en dicho día, tal y como se desprende del certificado elaborado por la entidad financiera [COMPLETAR] que se acompaña como documento nº [Nº DE DOCUMENTO]. En consecuencia, mi mandante ha recibido [IMPORTE] euros en su cuenta corriente; cuando, si no se hubieran vendido, el valor de las [COMPLETAR] acciones que le correspondían, habría ascendido a un total de [IMPORTE] euros, una diferencia de [IMPORTE] euros que ha perdido. Cantidad que es lo que aquí se reclama mediante el presente escrito expositivo.

SEXTO.- El [COMPLETAR] se envió burofax a la entidad bancaria, cuya copia se adjunta como documento nº [Nº], en solicitud de reclamación de la cantidad dejada de ganar por valor de [IMPORTE] euros. Dicha comunicación, hasta la fecha, no ha sido contestada.

A los anteriores hechos son de aplicación los siguientes:

SÉPTIMO.- La parte actora manifiesta que, previo a la presentación de la presente demanda, se han llevado a cabo posteriores negociaciones con la parte demandada, con el objetivo de cumplir el requisito de procedibilidad, y resolver la controversia de manera amistosa y extrajudicial. Dichas negociaciones se desarrollaron en cumplimiento de los principios de buena fe, con la intención de alcanzar una solución satisfactoria; incluyéndose entre las acciones realizadas el intercambio de comunicaciones formales mediante correspondencia escrita, en fechas [COMPLETAR], en las cuales esta parte expresó su disposición para dialogar y propuso alternativas de solución.

Finalmente, mi representado envió un requerimiento fehaciente al demandado con fecha [FECHA], fijando un plazo de 30 días naturales para llegar a un acuerdo amistoso, a través del abogado que firma este escrito, el cual fue contestado por el demandado por el mismo medio, rechazando el acuerdo/ habiendo sido solo posible un acuerdo parcial, viéndonos en la necesidad de acudir a la presente vía judicial, respecto a los extremos de la controversia en los que se mantiene la discrepancia.

Acompaño como documento nº [Nº DE DOCUMENTO], el requerimiento efectuado y como documento nº [Nº DE DOCUMENTO], la contestación del demandado.

FUNDAMENTOS DE DERECHO

I.- JURISDICCIÓN Y COMPETENCIA.

Radicando la competencia genérica en el orden civil de la jurisdicción, detenta la competencia objetiva y funcional la Sección Civil del Tribunal de Instancia, por aplicación de lo dispuesto en el arts. 85.1 LOPJ y art. 45 LEC. Asimismo, dado que se pretende la condena al abono de los daños causados por el incumplimiento contractual de la demandada, en el marco de un contrato de depósito y administración de acciones, y puesto que aquella tiene sucursal abierta al público en el partido judicial del Tribunal al cual tengo el honor de dirigirme, su situación debe determinar la competencia territorial, conforme al art. 51.1 LEC.

II.- CAPACIDAD Y LEGITIMACIÓN.

Mi mandante es mayor de edad y se encuentra en situación de pleno ejercicio de sus derechos civiles, en virtud de lo dispuesto en los arts. 6.1.1.º y 7.1 LEC. Asimismo, la demandada es persona jurídica, cuya capacidad se reconoce en el art. 6.1.3.º LEC, derivándose su personalidad de su constitución como sociedad anónima en escritura pública inscrita en el Registro Mercantil, con la necesidad de comparecer en juicio por medio de sus representantes legales (art. 7.4 LEC).

Corresponde la legitimación activa directa a mi representada, por cuanto que es heredera de la posición contractual de su padre, quien decidía el cuándo y el cómo vender las acciones de su propiedad; y que reclama por el perjuicio ocasionado al haberse venido acciones sin su consentimiento tras la muerte de aquel. Asimismo, en cuanto a la legitimación pasiva, corresponde a la entidad bancaria [COMPLETAR] como parte contractual que ha incumplido sus deberes de administración, y ha vendido acciones sin consentimiento del nuevo titular, generándole un claro perjuicio patrimonial.

III.- CUANTÍA Y PROCEDIMIENTO.

Conforme al art. 253 LEC cifro la cuantía de la presente demanda en [IMPORTE] euros, correspondiente a la cantidad reclamada y al total de lo debido, conforme a lo dispuesto en los arts. 251.1.ª y 8.ª LEC.

Por todo ello, el procedimiento ajustado a derecho será el del juicio declarativo ordinario regulado en los arts. 399 a 436 del mismo texto legal, atendiendo a la cuantía fijada, en aplicación de lo dispuesto en el art. 249.2 LEC.

IV.- POSTULACIÓN Y DEFENSA.

Conforme a los arts. 23 y 31 LEC se formula esta demanda a través de Procurador/a de los Tribunales con poder notarial para pleitos, y con dirección y firma de Letrado habilitado ante el Tribunal. Asimismo se cumplen los requisitos formales del art. 399 LEC.

V.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VI.- FONDO DE LA CUESTIÓN CONTROVERTIDA.

1) Acción ejercitada

Se plantea una demanda de reclamación de cantidad, al amparo de lo dispuesto en los arts. 1101 y ss. CCiv, por los perjuicios ocasionados tras el incumplimiento contractual de la demandada, consistente en vender las acciones que finalmente correspondían a mi mandante, sin haber recabado su consentimiento. Acciones que, una vez vendidas, experimentaron un considerable aumento, que es el que se reclama como lucro cesante. La entidad financiera no puede excusarse en la ignorancia del fallecimiento del padre de mi cliente, toda vez que tal circunstancia fue comunicada por el hermano D./Dña. [NOMBRE Y APELLIDOS], quien fue el que firmó la orden de venta, y puesto que el propio Banco había colaborado con la familia para facilitar la partición de herencia, habiendo emitido el estado de posición correspondiente al día de la defunción.

2) Del contrato de depósito y administración de acciones, y el incumplimiento contractual sufrido por mi mandante:

Como se ha indicado, se reclama en virtud de un incumplimiento del contrato de depósito y administración de valores, en este caso acciones que cotizan en el IBEX 35, que ligó durante más de treinta años a D./Dña. [NOMBRE Y APELLIDOS] y a la aquí demandada. Se trata, de esta manera, de una actividad muy habitual para las entidades financieras, que, en un clima de confianza, depositan y conservan los títulos valores de sus clientes, y administran los mismos en función de las órdenes que estos últimos les van proporcionando. Actividad que, en nuestro marco legal, sólo puede ser desarrollada por determinadas empresas de servicios de inversión y determinadas entidades de crédito como es la parte demandada, cuando estén autorizadas e inscritas en los registros administrativos correspondientes, según dispone el art. 129 LMV. El art. 126.a) de dicho texto legal tipifica tal contrato como un servicio auxiliar a los de inversión, definiendo su objeto como la custodia y administración por cuenta de clientes de instrumentos financieros diversos.

Es decir, se trata de un contrato habitualmente bancario que tiene como causa la custodia de los valores e instrumentos financieros negociables, sea cual sea su forma de representación. Se denomina administrado, atendiendo al carácter fructífero de los instrumentos financieros custodiados, que exige su gestión conservativa. Por ello, mientras que, en los depósitos bancarios de dinero, la especialidad consiste en su propia irregularidad y en el traspaso de la propiedad del numerario depositado desde el cliente depositante a la entidad de crédito depositaria, al efecto de posibilitar la intermediación en el crédito indirecto; en el caso que nos ocupa, los activos siguen siendo propiedad del depositante y la peculiaridad estriba en la actividad que se confía a la entidad depositaria, en calidad no sólo de custodio de los valores depositados, sino también de administrador de los mismos.

Dicha actividad, proporcionada por una entidad especializada en el sector financiero, a un cliente de su confianza, implica un deber acusado y riguroso de información, que debe presidir toda la vida del contrato. En este sentido, la Sentencia del Pleno de la Sala Primera de lo Civil del Tribunal Supremo 491/2017, de 13 de septiembre (Rec. 242/2015, Ponente: Vela Torres, Pedro José) señala lo siguiente "Según hemos afirmado con reiteración, existe un riguroso deber legal de información al cliente por parte de las entidades de servicios de inversión. Lo que en el caso concreto de la comercialización de participaciones preferentes se ha mantenido en las sentencias de esta sala 244/2013, de 18 de abril; 458/2014, de 8 de septiembre; 489/2015, de 16 de septiembre; 102/2016, de 25 de febrero; 603/2016, de 6 de octubre; 605/2016, de 6 de octubre; 625/2016, de 24 de octubre; 677/2016, de 16 de noviembre; 734/2016, de 20 de diciembre; y 62/2017, de 2 de febrero. No obstante, el incumplimiento de dicha obligación por la entidad financiera podría dar lugar, en su caso, a la anulabilidad del contrato por error vicio en el consentimiento, o a una acción de indemnización por incumplimiento contractual, para solicitar la indemnización de los daños provocados al cliente por la contratación del producto a consecuencia de un incorrecto asesoramiento".

Ese deber de información, resaltado por la doctrina jurisprudencial en una acción de anulabilidad, es aplicable en un caso como el presente; en el que un acto de disposición íntegra de lo administrado, se lleva a cabo sin informar, siquiera a posteriori, al cliente; y sin recabar el consentimiento de todos los titulares de las acciones finalmente vendidas.

3) De la necesidad de concurrencia del consentimiento de todos los herederos, y la ausencia del mismo:

En el presente caso, nos encontramos con una comunidad hereditaria formada por mi cliente y sus dos hermanos varones, que no puede pasar desapercibida a la entidad bancaria, la cual tiene perfecto conocimiento del deceso del anterior depositante. Y en este sentido, el art. 397 CCiv dispone que "Ninguno de los condueños podrá, sin consentimiento de los demás, hacer alteraciones en la cosa común, aunque de ellas pudieran resultar ventajas para todos". Precepto legal completado por el art. 1261 del mismo texto legal, que exige el consentimiento de los contratantes para la existencia del contrato.

En consecuencia, la venta de los bienes hereditarios por uno de los herederos, sin el consentimiento de los demás, como es el caso que nos ocupa, es una venta nula, tal y como aclara la Sentencia del Tribunal Supremo, 92/2012, de 7 de marzo de 2012, rec. 2084/2008. La misma, en aplicación de los dos artículos citados y reconociendo la existencia de dos posiciones jurisprudenciales anteriores; opta por declarar la nulidad de la compraventa por considerar que el vendedor no gozaba de la libre disponibilidad del bien transmitido, sin que se le puedan reconocer efectos obligacionales a lo acordado.

En esta misma línea, la sentencia del Tribunal Supremo, Sala Primera, de lo Civil, 641/2008 de 25 Jun. 2008, Rec. 2013/2001 señala que sólo la partición atribuirá el dominio de bienes concretos pertenecientes a la herencia, siempre que el dominio esté verdaderamente contenido en el caudal relicto [Sentencia del Tribunal Supremo, Sala Primera, de lo Civil, Sentencia de 3 Feb. 1982 y Sentencia del TS de 27 de mayo de 1982, 3 de junio de 1989, 5 de marzo de 1991, etc.]. Aún con mayor énfasis decía la Sentencia del Tribunal Supremo, Sala Primera, de lo Civil, de 29 Dic. 1988, con precedente en la de 16 de febrero de 1987, que la partición hereditaria tiene por objeto la transformación de las participaciones abstractas de los coherederos sobre el patrimonio relicto (derecho hereditario) en titularidades concretas sobre bienes determinados, bien en propiedad exclusiva, bien en proindivisión, ya que, efectivamente, de la comunidad hereditaria puede pasarse, por vía de partición, a un estado de indivisión regido por las normas de la comunidad ordinaria o por cuotas o romana (arts. 392 y ss. CCiv), como han señalado, entre muchas otras, la Sentencia del Tribunal Supremo, Sala Primera, de lo Civil, de 20 Oct. 1992, Rec. 3351/1990, Sentencia del Tribunal Supremo, Sala Primera, de lo Civil, de 25 Abr. 1994, 6 de marzo de 1999, Sentencia del Tribunal Supremo, Sala Primera, de lo Civil, 668/2001 de 28 Jun. 2001, Rec. 1443/1996, etc. La comunidad hereditaria, señala la Sala Primera, de lo Civil, de 24 Jul. 1998, Rec. 1170/1994, en cuanto recayente sobre la totalidad del patrimonio del causante, no en cuanto referida a bienes concretos aisladamente considerados, participa de la naturaleza de la comunidad de tipo romano, por lo que le es aplicable el art. 397 CCiv, con arreglo al cual los actos dispositivos de dichos bienes, integrantes de la referida comunidad hereditaria, requieren el consentimiento unánime de todos los coherederos.

4) De la indemnización de daños y perjuicios reclamada:

Como ya se ha indicado, la venta que se realizó de las acciones de mi mandante fue nula, sin perjuicio de que aquí no se ejercita acción de nulidad del acto de la venta, sino que se reclaman los perjuicios ocasionados por el lucro cesante o ganancia dejada de obtener, como consecuencia del incumplimiento contractual al realizar ese acto de disposición nulo. Por ello, se acude a la diferencia entre el valor de venta de las acciones, ingresado en la cuenta corriente de mi mandante, y lo que hubieran valido el día que se trató de disponer de ellas, si no se hubieran vendido. Todo ello, con base en los arts. 1101 y ss. CCiv.

En este sentido, la mencionada Sentencia del Tribunal Supremo, Sala Primera, 491/2017, de 13 Septiembre 2017, rec.242/2015 aclara que el incumplimiento de la obligación contractual habilita al cliente para reclamar los daños provocados, en este caso, por la disposición y enajenación inconsentida de los activos administrados. En la misma línea la Sentencia del Tribunal Supremo, Sala Primera, de lo Civil, 514/2018 de 20 Sep. 2018, Rec. 3161/2015 (D. Pedro José Vela Torres) que dispone que la determinación del daño resarcible debe hacerse sobre la base del perjuicio realmente experimentado por el acreedor, para lo cual deberán computarse todos aquellos lucros o provechos, dimanantes del incumplimiento, que signifiquen una minoración del quebranto patrimonial sufrido por el acreedor

Por todo ello, se debe condenar a la demandada a pagar la cantidad que se ha dejado de ganar, los 18.750 euros con los intereses legales procedentes desde el momento en que se solicita su pago. El [COMPLETAR], como se comprueba con la copia del burofax enviada y cuya copia se adjunta. Al respecto, declara el art. 1.108 CCiv que "Si la obligación consistiere en el pago de una cantidad de dinero, y el deudor incurriere en mora, la indemnización de daños y perjuicios, no habiendo pacto en contrario, consistirá en el pago de los intereses convenidos, y a falta de convenio, en el interés legal".

VII. COSTAS.

La parte demandada soportará el reintegro de todas las costas del juicio por el principio cuasiobjetivo de vencimiento del art. 394.1 LEC, para declarativos en primera instancia.

SUPLICO AL TRIBUNAL:

Que teniendo por presentado este escrito de demanda junto con los documentos que se acompañan y copias simples de todo ello, se sirva admitirlo a trámite, se me tenga por comparecido y parte demandante en el proceso y en la representación que ostento, entendiéndose conmigo las sucesivas diligencias, por promovido el correspondiente juicio ordinario en ejercicio de reclamación de cantidad frente a la entidad [COMPLETAR]. Asimismo, suplico que se le dé traslado de la demanda y documentos con ella presentados, emplazándosela en legal forma y, previos los trámites oportunos, en su día, se dicte sentencia por la que se condene a la demandada a pagar a mi cliente la cantidad de dieciocho mil setecientos cincuenta euros (euros), más los intereses legales desde reclamación operada el, con expresa condena en costas a la misma.

OTROSÍ PRIMERO DIGO: Interesa al derecho de esta parte utilizar para el juicio que, eventualmente, pudiera señalarse, el siguiente medio de prueba:

INTERROGATORIO DE LA PARTE adversa, en las personas de los representantes con conocimiento directo de los hechos, que serán citados bajo apercibimiento legal de ser tenidos por conformes, en caso de inasistencia, con los hechos en que hubieran intervenido por los que se les interrogue, y que les resulten perjudiciales.

TESTIFICAL de D./Dña. [NOMBRE Y APELLIDOS], subdirector de la Sucursal de [COMPLETAR] en la localidad de [COMPLETAR], calle [CALLE].

TESTIFICAL de D./Dña. [NOMBRE Y APELLIDOS] empleado de la Sucursal de [COMPLETAR] en la localidad de [COMPLETAR], calle [CALLE].

OTROSÍ SEGUNDO DIGO: Que esta parte manifiesta su voluntad expresa de cumplir con todos y cada uno de los requisitos exigidos para la validez de los actos procesales, y si por cualquier circunstancia hubiera incurrido en algún defecto, ofrece desde este momento su subsanación de forma inmediata y a requerimiento de la misma, todo ello a los efectos prevenidos en el art. 231 LEC.

OTROSÍ TERCERO DIGO: Que esta parte asume el compromiso de recibir cualquier comunicación dirigida por la oficina judicial, durante toda la fase declarativa, e, incluso, en una eventual fase de ejecución por medios telemáticos, en términos del art. 399.1 II LEC, consignándose a estos efectos la siguiente dirección de correo electrónico y nº [Nº] de teléfono:

Por lo expuesto,

AL TRIBUNAL NUEVAMENTE SUPLICO que, teniendo por hechas las afirmaciones anteriores, se admitan y provea en consecuencia.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

========================================================================
