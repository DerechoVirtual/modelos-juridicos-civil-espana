---
name: medidas-provisionales-previas-demanda-procurador-abogado-881
description: "Redacta el escrito «Medidas provisionales previas a la demanda con procurador y abogado» (formulario 881 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Medidas provisionales previas a la demanda con procurador y abogado

> Formulario 0881 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (34 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] PROFESIÓN
- [ ] LOCALIDAD
- [ ] DNI/NIE
- [ ] FECHA (4 veces)
- [ ] NÚMERO (8 veces)
- [ ] IMPORTE (13 veces)
- [ ] DESCRIBIR
- [ ] Nº (7 veces)
- [ ] MARCA/MODELO (4 veces)
- [ ] MATRÍCULA (4 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 63 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…previas a la interposición de demanda de»; «…y DNI n.º [DNI/NIE]. En este proceso»; «…berá intervenir el MINISTERIO FISCAL por»; «…contrajeron matrimonio»; «…(canónico,civil) en»; «…. De esa unión existen»; «…. De esa unión existen [COMPLETAR] hijos»; «…(nacidos del matrimonio o adoptados):»; «…, nacido el día [FECHA] y»; «…, cuentan por tanto en este momento»; «…,»; «… Civil que acompaño como documentos n.os»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 771 de la LEC
- arts. 36, 46 y 769 de la LEC
- art. 10 de la LEC
- art. 44 y 103 del CC
- art. 749.2 de la LEC
- art. 437.1 LEC
- art. 5 de la Ley Orgánica 1/2025
- arts. 102 y 103 del Código Civil
- arts. 92, 93, 94, 96 y 97 del CC
- art. 104 del CC
- art. 394 de la LEC
- art. 771.2 de la LEC

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

### Formulario 0881 · Medidas provisionales previas a la demanda con procurador y abogado

- Año del modelo: 2013
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 137 campos de relleno marcados en blanco; 8 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma orgánica y procesal de la LO 1/2025.

Medidas provisionales previas

A LA SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS] según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO] y en el que constan los datos personales de mi representado, ante el Tribunal comparezco bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO:

Que mediante el presente escrito y según permite el art. 771 de la LEC intereso la adopción de las medidas que se indicarán en el suplico de esta demanda previas a la interposición de demanda de [COMPLETAR] (nulidad, separación o divorcio) frente a D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, casado, de profesión [PROFESIÓN], con domicilio en [LOCALIDAD] y DNI n.º [DNI/NIE]. En este proceso [COMPLETAR] (si/no) deberá intervenir el MINISTERIO FISCAL por [COMPLETAR] (existir o no existir) hijos menores en el matrimonio. Basamos esta pretensión en los siguientes

HECHOS

Se presenta listado de documentos que acompañan a la demanda.

D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] contrajeron matrimonio [COMPLETAR] (canónico,civil) en [COMPLETAR] el día [FECHA], según acredito con certificación del Registro Civil que acompaño como documento n.º [NÚMERO].

De esa unión existen [COMPLETAR] hijos [COMPLETAR] (nacidos del matrimonio o adoptados): [COMPLETAR], nacido el día [FECHA], nacido el día [FECHA] y [COMPLETAR] nacido el día [FECHA], cuentan por tanto en este momento [COMPLETAR], [COMPLETAR] y 5 años de edad, según acredito con certificaciones del Registro Civil que acompaño como documentos n.os [COMPLETAR].

El domicilio familiar se encuentra en [COMPLETAR] y consiste en una vivienda (alquilada, en propiedad, cedida por [COMPLETAR], [COMPLETAR]), según acredito mediante certificado de empadronamiento que adjunto como documento n.º [NÚMERO].

Se presenta como documento n.º [NÚMERO], [COMPLETAR] (escritura de compraventa, contrato de arrendamiento [COMPLETAR])

Los ingresos familiares provienen de [COMPLETAR] (el trabajo de ambos cónyuges, el trabajo por cuenta ajena de D./Dña. [NOMBRE Y APELLIDOS], las rentas que produce [COMPLETAR], el negocio familiar de [COMPLETAR], el trabajo por cuenta ajena de D./Dña. [NOMBRE Y APELLIDOS] que se dedica a [COMPLETAR]).

