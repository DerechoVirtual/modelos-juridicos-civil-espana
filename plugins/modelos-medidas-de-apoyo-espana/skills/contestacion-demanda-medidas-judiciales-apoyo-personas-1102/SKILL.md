---
name: contestacion-demanda-medidas-judiciales-apoyo-personas-1102
description: "Redacta el escrito «Contestación a la demanda de medidas judiciales de apoyo a personas con discapacidad» (formulario 1102 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a la demanda de medidas judiciales de apoyo a personas con discapacidad

> Formulario 1102 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] Nº
- [ ] AÑO (2 veces)
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] NÚMERO (2 veces)
- [ ] FECHA
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 15 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…promovida por»; «…, la Entidad»; «…rio se afirma que mi representado padece»; «…sado en varias ocasiones tratamiento por»; «…;consideró que»; «…l demandado es la del indicado centro de»; «… adopción de medidas judiciales de apoyo»; «…asaría a quien se designara como curador»; «…resentantede la persona con discapacidad»; «…tulación De forma activa está legitimado»; «…l Ministerio Fiscal, el cónyuge, el hijo»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 753 de la LEC
- art. 757.2 de la LEC
- art. 749 de la LEC
- art. 249 del CC
- art. 394 de la LEC
- art. 759 de la LEC

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

### Formulario 1102 · Contestación a la demanda de medidas judiciales de apoyo a personas con discapacidad

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 26 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 2 huecos del original que se habían perdido sin marca, marcados (Nº, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Provisión de medidas judiciales de apoyo a personas con discapacidad n.º [Nº]/[AÑO]

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña [NOMBRE Y APELLIDOS], según acredito mediante poder notarial que acompaño, ante el Tribunal comparezco con la asistencia letrada de D./Dña [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO:

Que mediante el presente escrito procedo a CONTESTAR A LA DEMANDA en el proceso sobre adopción de medidas judiciales de apoyo a personas con discapacidad seguido en ese Tribunal con el número [NÚMERO] promovida por [COMPLETAR] (el Ministerio Fiscal, D./Dña. [NOMBRE Y APELLIDOS], la Entidad [COMPLETAR]) en el sentido de OPONERME a la misma, en atención a los siguientes:

HECHOS

De contrario se afirma que mi representado padece [COMPLETAR]

Aunque es cierto que D./Dña. [NOMBRE Y APELLIDOS] ha precisado en varias ocasiones tratamiento por [COMPLETAR], es evidente que en este momento está siguiendo de forma adecuada las pautas médicas y que su estado le permite gobernarse por sí mismo.

Así el Dr. en informe de fecha [FECHA];consideró que [COMPLETAR] (Doc. n.º [Nº DE DOCUMENTO]).

Por otro lado por desde el Hospital el Dr. llega a las siguientes conclusiones: (Doc. n.º [NÚMERO])

En definitiva la única asistencia que necesita el demandado es la del indicado centro de [COMPLETAR], sin que para ello resulte necesario la adopción de medidas judiciales de apoyo [COMPLETAR].

Entiende a esta parte que son motivos espurios los que mueven a los familiares de mi representado a promover la adopción de medidas judiciales de apoyo puesto que de esa manera el control de su patrimonio pasaría a quien se designara como curador [COMPLETAR].

Por las razones expresadas nos oponemos igualmente a la obligación de D./Dña [NOMBRE Y APELLIDOS] como representantede la persona con discapacidad [COMPLETAR].

FUNDAMENTOS DE DERECHO

Jurisdicción y competencia

Conforme con el correlativo.

Tramitación

Se seguirá el cauce del juicio verbal según prescribe el art. 753 de la LEC con las especialidades indicadas en los arts. 752 y 759 de esta norma sobre prueba, y conclusiones en la vista.

Legitimación y postulación

De forma activa está legitimado [COMPLETAR] (el Ministerio Fiscal, el cónyuge, el hijo [COMPLETAR]) en aplicación del art. 757.2 de la LEC, y de forma pasiva mi representado, que puede comparecer con su propia defensa y representación como hace en este caso, arts. 750 y 758 del mismo texto legal.

El Ministerio Fiscal, en aplicación del art. 749 de la LEC será siempre parte en estos procedimientos.

PRIMERO.— Fondo del asunto

El art. 249 del CC establece que las medidas de apoyo a las personas mayores de edad o menores emancipadas que las precisen para el adecuado ejercicio de su capacidad jurídica tendrán por finalidad permitir el desarrollo pleno de su personalidad y su desenvolvimiento jurídico en condiciones de igualdad. Estas medidas de apoyo deberán estar inspiradas en el respeto a la dignidad de la persona y en la tutela de sus derechos fundamentales. Las de origen legal o judicial solo procederán en defecto o insuficiencia de la voluntad de la persona de que se trate. Todas ellas deberán ajustarse a los principios de necesidad y proporcionalidad.

En el presente caso nos encontramos ante una persona que presenta una situación de [COMPLETAR] que puede ser tratada en centros oportunos para superar esa situación, lo que le permite gobernarse por sí mismo, siendo absolutamente desproporcionadas las medidas de apoyo pretendidas en la demanda.

Costas

En aplicación del art. 394 de la LEC deberán imponerse a la parte actora (salvo que ésta fuera el Ministerio Fiscal)

Por lo expuesto,

SUPLICO AL TRIBUNAL: que tenga por presentado este escrito, lo admita y acuerde tener por opuesta a esta parte a la adopción de medidas judiciales de apoyo y nombramiento de curador promovida por [COMPLETAR], a fin de que en su día se dicte sentencia desestimando íntegramente la demanda [COMPLETAR], (en su caso) e imponiendo las costas a la parte actora.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

OTROSÍ DIGO: que desde este momento se deja interesada la práctica de las siguientes pruebas en aplicación del art. 759 de la LEC:

1. Entrevista de mi representado por el Juzgador y por el Médico Forense de mi representado.

2.ºQue en su calidad de perito testigo sea oído en el acto del juicio el Psiquiatra Dr.

NUEVAMENTE SOLICITO: la práctica de las anteriores pruebas para acreditar la situación de mi representado, por ser justicia que pido en mismo lugar y fecha.

========================================================================
