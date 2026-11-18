---
name: ampliar-ejecucion-impago-pensiones-proceso-matrimonial-218
description: "Redacta el escrito «Ampliar la ejecución por impago de pensiones en proceso matrimonial y embargar bienes» (formulario 218 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Ampliar la ejecución por impago de pensiones en proceso matrimonial y embargar bienes

> Formulario 0218 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO (2 veces)
- [ ] SEDE (2 veces)
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] Nº
- [ ] AÑO
- [ ] LOCALIDAD
- [ ] FECHA (7 veces)
- [ ] IMPORTE (10 veces)
- [ ] Otros 16 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…, y bajo la dirección Letrada de Don»; «…numeración del juzgado de procedencia).]»; «…ia firme en el periodo comprendido entre»; «…e la obligación del ahora ejecutado, Don»; «…l periodo comprendido entre los meses de»; «…a»; «…referencia, habiendo vencido un total de»; «…cutado, progenitor y padre del menor Don»; «…numeración del juzgado de procedencia).]»; «…l periodo comprendido entre los meses de»; «…iento: - + Añadir más párrafos iguales –»; …

## Párrafos opcionales (2)

Inclúyelos solo si encajan en los hechos:

- OTROSÍ DIGO: Que en cumplimiento de lo previsto en el artículo 549.1.3º de la Ley de Enjuiciamiento Civil, est…
- OTROSÍ DIGO: Que no considerando suficientes los bienes señalados para el fin de la ejecución, esta parte inte…

## Correcciones de la revisión (5)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 776.1 de la LEC
- artículo 548 de la LEC
- art. 24 de la CE
- artículo 578 de la LEC
- art. 578.3 de la LEC
- artículo 711 de la LEC
- art. 539.2 de la LEC

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

### Formulario 0218 · Ampliar la ejecución por impago de pensiones en proceso matrimonial y embargar bienes

- Año del modelo: 2020
- Revisión 17-11-2026: 5 citas normativas corregidas tras comprobarlas en el BOE; 2 párrafos opcionales señalados; 42 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Procedimiento de ejecución número [Nº DE PROCEDIMIENTO]

A LA SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D/Dª [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en nombre y representación de D/Dª [NOMBRE Y APELLIDOS], conforme tengo debidamente acreditado en autos de proceso de divorcio número [Nº]/[AÑO] procedimiento de ejecución número [Nº DE PROCEDIMIENTO], promovido por mi principal contra D/Dª [NOMBRE Y APELLIDOS], y bajo la dirección Letrada de Don [COMPLETAR], ante la Sección de Familia, Infancia y Capacidad del Tribunal [NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).] de Instancia de [LOCALIDAD], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. «De los de» es residuo de los varios juzgados de una plaza. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] comparezco y, como mejor proceda en Derecho, DIGO:

Que habiéndose mantenido la situación de impago por el ejecutado de las pensiones a que viene condenado por sentencia firme en el periodo comprendido entre [COMPLETAR], con posterioridad al auto despachando ejecución de fecha [FECHA], por medio del presente escrito y en la indicada representación solicito la AMPLIACIÓN DE LA EJECUCIÓN por vencimiento de nuevas obligaciones en el citado periodo por importe de [IMPORTE] euros de principal y de [IMPORTE] euros, presupuestados para intereses y costas, al amparo de lo dispuesto en los artículos 517 y ss. de la Ley de Enjuiciamiento Civil, así como que se proceda al embargo de bienes y se adopten las medidas específicas de ejecución forzosa que se dirán, en base a los siguientes

Hechos

Primero.– Que en los presentes Autos se dictó Sentencia, la cual adquirió firmeza en fecha [FECHA], en virtud de la cual se establece la obligación del ahora ejecutado, Don [COMPLETAR], progenitor del hijo menor, a satisfacer en concepto de pensión de alimentos al menor la cantidad de [IMPORTE] euros mensuales, pagaderos dentro de los cinco primeros días de cada mes, en la cuenta designada y que consta en sentencia, cantidad que será revisable anualmente en función de la variación que experimente el índice de precios al consumo.

Segundo.– En fecha [FECHA] se despachó ejecución por importe de [IMPORTE] euros de principal y de [IMPORTE] euros, presupuestadas por intereses y costas, ante el impago del demandado por el periodo comprendido entre los meses de [COMPLETAR] a [COMPLETAR].

Tercero.– Que desde que se dictó el auto despachando ejecución y hasta la fecha, el ejecutado no ha abonado ninguna cantidad en concepto de alimentos a los que viene condenado por la sentencia firme de referencia, habiendo vencido un total de [COMPLETAR] mensualidades por importe total de [IMPORTE] euros, según desglose que se acompaña como documento número 1 con las correspondientes actualizaciones.

