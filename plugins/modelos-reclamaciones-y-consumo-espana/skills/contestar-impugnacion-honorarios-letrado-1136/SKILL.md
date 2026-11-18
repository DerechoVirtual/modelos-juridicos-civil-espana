---
name: contestar-impugnacion-honorarios-letrado-1136
description: "Redacta el escrito «Contestar a la impugnación de honorarios de letrado» (formulario 1136 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestar a la impugnación de honorarios de letrado

> Formulario 1136 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] NÚMERO
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…/»; «…, PLAZA N.º»; «…roceda en Derecho DIGO: Que con fecha de»; «… Autónoma, que concretamente en su norma»; «…, contiene la siguiente previsión»; «…gnación se desvanece si consideramos que»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 1136 · Contestar a la impugnación de honorarios de letrado

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 14 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Tasación de costas n.º [NÚMERO] / [COMPLETAR]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

PARA EL LETRADO DE LA ADMINISTRACIÓN DE JUSTICIA

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], según tengo acreditado en los autos referenciados ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que con fecha de [COMPLETAR] se me ha dado traslado del escrito de impugnación por excesivos de la tasación de costas practicada formulado por la representación procesal del demandado D./Dña. [NOMBRE Y APELLIDOS] Dentro de plazo legal y mediante el presente escrito contesto a la impugnación, oponiendo, a los aducidos de contrario los siguientes

ANTECEDENTES

La parte demandada impugna por excesiva la minuta de honorarios presentada por el letrado D./Dña. [NOMBRE Y APELLIDOS], que ha intervenido desde el inicio de la tramitación de los autos como encargado de la defensa técnica del demandante D./Dña. [NOMBRE Y APELLIDOS]

La minuta de Letrado presentada con el escrito de solicitud de tasación de costas se ajusta estrictamente al contenido de las normas de honorarios establecidas por el Colegio de Abogados de esta provincia/Comunidad Autónoma, que concretamente en su norma [COMPLETAR], contiene la siguiente previsión [COMPLETAR] (desarrollar justificación de adecuación a normas orientadoras de honorarios). El mencionado letrado ratifica, con la firma del presente escrito, que la determinación de su minuta se ha efectuado con absoluta sujeción al contenido de las normas orientadoras de honorarios profesionales elaboradas por su Colegio profesional.

La validez del argumento esgrimido por la parte contraria como base de su impugnación se desvanece si consideramos que [COMPLETAR] (desarrollar los hechos que sirvan de base a la contestación a la impugnación).

No acepta, en consecuencia, el Abogado firmante la reducción de minuta pretendida por la parte contraria. Para la determinación de la procedencia de la minuta de honorarios presentada por el Letrado firmante se interesa que se sometan a la consideración del Colegio de Abogados de esta ciudad testimonio de los siguientes particulares:

1. (designar los que resulten convenientes para cuantificar la suma de honorarios correspondiente a la intervención del abogado).

2.

A los anteriores antecedentes resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Art. 241 de la LEC, que relaciona pormenorizadamente los conceptos que integran la tasación de costas.

El art. 246.1 a 3 del precitado texto legal establece el procedimiento a seguir para dirimir la impugnación, y concede plazo de audiencia al letrado firmante por cinco días. El presente escrito de contestación se presenta, en consecuencia, dentro de plazo legal.

Deberá, ante la negativa del letrado firmante a aceptar la reducción de minuta pretendida de contrario, darse traslado al Colegio de Abogados, para emisión de informe sobre la adecuación a normas de la minuta presentada, de los particulares mencionados en el antecedente cuarto del presente escrito.

Desestimada que sea la impugnación, se impondrán a la parte contraria las costas del trámite (art. 246.3.º de la LEC).

Por lo expuesto,

SUPLICO: Que tenga por presentado este escrito con su copia preceptiva, se sirva admitirlo, teniendo por contestada en tiempo y forma la impugnación de tasación de costas formulada por la parte contraria, y en virtud de la fundamentación jurídica invocada, y previo traslado para informe al Colegio de Abogados de esta provincia de los particulares que se dejan interesados, se dicte decreto por el Letrado de la Administración de Justicia manteniendo la tasación practicada e imponiendo las costas de este incidente al impugnante.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
