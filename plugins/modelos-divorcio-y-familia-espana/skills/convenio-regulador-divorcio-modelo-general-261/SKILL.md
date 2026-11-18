---
name: convenio-regulador-divorcio-modelo-general-261
description: "Redacta el escrito «Convenio regulador de divorcio: modelo general» (formulario 261 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Convenio regulador de divorcio: modelo general

> Formulario 0261 del plugin **Familia** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Modelo de convenio regulador sin cláusula sobre animales de compañía: el art. 90.1.b) bis CC (Ley 17/2021, BOE-A-2021-20727) la exige cuando existan.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LOCALIDAD (4 veces)
- [ ] CALLE
- [ ] DESCRIBIR
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] IMPORTE (11 veces)
- [ ] NÚMERO (2 veces)
- [ ] Otros 38 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…eforma de la LO 1/2025. Que suscriben en»; «…a»; «… Que D. y Dña. contrajeron matrimonio en»; «…el»; «…al Tomo»; «…al Tomo [COMPLETAR], página»; «…, página [COMPLETAR] de la Sección»; «…(NÚMERO) hijos: - el»; «…al Tomo»; «…al Tomo [COMPLETAR], página»; «…, página [COMPLETAR] de la Sección»; «…de la Sección [COMPLETAR]. - el»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 154 del Código Civil
- artículo 156 del Código Civil

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

### Formulario 0261 · Convenio regulador de divorcio: modelo general

- Año del modelo: 2020
- Revisión 17-11-2026: 48 campos de relleno marcados en blanco; 12 huecos del original que se habían perdido sin marca, marcados (IMPORTE, NOMBRE Y APELLIDOS)
- Avisos de la revisión: Modelo de convenio regulador sin cláusula sobre animales de compañía: el art. 90.1.b) bis CC (Ley 17/2021, BOE-A-2021-20727) la exige cuando existan.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma de la LO 1/2025.

Que suscriben en [COMPLETAR] a [COMPLETAR] los cónyuges:

Intervienen ambos en su propio nombre y derecho, reconociéndose mutuamente la capacidad legal necesaria para suscribir la presente PROPUESTA DE CONVENIO REGULADOR DE DIVORCIO a cuyo efecto

EXPONEN

1º.- Que D. y Dña. contrajeron matrimonio en [COMPLETAR] el [COMPLETAR] bajo el régimen económico matrimonial de gananciales, tal y como consta en el Registro Civil de [LOCALIDAD] al Tomo [COMPLETAR], página [COMPLETAR] de la Sección [COMPLETAR].

2º.- Que de esa unión han nacido en [LOCALIDAD] (NÚMERO) hijos:

- el [COMPLETAR], tal y como consta en el Registro Civil de [LOCALIDAD] al Tomo [COMPLETAR], página [COMPLETAR] de la Sección [COMPLETAR].

- el [COMPLETAR], tal y como consta en el Registro Civil de [LOCALIDAD] al Tomo [COMPLETAR], página [COMPLETAR] de la Sección [COMPLETAR].

3º.- Que el domicilio familiar ha estado situado en C/ [CALLE] de [COMPLETAR]

4º.- Que los comparecientes han decidido poner fin a su vida en común y presentar demanda de disolución del matrimonio por divorcio, a cuyo fin suscriben la presente propuesta de convenio regulador de sus relaciones futuras y de ambos con sus hijos, que someten a aprobación judicial, con los siguientes

ACUERDOS

PRIMERO.- PATRIA POTESTAD

La patria potestad sobre [DESCRIBIR] y [COMPLETAR] se ejercerá por ambos progenitores conforme establece el art. 154 del Código Civil. Este ejercicio conjunto supone que las decisiones importantes relativas a dichos menores serán adoptadas por ambos progenitores de mutuo acuerdo, y en caso de discrepancia resolverá el tribunal conforme al trámite previsto en el artículo 156 del Código Civil. A título indicativo y no excluyente son decisiones incluidas en el ámbito de la patria potestad las relativas a las siguientes cuestiones:

a) Cambio de domicilio de los menores fuera del municipio de residencia habitual y traslado al extranjero, salvo viajes vacacionales.

b) Elección inicial o cambio de centro escolar.

c) Actos médicos no urgentes que supongan intervención quirúrgica o tratamiento médico de larga duración o psicológicos o de carácter no necesario.

