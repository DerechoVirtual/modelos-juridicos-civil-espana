---
name: declaracion-responsable-especial-vulnerabilidad-contra-850
description: "Redacta el escrito «Declaración responsable de especial vulnerabilidad contra el lanzamiento» (formulario 850 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Declaración responsable de especial vulnerabilidad contra el lanzamiento

> Formulario 0850 del plugin **Ejecución civil** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Ley 1/2013 (BOE-A-2013-5073): suspensión de lanzamientos hasta transcurridos 15 años desde su entrada en vigor el 15-5-2013 (es decir, hasta el 15-5-2028) y supuestos de vulnerabilidad del art. 1.2 vigente; revisar el formulario entero.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO (2 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] LOCALIDAD
- [ ] DNI/NIE
- [ ] Nº DE PROCEDIMIENTO
- [ ] SEDE (2 veces)
- [ ] FECHA (3 veces)
- [ ] NÚMERO (2 veces)
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…numeración del juzgado de procedencia).]»; «…tá domiciliado en la vivienda situada en»; «…viviendo con él su familia compuesta por»; «…con ese inmueble con la entidad bancaria»; «…• El conjunto de los ingresos asciende a»; «…. El conjunto de los ingresos asciende a»; «…) El conjunto de los ingresos asciende a»; «…ación económica actual viene derivada de»; «… familia, la declaración de invalidez de»; «…, el fallecimiento de»; «…, el divorcio»

## Correcciones de la revisión (8)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Ley 1/2013

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

### Formulario 0850 · Declaración responsable de especial vulnerabilidad contra el lanzamiento

- Año del modelo: 2013
- Revisión 17-11-2026: 8 citas normativas corregidas tras comprobarlas en el BOE; 22 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)
- Avisos de la revisión: Ley 1/2013 (BOE-A-2013-5073): suspensión de lanzamientos hasta transcurridos 15 años desde su entrada en vigor el 15-5-2013 (es decir, hasta el 15-5-2028) y supuestos de vulnerabilidad del art. 1.2 vigente; revisar el formulario entero.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD] y DNI nº [DNI/NIE] declara bajo su responsabilidad y para solicitar la suspensión del lanzamiento de su vivienda derivada del juicio hipotecario nº [Nº DE PROCEDIMIENTO]/[AÑO] que se sigue ante el Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], que los datos que suscribe a continuación son ciertos:

1º. Que está domiciliado en la vivienda situada en [COMPLETAR] conviviendo con él su familia compuesta por [COMPLETAR].

2º. Que adquirió esa vivienda mediante contrato de compraventa en fecha [FECHA] suscribiendo préstamo hipotecario para el pago de su precio y garantizado con ese inmueble con la entidad bancaria [COMPLETAR] en fecha [FECHA]. La garantía del préstamo hipotecario recae sobre la única vivienda en propiedad del deudor y fue concedido para su adquisición.

3º. Que al haber resultado imposible hacer frente al pago de los recibos mensuales por la entidad bancaria se promovió juicio ejecutivo hipotecario que se tramitó con el nº [NÚMERO] ante el Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO] en el que se dictó sentencia estimatoria de la demanda.

4º. En fecha [FECHA] se dictó auto por el que la parte actora se adjudicaba el inmueble en pago de la deuda contraída. (Si/No) se ha acordado el lanzamiento.

5º. Cumple quien suscribe y su unidad familiar los requisitos personales que exige la Ley 1/2013, de 14 de mayo, de medidas para reforzar la protección a los deudores hipotecarios.

En concreto:

Nos encontramos en situación de especial vulnerabilidad por ser: (Opciones):

a) Familia numerosa, de conformidad con la legislación vigente.

b) Unidad familiar monoparental con al menos un hijo a cargo. [NOTA DE REVISIÓN: Texto vigente del art. 1.2.b) Ley 1/2013. Fuente: Ley 1/2013, art. 1.2, BOE-A-2013-5073.]

c) Unidad familiar de la que forme parte un menor de edad. [NOTA DE REVISIÓN: Texto vigente del art. 1.2.c) Ley 1/2013. Fuente: Ley 1/2013, art. 1.2, BOE-A-2013-5073.]

