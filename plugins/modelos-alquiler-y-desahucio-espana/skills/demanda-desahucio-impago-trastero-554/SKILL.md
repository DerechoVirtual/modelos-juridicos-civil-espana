---
name: demanda-desahucio-impago-trastero-554
description: "Redacta el escrito «Demanda de desahucio por impago del trastero» (formulario 554 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de desahucio por impago del trastero

> Formulario 0554 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (8 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] COLEGIO
- [ ] Nº
- [ ] PROFESIÓN
- [ ] LOCALIDAD (2 veces)
- [ ] DNI/NIE
- [ ] NÚMERO (4 veces)
- [ ] ÓRGANO
- [ ] FECHA
- [ ] IMPORTE (3 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…con n.º [Nº] de colegiado»; «…situado en»; «…euros, y con una duración de»; «…el citado contrato. Desde el mes de»; «…rajudicial. En este sentido, se acudió a»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 438.5 y 6 de la LEC
- art. 438 de la LEC
- artículos 437.3 y 549.3 de la LEC
- art. 437.1 LEC
- art. 5 de la Ley Orgánica 1/2025
- artículo 1555.1 del Código Civil

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

### Formulario 0554 · Demanda de desahucio por impago del trastero

- Año del modelo: 2016
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 30 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (IMPORTE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Demanda de desahucio

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], en el que constan los datos personales de mi poderdante, ante el Tribunal comparezco bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], miembro del Ilte. Colegio de Abogados de [COLEGIO] con n.º [Nº] de colegiado [COMPLETAR] y como mejor proceda en derecho

DIGO.

Que mediante el presente escrito interpongo demanda a tramitar por el cauce del juicio verbal con las especialidades recogidas en el art. 438.5 y 6 de la LEC, en ejercicio de acción de desahucio por falta de pago, contra D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, de profesión [PROFESIÓN], domicilio en [LOCALIDAD] y DNI n.º [DNI/NIE], con base en los siguientes

HECHOS

 Se presenta listado de documentos que acompañan a la demanda.

D./Dña. [NOMBRE Y APELLIDOS] es propietario del cuarto trastero nº [NÚMERO] situado en [COMPLETAR], según acredito mediante [ÓRGANO]

En fecha [FECHA] el propietario suscribió contrato de arrendamiento de trastero con D./Dña. [NOMBRE Y APELLIDOS], con una renta mensual de [IMPORTE] euros, y con una duración de [COMPLETAR] Acredito estos extremos aportando como doc. n.º [NÚMERO] el citado contrato.

Desde el mes de [COMPLETAR] el demandado ha dejado de pagar la renta estipulada, adeudando a fecha de demanda la cantidad de [IMPORTE] euros, resultado de multiplicar la renta mensual vigente por el número de meses que no se ha liquidado la deuda.

No habiendo dado fruto los requerimientos practicados al demandado tendentes a evitar la vía judicial, doc. n.º [NÚMERO], finalmente nos vemos obligados a acudir al Tribunal en defensa de los derechos de mi representado.

Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

I.- JURISDICCIÓN Y COMPETENCIA .- Los artículos 21 y 22 de la Ley Orgánica del Poder Judicial consideran que la jurisdicción competente en esta materia es la española, y los artículos 45 y 52.1.7.º de la Ley de Enjuiciamiento Civil atribuyen la competencia al Tribunal al que nos dirigimos al ser éste el lugar donde se encuentra la finca.

II.- TRAMITACION .-

- Del cauce del juicio verbal con técnica monitoria: El artículo 437.4.3.ª [NOTA DE REVISIÓN: La acumulación en el verbal está en el art. 437.4 LEC. Fuente: LEC art. 437.4.3.ª (BOE-A-2000-323).], en concordancia con el artículo 71.2 de la Ley de Enjuiciamiento Civil permite la acumulación por el cauce del juicio verbal de acciones de reclamación de rentas o cantidades análogas vencidas y no pagadas, cualquiera que sea la cantidad reclamada, cuando se trate de juicios de desahucio de finca por falta de pago.

- Deben tenerse en cuenta, no obstante, las especialidades reguladas en los apartados 5 y 6 del art. 438 de la LEC, según las cuales el Letrado de la Administración de Justicia requerirá en el emplazamiento al demandando para que en el plazo de 10 días proceda a enervar si tiene derecho a ello, pagar y desalojar el inmueble, o formular oposición alegando sucintamente las razones por las que no procede el desahucio. Indicará igualmente en esta resolución la fecha de la eventual vista y la del lanzamiento, con apercibimiento de inmediato lanzamiento si no formulare oposición.

—De la ejecución directa si se dicta sentencia estimatoria o auto o decreto que ponga fin al procedimiento: Los artículos 437.3 y 549.3 de la LEC permiten solicitar en la demanda la ejecución directa del lanzamiento, y a tal fin en la resolución que se dicte citando a juicio se señalará ya día y hora para tal actuación, que se llevará a efecto en tal fecha.

