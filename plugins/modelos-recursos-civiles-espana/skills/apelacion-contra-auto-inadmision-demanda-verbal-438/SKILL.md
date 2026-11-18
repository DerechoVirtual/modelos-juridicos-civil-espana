---
name: apelacion-contra-auto-inadmision-demanda-verbal-438
description: "Redacta el escrito «Apelación contra el auto de inadmisión de demanda verbal» (formulario 438 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Apelación contra el auto de inadmisión de demanda verbal

> Formulario 0438 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] FECHA (5 veces)
- [ ] LUGAR (2 veces)
- [ ] Nº DE DOCUMENTO
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…os Tribunales, actuando en nombre de Don»; «…oria instada por el apelante contra Doña»; «…, Don»; «…, Don [COMPLETAR] y la menor Doña»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 458.1 LEC
- art. 459 LEC
- art. 767.1 LEC
- art. 767.1 de la LEC
- art. 767 LEC
- art. 39.2 CE

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

### Formulario 0438 · Apelación contra el auto de inadmisión de demanda verbal

- Año del modelo: 2018
- Revisión 17-11-2026: 12 campos de relleno marcados en blanco; 4 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de interposición de recurso de apelación contra auto de inadmisión de demanda de juicio verbal sobre reclamación de filiación paterna extramatrimonial y de impugnación de la matrimonial contradictoria.

Adaptado a la reforma del RDL 6/2023, aplicable a los procesos incoados desde el 20-3-2024.

A LA SALA

Don/Doña [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en nombre de Don [COMPLETAR], cuya representación tengo acreditada en los Autos de Juicio Verbal n.º [Nº DE PROCEDIMIENTO]/[AÑO], ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que en fecha [FECHA] se dictó Auto en este proceso cuya parte dispositiva es del tenor literal siguiente:

"DISPONGO INADMITIR A TRÁMITE la demanda de juicio verbal sobre reclamación de filiación paterna extramatrimonial y de impugnación de la matrimonial contradictoria interpuesta por el Procurador Don [NOMBRE Y APELLIDOS], en nombre y representación de Don [NOMBRE Y APELLIDOS], contra Doña [NOMBRE Y APELLIDOS], Dony la menor Doña"

Que entendiendo que dicha resolución no es ajustada a derecho, dicho sea con los debidos respetos y en términos de defensa, dentro del plazo de veinte días legalmente establecido en el art. 458.1 LEC, por medio del presente escrito interpongo contra la misma RECURSO DE APELACIÓN, en el que expongo las siguientes:

ALEGACIONES

De conformidad a lo dispuesto en el art. 459 LEC, por infracción de lo dispuesto en el art. 767.1 LEC.

Ciertamente dicho precepto dice que "en ningún caso se admitirá la demanda sobre determinación o impugnación de la filiación si con ella no se presenta un principio de prueba de los hechos en que se funde", pero entiende esta parte, dicho sea en términos estrictos de defensa, que el Tribunal de instancia efectúa una interpretación excesivamente formalista del requisito procesal establecido.

En este caso, hay prueba más que suficiente para admitir a trámite la demanda; no obstante el Tribunal acuerda no admitir la demanda, al entender que no se ha dado cumplimiento al requisito de procedibilidad establecido en el art. 767.1 de la LEC.

Se interesa, por tanto, la revocación de la resolución recurrida, solicitando se deje sin efecto el pronunciamiento de la parte dispositiva y se dicte Auto acordando la admisión a trámite de la demanda presentada.

Basta señalar, a los efectos de debatir lo razonado en la resolución impugnada, que lejos de la exigencia estricta que parece inferirse del auto apelado, el requisito del control previo de admisibilidad previsto en el art. 767 LEC, conforme a una consolidada doctrina jurisprudencial (SSTS de 7 de julio de 2003, rec. 3440/1997 y 12 de julio de 2004), ha de ser objeto de interpretación "espiritualizada" al constituir tal requisito un complemento tendente a procurar la seriedad de la demanda, pero nunca pueda dar lugar a una restricción ni a un obstáculo a la posibilidad que abre el art. 39.2 CE.

En este caso con la demanda se aportaron varios documentos de pagos efectuados respecto de gastos de colegio de la menor y relativos al grupo familiar de la misma, tales como recibos de la comunidad de propietarios, así como ingresos del ahora recurrente a la demandada y fotografías de distintas personas, identificadas en la demanda como el actor, junto con la menor y la madre de ésta, junto con cartas y felicitaciones de índole afectiva, prueba la citada que ha de reputarse suficiente, por si sola, para el control de razonabilidad de la demanda según consolidada jurisprudencia del propio TS, de la que son claro ejemplo la doctrina recogida en la citada sentencia de 7 de julio de 2003, rec. 3440/1997 y la de 18 de marzo de 2000, rec. 564/1995, por todo lo cual no procede sino revocar la resolución recurrida, disponiendo la admisión a trámite de la demanda formulada.

Por lo expuesto,

SUPLICO A LA SALA

Que habiendo por presentado este escrito se sirva tener por interpuesto RECURSO DE APELACIÓN frente a la resolución dictada en las presentes actuaciones de fecha [FECHA], notificada a esta parte en fecha [FECHA], y tras la pertinente tramitación, se dicte por la Sala Auto en el que, estimando el recurso de apelación interpuesto por Don/Doña [NOMBRE Y APELLIDOS], se revoque la citada resolución y en su lugar ordene la admisión a trámite de la demanda de juicio verbal sobre reclamación de filiación paterna extramatrimonial y de impugnación de la matrimonial contradictoria instada por el apelante contra Doña [COMPLETAR], Don [COMPLETAR] y la menor Doña [COMPLETAR].

Es justicia que pido en [LUGAR], a [FECHA].

OTROSÍ DIGO que, de conformidad con lo dispuesto en los apartados 3.b) y 6 de la disposición adicional decimoquinta de la LOPJ acompaño a este escrito como documento número [Nº DE DOCUMENTO] resguardo de consignación en la cuenta de Depósitos y Consignaciones abierta a nombre del Tribunal del depósito exigido para interponer el recurso por importe de 50 euros, por lo que,

SUPLICO A LA SALA

Que tenga por causada la manifestación anterior a los efectos oportunos.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

========================================================================
