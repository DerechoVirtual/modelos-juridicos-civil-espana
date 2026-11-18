---
name: demanda-ejecucion-convenio-regulador-matrimonio-mutuo-19
description: "Redacta el escrito «Demanda de ejecución del convenio regulador del matrimonio de mutuo acuerdo» (formulario 19 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de ejecución del convenio regulador del matrimonio de mutuo acuerdo

> Formulario 0019 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] Nº
- [ ] LOCALIDAD
- [ ] NOMBRE Y APELLIDOS (9 veces)
- [ ] NÚMERO (2 veces)
- [ ] FECHA (3 veces)
- [ ] IMPORTE (4 veces)
- [ ] FECHA DEL ACUERDO
- [ ] LUGAR
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…iento: - + Añadir más párrafos iguales –»; «…to al Registro de la Propiedad de los de»; «…z que por ser natural de la población de»; «…io. c) - + Añadir más párrafos iguales –»

## Párrafos opcionales (4)

Inclúyelos solo si encajan en los hechos:

- OTROSÍ PRIMERO DIGO que esta parte comparece con representación y defensa de su elección, interesando, de conf…
- OTROSÍ SEGUNDO DIGO: Que para el caso de que la parte ejecutada siga en su actitud de no afrontar su obligació…
- OTROSÍ TERCERO DIGO: Que en cumplimiento de lo previsto en el artículo 549.1.3º de la Ley de Enjuiciamiento Ci…
- OTROSÍ CUARTO DIGO: Que no considerando suficientes los bienes señalados para el fin de la ejecución, esta par…

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 549.2 de la LEC
- art. 776 de la LEC
- art. 750.2 de la LEC
- artículo 711 de la LEC

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

### Formulario 0019 · Demanda de ejecución del convenio regulador del matrimonio de mutuo acuerdo

