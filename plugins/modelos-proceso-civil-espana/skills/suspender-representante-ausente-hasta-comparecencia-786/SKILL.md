---
name: suspender-representante-ausente-hasta-comparecencia-786
description: "Redacta el escrito «Suspender al representante del ausente hasta la comparecencia» (formulario 786 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Suspender al representante del ausente hasta la comparecencia

> Formulario 0786 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] LOCALIDAD
- [ ] CALLE (2 veces)
- [ ] NÚMERO
- [ ] FECHA (3 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] Nº
- [ ] LUGAR
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…D.»; «…el expediente de jurisdicción voluntaria»; «…/»; «…/ [COMPLETAR], el»; «…se dictó, a instancia de mi hermano D.»; «…implemente me trasladé a la localidad de»; «…r de Alemania a trabajar en el sector de»; «…de»; «…, y de su hijo D.»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 75 de la Ley 15/2015
- art. 75 LJV
- art. 187 del Código Civil
- art. 68.1 LJV
- art. 3.2 LJV
- art. 68.4 LJV

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

### Formulario 0786 · Suspender al representante del ausente hasta la comparecencia

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 22 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito por el que se promueve el expediente en solicitud de que se deje sin efecto la declaración de ausencia de una persona y se suspenda la actuación del representante nombrado.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D. [COMPLETAR], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

Que por medio del presente escrito, y de conformidad con el art. 75 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud de que se deje sin efecto la declaración de ausencia de mi persona y se suspenda la actuación del representante nombrado, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que por el Tribunal al que tengo el honor de dirigirme, en el marco del expediente de jurisdicción voluntaria [COMPLETAR] / [COMPLETAR], el [COMPLETAR] se dictó, a instancia de mi hermano D. [COMPLETAR], decreto por el Letrado de la Administración de Justicia declarando mi ausencia legal con fecha [FECHA], de conformidad con lo dispuesto en el art. 183.1º del Código Civil, a partir de lo que se entendía una desaparición de mi domicilio sin encomienda de administración de bienes a apoderado alguno. En la propia resolución se nombró representante a al propio instante, todo lo cual devino firme, al no ser recurrido el citado decreto.

2.ª) Que mi hermano obró de manera imprudente al instar tal declaración, puesto que el hecho de que no mantuviéramos relaciones desde hace varios años, la falta de noticias mías no implicaba que yo desapareciera sin más. Simplemente me trasladé a la localidad de [COMPLETAR] en el sur de Alemania a trabajar en el sector de [COMPLETAR], con un contrato laboral de dos años; y no comuniqué tal extremo al único hermano que tengo.

3.ª) Una vez regresado a España, y tras conocer mi declaración legal de ausencia, acudo al expediente previsto en el art. 75 LJV, para revocar la misma, aportando documentación relativa a mi identidad, y ofreciéndome para cualquier prueba que se considere necesaria al respecto. En aplicación del art. 187 del Código Civil tengo derecho a recuperar mi patrimonio, y habiendo obrado mi hermano de manera imprudente, rayana en la mala fe, los frutos percibidos y los debidos percibir. Asimismo, y puesto que hasta la revocación aquí pretendida mi hermano D. sigue siendo representante de mis bienes en España a todos los efectos legales sin justificación para ello; solicito, en virtud de la posibilidad habilitada por el apartado tercero del mencionado precepto legal, que de manera inmediata, y tras examen de la documentación aportada, se decrete por el Letrado de la Administración de Justicia la suspensión de su actuación hasta la celebración de la comparecencia prevista en el apartado primero.

4.ª) Que es competente la Sección Civil del Tribunal de Instancia al que me dirijo conforme al art. 68.1 LJV, en relación con lo dispuesto en el art. 85.1º LOPJ, al encontrarse en su partido judicial mi último domicilio sito en la calle [CALLE] de [COMPLETAR]; y ser el órgano judicial que declaró la situación de ausencia legal que ahora se pretende impugnar.

5.ª) Se acompañan a este escrito testimonio de la declaración de ausencia, copia de mi contrato de trabajo en Alemania y su correspondiente traducción, copia de mi permiso de residencia en aquel país y su correspondiente traducción, copia del pasaporte, de mi DNI, y certificado literal de nacimiento. Se ofrece información testifical de mi actual pareja Dña. [NOMBRE Y APELLIDOS], y de su hijo D. [COMPLETAR], de [Nº] años de edad, con el mismo domicilio que el mío.

Por todo lo expuesto, al amparo del art. 187 del Código Civil, y del art. 75 LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria:

1.- Se proceda de manera inmediata por el Letrado de la Administración de Justicia a identificarme por la documentación aportada y se suspenda la actuación de mi hermano D. [NOMBRE Y APELLIDOS] como representante legal de mi persona a todos los efectos legales.
2.- Asimismo, y previa convocatoria de comparecencia, con citación del Ministerio Fiscal, mi persona, testigos propuestos y a quien se considere interesado; se dicte decreto revocando la declaración de ausencia realizada por decreto de fecha [FECHA], a todos los efectos legales.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma del solicitante

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 68.4 LJV, no exige requisito alguno de postulación.

========================================================================