SEGUNDO.- GUARDA Y CUSTODIA DE LOS HIJOS MENORES. RÉGIMEN DE VISITAS y COMUNICACIONES:

La guarda y custodia de los menores se atribuye a la madre, Dña. [NOMBRE Y APELLIDOS]

Se establece a favor del padre, D. el régimen de visitas siguiente:

2.1.- VISITAS EN PERÍODO ORDINARIO: Los hijos estarán con su padre fines de semana alternos desde el viernes a la salida del centro escolar, donde las recogerá, hasta el domingo a las 20,30 horas que serán entregadas en el domicilio de la madre. Cuando resulte necesario, el padre recogerá en la vivienda materna el equipaje de los menores.

Los puentes escolares se unirán al fin de semana más próximo para que en ese tiempo también estén con el progenitor a quien le corresponda estar con los hijos ese fin de semana. Si correspondiera al padre, les recogerá a la salida del colegio del día lectivo anterior al puente, y los reintegrará al domicilio de la madre el domingo o último día festivo a las 20,30 horas.

El padre estará con los menores la tarde de los [COMPLETAR] de la semana en que le corresponda estar con sus hijos el fin de semana, y la tarde de los [COMPLETAR] de la semana que no le corresponda estar con sus hijas el fin de semana, ambos días desde la salida del colegio hasta las 20,30 horas, comiendo en todo caso con ellas.

2.2.- VACACIONES Y PERÍODOS EXTRAORDINARIOS: Estos periodos interrumpen el régimen de visitas ordinario (semanal e intersemanal).

1.- Vacaciones de Navidad: se dividirán en dos periodos: el primero se iniciará el último día de clase previo a las vacaciones a la salida del Colegio y concluirá el día 30 de diciembre a las 20,30 horas; y el segundo comenzará el día 30 de diciembre a las 20,30 horas y concluirá el día inmediatamente anterior al reinicio de las clases a las 20,30 horas. El día de Reyes tendrá un régimen especial como se señala más adelante.

2.- Vacaciones de Semana Santa: se dividen en dos períodos de igual duración. El primer período comienza el último día de clase a la salida del centro educativo y concluye el día intermedio a las 20.30 horas El segundo comienza el día intermedio a las 20,30 horas y finaliza el día anterior al inicio de las clases a las 20,30 horas.

3.- Vacaciones de verano: se dividen en dos períodos. El primero comprende los días de junio sin actividad escolar desde el primer día no lectivo hasta el 30 de junio a las 20,30 horas y las segundas quincenas de los meses de julio y agosto desde el 16 de cada mes a las 15,00 horas al 31 a las 20,30 horas; y el segundo período comprende las dos primeras quincenas de los meses de julio y agosto desde el 30 de junio a las 20,30 horas al 16 de julio a las 15,00 horas y desde el 31 de julio a las 20,30 horas al 16 de agosto a las 15,00 horas y los primeros días de septiembre hasta el día anterior al inicio de las clases a las 20,30 horas.

4.- Día Del Padre.- En caso de que este día no coincida con uno de los días en que el padre disfrute de sus hijos, éste podrá tenerles en su compañía desde las 12,00 hasta las 20.30 horas, en caso de que fuera festivo; y en caso de que sea laborable desde que salgan del colegio hasta las 20.30 horas, recogiéndoles y entregándoles en el domicilio de su madre.

5.- Día De La Madre: En caso de que este día coincida con uno de los domingos en que el padre disfrute de sus hijos, se cambiará este fin de semana por el inmediatamente anterior o posterior, a elección del padre, sin alterar posteriormente el orden de visitas que se está llevando a cabo.

6.- Cumpleaños De las Menores: El progenitor que no esté con los hijos podrá comer o cenar con ellos a su elección siempre que la familia esté en [COMPLETAR]

7.- Dia 6 de enero: Este día el progenitor no custodio en tal momento tendrá derecho a tenerles en su compañía desde las 17,00 horas hasta reintegrarles a las 20,30 horas del mismo día.

Notas comunes al régimen de visitas:

A) Las entregas y recogidas de los menores se realizarán en el domicilio de la progenitora custodia, a excepción de las que se realicen en el colegio.

B) En todos los periodos vacacionales, y/o en cualquier momento en el que un progenitor pretenda efectuar desplazamiento con pernocta fuera del territorio nacional deberá indicar al otro el lugar en que se encuentra con sus hijos.

