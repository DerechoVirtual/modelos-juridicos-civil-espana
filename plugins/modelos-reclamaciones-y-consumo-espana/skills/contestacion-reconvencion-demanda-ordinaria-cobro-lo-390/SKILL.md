---
name: contestacion-reconvencion-demanda-ordinaria-cobro-lo-390
description: "Redacta el escrito «Contestación y reconvención en demanda ordinaria por cobro de lo indebido» (formulario 390 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación y reconvención en demanda ordinaria por cobro de lo indebido

> Formulario 0390 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD (3 veces)
- [ ] Nº DE DOCUMENTO
- [ ] COLEGIO
- [ ] ÓRGANO
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] FECHA (5 veces)
- [ ] IMPORTE (2 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] LUGAR (2 veces)
- [ ] Otros 17 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, plaza n.º»; «…D./Doña»; «…el Ilustre Colegio de Procurador/a.es de»; «…, con domicilio en [LOCALIDAD] y»; «…, y bajo la dirección letrada de D/Doña»; «…IDAD por importe, presentada por D./Doña»; «…, con la empresa»; «…que se acompañan como documentos núms. y»; «…ación reclamando como documentos núms. a»; «…onstar en el escrito de contestación, el»; «…spondientes al periodo de facturación de»; «…a»; …

## Elecciones que hay que hacer

- D./Doña / la mercantil
- NIF / CIF

## Párrafos opcionales (2)

Inclúyelos solo si encajan en los hechos:

- PRIMER OTROSI DIGO, que siendo el poder que acompaño, general para pleitos y necesitándolo para otros usos pro…
- TERCER OTROSI DIGO, que esta parte manifiesta su voluntad, a los efectos del art. 231 de la LEC, de cumplir, r…

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 1156 CC
- artículo 394 LEC
- artículo 406 LEC
- artículo 7.1 LEC
- artículo 10 LEC
- artículo 409 LEC
- artículo 1895 CC
- artículo 1896 CC
- artículo 1900 CC
- artículo 1901 CC
- art. 231 de la LEC

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

### Formulario 0390 · Contestación y reconvención en demanda ordinaria por cobro de lo indebido

- Año del modelo: 2019
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 7 desplegables convertidos en elección en blanco; 2 párrafos opcionales señalados; 32 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Contestación a la demanda de juicio ordinario al Tribunal de Instancia, sobre la reclamación de cantidad y reconvención por cobro de lo indebido, solicitando la obligación de la demandada de restituir las cantidades indebidamente cobradas, incrementados por el interés legal desde el cobro de la primera factura.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [COMPLETAR]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Doña [COMPLETAR], Procurador/a./a de los Tribunales, Coleg. del Ilustre Colegio de Procurador/a.es de [COMPLETAR], actuando en nombre y representación de [ELEGIR: D./Doña / la mercantil], con domicilio en [LOCALIDAD] y [COMPLETAR], como acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], y bajo la dirección letrada de D/Doña [COMPLETAR], Letrado/a del Ilustre Colegio de Abogados de [COLEGIO], ante el Tribunal comparece y como mejor proceda en Derecho DICE

Que habiendo sido notificado y emplazado mediante [ÓRGANO], por medio del presente escrito, vengo a formular CONTESTACIÓN A LA DEMANDA DE JUICIO ORDINARIO SOBRE RECLAMACIÓN DE CANTIDAD por importe, presentada por D./Doña [COMPLETAR], Procurador/a./a de los Tribunales, en nombre y representación de
D./Doña [NOMBRE Y APELLIDOS]
la mercantil
  en base a los siguientes

HECHOS

PRELIMINAR.-

Esta parte niega los hechos alegados en la demanda, excepto los que expresamente se admitan en el presente escrito

PRIMERO.- Conforme con el correlativo de la demanda en relación a la existencia de un contrato de suministros firmado por mi mandante, con fecha [FECHA], con la empresa [COMPLETAR].

SEGUNDO.- Disconforme con correlativo de la demanda. A pesar de la existencia de dicho contrato, con fecha [FECHA] se procedió a comunicar de manera fehaciente el cambio de titular, así como el nuevo número de CCC donde pasarían a ser domiciliados a partir de fecha [FECHA] los nuevos recibos emitidos. Se acredita tal extremo mediante solicitud de cambio de titular y acuse de recibo, que se acompañan como documentos núms. y [COMPLETAR].

TERCERO.- A consecuencia de ello, la empresa suministradora, a pesar de alegar la existencia de una deuda a nombre de mi mandante por importe de [IMPORTE], correspondiente al periodo de facturación, se está enriqueciendo sin causa alguna puesto que dichos recibos se están cobrando por duplicado, al anterior titular, la demandada, que ya no es cliente de la empresa, ni hace consumo alguno y al nuevo titular, verdadero obligado al pago de los mismos. Se acompaña como documento acreditativo de tal extremo las facturas emitidas a nombre de mi mandante y a nombre del nuevo titular correspondientes al periodo de facturación reclamando como documentos núms. a [COMPLETAR].

