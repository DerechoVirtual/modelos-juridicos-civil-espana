---
name: relevo-presidencia-solicitud-1341
description: "Redacta el escrito «Relevo de la presidencia: solicitud» (formulario 1341 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Relevo de la presidencia: solicitud

> Formulario 1341 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] Nº (4 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] FECHA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…io habitual se encuentra en la ciudad de»; «…nde llevo a cabo mi actividad laboral de»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Motivo / Propiedad / Residencia tercera edad — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (1)

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

### Formulario 1341 · Relevo de la presidencia: solicitud

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 14 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (FECHA, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en la, C/, n.º [Nº], piso, y DNI n.º [Nº], ante el Tribunal comparezco y como mejor proceda en derecho, DIGO:

Que mediante el presente escrito y en aplicación del artículo 13.2 de la Ley de Propiedad Horizontal (LPH), solicito del Tribunal que acuerde el relevo en el nombramiento de Presidente de la Comunidad de la C/, n.º [Nº] de de que he sido objeto, con base en las siguientes

ALEGACIONES

[ELEGIR UNA OPCIÓN Y REDACTARLA: Motivo / Propiedad / Residencia tercera edad — el texto de cada opción no venía en el formulario original]

Mi domicilio habitual se encuentra en la ciudad de [COMPLETAR], según acredito mediante certificado de empadronamiento expedido por el Ayuntamiento de esta localidad (documento n.º [Nº DE DOCUMENTO]).

Es también en esta localidad donde llevo a cabo mi actividad laboral de [COMPLETAR], tal como justifico mediante certificado de la empresa donde trabajo (documento n.º [Nº DE DOCUMENTO]).

Aunque me encuentro al corriente del pago de cuotas de la Comunidad, según consta en los recibos que acompaño, lo cierto es que me resulta imposible acudir a las reuniones de propietarios y votar en las Juntas.

En fecha, he recibido copia del acta de la Junta celebrada el día [FECHA], en la que se procedió a la renovación de cargos directivos correspondiéndome por votación el cargo de Presidente.

Por los motivos expresados me resulta imposible llevar a efecto de forma correcta las obligaciones que la LPH impone a los Presidentes de las Comunidades de Propietarios, pues al no residir en esa vivienda no puedo ni llevar la gestión ordinaria de los elementos comunes, ni expedir las certificaciones a las que está obligado en los plazos legales ni atender a las peticiones de los vecinos.

Así las cosas, entiendo que resultaría más adecuado que tal nombramiento recayera, provisionalmente y hasta nueva votación, en cualesquiera de los siguientes vecinos que me consta que ya han desempeñado este cargo con gran provecho para el resto de los propietarios:

— D./Dña. [NOMBRE Y APELLIDOS], del piso del inmueble.

— D./Dña. [NOMBRE Y APELLIDOS], del piso del inmueble.

— D./Dña. [NOMBRE Y APELLIDOS], del piso del inmueble.

A esta parte le consta que para el cargo fui propuesto por D./Dña. [NOMBRE Y APELLIDOS], vecino del piso y D./Dña. [NOMBRE Y APELLIDOS], vecino del piso, que deberán en consecuencia ser citados a la comparecencia que prevé la ley.

Al acto del juicio de equidad deberá ser citado también el Administrador de la finca D./Dña. [NOMBRE Y APELLIDOS], con domicilio en.

En caso de oponerse temerariamente a esta pretensión, esta parte solicita que se impongan las costas a los contradictores.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y copia de todo ello, lo admita y, previos los trámites legales oportunos, incluida la comparecencia de todos los citados en este escrito, acuerde dejar sin efecto el nombramiento de Presidente de la Comunidad de Propietarios de la C/, n.º [Nº], designando provisionalmente para este cargo a cualquiera de las tres personas indicadas por esta parte.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