C) La madre custodia avisará al padre con al menos un día de antelación de cualquier hecho justificado y acreditado que impida el desarrollo de las visitas, como pueda ser enfermedad de un hijo, pudiendo elegir el padre la fecha de la sustitución de esa concreta visita.

D) Los progenitores podrán comunicarse libremente con los menores por vía telefónica o telemática cuando se encuentren con el otro progenitor, facilitando éste los medios necesarios a este fin, y respetando en todo caso sus actividades y horarios de descanso.

E) En caso de que no existiera acuerdo sobre los periodos en que estará cada uno con los hijos, los años pares elegirá la madre y los impares el padre cada uno de los periodos, comunicándoselo al otro, como mínimo con dos meses de antelación.

TERCERO.- PENSIÓN DE ALIMENTOS

: El padre contribuirá a los alimentos de los hijos con la cantidad de [IMPORTE] (00€) al mes para cada hijo. Esta cantidad se abonará por anticipado dentro de los cinco primeros días de cada mes en la cuenta que la madre designe al efecto y su importe se actualizará anualmente, sólo si es al alza, aplicando a la cifra que cada año esté en vigor el IPC elaborado por el INE de los doce meses anteriores desde el mes en que se dicte la sentencia aprobando este convenio.

Se entiende por gastos extraordinarios los de tratamiento médico con prescripción facultativa, no cubiertos por el sistema público de salud, las clases que deban recibir para refuerzo o apoyo escolar recomendadas o prescritas por el centro educativo por problemas de aprendizaje o deficiente rendimiento académico.

Cuando se plantee la necesidad de estos gastos, deberá comunicarse de forma que deje constancia al otro progenitor la necesidad de realizar el gasto. Se fija como medio de notificación el whatsapp de ambos. En esta comunicación se deberá detallar cuál es el gasto concreto que precisen los hijos, adjuntando presupuesto o factura/recibo si se ha tenido que abonar por motivos de urgencia, donde figure el nombre del profesional que lo expide.

Los gastos extraordinarios serán sufragados al 50% por cada progenitor.

CUARTO.- USO DE LA VIVIENDA FAMILIAR Y AJUAR

.- Se atribuye el uso de la vivienda familiar y del ajuar doméstico a la madre para que viva en ella con sus hijas, por adquirir la plena titularidad de la finca conforme se expone en el Acuerdo Sexto.

El padre sacará de la vivienda sus muebles privativos y enseres de uso personal y abandonará la misma en el plazo máximo de 15 días desde la ratificación del acuerdo.

QUINTO.- PENSIÓN COMPENSATORIA

.- Los esposos pactan expresamente SI/NO reclamarse mutuamente cantidad alguna por el concepto de indemnización por desequilibrio ni pensión compensatoria, al tener cada uno de ellos capacidad económica suficiente y sí/no suponer a ninguno de ellos desequilibrio económico el presente divorcio.

SEXTO.- LIQUIDACIÓN DEL RÉGIMEN ECONÓMICO MATRIMONIAL DE GANANCIALES Y EXTINCIÓN DE CONDOMINIO

. La sentencia de divorcio determinará la disolución de este régimen económico matrimonial, que acuerdan las partes liquidar, junto con el condominio de la vivienda familiar, de la manera que a continuación se expone.

Sexto Primero.- Extinción de condominio de la vivienda común.

La vivienda que ha constituido el domicilio familiar fue adquirida en estado de solteros con carácter privativo y en proindiviso por partes iguales y cuya descripción es la que sigue:

“Vivienda: Esta vivienda se encuentra calificada como vivienda de protección pública VPC en expediente. Referencia catastral [COMPLETAR].

Valorada en [IMPORTE] €.

Cargas: Libre de arrendamientos, pero gravada con préstamo hipotecario suscrito con la [COMPLETAR] mediante subrogación del préstamo según consta en la escritura pública otorgada ante el Notario de [COMPLETAR] D. el [COMPLETAR] al número [NÚMERO] de su protocolo.

Queda un capital pendiente de amortizar de [IMPORTE] €.

Neto: Activo menos pasivo de privativo en proindiviso €.

1.- En este documento, los copropietarios acuerdan extinguir el condominio de la vivienda familiar de la que son titulares con carácter privativo y en proindiviso y que ostentan sobre la finca anteriormente descrita. Por tratarse de un bien indivisible, y con la expresa autorización de la [COMPLETAR] que se acompaña, consienten en extinguir el condominio y adjudicar el pleno dominio a Dª [COMPLETAR] así como la carga hipotecaria que acompaña a la vivienda, abonando el exceso en dinero a D. por su participación en la finca registral nº [NÚMERO] descrita con la cantidad de [IMPORTE] euros (000€).

