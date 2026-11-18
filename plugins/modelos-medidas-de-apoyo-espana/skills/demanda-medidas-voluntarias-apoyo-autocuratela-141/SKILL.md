---
name: demanda-medidas-voluntarias-apoyo-autocuratela-141
description: "Redacta el escrito «Demanda de medidas voluntarias de apoyo: autocuratela» (formulario 141 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de medidas voluntarias de apoyo: autocuratela

> Formulario 0141 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (8 veces)
- [ ] Nº DE DOCUMENTO (7 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] COLEGIO
- [ ] CALLE
- [ ] LOCALIDAD (4 veces)
- [ ] FECHA (4 veces)
- [ ] Nº DE EXPEDIENTE
- [ ] Nº DE PROCEDIMIENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Procurador/a de los Tribunales y de Don»; «… y se encuentra en estado de viuda de D.»; «…de alzheimer, diagnosticada desde el año»; «…por el Doctor D.»; «…borado por el Servicio de Psiquiatría de»; «…erio y voluntad en la toma de decisiones»; «…or de mi representado ante el Notario de»; «…D.»; «…presentación que ostento en nombre de D.»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 756.2 LEC
- art. 753 LEC
- arts. 23, 31 y 750 LEC
- art. 253.1 LEC
- art. 255 CCiv
- art. 268 CCiv
- art. 269 CCiv
- arts. 271 CCiv
- art. 394 LEC

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

### Formulario 0141 · Demanda de medidas voluntarias de apoyo: autocuratela

- Año del modelo: 2021
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 38 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda de solicitud de adopción de medidas voluntarias de apoyo a personas con discapacidad y nombramiento de curador.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales y de Don [COMPLETAR], según se acredita mediante certificación del Registro Electrónico de Apoderamientos Judiciales que se adjunta como documento nº [Nº DE DOCUMENTO], a quien asiste el Letrado/a en ejercicio D./Dña. [NOMBRE Y APELLIDOS], colegiado/a nº [Nº DE COLEGIADO/A] del Iltre. Colegio de Abogados de [COLEGIO], con despacho abierto en esta localidad, calle [CALLE], ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que por el presente escrito, en la representación que acredito y siguiendo instrucciones de mi mandante, formulo DEMANDA EN SOLICITUD DE ADOPCIÓN DE MEDIDAS JUDICIALES DE APOYO DE CARÁCTER ESTABLE a favor de Dña. [NOMBRE Y APELLIDOS] con domicilio en [LOCALIDAD], al aparecer incurso en situación de discapacidad, solicitando la constitución de curatela y nombramiento de curador en la persona del solicitante, con intervención del Ministerio Fiscal, todo ello en base a los siguientes:

HECHOS

PRIMERO.- La demandada, Dña. [NOMBRE Y APELLIDOS], es madre de mi representado, como acredito mediante la aportación de certificación literal de del Registro Civil de [LOCALIDAD], que se acompaña como documento nº [Nº DE DOCUMENTO] al presente escrito; y se encuentra en estado de viuda de D. [COMPLETAR], de cuya unión nacieron y viven dos hijos, mi representado y su hermana Dña. [NOMBRE Y APELLIDOS], según se acredita mediante certificaciones del Registro Civil que se acompañan como documentos números

SEGUNDO.- La demandada Dña. padece la enfermedad de alzheimer, diagnosticada desde el año [COMPLETAR] por el Doctor D. [COMPLETAR], tal y como consta acreditado en el informe elaborado por dicho facultativo, que se aporta como documento nº [Nº DE DOCUMENTO], en el cual se concluye que Dña. padecía la enfermedad de Alzheimer, de etiología degenerativa, con carácter persistente e irreversible en el tiempo.

TERCERO.- En estas circunstancias, con fecha [FECHA] fue promovido por mi representado expediente de jurisdicción voluntaria de solicitud de adopción de medidas de apoyo para persona con discapacidad y nombramiento de curador contra el que se formuló oposición por parte de la hermana de mi representado en fecha [FECHA], alegando que la demandada podía valerse por sí misma, y al estar en desacuerdo con que el curador designado fuera mi representado, dando por finalizado el expediente.

