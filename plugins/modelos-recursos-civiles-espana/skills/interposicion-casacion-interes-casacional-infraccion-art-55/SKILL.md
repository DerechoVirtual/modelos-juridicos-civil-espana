---
name: interposicion-casacion-interes-casacional-infraccion-art-55
description: "Redacta el escrito «Interposición de casación por interés casacional: infracción del art. 20 LCS (reforma RDL 5/2023)» (formulario 55 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Interposición de casación por interés casacional: infracción del art. 20 LCS (reforma RDL 5/2023)

> Formulario 0055 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] LOCALIDAD (8 veces)
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (14 veces)
- [ ] SEDE (2 veces)
- [ ] IMPORTE (3 veces)
- [ ] NÚMERO
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] LUGAR
- [ ] Otros 18 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…/[AÑO] A LA SECCIÓN»; «…en el Rollo arriba expresado, por la que»; «…– Que la sentencia impugnada, dictada el»; «…por parte de la Sección»; «… esta parte ante la sentencia dictada el»; «…numeración del juzgado de procedencia).]»; «…[COMPLETAR] en los autos»; «… art. 20 de la Ley de Contrato de Seguro»; «…; 2)»; «…lado, en sentencias firmes de la Sección»; «…numeración del juzgado de procedencia).]»; «…ma interpretación se recoge en la SAP de»; …

## Párrafos opcionales (2)

Inclúyelos solo si encajan en los hechos:

- OTROSÍ PRIMERO DIGO que, de conformidad con lo dispuesto en los apartados 3.d) y 6 de la disposición adicional…
- OTROSÍ SEGUNDO DIGO que, de conformidad a lo establecido en el art. 481.6 de la LEC, acompaño como documento n…

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 477.3 de la LEC
- artículo 470.1 de la LEC
- artículo 448.2 de la LEC
- artículo 215.5 LEC
- art. 477.2 LEC
- art. 481.6 de la LEC

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

### Formulario 0055 · Interposición de casación por interés casacional: infracción del art. 20 LCS (reforma RDL 5/2023)

- Año del modelo: 2023
- Revisión 17-11-2026: 3 citas normativas corregidas tras comprobarlas en el BOE; 2 párrafos opcionales señalados; 50 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma orgánica y procesal de la LO 1/2025.

Rollo nº [Nº DE PROCEDIMIENTO]/[AÑO]

A LA SECCIÓN [COMPLETAR] DE LA ILMA. AUDIENCIA PROVINCIAL DE [LOCALIDAD]

[NOTA DE REVISIÓN: Errata. La Audiencia Provincial no cambia de denominación. Fuente: LOPJ arts. 80 y 82 (Audiencia Provincial, sin cambio de denominación).]

D./Dña. [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales, actuando en representación de [NOMBRE DEL REPRESENTADO/A] según viene acreditado en los presentes autos, como mejor proceda en derecho, DIGO:

1) Que en fecha [FECHA] esta parte ha sido notificada de la sentencia de fecha [FECHA] dictada en el Rollo arriba expresado, por la que [COMPLETAR].
2) Que entendiendo que dicha sentencia no es ajustada a derecho, dicho sea con los debidos respetos y en términos de defensa, por medio del presente escrito interpongo contra la misma RECURSO DE CASACIÓN, en base a los siguientes presupuestos de admisibilidad y motivos:

I. Admisibilidad del recurso

Primero.– El presente recurso se deduce contra la sentencia dictada por la Audiencia Provincial en fecha [FECHA], que desestima el recurso de apelación de esta parte.

Segundo.– El cauce de acceso a la casación es el de interés casacional definido en el art. 477.3 de la LEC, puesto que la sentencia recurrida (en cada caso, se concretará el supuesto...) resuelve puntos y cuestiones sobre los que existe jurisprudencia contradictoria de las Audiencias Provinciales

Tercero.– El presente recurso se interpone dentro del plazo de veinte días establecido en el artículo 470.1 de la LEC, computados conforme al artículo 448.2 de la LEC (en su caso, en relación con el artículo 215.5 LEC), habiéndose constituido el depósito para recurrir tal como se expresa en el otrosí de este escrito.

Cuarto.– Que la sentencia impugnada, dictada el [COMPLETAR] por parte de la Sección [COMPLETAR] de la Audiencia Provincial de [LOCALIDAD] en resolución del recurso de apelación presentado por esta parte ante la sentencia dictada el [COMPLETAR] por la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] en los autos [COMPLETAR] se estima que incurre en los siguientes motivos de casación, que se desarrollan a continuación: 1) al amparo del art. 477.3 de la LEC, infracción del art. 20 de la Ley de Contrato de Seguro [COMPLETAR]; 2) [COMPLETAR].

