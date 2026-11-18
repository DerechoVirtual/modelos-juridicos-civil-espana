---
name: oposicion-tutor-curador-remocion-681
description: "Redacta el escrito «Oposición del tutor o curador a su remoción» (formulario 681 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición del tutor o curador a su remoción

> Formulario 0681 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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
- [ ] Nº DE COLEGIADO
- [ ] COLEGIO
- [ ] FECHA
- [ ] LOCALIDAD (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…e de jurisdicción voluntaria instado por»; «…a estimable colaboración de su esposa Dª»; «…, así como de Dª»; «…vista, y que son las siguientes: 1º) Don»; «…, con domicilio en [LOCALIDAD] 2º) Don»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 278 del Código Civil
- art. 394 de la LEC
- art. 438.8 de la LEC

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

### Formulario 0681 · Oposición del tutor o curador a su remoción

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 10 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 6 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE COLEGIADO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en nombre y representación de D. [NOMBRE Y APELLIDOS], según acredito mediante apoderamiento apud-acta otorgado ante Letrado de la Administración de Justicia de que acompaño, bajo la dirección letrada de D. [NOMBRE Y APELLIDOS], colegiado núm. [Nº DE COLEGIADO] del Iltre. Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco y como mejor proceda en Derecho

DIGO:

1) Que el pasado día [FECHA] mi representado ha sido citado en el expediente de jurisdicción voluntaria instado por [COMPLETAR] sobre remoción del cargo de tutor.

2) Que, de conformidad con lo dispuesto en el art. 49.1.II de la Ley de Jurisdicción Voluntaria, mediante el presente escrito me opongo a la solicitud de remoción del cargo de tutor de mi representado, en atención a los siguientes

HECHOS

 Se acepta los hechos relativos al procedimiento de constitución de la tutela del menor D. [NOMBRE Y APELLIDOS] y designación de tutor, pero se niega rotundamente la existencia de la causa de remoción alegada por el solicitante, puesto que mi representado en ningún modo ha faltado a las obligaciones propias de todo tutor, en el modo que señala el art. 278 del Código Civil, sino que antes al contrario las ha cumplido con extremado celo como se pasa a exponer seguidamente.

 Es preciso resaltar que la solicitud no argumenta causa o circunstancia alguna, en el orden personal, para declarar la remoción de mi representado, al margen de la patente mala relación existente con el solicitante, tal como se desprende del contenido de la solicitud.

Mi representado ha cumplido escrupulosamente sus deberes derivados del cargo de tutor, supervisando al tutelado de un modo diario y permanente, cuidándolo en todos los aspectos y atendiendo a sus deseos y preferencias, procurando su formación integral, aseo, alimentación, higiene en el domicilio, medicación, etc. y ello con la estimable colaboración de su esposa Dª [COMPLETAR], así como de Dª [COMPLETAR], persona que hace tiempo que viene ya trabajando no solo en las labores domésticas generales del domicilio, sino también colaborando de un modo importante en la atención y asistencia de toda clase que necesita el tutelado.

Por lo demás, mi representado ha venido desarrollando una administración de bienes en exclusivo interés del tutelado, tal como se desprende de las cuentas presentadas que acompañamos como documentos

 Los anteriores hechos nos llevan a formular oposición a la infundada solicitud planteada de contrario, debiendo resolverse la cuestión de forma contradictoria en el juicio contencioso donde acreditaremos oportunamente la veracidad de los hechos alegados por esta parte.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia y procedimiento

Artículos 43, 45 y 49 de la Ley de Jurisdicción Voluntaria.

Oposición

Es de aplicación el artículo 49.1.II de la Ley de Jurisdicción Voluntaria que establece que “si se suscitare oposición, el expediente se hará contencioso y el Letrado de la Administración de Justicia citará a los interesados a una vista, continuando la tramitación con arreglo a lo previsto para el juicio verbal”.

Legitimación

Está legitimado activamente mi representado para oponerse al estar directamente interesado en su condición de tutor. Está legitimado pasivamente el solicitante, debiendo intervenir el Ministerio Fiscal.

Inexistencia de la causa de remoción

No concurre ninguna de las causas de remoción contempladas en el art. 278 del Código Civil, tal como se ha expuesto en los hechos de este escrito de oposición.

Costas

Es de aplicación el art. 394 de la LEC, debiendo imponerse al solicitante-demandado.

Por lo anterior,

AL TRIBUNAL SUPLICO que tenga por presentado este escrito con los documentos que acompaño y sus copias, y en su virtud me tenga por opuesto a la solicitud de remoción del cargo de tutor de mi representado, acordando convertir el expediente en contencioso y citar a los interesados a la vista, y, tras los oportunos trámites, se dicte sentencia por la que desestime la remoción deducida por D. [NOMBRE Y APELLIDOS], con imposición de costas al citado solicitante-demandado.

OTROSÍ PRIMERO DIGO Que al amparo de lo establecido en el art. 438.8 de la LEC, comunico al Tribunal el nombre y demás circunstancias de las personas que han de declarar en su calidad de testigos ya que esta parte no los puede presentar voluntariamente, interesando que sean citadas para la vista, y que son las siguientes:

1º) Don [COMPLETAR], con domicilio en [LOCALIDAD]

2º) Don [COMPLETAR], con domicilio en [LOCALIDAD].

SUPLICO AL TRIBUNAL: Que acuerde la citación para la vista para que comparezcan el día señalado y declaren en calidad de testigos; todo ello con los apercibimientos que en Derecho procedan

En [LUGAR], a [DÍA] de [MES] de [AÑO].

(Firma Procurador y Abogado).

========================================================================
