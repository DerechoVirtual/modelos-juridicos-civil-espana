---
name: monitorio-intereses-moratorios-ya-liquidados-880
description: "Redacta el escrito «Monitorio con intereses moratorios ya liquidados» (formulario 880 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Monitorio con intereses moratorios ya liquidados

> Formulario 0880 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] NÚMERO (6 veces)
- [ ] COLEGIO
- [ ] NIF
- [ ] CALLE (2 veces)
- [ ] Nº
- [ ] TELÉFONO
- [ ] IMPORTE (6 veces)
- [ ] FECHA
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…sto PROCESO MONITORIO contra la sociedad»; «…omiciliada en C/ [CALLE] n.º [NÚMERO] de»; «…erto al público bajo el nombre comercial»; «…sito en la C/ [CALLE] n.º [NÚMERO] de»; «…de teléfono [TELÉFONO] y de fax»; «…ue acompañan a la petición. Con fecha de»; «…mi mandante vendió a la sociedad»; «…de su actividad mercantil, concretamente»; «…La mercantil»; «…al cobro de un recibo con vencimiento al»; «…rajudicial. En este sentido, se acudió a»; «…ente identificado al deudor, la sociedad»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 812, 813 y 814 de la LEC
- art. 814 de la LEC
- arts. 812 y 815 de la LEC
- art. 5 de la Ley Orgánica 1/2025
- artículo 2 de la Ley 10/2012
- Ley 3/2004

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