2.- En caso de que fuera necesario otorgar escritura complementaria o subsanatoria para la extinción de condominio de la vivienda familiar, las partes se comprometen a comparecer a su otorgamiento en la fecha que al efecto se señale por la adquirente.

3.- Hasta el momento de inscripción de la vivienda a favor de Dña. [NOMBRE Y APELLIDOS], se pacta que ambos copropietarios contribuirán por mitad al pago de los gastos comunes de propiedad, esto es: cuota mensual de hipoteca, IBI, seguro y derramas extraordinarias.

4.- Desde el mismo momento en que se ratifique el convenio los gastos de consumos y uso de la vivienda, serán abonados en exclusiva por Dª [COMPLETAR], suscribiendo los oportunos contratos a su nombre.

Sexto Segundo.- Liquidación de la sociedad de gananciales.

Constituye el Activo ganancial:

1º.- Vehículo valorado en [IMPORTE] €

2º.- Vehículo Volkswagen [COMPLETAR] valorado en [IMPORTE] €

3º.- Saldo en la cuenta [COMPLETAR]

4º.- Fondo de inversión con valor [COMPLETAR]

VALOR DEL ACTIVO: [IMPORTE] €

Constituye el PASIVO ganancial:

1º.- Préstamo para la adquisición del vehículo [COMPLETAR] pendiente de amortizar de [IMPORTE] €.

Neto ganancial: [IMPORTE] €

Corresponde a cada uno por su mitad ganancial, €

ADJUDICACIONES por la liquidación de la sociedad de gananciales:

A) A LA ESPOSA Dª [COMPLETAR]:

1.- El pleno dominio del vehículo valorado en [IMPORTE] €

2.- Mitad del saldo cuenta [COMPLETAR]

3.- Saldo del fondo [COMPLETAR].

A cada uno por su mitad ganancial…………………………………….€

B) AL ESPOSO D. [NOMBRE Y APELLIDOS]:

1.- El pleno dominio del vehículo valorado en [IMPORTE] €

2.- La totalidad del saldo pendiente del préstamo personal €

3.- Mitad del saldo cuenta [COMPLETAR]

4.- Saldo del fondo [COMPLETAR]

A cada uno por su mitad ganancial……………………………………..€

D. asume en exclusiva desde la ratificación judicial del convenio el pago del crédito descrito en el pasivo con las mismas obligaciones descritas para ella en su asunción del préstamo hipotecario que grava la vivienda, liberando a Dña [COMPLETAR] de esta deuda frente a él y frente a la entidad financiera, haciéndose responsable exclusiva de todos los gastos que se pudieran derivar por el impago de esta deuda.

Ambos cónyuges aprueban y ratifican en todas sus partes las operaciones tanto de extinción de condominio como de liquidación de la sociedad conyugal de gananciales, así como de las valoraciones fijadas de mutuo acuerdo.

Los comparecientes manifiestan que con las adjudicaciones resultantes ninguno tiene nada que reclamar al contrario, sin que asimismo existan más bienes de naturaleza ganancial que los expresamente relacionados. En caso de que aparezcan más bienes de naturaleza ganancial, se liquidarán al cincuenta por ciento.

SÉPTIMO.- Ambos cónyuges se obligan a ratificar esta Propuesta de Divorcio en sede judicial cuando fueran requeridos para ello.

OCTAVO.- GASTOS DEL PROCEDIMIENTO JUDICIAL. Los cónyuges de mutuo acuerdo han decidido que la representación en este procedimiento sea por procurador/a conjunto, por lo que convienen expresamente abonar sus honorarios, gastos y suplidos por mitad. Y cada uno abonará exclusivamente los gastos de su letrado.

NOVENO.- ENTRADA EN VIGOR DE LAS MEDIDAS. Las medidas personales pactadas en este documento entrarán en vigor el lunes siguiente a la notificación de la Sentencia de Divorcio, salvo el abandono del domicilio conyugal por parte del padre. De este modo el primer fin de semana siguiente a ese lunes comenzará el régimen de visitas a favor del padre.

Y para que conste y surta los efectos oportunos suscriben el presente documento que consta de diez folios en el lugar y fecha de encabezamiento ……., [COMPLETAR].
