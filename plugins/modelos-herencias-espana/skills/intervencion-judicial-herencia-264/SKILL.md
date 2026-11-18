---
name: intervencion-judicial-herencia-264
description: "Redacta el escrito «Intervención judicial de la herencia» (formulario 264 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Intervención judicial de la herencia

> Formulario 0264 del plugin **Sucesiones** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] Nº DE DOCUMENTO (9 veces)
- [ ] Nº
- [ ] FECHA (2 veces)
- [ ] LOCALIDAD (5 veces)
- [ ] NÚMERO (3 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 21 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…D.»; «…, perteneciente al ICA de»; «…con el nº [Nº] de colegiada»; «…TERVENCION JUDICIAL DE LA HERENCIA de D.»; «…, en la localidad de»; «…de cuya unión tuvo cuatro hijos llamados»; «…Aportamos como documentos números»; «…rimonio (y hermanos del demandante): -D.»; «…, vecino de»; «…y provisto de D.N.I. nº [NÚMERO] -D.»; «…-D. [COMPLETAR], vecino de»; «…y provisto de D.N.I. nº [NÚMERO] -D.»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 783.4 LEC
- arts. 790 a 805 LEC
- art. 793.1 LEC
- art. 1.051 CCiv
- arts. 790 y 792 LEC
- art. 798 LEC

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

### Formulario 0264 · Intervención judicial de la herencia

- Año del modelo: 2020
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 45 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Solicitud de intervención judicial de herencia abintestato sin declaración de herederos por el cónyuge o cualquiera de los parientes que se crea con derecho a la sucesión legítima.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D. [COMPLETAR], Procurador de los Tribunales y de D.ª [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], bajo la dirección letrada de D.ª [NOMBRE Y APELLIDOS], perteneciente al ICA de [COMPLETAR] con el nº [Nº] de colegiada [COMPLETAR], ante este Tribunal comparezco y como mejor proceda, DIGO:

Que a medio del presente escrito, en la representación enunciada y al amparo de lo dispuesto en el art. 792.1.1º LEC, solicito la INTERVENCION JUDICIAL DE LA HERENCIA de D. [COMPLETAR], todo ello sobre la base de los siguientes:

HECHOS

PRIMERO.- El cónyuge de mi representada falleció el día [FECHA], en la localidad de [COMPLETAR], según resulta del certificado de defunción expedido por el Registro Civil de [LOCALIDAD] que se acompaña como documento número [Nº DE DOCUMENTO].

SEGUNDO.- Al momento de su fallecimiento D. estaba casado con D.ª [NOMBRE Y APELLIDOS], de cuya unión tuvo cuatro hijos llamados [COMPLETAR]

Aportamos como documentos números [COMPLETAR] sendos certificados de nacimiento de los hijos habidos de dicho matrimonio; y como documento nº [Nº DE DOCUMENTO] certificado de matrimonio del Registro Civil de [LOCALIDAD] por el que se acredita la condición de mi mandante de cónyuge del finado.

TERCERO.- El finado no otorgó testamento alguno, según consta en el certificado de actos de últimas voluntades que aportamos como documento nº [Nº DE DOCUMENTO], por lo que su sucesión queda abintestato.

CUARTO.- A los efectos de tramitación de la presente solicitud, resultan interesados en la sucesión del causante los hijos comunes del matrimonio (y hermanos del demandante):

-D. [COMPLETAR], vecino de [COMPLETAR], con domicilio en [LOCALIDAD] y provisto de D.N.I. nº [NÚMERO]
-D. [COMPLETAR], vecino de [COMPLETAR], con domicilio en [LOCALIDAD] y provisto de D.N.I. nº [NÚMERO]
-D. [COMPLETAR], vecino de [COMPLETAR], con domicilio en [LOCALIDAD] y provisto de D.N.I. nº [NÚMERO]

QUINTO.- Los bienes del causante en el momento de su fallecimiento, s.e.u.o. son los siguientes:

- Relación de bienes y derechos del causante (Metálico, cuentas bancarias):
- Relación de bienes y derechos del causante: Bienes muebles (vehículos, etc.):
- Relación de bienes y derechos del causante (Valores, etc.):
- Relación de bienes y derechos del causante: Bienes inmuebles:
- Otros bienes:

SEXTO.- Habiendo fallecido D. sin testamento, ha sido instada por esta parte la declaración de herederos abintestato, en la Notaría de la ciudad de [COMPLETAR], como último lugar de residencia del causante, cuya constancia se acredita mediante la presentación del documento nº [Nº DE DOCUMENTO]

A estos efectos, esta parte ha requerido a los coherederos e hijos del causante D. [NOMBRE Y APELLIDOS] en varias ocasiones, a fin de otorgar la correspondiente escritura de partición de herencia.

Concretamente se ha citado a los coherederos e hijos del causante en la notaría de [COMPLETAR] para proceder a otorgar la correspondiente declaración de herederos. A pesar de tener toda la documentación preparada, ninguno de los tres comparecieron, desoyendo todos los requerimientos.

Así, se les ha requerido sin éxito mediante carta certificada con fecha [FECHA] y [COMPLETAR]. Aportamos como documento nº [Nº DE DOCUMENTO] el primer burofax y como documento nº [Nº DE DOCUMENTO] su acuse de recibo de [COMPLETAR]; y aportamos como documento nº [Nº DE DOCUMENTO] el segundo burofax y como documento nº [Nº DE DOCUMENTO] su acuse de recibo de

La necesidad de percibir las rentas y demás ingresos del caudal hereditario, preservando los mismos para hacer frente a las deudas y gastos de dicho caudal, hacer valer los créditos del causante, gestionando el cumplimiento de las obligaciones de los deudores, así como para proceder a su justo y equitativo reparto en un futuro, es lo que justifica solicitar el auxilio para la intervención efectiva de la herencia yacente de D. [NOMBRE Y APELLIDOS]

A los anteriores hechos son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- JURISDICCIÓN Y COMPETENCIA

De acuerdo con los arts. 85.1º LOPJ y 45 LEC, corresponde a los Tribunales de Instancia el conocimiento de todos los asuntos civiles que por disposición legal expresa no se hallen atribuidos a otros Tribunales. Del mismo modo, ostenta competencia territorial para el conocimiento de esta intervención judicial el Tribunal al que nos dirigimos de conformidad con los dispuesto en el art. 52.1.4º LEC, al corresponder el Tribunal al lugar en el que el finado tuvo su último domicilio.

II.- LEGITIMACIÓN

Mi representada ostenta legitimación activa para la interposición de esta solicitud, en su cualidad de cónyuge del finado, y conforme a lo dispuesto en el art. 792.1.1º LEC.

No habiendo interesados en la herencia menores o ausentes, [NOTA DE REVISIÓN: El art. 783.4 LEC vigente solo prevé la representación del Fiscal para menores sin representación legítima y ausentes. Fuente: LEC 1/2000 (BOE-A-2000-323) art. 783.4, redacción Ley 8/2021 (BOE-A-2021-9233) (art. 4.25).] no resulta necesaria la intervención del ministerio fiscal, a sensu contrario de lo dispuesto en el art. 783.4 LEC.

III.- PROCEDIMIENTO

La presente solicitud debe sustanciarse a través de los trámites del procedimiento para la intervención judicial de la herencia, previsto en los arts. 790 a 805 LEC.

IV.- PRESUPUESTO PROCESAL DE LA ACCIÓN

Concurren en este caso los presupuestos habilitantes dispuestos por el art. 792.1.1º LEC para la práctica de las actuaciones previstas en el art. 793.1 LEC, cual es que mi mandante es cónyuge del causante, y acredita haber promovido la declaración de herederos abintestato ante Notario.

Así las cosas, y verificada por el letrado de la Administración de Justicia la concurrencia de estas circunstancias, el Tribunal, por medio de Auto deberá mandar que se proceda a ocupar los libros, papeles y correspondencia del difunto, así como a inventariar y depositar los bienes, disponiendo lo que proceda sobre si administración, con arreglo a lo establecido en la LEC. Asimismo, podrá nombrar a una persona, con cargo al caudal hereditario, que efectúe y garantice el inventario y su depósito.

V.- ASUNTO DE FONDO.

El art. 1.051 CCiv dispone que "Ningún coheredero podrá ser obligado a permanecer en la indivisión de la herencia a menos que el testador prohíba expresamente la división. Pero, aun cuando la prohíba, la división tendrá siempre lugar mediante alguna de las causas por las cuales se extingue la sociedad".

Esta parte ha acompañado los documentos exigidos para acreditar la defunción del causante y la condición de heredero del compareciente, así como la imposibilidad de llevar a cabo la partición de herencia por cauces no imputables a nuestro mandante, por la actitud obstruccionista de los coherederos.

Así mismo, se han expuesto las razones que fundamentan esta solicitud, en concreto lo actos obstativos de los demás coherederos y la necesidad de salvaguardar el caudal hereditario, adoptando las medidas indispensables para la seguridad de los bienes, así como de los libros, documentos, colecciones, joyas y efectos del difunto susceptibles de sustracción u ocultación.

Dicha posibilidad sólo está prevista conforme a los arts. 790 y 792 LEC, para dos supuestos:

a) Cuando no conste la existencia de testamento ni herederos.
b) A instancia de personas con derechos sobre la herencia durante la tramitación de la declaración de herederos o de la división judicial.

