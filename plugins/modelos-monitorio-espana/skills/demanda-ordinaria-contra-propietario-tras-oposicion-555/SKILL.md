---
name: demanda-ordinaria-contra-propietario-tras-oposicion-555
description: "Redacta el escrito «Demanda ordinaria contra el propietario tras oposición al monitorio» (formulario 555 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda ordinaria contra el propietario tras oposición al monitorio

> Formulario 0555 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] Nº
- [ ] NIF
- [ ] Nº DE COLEGIADO/A
- [ ] FECHA
- [ ] ACTO O RESOLUCIÓN
- [ ] CALLE
- [ ] NÚMERO (6 veces)
- [ ] IMPORTE (5 veces)
- [ ] LUGAR (2 veces)
- [ ] DÍA (2 veces)
- [ ] MES (2 veces)
- [ ] AÑO (2 veces)
- [ ] LOCALIDAD
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de»; «…a fecha ha impagado las mensualidades de»; «…euros. En fecha ha sido requerido»; «… notificación del acuerdo al deudor. Don»; «…procedimiento. Con absoluta mala fe, Don»; «…cho. En prueba de ello, se acompaña como»; «…a el embargo preventivo de los bienes de»; «…, finca registral»; «…del Registro de la Propiedad»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 117 de la Constitución
- artículos 36, 45 y 248 de la Ley 1/2000

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

### Formulario 0555 · Demanda ordinaria contra el propietario tras oposición al monitorio

- Año del modelo: 2016
- Revisión 17-11-2026: 31 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (IMPORTE)
- Avisos de la revisión: REQUISITO DE PROCEDIBILIDAD (MASC). Desde el 3-4-2025, en los procesos declarativos (libro II LEC) y en los especiales (libro IV, incluido el monitorio según la letra del art. 5.2) la demanda solo se admite si antes se intentó un medio adecuado de solución de controversias con el mismo objeto: mediación, conciliación, persona experta independiente, oferta vinculante confidencial, negociación directa o entre abogados, Derecho colaborativo (art. 5.1 LO 1/2025). Excepciones: materias del art. 5.2 (derechos fundamentales, art. 158 CC, medidas judiciales de apoyo, filiación, tutela sumaria de la posesión, obra en ruina, ingreso, entrada en domicilio y sustracción de menores, juicio cambiario); art. 5.3 (demanda ejecutiva, cautelares previas, diligencias preliminares, jurisdicción voluntaria salvo desacuerdo conyugal, gananciales y patria potestad, monitorio europeo y escasa cuantía europeo); art. 3.2 (concursal o parte del sector público); violencia sobre la mujer, donde está vedado (art. 89.9 LOPJ). La demanda describe la negociación o su imposibilidad (art. 399.3 LEC) y acompaña el documento del art. 10 LO 1/2025 o la declaración responsable del art. 264.4.º LEC; si falta, se inadmite (art. 403.2 LEC). Plazo: un año desde la recepción de la solicitud no atendida o desde el fin sin acuerdo (art. 7.3). Consumo: basta la reclamación previa a la empresa (DA 7.ª). Texto sugerido: «CUMPLIMIENTO DEL REQUISITO DE PROCEDIBILIDAD. Con carácter previo, esta parte acudió a [medio] el [fecha], con el mismo objeto que esta demanda, sin alcanzar acuerdo, según acredita el documento n.º [ ] (arts. 5 y 10 LO 1/2025; arts. 264.4.º y 399.3 LEC)».

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda

Juicio ordinario

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de la Comunidad de Propietarios de la C/ núm. [Nº] de [COMPLETAR], CIF nº [NIF], según acredito mediante poder notarial otorgado por su Presidente D./Dña. [NOMBRE Y APELLIDOS], que actúa en nombre de ella ante el Tribunal comparezco con la asistencia letrada de D./Dña.(Colegiado nº [Nº DE COLEGIADO/A]), y como mejor proceda en

