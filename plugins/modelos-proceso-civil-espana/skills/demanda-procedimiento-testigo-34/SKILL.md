---
name: demanda-procedimiento-testigo-34
description: "Redacta el escrito «Demanda en procedimiento testigo» (formulario 34 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda en procedimiento testigo

> Formulario 0034 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] DNI/NIE
- [ ] LOCALIDAD (2 veces)
- [ ] Nº DE DOCUMENTO
- [ ] Nº DE COLEGIADO/A
- [ ] COLEGIO
- [ ] IMPORTE (3 veces)
- [ ] FECHA (2 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] NÚMERO
- [ ] PROVINCIA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…D.»; «…, Procurador de los Tribunales y de D.»; «…, bajo la dirección Letrada de D.»; «…euros contra la entidad bancaria»; «…, con sucursal abierta al público en»; «…euros y»; «…ECLAMACIÓN DE CANTIDAD contra la entidad»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 438 bis LEC
- art. 519 LEC
- artículo 438 bis LEC
- art. 1.303 CCiv
- Ley Orgánica 6/1985

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

### Formulario 0034 · Demanda en procedimiento testigo

- Año del modelo: 2024
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 24 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda de procedimiento testigo del art 438 bis LEC en relación con el art. 250.1.14º LEC, conforme a reforma del RDL 6/2023, de 19 de diciembre.

Adaptado a la LO 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D. [COMPLETAR], Procurador de los Tribunales y de D. [COMPLETAR], mayor de edad, provisto de DNI nº [DNI/NIE], con domicilio en [LOCALIDAD], como acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], bajo la dirección Letrada de D. [COMPLETAR], Colegiado nº [Nº DE COLEGIADO/A] del Ilustre Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco y como más procedente sea en Derecho DIGO:

Que mediante este escrito y en la representación que ostento, de conformidad con lo dispuesto en el art. 438 bis en relación con el art. 250.1.14º LEC, vengo a interponer demanda (procedimiento testigo) de Juicio Verbal de nulidad de condiciones generales de contratación insertas en contrato de préstamo con garantía hipotecaria y accesoria de reclamación de cantidad por la suma de [IMPORTE] euros contra la entidad bancaria [COMPLETAR], con sucursal abierta al público en [COMPLETAR], en base a los siguientes:

HECHOS

PRELIMINAR.‐

Esta parte hace constar que la presente demanda incluye pretensiones que están siendo objeto de procedimientos anteriores planteados por otros litigantes, que están siendo ventiladas ya en el Tribunal al que tengo el honor de dirigirme, algunos de ellos que afectan directamente a la misma entidad aquí demandada, por lo que de conformidad con lo dispuesto en el art. 438 bis LEC entendemos que procede la suspensión del presente procedimiento hasta que el procedimiento inicial y preferente sea resuelto, al considerar esta parte que no es preciso realizar un control de transparencia de la cláusula ni valorar la existencia de vicios en el consentimiento del contratante y que las condiciones generales de contratación cuestionadas tienen identidad sustancial, procediendo la extensión de los efectos de la sentencia dictada en el procedimiento testigo en los términos establecidos en el art. 519 LEC.

PRIMERO.- El día [FECHA], mi mandante concertó con la entidad bancaria demandada, un préstamo con garantía hipotecaria por un principal de [IMPORTE] euros y [COMPLETAR] cuotas mensuales, con objeto de adquirir una vivienda, gravando el inmueble, sito en [LOCALIDAD] con la referida garantía real. Se acompaña copia del contrato de préstamo, elevado a escritura pública el mismo día en la Notaria de D./Dña. [NOMBRE Y APELLIDOS] como documento n.º [NÚMERO].

En dicho contrato de préstamo, la prestamista predispuso una serie de condiciones generales de contratación, que después de detallarán, que fueron redactadas de manera unilateral, sin negociación previa, simultánea ni coetánea con los demandantes, sin reciprocidad alguna entre los derechos y obligaciones de los intervinientes, vulnerando normas legales e impidiendo al actor —como prestatario y consumidor— valorar las consecuencias de la inclusión de las cláusulas, que interesamos sean declaradas nulas.

Es evidente que las cláusulas que señalaremos y cuya nulidad interesamos reúnen los requisitos previstos en la Ley de las Condiciones Generales de Contratación (LCGC) y en la jurisprudencia desarrollada por el Tribunal Supremo, a los efectos de considerar que deberán reunir los requisitos de contractualidad, predisposición, imposición y generalidad. (STS de 9 de mayo de 2013, rec. 485/2012 y 29 de abril de 2015, rec. 1072/2013).

SEGUNDO.- A los anteriores hechos, son de aplicación los siguientes,

