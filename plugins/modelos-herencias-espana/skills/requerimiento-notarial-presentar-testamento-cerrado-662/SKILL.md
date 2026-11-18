---
name: requerimiento-notarial-presentar-testamento-cerrado-662
description: "Redacta el escrito «Requerimiento notarial para presentar un testamento cerrado» (formulario 662 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Requerimiento notarial para presentar un testamento cerrado

> Formulario 0662 del plugin **Sucesiones** · revisado el 17-11-2026.

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

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] FECHA (4 veces)
- [ ] Nº
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…A LA NOTARÍA DE»; «…, mayor de edad, con domicilio»; «…, en fecha [FECHA] de»; «…, en fecha [FECHA] de [COMPLETAR] de»; «…, autorizado en la Notaría de»; «…padre del solicitante, de vecindad civil»; «…, falleció el día [FECHA] de»; «…alleció el día [FECHA] de [COMPLETAR] de»; «…rgado testamento cerrado ante el Notario»; «…en fecha [FECHA] de»; «…en fecha [FECHA] de [COMPLETAR] de»; «…ima Voluntad que acompaño como documento»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 712.3 y 713 del Código Civil

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

### Formulario 0662 · Requerimiento notarial para presentar un testamento cerrado

- Año del modelo: 2015
- Revisión 17-11-2026: 24 campos de relleno marcados en blanco; 7 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA NOTARÍA DE [COMPLETAR]

D. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio [COMPLETAR], provisto del D.N.I., en mi propio nombre, ante la Notaría comparezco y

DIGO:

- Que al amparo de lo dispuesto en el art. 57.2 de la Ley del Notariado, por medio del presente escrito solicito que se requiera a D. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], quien me consta que tiene en su poder el testamento cerrado otorgado por D. [NOMBRE Y APELLIDOS], con último domicilio en [LOCALIDAD], en fecha [FECHA] de [COMPLETAR] de [COMPLETAR], autorizado en la Notaría de [COMPLETAR], en base a los siguientes

HECHOS Y FUNDAMENTOS

El causante D. [NOMBRE Y APELLIDOS], padre del solicitante, de vecindad civil [COMPLETAR], falleció el día [FECHA] de [COMPLETAR] de [COMPLETAR] en esta localidad a la edad de [Nº] años (acompaño como documento número [Nº DE DOCUMENTO] certificado de defunción del causante).

El causante había otorgado testamento cerrado ante el Notario [COMPLETAR] en fecha [FECHA] de [COMPLETAR] de [COMPLETAR], tal como consta inscrito en el Registro General de Actos de Última Voluntad que acompaño como documento [COMPLETAR], constando a este solicitante por manifestación del propio causante que el testamento fue entregado por su padre a su otro hermano D. [NOMBRE Y APELLIDOS], que lo tiene en su poder.

Habiendo transcurrido en exceso el plazo de diez días desde el fallecimiento del otorgante, D. no ha presentado el testamento conforme a lo previsto en el Código Civil, por lo que el solicitante se ve en la obligación de solicitar que se le requiera para que presente el testamento en esta Notaría, advirtiéndole del contenido de los artículos 712.3 y 713 del Código Civil.

Por lo anteriormente expuesto,

SOLICITO A LA NOTARÍA que tenga por formulada esta solicitud con la documentación que acompaño y, en virtud de la misma, se requiera a D. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], para que presente ante esa Notaría el testamento cerrado otorgado por el causante D. [NOMBRE Y APELLIDOS] en fecha [FECHA] de [COMPLETAR] de [COMPLETAR], apercibiéndole del contenido de los artículos 712.3 y 713 del Código Civil.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

(Firma del solicitante)

========================================================================
