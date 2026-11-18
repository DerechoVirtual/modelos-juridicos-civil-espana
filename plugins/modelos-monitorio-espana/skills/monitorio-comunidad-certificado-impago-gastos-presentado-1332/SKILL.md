---
name: monitorio-comunidad-certificado-impago-gastos-presentado-1332
description: "Redacta el escrito «Monitorio de la comunidad por certificado de impago de gastos, presentado por el presidente» (formulario 1332 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Monitorio de la comunidad por certificado de impago de gastos, presentado por el presidente

> Formulario 1332 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] PROFESIÓN
- [ ] DNI/NIE
- [ ] CALLE (2 veces)
- [ ] NÚMERO (4 veces)
- [ ] Nº
- [ ] TELÉFONO
- [ ] IMPORTE (6 veces)
- [ ] LOCALIDAD
- [ ] FECHA
- [ ] Nº DE DOCUMENTO
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…omiciliado en C/ [CALLE] n.º [NÚMERO] de»; «…o al público bajo el nombre comercial de»; «…sito en la C/ [CALLE] n.º [NÚMERO] de»; «…de teléfono [TELÉFONO] y de fax»; «…las cuotas de las mensualidades de»; «…rajudicial. En este sentido, se acudió a»; «…os la petición en por ser el lugar donde»; «…rador ni Abogado (artículo 814 de la LEC»; «…n los artículos 812, 813 y 814 de la LEC»; «…ido en los artículos 812 y 815 de la LEC»; «…Es justicia que pido en»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Juicio / Juicio verbal / Juicio ordinario — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 813 de la LEC
- artículo 814 de la LEC
- artículos 812, 813 y 814 de la LEC
- artículos 812 y 815 de la LEC
- art. 5 de la Ley Orgánica 1/2025

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

### Formulario 1332 · Monitorio de la comunidad por certificado de impago de gastos, presentado por el presidente

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 37 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Proceso monitorio

Petición inicial

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: No existe «Tribunal de Instancia Decano» (DT 3.ª LO 1/2025). Si el asunto es de familia, Sección de Familia, Infancia y Capacidad; en partidos sin Sección Civil separada, Sección Única, de Civil y de Instrucción. Fuente: LO 1/2025 DT 3.ª (los jueces decanos pasan a la Presidencia del TI) y LOPJ arts. 84.1, 84.3 y 166 (BOE-A-2025-76).]

Que mediante el presente escrito formulo petición inicial de procedimiento monitorio con objeto de que se requiera a D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, soltero, de profesión [PROFESIÓN],provisto de DNI n.º [DNI/NIE],domiciliado en C/ [CALLE] n.º [NÚMERO] de [COMPLETAR], quien también podrá ser citado en su establecimiento comercial abierto al público bajo el nombre comercial de [COMPLETAR] sito en la C/ [CALLE] n.º [NÚMERO] de [COMPLETAR] provisto de n.º [Nº] de teléfono [TELÉFONO] y de fax [COMPLETAR],para que haga efectiva la cantidad de [IMPORTE] euros que adeuda a la Comunidad actora en concepto de gastos comunes de Comunidad, según los siguientes

ANTECEDENTES DE HECHO

D./Dña. [NOMBRE Y APELLIDOS] es propietario de una vivienda de las que integran el bloque de edificios sito en [LOCALIDAD] que forman la Comunidad de propietarios reclamante.

Corresponde a dicho propietario satisfacer una cuota ordinaria mensual por gastos de Comunidad de [IMPORTE] euros.

Hasta la fecha adeuda D./Dña. [NOMBRE Y APELLIDOS] las cuotas de las mensualidades de [COMPLETAR] de gastos de Comunidad a cuyo pago viene obligado, deuda que asciende a [IMPORTE] euros, según se acredita con

En la Junta General Extraordinaria de la Comunidad celebrada el día [FECHA] se acordó reclamar judicialmente la suma adeudada por la cantidad liquidada en la suma de [IMPORTE] euros, conforme acredito con la certificación de dicho acuerdo que acompaño reseñada como documento n.º [NÚMERO].

Como documento n.º [NÚMERO] acompaño certificación acreditativa de la deuda que D./Dña. [NOMBRE Y APELLIDOS] mantiene pendiente de pago con la Comunidad instante por la suma de [IMPORTE] euros.

Son de aplicación los siguientes

Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

En aplicación del art. 813 de la LEC corresponde al Tribunal de Instancia del lugar donde esté situada la finca o del domicilio del deudor a elección del solicitante. En este caso presentamos la petición en por ser el lugar donde [COMPLETAR].

No precisa esta petición intervención de Procurador ni Abogado (artículo 814 de la LEC [COMPLETAR]).

Amparo la petición en lo dispuesto en los artículos 812, 813 y 814 de la LEC [COMPLETAR].

Acompaño el principio de acreditación documental exigido en los artículos 812 y 815 de la LEC [COMPLETAR], consistente en certificación de deuda por impago de gastos comunes de Comunidad de Propietarios de inmueble urbano, expedida en legal forma.

La presente demanda cumple con los requisitos de procedibilidad exigidos por el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

En aplicación del artículo 21.6 de la Ley de Propiedad Horizontal (LPH): Las costas se impondrán al deudor aun cuando pague al ser requerido.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL: Tenga por presentado este escrito, documentos adjuntos y copias de todo ello, y lo admita, teniendo por formulada petición inicial de procedimiento monitorio y en su virtud requiera el Letrado de la Administración de Justicia a D./Dña. [NOMBRE Y APELLIDOS] para que haga efectivo en el plazo de veinte días el importe de la deuda pendiente de pago ante la Comunidad de Propietarios actora por la suma de [IMPORTE] euros, bajo apercibimiento de que de no hacerlo el Letrado de la Administración de Justicia dictará decreto dando por terminado el proceso monitorio y dando traslado a esta parte para instar ejecución por la cantidad adeudada por principal y costas más los intereses de mora procesal pertinentes, dando a la ejecución el impulso legal pertinente hasta su completa efectividad e imponiéndole, aun cuando pague, las costas procesales.

[ELEGIR UNA OPCIÓN Y REDACTARLA: Juicio / Juicio verbal / Juicio ordinario — el texto de cada opción no venía en el formulario original]

Es justicia que pido en [COMPLETAR],a [DÍA] de [MES] de [AÑO]

========================================================================