En cómputo anual tales ingresos ascienden a [IMPORTE] euros ( euros mensuales). Acompaño a la demanda los documentos n.º [NÚMERO] consistentes en [DESCRIBIR] (declaración de IRPF, certificado anual de ingresos emitido por la empresa [COMPLETAR], nóminas, copia de libros de ingresos y gastos [COMPLETAR]), interesando desde este momento que se requiera a la otra parte para que aporte los originales.

El hijo [COMPLETAR] es mayor de edad, pero se encuentra cursando estudios universitarios de [COMPLETAR] (acompaño copia de matriculación como documento n.º [NÚMERO]), los hijos menores [COMPLETAR] se encuentran también en período de formación según se acredita con copias de sus respectivas matrículas en el centro [COMPLETAR].

Los gastos ordinarios para formación de los hijos se elevan a unos [IMPORTE] euros mensuales. A efectos acreditativos se acompaña facturas y tikets de adquisición de libros y material escolar y deportivo por importe de [IMPORTE] (documentos n.os [COMPLETAR])

A esto hay que añadir otros gastos de formación y sanitarios que surgen de manera periódica como son [COMPLETAR] y que importan [IMPORTE] euros (documentos n.os [COMPLETAR])

Los gastos ordinarios de mantenimiento de la vivienda y sus servicios y suministros suman un importe aproximado de [IMPORTE] euros, según se deduce de las facturas de [COMPLETAR] que aportamos como documentos n.os [COMPLETAR].

Y como cargas periódicas también hay que hacer constar la existencia de un crédito hipotecario para la adquisición de vivienda suscrito con la entidad [COMPLETAR] por un importe total de [IMPORTE] euros, con una cantidad pendiente de amortizar de [IMPORTE] euros y una cuota mensual de [IMPORTE] euros (documento n.º [NÚMERO]), y de un crédito personal suscrito con la entidad bancaria [COMPLETAR] por importe total de [IMPORTE]. euros, con una cantidad pendiente de amortizar de [IMPORTE] euros y una cuota mensual de [IMPORTE] euros.

Así las cosas esta parte interesa que se adopten las siguientes medidas:

1.º DERECHO A VIVIR SEPARADOS: Los cónyuges podrán vivir separados y fijar libremente su domicilio. Cesarán la presunción de convivencia y la posibilidad de vincular los bienes del otro cónyuge en el ejercicio de su actividad económica, quedando igualmente revocados todos los consentimiento y poderes mutuos.

2.º PATRIA POTESTAD, GUARDA Y CUSTODIA: La patria potestad se ejercerá por ambos cónyuges de manera conjunta y en cuanto a la guarda y custodia de los hijos menores:

(Opciones):

– Deberá atribuirse a D./Dña. [NOMBRE Y APELLIDOS], sin perjuicio del derecho del otro progenitor a relacionarse con sus hijos mediante el régimen de visitas que se propondrá y del derecho-deber de intervenir en su educación y formación. Entendemos que ésta es la pretensión más adecuada a la situación real y los intereses de los menores porque [COMPLETAR] (referencia a las relaciones paternofiliales [COMPLETAR], a los ingresos de cada uno, tiempo disponible para atención y cuidado de los hijos, adecuación de las respectivas viviendas [COMPLETAR])

– Interesamos que se acuerde el ejercicio compartido en atención a la estrecha relación que los hijos mantienen con ambos progenitores que no debe ser alterada por la ruptura matrimonial de éstos, porque el ejercicio responsable de la paternidad aconseja esta medida y porque la situación laboral de ambos permite esta solución. Se dan además las condiciones económicas idóneas para que se pueda llevar a efecto, puesto que los cónyuges cuentan con ingresos suficientes para tener y mantener una vivienda con las condiciones adecuadas para la estancia habitual de la prole.

En la práctica este ejercicio se llevaría a cabo de la siguiente manera: (Opciones):

a) semanas alternas con cada uno de los progenitores y mitad de vacaciones con cada uno de ellos

b) entre semanas: tres días con D./Dña. [NOMBRE Y APELLIDOS] y cuatro con D./Dña. [NOMBRE Y APELLIDOS] y primera mitad de vacaciones de verano, semana santa y navidad con D./Dña. [NOMBRE Y APELLIDOS] y segunda mitad con D./Dña. [NOMBRE Y APELLIDOS]

