---
name: autorizacion-judicial-consentir-intromision-honor-776
description: "Redacta el escrito «Autorización judicial para consentir la intromisión en el honor, intimidad e imagen del menor» (formulario 776 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Autorización judicial para consentir la intromisión en el honor, intimidad e imagen del menor

> Formulario 0776 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] CALLE (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] Nº (2 veces)
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, de profesión [PROFESIÓN] y»; «…y [COMPLETAR], y domiciliados en»; «…de edad, es nuestro/a hijo/a nacido/a el»; «…de total normalidad. 2.ª) Que la empresa»; «…serie de anuncios de la colonia infantil»; «… comunicamos a la Fiscalía de Familia de»; «…, nº [NÚMERO] de»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 59 y 60 de la Ley 15/2015
- art. 3 de la Ley Orgánica 1/1982
- arts. 59 y 60 LJV
- art. 59.3 LJV
- art. 60 LJV
- art. 3.2 LJV

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

### Formulario 0776 · Autorización judicial para consentir la intromisión en el honor, intimidad e imagen del menor

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 23 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito promoviendo el expediente de jurisdicción voluntaria para obtener la autorización judicial que otorgue el consentimiento de la intromisión legítima en el derecho a la propia imagen del/la menor

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS], casados, provistos con DNI [DNI/NIE], de profesión [PROFESIÓN] y [COMPLETAR], y domiciliados en [COMPLETAR], calle [CALLE], nº [NÚMERO]; ante el Tribunal comparecemos y como mejor en Derecho proceda, DECIMOS: (1)

Que por medio del presente escrito, y de conformidad con los arts. 59 y 60 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promovemos expediente de jurisdicción voluntaria en solicitud de autorización judicial del consentimiento de la intromisión legítima en el derecho a la propia imagen del/la menor de edad D./Dña. [NOMBRE Y APELLIDOS], en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que D./Dña. [NOMBRE Y APELLIDOS], de [Nº] años de edad, es nuestro/a hijo/a nacido/a el [COMPLETAR], con quien convivimos en el hogar familiar, junto a su hermano/a D./Dña. [NOMBRE Y APELLIDOS], de [Nº] años de edad. Lógicamente, ostentamos la patria potestad del/la mismo/a, la cual se desarrolla en condiciones de total normalidad.

2.ª) Que la empresa [COMPLETAR] SL, dedicada a publicidad, y con la que tenemos relación en nuestro ámbito laboral, nos ofreció un contrato para que la menor participara en una serie de anuncios de la colonia infantil [COMPLETAR], en la que diversos niños de distintas edades decían a la cámara que se aseaban con el citado producto, y jugaban y corrían con caras de felicidad. Atendiendo a lo dispuesto en el art. 3 de la Ley Orgánica 1/1982, de 5 de mayo, de protección civil del derecho al honor, a la intimidad personal y familiar y a la propia imagen, y dado que nuestra hija no tiene todavía unas condiciones de madurez de acuerdo con la legislación civil (que sitúa en 12 años la edad para ello), otorgamos nuestro consentimiento al respecto por escrito. Cumpliendo con lo ordenado en el apartado segundo de dicho precepto legal, comunicamos a la Fiscalía de Familia de [COMPLETAR] el consentimiento proyectado, oponiéndose el ministerio fiscal al respecto en el plazo de ocho días. La oposición, no demasiado clara de por sí, se fundamentaba en la reducida edad de la menor, sin mayor argumento.

3.ª) Por ello, y a los efectos de no incurrir en una intromisión ilegítima en la imagen de nuestro/a hijo/a, y de conformidad con el art. 2.2 y 3 del citado texto legal, acudimos al presente expediente previsto en los arts. 59 y 60 LJV, estando legitimados como representantes legales de aquella, tal y como exige el citado art. 59.3 LJV. En este sentido, el anuncio proyectado es absolutamente inocente y adecuado a niños de cualquier edad, y nuestra hija se tomará como un juego el hecho de estar con otros menores y ser grabada mientras juega y corre siguiendo las instrucciones que se le den.

4.ª) Que es competente la Sección Civil del Tribunal de Instancia al que me dirijo conforme al art. 59.2 de la Ley de Jurisdicción Voluntaria, en relación con lo dispuesto en el art. 85.1º LOPJ, al encontrarse en su partido judicial el domicilio donde reside la menor, sito en la calle [CALLE], nº [NÚMERO] de [COMPLETAR].

5.ª) Se acompañan a este escrito certificado de nacimiento de la menor, libro de familia, contrato ofrecido por la agencia de publicidad con reportaje fotográfico del anuncio propuesto, escrito de consentimiento proyectado, y escrito de oposición del Ministerio Fiscal.

Por todo lo expuesto, al amparo del art. 3 de la Ley Orgánica 1/1982, de 5 de mayo, de protección civil del derecho al honor, a la intimidad personal y familiar y a la propia imagen, y de los arts. 59 y 60 LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria, previa la convocatoria de comparecencia prevista en el art. 60 LJV, con citación del Ministerio Fiscal, de nosotros como padres, de la menor si se considera necesario, y de quien se estime pertinente; se dicte auto concediendo la autorización judicial para el consentimiento en la intromisión legítima en el derecho de la propia imagen del/la menor D./Dña. [NOMBRE Y APELLIDOS].

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma del solicitante

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 59.3 LJV, no exige dichos requisitos para la tramitación de la solicitud que nos ocupa.

========================================================================
