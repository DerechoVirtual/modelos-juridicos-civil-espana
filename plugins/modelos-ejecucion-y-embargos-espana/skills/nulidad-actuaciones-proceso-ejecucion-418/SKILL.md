---
name: nulidad-actuaciones-proceso-ejecucion-418
description: "Redacta el escrito «Nulidad de actuaciones en proceso de ejecución» (formulario 418 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Nulidad de actuaciones en proceso de ejecución

> Formulario 0418 del plugin **Ejecución civil** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] LOCALIDAD
- [ ] NÚMERO
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… tengo acreditado en los autos de juicio»; «…nte este Tribunal con número de registro»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 562.2 LEC
- art. 24.1 CE
- art. 686.3 LEC
- art. 553 LEC
- Ley 19/2015

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

### Formulario 0418 · Nulidad de actuaciones en proceso de ejecución

- Año del modelo: 2018
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 8 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito solicitando nulidad de actuaciones en proceso de ejecución por defecto de emplazamiento.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD] y D.N.I. número [NÚMERO], según tengo acreditado en los autos de juicio [COMPLETAR] seguidos ante este Tribunal con número de registro [COMPLETAR] y de los que dimana el presente procedimiento de ejecución, comparezco y como mejor proceda en derecho DIGO:

Que, al amparo de lo previsto en el art. 562.2 LEC, mediante el presente escrito insto la NULIDAD DE ACTUACIONES en los términos que luego se dirán, al concurrir el motivo previsto en el art. 225.3.º LEC, produciendo una situación de absoluta indefensión a esta parte, en base a las siguientes:

ALEGACIONES

PRIMERA

Al amparo de los arts. 166 y 225.3.º de la LEC, se insta la declaración de nulidad de todo lo actuado, por infracción de normas y garantías procesales, por cuanto el acto de comunicación se practicó con infracción de las normas legales, produciendo una evidente indefensión a mi representado, quien en ningún momento ha conocido que se estaba despachando ejecución contra el mismo.

SEGUNDA

La nulidad de actuaciones que se postula resulta palmaria del iter procedimental seguido en el curso de proceso de ejecución, al llevarse a cabo el emplazamiento edictal del ejecutado sin realizar ninguna actividad previa de averiguación del domicilio del mismo.

Por tanto, existe un defecto en la comunicación que impidió a mi representado el ejercicio de su derecho de defensa, al acudirse a la notificación edictal, lo que originó que el proceso de ejecución se desarrollara a espaldas del ejecutado, ocasionando una evidente indefensión, lo cual debe dar lugar a la nulidad de las actuaciones al momento inmediatamente anterior a la notificación a mi representado del auto despachando ejecución.

Así, en el procedimiento de ejecución hipotecaria se ha vulnerado su derecho a la tutela judicial efectiva sin indefensión (art. 24.1 CE) en cuanto no tuvo conocimiento del desarrollo del referido procedimiento ni, por lo tanto, pudo hacer valer en él los medios de defensa que la ley le confiere, como consecuencia de que el tribunal acudió a la notificación y requerimiento de pago por medio de edictos tras el intento infructuoso en la finca hipotecada y sin tratar de averiguar su domicilio real, como exige la jurisprudencia constitucional.

El Tribunal Constitucional se ha pronunciado en reiteradas ocasiones sobre el problema aquí planteado acerca de la comunicación del procedimiento de ejecución hipotecaria en el caso de que sea negativa la notificación y el requerimiento de pago en el domicilio que consta en el Registro de la Propiedad y, más concretamente, sobre la necesidad de que el órgano judicial agote las posibilidades de averiguación del domicilio real antes de acudir a notificación por edictos.

