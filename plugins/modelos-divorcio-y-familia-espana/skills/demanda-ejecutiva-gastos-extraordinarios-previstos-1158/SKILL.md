---
name: demanda-ejecutiva-gastos-extraordinarios-previstos-1158
description: "Redacta el escrito «Demanda ejecutiva de gastos extraordinarios previstos en la sentencia de separación o divorcio» (formulario 1158 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda ejecutiva de gastos extraordinarios previstos en la sentencia de separación o divorcio

> Formulario 1158 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] Nº (4 veces)
- [ ] COLEGIO
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] IMPORTE (8 veces)
- [ ] FECHA
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] Nº DE DOCUMENTO (4 veces)
- [ ] Otros 18 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…de»; «…de [COMPLETAR] de»; «…tamiento prescrito. Y como DOCUMENTOS Nª»; «…andante. Requerimiento de pago En fechas»; «…de»; «…de [COMPLETAR] de»; «…de [COMPLETAR] de [COMPLETAR] y»; «…de [COMPLETAR] y [COMPLETAR] de»; «…y [COMPLETAR] de [COMPLETAR] de»; «…adas de esta ejecución, al ejecutado. En»; «…,»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 545.1 LEC
- art. 538 LEC
- art. 539.1 LEC
- artículo 517.2.1 LEC
- artículos 549 y 550 LEC
- artículos 575 y 576 LEC
- arts. 539.2 y 583 LEC
- art. 575.1 LEC

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

### Formulario 1158 · Demanda ejecutiva de gastos extraordinarios previstos en la sentencia de separación o divorcio

