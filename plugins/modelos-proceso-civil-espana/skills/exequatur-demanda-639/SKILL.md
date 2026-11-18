---
name: exequatur-demanda-639
description: "Redacta el escrito «Exequatur: demanda» (formulario 639 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Exequatur: demanda

> Formulario 0639 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (13 veces)
- [ ] CALLE
- [ ] Nº DE DOCUMENTO
- [ ] FECHA
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 21 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Don»; «…unales, en nombre y representación de Dª»; «…de mutuo acuerdo del matrimonio entre Dª»; «…chos y fundamentos de derecho. Hechos Dª»; «…de»; «…de [COMPLETAR] de 19 Dª»; «… nacionalidad española por residencia el»; «…de»; «…rimonio celebrado el seis de Marzo entre»; «…y»; «… 20 declarando disuelto el matrimonio de»; «…y»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 52 de la Ley 29/2015
- art. 54 de la Ley 29/2015

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

### Formulario 0639 · Exequatur: demanda

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 38 campos de relleno marcados en blanco; 4 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015); 4 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

DEMANDA DE EXEQUATUR

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE QUE POR TURNO DE REPARTO CORRESPONDA

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

Don [COMPLETAR], Procurador de los Tribunales, en nombre y representación de Dª [COMPLETAR], residente en [LOCALIDAD], en la C/ [CALLE], según acredito mediante designación del Turno de Oficio/certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], ante el Tribunal comparezco y como mejor proceda en Derecho,

DIGO:

Que por medio del presente escrito, en aplicación de lo preceptuado en los artículos 52 y ss. de Ley 29/2015, de 30 de julio, de cooperación jurídica internacional en materia civil, vengo a presentar DEMANDA DE EXEQUÁTUR de la declaración de disolución de mutuo acuerdo del matrimonio entre Dª [COMPLETAR] y D. dictada por del Tribunal Transitorio de Familia de [LOCALIDAD] de [LOCALIDAD] de [LOCALIDAD] de -, para que tenga efectos legales en España, en base a los siguientes hechos y fundamentos de derecho.

Hechos

Dª [COMPLETAR] contrajo matrimonio con D. el día [FECHA] de [COMPLETAR] de 19

Dª [COMPLETAR] adquirió la nacionalidad española por residencia el [COMPLETAR] de [COMPLETAR] de 20, inscribiendo posteriormente su matrimonio en el Registro Civil Español

El matrimonio fue disuelto mediante resolución del Tribunal Transitorio de Familia de [LOCALIDAD] de [LOCALIDAD] de [LOCALIDAD] de 20

Por ser deseo de la Sra. contraer nuevamente matrimonio en España, necesita que la disolución de su matrimonio sea reconocida en España.

El ex cónyuge de la Sra. [NOMBRE Y APELLIDOS], D. reside actualmente en Perú, siendo su domicilio el siguiente el cual se designa a efectos de comunicaciones.

En prueba de lo expuesto se adjunta la siguiente documentación:

- Partida del matrimonio celebrado el seis de Marzo entre [COMPLETAR] y [COMPLETAR] de 19

- Acta de matrimonio del Registro del Estado Civil con inscripción de disolución del vínculo matrimonial.

- Resolución del Tribunal Transitorio de Familia de [LOCALIDAD] de [LOCALIDAD] de [LOCALIDAD] de 20 declarando disuelto el matrimonio de [COMPLETAR] y [COMPLETAR]

- Acta de conciliación con acuerdo total de [COMPLETAR] de [COMPLETAR] de 20 por la que se establece el régimen de “tenencia” y alimentos de las hijas del matrimonio, así como la renuncia de los cónyuges a cualquier pensión alimenticia.

- Inscripción del matrimonio en el Registro Civil español el [COMPLETAR] de [COMPLETAR] de 20

- Certificados de nacimiento de [COMPLETAR] y [COMPLETAR], hijas de la Sra. [NOMBRE Y APELLIDOS] y el Sr. [NOMBRE Y APELLIDOS]

A los anteriores hechos le son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

I.-COMPETENCIA Y JURISDICCIÓN

Según el artículos 52 de la Ley 29/2015, de 30 de julio, de cooperación jurídica internacional en materia civil son competentes para conocer de esta solicitud los Tribunales de Instancia de Madrid, por ser el lugar en que dicha resolución va a producir sus efectos.

Asimismo, tanto la demandante como las hijas del matrimonio residen en la actualidad en España.

II.-PROCEDIMIENTO

La tramitación del presente procedimiento deberá desarrollarse por los cauces establecidos en el artículos 52 y ss. de Ley 29/2015, de 30 de julio, de cooperación jurídica internacional en materia civil y el art. 399 y siguientes de la Ley de Enjuiciamiento Civil.

III.- LEGITIMACIÓN

Ambas partes se encuentran legitimadas, por haber sido los cónyuges para cuya declaración de divorcio de mutuo acuerdo se solicita la concesión del exequátur.

IV.- REQUISITOS FORMALES

De conformidad con lo establecido en el artículo 231 de la Ley de Enjuiciamiento Civil, esta parte manifiesta su convicción y voluntad de haber cumplido con todos los requisitos exigidos por la Ley; si bien, en caso de que se haya incurrido en algún defecto, solicitamos que se otorgue el plazo suficiente para que los mismos puedan ser subsanados.

V.- POSTULACIÓN Y DEFENSA

Según establece el art. 54 de la Ley 29/2015, la demandante es representada por el procurador de los tribunales Don [COMPLETAR] y asistida por el letrado D. [NOMBRE Y APELLIDOS]

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que teniendo por presentado éste escrito junto con los documentos que se acompañan y sus copias, se sirva admitirlos y, previos los trámites legales oportunos dicte en su día sentencia otorgando el EXEQUÁTUR de la declaración de disolución del vínculo matrimonial entre [COMPLETAR] y [COMPLETAR], dictada por resolución del Tribunal Transitorio de Familia de [LOCALIDAD] de [LOCALIDAD] de [LOCALIDAD] de 20

Por ser Justicia que respetuosamente solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Procurador/a de los Tribunales	Letrado/a

========================================================================
