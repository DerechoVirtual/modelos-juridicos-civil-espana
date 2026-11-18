---
name: autorizacion-judicial-titular-patria-potestad-menor-no-799
description: "Redacta el escrito «Autorización judicial para el titular de la patria potestad menor no emancipado» (formulario 799 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Autorización judicial para el titular de la patria potestad menor no emancipado

> Formulario 0799 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

- [ ] SEDE (2 veces)
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] Nº DE DOCUMENTO
- [ ] Nº
- [ ] CALLE (3 veces)
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Otros 16 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…años, y está bajo la tutela de D.»; «…, residente en la calle [CALLE] de»; «…, constituida mediante auto dictado el»; «…numeración del juzgado de procedencia).]»; «…el expediente de jurisdicción voluntaria»; «…/»; «…eron en accidente de tráfico acaecido el»; «…de»; «… [COMPLETAR], nació el pasado [FECHA] D.»; «…con una grave enfermedad, el Síndrome de»; «… venido siendo tratado en el Hospital de»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (4)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 157 del Código Civil
- art. 86 LJV
- art. 86.3 LJV
- art. 86.2 LJV
- art. 85.1 LJV
- art. 3.2 LJV
- art. 539 LEC
- art. 85.3 LJV
- Ley 15/2015

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

### Formulario 0799 · Autorización judicial para el titular de la patria potestad menor no emancipado

- Año del modelo: 2015
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 29 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito por el que se promueve el expediente en solicitud de autorización judicial para prestar consentimiento sobre la operación de un menor de edad sometido a patria potestad con progenitor menor no emancipado, concurriendo imposibilidad en su tutor de otorgarla.

Adaptado a la LO 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], como mejor proceda en derecho comparezco y DIGO: (1)

Que por medio del presente escrito, y de conformidad el art. 86 la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud de autorización judicial para prestar consentimiento sobre operación de menor de edad sometido a patria potestad con progenitor menor no emancipado, concurriendo imposibilidad en su tutor, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que mi mandante actualmente cuenta con [Nº] años, y está bajo la tutela de D. [COMPLETAR], residente en la calle [CALLE] de [COMPLETAR], constituida mediante auto dictado el [COMPLETAR], por el Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], en el expediente de jurisdicción voluntaria [COMPLETAR] / [COMPLETAR]. Sus padres, Dña. y D. fallecieron en accidente de tráfico acaecido el [COMPLETAR], y no se encuentra emancipado legalmente, ni se ha solicitado, ni está en tramitación, nada al respecto.

2.ª) Que fruto de la relación sentimental mantenida con Dña. [NOMBRE Y APELLIDOS], de 18 años de edad y con domicilio en la calle [CALLE] de [COMPLETAR], nació el pasado [FECHA] D. [COMPLETAR], quien cuenta con un año de edad. Dicho menor nació con una grave enfermedad, el Síndrome de [COMPLETAR], de carácter degenerativo que dificulta su desarrollo, y pone en grave peligro su vida. Ha venido siendo tratado en el Hospital de [COMPLETAR], donde el cirujano Doctor/a [COMPLETAR], ha recomendado una operación de [COMPLETAR], con objeto de poner freno o corregir la degeneración consecuencia de la grave enfermedad.

3.ª) Que el centro médico citado exige el consentimiento de ambos progenitores del menor, habida cuenta de los riesgos que la operación en sí entraña. Tras una exhaustiva información médica al respecto, la madre del menor lo ha prestado, y es voluntad de mi mandante prestarlo pues manifiesta su total consentimiento al respecto. Si bien, siendo como es, también, menor de edad sometido a tutela, se precisa la asistencia de su tutor o representante legal de conformidad con lo dispuesto en el art. 157 del Código Civil, al no encuadrarse aquel en las excepciones previstas en el art. 267 del mismo texto legal.

4.ª) Que actualmente, el tutor de mi cliente se encuentra trabajando en el extranjero, en la República Dominicana, y a pesar de los múltiples esfuerzos del tutelado no ha podido localizarle para que sea asistido en la prestación del mencionado consentimiento. Por ello, se acude al presente expediente previsto en el art. 86 LJV, el cual establece el cauce procesal para solucionar los supuestos de imposibilidad en esa asistencia previstos en el citado art. 157 del Código Civil. Mi mandante se encuentra legitimado para ello, según el citado art. 86.3 LJV, como progenitor que es, siendo imposible la asistencia del tutor en la presentación de este escrito, por el mismo motivo por el cual se recurre con la presente solicitud al auxilio judicial.

5.ª) Que es competente el Tribunal de Instancia al que me dirijo conforme al art. 86.2 LJV en relación con lo dispuesto en el art. 85.1º LOPJ, al encontrarse en su partido judicial el domicilio del menor de cuya operación se trata, sito en la calle [CALLE] de [COMPLETAR].

6.ª) Se acompañan a este escrito testimonio del auto que constituyó la tutela, de la diligencia que declaró su firmeza, el libro de familia de mi mandante, el certificado de nacimiento de su hijo, certificado médico sobre su enfermedad y la necesidad de la operación, copia del impreso que precisa el consentimiento paterno, y comunicaciones enviadas al tutor que no han tenido respuesta hasta la fecha.

Por todo lo expuesto, al amparo del art. 157 del Código Civil, y de los arts. 85 y ss. LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria, previa la convocatoria de comparecencia prevista en el art. 85.1 LJV, con citación del Ministerio Fiscal, de la madre del menor Dña. [NOMBRE Y APELLIDOS], del Doctor/a [COMPLETAR] y de quien se estime pertinente; se dicte auto autorizando judicialmente a mi mandante para prestar consentimiento sobre operación de su hijo menor de edad al concurrir imposibilidad para la asistencia del tutor del primero.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para presentar demanda de ejecución variará, según el art. 3.2 LJV, y el art. 539 LEC, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 85.3 LJV, no exige esos requisitos para la tramitación del expediente; sin perjuicio de que sea habitual la asistencia de dichos profesionales habida cuenta de la presumible falta de preparación del solicitante, menor de edad.

========================================================================
