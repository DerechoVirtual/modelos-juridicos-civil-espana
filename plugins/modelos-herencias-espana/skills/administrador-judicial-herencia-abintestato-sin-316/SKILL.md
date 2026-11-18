---
name: administrador-judicial-herencia-abintestato-sin-316
description: "Redacta el escrito «Administrador judicial de herencia abintestato sin declaración de herederos» (formulario 316 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Administrador judicial de herencia abintestato sin declaración de herederos

> Formulario 0316 del plugin **Sucesiones** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (11 veces)
- [ ] Nº DE DOCUMENTO (12 veces)
- [ ] CALLE (6 veces)
- [ ] NÚMERO (6 veces)
- [ ] FECHA (5 veces)
- [ ] LOCALIDAD
- [ ] Nº
- [ ] IMPORTE
- [ ] STS de 16 de septiembre de 1985
- [ ] STS de 21 de mayo de 1991
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 54 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, bajo la dirección letrada de Dª»; «…, perteneciente al I.C. de Abogados de»; «…con el número de colegiado»; «…Que D. [NOMBRE Y APELLIDOS], vecino de»; «…, nº [NÚMERO] de»; «…de [COMPLETAR] y provisto de D.N.I.»; «…, falleció en»; «…alleció en [COMPLETAR] el día [FECHA] de»; «…el día [FECHA] de [COMPLETAR] de»; «…ortamos como documento nº 1. D. nació en»; «…el día [FECHA] de»; «…el día [FECHA] de [COMPLETAR] de dos mil»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 792.1 de la LEC
- arts. 23 y 31 de la LEC
- art. 792 de la LEC
- artículo 783.4 LEC
- arts. 9.2, 21.1 y 22 de la LOPJ
- artículos 801 a 803 del CC
- artículo 901 del CC
- artículos 790 y 792 de la LEC
- artículo 798 LEC
- art. 792.2 de la LEC

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

### Formulario 0316 · Administrador judicial de herencia abintestato sin declaración de herederos

