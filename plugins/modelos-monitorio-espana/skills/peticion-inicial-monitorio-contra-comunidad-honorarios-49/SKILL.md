---
name: peticion-inicial-monitorio-contra-comunidad-honorarios-49
description: "Redacta el escrito «Petición inicial de monitorio contra la comunidad por honorarios del administrador» (formulario 49 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Petición inicial de monitorio contra la comunidad por honorarios del administrador

> Formulario 0049 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] DNI/NIE
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] NIF
- [ ] NÚMERO (2 veces)
- [ ] IMPORTE (3 veces)
- [ ] Nº DE DOCUMENTO (6 veces)
- [ ] ÓRGANO
- [ ] Nº
- [ ] FECHA
- [ ] Otros 17 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA»; «…ombramiento de administrador otorgada el»; «…frente a la COMUNIDAD DE PROPIETARIOS DE»; «…siguientes: HECHOS PRIMERO: La mercantil»; «…otorgada ante el notario de»; «…orgada ante el notario de [COMPLETAR] el»; «…e inscrita en el Registro Mercantil de»; «… de ello se acompaña como documento nº 2»; «…n y administración de fincas suscrito el»; «…o, los honorarios pactados ascendieron a»; «…licación de dicho contrato, en el mes de»; «…de»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 813 de la LEC
- artículo 13.3 LPH
- art. 5 de la Ley Orgánica 1/2025
- artículo 814 LEC
- art. 1100, 1101 y 1108 del Código Civil
- artículo 7.2 de la Ley 10/2012
- Ley 25/2015

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

### Formulario 0049 · Petición inicial de monitorio contra la comunidad por honorarios del administrador

- Año del modelo: 2023
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 40 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA [COMPLETAR] QUE POR TURNO CORRESPONDA

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

Don/Doña [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD] y DNI nº [DNI/NIE], actuando en calidad de administrador único/solidario, en nombre y representación de la mercantil [NOMBRE DEL REPRESENTADO/A], con domicilio en [LOCALIDAD] y CIF nº [NIF] según acredito con escritura de nombramiento de administrador otorgada el [COMPLETAR] ante el notario Don/Doña [NOMBRE Y APELLIDOS], al número [NÚMERO] de su protocolo, ante el Tribunal comparezco y como mejor proceda en Derecho, DIGO:

Que por medio de la presente formulo petición inicial de proceso monitorio frente a la COMUNIDAD DE PROPIETARIOS DE [COMPLETAR], con domicilio en el de su presidente (Don/Doña [NOMBRE Y APELLIDOS]), sito en [LOCALIDAD] reclamando la cantidad de [IMPORTE] euros en concepto de honorarios adeudados por administración de la misma. Baso la presente petición en los siguientes:

HECHOS

PRIMERO: La mercantil [COMPLETAR] tiene, entre otros, como objeto social, la gestión y administración de fincas rústicas y urbanas. En prueba de ello se acompaña la escritura de constitución como documento nº [Nº DE DOCUMENTO] otorgada ante el notario de [COMPLETAR] el [COMPLETAR] e inscrita en el Registro Mercantil de [COMPLETAR].

SEGUNDO: Dentro del ejercicio de su actividad mercantil, la peticionaria fue contratada por la comunidad de propietarios demandada para que se hiciera cargo de su administración.

En prueba de ello se acompaña como documento nº 2 [COMPLETAR] el contrato de gestión y administración de fincas suscrito el [COMPLETAR].

Como se comprueba con dicho contrato, los honorarios pactados ascendieron a [COMPLETAR], actualizables según IPC y a abonar mediante [ÓRGANO] en los [Nº] días de cada mes.

TERCERO: En aplicación de dicho contrato, en el mes de [COMPLETAR] de [COMPLETAR] se devengaron los honorarios de la actora que ascendieron a la cantidad de [IMPORTE] En prueba de ello acompaño como documento nº [Nº DE DOCUMENTO] la factura emitida por dichos servicios.

Girado el recibo a la cuenta de la comunidad el día [FECHA], el mismo fue devuelto por orden expresa de la deudora, como se acredita con el resguardo bancario emitido que se acompaña como documento nº [Nº DE DOCUMENTO] La devolución del recibo ha generado unos gastos de [COMPLETAR].

