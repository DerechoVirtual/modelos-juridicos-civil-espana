---
name: ejecucion-acta-notarial-deuda-dineraria-no-contradicha-667
description: "Redacta el escrito «Ejecución del acta notarial de deuda dineraria no contradicha» (formulario 667 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Ejecución del acta notarial de deuda dineraria no contradicha

> Formulario 0667 del plugin **Ejecución civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.
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

- [ ] SEDE
- [ ] LOCALIDAD (4 veces)
- [ ] FECHA (4 veces)
- [ ] IMPORTE (10 veces)
- [ ] Nº
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 21 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…D»; «…rado de la Administración de Justicia de»; «…, bajo la dirección letrada de D»; «… contradicha autorizada por el Notario D»; «…de fecha [FECHA] de»; «…de fecha [FECHA] de [COMPLETAR] de»; «…cución y costas, la cual dirijo contra D»; «…i representado solicitó en la Notaría de»; «…euros contra D»; «…de»; «…de [COMPLETAR] de»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 50 y 51 de la LEC
- artículo 550 de la LEC
- artículos 551 a 554 LEC
- artículo 517.2.9 de la LEC
- artículo 517 LEC
- artículo 590 LEC
- art. 4.1.e) de la Ley 10/2012
- Ley 15/2015

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

### Formulario 0667 · Ejecución del acta notarial de deuda dineraria no contradicha

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 42 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D [COMPLETAR], Procurador de los Tribunales en representación de [LOCALIDAD] según acredito por apoderamiento apud-acta otorgado ante el Letrado de la Administración de Justicia de [COMPLETAR], bajo la dirección letrada de D [COMPLETAR], Abogado del Iltre. Colegio de [LOCALIDAD], ante el Tribunal comparezco y como mejor en derecho proceda

DIGO:

Que por medio de la presente demanda y en la meritada representación solicito la ejecución del acta notarial de deuda dineraria no contradicha autorizada por el Notario D [COMPLETAR] de fecha [FECHA] de [COMPLETAR] de [COMPLETAR], en reclamación de la suma de [IMPORTE] euros en concepto de principal, intereses remuneratorios y de mora vencidos, con más la cantidad de [IMPORTE] euros, que se presupuesta en concepto de intereses que se pueden devengar en la presente ejecución y costas, la cual dirijo contra D [COMPLETAR], con domicilio en [LOCALIDAD], con base en los siguientes:

HECHOS

Mi representado solicitó en la Notaría de [COMPLETAR] expediente de reclamación de deuda dineraria en reclamación de [IMPORTE] euros contra D [COMPLETAR], como consecuencia de

Dicha cantidad se desglosa en [IMPORTE] euros de principal, [IMPORTE] euros por intereses remuneratorios y [IMPORTE] euros por intereses de demora.

En fecha [FECHA] de [COMPLETAR] de [COMPLETAR] se practicó requerimiento notarial de pago, sin que el deudor compareciera, autorizándose el acta notarial de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] en la que consta dicha circunstancia que constituye el título ejecutivo que funda la pretensión de esta parte.

(Se acompaña como documento [COMPLETAR] acta notarial de reclamación de deuda dineraria no contradicha de fecha [FECHA] de [COMPLETAR] de [COMPLETAR]).

FUNDAMENTOS DE DERECHO

Competencia

Art. 545.3 de la LEC: Es competente el Tribunal al que me dirijo al tratarse de un título extrajudicial con arreglo a lo establecido en los arts. 50 y 51 de la LEC, en relación con lo dispuesto en el art. 85.1º LOPJ.

Procedimiento

Artículo 549 LEC en relación con el que debe ser el contenido de la demanda ejecutiva y artículo 550 de la LEC en cuanto a los documentos a aportar. Y artículos 551 a 554 LEC en relación al despacho de ejecución.

Título ejecutivo

Artículo 71.3 de la Ley del Notariado en relación con el artículo 517.2.9 de la LEC: “Si en el plazo establecido el deudor no compareciere o no alegare motivos de oposición, el Notario dejará constancia de dicha circunstancia. En este caso, el acta será documento que llevara aparejada ejecución a los efectos del número 9.º del apartado 2 del artículo 517 de la Ley de Enjuiciamiento Civil. Dicha ejecución se tramitará conforme a lo establecido para los títulos ejecutivos extrajudiciales.”.

Tutela ejecutiva

Se interesa el despacho de ejecución por la cantidad de [IMPORTE] euros, tal como consta en el título, con más la de [IMPORTE] euros presupuestados para intereses y costas, conforme al artículo 517 LEC, en relación con los artículos 571 y ss. para la ejecución dineraria.

Costas

Artículo 539.2 LEC.

Por todo ello,

SUPLICO AL TRIBUNAL: Que teniendo por presentado este escrito con los documentos que lo acompañan y sus copias, se dicte auto conteniendo la orden general de ejecución y despachando la misma por la cantidad reclamada conforme a lo solicitado en la cantidad de [IMPORTE] euros en concepto de principal, más la cantidad de [IMPORTE] euros en concepto de intereses, gastos y costas.

OTROSÍ DIGO: Que, una vez dictado el auto general de ejecución y de conformidad con el art. 551.3.1º de la LEC, se solicita que por el Letrado de la Administración de Justicia responsable de la misma requiera de pago al deudor y, caso de no atender el requerimiento, se dicte decreto procediéndose al embargo de los siguientes bienes que se estiman suficientes para cubrir las indicadas responsabilidades en su totalidad:

(se designarían bienes en su caso)

Por lo que, SUPLICO que se dicte decreto en el que se contengan las medidas que dejo interesadas.

OTROSÍ DIGO II: Que desconociendo esta parte bienes que puedan ser objeto de embargo por parte de este Tribunal, al amparo de lo dispuesto en el artículo 590 LEC, esta parte solicita que, una vez dictado el auto general de ejecución y de conformidad con el art. 551.3.2º de la LEC, el Tribunal proceda a dirigirse a los efectos de determinación de la relación de bienes muebles e inmuebles, así como depósitos o imposiciones a plazo fijo que el ejecutado pueda tener a su nombre a los siguientes organismos:

1. Gerencia Territorial del Catastro de [COMPLETAR]

2. Delegación Territorial de la Agencia Tributaria de [COMPLETAR]

3. Registro de la Propiedad núm. [Nº] de [COMPLETAR]

4. Jefatura Provincial de Tráfico de [LOCALIDAD]

5. Caja de Ahorros Provincial de [COMPLETAR]

Por lo que, SUPLICO que se dicte decreto procediéndose a adoptar las medidas de localización y averiguación de bienes solicitadas.

OTROSI DIGO III: Que de conformidad a lo dispuesto en el art. 4.1.e) de la Ley 10/2012, redactado por Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria esta demanda está exenta del pago de la tasa judicial.

Por lo que, SUPLICO AL TRIBUNAL que tenga por hecha la anterior manifestación a los efectos pertinentes.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma Abogado y Procurador

========================================================================
