---
name: alzamiento-suspension-ejecucion-tras-desestimar-1488
description: "Redacta el escrito «Alzamiento de suspensión de ejecución tras desestimar la anulación del laudo, con indemnización» (formulario 1488 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alzamiento de suspensión de ejecución tras desestimar la anulación del laudo, con indemnización

> Formulario 1488 del plugin **Ejecución civil** · revisado el 17-11-2026.

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
- [ ] FECHA (3 veces)
- [ ] LOCALIDAD
- [ ] Nº DE PROCEDIMIENTO
- [ ] Nº DE DOCUMENTO
- [ ] IMPORTE (2 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…D»; «… por conceptos elaborada por el perito D»; «…er la caución prestada por el ejecutado.»; «…. Es justicia que pido en»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 712 LEC

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

### Formulario 1488 · Alzamiento de suspensión de ejecución tras desestimar la anulación del laudo, con indemnización

- Año del modelo: 2014
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 14 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Encabezamiento
HECHOS Y FUNDAMENTOS
Suplico
Firmas

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D [COMPLETAR] Procurador de los Tribunales obrando en nombre y representación del ejecutado D. según tengo acreditado en las actuaciones de proceso de ejecución núm. [Nº], por medio del presente escrito solicito el alzamiento de la suspensión y el resarcimiento de daños y perjuicios ocasionados por la demora, en base a los siguientes

HECHOS Y FUNDAMENTOS

Que en fecha [FECHA], por la Sala Civil y Penal del TSJ de [LOCALIDAD], se ha dictado sentencia desestimando la acción de anulación interpuesta por el ejecutado contra el laudo arbitral de fecha [FECHA], el cual es objeto del presente proceso de ejecución, acompañando testimonio de la sentencia en autos núm. [Nº DE PROCEDIMIENTO] como documento número [Nº DE DOCUMENTO], la cual es firme por no ser susceptible de recurso.

Que, al amparo de lo dispuesto en el art. 45.2 de la Ley de Arbitraje, solicito que se alce la suspensión decretada por resolución de fecha [FECHA] y que continúe este proceso de ejecución por sus trámites.

El art. 45.2 de la Ley de Arbitraje contempla el derecho del ejecutante a solicitar, en su caso, indemnización de los daños y perjuicios causados por la demora en la ejecución, a través de los cauces ordenados en los artículo 712 y siguientes de la Ley de Enjuiciamiento Civil.

En méritos de lo dispuesto en el anterior precepto, esta parte solicita que se le resarza de los daños y perjuicios ocasionados por la demora en la ejecución, derivados de no haber sido puesto en posesión del inmueble tal como establecía el laudo y de no haber percibido renta alguna en todo este periodo de tiempo, que se estiman en el importe de [IMPORTE] euros según se desprende de la liquidación que se acompaña individualizada y por conceptos elaborada por el perito D [COMPLETAR], procediéndose a su liquidación conforme a lo establecido en el art. 712 y ss. LEC, acordando la retención de la caución prestada por el ejecutado a estos efectos en tanto se sustancia y decide sobre esta cuestión incidental.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL: Que admita este escrito con el justificante del traslado a la parte ejecutado y, en méritos de las alegaciones que se vierten, se tenga por solicitado el alzamiento de la suspensión de este proceso de ejecución y en su virtud, que por el Letrado de la Administración de Justicia se dicte la correspondiente resolución y acordando:

1º) alzar la suspensión y continuar la ejecución por sus trámites.

2º) abrir el incidente contemplado en el art. 712 LEC a los efectos de liquidar los daños y perjuicios ocasionados al ejecutante que se estiman en el importe de [IMPORTE] euros según se desprende del informe que se acompaña individualizada y por conceptos elaborada por el perito D. [NOMBRE Y APELLIDOS]

3º) retener la caución prestada por el ejecutado. [COMPLETAR].

Es justicia que pido en [COMPLETAR]

Firma de abogado y procurador

========================================================================
