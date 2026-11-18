---
name: ejecucion-sentencia-demanda-1350
description: "Redacta el escrito «Ejecución de sentencia: demanda» (formulario 1350 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Ejecución de sentencia: demanda

> Formulario 1350 del plugin **Ejecución civil** · revisado el 17-11-2026.

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
- [ ] NÚMERO (2 veces)
- [ ] FECHA (2 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…ya ejecución se interesa es firme porque»; «…lanzamiento en juicios de desahucio. 6.º»; «…de orden general de ejecución, acordando»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: No ha abandonado / Ha abandonado, pero no ha pagado las rentas — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 549.4 de la LEC

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

### Formulario 1350 · Ejecución de sentencia: demanda

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 12 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Ejecución de sentencia

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

Que mediante el presente escrito formulo demanda ejecutiva interesando que se despache la ejecución de la sentencia n.º [NÚMERO] de fecha [FECHA] dictada en los autos citados contra el demandado D./Dña. [NOMBRE Y APELLIDOS], cuyos datos y circunstancias personales ya constan en las presentes actuaciones, a fin de que se dicte por el tribunal auto conteniendo orden general de ejecución y de despavho de ella conforme a lo acordado en el fallo de la referida sentencia, y por el Letrado de la Administración de Justicia decrete para su efectividad. Baso mi pretensión en los siguientes:

HECHOS

La sentencia cuya ejecución se interesa es firme porque [COMPLETAR].

El condenado al desahucio:

[ELEGIR UNA OPCIÓN Y REDACTARLA: No ha abandonado / Ha abandonado, pero no ha pagado las rentas — el texto de cada opción no venía en el formulario original]

De resultar insuficientes los descritos para hacer efectiva la deuda, interesamos las siguientes medidas de investigación judicial para hallar propiedades o rentas del mismo).

FUNDAMENTOS DE DERECHO

Corresponde conocer de esta ejecución al Tribunal que dictó la sentencia en aplicación de los artículos 61 y 545 de la Ley de Enjuiciamiento Civil.

1.º La sentencia de condena firme lleva aparejada ejecución según lo establecido en el artículo 517.2.1.º de la Ley de Enjuiciamiento Civil.

2.º

• Se ha cumplido el requisito del transcurso de 20 días desde la firmeza de la sentencia para solicitar la ejecución, según requiere el artículo 548 de la Ley de Enjuiciamiento Civil.

• Según permite el artículo 549.4 de la LEC no es de aplicación el plazo de espera de 20 días para ejecutar sentencia cuando la ejecución afecta a condenas de desahucio por falta de pago de rentas o cantidades debidas, o por expiración legal o contractual del plazo del arrendamiento.

3.º No es necesario acompañar el título ejecutivo ni el poder general para pleitos porque ya constan en autos, artículo 550.1.1.º y 2.º de la Ley de Enjuiciamiento Civil.

4.º Los artículos 551 y 553 de la Ley de Enjuiciamiento Civil fijan que la ejecución se despachará mediante auto conteniendo orden general de despacho de ejecución y de despacho de ella y decreto del Letrado de la Administración de Justicia para su efectividad.

5.º Los artículos 703 y 704 de la Ley de Enjuiciamiento Civil recogen las especialidades del lanzamiento en juicios de desahucio.

6.º [COMPLETAR]. El artículo 549 de la Ley de Enjuiciamiento Civil permite citar en esta demanda los bienes susceptibles de embargo y las medidas de localización e investigación de los mismos.

Los artículos 539, 561.1.1.ª y 583 de la Ley de Enjuiciamiento Civil permiten su imposición al ejecutado.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito, lo admita y tenga por formulada demanda de ejecución de la sentencia n.º [NÚMERO] de fecha [FECHA] dictada en estos autos contra D./Dña. [NOMBRE Y APELLIDOS] a fin de que en su día: 1.º El tribunal dicte auto de orden general de ejecución, acordando [COMPLETAR]. 2.ª Que por el Letrado de la Administración de Justicia se decrete los medios concretos de ejecución, todo ello con expresa imposición de costas al ejecutado.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