A los anteriores le son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Primero.- Conforme a los correlativos a la demanda sobre jurisdicción, competencia oponiéndose al resto de los alegados por no ser de aplicación o serlo "a sensu contrario"

Segundo.- Conforme con el correlativo de la demanda sobre capacidad y legitimación.

Tercero.- Conforme con el correlativo sobre representación y defensa, así como procedimiento.-

Cuarto.- Oponiéndonos a los fundamentos jurídico-materiales alegados en relación al fondo del asunto por no ser de aplicación o ser de aplicación a sensu contrario

Los motivos alegados en relación a la obligación de pago en virtud de contrato firmado por ambas partes, no son tales, puesto que por parte de mi mandante se ha cumplido con el pago, al estar los recibos domiciliados sin proceder al cambio de titular solicitado. El artículo 1156 CC dispone que las obligaciones se extinguirán por el pago o cumplimiento.

Quinto.- Costas.-

Se condene el actor a las costas de la primera instancia por la temeridad y mala fe conforme el artículo 394 LEC.

Por lo expuesto

SUPLICA AL TRIBUNAL,

que me tenga por personado y comparecido en tiempo y forma en representación de [NOMBRE DEL REPRESENTADO/A]
D./Doña [NOMBRE Y APELLIDOS]
la mercantil
  y por CONTESTADA LA DEMANDA, y tras el curso legal, se dicte sentencia por la que se desestime la demanda interpuesta y condene a la actora al pago de las costas ocasionadas en la instancia.

Por ser Justicia que pide en [LUGAR], a [FECHA].

OTROSI DIGO, que de conformidad con lo prevenido en el artículo 406 LEC por medio del presente escrito vengo a formular DEMANDA RECONVENCIONAL POR COBRO DE LO INDEBIDO por importe de frente a [ELEGIR: D./Doña / la mercantil], según lo establecido en los artículos 1895 y ss del Código Civil, con domicilio en [LOCALIDAD] y
NIF
CIF
  en base a los siguientes

HECHOS

PRIMERO.- Como se afirma en la demanda, existe un contrato de suministro por el cual el demandado reconvencional venía obligado a abonar las facturas emitidas por el suministro prestado.

SEGUNDO.- Igualmente, como se ha hecho constar en el escrito de contestación, el [COMPLETAR] se procedió a solicitar el cambio de titular, facilitando los datos de identificación y número de cuenta donde proceder a domiciliar los nuevos recibos que se emitiesen a partir de esa fecha.

TERCERO.- A pesar de ello, la demandante, ha seguido emitiendo facturas por importe de [IMPORTE], correspondientes al periodo de facturación de [COMPLETAR] a [COMPLETAR] de [COMPLETAR], y que han sido abonadas por la demandada reconvencional en el error de corresponder a periodos anteriores.

CUARTO.- Como se ha hecho constar igualmente en la contestación a la demanda, puesta mi representada en contacto con el actual titular, éste, a su vez, está abonando también las facturas emitidas correspondientes al mismo periodo reclamado, por lo cual mi mandante cae en la cuenta del error existente en el pago así como el que está abonando sin causa unas facturas que no le corresponden.

QUINTO.- Puesta mi mandante en contacto con la empresa suministradora, nuevamente le indican que dichos cobros corresponden a regularizaciones anteriores y, por tanto, viene igualmente obligada al pago de los mismos.

Aportadas las facturas correspondientes a los pagos reclamados, se puede comprobar que los cobros se corresponden al consumo del periodo de facturación idénticamente cobrado al actual titular del contrato, correspondiente al consumo realizado, por lo que el cobro realizado a mi mandante es indebido, debiendo proceder a la restitución del mismo.

SEXTO.- Existe mala fe por parte de la actora principal desde el mismo momento en el que no sólo está cobrando por duplicado, al nuevo titular y a mi mandante como antigua titular, sino que puesto en conocimiento de ellos, intentan enmascarar el verdadero origen de las facturas emitidas.

A los anteriores hechos, le son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Primero.- Jurisdicción y competencia.

La jurisdicción y competencia y para el conocimiento de la demanda reconvencional corresponde al mismo juez que esté conociendo de la demanda principal.

Segundo.- Capacidad y legitimación

Las partes, al ser las mismas que las de la demanda principal, tienen capacidad para ser parte, conforme dispone el artículo 6.1.1º LEC, respecto a la actora, y 6.1.1º o 6.1.3 LEC respecto a la demandada.

Igualmente tiene la actora capacidad procesal según lo dispuesto en el artículo 7.1 LEC.

Respecto a la legitimación, se encuentra invertida, correspondiendo:

