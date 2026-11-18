---
name: oposicion-medidas-menores-riesgo-tutela-generalitat-38
description: "Redacta el escrito «Oposición a medidas por menores en riesgo con tutela de la Generalitat (Cataluña)» (formulario 38 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición a medidas por menores en riesgo con tutela de la Generalitat (Cataluña)

> Formulario 0038 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] DNI/NIE (2 veces)
- [ ] FECHA (4 veces)
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… domicilio a efecto de notificaciones en»; «…y de»; «… domicilio a efecto de notificaciones en»; «…bajo el número de expediente»; «…de Catalunya, Servicios Territoriales de»; «…, que resolvía el expediente»; «… dicha Resolución se declaró al/la menor»; «…s siguientes circunstancias: (completar)»; «… medidas de protección sobre el/la menor»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 113 de la Ley 14/2010

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

### Formulario 0038 · Oposición a medidas por menores en riesgo con tutela de la Generalitat (Cataluña)

- Año del modelo: 2024
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 20 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de [NOMBRE DEL REPRESENTADO/A], mayor de edad, con DNI [DNI/NIE] y domicilio a efecto de notificaciones en [COMPLETAR] y de [COMPLETAR], mayor de edad, con DNI [DNI/NIE] y domicilio a efecto de notificaciones en [COMPLETAR], según se acredita mediante escritura de poder para pleitos, actuando bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco y como mejor proceda en Derecho,

DIGO

Que, por medio del presente escrito, en la representación que ostento, formulo ESCRITO INICIAL DE OPOSICIÓN A LA RESOLUCIÓN ADMINISTRATIVA EN MATERIA DE PROTECCIÓN DE MENORES dictada por la Dirección General de Atención a la Infancia y a la Adolescencia (en adelante, “DGAIA”) de la Generalitat de Catalunya en fecha [FECHA] bajo el número de expediente [COMPLETAR], en base a los siguientes,

HECHOS

PRIMERO.- En fecha [FECHA] se notificó a mis mandantes la Resolución dictada por la DGAIA de la Generalitat de Catalunya, Servicios Territoriales de [COMPLETAR], que resolvía el expediente [COMPLETAR] de protección del/ de la menor

En virtud de dicha Resolución se declaró al/la menor [COMPLETAR] en situación legal de desamparo, asumiendo la Administración las funciones tutelares del/ de la mismo/a.

Se acompaña como Documento núm. 1 copia de dicha resolución.

SEGUNDO.- Mis representados son los progenitores del/ de la menor, según se acredita mediante la copia del Libro de Familia que se acompaña como Documento núm. 2 y del certificado de nacimiento que se acompaña como Documento núm. 3.

TERCERO La Administración demandada inició el presente procedimiento en materia de protección de menores atendidas las siguientes circunstancias:

(completar) [COMPLETAR]

Mis representados no han podido acceder al expediente administrativo en el que se fundamenta la decisión adoptada y desconocen los motivos que han dado lugar a la misma, aunque, ya en este momento, niegan la existencia de una situación de riesgo, peligrosidad y, por ende, desamparo del/ de la menor.

A los anteriores hechos, le son de aplicación los siguientes,

FUNDAMENTOS DE DERECHO

PRIMERO. - JURISDICCIÓN Y COMPETENCIA

Al amparo de lo establecido en el artículo 779 de la Ley de Enjuiciamiento Civil, corresponde a los Tribunales de Instancia de [LOCALIDAD] por ser los del lugar en los que se encuentra la entidad protectora del/ de la menor.

SEGUNDO. – PROCEDIMIENTO Y CUANTÍA

En virtud de lo establecido en el artículo 779 de la Ley de Enjuiciamiento Civil, el procedimiento se tramitará con carácter preferente y se regirá por los cauces del juicio verbal de conformidad con lo dispuesto en el artículo 753.1 de la Ley de Enjuiciamiento Civil.

TERCERO. – CAPACIDAD Y LEGITIMACIÓN

Las partes poseen capacidad para intervenir en el presente procedimiento, al amparo de lo establecido en el artículo 6 y siguientes de la Ley de Enjuiciamiento Civil.

En virtud de lo establecido en el artículo 780 de la Ley de Enjuiciamiento Civil, la legitimación activa la ostentan mis mandantes al ser los progenitores del/ de la menor y la legitimación pasiva le corresponde a la Administración demandada, al ser el organismo que dictó la Resolución impugnada.

CUARTO. - REPRESENTACIÓN PROCESAL

La parte actora comparece debidamente representada por Abogado y Procurador, tal como prevé el artículo 750 de la Ley de Enjuiciamiento Civil.

QUINTO. - INTERVENCIÓN DEL MINISTERIO FISCAL

De conformidad con lo establecido en el artículo 749.2 de la Ley de Enjuiciamiento Civil, resulta preceptiva la intervención del Ministerio Fiscal al ser un procedimiento en el que existen menores.

SEXTO.- FONDO DEL ASUNTO

Resultan de aplicación los siguientes preceptos:

- Los artículos 228-1 y siguientes del Libro Segundo del Código Civil de Cataluña en cuanto a la protección de los menores en situación de desamparo.

- El artículo 779 de la Ley de Enjuiciamiento Civil en cuanto al carácter preferente de la tramitación de los procedimientos en que se sustancie la oposición a las resoluciones administrativas.

- El artículo 780 de la Ley de Enjuiciamiento Civil en cuanto a que no será necesaria reclamación previa en vía administrativa para formular oposición, ante los tribunales civiles, a las resoluciones administrativas en materia de protección de menores.

- El artículo 113 de la Ley 14/2010 de 27 de mayo, de los derechos y oportunidades en la infancia y la adolescencia en cuanto a que la declaración de desamparo es impugnable en los términos previstos en la Ley de Enjuiciamiento Civil sin necesidad de reclamación previa por vía administrativa.

SÉPTIMO. - IURA NOVIT CURIA

En todo lo no invocado en la presente demanda, opera el principio iura novit curia.

OCTAVO. - COSTAS

Deberán ser impuestas a la parte demandada en virtud de lo establecido en el artículo 394 de la Ley de Enjuiciamiento Civil.

En su virtud,

AL TRIBUNAL SOLICITO: Que teniendo por presentado este escrito junto con sus copias y documentos que le acompañan, se sirva admitirlo, teniendo por formulado ESCRITO INICIAL DE OPOSICIÓN A LA RESOLUCIÓN ADMINISTRATIVA dictada por la DGAIA de fecha [FECHA] en la que se adoptaron las citadas medidas de protección sobre el/la menor [COMPLETAR] y, en su virtud, previos los trámites legales oportunos, acuerde:

1. Reclamar testimonio completo del expediente administrativo que ha dado lugar a la Resolución impugnada.

2. Una vez recibido el expediente, se dé traslado a esta representación para formular la correspondiente demanda, tal como prevé el artículo 753 de la Ley de Enjuiciamiento Civil.

OTROSÍ PRIMERO DIGO: Que en virtud de lo establecido en el artículo 231 de la Ley de Enjuiciamiento Civil esta parte….

AL TRIBUNAL SUPLICO: Que tenga por hecha la anterior manifestación a los efectos oportunos.

En [LUGAR], a [FECHA].

Ldo.

Proc.