FUNDAMENTOS DE DERECHO

I. ‐ PROCEDIMIENTO TESTIGO.

Es de aplicación al caso el art. 438 bis LEC, el cual dispone que "1. En el caso de las demandas referidas en el artículo 250.1.14.º, sin perjuicio de lo dispuesto en el párrafo primero del apartado primero del artículo 438, el letrado o la letrada de la Administración de Justicia procederá a dar cuenta al tribunal, con carácter previo a la admisión de la demanda, cuando considere que la misma incluye pretensiones que están siendo objeto de procedimientos anteriores planteados por otros litigantes, que no es preciso realizar un control de transparencia de la cláusula ni valorar la existencia de vicios en el consentimiento del contratante y que las condiciones generales de contratación cuestionadas tienen identidad sustancial.

La parte actora y la parte demandada podrán solicitar en su escrito de demanda y contestación, que el procedimiento se someta a la regulación de este artículo, siempre que concurran los presupuestos señalados en el párrafo anterior.

2. Dada cuenta y examinado el asunto, el tribunal dictará auto acordando la suspensión del curso de las actuaciones hasta que se dicte sentencia firme en el procedimiento identificado como testigo o, en su caso, dictará providencia acordando seguir con la tramitación del procedimiento. En caso de que se hubiera dictado el auto acordando la suspensión, junto a su notificación se remitirá copia de aquellas actuaciones que consten en el procedimiento testigo y que, a juicio del tribunal, permitan apreciar las circunstancias establecidas en el apartado primero, quedando unido al procedimiento testimonio de las mismas. La expedición de las copias y del testimonio deberá realizarse de acuerdo con lo previsto en el artículo 236 quinques de la Ley Orgánica 6/1985, de 1 de julio, del Poder Judicial.

El procedimiento testigo se tramitará con carácter preferente".

II.- JURISDICCIÓN Y COMPETENCIA.

Radicando la competencia genérica en el orden civil de la jurisdicción, detenta la competencia objetiva y funcional el Tribunal de Instancia, por aplicación de lo dispuesto en los arts. 85.1º LOPJ y 45 LEC. Asimismo, por acuerdo de la Comisión Permanente del Consejo General del Poder Judicial, de fecha [FECHA], se especializó (confiriendo competencia objetiva) el órgano judicial al que tengo el honor de dirigirme, a fin de conocer en la provincia de [PROVINCIA], de la presente acción individual de condiciones generales de contratación. Concurren, en este sentido, los dos requisitos adicionales requisitos en la acción ejercitada: tiene relación con un préstamo con garantía hipotecaria, y el prestatario, mi cliente, es persona física.

Por último, dado que se pretende la nulidad de una condición general de contratación, y puesto que mi mandante tiene su domicilio en el partido judicial del Tribunal al cual tengo el honor de dirigirme, su situación debe determinar la competencia territorial, conforme al art. 52.1.14.º LEC.

III.- Por todo ello,

SUPLICO AL TRIBUNAL:

Que tenga por presentado este escrito con los documentos que se acompañan y copias de todo ello, se sirva admitirlo, me tenga por parte en la representación que ostento y por promovida DEMANDA DE JUICIO VERBAL DE NULIDAD FUNCIONAL DE CLAUSULAS CONTRACTUALES DE PRÉSTAMO HIPOTECARIO Y ACCESORIA DE RECLAMACIÓN DE CANTIDAD contra la entidad [COMPLETAR], y previos los trámites legales, incluido el recibimiento del pleito a prueba que desde este momento dejo interesado, para el supuesto de que se considere aplicable lo dispuesto en el artículo 438 bis LEC, con carácter principal acuerde la suspensión del procedimiento hasta que se dicte sentencia firme en el procedimiento testigo, y alternativamente, solo para el supuesto de que se considere que no existe identidad para la aplicación del artículo 438 bis LEC, se dicte la correspondiente sentencia por la que:

- Se declare la nulidad de las condiciones generales de la contratación referentes a gastos derivados de la formalización del préstamo hipotecario, intereses ordinarios, comisiones por reclamación de posiciones deudoras, teniéndose por no puestas, condenando a la demandada a estar y pasar por dicha declaración Como consecuencia de la declaración de nulidad, se condene a la demandada a la devolución de los gastos cobrados al demandante en aplicación de la cláusula relativa a los gastos derivados de la formalización del préstamo hipotecario, cuyo montante asciende a [IMPORTE] euros así como a los intereses de dicha cantidad en aplicación de lo dispuesto en el art. 1.303 CCiv.
- Se condene a la demandada al pago de las costas causadas en este procedimiento.

Es Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a	Firma de Procurador/a
