---
name: apelacion-jurisdiccion-voluntaria-modelo-generico-758
description: "Redacta el escrito «Apelación en jurisdicción voluntaria: modelo genérico» (formulario 758 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Apelación en jurisdicción voluntaria: modelo genérico

> Formulario 0758 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] FECHA (3 veces)
- [ ] IMPORTE
- [ ] DESCRIBIR
- [ ] ÓRGANO
- [ ] LUGAR
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…CION CIVIL DE LA AUDIENCIA PROVINCIAL DE»; «…engo acreditada en los autos de juicio /»; «…normas y garantías procesales siguientes»; «…ya que»; «…la prueba practicada en las actuaciones,»; «… normas de derecho sustantivo puesto que»; «…a instancia de las siguientes PRUEBAS: •»; «…i representación, no pudo practicarse. •»; «…oportuna protesta en la comparecencia. •»; «…uso fin al mismo en primera instancia. •»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 458.1 de la Ley 1/2000
- art. 20.2 de la Ley 15/2015
- art. 458.1 LEC
- art. 448.1 LEC
- arts. 23.1 y 31.1 LEC
- art. 3.2 LJV
- art. 276 LEC
- art. 460 LEC
- art. 20.1 LJV

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

### Formulario 0758 · Apelación en jurisdicción voluntaria: modelo genérico

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 19 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Recurso de apelación genérico a fin de que se remitan los autos a la Audiencia Provincial, previo emplazamiento legal para comparecer ante la misma, seguido que sea el legal procedimiento, dicte auto que revoque el de instancia, y se resuelva sobre la cuestión que es objeto de proceso, desestimando en su integridad la solicitud planteada en su momento.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCION CIVIL DE LA AUDIENCIA PROVINCIAL DE [COMPLETAR]

[NOTA DE REVISIÓN (comprobar): La AP no tiene «Sección Civil» como denominación legal: se cita la Sección por su número. Fuente: LOPJ arts. 80 y 82 (Audiencia Provincial, sin cambio de denominación).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], cuya representación tengo acreditada en los autos de juicio / [COMPLETAR], seguido contra D./Dña. [NOMBRE Y APELLIDOS], ante la Sala comparezco y como mejor proceda en derecho DIGO: (1)

Que en el plazo legal de veinte días desde la notificación del auto de fecha [FECHA], procedo a INTERPONER RECURSO DE APELACIÓN contra el mismo por medio del presente escrito en el que expongo los siguientes

REQUISITOS PROCESALES

I.- Se presenta este escrito de interposición ante ese Tribunal, que es el competente para conocer del recurso, con arreglo al art. 458.1 de la Ley 1/2000, de 7 de enero, de Enjuiciamiento Civil (en lo sucesivo, LEC), al cual se remite el art. 20.2 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV).

II.- Se presenta este escrito de interposición dentro del plazo de los veinte días desde la notificación efectiva de dicho auto (art. 458.1 LEC).

III.- Esta parte se halla legitimada por afectarle desfavorablemente la resolución impugnada, conforme exige el art. 448.1 LEC.

IV.- Las exigencias de postulación se llenan para este escrito de interposición, ya que está comparecida esta parte mediante Procurador de los Tribunales, y asistida de abogado en ejercicio, ambos colegiados y habilitados para ejercer ante el Tribunal (arts. 23.1 y 31.1 LEC, art. 3.2 LJV).

V.- Se acompaña a este escrito justificante acreditativo del depósito efectuado por importe de [IMPORTE] euros, en la cuenta de depósitos y consignaciones del Tribunal, conforme dispone la DA 15.ª de la Ley Orgánica del Poder Judicial.

FUNDAMENTOS DEL RECURSO

PRIMERO.- En primer lugar y tal como se denunció en su momento, se han infringido las normas y garantías procesales siguientes [COMPLETAR].

Como consecuencia de las mencionadas infracciones se ha sufrido indefensión consistente en [DESCRIBIR] ya que [COMPLETAR].

Tales circunstancias fueron denunciadas mediante [ÓRGANO].

SEGUNDA.- Por otro lado, el auto recurrido no ha tenido en cuenta que, según la prueba practicada en las actuaciones, [COMPLETAR].

TERCERA.- A todo ello se suma la incorrecta aplicación de las normas de derecho sustantivo puesto que [COMPLETAR].

Por lo expuesto,

SUPLICO A LA AUDIENCIA PROVINCIAL

que, teniendo por presentado este escrito con su copia, y documento/s acompañado/s, de lo que se ha dado traslado al Procurador de la parte contraria en la forma que previene el art. 276 LEC, se sirva tener por INTERPUESTO RECURSO DE APELACIÓN contra la resolución de fecha [FECHA], y

SUPLICO AL TRIBUNAL

que, seguido que sea el legal procedimiento, dicte auto que revoque el de instancia, y resolviendo sobre la cuestión que es objeto de proceso, desestime en su integridad la solicitud planteada en su momento.

OTROSÍ PRIMERO DIGO

conforme a lo regulado en el art. 460 LEC, al cual también se remite el art. 20.1 LJV, se interesa la práctica en segunda instancia de las siguientes PRUEBAS:

• [COMPLETAR], que fue propuesta y admitida en la primera instancia pero, por causa no imputable a mi representación, no pudo practicarse.

• [COMPLETAR], que fue indebidamente denegada en la primera instancia, habiéndose formulado la oportuna protesta en la comparecencia.

• [COMPLETAR], ya que se refiere a hechos de relevancia para la decisión del expediente ocurridos después de celebrada la comparecencia y antes del dictado del auto que puso fin al mismo en primera instancia.

• [COMPLETAR], puesto que se refiere a hechos de relevancia para la decisión del expediente ocurridos antes del dictado del auto, y de los que esta parte ha tenido conocimiento con posterioridad, como ha quedado justificado en las alegaciones formuladas en este escrito.

En virtud de lo expuesto,

A LA SALA SUPLICO

que se tenga por solicitada la práctica de las pruebas señaladas en la segunda instancia.

SUPLICO A LA AUDIENCIA PROVINCIAL

que teniendo por causada la manifestación anterior a los efectos oportunos, se sirva acordar de conformidad, como es procedente en Justicia que reitero.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) Exigible para la interposición de cualquier recurso de apelación frente a autos dictados por el juez que resuelvan definitivamente el expediente de jurisdicción voluntaria, conforme al art. 3.2 LJV. Y ello, independientemente de que las normas específicas de cada expediente no exijan tales requisitos de postulación para la primera instancia.

========================================================================
