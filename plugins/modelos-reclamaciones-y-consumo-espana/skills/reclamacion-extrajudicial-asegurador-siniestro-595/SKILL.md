---
name: reclamacion-extrajudicial-asegurador-siniestro-595
description: "Redacta el escrito «Reclamación extrajudicial al asegurador por siniestro de circulación» (formulario 595 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reclamación extrajudicial al asegurador por siniestro de circulación

> Formulario 0595 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] FECHA (2 veces)
- [ ] Nº (3 veces)
- [ ] MARCA/MODELO (6 veces)
- [ ] MATRÍCULA (3 veces)
- [ ] NÚMERO
- [ ] DESCRIBIR (3 veces)
- [ ] IMPORTE (2 veces)
- [ ] LUGAR
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…c/ A/A Compañía de Seguros»; «…a las [Nº] horas, en»; «…), asegurado por la Compañía»; «…vil obligatoria cubierta por la Compañía»; «…días, quedándome como secuelas»

## Elecciones que hay que hacer

- el / la

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Real Decreto Legislativo 8/2004
- Ley 35/2015

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

### Formulario 0595 · Reclamación extrajudicial al asegurador por siniestro de circulación

- Año del modelo: 2016
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (4); 1 desplegables convertidos en elección en blanco; 30 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Reclamación extrajudicial a compañía aseguradora previa a la presentación en vía civil de la demanda judicial reclamando la indemnización.

D./Dña. [NOMBRE Y APELLIDOS]

c/

A/A

Compañía de Seguros [COMPLETAR]

c/

Muy Sres. Míos (1):

El objeto de la presente es poner en su conocimiento los siguientes hechos.

El día [FECHA] a las [Nº] horas, en [COMPLETAR], cuando conducía el vehículo marca [MARCA/MODELO], modelo [MARCA/MODELO], matrícula [MATRÍCULA], del que soy propietario (en su caso, de titularidad de D./Dña. [NOMBRE Y APELLIDOS]), asegurado por la Compañía [COMPLETAR] con póliza de seguro n.º [NÚMERO], sufrí un accidente de tráfico consistente en [DESCRIBIR] al colisionar con el vehículo marca [MARCA/MODELO], modelo [MARCA/MODELO], matrícula [MATRÍCULA], conducido por D./Dña. [NOMBRE Y APELLIDOS], con cobertura de responsabilidad civil obligatoria cubierta por la Compañía [COMPLETAR] a la que me dirijo, con n.º [Nº] de póliza

El accidente fue causado por el vehículo asegurado por su Compañía, que era conducido por D./Dña. [NOMBRE Y APELLIDOS], según consta en la copia de parte amistoso que acompaño a la presente (en su caso, informe o atestado policial).

A consecuencia del accidente, he sufrido los siguientes daños:

— daños en el vehículo de mi propiedad, marca [MARCA/MODELO], modelo [MARCA/MODELO], matrícula [MATRÍCULA] consistentes en [DESCRIBIR], cuyo coste de reparación se reclama, y cuyo importe asciende a [IMPORTE] euros, más los gastos de grúa por transporte desde el lugar del accidente al taller de reparación por la cantidad de [IMPORTE] euros, según se acredita con las correspondientes facturas que se acompañan.
— lesiones consistentes en [DESCRIBIR], por la que tardé en curar [Nº] días, quedándome como secuelas [COMPLETAR], y por las que deberé ser indemnizado/a con arreglo a los criterios del Título IV y dentro de los límites indemnizatorios fijados en el Anexo del Texto refundido de la Ley sobre Responsabilidad Civil y Seguro en la Circulación de Vehículos a Motor, aprobado por Real Decreto Legislativo 8/2004, de 29 de octubre-TRLRCSCVM-, en su redacción dada por la Ley 35/2015, de 22 de septiembre, según el siguiente desglose: (2)

Acredito todo ello aportando informe pericial médico emitido por [ELEGIR: el / la]

Dr.
Dra.
 D./Dña. [NOMBRE Y APELLIDOS], especialista en valoración del daño corporal (3)

Pongo estos hechos en su conocimiento a los efectos previstos en el citado Texto Refundido (4).

Por tanto, de conformidad con lo dispuesto en el artículo 7 TRLRCSCVM, efectuamos la presente reclamación previa, a los efectos que en dicho precepto se recogen, y, en especial a la generación de los debidos intereses por parte de esa Compañía de seguros.

A la espera de sus noticias sobre el particular, reciba un cordial saludo, atentamente

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma	Firma

NOTAS DEL FORMULARIO

(1) La reclamación que recoge el modelo es presupuesto procesal para la presentación en vía civil de la demanda judicial reclamando la indemnización, disponiendo el art. 7.8 TRLRCSCVM que "No se admitirán a trámite, de conformidad con el artículo 403 de la Ley de Enjuiciamiento Civil, las demandas en las que no se acompañen los documentos que acrediten la presentación de la reclamación al asegurador". Ahora bien, la obligación de presentar reclamación previa frente a la aseguradora, es aplicable sólo a los accidentes ocurridos a partir del 1 de enero de 2016 (AAP Girona de 20 de mayo de 2016).

(2) Si ya existe sanidad se indicará el importe de la reclamación, en caso contrario se darán los datos para que en su momento se pueda calcular.

(3) En su caso, acompañando informes emitidos por médicos asistenciales -ej. informes de alta-.

(4) El art. 7.1 TRLRCSCVM especifica el contenido mínimo de la reclamación extrajudicial a realizar por el perjudicado al asegurador, con carácter previo a la interposición de la demanda judicial, que deberá contener "la identificación y los datos relevantes de quien o quienes reclamen, una declaración sobre las circunstancias del hecho, la identificación del vehículo y del conductor que hubiesen intervenido en la producción del mismo de ser conocidas, así como cuanta información médica asistencial o pericial o de cualquier otro tipo tengan en su poder que permita la cuantificación del daño".

Además, indica el citado precepto que en la reclamación comunicando el siniestro al asegurador, deberá solicitarse la "indemnización que corresponda".

¿Supone esto que es necesario que la reclamación contenga una pretensión indemnizatoria concreta? Lo que se ha venido interpretando hasta ahora es que, al menos respecto de los daños corporales, la pretensión puede ser concreta o inconcreta, esto es, debe contener una reclamación desglosada y detallada de los distintos conceptos y cuantías exigidas o bien una petición genérica de indemnización. Todo dependerá del estado en que se halle el lesionado en el momento en que se efectúa la reclamación, pues si ha finalizado el proceso curativo los mandatos de la buena fe y de la lógica exigirían que la reclamación sea clara, precisa y detallada con arreglo a los criterios y dentro de los límites indemnizatorios fijados en el TRLRCSCVM, no así si aquél ha comenzado o está en curso, pues la indeterminación del daño impediría tal clase de reclamación.

La reclamación puede ser efectuada directamente por el perjudicado o por quien actúe en su representación, y puede referirse tanto a daños materiales como a daños personales.

En fin, no se exigen especiales requisitos formales, en el sentido de que la misma se podrá llevar a cabo por cualquier medio, siempre y cuando deje suficiente constancia de su realización y recepción por parte de la aseguradora (copia sellada por la aseguradora de la reclamación presentada por escrito, envío por burofax con certificación de texto, etc.).

========================================================================
