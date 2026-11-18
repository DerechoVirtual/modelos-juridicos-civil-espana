---
name: reclamacion-honorarios-abogado-propio-cliente-1103
description: "Redacta el escrito «Reclamación de honorarios del abogado a su propio cliente» (formulario 1103 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reclamación de honorarios del abogado a su propio cliente

> Formulario 1103 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO (2 veces)
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (10 veces)
- [ ] COLEGIO
- [ ] IMPORTE (7 veces)
- [ ] NÚMERO (3 veces)
- [ ] FECHA
- [ ] Nº DE DOCUMENTO
- [ ] ÓRGANO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Juicio»; «…, PLAZA N.º»; «…, correo certificado con acuse de recibo»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 35 de la LEC

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

### Formulario 1103 · Reclamación de honorarios del abogado a su propio cliente

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 27 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (IMPORTE, Nº DE DOCUMENTO, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio [COMPLETAR] n.º [Nº DE PROCEDIMIENTO]/[AÑO]

Jura de cuentas de abogado

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

PARA EL LETRADO DE LA ADMINISTRACIÓN DE JUSTICIA

D./Dña. [NOMBRE Y APELLIDOS], Letrado del Iltre. Colegio de Abogados de [COLEGIO] y de D./Dña. [NOMBRE Y APELLIDOS], según tengo debidamente acreditado en el procedimiento referenciado, ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que mediante el presente escrito, y amparándome en lo dispuesto en el art. 35 de la LEC, promuevo RECLAMACIÓN DE CUENTA DE ABOGADO frente a D./Dña. [NOMBRE Y APELLIDOS], con domicilio en

en atención a los siguientes

ANTECEDENTES Y PRESUPUESTOS

Mi cliente D./Dña. [NOMBRE Y APELLIDOS], (demandante o demandado) en este procedimiento, no ha hecho efectiva la minuta girada por mi actuación en este proceso, por lo que mediante el presente escrito declaro formalmente que me es debida y que no se me ha satisfecho la suma de [IMPORTE] euros en concepto de honorarios devengados en la tramitación de este juicio. Acompaño como documento n.º [NÚMERO] minuta debidamente detallada.

(En su caso) Esta minuta se corresponde con el presupuesto de fecha [FECHA] que fue presentado al cliente y aceptado por él con su firma tal como se acredita con el documento n.º [Nº DE DOCUMENTO]

He requerido el pago a D./Dña. [NOMBRE Y APELLIDOS], según acredito con la copia de carta enviada mediante [ÓRGANO] (correo ordinario, fax, servicio de burofax, correo certificado con acuse de recibo [COMPLETAR]) que acompaño como documento n.º [NÚMERO],

Por ello, mediante el presente escrito y al amparo de lo dispuesto en el art. 35 de la LEC, solicito que por el Letrado de la Administración de Justicia se requiera a D./Dña. [NOMBRE Y APELLIDOS] para que me haga efectiva la suma reclamada de [IMPORTE] euros correspondiente a la minuta que me es debida, más la de [IMPORTE] euros que se consideran bastantes para cubrir las costas de este trámite, según justificamos con minuta de esta reclamación de costas que adjuntamos como documento n.º [NÚMERO] y que no incluye ejecución.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito, se sirva admitirlo y, previa la tramita- ción oportuna, acuerde lo siguiente:

1.º Dictar resolución mediante la que se requiera a D./Dña. [NOMBRE Y APELLIDOS] para que pague la suma de [IMPORTE] euros a que asciende la minuta de este letrado más otros [IMPORTE] euros que se consideran bastantes para costas, sin perjuicio de ulterior liquidación, si mediere posterior ejecución.

2.º Apercibir de ejecutar por la vía de apremio si no paga ni formula impugnación, debiendo acordarse por el Letrado de la Administración de Justicia, si se diera alguno de estos supuestos, el despacho de ejecución frente a D./Dña. [NOMBRE Y APELLIDOS] por la suma de [IMPORTE] euros a que asciende la minuta, más la de [IMPORTE] euros correspondiente a las costas del trámite, acordándose el embargo de bienes de su propiedad para cubrir dicha suma y ordenando su realización hasta la completa satisfacción del crédito del letrado firmante y las costas de este trámite.

3.º Si mediare impugnación, previos los trámites oportunos, dictar en su día decreto determinando como debida la cantidad que se reclama requiriendo bajo apercibimiento de apremio a D./Dña. [NOMBRE Y APELLIDOS] para que me haga efectiva en plazo de cinco días la suma resultante más las costas.

Todo ello con expresa imposición de las costas de este trámite, en todo caso, a D./Dña. [NOMBRE Y APELLIDOS]

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
