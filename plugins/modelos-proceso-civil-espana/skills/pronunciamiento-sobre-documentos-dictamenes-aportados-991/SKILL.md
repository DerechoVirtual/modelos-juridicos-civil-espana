---
name: pronunciamiento-sobre-documentos-dictamenes-aportados-991
description: "Redacta el escrito «Pronunciamiento sobre documentos y dictámenes aportados de contrario» (formulario 991 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pronunciamiento sobre documentos y dictámenes aportados de contrario

> Formulario 0991 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] NÚMERO (3 veces)
- [ ] FECHA (2 veces)
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] DESCRIBIR (3 veces)
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… Esta parte impugna el documento público»; «…aportado con el n.º [NÚMERO] por»; «…gnamos el documento privado que la parte»; «… recoge no es auténtica. A este efecto y»; «…do el dictamen un profesional experto en»; «…dad el objeto de la pericia se refería a»; «…, presentado con»; «…n), se amplíe a los siguientes extremos:»; «…n que ha presentado la otra parte con la»; «…, ya que existe relación de»; «…(parentesco, amistad»; «…(parentesco, amistad [COMPLETAR]) entre»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 338 y 427.3 de la LEC
- art. 343.2 de la LEC

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

### Formulario 0991 · Pronunciamiento sobre documentos y dictámenes aportados de contrario

- Año del modelo: 2013
- Revisión 17-11-2026: 20 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Con la venia: (Opciones):— Esta parte impugna el documento público [COMPLETAR] aportado con el n.º [NÚMERO] por [COMPLETAR] (el demandante o el demandado) en su escrito de [FECHA] (demanda o contestación), por entender que en el mismo existe una falsedad ideológica ya que en realidad no estamos ante una compraventa de vivienda, sino ante una donación de la misma, ya que no se ha acreditado la entrega del precio.— Impugnamos el documento privado que la parte [COMPLETAR] ha presentado con su escrito de [FECHA] con el n.º [NÚMERO], porque entendemos que la firma de D. [NOMBRE Y APELLIDOS] que en él se recoge no es auténtica. A este efecto y [COMPLETAR] (en aplicación de los arts. 338 y 427.3 de la LEC esta parte aportará antes del juicio informe pericial caligráfico para que se emita dictamen sobre [DESCRIBIR] o en aplicación de los arts. 339 y 427.4 interesamos que por el Tribunal se designe perito calígrafo para que emita informe sobre [DESCRIBIR])— Entendemos que la grabación presentada de contrario como prueba n.º [NÚMERO] no es auténtica, ya que ha fundido el contenido de varias conversaciones dándoles un sentido totalmente diferente al que, en cada una de ellas, se pretendía.— Respecto al informe pericial presentado de contrario negamos su validez, por haber emitido el dictamen un profesional experto en [COMPLETAR], cuando en realidad el objeto de la pericia se refería a [COMPLETAR] Así entendemos que se ajusta más a la realidad el que esta parte ha presentado con su escrito de — Interesamos que el informe del perito D. [NOMBRE Y APELLIDOS], presentado con [COMPLETAR] (la demanda o la contestación), se amplíe a los siguientes extremos: [COMPLETAR], y que se nos dé traslado de su resultado antes de la celebración del juicio.— En aplicación del art. 343.2 de la LEC procedo a formular tacha contra el perito D. [NOMBRE Y APELLIDOS] que ha emitido dictamen que ha presentado la otra parte con la [COMPLETAR] (demanda o contestación) sobre [DESCRIBIR], ya que existe relación de [COMPLETAR] (parentesco, amistad [COMPLETAR]) entre [COMPLETAR] (el perito y la parte que lo ha propuesto o su abogado)

========================================================================
