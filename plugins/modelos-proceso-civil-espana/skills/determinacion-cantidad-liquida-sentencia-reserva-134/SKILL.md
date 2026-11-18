---
name: determinacion-cantidad-liquida-sentencia-reserva-134
description: "Redacta el escrito «Determinación de la cantidad líquida de una sentencia con reserva de liquidación» (formulario 134 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Determinación de la cantidad líquida de una sentencia con reserva de liquidación

> Formulario 0134 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] NÚMERO (2 veces)
- [ ] SEDE (2 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] FECHA (2 veces)
- [ ] IMPORTE (6 veces)
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] Nº
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…de autos»; «…ción de cumplir el fallo de la sentencia»; «…a sentencia, comprendido entre el mes de»; «…al mes de»; «…que también se acompañan como documentos»; «…numeración del juzgado de procedencia).]»; «…dos en el anexo. Es justicia que pido en»

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 219 de la LEC
- artículo 517.2.1 de la LEC
- arts. 24.1 CE

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

### Formulario 0134 · Determinación de la cantidad líquida de una sentencia con reserva de liquidación

- Año del modelo: 2022
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 26 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Juicio ordinario n.º [NÚMERO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña [NOMBRE Y APELLIDOS], según tengo debidamente acreditado en autos de juicio ordinario, con n.º [NÚMERO] de autos [COMPLETAR], ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

1) Que en fecha [FECHA] se dictó sentencia firme en los autos arriba expresados en la cual se establecía el siguiente pronunciamiento: “Estimo la demanda y condeno a la demandada a que pague a la actora la cantidad resultante de restar a las disposiciones que haya efectuado por retirada de efectivo o por compras del crédito concedido por la actora, con la tarjeta VISA que se especifica en esta sentencia, la totalidad de los pagos que por cualquier concepto haya efectuado la deudora con arreglo a contabilización de las liquidaciones mensuales de la cuenta del crédito, lo que se determinará en ejecución de sentencia”.

2) Que, por medio de la presente, insto la ejecución de la sentencia firme, debiendo determinarse en la presente ejecución la cantidad líquida que debe satisfacer la demandada. al amparo de lo dispuesto en el art. 712 y siguiente de la LEC, en relación con el art. 219 de la LEC, la cual asciende a [IMPORTE] euros.

Basamos esta pretensión en los siguientes

HECHOS

PRIMERO.- La sentencia dictada por el Tribunal al que nos dirigimos acordaba la determinación en ejecución de sentencia, al amparo de lo dispuesto en el art. 219 de la LECiv, de las cantidades que adeuda la demanda conforme a las bases establecidas en la misma.

SEGUNDO.- La demandada no ha satisfecho ninguna cantidad ni ha manifestado su intención de cumplir el fallo de la sentencia [COMPLETAR], por lo que esta parte se ve en la obligación de solicitar la determinación de la cantidad líquida adeudada conforme a las bases establecidas en la sentencia.

TERCERO.- La liquidación resultante, de acuerdo al contenido de la sentencia, asciende al importe de [IMPORTE] euros, según se expresa en el cuadro-resumen que se acompañan como documento número [Nº DE DOCUMENTO], la cual se ha calcula en base a las operaciones aritméticas recogidas en el fallo y de acuerdo a las liquidaciones mensuales de la cuenta de crédito que se acompañan como documentos número [Nº DE DOCUMENTO], cuyo desglose es el siguiente:

1) Las disposiciones efectuadas con cargo a la tarjeta VISA núm. [Nº], en el periodo contemplado en la sentencia, comprendido entre el mes de [COMPLETAR] al mes de [COMPLETAR], asciende a un total de [IMPORTE] euros, según se acreditan por las liquidaciones mensuales, así como de los extractos de cuenta que también se acompañan como documentos [COMPLETAR].

2) Los pagos realizados por la actora ascienden a un total de [IMPORTE] euros, según constan en las liquidaciones mensuales de la cuenta de crédito y extracto de cuentas aportados, así como en la hoja contable que se acompaña como documento número [Nº DE DOCUMENTO].

3) El resultado de restar las disposiciones con los pagos, asciende a [IMPORTE] euros, el cual se solicita que se determine en la presente ejecución como cantidad líquida que adeuda la demandada, tras los trámites legales.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

PRIMERO.- Competencia: Artículo 545.1 LEC, en relación con lo dispuesto en el art. 85.1º LOPJ. La competencia es del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] ante el cual se formula esta demanda, por ser el que conoció del asunto en primera instancia.

SEGUNDO.- Procedimiento: Es de aplicación el procedimiento de los arts. 712 y siguientes de la LEC para la integración del título ejecutivo, para transformar una condena con reserva de liquidación en otra líquida, de acuerdo a las bases establecidas en la sentencia, y poder seguir los trámites de la ejecución dineraria.

TERCERO.- Tutela ejecutiva que se pretende: Se pretende la ejecución de la sentencia de condena firme con amparo en el artículo 517.2.1 de la LEC (arts. 24.1 CE, 18.2 LOPJ y SSTC 32/82 de 7/6, 83/01 de 26/3 y 116/03 de 16/6, entre otras muchas). Al tratarse de una sentencia con reserva de liquidación, conforme al art. 219 de la LEC, se pretende la determinación de la cantidad adeudada conforme a las bases de liquidación establecidas en la sentencia firme.

CUARTO.- Petición de liquidación de la cantidad objeto de condena: El art. 713 de la LECiv establece que junto con el escrito de petición de liquidación, en que solicite motivadamente su determinación judicial, se acompañarán los dictámenes y documentos que se consideren oportunos, dando traslado al deudor en el plazo de diez días para que, en el plazo de diez días, conteste lo que estime conveniente.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y copia de todo ello, tenga por interesada la determinación judicial de la cantidad líquida objeto de condena en la sentencia firme de fecha [FECHA] cuya ejecución se insta, a los que resultó condenada la parte ejecutada en la resolución judicial que constituye el título ejecutivo, y admitida que sea se confiera traslado a la parte ejecutada para que en el plazo de diez días conteste lo que estime conveniente, y seguido el trámite en la forma prevista en el artículo 714 y siguientes de la Ley de Enjuiciamiento Civil, dicte en su día resolución por el que fije la cantidad determinada en el importe solicitado de [IMPORTE] euros, la cual devengará, en su caso, los intereses moratorios correspondientes.

OTROSÍ PRIMERO DIGO que se acompaña en anexo relación de documentos presentados, expresados en este escrito, debidamente foliados y con índice electrónico, para su debida localización y consulta.

SUPLICO AL TRIBUNAL tenga hecha esta manifestación a los efectos oportunos y por aportados los documentos relacionados en el anexo.

Es justicia que pido en [COMPLETAR]

Firma Procurador/a Firma Abogado/a
