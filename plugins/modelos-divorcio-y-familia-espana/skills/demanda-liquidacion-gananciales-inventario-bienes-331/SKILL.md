---
name: demanda-liquidacion-gananciales-inventario-bienes-331
description: "Redacta el escrito «Demanda de liquidación de gananciales con inventario de bienes» (formulario 331 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de liquidación de gananciales con inventario de bienes

> Formulario 0331 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] Nº
- [ ] AÑO (2 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] COLEGIO
- [ ] FECHA
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] IMPORTE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…actúa en nombre y representación de Doña»; «…UE CONFORMAN DICHA SOCIEDAD frente a Don»; «…icos: HECHOS PRIMERO.- Mi mandante y Don»; «… separación/divorcio de los cónyuges Don»; «…y Doña»; «… actualmente vigente (documentos números»; «…a»; «…euros y del pasivo»; «…rajudicial. En este sentido, se acudió a»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 1.400 y 1.405 CCiv
- art. 807 LEC
- arts. 808 y 809 LEC
- arts. 23 y 31 LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 1.392 CCiv
- arts. 1.399 a 1.410 CCiv
- art. 1.404 CCiv
- arts. 1.359 y 1.360 CCiv
- art. 394 LEC

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

### Formulario 0331 · Demanda de liquidación de gananciales con inventario de bienes

- Año del modelo: 2020
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 20 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de solicitud conjunta de formación de inventario y liquidación de gananciales después de separación o divorcio.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, que actúa en nombre y representación de Doña [COMPLETAR], según consta debidamente acreditado en los autos de separación/divorcio contencioso nº [Nº]/[AÑO], asistida del Letrado en ejercicio D./Dña. [NOMBRE Y APELLIDOS], colegiado/a nº [Nº DE COLEGIADO/A] del Ilustre Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco y, como mejor proceda en Derecho, DIGO:

Que en la representación que ostento, vengo a solicitar la LIQUIDACIÓN DEL RÉGIMEN ECONÓMICO MATRIMONIAL DE SOCIEDAD DE GANANCIALES existente entre los cónyuges/ex cónyuges, y FORMACIÓN DE INVENTARIO DE LOS BIENES QUE CONFORMAN DICHA SOCIEDAD frente a Don [COMPLETAR], demandado en los autos principales, con arreglo a los siguientes hechos y fundamentos jurídicos:

HECHOS

PRIMERO.- Mi mandante y Don [COMPLETAR], formaban matrimonio cuyo régimen económico era el supletorio legal de la sociedad de gananciales.

SEGUNDO.- Que con fecha [FECHA] se dictó sentencia de separación/divorcio de los cónyuges Don [COMPLETAR] y Doña [COMPLETAR], cuyo testimonio se adjunta como documento nº [Nº DE DOCUMENTO], en la que entre otros pronunciamientos, acordaba el efecto legal de la disolución del régimen de gananciales, sentencia que es firme.

Como consecuencia, quedó disuelta de pleno derecho y pendiente de liquidación la sociedad de gananciales vigente entre los cónyuges.

TERCERO.- Los bienes cuyo activo constituye la sociedad económica de gananciales son:

Y el pasivo debe desglosarse en los siguientes apartados:

a) Deudas:
b) Importe actualizado de las cantidades satisfechas por uno de los cónyuges siendo de cargo de la sociedad:

Se acompañan documentos justificativos de las diferentes partidas, consistentes en certificaciones de los diferentes Registros de la Propiedad, certificaciones bancarias respecto a los valores y saldos depositados en entidades bancarias, así como certificación bancaria relativa al préstamo hipotecario actualmente vigente (documentos números [COMPLETAR] a [COMPLETAR]).

CUARTO.- A cada cónyuge le corresponde la mitad del activo, es decir [IMPORTE] euros y del pasivo [COMPLETAR]

No obstante, procede el ofrecimiento de adjudicaciones de bienes gananciales conforme disponen los arts. 1.400 y 1.405 CCiv en el sentido siguiente:

QUINTO.- Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

A los anteriores hechos le son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA.

Se atribuye legalmente al Tribunal de Instancia que hubiera conocido del proceso de separación/divorcio que determina la disolución de régimen económico matrimonial (art. 807 LEC).

II.- PROCEDIMIENTO.

El procedimiento es el que se señala en los arts. 808 y 809 LEC para la formación de inventario; y el art. 810 para la liquidación, bien entendido que primero se tramitará el procedimiento de inventario y, finalizado éste, el de liquidación del régimen económico matrimonial, uno después del otro.

III.- LEGITIMACIÓN.

Están legitimado activamente cualquiera de los cónyuges, en este caso mi representada, ostentando legitimación pasiva el otro cónyuge, como copartícipes en la sociedad de gananciales cuya liquidación se solicita.

IV.- POSTULACIÓN.

Conforme a los arts. 23 y 31 LEC, se presenta la solicitud representado por Procurador de los Tribunales y asistido de Abogado legalmente habilitado para ejercer ante el Tribunal.

V.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con el requisito de procedibilidad exigido por el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VI.- DERECHO SUSTANTIVO.

El divorcio/la separación de los cónyuges provoca la disolución automática de la sociedad de gananciales que regía el matrimonio, conforme al art. 1.392 CCiv. La liquidación de la misma exige el previo inventario del activo y el pasivo, conforme a lo dispuesto en los arts. 1.396 a 1.398 y concordantes CCiv.

Los arts. 1.399 a 1.410 CCiv regulan los aspectos sustantivos de la liquidación de la sociedad conyugal una vez terminado el inventario.

En concreto, los arts. 1.399 a 1.403 obligan a deducir las deudas de la sociedad y a efectuar los reintegros que proceda entre el patrimonio ganancial y los privativos de los cónyuges para determinar el remanente que deberá dividirse por mitad entre los cónyuges, conforme establece el art. 1.404 CCiv.

En relación con el crédito de la sociedad de gananciales frente al demandado por la mejora de un bien privativo con fondos gananciales, resultan aplicables los arts. 1.359 y 1.360 CCiv.

VII.- COSTAS.

Deben imponerse al demandado si se opone a la demanda, conforme al art. 394 LEC.

Por lo expuesto:

SUPLICO AL TRIBUNAL:

tenga por presentado este escrito y, sus copias, a las que se dará el destino legal, se sirva admitir todo ello, y tras los trámites oportunos se sirva dictar resolución por la que:

1º DECLARE que el inventario de liquidación de la sociedad de gananciales habida entre ambas partes litigantes comprenderá las partidas de activo y pasivo propuestas por esta parte.
2º ACUERDE la liquidación de la sociedad de gananciales conforme con lo expuesto en el cuerpo de este escrito.
3º ACUERDE la adjudicación a cada uno de los cónyuges de los bienes tal y como se solicita.

Es justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

	Firma de Procurador/a