c) pernocta entre semana en el que fue domicilio familiar y estancia a la hora de las comidas con D./ Dña. [NOMBRE Y APELLIDOS], fines de semana alternos con cada uno de los progenitores así como mitad de vacaciones con cada uno de ellos.

d) [COMPLETAR].

Presentamos como informe pericial el dictamen del Psicólogo [COMPLETAR] como n.º [NÚMERO] en el que se afirma que mediante la custodia compartida es como mejor se preserva el equilibrio de los hijos menores.

3.º (Para el caso de no se solicite o acuerde custodia no compartida) RÉGIMEN DE VISITAS: El progenitor que no ostente la guarda y custodia de los hijos menores podrá estar con ellos y tenerlos en su compañía:

Fines de semana alternos desde las [Nº] horas de [COMPLETAR] (la tarde del viernes o la mañana del sábado hasta las [Nº] horas del domingo)

La tarde de los [COMPLETAR] desde [COMPLETAR] hasta las [Nº] horas, siempre que no interfiera en sus actividades educativas, deportivas o de formación.

Vacaciones: mitad de las vacaciones escolares. En caso de que no existiera acuerdo entre los progenitores D./Dña. [NOMBRE Y APELLIDOS] elegirá los períodos de vacaciones que estará con sus hijos los años pares y

D./Dña. [NOMBRE Y APELLIDOS] los años impares.

Las vacaciones de verano comprenden [COMPLETAR] (los meses de julio y agosto, o los diez últimos días de junio y julio un período y agosto y los diez primeros días de septiembre el otro).

Las vacaciones de semana santa se reparten en dos períodos que comprenden uno de ellos los cuatro días de fiesta y el otro el resto de las vacaciones escolares.

Las vacaciones de navidad se repartirán en dos períodos que van el primero del primer día de vacaciones escolares hasta el día 30 de diciembre y el otro del día 31 de ese mes hasta el 7 de enero.

4.º USO DEL DOMICILIO Y AJUAR CONYUGAL: Deberá atribuirse a D./Dña. [NOMBRE Y APELLIDOS] por presentar el interés más necesitado de protección, ya que [COMPLETAR] ( tendrá atribuida la custodia de los hijos, carece de ingresos propios, la carga de cuidado de los hijos seguirá recayendo de manera principal sobre esa persona) El otro cónyuge podrá retirar, previo inventario, sus bienes y enseres de uso personal.

5.º CONTRIBUCIÓN AL LEVANTAMIENTO DE LAS CARGAS FAMILIARES: D./Dña. [NOMBRE Y APELLIDOS] deberá contribuir al levantamiento de las cargas familiares con la cantidad de [IMPORTE] euros mensuales que se entregarán a D./Dña. [NOMBRE Y APELLIDOS] por anticipado dentro de los cinco primeros días de cada mes y que se actualizará anualmente aplicando a la anualidad en cada momento en vigor el IPC de ese año o índice que lo sustituya.

Además cada cónyuge contribuirá al pago de las deudas comunes, la liquidación de los préstamos n.º [NÚMERO], aportando cada uno el cincuenta por ciento de la cuota mensual de cada uno de ellos. A este efecto ambos deberán ingresar antes del giro del recibo mensual dicha cifra.

Esta pretensión se justifica teniendo en cuenta los ingresos de cada cónyuge y los gastos familiares y cargas comunes. En concreto [COMPLETAR].

6.º OTRAS ATRIBUCIONES: El uso del vehículo modelo [MARCA/MODELO], matrícula [MATRÍCULA] se atribuirá a D./ Dña. [NOMBRE Y APELLIDOS] y el del vehículo modelo [MARCA/MODELO], matrícula [MATRÍCULA] se atribuirá a D./Dña. [NOMBRE Y APELLIDOS]

7.º MEDIDAS SOBRE EL PATRIMONIO COMÚN:

(Opciones):

a) La rentas derivadas de [COMPLETAR] que se gestionarán por D./Dña. [NOMBRE Y APELLIDOS] deberán repartirse mensualmente al cincuenta por ciento, así como los gastos, entre ambos.

b) La gestión ordinaria del negocio familiar de [COMPLETAR] se concederá hasta la liquidación del régimen económico a D./Dña. De dicha actuación deberá darse cuenta con una periodicidad de [COMPLETAR], presentando las mismas ante el Tribunal.

c) [COMPLETAR].

