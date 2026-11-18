---
name: agrupar-fincas-1186
description: "Redacta el escrito «Agrupar fincas» (formulario 1186 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Agrupar fincas

> Formulario 1186 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] MES
- [ ] AÑO
- [ ] LOCALIDAD (2 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] ESTADO CIVIL (2 veces)
- [ ] PROFESIÓN (2 veces)
- [ ] CALLE (2 veces)
- [ ] URBANA, solar de metros cuadrados de superficie sito en Linda: Norte; Sur; Este, y Oeste  (2 veces)
- [ ] En virtud de lo dispuesto en el art. 47 del Real Decreto Legislativo, se hace constar que la referencia catastral de la finca descrita es la siguiente

Dicha referencia catastral se ha acreditado con recibo del Impuesto de Bienes Inmuebles de Naturaleza Urbana correspondiente al año [COMPLETAR], fotocopia del cual, en un solo folio dejo unida a esta matriz para reproducir en sus copias (2 veces)
- [ ] Inscrita en el Registro de la Propiedad de [COMPLETAR], al tomo [COMPLETAR], libro de [COMPLETAR], folio [COMPLETAR], finca número [NÚMERO], inscripción  (2 veces)
- [ ] La finca descrita (está afecta a las siguientes cargas/no está afecta a carga alguna) y al corriente del pago de las obligaciones fiscales, según manifiestan.

Todo ello según nota remitida el día [FECHA] por el Registro de la Propiedad de [COMPLETAR], que protocolizo  (2 veces)
- [ ] Libre de arrendatarios y ocupantes, según manifiestan (2 veces)
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…En»; «…de [MES] de [AÑO] Ante mí:»; «…, profesión [PROFESIÓN], vecino/-a de»; «…, profesión [PROFESIÓN], vecino/-a de»; «… son colindantes entre sí por el lindero»; «…con una superficie de»; «…; linda al Norte con»; «…, al Sur con»; «…, al Sur con [COMPLETAR], al Este con»; «…y al Oeste con Pertenece a»; «…y a»; «…instrumento público, que va extendido en»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Ley 2/2011

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

### Formulario 1186 · Agrupar fincas

- Año del modelo: 2014
- Revisión 17-11-2026: 41 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [COMPLETAR], mi residencia, a [DÍA] de [MES] de [AÑO]

Ante mí: [COMPLETAR], Notario del Iltre. Colegio de [LOCALIDAD],

COMPARECEN:

D./Dña [NOMBRE Y APELLIDOS], mayor de edad, de estado civil [ESTADO CIVIL], profesión [PROFESIÓN], vecino/-a de [COMPLETAR], con domicilio en dicha ciudad en calle [CALLE] y D.N.I. número

Y D./Dña [NOMBRE Y APELLIDOS] (B), mayor de edad, de estado civil [ESTADO CIVIL], profesión [PROFESIÓN], vecino/-a de [COMPLETAR], con domicilio en dicha ciudad en calle [CALLE] y D.N.I. número

Constan sus circunstancias personales de sus manifestaciones y documentos exhibidos y reseñados.

INTERVIENEN:

Ambos en su propio nombre y derecho.

Tienen, a mi juicio, y según intervienen, capacidad y legitimación para otorgar esta ESCRITURA DE AGRUPACIÓN DE FINCAS, y, al efecto,

EXPONEN

PRIMERO.- Los comparecientes son copropietarios por mitad, con carácter ganancial, de las siguientes fincas:

Finca núm. 1:

Descripción: [URBANA, solar de metros cuadrados de superficie sito en Linda: Norte; Sur; Este, y Oeste ]

Referencia catastral: [En virtud de lo dispuesto en el art. 47 del Real Decreto Legislativo, se hace constar que la referencia catastral de la finca descrita es la siguiente

Dicha referencia catastral se ha acreditado con recibo del Impuesto de Bienes Inmuebles de Naturaleza Urbana correspondiente al año [COMPLETAR], fotocopia del cual, en un solo folio dejo unida a esta matriz para reproducir en sus copias].

Inscripción: [Inscrita en el Registro de la Propiedad de [COMPLETAR], al tomo [COMPLETAR], libro de [COMPLETAR], folio [COMPLETAR], finca número [NÚMERO], inscripción ].

