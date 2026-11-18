---
name: acta-inventario-211
description: "Redacta el escrito «Acta de inventario» (formulario 211 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acta de inventario

> Formulario 0211 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] DÍA
- [ ] COLEGIO
- [ ] NIF
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] Nº
- [ ] FECHA (4 veces)
- [ ] LOCALIDAD
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…MACIÓN DE INVENTARIO NÚMERO DE PROTOCOLO»; «…En»; «…En [COMPLETAR], a [DÍA] de de dos mil»; «…de de dos mil [COMPLETAR]. ANTE MI, Dª»; «…MPARECEN Dª., mayor de edad, viuda de D.»; «…, vecina de»; «…, vecino de»; «…, y provisto de D.N.I.,»; «…y estaba casado con su esposa Dª»; «… de cuyo matrimonio tuvo un hijo llamado»; «… Notoriedad autorizada por el notario de»; «…dos: ACTIVO: PASIVO: Deuda contraída con»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 5 de la LO 15/1999

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

### Formulario 0211 · Acta de inventario

- Año del modelo: 2020
- Revisión 17-11-2026: 22 campos de relleno marcados en blanco; 4 huecos del original que se habían perdido sin marca, marcados (DÍA, FECHA, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escritura de ACTA DE FORMACIÓN DE INVENTARIO

NÚMERO DE PROTOCOLO [COMPLETAR]

En [COMPLETAR], a [DÍA] de de dos mil [COMPLETAR].

ANTE MI, Dª [COMPLETAR], Notario del Ilustre Colegio de [COLEGIO]

COMPARECEN

Dª., mayor de edad, viuda de D. [COMPLETAR], vecina de [COMPLETAR], con domicilio en Avenida, y provista de NIF [NIF].

D. [NOMBRE Y APELLIDOS] mayor de edad, con igual vecindad y domicilio que la anterior, y provisto de NIF

IDENTIFICO al/ a los comparecientes por su reseñado documento nacional de identidad y tienen, a mi juicio, capacidad legal suficiente para instar y solicitar la presente ACTA DE FORMACIÓN DE INVENTARIO, y al efecto

EXPONEN

I.- CAUSANTE:

D. [NOMBRE Y APELLIDOS], vecino de [COMPLETAR], con domicilio en Avenida, nº [Nº], y provisto de D.N.I., [COMPLETAR] falleció en el día [FECHA], según resulta del certificado de defunción.

II.- CIRCUNSTANCIAS PERSONALES:

D.nació en el día [FECHA].

Al momento de su fallecimiento tenía su domicilio en [LOCALIDAD] y estaba casado con su esposa Dª [COMPLETAR], de cuyo matrimonio tuvo un hijo llamado [COMPLETAR]

III.- ULTIMAS VOLUNTADES:

Que al momento de su fallecimiento, D.no había otorgado testamento alguno, según consta en el certificado de actos de última voluntad.

Se ha tramitado expediente de declaración de herederos abintestato mediante acta de Notoriedad autorizada por el notario de [COMPLETAR] Don/doña [NOMBRE Y APELLIDOS], el día… bajo el número de protocolo

IV.-

El causante tuvo su última residencia habitual en España, teniendo su último domicilio en la población de.

Me acredita dicho extremo, por exhibición del DNI (certificado de empadronamiento, certificado de defunción).

Yo, notario, soy competente territorialmente por serlo para actuar en la población en la que el causante tuvo su último domicilio.

V.- Ley aplicable.

El causante tenía nacionalidad española y vecindad civil española, por lo que se le aplica las normas de derecho común, no constando nada en contrario.

Manifiesta el/la compareciente, además, que no ha iniciado ningún otro expediente de formación de inventario.

VI.- ANTECEDENTES. - DERECHO DE DELIBERAR.

Por escritura otorgada ante mí del día de hoy, número anterior correlativo, el/la compareciente se ha reservado el derecho a deliberar o reflexionar sobre la oportunidad de aceptar o renunciar la herencia del citado causante, para seguidamente solicitar la formación de inventario notarial a que se refiere los artículos 1010.2, 1011 y siguientes CC y 67 y 68 LN, (objeto de este expediente) con citación de acreedores y legatarios, para que acudan a presenciarlo, si les conviniere, con la finalidad de conocer el exacto alcance del activo y del pasivo y una vez conocida la exacta situación patrimonial, decidir si acepta pura y simplemente, renuncia o liquida la herencia mediante la aceptación a beneficio de inventario.

VII.- Manifestaciones relativas a la formación de inventario.

A estos efectos, manifiesta que los bienes dejados por el/la causante a su fallecimiento, única y exclusivamente en cuanto a lo que conoce y le consta, son los siguientes que se detallan, sin perjuicio de otros que pudieran aparecer y que serán descritos mediante diligencias posteriores y cuyo inventario final se confeccionará en los plazos legalmente establecidos:

ACTIVO:

PASIVO:

Deuda contraída con [COMPLETAR]

Informo a los señores comparecientes que deberán aportar la relación de bienes acompañada de las escrituras y documentos de importancia referidas a los mismos y en concreto: deberán hacerme entrega de escrituras, documentos y otros papeles de importancia que se encuentren, referidos a bienes muebles e inmuebles del causante, escrituras y documentación relevante acreditativa de la titularidad y del valor de las acciones/participaciones de las sociedades en las que fuera titular el causante a la fecha de su fallecimiento, certificaciones del dominio y cargas de los bienes inmuebles inscritos en el Registro de la Propiedad a nombre del causante, así como certificaciones o documentos expedidos por las entidades financieras depositarias, del metálico y valores mobiliarios, y si los valores estuvieran sometidos a cotización oficial, se incluirá su valoración a fecha determinada.

Asimismo, le informo que podrán designarse peritos, de conformidad con lo dispuesto en los artículos 50 y 68.2 LN, para la valoración de los bienes, si por la naturaleza de éstos, considerasen los interesados necesaria su intervención.

REQUERIMIENTO

Los comparecientes SOLICITAN de mí, el/la notario, que inicie el expediente de formación de inventario notarial, con citación de acreedores y legatarios, para que acudan a presenciarlo, si les conviniere. A tal efecto, me informa que el domicilio del cónyuge sobreviviente del causante es el mismo que el del propio requirente; siendo el de los acreedores conocidos:

Entidades financieras, administraciones públicas, particulares ..

Me autoriza a mí, la notaria, para que cite en los mismos términos que a los acreedores iniciales, a los que posteriormente puedan aparecer.

Me requiere asimismo para que proceda a dar publicidad al expediente en los tablones de anuncios de los Ayuntamientos de [COMPLETAR]

ACEPTO EL REQUERIMIENTO, que cumplimentaré mediante las actuaciones previstas en la ley.

PLAZO. - A tal efecto, la iniciación de la formalización del inventario notarial, comenzará el día [FECHA].. (dentro de los treinta días siguientes a la citación) del mes de … (se puede añadir hora concreta, a modo de una citación judicial, o fijar, en su caso, dada la forma de proceder en nuestra función notarial, el horario de despacho) y concluirá, con carácter ordinario, dentro de los sesenta días a contar desde su comienzo.

ADVIERTO al/la requirente, especialmente de lo siguiente:

Si por su culpa o negligencia no se principiare o no se concluyere el inventario en los plazos y con las solemnidades prescritas en el artículo 1.014 y siguientes, se entenderá que acepta la herencia pura y simplemente.

Le informo, asimismo, que dentro de los treinta días contados desde el siguiente a aquel en que se hubiese concluido el inventario, deberá manifestar si repudia o acepta la herencia, y si hace uso o no del beneficio de inventario, ya que, pasados los treinta días sin hacer dicha manifestación, se entenderá que la acepta pura y simplemente.

Que durante la formación del inventario y hasta la aceptación de la herencia, a instancia de parte, yo, la Notaria podré adoptar las provisiones necesarias para la administración y custodia de los bienes hereditarios con arreglo a lo que se prescribe en el Código y en la legislación notarial.

También le informo que perderá el beneficio de inventario:

1.º Si a sabiendas dejare de incluir en el inventario alguno de los bienes, derechos o acciones de la herencia.

2.º Si antes de completar el pago de las deudas y legados enajenase bienes de la herencia sin autorización de todos los interesados, o no diese al precio de lo vendido la aplicación determinada al concederle la autorización.

No obstante, podrá disponer de valores negociables que coticen en un mercado secundario a través de la enajenación en dicho mercado, y de los demás bienes mediante su venta en subasta pública notarial previamente notificada a todos los interesados, especificando en ambos casos la aplicación que se dará al precio obtenido.

Durante la formación del inventario y el término para deliberar no podrán los legatarios demandar el pago de sus legados, y que no se podrán pagar los legados, sino después de haber pagado a todos los acreedores.

A EFECTO DE NOTIFICACIONES A LOS ACREEDORES yo, la notaria, hago constar y les notifico:

• Que se está tramitando la formalización del inventario notarial, el cual se iniciará el día [FECHA] del presente año (dentro de los treinta días siguientes a la citación, se puede consignar hora concreta, a modo de una citación judicial, o fijar, en su caso, dada la forma de proceder en nuestra función notarial, el horario de despacho) y concluirá, con carácter ordinario, dentro de los sesenta días a contar desde su comienzo, a cuyo efecto les cito con el objeto que intervengan y presencien su formación y estén informados de su composición.

• Que me informen e indiquen la existencia y cuantía actualizada de las deudas del/la causante, así como de la circunstancia de estar alguna vencida y no satisfecha.

• Que la declaración de los bienes y deudas efectuada por el/la requirente en el inicio de este expediente, lo es en cuanto a lo que conoce y le consta y, por tanto, sin perjuicio de cualesquiera otros/as que en la tramitación de la presente acta puedan surgir, tanto en el activo como en el pasivo.

HAGO a la requirente la reservas y advertencias legales. Asimismo, le advierto de las responsabilidades de toda índole en que incurren en caso de falsedad en sus declaraciones y las relativas al artículo 5 de la LO 15/1999 de protección de datos de carácter personal.

Leo, por su elección, esta acta, la aprueba y firma conmigo Notario, que doy fe de que su consentimiento ha sido libremente prestado, de que el otorgamiento se adecua a la legalidad y a la voluntad debidamente informada de la interviniente, y de todo lo demás consignado en [COMPLETAR] folios folio de clase Notarial, números y los siguientes.
