---
name: diligencia-preliminar-concretar-miembros-grupo-afectados-1068
description: "Redacta el escrito «Diligencia preliminar para concretar los miembros de un grupo de afectados determinables» (formulario 1068 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Diligencia preliminar para concretar los miembros de un grupo de afectados determinables

> Formulario 1068 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] Nº DE DOCUMENTO
- [ ] Nº DE COLEGIADO
- [ ] COLEGIO
- [ ] NIF
- [ ] LOCALIDAD
- [ ] TELÉFONO
- [ ] FECHA (3 veces)
- [ ] DESCRIBIR (4 veces)
- [ ] CALLE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] IMPORTE
- [ ] Otros 21 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…rigiendo esta petición contra la entidad»; «…y número de fax»; «… circunstancias; por ejemplo: la entidad»; «…ha suministrado, entre los días»; «…y»; «…y [COMPLETAR] de»; «…y [COMPLETAR] de [COMPLETAR] de»; «…ó a los vecinos de los inmuebles números»; «…a»; «…oríficas, etc.). Como documentos números»; «…a»; «…or ejemplo: ejemplar original del diario»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 263 de la LEC
- artículo 258 de la LEC

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

### Formulario 1068 · Diligencia preliminar para concretar los miembros de un grupo de afectados determinables

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 39 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (COMPLETAR, Nº DE COLEGIADO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en nombre de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], ante el Tribunal comparezco bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], colegiado núm. [Nº DE COLEGIADO] del Iltre. Colegio de Abogados de [COLEGIO], y como mejor proceda en derecho DIGO:

Que mediante el presente escrito, en nombre de mi representado y al amparo de lo dispuesto en el artículo 256.1.6.º de la LEC, promuevo DILIGENCIA PRELIMINAR para la concreción de los componentes de un grupo de afectados por un hecho dañoso, dirigiendo esta petición contra la entidad [COMPLETAR], S.L., provista de CIF [NIF] y con domicilio social en [LOCALIDAD], provista de número de teléfono [TELÉFONO] y número de fax [COMPLETAR], basándome en los siguientes

ANTECEDENTES

Con fecha [FECHA] ocurrió un hecho dañoso consistente en [DESCRIBIR] (detallar circunstancias; por ejemplo: la entidad [COMPLETAR] ha suministrado, entre los días [COMPLETAR] y [COMPLETAR] de [COMPLETAR] de [COMPLETAR], un producto de los que fabrica consistente en [DESCRIBIR] con un defecto de fabricación que ha ocasionado daños a los usuarios consistentes en [DESCRIBIR]; o bien: un fallo en el suministro de energía eléctrica que afectó a los vecinos de los inmuebles números [COMPLETAR] a [COMPLETAR] de la calle [CALLE] de esta capital del que se siguieron graves perjuicios debidos tanto a averías en electrodomésticos como a la pérdida de alimentos conservados en cámaras frigoríficas, etc.). Como documentos números [COMPLETAR] a [COMPLETAR] acompaño justificantes documentales del acaecimiento del siniestro (por ejemplo: ejemplar original del diario [COMPLETAR] de fecha [FECHA] en el que se recoge una amplia crónica del acaecimiento del hecho dañoso).

Resultaría fácilmente determinable el grupo de afectados por el hecho detallado en el ordinal anterior si la empresa [COMPLETAR], S.L. se aviniese a facilitar los datos de los [COMPLETAR] (compradores del producto, vecinos que tienen contratado suministro de energía eléctrica, etc.), pero dicha empresa, temiendo que pudiera recibir diversas demandas se ha negado a facilitar tales datos, con objeto de obstaculizar la interposición de las reclamaciones.

No tiene mi representado posibilidad de acceso a los datos que interesa recabar, debido a la imposibilidad de acceso a [COMPLETAR] (por ejemplo al padrón municipal, etc.; justificar la necesidad de la diligencia preliminar solicitada).

El objeto concreto de la demanda que tiene intención de promover mi representado consiste en [COMPLETAR] (detallar con la mayor concreción posible, de modo que puedan ponerse en relación las diligencias preliminares con la demanda posterior a los efectos de conservación de la fianza previstos en el artículo de la LEC).

