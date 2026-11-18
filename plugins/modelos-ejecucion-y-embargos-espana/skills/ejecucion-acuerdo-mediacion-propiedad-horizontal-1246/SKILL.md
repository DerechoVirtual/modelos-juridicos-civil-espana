---
name: ejecucion-acuerdo-mediacion-propiedad-horizontal-1246
description: "Redacta el escrito «Ejecución de acuerdo de mediación en propiedad horizontal» (formulario 1246 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Ejecución de acuerdo de mediación en propiedad horizontal

> Formulario 1246 del plugin **Ejecución civil** · revisado el 17-11-2026.

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

- [ ] SEDE (2 veces)
- [ ] NOMBRE Y APELLIDOS (8 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] NIF
- [ ] FECHA (3 veces)
- [ ] LOCALIDAD
- [ ] DNI/NIE
- [ ] NÚMERO (2 veces)
- [ ] Nº (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…o de la Comunidad de Propietarios»; «… ante el mediador/organismo de mediación»; «…l acuerdo el propietario ahora demandado»; «…se comprometía a»; «…l que es titular el demandado situado en»; «…, finca registral»; «….2.2.º de la Ley de Enjuiciamiento Civil»; «…lo 548 de la Ley de Enjuiciamiento Civil»; «…ión de Justicia para su efectividad. 4.º»; «…amos para el caso de resultar necesarios»; «…que el ejecutado cumpla su obligación de»; «…ar conforme se le exige, se le impondrán»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Ley 5/2012

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

### Formulario 1246 · Ejecución de acuerdo de mediación en propiedad horizontal

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 35 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Ejecución de acuerdo de mediación

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de [NOMBRE DEL REPRESENTADO/A] D./Dña. [NOMBRE Y APELLIDOS] o de la Comunidad de Propietarios [COMPLETAR], con CIF nº [NIF], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, ante el Tribunal comparezco bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO:

Que mediante el presente escrito formulo demanda ejecutiva interesando que se despache la ejecución del acuerdo de mediación de fecha [FECHA] realizado ante el mediador/organismo de mediación [COMPLETAR] y protocolizado en fecha [FECHA] ante el Notario de esta ciudad D./Dña. [NOMBRE Y APELLIDOS] frente a D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD] y DNI n.º [DNI/NIE] a fin de que se dicte por el Tribunal auto conteniendo orden general de ejecución y de despacho de ella conforme a lo acordado en dicho acuerdo, y por el Letrado de la Administración de Justicia se decrete lo necesario para su efectividad. Basamos nuestra pretensión en los siguientes:

HECHOS

 Se hace constar que se presenta como documento nº 1 índice numerado de los documentos que acompañan a este escrito.

Acompaño como documento n.º [NÚMERO] acuerdo de mediación suscrito entre mi representado y el ahora demandado suscrito por ambos y por quien realizó la mediación D./Dña. [NOMBRE Y APELLIDOS]

Como documento n.º [NÚMERO] se acompaña escritura pública que lo protocoliza.

Como se puede comprobar en tal acuerdo el propietario ahora demandado [COMPLETAR] se comprometía a [COMPLETAR].

Ha transcurrido el plazo para ejecutar voluntariamente lo pactado sin que se haya llevado a efecto, razón por la que nos vemos obligados a acudir a la vía judicial..

Para el supuesto de que se tuviera que acudir a embargo de bienes apra llevar a cabo una ejecución subsidiaria o si debiera declararse indemnización sustitutoria desde este momento dejamos indicado como bien susceptible de embargo el inmueble del que es titular el demandado situado en [COMPLETAR], finca registral [COMPLETAR].

FUNDAMENTOS DE DERECHO

Corresponde conocer de esta ejecución a la Sección Civil del Tribunal de Instancia de [SEDE] en aplicación de los arts. 545.2 de la Ley de Enjuiciamiento Civil y 26 de la Ley 5/2012, de 6 de julio, de mediación en asuntos civiles y mercantiles

1.º El acuerdo de mediación elevado a escritura pública lleva aparejada ejecución según lo establecido en el artículo 517.2.2.º de la Ley de Enjuiciamiento Civil [COMPLETAR].

2.º Se ha cumplido el requisito del transcurso de 20 días para solicitar la ejecución, según requiere el artículo 548 de la Ley de Enjuiciamiento Civil [COMPLETAR].

3.º Los artículos 551 y 553 de la Ley de Enjuiciamiento Civil fijan que la ejecución se despachará mediante auto conteniendo orden general de despacho de ejecución y de despacho de ella y decreto del Letrado de la Administración de Justicia para su efectividad.

4.º [COMPLETAR] El artículo 549 de la Ley de Enjuiciamiento Civil permite citar en esta demanda los bienes susceptibles de embargo y las medidas de localización e investigación de los mismos, que concretamos para el caso de resultar necesarios [COMPLETAR].

5.º El auto que se dicte deberá determinar un plazo no superior a [Nº] días para que el ejecutado cumpla su obligación de [COMPLETAR] apercibiéndole expresamente de que, para el caso de no actuar conforme se le exige, se le impondrán [COMPLETAR].

Los artículos 539, 561.1.1.ª, 576.3 y 583 de la Ley de Enjuiciamiento Civil permiten su imposición al ejecutado.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito, lo admita y tenga por formulada demanda de ejecución de acuerdo de mediación de fecha [FECHA] frente a D./Dña. [NOMBRE Y APELLIDOS] a fin de que en su día:

1.º El tribunal dicte auto de orden general de ejecución instando a D./Dña. [NOMBRE Y APELLIDOS] para que cumpla en sus propios términos la obligación de [COMPLETAR] en un plazo de [Nº] días, apercibiéndole expresamente de que, para el caso de no actuar conforme se le exige, se le impondrán [COMPLETAR].

2.ª Que por el Letrado de la Administración de Justicia se decrete los medios concretos de ejecución, todo ello con expresa imposición de costas al ejecutado.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de abogado y procurador

========================================================================
