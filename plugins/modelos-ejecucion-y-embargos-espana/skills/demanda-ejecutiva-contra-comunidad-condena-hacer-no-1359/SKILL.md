---
name: demanda-ejecutiva-contra-comunidad-condena-hacer-no-1359
description: "Redacta el escrito «Demanda ejecutiva contra la comunidad por condena de hacer no personalísimo» (formulario 1359 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda ejecutiva contra la comunidad por condena de hacer no personalísimo

> Formulario 1359 del plugin **Ejecución civil** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO (2 veces)
- [ ] SEDE
- [ ] Nº (5 veces)
- [ ] FECHA (2 veces)
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Demanda ejecutiva De juicio»; «…de»; «…a, según exige el artículo 548 de la LEC»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 548 de la LEC
- artículo 539.2 de la LEC

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

### Formulario 1359 · Demanda ejecutiva contra la comunidad por condena de hacer no personalísimo

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 8 campos de relleno marcados en blanco; 6 huecos del original que se habían perdido sin marca, marcados (FECHA, Nº, Nº DE DOCUMENTO, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda ejecutiva

De juicio [COMPLETAR] /n.º [Nº DE PROCEDIMIENTO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [Nº]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

Que mediante el presente escrito formulo demanda ejecutiva frente a la Comunidad de Propietarios de la C/, n.º [Nº] de [COMPLETAR], condenada en Sentencia n.º [Nº] de fecha [FECHA] dictada en los autos referenciados, a fin de que, previa la tramitación oportuna, se dicte auto por el Juez despachando ejecución y decreto por el Secretario en el sentido de requerir a la condenada para que cumpla la obligación de hacer contenida en sentencia. Basamos esta pretensión en los siguientes

PRESUPUESTOS

Según exige el artículo 549 de la Ley de Enjuiciamiento Civil (LEC) hacemos constar que:

1.º El título ejecutivo en que se basa esta pretensión es la Sentencia n.º [Nº] de fecha [FECHA] dictada en autos de juicio, n.º [Nº DE PROCEDIMIENTO] por este Tribunal, cuya copia simple acompaño como documento n.º [Nº DE DOCUMENTO].

2.º La tutela ejecutiva que se pretende es el cumplimiento de la condena a la Comunidad de Propietarios de para en el plazo de. Consideramos que ese tiempo es suficiente para llevar a cabo la actuación pretendida en atención al informe pericial que obra en autos. Y en caso de que en el plazo que indicamos no se lleve a cabo la obligación recogida en el fallo, desde este momento interesamos que se nos faculte para.

3.º Aunque nos encontramos ante una obligación de hacer, en previsión de que en caso de incumplimiento por la demandada pueda transformarse en una ejecución dineraria, desde este momento designamos como bienes que puedan ser objeto de ejecución los siguientes: cuenta bancaria abierta en la entidad con n.º [Nº].

De momento se considera suficiente para hacer frente a las responsabilidades del contrario.

4.º La ejecución deberá despacharse contra la demandada Comunidad de Propietarios de.

Han transcurrido más de veinte días hábiles desde la notificación a la parte contraria de la sentencia, según exige el artículo 548 de la LEC [COMPLETAR], sin que el ejecutado haya cumplido con el fallo de la sentencia.

En aplicación del artículo 539.2 de la LEC las costas deberán imponerse al demandado.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con el documento que acompaño y copia de todo ello, admita a trámite la presente demanda ejecutiva y acuerde en su día dictar el Juez auto despachando ejecución contra la Comunidad de Propietarios de y decreto el Secretario por el que:

1.º Se le requiera para que en el plazo de proceda a cumplir con la obligación de hacer de contenida en el fallo de la sentencia del juicio principal.

2.º Apercibirle de que en el caso de que en el tiempo concedido no actúe en la forma que se le requiere, se procederá a.

3.º Condenándole, en todo caso, al pago de las costas de esta ejecución.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
