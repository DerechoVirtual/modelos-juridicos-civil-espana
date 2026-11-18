---
name: consignacion-ante-organo-judicial-jurisdiccion-729
description: "Redacta el escrito «Consignación ante órgano judicial en jurisdicción voluntaria» (formulario 729 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Consignación ante órgano judicial en jurisdicción voluntaria

> Formulario 0729 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (4 veces)
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] CALLE (3 veces)
- [ ] NÚMERO (3 veces)
- [ ] IMPORTE (3 veces)
- [ ] FECHA (3 veces)
- [ ] LUGAR
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA»; «… un contrato de arrendamiento firmado el»; «…, mediante un segundo burofax enviado el»; «…es de - + Añadir más párrafos iguales de»; «…es de - + Añadir más párrafos iguales de»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 98 de la Ley 15/2015
- arts. 1.176, 1.177 y 1.178 del Código Civil
- art. 99.1 LJV
- art. 98.2 LJV
- art. 1.176 del Código Civil
- art. 98 LJV
- art. 3.2 LJV
- art. 98.3 LJV

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

### Formulario 0729 · Consignación ante órgano judicial en jurisdicción voluntaria

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (2); 28 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito promoviendo el expediente en solicitud de consignación judicial, sea notificada dicha consignación por el Letrado de la Administración de Justicia a la obligada a fin de que retire la cantidad debida, procediéndose a dictar decreto en el que se tenga por aceptada la obligación a los efectos legales..

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA [COMPLETAR] DE [LOCALIDAD]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

Que por medio del presente escrito, y de conformidad el art. 98 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud de consignación judicial. Todo ello, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que regento un negocio de hostelería en el local sito en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ocupando el mismo en virtud de un contrato de arrendamiento firmado el [COMPLETAR] con Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO]. En dicho contrato se fijaba un plazo de diez años, y una renta mensual cifrada en [IMPORTE] euros, actualizables anualmente.

2.ª) Que desde hace tres meses, y a causa de una discusión con la propietaria a cuenta de unas humedades aparecidas en la parte de atrás del local, la entidad financiera donde se ha venido haciendo puntualmente el pago de la renta en los últimos dos años, no acepta los pagos mensuales, indicando que aquella ha cancelado la cuenta donde se ingresaba el dinero. A cuenta de ello, y a los efectos de evitar una acción de resolución de contrato por impago de rentas, el pasado [FECHA], ofrecí mediante burofax el pago íntegro de las tres mensualidades que ascendían a un total de [IMPORTE] euros, de manera incondicional. Ofrecimiento que ha sido desoído por Dña. [NOMBRE Y APELLIDOS], quien no ha dado respuesta alguna al respecto.

3.ª) Por ello, acudo al presente expediente previsto en los arts. 98 y ss. LJV, habiendo anunciado a la propietaria, mediante un segundo burofax enviado el [COMPLETAR], la consignación judicial, que se realizará en cuanto se disponga del número de cuenta del órgano judicial finalmente competente en la referida cantidad de [IMPORTE] euros, que comprende las mensualidades de

-
+
Añadir más párrafos iguales

 de [COMPLETAR],

La misma se pone a disposición del órgano judicial para su pago inmediato a Dña. [NOMBRE Y APELLIDOS].

4.ª) De esta forma, se reúnen los requisitos previstos en los arts. 1.176, 1.177 y 1.178 del Código Civil en orden a liberar al obligado al pago. La propietaria del inmueble ha desoído el ofrecimiento del pago, le ha sido previamente anunciada la consignación, y la cantidad se pone a disposición del Tribunal finalmente competente, ajustándose estrictamente a las disposiciones que regulan el pago. Asimismo, en la presente solicitud, de conformidad con lo exigido en el art. 99.1 LJV, se identifica a la persona interesada en la obligación, se indica su domicilio a los efectos de su citación, se expresan las razones de la consignación, y se pone la cantidad adeudada a disposición del órgano judicial. (2)

5.ª) Que es competente el Tribunal de Instancia al que me dirijo conforme al art. 98.2 LJV, al encontrarse en su partido judicial el local arrendado, y donde deben realizarse los pagos de las rentas que se rechazan.

6.ª) Se acompañan a este escrito el contrato de arrendamiento, copia del extracto bancario donde se pueden comprobar los pagos anteriores a los rechazados, burofax en el que se ofrece el pago, y burofax en el que se anuncia la consignación.

Por todo lo expuesto, al amparo del art. 1.176 del Código Civil, y del art. 98 LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria, se notifique por el Letrado de la Administración de Justicia a Dña. la existencia de la consignación a fin de que retire la cantidad debida, procediéndose a dictar decreto en el que se tenga por aceptada la obligación a los efectos legales, y se cancele la obligación relativa a las mensualidades de

-
+
Añadir más párrafos iguales

 de [COMPLETAR],

[NOMBRE Y APELLIDOS], del contrato de arrendamiento de fecha [FECHA].

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma del solicitante

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 98.3 LJV, no exige dichos requisitos para la tramitación de la solicitud que nos ocupa.

(2) En la práctica la solicitud se realiza sin el ingreso del dinero en la cuenta bancaria del Tribunal, puesto que todavía no se conoce cuál es el competente; es en el momento en que se conoce el mismo cuando se efectúa el ingreso anunciado.

========================================================================
