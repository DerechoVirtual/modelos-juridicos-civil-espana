---
name: demanda-modificacion-extinguir-pension-alimentos-368
description: "Redacta el escrito «Demanda de modificación para extinguir la pensión de alimentos» (formulario 368 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de modificación para extinguir la pensión de alimentos

> Formulario 0368 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] COLEGIO
- [ ] LOCALIDAD (3 veces)
- [ ] CALLE
- [ ] Nº (5 veces)
- [ ] AÑO
- [ ] FECHA (3 veces)
- [ ] IMPORTE (2 veces)
- [ ] NÚMERO
- [ ] DESCRIBIR
- [ ] STS de 5 de Noviembre de 1984 
- [ ] DNI/NIE
- [ ] LUGAR
- [ ] Otros 17 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…nales, en nombre y representación de Don»; «…CIÓN DE MEDIDAS DEFINITIVAS, contra Doña»; «…, cuyo domicilio es»; «…os del hijo común entonces menor de edad»; «…, a cargo de Don»; «…. TERCERO.- El mencionado hijo»; «…rabajando por cuenta ajena en la empresa»; «…CUARTO.- Por lo expuesto, acreditado que»; «…entencia. Se acompaña documentos números»; «…a»; «…rajudicial. En este sentido, se acudió a»; «…ir en el procedimiento corresponde a Don»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 775.1 LEC
- arts. 81, 86, 90 y 91CCiv
- art. 770 LEC
- art. 775.2 LEC
- art. 437.1 LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 93 CCiv
- art. 394 LEC
- art. 332 LEC
- Ley 15/2005

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

### Formulario 0368 · Demanda de modificación para extinguir la pensión de alimentos

- Año del modelo: 2019
- Revisión 17-11-2026: 39 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda en proceso contencioso de modificación de medidas definitivas, solicitando la extinción de la pensión alimenticia por mayoría de edad del hijo, en régimen de Derecho común.

Adaptado a la LO 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia

AL TRIBUNAL DE INSTANCIA DE [SEDE]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de Don [COMPLETAR], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], y bajo la dirección técnica de D./Dña. [NOMBRE Y APELLIDOS], Letrado/a ejerciente en el Iltre. Colegio de Abogados de [COLEGIO], con despacho abierto en [LOCALIDAD], calle [CALLE], ante el Tribunal comparezco y, como mejor proceda en Derecho, DIGO:

Que mediante el presente escrito, formulo DEMANDA DE MODIFICACIÓN DE MEDIDAS DEFINITIVAS, contra Doña [COMPLETAR], cuyo domicilio es [COMPLETAR], basándola en los siguientes hechos y fundamentos de derecho:

HECHOS

PRIMERO.- Que en los autos de separación/divorcio/adopción de medidas paterno-filiales, registrados en este Tribunal bajo el nº [Nº]/[AÑO], recayó sentencia, el día [FECHA], en cuyo fallo o parte dispositiva se adoptaba como medida definitiva, entre otras, la fijación de una cantidad de [IMPORTE] euros mensuales para alimentos del hijo común entonces menor de edad [COMPLETAR], a cargo de Don [COMPLETAR].

SEGUNDO.- Dicha sentencia, que es firme y ejecutoria, no ha sido modificada por ninguna otra resolución firme. Se acompaña testimonio de la sentencia como doc. nº [NÚMERO].

TERCERO.- El mencionado hijo [COMPLETAR], que tiene en la actualidad [Nº] años, por consiguiente mayor de edad, se encuentra desde hace [Nº] meses trabajando por cuenta ajena en la empresa [COMPLETAR], sita en [LOCALIDAD] de esta ciudad, con contrato indefinido, obteniendo unos ingresos mensuales de [IMPORTE] euros.

CUARTO.- Por lo expuesto, acreditado que [COMPLETAR] goza de plena independencia económica, transcurridos [Nº] años desde que se fijaron los alimentos, y superada ampliamente la mayoría de edad, es por lo que solicitamos que se suprima la pensión alimenticia acordada en su favor, en la citada sentencia.

Se acompaña documentos números [COMPLETAR] a [COMPLETAR] como prueba de los anteriores extremos, consistentes en [DESCRIBIR]

QUINTO.- Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA.

Conforme a lo establecido por el art. 775.1 LEC, es competente para conocer del presente procedimiento el Tribunal al que me dirijo, por ser el que acordó la medida que se quiere modificar.

II.- LEGITIMACIÓN.

La legitimación activa y pasiva para intervenir en el procedimiento corresponde a Don [COMPLETAR] y a Doña [COMPLETAR] (arts. 81, 86, 90 y 91CCiv), al ser las partes del divorcio del que deriva la modificación de medidas.

Así, es reiterado el criterio jurisprudencial que considera como único legitimado para intervenir en el proceso sobre pensión alimenticia de un hijo mayor de edad al progenitor con quien convive, al ser quien asume los gastos del hijo; el cual no siendo parte en el proceso matrimonial, no puede serlo en el de modificación posterior, por citar alguna, SAP León de 29 de noviembre de 2001, Rec. 349/2001, en la que se señala:

"Plantea la apelada, que el recurrente debía haber dirigido su demanda no solo frente a la esposa, sino también frente a su propio hijo; y al no haberlo hecho así, se ha incurrido en una falta de litisconsorcio pasivo necesario que no permite la supresión de una pensión de alimentos establecida a favor de un hijo mayor de edad, sin haberle traído al procedimiento para que pueda defenderse. Sin embargo, en algunas ocasiones ya hemos dicho que en estos procedimientos no pueden contemplarse otro tipo de relaciones que las que vinculan a uno y a otro cónyuge en función de los hijos comunes, sean o no mayores de edad; y aunque pudiera parecer tolerante una intervención coadyudante o adhesiva de los hijos mayores de edad en alguno de los puntos concretos que se analizan en estos procedimientos, no se constituye su intervención en necesaria, por lo que no puede apreciarse la excepción de litisconsorcio pasivo necesario"

En este sentido, por verse afectada por la sentencia que se dicte en dicho proceso, se indica como coadyuvante a [COMPLETAR], con domicilio en [LOCALIDAD], a los efectos de los arts. 13 y ss. LEC.

III.- PROCEDIMIENTO.

La modificación de las medidas definitivas tiene asignado el procedimiento previsto en el art. 770 LEC, o lo que es lo mismo, los trámites del procedimiento principal de separación o divorcio de conformidad con la nueva redacción del art. 775.2 LEC dada por la Ley 15/2005, de 8 de julio, dado que no son de mutuo acuerdo o propuestas por un cónyuge con el consentimiento del otro.

IV.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 en relación con el art. 437.1 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

V.- FUNDAMENTOS DE DERECHO MATERIALES O SOBRE EL FONDO DEL ASUNTO.

La modificación de medidas solicitada tiene su amparo legal en el art. 91 "in fine" CCiv, esto es, en una alteración de las circunstancias fácticas sobre las que se proyectó la fijación de las concretas medidas acordadas anteriormente con motivo de la separación/el divorcio/la adopción de medidas paterno-filiales, prevención que es presupuesto de este proceso, según la mención explícita del art. 775.1 LEC; y dicha alteración ha de calificarse como sustancial, es decir de importancia, afectando no a aspectos secundarios o accesorios.

En el presente caso, consta acreditado que el hijo ha alcanzado la mayoría de edad y desempeña un trabajo remunerado desde hace [Nº] meses, y así resulta de su contrato de trabajo. En estas circunstancias procede dejar sin efecto la pensión a su favor, por quedar probada la falta de necesidad de la misma. En este sentido se manifiesta, entre otras, la SAP Madrid de 579/2007, de 26 de abril, Rec. 108/2007- que señala que "la obligación de los padres de prestar alimentos carece de justificación para los hijos mayores de edad cuando éstos han alcanzado la posibilidad de proveer por sí mismos sus necesidades; posibilidad, que si bien no se identifica con una mera capacidad subjetiva de ejercer una profesión u oficio, sino que es preciso se trate de una posibilidad real y concreta en relación con las circunstancias concurrentes [STS de 5 de Noviembre de 1984 ], se viene entendiendo concurre cuando ya se ha producido su incorporación al mundo del trabajo".

De cuanto antecede, y a la vista de los hechos, se desprende inequívocamente la procedencia de la modificación de medidas solicitada al haberse producido una verdadera alteración de lo sustancial, esto es, desempeñar trabajo remunerado el hijo mayor beneficiario de la pensión alimenticia, y por ello, procede la supresión de dicha pensión establecida en su favor.

En definitiva, de cuanto antecede se desprende inequívocamente la procedencia de la modificación de medidas solicitada que ya no se dan los presupuestos del art. 93 CCiv que en su día justificaron el reconocimiento de la referida prestación alimenticia, al haberse producido una verdadera alteración de lo sustancial, esto es, desempeñar trabajo remunerado el hijo mayor beneficiario de la pensión alimenticia, por lo que procede la supresión de dicha pensión establecida en su favor, quedando siempre a salvo por parte del hijo, si se dieran las condiciones, la posibilidad de reclamar alimentos, en nombre propio, en los términos reconocidos por los arts. 142 y ss. CCiv, en el procedimiento correspondiente.

VI.- COSTAS.

No hay razón para inaplicar el principio del vencimiento en punto a costas procesales, en armonía con el art. 394 LEC, a fin de que esta parte salga indemne de que se le reconozca su derecho frente a la resistencia de la demandada.

En su virtud,

SUPLICO AL TRIBUNAL

que, teniendo por presentado este escrito junto con los documentos que a él se acompañan, se sirva admitirlo y tener por solicitada, en la representación que ostento DEMANDA DE MODIFICACIÓN DE MEDIDAS contra Doña [COMPLETAR], y previos los trámites legales oportunos, incluida la comunicación a la parte coadyuvante del presente proceso, por el tribunal se dicte sentencia declarando extinguida la pensión alimenticia fijada en sentencia de separación matrimonial/divorcio/adopción de medidas paterno-filiales, de fecha [FECHA], del hijo mayor de edad [COMPLETAR], con expresa condena en costas a la parte demandada.

PRIMER OTROSÍ DIGO: Interesa al derecho de esta parte, al amparo del art. 332 LEC, que por el Letrado de la Administración de Justicia se libre atento oficio a la TESORERÍA GENERAL DE LA SEGURIDAD SOCIAL para que se informe de la vida laboral de [COMPLETAR], con DNI nº [DNI/NIE]. Todo ello sin perjuicio de volver a solicitar la práctica de la prueba en el momento procesal oportuno o de ampliar los medios ya solicitados.

SUPLICO AL TRIBUNAL: Tenga por hechas las anteriores manifestaciones a los efectos legales oportunos.

Por ser de justicia que solicito en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a
