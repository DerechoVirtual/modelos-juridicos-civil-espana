---
name: demanda-ejecutiva-decreto-aprueba-tasacion-costas-121
description: "Redacta el escrito «Demanda ejecutiva del decreto que aprueba la tasación de costas» (formulario 121 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda ejecutiva del decreto que aprueba la tasación de costas

> Formulario 0121 del plugin **Ejecución civil** · revisado el 17-11-2026.

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
- [ ] Nº
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO (2 veces)
- [ ] FECHA (4 veces)
- [ ] IMPORTE (5 veces)
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ncias personales, en los autos de Juicio»; «… 1. Gerencia Territorial del Catastro de»; «… Territorial de la Agencia Tributaria de»; «…3. Registro de la Propiedad de»; «…5. Caja de Ahorros Provincial de»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 548 LEC
- art. 545.1 LEC
- art. 538 LEC
- art. 539.1 LEC
- art. 242.1 LEC
- art. 549 LEC
- art. 576 LEC
- artículo 590 LEC

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

### Formulario 0121 · Demanda ejecutiva del decreto que aprueba la tasación de costas

- Año del modelo: 2022
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 21 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda de ejecución de la resolución del LAJ que aprueba una tasación de costas, con solicitud de averiguación de la situación patrimonial del ejecutado, por desconocer la existencia de bienes susceptibles de embargo.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [Nº]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, que actúa en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según tengo acreditado, junto con la dirección letrada y las circunstancias personales, en los autos de Juicio [COMPLETAR] n.º [Nº DE PROCEDIMIENTO]/[AÑO], seguidos a instancias de D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco y como mejor proceda en Derecho, DIGO:

Que por medio de la presente demanda y en la meritada representación solicito la ejecución del Decreto del Letrado de la Administración de Justicia de fecha [FECHA], que aprueba la tasación de costas, en reclamación de la suma de [IMPORTE] euros en concepto de principal e intereses vencidos, con más la cantidad de [IMPORTE] euros, que se presupuesta en concepto de intereses que se pueden devengar en la presente ejecución y costas, la cual dirijo contra D. /Dña. [NOMBRE Y APELLIDOS], cuyas circunstancias constan en los autos principales, según resulta de los siguientes:

HECHOS

PRIMERO.- Que en fecha [FECHA] se dictó por parte del Tribunal resolución aprobando la tasación de costas que condenaba a D. /Dña. [NOMBRE Y APELLIDOS] al pago de [IMPORTE] euros en concepto de costas procesales, la cual no ha fue impugnada por ninguna de las partes, adquiriendo firmeza.

Se acompaña testimonio de la tasación de costas practicada en fecha [FECHA] y de la resolución de fecha [FECHA]

SEGUNDO.- Que habiendo transcurrido el plazo prevenido en el art. 548 LEC sin que se haya hecho efectiva la deuda por la parte condenada al pago, es por lo que se interesa su ejecución.

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA.

Según el art. 545.1 LEC, será competente para la ejecución de resoluciones judiciales, el tribunal que conoció del asunto en primera instancia.

Por eso se presenta esta demanda ante el Tribunal al que me honro en dirigirme, por ser el que conoció del asunto en primera instancia.

II.- LEGITIMACIÓN.

Concurre legitimación ordinaria directa ejecutiva, activa y pasiva, según lo dispuesto en el art. 538 LEC, conforme al que es parte en el proceso de ejecución la persona o personas que piden y obtienen el despacho de la ejecución, y la persona o personas frente a las que ésta se despacha, añadiendo que sólo podrá despacharse ejecución a instancia de quien aparezca como acreedor en el título ejecutivo, y frente a quien aparezca como deudor en el mismo título.

Tratándose de la ejecución de una resolución judicial firme, es obvio que mi patrocinado es el acreedor y la demandada es la deudora, tal y como concluye la parte dispositiva de la sentencia dictada en el juicio.

III.- POSTULACIÓN.

Conforme a lo dispuesto en el art. 539.1 LEC, la demanda viene autorizada por abogado y procurador, ya que estamos ante la ejecución de una resolución dictada en un proceso en que es preceptiva la intervención de dichos profesionales, estando el apoderamiento documentado en el proceso de declaración.

IV.- TÍTULO DE EJECUCIÓN.

El art. 517.2.1º LEC enumera como uno de los títulos que lleva aparejada ejecución la sentencia de condena firme, así como el art. 517.2.9º a las demás resoluciones judiciales que legalmente llevan aparejada ejecución, estableciendo el art. 242.1 LEC, que cuando hubiere condena en costas, luego que sea firme, se procederá a su exacción por el procedimiento de apremio, previa su tasación.

V.- REQUISITOS FORMALES.

La presente demanda contiene todos los requisitos enumerados en el art. 549 LEC, ya que se ha indicado cual es el título en que se funda, la tutela ejecutiva que se pretende y la persona frente a la que se interesa el despacho de la ejecución, así como las medidas de localización e investigación de los bienes del ejecutado. Por último, se acompaña a la demanda ejecutiva la documentación necesaria de la contemplada en el art. 550 del mismo texto legal.

VI.- INTERESES.

Conforme a lo establecido en el art. 576 LEC, desde que fuere dictada sentencia en primera instancia, toda sentencia o resolución que condene al pago de una cantidad de dinero líquida determinará, a favor del acreedor, el devengo de un interés anual igual al del interés legal del dinero incrementado en dos puntos o el que corresponda por pacto de las partes o por disposición especial de la ley, lo cual debe entenderse desde la resolución judicial firme que liquida la condena ilíquida.

VII.- COSTAS.

En virtud de lo dispuesto en el art. 539.2 en relación con el 583 LEC, las costas de esta ejecución deberán ser impuestas a la ejecutada, ya que ha sido quien ha originado la necesidad de este procedimiento al no haber cumplido con lo establecido en la sentencia recaída y en las tasación practicada en las presentes actuaciones.

De conformidad con lo anteriormente expuesto,

SUPLICO AL TRIBUNAL:

Que teniendo por presentado este escrito con los documentos que lo acompañan, y sus copias, se acuerde, sin necesidad de previo requerimiento al deudor, se dicte auto conteniendo la orden general de ejecución y despachando la misma, en el que conforme al art. 551.2.3º LEC fije la cantidad reclamada conforme a lo solicitado en la cantidad de [IMPORTE] euros en concepto de principal, más la cantidad de [IMPORTE] euros en concepto de intereses, gastos y costas.

OTROSÍ DIGO: Que desconociendo esta parte bienes que puedan ser objeto de embargo por parte de este Tribunal, al amparo de lo dispuesto en el artículo 590 LEC, esta parte solicita que, una vez dictado el auto general de ejecución y de conformidad con el art. 551.3.2º LEC, el Tribunal proceda a dirigirse a los efectos de determinación de la relación de bienes muebles e inmuebles, así como depósitos o imposiciones a plazo fijo que el ejecutado pueda tener a su nombre a los siguientes organismos:

1. Gerencia Territorial del Catastro de [COMPLETAR]
2. Delegación Territorial de la Agencia Tributaria de [COMPLETAR]
3. Registro de la Propiedad de [COMPLETAR]
4. Jefatura Provincial de Tráfico de [LOCALIDAD]
5. Caja de Ahorros Provincial de [COMPLETAR]

Por lo que, nuevamente

SUPLICO AL TRIBUNAL

que se dicte decreto procediéndose a adoptar las medidas de localización y averiguación de bienes solicitadas.

Es justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

	Firma de Procurador/a
