---
name: demanda-revision-laudo-firme-maquinacion-fraudulenta-1472
description: "Redacta el escrito «Demanda de revisión de laudo firme por maquinación fraudulenta» (formulario 1472 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de revisión de laudo firme por maquinación fraudulenta

> Formulario 1472 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.

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

- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (14 veces)
- [ ] Nº DE PROCEDIMIENTO (3 veces)
- [ ] ACTO O RESOLUCIÓN (2 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] SEDE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… LA SALA DE CIVIL DEL TRIBUNAL SUPREMO D»; «… este escrito, asistido por el Abogado D»; «…RBITRAL dictado por la Corte Arbitral de»; «…seguido ante la Corte Arbitral de»; «…constando como parte demandante D»; «…D»; «…numeración del juzgado de procedencia).]»; «…un nuevo domicilio de mi representada en»; «…l domicilio de la sociedad se trasladó a»; «…l firme dictado por la Corte Arbitral de»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 510 de la LEC
- art. 512 de la LEC
- art. 509 de la LEC
- art. 514 de la LEC
- art. 511 de la LEC
- art. 513 de la LEC

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

### Formulario 1472 · Demanda de revisión de laudo firme por maquinación fraudulenta

- Año del modelo: 2014
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 34 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (FECHA)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Parte
HECHOS
FUNDAMENTOS DE DERECHO
Suplico
Firmas

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SALA DE CIVIL DEL TRIBUNAL SUPREMO

D [COMPLETAR], Procurador de los Tribunales, actuando en nombre y representación de [NOMBRE DEL REPRESENTADO/A], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, asistido por el Abogado D [COMPLETAR], ante la Sala comparezco y como mejor proceda en derecho DIGO:

Que mediante el presente escrito, al amparo de lo dispuesto en los arts. 43 de la Ley de Arbitraje en relación con los artículos 509 y ss. de la LEC, formulo DEMANDA DE REVISIÓN DEL LAUDO ARBITRAL dictado por la Corte Arbitral de [COMPLETAR] en fecha [FECHA] en procedimiento arbitral número [Nº DE PROCEDIMIENTO] contra [ACTO O RESOLUCIÓN] al concurrir el motivo cuarto del art. 510 de la LEC, por haberse ganado injustamente mediante maquinaciones fraudulentas, en base a los siguientes,

HECHOS

 El laudo firme cuya revisión se pretende se dictó en fecha [FECHA] en el procedimiento arbitral número [Nº DE PROCEDIMIENTO] seguido ante la Corte Arbitral de [COMPLETAR] constando como parte demandante D [COMPLETAR] y parte demandada mi representada, siendo relevantes los siguientes datos de dicho proceso:

a) por escrito de fecha [FECHA] D [COMPLETAR] presentó solicitud de arbitraje contra mi representado en virtud de cláusula arbitral incluida en el contrato de fecha [FECHA], facilitando como domicilio el sito en [LOCALIDAD], que es el que figuraba en el contrato.

b) por la secretaría de la Corte Arbitral se intentó la notificación en el domicilio que constaba en el contrato como el de mi representado y, siendo negativa, se requirió al demandante para que manifestara el domicilio de mi representado, quien manifestó ignorar su domicilio, por lo que resolución de la Corte de fecha [FECHA] se consideró recibida la comunicación en fecha [FECHA], siguiéndose el procedimiento arbitral en ausencia de mi representado.

c) en fecha [FECHA] se publicó el laudo por edictos conforme al reglamento de la Corte Arbitral.

d) en fecha [FECHA] se insta por el demandante la ejecución forzosa del laudo arbitral ante la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], facilitando un nuevo domicilio de mi representada en [COMPLETAR], que efectivamente es el real, acordándose despachar la ejecución por auto de fecha [FECHA] y practicándose diligencia de embargo el día [FECHA] con el representante de mi representada, momento en el cual conoce mi representada la existencia del proceso.

 Tal como se describe en el expositivo anterior, el procedimiento arbitral se siguió de espaldas a mi representada, que sólo conoce el laudo el día [FECHA] cuando habiendo facilitado nuevo domicilio por el actor se entiende el embargo con su representante.

Ninguna de las actuaciones anteriores fueron conocidas por mi representada, que sólo tiene conocimiento del laudo en fase de ejecución, cuando ya ha alcanzado firmeza, lo que nos obliga a interponer la presente demanda de revisión conforme a lo establecido en el artículo 43 de la Ley de Arbitraje, lo que se hace en el plazo establecido en el art. 512 de la LEC.

 La presente demanda se formula al amparo del motivo cuarto del art. 510 de la LEC, al haberse ganado el laudo injustamente con motivo de maquinación fraudulenta del demandante.

