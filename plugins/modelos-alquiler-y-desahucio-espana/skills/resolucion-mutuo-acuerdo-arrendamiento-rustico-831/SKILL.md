---
name: resolucion-mutuo-acuerdo-arrendamiento-rustico-831
description: "Redacta el escrito «Resolución por mutuo acuerdo del arrendamiento rústico» (formulario 831 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Resolución por mutuo acuerdo del arrendamiento rústico

> Formulario 0831 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

- [ ] LUGAR (2 veces)
- [ ] FECHA (4 veces)
- [ ] NOMBRE Y APELLIDOS (12 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] IMPORTE
- [ ] STS de 5 de abril de 1979
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, mayor de edad, vecino/a de»; «…mayor de edad, agricultor/a, vecino/a de»; «…es propietario/a de la finca»; «…destinada al cultivo de»; «…destinada al cultivo de [COMPLETAR], de»; «…ctáreas, sita en el término municipal de»

## Elecciones que hay que hacer

- DNI / pasaporte

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 1262 CCiv

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

### Formulario 0831 · Resolución por mutuo acuerdo del arrendamiento rústico

- Año del modelo: 2015
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (2); 2 desplegables convertidos en elección en blanco; 27 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Documento de resolución de contrato de arrendamiento rústico por mutuo disenso de las partes.

En [LUGAR], a [FECHA].

REUNIDOS

DE UNA PARTE,

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, vecino/a de [COMPLETAR], con domicilio en [LOCALIDAD] y [ELEGIR: DNI / pasaporte] n.º [NÚMERO] (1)

Y DE OTRA,

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, agricultor/a, vecino/a de [COMPLETAR], con domicilio en [LOCALIDAD] y [ELEGIR: DNI / pasaporte] n.º [NÚMERO]

Intervienen ambos en su propio nombre y derecho, reconociéndose mutua y recíprocamente plena capacidad legal para cuanto pasan a manifestar y convenir y de sus libres y espontáneas voluntades, y a tal fin:

EXPONEN

I.- Que D./Dña. [NOMBRE Y APELLIDOS] es propietario/a de la finca [COMPLETAR] destinada al cultivo de [COMPLETAR], de [COMPLETAR] hectáreas, sita en el término municipal de [COMPLETAR], lindando la referida finca con

II.- Que con fecha [FECHA], D./Dña. [NOMBRE Y APELLIDOS], en calidad de arrendador/a, y D./Dña. [NOMBRE Y APELLIDOS], en calidad de arrendatario/a, suscribieron contrato de arrendamiento rústico sobre la finca descrita en el expositivo I.

III.- Que por motivos personales (2) las partes acuerdan dar por resuelto y extinguido el referido contrato de arrendamiento en los términos fijados en los siguientes,

ESTIPULACIONES

PRIMERA.- Ambas partes, de común acuerdo, resuelven y dejan sin ningún valor ni efecto la relación contractual que les vinculaba.

SEGUNDA.- D./Dña. [NOMBRE Y APELLIDOS] entrega la posesión de la finca descrita en el expositivo de este documento a su propietario/a, D./Dña. [NOMBRE Y APELLIDOS], que manifiesta recibirla a su entera satisfacción.

Asimismo, D./Dña. [NOMBRE Y APELLIDOS] reconoce a la parte arrendadora, D./Dña. [NOMBRE Y APELLIDOS], una deuda derivada de la entrega de la finca de forma anticipada por importe de [IMPORTE] euros, en concepto de indemnización por daños y perjuicios voluntariamente convenida.

A los efectos de la cancelación de la deuda, el arrendador concede de plazo hasta el próximo día [FECHA] para el abono de la misma.

TERCERA.- Manifiesta D./Dña. [NOMBRE Y APELLIDOS] que ha percibido la totalidad de las rentas y demás conceptos que eran de cargo del/ de la arrendatario/a, por lo que nada tiene que reclamar al mismo por dichos conceptos.

Manifiesta asimismo el/la arrendatario/a que ha recogido la cosecha correspondiente al presente año agrícola.

CUARTA.- Manifiestan ambas partes que con la firma de este documento, ambas quedan totalmente desligadas del contrato de arrendamiento que en este acuerdo se reseña, sin que nada tengan derecho a reclamarse como consecuencia del contrato que se resuelve, renunciando mutua y expresamente al ejercicio de acciones legales que pudieran derivarse del contrato referido que les ha vinculado hasta la fecha.

Y en prueba de conformidad con todo ello firman el presente documento por duplicado ejemplar y a un solo efecto en el lugar y fecha expresados en el encabezamiento.

En [LUGAR], a [FECHA].

Firma de EL/LA ARRENDADOR/A:

	Firma de EL/LA ARRENDATARIO/A
D./D.ª [NOMBRE Y APELLIDOS]	D./D.ª [NOMBRE Y APELLIDOS]

NOTAS DEL FORMULARIO

(1) Conforme a constante y reiterada jurisprudencia, el mutuo acuerdo resolutorio o pacto de resolución constituye en nuestro ordenamiento jurídico una causa de extinción de las obligaciones por resolución, disolución o ruptura del vínculo contractual, habiéndose referido a ella, entre otras, las SSTS de 21 de mayo de 1992, 25 de octubre de 1999, rec. 465/1995, 6 de octubre de 2000, rec. 2775/1995 y 30 de diciembre de 2002, rec. 1832/1997. Al referirse a la resolución por "mutuo acuerdo" o de "común acuerdo", el mutuo disenso comporta, en la apreciación de la doctrina más autorizada y la jurisprudencia dominante, la constancia de un consentimiento de signo contrario al constitutivo del vínculo contractual (contrarius consensus), esto es, la existencia de un "acuerdo de voluntades", "convenio" o "pacto" de las partes contratantes dirigido a resolver o disolver el contrato celebrado por ellas dejando sin efecto las obligaciones derivadas del mismo; presupone en otras palabras, la conclusión de "un negocio jurídico extintivo" [STS de 5 de abril de 1979], "la suscripción de común acuerdo de un convenio solutorio y liberatorio del anterior" (STS de 13 de febrero de 1965) o, lo que es igual, la manifestación de un "consentimiento contrario a la existencia del contrato" (STS de 30 de diciembre de 2002, rec. 1832/1997) que, como el consentimiento constitutivo, requiere el encuentro, concurso o entrecruzamiento de las concordes voluntades de sus otorgantes (art. 1262 CCiv), sea de manera simultánea, sea de forma sucesiva. Lo mismo que el consentimiento constitutivo, el extintivo o resolutorio propio del mutuo disenso, puede manifestarse tanto expresa como tácitamente, a través de actos que inequívoca y concluyentemente revelen la común voluntad de los contratantes de dejar sin efecto el negocio concluido, desligándose de las obligaciones por ellos contraídas y renunciando a exigir su efectividad y cumplimiento (STS de 25 de octubre de 1999, rec. 465/1995), pero ese tácito consentimiento ha de quedar probado. El mutuo disenso o común acuerdo de resolución del contrato no está sujeto a forma determinada.

(2) En su caso, especificar cualquier otro motivo por el que las partes por mutuo disenso acuerden la terminación del contrato.

========================================================================
