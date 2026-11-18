---
name: oposicion-apelacion-sobre-clausula-suelo-155
description: "Redacta el escrito «Oposición a la apelación sobre cláusula suelo» (formulario 155 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición a la apelación sobre cláusula suelo

> Formulario 0155 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] NÚMERO
- [ ] ACTO O RESOLUCIÓN
- [ ] FECHA (4 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… procesal de la LO 1/2025. A LA SALA Don»; «…ula controvertida, es decir, la cláusula»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 3 TRLGDCU
- art. 82.1 TRLGDCU
- art. 82.3 TRLGDCU
- art. 1.285 CCiv
- arts. 85 a 90 TRLGDCU
- art. 218 LEC
- arts. 1.101 y 1.303 CCiv
- art. 1.303 CCiv
- Ley 34/1984

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

### Formulario 0155 · Oposición a la apelación sobre cláusula suelo

- Año del modelo: 2021
- Revisión 17-11-2026: 10 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Oposición al recurso de apelación frente a la sentencia sobre cláusula suelo.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SALA

Don [COMPLETAR], Procurador de los Tribunales, actuando en nombre de [NOMBRE DEL REPRESENTADO/A], cuya representación tengo acreditada en los autos de juicio ordinario, seguidos con el nº [NÚMERO] contra [ACTO O RESOLUCIÓN], ante el Tribunal comparezco, y como mejor proceda en derecho, DIGO:

Que por diligencia de ordenación de fecha [FECHA] fui emplazado por término de diez días para formular OPOSICIÓN AL RECURSO DE APELACIÓN interpuesto de contrario, frente a la sentencia de fecha [FECHA], recaída en las presentes actuaciones, lo que hago por medio del presente escrito en el que expongo las siguientes:

ALEGACIONES

En primer lugar, mostramos nuestra absoluta conformidad con la resolución dictada por el tribunal al que gustosamente nos dirigimos y, por lo tanto, nos oponemos al recurso de apelación interpuesto de contrario.

Las razones de nuestra oposición al recurso son las que a continuación se exponen.

PRIMERA. Inexistencia de error del juzgador en la valoración de la prueba practicada.

La apelante pretende sustituir el fundado e imparcial criterio del Juzgador de instancia por el suyo propio, sin aportar argumento alguno que permita llegar a las conclusiones que pretende, pues durante la tramitación del presente procedimiento quedaron perfectamente demostradas las pretensiones formuladas por esta parte.

En síntesis, el recurso vuelve a reiterar en esta alzada lo discutido durante la instancia, alegando que la sentencia dictada en los presentes autos yerra, en la valoración de la prueba practicada, al considerar que la cláusula suelo declarada nula supera el control de transparencia, a la luz de la doctrina jurisprudencial.

Esta alegación no se fundamenta en el resultado de prueba alguna practicada en estos autos. Es más, la recurrente realiza una serie de afirmaciones, considerándolos hechos probados, sin que las mismas tengan sustento probatorio de ningún tipo.

Pues bien, lo cierto es que la citada cláusula contractual constituye una condición general de la contratación de carácter abusivo, al tratarse de una cláusula no negociada individualmente, incorporada de manera generalizada por la entidad bancaria demandada en sus contratos de préstamo hipotecario, que transgrede en principio de buena fe contractual al ocasionar en detrimento del cliente un desequilibrio de las obligaciones contractuales injustificado y favorable para una sola de las partes, en este caso la entidad bancaria demandada.

En primer lugar, cabe subrayar que mi mandante es un consumidor incluido en el ámbito del art. 3 TRLGDCU, el cual fija el concepto de consumidor al indicar, en su apartado 1, que: "A efectos de esta norma y sin perjuicio de lo dispuesto expresamente en sus libros tercero y cuarto, son consumidores o usuarios las personas físicas que actúen con un propósito ajeno a su actividad comercial, empresarial, oficio o profesión. Son también consumidores a efectos de esta norma las personas jurídicas y las entidades sin personalidad jurídica que actúen sin ánimo de lucro en un ámbito ajeno a una actividad comercial o empresarial". En este supuesto, ha quedado acreditado que mi representado concertó el préstamo para la adquisición de su vivienda habitual, por lo que actúa fuera del ámbito propio de su actividad profesional.

En segundo lugar, y en este ámbito de aplicación, el art. 82.1 TRLGDCU dispone que "Se considerarán cláusulas abusivas todas aquellas estipulaciones no negociadas individualmente y todas aquellas prácticas no consentidas expresamente que, en contra de las exigencias de la buena fe causen, en perjuicio del consumidor y usuario, un desequilibrio importante de los derechos y obligaciones de las partes que se deriven del contrato". Partiendo de este precepto, como ha indicado reiteradamente la jurisprudencia, el concepto de cláusula abusiva se puede centrar en aquella estipulación que no habiéndose negociado individualmente o consentido expresamente, causa, en contra de las exigencias de la buena fe y en detrimento del consumidor, un desequilibrio importante entre los derechos y obligaciones de las partes derivados del contrato, debiendo citarse en este sentido el art. 3.1 de la Directiva 93/13, a lo que es preciso añadir que el carácter abusivo de una cláusula se apreciará teniendo en cuenta la naturaleza de los bienes o servicios objeto del contrato y considerando todas las circunstancias concurrentes en el momento de su celebración, así como todas las demás cláusulas del contrato o de otro del que este dependa (art. 82.3 TRLGDCU), lo que debe implicar un llamamiento a una interpretación judicial del contrato, al amparo del art. 1.285 CCiv, guiada por los parámetros de la buena fe, atendiendo a las circunstancias concurrentes y en base a criterios sistemáticos, y sin olvidar la regla interpretativa "contra proferentem" que impide que una cláusula oscura se interprete a favor del predisponente. En todo caso se considerarán cláusulas abusivas las contempladas en el catálogo sito en el art. 82.4 y desarrollado en los arts. 85 a 90 TRLGDCU.

En este caso, la entidad bancaria fijó unilateralmente la cláusula del contrato, sin que mi representado tuviera una oportunidad real alguna de negociar los términos de su contrato y en particular la rebaja o supresión de la mencionada cláusula, sin que en el contrato de préstamo exista algún tipo de contrapartida que, consensuadamente, equilibrara el claro desequilibrio que genera la cláusula suelo, en especial, la fijación de una cláusula techo semejante, respetando así el principio de reciprocidad en que se asienta el equilibrio de derechos y obligaciones. Por tanto, mediante esta cláusula y sin contrapartida, la entidad demandada obtiene con el tipo de interés variable que establece como condición general de la contratación una posición más ventajosa objetivamente, en relación con mi representado que no goza en modo alguno de protección en caso de una variación al alza del índice de referencia, o de otras ventajas que compensen ese mínimo establecido a favor de la entidad bancaria.

Finalmente, se trata de una cláusula no transparente, que genera un desequilibrio contrario a las exigencias de la buena fe en perjuicio de los prestatarios, por lo que se dan las condiciones de ilicitud requeridas por el art. 8 LCGC para la nulidad de la cláusula predispuesta en un contrato de consumidores de techo/ suelo de intereses remuneratorios.

En definitiva, el juicio realizado por el juzgador a quo en orden a que la cláusula suelo, cuya nulidad se declara, no supera el control de transparencia, se adecúa a la jurisprudencia del Tribunal Supremo glosada en el sentencia recurrida.

Por todo lo expuesto precedentemente, no puede por menos que concluirse que esta parte comparte la conclusión que se alcanza en la sentencia dictada en la instancia de que la cláusula controvertida, es decir, la cláusula [COMPLETAR], relativa a limitaciones al tipo de interés variable a aplicar en el contrato de préstamo hipotecario concertado entre los litigantes en fecha [FECHA], ha de estimarse nula, y como tal ha de ser declarada.

SEGUNDA. De la condena al reintegro de las cantidades indebidamente abonadas como efecto legal derivado de la declaración de nulidad. Ausencia de incongruencia

Cuestiona la entidad apelante la condena que le ha sido impuesta al abono de las cantidades indebidamente abonadas que conlleva la declaración de nulidad de la citada cláusula.

En este sentido, no vulnera tampoco la sentencia recurrida, como alega el recurrente, el principio de congruencia, dispuesto en el art. 218 LEC, dado que, como ha declarado el Tribunal Supremo, "el control de abusividad de la cláusula no negociada en un contrato celebrado con un consumidor, en el que se inserta el control de transparencia, lleva consigo la nulidad de la cláusula controvertida, la pervivencia del contrato sin esa cláusula y la restitución de lo que el predisponente haya percibido como consecuencia de la aplicación de la cláusula abusiva" (STS 367/2017, de 8 de junio de 2017).

Asimismo, siendo la cláusula nula, debe procederse a la devolución de lo abonado en su virtud, de conformidad con lo dispuesto en los arts. 1.101 y 1.303 CCiv.

Respecto a este extremo, la STS, Sala Primera, de lo Civil, Pleno, 241/2013, de 9 de mayo de 2013, vino a declarar la irretroactividad de la declaración de nulidad, y consecuentemente la improcedencia de devolver a los consumidores prestatarios las cantidades cobradas en aplicación de la cláusula suelo, en cuanto ejercitada una acción colectiva de cesación de condición general de contratación, ésta tiene carácter declarativo, y no puede contener una condena a devolver lo cobrado de más. Esto generó cierta confusión, porque se entendió que ello no quería decir que el cliente que vio cómo la cláusula de su contrato se declaraba nula en dicho escenario, no pudiera reclamar la cantidad correspondiente, en un procedimiento aparte; ni, desde luego, que el cliente no pudiera reclamar tales cantidades en una acción individual de nulidad como la que aquí se ejercita. No obstante, para el Alto Tribunal no resultaba trascendente en este punto el que se tratara de una acción colectiva o de una individual, puesto que el conflicto jurídico es el mismo, y ante las respuestas dispares por parte de los Tribunales en cuanto a la devolución o no de las cuotas percibidas por las entidades prestamistas en aplicación de la cláusula suelo declarada abusiva, la STS, Sala Primera, de lo Civil, Pleno, 139/2015, de 25 de marzo de 2015, con el voto particular de dos magistrados, clarificó su doctrina declarando que los efectos de restitución derivados de la declaración de nulidad de la cláusula se extenderán a los pagos de intereses efectuados en aplicación de ella posteriores a la fecha de publicación de la sentencia de 9 de mayo de 2013.

Sin embargo, el TJUE en sentencia de 21 de diciembre de 2016 determina que esa limitación temporal impuesta por el TS es incompatible con el Derecho europeo, declarando que el carácter abusivo de una cláusula debe tener como consecuencia el restablecimiento de la situación en la que se encontraría el consumidor de no haber existido dicha cláusula, lo que supone la restitución íntegra de las cantidades que se hayan abonado indebidamente a la entidad bancaria sobre la base de la cláusula. Se trata, en definitiva, de llevar a la práctica lo dispuesto en el art. 1.303 CCiv, restituir las prestaciones recíprocas que hubieran sido objeto del contrato, o, en este caso, de la parte del contrato declarado nulo, aplicando el efecto disuasorio que impone la Directiva 93/13 al empresario que utiliza, de manera generalizada, cláusulas abusivas, al objeto de evitar que se reiteren en el futuro. Y en supuestos como el presente sólo se habían generado prestaciones en favor de la entidad demandada, dado que la cláusula techo no había entrado en funcionamiento (precisamente, la imposibilidad de que lo hiciera era uno de los argumentos esgrimidos), habiéndose generado un enriquecimiento injusto en favor de la entidad bancaria, que debía ser resarcido.

TERCERA. De la procedencia de la condena en costas a la entidad recurrente.

Recurre el banco demandado la condena en costas que impone la sentencia recurrida, como consecuencia lógica de la íntegra estimación de nuestra demanda.

La Sala Primera del Tribunal Supremo, en sentencia del Pleno nº 419/2017, de 4 de julio, ha declarado que procede la imposición de costas de las instancias, dada la concurrencia de los principios de vencimiento, no vinculación del consumidor a las cláusulas abusivas y efectividad del derecho comunitario. En este sentido, declara la citada sentencia que:

"Pues bien, en virtud de todas las anteriores consideraciones esta sala considera que el criterio más ajustado al principio de no vinculación del consumidor a las cláusulas abusivas y al principio de efectividad del Derecho de la Unión es que las costas de las instancias en casos similares al presente se impongan al banco demandado. Las razones en que se concretan esas consideraciones son las siguientes: »1.ª) El principio del vencimiento, que se incorporó al ordenamiento procesal civil español, para los procesos declarativos, mediante la reforma de la Ley de Enjuiciamiento Civil, por la Ley 34/1984, de 6 de agosto, es desde entonces la regla general, pues se mantuvo en el art. 394.1 de la vigente Ley de Enjuiciamiento Civil de 2000, de modo que la no imposición de costas al banco demandado supondría en este caso la aplicación de una salvedad a dicho principio en perjuicio del consumidor.

»2.ª) Si en virtud de esa salvedad el consumidor recurrente en casación, pese a vencer en el litigio, tuviera que pagar íntegramente los gastos derivados de su defensa y representación en las instancias, o en su caso de informes periciales o pago de la tasa, no se restablecería la situación de hecho y de derecho a la que se habría dado si no hubiera existido la cláusula suelo abusiva, y por tanto el consumidor no quedaría indemne pese a contar a su favor con una norma procesal nacional cuya regla general le eximiría de esos gastos. En suma, se produciría un efecto disuasorio inverso, no para que los bancos dejaran de incluir las cláusula suelo en los préstamos hipotecarios sino para que los consumidores no promovieran litigios por cantidades moderadas.

»3.ª) La regla general del vencimiento en materia de costas procesales favorece la aplicación del principio de efectividad del Derecho de la Unión y, en cambio, la salvedad a dicha regla general supone un obstáculo para la aplicación de ese mismo principio".

CUARTA. Desestimación del recurso.

A la vista de las anteriores consideraciones, entendemos que debe procederse a la íntegra desestimación del recurso interpuesto de contrario, con la confirmación de la sentencia dictada en la instancia y la expresa imposición a la apelante de las costas causadas.

En virtud de lo expuesto,

SUPLICO A LA SALA

que se tenga por presentado este escrito, a fin de que sea unido a las actuaciones, y se tenga por formulada oposición al recurso de apelación formulado de contrario contra la resolución de fecha [FECHA], de manera que tras los trámites que resulten de rigor, dicte nueva sentencia por la que, desestimando el mencionado recurso, se confirme íntegramente la dictada en su día por el Juzgador de Instancia, con expresa imposición de las costas causadas en la alzada.

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del Abogado

Firma del Procurador
