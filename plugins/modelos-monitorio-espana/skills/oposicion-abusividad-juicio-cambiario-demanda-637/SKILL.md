---
name: oposicion-abusividad-juicio-cambiario-demanda-637
description: "Redacta el escrito «Oposición por abusividad al juicio cambiario: demanda» (formulario 637 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición por abusividad al juicio cambiario: demanda

> Formulario 0637 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (4 veces)
- [ ] NÚMERO
- [ ] LOCALIDAD (2 veces)
- [ ] IMPORTE (4 veces)
- [ ] Nº
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…rado de la Administración de Justicia de»; «…de»; «…de [COMPLETAR] de»; «…de [LOCALIDAD] de»; «…de»; «…de [COMPLETAR] de»; «…rcantil formalizado entre las partes con»; «…tereses, aplicándose el interés fijo del»; «…ostas al demandante del juicio cambiario»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 824 de la LEC
- art. 517 LEC
- art. 824 LEC
- artículo 94.2 de la Ley 19/1985
- arts. 826 y 394 LEC
- art. 826 de la LEC
- Real Decreto Legislativo 1/2007

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

### Formulario 0637 · Oposición por abusividad al juicio cambiario: demanda

- Año del modelo: 2015
- Revisión 17-11-2026: 24 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario revisado conforme a la LO 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia

D. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en representación de [NOMBRE DEL REPRESENTADO/A], según resulta de la designación apud acta otorgada ante el Letrado de la Administración de Justicia de [COMPLETAR] que acompaño, ante el Tribunal y como mejor proceda en Derecho DIGO:

1) Que en fecha [FECHA] de [COMPLETAR] de [COMPLETAR] mi representado ha sido requerido de pago en el juicio cambiario seguido ante ese Tribunal con el número [NÚMERO] a instancias de [LOCALIDAD] en virtud de pagaré de fecha [FECHA] de [LOCALIDAD] de [COMPLETAR] en reclamación de [IMPORTE] euros.

2) Que, al amparo de lo establecido en el artículo 824 de la LEC, formulo DEMANDA DE OPOSICIÓN AL JUICIO CAMBIARIO en base a los siguientes

HECHOS

La demanda de juicio cambiario interpuesta por la actora se funda en el pagaré que acompaña por importe de [IMPORTE] euros de principal e intereses ordinarios, solicitando el pago de los intereses de demora devengados desde el día de la presentación al pago del pagaré que se ejecuta, hasta el completo pago de las cantidades reclamadas mediante el presente procedimiento;

La oposición que formulamos se funda en que el pagaré en cuestión documenta la deuda derivada del contrato de préstamo de fecha [FECHA] de [COMPLETAR] de [COMPLETAR], y fue firmado en blanco por mi representado, aplicando la entidad demandante una cláusula abusiva como se expondrá seguidamente.

El pagaré objeto de este juicio cambiario trae causa del contrato de préstamo mercantil formalizado entre las partes con [COMPLETAR], bajo la denominación “contrato de préstamo formalizado con pagaré”, que se acompaña como documento número 1 del índice electrónico, y con vencimiento previsto para el día [FECHA], por importe de un principal de [IMPORTE] euros. En el citado préstamo se pactó que la deuda se satisfaría mediante un pago de cuotas de [IMPORTE] euros mensuales, comprensivos de capital e intereses, aplicándose el interés fijo del [COMPLETAR] % nominal anual.

En las condiciones generales se contemplaba como cláusula núm. [Nº], del siguiente tenor: ”ambas partes convienen la incorporación de las obligaciones de devolución del capital y pago de intereses que, para la parte prestataria y los fiadores, se derivan de este contrato a un pagaré emitido por la parte prestataria con el aval de los fiadores de este préstamo como garantía de devolución. El pagaré se emite en esta fecha, a la vista y se establece un término de presentación al cobro no superior a la duración de este préstamo más 12 meses”.

Al efecto, mi representado firmó el pagaré ahora presentado, en blanco, que ulteriormente ha sido rellenado unilateralmente por la entidad demandante.

Se formula oposición al entender que la formalización del pagaré objeto de esta demanda a la vez que se formaliza el contrato de préstamo a favor de la entidad demandante, quedando esta como legítima tenedora del mismo para garantía del cumplimiento de aquel negocio, es totalmente abusiva.

