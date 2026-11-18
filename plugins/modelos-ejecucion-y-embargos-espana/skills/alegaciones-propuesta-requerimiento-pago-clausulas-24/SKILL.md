---
name: alegaciones-propuesta-requerimiento-pago-clausulas-24
description: "Redacta el escrito «Alegaciones a la propuesta de requerimiento de pago por cláusulas abusivas» (formulario 24 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones a la propuesta de requerimiento de pago por cláusulas abusivas

> Formulario 0024 del plugin **Ejecución civil** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] DNI/NIE
- [ ] LOCALIDAD
- [ ] Nº DE DOCUMENTO
- [ ] FECHA (2 veces)
- [ ] IMPORTE (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…de»; «…de [COMPLETAR] de»; «…de»; «…de [COMPLETAR] de»; «…derivada de la aplicación de la cláusula»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 815.3 de la LEC

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

### Formulario 0024 · Alegaciones a la propuesta de requerimiento de pago por cláusulas abusivas

- Año del modelo: 2024
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 18 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL/ DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

Don/Doña [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales y de [NOMBRE DEL REPRESENTADO/A], con DNI [DNI/NIE] y domicilio en [LOCALIDAD], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], ante el Tribunal comparezco y como mejor proceda en Derecho,

DIGO

PRIMERO.- Que en fecha [FECHA] de [COMPLETAR] de [COMPLETAR], mi representado/a presentó petición inicial de juicio monitorio contra D./Dña. [NOMBRE Y APELLIDOS], en reclamación del importe de [IMPORTE] euros correspondientes a las facturas no abonadas por la parte demandada a mi mandante.

SEGUNDO Que, mediante Auto de fecha [FECHA] de [COMPLETAR] de [COMPLETAR], habida cuenta que la relación contractual litigiosa se funda en un contrato celebrado entre un empresario y un consumidor y el Tribunal estima que la cantidad reclamada es calificada como abusiva, se ha planteado a mi mandante una propuesta de requerimiento de pago por importe de [IMPORTE], tras excluir de la cantidad reclamada la cuantía derivada de la aplicación de la cláusula [COMPLETAR] del contrato.

TERCERO Que, dentro del plazo legal de 10 días conferido por el artículo 815.3 de la LEC, mi mandante acepta expresamente la propuesta formulada por el Tribunal, interesando se proceda a requerir de pago a la parte demandada por dicha cantidad.

(Alternativamente,

Que, dentro del plazo legal de 10 días conferido por el artículo 815.3 de la LEC, mi mandante rechaza expresamente la propuesta formulada por el Tribunal, interesando se tenga por desistida a esta parte, que hará valer su pretensión en el correspondiente procedimiento declarativo).

En su virtud,

AL TRIBUNAL SUPLICO: Que teniendo por presentado este escrito junto con sus copias, se sirva admitirlo y, previos los trámites legales oportunos, tenga por aceptada la propuesta de reducción efectuada por el Tribunal, dictando resolución por la que se acuerde la continuación del procedimiento y el requerimiento de pago al deudor por el importe de

(Alternativamente,

AL TRIBUNAL SUPLICO: Que teniendo por presentado este escrito junto con sus copias, se sirva admitirlo y, previos los trámites legales oportunos, tenga por rechaza la propuesta de reducción efectuada por el Tribunal, dictando resolución por la que se tenga por desistida a esta parte de dicha reclamación a efectos de que pueda hacer valer su pretensión en el correspondiente procedimiento declarativo.)

OTROSÍ PRIMERO DIGO que al amparo de lo establecido en el artículo 231 de la Ley de Enjuiciamiento Civil, esta parte manifiesta expresamente su voluntad de dar el estricto cumplimiento a cuantos requisitos le resulten legalmente exigibles en el curso del presente procedimiento, en todas sus instancias e incidentes, subsanando cualquier eventual defecto en que pueda incurrir en sus actos procesales.

AL TRIBUNAL SUPLICO, que tenga por efectuada la anterior manifestación a los efectos legales oportunos.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma Letrado/aFirma Procurador/a
