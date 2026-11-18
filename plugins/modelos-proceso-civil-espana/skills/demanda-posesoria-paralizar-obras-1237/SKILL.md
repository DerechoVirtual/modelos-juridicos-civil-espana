---
name: demanda-posesoria-paralizar-obras-1237
description: "Redacta el escrito «Demanda posesoria para paralizar obras» (formulario 1237 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda posesoria para paralizar obras

> Formulario 1237 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- MASC mal resuelto: afirma que la suspensión de obra nueva está excluida por el art. 5.3 LO 1/2025, pero ni el 5.2 ni el 5.3 la excluyen (solo la tutela sumaria de la posesión y la obra en ruina). Debe acreditarse el MASC.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] DNI/NIE
- [ ] CALLE
- [ ] Nº (2 veces)
- [ ] Nº DE DOCUMENTO
- [ ] FECHA
- [ ] IMPORTE
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 16 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… domicilio en la C/ [CALLE] núm. [Nº] de»; «…es propietario de»; «…es propietario de [COMPLETAR] situado en»; «…de»; «…. En el día de»; «…r una obra que consiste aparentemente en»; «…an realizado las siguientes actividades:»; «… obra, según el informe que acompañamos:»; «…inada por el artículo 52.1.8.º de la LEC»; «…blecido en el artículo 249.1.8 de la LEC»; «…ido en el artículo 251.3.ª.5.º de la LEC»; «…n la prohibición del artículo 397 del CC»; …

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Nombramiento perito e informe obra / Reconocimiento judicial e incidencia / Nombramiento perito e informe obra, conjuntamente con el reconocimiento judicial — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículos 21 y 22 de la LOPJ
- artículos 85 de la LOPJ
- artículo 249.1.8 de la LEC
- artículo 441.2 de la LEC
- artículo 10 de la LEC
- artículo 7 de la LPH
- artículo 397 del CC
- artículos 23 y 31 de la LEC
- art. 5.3 LO 1/2025
- artículos 7 y 9 de la LPH
- artículo 394 de la LEC

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

### Formulario 1237 · Demanda posesoria para paralizar obras

- Año del modelo: 2013
- Revisión 17-11-2026: 2 puntualizaciones normativas añadidas en el texto; 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 28 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (DNI/NIE, Nº DE DOCUMENTO)
- Avisos de la revisión: MASC mal resuelto: afirma que la suspensión de obra nueva está excluida por el art. 5.3 LO 1/2025, pero ni el 5.2 ni el 5.3 la excluyen (solo la tutela sumaria de la posesión y la obra en ruina). Debe acreditarse el MASC.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Acción posesoria de obra nueva

Demanda

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

Que mediante el presente escrito formulo demanda a tramitar por el cauce del juicio verbal en ejercicio de acción posesoria de suspensión de obra nueva para que por D./Dña. [NOMBRE Y APELLIDOS] con DNI núm. [DNI/NIE] y domicilio en la C/ [CALLE] núm. [Nº] de [COMPLETAR] se proceda a la paralización de la obra que se concretará en el suplico de la demanda en atención a los siguientes:

HECHOS

(Para los Tribunales en los que se haya implantado la presentación de escritos a través del sistema telemático con firma electrónica-Lex Net). Acompañamos como documento nº 1 índice numerado de los documentos que se presentan con esta demanda.

D./Dña. [NOMBRE Y APELLIDOS] es propietario de [COMPLETAR] situado en [COMPLETAR], según acredito con nota simple emitida por el Registro de la Propiedad núm. [Nº] de [COMPLETAR] que acompaño como documento núm. [Nº DE DOCUMENTO].

En el día de [COMPLETAR] ha comenzado a realizar una obra que consiste aparentemente en [COMPLETAR], puesto que según informe pericial que acompaño con el núm. emitido por el técnico en D./Dña. [NOMBRE Y APELLIDOS] se han realizado las siguientes actividades: [COMPLETAR].

Tal obra, según el informe que acompañamos: [COMPLETAR].

En su caso:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Nombramiento perito e informe obra / Reconocimiento judicial e incidencia / Nombramiento perito e informe obra, conjuntamente con el reconocimiento judicial — el texto de cada opción no venía en el formulario original]

Requerido el demandado para que cese esta situación se ha negado a ello sin dar explicación alguna, motivo por el que nos vemos obligados a interponer esta acción, autorizada por Junta extraordinaria de fecha [FECHA].

FUNDAMENTOS DE DERECHO

Los artículos 21 y 22 de la LOPJ atribuyen a la jurisdicción española y al orden civil el conocimiento de estas materias, y los artículos 85 de la LOPJ y 45 de la LEC designan a los Tribunales de Instancia como los encargados de conocer estas pretensiones.

La competencia territorial viene determinada por el artículo 52.1.8.º de la LEC [COMPLETAR].

PRIMERO.— El artículo 250.1.5.ª de la LEC remite al cauce del juicio verbal las demandas que pretendan que el Tribunal resuelva, con carácter sumario, la suspensión de una obra nueva. Y éste procedimiento debe tener prevalencia, por su carácter sumario, sobre lo establecido en el artículo 249.1.8 de la LEC [COMPLETAR].

La cuantía se fija en [IMPORTE] euros en atención a lo establecido en el artículo 251.3.ª.5.º de la LEC [COMPLETAR].

SEGUNDO.— En aplicación de lo establecido en el artículo 441.2 de la LEC interesamos que antes de que se de traslado para la contestación a la demanda, dirija inmediata orden de suspensión al dueño de la obra.

Según el artículo 10 de la LEC están legitimadas ambas partes por ser titulares del objeto de este proceso, La Comunidad en atención a lo establecido en el artículo 7 de la LPH y el comunero según la prohibición del artículo 397 del CC [COMPLETAR].

Los artículos 23 y 31 de la LEC exigen la firma de la demanda por procurador y letrado cuando la cuantía de la demanda exceda las 2.000 euros.

La presente demanda no está sujeta al previo intento de resolución de controversias en vía no jurisdiccional por tratarse de materias excluidas del requisito de procedibilidad de acuerdo con el art. 5.3 LO 1/2025, en cuanto el interdicto de obra nueva [NOTA DE REVISIÓN: Error: el art. 5.3 no menciona la suspensión de obra nueva y el art. 5.2 solo excluye la tutela sumaria de la posesión (letra e) y la demolición de obra en ruina (letra f). La suspensión de obra nueva (art. 250.1.5.º LEC) exige MASC. Fuente: LO 1/2025 art. 5.2 y 5.3 (BOE-A-2025-76).] es un procedimiento especial y sumario que pretende, de manera cautelar, salvaguardar la posesión, propiedad o cualquier otro derecho real frente a una obra nueva en construcción que de seguir en el tiempo podría llevar a daños irreparables en los derechos que se pretenden defender.

En este sentido, destaca la naturaleza de medida cautelar de la suspensión de obra nueva, entre otras, la SAP Las Palmas 194/2003, de 10 de abril:

El interdicto de obra nueva, es un proceso cautelar conservativo que se inicia ante el temor de una lesión, actual o inminente, en la propiedad, posesión o derechos reales del reclamante, basado en la racional creencia de la producción de un posible, o real, perjuicio derivado de una obra en construcción. Se trata con este proceso sumario de evitar - mediante la paralización de la obra en construcción- los perjuicios que una demolición total de la obra presuntamente dañosa puede acarrear. Se dirige, por ello, a obtener la paralización provisional de una obra que lesiona el derecho de propiedad o posesión del actor, y está en función de un segundo proceso declarativo que, a través del interdicto, se prepara.

PRIMERO.— El artículo 250.1.5.º de la LEC permite solicitar la tutela sumaria de la posesión mediante la solicitud de suspensión de una obra nueva que perturbe o pueda causar perjuicios a quien solicita el auxilio judicial.

SEGUNDO.— De la redacción del artículo 441.2 de la LEC se puede desprender que uno de los requisitos que se exige para poder valerse de esta acción consiste en que la obra se esté realizando y no haya concluido. En este caso se puede apreciar por el informe y las fotografías que aportamos que nos encontramos dentro de ese supuesto, ya que se están realizando las labores preliminares de la construcción.

TERCERO.— Los artículos 7 y 9 de la LPH prohíben al comunero realizar obras que afecten a los elementos comunes o estructura del edificio sin consentimiento de la Comunidad, en este caso [COMPLETAR].

En aplicación del artículo 394 de la LEC deberán imponerse al demandado al desestimarse sus pretensiones.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y copia de todo ello, lo admita a trámite el Letrado de la Administración de Justicia y,

1.º [COMPLETAR]

2.º Con carácter previo al traslado para la contestación a la demanda, se dicte resolución dirigiendo al demandado D/Dña. [NOMBRE Y APELLIDOS] inmediata orden de suspensión de la obra de [COMPLETAR] y que se practiquen los medios de prueba interesados con carácter previo a la celebración de la vista.

3.º Así como que en su día y previa citación de las partes a la vista del juicio verbal cuya celebración se solicita, se dicte sentencia por la que se acuerde la definitiva suspensión de los trabajos de la obra que el demandado está realizando en [COMPLETAR] consistente en [DESCRIBIR], así como que se repongan las cosas al estado anterior.

4.º Que se condene en costas al demandado.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firmas de abogado y procurador

========================================================================