### Formulario 0880 · Monitorio con intereses moratorios ya liquidados

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 40 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma orgánica y procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: No existe «Tribunal de Instancia Decano» (DT 3.ª LO 1/2025). Si el asunto es de familia, Sección de Familia, Infancia y Capacidad; en partidos sin Sección Civil separada, Sección Única, de Civil y de Instrucción. Fuente: LO 1/2025 DT 3.ª (los jueces decanos pasan a la Presidencia del TI) y LOPJ arts. 84.1, 84.3 y 166 (BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante poder notarial que acompaño rogando me sea devuelto una vez testimoniado en autos, ante el Tribunal comparezco bajo la dirección del Letrado D./Dña. [NOMBRE Y APELLIDOS], Colegiado n.º [NÚMERO] del Ilustre Colegio de Abogados de [COLEGIO] y como mejor proceda en Derecho DIGO:

Que mediante el presente escrito, y en nombre de mi representado, formulo PETICIÓN INICIAL mediante la que insto PROCESO MONITORIO contra la sociedad [COMPLETAR], SL, provista de CIF [NIF], domiciliada en C/ [CALLE] n.º [NÚMERO] de [COMPLETAR], quien también podrá ser citada en su establecimiento comercial abierto al público bajo el nombre comercial [COMPLETAR] sito en la C/ [CALLE] n.º [NÚMERO] de [COMPLETAR] provisto de n.º [Nº] de teléfono [TELÉFONO] y de fax [COMPLETAR], con objeto de que se requiera a dicha sociedad deudora para que en plazo legal pague a mi representado la cantidad de [IMPORTE] euros que le adeuda, según los siguientes

ANTECEDENTES DE HECHO

(En su caso, si en la circunscripción se hace presentación telemática)

Se presenta listado de documentos que acompañan a la petición.

Con fecha de [COMPLETAR] mi mandante vendió a la sociedad [COMPLETAR], SL géneros de los que habitualmente fabrica en su establecimiento en el marco de su actividad mercantil, concretamente [COMPLETAR], que fueron entregados en la expresada fecha, firmando el representante de la sociedad compradora, en señal de conformidad con la recepción de las mercaderías, el albarán de entrega que acompaño reseñado como documento n.º [NÚMERO] La mercantil [COMPLETAR], SL adquirió tales bienes con objeto de revenderlos con ánimo de lucro, en el desarrollo de su actividad mercantil ordinaria.

A la fecha de la compra mi poderdante entregó a la sociedad compradora la factura que acompaño reseñada como documento n.º [NÚMERO], por el precio de los bienes adquiridos, que ascendió a [IMPORTE] euros.

Para el pago de los géneros detallados en la factura antedicha las partes convinieron la puesta en circulación de un recibo por el importe de la factura con vencimiento al día [FECHA] y con domicilio de pago en la cuenta bancaria que indicó la sociedad compradora. Estas condiciones fueron expresamente documentadas y aceptadas por las partes en el propio albarán de entrega de los géneros.

En la fecha del vencimiento acordado el recibo fue presentado al cobro, resultando desatendido e impagado. Como documento n.º [NÚMERO] acompaño ejemplar original del mencionado recibo impagado, en el que consta el sello bancario acreditativo de su presentación al cobro.

La devolución del recibo ha ocasionado a mi mandante gastos por [IMPORTE] euros, como acredito con el justificante bancario de gastos de devolución que acompaño como documento n.º [Nº DE DOCUMENTO]

La contratación suscrita entre las partes para el suministro de los géneros es de naturaleza comercial, y responde a las respectivas actividades mercantiles que desarrollan ambas partes. Es de aplicación a esta relación la Ley 3/2004 de Medidas de Lucha contra la Morosidad en las operaciones Comerciales.

El medio de pago convenido entre las partes, tal y como consta en el albarán adjunto que suscribió el representante de la mercantil compradora, era el de presentación al cobro de un recibo con vencimiento al [COMPLETAR], por lo que a partir del día siguiente al de la obligación de pago y hasta la fecha inmediatamente anterior a esta petición inicial monitoria, se han generado los intereses de mora según los porcentajes establecidos por las Resoluciones de la Dirección General del Tesoro y Política Financiera que establecen los tipos aplicables a la previsión de la Ley 3/2004 de Medidas de Lucha Contra la Morosidad en las Operaciones Comerciales, de conformidad con el siguiente cuadro cronológico, en el que se reseña la fecha de la Orden de la Dirección General del Tesoro y Política Financiera con el porcentaje establecido para cada semestre natural:

Semestre	Resolución D.G.T.	Tipo	Inicio cómputo	Días	Importe	Interés
1.º /	/	/				 euros
2.º /	/	/				 euros
1.º /	/	/				 euros
2.º /	/	/				 euros
1.º /	/	/				 euros
/	/	/				 euros
					Total 	 euros

Ascienden los intereses moratorios derivados de la aplicación de la Ley 3/2004 al importe conjunto de [IMPORTE] euros.

Resulta de todo ello que la sociedad, SL adeuda a mi representado la suma conjunta de [IMPORTE] euros, correspondiente a principal de la factura que acompaño, gastos de devolución del recibo puesto en circulación para su pago e intereses moratorios legales liquidados.

Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

Competencia

Corresponde al Tribunal de Instancia del domicilio del deudor (Art. 813 de la LEC, en relación con lo dispuesto en el art. 85.1º LOPJ).

Postulación

Aunque no precisa esta petición inicial de proceso monitorio intervención de procurador ni abogado (Art. 814 de la LEC) esta parte comparece representada por Procurador y asistida de Letrado.

Amparo la petición en lo dispuesto en los arts. 812, 813 y 814 de la LEC.

A los efectos previstos en el art. 814 de la LEC se deja debidamente identificado al deudor, la sociedad [COMPLETAR], SL, y señalado el domicilio donde puede ser hallada.

Acompaño acreditación documental exigida en los arts. 812 y 815 de la LEC, consistente en [DESCRIBIR] (albarán de entrega, factura, recibo girado al cobro, justificante bancario de gastos por devolución).

La presente demanda cumple con los requisitos de procedibilidad exigidos por el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL: que tenga por presentado este escrito, documentos adjuntos y copias de todo ello, lo admita a trámite, teniendo por formulada, en nombre de D/Dña. [NOMBRE Y APELLIDOS], PETICIÓN INICIAL de promoción de PROCESO MONITORIO contra la sociedad [COMPLETAR], SL y en su virtud requiera el Letrado de la Administración de Justicia a dicha mercantil deudora para que en el plazo de veinte días pague a mi representado la cantidad de [IMPORTE] euros que le adeuda, bajo apercibimiento de que de no hacerlo se despachará ejecución contra sus bienes por la cantidad adeudada más los intereses de mora procesal pertinentes y costas de la ejecución, acordando además lo siguiente:

1.º Para el supuesto de que la mercantil deudora no pagare la suma reclamada y no formulare oposición en debida forma, dicte decreto el Letrado de la Administración de Justicia dando por terminado el proceso monitorio y dándonos traslado para formular despacho de ejecución.

2.º OPCIONES:

a) En asuntos cuya cuantía no supere 15.000 euros: Para el supuesto de que el deudor presentase escrito de oposición en plazo legal, dicte decreto el Letrado de la Administración de Justicia dando por terminado este proceso y acordando seguir los trámites del juicio verbal con traslado a esta parte para su contestación.

b) En asuntos cuya cuantía supere 15.000 euros: Para el supuesto de que el deudor presentase escrito de oposición en plazo legal, acuerde darme traslado del mismo para formular demanda en el plazo de un mes legalmente previsto.

Es Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

(Para personas jurídicas y cuantía superior a 2.000 euros) OTROSÍ DIGO: Que acompaño modelo 696 de autoliquidación de la tasa judicial, según exige el artículo 2 de la Ley 10/2012, de 20 de noviembre y la Orden que regula los modelos de autoliquidación.

NUEVAMENTE SUPLICO: Que tenga por cumplimentado este trámite por ser justicia que pido en mismo lugar y fecha.

========================================================================
