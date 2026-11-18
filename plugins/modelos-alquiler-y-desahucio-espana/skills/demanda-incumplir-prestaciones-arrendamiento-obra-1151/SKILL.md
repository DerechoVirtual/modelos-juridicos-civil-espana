---
name: demanda-incumplir-prestaciones-arrendamiento-obra-1151
description: "Redacta el escrito «Demanda por incumplir prestaciones del arrendamiento de obra» (formulario 1151 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda por incumplir prestaciones del arrendamiento de obra

> Formulario 1151 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] Nº
- [ ] COLEGIO
- [ ] FECHA (5 veces)
- [ ] IMPORTE (6 veces)
- [ ] NÚMERO (7 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Esta demanda se dirige contra la empresa»; «…, con sede social en esta ciudad en»; «…l cual se elaboró el contrato firmado en»; «… pretendemos. Adjuntamos como docs. n.os»; «…, informe técnico del perito en»; «… imposible por la negativa de la empresa»; «…guirlo por culpa exclusiva de la empresa»; «…ia la presente demanda contra la empresa»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 248.2, 249.2 y 251 de la LEC
- art. 399.5 de la LEC
- artículo 2 de la Ley 10/2012
- art. 10 de la LEC
- arts. 23 y 31 de la LEC
- art. 394.1 de la LEC
- art. 395 de la LEC
- Ley Orgánica 1/2025

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

### Formulario 1151 · Demanda por incumplir prestaciones del arrendamiento de obra

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 34 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (IMPORTE, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda Juicio ordinario

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], ante el Tribunal comparezco, bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], con n.º [Nº] de colegiado del Iltre. Colegio de Abogados de [COLEGIO], y como mejor proceda en derecho DIGO:

Que mediante el presente escrito interpongo demanda a tramitar por el cauce del juicio ordinario para que se declare la obligación de cumplir el contrato privado de arrendamiento de obra de fecha [FECHA] o, subsidiariamente, que se acuerde su resolución con expreso reconocimiento del derecho a ser indemnizado en la cantidad de [IMPORTE] euros más los intereses legales de esta cantidad desde la fecha de interposición de la reclamación. Esta demanda se dirige contra la empresa [COMPLETAR], con sede social en esta ciudad en [COMPLETAR], y se basa en los siguientes

HECHOS

Mi representado contrató con la demandada la instalación en su vivienda de parquet flotante. A tal efecto por la citada empresa se elaboró un presupuesto que fue sometido a la aceptación del actor y sobre el cual se elaboró el contrato firmado en [COMPLETAR] y de fecha [FECHA], cuyo cumplimiento o resolución pretendemos. Adjuntamos como docs. n.os [COMPLETAR] el presupuesto aceptado y el contrato. La titularidad del inmueble se acredita con nota simple del Registro de la Propiedad que acompañamos como doc. n.º [Nº DE DOCUMENTO]

Para facilitar la labor de los operarios la familia de D./Dña. [NOMBRE Y APELLIDOS] (actor) se trasladó a vivir a un apartamento que alquiló por quince días por un precio de [IMPORTE] euros. Adjunto como doc. n.º [NÚMERO] el contrato de arrendamiento.

Entre las partes se había convenido un precio total de [IMPORTE] euros, que incluía materiales y mano de obra, que la instalación se realizaría en el plazo improrrogable de 15 días, y que se comenzaría eldía [FECHA], añadiéndose una cláusula penal para el caso de incumplimiento. Por ese motivo, llegada la fecha se realizó el traslado de los ocupantes a su nueva residencia temporal y se dejó al demandado una llave de la vivienda para que pudiera realizar las obras.

Transcurrida una semana del plazo acordado, mi representado se personó en su domicilio para comprobar como se iba ejecutando la instalación y cuál no sería su sorpresa cuando advierte que apenas se han producido progresos en la obra.

Alarmado por esta circunstancia, se puso al habla con el representante de la empresa para averiguar la causa de la demora, y se le expuso que estaban acabando otra y que no se preocupara que en el tiempo convenido habrían acabado tal obra.

Pero transcurrido el plazo de los quince días la obligación se había cumplido sólo parcialmente, ya que se había instalado la madera en dos de las cuatro habitaciones. Por otro lado, a pesar de que inicialmente se había considerado innecesario, habían levantado el suelo del resto de la casa, para proceder posteriormente a colocar el nuevo.

Adjuntamos como doc. n.º [NÚMERO] acta notarial del estado de la vivienda a fecha [FECHA] y acompañamos con el n.º [NÚMERO] cinta de vídeo donde se puede apreciar de forma gráfica las deficiencias que alegamos.

Así las cosas el demandado forzó una renegociación del contrato, y de forma oral se le concedieron quince días más para acabar la obra, aunque desde ese momento se dejó claro que el actor no asumía ningún gasto por el levantamiento del suelo que de forma unilateral había decidido el contratista sin consultar con el propietario. Acompañamos con el n.º [NÚMERO], informe técnico del perito en [COMPLETAR] (título)

D. sobre la forma de ejecución de la obra, en el que se hace constar que no es necesario realizar la actividad adicional que se llevó a cabo.

Transcurrido el mes la colocación del suelo no se había completado, ya que sólo se había terminado un habitación más. El demandado alegó en este caso que no pensaba finalizar la obra hasta que no se asumiera por esta parte la obligación de pagar las actuaciones complementarias que habían realizado.

