---
name: revocacion-cese-nombramientos-689
description: "Redacta el escrito «Revocación o cese de nombramientos» (formulario 689 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Revocación o cese de nombramientos

> Formulario 0689 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] SEDE (2 veces)
- [ ] NOMBRE Y APELLIDOS (9 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE (3 veces)
- [ ] NÚMERO (4 veces)
- [ ] NIF
- [ ] IMPORTE
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Otros 20 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… Hechos y consideraciones jurídicas: 1.ª»; «…) Que mi mandante es socio de la entidad»; «…SL constituida el»; «…gún consta en la escritura autorizada el»; «…, Notario de»; «…de los de»; «…de los de [COMPLETAR] el»; «… los de [COMPLETAR] el [COMPLETAR], Tomo»; «…el [COMPLETAR], Tomo [COMPLETAR], Folio»; «…omo [COMPLETAR], Folio [COMPLETAR], Hoja»; «…, con CIF [NIF]. Es titular de»; «…social. Los administradores sociales son»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 266.1 del Real Decreto Legislativo 1/2010
- arts. 122 y 123 LJV
- artículo 121.1 LJV
- art. 120 LJV
- art. 122.2 LJV
- art. 3.2 LJV
- art. 121.3 LJV

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

### Formulario 0689 · Revocación o cese de nombramientos

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; restos de formato retirados; notas del formulario agrupadas al final (1); 44 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Por medio del presente escrito, y de conformidad con el art. 120 de la Ley de Jurisdicción Voluntaria, se promueve expediente en solicitud de cese de auditor nombrado.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, como mejor proceda en derecho comparezco y DIGO: (1)

Que por medio del presente escrito, y de conformidad con el art. 120 de la Ley de Jurisdicción Voluntaria, promuevo expediente en solicitud de cese de auditor nombrado. Todo ello, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª [COMPLETAR])

Que mi mandante es socio de la entidad [COMPLETAR] SL constituida el [COMPLETAR], según consta en la escritura autorizada el [COMPLETAR] por D./Dña. [NOMBRE Y APELLIDOS], Notario de [COMPLETAR], su domicilio social se halla sito en [LOCALIDAD], calle [CALLE], nº [NÚMERO], y fue inscrita en el Registro Mercantil nº [NÚMERO] de los de [COMPLETAR] el [COMPLETAR], Tomo [COMPLETAR], Folio [COMPLETAR], Hoja [COMPLETAR], con CIF [NIF]. Es titular de [COMPLETAR] particiones, de [IMPORTE] euros, de valor nominal, lo que supone un 12,22% del capital social. Los administradores sociales son [COMPLETAR], con domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO]. Se aporta también listado de socios y sus direcciones.

2.ª [COMPLETAR])

Que el pasado [FECHA], mediante decreto dictado por el Letrado de la Administración de Justicia de la Sección de lo Mercantil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], se nombró auditor de la referida entidad a D./Dña. [NOMBRE Y APELLIDOS], con despacho profesional en [COMPLETAR], calle [CALLE], nº [NÚMERO], tras petición al respecto planteada por los socios D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS]. La citada resolución no fue recurrida.

3.ª [COMPLETAR])

Que las labores de auditoría se encuentran paralizadas desde hace más de tres meses, porque el auditor nombrado no es capaz de llevarlas a cabo, a causa de la complejidad del sector al que se dedica la mercantil en cuestión, lo que influye decisivamente en las labores auditoras. En este sentido, D./Dña. [NOMBRE Y APELLIDOS] carece de medios, experiencia y conocimientos específicos al respecto, y, por lo que parece, y a pesar de que mi mandante se lo ha aconsejado, no acaba de dar el paso para renunciar al cargo, sin que se cumpla, por ello, la necesidad de auditoría que determinó su nombramiento.

4.ª [COMPLETAR])

Concurre, en consecuencia, la justa causa para revocar el nombramiento de auditor a la que hace referencia el art. 266.1 del Real Decreto Legislativo 1/2010, de 2 de julio, por el que se aprueba el texto refundido de la Ley de Sociedades de Capital (en lo sucesivo, TRLSC), atendiendo a su incapacidad para realizar una auditoría en condiciones. Asimismo, mi representado se encuentra legitimado para ello, al disponer de más de un 5% del capital social, tal y como establece el referido precepto legal, en relación con el art. 265 TRLSC. Por ello, deberán seguirse los trámites previstos en los arts. 122 y 123 LJV, convocándose a una comparecencia ante el Letrado de la Administración de Justicia, al auditor en cuestión, los administradores sociales, los socios de la entidad, y quien se estime conveniente

5.ª [COMPLETAR])

Que es competente la Sección de lo Mercantil del Tribunal de Instancia al que me dirijo conforme al artículo 121.1 LJV, al encontrarse en su partido judicial el domicilio social de la entidad que designó al auditor cuyo cese se pretende.

6.ª [COMPLETAR])

Se acompañan a esta solicitud copia simple de la escritura de constitución mencionada, certificación del Registro Mercantil donde constan los datos mencionados, certificación expedida por el Secretario del Consejo de Administración de [COMPLETAR] SL del Libro Registro donde constan titularidades sociales, copia testimoniada del decreto en el que se designaba a D./Dña. [NOMBRE Y APELLIDOS] como auditor, y listado de socios y sus direcciones.

Por todo lo expuesto, al amparo del art. 266 TRLSC y del art. 120 LJV,

SOLICITO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria para el cese de auditor; y previa convocatoria de comparecencia ante el Letrado de la Administración de Justicia prevista en el art. 122.2 LJV, con citación del propio D./Dña. [NOMBRE Y APELLIDOS], los administradores sociales, los socios, y a quien se estime oportuno, se dicte decreto cesando en su cargo al primero, con remisión del correspondiente testimonio al Registro Mercantil.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito, el art. 121.3 LJV, considera preceptiva la intervención de Abogado y Procurador para la solicitud en análisis.

========================================================================
