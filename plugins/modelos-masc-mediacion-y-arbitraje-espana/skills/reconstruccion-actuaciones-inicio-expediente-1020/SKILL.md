---
name: reconstruccion-actuaciones-inicio-expediente-1020
description: "Redacta el escrito «Reconstrucción de actuaciones: inicio del expediente» (formulario 1020 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reconstrucción de actuaciones: inicio del expediente

> Formulario 1020 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO (2 veces)
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] NÚMERO (2 veces)
- [ ] DESCRIBIR
- [ ] FECHA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Juicio»; «…, PLAZA N.º»; «…en el ejercicio de la acción»; «…demanda fueron referenciados como juicio»; «…de este Tribunal. Con fecha de»; «…os o desaparecidos) como consecuencia de»; «…ión se encontraba en la fase procesal de»; «…: Consta en el Registro de»; «… 234 y 235 de la LEC: 1. Se acordará por»; «…ión total/parcial de los autos de juicio»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 232 de la LEC

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

### Formulario 1020 · Reconstrucción de actuaciones: inicio del expediente

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 19 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (FECHA, NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio [COMPLETAR] n.º [Nº DE PROCEDIMIENTO]/[AÑO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según tengo acreditado en los autos referenciados ante el Tribunal comparezco, y como mejor proceda en Derecho DIGO:

Que mediante el presente escrito promuevo EXPEDIENTE DE RECONSTRUCCIÓN TOTAL/PARCIAL DE LOS AUTOS, con objeto de que, tramitado en forma y con la intervención como parte del Ministerio Fiscal, se dicte auto mediante el que se determine la forma en que deberán quedar reconstruidas las actuaciones, basando mi solicitud en los siguientes

HECHOS

Los presentes autos se iniciaron en virtud de demanda promovida por mi mandante D./Dña. [NOMBRE Y APELLIDOS] en el ejercicio de la acción [COMPLETAR] dirigida contra el demandado D./ Dña. [NOMBRE Y APELLIDOS], quien compareció en los autos y contestó a la demanda representado por el Procurador D./Dña. [NOMBRE Y APELLIDOS]

Los autos formados a raíz de la presentación de la demanda fueron referenciados como juicio [COMPLETAR] n.º [NÚMERO] de este Tribunal.

Con fecha de [COMPLETAR] dichos autos resultaron destruidos (o mutilados o desaparecidos) como consecuencia de [COMPLETAR] (reseñar circunstancias lo más detalladas posibles sobre el deterioro o desaparición total o parcial de los autos, con expresión de la fecha más aproximada posible).

En el momento de la desaparición/destrucción/mutilación de los autos su tramitación se encontraba en la fase procesal de [COMPLETAR]

Detallo a continuación todos los datos que esta parte conoce sobre el desarrollo procedimental de los autos, que apoyo con las correspondientes copias simples de los escritos y comunicaciones judiciales notificadas a esta parte que se acompañan al presente escrito:

(Desarrollar cuantos datos se conozcan y aportar las copias auténticas o simples de documentos de que se disponga, así como todas las copias de las comunicaciones judiciales notificadas a la parte solicitante.)

Para la reconstrucción total de los documentos de los que esta parte no tiene copia se podrá acudir a los siguientes Registros públicos:

1. Documento sobre [DESCRIBIR]: Consta en el Registro de [COMPLETAR] 2.

Los medios de investigación que aparecen como posibles para la total reconstrucción de las actuaciones son los siguientes:

Resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

COMPETENCIA.—Es competente para la reconstrucción total o parcial de todo tipo de actuaciones judiciales el Letrado de la Administración de Justicia en que la destrucción o mutilación hubiere acontecido: art. 232 de la LEC.

LEGITIMACIÓN.—Art. 233 de la LEC: La reconstrucción puede acordarse de oficio o a instancia de parte o sus herederos.

Art. 232.2 de la LEC. Deberá ser siempre parte el Ministerio Fiscal en los expedientes de reconstrucción de actuaciones.

Se cumplen los presupuestos procesales de determinación de fecha [FECHA] y circunstancias de la destrucción/mutilación, situación procesal del asunto y se acompañan cuantas copias de documentos obraban en poder de esta parte. Igualmente se expresan los Registros en que constan los restantes documentos y los medios de reconstrucción que aparecen como posibles.

TRÁMITE.—Arts. 234 y 235 de la LEC:

1. Se acordará por [COMPLETAR] (Providencia o diligencia del Letrado de la Administración de Justicia) el inicio del expediente citando a las partes a comparecencia ante el Letrado de la Administración de Justicia dentro del plazo de diez días para que comparezcan las partes y sus abogados, por ser preceptiva la intervención de éstos en la tramitación de los presentes autos.

2. Se requerirá manifestación a las partes sobre su conformidad o disconformidad con las copias de documentos presentadas.

3. Previo informe del Ministerio Fiscal, el Letrado de la Administración de Justicia determinará los extremos sobre los que media acuerdo y aquellos sobre las que existe desacuerdo y si no existiera controversia por decreto se tendrá por reconstituidas las actuaciones.

4. Si hubiere disconformidad el Letrado de la Administración de Justicia convocará a las partes y al Ministerio Fiscal a vista ante el Tribunal, resolviendo tras la práctica de la prueba mediante auto.

5. mediante auto se resolverá la forma en que deben quedar reconstruidas las actuaciones o la imposibilidad de su reconstrucción.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito, documentos y copias que se adjuntan, se sirva admitir todo ello, teniendo por promovido expediente para la reconstrucción total/parcial de los autos de juicio [COMPLETAR] n.º [NÚMERO] de este Tribunal, dando traslado el Letrado de la Administración de Justicia de este escrito a las partes y al Ministerio Fiscal y acordando iniciar el procedimiento con señalamiento de fecha para comparecencia del Ministerio Fiscal y de las partes, y, tramitado que sea en forma el expediente, dicte decreto el Letrado de la Administración de Justicia declarando reconstituidas las actuaciones o, en caso de no existir acuerdo, resuelva el Tribunal lo oportuno.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
