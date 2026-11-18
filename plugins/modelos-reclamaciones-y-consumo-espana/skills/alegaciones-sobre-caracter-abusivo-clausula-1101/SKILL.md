---
name: alegaciones-sobre-caracter-abusivo-clausula-1101
description: "Redacta el escrito «Alegaciones sobre el carácter abusivo de una cláusula» (formulario 1101 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones sobre el carácter abusivo de una cláusula

> Formulario 1101 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] NÚMERO (4 veces)
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…/»; «…, PLAZA N.º»; «…(la entidad»; «…GACIONES El título ejecutivo consiste en»; «…La cláusula sometida a valoración regula»; «…anticipado, …) y literalmente indica que»; «…Entiende esta parte que tal pacto»; «…(sí/no) tiene carácter abusivo porque»; «…; Ley 5/2019, art. 25, BOE-A-2019-3814.]»; «…ales condiciones que se establecían para»; «…(Desarrollar) Por esas razones procede»; «…cuerde dictar auto por el que se declare»

## Correcciones de la revisión (3)

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

### Formulario 1101 · Alegaciones sobre el carácter abusivo de una cláusula

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 2 puntualizaciones normativas añadidas en el texto; 21 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio ejecutivo nº [NÚMERO] / [COMPLETAR]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de [NOMBRE DEL REPRESENTADO/A] (la entidad [COMPLETAR] o de D./Dña. [NOMBRE Y APELLIDOS]), según tengo debidamente acreditado en el procedimiento referenciado, ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que con el presente escrito procedo a evacuar el trámite conferido por auto de fecha [FECHA] mediante el cual se nos da traslado por plazo de quince días para formular alegaciones sobre el posible carácter abusivo de la cláusula nº [NÚMERO] del documento respecto al cual se solicita ejecución. Esta parte … (si/no) considera que exista tal carácter abusivo según las siguientes

ALEGACIONES

El título ejecutivo consiste en [COMPLETAR] (alguno de los descritos en el art. 517.2, 4º, 5º, 6º, 7º y documentos con fuerza ejecutiva del nº 9º).

La cláusula sometida a valoración regula [COMPLETAR] (los intereses de demora, el vencimiento anticipado, …) y literalmente indica que [COMPLETAR]

Entiende esta parte que tal pacto [COMPLETAR] (sí/no) tiene carácter abusivo porque [COMPLETAR] (Opciones):

1º. Los intereses de demora superan en tres veces el interés legal del dinero [NOTA DE REVISIÓN: El límite de «tres veces el interés legal» es la redacción anterior del art. 114.3 LH; desde el 16-6-2019, para préstamos de persona física con hipoteca residencial, la demora es el remuneratorio más tres puntos (art. 25 Ley 5/2019). Para otros títulos, el criterio jurisprudencial aplicable: NO VERIFICADO. Fuente: LH art. 114, BOE-A-1946-2453; Ley 5/2019, art. 25, BOE-A-2019-3814.] [COMPLETAR]

2º. Los intereses se pactaron en relación a las especiales condiciones que se establecían para [COMPLETAR] (Desarrollar)

Por esas razones procede [COMPLETAR] (Opciones):

1º. declara la validez de las cláusulas acordando seguir adelante con la ejecución.

2º. dictar auto declarando la improcedencia de la ejecución con expresa condena en costas a la parte actora.

3º. dictar auto en el que se declaren abusivas las cláusulas nº [NÚMERO] que no deberán, por tanto, incluirse en la ejecución.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito, lo admita y acuerde dictar auto por el que se declare [COMPLETAR] (Opciones):

1º. la validez de las cláusulas acordando seguir adelante con la ejecución.

2º. la improcedencia de la ejecución con expresa condena en costas a la parte actora por el carácter abusivo de las cláusulas en las que se funda la presente ejecución.

3º. el carácter abusivo de las cláusulas nº [NÚMERO] que no deberán, por tanto, incluirse en la ejecución.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