A fin de evitar esta situación de indivisibilidad del caudal, el Tribunal Supremo ha recocido en los herederos legitimación para actuar en beneficio de la herencia yacente, pudiendo ejercitar la acciones necesarias en defensa de los derechos de la masa hereditaria (STS de 16 de septiembre de 1985, [COMPLETAR]) e igualmente reconoce a los titulares de créditos contra la herencia la posibilidad de dirigir su demanda contra aquélla, en situación de yacencia, y las personas que se crean con derecho a la misma, tratando así de evitar los perjuicios que una demora pudiera ocasionar (STS de 21 de mayo de 1991, [COMPLETAR].

Por su parte la DGRN-DGSJFP, para la inscripción o anotación relativa a bienes titularidad del causante que ha dado lugar a la herencia yacente exige o bien se acredite en el mandamiento que se ha dado emplazamiento a alguno de los posibles llamados a la herencia, o bien que se ha procedido al nombramiento judicial de un administrador de la herencia yacente.

El art. 798 LEC dispone que mientras la herencia no haya sido aceptada por los herederos, el administrador de los bienes representará a la herencia en todos los pleitos que se promuevan o que estuvieren principiados al fallecer el causante y ejercitará en dicha representación las acciones que pudieran corresponder al difunto hasta que se haga la declaración de herederos.

Por todo lo cual,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito, con los documentos y copias que acompaño de los mismos, se sirva admitirlo y a mí por comparecido en nombre de mi mandante, por propuesto este escrito de SOLICITUD DE INTERVENCIÓN JUDICIAL DE LA HERENCIA de Don [COMPLETAR], y después de cumplidos los demás trámites procesales, tenga a bien estimarla y se ACUERDE:

- La intervención del caudal hereditario.
- La ocupación de los libros, papeles y correspondencia del difunto.
- La formación de Inventario y Depósito de bienes.
-El nombramiento urgente e inmediato de un ADMINISTRADOR DE LA HERENCIA YACENTE de Don [COMPLETAR], de modo que además de representar a la herencia yacente, proceda de inmediato a gestionar dicho patrimonio con la diligencia de un buen padre de familia, adoptando las medidas necesarias para la protección del caudal y para que el administrador judicial pueda cumplir su fin, adoptando en su caso las medidas coercitivas que hubiera lugar en derecho.

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado

	Firma de Procurador
