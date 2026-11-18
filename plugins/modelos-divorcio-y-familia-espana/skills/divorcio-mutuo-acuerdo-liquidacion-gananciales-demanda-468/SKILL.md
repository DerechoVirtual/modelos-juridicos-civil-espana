---
name: divorcio-mutuo-acuerdo-liquidacion-gananciales-demanda-468
description: "Redacta el escrito «Divorcio de mutuo acuerdo con liquidación de gananciales: demanda» (formulario 468 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Divorcio de mutuo acuerdo con liquidación de gananciales: demanda

> Formulario 0468 del plugin **Familia** · revisado el 17-11-2026.

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

- (media) Afirma que el mutuo acuerdo «no está sujeto» a MASC: el art. 5.2 LO 1/2025 no lo excluye. Más seguro decir que el requisito se cumple con la negociación directa reflejada en el convenio firmado por ambas partes (arts. 5.1 y 10.2 LO 1/2025).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] PROFESIÓN (2 veces)
- [ ] CALLE
- [ ] FECHA (3 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] Otros 15 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Don»; «… Tribunales en nombre de los esposos Don»; «…y Doña»; «…la esposa, vecinos de la localidad de»; «…, del mes de»; «…, del mes de [COMPLETAR], del año»; «… del año [COMPLETAR], en la localidad de»; «…monio nacieron y viven en la actualidad,»; «…, del mes de»; «…, del mes de [COMPLETAR], del año»; «…, y el día [FECHA], del mes de»; «…, del mes de [COMPLETAR], del año»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 86.5.a) LOPJ
- arts. 775.2 y 777.9 LEC
- art. 90.3 CCiv
- Ley Orgánica 1/2025

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

### Formulario 0468 · Divorcio de mutuo acuerdo con liquidación de gananciales: demanda

- Año del modelo: 2017
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 24 campos de relleno marcados en blanco
- Avisos de la revisión: (media) Afirma que el mutuo acuerdo «no está sujeto» a MASC: el art. 5.2 LO 1/2025 no lo excluye. Más seguro decir que el requisito se cumple con la negociación directa reflejada en el convenio firmado por ambas partes (arts. 5.1 y 10.2 LO 1/2025).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

Don [COMPLETAR], Procurador de los Tribunales en nombre de los esposos Don [COMPLETAR] y Doña [COMPLETAR], mayores de edad, de profesión [PROFESIÓN] el marido y de profesión [PROFESIÓN] la esposa, vecinos de la localidad de [COMPLETAR], con domicilio en calle [CALLE], número, lo que acredito mediante copia electrónica de poder notarial de representación que acompaño, ante el Tribunal que por turno de reparto corresponda comparezco y como mejor proceda en Derecho, DIGO:

Que en la indicada representación, siguiendo instrucciones de mis principales, promuevo petición de DIVORCIO DE MUTUO ACUERDO, la cual baso en los siguientes

HECHOS

Mis principales contrajeron matrimonio en forma (civil o religiosa que corresponda), el día [FECHA], del mes de [COMPLETAR], del año [COMPLETAR], en la localidad de [COMPLETAR], conforme acredito mediante certificación literal de matrimonio expedida por el Registro civil, que acompaño como documento núm. uno, constando inscrito el mismo en el Tomo ..., Folio, Sección ... (en virtud de certificación eclesiástica, de ser matrimonio canónico), de lo que se deduce que se cumple con creces el requisito que exige el Código civil del transcurso de tres meses desde la celebración del matrimonio.

Del citado matrimonio nacieron y viven en la actualidad, [COMPLETAR] y .. nacidos, respectivamente, el día [FECHA], del mes de [COMPLETAR], del año [COMPLETAR], y el día [FECHA], del mes de [COMPLETAR], del año [COMPLETAR], según acredito mediante las respectivas certificaciones literales de nacimiento expedidas por el Registro civil de [LOCALIDAD], que acompaño como documentos núms. dos y tres.

El domicilio familiar está sito en [LOCALIDAD], según acredito mediante certificación de empadronamiento, que acompaño como documento núm. cuatro.

El régimen económico del matrimonio es el de sociedad de gananciales, ya que ambos esposos tenían vecindad civil ... cuando contrajeron matrimonio y no se han otorgado capitulaciones matrimoniales.

Siendo voluntad de ambas partes proceder a la disolución por divorcio de mutuo acuerdo, acompañan como documento núm. cinco, la preceptiva propuesta de convenio regulador en la que se incluye lo relativo a la disolución y liquidación de la sociedad de gananciales, a fin de que, previa su ratificación por separado, e Informe del Ministerio Fiscal, sea aprobado judicialmente y queden regulados conforme al mismo los efectos derivados de dicha disolución.

A los anteriores Hechos le son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

I.- Competencia y procedimiento. Es competente este Tribunal por razón del domicilio conyugal, conforme prevé el artículo 769.1 de la Ley de Enjuiciamiento civil, en relación con lo dispuesto en el art. 86.5.a) LOPJ, debiendo seguirse el procedimiento previsto en el articulo 777 de la citada Ley procesal.

II.- Legitimación. La ostentan ambas partes por su condición de cónyuges del matrimonio cuyo divorcio de mutuo acuerdo se solicita, de conformidad con lo previsto en el art. 81 y 86 del Código civil.

III.- Cumplimiento de los requisitos de procedibilidad. La presente demanda no está sujeta al previo intento de resolución de controversias en vía no jurisdiccional, de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia, por tratarse en sí de un acuerdo consensual y voluntario entre las partes, necesitando únicamente la homologación del mismo por parte del Tribunal, siendo que el convenio regulador (arts. 775.2 y 777.9 LEC y art. 90.3 CCiv) se entiende acreditativo de haber realizado esa actividad negociadora.

IV.- Divorcio de mutuo acuerdo. Artículo 86 en relación con el art. 81 del Código civil.

V.- Efectos derivados o medidas. Artículos 90 y 1392 siguientes y concordantes del Código civil.

VI.- Audiencia de los menores. La audiencia de los menores es preceptiva, conforme a lo previsto en el artículo 92 del Código civil, por tener ambos hijos más de doce años.

VII.- Intervención del Ministerio Fiscal. Procede la intervención del Ministerio Fiscal por existir hijos menores de edad, conforme a lo previsto en el artículo 749. 2 de la L.E.C.

En su virtud

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos acompañados y lo admita; por promovido por el Procurador que suscribe, con quien se entiendan las sucesivas diligencias, en nombre y representación de Don [COMPLETAR] y Doña [COMPLETAR], con devolución de la escritura de poderes acompañada una vez quede testimonio en autos, petición de DISOLUCIÓN MATRIMONIAL POR DIVORCIO DE MUTUO ACUERDO y, por los trámites procesales pertinentes, previa ratificación de las partes por separado, audiencia de los menores y con intervención del Ministerio Fiscal, dicte sentencia por la que, dando lugar a la disolución, determine como efectos derivados de la misma los contenidos en la propuesta de convenio regulador aportado como documento núm. cinco, el cual sea íntegramente aprobado.

Es justicia que insto en [COMPLETAR]. (lugar y fecha)

Firma de Abogado y Procurador.

========================================================================
