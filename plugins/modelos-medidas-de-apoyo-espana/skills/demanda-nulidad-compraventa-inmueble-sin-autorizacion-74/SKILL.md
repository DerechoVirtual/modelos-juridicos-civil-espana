---
name: demanda-nulidad-compraventa-inmueble-sin-autorizacion-74
description: "Redacta el escrito «Demanda de nulidad de compraventa de inmueble sin autorización judicial del tutor o curador» (formulario 74 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de nulidad de compraventa de inmueble sin autorización judicial del tutor o curador

> Formulario 0074 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

- [ ] SEDE (3 veces)
- [ ] NOMBRE Y APELLIDOS (15 veces)
- [ ] LOCALIDAD (4 veces)
- [ ] FECHA (8 veces)
- [ ] Nº DE DOCUMENTO (6 veces)
- [ ] NÚMERO
- [ ] IMPORTE (4 veces)
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…rado de la Administración de Justicia de»; «…numeración del juzgado de procedencia).]»; «… nombre del tutelado, vendía el inmueble»; «…entes, tal como se recoge en el apartado»; «… de julio, de la jurisdicción voluntaria»; «…, elaborado por el perito tasador Sr/Sra»; «…rajudicial. En este sentido, se acudió a»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 271 del CC
- art. 61 de la Ley 15/2015
- art. 1301 del CC
- art. 1303 del Código Civil
- art. 1304 del CC
- arts. 50 y 52 LEC
- art. 249.2 LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 1300 del CC
- arts. 1303 y 1304 del CC
- art. 1303 CC
- art. 394 LEC
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

### Formulario 0074 · Demanda de nulidad de compraventa de inmueble sin autorización judicial del tutor o curador

- Año del modelo: 2023
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 49 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D/Dª [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales en representación de D/Dª [NOMBRE Y APELLIDOS], en su condición de curador de D/Dª [NOMBRE Y APELLIDOS], según acredito por certificación del registro electrónico de apoderamientos judiciales que acompaño (o mediante designación apud acta ante el Letrado de la Administración de Justicia de [COMPLETAR], bajo la dirección letrada de D/Dª [NOMBRE Y APELLIDOS], Abogado/a del Iltre. Colegio de [LOCALIDAD], ante el Tribunal comparezco y como mejor en derecho proceda DIGO:

Que, por medio de la presente, formulo demanda de juicio ordinario en ejercicio de la acción de nulidad del contrato de compraventa de fecha [FECHA], demanda que dirijo contra D/Dª [NOMBRE Y APELLIDOS] y D/Dª [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], con base en los siguientes

HECHOS

PRIMERO.- Se ejercita en el presente proceso la acción de nulidad del contrato de compraventa del inmueble sito en [LOCALIDAD], realizada por la anterior tutora de la persona que precisa apoyo D/Dª [NOMBRE Y APELLIDOS], a los compradores demandados, en fecha [FECHA], en escritura pública otorgada ante el notario D/Dª [NOMBRE Y APELLIDOS], por haberse realizado la enajenación sin la preceptiva autorización judicial.

Mi representado actúa como curador en ejercicio de la acción en nombre de D/Dª [NOMBRE Y APELLIDOS], al haber sido designado por auto del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], tras el fallecimiento de la anterior tutora D/Dª [NOMBRE Y APELLIDOS], tal como se acredita por el testimonio que se acompaña como documento número [Nº DE DOCUMENTO], ostentando funciones de representación.

Con carácter previo al ejercicio de la acción, mi representado solicitó autorización judicial para interponer la presente demanda en ejercicio de la acción de nulidad de la referida compraventa, la cual fue concedida por auto de fecha [FECHA], el citado Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO], que se acompaña como documento número

