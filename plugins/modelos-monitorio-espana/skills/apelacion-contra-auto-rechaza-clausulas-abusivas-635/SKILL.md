---
name: apelacion-contra-auto-rechaza-clausulas-abusivas-635
description: "Redacta el escrito «Apelación contra el auto que rechaza cláusulas abusivas en el monitorio» (formulario 635 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Apelación contra el auto que rechaza cláusulas abusivas en el monitorio

> Formulario 0635 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] FECHA (7 veces)
- [ ] Nº DE RESOLUCIÓN
- [ ] SEDE (2 veces)
- [ ] Nº DE PROCEDIMIENTO (2 veces)
- [ ] NÚMERO (5 veces)
- [ ] ...
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…numeración del juzgado de procedencia).]»; «…(NIG»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 455 y 458 de la LEC
- art. 455 de la LEC
- artículo 458 de la LEC
- artículo 448.2 de la LEC
- artículo 215.5 LEC
- art. 1154 del Código Civil
- art. 231 de la LEC

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

### Formulario 0635 · Apelación contra el auto que rechaza cláusulas abusivas en el monitorio

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 23 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA AUDIENCIA PROVINCIAL DE [LOCALIDAD] (SECCIÓN CIVIL)

D/Dª [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, actuando en representación de D/Dª [NOMBRE Y APELLIDOS], según acredito mediante certificación de apoderamiento electrónico que acompaño, bajo la dirección letrada de D/Dª [NOMBRE Y APELLIDOS], comparezco y como mejor proceda en derecho DIGO:

1) Que en fecha [FECHA] esta parte ha sido notificada de la Sentencia número [Nº DE RESOLUCIÓN], de fecha [FECHA], dictada por el Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] en autos de proceso ordinario número [Nº DE PROCEDIMIENTO] (NIG [COMPLETAR]), dimanante del procedimiento monitorio número [Nº DE PROCEDIMIENTO], de la que se acompaña copia.

(caso de aclaración/complemento. Frente a dicha sentencia se dedujo solicitud de complemento siendo desestimada por auto de fecha [FECHA] notificado en fecha [FECHA]).

2) Que entendiendo que dicha sentencia no es ajustada a derecho, dicho sea con los debidos respetos y en términos de defensa, por medio del presente escrito, al amparo de lo dispuesto en los arts. 455 y 458 de la LEC, interpongo contra la misma RECURSO DE APELACIÓN, impugnando todos sus pronunciamientos, en base a los siguientes presupuestos de admisibilidad y alegaciones:

I. ADMISIBILIDAD DEL RECURSO

PRIMERO.- El presente recurso se deduce contra la citada sentencia dictada por el Tribunal de Instancia número [NÚMERO] en fecha [FECHA], cuyo fallo es del tenor literal siguiente: ()

SEGUNDO.- La sentencia es recurrible en apelación, según lo dispuesto en el art. 455 de la LEC.

TERCERO.- El presente recurso se interpone ante el tribunal competente para conocer del mismo, dentro del plazo de veinte días establecido en el artículo 458 de la LEC, computados conforme al artículo 448.2 de la LEC (en su caso, en relación con el artículo 215.5 LEC), habiéndose constituido el depósito para recurrir tal como se expresa en el otrosí de este escrito.

CUARTO.- Por medio del presente recurso se impugnan todos los pronunciamientos de la sentencia apelada, tanto el de desestimación de la existencia de cláusulas abusivas en el contrato de préstamo de financiación al comprador por el que se inició el monitorio del que dimana el proceso ordinario, como el de condena a mi representado, como el de intereses y costas.

II. ALEGACIONES

Infracción de la Ley de Condiciones Generales de la Contratación y de la Ley General de Defensa de Consumidores y Usuarios por entenderse indebidamente que esta normativa legal no es aplicable a las cláusulas del contrato por el que se despachó ejecución.

La jurisprudencia del Tribunal Supremo en sentencias de 8 de septiembre de 2014, rec. 1217/2013; 2 de diciembre de 2014, rec. 389/2012 y 22 de abril de 2015, rec. 2351/2012. ha considerado que la contratación bajo condiciones generales constituye un auténtico modo de contratar, claramente diferenciado del paradigma del contrato por negociación regulado en el Código Civil. Su eficacia exige que, además de la prestación del consentimiento del adherente a la inclusión de unas cláusulas redactadas de un modo claro y comprensible, y transparentes en sus consecuencias económicas y jurídicas, el profesional o empresario cumpla unos especiales deberes de configuración del contrato predispuesto en el caso de cláusulas no negociadas en los contratos celebrados con consumidores, que supongan el respeto, de acuerdo con las exigencias de la buena fe, al justo equilibrio entre los derechos y obligaciones de las partes, lo que en todo caso excluye la utilización de cláusulas abusivas.