Cuarto.– Pese a las reiteradas gestiones realizadas por mi principal y esta representación a fin y efecto de que el ejecutado abonara el importe fijado en la sentencia en concepto de pensión de alimentos para el hijo menor, a día de hoy, no se ha abonado cantidad alguna, habiendo recibido esta representación comunicación del Tribunal al que me dirijo en fecha [FECHA], en la cual se hacen constar relación de bienes del ejecutado, cuya traba se interesa desde este momento, instando asimismo la mejora de embargo a efectos de cubrir las responsabilidades por las que se amplía la ejecución, además de instar la imposición de multas coercitivas conforme al art. 776.1 de la LEC, según se expone seguidamente.

Quinto.– Que el ejecutado, progenitor y padre del menor Don [COMPLETAR] de forma reiterada y persistente está incumpliendo la obligación impuesta en virtud de la sentencia que se ejecuta y cuya ampliación se solicita, consistente en el pago mensual de [IMPORTE] euros en concepto de pensión de alimentos para el hijo menor.

Que desde que ha adquirido firmeza la sentencia que establece la obligación al progenitor de abonar el citado importe por el concepto indicado, y pese a las gestiones de mi principal, madre del hijo en común menor de edad, su actitud ha sido de total y completa despreocupación, por no mejor decir que se obstina en no pagar por el mero hecho de perjudicar a la madre del menor.

Que en la actualidad no ha ingresado en la cuenta consignada en el Tribunal cantidad alguna, por lo que adeuda un total de cinco mensualidades, todo ello sin perjuicio de que por su actitud mucho nos tememos que no tiene intención o propósito de realizar ingreso alguno en el futuro, por lo que se solicita que se adopten las medidas de ejecución específicas y se impongan las multas coercitivas correspondientes conforme establece el art. 776.1ª de la LEC.

A los anteriores hechos, son de aplicación los siguientes

Fundamentos de derecho

Primero.– Competencia

Artículo 545.1 LEC. La competencia es de la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] ante el cual se formula esta demanda, por ser el que conoció del asunto en primera instancia.

Segundo.– Procedimiento

Artículo 549 LEC, en relación con el que debe ser el contenido de la demanda ejecutiva, y artículos 551 y ss., y art. 776 y concordantes de la LEC, en cuanto al despacho de ejecución.

Son de aplicación, asimismo: artículo 548 de la LEC: No se despachará ejecución dentro de los veinte días posteriores a aquel en que la resolución de condena sea firme. La demanda se presenta transcurrido este plazo. Art. 550 de la LEC exime de la obligación de presentar el título cuando la ejecución se funde en resolución que obre en los autos

Tercero.– Tutela ejecutiva que se pretende

Se pretende la ampliación de la ejecución de la sentencia para el cumplimiento del pronunciamiento firme condena firme con amparo en el artículo 517.2.1º de la LEC. La ejecución de la sentencia forma parte esencial de la función jurisdiccional, pues a los Tribunales no sólo les corresponde juzgar, es decir, declarar el derecho aplicable al caso concreto (proceso de declaración), sino también hacer ejecutar lo juzgado (proceso de ejecución), y ello con carácter exclusivo y excluyente, formando parte integrante del art. 24 de la CE el derecho a la ejecución de la sentencia en sus propios términos.

El artículo 578 de la LEC permite solicitar en este momento la ampliación de la ejecución a los plazos que vayan venciendo de la deuda, siempre que se presente, como hacemos en la fundamentación fáctica, una liquidación final de la deuda que incluya los vencimientos de principal e intereses producidos durante la ejecución. Resultando esta ejecución conforme con el título ejecutivo, como es el caso, el auto en el que se despache ejecución advertirá al ejecutado de que la ejecución se entenderá ampliada automáticamente si a las fechas de vencimiento no se hubieran consignado a disposición del Tribunal las cantidades correspondientes y de que el pago a esta parte se hará conforme a la liquidación que en este momento presentamos.

Cuarto.– Actos de ejecución que se solicitan

Se insta la materialización del embargo sobre los bienes titularidad del ejecutado que figuran en la relación comunicada por el Tribunal al que nos dirigimos, y la mejora de embargo conforme al art. 578.3 de la LEC

Quinto.– Imposición de multas coercitivas

Que ante el incumplimiento reiterado del progenitor de las obligaciones de pago de las cantidades que le corresponden, y sin perjuicio de hacer efectivas sobre su patrimonio las cantidades debidas y no satisfechas, es por lo que con arreglo a lo dispuesto en el artículo 776.1.ª de la Ley de Enjuiciamiento Civil se interesa la imposición de multas coercitivas, que dada la actitud del progenitor se considera más que justificado se acuerden en su importe máximo, por lo que de conformidad con los porcentajes permitidos en el artículo 711 de la LEC.

Sexto.– Costas procesales

