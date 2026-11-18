---
name: alegaciones-arrendador-gran-tenedor-incidente-suspension-23
description: "Redacta el escrito «Alegaciones del arrendador gran tenedor en el incidente de suspensión del arrendatario» (formulario 23 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones del arrendador gran tenedor en el incidente de suspensión del arrendatario

> Formulario 0023 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Desahucio de vivienda desde el 8-10-2026: comprobar la suspensión del art. 2 RDL 29/2026 (hasta 31-12-2030; aplicable a ejecuciones en curso, DT 2.ª) y, si es por impago y el inquilino es vulnerable, la enervación extraordinaria a cargo de la Administración del art. 22.6 LEC (dos meses de suspensión; independiente de la del 22.4).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (5 veces)
- [ ] Nº (2 veces)
- [ ] Otros 20 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…de»; «…de [COMPLETAR] de»; «…de»; «…de [COMPLETAR] de»; «…a eventual vista en caso de oposición el»; «…de»; «…de [COMPLETAR] de»; «…horas y para el eventual lanzamiento el»; «…de»; «…de [COMPLETAR] de»; «…de»; …

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 3.k) de la Ley 12/2023
- artículo 441.7 de la LEC

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

### Formulario 0023 · Alegaciones del arrendador gran tenedor en el incidente de suspensión del arrendatario

- Año del modelo: 2024
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 30 campos de relleno marcados en blanco
- Avisos de la revisión: Desahucio de vivienda desde el 8-10-2026: comprobar la suspensión del art. 2 RDL 29/2026 (hasta 31-12-2030; aplicable a ejecuciones en curso, DT 2.ª) y, si es por impago y el inquilino es vulnerable, la enervación extraordinaria a cargo de la Administración del art. 22.6 LEC (dos meses de suspensión; independiente de la del 22.4).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

[NOTA DE REVISIÓN: Errata: un desahucio no corresponde a la Sección de Familia. Fuente: LO 1/2025, BOE-A-2025-76.]

Don/Doña [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales y de [NOMBRE DEL REPRESENTADO/A], representación que tengo acreditada en los presentes autos, ante el Tribunal comparezco y como mejor proceda en Derecho,

DIGO

Que, por medio del presente escrito, evacuando el trámite de alegaciones previsto en los apartados 5 y 6 del artículo 441 de la Ley de Enjuiciamiento Civil (en adelante, “LEC”), vengo a realizar las siguientes,

ALEGACIONES

PRIMERO.- En fecha [FECHA] de [COMPLETAR] de [COMPLETAR] se presentó demanda de juicio verbal de desahucio por falta de pago frente a la parte demandada.

Dicha demanda fue admitida a trámite por Decreto de [FECHA] de [COMPLETAR] de [COMPLETAR], señalándose fecha para la celebración de la eventual vista en caso de oposición el [COMPLETAR] de [COMPLETAR] de [COMPLETAR] a las [Nº] horas y para el eventual lanzamiento el [COMPLETAR] de [COMPLETAR] de [COMPLETAR] a las [Nº] horas.

SEGUNDO Que, tal como se acreditó en la demanda, mi mandante ostenta la condición de gran tenedor, al amparo de lo establecido en el artículo 3.k) de la Ley 12/2023, de 24 mayo, por el derecho a la vivienda.

TERCERO En fecha [FECHA] de [COMPLETAR] de [COMPLETAR], la parte demandada anunció que acudiría a los servicios sociales a efectos de valorar su posible situación de especial vulnerabilidad.

CUARTO Por Decreto de [FECHA] de [COMPLETAR] de [COMPLETAR] se acordó la suspensión del procedimiento hasta que las Administraciones locales en materia de vivienda y asistencia social evaluasen la situación de la parte arrendataria y emitiesen la correspondiente propuesta de medidas a adoptar para garantizar la alternativa de vivienda digna para la parte demandada.

QUINTO En fecha [FECHA] de [COMPLETAR] de [COMPLETAR] se ha dado traslado a esta parte del informe de Servicios Sociales por el cual se considera acreditada la situación de vulnerabilidad de la parte demandada.

SEXTO Esta parte muestra su disconformidad con dicho informe, por considerar no acreditada la concurrencia de una situación de vulnerabilidad.

La suma de los ingresos percibidos por la parte arrendataria supera el triple del Indicar Público de Renta de Efectos Múltiples (IPREM) mensual. A tal efecto, se hace constar que:

(completar)

SÉPTIMO Habiéndose dado estricto cumplimiento al procedimiento establecido en el artículo 441.7 de la LEC, interesa al Derecho de esta parte se declare que no existe situación de vulnerabilidad de la parte arrendataria y se proceda al inmediato alzamiento de la suspensión del procedimiento.

En su virtud,

AL TRIBUNAL SUPLICO: Que teniendo por presentado este escrito, se sirva admitirlo y previos los trámites legales oportunos, tenga por hechas las manifestaciones contenidas en el cuerpo del mismo y, al amparo de lo dispuesto en el artículo 441.7 de la LEC, proceda a dictar Auto por el que declare la inexistencia de situación de vulnerabilidad de la parte arrendataria y acuerde el alzamiento de la suspensión del presente procedimiento y la continuación del mismo, señalando nueva fecha para la práctica del lanzamiento.

En [COMPLETAR] de [COMPLETAR] de [COMPLETAR]

Firma Letrado/a Firma Procurador/a