SEGUNDO.- La compraventa cuya nulidad se pretende se formalizó en escritura pública de fecha [FECHA], otorgada ante el Notario D/Dª [NOMBRE Y APELLIDOS], en virtud de la cual el anterior tutor de mi representado D/Dª [NOMBRE Y APELLIDOS], actuando en nombre del tutelado, vendía el inmueble [COMPLETAR] a los compradores demandados D/Dª [NOMBRE Y APELLIDOS] y D/Dª [NOMBRE Y APELLIDOS], por precio de [IMPORTE] euros, el cual fue satisfecho en el acto del otorgamiento (se acompaña como documento número [Nº DE DOCUMENTO] escritura pública de compraventa de fecha [FECHA]).

El tutor actuante había sido nombrado en sentencia de incapacidad de fecha [FECHA], dictada en el régimen anterior a la Ley 8/2021, de 2 de junio, en virtud de la cual se constituía la tutela de D/Dª [NOMBRE Y APELLIDOS], la cual fue inscrita en el Registro Civil ( se acompañan como documentos número [Nº DE DOCUMENTO], testimonio de la sentencia y certificación de inscripción registral).

Por tanto, conforme a lo que disponía el art. 271 del CC, en su anterior redacción, era necesaria la autorización judicial para proceder a la venta del inmueble del tutelado, lo cual era conocido por todos los intervinientes, tal como se recoge en el apartado [COMPLETAR] de la escritura pública de compraventa, donde consta expresamente la advertencia del Notario otorgante en los siguientes términos: "No se exhibe autorización judicial que faculte a dicha tutora para la compraventa objeto de esta escritura, de cuya necesidad advierto a los aquí otorgantes, a lo que se muestran conformes e insisten en el otorgamiento de esta escritura, comprometiéndose la citada tutora a obtener la aprobación judicial de esta venta, a la mayor brevedad posible".

No obstante dicha manifestación, la tutora en ningún momento recabó la autorización judicial para la venta, por lo que, siendo manifiestamente lesivo el negocio para los intereses de la persona sujeta a curatela, mi representado ejercita esta acción en demanda de la nulidad de la citada compraventa.

TERCERO.- La acción ejercitada se funda en la jurisprudencia que aplica el régimen de anulabilidad a los casos en que el tutor, ahora curador, enajena un bien inmueble de la persona con discapacidad sin autorización judicial, expresada en la STS 2/2018, de 10 de enero de 2018, rec. 2111/2015, por ser el más adecuado para la protección de los intereses de la persona que precisa el apoyo.

Según recoge dicha sentencia, “la aplicación del régimen de la anulabilidad viene respaldada ahora por el tenor del art. 61 de la Ley 15/2015, de 2 de julio, de la jurisdicción voluntaria [COMPLETAR], que se refiere literalmente a la tramitación del expediente en los casos en que el representante legal “necesite autorización o aprobación judicial para la validez de actos de disposición”. Aunque se trate de una norma de procedimiento con pretensión de aplicarse en todos los Derechos civiles españoles (disp. final vigésima), entre los que se encuentran el aragonés y el catalán, que expresamente establecen como consecuencia de la falta de autorización necesaria la anulabilidad, el texto refuerza la calificación del acto realizado por el tutor como inválido”.

Por tanto, descartada la nulidad absoluta por su falta de adecuación a la protección de los intereses de los menores y personas con la capacidad modificada judicialmente, para dar solución a los actos celebrados por el representante legal sin autorización judicial resulta necesario acudir, con las adaptaciones precisas, a la anulabilidad:

Según la jurisprudencia, es de aplicación el régimen de los arts. 1300 y siguientes del Código Civil, viéndose mi representado obligado a ejercitar la acción en defensa de los intereses de la persona que precisa apoyo, por cuanto que el precio de venta pactado fue muy inferior al valor de mercado del inmueble, resultando innecesaria la enajenación a la vista de la solvencia patrimonial de la persona con discapacidad, lo cual explica asimismo que no se recabara la preceptiva autorización judicial por la anterior tutora, puesto que difícilmente pudiera haberse obtenido en estas circunstancias.

A efectos acreditativos, acompañamos como documento número [Nº DE DOCUMENTO], dictamen de tasación pericial del inmueble, elaborado por el perito tasador Sr/Sra [COMPLETAR], de donde se desprende indudablemente que el precio pactado fue notoriamente inferior al de valor de tasación, con una diferencia de [IMPORTE] euros.