En efecto, mi representada tiene su domicilio en [LOCALIDAD], lugar donde se practica la diligencia de embargo, y un almacén en el domicilio sito en [LOCALIDAD], que el demandante facilitó como domicilio de la demandada, el lugar donde anteriormente estaban las oficinas de la sociedad a la que represento en el momento en que se celebró el contrato.

El demandante, fue asesor de esta sociedad, como claramente se acredita por el contenido de la demanda, donde se reclama una cantidad presuntamente devengada por la prestación de sus servicios como asesor financiero, por lo que es perfectamente conocedor de estas circunstancias, conociendo que el domicilio de la sociedad se trasladó a [COMPLETAR] en fecha [FECHA], anterior a la presentación de la solicitud de arbitraje ante la Corte cuando aún estaba prestando servicios para la demandada.

El demandante conocía perfectamente esta circunstancia, en su condición de asesor fiscal; sin embargo, al interponer la demanda judicial y aún siendo conocedor de este hecho, facilitó el antiguo domicilio a sabiendas de que la sociedad se había trasladado al nuevo domicilio. Por tanto, es lógico deducir que su intención fue seguir el arbitraje a espaldas de la demandada, como finalmente consiguió. Ello se ratifica por el hecho que, una vez firme el laudo, facilita el domicilio correcto de la demandada para la ejecución forzosa y practicar el embargo, lo que pone de manifiesto que conocía este domicilio y si no lo facilitó anteriormente fue con la evidente intención de evitar la defensa que mi representada pudiera hacer en el procedimiento.

Esta conducta entra dentro del concepto de maquinación fraudulenta del art. 510.4º de la LEC, puesto que como ha señalado el Alto Tribunal al que me dirijo en sus sentencias de 16 de febrero de 1998, rec. 2218/1994 y 13 de marzo de 2000, rec. 472/1999, entre otras muchas, la maquinación fraudulenta se integra por toda conducta dolosa o negligente que impide la comunicación con la persona que es demandada, incluyendo en este caso el supuesto en que se ha designado un domicilio ficticio, como es el que anteriormente ocupaba mi representada que el demandante designó como domicilio ante la Corte de Arbitraje. A ello se añade que omitió en toda la fase declarativa cualquier mención al nuevo domicilio, que conocía el demandante, como asesor fiscal de mi representada en aquel tiempo, al cual se había trasladado mi representada y que luego facilitó en fase de ejecución de sentencia, transcurrido apenas un mes desde la publicación del laudo.

 Mi representada, con anterioridad a la interposición de la presente demanda, ha depositado la cantidad de 300 euros en la cuenta de depósitos y consignaciones de la Sala, según se acredita por el resguardo que se acompaña a la presente demanda.

A los anteriores hechos son de aplicación los siguientes,

FUNDAMENTOS DE DERECHO

En cuanto a la jurisdicción y competencia, es competente la Sala a la que me dirijo conforme al art. 509 de la LEC al ser controvertida en el proceso una materia de derecho civil común, debiendo sustanciarse conforme a lo dispuesto en el art. 514 de la LEC.

Está legitimado activamente la parte demandante de la revisión, conforme al art. 43 de la Ley de Arbitraje en relación con el art. 511 de la LEC, al haber resultado condenada en el laudo firme impugnado, y lo está pasivamente el demandado por ser la parte actora en el procedimiento arbitral.

La revisión se solicita dentro de los plazos del art. 512 de la LEC, al no haber transcurrido cinco años desde la fecha de publicación del laudo ni tres meses desde el día [FECHA], fecha en que conoció la existencia del proceso con la práctica de la diligencia de embargo, tal como se ha relatado en el hecho segundo.

Depósito

Mi mandante acompaña resguardo acreditativo del depósito conforme establece el art. 513 de la LEC.

Motivos de revisión

La revisión se solicita al amparo del ordinal 4º del art. 510 de la LEC al haberse ganado el laudo en virtud de maquinación fraudulenta del demandante en el proceso del que trae causa la revisión, quien en todo momento ocultó el domicilio real de la sociedad que represento. Asimismo citamos las sentencias de la Sala de 12 de junio de 2000 y 24 de septiembre de 2001 en apoyo de nuestras pretensiones.

Por lo expuesto es de justicia y

SUPLICO A LA EXCMA. SALA que tenga por presentada esta demanda de revisión del laudo arbitral firme dictado por la Corte Arbitral de [COMPLETAR] en fecha [FECHA] en procedimiento arbitral número [Nº DE PROCEDIMIENTO] contra [ACTO O RESOLUCIÓN] y, tras los trámites legales, dicte sentencia por la que rescinda el laudo impugnado, condenando a las partes a estar y pasar por tal declaración, con devolución del depósito constituido para recurrir.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma Procurador y Abogado

========================================================================
