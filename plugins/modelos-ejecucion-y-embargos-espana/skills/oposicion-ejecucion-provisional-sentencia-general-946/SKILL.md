---
name: oposicion-ejecucion-provisional-sentencia-general-946
description: "Redacta el escrito «Oposición a la ejecución provisional de sentencia (general)» (formulario 946 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición a la ejecución provisional de sentencia (general)

> Formulario 0946 del plugin **Ejecución civil** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO (2 veces)
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] FECHA (3 veces)
- [ ] NÚMERO (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…roceda en derecho DIGO: Que con fecha de»; «…resente asunto concurre la circunstancia»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 528 de la LEC
- art. 529.1 de la LEC
- art. 529 de la LEC
- art. 528.2 LEC
- art. 528.2 de la LEC

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

### Formulario 0946 · Oposición a la ejecución provisional de sentencia (general)

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 14 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Ejecución provisional n.º [Nº DE PROCEDIMIENTO]/[AÑO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales, en nombre de D./Dña. [NOMBRE Y APELLIDOS] según tengo debidamente acreditado en el procedimiento principal, ante el Tribunal comparezco bajo la dirección del Letrado D./Dña. [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO:

Que con fecha de [COMPLETAR] se me ha notificado el auto de fecha [FECHA] mediante el que se acuerda despachar la ejecución provisional de la sentencia recaída en estos autos y se concede a esta parte plazo para formalizar oposición a la misma.

Dentro de plazo legal y al amparo de lo dispuesto en el art. 528 de la LEC, formalizo mediante el presente escrito OPOSICIÓN A LA DEMANDA EJECUTIVA EN SOLICITUD DE EJECUCIÓN PROVISIONAL de la sentencia n.º [NÚMERO] de fecha [FECHA] formulada por la representación procesal de D./Dña. [NOMBRE Y APELLIDOS], oponiéndome a la ejecución provisional despachada, y sentando como correlativos a los de la demanda ejecutiva que ha motivado tal ejecución los siguientes

HECHOS

 (Rebatir o puntualizar los hechos aducidos en la demanda ejecutiva y aportar documentos que apoyen el relato fáctico alternativo. Aducir hechos que apoyen la pretensión de dejar sin efecto la ejecución provisional. Aportar documentos de apoyo).

A los hechos antecedentes resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

CONFORME CON LOS CORRELATIVOS SOBRE COMPETENCIA Y LEGITIMACIÓN.

REQUISITOS PROCESALES Y TRÁMITE:

• Se presenta este escrito de oposición a la ejecución provisional dentro de los cinco días siguientes a la notificación de la resolución por la que se acuerda el despacho de la ejecución provisional (art. 529.1 de la LEC).

• Ha sido ya despachada oposición provisional, por lo que cabe formalizar el presente escrito de oposición, a tenor de lo dispuesto en el inciso 1 del art. 528 de la LEC.

• Debe seguirse para sustanciar esta oposición el trámite previsto en el art. 529 de la LEC.

CAUSAS DE OPOSICIÓN.—(Téngase en cuenta que las causas de oposición están tasadas y solo cabe oponer las comprendidas en el art. 528.2 LEC). El art. 528.2 de la LEC determina que «la oposición a la ejecución provisional podrá fundarse únicamente, y sin perjuicio de lo establecido en el apartado 4 de este artículo en las siguientes causas: 1.ª En todo caso, haberse despachado la ejecución provisional con infracción del artículo anterior. 2.ª Si la sentencia fuere de condena no dineraria, resultara imposible o de extrema dificultad, atendida la naturaleza de las actuaciones ejecutivas, restaurar la situación anterior a la ejecución provisional o compensar económicamente al ejecutado mediante el resarcimiento de los daños y perjuicios que se le causaren, si aquella sentencia fuese revocada.».

El n.º 4 de este artículo añade la posibilidad de oponer también el pago o cumplimiento de lo ordenado en sentencia o la existencia de pactos en el proceso para evitar la ejecución provisional.

En el presente asunto concurre la circunstancia [COMPLETAR] (desarrollar y acreditar encaje en uno de los supuestos legales anteriores).

Por todo lo expuesto,

SUPLICO AL TRIBUNAL: Tenga por presentado este escrito junto con los documentos acompañados (en su caso, y copias de todo ello), se sirva admitirlo, teniendo por formulada en tiempo y forma oposición a la ejecución provisional de la sentencia n.º [NÚMERO] de fecha [FECHA] dictada en estos autos que viene despachada, ordenando lo necesario para el impulso del trámite procedimental pertinente para en definitiva dictar auto mediante el que se declare no haber lugar a que prosiga la ejecución provisional acordada, y se acuerde que se alcen los embargos, trabas y medidas de garantía adoptados.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
