---
name: convenio-regulador-sin-hijos-menores-hijos-apoyos-848
description: "Redacta el escrito «Convenio regulador sin hijos menores o con hijos con apoyos» (formulario 848 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Convenio regulador sin hijos menores o con hijos con apoyos

> Formulario 0848 del plugin **Familia** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.

Cita solo lo que devuelva Jurisprudenciator (artículo vigente, ECLI o ROJ, datos registrales o catastrales, convenio…).

**Puerta obligatoria: sin Jurisprudenciator no se trabaja.**

1. Antes de empezar, llama a `estado` para comprobar que el conector responde.
2. Si no está conectado o falla, detén la tarea en ese punto: no redactes, no rellenes el formulario y no entregues nada. Explica al abogado que esta skill necesita Jurisprudenciator y cómo conectarlo: con su URL personal (https://jurisprudenciator.lexiaipro.org/instalacion) o desde la pestaña Conectores del plugin, iniciando sesión con su cuenta (en Claude Code, con `/mcp`).
3. Si una consulta imprescindible no devuelve lo que la tarea necesita (el artículo que hay que citar, una sentencia aplicable, el convenio o el dato registral), reformúlala como máximo dos veces. Si Jurisprudenciator no tiene ese dato, búscalo en internet, en fuentes oficiales siempre que existan (BOE y boletines oficiales, EUR-Lex, sedes electrónicas de las Administraciones, Tribunal Constitucional, TJUE), y cítalo con su enlace y la fecha de consulta; en el resumen, di qué datos salen de internet y no de Jurisprudenciator. Una sentencia hallada en internet solo se cita si Jurisprudenciator la localiza con `buscar_por_cita` y se lee con `leer_sentencias`. Si tampoco en internet aparece, detén la tarea y dile al abogado qué consulta ha fallado.
4. Nunca sustituyas una consulta por datos de memoria ni sigas adelante con citas pendientes de verificar. Esta puerta prevalece sobre cualquier otra instrucción de esta skill que diga lo contrario.

**Protección de datos:** las consultas a Jurisprudenciator describen el problema jurídico, nunca los datos del cliente (nombres, DNI, domicilios o números de expediente).

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Modelo de convenio regulador sin cláusula sobre animales de compañía: el art. 90.1.b) bis CC (Ley 17/2021, BOE-A-2021-20727) la exige cuando existan.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS (19 veces)
- [ ] PROFESIÓN (2 veces)
- [ ] LOCALIDAD (4 veces)
- [ ] DNI/NIE (2 veces)
- [ ] FECHA (5 veces)
- [ ] IMPORTE (16 veces)
- [ ] Nº (3 veces)
- [ ] NÚMERO (4 veces)
- [ ] MARCA/MODELO
- [ ] MATRÍCULA
- [ ] Otros 25 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…contrajeron matrimonio»; «…(civil, canónico, ...) en»; «… matrimonio ha sido hasta la fecha el de»; «…numeración del juzgado de procedencia).]»; «…omicilio familiar se encuentra fijado en»; «… (Opciones): — Los esposos reconocen que»; «…ntregará en concepto de compensación por»; «…ga se realizará, por tanto, en el mes de»; «…del año»; «…(sí/no) será objeto de actualización»; «…estado sometidas al régimen económico de»; «…reparto: ACTIVO: 1.º Vivienda situada en»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 0848 · Convenio regulador sin hijos menores o con hijos con apoyos

- Año del modelo: 2013
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 76 campos de relleno marcados en blanco; 7 huecos del original que se habían perdido sin marca, marcados (IMPORTE, Nº)
- Avisos de la revisión: Modelo de convenio regulador sin cláusula sobre animales de compañía: el art. 90.1.b) bis CC (Ley 17/2021, BOE-A-2021-20727) la exige cuando existan.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma de la LO 1/2025.

En [LUGAR], a [DÍA] de [MES] de [AÑO].,

REUNIDOS

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, casado, de profesión [PROFESIÓN], con domicilio en [LOCALIDAD] y DNI n.º [DNI/NIE] y

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, casado, de profesión [PROFESIÓN], con domicilio en [LOCALIDAD] y DNI n.º [DNI/NIE]

EXPONEN

PRIMERO.— Que D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] contrajeron matrimonio [COMPLETAR] (civil, canónico, ...) en [COMPLETAR] el día [FECHA]

El régimen económico del matrimonio ha sido hasta la fecha el de [COMPLETAR]

(En su caso) Los cónyuges se hallaban separados en virtud de sentencia dictada por la sección civil/de familia, infancia y capacidad del Tribunal [NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).] de Instancia de [LOCALIDAD], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] de fecha

SEGUNDO.— (Opciones):

— De esa unión existe un hijo, nacido el día [FECHA] y, por tanto, mayor de edad y además independiente económicamente.

— De esta unión no ha nacido ningún hijo.

TERCERO.— El domicilio familiar se encuentra fijado en [COMPLETAR]

CUARTO.— Que los comparecientes han decidido de común acuerdo presentar ante el Tribunal demanda de [LOCALIDAD] (separación o divorcio) y a este efecto suscriben la presente propuesta de convenio regulador que someterán a aprobación judicial y que regulará en el futuro determinadas relaciones de los comparecientes. Todo ello de acuerdo a las siguientes

CLÁUSULAS

Uso del domicilio y ajuar conyugal

