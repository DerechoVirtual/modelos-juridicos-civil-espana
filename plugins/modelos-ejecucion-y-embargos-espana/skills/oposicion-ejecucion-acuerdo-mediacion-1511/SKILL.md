---
name: oposicion-ejecucion-acuerdo-mediacion-1511
description: "Redacta el escrito «Oposición a la ejecución de un acuerdo de mediación» (formulario 1511 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición a la ejecución de un acuerdo de mediación

> Formulario 1511 del plugin **Ejecución civil** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] FECHA (6 veces)
- [ ] IMPORTE
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 22 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…rado de la Administración de Justicia de»; «…que acompaño»; «…de»; «…de [COMPLETAR] de»; «…de»; «…de [COMPLETAR] de»; «…de»; «…de [COMPLETAR] de»; «… como representante legal de la sociedad»; «…de»; «…de [COMPLETAR] de»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 556 y 559 de la LEC
- artículo 559.1 de la LEC

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

### Formulario 1511 · Oposición a la ejecución de un acuerdo de mediación

- Año del modelo: 2014
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 32 campos de relleno marcados en blanco; 4 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Parte
Oposición a la ejecución
HECHOS
FUNDAMENTOS DE DERECHO
Suplico
Firmas

Formulario adaptado a la reforma procesal de la LO 1/2025.

PROCEDIMIENTO DE EJECUCIÓN

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D. [NOMBRE Y APELLIDOS] Procurador de los Tribunales, en nombre y representación de D. [NOMBRE Y APELLIDOS], parte ejecutada en el procedimiento de ejecución arriba referenciado, según acredito mediante designación apud acta realizada ante el Letrado de la Administración de Justicia de [COMPLETAR] que acompaño [COMPLETAR], ante el Tribunal comparezco y como mejor proceda en Derecho

DIGO:

1) Que el pasado día [FECHA] de [COMPLETAR] de [COMPLETAR] mi representado ha sido notificado del auto despachando ejecución de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] en virtud de escritura elevando el acuerdo de mediación de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] y siendo parte ejecutante

2) Que, al amparo de lo dispuesto en el artículo 556 y 559 de la LEC y dentro del plazo establecido, por medio del presente escrito formulo OPOSICIÓN A LA EJECUCIÓN, por defectos procesales y por motivos de fondo, y ello en base a los siguientes:

HECHOS

PRIMERO.- Mi representado carece de la representación con que se le demanda como representante legal de la sociedad [COMPLETAR], sin que el mismo tenga dicho carácter, teniendo en cuenta que desde hace más de seis meses mi mandante no ostenta cargo de representación alguno en la sociedad, ya que dejó de ostentar el cargo de administrador único y socio desde fecha [FECHA] de [COMPLETAR] de [COMPLETAR], tal y como se acredita mediante la aportación de la Escritura Pública otorgada ante el Notario de [COMPLETAR], D. [NOMBRE Y APELLIDOS],que se aporta como documento número

SEGUNDO.- La deuda objeto de reclamación que fue convenida en el acuerdo de mediación que se pretende ejecutar, fue objeto de transacción en escritura pública de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] donde se englobaban las diferentes deudas existentes con el ejecutante y se convenía el pago de las mismas mediante plazos mensuales de [IMPORTE] euros, tal y como se acredita mediante la aportación de la Escritura Pública otorgada ante el Notario de [COMPLETAR], D. [NOMBRE Y APELLIDOS],que se aporta como documento número [Nº DE DOCUMENTO], los cuales han venido siendo cumplidos puntualmente (acompaño como documentos [COMPLETAR] justificantes de pago de los plazos mensuales desde el [FECHA] de [COMPLETAR] de [COMPLETAR] hasta [COMPLETAR] de [COMPLETAR] de [COMPLETAR]).

A los anteriores hechos le son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

PROCEDIMIENTO:Artículos 556, 559 y 560 de la LEC, no entendiendo necesaria la celebración de vista por quedar acredita la oposición por los documentos aportados.

LEGITIMACIÓN:Artículo 556.1 LEC, al ser parte ejecutada en el presente proceso de ejecución.

OPOSICIÓN A LA EJECUCIÓN: MOTIVOS PROCESALES: Es de aplicación la causa primera del artículo 559.1 de la LEC al carecer mi representado del carácter o representación con que se demanda. En este caso, concurre dicho defecto procesal puesto que, como indica el AAP Madrid, Sec. 13ª, 9-12-2010 (Rec. 562/2009), la carencia de carácter del ejecutado está expresamente contemplada como causa de oposición por defectos o motivos procesales en el art. 559.1,1º de la L.E.C. y se refiere sustancialmente a aquellos supuestos en los que la demanda se ha interpuesto correctamente contra la entidad demandada, pero el demandante incurre en el error de atribuir el carácter de representante de la misma a quien no lo ostenta.

OPOSICIÓN A LA EJECUCIÓN: MOTIVOS DE FONDO: Es de aplicación el art. 556.1.II de la LEC al existir una transacción entre las partes, formalizada en el documento público que se aporta como documento……, la cual impide el ejercicio de la ejecución forzosa pretendida de contrario.

COSTAS:Artículos 559.2 y 560 LEC, debiendo imponerse al ejecutante.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Tenga por presentado este escrito, documentos y copias, se sirva admitirlos y unirlos a autos, teniendo por formulada, en tiempo y forma, oposición a la demanda ejecutiva instada de contrario y, previa su sustanciación, estime la oposición deducida y proceda a dictar auto dejando sin efecto la ejecución despachada, condenando en costas al ejecutante.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma Abogado y Procurador

========================================================================
