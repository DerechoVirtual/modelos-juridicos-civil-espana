---
name: modelo-normalizado-contestacion-demanda-verbal-615
description: "Redacta el escrito «Modelo normalizado de contestación a la demanda verbal» (formulario 615 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Modelo normalizado de contestación a la demanda verbal

> Formulario 0615 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NIF
- [ ] CALLE (2 veces)
- [ ] NÚMERO (3 veces)
- [ ] TELÉFONO (2 veces)
- [ ] CORREO ELECTRÓNICO
- [ ] IMPORTE (2 veces)
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «… la calle [CALLE], número [NÚMERO], piso»; «…, piso [COMPLETAR], de la localidad de»; «…, número [NÚMERO], piso»; «…, piso [COMPLETAR], de la localidad de»; «…con número de teléfono [TELÉFONO], fax»; «…y niego los restantes»

## Elecciones que hay que hacer

- domiciliado / domiciliada
- el demandante / la demandante

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS
- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS
- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS
- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 438 LEC
- artículo 438 de la LEC
- Ley 42/2015

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

### Formulario 0615 · Modelo normalizado de contestación a la demanda verbal

- Año del modelo: 2016
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (4); 3 desplegables convertidos en elección en blanco; 4 bloques de alternativas señalados; 22 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo normalizado de contestación a la demanda de juicio verbal previsto en el art. 438 LEC para los casos de juicios verbales en los que sea posible actuar sin abogado ni procurador. Los impresos normalizados deben estar en el Tribunal a disposición de los demandados y en el Decreto de admisión se les debe comunicar esa disponibilidad.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS] con DNI y NIF/CIF número [NIF], [ELEGIR: domiciliado / domiciliada] en la calle [CALLE], número [NÚMERO], piso [COMPLETAR], de la localidad de [COMPLETAR], con número de teléfono [TELÉFONO] y domicilio laboral en la calle [CALLE], número [NÚMERO], piso [COMPLETAR], de la localidad de [COMPLETAR] con número de teléfono [TELÉFONO], fax [COMPLETAR] y dirección de correo electrónico [CORREO ELECTRÓNICO] (1) (2),

FORMULO CONTESTACIÓN SUCINTA A LA DEMANDA DE JUICIO VERBAL en el procedimiento de juicio verbal n.º [NÚMERO] seguido a instancias de D./Dña. [NOMBRE Y APELLIDOS].

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

(Marque una de las siguientes opciones:)

Niego los hechos aducidos por [ELEGIR: el demandante / la demandante]

Admito alguno de los hechos aducidos por [ELEGIR: el demandante / la demandante] y niego los restantes [COMPLETAR]

Admito los hechos aducidos por el demandante y me allano a la demanda.

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

(Marque una de las siguientes opciones:)

Presento documentos y/o dictámenes periciales relativos a los hechos en que baso la contestación de la demanda. (3) (4)

No presento documentos y/o dictámenes periciales relativos a los hechos en que baso la contestación de la demanda.

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

(Marque una de las siguientes opciones:)

Estimo pertinente la celebración de vista.

No estimo pertinente la celebración de vista, solicitando que se dicte sentencia sin más trámite.

En atención a lo expuesto,

PIDO AL TRIBUNAL:

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

(Marque una de las siguientes opciones:)

Que se desestime la demanda y se me absuelva de los pedimentos en ella efectuados, con imposición de las costas procesales a la parte actora.

Que se desestime parcialmente la demanda y se me condene al pago de la cantidad de [IMPORTE], más intereses y sin expresa imposición de costas.

Que se me tenga por allanado a la demanda, estimando la misma y condenándome al pago de la cantidad de [IMPORTE], más intereses y sin expresa imposición de costas procesales.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

NOTAS DEL FORMULARIO

(1) Modelo aprobado por Acuerdo de 22 de diciembre de 2015, de la Comisión Permanente del Consejo General del Poder Judicial (BOE 28-1-2016).

La Ley 42/2015, de 5 de octubre, de reforma de la Ley de Enjuiciamiento Civil, ha introducido en el artículo 438 de la LEC la previsión de que existan a disposición de los demandados, en los casos de juicios verbales en los que sea posible actuar sin abogado ni procurador, impresos normalizados para contestar a la demanda. Dichos impresos deben estar en el Tribunal a disposición de los demandados y en el Decreto de admisión se les debe comunicar esa disponibilidad.

(2) Importante: Antes de redactar el escrito de contestación de la demanda, lea con atención la guía que han de facilitarle con este modelo.

(3) Importante: Deberá presentar con la contestación de la demanda todos los documentos y/o dictámenes periciales de que disponga relativos a los hechos alegados en el escrito-modelo de contestación.

(4) Documentación que se adjunta (en su caso):

========================================================================
