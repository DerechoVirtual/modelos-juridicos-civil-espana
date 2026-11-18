---
name: sustitucion-tutor-demanda-393
description: "Redacta el escrito «Sustitución de tutor: demanda» (formulario 393 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Sustitución de tutor: demanda

> Formulario 0393 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (13 veces)
- [ ] Nº DE COLEGIADO
- [ ] COLEGIO
- [ ] FECHA
- [ ] NÚMERO
- [ ] Nº
- [ ] DESCRIBIR
- [ ] LOCALIDAD (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…rado de la Administración de Justicia de»; «…revenido en el art. 279 del Código Civil»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 279 del Código Civil
- art. 50 de la LJV
- art. 213 del Código Civil
- art. 14.2 LJV
- art. 43.2 de la LJV
- art. 45 y 50 de la LJV
- art. 279 del CC
- art. 223 del CC
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

### Formulario 0393 · Sustitución de tutor: demanda

- Año del modelo: 2019
- Revisión 17-11-2026: 15 campos de relleno marcados en blanco; 9 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE COLEGIADO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

D./Dª [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales en nombre y representación de D./Dª [NOMBRE Y APELLIDOS], y de D./Dª [NOMBRE Y APELLIDOS], tal y como acredito por apoderamiento apud-acta otorgado ante el Letrado de la Administración de Justicia de [COMPLETAR], bajo la dirección letrada del Letrado/a D./Dª [NOMBRE Y APELLIDOS], colegiado núm. [Nº DE COLEGIADO] del Ilustre Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco y como mejor proceda en Derecho, DIGO:

Que mediante en la representación que ostento promuevo EXPEDIENTE DE JURISDICCIÓN VOLUNTARIA para la aceptación de la EXCUSA del ejercicio del cargo tutelar por mi mandante respecto del tutelado D/Dª. [NOMBRE Y APELLIDOS], habiendo sido designado por resolución de fecha [FECHA], dictada en el proceso número [NÚMERO], seguido ante el Tribunal al que me dirijo, Y NOMBRAMIENTO de nuevo tutor, proponiéndose para el cargo a D/Dª. [NOMBRE Y APELLIDOS], de acuerdo con lo establecido en el artículo 223, 279 y concordantes del Código Civil y art. 44 y siguientes de la Ley 15/2015, de 2 de julio, de Jurisdicción Voluntaria (LJV), en base a los siguientes

HECHOS

PRIMERO- El tutor designado D./Dª [NOMBRE Y APELLIDOS] ha cumplido recientemente [Nº] años de edad y está aquejado de una enfermedad consistente en [DESCRIBIR] lo cual le impide ejercer el cargo debidamente, tal como se acredita por los documentos que se acompañan como número

El tutor ha venido cumpliendo sus obligaciones durante todo este tiempo, pero, de forma sobrevenida, por razones de edad y enfermedad, le resulta excesivamente gravoso el ejercicio del cargo, por lo que formula su renuncia al concurrir causa establecida en el art. 279 del Código Civil y al amparo de lo dispuesto en el art. 50 de la LJV, al alegarse un motivo sobrevenido.

SEGUNDO.- Asimismo, y de conformidad con lo prevenido en el art. 279 del Código Civil [COMPLETAR], se interesa que se nombre a D/Dª. [NOMBRE Y APELLIDOS] como nuevo tutor/a, conforme a la prelación del art. 213 del Código Civil, quien reúne los requisitos para el ejercicio del cargo y al ser persona de parecidas condiciones al actual tutor, puesto que es asimismo abuelo/a del tutelado, si bien por la línea paterna, con menos edad y buen estado de salud, a lo que hay que añadir que los tres hermanos del tutelado conviven con el ascendiente ahora propuesto como nuevo tutor, que está cuidando de hecho al tutelado como consecuencia de los impedimentos que padece el tutor inicialmente designado y que las relaciones personales son excelentes entre todos ellos.

TERCERO- A los efectos del art. 14.2 LJV, debo hacer constar que, al margen del tutelado y de mis representados, los parientes más próximos del tutelado, que pueden estar interesados en el expediente, son los siguientes:

D. [NOMBRE Y APELLIDOS], hermano, con domicilio en [LOCALIDAD]

()

FUNDAMENTOS DE DERECHO

PRIMERO.- Competencia. El art. 43.2 de la LJV establece que el órgano judicial que haya conocido de un expediente sobre tutela, curatela o guarda de hecho, será competente para conocer de todas las incidencias, trámites y adopción de medidas o revisiones posteriores, siempre que el menor o persona con discapacidad resida en la misma circunscripción, como es el caso.

SEGUNDO.- PROCEDIMIENTO El procedimiento a seguir en el presente supuesto es el de jurisdicción voluntaria, regulado en el art. 45 y 50 de la LJV.

TERCERO.- LEGITIMACIÓN. Está legitimado activamente el solicitante en su condición de tutor, debiendo ser emplazado asimismo la persona propuesta para la tutela en el caso de aceptarse la excusa.

CUARTO.- FUNDAMENTOS DE FONDO.

El art. 279 del CC, de aplicación a la tutela según lo dispuesto en el art. 223 del CC, establece que será excusable el desempeño de la curatela si resulta excesivamente gravoso o entraña grave dificultad para la persona nombrada para el ejercicio del cargo. También podrá excusarse el curador de continuar ejerciendo la curatela cuando durante su desempeño le sobrevengan los motivos de excusa. Las personas jurídicas privadas podrán excusarse cuando carezcan de medios. Una vez admitida la excusa, se procederá al nombramiento de nuevo tutor.

La aplicación de ambos preceptos, de acuerdo al principio del interés superior del menor, determina la procedencia de las pretensiones sostenidas en esta solicitud.

Por lo expuesto,

AL TRIBUNAL SUPLICO: Que tenga por presentado este escrito con los documentos que se acompañan, lo admita, y tenga por promovido expediente de jurisdicción voluntaria de sustitución de tutor, y practicadas las diligencias oportunas, incluida la información testifical que se interesa en el otrosí y con intervención del Ministerio Fiscal, y previos los demás trámites con arreglo a Derecho dicte resolución en la que se acuerde aceptar la renuncia en el cargo de tutor D/Dª. [NOMBRE Y APELLIDOS], con las consecuencias inherentes, y que se nombre como nuevo tutor del tutelado D/Dª [NOMBRE Y APELLIDOS]. a D/Dª. [NOMBRE Y APELLIDOS], y acordando remitir la correspondiente comunicación al Registro Civil de

OTROSÍ PRIMERO DIGO que a fin de acreditar la certeza de los hechos relatados, solicito que en la comparecencia sean oído mis representados y el tutelado, por tener suficiente madurez, así como a los parientes designados, y la persona propuesta para ser nombrada tutor, y ofrezco los siguientes testigos para acreditar la certeza de los hechos expresados:

- D. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD]

SUPLICO AL TRIBUNAL: Tenga por propuestos a los testigos y personas indicadas, admitiendo la testifical ofrecida, comprometiéndose esta parte a que comparezcan en el día y hora que se señale (o, en su caso, solicitando que sean citados judicialmente para la práctica de la diligencia).

Es Justicia que insto en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de procurador y letrado
