---
name: autorizacion-usufructuario-reclamar-creditos-vencidos-708
description: "Redacta el escrito «Autorización al usufructuario para reclamar créditos vencidos del usufructo» (formulario 708 de propiedad y derechos reales, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Autorización al usufructuario para reclamar créditos vencidos del usufructo

> Formulario 0708 del plugin **Propiedad y derechos reales** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (4 veces)
- [ ] NOMBRE Y APELLIDOS (9 veces)
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] CALLE (3 veces)
- [ ] NÚMERO (3 veces)
- [ ] IMPORTE (2 veces)
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA»; «…dicación de la herencia de mi marido, D.»; «…ntad contenida en testamento otorgado el»; «…, ante el Notario de»; «…un usufructo sobre el Fondo de Inversión»; «…, de la entidad financiera»; «…mediante burofax recibido el»; «…to copia autorizada del testamento de D.»; «… constituido sobre el Fondo de Inversión»; «…, de la entidad financiera»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 103.1 de la LJV
- art. 100 de la Ley 15/2015
- art. 507 del Código Civil
- art. 471 del Código Civil
- art. 103.1 LJV
- art. 101.1 LJV
- art. 100 LJV
- art. 3.2 LJV
- art. 101.2 LJV

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

### Formulario 0708 · Autorización al usufructuario para reclamar créditos vencidos del usufructo

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 35 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito que promueve el expediente de jurisdicción voluntaria en solicitud de autorización judicial para reclamar créditos vencidos derivados del usufructo, previa la convocatoria de comparecencia prevista en el art. 103.1 de la LJV, con citación de los nudos propietarios y de quien se estime pertinente.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA [COMPLETAR] DE [LOCALIDAD]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

Que por medio del presente escrito, y de conformidad el art. 100 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud de autorización judicial para reclamar créditos vencidos derivados del usufructo. Todo ello, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que mediante escritura de adjudicación de la herencia de mi marido, D. [COMPLETAR], y de conformidad con su última voluntad contenida en testamento otorgado el [COMPLETAR], ante el Notario de [COMPLETAR] D./Dña. [NOMBRE Y APELLIDOS], se constituyó un usufructo sobre el Fondo de Inversión [COMPLETAR], de la entidad financiera [COMPLETAR] SA. El uso y disfrute de dicho activo fue adjudicado a mi persona, y su nuda propiedad, a partes iguales, a los dos hijos del causante, de un matrimonio anterior, D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], y a D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO]. En la propia constitución se me reveló de la obligación de prestar fianza como usufructuaria.

2.ª) Que en el último año, y gracias a la buena evolución de los mercados bursátiles, se han generado dividendos que constituyen créditos vencidos por importe de [IMPORTE] euros. Se acompaña certificación bancaria de la citada entidad, en la que se advera lo expuesto.

3.ª) Que, cumpliendo con lo exigido en el art. 507 del Código Civil, mediante burofax enviado a ambos nudos propietarios el pasado [FECHA], se solicitó su permiso para percibir los dividendos generados, habiéndose negado D./Dña. [NOMBRE Y APELLIDOS] mediante burofax recibido el [COMPLETAR], y sin que D./Dña. [NOMBRE Y APELLIDOS] haya ofrecido respuesta alguna hasta la fecha.

4.ª) A los efectos de poder percibir los frutos del usufructo a los que tengo derecho conforme dispone el art. 471 del Código Civil, acudo al expediente previsto en los arts. 100 y ss. LJV, a fin de obtener la autorización judicial necesaria, ante la falta de acuerdo con los nudos propietarios. A los efectos de la comparecencia judicial prevista en el art. 103.1 LJV, se propone la documental que se acompaña y el interrogatorio de los citados propietarios, para el supuesto de que nieguen haber denegado su consentimiento. Finalmente, y cumpliendo con lo exigido en el segundo párrafo de dicho texto legal, me comprometo a informar periódicamente sobre las gestiones realizadas para su cobro, y su resultado final.

5.ª) Que es competente el Tribunal de Instancia al que me dirijo conforme al art. 101.1 LJV en relación con lo dispuesto en el art. 85.1º LOPJ, al encontrarse en su partido judicial mi domicilio.

6.ª) Se acompañan a este escrito copia autorizada del testamento de D. [COMPLETAR], de la escritura de partición y adjudicación de herencia, certificación de la entidad financiera, burofaxes enviados a los nudos propietarios, y burofax recibido de D./Dña. [NOMBRE Y APELLIDOS].

Por todo lo expuesto, al amparo del art. 507 del Código Civil, y del art. 100 LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria, previa la convocatoria de comparecencia prevista en el art. 103.1 de la Ley de Jurisdicción Voluntaria, con citación de los nudos propietarios y de quien se estime pertinente; se dicte auto autorizándome para cobrar el crédito vencido del usufructo constituido sobre el Fondo de Inversión [COMPLETAR], de la entidad financiera [COMPLETAR] SA, por importe de [IMPORTE] euros; comprometiéndome a informar al respecto en el periodo que se fije judicialmente.

Asimismo, se anuncia la siguiente prueba a practicar en la citada comparecencia

.- Documental acompañada al presente escrito.
.- Interrogatorio de D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS].

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma del solicitante

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito, el art. 101.2 LJV no exige dichos requisitos para la tramitación de la solicitud que nos ocupa.

========================================================================