Actualmente, tras la reforma de la Ley 8/2021, de 2 de junio, la acción está sujeta al plazo de cuatro años que computa desde la celebración del contrato, según lo dispuesto en el art. 1301 del CC, que en este caso no han transcurrido desde la celebración de la compraventa, tal como ha quedado expuesto.

CUARTO.- La pretensión que se sostiene es la de declaración de nulidad del contrato de compraventa con las consecuencias inherentes, en aplicación de lo dispuesto en el art. 1303 del Código Civil, debiendo las partes restituirse recíprocamente sus prestaciones, de modo que esta parte deberá devolver el precio recibido y los demandados entregar el inmueble a mi representado en el estado libre de cargas en que se produjo la venta con sus frutos.

No procede el abono de intereses sobre el precio recibido por parte de la persona que precisa del apoyo, por cuanto que el art. 1304 del CC establece que no será aplicable a los casos de nulidad procedente de haber prescindido de las medidas de apoyo establecidas cuando fueran precisas, siempre que el contratante con derecho a la restitución fuera conocedor de la existencia de medidas de apoyo en el momento de la contratación o se hubiera aprovechado de otro modo de la situación de discapacidad obteniendo de ello una ventaja injusta, como sucede en este caso en que el inmueble se compró a un precio muy inferior al de mercado y los compradores eran conocedores que adquirían el inmueble sin la preceptiva autorización judicial, según consta expresamente en la escritura de compraventa, al haber sido advertidos por el/la Sr./a Notario/a actuante.

A fin de evitar el ejercicio de esta acción, mi representado requirió a los demandados para que procedieran a devolver las prestaciones de forma amistosa, los cuales han hecho caso omiso a este requerimiento, lo que nos obliga a entablar la acción judicial (acompaño como documentos número [Nº DE DOCUMENTO] burofax y acuse de recibo de fecha [FECHA]).

Por todo ello, solicitamos la nulidad de la compraventa, con las consecuencias inherentes.

QUINTO.- Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

PRIMERO.- Competencia.- Corresponde a los Tribunales de [LOCALIDAD], de conformidad a lo dispuesto en los arts. 50 y 52 LEC, en relación con lo dispuesto en el art. 85.1º LOPJ.

SEGUNDO.- Legitimación.- Le corresponde la activa a esta parte ante su condición de curador de la persona que precisa apoyo, lo que le faculta a ejercer la acción en su nombre tras obtener la autorización judicial, en tanto que la pasiva corresponde a los demandados compradores.

TERCERO.- Procedimiento.- Es el procedimiento ordinario, con fundamento en el art. 249.2 LEC dado el valor del inmueble es de [IMPORTE] €, que excede de los 15.000 euros, por lo que deben seguirse las normas del juicio ordinario.

CUARTO.- Plazo. El art. 1301 del CC establece: “La acción de nulidad caducará a los cuatro años. Ese tiempo empezará a correr (…) 4.º Cuando la acción se refiera a los contratos celebrados por personas con discapacidad prescindiendo de las medidas de apoyo previstas cuando fueran precisas, desde la celebración del contrato”.

QUINTO.- Cumplimiento de los requisitos de procedibilidad: La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

SEXTO.- Acción ejercitada: Nulidad de la compraventa. El art. 1300 del CC establece: “Los contratos en que concurran los requisitos que expresa el artículo 1.261 pueden ser anulados, aunque no haya lesión para los contratantes, siempre que adolezcan de alguno de los vicios que los invalidan con arreglo a la ley”. Por su parte, el vigente art. 287.2º del CC, y en los mismos términos el precedente art. 271 del CC, en su redacción anterior a la reforma operada por Ley 8/2021, establece: El curador que ejerza funciones de representación de la persona que precisa el apoyo necesita autorización judicial para los actos que determine la resolución y, en todo caso, para los siguientes: (..) 2.º Enajenar o gravar bienes inmuebles, establecimientos mercantiles o industriales, bienes o derechos de especial significado personal o familiar, bienes muebles de extraordinario valor, objetos preciosos y valores mobiliarios no cotizados en mercados oficiales de la persona con medidas de apoyo, dar inmuebles en arrendamiento por término inicial que exceda de seis años, o celebrar contratos o realizar actos que tengan carácter dispositivo y sean susceptibles de inscripción. Se exceptúa la venta del derecho de suscripción preferente de acciones. La enajenación de los bienes mencionados en este párrafo se realizará mediante venta directa salvo que el Tribunal considere que es necesaria la enajenación en subasta judicial para mejor y plena garantía de los derechos e intereses de su titular”.