a) Activa: Corresponde a [ELEGIR: D./Doña / la mercantil], con [ELEGIR: NIF / CIF], en su calidad de titular de la relación jurídica u objeto litigioso conforme al artículo 10 LEC como demandante reconvencional.
b) Pasiva: Corresponde a [COMPLETAR]
D./Doña [NOMBRE Y APELLIDOS]
la mercantil
  con [ELEGIR: NIF / CIF], en su calidad de titular de la relación jurídica u objeto litigioso conforme al artículo 10 LEC, como demandada reconvencional.

Tercero.- Procedimiento y cuantía

Conforme a lo dispuesto en el artículo 409 LEC, la reconvención se sustanciará y resolverá al propio tiempo y en la misma forma que la cuestión principal debiendo ser resuelta con éste en la sentencia definitiva

La cuantía de la reconvención se fija en [COMPLETAR].

Cuarto.- Fondo del asunto

Será de aplicación en artículo 1895 CC en relación al cobro de lo indebido, que establece que cuando se recibe alguna cosa que no había derecho a cobrar, y que por error ha sido indebidamente entregada, surge la obligación de restituirla. Concurren todos y cada uno de los requisitos exigidos jurisprudencialmente (STS 534/2010, de 30 de julio) la existencia del negocio jurídico que constituye el cobro o pago de lo indebido son tres:

• El pago efectivo realizado por el presunto deudor con la finalidad de extinguir la deuda, "animus solvendi", entendido como la entrega de cuerpo cierto in genere. El animus solvendi no es otra cosa que la voluntad del deudor de pagar.
• La inexistencia de obligación entre el que paga y el que recibe, denominado indebitum, y, por consiguiente, la falta de causa en el pago, existiendo un indebitum ex persona, a pesar de existir un vínculo jurídico que se habría generado a partir del cambio del titular, el deudor pasa a ser, precisamente a consecuencia del mismo, sujeto distinto a mi mandante.
• Erro por parte del que hizo el pago, mi mandante, en la errónea creencia de estar abonando las facturas abonadas, ha abonado durante meses las mismas, con el ánimo de extinguir la deuda.

Resulta de aplicación el párrafo primero del artículo 1896 CC siendo procedente el abono del interés legal ante la mala fe del que recibe el pago, debiendo fijarse el diez a quo desde el mismo día en que se emite la primera factura indebida, es presentada al cobro, y en consecuencia es abonada.

En relación a la prueba, conforme dispone el artículo 1900 CC, corresponde al que hubiera hecho el pago acreditarlo, así como el error alegado. En este sentido, se ha acredita el pago realizado mediante las facturas presentadas y los movimientos bancarios de la cuenta titularidad de mi mandante. Y a pesar de acreditar el error pagado, en aplicación al artículo 1901 CC, se establece la presunción del error al haberse realizado un pago que no es debido, que no puede ser desvirtuado por la mera alegación de liberalidad o por otra causa justa.

Quinto.- Costas

Procede la condena en costas de la parte demandada en esta reconvención por el principio cuasiobjetivo de vencimiento al amparo del artículo 394 LEC, al ver vistas, ésta, rechazadas todas sus pretensiones, sin que exista duda, de hecho o derecho, alguna.

Por lo expuesto

SUPLICO AL TRIBUNAL,

que tenga por presentado este escrito con los documentos que se acompañan, junto con sus copias, y por presentada DEMANDA DE RECONVENCIÓN POR COBRO DE LO INDEBIDO contra [ELEGIR: D./Doña / la mercantil], con domicilio en [LOCALIDAD] y [ELEGIR: NIF / CIF], lo admita y dé traslado de la misma al demandando, para que, en el plazo de veinte días, conteste a la misma, y tras el curso legal, se dicte sentencia por la que se DECLARE:

• Se declare la obligación de la demandada de restituir las cantidades indebidamente cobradas que asciende a [COMPLETAR], incrementados por el interés legal desde el cobro de la primera factura, que asciende a [COMPLETAR]. Todo ello con la imposición de costas a la parte demandada reconvencional.

Por ser Justicia que pide en [LUGAR], a [FECHA].

[OPCIONAL — incluir si procede]

PRIMER OTROSI DIGO, que siendo el poder que acompaño, general para pleitos y necesitándolo para otros usos procesales,

SUPLICO AL TRIBUNAL, que previo su inserción por copia en autos, acuerde su desglose y devolución a esta parte.

[OPCIONAL — incluir si procede]

TERCER OTROSI DIGO, que esta parte manifiesta su voluntad, a los efectos del art. 231 de la LEC, de cumplir, rigurosamente, los requisitos previstos en la LEC., y de subsanar cualquier defecto en que haya podido incurrir en este escrito de demanda.

SUPLICO AL TRIBUNAL que tenga por hecha la anterior manifestación a los efectos del art. 231 de la LEC.

Firma del Abogado	Firma del Procurador/a
