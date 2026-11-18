---
name: cesion-secreto-empresarial-contrato-378
description: "Redacta el escrito «Cesión de secreto empresarial: contrato» (formulario 378 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Cesión de secreto empresarial: contrato

> Formulario 0378 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] NOMBRE DEL REPRESENTADO/A (2 veces)
- [ ] FECHA (3 veces)
- [ ] IMPORTE (2 veces)
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…or de edad, de estado civil, vecino/a de»; «…, domiciliado en»; «…or de edad, de estado civil, vecino/a de»; «…, domiciliado en»; «…DENTE es titular del secreto empresarial»; «…mercantil que tiene por objeto social la»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Real Decreto 1720/2007
- Ley Orgánica 15/1999

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

### Formulario 0378 · Cesión de secreto empresarial: contrato

- Año del modelo: 2019
- Revisión 17-11-2026: 13 campos de relleno marcados en blanco; 7 huecos del original que se habían perdido sin marca, marcados (COMPLETAR, FECHA, IMPORTE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Contrato de licencia de explotación de patente en el cual el licenciatario asume todos los derechos de explotación de la patente que correspondían a su titular, sin que pueda ceder esta licencia a un tercero ni conceder sublicencias

En [LUGAR], a [DÍA] de [MES] de [AÑO].

REUNIDOS

De una parte:

D./D.ª [NOMBRE Y APELLIDOS], mayor de edad, de estado civil, vecino/a de [COMPLETAR], domiciliado en [COMPLETAR], con documento nacional de identidad número

De otra:

D./D.ª [NOMBRE Y APELLIDOS], mayor de edad, de estado civil, vecino/a de [COMPLETAR], domiciliado en [COMPLETAR], con documento nacional de identidad número

INTERVINIENTES

D./D.ª [NOMBRE Y APELLIDOS], en nombre y representación de [NOMBRE DEL REPRESENTADO/A], en lo sucesivo «LA CEDENTE», en virtud de poder otorgado a su favor ante el Notario de D./D.ª [NOMBRE Y APELLIDOS], en fecha [FECHA], con el número de protocolo, poder que se halla debidamente inscrito en el Registro Mercantil de y vigente, según manifiesta.

D./D.ª [NOMBRE Y APELLIDOS], en nombre y representación de [NOMBRE DEL REPRESENTADO/A], en lo sucesivo «EL/LA ADQUIRENTE», en virtud de poder otorgado a su favor ante el Notario de D./D.ª [NOMBRE Y APELLIDOS], en fecha [FECHA], con el número de protocolo, poder que se halla debidamente inscrito en el Registro Mercantil de y vigente, según manifiesta.

Todas las partes, en el respectivo carácter con el que intervienen, se reconocen mutuamente la capacidad legal en Derecho necesaria para concertar el presente CONTRATO DE CESIÓN DE SECRETO EMPRESARIAL, y a tal efecto, libremente y de común acuerdo,

EXPONEN

PRIMERO Que LA CEDENTE es titular del secreto empresarial [COMPLETAR]

SEGUNDO Que el/la ADQUIRENTE es una sociedad mercantil que tiene por objeto social la [COMPLETAR] y está interesado en adquirir el derecho sobre uso del secreto empresarial supra mencionado.

TERCERO Que en vista de lo anterior, ambas partes de común acuerdo llevan a efecto el presente contrato con arreglo a las siguientes:

CLÁUSULAS

OBJETO

Por el presente contrato, LA CEDENTE transmite al ADQUIRENTE la titularidad del secreto empresarial en los términos y condiciones que se detallan en el presente contrato.

PRECIO

El precio de la cesión del secreto descrito en el Exponendo primero se concreta en la cantidad de [IMPORTE] euros ( €) más el Impuesto sobre el Valor Añadido correspondiente, esto es, € ( EUROS) adicionales.

CONDICIÓN SUSPENSIVA

La transmisión de la titularidad se entiende hecha bajo condición suspensiva a favor de LA CEDENTE hasta el momento en que el importe total del precio haya sido satisfecho, esto es, hasta el día [FECHA]

DECLARACIONES Y GARANTÍAS

Sobre la titularidad

LA CEDENTE declara ser la titular registral del secreto y garantiza que ninguna otra persona física o jurídica o entidad de cualquier otra índole ostenta derecho alguno sobre la misma.

Sobre sistemas de inteligencia artificail

Las Partes acuerdan que las cesiones efectuadas en los anteriores apartados se realizan sin la facultad de emplear los derechos cedidos para el entrenamiento, alimentación o aprendizaje automático de ningún sistema de inteligencia artificial ni de tecnologías basadas en esta, entendiéndose por tal, a título enunciativo pero no limitativo, herramientas de generación de lenguaje natural, reconocimiento de voz, plataformas de aprendizaje automático, motores de administración de decisiones, plataformas de aprendizaje profundo, procesos de automatización robóticos, herramientas de análisis de textos y procesamiento de lenguaje natural y cualquier otra tecnología disruptiva relacionada (en adelante y en su conjunto, la "Inteligencia Artificial"). De tal manera que, el uso de los derechos cedidos por mor del presente Contrato para los enunciados usos constituirá un incumplimiento sustancial del mismo. El ADQUIRENTE habrá de respetar el compromiso adquirido en virtud de la anterior Estipulación en los contratos, negocios y relaciones jurídicas que mantenga con terceros, sean personas físicas o jurídicas, adoptando todas las medidas necesarias a tal fin e incluyendo, si fuese necesario, previsiones escritas en los contratos que celebre con estos terceros.

Sobre el pago de las cuotas de mantenimiento

LA CEDENTE se hace responsable de los daños o perjuicios que le ocasione al ADQUIRENTE los eventuales incumplimientos o excepciones a las manifestaciones y garantías vertidas en los párrafos precedentes.

CONDICION RESOLUTORIA

El incumplimiento por el/la ADQUIRENTE de las condiciones de uso del secreto dará lugar a la inmediata resolución del contrato y al abono de una indemnización por daños y perjuicios LA CEDENTE de [IMPORTE] euros.

DEBER DE CONFIDENCIALIDAD

Las Partes se obligan a no revelar, ceder o transferir a terceros ninguna información referente a los negocios, clientes, operaciones, instalaciones, procedimientos, métodos, transacciones, «know-how», o cualquier otro aspecto relacionado con la actividad de la contraparte que pudieran conocer o hayan conocido con motivo de la celebración del presente contrato.

RESOLUCIÓN DEL CONTRATO

El Contrato podrá resolverse por las siguientes causas:

1. Por voluntad de cualquiera de las Partes cuando medie incumplimiento grave de las obligaciones pactadas.

2. Por acuerdo de las Partes por escrito.

3. La extinción de la personalidad jurídica de cualquiera de las Partes o la suspensión de pagos, quiebra, concurso o embargo de bienes de alguna de ellas a menos que se garantice de cualquier forma la deuda.

En cualquier caso, la Parte que pretenda resolver el presente Contrato alegando incumplimiento de la contraparte, deberá requerirle al cumplimiento de la obligación de forma fehaciente, otorgándole un plazo de días a la Parte incumplidora para que pueda subsanar dicho incumplimiento. Transcurrido dicho plazo sin que los incumplimientos hubiesen sido subsanados, el perjudicado podrá ejercitar la mencionada facultad.

En el supuesto de que los incumplimientos fueren de imposible subsanación en el plazo de 30 días, el perjudicado podrá ejercitar directamente la facultad opción, sin necesidad de remitir, previamente, el antedicho requerimiento.

NOTIFICACIONES

Toda notificación que se efectúe entre las partes se hará por escrito y será entregada personalmente o de cualquier otra forma que certifique la recepción por la parte notificada en los respectivos domicilios indicados en el encabezamiento de este Contrato.

Cualquier cambio de domicilio de una de las partes deberá ser notificado a la otra de forma inmediata y por un medio que garantice la recepción del mensaje.

GENERALIDADES

El presente contrato anula y reemplaza cualquier contrato o acuerdo anterior entre las partes con el mismo objeto y sólo podrá ser modificado por un nuevo acuerdo firmado por ambas partes.

Si alguna de las cláusulas del presente contrato fuere declarada nula o inaplicable, dicha cláusula se considerará excluida del contrato, sin que implique la nulidad del mismo. En este caso las partes harán cuanto esté a su alcance para encontrar una solución equivalente que sea válida y que refleje debidamente sus intenciones.

Los encabezamientos de las distintas cláusulas lo son sólo a efectos informativos, y no afectarán, calificarán o ampliarán la interpretación de este Contrato.

En el caso de que el cumplimiento de este Contrato suponga la necesidad de acceder a datos de carácter personal, como encargados del tratamiento, quedamos obligados al cumplimiento de la LO 3/2018, de 5 diciembre, de Protección de Datos Personales y Garantía de los Derechos Digitales y del Real Decreto 1720/2007, de 21 de diciembre, por el que se aprueba el Reglamento de desarrollo de la Ley Orgánica 15/1999 y demás normativa aplicable.

Y en prueba de conformidad y aceptación de cuanto antecede, ambas partes firman los folios del presente CONTRATO DE CESIÓN DE SECRETO EMPRESARIAL, extendido por duplicado y a un solo efecto, en la ciudad y fecha mencionados en el encabezamiento

Fdo. Don/Doña(La cedente)

Fdo. Don/Doña(El/La Adquirente)