8.º MEDIDAS DE GARANTÍA: Para asegurar el cumplimiento de las obligaciones anteriores se adoptarán las siguientes medidas: [COMPLETAR].

Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

Jurisdicción y competencia

Los arts. 21, 22 y 86.5 a) de la LOPJ y arts. 36, 46 y 769 de la LEC atribuyen a la jurisdicción española y a las Secciones de Familia, Infancia y Capacidad de los Tribunales de Instancia el conocimiento de esta materia. En concreto será competente, a elección del demandante, el Tribunal del último domicilio del matrimonio o de residencia del otro demandado.

En los partidos con secciones especializadas de familia será ésta la que conozca del asunto.

Tramitación

Se seguirá el cauce establecido en el art. 771 de la LEC, citando el Letrado de la Administración de Justicia a las partes y al Ministerio Fiscal a una comparecencia para llegar a un acuerdo o resolver sobre las medidas tras oír a las partes.

Postulación

Aunque no es preceptivo que este escrito se suscriba por procurador y letrado, si lo es para todo escrito e intervención posterior de las partes, art. 771.1 párr. segundo de la LEC.

Legitimación

Según el art. 10 de la LEC, en relación con los art. 44 y 103 del CC, están legitimados de forma activa y pasiva para solicitar estas medidas los cónyuges.

El art. 749.2 de la LEC exige la intervención del Ministerio Fiscal en estos pleitos cuando existan menores o personas con discapacidad. [NOTA DE REVISIÓN: El art. 749.2 LEC ya no habla de «incapacitados». Fuente: LEC 1/2000 (BOE-A-2000-323) art. 749.2, redacción Ley 8/2021 (BOE-A-2021-9233): «sea menor, persona con discapacidad o esté en situación de ausencia legal».]

Cumplimiento de los requisitos de procedibilidad

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC en relación con el art. 437.1 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Fondo del asunto

1.º La LEC en su art. 771 remite a los arts. 102 y 103 del Código Civil que regulan las medidas que se adoptarán en caso de crisis conyugal con relación a los hijos, bienes y cargas comunes.

2.º Para determinar estas medidas deberá acudirse a la regulación de los arts. 92, 93, 94, 96 y 97 del CC.

3.º El art. 104 del CC dice que el cónyuge que se proponga demandar la nulidad, separación o divorcio de su matrimonio puede solicitar los efectos y medidas recogidas en los arts. 102 y 103 de este mismo texto. Y que las medidas acordadas sólo subsistirán si dentro de los treinta días siguientes a contar desde que fueron adoptadas, se presenta la demanda de nulidad, separación o divorcio.

Costas

En aplicación del art. 394 de la LEC deberán imponerse al que se opusiera temerariamente a este pretensión.

Por lo expuesto,

SUPLICO AL TRIBUNAL: que tenga por presentado este escrito con los documentos que acompaño, lo admita a trámite y acuerde el Letrado de la Administración de Justicia citar a las partes a la comparecencia prevista en el art. 771 de la LEC y, tras los trámites oportunos, dicte auto por el que se adopten las siguientes medidas:

1.º Que se reconozca a los cónyuges el DERECHO A VIVIR SEPARADOS y fijar libremente su domicilio, cesando la presunción de convivencia y la posibilidad de vincular los bienes del otro cónyuge en el ejercicio de su actividad económica y quedando revocados todos los consentimiento y poderes mutuos.

2.º PATRIA POTESTAD, GUARDA Y CUSTODIA: La patria potestad se ejercerá por ambos cónyuges de manera conjunta y en cuanto a la guarda y custodia de los hijos menores:

(Opciones):

– Deberá atribuirse a D./Dña. [NOMBRE Y APELLIDOS]

– Interesamos que se acuerde el ejercicio compartido por ambos progenitores, que se llevaría a cabo de la siguiente manera: [COMPLETAR].

(Opciones):

a) semanas alternas con cada uno de los progenitores y mitad de vacaciones con cada uno de ellos

b) entre semanas: tres días con D./Dña. [NOMBRE Y APELLIDOS] y cuatro con D./Dña. [NOMBRE Y APELLIDOS] y primera mitad de vacaciones de verano, semana santa y navidad con D./Dña. [NOMBRE Y APELLIDOS] y segunda mitad con D./Dña. [NOMBRE Y APELLIDOS]

