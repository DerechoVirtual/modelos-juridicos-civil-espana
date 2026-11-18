---
name: autorizacion-enajenar-bienes-menores-personas-apoyos-754
description: "Redacta el escrito «Autorización para enajenar bienes de menores o personas con apoyos» (formulario 754 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Autorización para enajenar bienes de menores o personas con apoyos

> Formulario 0754 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] FECHA (3 veces)
- [ ] NÚMERO (3 veces)
- [ ] CALLE (3 veces)
- [ ] IMPORTE (2 veces)
- [ ] LUGAR
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…numeración del juzgado de procedencia).]»; «… se encuentra ingresada en la Residencia»; «…, sita en la calle [CALLE] de»; «…de»; «… finca nº [NÚMERO], inscrita en el folio»; «…, inscrita en el folio [COMPLETAR], tomo»; «…, tomo [COMPLETAR], libro»; «…por la Sociedad de Tasaciones»; «…de»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 62.2 LJV
- art. 65.2 LJV
- art. 66 LJV
- art. 62.1 LJV
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

### Formulario 0754 · Autorización para enajenar bienes de menores o personas con apoyos

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 26 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito promoviendo el expediente para obtener la autorización judicial para la venta de un bien inmueble de persona con discapacidad con medidas de apoyo para el ejercicio de su capacidad jurídica.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], asistido por el defensor judicial D./Dña. [NOMBRE Y APELLIDOS] según acredito mediante copia fehaciente de la escritura de poderes, que acompaño para su unión a los autos por copia testimoniada con devolución de aquélla, como mejor proceda en derecho comparezco y DIGO: (1)

Que por medio del presente escrito, y de conformidad con los arts. 61 y ss. de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud de autorización judicial para la venta de bien inmueble de persona con discapacidad con medidas de apoyo para el ejercicio de su capacidad jurídica, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que mi representado es hijo y curador con funciones de representación de su madre Dña. [NOMBRE Y APELLIDOS], en virtud de sentencia dictada por la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] en fecha [FECHA], en autos de proceso sobre provisión de medidas judiciales de apoyo a las personas con discapacidad nº [NÚMERO], que devino firme al no ser recurrida.

2.ª) Que la persona a la que presta apoyo se encuentra ingresada en la Residencia [COMPLETAR], sita en la calle [CALLE] de [COMPLETAR], desde un momento anterior a la constitución de la curatela. En dicho lugar se encuentra bien atendida, recibiendo los servicios necesarios adecuados a sus graves dificultades de movilidad. El coste de la residencia, que en atención al grado de invalidez, supone la cantidad de [IMPORTE] euros mensuales, ha sido hasta el momento sufragado con los valores mobiliarios propiedad de aquella, tal y como se ha venido poniendo de manifiesto en las cuentas anuales presentadas ante el órgano judicial, según lo dispuesto en el art. 292 I CCiv. Si bien, como ya se avisó en el informe del año pasado, el próximo mes de noviembre se habrán agotado los valores, a pesar de los eventuales rendimientos más optimistas que puedan ofrecerse. Por ello, mi cliente se ve en la necesidad de buscar otra vía de pago de los altos costes de la citada Residencia.

3.ª) Y en este sentido, dentro del patrimonio de la persona a la que se presta apoyo se encuentra la vivienda en la que vivía sita en la calle [CALLE] de [COMPLETAR], finca nº [NÚMERO], inscrita en el folio [COMPLETAR], tomo [COMPLETAR], libro [COMPLETAR], del Registro de la Propiedad nº [NÚMERO] de Madrid. Tal inmueble, con un valor de mercado de [IMPORTE] euros, según tasación pericial realizada el pasado [FECHA] por la Sociedad de Tasaciones [COMPLETAR] SL; ya no sirve de utilidad a aquella, al ser un cuarto piso al que se accede con un último tramo de escaleras, y que no se encuentra adaptado a las dificultades de movilidad antes referidas. Asimismo, ha sido imposible alquilar la vivienda, a pesar de haberse ofertado desde que la persona a la que se presta apoyo fue ingresada en la residencia en tres inmobiliarias distintas. En consecuencia, el inmueble se encuentra vacío e improductivo, siendo necesaria su venta para obtener fondos necesarios para seguir abonando las cuotas de la residencia que Dña. precisa para vivir acorde a sus dificultades.

4.ª) Por todo ello, exigiendo el art. 287.2º CCiv autorización judicial para la venta proyectada, se insta el presente expediente contemplado en los arts. 61 y ss. LJV. Mi cliente se encuentra legitimado según art. 62.2 LJV, como representante legal de su madre, y acude al procedimiento de pública subasta previsto en el art. 65.2 LJV. A tal fin, se ha identificado el bien, se ha expuesto la utilidad y el motivo de la venta, y la finalidad a la que debe aplicarse la suma que finalmente se obtenga. Asimismo, mi mandante se muestra dispuesto a aceptar cualquier tipo de control judicial que asegure tal destino, tal y como prevé el art. 66 LJV. Por último, con el dictamen pericial aportado se ofrece un valor real del mismo que servirá de tipo a la subasta pretendida.

5.ª) Que es competente la Sección Civil del Tribunal de Instancia al que me dirijo conforme al art. 62.1 LJV, al encontrarse en su partido judicial la residencia donde se encuentra la madre de mi mandante, sita en la calle [CALLE] de [COMPLETAR].

6.ª) Se acompañan a este escrito testimonio de la sentencia que acordó la adopción de medidas de apoyo y la designación de curador, inventario de su patrimonio presentado inicialmente, cuentas anuales de los últimos tres años, extracto bancario sobre los movimientos de los valores mobiliarios, certificado de la Residencia sobre su coste y servicios prestados a la persona a la que se presta apoyo, certificación del Registro de la Propiedad, tasación pericial del inmueble en cuestión, y certificaciones de inmobiliarias adverando las ofertas de alquiler finalmente no conseguidas.

Por todo lo expuesto, al amparo del art. 287.2º CCiv, y de los arts. 61 y ss. LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria, previa la convocatoria de comparecencia prevista en el art. 64 de la Ley de Jurisdicción Voluntaria, con citación del Ministerio Fiscal, de la persona a la que se presta apoyo si se considera necesaria, y de quien se estime pertinente; se dicte auto autorizando judicialmente a mi cliente para la venta de la vivienda referida propiedad de su madre Dña. [NOMBRE Y APELLIDOS] en pública subasta, para aplicar el precio al pago de la residencia donde se encuentra.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para presentar demanda de ejecución variará, según el art. 3.2 LJV, y el art. 539 LEC, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 62.3 LJV, exige dichos requisitos de postulación cuando el acto cuya autorización se insta supera los 6.000 euros. Extremo que concurrirá en casi cualquier venta de inmueble como el que nos ocupa.

========================================================================
