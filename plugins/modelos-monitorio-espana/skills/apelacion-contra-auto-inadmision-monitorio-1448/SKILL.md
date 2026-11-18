---
name: apelacion-contra-auto-inadmision-monitorio-1448
description: "Redacta el escrito «Apelación contra el auto de inadmisión del monitorio» (formulario 1448 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Apelación contra el auto de inadmisión del monitorio

> Formulario 1448 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] NOMBRE DEL REPRESENTADO/A (2 veces)
- [ ] NÚMERO
- [ ] FECHA (5 veces)
- [ ] ÓRGANO O PERSONA
- [ ] LUGAR (2 veces)
- [ ] Nº DE DOCUMENTO
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…como explicita en el fundamento jurídico»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 458.1 LEC
- art. 459 LEC
- art. 812.1 LEC

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

### Formulario 1448 · Apelación contra el auto de inadmisión del monitorio

- Año del modelo: 2014
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 15 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Receptor
ALEGACIONES
SUPLICO A LA AUDIENCIA PROVINCIAL:
Firmas

Escrito interponiendo recurso de apelación contra auto de inadmisión a trámite de petición inicial de procedimiento monitorio.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCION CIVIL DE LA AUDIENCIA PROVINCIAL DE

[NOTA DE REVISIÓN (comprobar): La AP no tiene «Sección Civil» como denominación legal: se cita la Sección por su número. Fuente: LOPJ arts. 80 y 82 (Audiencia Provincial, sin cambio de denominación).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, actuando en nombre de [NOMBRE DEL REPRESENTADO/A] S.L., cuya representación tengo acreditada en los Autos de Proceso Monitorio n.º [NÚMERO], ante la Sala comparezco y como mejor proceda en derecho DIGO:

Que en fecha [FECHA] se dictó Auto en este proceso cuya parte dispositiva es del tenor literal siguiente:

"QUE DEBO ACORDAR LA INADMISIÓN DEL PROCESO MONITORIO formulado por el Procurador/a D./Dña. [NOMBRE Y APELLIDOS], en representación de [NOMBRE DEL REPRESENTADO/A] S.L. contra D./Dña. [NOMBRE Y APELLIDOS] "

Que entendiendo que dicha resolución no es ajustada a derecho, dicho sea con los debidos respetos y en términos de defensa, dentro del plazo de veinte días legalmente establecido en el art. 458.1 LEC, por medio del presente escrito interpongo contra la misma RECURSO DE APELACIÓN, en el que expongo las siguientes:

ALEGACIONES

De conformidad a lo dispuesto en el art. 459 LEC, por infracción de lo dispuesto en el art. 812.1.2.ª LEC.

Dicho precepto dice que podrá acudir al proceso monitorio quien pretenda de otro el pago de deuda dineraria de cualquier importe, líquida, determinada, vencida y exigible, cuando la deuda se acredite de alguna de las formas siguientes: 2.ª Mediante facturas, albaranes de entrega, certificaciones, telegramas, telefax o cualesquiera otros documentos que, aun unilateralmente creados por el acreedor, sean de los que habitualmente documentan los créditos y deudas en relaciones de la clase que aparezca existente entre acreedor y deudor.

La resolución de fecha [FECHA] acuerda la inadmisión del proceso monitorio porque, como explicita en el fundamento jurídico [COMPLETAR] de dicha resolución, mi mandante presenta dos facturas, no firmadas por el deudor, y las considera insuficientes porque debió de haber aportado el acreedor, además de esos documentos unilaterales, cualquier otro que pudiera acreditar la relación comercial existente entre las partes.

Pues bien, a juicio de esta parte, a los efectos de admisión a trámite del procedimiento monitorio, el Juez únicamente ha de comprobar si con la petición monitoria se han presentado documentos que, integrados con las alegaciones del acreedor sobre el origen y cuantía de la deuda, constituyen un principio de prueba acreditativa de la existencia de la deuda que se reclama, sin que, en modo alguno, pueda reclamarse en este momento procesal una justificación plena de la existencia o certeza del crédito.

Basta con atender a la relación de documentos que se detalla en el apartado 2.º del art. 812.1 LEC, para ver que la presentación de dos facturas, que pueden ser definidas como una cuenta detallada con descripción e indicación de la naturaleza, medida, número y precio de los distintos objetos dados en venta, es más que suficiente para crear una buena apariencia jurídica de la deuda que se reclama, que es lo único que en este momento procesal se precisa para la admisión del monitorio, no la justificación plena de la existencia o certeza del crédito.

Por lo expuesto,

SUPLICO A LA AUDIENCIA PROVINCIAL:

Que habiendo por presentado este escrito se sirva tener por interpuesto RECURSO DE APELACIÓN frente a la resolución dictada en las presentes actuaciones de fecha [FECHA] y tras la pertinente tramitación, se dicte por ésta Auto en el que, estimando el recurso de apelación interpuesto por [ÓRGANO O PERSONA] S.L., se revoque la citada resolución y en su lugar ordene la admisión a trámite de la solicitud de procedimiento monitorio instada por la apelante contra D./Dña. [NOMBRE Y APELLIDOS] y que por el Tribunal de instancia se acuerde expedir requerimiento de pago, conforme a lo interesado.

Es justicia que pido en [LUGAR], a [FECHA].

OTROSÍ DIGO que, de conformidad con lo dispuesto en los apartados 3.b) y 6 de la disposición adicional decimoquinta de la LOPJ acompaño a este escrito como documento número [Nº DE DOCUMENTO] resguardo de consignación en la cuenta de Depósitos y Consignaciones abierta a nombre del Tribunal del depósito exigido para interponer el recurso por importe de 50 euros, por lo que,

SUPLICO AL TRIBUNAL que tenga por causada la manifestación anterior a los efectos oportunos.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

========================================================================