c) pernocta entre semana en el que fue domicilio familiar y estancia a la hora de las comidas con D./ Dña. [NOMBRE Y APELLIDOS], fines de semana alternos con cada uno de los progenitores así como mitad de vacaciones con cada uno de ellos.

d) [COMPLETAR].

3.º (Para el caso de custodia no compartida) RÉGIMEN DE VISITAS: El progenitor que no ostente la guarda y custodia de los hijos menores podrá estar con ellos y tenerlos en su compañía:

Fines de semana alternos desde las [Nº] horas de [COMPLETAR] (la tarde del viernes o la mañana del sábado hasta las [Nº] horas del domingo)

La tarde de los [COMPLETAR] desde [COMPLETAR] hasta las [Nº] horas, siempre que no interfiera en sus actividades educativas, deportivas o de formación.

Vacaciones: mitad de las vacaciones escolares. En caso de que no existiera acuerdo entre los progenitores D./Dña. [NOMBRE Y APELLIDOS] elegirá los períodos de vacaciones que estará con sus hijos los años pares y D./ Dña. los años impares.

Las vacaciones de verano: se dividirán entre [COMPLETAR] (los meses de julio y agosto, o los diez últimos días de junio, julio y agosto y los diez primeros días de septiembre).

Las vacaciones de Semana Santa se reparten en dos períodos que comprenden uno de ellos los cuatro días de fiesta y el otro el resto de las vacaciones escolares.

Las vacaciones de Navidad se repartirán en dos períodos que van el primero del primer día de vacaciones escolares hasta el día 30 de diciembre y el otro del día 31 de diciembre hasta el 7 de enero.

4.º USO DEL DOMICILIO Y AJUAR CONYUGAL: Deberá atribuirse a D./Dña. El otro cónyuge podrá retirar, previo inventario, sus bienes y enseres de uso personal.

5.º CONTRIBUCIÓN AL LEVANTAMIENTO DE LAS CARGAS FAMILIARES: D./Dña. [NOMBRE Y APELLIDOS] deberá contribuir al levantamiento de las cargas familiares con la cantidad de [IMPORTE] euros mensuales que se entregarán a D./Dña. [NOMBRE Y APELLIDOS] por anticipado dentro de los cinco primeros días de cada mes y que se actualizará anualmente aplicando a la anualidad en cada momento en vigor el IPC de ese año o índice que lo sustituya.

Además cada cónyuge contribuirá al pago de las deudas comunes, la liquidación de los préstamos n.º [Nº], aportando cada uno el cincuenta por ciento de la cuota mensual de cada uno de ellos. A este efecto ambos deberán ingresar antes del giro del recibo mensual dicha cifra.

6.º OTRAS ATRIBUCIONES: El uso del vehículo modelo [MARCA/MODELO], matrícula [MATRÍCULA] se atribuirá a D./Dña. [NOMBRE Y APELLIDOS] y el del vehículo modelo [MARCA/MODELO], matrícula [MATRÍCULA] se atribuirá a D./Dña. [NOMBRE Y APELLIDOS]

7.º MEDIDAS SOBRE EL PATRIMONIO COMÚN:

(Opciones):

a) La rentas derivadas de [COMPLETAR] que se gestionarán por D./Dña. [NOMBRE Y APELLIDOS] deberán repartirse mensualmente al cincuenta por ciento, así como los gastos, entre ambos.

b) La gestión ordinaria del negocio familiar de [COMPLETAR] se concederá hasta la liquidación del régimen económico a D./Dña. De dicha actuación deberá darse cuenta con una periodicidad de [COMPLETAR], presentando las mismas ante el Tribunal.

c) [COMPLETAR].

8.º MEDIDAS DE GARANTÍA: Para asegurar el cumplimiento de las obligaciones anteriores se adoptarán las siguientes medidas: [COMPLETAR].

Las costas deberán imponerse a la otra parte si se opusiera temerariamente a esta pretensión.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

(En su caso, en situaciones acreditadas de urgencia): OTROSÍ DIGO: Que en atención a la urgencia del caso derivada de [COMPLETAR] y según permite el art. 771.2 de la LEC interesamos la adopción urgente antes de la vista de las medidas que interesamos relativas a la custodia de los hijos y usos de la vivienda familiar.

NUEVAMENTE SUPLICO: Que tenga por interesada esta medida y ordene lo necesario para su práctica por ser justicia que pido en mismo lugar y fecha

========================================================================