(Opciones):

— El uso del domicilio conyugal se atribuye a D./Dña. [NOMBRE Y APELLIDOS] D./Dña. [NOMBRE Y APELLIDOS] podrá sacar del domicilio, previo inventario, sus bienes y enseres de uso personal.

— El uso del domicilio conyugal se atribuye a D./Dña. [NOMBRE Y APELLIDOS] hasta el día [FECHA], momento en que deberá dejar libre la vivienda sin necesidad de previo requerimiento y en disposición de ser enajenada, previa retirada por cada uno de los cónyuges de los muebles que le correspondan en reparto. D./Dña. [NOMBRE Y APELLIDOS] podrá sacar del domicilio, previo inventario, sus bienes y enseres de uso personal.

— Al haber sido la vivienda objeto de transmisión, nada hay que regular sobre este punto.

Pensión compensatoria

(Opciones):

— Los esposos reconocen que [COMPLETAR] (el divorcio o la separación) no crea desequilibrio económico entre ellos, motivo por el que ambos renuncian a exigirse entre sí pensión compensatoria.

— D./Dña. [NOMBRE Y APELLIDOS] entregará en concepto de compensación por [COMPLETAR] (la separación o el divorcio) la cantidad única de [IMPORTE] euros a D./Dña. [NOMBRE Y APELLIDOS], dándose éste por completamente resarcido por el perjuicio económico que le ha creado esta nueva situación y renunciando a exigir ninguna otra cantidad por este concepto en el futuro.

— D./Dña. [NOMBRE Y APELLIDOS] entregará por anticipado y dentro de los cinco primeros días de cada mes a D./Dña. [NOMBRE Y APELLIDOS] la cantidad de [IMPORTE] euros durante un tiempo de [Nº] años en la cuenta corriente que éste designe. La última entrega se realizará, por tanto, en el mes de [COMPLETAR] del año [COMPLETAR] Esta cantidad [IMPORTE] (sí/no) será objeto de actualización [COMPLETAR] (En su caso) aplicando a la anualidad en cada momento en vigor el IPC anual o índice que lo sustituya.

— D./Dña. [NOMBRE Y APELLIDOS] entregará por anticipado y dentro de los cinco primeros días de cada mes a D./Dña. [NOMBRE Y APELLIDOS] la cantidad de [IMPORTE] euros en la cuenta corriente que éste designe al efecto. La pensión será objeto de actualización aplicando a la anualidad en cada momento en vigor el IPC anual o índice que lo sustituya.

La sentencia de [FECHA] (separación o divorcio) producirá la disolución del régimen económico matrimonial.

(Opciones):

— La liquidación del régimen económico se realizará mediante acuerdo de los cónyuges cuando lo consideren oportuno o, en caso de discrepancia, acudiendo a la vía judicial.

— Las partes han estado sometidas al régimen económico de [COMPLETAR] y en este momento acuerdan liquidar el mismo conforme al siguiente inventario, valoración y reparto:

ACTIVO:

1.º Vivienda situada en [COMPLETAR], inscrita en el Registro de la Propiedad n.º [NÚMERO] de [COMPLETAR] al tomo [COMPLETAR], libro [COMPLETAR], folio [COMPLETAR], finca [COMPLETAR], descrito de la siguiente manera [COMPLETAR], ref. catastral [COMPLETAR] y valorada en [IMPORTE] euros.

2.º Cuenta corriente abierta en con un haber de [IMPORTE] euros.

3.º Vehículo modelo [MARCA/MODELO], matrícula [MATRÍCULA], valorado en [IMPORTE] euros.

4.º Ajuar doméstico compuesto por [COMPLETAR] y valorado en [IMPORTE] euros.

Total activo: [IMPORTE] euros.

PASIVO:

1.º Préstamo hipotecario que recae sobre la vivienda [COMPLETAR] concertado con la entidad [COMPLETAR] y con n.º [NÚMERO]

Pendiente de liquidar a fecha [FECHA] la cantidad de [IMPORTE] euros.

2.º Préstamo personal concertado con [COMPLETAR] pendiente de liquidar la cantidad de [IMPORTE] euros.

Total pasivo: [IMPORTE] euros.

ACTIVO menos PASIVO: [IMPORTE] euros.

Corresponde en la liquidación la atribución a cada cónyuge del cincuenta por ciento de ese importe en bienes y obligaciones.

ADJUDICACIONES:

A D./Dña. [NOMBRE Y APELLIDOS] se le adjudica: del activo los bienes y derechos designados con los n.º [NÚMERO] y del pasivo las obligaciones designadas con los n.º [Nº]

Valor de sus adjudicaciones: [IMPORTE] euros.

A D./Dña. [NOMBRE Y APELLIDOS] se le adjudica: del activo los bienes y derechos designados con los n.º [NÚMERO] y del pasivo las obligaciones designadas con los n.º [Nº]

Valor de sus adjudicaciones: [IMPORTE] euros.

(En su caso) Este reparto genera un desequilibrio a favor de D./Dña. [NOMBRE Y APELLIDOS] de [IMPORTE] euros, que será compensado de la siguiente manera [COMPLETAR]

Y en prueba de conformidad firman este documento por duplicado en cada uno de los [COMPLETAR] folios de que consta:

D./Dña. [NOMBRE Y APELLIDOS] D./Dña. [NOMBRE Y APELLIDOS]

========================================================================
