---
name: apelacion-contra-auto-desestima-oposicion-ejecucion-1191
description: "Redacta el escrito «Apelación contra el auto que desestima la oposición a ejecución hipotecaria por abusividad» (formulario 1191 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Apelación contra el auto que desestima la oposición a ejecución hipotecaria por abusividad

> Formulario 1191 del plugin **Ejecución civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.
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

- [ ] NÚMERO
- [ ] LOCALIDAD
- [ ] FECHA (4 veces)
- [ ] SEDE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…DIGO Que en fecha [FECHA] de»; «…de [COMPLETAR] de»; «…de»; «…la nulidad por abusividad de la cláusula»; «… cláusulas no negociadas individualmente»; «…, con posibilidad de comprensión directa»; «…de nulidad por abusividad de la cláusula»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 695.4 de la LEC
- art. 458 de la LEC
- artículos 80.1, 82 y 83 del RDL 1/2007
- Ley 9/2015

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

### Formulario 1191 · Apelación contra el auto que desestima la oposición a ejecución hipotecaria por abusividad

- Año del modelo: 2014
- Revisión 17-11-2026: 13 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (COMPLETAR)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Proceso de ejecución hipotecaria número [NÚMERO]

A LA AUDIENCIA PROVINCIAL DE [LOCALIDAD]

DIGO

Que en fecha [FECHA] de [COMPLETAR] de [COMPLETAR] se ha dictado auto desestimando la oposición a la ejecución por abusividad formulada por esta parte, el cual ha sido notificado a esta parte en fecha [FECHA] de [COMPLETAR] de

El auto que se impugna es apelable de conformidad a lo dispuesto en el art. 695.4 de la LEC, redactado por la disposición final tercera de la Ley 9/2015, de 25 de mayo, el cual establece que contra el auto que ordene el sobreseimiento de la ejecución, la inaplicación de una cláusula abusiva o la desestimación de la oposición por la causa prevista en el apartado 1.4.º del art. 695, podrá interponerse recurso de apelación.

Al amparo de dicho precepto, y entendiendo que la resolución que se impugna no es ajustada a derecho, dicho sea con los debidos respetos y en términos de defensa, por medio del presente escrito interpongo contra la misma RECURSO DE APELACIÓN impugnando el pronunciamiento desestimatorio de la nulidad por abusividad de la cláusula [COMPLETAR] del contrato de préstamo hipotecario y el de ordenar continuar la ejecución adelante con costas.

Y que, de conformidad a lo dispuesto en el art. 458 de la LEC, fundo el recurso de apelación en las siguientes

ALEGACIONES

PRIMERA Infracción de la Ley de Condiciones Generales de la Contratación por entenderse indebidamente que no es aplicable dicho texto legal a la cláusula impugnada.

El auto que se impugna concluye que no es aplicable al contrato de préstamo hipotecario objeto del presente litigio la Ley de Condiciones Generales de Contratación lo que infringe la jurisprudencia expresada en la STS del Pleno de la Sala Primera de fecha de 9 de mayo de 2013 que afirma que el hecho de que se refieran al objeto principal del contrato en el que están insertadas, no es obstáculo para que una cláusula contractual sea calificada como condición general de la contratación, ya que esta se definen por el proceso seguido para su inclusión en el mismo, y que el conocimiento de una cláusula -sea o no condición general o condición particular- es un requisito previo al consentimiento y es necesario para su incorporación al contrato, ya que, en otro caso, sin perjuicio de otras posibles consecuencias - singularmente para el imponente- no obligaría a ninguna de las partes

En el mismo sentido, la STJUE de 21 de diciembre de 2016 (asuntos acumulados C-154/15, C-307/15 y C-308/15, apartado 50) expresa que el Tribunal de Justicia ha declarado que reviste una importancia fundamental para el consumidor disponer, antes de la celebración de un contrato, de información sobre las condiciones contractuales y las consecuencias de dicha celebración. El consumidor decide si desea quedar vinculado por las condiciones redactadas de antemano por el profesional basándose principalmente en esa información, con cita de la STJUE de 21 de marzo de 2013, RWE Vertrieb, C-92/11, apartado 44), lo cual en este caso no se ha producido. De ello se deriva que, contrariamente a lo decidido por el órgano jurisdiccional, la cláusula ahora impugnada puede ser sometida al control judicial del carácter abusivo de las cláusulas contractuales que se refieran a la definición del objeto principal del contrato, aunque exista una normativa bancaria.

En definitiva, como indica la jurisprudencia, el cumplimiento de los requisitos de transparencia de la cláusula aisladamente considerada, exigidos por la LCGC para la incorporación a los contratos de condiciones generales, es insuficiente para eludir el control de abusividad de una cláusula no negociada individualmente, aunque describa o se refiera a la definición del objeto principal del contrato, si no es transparente, puesto que la transparencia de las cláusulas no negociadas, en contratos suscritos con consumidores, incluye el control de comprensibilidad real de su importancia en el desarrollo razonable del contrato.

