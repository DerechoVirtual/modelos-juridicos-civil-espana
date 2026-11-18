---
name: recurso-revision-directo-contra-decreto-resuelve-194
description: "Redacta el escrito «Recurso de revisión directo contra el decreto que resuelve la impugnación de tasación de costas» (formulario 194 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Recurso de revisión directo contra el decreto que resuelve la impugnación de tasación de costas

> Formulario 0194 del plugin **Ejecución civil** · revisado el 17-11-2026.

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
- [ ] Nº
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] Nº DE PROCEDIMIENTO
- [ ] ACTO O RESOLUCIÓN
- [ ] FECHA (5 veces)
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] IMPORTE (5 veces)
- [ ] COLEGIO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…D./Doña.»; «… tengo acreditada en los autos de juicio»; «… Colegio de Abogados, en este caso el de»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 241 y 245 LEC

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

### Formulario 0194 · Recurso de revisión directo contra el decreto que resuelve la impugnación de tasación de costas

- Año del modelo: 2021
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 23 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Recurso de revisión frente al Decreto desestimando la impugnación por excesivos de los honorarios del letrado, cuando los mismos resultan manifiestamente desproporcionados.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [Nº]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Doña. [COMPLETAR], Procurador/a de los Tribunales, actuando en nombre de [NOMBRE DEL REPRESENTADO/A], cuya representación tengo acreditada en los autos de juicio [COMPLETAR] nº [Nº DE PROCEDIMIENTO], seguido contra [ACTO O RESOLUCIÓN], ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que el pasado día [FECHA] se me ha notificado el decreto de fecha [FECHA], por el que se resuelve la impugnación de la tasación de costas de fecha [FECHA], y estimando el mismo lesivo para los intereses de mi mandante, dicho sea en términos de defensa, dentro del plazo de cinco días legalmente establecido en el art. 454.bis LEC, ante el Tribunal interpongo contra el mismo recurso de revisión, fundamentándolo en las siguientes:

ALEGACIONES

PRIMERA.- El decreto impugnado acuerda desestimar la impugnación por excesivos de los honorarios del letrado D./Dña. [NOMBRE Y APELLIDOS] incluidos en la tasación de costas de fecha [FECHA], por lo que puede ser recurrido directamente en revisión, tal como establece el art. 246.4 en relación con 454 bis.1, ambos LEC, al estar prevenido expresamente en la Ley.

SEGUNDA.- A juicio de esta parte, el decreto recurrido infringe los arts. 241 y 245 LEC al desestimar la impugnación formulada por esta parte por ser excesivos los honorarios del letrado D./Dña. [NOMBRE Y APELLIDOS], incluidos en la tasación de costas, por inaplicación de las pautas de valoración usuales, reiteradas en la doctrina jurisprudencial, que exigen la ponderación de las circunstancias concurrentes en cada caso en función del grado de complejidad del asunto y trabajo realizado, así como la adecuación de la minuta de honorarios a los criterios orientadores de Honorarios Profesionales del Colegio de Abogados, en este caso el de [COMPLETAR].

Los citados criterios jurisprudenciales se recogen, entre otros muchos, en el ATS I de 10 de enero de 2005, rec. 1884/1998, que expresa que debe atenderse a todas las circunstancias concurrentes, tales como trabajo realizado en relación con el interés y cuantía económica del asunto, tiempo de dedicación, dificultades del escrito de impugnación, resultados obtenidos, etc., sin que por tanto sean determinantes por sí solos ni la cuantía ni los criterios del Colegio de Abogados, precisamente por ser éstos de carácter orientador.

Criterios reiterados más recientemente en AATS I de 1 de marzo de 2011, rec. 2477/2005; 29 de mayo de 2012, rec. 935/2008; o 19 de abril de 2017, rec. 2095/2014.

Como vemos, conforme a jurisprudencia inconcusa, es criterio consolidado la no aplicación automática, en ningún caso, del Baremo Orientador del Colegio de Abogados, sino la realización de una media ponderada y razonable de las circunstancias concurrentes en el caso concreto.

Jurisprudencia que tiene reflejo en la doctrina de apelación. Así, ningún Tribunal se limita a aplicar automáticamente y sin ningún tipo de valoración crítica de las circunstancias concurrentes el resultado obtenido por la «tabla» del Colegio de Abogados, sino que la jurisprudencia exige que se haga un examen pormenorizado de las circunstancias concurrentes, pues "no se trata de predeterminar, fijar o decidir cuáles deben ser los honorarios del letrado de la parte favorecida por la condena en costas, ya que el trabajo de éste se remunera por la parte a quien defiende y con quien le vincula una relación de arrendamiento de servicios, libremente estipulada por las partes contratantes, sino de determinar la carga que debe soportar el condenado en costas respecto de los honorarios del letrado minutante, pues aunque la condena en costas va dirigida a resarcir al vencedor de los gastos originados directa e inmediatamente en el pleito entre los que se incluyen los honorarios del letrado, la minuta incluida en la tasación debe ser una media ponderada y razonable dentro de los parámetros de la profesión" (por todas, SAP Madrid de 27 de junio de 2014, rec. 743/2012).

En el decreto impugnado, el Abogado minutante realizó un escrito de oposición en el que se limitó a oponerse al recurso y solicitar la confirmación de la sentencia, sin realizar ningún tipo de desarrollo argumental, por lo que la aplicación estricta del Baremo con la consiguiente reclamación de [IMPORTE] euros, es totalmente desproporcionada para el caso, de lo que resulta que, ponderando la trascendencia del escrito de oposición, lo allí discutido, el trabajo efectivamente realizado, y los parámetros normales de la profesión que derivan del Baremo del Colegio de Abogados de [COLEGIO], entendemos que debe reducirse la cuantía en aplicación de la doctrina jurisprudencial antes expresada, por lo que se solicita que se revoque el Decreto impugnado, y se modifique la tasación de costas, reduciendo la minuta del Abogado D./Dña. [NOMBRE Y APELLIDOS] a la razonable cuantía de [IMPORTE] euros propuesta en nuestro escrito de impugnación.

Hemos de señalar, que es práctica forense habitual, tanto en el Tribunal Supremo, como en las distintas Audiencias Provinciales, moderar los honorarios de la asistencia letrada cuando, en aplicación del Baremo Orientador, el mismo resulta claramente desproporcionado, como señala el ya citado ATS I de 19 de abril de 2017, rec. 2095/2014.

Por ello, para el caso de que se considere que la cantidad propuesta por esta parte ( euros más IVA), resultara exigua o excesiva, solicitamos que se minore los mismos a la cantidad de [IMPORTE] euros más IVA, o a la cantidad que razonablemente estime el Tribunal conveniente, a la vista de la trascendencia del asunto, el trabajo efectivamente desarrollado y los parámetros normales de la profesión.

TERCERA.- Se acompaña a este escrito justificante acreditativo del depósito efectuado por importe de [IMPORTE] euros, en la cuenta de depósitos y consignaciones del Tribunal, conforme dispone la DA 15ª LOPJ.

Por lo expuesto, SE SOLICITA que teniendo por presentado este escrito, con justificante de traslado, se sirva admitirlo, tener por interpuesto recurso directo de revisión contra el decreto dictado por el Letrado de la Administración de Justicia de ese órgano de fecha [FECHA] y, tras los trámites legales, se dicte por el Tribunal auto por el que se revoque el decreto impugnado, estimando la impugnación de la tasación por excesivas y reduciendo la cuantía de la minuta del Abogado D./Dña. [NOMBRE Y APELLIDOS] a la cantidad de [IMPORTE] euros o a la cantidad que razonablemente estime conveniente, a la vista de la trascendencia del asunto, el trabajo efectivamente desarrollado y los parámetros normales de la profesión.

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del Abogado

Firma del Procurador
