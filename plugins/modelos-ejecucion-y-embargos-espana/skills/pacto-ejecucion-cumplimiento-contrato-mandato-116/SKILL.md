---
name: pacto-ejecucion-cumplimiento-contrato-mandato-116
description: "Redacta el escrito «Pacto de ejecución y cumplimiento de un contrato de mandato» (formulario 116 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pacto de ejecución y cumplimiento de un contrato de mandato

> Formulario 0116 del plugin **Ejecución civil** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] FECHA (6 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] PROVINCIA (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] LOCALIDAD
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, mayor de edad, vecino/a de»; «… con domicilio en la localidad/ciudad de»; «…, mayor de edad, vecino/a de»; «… con domicilio en la localidad/ciudad de»

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

### Formulario 0116 · Pacto de ejecución y cumplimiento de un contrato de mandato

- Año del modelo: 2022
- Revisión 17-11-2026: 17 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [FECHA]

REUNIDOS

De una parte D./Dª [NOMBRE Y APELLIDOS], mayor de edad, vecino/a de [COMPLETAR], con domicilio en la localidad/ciudad de [COMPLETAR], provincia de [PROVINCIA], provisto/a del N.I.F. número [NÚMERO] ( en adelante, EL MANDANTE)

Y de otra parte D./Dª [NOMBRE Y APELLIDOS], mayor de edad, vecino/a de [COMPLETAR], con domicilio en la localidad/ciudad de [COMPLETAR], provincia de [PROVINCIA], provisto/a del N.I.F. número [NÚMERO] (en adelante, EL MANDATARIO)

Ambas partes intervienen EN SU PROPIO NOMBRE a fin de expresar el cumplimiento del contrato de mandato suscrito en fecha [FECHA] a plena satisfacción del MANDANTE, conforme se describirá a continuación, y al efecto

EXPONEN

I. El pasado día [FECHA] ambas partes suscribieron un contrato de mandato especial para la adquisición de la vivienda sita en [LOCALIDAD], actuando el MANDATARIO en su propio nombre por cuenta del MANDANTE, en las condiciones establecidas en dicho contrato.

II. En ejecución de dicho contrato de mandato, el MANDATARIO ha adquirido la citada vivienda por escritura pública de fecha [FECHA] con arreglo a las instrucciones que le fueron dadas por el MANDANTE, la cual se adjunta como ANEXO I de este documento de ejecución y cumplimiento del mandato.

Y siendo interés de ambas partes dejar constancia del cumplimiento del referido contrato a todos los efectos, convienen el presente con arreglo a las siguientes

ESTIPULACIONES

PRIMERA.- EJECUCIÓN DEL MANDATO

En ejecución del contrato de mandato expresado en el expositivo primero, el MANDATARIO transfiere al MANDANTE la plena titularidad de la finca adquirida en su nombre por escritura pública de fecha [FECHA] expresada en el expositivo segundo.

Ambas partes se comprometen a realizar las demás gestiones que, en su caso, sean necesarias para la plena efectividad de la transmisión.

SEGUNDA.- CUMPLIMIENTO DEL MANDATO

El MANDANTE manifiesta expresamente que el contrato de mandato de fecha [FECHA] ha sido cumplido a plena satisfacción por el MANDATARIO, quien ha cumplido todas sus obligaciones con la mayor diligencia, dentro de los límites del mandato y sujetándose en todo momento a las instrucciones del MANDANTE.

Al haber finalizado el mandato por cumplimiento del contrato, el MANDATARIO hace entrega al MANDANTE de los documentos de apoderamiento para realizar el negocio, los cuales son recibidos de conformidad en este mismo acto.

TERCERA.- RENDICIÓN DE CUENTAS

El MANDATARIO afirma haber recibido del MANDANTE todas las cantidades necesarias para la ejecución del mandato.

Ambas partes manifiestan que se ha procedido a la rendición de cuentas, sin que nada tengan que reclamarse recíprocamente por este concepto.

CUARTA.- EFECTOS

El MANDANTE ratifica todos y cada uno de los actos del MANDATARIO realizados en su nombre, aprobando la rendición de cuentas y asumiendo cualquier responsabilidad derivada del negocio concertado.

El MANDATARIO manifiesta expresamente que el MANDANTE ha cumplido con todas sus obligaciones.

Ambas partes hacen constar que no existe ninguna obligación pendiente derivada del cumplimiento del mandato.

Ambas partes se autorizan recíprocamente para dar a conocer este documento a terceros interesados a todos los efectos.

Y en prueba de conformidad, una vez leído el contrato, ambas partes firman el presente documento al que incorpora como ANEXO I la escritura de compraventa descrita en el fundamento segundo, por duplicado y a un solo efecto, en el lugar y fecha indicados en el encabezamiento.

(Firmas de las partes)
