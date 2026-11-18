---
name: suspension-lanzamiento-vivienda-habitual-ley-12-2023-58
description: "Redacta el escrito «Suspensión del lanzamiento de vivienda habitual (Ley 12/2023, derecho a la vivienda)» (formulario 58 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Suspensión del lanzamiento de vivienda habitual (Ley 12/2023, derecho a la vivienda)

> Formulario 0058 del plugin **Ejecución civil** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Desahucio de vivienda desde el 8-10-2026: comprobar la suspensión del art. 2 RDL 29/2026 (hasta 31-12-2030; aplicable a ejecuciones en curso, DT 2.ª) y, si es por impago y el inquilino es vulnerable, la enervación extraordinaria a cargo de la Administración del art. 22.6 LEC (dos meses de suspensión; independiente de la del 22.4). La suspensión del art. 441.5-6 LEC es de dos meses (persona física) o cuatro (jurídica).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] Nº
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] NÚMERO (2 veces)
- [ ] COLEGIO
- [ ] FECHA
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de contrato de arrendamiento de fecha de»; «…os medios válidos en derecho, situada en»; «…del informe emitido por los servicios de»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 441.5 LEC
- art. 3.k) de la Ley 12/2023

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

### Formulario 0058 · Suspensión del lanzamiento de vivienda habitual (Ley 12/2023, derecho a la vivienda)

- Año del modelo: 2023
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 15 campos de relleno marcados en blanco
- Avisos de la revisión: Desahucio de vivienda desde el 8-10-2026: comprobar la suspensión del art. 2 RDL 29/2026 (hasta 31-12-2030; aplicable a ejecuciones en curso, DT 2.ª) y, si es por impago y el inquilino es vulnerable, la enervación extraordinaria a cargo de la Administración del art. 22.6 LEC (dos meses de suspensión; independiente de la del 22.4). La suspensión del art. 441.5-6 LEC es de dos meses (persona física) o cuatro (jurídica).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de la persona arrendataria instando, de conformidad con lo previsto en el art. 441.5 LEC, incidente de suspensión extraordinaria del desahucio o lanzamiento ante el Tribunal por encontrarse en una situación de vulnerabilidad económica que le imposibilite encontrar una alternativa habitacional para sí y para las personas con las que conviva.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [Nº]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según tengo acreditado en los autos del juicio verbal de desahucio nº [NÚMERO], asistido del Letrado D./Dña. [NOMBRE Y APELLIDOS], ejerciente nº [NÚMERO] del Iltre. Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco y, como mejor proceda en Derecho, DIGO:

Que mediante el presente escrito vengo a solicitar la SUSPENSIÓN DEL LANZAMIENTO SOBRE LA VIVIENDA HABITUAL por encontrarse mi mandante en situación de vulnerabilidad económica, al amparo de la Ley 12/2023, de 24 de mayo, por el derecho a la vivienda, de conformidad con las siguientes:

ALEGACIONES

PRIMERA.- Que ante este tribunal se sigue procedimiento de desahucio frente a mi mandante, en la que se ha decretado el lanzamiento de la vivienda arrendada, en virtud de contrato de arrendamiento de fecha de [COMPLETAR].

La vivienda sobre la que versa el arrendamiento es, desde que se entregaron las llaves conforme contrato y hasta la fecha, la vivienda habitual de mi representado, constituyendo el domicilio permanente de esta parte que la ocupa, que puede acreditarse a través de los datos obrantes en el padrón municipal u otros medios válidos en derecho, situada en [COMPLETAR], de la que es propietario y arrendador Don/Dña. [NOMBRE Y APELLIDOS].

SEGUNDA.- Que mi representado se encuentra inmerso en situación de vulnerabilidad económica conforme a la Ley 12/2023, de 24 de mayo, por el derecho a la vivienda, en virtud del informe emitido por los servicios de [COMPLETAR] de fecha [FECHA] en materia de vivienda, asistencia social, evaluación e información de situaciones de necesidad social y atención inmediata a personas en situación o riesgo de exclusión social que ha sido específicamente designada conforme la legislación y normativa autonómica en materia de vivienda; el cual se acompaña a este escrito como documento nº [Nº DE DOCUMENTO].

TERCERA.- Que concurre en la parte arrendadora la condición de gran tenedor conforme a la definición prevista en el art. 3.k) de la Ley 12/2023, de 24 de mayo, por el derecho a la vivienda, a cuya acreditación se adjunta como documento nº [Nº DE DOCUMENTO] certificación del Registro de la Propiedad.

En virtud de lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito, con sus documentos y copias, tenga por formulada solicitud de suspensión del lanzamiento al amparo de la Ley 12/2023, de 24 de mayo, por el derecho a la vivienda.

Por ser de justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

Firma de Procurador/a
