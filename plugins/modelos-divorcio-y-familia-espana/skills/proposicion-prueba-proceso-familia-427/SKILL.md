---
name: proposicion-prueba-proceso-familia-427
description: "Redacta el escrito «Proposición de prueba en proceso de familia» (formulario 427 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Proposición de prueba en proceso de familia

> Formulario 0427 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] NÚMERO (5 veces)
- [ ] COLEGIO
- [ ] FECHA (4 veces)
- [ ] LOCALIDAD (4 veces)
- [ ] LUGAR
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ales, en nombre y representación de Doña»; «…o examen de los progenitores y del menor»; «…responda se certifique en relación a Don»; «…ona autorizada. 2.- Se requiera al BANCO»; «…activo financiero que figure a nombre de»; «…rsonas físicas (IRPF) presentada por Don»; «…tificado de vida laboral completa de Don»; «…a actualidad. 4.- Se oficie a la EMPRESA»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 293, 335, 339 y 440 LEC

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

### Formulario 0427 · Proposición de prueba en proceso de familia

- Año del modelo: 2018
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 26 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de proposición de prueba en proceso de familia formulada antes de la vista.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de Doña [COMPLETAR], según tengo acreditado en los autos de separación contenciosa nº [Nº DE PROCEDIMIENTO], asistido del/la Letrado/a D./Dña. [NOMBRE Y APELLIDOS], ejerciente n.º [NÚMERO] del Iltre. Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco y, como mejor proceda en Derecho, DIGO:

Que habiendo sido notificada a esta resolución de fecha [FECHA], por la que se convoca a las partes a la celebración de la vista el día [FECHA], y sin perjuicio de los que se interesen en dicho acto procesal, al amparo de lo establecido en los arts. 293, 335, 339 y 440 LEC, propongo como prueba anticipada a la celebración del juicio la práctica de los siguientes

MEDIOS DE PRUEBA

PERICIAL PSICOSOCIAL para que por el gabinete del equipo psicosocial adscrito a ese Tribunal, previo examen de los progenitores y del menor [COMPLETAR] se dictamine sobre a quién debe otorgarse la guarda y custodia del hijo menor de edad, y cuál sea el derecho de visitas más adecuado, que haya de concederse al progenitor no custodio.

DOCUMENTAL, consistente en que:

1.- Se requiera al DEPARTAMENTO DE AVERIGUACIÓN PATRIMONIAL, para que por quien corresponda se certifique en relación a Don [COMPLETAR], con D.N.I. n.º [NÚMERO] sobre las cuentas corrientes, depósitos que el mismo pudiera tener a su nombre como titular o persona autorizada.
2.- Se requiera al BANCO [COMPLETAR], con domicilio en [LOCALIDAD], para por quien corresponda se expida certificación en la que se haga constar los saldos y movimientos que se hayan producido desde el día [FECHA] hasta el día de hoy, de cualquier cuenta, depósito, fondo de pensiones u otro tipo de activo financiero que figure a nombre de [COMPLETAR], con D.N.I. n.º [NÚMERO].

Esta parte considera perfectamente posible, pertinente y útil en el presente momento la práctica de dicha prueba, teniendo en cuenta que hay que fijar en la litis una pensión alimenticia a favor del hijo menor de edad.

3.- Se remita atento oficio a la ADMINISTRACIÓN ESTATAL DE LA AGENCIA TRIBUTARIA sita en [LOCALIDAD], para que libre y remita al Tribunal certificación de la declaración del impuesto de la renta de las personas físicas (IRPF) presentada por Don [COMPLETAR], titular del D.N.I. nº [NÚMERO], correspondientes a los cinco últimos períodos impositivos.
4.- Se remita atento oficio a la TESORERÍA GENERAL DE LA SEGURIDAD SOCIAL, sita en [LOCALIDAD], para que, por quien corresponda, se libre y remita al Tribunal certificado de vida laboral completa de Don [COMPLETAR], titular del D.N.I. n.º [NÚMERO] así como el régimen o regímenes en los que se encuentra dado de alta en la actualidad.
4.- Se oficie a la EMPRESA [COMPLETAR], con domicilio en [LOCALIDAD], para la que presta sus servicios el demandado para que libre y remita al Tribunal certificación de las percepciones de todo tipo (nómina, dietas, gratificaciones, etc.) recibidas por el mismo durante los últimos doce meses.

Por lo expuesto:

SUPLICO AL TRIBUNAL

tenga por presentado este escrito, lo admita, y acuerde lo procedente para la práctica de los medios de prueba que se proponen.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

========================================================================
