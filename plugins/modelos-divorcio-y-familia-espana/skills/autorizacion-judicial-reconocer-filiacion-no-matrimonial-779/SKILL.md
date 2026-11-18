---
name: autorizacion-judicial-reconocer-filiacion-no-matrimonial-779
description: "Redacta el escrito «Autorización judicial para reconocer una filiación no matrimonial» (formulario 779 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Autorización judicial para reconocer una filiación no matrimonial

> Formulario 0779 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (3 veces)
- [ ] NOMBRE Y APELLIDOS (9 veces)
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] CALLE (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…DEL TRIBUNAL DE INSTANCIA»; «…da legal de hecho por la entidad pública»; «…, el representante de la entidad pública»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL
- madre / padre
- esta última mi hermana / siendo este último mi hermano
- la madre / el padre

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 125 del Código Civil
- art. 24.1 de la Ley 15/2015
- art. 3.2 LJV

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

### Formulario 0779 · Autorización judicial para reconocer una filiación no matrimonial

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 3 desplegables convertidos en elección en blanco; 23 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Solicitud de iniciación del expediente de jurisdicción voluntaria para obtener la autorización judicial para el otorgamiento del reconocimiento de la filiación no matrimonial de un menor de edad.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA [COMPLETAR] DE [LOCALIDAD]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

Que por medio del presente escrito promuevo expediente de jurisdicción voluntaria para obtener la autorización judicial para el otorgamiento del reconocimiento de la filiación no matrimonial del menor de edad D./Dña. [NOMBRE Y APELLIDOS], hijo/a de D./Dña. [NOMBRE Y APELLIDOS]., en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que el/la menor D./Dña. [NOMBRE Y APELLIDOS], hijo/a de D./Dña. [NOMBRE Y APELLIDOS], nació en fecha [FECHA], inscribiéndose como tal en el Registro Civil, a partir del certificado del Ginecólogo que asistió al parto, y la declaración de su madre. El menor cuenta actualmente con dos años de edad. No se hizo constar legalmente la paternidad del mismo.

2.ª) Que dicho menor nació de fruto de la relación sentimental que mantuve con su [ELEGIR: madre / padre], siendo [ELEGIR: esta última mi hermana / siendo este último mi hermano] de doble vínculo, hijos ambos de D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS].

3.ª) Que acudo al presente expediente para obtener autorización judicial para el reconocimiento de la filiación no matrimonial, tal y como prevé el art. 125 del Código Civil, la cual resulta concedida siempre que convenga al menor en cuestión.

4.ª) El reconocimiento pretendido conviene, sin ningún género de dudas, al propio menor, toda vez que el mismo se encuentra en situación de guarda legal de hecho por la entidad pública [COMPLETAR], a causa de las dificultades de su madre para hacerse cargo de su custodia, y de los problemas psicológicos sufridos por la misma de manera permanente. El hecho de carecer de padre conocido, independientemente de que los progenitores seamos hermanos, no favorece al menor. Por el contrario, el reconocimiento de mi paternidad le beneficiará, dado que dispongo de una situación personal y patrimonial que me permite hacerme cargo del menor, y proveer todas las necesidades que un niño de su edad precisa.

5.ª) Que es competente el Tribunal de Instancia al que me dirijo conforme al art. 24.1 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV) en relación con lo dispuesto en el art. 85.1º LOPJ, al encontrarse en su partido judicial el domicilio del menor, el hogar infantil sito en [LOCALIDAD], calle [CALLE], nº [NÚMERO].

6.ª) Se acompañan a este escrito copia de la inscripción de nacimiento del menor; fotocopias de los documentos nacionales de identidad de ambos progenitores donde se aprecia nuestra condición de hermanos; resolución administrativa constituyendo la guarda legal del menor; y copia de mis declaraciones de patrimonio y de IRPF del pasado ejercicio.

Por todo lo expuesto, al amparo del art. 122 y ss. del Código Civil y los arts. 23 y ss. LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria, previa la convocatoria de comparecencia a la que serán citados [ELEGIR: la madre / el padre] D./Dña. [NOMBRE Y APELLIDOS], el representante de la entidad pública [COMPLETAR], el Ministerio Fiscal, y yo como solicitante; se dicte auto concediendo autorización judicial para el otorgamiento del reconocimiento de la filiación no matrimonial del menor D./Dña. [NOMBRE Y APELLIDOS].

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma del solicitante

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito, el art. 24.LJV no exige dichos requisitos para la tramitación de la solicitud que nos ocupa.

========================================================================
