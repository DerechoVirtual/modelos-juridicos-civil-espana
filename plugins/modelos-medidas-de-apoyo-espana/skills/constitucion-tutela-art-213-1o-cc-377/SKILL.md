---
name: constitucion-tutela-art-213-1o-cc-377
description: "Redacta el escrito «Constitución de tutela (art. 213.1º CC)» (formulario 377 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Constitución de tutela (art. 213.1º CC)

> Formulario 0377 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (12 veces)
- [ ] NÚMERO (6 veces)
- [ ] COLEGIO
- [ ] CALLE (3 veces)
- [ ] Nº
- [ ] FECHA (2 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] LUGAR
- [ ] Otros 18 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «…tela y nombramiento de tutor de la menor»; «…de»; «…de [COMPLETAR] de»; «…de [COMPLETAR] de [COMPLETAR] en»; «…n se acredita con los documentos números»; «…a»; «…, n.º [NÚMERO] de»; «…, n.º [NÚMERO] de»; «… 6.ª) Que antes de su fallecimiento, Don»; «…y Doña»; «…rgado testamento ante el/la Notario/a de»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 45.1 LJV
- art. 211 CCiv
- art. 43.1 LJV
- art. 206 CCiv
- art. 199 CCiv
- arts. 4 y 45.2 LJV
- art. 3 y 43.3 LJV
- arts. 46.5 LJV

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

### Formulario 0377 · Constitución de tutela (art. 213.1º CC)

- Año del modelo: 2019
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 45 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito promoviendo expediente de jurisdicción voluntaria para la constitución de la tutela y nombramiento de tutor de un menor designada en testamento.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS] Procurador de los Tribunales, y de Dña. [NOMBRE Y APELLIDOS], según acredito mediante escritura pública de poderes que solicito, una vez incorporada por copia en autos, me sea devuelta por precisarla para otros usos, a quien asiste el Letrado en ejercicio D./Dña. [NOMBRE Y APELLIDOS], colegiado n.º [NÚMERO] del Iltre. Colegio de Abogados de [COLEGIO], con despacho abierto en esta localidad, calle [CALLE] de [COMPLETAR], ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que por medio del presente escrito promuevo EXPEDIENTE DE JURISDICCIÓN VOLUNTARIA para la constitución de tutela y nombramiento de tutor de la menor [COMPLETAR], en base a los siguientes hechos y consideraciones jurídicas:

1.ª) Que mi representada es abuela materna de la menor .Se acompaña libro de familia como documento n.º [NÚMERO].

2.ª) Que la menor tiene en la actualidad [Nº] años de edad tal como se acredita con el correspondiente certificado de nacimiento que se acompaña como documento n.º [NÚMERO].

3.ª) Que la citada menor quedó huérfana por el fallecimiento de sus padres en accidente de circulación ocurrido el día [FECHA] de [COMPLETAR] de [COMPLETAR] en [COMPLETAR], según se acredita con los documentos números [COMPLETAR] a [COMPLETAR] adjuntos, al efecto copia del atestado policial del expresado accidente y certificados de defunción de ambos.

4.ª) Que desde que fallecieron sus padres hasta el momento actual la menor ha convivido con mi representada en el domicilio de ésta sito en [LOCALIDAD]. Se acompaña certificado de convivencia expedido por la Policía Municipal como documento n.º [NÚMERO].

5.ª) Que el resto de familiares de la menor de los que se tiene conocimiento son, por parte de padre D./Dña. [NOMBRE Y APELLIDOS]; y por parte de madre D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS].

Al efecto señalo el domicilio de D./Dña. [NOMBRE Y APELLIDOS], residente en la calle [CALLE], n.º [NÚMERO] de [COMPLETAR], y el de D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS], residentes en la calle [CALLE], n.º [NÚMERO] de [COMPLETAR], como otros parientes más próximos, conforme al art. 45.1 LJV.

6.ª) Que antes de su fallecimiento, Don [COMPLETAR] y Doña [COMPLETAR] habían otorgado testamento ante el/la Notario/a de [COMPLETAR], D./Dña. [NOMBRE Y APELLIDOS], en el que designaban tutora de su hija menor de edad a Dña. [NOMBRE Y APELLIDOS], en el supuesto de que ambos fallecieran antes de que su hija cumpliera la mayoría de edad, como acreditamos con la certificación del Registro General de Actos de Última Voluntad y copia testimoniada del testamento, que se aportan como documentos números [COMPLETAR].

