---
name: demanda-repeticion-antiguo-propietario-1245
description: "Redacta el escrito «Demanda de repetición del antiguo propietario» (formulario 1245 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de repetición del antiguo propietario

> Formulario 1245 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] IMPORTE (4 veces)
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] LOCALIDAD
- [ ] CALLE (2 veces)
- [ ] DNI/NIE
- [ ] FECHA (3 veces)
- [ ] NÚMERO (4 veces)
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Juicio»; «…manda a tramitar por el cauce del juicio»; «… cuotas de Comunidad correspondientes al»; «…n.º [NÚMERO] del edificio situado en»; «…. Las mensualidades adeudadas eran»; «…aya existido un cambio de titularidad en»; «…n la cuenta de consignación del Tribunal»; «…egún acredito mediante carga girada a él»; «…rajudicial. En este sentido, se acudió a»; «…specíficas en el artículo 21.4 de la LPH»; «…euros, se seguirá el cauce del juicio»; «…en aplicación del artículo»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 21 y 22 de la LOPJ
- artículo 50 de la LEC
- artículo 21.4 de la LPH
- artículo 10 de la LEC
- artículo 21 de la LPH
- art. 5 de la Ley Orgánica 1/2025
- artículo 9.1.i) de la LPH
- artículo 394 de la LEC

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

### Formulario 1245 · Demanda de repetición del antiguo propietario

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 38 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio [COMPLETAR]

Demanda

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

Que mediante el presente escrito formulo demanda a tramitar por el cauce del juicio [COMPLETAR] en ejercicio de acción de repetición regulada en el artículo 21.4 de la Ley de Propiedad Horizontal (LPH) y en reclamación de [IMPORTE] euros contra D./Dña. [NOMBRE Y APELLIDOS] con domicilio en [LOCALIDAD], C/ [CALLE] y DNI n.º [DNI/NIE]. Basamos esta pretensión en los siguientes

HECHOS

Para los Tribunales en los que se haya implantado la presentación de escritos a través del sistema telemático con firma electrónica-Lex Net). Acompañamos como documento nº 1 índice numerado de los documentos que se presentan con esta demanda.

Con fecha [FECHA] se notificó a mi representado petición inicial de procedimiento monitorio presentada por la Comunidad de Propietarios de la C/ [CALLE] en reclamación de [IMPORTE] euros por impago de las cuotas de Comunidad correspondientes al [COMPLETAR] n.º [NÚMERO] del edificio situado en [COMPLETAR]. Las mensualidades adeudadas eran [COMPLETAR].

Adjunto como documento n.º [NÚMERO] copia de la petición inicial de procedimiento monitorio así como la documentación que acompañaba a ésta. Como se puede apreciar, la solicitud se dirigía de forma solidaria al propietario anterior, mi representado, y al actual, D./Dña. [NOMBRE Y APELLIDOS], a quien se demanda ahora en este nuevo juicio.

En fecha [FECHA] esta parte había procedido a la venta del inmueble ya descrito, según se prueba con la escritura de compraventa de fecha [FECHA] suscrita entre las partes de este juicio, que acompaño con el n.º [NÚMERO]. Se puede apreciar que en el momento de la transmisión D./Dña. [NOMBRE Y APELLIDOS] estaba al corriente del pago de las cuotas de Comunidad vencidas a esa fecha, según certificado que oportunamente emitió el Secretario de la Comunidad con el visto bueno del Presidente (documento n.º [NÚMERO]).

Puesto al habla con el Presidente de la Comunidad me comunica que no le constaba de forma fehaciente que haya existido un cambio de titularidad en [COMPLETAR] y que se ha intentado cobrar los recibos en el inmueble al actual usuario que no se ha hecho cargo de éstos ni designado ningún número de cuenta para que se le pasaran al cobro.

El nuevo propietario manifestó a esta parte la imposibilidad de hacer frente a esa deuda, por lo cual, y para evitar mayores gastos y molestias, D./Dña. [NOMBRE Y APELLIDOS] se hizo cargo de la deuda, ingresando la cantidad reclamada en la cuenta de consignación del Tribunal [COMPLETAR], haciendo expresa reserva de su derecho de repetición contra el deudor real.

Se ha reclamado al actual propietario la cifra abonada por D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante carga girada a él [COMPLETAR] sin que hasta la fecha haya contestado a este requerimiento, motivo por el cual nos vemos obligados a presentar esta demanda.

Previamente a la interposición de la demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

Los artículos 21 y 22 de la LOPJ y 36 de la LEC atribuyen con carácter general a la jurisdicción española y al orden civil el conocimiento de esta materia. Los artículos 85.1º de la LOPJ y 45 de la LEC designan a los Tribunales de Instancia como órganos que específicamente resolverán estos pleitos. En aplicación del artículo 50 de la LEC será competente el Tribunal del domicilio del demandado.

A falta de reglas específicas en el artículo 21.4 de la LPH [COMPLETAR], nos remitimos a la regulación general. Y así en atención a la cuantía reclamada, [IMPORTE] euros, se seguirá el cauce del juicio [COMPLETAR] en aplicación del artículo [COMPLETAR] de la LEC. Esta cifra sirve también para fijar la cuantía de la demanda.

El artículo 10 de la LEC legitima para comparecer y actuar en juicio a los titulares de la relación jurídica o del objeto litigioso, y el citado artículo 21 de la LPH autoriza al propietario anterior a repetir contra el propietario actual cuando haya pagado cuotas de Comunidad que éste debía haber abonado.

Los artículos 23 y 31 determinan los supuestos en que las partes han de comparecer representadas por procurador y asistidas por letrado.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

PRIMERO.— El artículo 21.4 de la LPH dice que cuando el propietario anterior de la vivienda o local deba responder solidariamente del pago de la deuda, podrá dirigirse contra él la petición inicial de juicio monitorio sin perjuicio de su derecho a repercutir contra el actual propietario. La misma obligación y derecho tiene el titular registral.

En este caso ha quedado acreditado que la deuda por las cuotas impagadas se ha generado en el tiempo en que ya era titular de la finca el ahora demandado y, por tanto, a él ha beneficiado este pago en exclusiva.

SEGUNDO.— El artículo 9.1.i) de la LPH establece la obligación de comunicar al Secretario de la Comunidad los cambios de titularidad de las viviendas y locales, y sanciona el incumplimiento de esta obligación declarando la responsabilidad solidaria con el nuevo propietario para las deudas devengadas con posterioridad a la transmisión, pero con la posibilidad de repetir sobre éste el pago.

En aplicación del artículo 394 de la LEC deberán imponerse a la parte demandada.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y copia de todo ello, admita a trámite el Letrado de la Administración de Justicia la presente demanda y en su día, previos los trámites legales oportunos, se dicte sentencia por la que se condene a D./Dña. [NOMBRE Y APELLIDOS] a entregar a D./Dña. [NOMBRE Y APELLIDOS] la cantidad de [IMPORTE] euros en concepto de cuotas de Comunidad a las que éste estaba obligado al pago [COMPLETAR], más los intereses legales desde el momento en que esta parte realizó la liquidación de la deuda así como al pago de las costas de este juicio.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firmas de abogado y procurador

========================================================================