En concreto, en la sentencia STC 122/2013, FJ 3, con cita de doctrina precedente, el Tribunal Constitucional ha afirmado que "cuando del examen de los autos o de la documentación aportada por las partes se deduzca la existencia de un domicilio que haga factible practicar de forma personal los actos de comunicación procesal con el demandado, debe intentarse esta forma de notificación antes de acudir a la notificación por edictos (por todas, SSTC 40/2005, de 28 de febrero, FJ 2; 293/2005, de 21 de noviembre, FJ 2; y 245/2006, de 24 de julio, FJ 2)". Incluso cuando no conste ese domicilio en las actuaciones habría que realizar otras gestiones en orden a la averiguación del domicilio real (por todas, SSTC 19/2004, FJ 4, y 126/2006, FJ 4), siempre que ello no suponga exigir al órgano judicial una desmedida labor investigadora sobre la efectividad del acto de comunicación (SSTC 126/1999, FJ 4; 82/2000, FJ 6; 113/2001, FJ 5, y 131/2014, FJ 2, entre otras).

Así, dice la citada STC 122/2013, FJ 5, "desde una estricta perspectiva constitucional, procede realizar una interpretación secundum constitutionem del art. 686.3 LEC, integrando su contenido, de forma sistemática, con el art. 553 LEC, precepto rector de la llamada al proceso de ejecución hipotecaria, y con la doctrina de este Tribunal en cuanto a la subsidiariedad de la comunicación edictal, la cual tiene su fuente directa en el derecho de acceso al proceso del art. 24.1 CE, de manera que la comunicación edictal en el procedimiento de ejecución hipotecaria sólo puede utilizarse cuando se hayan agotado los medios de averiguación del domicilio del deudor o ejecutado".

TERCERA

La aplicación al presente caso de la doctrina sentada en la STC 122/2013, reiterada en sentencias posteriores (SSTC 30/2014, FJ 3; 131/2014, FJ 4; 137/2014, FJ 3; 89/2015, FJ 3; 151/2016, FJ 2; 106/2017, FJ 4; y 5/2018, FJ 3), conduce a apreciar la vulneración del derecho de mi representado en amparo a la tutela judicial efectiva sin indefensión (art. 24.1 CE). Esto no supone el reconocimiento de eficacia retroactiva a la reforma llevada a cabo por la Ley 19/2015, de 13 de julio en el art. 686.3 LEC —que en su redacción anterior no obligaba a desarrollar ninguna posibilidad de averiguación del domicilio real antes de acudir a la comunicación edictal—, sino la aplicación del contenido del art. 24.1 CE de acuerdo con la doctrina constitucional antes referida.

En efecto, una vez que resultó infructuoso el intento de notificación personal en la finca hipotecada, el Tribunal de Instancia ordenó, sin más trámites, que el deudor fuera notificado del despacho de la ejecución y requerido de pago por medio de edictos. Pese a que en la escritura de constitución de la hipoteca constaba el domicilio real de los recurrentes, el tribunal no intentó efectuar ningún acto de comunicación en ese domicilio. Por otro lado, aun cuando de la diligencia negativa de notificación podía inferirse que los destinatarios no tenían su residencia habitual en el citado inmueble, tampoco efectuó el tribunal intento alguno de averiguación de dicho domicilio real a través de medios fácilmente accesibles como el punto neutro judicial, red informática al servicio de la Administración de Justicia, que permite a ésta el acceso a los datos que se contienen en diversos registros y organismos públicos, que éstos suministran al juez con sujeción a la normativa que les es propia (STC 50/2017, FJ 4). En suma, el órgano judicial acudió a la comunicación edictal sin haber agotado previamente las posibilidades razonables de averiguación del domicilio real del ejecutado, para proceder a la notificación personal.

Por lo expuesto,

SUPLICO AL TRIBUNAL:

Que tenga por presentado este escrito y por promovido incidente de nulidad de actuaciones practicadas en este proceso, y, previos los trámites legales, dicte resolución por la que declare la nulidad de lo actuado reponiendo las actuaciones all momento inmediatamente anterior al requerimiento de pago a mi representado para que se le comunique el despacho de ejecución en legal forma.

Es justicia de hacerse en [LUGAR], a [FECHA].

Firma del Abogado	Firma del Procurador/a

========================================================================