Se aporta como documento nº [Nº DE DOCUMENTO] resolución recaída en el citado expediente de jurisdicción voluntaria nº [Nº DE EXPEDIENTE] seguido ante el Tribunal al que me dirijo, cuya incorporación a estos autos se solicitará por medio de otrosí, donde obra asimismo la oposición formulada.

CUARTO.- En la actualidad, Dña. sufre un cuadro de demencia causado por el padecimiento de la enfermedad de Alzheimer de carácter evolutivo y progresivo, en fase avanzada, tal y como consta acreditado en el informe elaborado por el Servicio de Psiquiatría de [COMPLETAR], que se aporta como documento nº [Nº DE DOCUMENTO] del que se infiere la crítica situación mental de Dña. [NOMBRE Y APELLIDOS], con alteraciones en la orientación espacial y temporal, capacidad de reconocer a las personas, y pérdida de criterio y voluntad en la toma de decisiones [COMPLETAR] que "evidencia la falta de capacidad mental de la persona afectada".

QUINTO.- La madre de mi representada reside en la actualidad en el domicilio del demandante, quien se ocupa de forma exclusiva de sus cuidados desde el fallecimiento del marido de la demandada y padre de mi representado en el año

La otra hija de la demandad, residente en [LOCALIDAD], respectivamente, no ha querido ocuparse en ningún momento de su madre, habiendo propuesto a mi representado en reiteradas ocasiones el internamiento de la madre en un centro cerrado, a lo cual siempre se ha negado mi representado por respeto a lo dispuesto por su madre en la escritura de autocuratela de fecha [FECHA] a la que seguidamente se hará referencia.

SEXTO.- Tal como se ha indicado anteriormente, la demandada, en fecha [FECHA], ostentando plena capacidad de obrar, y en previsión de que su enfermedad progresaría de forma degenerativa, otorgó escritura pública respecto a la designación del curador de mi representado ante el Notario de [COMPLETAR] D. [COMPLETAR], manifestando su voluntad de ser cuidada en su persona y bienes por mi representado y de residir en su domicilio junto a la familia de mi representado o, en otro caso, en compañía de sus otra hija, expresando que no quería ser internada en un centro, salvo que fuera estrictamente imprescindible (acompaño como documento nº [Nº DE DOCUMENTO] copia autorizada de la citada escritura de autocuratela) [NOTA DE REVISIÓN: El propio formulario la llama antes «escritura de autocuratela»; la figura es la del art. 271 CC. Fuente: Código Civil (BOE-A-1889-4763) art. 271, redacción Ley 8/2021 (BOE-A-2021-9233).].

Por este motivo, siendo la persona designada mi mandante y habiendo respetado la voluntad de su madre, se interesa que se le nombre como curadora de su madre, reuniendo mi representada las condiciones de aptitud e idoneidad establecidas legalmente, aportando a efectos acreditativos certificado negativo de antecedentes penales como documento nº [Nº DE DOCUMENTO].

A los anteriores hechos son de aplicación los siguientes:

FUNDAMENTOS DE DERECHOI

I.- COMPETENCIA.

De acuerdo con lo establecido en el art. 756.2 LEC corresponderá la competencia a la Sección Civil del Tribunal de Instancia al que me dirijo, por ser el del domicilio de la demandada.

II.- PROCEDIMIENTO.

De acuerdo con lo establecido en el art. 753 LEC, el presente procedimiento se sustanciará por los trámites del Juicio verbal, con las especialidades establecidas en los arts. 748 y ss. LEC y, respecto al proceso de adopción de medidas judiciales de apoyo, de los arts. 756 y ss. LEC.

III.- LEGITIMACIÓN.

De acuerdo con lo establecido en el art. 757 LECiv, el proceso para la adopción judicial de medidas de apoyo a una persona con discapacidad puede promoverlo la propia persona interesada, su cónyuge no separado de hecho o legalmente o quien se encuentre en una situación de hecho asimilable, su descendiente, ascendiente o hermano. En estos procesos debe intervenir el Ministerio Fiscal.

IV.- POSTULACIÓN.

Se cumplen los requisitos de postulación, dado que se deduce la demanda bajo representación técnica de procurador de los tribunales, y con asistencia letrada de abogado en ejercicio para la defensa, de conformidad con los arts. 23, 31 y 750 LEC.

