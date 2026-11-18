---
name: escritura-constitucion-pareja-hecho-otros-pactos-galicia-559
description: "Redacta el escrito «Escritura de constitución de pareja de hecho y otros pactos (Galicia)» (formulario 559 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Escritura de constitución de pareja de hecho y otros pactos (Galicia)

> Formulario 0559 del plugin **Familia** · revisado el 17-11-2026.

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

- Pacto de designación recíproca de «tutores» entre convivientes: para mayores procede autocuratela (art. 271 CC) en escritura pública.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] DESCRIBIR
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…IÓN DE PAREJA DE HECHO Y OTROS PACTOS En»; «…, a»; «…, a [COMPLETAR] de»; «…, a [COMPLETAR] de [COMPLETAR], de»; «… afectividad análoga a la conyugal desde»; «…de de»; «…ue el domicilio de la pareja de hecho es»; «…r en los que se señalan en los apartados»; «…das cantidades se realizará por medio de»; «…ran que la vivienda de la pareja está en»; «… del responsable son las siguientes: Don»; «…, con dirección en»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

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

### Formulario 0559 · Escritura de constitución de pareja de hecho y otros pactos (Galicia)

- Año del modelo: 2016
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 15 campos de relleno marcados en blanco
- Avisos de la revisión: Pacto de designación recíproca de «tutores» entre convivientes: para mayores procede autocuratela (art. 271 CC) en escritura pública.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

ESCRITURA PÚBLICA DE CONSTITUCIÓN DE PAREJA DE HECHO Y OTROS PACTOS

En [COMPLETAR], a [COMPLETAR] de [COMPLETAR], de [COMPLETAR].

Ante mí, Nombre, Notario del Ilustre Colegio de Galicia,

Exponen

I. Que conviven juntos y en relación de afectividad análoga a la conyugal desde [COMPLETAR] de de [COMPLETAR] y con intención o vocación de permanencia.

II. Que el domicilio de la pareja de hecho es [COMPLETAR].

III. Que uno () o ambos tiene/n vecindad civil gallega.

IV. Que no están incursos en ninguna de las causas que imposibilitan la constitución de la pareja de hecho establecidas en la Ley 2/2006, de 14 de junio, de Derecho Civil de Galicia, en la redacción dada por la Ley 10/2007, de 28 de junio.

V. Que no han sido sometidos a modificación judicial de la capacidad de obrar, gozando de plena capacidad de obrar.

VI. Que ambos tienen pleno conocimiento de la situación personal, económica y laboral de la otra parte, habiéndose informado de manera detallada de tales circunstancias y en modo adecuado a su capacidad de entender con carácter previo a la realización de este pacto.

Y al efecto,

Otorgan

A) PACTO DE CONSTITUCIÓN DE PAREJA DE HECHO

Primero. Que desean constituirse como PAREJA DE HECHO a todos los efectos legales y, especialmente, ser equiparados dichos efectos a los del matrimonio de acuerdo con la Disposición Adicional Tercera de la Ley 2/2006, de 14 de junio, de Derecho Civil de Galicia, en la redacción dada por la Ley 10/2007, de 28 de junio. De manera particular en los que se señalan en los apartados [COMPLETAR].

Segundo. De conformidad con lo anterior solicitan su inscripción como pareja de hecho en el Registro de Parejas de Hecho, adscrito a la Consellería competente en materia de justicia, correspondiente al domicilio de la pareja de hecho.

B) PACTOS SOBRE LAS RELACIONES ECONÓMICAS

Primero. Convienen regir la pareja de hecho por las siguientes normas patrimoniales:

a) Levantamiento de cargas. Los convivientes acuerdan colaborar de manera equitativa al levantamiento de las cargas económicas que origine la convivencia en común.

Por “cargas económicas que origine la convivencia” se han de entender los gastos domésticos comunes consistentes en [DESCRIBIR].

El modo de abono de las referidas cantidades se realizará por medio de [COMPLETAR].