- Año del modelo: 2020
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 89 campos de relleno marcados en blanco; 10 huecos del original que se habían perdido sin marca, marcados (IMPORTE, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

QUE POR TURNO CORRESPONDA

D./D.ª [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./D.ª [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], bajo la dirección letrada de Dª [COMPLETAR], perteneciente al I.C. de Abogados de [COMPLETAR] con el número de colegiado [COMPLETAR], ante este Tribunal comparezco y como mejor proceda DIGO:

Que a medio del presente escrito, en la representación enunciada y al amparo de lo dispuesto en el art. 792.1 de la LEC, SOLICITO LA INTERVENCION JUDICIAL DE LA HERENCIA DE D. [NOMBRE Y APELLIDOS], en tanto no se ha procedido a la división de dicha herencia, es por lo que demanda que halla su base en los siguientes

HECHOS

PRIMERO Causante: D. [NOMBRE Y APELLIDOS]

Que D. [NOMBRE Y APELLIDOS], vecino de [COMPLETAR], con domicilio en calle [CALLE], nº [NÚMERO] de [COMPLETAR] y provisto de D.N.I. [COMPLETAR], falleció en [COMPLETAR] el día [FECHA] de [COMPLETAR] de [COMPLETAR], según resulta del certificado de defunción, que aportamos como documento nº 1.

D. nació en [COMPLETAR] el día [FECHA] de [COMPLETAR] de dos mil [COMPLETAR].

Al momento de su fallecimiento tenía su domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], y estaba viudo de Dª., de cuyo matrimonio tuvo hijos llamados, [COMPLETAR] y

Aportamos como documentos nºs 2, 3, 4 y 5 sendos certificados de nacimiento de los hijos habidos del matrimonio.

SEGUNDO ÚLTIMAS VOLUNTADES.

Que al momento de su fallecimiento, D. NO había otorgado testamento, según consta en el certificado de actos de últimas voluntades que aportamos como documento nº 4.

TERCERO .- PREMORIENCIA DE LA ESPOSA DE D.. [NOMBRE Y APELLIDOS]

Dª., provista de D.N.I., falleció en [COMPLETAR] el día [FECHA] de [COMPLETAR] de [COMPLETAR].

Dª falleció intestada y a día de hoy no se ha otorgado escritura de herencia de la expresada causante. Aportamos certificado de defunción como documento 5, y certificado de actos de últimas voluntades como documento nº 6.

Cuarto .- HEREDEROS E INVENTARIO DE BIENES DEL CAUSANTE D.. [NOMBRE Y APELLIDOS].

A los efectos de tramitación de la presente solicitud, resultan interesados en la partición de herencia del causante:

1.- El demandante, D. [COMPLETAR], hijo a su vez de la causante.

2.- Los otros tres hijos comunes del matrimonio (y hermanos del demandante):

D. [NOMBRE Y APELLIDOS], vecino de [COMPLETAR], con domicilio en calle [CALLE], nº [Nº] de y provisto de D.N.I.,

Dª [COMPLETAR] vecino de [COMPLETAR], con domicilio en calle [CALLE], nº [NÚMERO] de y provisto de D.N.I.,

Dª [COMPLETAR] vecino de [COMPLETAR], con domicilio en calle [CALLE], nº [NÚMERO] de y provisto de D.N.I.

El inventario de bienes al momento del fallecimiento del causante D, es s.e.u.o. el siguiente:

BIENES INMUEBLES RÚSTICOS:
Mitad ganancial de la finca rústica en término municipal de (Valladolid) al pago de [COMPLETAR], inscrita en el Registro de la Propiedad de [COMPLETAR] al Tomo [COMPLETAR], Libro [COMPLETAR], Folio [COMPLETAR], con una superficie de [COMPLETAR], finca [COMPLETAR].

Estado: libre de cargas y arrendamientos.

Esta finca tiene inherentes 25 derechos de la PAC, cuyo importe anual es de [IMPORTE] €.

Título originario: adquirida por compra en escritura pública otorgada ante el notario D. el día [FECHA] de [COMPLETAR] de [COMPLETAR], al número de protocolo [COMPLETAR].

Referencia catastral:

BIENES INMUEBLES URBANOS:
Vivienda urbana sita en la calle [CALLE], número [NÚMERO] de [COMPLETAR].

Descripción del inmueble y linderos [COMPLETAR]

Referencia catastral [COMPLETAR]

Título actual: escritura de [COMPLETAR] de [COMPLETAR] de [COMPLETAR] de compraventa ante el notario de [COMPLETAR] D.al número de su protocolo [COMPLETAR]

Inscripción registral [COMPLETAR].

Estado:

BIENES MUEBLES:
DEPÓSITOS Y OTROS PRODUCTOS BANCARIOS:
PARTICIPACIONES EN SOCIEDADES MERCANTILES:
CRÉDITOS a favor del causante:
Mobiliario y ajuar familiar.

A efectos acreditativos, aportamos los siguientes documentos:

Como documentos nº [Nº DE DOCUMENTO] a [COMPLETAR] ambos inclusive, escrituras de compraventa de los bienes inmuebles
Como documentos nº [Nº DE DOCUMENTO] y [COMPLETAR] ambos inclusive, documentos acreditativos de las cargas y gravámenes, escrituras de préstamo hipotecario, contratos de arrendamiento.
Como documentos nº [Nº DE DOCUMENTO] y [COMPLETAR] ambos inclusive, sobre contratos de arrendamiento rústico.
Como documento nº [Nº DE DOCUMENTO], la carga acreditativa sobre la finca rústica
Como documentos nº [Nº DE DOCUMENTO] y [COMPLETAR], un conjunto de fotografías de las colecciones
Como documentos nº [Nº DE DOCUMENTO] y [COMPLETAR], el certificado de saldos expedidos por las entidades bancarias.
Como documentos nº [Nº DE DOCUMENTO] y [COMPLETAR], la escritura de constitución de la Sociedad y el certificado de cuentas anuales y memoria del Registro Mercantil.
Como documento nº [Nº DE DOCUMENTO] el Acta notarial suscrito ante el Notario D el día [FECHA] al número [NÚMERO] de su protocolo de reconocimiento de deuda a favor del causante.

QUINTO.- FUNDAMENTO FÁCTICO PARA SOLICITAR ESTA INTERVENCIÓN. REQUERIMIENTOS A LOS TRES COHEREDEROS D. [NOMBRE Y APELLIDOS], Dª Y Dª.

Habiendo fallecido D. [COMPLETAR], esta parte ha requerido a los coherederos e hijos del causante D. [NOMBRE Y APELLIDOS] en varias ocasiones, a fin de otorgar la correspondiente escritura de partición de herencia. Así, se les ha requerido mediante carta certificada el [COMPLETAR] y el [COMPLETAR] Aportamos como documento 34 el primer burofax y como documento 35 su acuse de recibo de [COMPLETAR]; y aportamos como documento 36 el segundo burofax y como documento 37 su acuse de recibo de

Concretamente se les ha citado en la notaría de [COMPLETAR] para proceder a otorgar la correspondiente declaración de herederos. A pesar de tener toda la documentación preparada, ninguno de los tres comparecieron, desoyendo todos los requerimientos.

Lejos de colaborar con esta parte, o con la notaría encargada de la tramitación de la herencia, los coherederos (relatar actos violentos, de apropiación u obstativos para la toma de posesión de bienes de la herencia, o de información o control del causal por parte de un heredero legítimo)

Aportamos como documento nº [Nº DE DOCUMENTO] la denuncia presentada, como documento nº [Nº DE DOCUMENTO] el justificante de lexnet de presentación y como documento nº [Nº DE DOCUMENTO] el Auto de sobreseimiento y remisión al tribunal civil que corresponda.

Otras razones necesarias que fundamentan la solicitud de la presente intervención son:

La necesidad de que se afronten los pagos por cuotas hipotecarias y otros pagos de manera puntual, obligación que vienen incumpliendo los coherederos precitados.
La necesidad de percibir las rentas y demás ingresos del caudal hereditario, preservando los mismos para hacer frente a las deudas y gastos de dicho caudal, así como para proceder a su justo y equitativo reparto en un futuro.
La intervención en el negocio familiar por cuanto no existe quorum para nombrar un administrador provisional hasta la completa liquidación de la herencia, siendo imposible la operatividad diaria del negocio.
Hacer valer los créditos del causante, gestionando el cumplimiento de las obligaciones de los deudores.
Gestionar los próximos vencimientos de los fondos de inversión, evitando su prórroga.

Siendo todos los requerimientos infructuosos hasta la fecha no queda otra alternativa que acudir a la vía judicial a solicitar el auxilio para la intervención efectiva de la herencia yacente de D.. [NOMBRE Y APELLIDOS].

FUNDAMENTOS DE DERECHO

I.CAPACIDAD.- La parte ostenta la capacidad procesal necesaria conforme a lo establecido en los arts. 6 y ss. de la LEC..

II.- REPRESENTACIÓN.- Conforme a lo dispuesto en los arts. 23 y 31 de la LEC y siendo preceptiva la intervención de abogado, esta parte acude asistida de letrado y representada por procurador.

III.- LEGITIMACIÓN.- Corresponde a mi representado como heredero de su padre, teniendo interés legítimo en la herencia de su padre D… conforme a lo dispuesto en el art. 792 de la LEC.

No resulta necesaria la intervención del ministerio fiscal, a sensu contrario del artículo 783.4 LEC.

IV.- JURISDICCIÓN y COMPETENCIA.- Es competente la jurisdicción civil, con arreglo a lo establecido en los arts. 9.2, 21.1 y 22 de la LOPJ, y 36 de la LEC.

Es competente el Tribunal al que nos dirigimos de conformidad con los dispuesto en el art. 52.1.4º de la LEC, al corresponder el Tribunal al lugar en el que el finado tuvo su último domicilio.

V.- PROCEDIMIENTO.- La presente solicitud debe sustanciarse a través de las reglas contenidas en los arts. 792 y siguiente de la LEC, al no haberse podido llegar a un acuerdo entre los distintos coherederos, y sin perjuicio de que pueda alcanzarse aquél en cualquier estado del juicio.

En este caso concreto, no existe la figura del administrador por cuanto no existe testamento ni así lo ha dispuesto el testador, a sensu contrario de los artículos 801 a 803 del CC, a través del propio albacea, conforme indica el artículo 901 del CC o de otro designado al efecto.

Al no disponer de administrador testamentario, la administración sólo puede ser dativa, a través del trámite previsto en los artículos 790 y ss de la Ley de Enjuiciamiento Civil (LEC).

VI.- ASUNTO DE FONDO. Nuestro Código Civil establece en su art. 1051 que «Ningún coheredero podrá ser obligado a permanecer en la indivisión de la herencia a menos que el testador prohíba expresamente la división. Pero, aun cuando la prohíba, la división tendrá siempre lugar mediante alguna de las causas por las cuales se extingue la sociedad”.

Esta parte ha acompañado los documentos exigidos para acreditar la defunción del causante y la condición de herederos del compareciente, así como la imposibilidad de llevar a cabo la partición de herencia por cauces no imputables a nuestro mandante, por la actitud obstruccionista de los coherederos.

Así mismo, se han expuesto las razones que fundamentan esta solicitud, en concreto lo actos obstativos de los demás coherederos y la necesidad de salvaguardar el caudal hereditario, adoptando las medidas indispensables para la seguridad de los bienes, así como de los libros, documentos, colecciones, joyas y efectos del difunto susceptibles de sustracción u ocultación.

Dicha posibilidad sólo está prevista conforme a los artículos 790 y 792 de la LEC, para dos supuestos;

a) Cuando no conste la existencia de testamento ni herederos.

