---
name: oposicion-rendicion-final-cuentas-tutor-fallecimiento-236
description: "Redacta el escrito «Oposición a la rendición final de cuentas del tutor por fallecimiento del tutelado» (formulario 236 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición a la rendición final de cuentas del tutor por fallecimiento del tutelado

> Formulario 0236 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Oposición a la cuenta final del «tutor» por fallecimiento de la «tutelada»: el art. 232 CC vigente solo regula la tutela de menores; si la tutelada era mayor con discapacidad, aplicar el art. 292 CC (DT 2.ª Ley 8/2021 (BOE-A-2021-9233)).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] Nº DE EXPEDIENTE
- [ ] SEDE
- [ ] FECHA (5 veces)
- [ ] LOCALIDAD
- [ ] IMPORTE (4 veces)
- [ ] LUGAR
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…e rendición final de cuentas del tutor D»; «…l de la tutela presentada por el tutor D»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 232 del Código Civil
- art. 232 del Código Civil
- art. 228 del Código Civil
- art. 232 CC

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

### Formulario 0236 · Oposición a la rendición final de cuentas del tutor por fallecimiento del tutelado

- Año del modelo: 2020
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 14 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)
- Avisos de la revisión: Oposición a la cuenta final del «tutor» por fallecimiento de la «tutelada»: el art. 232 CC vigente solo regula la tutela de menores; si la tutelada era mayor con discapacidad, aplicar el art. 292 CC (DT 2.ª Ley 8/2021 (BOE-A-2021-9233)).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Expediente de jurisdicción voluntaria número [Nº DE EXPEDIENTE]

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

1) Que el pasado día [FECHA] mi representado ha sido emplazado en el expediente de jurisdicción voluntaria sobre rendición final de cuentas del tutor D [COMPLETAR], por extinción de la tutela por fallecimiento del tutelado, de quien mi mandante ostenta la condición de heredero.

2) Que, de conformidad con lo dispuesto en el artículo 232 del Código Civil y art. 51 de la Ley de Jurisdicción Voluntaria (LJV), mediante el presente escrito me opongo a la aprobación de la cuenta final de la tutela, en atención a los siguientes

Hechos

PRIMERO.- En primer lugar, nos oponemos a la cuenta por la limitación del periodo de rendición que ha realizado el tutor, que se refiere exclusivamente al último año, cuando viene desempeñando su cargo desde mucho tiempo atrás y la cuenta final ha de alcanzar a la totalidad del tiempo en que se ejerció la tutela.

En efecto, las cuentas presentadas por el tutor se refieren al lapso temporal entre el día [FECHA] y el día [FECHA], fecha de fallecimiento de la tutelada, a modo de rendición de cuentas anual ordinaria, cuando lo que realmente procede es rendir la cuenta general justificada de su administración según ordena el art. 232 del Código Civil, aun cuando se hayan aprobado las anteriores cuentas anuales, por lo que no puede aprobarse la cuenta final al no rendirse cuenta general de todo el periodo de desempeño del cargo tutelar.

De este modo, no puede presentarse la cuenta final como si tratara de rendición de cuentas anual ordinaria, pues el art. 232 exige rendir la cuenta general justificada de la administración durante todo el periodo, cuando se extingue la tutela por fallecimiento del tutelado como es el caso, aun cuando se hayan aprobado las anteriores cuentas anuales, y en tanto que la rendición de cuentas anual tiene carácter informativo en tanto que la rendición general por extinción de la tutela goza de sustantividad propia, no habiéndose cumplido por el tutor en la cuenta presentada, por lo que no puede ser aprobada.

SEGUNDO.- En cuanto al fondo, se formula oposición por omisión de bienes del tutelado, falta de justificación de las partidas y la inclusión de gastos propios del tutor, que no se han realizado en beneficio del tutelado ni se corresponden con el ejercicio del cargo.

Entrando en el examen de las partidas correspondientes a este limitado periodo de rendición de cuentas, nos oponemos a su aprobación por ocultación de bienes, puesto que se ha omitido toda referencia al piso en Madrid titularidad del tutelado, sito en [LOCALIDAD], el cual fue heredado por el mismo en fecha [FECHA], tal como se acredita por la escritura de aceptación de herencia que se acompaña como documento número 1.

En la cuenta, no hay constancia de este inmueble, ni de su compra o venta durante la vigencia de la tutela, por parte de la tutelada, ni tampoco se relaciona ingreso o gasto alguno en relación con dicho inmueble, de manera que existe una ocultación que impide la aprobación de la cuenta por falta de justificación, de la que se pueden derivar asimismo perjuicios para los herederos.

