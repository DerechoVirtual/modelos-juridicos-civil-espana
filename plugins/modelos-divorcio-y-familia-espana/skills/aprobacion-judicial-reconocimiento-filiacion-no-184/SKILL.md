---
name: aprobacion-judicial-reconocimiento-filiacion-no-184
description: "Redacta el escrito «Aprobación judicial del reconocimiento de filiación no matrimonial (art. 23.3.b LJV)» (formulario 184 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Aprobación judicial del reconocimiento de filiación no matrimonial (art. 23.3.b LJV)

> Formulario 0184 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NÚMERO
- [ ] LOCALIDAD (4 veces)
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 18 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Don»; «…, Procurador de los Tribunales y de Don»; «…liación no matrimonial del menor de edad»; «…es Hechos y consideraciones jurídicas 1ª»; «…) Que el menor»; «…) Que el menor [COMPLETAR] nació en»; «… figura como hijo no matrimonial de Doña»; «…2ª»; «…2ª [COMPLETAR]) Que el que suscribe, Don»; «…tado tuvo con su madre como es de ver de»; «…3ª»; «…) Que la madre biológica del menor, Doña»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 23.3.b) LJV
- art. 23.3.b) de la Ley 15/2015
- art. 24.1 LJV
- art. 24.3 LJV
- arts. 25 y 26 LJV
- art. 25 LJV

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

### Formulario 0184 · Aprobación judicial del reconocimiento de filiación no matrimonial (art. 23.3.b LJV)

- Año del modelo: 2021
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 30 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 2 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Solicitud de iniciación del expediente de jurisdicción voluntaria para obtener la aprobación judicial para la eficacia del reconocimiento de la filiación no matrimonial de un menor de edad en el supuesto previsto en el art. 23.3.b) LJV.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

Don [COMPLETAR], Procurador de los Tribunales y de Don [COMPLETAR], representación que acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], abogado ejerciente, n.º [NÚMERO] del Iltre. Colegio de [LOCALIDAD], con despacho abierto en [LOCALIDAD], ante el Tribunal comparezco y, como mejor proceda en Derecho, DIGO:

Que por medio del presente escrito promuevo expediente de jurisdicción voluntaria para obtener la aprobación judicial para la eficacia del reconocimiento de la filiación no matrimonial del menor de edad [COMPLETAR], hijo de Dña. [NOMBRE Y APELLIDOS], en base a los siguientes

Hechos y consideraciones jurídicas

1ª [COMPLETAR])

Que el menor [COMPLETAR] nació en [COMPLETAR], el día [FECHA], constando inscrito su nacimiento en el Registro Civil de [LOCALIDAD]. Se acompaña certificación literal de nacimiento como documento nº [Nº DE DOCUMENTO]

En dicha inscripción de nacimiento figura como hijo no matrimonial de Doña [COMPLETAR]

2ª [COMPLETAR])

Que el que suscribe, Don [COMPLETAR], es el padre biológico del menor, fruto de la relación sentimental que mi representado tuvo con su madre como es de ver de [COMPLETAR]

3ª [COMPLETAR])

Que la madre biológica del menor, Doña [COMPLETAR], falleció el pasado día [FECHA] en [COMPLETAR], como acredita el certificado de defunción que se acompaña como documento nº [Nº DE DOCUMENTO]

4ª [COMPLETAR])

Por dicha razón acudo al presente expediente para obtener la aprobación judicial para la eficacia del reconocimiento de la filiación no matrimonial, tal y como prevé el art. 23.3.b) de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), dado que dicho reconocimiento no se ha efectuado en testamento, ni dentro del plazo establecido para practicar la inscripción del nacimiento del citado menor.

Conforme a dicho precepto, está legitimado para solicitar la aprobación judicial para la eficacia del reconocimiento de la filiación no matrimonial de un menor, el que no tenga el consentimiento expreso del representante legal o la asistencia del curador del reconocido, ni del progenitor legalmente conocido, siempre que no hubiera sido reconocido en testamento o dentro del plazo establecido para practicar la inscripción del nacimiento, siendo que se solicita porque el progenitor del hijo menor legalmente conocido (la madre) ha fallecido y, por lo tanto, no puede prestar su consentimiento.

5ª [COMPLETAR])

Que es competente la Sección Civil del Tribunal de Instancia al que me dirijo conforme al art. 24.1 LJV, al encontrarse en su partido judicial el domicilio del menor, quien vive con su abuela en el domicilio sito en

6ª [COMPLETAR])

En la tramitación del presente expediente no es preceptiva la intervención de Abogado ni Procurador, por aplicación del art. 24.3 LJV. No obstante, esta parte interviene representada por el Procurador y bajo la defensa técnica del Letrado que suscriben esta solicitud.

7ª [COMPLETAR])

Respecto al procedimiento a seguir, es de aplicación lo previsto en los arts. 25 y 26 LJV.

Por todo lo expuesto, al amparo de los arts. 23 y ss. LJV,

SUPLICO AL TRIBUNAL:

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria, previa la convocatoria de comparecencia a la que serán citados el Ministerio Fiscal, y mi representado como solicitante; se dicte auto concediendo la aprobación judicial para la eficacia del otorgamiento del reconocimiento de la filiación no matrimonial del menor

OTROSÍ PRIMERO DIGO que, a los efectos de celebración de la comparecencia prevenida en el art. 25 LJV, se interesa que sean oídas las siguientes personas:

Doña [COMPLETAR], abuela materna, con domicilio en [LOCALIDAD]

Por lo que,

SUPLICO AL TRIBUNAL que tenga por solicitada la audiencia de los interesados, comprometiéndose esta parte a presentarlos voluntariamente en el día y hora que se señale para la celebración de la comparecencia.

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del Abogado

Firma del Procurador
