---
name: pedir-exoneracion-costas-moderacion-cuantia-4
description: "Redacta el escrito «Pedir la exoneración de costas o la moderación de su cuantía» (formulario 4 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pedir la exoneración de costas o la moderación de su cuantía

> Formulario 0004 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] o la moderación de su cuantía (2 veces)
- [ ] SEDE
- [ ] Nº
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] Nº DE PROCEDIMIENTO (2 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] COLEGIO
- [ ] FECHA (8 veces)
- [ ] IMPORTE (4 veces)
- [ ] DESCRIBIR
- [ ] Nº DE DOCUMENTO
- [ ] O MODERACIÓN DE LA CUANTIA EN UN [COMPLETAR] POR 100 
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… tengo acreditada en los autos de juicio»; «…nómica efectuada por la parte actora era»; «…dante fue la de efectuar ofrecimiento de»; «…y»; «…, en la que se condenaba a mi mandante a»; «…eración (en su caso, la moderación en un»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 245.5 LEC
- artículo 245 de la Ley 1/2000

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

### Formulario 0004 · Pedir la exoneración de costas o la moderación de su cuantía

- Año del modelo: 2025
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 30 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de la parte condenada al pago de las costas en solicitud de exoneración de su pago [o la moderación de su cuantía] cuando hubiera formulado una propuesta a la parte contraria en cualquiera de los medios adecuados de solución de controversias al que hubieran acudido, la misma no hubiera sido aceptada por la parte requerida y la resolución judicial que ponga término al procedimiento sea sustancialmente coincidente con el contenido de dicha propuesta.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [Nº]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D/Dña. [NOMBRE Y APELLIDOS], Procurador/a de los tribunales y de D/Dña. [NOMBRE Y APELLIDOS], representación que tengo acreditada en los autos de juicio [COMPLETAR], nº [Nº DE PROCEDIMIENTO], ante el tribunal comparezco bajo la dirección letrada de D/Dña. [NOMBRE Y APELLIDOS], colegiado/a nº [Nº DE COLEGIADO/A], del Ilustre Colegio de Abogados de [COLEGIO], y como mejor en derecho proceda DIGO:

Que de acuerdo con el art. 245.5 LEC SOLICITO LA EXONERACIÓN DEL PAGO DE LAS COSTAS [o la moderación de su cuantía] impuestas en el presente procedimiento, en base a los siguientes:

Hechos y consideraciones jurídicas

Primera.- Mi representado ha sido condenado al pago de las costas del presente procedimiento por sentencia nº [Nº DE PROCEDIMIENTO], de fecha [FECHA]

Segunda.- Las costas han sido tasadas por el/la Letrado/a de la administración de Justicia por un monto total de [IMPORTE] euros, correspondiendo [IMPORTE] euros a los honorarios del letrado, [IMPORTE] euros a los derechos del procurador, y [IMPORTE] euros en concepto de otros costes.

Tercera.- Mi representado interesó con carácter previo a la interposición de la demanda un medio adecuado de carácter no jurisdiccional de solución de la controversia, contemplado en la LO 1/2025, de 2 enero, de medidas en materia de eficiencia del Servicio Público de Justicia, relativo a [DESCRIBIR], según se acredita con la documentación íntegra referida a la propuesta formulada que se acompaña como documentos números

De la lectura de la indicada comunicación, se advierte que la reclamación económica efectuada por la parte actora era [COMPLETAR]

Cuarta.- La postura de mi mandante fue la de efectuar ofrecimiento de [COMPLETAR] al objeto de efectuar una transacción de la reclamación inicial, que no fue aceptada por la parte actora, según se advierte del documento nº [Nº DE DOCUMENTO] y [COMPLETAR] adjunto, al, efecto la respuesta efectuada por mi mandante y la negativa de su aceptación por la parte actora.

Quinta.- Tramitado el correspondiente juicio, el mismo concluyó con la precitada sentencia de fecha [FECHA], hoy firme, en la que se condenaba a mi mandante a [COMPLETAR], que es un pronunciamiento sustancialmente idéntico al que en su momento ya se le ofreció al actor por mi mandante, en la comunicación de fecha [FECHA] adjunta.

Sexta.- Es por todo ello que, coincidiendo sustancialmente la condena efectuada a mi mandante en la sentencia de fecha [FECHA], con la propuesta de solución no jurisdiccional efectuada por mi mandante al actor, en escrito de fecha [FECHA] previo a la demanda, que interesa mi mandante la exoneración (en su caso, la moderación en un [COMPLETAR] por 100 equivalente a la diferencia de la condena del pago de las costas procesales).

Séptima.- De conformidad con lo establecido en el art. 245.5 LEC, sin perjuicio de lo dispuesto en los apartados anteriores y en el mismo plazo, la parte condenada al pago de las costas podrá solicitar la exoneración de su pago o la moderación de su cuantía cuando hubiera formulado una propuesta a la parte contraria en cualquiera de los medios adecuados de solución de controversias al que hubieran acudido, la misma no hubiera sido aceptada por la parte requerida y la resolución judicial que ponga término al procedimiento sea sustancialmente coincidente con el contenido de dicha propuesta.

Las mismas consecuencias tendrá el rechazo injustificado de la propuesta que hubiese formulado el tercero neutral, cuando la sentencia recaída en el proceso sea sustancialmente coincidente con la citada propuesta.

A la solicitud de exoneración o modificación deberá acompañar la documentación íntegra referida a la propuesta formulada, que en este momento procesal y a estos efectos, estará dispensada de confidencialidad. De no acompañarse dicha documentación, el Letrado de la Administración de Justicia, mediante decreto, inadmitirá a trámite la solicitud. Frente a este decreto cabrá interponer recurso de revisión.

Octava.- De acuerdo con el art. 9.2 de la ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia las partes, los abogados o abogadas y la tercera persona neutral no podrán declarar o aportar documentación derivada del proceso de negociación o relacionada con el mismo ni ser obligados a ello en un procedimiento judicial o en un arbitraje, excepto:

a) Cuando todas las partes de manera expresa y por escrito se hayan dispensado recíprocamente o al abogado o abogada o a la tercera persona neutral del deber de confidencialidad.
b) Cuando se esté tramitando la impugnación de la tasación de costas y solicitud de exoneración o moderación de las mismas según lo previsto en el artículo 245 de la Ley 1/2000, de 7 de enero, de Enjuiciamiento Civil y a esos únicos fines, sin que pueda utilizarse para otros diferentes ni en procesos posteriores.
c) Cuando, mediante resolución judicial motivada, sea solicitada por los jueces y juezas del orden jurisdiccional penal.
d) Cuando sea necesario por razones de orden público, en particular cuando así lo requiera la protección del interés superior del menor o la prevención de daños a la integridad física o psicológica de una persona.

Por lo expuesto.

SOLICITO AL TRIBUNAL: Que teniendo por presentado este escrito junto con sus documentos y copias de todo ello, se sirva admitirlo y tener por formulada solicitud de EXONERACIÓN [O MODERACIÓN DE LA CUANTIA EN UN [COMPLETAR] POR 100 ] de la tasación de costas de fecha [FECHA] practicada en las actuaciones arriba referenciadas por resultar la condena contenida en la sentencia firme de fecha [FECHA] sustancialmente idéntica a la contrapropuesta efectuada por mi mandante al actor, en fecha [FECHA], en sede del procedimiento extrajudicial de solución de conflicto previo al juicio tramitado, sin que el mismo la hubiera considerado o aceptado.

PRIMER OTROSÍ DIGO: Que a los efectos de lo previsto en el art. 9.2 de la ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia, tenga por exonerada a esta parte de la prohibición de aportar la documentación derivada del proceso de negociación extrajudicial de solución de conflicto, a los solos efectos de la impugnación de la tasación de costas procesales.

AL TRIBUNAL NUEVAMENTE SOLICITO: Que tenga por efectuada la anterior manifestación a los efectos legales oportunos.

Es Justicia que debe hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a	Firma de Procurador/a
