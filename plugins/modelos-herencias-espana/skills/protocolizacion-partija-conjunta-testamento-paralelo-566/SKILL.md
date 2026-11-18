---
name: protocolizacion-partija-conjunta-testamento-paralelo-566
description: "Redacta el escrito «Protocolización de partija conjunta y testamento paralelo (Galicia)» (formulario 566 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Protocolización de partija conjunta y testamento paralelo (Galicia)

> Formulario 0566 del plugin **Sucesiones** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Inmuebles** (referencia catastral, superficie, uso) → `consultar_catastro` (y `callejero_catastro` para localizar la dirección).

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

- [ ] Nº (2 veces)
- [ ] LUGAR (2 veces)
- [ ] DÍA (2 veces)
- [ ] MES (2 veces)
- [ ] AÑO (2 veces)
- [ ] PROFESIÓN
- [ ] LOCALIDAD (2 veces)
- [ ] HORA
- [ ] NOMBRE Y APELLIDOS
- [ ] NIF
- [ ] FECHA
- [ ] Otros 23 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Ilustre Colegio de Galicia, Comparecen y»; «…, vecinos de»; «…ega y titulares de los DNI y NIF números»; «…y»; «…uerte, partición que consta extendida en»; «…en este instrumento público extendido en»; «… papel del Estado de uso notarial, serie»; «…, mayor de edad, casado»; «…, vecino de»; «…ERTO, y al efecto Expone I. Que nació en»; «…, el día [FECHA] de»; «…, el día [FECHA] de [COMPLETAR] de»; …

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

### Formulario 0566 · Protocolización de partija conjunta y testamento paralelo (Galicia)

- Año del modelo: 2016
- Revisión 17-11-2026: 32 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

PROTOCOLIZACIÓN DE PARTIJA CONJUNTA Y TESTAMENTO PARALELO OTORGADO POR LOS CAUSANTES

Núm. [Nº]

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Ante mí, Notario del Ilustre Colegio de Galicia,

Comparecen

 y [COMPLETAR], mayores de edad, casados bajo el régimen legal de gananciales, de profesión [PROFESIÓN], vecinos de [COMPLETAR], con domicilio en [LOCALIDAD], de vecindad civil gallega y titulares de los DNI y NIF números [COMPLETAR] y [COMPLETAR] respectivamente.

Intervienen en su propio nombre y derecho.

Tienen a mi juicio, en los conceptos en que intervienen, capacidad legal y legitimación para otorgar este ACTA DE PROTOCOLIZACION DE PARTIJA INTER VIVOS, a cuyo fin,

Exponen

I. Que a fin de evitar contiendas entre sus herederos han procedido al amparo de los artículos 273 y siguientes de la Ley de Derecho Civil de Galicia, a realizar la partición de sus bienes para después de su muerte, partición que consta extendida en [COMPLETAR] folios de papel común firmados por los comparecientes

II. Y expuesto cuanto antecede,

Me requieren

A mí, el Notario, para que protocolice el expresado cuaderno particional a fin de que surta todos sus efectos al fallecimiento de los comparecientes y yo, el Notario, acepto el requerimiento y previo examen del mismo, lo dejo unido a la presente.

Asimismo incorporo a la presente las certificaciones catastrales descriptivas y gráficas correspondientes a las fincas objeto del cuaderno descrito, únicamente en cuanto a las que en su descripción aparece reflejada dicha referencia.

CLÁUSULA LOPD. El/los interviniente/s acepta/n la incorporación de sus datos y la copia del documento de identidad a los ficheros de la Notaría con la finalidad de realizar las funciones propias de la actividad notarial y efectuar las comunicaciones de datos previstas en la ley a las Administraciones públicas y, en su caso, al Notario que suceda al actual en la plaza. Puede/n ejercitar sus derechos de acceso, rectificación, cancelación y oposición en la Notaría. En caso de que se incluyan datos de personas distintas del/de los interviniente/s, este/estos deberá/n haberle/s informado con carácter previo, del contenido de este párrafo.

Leo, por su elección, esta escritura a los comparecientes, quienes la consienten, ratifican y firman libremente.

De haber identificado a los comparecientes por medio de sus respectivos documentos personales de identidad, de que el otorgamiento se adecúa a la legalidad y a la voluntad debidamente informada de los otorgantes o intervinientes y de todo lo demás contenido en este instrumento público extendido en [COMPLETAR] folios de papel del Estado de uso notarial, serie [COMPLETAR], números: de todo lo cual yo, el Notario, doy fe.

TESTAMENTO ABIERTO OTORGADO POR

Núm. [Nº]

En [LUGAR], a [DÍA] de [MES] de [AÑO].

A las [HORA].

Ante mí, Notario del Ilustre Colegio de Galicia,

Comparece

[NOMBRE Y APELLIDOS], mayor de edad, casado [COMPLETAR], vecino de [COMPLETAR], con domicilio en [LOCALIDAD], de vecindad civil gallega y titular del DNI y NIF número [NIF].

Tiene a mi juicio, capacidad legal suficiente y legitimación para otorgar el presente TESTAMENTO ABIERTO, y al efecto

Expone

I. Que nació en [COMPLETAR], el día [FECHA] de [COMPLETAR] de [COMPLETAR].

II. Que es hijo de [COMPLETAR] y de [COMPLETAR], ya fallecidos.

III. Que está casado en únicas nupcias [COMPLETAR] con [COMPLETAR], de cuyo matrimonio tiene [COMPLETAR] hijos llamados y [COMPLETAR].

IV. Expuesto lo que antecede otorga su última voluntad con arreglo a las siguientes,

Cláusulas

El testador lega su citado cónyuge [COMPLETAR], el usufructo voluntario y universal de viudedad, con el contenido y efectos establecidos en la Ley de Derecho Civil de Galicia, relevándole de la obligación de hacer inventario.

Instituye herederos a sus [COMPLETAR] citados hijos en la forma y proporción que resulta de la partija protocolizada a medio de acta autorizada por mí en el día de hoy.

Sustituye vulgarmente a los herederos, en todas las disposiciones contenidas a su favor en la partija reseñada por sus respectivos descendientes.

CLÁUSULA LOPD. El/los interviniente/s acepta/n la incorporación de sus datos y la copia del documento de identidad a los ficheros de la Notaría con la finalidad de realizar las funciones propias de la actividad notarial y efectuar las comunicaciones de datos previstas en la ley a las Administraciones públicas y, en su caso, al Notario que suceda al actual en la plaza. Puede/n ejercitar sus derechos de acceso, rectificación, cancelación y oposición en la Notaría. En caso de que se incluyan datos de personas distintas del/de los interviniente/s, este/estos deberá/n haberle/s informado con carácter previo, del contenido de este párrafo.

Le leo, en alta voz e íntegramente, este testamento al testador, previamente advertido de su derecho de leerlo por sí, a lo que renuncia, declarando que sabe y puede hacerlo, y ratifica su contenido por ser fiel expresión de su voluntad, y lo firma conmigo.

De identificar debidamente al otorgante por su reseñado Documento de Identidad, de que el consentimiento ha sido prestado libremente, de que el otorgamiento se adecua a la legalidad y a la voluntad debidamente informada del otorgante, de haberse cumplido en un solo acto y sin interrupción todas las formalidades de la ley y, en cuanto fuere procedente, de todo lo demás contenido en este instrumento público extendido en [COMPLETAR] folios de papel de uso exclusivo para documentos notariales, serie [COMPLETAR], números [COMPLETAR] y el siguiente en orden correlativo, de todo lo cual, yo, el Notario, doy fe.

========================================================================
