---
name: ineficacia-sobrevenida-testamento-premoriencia-herederos-210
description: "Redacta el escrito «Ineficacia sobrevenida del testamento por premoriencia de los herederos» (formulario 210 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Ineficacia sobrevenida del testamento por premoriencia de los herederos

> Formulario 0210 del plugin **Sucesiones** · revisado el 17-11-2026.

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

- [ ] COLEGIO
- [ ] NÚMERO
- [ ] NIF (7 veces)
- [ ] NÚMERO DE LA CALLE (5 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] FECHA (2 veces)
- [ ] LOCALIDAD
- [ ] IMPORTE
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…TO de Dª EUTIQUIA NÚMERO DE PROTOCOLO En»; «…, a»; «…Partes Dª. PETRA»; «…, mayor de edad, vecina de»; «…umentales: Dª., mayor de edad, vecina de»; «…, mayor de edad, vecina de»; «…: D.ª EUTIQUIA, mayor de edad, vecina de»; «…y estaba viuda de su esposo D. Eufrasio»; «…jos. D. EUFRASIO premurió a su esposa en»; «…ario D. el día al número de su protocolo»; «… testigos: Dª., mayor de edad, vecina de»; «…, mayor de edad, vecina de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 11 de la Ley Orgánica 3/2018

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

### Formulario 0210 · Ineficacia sobrevenida del testamento por premoriencia de los herederos

- Año del modelo: 2020
- Revisión 17-11-2026: 24 campos de relleno marcados en blanco; 8 huecos del original que se habían perdido sin marca, marcados (IMPORTE, NOMBRE Y APELLIDOS, NÚMERO DE LA CALLE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Encabezamiento

Escritura de ACTA DE NOTORIEDAD PARA LA DECLARACIÓN DE HEREDEROS ABINTESTATO de Dª EUTIQUIA

NÚMERO DE PROTOCOLO

En [COMPLETAR], a [COMPLETAR] de dos mil.

ANTE MI, Dª, Notario del Ilustre Colegio de [COLEGIO]

Partes

Dª. PETRA [COMPLETAR], mayor de edad, vecina de [COMPLETAR], con domicilio en Avenida, nº [NÚMERO] y provista de NIF [NIF]

D. ISIDRO mayor de edad, con igual vecindad y domicilio que la anterior, y provisto de NIF [NIF].

Y de otra como testigos instrumentales:

Dª., mayor de edad, vecina de [COMPLETAR], con domicilio en Avenida, nº [NÚMERO DE LA CALLE] y provista de NIF [NIF].

D. [NOMBRE Y APELLIDOS], mayor de edad, vecina de [COMPLETAR], con domicilio en Avenida, nº [NÚMERO DE LA CALLE] y provisto de NIF [NIF].

Tienen a mi juicio la capacidad legal necesaria para otorgar la presente ACTA DE NOTORIEDAD, y en consecuencia

Expositivo

I.- CAUSANTE:

D.ª EUTIQUIA, mayor de edad, vecina de [COMPLETAR], con domicilio en Avenida, nº [NÚMERO DE LA CALLE] y provista de NIF [NIF] falleció en el día [FECHA], según resulta del certificado de defunción.

II.- CIRCUNSTANCIAS PERSONALES:

D.ª EUTIQUIA nació en el día [FECHA].

Al momento de su fallecimiento tenía su domicilio en [LOCALIDAD] y estaba viuda de su esposo D. Eufrasio [COMPLETAR], de cuyo matrimonio no hubo hijos.

D. EUFRASIO premurió a su esposa en [COMPLETAR]

III.- ULTIMAS VOLUNTADES:

Que al momento de su fallecimiento, D.ª EUTIQUIA había otorgado testamento ante el Notario D. el día al número de su protocolo [COMPLETAR], según consta en el certificado de actos de última voluntad.

Dª EUTIQUIA otorgó testamento en el que:

“1.- instituyó heredero único “a su esposo D. EUFRASIO y le otorga el usufructo de todos sus bienes.

2.- Con cargo al tercio de libre disposición, legó el fondo de inversiones de la entidad BZ por importe de [IMPORTE] euros a favor de la Asociación Española de Amigos del Parque Natural Botánico..”

Dª EUTIQUIA falleció el sin haber revocado el testamento.

IV.- INEFICACIA SOBREVENIDA DEL TESTAMENTO PO PREMORIENCIA DEL HEREDERO TESTAMENTARIO.

El fallecimiento de D. Eufrasio constituye una causa de ineficacia sobrevenida del testamento por lo que procede abrir la sucesión intestada de Dª Eutiquia siendo los legitimarios sus hermanos D. Isidro y Dª Petra, en tanto que son los familiares más próximos a la causante en línea cotaleral, no existiendo herederos forzosos (hijos, nietos ni ascendientes).

V.- DILIGENCIA-DOCUMENTACION:

- certificado literal de defunción

- certificado de actos de últimas voluntades

- D.N.I. del causante

- copia del libro de familia y certificado de matrimonio

- testamento de Dª EUTIQUIA

- certificado de defunción de D. Eufrasio esposo de la causante.

- certificado de nacimiento de D. Isidro y Dª Petra

- certificado de defunción de los padres de Dª Eutiquia

VI.- PRUEBA TESTIFICAL.

Se acompañan los siguientes testigos:

Dª., mayor de edad, vecina de [COMPLETAR], con domicilio en Avenida, nº [NÚMERO DE LA CALLE] y provista de NIF [NIF].

D. [NOMBRE Y APELLIDOS], mayor de edad, vecina de [COMPLETAR], con domicilio en Avenida, nº [NÚMERO DE LA CALLE] y provisto de NIF [NIF].

REQUERIMIENTO

Y me requiere para previa la oportuna prueba documental y testifical compruebe y declare la notoriedad de los hechos expuestos y en consecuencia reconozca como únicos herederos ab intestato de la citada causante Dª Eutiquia a sus hermanos D. Isidro y Dª Petra.

Manifiesta que no ha promovido ni tiene conocimiento de que otra persona con interés legítimo haya promovido acta notarial con la misma finalidad que ésta.

Con tal finalidad los comparecientes

1.- Aseveran la certeza de los hechos positivos y negativos contenidos en el Exponendo que antecede.

2.- Ofrecen para su justificación: a) acreditar documentalmente la apertura de la sucesión intestada y la relación de parentesco de los herederos con el/la causante. b) La declaración testifical sobre la veracidad de los hechos sometidos a notoriedad.

