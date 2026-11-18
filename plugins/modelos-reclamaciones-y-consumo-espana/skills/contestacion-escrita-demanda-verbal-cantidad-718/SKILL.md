---
name: contestacion-escrita-demanda-verbal-cantidad-718
description: "Redacta el escrito «Contestación escrita a la demanda verbal de cantidad» (formulario 718 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación escrita a la demanda verbal de cantidad

> Formulario 0718 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.

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
- [ ] LOCALIDAD (2 veces)
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] CALLE
- [ ] NÚMERO
- [ ] Nº DE DOCUMENTO
- [ ] COLEGIO
- [ ] Nº
- [ ] SSTS de 25 de junio de 1993 y 19 de julio de 1994 
- [ ] LUGAR (2 veces)
- [ ] FECHA (2 veces)
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, con n.º [Nº] de colegiado»; «…me persono en los autos de juicio verbal»; «…/»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 23 y 31 LEC
- art. 1254 CCiv
- art. 394 LEC
- art. 438.1 LEC
- Ley 42/2015

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

### Formulario 0718 · Contestación escrita a la demanda verbal de cantidad

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 17 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Contestación escrita a demanda que se generaliza para todos los juicios verbales, sin excepción, a partir del 7 de octubre de 2015 (Ley 42/2015, reforma LEC). También se hace constar en el formulario la otra novedad significativa, que es la necesidad de las partes de pronunciarse sobre la necesidad o no de celebrar vista.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] DE [LOCALIDAD]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], representación que debidamente acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], bajo la asistencia de D./Dña. [NOMBRE Y APELLIDOS], Letrado/a del Ilustre Colegio de Abogados de [COLEGIO], con n.º [Nº] de colegiado [COMPLETAR], ante el Tribunal comparezco y respetuosamente (1) DIGO:

Que siguiendo expresas instrucciones de mi mandante, por medio del presente me persono en los autos de juicio verbal [COMPLETAR] / [COMPLETAR], seguidos en su contra por D./Dña. [NOMBRE Y APELLIDOS], y formulo CONTESTACIÓN A LA DEMANDA, en base a los hechos y fundamentos que a continuación se exponen.

HECHOS

PRIMERO

Con carácter previo se niegan los hechos expuestos en la demanda que se contesta, en cuanto no sean expresamente reconocidos en los siguientes apartados de hecho.

SEGUNDO

Es más cierto que mi mandante acudió al despacho del actor para interesarle su dictamen como profesional en la materia, requiriéndole dicho profesional que le aportara escrituras y documentos con la finalidad de que el demandante pudiera llevar a cabo su cometido. Se convino, siempre verbalmente, que el demandante tomaría una primera impresión del encargo y antes de estudiar la posibilidad de ejercer acciones, comunicaría a mi parte el importe aproximado de su minuta, que incluiría no sólo el dictamen previo sino además la llevanza del posible pleito.

En esta situación y al cabo de varios meses sin tener otra noticia ni requerimiento previo alguno nos encontramos con la presentación y exigencia de pago de su minuta de honorarios, con la natural extrañeza por nuestra parte ya que ni siquiera se le ha entregado el informe o dictamen a que dicha minuta corresponda.

TERCERO

No es cierto que mi parte haya sido notificada o requerida previamente de pago, ni que haya habido gestiones extrajudiciales para que el actor cobrara lo que aquí y ahora reclama.

A los anteriores hechos son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- JURISDICCIÓN Y COMPETENCIA

Conforme con los señalados de contrario.

II.- PROCEDIMIENTO

El juicio verbal a que se refieren los arts. 437 y siguientes LEC.

III.- LEGITIMACIÓN

Conformes con la exposición del demandante sobre legitimación activa y pasiva.

IV.- CUANTÍA

Conformes con la cuantía señalada de contrario.

V.- POSTULACIÓN Y DEFENSA

Esta parte contesta y comparece en autos por medio de Abogado y Procurador, arts. 23 y 31 LEC.

VI.- MATERIALES O SOBRE EL FONDO DEL ASUNTO

Estimamos inaplicables los fundamentos jurídicos citados por la demandante.

Citamos el art. 1254 CCiv en cuanto refiere que el contrato existe desde que una o varias personas consienten en obligarse respecto de otra u otras, a dar alguna cosa o prestar algún servicio. En el presente caso los contactos previos entre demandante y demandado no pueden generar obligación alguna en tanto el contrato no se perfeccione, no estándose ante la figura del llamado precontrato sino ante un mero trato preliminar, sin concretarse ni consolidarse ninguno de los elementos esenciales del contrato cual es la fijación del precio, a cuya determinación se pospone la prestación del consentimiento [SSTS de 25 de junio de 1993 y 19 de julio de 1994 ].

VII.- COSTAS

Conforme al art. 394 LEC, las costas han de imponerse a la parte demandante.

Por lo expuesto,

SUPLICO AL TRIBUNAL

Que tenga por presentado este escrito con sus documentos y copias de todo ello, teniéndome por comparecido y parte en la representación que ostento, mandando se entiendan conmigo las sucesivas actuaciones; tenerme por contestado y opuesto a la demanda, y siguiendo el pleito su curso, dictar Sentencia desestimando la demanda y absolviendo de sus pedimentos al demandado, con expresa imposición de costas a la parte actora.

Es Justicia que solicito en [LUGAR], a [FECHA].

OTROSÍ DIGO: Que interesa a esta parte la celebración de vista, al existir controversia sobre los hechos y ser necesaria la práctica de prueba para la resolución de este proceso.

SUPLICO AL TRIBUNAL: Que, teniendo por causada la manifestación antecedente, se sirva señalar la celebración de vista.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

NOTAS DEL FORMULARIO

(1) El art. 438.1 LEC, reformado por Ley 42/2015, introduce con carácter general la contestación escrita a la demanda en el juicio verbal –que antes solo se preveía para determinados procesos especiales-, en el plazo de diez días conforme a lo dispuesto para el juicio ordinario.

========================================================================
