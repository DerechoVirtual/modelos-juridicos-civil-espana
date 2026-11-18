---
name: autorizacion-judicial-disponer-vivienda-habitual-672
description: "Redacta el escrito «Autorización judicial para disponer de la vivienda habitual por desacuerdo de los cónyuges» (formulario 672 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Autorización judicial para disponer de la vivienda habitual por desacuerdo de los cónyuges

> Formulario 0672 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] SEDE (2 veces)
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] Nº DE DOCUMENTO (4 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] FECHA (3 veces)
- [ ] Nº (2 veces)
- [ ] IMPORTE (8 veces)
- [ ] ÓRGANO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 18 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, vecino/a de»; «…esentado y su cónyuge, de vecindad civil»; «…de»; «…de [COMPLETAR] de»; «…o su régimen económico matrimonial el de»; «…. El matrimonio tiene un hijo menor»; «…ivienda anteriormente ocupada. En el año»; «…ción registral: “ Urbana. vivienda, sita»; «…” En fecha [FECHA] de»; «…” En fecha [FECHA] de [COMPLETAR] de»; «…para remontarla. En efecto, desde el año»; «…on el certificado de la entidad bancaria»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 1320 del Código Civil
- art. 1320 del Código Civil
- art. 5 de la Ley Orgánica 1/2025

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

### Formulario 0672 · Autorización judicial para disponer de la vivienda habitual por desacuerdo de los cónyuges

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 43 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dª [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre de D./Dª [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], ante el Tribunal comparezco y como mejor proceda en Derecho,

DIGO:

Que mediante el presente escrito, al amparo del artículo 90.1.a) de la Ley de Jurisdicción Voluntaria y artículo 1320 del Código Civil, promuevo expediente de jurisdicción voluntaria solicitando que se autorice judicialmente la venta de la vivienda habitual del matrimonio sita en [LOCALIDAD], al no estar de acuerdo con el citado negocio el cónyuge D./Dª [NOMBRE Y APELLIDOS], vecino/a de [COMPLETAR], con domicilio en [LOCALIDAD], quien debe ser citado en este expediente, en base a los siguientes

HECHOS

Mi representado y su cónyuge, de vecindad civil [COMPLETAR], contrajeron matrimonio en fecha [FECHA] de [COMPLETAR] de [COMPLETAR], siendo su régimen económico matrimonial el de [COMPLETAR]. El matrimonio tiene un hijo menor [COMPLETAR], de [Nº] años de edad, que convive con sus padres.

Durante los primeros años fijaron su domicilio en esta ciudad, en la vivienda sita en [LOCALIDAD], la cual ocuparon como arrendatarios pagando una renta mensual de

Adjunto acompaño como documentos certificación literal de matrimonio, de nacimiento del hijo y contrato de arrendamiento de la vivienda anteriormente ocupada.

En el año [COMPLETAR] falleció la madre del solicitante, quien dejó en herencia a mi representado el inmueble con la siguiente descripción registral:

“ Urbana. vivienda, sita [COMPLETAR]

”

En fecha [FECHA] de [COMPLETAR] de [COMPLETAR], el matrimonio se trasladó a vivir a este inmueble, titularidad de mi representado, con su hijo menor, donde han estado viviendo hasta la actualidad y respecto del cual se solicita esta autorización para ser enajenado.

A efectos acreditativos acompaño como documentos núm. certificación registral, escritura de aceptación de herencia y certificado de empadronamiento.

El motivo por el que se solicita autorización para la venta de esta vivienda habitual deriva de la mala marcha de los negocios de mi representado, el cual se ha dedicado profesionalmente como empresario autónomo a la construcción y que, como consecuencia de la crisis económica, se ha visto inmerso en una situación de endeudamiento que hace necesario la venta de esta vivienda para remontarla.

En efecto, desde el año [COMPLETAR], los ingresos regulares de mi representado no alcanzan los [IMPORTE] euros mensuales, a lo cual hay que añadir que el cónyuge quedó en desempleo y que aumentaron los gastos del hijo común al estar estudiando en el Centro de

