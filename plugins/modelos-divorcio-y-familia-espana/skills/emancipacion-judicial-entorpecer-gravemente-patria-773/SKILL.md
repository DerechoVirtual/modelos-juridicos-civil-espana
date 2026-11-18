---
name: emancipacion-judicial-entorpecer-gravemente-patria-773
description: "Redacta el escrito «Emancipación judicial por entorpecer gravemente la patria potestad» (formulario 773 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Emancipación judicial por entorpecer gravemente la patria potestad

> Formulario 0773 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] Nº DE DOCUMENTO
- [ ] Nº
- [ ] FECHA (2 veces)
- [ ] LOCALIDAD
- [ ] Nº DE EXPEDIENTE
- [ ] IMPORTE
- [ ] CALLE
- [ ] LUGAR
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ientemente en el Centro Penitenciario de»; «… impuesta por sentencia firme dictada el»; «…/»; «…numeración del juzgado de procedencia).]»; «…de»; «…ón del Ministerio Fiscal, de su padre D.»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 53.1.c) de la Ley 15/2015
- art. 53.1.c) LJV
- art. 54.1 LJV
- art. 53.1 LJV
- art. 55 LJV
- art. 3.2 LJV
- art. 539 LEC
- art. 53.3 de la LJV

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

### Formulario 0773 · Emancipación judicial por entorpecer gravemente la patria potestad

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 22 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito promoviendo el expediente de jurisdicción voluntaria para la emancipación del menor por concesión judicial, tras haber fallecido su madre e ingresado su padre en un centro penitenciario.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], asistido por el defensor judicial D./Dña. [NOMBRE Y APELLIDOS] según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], como mejor proceda en derecho comparezco y DIGO: (1)

Que por medio del presente escrito, y de conformidad con el art. 53.1.c) de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente de jurisdicción voluntaria en solicitud de emancipación por concesión judicial de mi representado, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que mi cliente de [Nº] años de edad es hijo/a de D. y Dña. [NOMBRE Y APELLIDOS], habiendo fallecido esta última hace tres años, en fecha [FECHA], tras una larga enfermedad. Se encuentra, de esta forma, bajo la patria potestad de su padre.

2.ª) Que dicho padre ha ingresado recientemente en el Centro Penitenciario de [COMPLETAR] para cumplir una pena de prisión de cinco años, impuesta por sentencia firme dictada el [COMPLETAR] por la Audiencia Provincial de [LOCALIDAD]. En consecuencia, concurre una de las causas legales previstas en el art. 244.3º CCiv y del art. 53.1.c) LJV, al entorpecer gravemente el ingreso en prisión referido el ejercicio de la patria potestad respecto al menor. En expediente de jurisdicción voluntaria nº [Nº DE EXPEDIENTE] / [COMPLETAR] tramitado ante el Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], se nombró defensor judicial del menor a D./Dña. [NOMBRE Y APELLIDOS], quien le asiste en este acto, cumpliendo el requisito de legitimación previsto en el art. 54.1 LJV.

3.ª) Actualmente, mi mandante compatibiliza sus estudios con un trabajo en un establecimiento de comida rápida, con contrato fijo, por el que percibe la cantidad mensual de [IMPORTE] euros. Por ello, estando a menos de un año de cumplir la mayoría de edad, disponiendo de ingresos que le permiten atender sus gastos ordinarios, y llevar, en definitiva, una vida independiente, y concurriendo la citada causa de emancipación, solicito la concesión judicial al efecto.

4.ª) Que es competente el Tribunal de Instancia al que me dirijo conforme al art. 53.1 LJV en relación con lo dispuesto en el art. 85.1º LOPJ, al encontrarse en su partido judicial el domicilio donde reside mi mandante, sito en la calle [CALLE] de [COMPLETAR].

5.ª) Se acompañan a este escrito certificado de nacimiento de mi cliente, certificado de defunción de su madre, copia del libro de familia, copia de la sentencia condenatoria de su padre, testimonio del decreto del Letrado de la Administración de Justicia nombrando al defensor judicial, y contrato de trabajo en el establecimiento de comida rápida.

Por todo lo expuesto, al amparo de los arts. 239 y ss. CCiv, y de los arts. 53 y ss. LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria, previa la convocatoria de comparecencia prevista en el art. 55 LJV, con citación del Ministerio Fiscal, de su padre D. [COMPLETAR], del defensor judicial D./Dña. [NOMBRE Y APELLIDOS], del propio menor, y de quien se estime pertinente, y previa práctica de las pruebas que se consideren oportunas; se dicte auto acordando la emancipación por concurrencia de causa que entorpece gravemente el ejercicio de la patria potestad.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para presentar demanda de ejecución variará, según el art. 3.2 LJV, y el art. 539 LEC, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 53.3 de la LJV no exige dichos requisitos para la tramitación de la solicitud que nos ocupa, salvo que se formule oposición, en cuyo caso será preceptiva la asistencia de letrado a partir de ese momento. Si bien, tratándose de un menor, se considera lógico que se articule el escrito a través de los profesionales indicados, con conocimientos específicos en la materia.

========================================================================
