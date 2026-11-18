---
name: ampliacion-objetiva-demanda-1093
description: "Redacta el escrito «Ampliación objetiva de la demanda» (formulario 1093 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Ampliación objetiva de la demanda

> Formulario 1093 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO (2 veces)
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] IMPORTE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Juicio»; «…, PLAZA N.º»; «…rdinario en el ejercicio de la acción de»; «…do en autos, la acción en reclamación de»; «…euros por»; «…o ordinario en ejercicio de la acción de»; «…bién contra dicho demandado la acción de»; «…a»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 401 de la LEC
- art. 73 de la LEC

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

### Formulario 1093 · Ampliación objetiva de la demanda

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 17 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio [COMPLETAR] n.º [Nº DE PROCEDIMIENTO]/[AÑO].

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según tengo acreditado en los autos referenciados, ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que mediante el presente escrito, y en la representación que acredito, amplio la demanda de juicio ordinario en el ejercicio de la acción de [COMPLETAR] deducida por esta parte contra D./Dña. [NOMBRE Y APELLIDOS], con objeto de que se tenga también por ejercitada contra dicho demandado, ya circunstanciado en autos, la acción en reclamación de [COMPLETAR], teniendo por ampliada la demanda principal, para que en su día se dicte sentencia de conformidad con el suplico de este escrito de ampliación de demanda que baso en los siguientes

HECHOS

 (Reproducir los de la demanda y añadir a los que sustenten la ampliación con determinación de las circunstancias de nuevo conocimiento que han motivado la ampliación de la demanda).

El demandado D./Dña. [NOMBRE Y APELLIDOS], no ha contestado aún a la demanda que ha dado origen a los presentes autos.

A los hechos antecedentes resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

Legitimación

Procedimiento

En atención a la ampliación formulada la cuantía del juicio pasaría a ser la de [IMPORTE] euros por [COMPLETAR].

1) AMPLIACIÓN DE DEMANDA: El art. 401 de la LEC establece que “antes de la contestación podrá ampliarse la demanda para acumular nuevas acciones a las ya ejercitadas o para dirigirlas contra nuevos demandados”.

Art. 71 de la LEC: Establece que el actor podrá acumular en la demanda cuantas acciones le competan contra el demandado, aunque provengan de diferentes títulos, siempre que aquellas no sean incompatibles entre sí.

Art. 72 de la LEC: Podrán acumularse, ejercitándose simultáneamente, las acciones que uno tenga contra varios sujetos o varios contra uno, siempre que entre esas acciones exista un nexo por razón del título o causa de pedir.

2) Por su parte el art. 73 de la LEC determina los requisitos para la admisibilidad de la acumulación:

“1.º Que el Tribunal que deba entender de la acción principal posea jurisdicción y competencia por razón de la materia o por razón de la cuantía para conocer de la acumulada o acumuladas. Sin embargo, a la acción que haya de sustanciarse en juicio ordinario podrá acumularse la acción que, por sí sola, se habría de ventilar, por razón de su cuantía, en juicio verbal.

2.º Que las acciones acumuladas no deban, por razón de su materia, ventilarse en juicios de diferente tipo.

3.º Que la ley no prohíba la acumulación en los casos en que se ejerciten determinadas acciones en razón de su materia o por razón de algún tipo de juicio que se haya de seguir.”

Analizando las acciones acumuladas en la demanda se llega a la conclusión de que su ejercicio conjunto no vulnera ninguno de los límites antedichos.

Art. 401.2 de la LEC: ampliada la demanda, “el plazo para contestar a la demanda se volverá a contar desde el traslado de la ampliación de la demanda”.

3) (En su caso) Acompañamos modelo 696 de liquidación de la tasa judicial de esta ampliación.

Fondo

 (desarrollar fundamentos de derecho aplicables a los hechos que sirven de base a la acción ejercitada).

Costas

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito, se sirva admitirlo, teniendo por ampliada la demanda de juicio ordinario en ejercicio de la acción de [COMPLETAR] dirigida contra D./Dña. [NOMBRE Y APELLIDOS], acordando admitir a trámite la presente ampliación de demanda y teniendo por ejercitada también contra dicho demandado la acción de [COMPLETAR] dándole traslado de este escrito de ampliación para que la conteste en plazo legal, y dando a los autos el impulso procedimental pertinente en su día se dicte sentencia por la que se condene al demandado D./Dña. [NOMBRE Y APELLIDOS] a [COMPLETAR] (detallar las peticiones reproduciendo las de la demanda y las nuevas que correspondan a la ampliación, expresándolas con la debida separación que exige el art. 399 5 de la LEC), con expresa imposición de las costas del juicio al demandado.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