derecho DIGO:

Que mediante el presente escrito en nombre de mi mandante, y dentro del plazo concedido mediante Diligencia de Ordenación de fecha [FECHA], formulo DEMANDA DE JUICIO ORDINARIO en reclamación de cantidad que en súplica se concretará contra [ACTO O RESOLUCIÓN], como consecuencia de la oposición formulada en seguidos ante ese Tribunal, y ello con fundamento en los siguientes hechos y fundamentos de derecho:

HECHOS

D./Dña. [NOMBRE Y APELLIDOS] es propietario de del edificio situado en la C/ [CALLE], según consta en la nota simple expedida por el Registro de la Propiedad n.º [NÚMERO] que adjuntamos como documento n.º [NÚMERO].

La cuota de participación que le corresponde es del %, según costa en el citado documento. En virtud de esta participación le corresponde contribuir a los gastos comunes con una cuota mensual de [IMPORTE] euros. Sin embargo, hasta la fecha ha impagado las mensualidades de [COMPLETAR], por lo que adeuda la cantidad de [IMPORTE] euros.

En fecha ha sido requerido [COMPLETAR], para que procediera a la liquidación de la deuda sin que hasta la fecha se haya hecho efectiva. Adjunto como documento n.º [NÚMERO] copia del citado requerimiento y como documento n.º [NÚMERO] factura de su importe, que asciende a [IMPORTE] euros.

En la Junta General Extraordinaria de la Comunidad de celebrada el día se acordó fijar la suma adeudada y reclamarla por vía judicial, autorizando al Presidente para que actuara en ese sentido ante los Tribunales en nombre de la Comunidad. Adjunto como documento n.º [NÚMERO] certificación del Secretario con el visto bueno del Presidente del acuerdo de la Junta aprobando la liquidación de la deuda de D./Dña. [NOMBRE Y APELLIDOS] con la Comunidad de Propietarios.

Como documento n.º [NÚMERO] acompaño acreditación de la notificación del acuerdo al deudor.

Don [COMPLETAR] se opuso al procedimiento monitorio del que dimana el juicio ordinario que se inicia mediante la presente demanda, oponiendo la excepción de pago. A tal efecto acompañaba un listado bancario de movimientos. Pues bien, las cuotas abonadas que se recogen en dicho listado no se corresponden con las cuotas reclamadas en el presente procedimiento.

Con absoluta mala fe, Don [COMPLETAR] intenta aprovechar que los recibos por derramas se giraban mensualmente y de forma separada a los recibos por cuotas ordinarias, queriendo hacer ver que ha abonado los gastos que se le reclaman, cuando en realidad no lo ha hecho.

En prueba de ello, se acompaña como [COMPLETAR] la relación de recibos reclamados y los documentos bancarios que acreditan la devolución de estos y consecuentemente la situación de impago de los mismos.

FUNDAMENTOS DE DERECHO

I.- JURISDICCIÓN Y COMPETENCIA

Son de aplicación al caso los artículos 117 de la Constitución Española, artículos 21, 22.1 y 85.1º de la Ley Orgánica del Poder Judicial y artículos 36, 45 y 248 de la Ley 1/2000, de 7 de enero, de Enjuiciamiento Civil, que determinan la jurisdicción ordinaria como la única competente para conocer de los negocios o demandas civiles que se susciten en territorio español entre españoles, entre extranjeros y entre españoles y extranjeros con arreglo a lo establecido en la Ley Orgánica del Poder Judicial y en los tratados y convenios internacionales en los que España sea parte. Dentro de ésta, corresponde el conocimiento del juicio al Tribunal al que me dirijo, puesto que de lo establecido en el artículo 818.2 de la Ley de Enjuiciamiento Civil sólo cabe deducir una norma implícita de competencia funcional para el conocimiento del juicio ordinario dimanante de un juicio monitorio previo a favor del Tribunal Instancia que conoció de esa último.

