---
name: mediacion-disputas-contrato-1181
description: "Redacta el escrito «Mediación en disputas: contrato» (formulario 1181 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Mediación en disputas: contrato

> Formulario 1181 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] DNI/NIE (2 veces)
- [ ] ESTADO CIVIL
- [ ] PROFESIÓN (2 veces)
- [ ] CALLE (2 veces)
- [ ] Nº (2 veces)
- [ ] TELÉFONO (2 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] FECHA (2 veces)
- [ ] IMPORTE (4 veces)
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, a [DÍA] de [MES] de [AÑO]. REUNIDOS D»; «…, vecindad civil»; «…, profesión [PROFESIÓN] y domiciliado en»; «…, C.P., calle [CALLE], núm. [Nº], piso»; «…, núm. [Nº], piso [COMPLETAR], letra»; «…letra [COMPLETAR], dirección electrónica»; «…, en adelante PARTE MEDIADA (A) D»; «…, vecindad civil»; «…, profesión [PROFESIÓN] y domiciliado en»; «…, C.P., calle [CALLE], núm. [Nº], piso»; «…, núm. [Nº], piso [COMPLETAR], letra»; «…letra [COMPLETAR], dirección electrónica»; …

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 1181 · Mediación en disputas: contrato

- Año del modelo: 2015
- Revisión 17-11-2026: 29 campos de relleno marcados en blanco; 4 huecos del original que se habían perdido sin marca, marcados (FECHA, IMPORTE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [DÍA] de [MES] de [AÑO].

REUNIDOS

D [COMPLETAR], mayor de edad, con DNI [DNI/NIE], vecindad civil [COMPLETAR], estado civil [ESTADO CIVIL], profesión [PROFESIÓN] y domiciliado en [COMPLETAR], C.P., calle [CALLE], núm. [Nº], piso [COMPLETAR], letra [COMPLETAR], dirección electrónica [COMPLETAR], y teléfono [TELÉFONO], en adelante PARTE MEDIADA (A)

D [COMPLETAR], mayor de edad, con DNI [DNI/NIE], vecindad civil [COMPLETAR], profesión [PROFESIÓN] y domiciliado en [COMPLETAR], C.P., calle [CALLE], núm. [Nº], piso [COMPLETAR], letra [COMPLETAR], dirección electrónica [COMPLETAR], y teléfono [TELÉFONO], en adelante PARTE MEDIADA (B)

Y D, mayor de edad, vecindad civil, estado civil, de profesión mediador con número de registro, con domicilio en [LOCALIDAD], dirección de correo electrónico, en adelante EL MEDIADOR

Todos ellos intervienen en su propio nombre y derecho con el fin de desarrollar una mediación para la resolución del conflicto que se describirá a continuación, y al efecto

EXPONEN

I. Entre las PARTES MEDIADAS existe un conflicto derivado del contrato de arrendamiento sobre el local suscrito por ambas partes en fecha [FECHA] otorgado en fecha [FECHA], concretándose la controversia en determinar a quién corresponde la obligación de pago de las obras realizadas por el arrendatario D, PARTE MEDIADA (A), en el local arrendado según contrato, cuyo importe asciende a [IMPORTE] euros.

II. Para solventar dicho conflicto ambas PARTES MEDIADAS pretenden someterlo a mediación, designado a D como MEDIADOR, quien acepta en este acto.

Por lo que convienen concertar el presente contrato de MEDIACIÓN con arreglo a las siguientes

ESTIPULACIONES

Objeto de la mediación

Será objeto de mediación la determinación de la distribución de las obligaciones de pago derivadas de las obras realizadas en el local arrendado sito en [LOCALIDAD], cuyo importe asciende a [IMPORTE] euros, con el siguiente detalle:

(se describirían las obras realizadas)

Procedimiento de mediación

Las PARTES MEDIADAS acuerdan fijar la celebración de una sesión preliminar por separado que será señalada por el MEDIADOR, conviniendo que posteriormente se celebrarán hasta un máximo de cinco sesiones conjuntas a criterio del MEDIADOR.

Las partes acuerdan que el plazo de duración máxima del procedimiento de mediación será de tres meses a contar desde la firma del presente documento, y que podrá prorrogarse durante un mes por mutuo acuerdo de las partes.

El procedimiento de mediación se desarrollará en la localidad de [COMPLETAR] en el lugar que determine el MEDIADOR y la lengua será el castellano.

Derechos y obligaciones de las partes mediadas

Las PARTES MEDIADAS se comprometen a seguir el procedimiento de mediación de buena fe y, en especial, a asistir a las reuniones de mediación; valorar las propuestas del MEDIADOR y proponerle contrapropuestas, en su caso, con la finalidad de obtener acuerdos; y a satisfacer las compensaciones económicas al MEDIADOR, así como los gastos ocasionados por la mediación.

Las PARTES MEDIADAS tienen derecho a dar por terminadas las actuaciones en el curso del procedimiento cuando entiendan que no es posible llegar a un acuerdo.

Derechos y obligaciones del mediador

El MEDIADOR acepta la mediación encomendada en este contrato, obligándose a cumplir su encargo de manera leal y diligente de acuerdo con los principios que rigen la mediación, así como a responder de los daños y perjuicios que pueda ocasionar en la ejecución del contrato.

El MEDIADOR queda sujeto al deber de secreto y confidencialidad.

En contraprestación, el MEDIADOR será remunerado en la cantidad de [IMPORTE] euros.

En concepto de provisión de fondos, cada una de las partes entregan en este acto al MEDIADOR la cantidad de [IMPORTE] euros, sirviendo el presente documento de eficaz carta de pago.

El coste de la mediación se dividirá por igual entre las PARTES MEDIADAS, y se abonará a la finalización del procedimiento.

Conclusión de la mediación

El procedimiento de mediación concluirá por acuerdo o sin alcanzar dicho acuerdo, por ejercicio del derecho a dar por terminadas las actuaciones, por imposibilidad apreciada por el MEDIADOR de llegar a un acuerdo, o por finalización del plazo máximo de duración del procedimiento o, en su caso, de las prórrogas.

En caso de alcanzarse un acuerdo, las PARTES MEDIADAS se comprometen a elevarlo a escritura pública a requerimiento de cualquiera de ellas..

Y en prueba de conformidad, una vez leído el contrato, ambas partes y el mediador firman el presente documento, por triplicado y a un solo efecto, en el lugar y fecha indicados en el encabezamiento..

(Firmas de las partes y del mediador).

========================================================================