CUARTO: Con carácter previo a la presentación de esta petición inicial de procedimiento monitorio, se ha dirigido reclamación (que adjunto como documento nº [Nº DE DOCUMENTO]), al presidente de la comunidad, quien tras ponerse en contacto con la acreedora, se ha negado ha abonar las cantidades pendientes.

QUINTO: Consecuentemente, la comunidad de propietarios demandada adeuda a mi representada la cantidad total de [COMPLETAR], que se desglosa de la siguiente manera: (importe de la factura nº [NÚMERO]); y [COMPLETAR] (gastos de devolución bancaria).

SEXTO: Asimismo, previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

A los anteriores hechos son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

JURISDICCIÓN Y COMPETENCIA

Conforme a lo dispuesto en el art. 813 de la LEC, en relación con lo dispuesto en el art. 85.1º LOPJ, será exclusivamente competente para el proceso monitorio el Tribunal de Instancia del domicilio o residencia del deudor.

REPRESENTACIÓN Y LEGITIMACIÓN

La representación de la mercantil peticionaria la ostenta el administrador suscribiente conforme al artículo 233 de la LSC quien se encuentra legitimada activamente como acreedora de los servicios prestados e impagados.

Asimismo, el artículo 13.3 LPH señala que el presidente de la comunidad de propietarios ostenta su representación legal. La legitimación pasiva la ostenta la indicada comunidad de propietarios como deudora de las cantidades reclamadas.

POSTULACIÓN Y DEFENSA

No se precisa para esta petición inicial de proceso monitorio intervención de procurador ni abogado (Art. 814 de la LEC), por lo que esta parte comparece representada por su administrador, representante legal de la misma.

CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD

La presente demanda cumple con los requisitos de procedibilidad exigidos por el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

PETICIÓN INICIAL

Se cumplen los requisitos establecidos en el artículo 814 LEC, para la petición inicial del procedimiento monitorio: identificación del deudor, domicilios de las partes, expresión del el origen y cuantía de la deuda, y asimismo, se adjuntan los documentos que acreditan la deuda reclamada.

PROCEDIMIENTO

Artículos 815 y ss. de la LEC.

FONDO

Resultan de aplicación los art. 1091, 1100, 1101, 1258, 1544 y concordantes del Código Civil, por incumplimiento del contrato de servicios de gestión y administración de fincas por parte de la demandada quien ha impagado el precio de los servicios contratados y efectuados.

INTERESES

Es de aplicación el art. 1100, 1101 y 1108 del Código Civil, devengándose el interés legal desde la fecha de la mora.

En base a lo anterior,

SUPLICO AL TRIBUNAL se tenga por presentado este escrito con sus documentos, se sirva admitirlo y tener por interpuesta petición de juicio monitorio frente a la comunidad de propietarios [COMPLETAR] en reclamación de [IMPORTE] euros más los intereses correspondientes dictándose en su consecuencia por el Letrado de la Administración de Justicia resolución requiriendo de pago a la demandada a fin de que en el plazo de veinte días pague la cantidad anterior acreditándolo o comparezca ante ese Tribunal y alegue en escrito de oposición las razones en base a las que se opone al pago. En caso de que no compareciere se solicita que por el Letrado de la Administración de Justicia se dicte decreto dando por finalizado el proceso monitorio con traslado a esta parte para el despacho de ejecución.

Firma administrador societario.

OTROSÍ DIGO.- Que estando la presente demanda sujeta al abono de la tasa por el ejercicio de la potestad jurisdiccional fijada por la Ley 10/2012, de 20 de noviembre, modificada por RDL 3/2013 y Ley 25/2015, de 28 julio, y desarrollada por Orden HAP/2662/2012, de 13 de diciembre, siendo mi representada personas jurídica no exenta de su pago, se acompaña a la presente demanda como documento nº [Nº DE DOCUMENTO] la correspondiente autoliquidación con el ejemplar para la Administración de Justicia debidamente validado y en el que consta el pago de la cantidad de 100 euros correspondiente a la cuota fija, sin que se incluya la cuota variable prevista en el artículo 7.2 de la Ley 10/2012 al haber sido declarado inconstitucional y nulo por la STC 140/2016, de 21 de julio.

En virtud de lo anterior,

SUPLICO AL TRIBUNAL que tenga por hecha la anterior manifestación a los efectos pertinentes y por acompañado el documento justificativo del abono de la tasa.