II.- PROCEDIMIENTO

El interés económico de la demanda supera la suma de 15.000 euros; por lo que será de aplicación lo dispuesto en los artículos 249 y 254.1 de tan meritada Ley Procesal, debiendo ventilarse y decidirse por el juicio declarativo ordinario, regulado en el Título II del Libro II de la Ley de Enjuiciamiento Civil (artículos 399 y siguientes), siendo asimismo de aplicación las Disposiciones Comunes a los Procesos Declarativos previstas en el Título I de dicho Libro (artículos 248 y siguientes).

III.-CAPACIDAD PARA SER PARTE Y PROCESAL

La tienen demandante y demandadas a tenor de lo dispuesto en los artículos 6 y 7 de la Ley de Enjuiciamiento Civil.

IV.LEGITIMACIÓN

Activa: Corresponde a la demandante, acreedora de la cantidad reclamada.

Pasiva: Corresponde al demandado como titular registral del inmueble generador de los impagos reclamados.

V.-POSTULACIÓN Y DEFENSA

Se cumplen con las normas procesales de postulación ya que la demanda se presenta por medio de Procurador legalmente habilitado y bajo la dirección de Letrado firmante de la misma conforme a lo dispuesto en los artículos 23 y 31 de la Ley de Enjuiciamiento Civil.

VI.-REQUISITOS FORMALES

Se inicia el presente procedimiento por medio de demanda que reúne todos los requisitos exigidos en el artículo 399 de la Ley de Enjuiciamiento Civil y demás relativos a esta materia, todos de la Ley Procesal Civil.

VII.- CUANTÍA

Por así exigirlo el apartado 1º del artículo 253 de la Ley de Enjuiciamiento Civil, se pone de manifiesto que la cuantía de esta demanda es de QUINCE MIL TRESCIENTOS OCHO EUROS Y VEINTINUEVE CÉNTIMOS DE EURO (8.308,29 €).

VIII.-FONDO DEL ASUNTO

1.- Artículo 396 del Código Civil

2.- Artículo 9.1.e) de la Ley de Propiedad Horizontal:

“1. Son obligaciones de cada propietario: ()

e) Contribuir, con arreglo a la cuota de participación fijada en el título o a lo especialmente establecido, a los gastos generales para el adecuado sostenimiento del inmueble, sus servicios, cargas y responsabilidades que no sean susceptibles de individualización.”

IV.- COSTAS. Conforme al apartado 1º del artículo 394 de la Ley de Enjuiciamiento Civil las costas habrán de imponerse a la parte demandada.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y copia de todo ello, admita a trámite el Letrado de la Administración de Justicia la presente demanda y, en su día, y previos los trámites procesales oportunos, se dicte sentencia por la que se condene a D./Dña. [NOMBRE Y APELLIDOS] a abonar a la comunidad de propietarios demandante la cantidad de [IMPORTE], más los intereses legales desde la interposición del procedimiento monitorio, así como a las costas del procedimiento.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firmas de abogado y procurador

OTROSÍ DIGO: Que según lo establecido en el artículo 21.4 de la Ley de Propiedad horizontal, se solicita el embargo preventivo de los bienes de [COMPLETAR], en cantidad suficiente para cubrir el principal, más las costas e intereses calculados en la cantidad de [IMPORTE], sin necesidad de prestar caución.

Por lo que,

SUPLICO AL TRIBUNAL: que, teniendo por efectuada esta petición, se proceda al embargo de la vivienda sita en [LOCALIDAD], finca registral [COMPLETAR] del Registro de la Propiedad [COMPLETAR], ordenando librar el oportuno mandamiento duplicado dirigido al Registro de la Propiedad correspondiente, a fin de efectuar la anotación preventiva de embargo sobre bienes inmuebles, a tenor del art. 42.2 de la Ley Hipotecaria.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firmas de abogado y procurador

========================================================================
