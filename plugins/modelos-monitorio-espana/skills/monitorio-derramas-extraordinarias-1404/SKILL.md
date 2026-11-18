---
name: monitorio-derramas-extraordinarias-1404
description: "Redacta el escrito «Monitorio por derramas extraordinarias» (formulario 1404 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Monitorio por derramas extraordinarias

> Formulario 1404 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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
- [ ] IMPORTE (8 veces)
- [ ] Nº
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…mayor de edad, con domicilio en la C/ de»; «…r de trabajo, empresa con sede en C/, de»; «…damente remitida al propietario afectado»; «…rajudicial. En este sentido, se acudió a»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Tipo de juicios / Juicio verbal / Juicio ordinario — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 813 de la LEC
- artículos 812 y 815 de la LEC
- art. 5 de la Ley Orgánica 1/2025
- artículo 814.2 de la LEC
- artículo 21.6 de la LPH
- artículo 21.5 de la LPH

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

### Formulario 1404 · Monitorio por derramas extraordinarias

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 9 campos de relleno marcados en blanco; 12 huecos del original que se habían perdido sin marca, marcados (IMPORTE, NOMBRE Y APELLIDOS, Nº, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Proceso monitorio

Petición inicial

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: No existe «Tribunal de Instancia Decano» (DT 3.ª LO 1/2025). Si el asunto es de familia, Sección de Familia, Infancia y Capacidad; en partidos sin Sección Civil separada, Sección Única, de Civil y de Instrucción. Fuente: LO 1/2025 DT 3.ª (los jueces decanos pasan a la Presidencia del TI) y LOPJ arts. 84.1, 84.3 y 166 (BOE-A-2025-76).]

Que mediante el presente escrito y según permiten los artículos 812 y 815 de la Ley de Enjuiciamiento Civil (LEC), formulo petición inicial de juicio monitorio frente a D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en la C/ de [COMPLETAR], que puede ser citado también en su lugar de trabajo, empresa con sede en C/, de [COMPLETAR], en reclamación de [IMPORTE] euros. Basamos esta pretensión en los siguientes

HECHOS

(Para los Tribunales en los que se haya implantado la presentación de escritos a través del sistema telemático con firma electrónica-Lex Net y la Comunidad haya designado procurador para su representación) Acompañamos como documento nº 1 índice numerado de los documentos que se presentan con esta petición inicial de procedimiento monitorio.

La Comunidad de Propietarios acordó en Junta General Extraordinaria de fecha proceder a realizar las siguientes obras en elementos comunes.

Para poder hacer frente a esas reformas se acordó igualmente una derrama extraordinaria total de [IMPORTE] euros, que se repartía entre todos los propietarios a abonar en mensualidades. En atención a su cuota de participación D./Dña. [NOMBRE Y APELLIDOS] tenía que pagar un total de [IMPORTE] euros, que dividido en seis meses daba una cuota extraordinaria de [IMPORTE] euros al mes.

Adjunto como documentos n.º citación a la reunión y copia del acta.

D./Dña. [NOMBRE Y APELLIDOS]

En el tiempo transcurrido desde el acuerdo no se ha procedido a su impugnación por este vecino.

Ante el impago de las cuotas indicadas, se convocó a nueva Junta Extraordinaria que incluía en el apartado n.º [Nº] del orden del día la aprobación del estado de deudas y la autorización al Presidente para reclamar en nombre de la Comunidad estas derramas.

Esta convocatoria fue debidamente remitida al propietario afectado [COMPLETAR].

En la Junta se aprobó la propuesta y la liquidación según certificación emitida por el Secretario con el visto bueno del Presidente, que acompaño como documento n.º [Nº DE DOCUMENTO].

(En su caso) Se ha practicado requerimiento previo que no ha sido atendido. Los gastos por esta actuación, que también se reclaman, ascendieron a [IMPORTE] euros según acredito con factura de que acompaño como documento n.º [Nº DE DOCUMENTO].

Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

Según el artículo 813 de la LEC, en relación con lo dispuesto en el art. 85.1º LOPJ, corresponde al Tribunal de Instancia del domicilio del deudor o el del lugar donde esté situada la finca.

El artículo 812.2.2.º de la LEC permite utilizar el proceso monitorio para la reclamación de cuotas impagadas de Comunidad. Los artículos 814 y siguientes de la misma norma indican el cauce a seguir.

Acompañamos los documentos exigidos en los artículos 812 y 815 de la LEC y 21 de la Ley de Propiedad Horizontal (LPH): certificado de liquidación de deuda y acreditación de gastos de requerimiento.

La presente demanda cumple con los requisitos de procedibilidad exigidos por el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

No precisa esta solicitud la intervención de Abogado y Procurador tal como indica el artículo 814.2 de la LEC, pero, si la Comunidad se sirviera de estos profesionales, el deudor deberá pagar las costas con los límites establecidos en el artículo 21.6 de la LPH y 394 de la LEC.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y copia de todo ello, lo admita a trámite el Letrado de la Administración de Justicia y tenga por formulada petición inicial de proceso monitorio y en su virtud requiera a D./Dña. [NOMBRE Y APELLIDOS] para que en el plazo legal haga efectiva la cantidad de [IMPORTE] euros correspondientes a las cuotas impagadas y [IMPORTE] euros por los gastos de requerimiento más las costas procesales, bajo apercibimiento de que, de no hacerlo, se dictará decreto teniendo por finalizado el proceso y dando traslado a esta parte para instar ejecución por la cantidad adeudada por principal y costas más los intereses de mora pertinentes, dando a la ejecución el impulso procesal pertinente hasta su completa efectividad.

[ELEGIR UNA OPCIÓN Y REDACTARLA: Tipo de juicios / Juicio verbal / Juicio ordinario — el texto de cada opción no venía en el formulario original]

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firmas de abogado y procurador

OTROSÍ I DIGO: Que según permite el artículo 21.5 de la LPH desde este momento intereso que, si el demandado formulara oposición, se acuerde el embargo de bienes del deudor por la suma de [IMPORTE] euros que provisionalmente se calculan, sin perjuicio de ulterior liquidación, para cubrir principal, intereses y costas, y todo ello sin que esta parte tenga que prestar caución.

Firmas de abogado y procurador

========================================================================
