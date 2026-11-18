---
name: oposicion-monitorio-paso-juicio-ordinario-1025
description: "Redacta el escrito «Oposición al monitorio con paso al juicio ordinario» (formulario 1025 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición al monitorio con paso al juicio ordinario

> Formulario 1025 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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

- [ ] NÚMERO (3 veces)
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] COLEGIO
- [ ] FECHA
- [ ] IMPORTE
- [ ] Si la cuantía lo exige: Se firma este escrito por Procurador y Abogado (art. 818 LEC)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…/»; «…roceda en derecho DIGO: Que con fecha de»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 818 de la LEC
- art. 815.1 de la LEC
- art. 818 LEC

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

### Formulario 1025 · Oposición al monitorio con paso al juicio ordinario

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 17 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Proceso monitorio n.º [NÚMERO] / [COMPLETAR]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] PLAZA Nº [NÚMERO]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, interviniendo en nombre de D./Dña. [NOMBRE Y APELLIDOS] en virtud de la representación que acredito con la escritura de poder que acompaño, en la que constan las circunstancias personales de mi mandante, y cuya devolución solicito previa su oportuna constancia, en autos ante el tribunal comparezco bajo la dirección del Letrado D./Dña. [NOMBRE Y APELLIDOS], Colegiado n.º [NÚMERO] del Colegio de Abogados de [COLEGIO], y como mejor proceda en derecho DIGO:

Que con fecha de [COMPLETAR] se me ha notificado el decreto del Letrado de la Administración de Justicia de fecha [FECHA] mediante el que se acuerda requerir a mi poderdante el pago de la suma de [IMPORTE] euros reclamada con la petición inicial de proceso monitorio formulada por D./Dña. [NOMBRE Y APELLIDOS]

Dentro de plazo legal y al amparo de lo dispuesto en el art. 818 de la LEC, formulo el presente ESCRITO de OPOSICIÓN a la reclamación deducida mediante petición inicial de proceso monitorio por D./Dña. [NOMBRE Y APELLIDOS], sentando como correlativos a los del escrito de petición inicial los siguientes

HECHOS

 (Expresar la/s causa/s de la oposición al pago. Rebatir o puntualizar sucintamente los hechos aducidos en la solicitud —se pueden aportar documentos que apoyen el relato fáctico alternativo—. Aducir hechos que apoyen la oposición al pago.)

A los hechos antecedentes resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

Conforme, a los meros efectos procesales, con el correlativo.

Requisitos procesales y trámite

• Se presenta este escrito de oposición a la reclamación formulada contra mi poderdante dentro de los veinte días siguientes a la notificación de la resolución por la que se acuerda el requerimiento de pago a mi mandante (art. 815.1 de la LEC).

• [Si la cuantía lo exige: Se firma este escrito por Procurador y Abogado (art. 818 LEC)].

• Debe seguirse para sustanciar esta oposición el trámite previsto en el art. 818 de la LEC.

Causa/s de oposición

Invoco la/s siguiente/s causas de oposición:

 (desarrollar la/s razón/razones por las que, al entender del requerido, no se debe, en todo o en parte, la cantidad reclamada.)

Por todo lo expuesto,

SUPLICO AL TRIBUNAL: Tenga por presentado este escrito, poder, documentos y copias de todo ello, se sirva admitirlo, teniendo por formulada en tiempo y forma OPOSICIÓN a la reclamación de cantidad formulada por D./Dña. [NOMBRE Y APELLIDOS] mediante la solicitud inicial de proceso monitorio que ha dado lugar a estos autos, ordenando lo necesario para el impulso del trámite procedimental pertinente,

(OPCIONES):

• E imponiendo a D./Dña. [NOMBRE Y APELLIDOS] (reclamante) las costas del proceso si no interpone demanda en el plazo de un mes desde el traslado de esta oposición.

Es Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