Es de aplicación lo dispuesto en el art. 539.2 de la LEC en relación a las costas y gastos de la ejecución.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con el documento que acompaño y copia de todo ello, admita a trámite la presente demanda de ampliación de ejecución de la sentencia de fecha [FECHA] dictada en estos autos contra D./Dña. [NOMBRE Y APELLIDOS], la admita a trámite y acuerde lo siguiente:

1.º Que se dicte auto de orden general de ejecución despachando ésta, en el que amplíe la ejecución decretada en auto de fecha [FECHA] por el principal de [IMPORTE] euros y otros [IMPORTE] euros que, por el momento y sin perjuicio de ulterior liquidación, se consideran bastantes para intereses, gastos y costas, por las pensiones impagadas correspondientes al periodo comprendido entre los meses de [COMPLETAR] al mes de
2.º Que en el mismo día o en el siguiente hábil por el Letrado de la Administración de Justicia:
– Que se proceda a la mejora de embargo para cubrir las cantidades por las que se amplía el despacho de ejecución.
– Que se decrete el embargo de los bienes concretos titularidad del ejecutado que figuran en la relación comunicada por el Tribunal en fecha [FECHA], adoptando las medidas de garantía de la traba previstas legalmente, y que son los siguientes:
3º. Que, previos los trámites legales, se proceda a dictar resolución motivada en la que se acuerdo la imposición de multas coercitivas por incumplimiento de medidas al ejecutado por incumplimiento reiterado de sus obligaciones de pago, solicitándose que se impongan multas mensuales en su importe máximo dada la conducta culpable, reiterada y persistente en el impago, con los apercibimientos correspondientes y sin perjuicio de hacer efectivas sobre su patrimonio las cantidades debidas y no satisfechas.
4º Que se impongan al ejecutado las costas de la ejecución y su ampliación.

OTROSÍ DIGO I: Que para el caso de que el ejecutado, padre y progenitor de los menores, siga en su actitud de no afrontar su obligación de satisfacer el importe de la pensión en concepto de alimentos para el hijo menor, igualmente interesamos que en la resolución que se dicte en forma de Auto se acuerde despachar ejecución contra bienes del demandado y en cantidad suficiente para cubrir la suma de [IMPORTE] euros mensuales que en lo sucesivo se devenguen, así como los réditos que se devenguen durante la ejecución y las costas del proceso, para con su producto dar entero y cumplido pago a mi poderdante de cuantos importes en concepto de principal se acrediten, intereses, gastos y costas, las cuales serán a cargo del ejecutado.

Por lo que,

AL TRIBUNAL SOLICITO: Que tenga por realizada la anterior manifestación, y acuerde de conformidad.

[OPCIONAL — incluir si procede]

OTROSÍ DIGO: Que en cumplimiento de lo previsto en el artículo 549.1.3º de la Ley de Enjuiciamiento Civil, esta parte señala los siguientes bienes del ejecutado susceptibles de embargo, a efectos de que se proceda a la mejora de embargo solicitada, y de los que se tiene conocimiento:

-
+
Añadir más párrafos iguales

– [COMPLETAR]

Por lo que.

AL TRIBUNAL SUPLICO: Que proceda a la mejora de embargo de los bienes del ejecutado que resultan señalados, adoptando las medidas oportunas para la efectividad de dichos embargos.

[OPCIONAL — incluir si procede]

OTROSÍ DIGO: Que no considerando suficientes los bienes señalados para el fin de la ejecución, esta parte interesa se proceda a la adopción de las siguientes medidas de localización e investigación que interese al amparo del artículo 590 de la Ley de Enjuiciamiento Civil y en particular:

a) Dirija mandamiento al Registro de la Propiedad de los de [COMPLETAR] a los fines de que informe a este Tribunal de aquellas fincas o titularidades que resulten en los libros de dicho Registro a nombre del ejecutado, toda vez que esta parte ha tenido conocimiento que es el lugar donde reside en la actualidad, y podría resultar titular de bienes radicados en aquel distrito hipotecario.
b) Se remita oficio a la Agencia Estatal de Administración Tributaria a los fines de que libre certificación y la remita a las presentes actuaciones, en relación con los bienes patrimoniales declarados por el ejecutado en su última declaración fiscal efectuada a los efectos del Impuesto sobre el patrimonio.
-
+
Añadir más párrafos iguales

– [COMPLETAR].

Por lo que,

AL TRIBUNAL SUPLICO: Que teniendo por hechas las anteriores manifestaciones, acuerde de conformidad.

Es de Justicia que insto en [COMPLETAR], [COMPLETAR].

Abogado/a	Procurador/a

Fdo. D./Dña. [NOMBRE Y APELLIDOS]: 	Fdo. D./Dña. [NOMBRE Y APELLIDOS]:
