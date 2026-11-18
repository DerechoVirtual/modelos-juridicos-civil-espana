---
name: oposicion-tenedor-titulo-expediente-691
description: "Redacta el escrito «Oposición del tenedor del título al expediente» (formulario 691 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición del tenedor del título al expediente

> Formulario 0691 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] Nº DE DOCUMENTO
- [ ] FECHA (5 veces)
- [ ] IMPORTE (11 veces)
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] Nº DE EXPEDIENTE
- [ ] LUGAR
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… Hechos y consideraciones jurídicas: 1.ª»; «… cuatro letras de cambio numeradas como,»; «…, y»; «…bio habían sido aceptadas por la entidad»; «…ban depositadas en la entidad financiera»; «…, sin mayor explicación al respecto. 2.ª»; «…/»; «…, y se citó a la entidad emisora»; «… parte de la citada entidad emisora. 3.ª»; «…guno la interdicción aquí combatida. 4.ª»; «…negociar las letras de cambio numeradas,»; «…, y»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 135.9 de la Ley 15/2015
- art. 137.4 LJV
- art. 135 LJV
- art. 3.2 LJV
- art. 133.3 LJV

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

### Formulario 0691 · Oposición del tenedor del título al expediente

- Año del modelo: 2015
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 38 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Oposición a la solicitud de prohibición de transmisión de letras de cambio

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], como mejor proceda en derecho comparezco y DIGO: (1)

Que por medio del presente escrito, y al amparo de lo dispuesto en el artículo 135.9 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), procedo a mostrar OPOSICIÓN a la solicitud de prohibición de transmisión de letras de cambio. Todo ello, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª [COMPLETAR])

Que el pasado [FECHA], D./Dña. [NOMBRE Y APELLIDOS] instó ante el órgano judicial al cual tengo el honor de dirigirme, expediente de jurisdicción voluntaria con objeto de obtener la prohibición de transmitir cuatro letras de cambio numeradas como, [COMPLETAR], y [COMPLETAR]; por importes de [IMPORTE] euros, [IMPORTE] euros [IMPORTE], [IMPORTE] euros, y [IMPORTE] euros respectivamente. Las letras de cambio habían sido aceptadas por la entidad [COMPLETAR] SL con domicilio social en [LOCALIDAD], calle [CALLE], nº [NÚMERO], y se encontraban depositadas en la entidad financiera [COMPLETAR] SA. En su solicitud sostenía que las cambiales indicadas le habían sido sustraídas, sin mayor explicación al respecto.

2.ª [COMPLETAR])

Mediante diligencia de ordenación de fecha [FECHA], se incoó el presente expediente con nº [Nº DE EXPEDIENTE] / [COMPLETAR], y se citó a la entidad emisora [COMPLETAR] SA a la comparecencia prevista en el art. 137.4 LJV. Asimismo, en fecha [FECHA] se dictó decreto acordando la prohibición de transmisión frente a la que se pretende alzar la presente oposición. La misma se plantea en este momento tras habérsele comunicado a mi representado la incoación del expediente por parte de la citada entidad emisora.

3.ª [COMPLETAR])

Las cuatro letras de cambio en cuestión no han sido sustraídas ilegítimamente al promotor del expediente, ni han sido extraviadas de manera alguna. El pasado [FECHA] las mismas fueron objeto de cesión, en pago de una deuda por importe de [IMPORTE] euros, que mi cliente ostentaba frente a aquel. Se acompaña documento privado en el cual se reconoce tal transacción firmada por ambas partes. En consecuencia, D./Dña. [NOMBRE Y APELLIDOS] es el legítimo poseedor de las letras de cambios, y tiene derecho a transmitir las mismas, en las formas y maneras previstas por la Ley Cambiaria y del Cheque, sin que procede en modo alguno la interdicción aquí combatida.

4.ª [COMPLETAR])

En atención a las razones expuestas se formula el presente escrito de oposición; a los efectos de que no tengan lugar los efectos previstos en los apartados séptimo y octavo del art. 135 LJV, y vedar la anulación del título, de conformidad con el apartado noveno del mismo precepto legal. Y ello, sin perjuicio de que se plantee con posterioridad el correspondiente procedimiento declarativo contencioso.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito y por opuesta esta parte a la prohibición de transmitir y negociar las letras de cambio numeradas, [COMPLETAR], y [COMPLETAR]; por importes de [IMPORTE] euros, [IMPORTE] euros [IMPORTE], [IMPORTE] euros, y [IMPORTE] euros respectivamente; a los efectos legales correspondientes.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito, el art. 133.3 LJV establece como preceptiva la intervención de Abogado y Procurador para la solicitud en análisis.

========================================================================
