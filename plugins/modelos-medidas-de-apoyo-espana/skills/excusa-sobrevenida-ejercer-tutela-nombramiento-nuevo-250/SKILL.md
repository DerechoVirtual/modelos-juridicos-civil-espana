---
name: excusa-sobrevenida-ejercer-tutela-nombramiento-nuevo-250
description: "Redacta el escrito «Excusa sobrevenida para ejercer la tutela y nombramiento de nuevo tutor (Cataluña)» (formulario 250 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Excusa sobrevenida para ejercer la tutela y nombramiento de nuevo tutor (Cataluña)

> Formulario 0250 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- NO VERIFICADO: excusa de «tutor» de un mayor con discapacidad conforme al CCCat (arts. 222-18 y 222-19); tras la reforma catalana de 2021 la tutela de mayores parece suprimida. Comprobar en el DOGC antes de usarlo.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NÚMERO
- [ ] Nº
- [ ] AÑO (2 veces)
- [ ] FECHA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Doña»; «…Doña [COMPLETAR], como tutora de»; «…iba referenciados fue nombrada tutora de»; «…a sido diagnosticada de la enfermedad de»; «…nzada edad, afectada de la enfermedad de»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 0250 · Excusa sobrevenida para ejercer la tutela y nombramiento de nuevo tutor (Cataluña)

- Año del modelo: 2020
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 9 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 1 huecos del original que se habían perdido sin marca, marcados (Nº)
- Avisos de la revisión: NO VERIFICADO: excusa de «tutor» de un mayor con discapacidad conforme al CCCat (arts. 222-18 y 222-19); tras la reforma catalana de 2021 la tutela de mayores parece suprimida. Comprobar en el DOGC antes de usarlo.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito del tutor/curador alegando excusa sobrevenida para el desempeño de la tutela y solicitando nombramiento de nuevo tutor (Cataluña).

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE] PLAZA JUDICIAL Nº [NÚMERO]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

Doña [COMPLETAR], como tutora de [COMPLETAR] ante el Tribunal comparece en los autos de procedimiento especial sobre adopción de medidas a personas con discapacidad n.º [Nº]/[AÑO], y como mejor proceda en Derecho, DIGO (1):

Que por resolución dictada en este Tribunal con fecha [FECHA] recaída en los autos más arriba referenciados fue nombrada tutora de [COMPLETAR]; cargo que, una vez aceptado, aún sigo desempeñando.

Que al amparo de los arts. 222-18 CCC y 50 LJV mediante este escrito presento EXCUSA SOBREVENIDA en la que solicita ser relevada del cargo de tutora, con arreglo a las razones que a continuación se expresan.

La suscribente ha sido diagnosticada de la enfermedad de [COMPLETAR], que requiere especiales cuidados y ha motivado mi ingreso hospitalario en diversas ocasiones, tal y como se acredita con los informes médicos que se acompañan como documentos números

Que la situación personal en la que me encuentro, dada además mi avanzada edad, afectada de la enfermedad de [COMPLETAR], me impide en la actualidad continuar desempeñando ese cargo con la diligencia debida.

Que dispone el art. 222-18.1 CCC que pueden alegarse como excusas para no ejercer cargos tutelares la edad, la enfermedad, la falta de relación con la persona que debe ser puesta en tutela, las derivadas de las características del empleo profesional del designado o cualquier otra que haga el ejercicio de la tutela especialmente gravoso o que pueda afectarlo.

Por lo expuesto, de acuerdo con lo dispuesto en los mencionados preceptos legales, en relación con el art. 222-19 del mencionado Código,

SUPLICO AL TRIBUNAL:

Que teniendo por presentado este escrito y los documentos que se acompañan, previos los trámites legales, se sirva admitir la excusa alegada y se me libere del cargo de tutora para el que fui nombrada y vengo desempeñando, relevándome de las obligaciones que dicho cargo requiere y procediéndose a la designación de nuevo tutor.

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del interesado

NOTAS DEL FORMULARIO

(1) La excusa debe alegarse con la máxima diligencia poible (arts. 222-19.1 CCC y 50.1 LJV). No es preceptiva la intervención de abogado y/o procurador.
