---
name: extraccion-organos-donantes-vivos-746
description: "Redacta el escrito «Extracción de órganos de donantes vivos» (formulario 746 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Extracción de órganos de donantes vivos

> Formulario 0746 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.

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
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] LOCALIDAD
- [ ] CALLE (2 veces)
- [ ] NÚMERO
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 15 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…D.»; «…con quien tengo un hijo menor de edad D.»; «… y me dedico desde hace más de 20 años a»; «…o de manera ininterrumpida en la empresa»; «…r uno de mis dos riñones a mi hermano D.»; «…timo, aquejado de la grave enfermedad de»; «…osterior se ha programado en el Hospital»; «…, sito en la calle [CALLE] de»; «…se llevará a cabo por el cirujano Doctor»; «…rarse en su partido judicial el hospital»; «…racción de órganos concedida al Hospital»; «… mental y física emitido por el Doctor/a»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 79.1 LJV
- art. 3 de la Ley 30/1979
- art. 78.1 LJV
- art. 78.2 LJV
- art. 4 de la Ley 30/1979
- art. 3.2 LJV
- art. 79.2 LJV
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

### Formulario 0746 · Extracción de órganos de donantes vivos

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 24 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito promoviendo el expediente en solicitud para la constatación del consentimiento libre, consciente y desinteresado, para la extracción de un órgano.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D. [COMPLETAR], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

Que por medio del presente escrito, y de conformidad con los arts. 78 y ss de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud para la constatación de mi consentimiento libre, consciente y desinteresado, para la extracción de órgano, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que soy mayor de edad, me encuentro casado con Dña. [NOMBRE Y APELLIDOS], con quien tengo un hijo menor de edad D. [COMPLETAR], y me dedico desde hace más de 20 años a [COMPLETAR], trabajando de manera ininterrumpida en la empresa [COMPLETAR]. Siendo una persona capaz en todos los sentidos, acudo al presente expediente para dejar constancia de mi voluntad consciente y desinteresada de donar uno de mis dos riñones a mi hermano D. [COMPLETAR]. Este último, aquejado de la grave enfermedad de [COMPLETAR], ha visto como uno de los suyos ha quedado inutilizado, mientras que el segundo funciona de manera deficiente, y existe un grave riesgo de deje de funcionar, lo que pondría en peligro su vida de manera irremediable.

2.ª) En este sentido, a los efectos de expresar las circunstancias previstas en el art. 79.1 LJV, la extracción e implante posterior se ha programado en el Hospital [COMPLETAR], sito en la calle [CALLE] de [COMPLETAR], centro autorizado por el Ministerio de Sanidad según lo dispuesto en el art. 3 de la Ley 30/1979, de 27 de octubre, sobre extracción y trasplante de órganos. La operación se llevará a cabo por el cirujano Doctor [COMPLETAR], especialista en la materia, quien procederá también a implantarlo posteriormente en mi hermano.

3.ª) Que concurren los requisitos exigidos por la citada legislación, a la que se remite el art. 78.1 LJV: soy mayor de edad, me encuentro en pleno goce de mis facultades mentales, y no estoy aquejado de ninguna deficiencia psíquica o enfermedad mental, que restrinja mi capacidad. He sido informado de las consecuencias previsibles de orden somático, psíquico y psicológico de la donación, de sus repercusiones en mi vida personal, familiar y profesional, y de los beneficios evidentes que se esperan en mi hermano como receptor, quien pasará a tener un riñón sano donde ahora tiene sólo uno con mal funcionamiento. Por último, cumpliendo con lo ordenado por el art. 2 de la citada Ley 30/1979, de 27 de octubre, ni existe compensación alguna prevista para mí, ni se ha solicitado precio ninguno al receptor.

4.ª) Que es competente el Tribunal de Instancia al que me dirijo conforme al art. 78.2 LJV, en relación con lo dispuesto en el art. 85.1º LOPJ, al encontrarse en su partido judicial el hospital [COMPLETAR] en el que me encuentro ingresado y donde se realizará tanto la futura extracción del órgano que ofrezco para su trasplante, como su inserción en el cuerpo de mi hermano.

5.ª) Se acompañan a este escrito documento de autorización para la extracción de órganos concedida al Hospital [COMPLETAR], certificado médico sobre mi plena salud mental y física emitido por el Doctor/a [COMPLETAR], copia de la información escrita recibida sobre la operación de extracción y sus consecuencias, informe médico sobre el estado de salud de mi hermano D. [COMPLETAR], mi libro de familia y certificado de mi empresa sobre los años trabajados.

Por todo lo expuesto, al amparo del art. 4 de la Ley 30/1979, de 27 de octubre, sobre extracción y trasplante de órganos, y de los arts. 78 y ss. LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria; y previa convocatoria de comparecencia con citación del cirujano Doctor/a [COMPLETAR], de mi persona, de mi hermano D. [NOMBRE Y APELLIDOS] y de quien se considere interesado; y tras requerir las explicaciones que se consideren oportunas, se dicte auto que permita extender por escrito el documento de cesión del riñón a D. [COMPLETAR], y que será firmado por el citado Doctor/a y por mí como interesado.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma del solicitante

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 79.2 LJV, no exige requisito alguno de postulación.

========================================================================