d) Unidad familiar en la que alguno de sus miembros tenga reconocido un grado de discapacidad igual o superior al 33 por ciento [NOTA DE REVISIÓN: Texto vigente del art. 1.2.d) Ley 1/2013. Fuente: Ley 1/2013, art. 1.2, BOE-A-2013-5073.], situación de dependencia o enfermedad que le incapacite acreditadamente de forma permanente para realizar una actividad laboral.

e) Unidad familiar en la que el deudor hipotecario se encuentre en situación de desempleo. [NOTA DE REVISIÓN: Art. 1.2.e) Ley 1/2013 vigente: ya no exige haber agotado las prestaciones. Fuente: Ley 1/2013, art. 1.2, BOE-A-2013-5073.]

f) Unidad familiar con la que convivan, en la misma vivienda, una o más personas que estén unidas con el titular de la hipoteca o su cónyuge por vínculo de parentesco hasta el tercer grado de consanguinidad o afinidad, y que se encuentren en situación personal de discapacidad, dependencia, enfermedad grave que les incapacite acreditadamente de forma temporal o permanente para realizar una actividad laboral.

g) Unidad familiar en la que exista una víctima de violencia de género. [NOTA DE REVISIÓN: Texto vigente del art. 1.2.g) Ley 1/2013. Fuente: Ley 1/2013, art. 1.2, BOE-A-2013-5073.]

h) El deudor mayor de 60 años. [NOTA DE REVISIÓN: Art. 1.2.h) Ley 1/2013 (letra duplicada en el formulario). Fuente: Ley 1/2013, art. 1.2, BOE-A-2013-5073.]

6º. Igualmente nos encontramos incluidos dentro de los límites de ingresos de la unidad familiar que exige la norma para aplicar este beneficio de la suspensión del lanzamiento ya que

(Opciones):

• El conjunto de los ingresos asciende a [COMPLETAR] y, por tanto, no supera el límite de tres veces el Indicador Público de Renta de Efectos Múltiples anual de catorce pagas, incrementado en su caso por cada hijo a cargo. [NOTA DE REVISIÓN: Art. 1.3.a) Ley 1/2013: IPREM anual de 14 pagas; +0,15 IPREM por hijo en familias monoparentales y +0,10 en las demás. Fuente: Ley 1/2013, art. 1.3, BOE-A-2013-5073.]

• (Si alguno de los miembros está en situación personal de discapacidad, dependencia o enfermedad grave). El conjunto de los ingresos asciende a [COMPLETAR] y, por tanto, no supera el límite de cuatro veces el Indicador Público de Renta de Efectos Múltiples.

• (Si el ejecutado padece parálisis cerebral, enfermedad mental o discapacidad intelectual, con un grado de discapacidad reconocido igual o superior al 33 por ciento, o discapacidad física o sensorial, con un grado de discapacidad reconocido igual o superior al 65 por ciento, o enfermedad grave que incapacite acreditadamente, a la persona o a su cuidador, para realizar una actividad laboral) El conjunto de los ingresos asciende a [COMPLETAR] y, por tanto, no supera el límite de cinco veces el Indicador Público de Renta de Efectos Múltiples.

Nuestra situación económica actual viene derivada de [COMPLETAR] (la pérdida de empleo, del cabeza de familia, la declaración de invalidez de [COMPLETAR], el fallecimiento de [COMPLETAR], el divorcio [COMPLETAR]) que se produjo en fecha … (meses o años siempre dentro de los cuatro años anteriores al momento de la solicitud), razón por la que la unidad familiar ha sufrido una alteración significativa de sus circunstancias económicas, en términos de esfuerzo de acceso a la vivienda, resultando que el importe mensual de la cuota hipotecaria resulta superior al 50 por ciento de los ingresos netos que percibe el conjunto de los miembros de la unidad familiar.

Y para que conste y surta los efectos oportunos suscribe la presente declaración responsable en el lugar y fecha del encabezamiento.

========================================================================
