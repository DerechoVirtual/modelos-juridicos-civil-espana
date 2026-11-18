---
name: oposicion-demandante-enervacion-requerimiento-previo-1192
description: "Redacta el escrito «Oposición del demandante a la enervación por requerimiento previo de pago» (formulario 1192 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición del demandante a la enervación por requerimiento previo de pago

> Formulario 1192 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] NÚMERO
- [ ] SEDE
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (3 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Don»; «…de»; «…de [COMPLETAR] de»; «…tario por cualquier medio fehaciente con»; «…de»; «…de [COMPLETAR] de»; «…de»; «…de [COMPLETAR] de»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 22.4 de la LEC
- art. 443 de la LEC

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

### Formulario 1192 · Oposición del demandante a la enervación por requerimiento previo de pago

- Año del modelo: 2014
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 15 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio verbal de desahucio por falta de pago núm [NÚMERO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

Don [COMPLETAR], Procurador de los Tribunales, en nombre y representación de [NOMBRE DEL REPRESENTADO/A], parte demandante en el proceso de desahucio arriba expresado, ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que habiendo recibido traslado del escrito del demandado solicitando la enervación de la acción de desahucio, por medio del presente escrito me opongo a la enervación pretendida de contrario en base los siguientes

HECHOS Y FUNDAMENTOS

Esta parte se opone a la enervación pretendida de contrario por cuanto que el demandado fue requerido en fecha [FECHA] de [COMPLETAR] de [COMPLETAR] para que abonara las rentas, sin que hubiera efectuado el pago en la fecha de interposición de la demanda, según establece el art. 22.4.II de la LEC, el cual dispone que la enervación “no será de aplicación cuando el arrendatario hubiera enervado el desahucio en una ocasión anterior, excepto que el cobro no hubiera tenido lugar por causas imputables al arrendador, ni cuando el arrendador hubiese requerido de pago al arrendatario por cualquier medio fehaciente con [COMPLETAR], al menos, treinta días de antelación a la presentación de la demanda y el pago no se hubiese efectuado al tiempo de dicha presentación”.

Consta acreditado que mi representado requirió de pago al demandado en fecha [FECHA] de [COMPLETAR] de [COMPLETAR], sin que efectuara la consignación hasta el día [FECHA] de [COMPLETAR] de [COMPLETAR], esto es, después de interpuesta la demanda, por lo que no debe darse lugar a la enervación.

En cuanto a las alegaciones relativas al requerimiento previo efectuado por esta parte, la Sala Primera del Tribunal Supremo, en Sentencias de 28 de mayo de 2014 y de 23 de junio de 2014, ha establecido como requisitos del requerimiento los siguientes:”1. La comunicación ha de contener un requerimiento de pago de renta o cantidad asimilada. 2. Ha de ser fehaciente, es decir, por medio que permita acreditar que llegó a conocimiento del arrendatario, con la claridad suficiente. 3. Ha de referirse a rentas impagadas. 4. Debe transcurrir el plazo legalmente previsto, que ha venido fluctuando entre uno y dos meses, en las sucesivas reformas legales. Y 5. Que el arrendatario no haya puesto a disposición del arrendador la cantidad reclamada”.

Dichos requisitos se cumplen en este caso, habiendo expresado las citadas SSTS de 28 de mayo de 2014, rec. 1051/2012 y de 23 de junio de 2014, rec. 1437/2013 que en el art. 22.4 de la LEC no se exige que se comunique expresamente al arrendatario que el contrato va a ser resuelto, y que no procederá enervación de la acción de desahucio si no se paga en el plazo preceptivo, puesto que el legislador no obliga al arrendador a que se constituya en asesor del arrendatario, sino tan solo a que le requiera de pago, como en este caso se hizo.

Por tanto, nos oponemos a la enervación, solicitando que se continúe la tramitación conforme dispone el art. 22.4 de la LEC, con imposición de costas al demandado.

Por todo ello,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito, con justificante de traslado, y en su virtud me tenga por opuesto a la enervación de la acción, procediéndose por el Letrado de la Administración de Justicia a la citación de las partes a la vista prevenida en el art. 443 de la LEC y, tras los trámites legales, se dicte sentencia dando lugar la desahucio con imposición de costas al demandado.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
