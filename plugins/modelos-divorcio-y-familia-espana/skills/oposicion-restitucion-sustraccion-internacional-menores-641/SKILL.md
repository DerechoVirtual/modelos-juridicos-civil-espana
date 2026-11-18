---
name: oposicion-restitucion-sustraccion-internacional-menores-641
description: "Redacta el escrito «Oposición a la restitución en sustracción internacional de menores» (formulario 641 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición a la restitución en sustracción internacional de menores

> Formulario 0641 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] Nº DE COLEGIADO
- [ ] COLEGIO
- [ ] FECHA
- [ ] ÓRGANO
- [ ] Nº DE DOCUMENTO
- [ ] ÓRGANO O PERSONA
- [ ] Nº
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…rado de la Administración de Justicia de»; «… días para que compareciera con el menor»; «… la restitución o retorno solicitada por»; «…al Estado de»; «…na decisión de los Tribunales del Estado»; «…denuncias ante los Tribunales del Estado»; «… a la solicitud de restitución del menor»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (1)

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

### Formulario 0641 · Oposición a la restitución en sustracción internacional de menores

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 15 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 6 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE COLEGIADO, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

D. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en nombre y representación de D. [NOMBRE Y APELLIDOS], según acredito mediante apoderamiento apud-acta otorgado ante el Letrado de la Administración de Justicia de [COMPLETAR] que acompaño, bajo la dirección letrada de D. [NOMBRE Y APELLIDOS], colegiado núm. [Nº DE COLEGIADO] del Iltre. Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco y como mejor proceda en Derecho

DIGO:

1) Que el pasado día [FECHA] mi representado fue requerido por plazo de tres días para que compareciera con el menor [COMPLETAR] y manifestara si accede a la restitución o retorno solicitada por [COMPLETAR] al Estado de [COMPLETAR], o se opusiera a ella.

2) Que, de conformidad con lo dispuesto en el art. 778 ter, apartado 6, de la Ley de Enjuiciamiento Civil, mediante el presente escrito me persono y formulo OPOSICIÓN a la solicitud de restitución del menor, en atención a los siguientes

HECHOS

Esta parte se opone a la solicitud deducida por el demandante [ÓRGANO], invocando el Convenio de la Haya de 1980 y el Reglamento de Bruselas II, al concurrir la causa de la letra b) del artículo 13 del Convenio, sin que el demandante aporte ninguna garantía sobre el grave riesgo de exposición a un peligro físico y psíquico del menor de producirse la restitución.

Al respecto, y si bien aceptamos que existe una decisión de los Tribunales del Estado [COMPLETAR] sobre la custodia del menor, negamos rotundamente los hechos relatados en la demanda respecto de las causas del traslado del menor y las relaciones entre los progenitores y del demandante con el menor, puesto que el traslado fue debido a los continuos episodios de malos tratos del demandante contra mi representado y contra el menor.

Tal como se ha indicado, existe un grave riesgo para el menor derivado de la situación continuada de maltrato y de la nula relación personal con el demandante, quien se ha desentendido totalmente del cuidado y educación del menor desde su nacimiento, habiéndose producido varios episodios de malos tratos que motivaron dos denuncias ante los Tribunales del Estado [COMPLETAR] que se acompañan debidamente traducidas como documentos núm. [Nº DE DOCUMENTO]

Ante esta situación insostenible, mi representado tuvo que trasladarse con el menor al domicilio de sus padres en España, donde permanece en situación totalmente normalizada y estable durante casi un año.

En estas condiciones, la permanencia del menor en España es absolutamente necesaria para el normal desarrollo de su personalidad, puesto que el menor está escolarizado y plenamente integrada en su nuevo medio, y la separación del menor de mi representado, que ha venido cuidándola desde su nacimiento, pondría a la menor en grave situación de riesgo, causándole incluso, posiblemente, un conflicto de identidad, con sentimientos de pérdida y abandono, inseguridad y desorientación en un período evolutivo significativo y decisivo para su desarrollo.

Por el contrario, la restitución del menor al país de origen pondría a la misma en una situación de grave riesgo físico y psíquico, no solo por las graves consecuencias que supondría separarle de mi representado, sino también por la situación continuada de maltrato vivida y el riesgo de reiteración por parte del demandante y su nula relación personal y afectiva con la menor.