- Año del modelo: 2015
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 44 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 4 huecos del original que se habían perdido sin marca, marcados (IMPORTE, Nº, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dª [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dª [NOMBRE Y APELLIDOS], cuya representación tengo acreditada en los autos de juicio de divorcio núm. [Nº], seguidos contra D./Dª [NOMBRE Y APELLIDOS], donde constan el resto de sus datos personales, comparezco en este TRIBUNAL con la asistencia del Letrado D./Dª [NOMBRE Y APELLIDOS], del Ilustre Colegio de Abogados de [COLEGIO], y DIGO:

Que por medio del presente escrito y en la representación que ostento, formulo DEMANDA EJECUTIVA contra D./Dª [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], pta., el resto de cuyas circunstancias constan en los autos principales, en calidad de deudor, según el título ejecutivo que luego se dirá, en reclamación de la suma de [IMPORTE] euros ( €), en concepto de principal, más otros [IMPORTE] euros ( €) para cubrir intereses vencidos, y de otros [IMPORTE] euros ( €) para cubrir intereses y costas de la ejecución (cantidad que se establece por ahora y de forma prudencial, sin perjuicio de ulterior liquidación).

La presente demanda se basa en los siguientes

HECHOS

Título ejecutivo

En fecha [FECHA] de [COMPLETAR] de [COMPLETAR], este Tribunal dictó sentencia de separación/divorcio en autos núm. [Nº DE PROCEDIMIENTO]/[AÑO], en la que se declaró la obligación del/de la demandado/a de satisfacer a mi representado/a la cantidad de [IMPORTE] euros ( €) mensuales, actualizables anualmente de acuerdo con el IPC, en concepto de pensión alimenticia en favor del hijo común cuya guarda y custodia atribuyó la misma sentencia a mi representado/a; así mismo se declaró la obligación de satisfacer ambos progenitores los gastos extraordinarios por mitad, incluyéndose entre tales gastos extraordinarios, de modo expreso, los odontológicos y, en general, los gastos médicos no cubiertos por la Seguridad Social o por los Seguros médicos de que fuera beneficiario el menor. Dicha sentencia constituye el título ejecutivo en que se funda la presente demanda.

Se acompaña, como DOCUMENTO Nº [Nº DE DOCUMENTO], testimonio de la citada sentencia, en que consta su firmeza.

Suma adeudada y concepto en que se adeuda

Hace [Nº] meses se diagnosticó al hijo común el siguiente problema odontológico: (se describe), prescribiéndosele como tratamiento: (se describe). Tal gasto, que tiene carácter necesario, no se haya cubierto por la Seguridad Social ni por el seguro privado del que es beneficiario el menor.

Se acompaña, como DOCUMENTO Nº [Nº DE DOCUMENTO], informe médico y presupuesto del tratamiento prescrito. Y como DOCUMENTOS Nª [COMPLETAR] y Nº [Nº DE DOCUMENTO], facturas correspondientes a los pagos efectuados por mi mandante.

Requerimiento de pago

En fechas [COMPLETAR] de [COMPLETAR] de [COMPLETAR] y [COMPLETAR] de [COMPLETAR] de [COMPLETAR], se requirió al padre/madre del menor para que abonase la mitad del referido gasto, primero por vía telefónica y después por burofax, sin que se haya atendido tal requerimiento ni se haya dado respuesta alguna.

Se acompaña, como DOCUMENTO Nº [Nº DE DOCUMENTO], burofax por medio del cual se efectuó el citado requerimiento.

Demanda ejecutiva

Dado que la parte demandada no ha abonado la suma correspondiente al 50% del citado gasto, procedemos a interponer la presente demanda ejecutiva, de acuerdo con los siguientes

FUNDAMENTOS DE DERECHO

Competencia

Es competente el Tribunal al que me dirijo, conforme a lo dispuesto en el artículo 545.1 LEC, al haber conocido del procedimiento de separación/divorcio en el que se dictó la sentencia cuya ejecución se solicita.

Legitimación

Concurre legitimación activa y pasiva en las partes demandante y demandada, conforme a lo dispuesto en el art. 538 LEC. Dispone ésta norma que son parte en el proceso de ejecución la persona o personas que piden y obtienen el despacho de la ejecución y la persona o personas frente a las que ésta se despacha. Y que la ejecución podrá despacharse, a instancia de quien aparezca como acreedor en el título ejecutivo, frente a quien aparezca como deudor en el mismo título. De la sentencia firme de separación/divorcio en que se basa la presente ejecución resulta que ostenta la posición acreedora mi mandante, que tiene atribuida la guarda y custodia del hijo común y ha satisfecho íntegramente los gastos odontológicos que deben costearse por mitad entre ambos progenitores; y la posición deudora al demandado, que debe la cantidad reclamada por el concepto antes indicado.

Representación y defensa

Se actúa por medio de Procurador y bajo defensa Letrada, tal y como es preceptivo conforme al art. 539.1 LEC.

Acción ejercitada y título ejecutivo

Se ejercita acción ejecutiva basada en resolución judicial, conforme a lo dispuesto en el artículo 517.2.1 LEC.

Requisitos formales

Se han satisfecho los requisitos formales previstos en los artículos 549 y 550 LEC.

Principal e intereses

Resultan aplicables los artículos 575 y 576 LEC.

Costas

Las costas deberán ser impuestas al ejecutado conforme a lo dispuesto en los arts. 539.2 y 583 LEC.

Iura novit curia y cuantos resulten de pertinente aplicación.

Por lo expuesto

SUPLICO AL TRIBUNAL: Que teniendo por presentado este escrito con los documentos que lo acompañan y copia de todo ello, lo admita y tenga por interpuesta DEMANDA EJECUTIVA contra D./Dª [NOMBRE Y APELLIDOS], y previo traslado a la parte contraria y demás trámites legales, despache ejecución contra los bienes del demandado, D./Dª [NOMBRE Y APELLIDOS], en cantidad suficiente para cubrir la suma de [IMPORTE] euros ( €), más otros [IMPORTE] euros ( €) para intereses vencidos, intereses que devengue la ejecución y costas, cantidad esta última que se fija de forma provisional, sin perjuicio de su posterior liquidación, tal y como señala el art. 575.1 LEC en [IMPORTE] euros ( €) - Total: [IMPORTE] euros ( €) -; y sin necesidad de requerimiento previo se proceda al embargo de bienes del ejecutado en cantidad bastante para cubrir las cantidades reclamadas y, previos los trámites legales oportunos, se proceda a su realización para con su producto satisfacer lo debido a mi representado/a. Todo ello, con expresa imposición de las costas derivadas de esta ejecución, al ejecutado.

En [COMPLETAR], [COMPLETAR] de [COMPLETAR] de [COMPLETAR]

Firma y nº [Nº] del Letrado

Firma del Procurador

OTROSI DIGO: De acuerdo con lo dispuesto en el artículo 549.1.3º de la LEC esta parte señala como bienes del demandado susceptibles de embargo, de los que tiene conocimiento: Se identifica los bienes

En su virtud;

SUPLICO AL TRIBUNAL: Proceda al embargo de los bienes del ejecutado que resultan señalados, adoptando las medidas oportunas para la efectividad de dicho embargo.

En [COMPLETAR], [COMPLETAR] de [COMPLETAR] de [COMPLETAR]

Firma y nº [Nº] del Letrado	Firma del Procurador

========================================================================