TERCERO.- Nos oponemos asimismo a la aprobación de la cuenta por la total ausencia de justificación de las diferentes partidas de la cuenta que presenta el tutor.

El objetivo de la rendición final, si bien no es el propio de una contabilidad precisa o de una auditoría contable, sí debe contener los elementos para juzgar si se ha ejercido el cargo con rectitud e integridad y en beneficio del pupilo, sin desviaciones improcedentes o apropiaciones indebidas. En todo caso, una rendición final de cuentas exige la aportación de elementos de juicio que puedan ayudar a apreciar si el tutor ha defendido el patrimonio del pupilo.

Nada de esto se cumple en la cuenta presentada, pues el tutor no ha aportado los extractos bancarios, ni justificación de la situación de los inmuebles y sus cargas, ni tan siquiera los recibos de los gastos relacionados que se han satisfecho con cargo al patrimonio del tutelado, por lo que no puede considerarse justificada la cuenta presentada, por lo que debe denegarse asimismo su aprobación por este motivo.

CUARTO.- Finalmente, nos oponemos a la aprobación de la cuenta por la inclusión de gastos particulares del tutor y en su propio beneficio, a reserva de las acciones civiles o penales que correspondan a mi representado.

Entrando en las concretas partidas, el tutor incluye una partida de gastos de viaje por importe de [IMPORTE] euros, a todas luces excesiva pues tutor y tutelada residían en la misma localidad, sin que exista ni el más mínimo indicio de que el tutor tuviera que desplazarse a ningún sitio por razones de ejercicio del cargo. No se puede olvidar que el tutor está obligado a ejercer la administración con la diligencia debida, art. 228 del Código Civil, de modo que los desplazamientos motivados por dicha administración, y en consecuencia los gastos inherentes a los mismos, deben ser justificados y proporcionados, sin que en modo alguno se cumpla en este caso.

En la partida de gastos del geriátrico, no se recoge la fianza que debía devolver el centro y que se constituyó cuando ingresó en el mismo la tutelada por importe de [IMPORTE] euros. Ello supone la ocultación de un haber del patrimonio de la tutelada, sin que exista referencia alguna a tal activo en la cuenta presentada.

En cuanto a los gastos de conservación de los inmuebles titularidad de la tutelada, en concepto de electricidad, agua, comunidad, impuestos y seguros por importe de [IMPORTE] euros resultan totalmente excesivos y carecen de cualquier justificación en la cuenta presentada.

Finalmente, en cuanto a los ingresos, no se incluye la renta vitalicia por importe mensual de [IMPORTE] euros que dispusieron los padres de la tutelada en la herencia y que se refleja en la escritura de aceptación que se acompaña, sin que se haga mención alguna a dicho ingreso en la cuenta.

Por estos motivos y los expuestos, debemos oponernos a la aprobación de la cuenta final, solicitando que se deniegue la solicitud formulada.

A los anteriores hechos son de aplicación los siguientes

Fundamentos de Derecho

PRIMERO.- COMPETENCIA Y PROCEDIMIENTO.Artículo 51 de la Ley de Jurisdicción Voluntaria.

SEGUNDO.- OPOSICIÓN. Es de aplicación el artículo 51.4 de la Ley de Jurisdicción Voluntaria que establece: “estas disposiciones serán de aplicación en los supuestos de rendición final de cuentas por extinción de la tutela o curatela, debiendo ser presentada, en su caso, en el plazo de tres meses desde el cese del cargo, prorrogables por el tiempo que fuere necesario si concurre justa causa. En estos casos también se oirá, si procediera, al nuevo tutor o curador y a los herederos del tutelado o asistido, en su caso”. En el mismo sentido, el art. 232 CC.

TERCERO.- CUENTA FINAL DE LA TUTELA. Son de aplicación los arts. 232 y siguientes del CC, disponiendo el art. 232: “El tutor, sin perjuicio de la obligación de rendición anual de cuentas, al cesar en sus funciones deberá rendir ante la autoridad judicial la cuenta general justificada de su administración en el plazo de tres meses, prorrogables por el tiempo que fuere necesario si concurre justa causa (…)”

Por lo anterior,

AL TRIBUNAL SUPLICO que tenga por presentado este escrito con los documentos que acompaño y sus copias, y en su virtud me tenga por opuesto a la aprobación de la cuenta final de la tutela presentada por el tutor D [COMPLETAR] y, tras los trámites legales, deniegue la aprobación de la cuenta general con los efectos inherentes.

En [LUGAR], a [FECHA].

(Firma Procurador y Abogado).
