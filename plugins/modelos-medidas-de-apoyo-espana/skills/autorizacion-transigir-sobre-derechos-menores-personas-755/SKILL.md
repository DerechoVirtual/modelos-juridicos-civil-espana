---
name: autorizacion-transigir-sobre-derechos-menores-personas-755
description: "Redacta el escrito «Autorización para transigir sobre derechos de menores o personas con apoyos» (formulario 755 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Autorización para transigir sobre derechos de menores o personas con apoyos

> Formulario 0755 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

- [ ] SEDE (4 veces)
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] FECHA (4 veces)
- [ ] NÚMERO (4 veces)
- [ ] IMPORTE (3 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] CALLE
- [ ] Nº
- [ ] LUGAR
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…numeración del juzgado de procedencia).]»; «…/»; «… presta apoyo fue operada en el Hospital»; «…de»; «…87.7º CCiv, otorgada por auto dictado el»; «…numeración del juzgado de procedencia).]»; «…la primera operación, contra el Hospital»; «…de»; «…, y contra la entidad aseguradora»; «…/»; «…de»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (5)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 62.2 LJV
- art. 65.3 LJV
- artículo 62.1 LJV
- art. 64 LJV
- art. 539 LEC
- art. 62.3 LJV
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

### Formulario 0755 · Autorización para transigir sobre derechos de menores o personas con apoyos

- Año del modelo: 2015
- Revisión 17-11-2026: 3 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 37 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito promoviendo el expediente para obtener la autorización judicial para transigir sobre el derecho de una persona con discapacidad con medidas de apoyo para el ejercicio de su capacidad jurídica.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], asistido por el defensor judicial D./Dña. [NOMBRE Y APELLIDOS] según acredito mediante copia fehaciente de la escritura de poderes, que acompaño para su unión a los autos por copia testimoniada con devolución de aquélla, como mejor proceda en derecho comparezco y DIGO: (1)

Que por medio del presente escrito, y de conformidad con los arts. 61 y ss. de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud de autorización judicial para transigir sobre derecho de persona con discapacidad con medidas de apoyo para el ejercicio de su capacidad jurídica, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que mi representado es hijo y curador con funciones de representación de su madre Dña. [NOMBRE Y APELLIDOS], en virtud de sentencia dictada por la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] en fecha [FECHA], en autos de proceso sobre provisión de medidas judiciales de apoyo a las personas con discapacidad nº [NÚMERO], que devino firme al no ser recurrida. En dicha resolución, se nombró curador a mi mandante, y se ordenó la apertura del expediente de jurisdicción voluntaria de curatela que se tramita en el mismo tribunal con nº [NÚMERO] / [COMPLETAR].

2.ª) Que el pasado [FECHA] la persona a la que presta apoyo fue operada en el Hospital [COMPLETAR] de [COMPLETAR] para implantar una prótesis de rodilla, tras decisión del médico de la seguridad social como único remedio a las graves dificultades que padecía para la deambulación y los dolores que sufría. Desgraciadamente la operación no tuvo éxito, pues la zona resultó infectada, produciéndose una agravación del cuadro clínico, lo que hizo necesario hasta tres operaciones más para reconducir el problema. Como consecuencia de todo ello, la persona a la que se presta el apoyo ha sufrido unas graves secuelas de manera permanente con una rigidez de la rodilla que le impide alcanzar la flexión y extensión de la misma, precisando de ayuda constante para caminar.

3.ª) El pasado [FECHA], y previa la correspondiente autorización judicial exigida por el art. 287.7º CCiv, otorgada por auto dictado el [COMPLETAR] por la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR]; entablé demanda en su nombre para reclamar los daños y perjuicios ocasionados. La demanda dirigida contra el Doctor/a D./Dña. [NOMBRE Y APELLIDOS] que llevó a cabo la primera operación, contra el Hospital [COMPLETAR] de [COMPLETAR], y contra la entidad aseguradora [COMPLETAR] SA, reclamaba el pago de [IMPORTE] euros, intereses legales y costas, y fue repartida a la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO], el cual lo tramita como procedimiento ordinario nº [Nº DE PROCEDIMIENTO] / [COMPLETAR].

4.ª) En el marco de dicho proceso, y tras intensas negociaciones con las representaciones legales de los codemandados, se nos ha ofrecido finalmente un acuerdo para fijar la indemnización en [IMPORTE] euros más intereses legales, sin imposición de costas. Dicha cantidad resulta aceptable habida cuenta de la posibilidad de que la decisión judicial finalmente firme pueda no ser favorable, y del probable retraso, en caso de estimación, de una sentencia judicial firme que dilate el momento del cobro de la correspondiente indemnización, y dispare los gastos procesales. Por ello, se considera que el acuerdo finalmente ofrecido es conveniente para los intereses de la persona a la que se presta apoyo, y mi mandante se muestra dispuesto a aceptarlo y firmarlo.

5.ª) Por todo ello, exigiendo el art. 287.4º CCiv autorización judicial para la transacción proyectada, se insta el presente expediente contemplado en los arts. 61 y ss. LJV. Mi cliente se encuentra legitimado según art. 62.2 LJV, como representante legal de su madre que es, e identifica en este escrito el derecho a transaccionar, con exposición de todos los detalles del mismo, y su utilidad y conveniencia al respecto, con los argumentos expuestos. Asimismo, de conformidad con el art. 65.3 LJV, se solicita la expedición de testimonio del auto que ponga fin al presente expediente para hacer uso del mismo en el procedimiento ordinario referido.

6.ª) Que es competente la Sección Civil del Tribunal de Instancia al que me dirijo conforme al artículo 62.1 LJV, al encontrarse en su partido judicial el domicilio donde se encuentra la madre de mi mandante, sito en la calle [CALLE] de [COMPLETAR].

7.ª) Se acompañan a este escrito testimonio de la sentencia que acordó la adopción de medidas de apoyo y la designación de curador, informes médicos de las distintas operaciones, copia de la demanda de juicio ordinario con la pericial médica aportada, testimonio de auto autorizando la interposición de la misma, y oferta transaccional presentada por escrito por los codemandados antes relacionados.

Por todo lo expuesto, al amparo del art. 287.4º CCiv, y de los arts. 61 y ss. LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria, previa la convocatoria de comparecencia prevista en el art. 64 LJV, con citación del Ministerio Fiscal, de la persona a la que se presta apoyo si se considera necesaria, y de quien se estime pertinente; se dicte auto autorizando judicialmente la transacción consistente en fijar en [IMPORTE] euros más intereses legales, y sin costas, la indemnización a percibir por Dña. [NOMBRE Y APELLIDOS], reclamada en el Procedimiento Ordinario nº [Nº], tramitado ante la Sección Civil del Tribunal de Instancia nº [NÚMERO] / [COMPLETAR]. Y, asimismo, que se expida testimonio de dicha resolución judicial para usarlo en el procedimiento ordinario indicado.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para presentar demanda de ejecución variará, según el art 3.2 LJV, y el art. 539 LEC, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 62.3 LJV, exige dichos requisitos de postulación cuando el acto cuya autorización se insta supera los 6.000 euros. Extremo que concurre en el importe de la transacción que se expone como ejemplo.

========================================================================