Como indica la citada STS núm. 2/2018, de 10 de enero de 2018, rec. 2111/2015, la finalidad de la exigencia de autorización judicial para los actos realizados por el tutor no era, en la tradición jurídica del Código civil, ni lo es en la actualidad, la de complementar la capacidad de quien no la tiene plenamente reconocida por el ordenamiento. Se dirige, por el contrario, a garantizar que los actos realizados por el tutor y que pueden comprometer de manera importante la entidad del patrimonio del tutelado se realicen en su interés. Más allá del control genérico de los informes periódicos o de la rendición de cuentas, se trata de que el juez pueda ponderar la necesidad, la conveniencia o la oportunidad de celebrar actos de transcendencia económica y de que los mismos se celebran en beneficio del tutelado, atendiendo a sus circunstancias personales pero también a criterios objetivos, de lo que con arreglo a un criterio razonable de una persona media puede considerarse útil o no, atendiendo además al momento en el que se realiza el acto. En consecuencia, la falta de este requisito determina la nulidad del contrato.

SÉPTIMO.- Efectos de la nulidad. Son de aplicación los arts. 1303 y 1304 del CC. El art. 1303 CC establece: “Declarada la nulidad de una obligación, los contratantes deben restituirse recíprocamente las cosas que hubiesen sido materia del contrato, con sus frutos, y el precio con los intereses, salvo lo que se dispone en los artículos siguientes”. Por su parte, el art. 1304 del CC establece: “Cuando la nulidad proceda de la minoría de edad, el contratante menor no estará obligado a restituir sino en cuanto se enriqueció con la prestación recibida. Esta regla será aplicable cuando la nulidad proceda de haber prescindido de las medidas de apoyo establecidas cuando fueran precisas, siempre que el contratante con derecho a la restitución fuera conocedor de la existencia de medidas de apoyo en el momento de la contratación o se hubiera aprovechado de otro modo de la situación de discapacidad obteniendo de ello una ventaja injusta”.

OCTAVO. En materia de costas el art. 394 LEC señala que las de primera instancia se imponen a la parte que vea en primera instancia rechazadas sus pretensiones.

Con base en lo anterior,

SUPLICO AL TRIBUNAL que tenga por presentada la presente demanda, con el dictamen pericial y los documentos a ella adjuntos, por parte en la representación que ostento, y tras la pertinente tramitación se dicte por ese Tribunal sentencia por la que se declare la nulidad del contrato de compraventa de fecha [FECHA], con los efectos inherentes, condenado a los demandados a estar y pasar por dicha declaración, con obligación de entrega del inmueble libre de cargas, dejándola a disposición de mi representado, con simultánea devolución del precio sin intereses por parte de la actora, y todo ello con imposición de costas a la parte demandada.

OTROSÍ PRIMERO DIGO que se fija la cuantía del presente procedimiento en [IMPORTE] euros.

Por lo que, SUPLICO AL TRIBUNAL se tenga por efectuada la anterior manifestación a los efectos pertinentes.

OTROSÍ SEGUNDO DIGO que se acompaña en anexo relación de documentos e informe pericial presentados, debidamente foliados y con índice electrónico, para su debida localización y consulta.

Por lo que, SUPLICO AL TRIBUNAL tenga hecha esta manifestación a los efectos oportunos y por aportados los documentos e informe pericial relacionados en el anexo.

 a [DÍA] de [MES] de [AÑO]

Firma Abogado Firma Procurador