Todas estas circunstancias se reflejan en el informe pericial elaborado por [ÓRGANO O PERSONA], donde constan los graves riesgos que supondría para la salud del menor el trasladarlo a su país de procedencia.

A efectos acreditativos aportamos como documentos núm. [Nº], informe del centro escolar y de los servicios sociales del Ayuntamiento de [LOCALIDAD]

Por todo ello, esta parte se opone a la solicitud de restitución, por existir un grave riesgo de que la restitución del menor lo exponga a un peligro grave físico o psíquico, como se acreditará y sin duda se ratificará por V.I. cuando oiga al menor, debiendo denegarse la solicitud según lo dispuesto en el art. 13.b) del Convenio de la Haya de 1980 en relación con el artículo 11.4 del Reglamento núm. 2201/2003 de 27 de noviembre de 2003, de la Unión Europea, aplicable por razones de vigencia temporal, por cuanto que no obstante consagrar este último precepto precepto la obligación, para la autoridad judicial del Estado requerido, de ordenar la restitución del menor, aun cuando pueda estar expuesto a esos peligros físicos o psíquicos, para ello es preciso que se haya acreditado que el estado de origen y requirente, ha adoptado o esté dispuesto a adoptar las medidas adecuadas para garantizar la protección del menor, tras la restitución, lo cual en el caso ni tan siquiera se ha mencionado en la solicitud.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia y procedimiento

Artículos 778 bis.2 y 778.ter de la LEC, debiendo oírse separadamente al menor en presencia del Ministerio Fiscal.

Oposición

Es de aplicación el apartado 6 del citado art. 778 ter que establece que “si en la primera comparecencia el requerido formulase oposición a la restitución o retorno del menor al amparo de las causas establecidas en el correspondiente convenio o norma internacional aplicable, lo que deberá realizar por escrito, el Letrado de la Administración de Justicia en el mismo día dará traslado de la oposición y citará a todos los interesados y al Ministerio Fiscal a una vista que se celebrará dentro del improrrogable plazo de los cinco días siguientes”.

Causas de oposición

Habiéndose invocado el Convenio de la Haya y el Reglamento de Bruselas II, es de aplicación la causa establecida en el 13.b) del citado Convenio: “No obstante lo dispuesto en el artículo precedente, la autoridad judicial o administrativa del Estado requerido no está obligada a ordenar la restitución del menor si la persona, institución u otro organismo que se opone a su restitución demuestra que (…) b) existe un grave riesgo de que la restitución del menor lo exponga a un peligro grave físico o psíquico o que de cualquier otra manera ponga al menor en una situación intolerable”. Por su parte, el art. 11.4 del Reglamento de Bruselas II, si bien establece que los órganos jurisdiccionales no podrán denegar la restitución de un menor basándose en lo dispuesto en la letra b) del artículo 13 del Convenio de La Haya de 1980 si se demuestra que se han adoptado medidas adecuadas para garantizar la protección del menor tras su restitución, lo cierto es que en ningún modo se ha acreditado la adopción de medida alguna de garantía.

Improcedencia de la restitución: interés superior del menor

Los preceptos internacionales invocados deben interpretarse conforme a la LO 1/1996, de 15 de enero, de protección jurídica del menor, al art. 778.ter, apartado 8, de la LEC, y al artículo 12 de la Convención de Naciones Unidas de 1989, sobre los derechos del niño, de lo que se deriva que el interés del menor es el absolutamente prevalente, y en este caso es indudable que debe denegarse la restitución en su interés, dada su situación personal y familiar, así como los riesgos que entraña la restitución.

Costas

Es de aplicación el art. 778 quinquies, apartado 10, de la LEC

Por lo anterior,

AL TRIBUNAL SUPLICO que tenga por presentado este escrito con los documentos que acompaño y sus copias, y en su virtud me tenga por opuesto a la solicitud de restitución del menor [COMPLETAR] y, tras los oportunos trámites, se dicte sentencia por la que deniegue la restitución deducida por D. [NOMBRE Y APELLIDOS], declarando las costas de oficio.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

(Firma Procurador y Abogado)

========================================================================
