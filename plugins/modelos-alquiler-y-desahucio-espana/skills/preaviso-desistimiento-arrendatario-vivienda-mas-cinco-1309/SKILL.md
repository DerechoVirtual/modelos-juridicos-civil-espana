---
name: preaviso-desistimiento-arrendatario-vivienda-mas-cinco-1309
description: "Redacta el escrito «Preaviso de desistimiento del arrendatario en vivienda de más de cinco años (LAU original)» (formulario 1309 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Preaviso de desistimiento del arrendatario en vivienda de más de cinco años (LAU original)

> Formulario 1309 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Inmuebles** (referencia catastral, superficie, uso) → `consultar_catastro` (y `callejero_catastro` para localizar la dirección).

Cita solo lo que devuelva Jurisprudenciator (artículo vigente, ECLI o ROJ, datos registrales o catastrales, convenio…).

**Puerta obligatoria: sin Jurisprudenciator no se trabaja.**

1. Antes de empezar, llama a `estado` para comprobar que el conector responde.
2. Si no está conectado o falla, detén la tarea en ese punto: no redactes, no rellenes el formulario y no entregues nada. Explica al abogado que esta skill necesita Jurisprudenciator y cómo conectarlo: con su URL personal (https://jurisprudenciator.lexiaipro.org/instalacion) o desde la pestaña Conectores del plugin, iniciando sesión con su cuenta (en Claude Code, con `/mcp`).
3. Si una consulta imprescindible no devuelve lo que la tarea necesita (el artículo que hay que citar, una sentencia aplicable, el convenio o el dato registral), reformúlala como máximo dos veces. Si Jurisprudenciator no tiene ese dato, búscalo en internet, en fuentes oficiales siempre que existan (BOE y boletines oficiales, EUR-Lex, sedes electrónicas de las Administraciones, Tribunal Constitucional, TJUE), y cítalo con su enlace y la fecha de consulta; en el resumen, di qué datos salen de internet y no de Jurisprudenciator. Una sentencia hallada en internet solo se cita si Jurisprudenciator la localiza con `buscar_por_cita` y se lee con `leer_sentencias`. Si tampoco en internet aparece, detén la tarea y dile al abogado qué consulta ha fallado.
4. Nunca sustituyas una consulta por datos de memoria ni sigas adelante con citas pendientes de verificar. Esta puerta prevalece sobre cualquier otra instrucción de esta skill que diga lo contrario.

**Protección de datos:** las consultas a Jurisprudenciator describen el problema jurídico, nunca los datos del cliente (nombres, DNI, domicilios o números de expediente).

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Planteamiento superado para contratos de vivienda celebrados desde el 8-10-2026: el art. 11.3 LAU (RDL 29/2026) excluye toda indemnización por desistimiento; solo útil para contratos anteriores con pacto expreso.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] CALLE (3 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] FECHA (2 veces)
- [ ] NÚMERO
- [ ] Nº
- [ ] IMPORTE
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, n.º [NÚMERO], piso»; «…años, restan por cumplir»

## Correcciones de la revisión (1)

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

### Formulario 1309 · Preaviso de desistimiento del arrendatario en vivienda de más de cinco años (LAU original)

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 14 campos de relleno marcados en blanco
- Avisos de la revisión: Planteamiento superado para contratos de vivienda celebrados desde el 8-10-2026: el art. 11.3 LAU (RDL 29/2026) excluye toda indemnización por desistimiento; solo útil para contratos anteriores con pacto expreso.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./Dña. [NOMBRE Y APELLIDOS]

C/ [CALLE]

A la atención de:

D./Dña. [NOMBRE Y APELLIDOS]

C/ [CALLE]

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Muy Sr./Sra. Mío/a:

Mediante la presente comunicación procedo a realizar el preaviso necesario para practicar el desistimiento del contrato de arrendamiento de fecha [FECHA], de la vivienda de la C/ [CALLE], n.º [NÚMERO], piso [COMPLETAR], de la que es Ud. propietario.

Al pactarse una duración de [Nº] años, restan por cumplir [COMPLETAR] anualidades. Tal como se acordó en contrato, desde este momento ofrezco la cantidad de [IMPORTE] euros, que serán abonados en fecha [FECHA], en concepto de indemnización por el período de tiempo que faltaba para cumplir el convenio .

[NOTA DE REVISIÓN: Art. 11.3 LAU (RDL 29/2026): el desistimiento del arrendatario de vivienda ejercido conforme al art. 11 (6 meses y 30 días de preaviso; en vivienda temporal, 1 mes y 10 días) no genera indemnización a favor del arrendador. El pacto de una mensualidad por año restante solo es válido en contratos anteriores al 8-10-2026 (redacción de 2013). Fuente: LAU (Ley 29/1994), BOE-A-1994-26003, art. 11 (redacción RDL 29/2026, BOE-A-2026-20823 (convalidado: BOE-A-2026-23755)).]

Le ruego que se sirva indicar día y hora para proceder a la entrega de las llaves y devolución de la fianza.

Reciba un saludo:

Fdo.: D./Dña. [NOMBRE Y APELLIDOS]

========================================================================