Para remontar esta situación se vio obligado a hipotecar la vivienda habitual, tal como consta en la certificación que se acompaña, quedando pendiente un total de [IMPORTE] euros de principal, intereses y costas, y adeudándose en la actualidad dos mensualidades, tal como justifico con el certificado de la entidad bancaria [COMPLETAR] que acompaño como documento núm. [Nº DE DOCUMENTO]

Asimismo, en fecha [FECHA] de [COMPLETAR] de [COMPLETAR] concertó un préstamo personal por importe de [IMPORTE] euros, que resultó impagado, siguiéndose autos núm. [Nº] de proceso de ejecución en la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], en el que se ha decretado el embargo de la vivienda para responder de una deuda de [IMPORTE] euros, tal como consta en la nota registral acompañada.

Mi representado carece de otros bienes para hacer frente a estas deudas.

Ante esta situación, y ante la oposición de su cónyuge a la venta de la vivienda en que residen, mi representado se ve en la obligación de solicitar la autorización judicial como única solución para superar la situación de endeudamiento en que se ve inmerso.

La oposición del cónyuge deriva sin duda del alto valor de la vivienda en la que residen, ubicada en una de las mejores zonas de la ciudad como es notorio. Sin embargo, lo cierto es que es una vivienda en exceso amplia para las necesidades de la familia, puesto que tiene una superficie de [COMPLETAR] metros cuadrados, a la vez que es muy oneroso su mantenimiento, puesto que el IBI asciende a [IMPORTE] euros y los gastos de comunidad incluyen el pago de un conserje y el mantenimiento de la zona comunitaria con piscina y pistas de tenis que ascienden a [IMPORTE] euros mensuales.

Ello redunda en la necesidad de vender la vivienda, puesto que su mantenimiento es en exceso gravoso y excede en mucho a las necesidades y posibilidades de la familia.

Mi representado tiene la expectativa de obtener la cantidad de [IMPORTE] euros por la venta de la vivienda y ha gestionado el posible alquiler de una vivienda en la zona de menores dimensiones para vivir la familia, lo cual costaría una cantidad aproximada de [IMPORTE] euros, todo lo cual se acredita por el informe del Agente de la Propiedad Inmobiliaria D. [NOMBRE Y APELLIDOS] que acompaño como documento núm. [Nº DE DOCUMENTO]

Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

A los anteriores hechos les son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

Competencia

Son competentes los Tribunales de Instancia de esta ciudad, por ser la del domicilio del matrimonio, conforme a lo dispuesto en el art. 90.3 de la Ley de Jurisdicción Voluntaria.

Procedimiento

Debe seguirse el procedimiento de jurisdicción voluntaria regulado en el art. 90 de la Ley de Jurisdicción Voluntaria.

Legitimación y postulación

Esta parte está legitimada conforme a lo dispuesto en el art. 1320 del Código Civil y art. 90 de la Ley de Jurisdicción Voluntaria, compareciendo con Abogado y Procurador al solicitarse autorización para un acto de contenido patrimonial de valor superior a 6.000 euros, según se acredita en el informe acompañado.

Cumplimiento de los requisitos de procedibilidad.

La presente demanda cumple con los requisitos de procedibilidad exigidos por el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Fundamentos de fondo

El artículo 1320 del Código Civil dispone que para disponer de los derechos sobre la vivienda habitual y los muebles de uso ordinario de la familia, aunque tales derechos pertenezcan a uno solo de los cónyuges, se requerirá el consentimiento de ambos o, en su caso, autorización judicial, la cual se solicita al ser necesaria la venta del inmueble y ante la oposición del cónyuge no solicitante [ÓRGANO].

Por lo expuesto:

SUPLICO AL TRIBUNAL tenga por presentado este escrito, me tenga por parte en la representación, entendiéndose conmigo las sucesivas actuaciones, por promovido y se incoe el oportuno expediente de jurisdicción voluntaria, y una vez oído el cónyuge no solicitante, el hijo menor [COMPLETAR] y el Ministerio fiscal, y practicadas cuantas actuaciones se consideren necesarias, se dicte en su día auto por el que se acuerde autorizar la venta de la vivienda habitual del matrimonio conforme a lo solicitado.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del Abogado y Procurador.

========================================================================