Anualmente se revisará el importe de los gastos domésticos y se realizará una liquidación de los abonados durante el año.

La continuación de la convivencia supone, por sí misma, el reconocimiento y aceptación de las cantidades abonadas por la otra parte así como la satisfacción con el cumplimiento de su obligación, salvo que constase requerimiento o reconocimiento de lo contrario.

b) Régimen económico. Los convivientes acuerdan seguir el criterio de autonomía e independencia patrimonial en el uso, disfrute, adquisición y disposición de los bienes. En los supuestos de adquisición conjunta de algún bien se presume que se realiza en proindiviso ordinario en función del porcentaje del importe aportado por cada uno. De la misma manera, cada conviviente hará frente a sus deudas y obligaciones personales, no pudiendo comprometer el patrimonio del otro.

c) Vivienda habitual. Los convivientes declaran que la vivienda de la pareja está en [COMPLETAR]. La titularidad jurídica de la vivienda no se modificará por el mero hecho de la convivencia y el/los propietarios conservan su/s facultades de disposición sobre ella sin necesidad de consentimiento del conviviente no titular.

d) Ajuar. Los convivientes se comprometen a elaborar de manera conjunta el inventario comprensivo de los bienes que constituyen el ajuar doméstico señalando su titularidad. Podrán ir ampliándolo a medida que se vayan incorporando bienes. La titularidad de los bienes corresponde al conviviente que haya abonado el importe de su compra. En los supuestos en que no se pueda determinar con claridad la titularidad se presumirá que ambos han contribuido por mitad.

C) PACTOS DE RELACIONES PERSONALES

Primero. Establecen los siguientes pactos en la dimensión personal de la relación:

a) Distribución de tareas domésticas. Los convivientes acuerdan colaborar de manera equitativa a la realización de las tareas, gestiones y responsabilidades domésticas.

b) Ejercicio de la función parental. Los convivientes acuerdan y se comprometen a ejercitar de manera conjunta y compartida, tanto durante la convivencia como en caso de cese, las funciones parentales respecto de los hijos menores comunes.

c) Para el supuesto de que fuese necesario, es su voluntad proponer recíprocamente al otro como curador, para el caso de que cualquiera de ellos precise medidas de apoyo. [NOTA DE REVISIÓN (comprobar): Para mayores de edad no cabe tutela; la autodesignación es la autocuratela del art. 271 CC (en escritura pública, como es el caso). Fuente: Código Civil (BOE-A-1889-4763) art. 271, redacción Ley 8/2021 (BOE-A-2021-9233).]

D) SOLICITUD DE INSCRIPCIÓN EN EL REGISTRO DE PAREJAS

Solicitan, así mismo, la inscripción de los pactos que anteceden en el Registro de Parejas de Hecho antes mencionado.

Así lo dicen y otorgan después de hacerles las reservas y advertencias legales.

De acuerdo con lo establecido en la Ley, los comparecientes quedan informados y aceptan la incorporación de sus datos a los ficheros automatizados existentes en la Notaría, que se conservarán en la misma con carácter confidencial, sin perjuicio de las remisiones de obligado cumplimiento a las Administraciones Públicas que estipula la ley. Su finalidad es realizar la formalización del documento presente, su facturación y seguimiento posterior y las funciones propias de la actividad notarial. La identidad y dirección del responsable son las siguientes: Don [COMPLETAR], con dirección en [COMPLETAR].

Les permito la lectura de esta escritura, a los comparecientes, por su opción, la encuentran conforme, aprueban y firman conmigo, el Notario, que de haberles identificado por sus reseñados documentos, de que tienen, a mi juicio, capacidad y legitimación suficientes para todos los actos jurídicos contenidos en este instrumento público, de que han prestado libremente su consentimiento, de que el otorgamiento se adecua a la legalidad y a la voluntad debidamente informada de los otorgantes o intervinientes y de su contenido extendido en [COMPLETAR] folios, que son el presente y los [COMPLETAR] siguientes en orden correlativo, DOY FE.

========================================================================