b) A instancia de personas con derechos sobre la herencia durante la tramitación de la declaración de herederos o de la división judicial

A fin de evitar esta situación de inderogabilidad del caudal, el Tribunal Supremo ha recocido en los herederos legitimación para actuar en beneficio de la herencia yacente, pudiendo ejercitar la acciones necesarias en defensa de los derechos de la masa hereditaria [STS de 16 de septiembre de 1985] e igualmente reconoce a los titulares de créditos contra la herencia la posibilidad de dirigir su demanda contra aquélla, en situación de yacencia, y las personas que se crean con derecho a la misma, tratando así de evitar los perjuicios que una demora pudiera ocasionar [STS de 21 de mayo de 1991].

Por su parte la DGRN, para la inscripción o anotación relativa a bienes titularidad del causante que ha dado lugar a la herencia yacente exige o bien se acredite en el mandamiento que se ha dado emplazamiento a alguno de los posibles llamados a la herencia, o bien que se ha procedido al nombramiento judicial de un administrador de la herencia yacente.

El artículo 798 LEC dispone que mientras la herencia no haya sido aceptada por los herederos, el administrador de los bienes representará a la herencia en todos los pleitos que se promuevan o que estuvieren principiados al fallecer el causante y ejercitará en dicha representación las acciones que pudieran corresponder al difunto hasta que se haga la declaración de herederos.

Por todo lo cual,

AL TRIBUNAL SUPLICO tenga por presentado este escrito, su copia, el poder y los documentos que se acompañan; tenga por promovida al amparo de lo dispuesto en el art. 792.2 de la LEC DEMANDA DE SOLICITUD DE INTERVENCION JUDICIAL DE LA HERENCIA DE D [COMPLETAR] y después de cumplidos los demás trámites procesales, tenga a bien estimarla y se acuerde el nombramiento urgente e inmediato de un ADMINISTRADOR DE LA HERENCIA YACENTE de D [COMPLETAR], de modo que además de representar a la herencia yacente, proceda de inmediato a gestionar dicho patrimonio con la diligencia de un buen padre de familia, adoptando las medidas necesarias para la protección del caudal y para que el administrador judicial pueda cumplir su fin, adoptando en su caso las medidas coercitivas que hubiera lugar en derecho.

Es de Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].
