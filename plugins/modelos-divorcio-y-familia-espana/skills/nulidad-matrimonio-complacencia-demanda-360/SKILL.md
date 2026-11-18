---
name: nulidad-matrimonio-complacencia-demanda-360
description: "Redacta el escrito «Nulidad de matrimonio de complacencia: demanda» (formulario 360 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Nulidad de matrimonio de complacencia: demanda

> Formulario 0360 del plugin **Familia** · revisado el 17-11-2026.

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

- (media) Excluye el MASC por el art. 4.1, párrafo segundo, LO 1/2025 (materia indisponible), no por el art. 5.2. El argumento es defendible, pero ninguna letra del art. 5.2 recoge esta materia: advertir del riesgo de inadmisión (art. 403.2 LEC).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (15 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] COLEGIO
- [ ] LOCALIDAD (3 veces)
- [ ] Nº DE DOCUMENTO
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Nº (2 veces)
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…con domicilio en esta ciudad»; «…se a los siguientes Hechos PRIMERO.- Don»; «…y Doña»; «…contrajeron matrimonio civil en»; «…con fecha de»; «…s el de gananciales. CUARTO.- Don y Doña»; «…ron a través de un chat de citas llamado»; «…viajó a»; «…se marchó a casa de unos parientes en»; «… NULIDAD MATRIMONIAL DE LOS CÓNYUGES DON»; «…y DOÑA»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 73.1 del Código Civil
- artículo 45 del Código Civil

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

### Formulario 0360 · Nulidad de matrimonio de complacencia: demanda

- Año del modelo: 2019
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 36 campos de relleno marcados en blanco; 4 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº, Nº DE DOCUMENTO)
- Avisos de la revisión: (media) Excluye el MASC por el art. 4.1, párrafo segundo, LO 1/2025 (materia indisponible), no por el art. 5.2. El argumento es defendible, pero ninguna letra del art. 5.2 recoge esta materia: advertir del riesgo de inadmisión (art. 403.2 LEC).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD DEL TRIBUNAL DE INSTANCIA DE [SEDE] QUE POR TURNO CORRESPONDA

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

DON/DOÑA [NOMBRE Y APELLIDOS] Procurador de los Tribunales con número de colegiado/a, en representación de DON/DOÑA [NOMBRE Y APELLIDOS] con domicilio en esta ciudad [COMPLETAR] Calle [CALLE], y provisto de D.N.I. según acredito mediante escritura de poder que debidamente bastanteada acompaño en forma como documento número 1 y bajo la dirección letrada de DON/DOÑA [NOMBRE Y APELLIDOS], abogado/a nº [NÚMERO] de Colegio de Abogados de [COLEGIO] como mejor proceda en Derecho ante el Tribunal comparezco y DIGO:

Que en la representación que ostento deduzco DEMANDA DE NULIDAD MATRIMONIAL, contra DON/DOÑA [NOMBRE Y APELLIDOS], con Tarjeta de Residencia nº [NÚMERO] y domicilio en [LOCALIDAD] Calle [CALLE] por la causa tipificada en el artículo 73.1 del Código Civil, en base a los siguientes

Hechos

PRIMERO.- Don [COMPLETAR] y Doña [COMPLETAR] contrajeron matrimonio civil en [COMPLETAR] con fecha de [COMPLETAR], inscrito en el Registro Civil de [LOCALIDAD] según acredito mediante documento núm. [Nº DE DOCUMENTO]

SEGUNDO.- Del citado matrimonio no han nacido hijos.

TERCERO.- No se otorgaron capitulaciones matrimoniales ni antes ni después del matrimonio por lo que el régimen económico matrimonial es el de gananciales.

CUARTO.- Don y Doña [COMPLETAR] se conocieron a través de un chat de citas llamado [COMPLETAR]. Comenzaron una relación on line. El /ella le manifestó la conveniencia dada su situación laboral y personal de conseguir viajar a España y obtener la residencia legal en este país.

Así, Don/Doña [NOMBRE Y APELLIDOS] viajó a [COMPLETAR] y se casaron en el consulado de España en la citada ciudad sin haberse apenas conocido. Con posterioridad regresaron a España y se instalaron en el domicilio de Don/Doña [NOMBRE Y APELLIDOS] en un primer momento si bien Don/Doña [NOMBRE Y APELLIDOS] se marchó a casa de unos parientes en [COMPLETAR] a los tres días de su llegada.

QUINTO.- Por tanto Don/Doña [NOMBRE Y APELLIDOS], nunca otorgaron verdadero consentimiento matrimonial y nunca tuvo voluntad de contraer matrimonio sino de utilizarlo como medio para conseguir la residencia legal en España de Don/Doña [NOMBRE Y APELLIDOS]