SEGUNDA Infracción de los artículos 80.1, 82 y 83 de la Ley General de Defensa de Consumidores y Usuarios por cuanto que la cláusula impugnada es nula.

Tal como se alegó en nuestra oposición, la cláusula suelo impugnada en el presente procedimiento, no supera los requisitos de transparencia precisos para la comprensibilidad real de su importancia en el desarrollo razonable del contrato, declarando, de conformidad con los artículos 80.1, 82 y 83 del RDL 1/2007, LGDCU, lo que determina su nulidad.

La "cláusula suelo" que se impugna puede ser controlada judicialmente como indica la citada STS de 9 de mayo de 2013 no elimina la posibilidad de controlar judicialmente si su contenido es abusivo, debiendo someterse al doble control de transparencia, lo que incluye el control de la comprensibilidad real de su importancia en el desarrollo razonable del contrato, de conformidad con el 80.1 TRLCU cuando dispone que "en los contratos con consumidores y usuarios que utilicen cláusulas no negociadas individualmente [COMPLETAR], aquéllas deberán cumplir los siguientes requisitos: a) Concreción, claridad y sencillez en la redacción, con posibilidad de comprensión directa [COMPLETAR]-;b) Accesibilidad y legibilidad, de forma que permita al consumidor y usuario el conocimiento previo a la celebración del contrato sobre su existencia y contenido; c) Buena fe y justo equilibrio entre los derechos y obligaciones de las partes, lo que en todo caso excluye la utilización de cláusulas abusivas".

En este caso, tal como consta en las actuaciones, el análisis de la oferta vinculante de préstamo y de la escritura de préstamo y constitución de hipoteca de fecha [FECHA], se desprende que la cláusula suelo allí establecida no supera el control de transparencia establecido en la comentada sentencia del Tribunal Supremo, puesto que se incluye enmascarada entre informaciones abrumadoramente exhaustivas que, en definitiva, dificultan su identificación y proyectan sombras sobre lo que considerado aisladamente sería claro; pero es que además tampoco se cumplen determinados requisitos exigidos por la jurisprudencia; así, la falta de una información suficientemente clara de que se trata de un elemento definitorio del objeto principal del contrato; no existe simulaciones de escenarios diversos relacionados con el comportamiento razonablemente previsible del tipo de interés en el momento de contratar, ni que se explicara e indicara a mi representado la aplicación de la mencionada cláusula; no hay información previa clara y comprensible sobre el coste comparativo con otras modalidades de préstamo de la propia entidad -caso de existir- o advertencia de que al concreto perfil de cliente no se le ofertan las mismas; no consta tampoco que le fuera entregada a mi representado la mencionada oferta vinculante y, por último no consta firmada expresamente la parte de la oferta vinculante donde consta redactada la cláusula.

Ello debe determinar la estimación de la oposición a la ejecución formulada por esta parte con los pronunciamientos inherentes, esto es, la declaración de nulidad por abusividad de la cláusula [COMPLETAR] del préstamo hipotecario y su inaplicación, con imposición de costas a la parte ejecutante. Todo ello a reserva del derecho de esta parte a la reclamación de los intereses indebidamente abonados conforme a la jurisprudencia establecida por la STJUE de 21 de diciembre de 2016 (asuntos acumulados C-154/15, C-307/15 y C-308/15) y asumida por el Pleno de la Sala de lo Civil en Recursos de casación 740/2014 y 2223/2014.

En base a lo anterior,

SUPLICO A LA SALA: Que tenga por presentado este escrito, con justificante de traslado, teniendo por interpuesto el recurso de apelación frente al auto de fecha [FECHA] dictado por la Sección Civil del Tribunal de Instancia de [SEDE] en las presentes actuaciones, y tras la pertinente tramitación, se dicte por la Sala auto en el que, declarando haber lugar al recurso de apelación, revoque el auto apelado y estime la oposición deducida por esta parte, con imposición al ejecutante de las costas del incidente de oposición.

OTROSÍ PRIMERO DIGO que de conformidad con lo dispuesto en los apartados 3.b) y 6 de la disposición adicional decimoquinta de la LOPJ acompaño a este escrito resguardo de consignación en la cuenta de Depósitos y Consignaciones abierta a nombre del Tribunal del depósito exigido para interponer el recurso por importe de 50 euros.

Por lo que, SUPLICO A LA SALA que tenga por constituido el depósito, dejando interesada desde este momento su devolución para el caso de estimación total o parcial del recurso.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