—De la cuantía del pleito: La cuantía del procedimiento se fija en [IMPORTE] euros, en aplicación del artículos 251.3.ª y 9.ª y 252.2 de la Ley de Enjuiciamiento Civil, que afirma que si las acciones acumuladas son las de desahucio y reclamación de rentas o cantidades debidas la cuantía de la demanda vendrá determinada por la acción de mayor valor, es decir, o una anualidad de renta o el importe de la cuantía reclamada.

—Del cumplimiento de los requisitos de procedibilidad: La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 en relación con el art. 437.1 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

III.- LEGITIMACIÓN Y POSTULACIÓN .- La activa corresponde al propietario del inmueble y la pasiva al inquilino que no paga la renta en aplicación del artículo 10 de la Ley de Enjuiciamiento Civil por ser ambos los titulares de la relación jurídica de la que deriva la deuda.

De conformidad con lo dispuesto en la vigente Ley de Enjuiciamiento Civil, en concreto en su artículo 23.1 y 2, esta parte litiga representada por Procurador y bajo la dirección técnica de Letrado debidamente habilitados, siendo preceptiva la intervención de ambos, pese a no alcanzar la cuantía los 2.000 €, y ello porque el tipo de juicio no se determina por razón de la cuantía sino por razón de la materia, de conformidad con el artículo 250.1.1º de la Ley de Enjuiciamiento Civil.

IV.- FONDO DEL ASUNTO .-

Primero.- El artículo 1555.1 del Código Civil obliga al arrendatario a pagar el precio del arrendamiento en los términos convenidos, y el artículo 1569.2 del mismo texto faculta al arrendador a solicitar el desahucio judicial por no pagar el precio.

Segundo.- Artículo 1569.2 del Código Civil: el arrendador puede desahuciar judicialmente al arrendatario por no pagar el precio convenido.

Tercero.- Los artículos 22.4 y 439.3 de la Ley de Enjuiciamiento Civil exigen que en la demanda se haga constar la posibilidad o no de enervar la acción, tal y como esta parte ya ha puesto de manifiesto. El Tribunal deberá indicar al dar traslado de la demanda, según previenen los artículos 22.4 y 438.5 de la Ley de Enjuiciamiento Civil, si existe o no la posibilidad de enervación.

Cuarto.- Artículo 438.5 de la Ley de Enjuiciamiento Civil: En el requerimiento, se apercibirá al demandado de que en los diez días siguientes a esta notificación podrá desalojar el inmueble, pagar al actor, enervar en su caso u oponerse a la pretensión indicando, igualmente que la falta de oposición supone la prestación del consentimiento a la resolución del contrato. En todo caso se fijará el día y la hora para que tenga lugar, en su caso, el lanzamiento, que deberá producirse antes de treinta días desde la fecha señalada para la vista, advirtiendo al demandado de que si la sentencia es condenatoria y no se recurre, se procede al lanzamiento sin notificación posterior.

V.- COSTAS E INTERESES.- En aplicación del artículo 394 de la Ley de Enjuiciamiento Civil las costas se impondrán al demandado.

Por lo expuesto.

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y copia de todo ello, admita el Letrado de la Administración de Justicia a trámite la presente demanda, acordando:

—Requerir al demandado para que en el plazo de diez días enerve la acción pagando o consignando las cantidades que adeuda, desaloje el trastero o formule oposición dejando fijado en el derecho de admisión a trámite de la demanda la fecha para la vista del juicio verbal que se celebrará solo si mediare oposición, así como la fecha del lanzamiento.

—Para el caso de que no se formule oposición, que se dicte por el Letrado de la Administración de Justicia decreto de terminación del juicio de desahucio procediendo sin más al lanzamiento en la fecha fijada en el requerimiento al demandado.

—Si se celebrare la vista que en su día se dicte sentencia por la que se declare resuelto el contrato de arrendamiento de fecha del cuarto trastero nº [NÚMERO] sito en [LOCALIDAD], suscrito entre D./Dña. [NOMBRE Y APELLIDOS] como arrendador D./Dña. [NOMBRE Y APELLIDOS] como arrendatario, condenándole a que lo desaloje, teniéndose por solicitada ejecución de la sentencia y fijando día y hora para el lanzamiento directo del demandado en el requerimiento de pago que tras la admisión de la demanda se le haga.

En todo caso se impondrán las costas al demandado.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

OTROSÍ DIGO: Que, de conformidad con lo dispuesto en el art. 22.4 y 439.3 de la Ley de Enjuiciamiento Civil, la arrendataria podrá enervar la presente acción pagando al actor, o poniendo en su caso a disposición del Tribunal o notarialmente el importe de las cantidades reclamadas en la demanda y en su caso las que adeude en el momento de dicho pago enervador del desahucio.

Por lo expuesto

NUEVAMENTE SUPLICO: Que tenga por hecha la anterior manifestación a los efectos oportunos, por ser justicia que pido en mismo lugar y fecha.

========================================================================