3.- Y que dados los hechos expuestos los únicos herederos abintestato del causante son D. Isidro y Dª Petra, hermanos de Dª Eutiquia.

Vista la capacidad e interés del requirente y siendo notario hábil para actuar conforme al artículo 55 de la Ley Notarial ACEPTO el requerimiento, una vez consultado vía telemática el aplicativo de las actas en el histórico del colegio, que practicaré por diligencias sucesivas y a continuación, advirtiéndole que para la verificación de la notoriedad pretendida y en la instrucción del Acta, practicaré cuantas diligencias y averiguaciones juzgue oportuno, hayan sido o no propuestas en el requerimiento y una vez concluida dicha tramitación, si procede, autorizaré Acta de Notoriedad de Declaración de Herederos Abintestato, que incorporaré a mi protocolo en la fecha y bajo el número que corresponda, dejando constancia en ésta del otorgamiento de la misma.

Hago las reservas y advertencias legales.

A tenor de lo previsto en el artículo 11 de la Ley Orgánica 3/2018, de 5 de diciembre, de Protección de Datos Personales y garantía de los derechos digitales, el compareciente queda informado y acepta que los datos recabados y que en esta escritura constan, han quedado incorporados a los ficheros automatizados de la notaría a mi cargo, y que podrá ejercer los derechos de acceso, rectificación, cancelación y oposición ante el notario autorizante o quién legalmente le sustituya, en la notaría de este domicilio.

Leída por mí este acta, después de advertido el requirente de su derecho a hacerlo por sí, y tras mis explicaciones, la encuentra conforme, presta su consentimiento y firma conmigo el notario, que doy fe identificarle mediante su reseñado Documento Nacional de Identidad, de su capacidad y legitimación para este acto, de que el consentimiento ha sido libremente prestado, de que el otorgamiento se adecua a la legalidad y a la voluntad debidamente informada del otorgante y de todo lo contenido en este Instrumento Público, extendido en

Y no teniendo más que hacer constar, doy por terminada la presente acta que queda incorporada al protocolo, informando a los otorgantes y de todo lo demás, DOY FE