Tiene intención mi poderdante de promover la reclamación judicial a través del grupo de consumidores o usuarios afectados por hecho dañoso del que forma parte. El artículo 6.7.º de la LEC exige que «el grupo se constituya con la mayoría de los afectados», motivo por el que precisa conocer los datos cuya puesta de manifestación se solicita con esta diligencia preliminar.

Resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

Es competente el Tribunal al que me dirijo en virtud de lo dispuesto por el artículo 257 de la Ley de Enjuiciamiento Civil (LEC).

Procedimiento

La solicitud se tramitará por el cauce establecido en las artículos 258 y siguientes de la Ley de Enjuiciamiento Civil.

Caución

El artículo 263 de la LEC exige el ofrecimiento de prestación de caución para responder de eventuales gastos y daños y perjuicios que se pudieran irrogar a la parte frente a la que se promueven estas diligencias. Se verifica dicho ofrecimiento mediante otrosí.

Fondo

El artículo 256.1.6.° de la LEC habilita la preparación del juicio «Por petición de quien pretenda iniciar un proceso para la defensa de los intereses colectivos de consumidores y usuarios al objeto de concretar a los integrantes del grupo de afectados cuando, no estando determinados, sean fácilmente determinables. A tal efecto el tribunal adoptará las medidas oportunas para la averiguación de los integrantes del grupo, de acuerdo a las circunstancias del caso y conforme a los datos suministrados por el solicitante, incluyendo el requerimiento al demandado para que colabore en dicha determinación».

En el presente caso se justifican la pertinencia y proporcionalidad de la diligencia preliminar interesada por las circunstancias de [COMPLETAR] (justificar mediante la alegación de las circunstancias concurrentes).

La justa causa y el interés legítimo de mi mandante que exige el artículo 258 de la LEC radican en su condición de afectado por el hecho dañoso [COMPLETAR].

Concurre en la persona frente a la que se dirige esta solicitud la condición de responsable de los daños causados al grupo de afectados cuya determinación se persigue.

 (desarrollar cuantas razones contribuyan a plantear la diligencia como adecuada a la finalidad perseguida y acreditar que la medida guarda proporcionalidad con dicho fin).

Determina el artículo 261.5.ª de la LEC que «Tratándose de las diligencias previstas en el artículo 256.1.6, ante la negativa del requerido o de cualquier otra persona que pudiera colaborar en la determinación de los integrantes del grupo, el tribunal ordenará que se acuerden las medidas de intervención necesarias, incluida la de entrada y registro, para encontrar los documentos o datos precisos, sin perjuicio de la responsabilidad penal en que se pudiera incurrir por desobediencia a la autoridad judicial [COMPLETAR]».

Por todo lo expuesto,

SUPLICO AL TRIBUNAL que tenga por presentado este escrito, con el poder y el documento que se acompañan con sus preceptivas copias, se sirva admitirlo, teniendo por promovida la diligencia preliminar solicitada, y en su virtud requiera a la mercantil [COMPLETAR], S.L., bajo apercibimiento de la responsabilidad penal en que se pudiera incurrir por desobediencia a la autoridad judicial, para que comunique la relación (o colabore en la determinación) de los afectados por el hecho dañoso consistente en [DESCRIBIR] acaecido el día [FECHA], acordando, si no colabora ni formula oposición, la entrada y registro en las oficinas de dicha entidad sitas en [COMPLETAR], todo ello con los demás pronunciamientos procedentes en derecho, y, una vez practicada la diligencia interesada, se me expida testimonio de su resultado.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

OTROSÍ DIGO: (que a los efectos previstos en los artículos 256.3 y 258.3, y aun cuando esta parte entiende que la diligencia solicitada no la precisaría, ofrecemos prestar, en la forma y plazos legalmente establecidos, la caución de [IMPORTE] euros o subsidiariamente la que fije el Tribunal, comprometiéndonos a constituir dicha caución.

Nuevamente suplico al Tribunal: tenga por hecha la anterior manifestación y por ofrecida la prestación de caución a los efectos legales oportunos.

Es justicia que reitero en igual lugar y fecha.

========================================================================
