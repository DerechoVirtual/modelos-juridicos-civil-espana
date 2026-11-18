---
name: ejecucion-auto-medidas-provisionales-demanda-423
description: "Redacta el escrito «Ejecución de auto de medidas provisionales: demanda» (formulario 423 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Ejecución de auto de medidas provisionales: demanda

> Formulario 0423 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] Nº (3 veces)
- [ ] AÑO
- [ ] NÚMERO (2 veces)
- [ ] COLEGIO
- [ ] FECHA (4 veces)
- [ ] LUGAR
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…buía la guarda y custodia de los menores»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 545 LEC
- art. 538 LEC
- art. 539.1 LEC
- art. 207.2 LEC
- art. 549 de la LEC
- arts. 551 a 554 LEC
- arts. 699 LEC
- art. 776 LEC
- art. 539.2 LEC

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

### Formulario 0423 · Ejecución de auto de medidas provisionales: demanda

- Año del modelo: 2018
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 rangos de artículos despegados («25 a31» → «25 a 31»); 19 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Solicitud de ejecución de resolución que atribuye provisionalmente guarda y custodia de menores.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], representación que tengo debidamente acreditada en los Autos de medidas provisionales n.º [Nº]/[AÑO], ante el Tribunal comparezco y como mejor proceda en Derecho, DIGO:

Que por medio del presente escrito y en la indicada representación de D./Dña. [NOMBRE Y APELLIDOS], asistido/a del/de la Letrado/a D./Dña. [NOMBRE Y APELLIDOS], colegiado/a n.º [NÚMERO] del Ilustre Colegio de Abogados de [COLEGIO], formulo DEMANDA DE EJECUCIÓN FORZOSA del Auto de medidas provisionales de fecha [FECHA] dictado en los presentes autos, contra D./Dña. [NOMBRE Y APELLIDOS], con domicilio en la c/ nº [NÚMERO], donde podrá ser citado y emplazado basándose en los siguientes,

HECHOS

PRIMERO.- Habiéndose presentado por mi representado/a solicitud de medidas provisionales junto con la demanda de separación/divorcio, contra su esposo/a D./Dña. [NOMBRE Y APELLIDOS], que inició el procedimiento de referencia, y tras celebrarse la preceptiva vista, el Tribunal al que me dirijo dictó auto en fecha [FECHA], en el que entre otros pronunciamientos, atribuía la guarda y custodia de los menores [COMPLETAR] a mi representado/a, estableciéndose un régimen de visitas para el otro progenitor.

Acompaño al presente escrito testimonio del meritado auto, designando a los efectos oportunos, las actuaciones seguidas en los presentes autos.

SEGUNDO.- Que siendo firme dicha resolución, y no habiéndose dado cumplimiento voluntario a la misma, procede su ejecución, por lo que encontrándose aún los menores bajo la custodia de D./Dª [NOMBRE Y APELLIDOS], deberá de requerirse al mismo para que dentro del plazo de [Nº] días traslade a los hijos al domicilio de mi representada, en unión de sus ropas, libros y otros enseres de uso personal, bajo los apercibimientos legales.

A los anteriores hechos les son de aplicación los siguientes,

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA

De acuerdo al art. 545 LEC, resulta competente la Sección de Familia, Infancia y Capacidad del Tribunal [NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).] de Instancia al cual me dirijo por ser el órgano judicial que ha dictado la resolución cuya ejecución se insta.

II.- LEGITIMACIÓN

El art. 538 LEC regula que es parte en el proceso de ejecución la persona o personas que piden y obtienen el despacho de la ejecución y la persona o personas frente a las que ésta se despacha.

III.- POSTULACIÓN.

Conforme a lo dispuesto en el art. 539.1 LEC, la demanda viene firmada por abogado y procurador, ya que estamos ante la ejecución de una resolución dictada en un proceso en que es preceptiva la intervención de dichos profesionales.

IV.- TÍTULO DE EJECUCIÓN

En la presente ejecución es título ejecutivo el auto de medidas provisionales, lo que habilita el art. 517.2.9º en relación al art. 207.2 LEC.

V.- REQUISITOS FORMALES

La presente demanda contiene todos los requisitos enumerados en el art. 549 de la LEC, ya que se ha indicado cual es el título en que se funda, la tutela ejecutiva que se pretende y las personas frente a las que se interesa el despacho de la ejecución. Por último, se acompaña a la demanda ejecutiva la documentación necesaria de la contemplada en el art. 550 del mismo texto legal.

VI.- PROCEDIMIENTO

El Tribunal despachará ejecución y el Letrado de la Administración de Justicia concretará las medidas ejecutivas, por los trámites de los arts. 551 a 554 LEC, en relación con los arts. 699 LEC y ss.; con las especialidades que se contienen en el art. 776 LEC para la ejecución forzosa de los pronunciamientos sobre medidas.

VII.- COSTAS

En virtud de lo dispuesto en el art. 539.2 LEC en relación con el 583 LEC, las costas de esta ejecución deberán ser impuestas al ejecutado, ya que ha sido quien ha originado la necesidad de este procedimiento al no haber cumplido con lo establecido en la resolución recaída en las presentes actuaciones.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito y por realizadas las manifestaciones que en él se contienen, se sirva admitirlo y tener por formulada DEMANDA DE EJECUCIÓN FORZOSA del Auto de medidas provisionales de fecha [FECHA], y previos los trámites legales se dicte auto de orden general de ejecución y despachando ejecución contra el/la ejecutado/a, que se le notificará personalmente en el domicilio arriba referenciado, dictándose decreto por el/la Letrado/a de la Administración de Justicia responsable de la ejecución, por la que se acuerde requerir a D./Dª [NOMBRE Y APELLIDOS] para que en el término de [Nº] días o en el plazo que el tribunal estime oportuno, traslade a los menores al domicilio de mi representado/a, en unión de sus ropas, libros y otros enseres de uso personal, bajo los apercibimientos legales.

Y todo ello con imposición de costas a la parte ejecutada.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

========================================================================