De ahí que el art. 82.1 del Texto Refundido de la Ley General para la Defensa de los Consumidores y Usuarios considere cláusulas abusivas las estipulaciones no negociadas individualmente que, en contra de las exigencias de la buena fe, causen, en perjuicio del consumidor y usuario, un desequilibrio importante de los derechos y obligaciones de las partes que se deriven del contrato; el art. 8.2 de la Ley de Condiciones Generales de la Contratación prevea que «serán nulas las condiciones generales que sean abusivas, cuando el contrato se haya celebrado con un consumidor »; el art. 83 del Texto Refundido de la Ley General para la Defensa de los Consumidores y Usuarios establezca que «las cláusulas abusivas serán nulas de pleno derecho y se tendrán por no puestas»; y el art. 6.1 de la Directiva 1993/13/CEE, de 5 abril, sobre cláusula abusivas en contratos celebrados con consumidores (en lo sucesivo, la Directiva 1993/13/CEE) disponga que «los Estados miembros establecerán que no vincularán al consumidor [...] las cláusulas abusivas que figuren en un contrato celebrado entre éste y un profesional».

Lo expuesto supone que, tratándose de cláusulas no negociadas en contratos concertados con consumidores, la ausencia de vicios del consentimiento o, lo que es lo mismo, que el consumidor haya prestado válidamente su consentimiento al contrato predispuesto por el profesional, incluso en el caso de cláusulas claras, comprensibles y transparentes, no es obstáculo para que pueda declararse la nulidad de las cláusulas abusivas cuando, pese a las exigencias de la buena fe, causan en detrimento del consumidor un desequilibrio importante entre los derechos y obligaciones de las partes que se derivan del contrato (art. 3.1 de la Directiva 1993/13/CEE y 82.1 del Texto Refundido de la Ley General para la Defensa de los Consumidores y Usuarios).

En definitiva, como indica la jurisprudencia, el cumplimiento de los requisitos de transparencia de la cláusula aisladamente considerada, exigidos por la LCGC para la incorporación a los contratos de condiciones generales, es insuficiente para eludir el control de abusividad de una cláusula no negociada individualmente, aunque describa o se refiera a la definición del objeto principal del contrato, si no es transparente, puesto que la transparencia de las cláusulas no negociadas, en contratos suscritos con consumidores, incluye el control de comprensibilidad real de su importancia en el desarrollo razonable del contrato.

Por tanto, es indudable que es de aplicación el marco normativo antes expuesto al contrato concertado por mi representado con la entidad demandante y, más concretamente, a la cláusula cuestionada por abusiva como se expone a continuación.

Infracción de los artículos 82 y siguientes de la Ley General de Defensa de Consumidores y Usuarios por cuanto que la cláusula impugnada que establece el interés de demora es susceptible de control de abusividad de su contenido, no solo en cuanto a su transparencia, sino también respecto a si, en contra de las exigencias de la buena fe y en perjuicio del consumidor y usuario, causan un desequilibrio importante de los derechos y obligaciones de las partes que se deriven del contrato, por no estar incluida en el ámbito de aplicación del art. 4.2 de la Directiva 1993/13/CEE.

Aunque la jurisprudencia del TS ha declarado que no es posible moderar los intereses de demora aplicando el art. 1154 del Código Civil, ha dejado a salvo la posibilidad de controlar las cláusulas que establecen tales intereses cuando se trata de cláusulas no negociadas en contratos concertados con consumidores. La cláusula que establece el interés de demora no define el objeto principal del contrato ni la adecuación entre el precio y la prestación. Regula un elemento accesorio como es la indemnización a abonar por el prestatario en caso de retraso en el pago de las cuotas y, como tal, no resulta afectada por la previsión del art. 4.2 de la Directiva, que solo prevé el control de transparencia sobre las cláusulas que definan el objeto principal del contrato o a la adecuación entre precio y retribución, por una parte, y los servicios o bienes que hayan de proporcionarse como contrapartida. Es más, tanto la Directiva como la Ley, actualmente el Texto Refundido de la Ley General para la Defensa de los Consumidores y Usuarios, prevén expresamente la abusividad de este tipo de cláusulas cuando existe una desproporción de la indemnización por incumplimiento del consumidor con el quebranto patrimonial efectivamente causado al profesional o empresario.