II. Motivos del recurso

Primero.–

Encabezamiento.–

El primer motivo se interpone al amparo de lo dispuesto en el art. 477.3.I de la LEC, al existir jurisprudencia contradictoria de las Audiencias Provinciales, por infracción del art. 20 de la Ley de Contrato de Seguro, el cual resulta vulnerado por cuanto que se hace una interpretación incorrecta del mismo, al aplicar el interés del 20% a todo el periodo de mora una vez transcurridos más de dos años desde el siniestro, cuando el tenor literal del precepto establece que dicho interés de mora del 20% sólo puede aplicarse a partir de los dos años. Existe jurisprudencia contradictoria de las Audiencias Provinciales, de un lado, en la sentencia impugnada y en la sentencia firme de la misma Sección de la AP de [LOCALIDAD] de fecha [FECHA], en las cuales se sostiene la interpretación que se estima errónea, y, de otro lado, en sentencias firmes de la Sección [COMPLETAR] de la AP de [LOCALIDAD] de fecha [FECHA] y de la AP de [LOCALIDAD] de fecha [FECHA], en las cuales se sostiene la interpretación que se estima correcta, pretendiéndose que la Sala fije doctrina estableciendo que el art. 20 LCS dispone que el interés del 20% sólo se devenga una vez transcurridos los dos primeros años del siniestro y, por tanto, en los dos primeros años desde la producción del siniestro se devenga el interés legal incrementado en un 50%.

Desarrollo del motivo.–

El motivo se funda en la infracción del art. 20 de la Ley de Contrato de Seguro, cuya aplicación ha tenido relevancia para el fallo, puesto que el criterio de la sentencia de aplicar el interés del 20% a todo el periodo de mora, desde la producción del siniestro por haber transcurrido más de dos años, supone un incremento de [IMPORTE] euros, en concepto de intereses de mora, que es la que resulta de la diferencia entre la pretensión de esta parte de que se aplicara el interés legal incrementado en un 50% durante los dos primeros años, con la interpretación de la sentencia recurrida, que aplica el interés del 20% a todo el periodo de mora, incluidos los dos primeros años.

El cauce de acceso al recurso es el de interés casacional del art. 477.3 de la LEC, por existir jurisprudencia contradictoria de las Audiencias Provinciales, entendiendo que la sentencia recurrida aplica incorrectamente el art. 20 de la Ley de Contrato de Seguro.

Así, la sentencia recurrida, al estimar el recurso de apelación presentado de contrario contra la sentencia de la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO], de fecha [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], hace una interpretación incorrecta del art. 20 de la LCS al aplicar en un caso como el presente, una vez transcurridos más de dos años desde la producción del siniestro, un interés del 20% desde la fecha del siniestro, y no el legal incrementado en un 50% durante los dos primeros años y el del 20% a partir de esa fecha, lo cual implica una infracción sustantiva justificativa del acceso a la casación con fundamento en el art. 477.2 LEC. Esta misma interpretación se recoge en la SAP de [COMPLETAR], Sección [COMPLETAR], de fecha [FECHA].

El fundamento de la posición que sostiene esta parte se encuentra en la interpretación que se realiza, de forma totalmente contradictoria e incompatible con la de la Sentencia impugnada, por las SAP de [COMPLETAR], Sección [COMPLETAR], de fecha [FECHA], así como por la SAP [COMPLETAR], Sección [COMPLETAR], de fecha [FECHA]. Todas estas sentencias son firmes y se acompañan por copia como documentos número [Nº DE DOCUMENTO].

Para el desarrollo del motivo de impugnación, es necesario partir de los hechos fijados en la sentencia, que no han sido controvertidos, que fijan como día inicial del cómputo de los intereses el día [FECHA], como consecuencia de que el demandante no reclamó a mi representada hasta el día [FECHA], sin que éste tuviera conocimiento del siniestro con anterioridad, lo que determina este término inicial en aplicación de la jurisprudencia uniforme en la materia. El día final, tras las vicisitudes relatadas en la Sentencia impugnada, se fija el día [FECHA], que es el que se realizó el pago, que esta parte no impugna en este recurso extraordinario.

