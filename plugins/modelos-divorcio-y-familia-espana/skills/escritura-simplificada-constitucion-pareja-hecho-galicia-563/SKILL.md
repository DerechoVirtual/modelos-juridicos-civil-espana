---
name: escritura-simplificada-constitucion-pareja-hecho-galicia-563
description: "Redacta el escrito «Escritura simplificada de constitución de pareja de hecho (Galicia)» (formulario 563 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Escritura simplificada de constitución de pareja de hecho (Galicia)

> Formulario 0563 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] Nº
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…en este instrumento público extendido en»; «… papel del Estado de uso notarial, serie»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 1.435 a 1.444 del vigente Código Civil
- Ley 2/2006
- Ley 10/2007

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

### Formulario 0563 · Escritura simplificada de constitución de pareja de hecho (Galicia)

- Año del modelo: 2016
- Revisión 17-11-2026: 3 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

ESCRITURA PÚBLICA DE CONSTITUCION DE PAREJA DE HECHO Y OTROS PACTOS (MODELO SIMPLIFICADO)

Núm. [Nº]

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Ante mí, Notario del Ilustre Colegio de Galicia,

Exponen

I. Que ambos son mayores de edad, capaces y conviven con intención o vocación de permanencia en una relación de afectividad análoga a la conyugal.

II. Que ambos comparecientes tienen vecindad civil gallega.

(al menos uno de ambos debe tener tal vecindad civil)

III. Que no concurre en ninguno de ellos circunstancia legal alguna que les impida llevar a cabo la formalización de la citada pareja de hecho.

IV. Expuesto lo anterior,

Otorgan

Manifestación de voluntad de constituirse en pareja de hecho.

Ambos comparecientes manifiestan en este acto su voluntad de constituir una pareja de hecho entre sí, equiparando sus efectos a los del matrimonio en los términos recogidos en la Ley 2/2006 de 14 de junio, de Derecho Civil de Galicia, conforme a la Disposición Adicional Tercera de la misma en la redacción dada por la Ley 10/2007, de 28 de junio.

Pacto regulador de sus relaciones económicas.

El régimen económico y patrimonial de la pareja será el de absoluta separación de bienes y se regirá por lo dispuesto en los artículos 1.435 a 1.444 del vigente Código Civil, régimen al que deciden acogerse de mutuo acuerdo, según lo cual pertenecerán a cada uno de los integrantes de la pareja, los bienes y deudas que cada uno tuviese en el momento de la constitución de la misma y los que después adquiriese por cualquier título; lo mismo sucederá con las deudas futuras. Asimismo corresponderá a cada uno, la administración, goce y libre disposición de tales bienes.

Los bienes que adquieran en común se regirán por las normas generales aplicables a la comunidad de bienes.

Cláusula LOPD. El/los interviniente/s acepta/n la incorporación de sus datos y la copia del documento de identidad a los ficheros de la Notaría con la finalidad de realizar las funciones propias de la actividad notarial y efectuar las comunicaciones de datos previstas en la ley a las Administraciones Públicas y, en su caso, al Notario que suceda al actual en la plaza. Puede/n ejercitar sus derechos de acceso, rectificación, cancelación y oposición en la Notaría. En caso de que se incluyan datos de personas distintas del/de los interviniente/s, este/estos deberá/n haberle/s informado con carácter previo, del contenido de este párrafo.

Hago las reservas y advertencias legales, en especial la de la necesidad de inscripción en el Registro de Parejas de Hecho de Galicia, cuya inscripción tiene carácter constitutivo conforme al artículo 1.2 del Decreto 248/2007, de 20 de diciembre.

Leo, por su elección, esta escritura a los comparecientes, quienes la consienten, ratifican y firman libremente.

De haber identificado a los comparecientes por medio de sus respectivos documentos personales de identidad, de que el otorgamiento se adecúa a la legalidad y a la voluntad debidamente informada de los otorgantes o intervinientes y de todo lo demás contenido en este instrumento público extendido en [COMPLETAR] folios de papel del Estado de uso notarial, serie [COMPLETAR], números: de todo lo cual yo, el Notario, doy fe.

========================================================================