Debe recordarse asimismo que el TJUE ha considerado que no puede hacerse una aplicación extensiva de la restricción del control de abusividad previsto en el citado art. 4.2 de la Directiva, al constituir una excepción del mecanismo de control del fondo de las cláusulas abusivas previsto en el sistema de protección de los consumidores que establece esa Directiva (STJUE de 30 de abril de 2014, asunto C-26/13, caso Árpád Kásler y Hajnalka Káslerné Rábai, párrafo 42).

El art. 85.6 del Texto Refundido Ley General para la Defensa de los Consumidores y Usuarios establece que son abusivas las cláusulas que supongan la imposición de una indemnización desproporcionadamente alta al consumidor y usuario que no cumpla sus obligaciones. Lo determinante para decidir sobre la corrección de esta solución será el examen de esa proporcionalidad entre el incumplimiento del consumidor y la indemnización asociada al incumplimiento. En el caso de los contratos de préstamo sin garantía real celebrados por negociación, las máximas de experiencia nos muestran que el interés de demora se establece por la adición de un pequeño porcentaje adicional sobre el interés remuneratorio pactado. Por tanto, el interés de demora establecido en cláusulas no negociadas debe consistir, para no resultar abusivo, en un porcentaje adicional que no debe ser muy elevado por cuanto que la ausencia de garantías reales determina que el interés remuneratorio ya sea elevado, por lo que la adición de un porcentaje excesivo conllevaría un alejamiento injustificado de los porcentajes que la legislación nacional establece para los supuestos de ausencia de pacto, incluso en aquellos casos en los que el deudor es un profesional.

Con base en los criterios expresados, el TS considera abusivo un interés de demora que suponga un incremento de más de dos puntos porcentuales respecto del interés remuneratorio pactado en un préstamo personal y así fija como doctrina jurisprudencial que en los contratos de préstamo sin garantía real concertados con consumidores, es abusiva la cláusula no negociada que fija un interés de demora que suponga un incremento de más de dos puntos porcentuales respecto del interés remuneratorio pactado.

En consecuencia, el interés de demora establecido en la cláusula cuestionada del contrato de préstamo objeto de este procedimiento monitorio es claramente abusivo porque consistía en la adición de más de diez puntos porcentuales al interés remuneratorio, hasta alcanzar un interés superior al veinte por ciento, lo cual debe determinar la exclusión de los intereses de demora reclamados por aplicación de la normativa y jurisprudencia expuestas. Por ello se solicita que se declaren nulos, abusivos y sin efecto alguno los intereses de demora,

En base a lo anterior,

SUPLICO A LA SALA que tenga por interpuesto recurso de apelación contra la sentencia de fecha [FECHA] dictada por el Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO], en el proceso número [NÚMERO], con justificante de traslado a la otra parte que acompaño, y, previos los trámites legales, dicte sentencia por la que estime el recurso interpuesto, declarando la abusividad de las cláusulas núm [NÚMERO] y núm [NÚMERO] del contrato de préstamo de fecha [FECHA] concertado por ambas partes, con los pronunciamientos inherentes.

OTROSÍ PRIMERO DIGO que de conformidad con lo dispuesto en los apartados 3.b) y 6 de la disposición adicional decimoquinta de la LOPJ acompaño a este escrito resguardo de consignación en la cuenta de Depósitos y Consignaciones abierta a nombre del Tribunal del depósito exigido para interponer el recurso por importe de 50 euros.

Por lo que, SUPLICO A LA SALA que tenga por constituido el depósito, dejando interesada desde este momento su devolución para el caso de estimación total o parcial del recurso.

OTROSÍ SEGUNDO DIGO que, acompaño los siguientes documentos referenciados mediante índice electrónico:

-Documento número 1: certificación de apoderamiento electrónico.

-Documento número 2: copia de la sentencia impugnada, que contiene firma electrónica que la identifica (o código seguro de verificación).

-Documento número 3: resguardo de depósito para recurrir.

SUPLICO A LA SALA que tenga por aportados los citados documentos.

OTROSÍ TERCERO DIGO que esta parte manifiesta su voluntad de cumplir los requisitos exigidos por la LEC para la interposición del recurso de apelación, por lo que solicita que le sea concedido el oportuno trámite de subsanación, en el caso de haber cometido algún defecto, de conformidad con lo dispuesto en el art. 231 de la LEC.

SUPLICO A LA SALA que tenga por hechas las manifestaciones y acuerde de conformidad.

En lugar, fecha y firma de abogado y procurador

========================================================================
