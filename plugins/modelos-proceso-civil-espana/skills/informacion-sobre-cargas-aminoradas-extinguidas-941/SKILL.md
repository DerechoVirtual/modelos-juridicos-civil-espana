---
name: informacion-sobre-cargas-aminoradas-extinguidas-941
description: "Redacta el escrito «Información sobre cargas aminoradas o extinguidas» (formulario 941 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Información sobre cargas aminoradas o extinguidas

> Formulario 0941 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] SEDE (2 veces)
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] CALLE
- [ ] NÚMERO (3 veces)
- [ ] Nº (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 15 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…sita en C/ [CALLE] de»; «…de»; «…de [COMPLETAR] al tomo»; «…de [COMPLETAR] al tomo [COMPLETAR] libro»; «…libro [COMPLETAR] folio»; «…folio [COMPLETAR] n.º [Nº] de finca»; «… sobre el referido inmueble: 1. Hipoteca»; «…. 2. Anotación preventiva de embargo»; «…etalle: 1.º Oficio dirigido a la entidad»; «…domiciliada en»; «…, mayor de edad, y domiciliado en»; …

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 657 de la LEC

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

### Formulario 0941 · Información sobre cargas aminoradas o extinguidas

- Año del modelo: 2013
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 30 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Ejecución nº [Nº DE PROCEDIMIENTO]/[AÑO].

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR].

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, interviniendo en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS] según tengo acreditado en los autos referenciados, ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que en la tramitación de los presentes autos viene acordado el embargo de la vivienda propiedad del demandado D./Dña. [NOMBRE Y APELLIDOS] sita en C/ [CALLE] de [COMPLETAR], e inscrita en el Registro de la Propiedad n.º [NÚMERO] de [COMPLETAR] al tomo [COMPLETAR] libro [COMPLETAR] folio [COMPLETAR] n.º [Nº] de finca [COMPLETAR].

Habiéndose expedido por el Sr. Registrador titular del Registro de la Propiedad referenciado en el párrafo anterior certificación de dominio y cargas, de dicha certificación se desprende la existencia de las siguientes cargas y gravámenes que pesan sobre el referido inmueble:

1. Hipoteca [COMPLETAR].

2. Anotación preventiva de embargo [COMPLETAR].

Interesa al derecho de esta parte, y así lo solicitamos al amparo de lo dispuesto en el art. 657 de la LEC, que por el Letrado de la Administración de Justicia se dirija requerimiento a los titulares de los créditos que aparecen garantizados mediante dichas cargas y gravámenes para que informen cumplidamente de la situación de sus créditos, comunicando las siguientes circunstancias:

1.º Si los créditos subsisten o han resultado extinguidos.

2.º En caso de subsistencia, qué cantidad queda pendiente de pago, la fecha del vencimiento y los plazos y condiciones en que debe efectuarse.

3.º Si el crédito se encuentra vencido y no pagado, el interés moratorio que devenga por día de retraso, con expresión de la cantidad de los intereses ya devengados.

En consecuencia, solicito que se expidan los siguientes oficios a los titulares de los créditos garantizados con las cargas y gravámenes relacionadas según este detalle:

1.º Oficio dirigido a la entidad [COMPLETAR] domiciliada en [COMPLETAR], para que informe de la situación de su crédito hipotecario frente al ejecutado D./Dña. [NOMBRE Y APELLIDOS], reseñada con el n.º [NÚMERO] de la anterior relación de cargas y gravámenes.

2.º Oficio dirigido a D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, y domiciliado en [COMPLETAR], para que informe de la situación de su crédito frente al ejecutado D. garantizado con anotación preventiva de embargo letra A) practicada sobre la vivienda [COMPLETAR] en la ejecución seguida con n.º [Nº] de autos [COMPLETAR] de la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], reseñado con el n.º [NÚMERO] de la anterior relación de cargas y gravámenes.

A efectos de garantizar la eficacia de la diligencia, interesamos que en los oficios que se libren se señale el plazo prudencial que se determine para la contestación de los titulares de los créditos a quienes se dirijan dichos oficios.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito, lo admita y, en su virtud, acuerde el Letrado de la Administración de Justicia expedir los oficios que se dejan solicitados para que sus destinatarios informen sobre la situación de los créditos garantizados con cargas y gravámenes con que aparece gravada la vivienda embargada en la presente ejecución, a fin de que contesten, a las cuestiones sobre la situación de dichos créditos que se dejan detalladas en el presente escrito, entregando los oficios que se libren al Procurador firmante para que cuide de su diligenciamiento.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
