---
name: impugnacion-testamento-pretericion-212
description: "Redacta el escrito «Impugnación de testamento por preterición» (formulario 212 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Impugnación de testamento por preterición

> Formulario 0212 del plugin **Sucesiones** · revisado el 17-11-2026.

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

- [ ] SEDE (2 veces)
- [ ] CALLE
- [ ] NÚMERO
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… amparo de lo dispuesto en los artículos»; «…del demandante. D. Mauro nació el día de»; «…o del matrimonio de Dª Marcela y D. Luis»; «…tos de estas hermanas como documento nºs»; «…co testamento en 1970 ante el Notario D.»; «…alicio de sus bienes a su esposo D. Luis»; «…mento, que aportamos como documentos nºs»; «…acompañan al presente dotados de números»; «…a»; «…are abierta la sucesión intestada de Dª.»; «…rte demandada. Es justicia que pido en a»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 251.12 de la LEC
- art. 5 de la Ley Orgánica 1/2025
- artículo 807 CC
- artículo 813 CC
- artículo 814 del Código Civil
- artículo 394 LEC

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

### Formulario 0212 · Impugnación de testamento por preterición

- Año del modelo: 2020
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 17 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Encabezamiento

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

QUE POR TURNO CORRESPONDA

Que mediante el presente escrito y en la representación que ostento, al amparo de lo dispuesto en los artículos [COMPLETAR], vengo a interponer DEMANDA DE JUICIO ORDINARIO EN EJERCICIO DE ACCIÓN DE IMPUGNACIÓN DEL TESTAMENTO DE Dª MARCELA por preterición no intencional contra Dª INES Y Dª ESTELA (hermanas de nuestro representado), mayores de edad, provistas de DD.NN.II., con domicilio en Calle [CALLE], sobre la base de los siguientes

HECHOS

Primero. – Filiación del demandante.

D. Mauro nació el día de [COMPLETAR], fruto del matrimonio de Dª Marcela y D. Luis [COMPLETAR].

Así lo acreditamos mediante el certificado de nacimiento que aportamos como documento nº 2 y el Libro de Familia que aportamos como documento nº 3.

Dª Marcela estuvo casada en primeras nupcias con D. Agapito, habiendo nacido de esta matrimonio una hija llamada Inés en 1955.

Y fruto del segundo matrimonio con Don Luis nació en 1964 otra hija llamada Estela.

Aportamos los certificados de nacimientos de estas hermanas como documento nºs [COMPLETAR] así como el certificado de este segundo matrimonio.

Segundo. – Herencia testada de Dª Marcela, madre de nuestro mandante.

Dª Marcela otorgó su único testamento en 1970 ante el Notario D. [COMPLETAR], al número [NÚMERO] de su protocolo, en cuya virtud instituye herederas universales de todos sus bienes, derechos y acciones a sus expresadas hijas Inés y Estela, a quienes sustituirán, para todos los casos legales de la vulgar, excepto la renuncia, por sus respectivos descendientes. Y lega el usufructo universal y vitalicio de sus bienes a su esposo D. Luis [COMPLETAR], con cargo al tercio de libre disposición.. Aportamos copia auténtica de dicho testamento como documento nº [Nº DE DOCUMENTO].

D. Luis ha premuerto a Dª Marcela, tal y como acreditamos con el certificado de defunción del mismo como documento nº [Nº DE DOCUMENTO].

Al fallecer Dª Marcela en estado de viuda en 2019 se abre el testamento y se desvela que el heredero forzoso Mauro ha sido desheredado de facto, por no estar incluido en el testamento.

Aportamos el certificado de defunción de la causante, el certificado de actos de última voluntad y el precitado testamento, que aportamos como documentos nºs [COMPLETAR] respectivamente.

Tercero.- Mi representado ha intentado llegar a un acuerdo con sus hermanas para repartir equitativamente la herencia, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial, siendo los resultados totalmente infructuosos, como se acredita con los DOCUMENTOS que se acompañan al presente dotados de números [COMPLETAR] a [COMPLETAR], lo que nos obliga a interponer la presente demanda.

FUNDAMENTOS DE DERECHO

I.- Competencia.- Es competente el Tribunal de Instancia de [SEDE] que por turno corresponda, en virtud del artículo 50.1 y 52.4º LEC, por ser el correspondiente al del partido del último domicilio del causante, concretamente en la calle de la localidad de

II.- Legitimación.- Nuestro representado está legitimado activamente al ostentar la condición de heredero legítimo de su difunta madre.

Y pasivamente lo están sus hermanas por estar instituídas como herederas universales en una disposición testamentaria que se pretende anular.

III.- Procedimiento.- El presente procedimiento debe sustanciarse por los trámites señalados para el juicio ordinario por razón de la cuantía, al superar el límite de 15.000€, ex artículo 251.12 de la LEC.

IV.- Postulación y defensa.- Nuestro mandante comparece debidamente representado por medio de Procurador de los Tribunales y asistidos por Letrado, de acuerdo con lo dispuesto en el artículo 23 y 31 ambos de la LEC.

V.- Cumplimiento de los requisitos de procedibilidad.- La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VI.- FONDO DEL ASUNTO:

El Código Civil en su artículo 806 determina que “Legítima es la porción de bienes de que el testador no puede disponer por haberla reservado la ley a determinados herederos, llamados por esto herederos forzosos”, siendo dichos herederos forzosos ex artículo 807 CC:

1.º Los hijos y descendientes respecto de sus padres y ascendientes.

En relación con ello, el artículo 813 CC prohíbe al testador privar de este derecho “El testador no podrá privar a los herederos de su legítima sino en los casos expresamente determinados por la ley”.

Por su parte, dispone el artículo 814 del Código Civil:

“La preterición de un heredero forzoso no perjudica la legítima. Se reducirá la institución de heredero antes que los legados, mejoras y demás disposiciones testamentarias.

Sin embargo, la preterición no intencional de hijos o descendientes producirá los siguientes efectos:

• 1.º Si resultaren preteridos todos, se anularán las disposiciones testamentarias de contenido patrimonial.

• 2.º En otro caso, se anulará la institución de herederos, pero valdrán las mandas y mejoras ordenadas por cualquier título, en cuanto unas y otras no sean inoficiosas. No obstante, la institución de heredero a favor del cónyuge sólo se anulará en cuanto perjudique a las legítimas.

Los descendientes de otro descendiente que no hubiere sido preterido, representan a éste en la herencia del ascendiente y no se consideran preteridos.

Si los herederos forzosos preteridos mueren antes que el testador, el testamento surtirá todos sus efectos.

A salvo las legítimas, tendrá preferencia en todo caso lo ordenado por el testador.”

La Sentencia 669/2006 de 22 de junio del TS determina la distinción en preterición intencional y no intencional o errónea, entendiendo esta última cuando el testador omitió la mención del legitimario hijo o descendiente (no otro) porque ignoraba (erróneamente) su existencia" para en consecuencia, estimar que en el presente caso el testador omitió al único legitimario, su hijo, en el testamento, ignorando su existencia.

A propósito de ésta es unánime la Jurisprudencia (por todas Sentencia 17/2001 del TS de 23 de enero) al estimar que siempre se produce en los supuestos de testamento otorgado antes del nacimiento de los hijos o descendientes, afirmando el Tribunal Supremo que "según pacífica doctrina, en el caso de que los hijos hayan nacido después de otorgado el testamento la no intencionalidad de su preterición en el mismo queda demostrada "ex re ipsa". Conclusión que todavía se impone con mayor fuerza cuando...el momento de la concepción del hijo preterido es asimismo posterior a aquel otorgamiento...Como esta Sala tuvo ocasión de declarar en la ya lejana sentencia de 1 de julio de 1969, la preterición ha de resultar exclusivamente del testamento, por ser éste la expresión más solemne de quien dispone de sus bienes para después de su muerte evitando formular hipótesis sobre la posible causa de la omisión del heredero, ya que la presunta voluntad del causante carece de toda eficacia si no aparece del propio testamento"

El TS determina igualmente que la intencionalidad o no de la preterición ha de referirse al momento del otorgamiento del testamento que es cuando puede valorarse si el testador conocía o no de la existencia del legitimario al omitirlo, es decir, "estos conceptos vienen referidos al testamento, no a la muerte”.

En conclusión, se deberá declarar la nulidad del testamento y dejar sin efecto todas las disposiciones testamentarias patrimoniales.

VII.- Costas.- Ex artículo 394 LEC, se impondrán las costas a la parte que vea en primera instancia rechazadas sus pretensiones.

Por lo expuesto,

AL TRIBUNAL SUPLICO que tenga por presentado este escrito, con sus copias y los documentos acompañados, admita todo ello y dé trámite legal. Tenga por interpuesta demanda en ejercicio de ACCIÓN DE IMPUGNACIÓN DE TESTAMENTO por preterición no intencional otorgado por Dª Marcela contra las demandadas. Y tras los demás trámites legales, incluido el recibimiento del pleito a prueba, se estime íntegramente la demanda y en consecuencia:

1º.- declare la nulidad total de dicha disposición testamentaria, dejándole sin efecto alguno, como consecuencia de la preterición no intencional del heredero forzoso Mauro;

2º.- declare el derecho que le corresponde a nuestro mandante como heredero legitimario en la herencia de su madre Dª Marcela;

3º.- y en consecuencia con lo anterior, declare abierta la sucesión intestada de Dª. [COMPLETAR].

Y ello con expresa imposición de costas a la parte demandada.

Es justicia que pido en a [COMPLETAR]

Ldo. Procurador
