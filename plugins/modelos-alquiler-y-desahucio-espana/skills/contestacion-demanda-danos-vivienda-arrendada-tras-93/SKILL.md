---
name: contestacion-demanda-danos-vivienda-arrendada-tras-93
description: "Redacta el escrito «Contestación a la demanda por daños en la vivienda arrendada tras el arrendamiento» (formulario 93 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a la demanda por daños en la vivienda arrendada tras el arrendamiento

> Formulario 0093 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

- [ ] NÚMERO
- [ ] SEDE (2 veces)
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] FECHA (5 veces)
- [ ] IMPORTE (2 veces)
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…numeración del juzgado de procedencia).]»; «…enda arrendada, titularidad de la actora»; «…euros, tal como se recoge en la cláusula»; «…o de pago que se acompaña como documento»; «…vienda, que se acompañan como documentos»; «… documentos relacionados en el anexo. En»

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 1561, 1562, 1563 y 1564 del CC

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

### Formulario 0093 · Contestación a la demanda por daños en la vivienda arrendada tras el arrendamiento

- Año del modelo: 2022
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 24 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Proceso ordinario número [NÚMERO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D/Dª [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en la representación que ostento de D/Dª [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], y bajo la dirección Letrada de D/Dª [NOMBRE Y APELLIDOS] ante la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. «De los de» es residuo de los varios juzgados de una plaza. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] en el proceso declarativo arriba expresado comparezco y, como mejor proceda en Derecho, DIGO:

Que habiéndose dado traslado a esta parte de la demanda formulada por D/Dª [NOMBRE Y APELLIDOS], en ejercicio de la acción de reclamación de daños en la vivienda arrendada, titularidad de la actora [COMPLETAR], siguiendo instrucciones de mi poderdante, por medio del presente escrito y en nombre del mismo formulo en tiempo y forma CONTESTACIÓN A LA DEMANDA, oponiéndome a la misma en base a los siguientes

HECHOS

PRIMERO.- Se niegan todos los hechos expuestos en la demanda a excepción de los que se vean aceptados en la presente contestación.

Se acepta la existencia del contrato de arrendamiento aportado como documento número [Nº DE DOCUMENTO] de la demanda y la expiración del plazo el día [FECHA], habiéndose desarrollado normalmente la relación arrendaticia durante todo ese periodo.

En la demanda se omite que mi representada, al formalizar el contrato, depositó como fianza el importe de dos mensualidades de renta, que ascienden a [IMPORTE] euros, tal como se recoge en la cláusula [COMPLETAR] del contrato y se acredita por el recibo de pago que se acompaña como documento [COMPLETAR] de esta contestación.

Esta omisión es relevante, puesto que la actora en ningún momento se refiere a dicha cantidad, que en su caso debería aplicarse al pago de los presuntos daños que reclama, al no haber pendiente ninguna cantidad en concepto de renta, tal como se expondrá posteriormente al alegar la excepción de compensación.

Asimismo, omite que ambas partes convinieron que se efectuaría la entrega de llaves personalmente el día [FECHA] en la vivienda arrendada, y que fue la actora quien manifestó que le era totalmente imposible acudir, por lo que remitió un correo electrónico a mi representada el día anterior para que le depositara las llaves en el vecino del piso cuarto, quien se las haría llegar (acompaño como documento número [Nº DE DOCUMENTO] copia del correo electrónico remitido por la actora en fecha [FECHA]).

Esta omisión de la demandante es absolutamente relevante, puesto que fue la actora quien excusó su presencia personal en la entrega de la vivienda, donde podrían haberse puesto de manifiesto los supuestos daños que ahora reclama, pretendiendo formular una reclamación con base a unas comprobaciones y valoraciones realizadas transcurridos más de dos meses después del efectivo desalojo de la vivienda, como alegamos a continuación.

SEGUNDO.- Se niegan los daños reclamados y asimismo se niega que la situación en que se encontraba la vivienda en el momento de la entrega sea la descrita por la demandante.

La falta de concordancia entre el estado de la vivienda en el momento de la entrega respecto del estado de la vivienda que describe la demandante, se constata del contraste de fechas entre el efectivo desalojo y entrega de llaves, que se produjo el día [FECHA], y la fecha del acta notarial de presencia, que se levanta el día [FECHA], transcurridos más de dos meses desde el efectivo desalojo.

En este periodo intermedio de más de dos meses no se acredita en modo alguno que la vivienda haya estado vacía, de manera que se desconoce qué ha sucedido en la misma, no siendo lógico imputar a mi representada unos daños cuyo conocimiento se manifiesta más de dos meses después, retraso que es únicamente imputable a la arrendadora demandante.

Esta falta de realidad del estado de la vivienda descrito en la demanda se constata por el contraste de las fotografías realizadas por mi representada en el momento del desalojo de la vivienda, que se acompañan como documentos [COMPLETAR].

Dichas fotografías fueron realizadas el día de entrega de llaves y se corresponden con el estado real de la vivienda, constando en cada una de las fotografías la fecha y hora en que fueron efectuadas desde el teléfono móvil de mi representada.

Por tanto, no es de aplicación la jurisprudencia alegada por la parte actora sobre la presunción “iuris tantum” de culpabilidad del arrendatario por el deterioro, pues esta presunción tiene como presupuesto necesario que el arrendador pruebe la existencia de daños en el momento de la entrega, lo cual no se produce en este caso pues han transcurrido más de dos meses desde que se desalojó la vivienda, de modo que no puede entenderse acreditado que los daños reclamados existieran en el momento del desalojo, ni que sean imputables a mi representada, ni mucho menos que se deriven de un mal uso o uso no normal, o incívico por parte de la arrendataria.

TERCERO.- Alegamos asimismo la compensación de deudas, para el caso de que se estimara la existencia de algún daño imputable a mi representada, puesto que mi representada ostenta el crédito derivado de la fianza arrendaticia prestada por importe de dos mensualidades de renta, sin que la demandante haya procedido a su devolución ni haya hecho mención alguna en el escrito de demanda.

En la demanda se reconoce que no existe ninguna cantidad pendiente de pago en concepto de renta arrendaticia, por lo que el único destino de la fianza sería el de resarcir los daños de la vivienda arrendada.

Mi representada niega la existencia de dichos daños, pero en el caso de que se estimaran acreditados, los mismos deben compensarse con el importe satisfecho por mi representada en concepto de fianza arrendaticia, al ser acreedora de la misma una vez finalizado el contrato de arrendamiento.

CUARTO.- Por todo lo expuesto, se solicita la desestimación de la demanda, y para el improbable caso de que se estimara procedente alguna partida, se pretende que la misma se compense con el importe de la fianza arrendaticia de la que es acreedor mi representada, por ser cantidad vencida, líquida y exigible al haber finalizado el contrato.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

PRIMERO.- Competencia, procedimiento y legitimación. Se acepta la competencia y la tramitación de la causa por los tramites del juicio ordinario, así como la legitimación de las partes, en su condición de partes en el contrato de arrendamiento precedente, aceptando asimismo la cuantía de [IMPORTE] euros y asumiendo las alegaciones en este sentido vertidas en el escrito de demanda.

SEGUNDO.- Excepción de compensación. El art. 408.1 de la LECiv establece: “Si, frente a la pretensión actora de condena al pago de cantidad de dinero, el demandado alegare la existencia de crédito compensable, dicha alegación podrá ser controvertida por el actor en la forma prevenida para la contestación a la reconvención, aunque el demandado sólo pretendiese su absolución y no la condena al saldo que a su favor pudiera resultar”.

Alegamos compensación por el importe del crédito derivado de la fianza arrendaticia satisfecha por mi representada, la cual deberá ser compensada en el caso de que se estima alguna deuda contra mi representada por daños en la vivienda arrendada.

TERCERO.- Improcedencia de la acción. Se acepta la aplicación de los arts. 1561, 1562, 1563 y 1564 del CC, de los que resulta la improcedencia de la acción al haber devuelto la vivienda mi representada en el mismo estado en que la recibió.

CUARTO.- Costas. En materia de costas el art 394 LEC, debiendo imponerse a la parte actora.

En base a lo anterior,

SUPLICO AL TRIBUNAL que tenga por presentado este escrito junto con sus copias, teniendo a esta parte por personada en las presentes actuaciones entendiéndose conmigo las siguientes diligencias y por contestada a la demanda interpuesta contra mi principal y, tras la pertinente tramitación y teniendo por opuesta la compensación, se sirva dictar sentencia por la que se desestime la demanda presentada contra mi principal, con imposición de costas a la parte demandante.

OTROSÍ DIGO que se acompaña en anexo relación de documentos e informe pericial presentados debidamente foliados y con índice electrónico para su debida localización y consulta.

Por lo que,

SUPLICO AL TRIBUNAL tenga hecha esta manifestación a los efectos oportunos y por aportados los documentos relacionados en el anexo.

En [COMPLETAR]

Firma Abogado/a y Procurador/a
