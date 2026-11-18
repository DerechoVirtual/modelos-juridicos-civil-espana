---
name: contestacion-demanda-filiacion-defensor-judicial-menor-1194
description: "Redacta el escrito «Contestación a demanda de filiación por defensor judicial del menor» (formulario 1194 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a demanda de filiación por defensor judicial del menor

> Formulario 1194 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] FECHA
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…ismo se ajustan a la realidad. TERCERO.-»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 753 y 767 LEC
- art. 764.1 LEC

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

### Formulario 1194 · Contestación a demanda de filiación por defensor judicial del menor

- Año del modelo: 2014
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 5 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

Que por medio del presente escrito paso a CONTESTAR A LA DEMANDA DE RECLAMACIÓN DE PATERNIDAD interpuesta por D./Dña. [NOMBRE Y APELLIDOS]. Contestación que baso en los siguientes:

HECHOS

PRIMERO.- Conforme con el contenido del hecho primero de la demanda, habida cuenta de que los hechos descritos en el mismo se ajustan a la realidad.

SEGUNDO.- Conforme con el contenido del hecho segundo de la demanda, habida cuenta de que los hechos descritos en el mismo se ajustan a la realidad.

TERCERO.- [COMPLETAR]

A los anteriores hechos son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- DE LA JURISDICCIÓN Y COMPETENCIA.

Nada que oponer al correlativo de la demanda en cuanto a la jurisdicción y a la competencia del Tribunal de [LOCALIDAD]

II.- DE LA CAPACIDAD PROCESAL Y REPRESENTACIÓN, POSTULACIÓN Y LEGITIMACIÓN.

Conforme con los correlativos de la demanda.

III.- DEL PROCEDIMIENTO E INTERVENCIÓN DEL MINISTERIO FISCAL.

Nada que oponer respecto a que la demanda interpuesta de contrario y la presente contestación deberán tramitarse de acuerdo a las reglas del juicio verbal, si bien con las especialidades reguladas en el art. 753 y 767 LEC.

Nada que objetar respecto a la imperativa intervención del Ministerio Fiscal.

IV.- DEL FONDO.

Para los procesos en que se ejercitan acciones de filiación, es constante la jurisprudencia de nuestro alto tribunal en el sentido de que, cuando la madre se opone a la demanda de reclamación de paternidad, «son contrarios los intereses de la madre demandada, que no quiere establecer en ningún caso la realidad que sea procedente sobre la paternidad, con los intereses del hijo, tanto desde el punto de vista de su persona como del orden público del estado civil» (STS de 7 de noviembre de 2002, rec. 892/1997).

El principio en esta materia es la búsqueda a todo trance de la verdadera filiación natural o biológica, y por ende, la indisponibilidad del objeto del proceso, y la búsqueda de oficio de la autenticidad de la procreación, contando el Juzgador con posibilidades inquisitivas, siendo regla la viabilidad de solicitar de los tribunales la determinación legal de la filiación o la impugnación de la legalmente determinada (art. 764.1 LEC), con la sola salvedad del respeto a la cosa juzgada material, ya que la investigación de la paternidad es de oportunidad procesal única, práctica de la prueba biológica a la que desde luego esta parte anuncia que no se opondrá.

En virtud de lo expuesto,

AL TRIBUNAL SUPLICO:

Que tenga por presentado este escrito con los documentos al mismo acompañados, y copias de todo ello, lo admita, teniéndome por personado y por contestada la demanda en tiempo y forma, siguiéndose el proceso por todos sus trámites, se sirva dictar sentencia congruente con lo pedido y todos los efectos legales inherentes a ello, atenida a lo que resulte de la prueba practicada.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

========================================================================
