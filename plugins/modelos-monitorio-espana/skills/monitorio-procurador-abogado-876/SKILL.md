---
name: monitorio-procurador-abogado-876
description: "Redacta el escrito «Monitorio con procurador y abogado» (formulario 876 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Monitorio con procurador y abogado

> Formulario 0876 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (8 veces)
- [ ] NÚMERO (3 veces)
- [ ] COLEGIO
- [ ] DNI/NIE
- [ ] CALLE
- [ ] TELÉFONO
- [ ] IMPORTE (4 veces)
- [ ] ÓRGANO
- [ ] Nº DE DOCUMENTO
- [ ] DESCRIBIR
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…n nombre y representación de la sociedad»; «…n.º [NÚMERO] piso»; «…n.º [NÚMERO] piso [COMPLETAR] de»; «…ue acompañan a la petición. En el mes de»; «…del año»; «…Como documentos números»; «…os adquiridos se pusieron en circulación»; «…iento. Acompaño, como documentos números»; «…a»; «…rajudicial. En este sentido, se acudió a»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 813 de la LEC
- artículos 814 a 818 de la LEC
- arts. 812 y 815 de la LEC
- art. 5 de la Ley Orgánica 1/2025
- artículo 814 de la LEC
- artículo 2 de la Ley 10/2012

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

### Formulario 0876 · Monitorio con procurador y abogado

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 1 rangos de artículos despegados («25 a31» → «25 a 31»); 35 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma orgánica y procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: No existe «Tribunal de Instancia Decano» (DT 3.ª LO 1/2025). Si el asunto es de familia, Sección de Familia, Infancia y Capacidad; en partidos sin Sección Civil separada, Sección Única, de Civil y de Instrucción. Fuente: LO 1/2025 DT 3.ª (los jueces decanos pasan a la Presidencia del TI) y LOPJ arts. 84.1, 84.3 y 166 (BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en nombre y representación de la sociedad [COMPLETAR], según acredito con la escritura de poder que acompaño y cuya devolución solicito previa su oportuna constancia en Autos, ante el Tribunal comparezco bajo la dirección del Abogado D./Dña. [NOMBRE Y APELLIDOS], Colegiado n.º [NÚMERO] del Ilustre Colegio de Abogados de [COLEGIO], y como mejor proceda en Derecho DIGO:

Que mediante el presente escrito formulo PETICIÓN INICIAL promoviendo PROCESO MONITORIO contra D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, provisto de DNI [DNI/NIE], domiciliado en C/ [CALLE] n.º [NÚMERO] piso [COMPLETAR] de [COMPLETAR], provisto de número de teléfono [TELÉFONO], con objeto de que se requiera a dicho deudor para que haga efectiva a mi representado la cantidad de [IMPORTE] euros que le adeuda, según los siguientes

ANTECEDENTES DE HECHO

(En su caso, si en la circunscripción se hace presentación telemática) Se presenta listado de documentos que acompañan a la petición.

En el mes de [COMPLETAR] del año [COMPLETAR], D./Dña. [NOMBRE Y APELLIDOS] adquirió de mi representado los géneros que constan en la factura que acompaño reseñada como documento n.º [NÚMERO] Como documentos números [COMPLETAR] acompaño los albaranes que dicho comprador firmó en señal de conformidad con la recepción de los géneros.

Para el pago del precio de los géneros adquiridos se pusieron en circulación [COMPLETAR] efectos, que fueron impagados y devueltos a su vencimiento. Acompaño, como documentos números [COMPLETAR] a [COMPLETAR], ejemplares originales de dichos efectos devueltos y los justificantes de los gastos bancarios generados por su devolución.

Adeuda en consecuencia D./Dña. [NOMBRE Y APELLIDOS] a mi poderdante [ÓRGANO] la suma de [IMPORTE] euros, sin que aquél haya tenido a bien atender los múltiples requerimientos de pago que se le han cursado.

Son de aplicación los siguientes

Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

Competencia

En aplicación del artículo 813 de la LEC, en relación con lo dispuesto en el art. 85.1º LOPJ, corresponde al Tribunal de Instancia del domicilio o residencia del deudor o, en el caso de no ser conocidos, al del lugar en el que el deudor pueda ser hallado.

Tramitación

Será de aplicación lo establecido en los artículos 814 a 818 de la LEC.

Acompaño la acreditación documental exigida en los arts. 812 y 815 de la LEC, consistente en [DESCRIBIR] (factura, albaranes de entrega firmados por el deudor, efectos girados al cobro y justificantes bancarios de gastos de devolución).

Cumplimiento de los requisitos de procedibilidad

La presente demanda cumple con los requisitos de procedibilidad exigidos por el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Legitimación

A los efectos previstos en el artículo 814 de la LEC se deja identificado al deudor D./Dña. [NOMBRE Y APELLIDOS] y el domicilio donde puede ser hallado.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL que tenga por presentado este escrito, documentos adjuntos y copias de todo ello, teniendo por formulada PETICIÓN INICIAL de promoción de PROCESO MONITORIO contra D./Dña. [NOMBRE Y APELLIDOS] y en su virtud requiera el Letrado de la Administración de Justicia a dicho deudor para que en el plazo de veinte días pague a mi representada [NOMBRE DEL REPRESENTADO/A] la cantidad de [IMPORTE] euros que adeuda bajo apercibimiento de que de no hacerlo se despachará ejecución por la cantidad adeudada más los intereses de mora procesal pertinentes y costas, acordando además lo siguiente:

1.º Para el supuesto de que el deudor no pagare la suma reclamada y no formulare oposición en debida forma en plazo legal, dicte el Letrado de la Administración de Justicia decreto dando por terminado el proceso monitorio y dándonos traslado para instar el despacho de ejecución.

2.º OPCIONES:

a) (En asuntos cuya cuantía no supere 15.000 euros): Para el supuesto de que el deudor presentase escrito de oposición en plazo legal, dicte decreto el Letrado de la Administración de Justicia dando por terminado este proceso y acordando seguir los trámites del juicio verbal dando traslado a esta parte para contestar, y en su día se dicte sentencia condenando a D./Dña. [NOMBRE Y APELLIDOS] a pagar a mi mandante la suma reclamada de [IMPORTE] euros, más los intereses procedentes, e imponiéndole en todo caso las costas del procedimiento.

b) (En asuntos cuya cuantía supere 15.000 euros): Para el supuesto de que el deudor presentase escrito de oposición en plazo legal, acuerde darme traslado del mismo para formular demanda en el plazo de un mes legalmente previsto continuando la tramitación por el cauce del juicio ordinario.

Es Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

(Para personas jurídicas y cuantía superior a 2.000 euros) OTROSÍ DIGO: Que acompaño modelo 696 de autoliquidación de la tasa judicial, según exigen el artículo 2 de la Ley 10/2012, de 20 de noviembre, y la Orden que aprueba los modelos de autoliquidación.

NUEVAMENTE SUPLICO. Que se acuerde tener por liquidada la tasa judicial por ser justicia que pido en mismo lugar y fecha.

========================================================================