Cargas y gravámenes: [La finca descrita (está afecta a las siguientes cargas/no está afecta a carga alguna) y al corriente del pago de las obligaciones fiscales, según manifiestan.

Todo ello según nota remitida el día [FECHA] por el Registro de la Propiedad de [COMPLETAR], que protocolizo ].

Arrendatarios: [Libre de arrendatarios y ocupantes, según manifiestan].

Finca número 2:

Descripción: [URBANA, solar de metros cuadrados de superficie sito en Linda: Norte; Sur; Este, y Oeste ].

Referencia catastral: [En virtud de lo dispuesto en el art. 47 del Real Decreto Legislativo, se hace constar que la referencia catastral de la finca descrita es la siguiente

Dicha referencia catastral se ha acreditado con recibo del Impuesto de Bienes Inmuebles de Naturaleza Urbana correspondiente al año [COMPLETAR], fotocopia del cual, en un solo folio dejo unida a esta matriz para reproducir en sus copias].

Inscripción: [Inscrita en el Registro de la Propiedad de [COMPLETAR], al tomo [COMPLETAR], libro de [COMPLETAR], folio [COMPLETAR], finca número [NÚMERO], inscripción ].

Cargas y gravámenes: [La finca descrita (está afecta a las siguientes cargas/no está afecta a carga alguna) y al corriente del pago de las obligaciones fiscales, según manifiestan.

Todo ello según nota remitida el día [FECHA] por el Registro de la Propiedad de [COMPLETAR], que protocolizo ].

Arrendatarios: [Libre de arrendatarios y ocupantes, según manifiestan].

SEGUNDO.- Que tal como resulta de la descripción expuesta, ambas fincas son colindantes entre sí por el lindero [COMPLETAR]

TERCERO.- Los comparecientes AGRUPAN las fincas antes descritas, por ser colindantes entre sí, formando la siguiente Finca RESULTANTE DE LA AGRUPACIÓN:

URBANA, solar sito en [LOCALIDAD] con una superficie de [COMPLETAR]; linda al Norte con [COMPLETAR], al Sur con [COMPLETAR], al Este con [COMPLETAR] y al Oeste con

Pertenece a [COMPLETAR] y a [COMPLETAR] en cuanto a la totalidad del pleno dominio con carácter ganancial.

Valor Euros.

CUARTO.- Con los antecedentes expuestos, los señores comparecientes según intervienen:

OTORGAN

Que agrupan las fincas descritas en el expositivo PRIMERO de esta escritura, en la que se describe en el expositivo TERCERO de esta misma escritura, cuya inscripción como finca nueva e independiente dejan solicitada del Señor Registrador de la Propiedad número de

AUTORIZACIÓN.- Hago las reservas y advertencias legales; en particular las que se expresan a continuación, y a efectos fiscales he advertido a los comparecientes de la obligación de presentación de la documentación a liquidación dentro de plazo y, en general, de las responsabilidades tributarias que le incumbe en su aspecto material, formal y sancionador, y de las consecuencias de toda índole que se derivarían de la inexactitud de sus declaraciones.

COMUNICACIÓN AL REGISTRO DE LA PROPIEDAD: Por expresa indicación de los interesados, procederé a la presentación telemática de esta escritura en el Registro de la Propiedad correspondiente.

COMUNICACIÓN AL CATASTRO: Procederé a la comunicación prevista en el art. 47.2 de la Ley del Catastro, según redacción dada por la Ley 2/2011 de 4 de marzo de Economía Sostenible, por remisión del formulario aprobado en la Resolución de 21 de diciembre de 2015, de la Subsecretaría.

PROTECCIÓN DE DATOS PERSONALES. Advierto expresamente a los comparecientes que sus datos van a ser incorporados al fichero del Protocolo y documentación notarial y al fichero de Administración y organización, así como del hecho de que, en su caso, tales datos pueden ser cedidos a aquellas Administraciones públicas que según una norma con rango de ley tengan derecho a ello. Hechas las advertencias de sus derechos al respecto.

Les leo, por su elección, esta escritura, advertidos de su derecho a leerla por sí, del que no usan y, tras hacerle las oportunas explicaciones verbales para su cabal conocimiento, manifiestan quedar enterados, la aceptan, se ratifican y firman.

De lo cual, de conocer a las comparecientes y de todo lo contenido en este instrumento público, que va extendido en [COMPLETAR] folios de papel para documentos notariales de la serie [COMPLETAR], números [COMPLETAR] y el presente que firmo, rubrico y sello, yo el Notario, doy fe.

========================================================================