Así las cosas se rompieron las negociaciones y mi representado volvió a su casa en el estado en que ésta se encontraba. Su intención consiste en que o bien se concluyan las obras o bien se acuerde la resolución del contrato para que así pueda acudir a otro especialista para que finalice la obra. El informe pericial que acompañamos con el n.º [NÚMERO] valora el coste de la obra que resta por ejecutar.

En el contrato se establecía el pago en dos plazos, el cincuenta por ciento al inicio de la obra y la otra mitad a su conclusión. Adjuntamos como doc. n.º [NÚMERO] el recibo de pago inicial. El precio de la obra se calculaba en atención a la mano de obra y a los metros de parquet que se iban a instalar. Teniendo en cuenta, tal como se hace constar en el informe ya citado, que se ha ejecutado más o menos la mitad de la obra, esta parte nada adeuda al demandado, puesto que le ha pagado lo que realmente ha realizado.

Finalmente, y para el caso de que se decida resolver el contrato y resarcir por los daños causados, entendemos que se puede incluir dentro de éstos el precio del alquiler de los quince días en que se alargó el contrato. Presentamos el recibo de pago como doc. n.º [Nº DE DOCUMENTO]

Según se acredita con el doc. n.º [NÚMERO], se presentó una reclamación ante la Oficina Municipal de información al consumidor para intentar un arreglo por esta vía, algo que resultó imposible por la negativa de la empresa [COMPLETAR] Dejamos acotados los archivos de esa entidad pública a efectos probatorios al resultarle imposible a esta parte obtener copia de todo el expediente.

FUNDAMENTOS DE DERECHO

Tramitación

En atención al valor contratado de la obra, que asciende según el contratoa

 [IMPORTE] euros se seguirá el cauce del juicio ordinario en aplicación de los arts. 248.2, 249.2 y 251 de la LEC. El art. 399.5 de la LEC permite realizar peticiones subsidiarias.

(En su caso) Acompañamos modelo 696 de autoliquidación de la tasa judicial, en cumplimiento de lo exigido por el artículo 2 de la Ley 10/2012, de 20 de noviembre.

Legitimación

El art. 10 de la LEC legitima para comparecer y actuar en juicio a los titulares de la relación jurídica u objeto litigioso. En este caso actor y demandado son los titulares del contrato cuyo cumplimiento se pretende.

Postulación

En aplicación de los arts. 23 y 31 de la LEC ambos deberán comparecer representados por procurador y asistidos por abogado.

Cumplimiento de los requisitos de procedibilidad

La presente demanda cumple con el requisito de procedibilidad exigido por la disp. adic. 7ª de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Fondo del asunto

1.º Art. 1091 del CC, según el cual las obligaciones que nacen de los contratos tienen fuerza de ley entre las partes y deben cumplirse al tenor de los mismos.

2.º Arts. 1588 y siguientes del CC sobre el arrendamiento de obra que permiten contratar su ejecución poniendo, el que la realiza, su trabajo y el material.

3.º Art. 1124 del CC: “la facultad de resolver las obligaciones se entiende implícita en las recíprocas, para el caso de que uno de los obligados no cumpliere lo que le incumbe.

El perjudicado podrá escoger entre exigir el cumplimiento o la resolución de la obligación, con el resarcimiento de daños y abono de intereses en ambos casos”.

En este supuesto se ha acreditado la existencia del contrato, el contenido de sus obligaciones, el incumplimiento por una de las partes, la parte de obra que falta por ejecutar, y los perjuicios económicos que ha ocasionado al actor.

Costas

En aplicación del art. 394.1 de la LEC, deberán imponerse al demandado al rechazarse todas sus pretensiones, incluso aunque se allanara a la demanda, art. 395 de la LEC, por haberse acreditado que se ha intentado evitar esta vía sin conseguirlo por culpa exclusiva de la empresa [COMPLETAR] que ha cerrado toda vía para la negociación.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos y medios que acompaño, y copia de todo ello, admita a trámite el Letrado de la Administración de justicia la presente demanda contra la empresa [COMPLETAR] y en su día, previos los trámites legales oportunos con el recibimiento del juicio a prueba que se deja expresamente solicitado, se dicte sentencia por la que se declare lo siguiente:

1.º Que se condene al demandado a ejecutar por completo la obra a la que se comprometió por contrato de fecha [FECHA], en el modo y forma que figura en tal contrato, y según se fija en el informe pericial que esta parte aporta como prueba, fijando un plazo máximo de quince días para su realización.

2.º De forma subsidiaria, y para el caso de que el Tribunal considere que no existen causas para señalar plazo, que se decrete la resolución del contrato ya identificado, haciendo expresa declaración de que esta parte nada adeuda al demandado.

3.º Que en el primer caso se indemnice al actor con la cantidad de [IMPORTE] euros por los perjuicios causados como consecuencia de la necesidad de prorrogar la duración del alquiler para permitir la realización de las obras, y en el segundo que se añada a esta cantidad la de [IMPORTE] euros en que se valora la obra necesaria para reponer el suelo levantado sin autorización del propietario y para ejecutar una obra que finalmente no se llevó a cabo.

4.º En todo caso se interesa igualmente la condena en costas del demandado, incluso aunque se allane, así como al pago de intereses de la cantidad que se declare para indemnizar al actor, que empezarán a contarse desde la interposición de la demanda.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