SEXTO.- Don/Doña [NOMBRE Y APELLIDOS] falleció a los tres meses de estos hechos sin que hubiera iniciado los trámites de nulidad matrimonial y/o divorcio.

En orden a los efectos o medidas consecuencia de orden personal y patrimonial derivados de la nulidad, recordamos como se ha reseñado el sistema económico matrimonial era el de la sociedad de gananciales y Don/Doña [NOMBRE Y APELLIDOS] posee un saneado patrimonio consistente en [DESCRIBIR].

A los anteriores hechos le son de aplicación los siguientes

Fundamentos de Derecho

I

Artículo 769 LECiv, sobre la competencia.

Correspondiendo el conocimiento de la demanda al Tribunal de Instancia del domicilio conyugal sito en [LOCALIDAD] quedando atribuida a las Secciones de Familia, Infancia y Capacidad, especializadas [NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).] en el conocimiento de esta materia.

II

Artículos 770 LECiv, y 437 y siguientes de la LECiv en cuanto al procedimiento a seguir, por los trámites establecidos para el Juicio Verbal con las salvedades previstas en el artículo 770 LECiv.

III

Artículo 74 del Código Civil, que faculta a los cónyuges y demás personas con interés legítimo y directo, requisito que concurre en mi mandante por ser el único hijo de Don/Doña [NOMBRE Y APELLIDOS]. según acredito mediante certificado literal de nacimiento.

Es preceptiva la intervención del Ministerio Fiscal de conformidad a su Estatuto Orgánico.

IV

La presente demanda no está sujeta al previo intento de resolución de controversias en vía no jurisdiccional, por tratarse de materias excluidas del requisito de procedibilidad, de acuerdo con el art. 4.1 II LO 1/2025, por cuanto se solicita únicamente un pronunciamiento sobre el vínculo matrimonial (nulidad), al tratarse de procedimientos no negociables o dependientes del transcurso del tiempo, quedando estos procesos fuera del principio de disponibilidad.

V

Respecto a los Fundamentos de Derecho material de la acción deducida señalar que el artículo 45 del Código Civil establece que: “No hay matrimonio sin consentimiento matrimonial. La condición, término o modo del consentimiento se tendrá por no puesta.”

Y el artículo 73 del mismo texto legal señala que: “Es nulo cualquiera que sea la forma de su celebración:

1.º El matrimonio celebrado sin consentimiento matrimonial.”

El matrimonio sin consentimiento por parte de cualquiera de los cónyuges anula el matrimonio. Es obvio que se contrajo matrimonio sin verdadera voluntad de constituir vínculo matrimonial y a los solos efectos de conseguir por Don/Doña [NOMBRE Y APELLIDOS] residencia legal en España y no los fines que el matrimonio conlleva.

Muy esclarecedora a este respecto es, en un caso muy similar a éste, la Sentencia dictada por la Audiencia Provincial de Guipúzcoa Audiencia Provincial de Guipúzcoa (Sección 3ª) nº 59/2016 de 30 marzo, rec. 3047/2016 en el que se declara la nulidad matrimonial a instancia de la entidad «MUTUALIA, mutua de Accidentes de Trabajo y Enfermedades Profesionales de la Seguridad Social nº 2» en la que se confirma la Sentencia de Primera Instancia y en la que se declara la nulidad de matrimonio celebrado no con la finalidad de contraer matrimonio, sino para regularizar la situación en España de la esposa sin que hubiera existido vivienda y convivencia conyugal.

VI

Artículo 394 LECiv, sobre las costas procesales.

Por todo lo cual,

SUPLICO AL TRIBUNAL: Que teniendo por presentada la presente demanda con los documentos que se adjuntan y copias de todo ello, se sirva admitirlo, tenga al procurador que suscribe por personado y parte en la representación que ostenta de Don/Doña [NOMBRE Y APELLIDOS], y previo recibimiento del pleito a prueba que desde este momento se deja interesado, tras los trámites oportunos, con la preceptiva intervención del Ministerio Fiscal, se dicte Sentencia, por la que se declare, la NULIDAD MATRIMONIAL DE LOS CÓNYUGES DON [COMPLETAR] y DOÑA [COMPLETAR] extendiéndose la misma a todos los actos y derechos que el demandado Don/Doña [NOMBRE Y APELLIDOS] disfruta, consecuencia del fraudulento matrimonio y con expresa condena en costas.

Es Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Fdo. LetradoFdo. Procurador

Coleg. núm. [Nº]

Coleg. núm. [Nº]