La STS de Pleno de 12 de septiembre de 2014, rec. 1438/2013, así lo indica al afirmar que “La condición general de los contratos de préstamo concertados con consumidores, en la que se prevea la firma por el prestatario (y en su caso por fiador) de un pagaré, en garantía de aquel, en el que el importe por el que se presentará la demanda de juicio cambiario es complementado por el prestamista con base a la liquidación realizada unilateralmente por él, es abusiva y, por tanto, nula, no pudiendo ser tenida por incorporada al contrato de préstamo, y, por ende, conlleva la ineficacia de la declaración cambiaria”.

El Tribunal Supremo afirma que esta cláusula es abusiva pues se inserta en documento privado, no constitutivo de título ejecutivo del art. 517 LEC por ausencia de intervención de fedatario público, otorgándose al banco una mejora sustancial de su posición jurídica frente al consumidor, pues se le permite el acceso a un proceso privilegiado para el cobro de su crédito, eludiéndose el proceso de ejecución de título no judicial en el que la conclusión del mismo y la liquidación es controlada por el fedatario público, sin que existan contrapartidas sustanciales para el consumidor; se trata de una cláusula predispuesta que si bien abarata costes, también priva al consumidor de información, asesoramiento previo, control de la legalidad, fehaciencia y seguridad jurídica, que son funciones que llevan a cabo los notarios. Asimismo, se impide al tribunal el control de oficio de las cláusulas abusivas que pudiera contener el contrato de préstamo, se impide la contradicción del demandado cambiario, pues difícilmente podrá oponer la excepción de complementación abusiva del pagaré, al desconocer en qué términos ha hecho la liquidación el acreedor; y dicha cláusula invierte la carga de la prueba, por lo que, en definitiva, la utilización de esta condición general permite a la entidad prestamista el acceso a un proceso privilegiado que comienza con un embargo cautelar sin necesidad de oír al demandado y sin que tenga que prestar caución ni justificar el periculum in mora, con base en un contrato que requiere una previa liquidación para determinar la cantidad adeudada en un momento concreto.

Por todo ello, se solicita la estimación de la oposición cambiaria con base en el carácter abusivo tanto del pagaré en blanco librado en garantía de un préstamo al consumo como de este contrato por las razones expuestas, de acuerdo a la normativa de protección de consumidores que se expresará en los fundamentos de esta demanda.

FUNDAMENTOS DE DERECHO

Competencia

Corresponde al Tribunal al que me dirijo al ser el que tramita el juicio cambiario que se sigue frente a mi principal que está domiciliado en este partido judicial.

Fondo

El art. 824 LEC en relación con el artículo 10 y 20.1 b) del Real Decreto Legislativo 1/2007, de 16 de noviembre, por el que se aprueba el texto refundido de la Ley General para la Defensa de los Consumidores y Usuarios, y del artículo 67.2 en relación con el artículo 94.2 de la Ley 19/1985, de 16 de julio, Cambiaria y del Cheque, siendo de aplicación la doctrina jurisprudencial de la Sala Primera del Tribunal Supremo expresada en las SSTS 12 de septiembre de 2014, rec. 1460/2013 y 11 de noviembre de 2015, rec. 102/2014 en los siguientes términos: “La condición general de los contratos de préstamo concertados con consumidores, en la que se prevea la firma por el prestatario (y en su caso por fiador) de un pagaré, en garantía de aquel, en el que el importe por el que se presentará la demanda de juicio cambiario es complementado por el prestamista con base a la liquidación realizada unilateralmente por él, es abusiva y, por tanto, nula, no pudiendo ser tenida por incorporada al contrato de préstamo, y, por ende, conlleva la ineficacia de la declaración cambiaria”.

Costas

Se solicita su imposición al demandante del presente juicio cambiario en el que se formula oposición con fundamento en los arts. 826 y 394 LEC.

En base a lo anterior,

SUPLICO AL TRIBUNAL: que tenga por presentado el presente escrito y por formulada oposición cambiaria frente al requerimiento de pago que se efectuó frente a mi principal y tras la pertinente tramitación, se solicita se dicte sentencia por la que estimando la presente demanda de oposición cambiaria se deje sin efecto lo acordado en el presente juicio cambiario y las medidas en él fijadas. Todo ello con imposición de costas al demandante del juicio cambiario [COMPLETAR].

OTROSÍ DIGO que, conforme a lo prevenido en el art. 826 de la LEC, solicito la celebración de vista, al ser necesaria para dirimir la controversia fáctica planteada en esta oposición sobre el carácter abusivo de las cláusulas insertas en el contrato de préstamo del que trae causa el pagaré.

Por lo que

SUPLICO AL TRIBUNAL que acuerde de conformidad.

[NOMBRE Y APELLIDOS], a [DÍA] de [MES] de [AÑO]

========================================================================
