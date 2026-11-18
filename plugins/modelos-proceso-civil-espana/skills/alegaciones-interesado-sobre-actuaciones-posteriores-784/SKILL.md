---
name: alegaciones-interesado-sobre-actuaciones-posteriores-784
description: "Redacta el escrito «Alegaciones del interesado sobre actuaciones posteriores a la comparecencia» (formulario 784 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones del interesado sobre actuaciones posteriores a la comparecencia

> Formulario 0784 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] FECHA (6 veces)
- [ ] Nº DE EXPEDIENTE
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…/»; «…, profesora del Colegio»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 85.2 de la Ley 15/2015
- art. 86 LJV
- art. 156 del Código Civil
- art. 85 LJV
- art. 85.2 LJV
- art. 3.2 LJV
- art. 539 LEC
- art. 85.3 LJV

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

### Formulario 0784 · Alegaciones del interesado sobre actuaciones posteriores a la comparecencia

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 16 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito por el que se formulan alegaciones en relación al traslado recibido sobre actuaciones posteriores a la comparecencia del Letrado de la Administración de Justicia, solicitando que se resuelva continuar con el expediente, y que se atribuya al interesado la facultad de decidir sobre el sacramento de la comunión de su hijo/a menor

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, como mejor proceda en derecho comparezco y DIGO: (1)

Que por medio del presente escrito, y al amparo de lo dispuesto en el artículo 85.2 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), formulo ALEGACIONES en relación al traslado recibido sobre actuaciones posteriores a la comparecencia del Letrado de la Administración de Justicia, en base a las siguientes

ALEGACIONES

1.ª) Que el pasado [FECHA], mi mandante instó ante el órgano judicial al cual tengo el honor de dirigirme, expediente de jurisdicción voluntaria previsto en el art. 86 LJV, en orden a solicitar la atribución judicial de la facultad para decidir sobre que su hija menor de edad recibiera el sacramento de la primera comunión, a partir de lo dispuesto en el art. 156 del Código Civil. Mediante diligencia de ordenación de fecha [FECHA], se incoó el presente expediente con nº [Nº DE EXPEDIENTE] / [COMPLETAR], y se convocó la comparecencia prevista en el art. 85 LJV, que tuvo lugar el pasado [FECHA].

2.ª) En dicho acto procesal, y tras la práctica de las diligencias propuestas por las partes, se acordó por su señoría, a instancia del Ministerio Fiscal, practicar la ulterior testifical de la tutora de la menor, la madre Dña. [NOMBRE Y APELLIDOS], profesora del Colegio [COMPLETAR] de [LOCALIDAD], en orden a conocer las convicciones religiosas de la misma. La prueba, habida cuenta del delicado estado de salud de la testigo, se practicó el pasado [FECHA] en su domicilio.

3.ª) Por diligencia de ordenación de fecha [FECHA], se me ha dado traslado del acta de dicha testifical, para que, de conformidad con el art. 85.2 LJV, realice alegaciones en cinco días.

4.ª) Y de esta forma, tal y como se ponía de manifiesto en la solicitud que originó el presente expediente, las convicciones religiosas de la hija de mi cliente están fuertemente arraigadas, habiendo asistido voluntariamente a todas las celebraciones religiosas programadas por la citada profesora en los últimos tres años. Resulta evidente, por ello, que a pesar de la oposición de su madre, es conveniente para su formación integral que reciba el sacramento de la comunión como cualquier menor que es educada en la fe cristiana.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito y los documentos que se acompañan, y por deducidas alegaciones en relación a la testifical practicada, de conformidad con el art. 85.2 LJV; se resuelva continuar con el expediente, y se atribuya a mi mandante la facultad de decidir sobre el sacramento de la comunión de su hija menor Dña. [NOMBRE Y APELLIDOS].

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para presentar demanda de ejecución variará, según el art. 3.2 LJV, y el art. 539 LEC, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 85.3 LJV, no exige esos requisitos para la tramitación del expediente; sin perjuicio de que sea habitual la asistencia de dichos profesionales habida cuenta de que, normalmente, se tratará de desacuerdos entre progenitores separados o divorciados con fuertes controversias.

========================================================================