- Año del modelo: 2024
- Revisión 17-11-2026: 4 párrafos opcionales señalados; 23 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (FECHA DEL ACUERDO, Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Regulación legal: arts. 549, 750 y 776 de la Ley de Enjuiciamiento Civil

Este formulario desarrolla una demanda ejecutiva por incumplimiento de medidas pactadas en un convenio regulador. Una vez aprobado el convenio en proceso de mutuo acuerdo, cualquiera de las partes puede instar su ejecución forzosa, formulando demanda ejecutiva conforme a lo dispuesto en el art. 549.2 de la LEC, con las especialidades establecidas en el art. 776 de la LEC, en su caso.

La cuestión específica que se plantea es que, si se ha comparecido en el proceso de mutuo acuerdo con una misma representación y defensa, deben observarse las reglas establecidas en el art. 750.2 de la LEC para que cada parte pueda comparecer con su propia representación y defensa, para seguir el proceso de ejecución con todas las garantías de contradicción.

El art. 750.2.II de la LEC establece, para el caso en que a pesar del acuerdo suscrito por las partes y homologado por el Tribunal, una de las partes pida la ejecución judicial de dicho acuerdo, que el Letrado de la Administración de Justicia requerirá a la otra para que nombre abogado y procurador que la defienda y represente.

Formulario revisado conforme a la LO 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Procedimiento de divorcio de mutuo acuerdo núm. [Nº]

AL TRIBUNAL DE [LOCALIDAD]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, actuando en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito por certificación del registro electrónico de apoderamientos judiciales que acompaño, bajo la dirección Letrada de D./Dña. [NOMBRE Y APELLIDOS], comparezco en los autos de procedimiento de divorcio de mutuo acuerdo, seguidos ante el Tribunal al que me dirijo con el número [NÚMERO], habiendo sido parte mi mandante y D./Dña. [NOMBRE Y APELLIDOS], y, como mejor proceda en Derecho, DIGO:

Que por medio del presente escrito y en la indicada representación me veo en la obligación de formular SOLICITUD DE EJECUCIÓN FORZOSA DE MEDIDAS, al amparo de lo dispuesto en los artículos 517, 549.2 y concordantes de la Ley de Enjuiciamiento Civil, con las especialidades previstas en el artículo 776 de la citada ley, en base a los siguientes

Hechos y fundamentos

Primero.– Que en los presentes Autos, seguidos ante ese Tribunal con el número [NÚMERO], ha sido dictada Sentencia de divorcio de mutuo acuerdo, la cual ha adquirido firmeza en fecha [FECHA], en virtud de la cual se aprobó el convenio regulador suscrito por las partes en fecha [FECHA], en cuyo apartado tercero se pactaron una serie de medidas en relación con los hijos, en las que se establece la obligación del ahora ejecutado/a D./Dña. [NOMBRE Y APELLIDOS], progenitor/a del hijo menor, a satisfacer en concepto de pensión de alimentos al menor la cantidad de [IMPORTE]. euros mensuales, pagaderos dentro de los cinco primeros días de cada mes, en la cuenta designada por mi principal y que consta en el convenio regulador, cantidad que será revisable anualmente en función de la variación que experimente el índice de precios al consumo.

Segundo.– El obligado al pago no ha abonado el importe estipulado en el convenio regulador durante los dos últimos meses, estando en adeudar en este momento a mi mandante la cantidad de [IMPORTE] euros.

Tercero.– Que las gestiones realizadas por mi principal y esta defensa a fin y efecto de que el/la progenitora del menor abonara el importe estipulado en el convenio regulador han sido infructuosas, por lo que mi mandante se ve en la obligación de instar la ejecución forzosa del convenio, compareciendo con nueva representación y defensa de su elección, debiendo ser requerido la parte ejecutada a los efectos del art. 750.2 de la LEC, tal como interesamos en el otrosí.

Por lo que,

SUPLICO AL TRIBUNAL: Que teniendo por presentado este escrito y por promovida en la representación que ostento de D./Dña. [NOMBRE Y APELLIDOS] la SOLICITUD DE EJECUCIÓN FORZOSA DE MEDIDAS acordadas en Sentencia firme dictada en los presentes autos de divorcio de mutuo acuerdo en fecha [FECHA DEL ACUERDO].... y, en su virtud, acuerde despachar ejecución contra D./Dña. [NOMBRE Y APELLIDOS], en cantidad suficiente para cubrir la suma de [IMPORTE]. euros, así como las mensualidades que se devenguen durante la ejecución y las costas del proceso, a cuyo efecto por ahora y en forma ponderada se fija la cantidad de [IMPORTE]. euros. Y que, previo requerimiento de pago en legal forma, se proceda al embargo sobre bienes del ejecutado en cantidad bastante para cubrir las cantidades reclamadas y para que, tras los trámites legales oportunos, se proceda a su realización para con su producto dar entero y cumplido pago a mi poderdante de cuanto acredita por principal, intereses, gastos y costas, las cuales serán a cargo del ejecutado, dando a los autos el impulso procesal con arreglo a derecho.

[OPCIONAL — incluir si procede]

OTROSÍ PRIMERO DIGO que esta parte comparece con representación y defensa de su elección, interesando, de conformidad a lo dispuesto en el art. 750.2 de la LEC que se requiera a la parte ejecutada para que nombre abogado y procurador que la defienda y represente, si a su derecho conviniere.

Por lo que, SUPLICO AL TRIBUNAL tenga por hecha la manifestación y acuerde de conformidad.

[OPCIONAL — incluir si procede]

OTROSÍ SEGUNDO DIGO: Que para el caso de que la parte ejecutada siga en su actitud de no afrontar su obligación de satisfacer el importe de la pensión en concepto de alimentos para el hijo menor, se interesa que se aperciba a la parte ejecutada de que podrán imponérsele por el letrado o letrada de la Administración de Justicia multas coercitivas, con arreglo a lo dispuesto en el artículo 711 de la LEC, y sin perjuicio de hacer efectivas sobre su patrimonio las cantidades debidas y no satisfechas.

Por lo que, SUPLICO AL TRIBUNAL tenga por realizada la anterior manifestación, y acuerde de conformidad.

[OPCIONAL — incluir si procede]

OTROSÍ TERCERO DIGO: Que en cumplimiento de lo previsto en el artículo 549.1.3º de la Ley de Enjuiciamiento Civil, esta parte señala los siguientes bienes de la parte ejecutada susceptibles de embargo y de los que se tiene conocimiento:

-
+
Añadir más párrafos iguales

– [COMPLETAR]

Por lo que, SUPLICO AL TRIBUNAL proceda al embargo de los bienes del ejecutado que resultan señalados, adoptando las medidas oportunas para la efectividad de dichos embargos.

[OPCIONAL — incluir si procede]

OTROSÍ CUARTO DIGO: Que no considerando suficientes los bienes señalados para el fin de la ejecución, esta parte interesa se proceda a la adopción de las siguientes medidas de localización e investigación que interese al amparo del artículo 590 de la Ley de Enjuiciamiento Civil y en particular:

a) Dirija mandamiento al Registro de la Propiedad de los de [COMPLETAR] a los fines de que informe a este Tribunal de aquellas fincas o titularidades que resulten en los libros de dicho Registro a nombre del ejecutado, toda vez que por ser natural de la población de [COMPLETAR], donde reside gran parte de su familia, podría resultar titular de bienes radicados en aquel distrito hipotecario.
b) Se remita oficio a la Agencia Estatal de Administración Tributaria a los fines de que libre certificación y la remita a las presentes actuaciones, en relación con los bienes patrimoniales declarados por el ejecutado en su última declaración fiscal efectuada a los efectos del Impuesto sobre el patrimonio.
c)
-
+
Añadir más párrafos iguales

– [COMPLETAR]

Por lo que, SUPLICO AL TRIBUNAL tenga por hechas las anteriores manifestaciones y acuerde de conformidad.

Es de Justicia que insto en [LUGAR], a [FECHA].

Letrado/a	Procurador/a

Fdo. D./Dña. [NOMBRE Y APELLIDOS] 	Fdo. D./Dña. [NOMBRE Y APELLIDOS]