V.- CUANTÍA.

La cuantía de la demanda resulta inestimable, manifestación que llena el deber consignado en el art. 253.1 LEC.

VI.- FONDO DE LA PRETENSIÓN

Medidas voluntarias de apoyo.

El art. 255 CCiv dispone:

"Cualquier persona mayor de edad o menor emancipada en previsión o apreciación de la concurrencia de circunstancias que puedan dificultarle el ejercicio de su capacidad jurídica en igualdad de condiciones con las demás, podrá prever o acordar en escritura pública medidas de apoyo relativas a su persona o bienes.

Podrá también establecer el régimen de actuación, el alcance de las facultades de la persona o personas que le hayan de prestar apoyo, o la forma de ejercicio del apoyo, el cual se prestará conforme a lo dispuesto en el artículo 249.

Asimismo, podrá prever las medidas u órganos de control que estime oportuno, las salvaguardas necesarias para evitar abusos, conflicto de intereses o influencia indebida y los mecanismos y plazos de revisión de las medidas de apoyo, con el fin de garantizar el respeto de su voluntad, deseos y preferencias.

El Notario autorizante comunicará de oficio y sin dilación el documento público que contenga las medidas de apoyo al Registro Civil para su constancia en el registro individual del otorgante.

Solo en defecto o por insuficiencia de estas medidas de naturaleza voluntaria, y a falta de guarda de hecho que suponga apoyo suficiente, podrá la autoridad judicial adoptar otras supletorias o complementarias"

Alcance de las medidas.

El art. 268 CCiv establece que "las medidas tomadas por la autoridad judicial en el procedimiento de provisión de apoyos serán proporcionadas a las necesidades de la persona que las precise, respetarán siempre la máxima autonomía de esta en el ejercicio de su capacidad jurídica y atenderán en todo caso a su voluntad, deseos y preferencias", en tanto que el art. 269 CCiv establece que "la autoridad judicial constituirá la curatela mediante resolución motivada cuando no exista otra medida de apoyo suficiente para la persona con discapacidad".

Nombramiento de curador.

Citamos los arts. 271 CCiv sobre la delación voluntaria de curador y la autocuratela.

VII - REGISTRO CIVIL

Conforme al art. 4.11º LRC 20/2011, la resoluciones judiciales dictadas en procedimientos de provisión de medidas judiciales de apoyo a personas con discapacidad son inscribibles en el Registro Civil por cuanto se refieren a la identidad, estado civil y demás circunstancias de la persona.

VIII.- COSTAS.

No procede hacer imposición de costas atendida la naturaleza del proceso que se insta, salvo oposición injustificada por parte de tercero con interés legítimo, en cuyo caso deberá aplicarse lo dispuesto en el art. 394 LEC.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL:

que tenga por presentado este escrito con los documentos y copias que se acompañan, admitiéndolo, dándose a las copias el curso legal correspondiente acordando tenerme por comparecido y parte en la representación que ostento en nombre de D. [COMPLETAR], entendiéndose conmigo las sucesivas diligencias teniendo por promovida demanda de adopción de medidas judiciales de apoyo de Dña. [NOMBRE Y APELLIDOS], cuyas circunstancias personales han sido ya referenciadas y tras su sustanciación, con la preceptiva intervención del Ministerio Fiscal, se dicte sentencia por la que se constituya la curatela de Dña. [NOMBRE Y APELLIDOS], con la extensión necesaria conforme a la situación y circunstancias de la persona con discapacidad y a sus necesidades de apoyo, nombrándose curador a mi representado, procediendo a darle posesión del cargo, y librándose, una vez firme la resolución, testimonio de la misma para su inscripción en el Registro Civil de [LOCALIDAD], junto a lo demás que en Derecho proceda.

OTROSI DIGO:

que solicito que se incorporen íntegramente a este proceso las actuaciones seguidas en el procedimiento de jurisdicción voluntaria nº [Nº DE PROCEDIMIENTO], en expediente de adopción de medidas judiciales de apoyo respecto a la misma persona con discapacidad y que finalizó por oposición de tercero interesado.

Por lo que, nuevamente

SUPLICO AL TRIBUNAL que acuerde de conformidad.

Es justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

	Firma de Procurador/a