Aceptado por las partes el día inicial y final del cómputo de los intereses, entendemos que es errónea la interpretación que hace la Sentencia impugnada del art. 20.4º de la Ley de Contrato de Seguro, al entender, contrariamente a su tenor literal, que hay un único periodo de mora cuando han transcurrido más de dos años desde la producción del siniestro.

Tal como se refleja en las Sentencias de contraste dictadas por las Audiencias Provinciales de [LOCALIDAD] y de [LOCALIDAD], el art. 20.4º de la LCS distingue dos periodos: el primero, en que la indemnización por mora consiste en el pago de un interés anual igual al del interés legal del dinero vigente en el momento en que se devengue, incrementado en el 50 por 100, que alcanza hasta que se cumplen dos años desde la fecha de producción del siniestro; y el segundo, que se inicia una vez, transcurridos dos años desde la producción del siniestro, donde el interés anual no puede ser inferior al 20 por 100.

Por tanto, los intereses se calculan, durante los dos primeros años, al tipo legal más un 50% y, a partir de ese momento, al tipo del 20% si aquel no resulta superior, lo cual llevaría en nuestro caso a disminuir la indemnización por mora en el importe de [IMPORTE] euros, que es la diferencia entre el tipo de interés del 20% aplicado en el periodo de los dos primeros años y el % que debería haberse aplicado, resultante de incrementar en un 50% el interés legal.

Ante la interpretación contradictoria que se realiza en la sentencia impugnada, solicitamos que se fije la correcta doctrina jurisprudencial sobre el art. 20 LCS, en cuanto al importe de la indemnización por mora, solicitando de la Excma. Sala que establezca que el art. 20.4º de la LCS debe interpretarse en el sentido de que el interés del 20% sólo se devenga una vez transcurridos los dos primeros años del siniestro y, por tanto, en los dos primeros años desde la producción del siniestro se devenga el interés legal incrementado en un 50%.

Es por ello que se pretende, con estimación del recurso de casación y que se case la sentencia, aplicando el interés legal incrementado en un 50% en los dos primeros años desde la producción del siniestro.

Segundo.– [COMPLETAR]

Por lo expuesto,

SUPLICO A LA SALA Que tenga por presentado este escrito con certificación de traslado, se sirva admitirlo y, en su virtud, tenga por interpuesto recurso de casación contra la sentencia de fecha [FECHA] dictada en el Recurso arriba indicado y que se remitan los autos a la Sala Primera del Tribunal Supremo, suplicando a la Excma. Sala estime el recurso de casación interpuesto, casando en parte la sentencia dictada, y acuerde:

1) Fijar como doctrina jurisprudencial que el art. 20.4º de la LCS debe interpretarse en el sentido de que el interés del 20% sólo se devenga una vez transcurridos los dos primeros años del siniestro y, por tanto, en los dos primeros años desde la producción del siniestro se devenga el interés legal incrementado en un 50%.
2) Aplique en el caso el interés legal incrementado en un 50% en los dos primeros años a partir del siniestro, fijando la indemnización a satisfacer por esta parte en la cantidad de [IMPORTE] euros, en concepto de interés de demora.

[OPCIONAL — incluir si procede]

OTROSÍ PRIMERO DIGO que, de conformidad con lo dispuesto en los apartados 3.d) y 6 de la disposición adicional decimoquinta de la LOPJ acompaño a este escrito resguardo de consignación en la cuenta de Depósitos y Consignaciones abierta a nombre del Tribunal del depósito exigido para interponer el recurso por importe de 50 euros.

Por lo que, SUPLICO A LA SALA que tenga por constituido el depósito, dejando interesada desde este momento su devolución para el caso de estimación total o parcial del recurso.

[OPCIONAL — incluir si procede]

OTROSÍ SEGUNDO DIGO que, de conformidad a lo establecido en el art. 481.6 de la LEC, acompaño como documento número 1 copia de la sentencia impugnada, que contiene firma electrónica que la identifica (o código seguro de verificación), así como texto de las Sentencias de las Audiencias Provinciales de [LOCALIDAD] que se aducen como fundamento de interés casacional, como documentos número [Nº DE DOCUMENTO].

Por lo que, SUPLICO A LA SALA que tenga por aportados los citados documentos.

En [LUGAR], a [FECHA].

Procurador/a	Abogado/a

Fdo. D./Dña. [NOMBRE Y APELLIDOS]: 	Fdo. D./Dña. [NOMBRE Y APELLIDOS]:
