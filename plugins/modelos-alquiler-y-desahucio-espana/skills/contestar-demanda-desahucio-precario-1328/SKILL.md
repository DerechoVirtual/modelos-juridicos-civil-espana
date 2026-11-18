---
name: contestar-demanda-desahucio-precario-1328
description: "Redacta el escrito «Contestar a la demanda de desahucio por precario» (formulario 1328 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestar a la demanda de desahucio por precario

> Formulario 1328 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

- [ ] NÚMERO (2 veces)
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] Nº
- [ ] COLEGIO
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…numeración del juzgado de procedencia).]»; «…, nº [Nº] de Colegiado»; «…io en precario de la vivienda situada en»; «…de la vivienda, afirmación infundada por»; «…a en uso a cambio de contraprestación de»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Falta acreditación de titularidad / Usufructo / Titularidad cierta / Otras — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Pacto verbal / Existe contraprestación / Pacto y devolución contraprestación / Otras — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 438 de la LEC
- artículos 1543, 1546 y 1555 del Código Civil
- art. 394 LEC

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

### Formulario 1328 · Contestar a la demanda de desahucio por precario

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 2 bloques de opciones sin texto dejados en blanco con sus rótulos; 17 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio de desahucio en precario n.º [NÚMERO]

Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito con poder notarial que acompaño, ante el Tribunal comparezco con la asistencia letrada de D./Dña. [NOMBRE Y APELLIDOS], nº [Nº] de Colegiado [COMPLETAR] Del Ilte. Colegio de Abogados de [COLEGIO], y como mejor proceda en derecho, DIGO:

Que según permite el art. 438 de la LEC procedo a contestar a la demanda de desahucio en precario de la vivienda situada en [COMPLETAR], promovida por D./Dña. [NOMBRE Y APELLIDOS], en el sentido de oponerme a ella en atención a los siguientes:

HECHOS

En relación con los hechos:

1.º Sobre la propiedad de la vivienda:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Falta acreditación de titularidad / Usufructo / Titularidad cierta / Otras — el texto de cada opción no venía en el formulario original]

2.º Sobre la relación entre las partes:

PRIMERO.- Se afirma de contrario que esta parte no ostenta derecho alguno para servirse de la vivienda, afirmación infundada por [COMPLETAR] (ser cotitular de la propiedad, haber sido cedida en uso a cambio de contraprestación de [COMPLETAR]), según se acredita con los documentos que presentamos con los nº [NÚMERO].

SEGUNDO.- Este dato es sobradamente conocido por el ahora demandante. De hecho fue informado de las obras que recientemente se realizaron en la vivienda a costa de mi representado, a las que dio su conformidad D./Dña. [NOMBRE Y APELLIDOS], según acredito con los documentos nº [Nº DE DOCUMENTO].

3.º TERCERO.- El demandado no se encuentra, por tanto, en precario, entendido éste como una tenencia sin título o por mera tolerancia del dueño ya que, según acreditamos, mi representado deriva su derecho arrendaticio de

[ELEGIR UNA OPCIÓN Y REDACTARLA: Pacto verbal / Existe contraprestación / Pacto y devolución contraprestación / Otras — el texto de cada opción no venía en el formulario original]

3.º El demandado no se encuentra, por tanto, en precario, entendido éste como una tenencia sin título o por mera tolerancia del dueño ya que, según acreditamos, mi representado deriva su derecho arrendaticio de

FUNDAMENTOS DE DERECHO

I, II y III.- Conforme con los relativos a JURISDICCIÓN Y COMPETENCIA, TRAMITACIÓN Y LEGITIMACIÓN.

PRIMERO: Resultan de aplicación los artículos 1543, 1546 y 1555 del Código Civil, en atención a los cuales existe arrendamiento cuando una de las partes se obliga a pagar precio cierto como contraprestación por la puesta a su disposición del uso de la vivienda.

SEGUNDO: Igualmente es de aplicación el artículo 2 de la Ley de Arrendamientos Urbanos que define el arrendamiento de vivienda y la regulación sobre este negocio.

En este caso no existe una relación de precario, sino arrendaticia, porque hay contrato verbal y contraprestación por esta parte. Por eso no procede el desalojo de mi representado.

En aplicación del art. 394 LEC deberá acordarse la expresa imposición de costas a la parte actora.

Por lo expuesto,

SUPLICO AL TRIBUNAL. Que tenga por presentado esta contestación a la demanda, se admita a trámite y, previos los trámites oportunos, en su día se dicte sentencia mediante la que se desestime íntegramente la demanda de desahucio en precario de la vivienda situada en …, con expresa imposición de costas a la parte actora.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