7.ª) Que mi mandante se ha ocupado de la educación y manutención de la menor [COMPLETAR] desde el fallecimiento de sus padres.

8.ª) Que mi mandante se postula como tutora de su nieta [COMPLETAR] teniendo encaje en el art. 213.1º CCiv al ser la persona designada por los padres de la menor en sus disposiciones de última voluntad que está en condiciones de hacerse cargo de las indicadas funciones, que de hecho ya verifica desde el fallecimiento de los padres de la menor y, que además constituye la familia directa más próxima.

9.ª) Que habiendo disposición testamentaria, el cargo de tutor debe corresponder a mi mandante, que cuenta con ingresos económicos suficientes para el mantenimiento del menor, está en el pleno ejercicio de sus derechos civiles y no está incurso en ninguna causa de inhabilidad, cumpliendo los requisitos del art. 211 CCiv.

10.ª) Que la presente solicitud debe ser tramitada por las normas establecidas en los arts. 17 a 20 y 44 y ss. LJV.

11.ª) Que es competente el Tribunal de Instancia al que me dirijo a tenor de lo previsto en el art. 43.1 LJV en relación con lo dispuesto en el art. 85.1º LOPJ, por ser el del lugar del domicilio de la menor.

12.ª) Que mi representada está legitimada activamente para el ejercicio de la solicitud efectuada en petición de constitución de tutela de su nieta [COMPLETAR] por cuanto es el familiar llamado a ella al que se refiere el art. 206 CCiv. La legitimación pasiva corresponde a la menor [COMPLETAR], conforme a lo dispuesto en el art. 199 CCiv que previene que estarán sujetos a tutela los menores no emancipados que no estén bajo la patria potestad, circunstancia que concurre en este caso, de la que consta disposición testamentaria sobre la constitución de la tutela.

13.ª) Que los arts. 4 y 45.2 LJV establecen que el Ministerio Fiscal intervendrá en los expedientes de jurisdicción voluntaria cuando afecten al estado civil o condición de la persona o esté comprometido el interés de un menor o una persona con discapacidad con medidas de apoyo para el ejercicio de su capacidad jurídica, actuando en interés de éste.

14.ª) Que conforme a lo dispuesto en el art. 3 y 43.3 LJV la solicitud está firmada por abogado y procurador, pese a que su intervención no es preceptiva en el caso de autos.

15.ª) Que conforme a lo dispuesto en los arts. 46.5 LJV y 283 y ss. RRC, debe procederse a la inscripción de la tutela de la menor y del nombramiento de tutora.

Por todo lo expuesto, al amparo de los arts. 199 y ss. CCiv, particularmente el art. 213 sobre la delación de la tutela y el nombramiento del tutor, y de los arts. 44 y ss. LJV,

SUPLICO AL TRIBUNAL:

Que habiendo presentado este escrito, con sus copias, se sirva admitirlo, me tenga por comparecido y parte en la representación que ostento de Dña. [NOMBRE Y APELLIDOS] y se entiendan conmigo las sucesivas diligencias en la forma prevenida en la ley y, admitiendo a trámite la presente petición de jurisdicción voluntaria en solicitud de constitución de tutela en relación a la menor [COMPLETAR] y, dicte el/la Letrado de la Administración de Justicia decreto por el que admitiendo a trámite la solicitud, con intervención del Ministerio Fiscal, se proceda a la citación a comparecencia de la interesada (si fuere mayor de 12 años o, al menor de dicha edad que tuviera suficiente madurez) para que pueda personarse en autos y llevar a cabo las alegaciones que estime de interés al respecto junto al promotor, a los parientes más próximos antes identificados y al Ministerio Fiscal (y a cuantas personas se considere oportuno) y, previo los trámites legales dicte el Tribunal auto acordando la constitución de la tutela de [LOCALIDAD], y el nombramiento de mi mandante como tutora de la misma, dando cumplimiento así a las disposiciones testamentarias de los padres fallecidos de la citada menor. Y una vez firme dicha resolución, sin constitución de fianza legal, se le de posesión en el cargo, aprobándose las medidas de vigilancia y control que se consideren pertinentes, junto a lo demás que en Derecho proceda, incluida la inscripción registral de la tutela de la menor y del nombramiento de tutora.

Por ser de justicia que solicito en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a
