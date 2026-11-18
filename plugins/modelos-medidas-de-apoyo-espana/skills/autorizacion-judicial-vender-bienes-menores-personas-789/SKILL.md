---
name: autorizacion-judicial-vender-bienes-menores-personas-789
description: "Redacta el escrito «Autorización judicial para vender bienes de menores o personas con apoyos» (formulario 789 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Autorización judicial para vender bienes de menores o personas con apoyos

> Formulario 0789 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] Nº
- [ ] FECHA (2 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] IMPORTE (3 veces)
- [ ] LUGAR
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «…, finca nº [NÚMERO] Inscrita en el folio»; «…Inscrita en el folio [COMPLETAR], tomo»; «…, tomo [COMPLETAR], libro»; «…de»; «…os escolares en el prestigioso Instituto»; «…ibilidades de ingresar en la Universidad»; «…de Londres, para estudiar la carrera de»; «…ferta de compra efectuada por la entidad»; «…de»; «…ferida propiedad de su hija a la entidad»; «…los estudios de la menor en el Instituto»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 164 del Código Civil
- art. 66 LJV
- art. 63.3 LJV
- art. 62.1 LJV
- art. 166 del Código Civil
- art. 3.2 LJV
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

### Formulario 0789 · Autorización judicial para vender bienes de menores o personas con apoyos

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 29 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito promoviendo el expediente para obtener la autorización judicial para la venta directa de un bien inmueble de un menor sometido a patria potestad.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], asistido por el defensor judicial D./Dña. [NOMBRE Y APELLIDOS] según acredito mediante copia fehaciente de la escritura de poderes, que acompaño para su unión a los autos por copia testimoniada con devolución de aquélla, como mejor proceda en derecho comparezco y DIGO: (1)

Que por medio del presente escrito, y de conformidad con los arts. 61 y ss. de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud de autorización judicial para la venta directa de bien inmueble de menor sometido a patria potestad, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que mi representada es la madre de Dña. [NOMBRE Y APELLIDOS], de [Nº] años de edad, con quien convive y quien ostenta en exclusiva la patria potestad sobre ella, tras el fallecimiento de su marido y padre de la menor en fecha [FECHA]. A la muerte del mismo, la niña heredó una serie de inmuebles, entre los que se encuentra la vivienda sita en la calle [CALLE] de [COMPLETAR], finca nº [NÚMERO] Inscrita en el folio [COMPLETAR], tomo [COMPLETAR], libro [COMPLETAR], del Registro de la Propiedad nº [NÚMERO] de [COMPLETAR].

2.ª) Que la menor ha obtenido en su colegio unas calificaciones excelentes, y, como consecuencia de los cuales, se le brinda la oportunidad de hacer los dos últimos años de sus estudios escolares en el prestigioso Instituto [COMPLETAR], cursando parte de sus estudios en el extranjero, de manera íntegra en el idioma inglés. De esta forma, obteniendo un buen resultado en los dos próximos cursos, se aumentarían las posibilidades de ingresar en la Universidad [COMPLETAR] de Londres, para estudiar la carrera de [COMPLETAR], que es del gusto de la menor. Lo que la daría una salida brillante en tal sector profesional habida cuenta del prestigio del citado centro universitario.

3.ª) El único problema es el alto coste de los estudios, y los gastos que se generarían con la estancia en el extranjero, con un mínimo de seis meses por curso, y que alcanzarían, sin perjuicio de un posible incremento, la cantidad aproximada de [IMPORTE] euros. Importe que excede de las posibilidades económicas de mi mandante puesto que la pensión que le dejó su marido es inferior a los ingresos que el mismo obtenía en vida. Por ello, y dado que el inmueble propiedad de la niña se encuentra improductivo, se entiende necesaria su venta para sufragar los altos costes de una educación exclusiva y realmente interesante para su futuro profesional.

4.ª) Por mandato del art. 164 del Código Civil, mi cliente administra los bienes de su hija, y, en concreto, la vivienda que nos ocupa, que no se encuentra entre las excepciones previstas en tal precepto. Asimismo, el art. 166 del mismo texto legal le obliga, como tal administradora, a la hora de enajenar un bien inmueble, justificar la utilidad o necesidad de la venta, y a obtener la previa autorización del juez con audiencia del Ministerio Fiscal. Por ello, se insta el presente expediente contemplado en los arts. 61 y ss. LJV. Mi cliente se encuentra legitimado según art. 62.2 de dicho texto legal, como representante legal de su hija. A tal fin, se ha identificado el bien, se ha expuesto la utilidad y el motivo de la venta, y la finalidad a la que debe aplicarse la suma que finalmente se obtenga. En este sentido, mi mandante se muestra dispuesto a aceptar cualquier tipo de control judicial que asegure tal destino, tal y como prevé el art. 66 LJV.

5.ª) Por otro lado, mi mandante ha recibido una excelente oferta de compra efectuada por la entidad [COMPLETAR] SL, por un precio de [IMPORTE] euros pagaderos al contado, Precio superior al valor de mercado que resulta de la tasación pericial actualizada que se aporta cumpliendo con lo dispuesto en el art. 63.3 LJV. Por ello, y dado que será difícil encontrar una oferta, siquiera similar, se solicita que se autorice también la venta directa de la vivienda en cuestión, que garantiza un buen rendimiento a la pretendida enajenación.

6.ª) Que es competente la Sección Civil del Tribunal de Instancia al que me dirijo conforme al art. 62.1 LJV, al encontrarse en su partido judicial el domicilio de la menor sometida a patria potestad, sito en la calle [CALLE] de [COMPLETAR].

7.ª) Se acompañan a este escrito certificado de fallecimiento del padre de la menor, escritura de partición de su herencia, certificación del Registro de la Propiedad, presupuesto de los gastos de estudios escolares que se pretenden acometer, certificado de la pensión mensual que percibe mi mandante, y tasación pericial del inmueble.

Por todo lo expuesto, al amparo del art. 166 del Código Civil, y de los arts. 61 y ss. LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria, previa la convocatoria de comparecencia prevista en el art. 64 de la Ley de Jurisdicción Voluntaria, con citación del Ministerio Fiscal, de la menor Dña. [NOMBRE Y APELLIDOS], y de quien se estime pertinente; se dicte auto autorizando judicialmente a mi cliente para la venta directa de la vivienda referida propiedad de su hija a la entidad [COMPLETAR] SL por precio de [IMPORTE] euros, pagaderos al contado. Todo ello, para aplicar el precio al pago de los estudios de la menor en el Instituto [COMPLETAR], y en la Universidad [COMPLETAR].

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para presentar demanda de ejecución variará, según el art. 3.2 LJV, y el art. 539 LEC, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 62.3 LJV, exige dichos requisitos de postulación cuando el acto cuya autorización se insta supera los 6.000 euros. Extremo que concurrirá en casi cualquier venta de inmueble como el que nos ocupa.

========================================================================
