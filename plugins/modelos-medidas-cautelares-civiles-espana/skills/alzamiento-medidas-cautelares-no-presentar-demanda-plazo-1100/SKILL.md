---
name: alzamiento-medidas-cautelares-no-presentar-demanda-plazo-1100
description: "Redacta el escrito «Alzamiento de medidas cautelares por no presentar la demanda en plazo» (formulario 1100 de medidas cautelares y diligencias preliminares, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alzamiento de medidas cautelares por no presentar la demanda en plazo

> Formulario 1100 del plugin **Medidas cautelares y diligencias preliminares** · revisado el 17-11-2026.

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
- [ ] AÑO (2 veces)
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] Nº DE COLEGIADO
- [ ] COLEGIO
- [ ] FECHA (3 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Autos»; «…, PLAZA N.º»; «…vio su testimonio en autos, en los autos»; «…adoptó/aron la/s medida/s cautelar/es de»; «…y»; «…fue notificado a las partes con fecha de»; «…r la/s referidas medida/s cautelar/es de»; «…y»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 730.2 de la LEC
- artículo 135.1 de la LEC

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

### Formulario 1100 · Alzamiento de medidas cautelares por no presentar la demanda en plazo

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 16 campos de relleno marcados en blanco; 7 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE COLEGIADO, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Autos [COMPLETAR] núm. [Nº DE PROCEDIMIENTO]/[AÑO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D.ª [NOMBRE Y APELLIDOS], Procuradora de los Tribunales, interviniendo en nombre de D. [NOMBRE Y APELLIDOS], en virtud de la representación que acredito (o tengo acreditada, si ya se produjo la personación) mediante la escritura de poder que acompaño y cuya devolución solicito previo su testimonio en autos, en los autos [COMPLETAR] núm. [Nº DE PROCEDIMIENTO] seguidos a instancia de la representación procesal de D. [NOMBRE Y APELLIDOS] contra mi representado, ante el Tribunal comparezco bajo la dirección letrada del Abogado D. [NOMBRE Y APELLIDOS], colegiado núm. [Nº DE COLEGIADO] del Colegio de Abogados de [COLEGIO], y como mejor proceda en derecho DIGO:

Que mediante auto de fecha [FECHA] se acordó la adopción de la/s medida/s cautelar/es de (por ejemplo: embargo preventivo de la vivienda y depósito de cosa mueble), medida/s que fueron inmediatamente hecha/s efectiva/s(por ejemplo: con inscripción en el Registro de la Propiedad del embargo trabado y constitución de depósito en).

Mediante el presente escrito, y en nombre de mi representado, solicito la revocación y alzamiento de la/s medida/s cautelar/es referida/s en el párrafo anterior, acordada mediante el auto de fecha [FECHA] Apoyo esta solicitud en los siguientes

ANTECEDENTES Y FUNDAMENTOS

Mediante auto de fecha [FECHA] dictado en estos autos se adoptó/aron la/s medida/s cautelar/es de [COMPLETAR] y [COMPLETAR] antes mencionada/s.

Dicho auto fue notificado a las partes con fecha de [COMPLETAR]

La solicitud de adopción de la medida a que nos venimos refiriendo se formuló con antelación a la presentación de demanda y al amparo de lo autorizado en el artículo 730.2 de la LEC.

Determina el precepto citado en el ordinal anterior —artículo 730.2 de la LEC—, para el supuesto de presentación de la solicitud de medidas con anterioridad a demanda, que «En este caso, las medidas que se hubieran acordado quedarán sin efecto si la demanda no se presentare ante el mismo Tribunal que conoció de la solicitud de aquéllas en los veinte días siguientes a su adopción. El Letrado de la Administración de Justicia, de oficio, acordará mediante decreto que se alcen o revoquen los actos de cumplimiento que hubieran sido realizados, condenará al solicitante en las costas y declarará que es responsable de los daños y perjuicios que haya producido al sujeto respecto del cual se adoptaron las medidas».

Han transcurrido más de veinte días hábiles —y el plazo de gracia establecido en el artículo 135.1 de la LEC— desde la notificación del auto con el que se adoptaron la/s medida/s que vienen acordadas sin que el actor D. haya presentado la demanda a que dicha/s medida/s estaban condicionadas. Procede, en consecuencia, que se revoque/n y alce/n la/s medida/s acordada/s.

Como consecuencia de la adopción de tal/es medida/s cautelar/es se han irrogado a mi representado graves daños y perjuicios, consistentes en (detallar y desarrollar).

Por todo lo expuesto,

Suplico al Tribunal que tenga por presentado este escrito (en su caso: poder, documentos) y copias de todo ello, se sirva admitirlo teniendo por formalizada solicitud de revocación y alzamiento de la/s medida/s cautelar/es, y en su virtud dicte resolución mediante la que se acuerde revocar y alzar la/s referidas medida/s cautelar/es de [COMPLETAR] y [COMPLETAR] que viene/n acordada/s, imponiendo las costas del incidente al actor D. [NOMBRE Y APELLIDOS] y acordando, también, el pago a mi representado de los daños y perjuicios que tal/es medida/s le hayan ocasionado.

Por ser Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
