---
name: homologacion-judicial-transaccion-ejecucion-sentencia-204
description: "Redacta el escrito «Homologación judicial de transacción en ejecución de sentencia» (formulario 204 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Homologación judicial de transacción en ejecución de sentencia

> Formulario 0204 del plugin **Ejecución civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.
- **Inmuebles** (referencia catastral, superficie, uso) → `consultar_catastro` (y `callejero_catastro` para localizar la dirección).

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
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO (2 veces)
- [ ] Nº
- [ ] ACTO O RESOLUCIÓN
- [ ] FECHA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…/a de los Tribunales, que actúa en la de»; «…de autos»; «…IMERO.- Que este proceso se promovió por»; «…o representación del Procurador/a Sr./a.»; «… representada por la Procurador/a Sr./a.»; «… la transacción judicial alcanzada entre»; «…y»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 19.1 LEC
- art. 19 LEC

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

### Formulario 0204 · Homologación judicial de transacción en ejecución de sentencia

- Año del modelo: 2020
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 15 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito comunicando al Tribunal un acuerdo transaccional alcanzado en ejecución de sentencia.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, actuando en nombre y representación de [NOMBRE DEL REPRESENTADO/A], demandante, y D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, que actúa en la de [COMPLETAR], demandada, conforme a los poderes para pleitos con facultades especiales expresas para transigir que se tienen aportados y testimoniados en los autos de Juicio Ordinario nº [Nº DE PROCEDIMIENTO]/[AÑO], que se encuentra en ejecución de sentencia que se siguen con el nº [Nº] de autos [COMPLETAR], ante el Tribunal comparecemos y como mejor proceda en Derecho, DECIMOS:

PRIMERO.- Que este proceso se promovió por [COMPLETAR], bajo representación del Procurador/a Sr./a. [COMPLETAR], frente a [ACTO O RESOLUCIÓN], representada por la Procurador/a Sr./a. [COMPLETAR], ejercitándose la pretensión de

SEGUNDO.- Dichas partes en este proceso han alcanzado un acuerdo transaccional del siguiente tenor literal:

Se acompaña documento original que consigna el acuerdo, de fecha [FECHA]

TERCERO.- Que según el art. 19.1 LEC, los litigantes están facultados para disponer el objeto del juicio y podrán renunciar, desistir del juicio, allanarse, someterse a arbitraje y transigir sobre lo que sea objeto del mismo. Y según el apartado 2 del mismo precepto, si las partes pretendieran una transacción judicial y el acuerdo o convenio que alcanzaren fuere conforme a lo previsto en el apartado anterior, será homologado por el tribunal que esté conociendo del litigio al que se pretenda poner fin.

Que dispone asimismo el apartado 3 del art. 19 LEC que los actos a que se refieren los apartados anteriores podrán realizarse, según su naturaleza, en cualquier momento de la primera instancia o de los recursos o de la ejecución de sentencia.

CUARTO.- Puesto que no se desprende del reseñado acuerdo, como se comprueba de los elementos obrantes en autos, que haya prohibición o limitaciones de que habla el art. 19.1 LEC, debe declararse homologada la transacción, y finalizado el juicio.

En su virtud,

AL TRIBUNAL SUPLICAMOS

que, teniendo por presentado este escrito, se sirva admitirlo junto con el documento original que le acompaña, quedando unido a los autos de su razón y conforme a lo manifestado, se proceda a homologar por el Tribunal la transacción judicial alcanzada entre [COMPLETAR] y [COMPLETAR], en los términos expuestos, y se declare finalizado el presente litigio.

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del Abogado/a del actor	Firma del Procurador/a del actor

Firma del Abogado/a del demandado	Firma del Procurador/a del demandado
