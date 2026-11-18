---
name: pedir-contador-partidor-nuevo-cuaderno-particional-46
description: "Redacta el escrito «Pedir al contador-partidor un nuevo cuaderno particional adaptado a la sentencia de apelación» (formulario 46 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pedir al contador-partidor un nuevo cuaderno particional adaptado a la sentencia de apelación

> Formulario 0046 del plugin **Sucesiones** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
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
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] DNI/NIE
- [ ] Nº DE COLEGIADO/A
- [ ] COLEGIO
- [ ] FECHA (5 veces)
- [ ] LUGAR
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…Dª»; «…arezco bajo la dirección letrada de Doña»; «…tencia fue recurrida en apelación por Dª»; «…y Dª»; «…, s.e.u.o. el valor actualizado sería de»; «…usantes la mitad del crédito frente a Dª»; «…las herencias como crédito a favor de Dª»

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

### Formulario 0046 · Pedir al contador-partidor un nuevo cuaderno particional adaptado a la sentencia de apelación

- Año del modelo: 2023
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 17 campos de relleno marcados en blanco; 6 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

División Herencia /

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

Dª [COMPLETAR], Procurador de los Tribunales, en nombre y representación de D. [NOMBRE Y APELLIDOS], con DNI número [DNI/NIE] tal y como consta en los presentes autos, ante el Tribunal comparezco bajo la dirección letrada de Doña [COMPLETAR], Colegiada número [Nº DE COLEGIADO/A] del Ilustre Colegio de Abogados de [COLEGIO], y como mejor en Derecho proceda,

Digo

Primero.– Que con fecha [FECHA], este Tribunal al que tengo el honor de dirigirme dictó Sentencia cuyo Fallo es del tenor siguiente:

"Apruebo parcialmente el cuaderno particional y operaciones de avalúo, división y adjudicación de los bienes hereditarios en él contenidas, elaborado por el contador-partidor Sr. [NOMBRE Y APELLIDOS], quien deberá efectuar las correcciones que se indican en el fundamento tercero de la sentencia."

Segundo.– Que dicha Sentencia fue recurrida en apelación por Dª [COMPLETAR] y Dª [COMPLETAR], habiéndose dictado Sentencia por la Ilma. Audiencia Provincial el día [FECHA], cuyo fallo estima parcialmente los recursos interpuestos por las apelantes.

Tercero.– Que siendo firme dicha Sentencia, tal y como consta en la DIOR de fecha [FECHA], a medio del presente escrito solicitamos que se dé traslado nuevamente al contador-partidor Sr. [NOMBRE Y APELLIDOS] a fin de que redacte un nuevo cuaderno particional que se adapte al contenido de la Sentencia de apelación, en el sentido siguiente:

1º.- Que se actualice la vivienda a razón de 1.080€ por cada año transcurrido desde el 30/01/2017 y proporcionalmente los períodos inferiores al año, partiendo de los 97.200€ fijados en la sentencia de instancia.

Por tanto, s.e.u.o. el valor actualizado sería de [COMPLETAR]: Z€

1.080€ x (número de meses transcurridos) = Y

Y + 97.200€ = Z

2º.- Se incluya en el activo de la herencia de ambos causantes la mitad del crédito frente a Dª [COMPLETAR] por la renta de la vivienda y plaza de garaje desde el 2/05/1995 hasta el cese de uso (que se ha producido el día [FECHA]).

Por lo tanto, s.e.u.o. se incluirá:

A= renta fijada por el organismo competente para alquileres de V.P.O.

Período a computar: 02/05/1995 hasta Y = B meses

B meses x A = crédito incluible en el activo

3º.- Se incluya en el pasivo de la herencia de ambos causantes la mitad del IBI desde el fallecimiento de los causantes, que s.e.u.o. asciende a X€.

4º.- Se incluya en el pasivo de la herencia de ambos causantes la mitad de 4.246,76€, es decir, 2.138,38€ en cada una de las herencias como crédito a favor de Dª [COMPLETAR].

AL TRIBUNAL SUPLICO que teniendo por presentado escrito, lo admita y dé trámite legal. Acuerde requerir nuevamente al contador-partidor Sr. [NOMBRE Y APELLIDOS] a fin de que redacte un nuevo cuaderno particional que se adapte a la Sentencia de apelación conforme al contenido del apartado tercero del presente escrito. Y una vez presentado el nuevo Cuaderno Particional, se nos dé traslado a fin de prestar conformidad o no con el mismo antes de proceder a su protocolización.

Es Justicia que pido en [LUGAR], a [FECHA].

Abogado/a	Procurador/a

Fdo. D./Dña. [NOMBRE Y APELLIDOS]: 	Fdo. D./Dña. [NOMBRE Y APELLIDOS]:
