---
name: oposicion-ejecucion-auto-homologa-acuerdo-mediacion-1510
description: "Redacta el escrito «Oposición a la ejecución de auto que homologa un acuerdo de mediación» (formulario 1510 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición a la ejecución de auto que homologa un acuerdo de mediación

> Formulario 1510 del plugin **Ejecución civil** · revisado el 17-11-2026.

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
- [ ] Nº
- [ ] NOMBRE Y APELLIDOS
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] Nº DE PROCEDIMIENTO
- [ ] FECHA (2 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] ÓRGANO O PERSONA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…la LO 1/2025. Procedimiento de ejecución»; «…onsta acreditado en los autos de proceso»; «…de»; «…de [COMPLETAR] de»; «…de»; «…de [COMPLETAR] de»; «…00 euros correspondiente a la cuota fija»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 556.1 de la LEC
- artículo 556.1 de la LEC
- artículos 561.2 LEC
- artículo 7.2 de la Ley 10/2012
- Ley 25/2015

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

### Formulario 1510 · Oposición a la ejecución de auto que homologa un acuerdo de mediación

- Año del modelo: 2014
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 16 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Parte
Oposición a la ejecución
HECHOS
FUNDAMENTOS DE DERECHO
Suplico
Otrosí de prueba
Otrosí de tasa
Firmas

Formulario adaptado a la reforma procesal de la LO 1/2025.

Procedimiento de ejecución [COMPLETAR]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [Nº]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D. [NOMBRE Y APELLIDOS] Procurador de los Tribunales, en nombre y representación de [NOMBRE DEL REPRESENTADO/A], parte ejecutada, según consta acreditado en los autos de proceso [COMPLETAR] número [Nº DE PROCEDIMIENTO] seguidos ante ese Tribunal del que dimana el proceso de ejecución arriba referenciado, ante el Tribunal comparezco y como mejor proceda en Derecho

DIGO:

Que dentro del plazo legal paso a formular OPOSICIÓN A LA EJECUCIÓN despachada por auto de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] con base a los siguientes:

HECHOS

PRIMERO.- La cantidad que se reclama en la demanda en ejecución del auto de homologación del acuerdo de mediación alcanzado por las partes en este proceso no resulta debida, puesto que mi representado abonó dicha cantidad el pasado día [FECHA] de [COMPLETAR] de [COMPLETAR] esto es, dentro de los veinte días posteriores a la homologación del acuerdo, tal como se acredita por resguardo de transferencia bancaria a la cuenta del ejecutante que se acompaña como documento número [Nº DE DOCUMENTO], donde consta como concepto "pago de las cantidades convenidas en proceso número ".

Por tanto, concurre el motivo contemplado en el art. 556.1 de la LEC de pago de la cantidad convenida en el acuerdo de mediación, por lo cual solicitamos que se estime la oposición, con imposición de costas al ejecutante que temerariamente ha iniciado la acción ejecutiva.

A los anteriores hechos le son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

PROCEDIMIENTO. Artículos 556, 560 y 561 LEC.

LEGITIMACIÓN. Artículo 538 LEC al ser mi mandante la parte ejecutada en el presente proceso de ejecución.

OPOSICIÓN A LA EJECUCIÓN. El artículo 556.1 de la LEC establece que el ejecutado podrá oponerse a la ejecución por escrito alegando el pago o cumplimiento de lo ordenado en la sentencia, laudo o acuerdo, que habrá de justificar documental tal como se hace con la aportación del documento número

COSTAS. Deben ser objeto de imposición al ejecutante de conformidad con lo dispuesto en los artículos 561.2 LEC.

Por lo expuesto,

SUPLICO AL TRIBUNAL: tenga por presentado este escrito con los documentos adjuntos y sus copias, se sirva admitirlos y unirlos a los autos, teniendo por formulada OPOSICIÓN A LA DEMANDA EJECUTIVA formulada por [ÓRGANO O PERSONA] contra mi principal, y, tras los trámites legales, dicte auto dejando sin efecto la ejecución despachada, mandando el inmediato alzamiento de los embargos acordados y reintegrando a mi mandante en la posición anterior a la ejecución, imponiendo las costas al ejecutante.

OTROSÍ PRIMERO DIGO: de conformidad con el artículo 560 LECiv se solicita la celebración de la vista pública a fin de que se realice la prueba que a continuación se detalla:

Por lo que, SUPLICO AL TRIBUNAL: Se proceda a la celebración de la vista pública solicitada al efecto de la práctica de la totalidad de la prueba propuesta.

OTROSÍ DIGO Que estando la presente demanda sujeta al abono de la tasa por el ejercicio de la potestad jurisdiccional fijada por la Ley 10/2012, de 20 de noviembre, modificada por RDL 3/2013 y Ley 25/2015, de 28 julio, y desarrollada por Orden HAP/2662/2012, de 13 de diciembre, siendo mi representada personas jurídica no exenta de su pago, se acompaña a la presente demanda como documento nº [Nº DE DOCUMENTO] la correspondiente autoliquidación con el ejemplar para la Administración de Justicia debidamente validado y en el que consta el pago de la cantidad de 200 euros correspondiente a la cuota fija [COMPLETAR], sin que se incluya la cuota variable prevista en el artículo 7.2 de la Ley 10/2012 al haber sido declarado inconstitucional y nulo por la STC 140/2016, de 21 de julio.

Por lo que, SUPLICO AL TRIBUNAL que tenga por hecha la anterior manifestación a los efectos pertinentes y por acompañado el documento justificativo del abono de la tasa.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma abogado y procurador.

========================================================================
