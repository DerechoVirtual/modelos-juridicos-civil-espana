---
name: apelacion-contra-auto-deniega-despacho-ejecucion-1462
description: "Redacta el escrito «Apelación contra el auto que deniega el despacho de ejecución hipotecaria» (formulario 1462 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Apelación contra el auto que deniega el despacho de ejecución hipotecaria

> Formulario 1462 del plugin **Ejecución civil** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO
- [ ] FECHA (4 veces)
- [ ] NÚMERO
- [ ] LUGAR
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…CION CIVIL DE LA AUDIENCIA PROVINCIAL DE»; «… auto denegando el despacho de ejecución»; «… constitución de hipoteca, autorizada el»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 552.2 LEC
- art. 458 LEC
- art. 685 LEC

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

### Formulario 1462 · Apelación contra el auto que deniega el despacho de ejecución hipotecaria

- Año del modelo: 2014
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 13 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Receptor
ALEGACIONES
SUPLICO AL TRIBUNAL
Firmas

Modelo de escrito interponiendo recurso de apelación contra el auto que deniega el despacho de ejecución hipotecaria.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCION CIVIL DE LA AUDIENCIA PROVINCIAL DE [COMPLETAR]

[NOTA DE REVISIÓN (comprobar): La AP no tiene «Sección Civil» como denominación legal: se cita la Sección por su número. Fuente: LOPJ arts. 80 y 82 (Audiencia Provincial, sin cambio de denominación).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], como tengo debidamente acreditado en procedimiento de ejecución hipotecaria n.º [Nº DE PROCEDIMIENTO]/[AÑO], seguido contra D./Dña. [NOMBRE Y APELLIDOS], y bajo la dirección Letrada de D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco y DIGO:

I.-Que con fecha [FECHA] se ha dictado auto denegando el despacho de ejecución [COMPLETAR] el cual ha sido notificado a esta parte en fecha [FECHA], cuya parte dispositiva es del tenor literal siguiente:

"No ha lugar a despachar ejecución en los términos propuestos por el Procurador Donen nombre y representación de Donpor no aportar la letra de cambio cuyo pago garantiza la hipoteca que pretende ejecutar, sin perjuicio de que presente nueva demanda ejecutiva aportando la letra de cambio garantizada por la hipoteca"

II.-Que el auto que se impugna es apelable directamente al amparo del art. 552.2 LEC.

III.-Que entendiendo que dicha resolución no es ajustada a derecho, dicho sea con los debidos respetos y en términos de defensa, por medio del presente escrito interpongo contra la misma RECURSO DE APELACIÓN impugnando el pronunciamiento denegatorio del despacho de la ejecución.

IV.-Que cumpliendo la exigencia del art. 458 LEC, se hace constar que la base impugnatoria del presente recurso descansa en las siguientes:

ALEGACIONES

Se cumplen todos los requisitos legales para poder ejercitar la acción hipotecaria al no resultar exigible acompañar la letra de cambio para iniciar la ejecución, puesto que nos encontramos ante un reconocimiento de deuda con garantía hipotecaria para cuyo pago se libró la letra de cambio, siendo la escritura el verdadero título que legitima el ejercicio de la acción ejecutiva (y no la letra), conteniéndose en el documento público las causas de la deuda, id est, realización de unos trabajos profesionales, y reclamarse la deuda por uno de los acreedores acreditados en la escritura de reconocimiento de deuda y no por un único poseedor de un título ejecutivo.

La cuestión esencial se reconduce así a determinar si la hipoteca se constituyó para garantizar el pago de la deuda a que se circunscribe el reconocimiento reflejado en el título que se acompañó a la demanda ejecutiva como documento n.º [NÚMERO] o, por el contrario, en garantía de la letra de cambio preindicada, a cuyo efecto habrá de estarse a lo que resulte de la escritura pública de reconocimiento de deuda y constitución de hipoteca, autorizada el [COMPLETAR] por el Notario D./Dña. [NOMBRE Y APELLIDOS], donde se recoge en la cláusula la estipulación de que "la hipoteca se constituye para el aseguramiento del pago de la deuda total"; razonamiento que, sin necesidad de motivación adicional, comportaría la estimación del recurso, máxime cuando el art. 155 LH, al no aludir a títulos endosables —la letra de cambio es el título valor endosable por antonomasia— nunca sería aplicable, sino el art. 154 del citado texto legal, donde se contempla la constitución de hipoteca para garantizar títulos transmisibles por endoso, lo que se trae a colación a mayor abundamiento, dado el tenor paladino de lo pactado por los otorgantes en el título con cuyo basamento se postuló en la demanda ejecutiva, a la que se acompañó los documentos exigidos en el art. 685 LEC, razones que justifican a nuestro juicio la revocación del auto impugnado y que se proceda a despachar ejecución y continuar el procedimiento conforme a lo prevenido legalmente.

En virtud de lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito con sus copias lo admita y tenga por interpuesto en tiempo y forma RECURSO DE APELACIÓN contra el auto de fecha [FECHA] y, seguido que sea el legal procedimiento, se dicte auto en el que, declarando haber lugar al recurso de apelación, se acuerde el despacho de ejecución en los términos solicitados en nuestra demanda ejecutiva.

OTROSÍ DIGO que en cumplimiento de lo establecido en la disposición adicional decimoquinta, apartado tercero, de la Ley Orgánica del Poder Judicial, se acompaña resguardo acreditativo de haber de consignado como depósito la cantidad de 50 euros.

En su virtud,

SUPLICO AL TRIBUNAL que tenga por acreditada la consignación exigida para la admisión a trámite del presente recurso, sin perjuicio de que, en caso de estimación, disponga su devolución conforme a lo establecido en el apartado octavo de dicha disposición.

Es de Justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

========================================================================
