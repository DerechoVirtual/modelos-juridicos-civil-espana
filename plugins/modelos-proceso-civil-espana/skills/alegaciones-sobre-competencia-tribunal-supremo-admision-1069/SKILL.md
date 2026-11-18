---
name: alegaciones-sobre-competencia-tribunal-supremo-admision-1069
description: "Redacta el escrito «Alegaciones sobre la competencia del Tribunal Supremo en la admisión» (formulario 1069 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones sobre la competencia del Tribunal Supremo en la admisión

> Formulario 1069 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] NÚMERO (2 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] FECHA (2 veces)
- [ ] ÓRGANO O PERSONA
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Sección»; «…(»; «…lo establecido en el art. 484 de la LEC.»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 478.1 de la LEC
- art. 484 de la LEC

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

### Formulario 1069 · Alegaciones sobre la competencia del Tribunal Supremo en la admisión

- Año del modelo: 2013
- Revisión 17-11-2026: 12 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Recurso n.º [NÚMERO] Sección [COMPLETAR]

A LA SECCIÓN DE ADMISIÓN DE LA SALA PRIMERA DEL TRIBUNAL SUPREMO

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según tengo debidamente acreditado en el recurso n.º [NÚMERO], ante la Sala comparezco y como mejor proceda en derecho DIGO:

Que se ha notificado a esta parte con fecha [FECHA] providencia de fecha [FECHA] mediante la que se pone de manifiesto a las partes la posibilidad de que este Tribunal no resulte competente para conocer del recurso interpuesto por [ÓRGANO O PERSONA] ( [COMPLETAR]), y por la que se concede plazo para manifestar lo que a nuestro derecho convenga, trámite que procedemos a evacuar conforme a las siguientes

ALEGACIONES

ÚNICO.— El art. 478.1 de la LEC establece que el conocimiento del recurso de casación corresponde a la Sala Primera del Tribunal Supremo. No obstante, corresponderá a las Salas de lo Civil y Penal de los Tribunales Superiores de Justicia conocer de los recursos de casación que procedan contra las resoluciones de los tribunales civiles con sede en la Comunidad Autónoma, siempre que el recurso se funde, exclusivamente o junto a otros motivos, en infracción de las normas del Derecho civil, foral o especial propio de la Comunidad, y cuando el correspondiente Estatuto de Autonomía haya previsto esta atribución.

En este caso, el recurso se funda en la infracción de normas de derecho civil propias de la Comunidad Autónoma de……………., cuyo TSJ tiene atribuido el conocimiento del recurso de casación, según dispone el art. ………. del Estatuto de Autonomía de……………

A ello no obsta que se invoque el derecho común como supletorio en el escrito de interposición del recurso de casación, puesto que reiterada jurisprudencia establece, en interpretación del citado art. 478.1 de la LEC, que también debe entenderse que es de competencia a la Sala Civil y Penal del TSJ en los supuestos en que se invoque el derecho común como supletorio, en virtud de la “vis atractiva”, evitando así, además, que el Tribunal Supremo tuviese que aplicar preceptos específicos del ordenamiento civil propio de la Comunidad Autónoma, que probablemente tendría que utilizar de forma colateral en sus razonamientos de derecho para resolver la cuestión debatida, lo que no parece cometido propio del citado Alto Tribunal al que nos dirigimos.

Por lo expuesto, solicitamos que se declare la falta de competencia del Tribunal Supremo, acordando la remisión de las actuaciones y emplazamiento de las partes para que comparezcan ante la Sala del TSJ de………………….., en el plazo de diez días, conforme a lo establecido en el art. 484 de la LEC.

[COMPLETAR]

Por lo expuesto,

SUPLICO A LA SALA: Que tenga por presentado este escrito con sus copias, lo admita y, previos los trámites oportunos, acuerde declararse no competente para conocer del presente recurso de casación, ordenando la remisión de las actuaciones a la Sala de lo Civil del Tribunal Superior de Justicia de [LOCALIDAD], emplazando a las partes para su comparecencia ante el mismo.

Por ser justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
