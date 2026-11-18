---
name: demanda-reclamacion-legitima-galicia-345
description: "Redacta el escrito «Demanda de reclamación de legítima (Galicia)» (formulario 345 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de reclamación de legítima (Galicia)

> Formulario 0345 del plugin **Sucesiones** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (21 veces)
- [ ] NÚMERO
- [ ] LOCALIDAD (5 veces)
- [ ] CALLE (2 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Otros 19 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, con D.N.I. nº [NÚMERO], vecina de»; «…, falleció el»; «…mento nº —), bajo testamento otorgado el»; «…ante la notaria de»; «…ante la notaria de [COMPLETAR], Sra.»; «…, falleció el»; «…mento nº —), bajo testamento otorgado el»; «…ante la notaria de»; «…ante la notaria de [COMPLETAR], Sra.»; «…, legando a su nieta»; «…amento que se acompañan bajo los números»; «…, de la localidad de»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 85.1 LOPJ
- arts. 23 y 31 LEC
- arts. 248 y 249.2 LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 399 LEC
- art. 394.1 LEC

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

### Formulario 0345 · Demanda de reclamación de legítima (Galicia)

- Año del modelo: 2019
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 53 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda de juicio ordinario sobre reclamación de legítima ex art. 243 de la Ley de Derecho Civil de Galicia.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, que actúa en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], con D.N.I. nº [NÚMERO], vecina de [COMPLETAR], y domicilio en [LOCALIDAD], calle [CALLE], como acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], bajo la dirección del Letrado/a en ejercicio D./Dña. [NOMBRE Y APELLIDOS], abogado del Iltre. Colegio de [LOCALIDAD], y despacho abierto en [LOCALIDAD], calle [CALLE], ante el Tribunal comparezco, y como mejor proceda en Derecho, DIGO:

Que por medio del presente escrito y siguiendo concretas instrucciones de mi mandante, interpongo DEMANDA DE JUICIO DECLARATIVO ORDINARIO, en ejercicio de la acción que más adelante se dirá, frente a Doña CONCEPCIÓN, mayor de edad, vecina de esta ciudad, con domicilio en [LOCALIDAD], sirviendo de base a la presente demanda los siguientes:

HECHOS

PRIMERO. D./Dña. [NOMBRE Y APELLIDOS], casada en únicas nupcias con D./Dña. [NOMBRE Y APELLIDOS], falleció el [COMPLETAR] (se acredita con certificación de defunción —documento nº —), bajo testamento otorgado el [COMPLETAR] ante la notaria de [COMPLETAR], Sra. [COMPLETAR], y en el que instituyó heredero a su esposo y legó la legítima estricta a su nieta Cándida, hija de su hijo premuerto D./Dña. [NOMBRE Y APELLIDOS] (se aporta copia del testamento —documento nº —, en relación con la certificación del Registro de Actos de última Voluntad —documento nº —).

SEGUNDO. Por su parte, D./Dña. [NOMBRE Y APELLIDOS], falleció el [COMPLETAR] (se acredita con la certificación de defunción —documento nº —), bajo testamento otorgado el [COMPLETAR] ante la notaria de [COMPLETAR], Sra. [COMPLETAR], y en el que instituyó heredera a D./Dña. [NOMBRE Y APELLIDOS], legando a su nieta [COMPLETAR] la legítima estricta (se acredita con la certificación librada por el Registro de Actos de Ultima Voluntad y copia autorizada del mencionado testamento que se acompañan bajo los números [COMPLETAR] de documentos)

D./Dña. [NOMBRE Y APELLIDOS], abuelo de mi representada, había residido en el domicilio sito en [LOCALIDAD], de la localidad de [COMPLETAR], ostentando la vecindad foral gallega (acompaño como documentos números [COMPLETAR] certificados de nacimiento de mi representada, libro de familia y certificado de defunción del finado).

TERCERO. D./Dña. [NOMBRE Y APELLIDOS] había fallecido el [COMPLETAR], sin haber otorgado testamento, estando separado judicialmente de su esposa D./Dña. [NOMBRE Y APELLIDOS] en virtud de sentencia de fecha [FECHA], con la que había tenido una hija, [COMPLETAR], nacida el [COMPLETAR] y que fue declarada heredera ab intestato de aquél por acta notarial de [COMPLETAR] (cfr. la copia del acta notarial, en relación con la certificación de fallecimiento de D./Dña. [NOMBRE Y APELLIDOS] y los demás documentos que figuran incorporados en el expediente notarial, que se acompaña como documento nº [Nº DE DOCUMENTO]).

CUARTO. Ante la falta de respuesta a sus reclamaciones de pago de la legítima, D./Dña. [NOMBRE Y APELLIDOS] presentó una solicitud de acto de conciliación, a los efectos de cumplir el requisito de procedibilidad para la iniciación de la vía jurisdiccional, frente D./Dña. [NOMBRE Y APELLIDOS], quien compareció en la fecha señalada y manifestó que "reconoce los hechos expuestos y que está de acuerdo con darle la parte que le corresponda a Cándida" (se acredita con el acta del acto de conciliación finalizado con avenencia —documento nº —), no obstante lo cual, a pesar de los requerimientos practicados (se acompañan copias auténticas de los requerimientos notariales practicados como documentos números [COMPLETAR]), el último de los cuales tenía por objeto que la conciliada formalizase inventario, con valoración de bienes, lo protocolizase ante notario y pagase a la conciliante la legítima que le correspondía, aquélla hizo caso omiso, por lo que, al carecer de datos sobre los bienes que forman el activo patrimonial de la herencia de su abuelo D./Dña. [NOMBRE Y APELLIDOS], más allá de los obrantes en los registros públicos, mi representada se ve en la ineludible obligación de ejercer la presente acción, siendo de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- JURISDICCIÓN Y COMPETENCIA.

Radicando la competencia genérica en el orden civil de la jurisdicción, detenta la competencia objetiva y funcional la Sección Civil del Tribunal de Instancia, por aplicación de lo dispuesto en los arts. 85.1 LOPJ y 45 LEC, y territorialmente es competente el Tribunal a que me dirijo, puesto que está prevenido el fuero territorial preceptivo específico para los juicios sobre cuestiones hereditarias, con arreglo a lo previsto en el art. 52.1.4.º LEC, del lugar del último domicilio del finado, siendo de este partido la población en que se hallaba la residencia donde murió D./Dña. [NOMBRE Y APELLIDOS].

II.- CAPACIDAD Y LEGITIMACIÓN.

Mi mandante D./Dña. [NOMBRE Y APELLIDOS], es persona física, mayor de edad, en pleno ejercicio de sus derechos civiles, así como lo es la demandada, D./Dña. [NOMBRE Y APELLIDOS], por lo que tienen ambas capacidad para ser parte y capacidad procesal ex arts. 6.1.1º y 7.1 LEC.

Corresponde la legitimación activa directa a mi mandante, ya que es legitimaria, como nieta del causante, y está legitimada pasivamente de forma directa la demandada, en su condición de heredera testamentaria.

III.- POSTULACIÓN Y DEFENSA.

Conforme a los arts. 23 y 31 LEC se formula esta demanda por medio de representación a Procurador de los Tribunales con poder notarial para pleitos, y bajo dirección y firma de Letrado habilitado ante el Tribunal.

IV.- PROCEDIMIENTO Y CUANTÍA

La presente demanda deberá sustanciarse por las normas del juicio ordinario, a tenor de lo prevenido en los arts. 248 y 249.2 LEC, que fija los cauces del procedimiento declarativo ordinario a aquellos asuntos cuya cuantía exceda de los 15.000 euros, o aquellas cuyo interés económico resulte imposible de calcular, ni siquiera de modo relativo.

En este sentido, fijamos como cuantía la de indeterminada, por desconocer esta parte el montante de los bienes que integran el caudal relicto del finado

V.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VI.- REQUISITOS FORMALES.

No aparecen, aparte de los requisitos genéricos de la demanda en juicio ordinario del art. 399 LEC, otros de carácter formal cuya falta, por el tipo de acción, invalidarían el proceso para pronunciarse sobre el fondo del asunto.

VII.- FONDO DEL ASUNTO.

Ejercita esta parte una acción de formación de inventario de los bienes de la herencia y avalúo de los bienes y derechos que la integran, como prejudicial de la acción principal de reclamación del pago de la legítima estricta en la herencia de su abuelo D./Dña. [NOMBRE Y APELLIDOS] ex art. 243 de la Ley de Derecho Civil de Galicia, legislación aplicable atendida su vecindad civil gallega, contra la heredera testamentaria del mismo.

Es evidente que la demandante tiene derecho a la parte de la legítima que le corresponde en la herencia, y más concretamente, a la cuarta parte del haber hereditario, para lo cual lógicamente es imprescindible que se practiquen las operaciones necesarias para conocer el activo y el pasivo de la herencia.

El objeto de la tutela judicial que se solicita se dirige a determinar y valorar el conjunto de bienes y derechos que conforman el patrimonio hereditario, como paso previo para calcular la cuota que corresponde en concepto de legítima y de la que debe responder la demandada como heredera testamentaria.

VIII.- COSTAS.

Conforme al principio del art. 394.1 LEC, del vencimiento objetivo, las costas irrogadas a esta parte en el juicio declarativo en la primera instancia se han de pronunciar a cargo de la demandada.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL

que, habiendo por presentado este escrito, con sus documentos y copias, se sirva admitirlo, me tenga por parte en la representación que ostento de D./Dña. [NOMBRE Y APELLIDOS] y por formulada demanda de juicio declarativo ordinario frente a D./Dña. [NOMBRE Y APELLIDOS], emplazarle para que comparezca y conteste, seguir el procedimiento por sus trámites y, en su momento, dictar sentencia por la que se condene a la demandada a satisfacer a la demandante la cantidad que le corresponde por sus derechos legitimarios en la herencia de su abuelo [COMPLETAR] y que habrá de ser obtenida del inventario de bienes y derechos de la herencia del causante citado que resulta en período de prueba, y todo ello con expresa imposición de las costas a la parte demandada.

Por ser de justicia que solicito en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a
