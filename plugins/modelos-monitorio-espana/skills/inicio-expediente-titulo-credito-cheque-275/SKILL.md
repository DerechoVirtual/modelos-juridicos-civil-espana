---
name: inicio-expediente-titulo-credito-cheque-275
description: "Redacta el escrito «Inicio de expediente de título de crédito: cheque» (formulario 275 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Inicio de expediente de título de crédito: cheque

> Formulario 0275 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] NÚMERO
- [ ] FECHA (2 veces)
- [ ] IMPORTE (2 veces)
- [ ] Nº (3 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 18 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, Hechos y consideraciones jurídicas: 1ª»; «…, en la localidad de»; «… está domiciliado en la entidad bancaria»; «…, nº [Nº] de cuenta»; «…s comerciales entre el solicitante y Don»; «…de serie»; «…alonario emitido por la entidad bancaria»; «…, sucursal de»; «…reconocimiento de deuda en cuya cláusula»; «…emisión del cheque y copia del mismo. 2ª»; «…l cheque para su abono en la sucursal de»; «… formulada en la Comisaría de Policía de»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 132 de la Ley 15/2015
- art. 133.2 LJV
- art. 133.1 LJV
- art. 132 LJV
- art. 154 de la Ley 19/1985
- art. 135 LJV
- art. 3.2 LJV
- art. 133.3 LJV

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

### Formulario 0275 · Inicio de expediente de título de crédito: cheque

- Año del modelo: 2020
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 32 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito inicial de expediente de jurisdicción voluntaria por robo de cheque bancario.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], como mejor proceda en derecho comparezco y DIGO (1):

Que por medio del presente escrito, y de conformidad con el art. 132 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud de prohibición de transmisión y pago de títulos de crédito sustraídos. Todo ello, en base a los siguientes,

Hechos y consideraciones jurídicas:

1ª [COMPLETAR])

Mi mandante es legítimo tenedor del cheque nº [NÚMERO] emitido el pasado día [FECHA], en la localidad de [COMPLETAR], por importe de [IMPORTE] euros, el cual está domiciliado en la entidad bancaria [COMPLETAR], nº [Nº] de cuenta [COMPLETAR], con vencimiento

El citado título de crédito fue emitido como consecuencia de las relaciones comerciales entre el solicitante y Don [COMPLETAR], en virtud de las cuales el firmante adeudaba la cantidad de [IMPORTE] euros, emitiéndose el cheque con el nº [Nº] de serie [COMPLETAR], del talonario emitido por la entidad bancaria [COMPLETAR], sucursal de [COMPLETAR].

Se acompaña como documentos nº [Nº DE DOCUMENTO], copia del contrato de reconocimiento de deuda en cuya cláusula [COMPLETAR] consta la emisión del cheque y copia del mismo.

2ª [COMPLETAR])

En el día de la fecha, cuando el solicitante se dirigía a ingresar el cheque para su abono en la sucursal de [COMPLETAR] fue víctima de un robo con intimidación a las [Nº] horas del día [FECHA], en el cual le ha sido sustraído, entre otros bienes y efectos, el referido cheque, tal como consta relacionado en la denuncia formulada en la Comisaría de Policía de [COMPLETAR] que acompaño como documento nº [Nº DE DOCUMENTO]

3ª [COMPLETAR])

Por ello, es interés de mi cliente que se prohíba que el cheque sustraído pueda ser transmitido, o se pueda pagar su importe a su eventual tenedor, y que se le dé a tal hecho la publicidad legalmente procedente. Se acude, en consecuencia, al procedimiento previsto en los arts. 132 y ss. LJV, que permite llevar a la práctica el derecho previsto en el art. 548 del Código de Comercio. En este sentido, mi mandante se encuentra legitimado para la solicitud que se plantea, al haber sido el legítimo tenedor de los títulos de crédito indicados, en virtud de lo dispuesto en el art. 133.2 LJV. Asimismo, procederá el anuncio del expediente en el Boletín Oficial del Estado, en un periódico de gran circulación en la Comunidad de [COMPLETAR], y la convocatoria de una comparecencia con citación de los interesados.

4ª [COMPLETAR])

Que es competente la Sección de lo Mercantil del Tribunal de Instancia al que me dirijo conforme al art. 133.1 LJV, al encontrarse en su partido judicial el lugar de pago previsto en el título, el domicilio social de la entidad

5ª [COMPLETAR])

Que establece el art. 132 LJV, que se aplicarán las disposiciones del Capítulo VII cuando se solicite la adopción de las medidas previstas en la legislación mercantil en los casos de robo, hurto, extravío o destrucción de títulos valor o de representación de partes de socio.

En particular, dispone el art. 154 de la Ley 19/1985, de 16 de julio, Cambiaria y del Cheque que, en los casos de extravío, sustracción o destrucción de un cheque, el tenedor desposeído del mismo podrá acudir ante el Juez para impedir que se pague a tercera persona, para que aquél sea amortizado y para que se reconozca su titularidad. El tenedor desposeído podrá realizar todos los actos tendentes a la conservación de su derecho. Podrá incluso exigir el pago del cheque, prestando la caución que fije el Juez, o la consignación judicial del importe de aquél.

Por todo lo expuesto, al amparo de los arts. 132 y ss. LJV, y del art. 548 del Código de Comercio,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria; previa publicación en el Boletín Oficial del Estado y en un periódico de gran circulación en la Comunidad de [COMPLETAR], y previa convocatoria de comparecencia ante el Letrado de la Administración de Justicia prevista en el art. 135 LJV, con citación de la entidad [COMPLETAR], y tras los trámites correspondientes, acuerde la suspensión de la obligación de pago y, transcurrido el plazo legal, se dicte resolución autorizando a mi representado al cobro de su crédito en la fecha de vencimiento.

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado

	Firma de Procurador

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito, el art. 133.3 LJV establece como preceptiva la intervención de Abogado y Procurador para la solicitud en análisis.
