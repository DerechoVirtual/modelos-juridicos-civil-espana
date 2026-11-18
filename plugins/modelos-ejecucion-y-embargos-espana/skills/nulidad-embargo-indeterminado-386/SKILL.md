---
name: nulidad-embargo-indeterminado-386
description: "Redacta el escrito «Nulidad de embargo indeterminado» (formulario 386 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Nulidad de embargo indeterminado

> Formulario 0386 del plugin **Ejecución civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.
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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] LOCALIDAD
- [ ] NÚMERO
- [ ] FECHA (5 veces)
- [ ] Nº (3 veces)
- [ ] AÑO (3 veces)
- [ ] LUGAR
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… tengo acreditado en los autos de juicio»; «…nte este Tribunal con número de registro»; «…la ejecutada y se pretende su traba para»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 588 LEC
- art. 588.1 LEC
- art. 590 LEC
- art. 562.2 LEC
- art. 227.2 LEC

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

### Formulario 0386 · Nulidad de embargo indeterminado

- Año del modelo: 2019
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 13 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de escrito del ejecutado solicitando nulidad de embargo por vulneración del art. 588 LEC.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de [NOMBRE DEL REPRESENTADO/A], S.L., con domicilio en [LOCALIDAD] y N.I.F. número [NÚMERO], según tengo acreditado en los autos de juicio [COMPLETAR] seguidos ante este Tribunal con número de registro [COMPLETAR] y de los que dimana el presente procedimiento de ejecución, comparezco y como mejor proceda en derecho DIGO:

Que en fecha [FECHA] me ha sido notificado Decreto n.º [Nº]/[AÑO], de fecha [FECHA], dictado por este Tribunal, en virtud del cual, al amparo del art. 551.3.1º LEC y de acuerdo con la petición literal de la parte ejecutante en su demanda, se ha acordado el embargo de las devoluciones que por IVA o IRPF pudieran corresponder "en la actualidad o en futuro a la Sociedad, S.L.", sin mayor precisión sobre el contenido de dicha medida de embargo ordenada.

Que sin perjuicio de la oposición en su caso planteada frente a la referida demanda ejecutiva, por medio del presente escrito vengo a SOLICITAR LA NULIDAD POR INDETERMINACIÓN DEL EMBARGO ORDENADO en los términos arriba indicados, o, subsidiariamente, a formular RECURSO DE REPOSICIÓN dirigido frente a la antedicha resolución judicial, en virtud de las siguientes

ALEGACIONES

Primera.- El embargo sobre las "devoluciones que por IVA o IRPF pudieran corresponder en la actualidad o en un futuro a la sociedad, S.L.", debe declararse nulo en aplicación de lo dispuesto en el art. 588.1 LEC que establece esta consecuencia para todos aquellos embargos practicados sobre bienes y derechos cuya efectiva existencia no conste. Exige este precepto que el embargo recaiga sobre bienes y derechos de existencia real y efectiva al momento de ser acordado, proscribiendo aquellos que tengan carácter genérico e indeterminado. Por excepción, el mismo artículo en su apartado 2, admite el embargo de los depósitos bancarios y saldos favorables que arrojaren las cuentas abiertas en entidades de crédito, siempre que se determine una cantidad como límite máximo, pudiendo el ejecutado disponer en lo que exceda de dicho límite.

El embargo aquí cuestionado, no recae —cual debiera— sobre un bien o un derecho de existencia conocida y actual, aun estuviera en fase de formación, expectante o no consolidado, sino sobre un hipotético e indeterminado derecho futuro, como clarísimamente revela la propia expresión utilizada para acordarlo y que ha sido transcrita.

Para que una expectativa jurídica o derecho en formación sea susceptible de embargo es determinante como señala el propio Decreto recurrido, la concurrencia de un hecho, situación o relación con virtualidad suficiente como para poder generar en el futuro un derecho con valor económico a favor del deudor.

El Tribunal fija este hecho adquisitivo, literalmente, "en la sola existencia de la mercantil demandada, de la que se presume su actividad que, en cuanto tal, queda sujeta a tales impuestos (IVA o Sociedades) con obligación legal para los sujetos pasivos para liquidarlos".

Esta parte no comparte en absoluto esta afirmación judicial, pues además de que incurre en cierta confusión entre lo que es el plano subjetivo y objetivo del derecho, amplía excesivamente el concepto y ámbito del designado hecho adquisitivo, distorsionando el verdadero objeto y la finalidad que nuestro actual ordenamiento procesal, otorga al acto del embargo.

Desde la perspectiva que ofrecen la actual y más completa regulación del embargo (arts. 584 y ss. LEC), se estima que para que un hecho actual pueda ser calificado como adquisitivo de una expectativa jurídica, susceptible de embargo, debe revestir, además de una objetiva importancia, una concreta e inequívoca significación como causa inicial generadora de un derecho patrimonial que en el futuro puede consolidarse e ingresar definitivamente en el patrimonio del deudor embargado.

Ello en modo alguno puede predicarse de los hechos que cita la resolución recurrida, pues, las eventuales devoluciones tributarias por los impuestos del valor añadido y sociedades, no surgen por la simple existencia de la mercantil ejecutada, aunque se presuma su actividad y su general condición de sujeto pasivo de tales impuestos, sino por la realidad de las autoliquidaciones y declaraciones tributarias que como tal sujeto pasivo y por la realización del correspondiente hecho imponible (que, lógicamente, puede o no suceder) hubiera presentado ante la Administración Tributaria y de las que derive que al término del período impositivo este haya ingresado mayor cantidad que la que, por tales impuestos, le corresponde.

Hasta entonces, no se ha producido el hecho adquisitivo y consecuentemente el derecho a la devolución no está presente en el patrimonio de la sociedad ejecutada, ni siquiera de manera expectante o en formación. Constituye una mera esperanza o posibilidad de existencia futura, no susceptible de embargo —so pena de nulidad— de conformidad con el comentado art. 588.1 LEC.

Revela la propia resolución recurrida, que cuando el embargo se acuerda, se desconoce si la ejecutada tributa o no a Hacienda y en el primer caso, si ello genera o no derecho a devolución, se hace pues «hipótesis» sobre la posible existencia del derecho en el patrimonio de la ejecutada y se pretende su traba para [COMPLETAR], a través de la notificación de la misma a la Administración Tributaria, determinar si aquel derecho existen o no realmente, adelantando así de forma contraria a la operativa legal del embargo, la fase de averiguación e investigación del patrimonio del ejecutado (art. 590 LEC) a la fase de afección.

Segunda.- En cuanto a la tramitación procedimental que debe seguirse a tal fin, lo cierto es que el art. 562.2 LEC efectúa una remisión global a los preceptos reguladores de las causas de nulidad de actuaciones, entre los cuales, el art. 227.2 LEC permite al tribunal, de oficio, o bien a instancia de parte como aquí es el caso, decretar la nulidad de actuaciones sin necesidad de incoar el incidente excepcional a continuación reglado, al no haber recaído todavía resolución que ponga fin al proceso.

Por lo expuesto,

SUPLICO AL TRIBUNAL:

Que teniendo por presentado este escrito, junto con sus copias (y en su caso documentos acompañados), sírvase admitirlo y así téngase por debidamente formulada, al amparo de los arts. 225.7º, 562.2 y 588.1 LEC, solicitud de NULIDAD POR INDETERMINACIÓN DEL EMBARGO ordenado en el Decreto n.º [Nº]/[AÑO] de fecha [FECHA], y, tras los trámites legales oportunos que procedan:

A) Al amparo del trámite previsto en el art. 227.2 LEC, en relación con los arts. 225.7º, 562.2 y 588.1 LEC, acuérdese la nulidad del embargo ordenado en dicha resolución judicial, dejándolo sin efecto, por infringir frontalmente dicha medida de embargo el principio de determinación establecido en el art. 588.1 LEC.
B) Subsidiariamente al trámite procedimental invocado, téngase por formulado RECURSO DE REPOSICIÓN frente al Decreto n.º [Nº]/[AÑO], de fecha [FECHA], por la infracción de los preceptos de constante referencia (arts. 225.7º y 588.1 LEC) y con base en los mismos motivos descritos en el cuerpo de este escrito.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a
