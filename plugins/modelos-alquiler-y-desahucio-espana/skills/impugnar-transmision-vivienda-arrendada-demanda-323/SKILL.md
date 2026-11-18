---
name: impugnar-transmision-vivienda-arrendada-demanda-323
description: "Redacta el escrito «Impugnar la transmisión de la vivienda arrendada: demanda» (formulario 323 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Impugnar la transmisión de la vivienda arrendada: demanda

> Formulario 0323 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] LOCALIDAD (4 veces)
- [ ] Nº DE DOCUMENTO (5 veces)
- [ ] CALLE (2 veces)
- [ ] FECHA (5 veces)
- [ ] IMPORTE (4 veces)
- [ ] NÚMERO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 21 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…unales en nombre y representación de Don»; «…RATO DE ARRENDAMIENTO URBANO, contra Don»; «…bió un contrato de arrendamiento con Don»; «…, Don»; «…rio, enajenó la vivienda arrendada a Don»; «…ura pública autorizada por el Notario de»; «…de»; «…de [COMPLETAR], Tomo»; «…de [COMPLETAR], Tomo [COMPLETAR], Libro»; «…, Libro [COMPLETAR], Folio»; «…, Folio [COMPLETAR], Finca»; «…ros. La vivienda fue arrendada en el año»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 85.1 LOPJ
- art. 45 LEC
- art. 7 LEC
- art. 253 LEC
- arts. 23 y 31 LEC
- art. 399.3 de la LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 2.2 CCiv
- art. 9.3 CE
- art. 1.7 CCiv
- art. 394 LEC
- Ley 29/1994

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

### Formulario 0323 · Impugnar la transmisión de la vivienda arrendada: demanda

- Año del modelo: 2020
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 46 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda sobre acción impugnatoria de transmisión de vivienda por exceder del precio de capitalización anual de la renta. Arrendamiento de viviendas anteriores al 9 de mayo de 1985.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña [NOMBRE Y APELLIDOS], Procurador/a. de los Tribunales en nombre y representación de Don [COMPLETAR], con domicilio en [LOCALIDAD], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO]; dirigido por el Abogado D./Dña [NOMBRE Y APELLIDOS], que redacta y firma el presente escrito, con despacho profesional abierto en esta localidad, calle [CALLE], ante el Tribunal comparezco y como mejor proceda en derecho, DIGO:

Que por medio del presente escrito deduzco DEMANDA DE JUICIO ORDINARIO EN ASUNTO RELATIVO A CONTRATO DE ARRENDAMIENTO URBANO, contra Don [COMPLETAR] con domicilio en [LOCALIDAD]; ejercitando acción impugnatoria de la transmisión efectuada de la vivienda arrendada sita en [LOCALIDAD], en base a los siguientes:

HECHOS

PRIMERO. Que con fecha [FECHA] mi mandante suscribió un contrato de arrendamiento con Don [COMPLETAR], respecto de la vivienda sita en [LOCALIDAD]

Adjunto, señalado como documento número [Nº DE DOCUMENTO], contrato de arrendamiento suscrito por las partes.

SEGUNDO. Con fecha [FECHA], Don [COMPLETAR], arrendador-propietario, enajenó la vivienda arrendada a Don [COMPLETAR] por la cantidad de [IMPORTE] euros, en virtud de escritura pública autorizada por el Notario de [COMPLETAR], Don [NOMBRE Y APELLIDOS]

Dicha escritura fue inscrita en el Registro de la Propiedad nº [NÚMERO] de [COMPLETAR], Tomo [COMPLETAR], Libro [COMPLETAR], Folio [COMPLETAR], Finca [COMPLETAR]

TERCERO. La renta anual que en el momento de la transmisión venía pagando mi mandante era de [IMPORTE] euros. El precio de la transmisión fue de [IMPORTE] euros. La vivienda fue arrendada en el año [COMPLETAR], y por tanto con posterioridad a la fecha indicada en el art. 53 del Texto Refundido de la Ley de Arrendamientos Urbanos aprobado por Decreto 4104/1964, de 24 de diciembre (TRLAU), el 1 de enero de 1942.

En definitiva, el precio de la transmisión, cargas incluidas, excede de la capitalización de la renta anual que en el momento de la transmisión paga el inquilino al tipo del [COMPLETAR] %.

Se acompaña a esta demanda, como documento nº [Nº DE DOCUMENTO], notificación del adquirente a mi cliente de las condiciones en que se efectuó la transmisión.

CUARTO. La parte actora manifiesta que, previo a la presentación de la presente demanda, se han llevaron a cabo negociaciones con la parte demandada, con el objetivo de cumplir el requisito de procedibilidad, y resolver la controversia de manera amistosa y extrajudicial. Dichas negociaciones se desarrollaron en cumplimiento de los principios de buena fe, con la intención de alcanzar una solución satisfactoria; incluyéndose entre las acciones realizadas el intercambio de comunicaciones formales mediante correspondencia escrita, en fechas [COMPLETAR], en las cuales esta parte expresó su disposición para dialogar y propuso alternativas de solución.

Finalmente, mi representado envío un requerimiento fehaciente al demandado con fecha [FECHA], fijando un plazo de 30 días naturales para llegar a un acuerdo amistoso, a través del abogado que firma este escrito, el cual fue contestado por el demandado por el mismo medio, rechazando el acuerdo/ habiendo sido solo posible un acuerdo parcial, viéndonos en la necesidad de acudir a la presente vía judicial, respecto a los extremos de la controversia en los que se mantiene la discrepancia.

Acompaño como documento nº [Nº DE DOCUMENTO], el requerimiento efectuado y como documento nº [Nº DE DOCUMENTO], la contestación del demandado.

FUNDAMENTOS DE DERECHO

I.- JURISDICCIÓN Y COMPETENCIA.

En cuanto a la competencia objetiva, el art. 85.1 LOPJ y art. 45 LEC, designan a los Tribunales de Instancia, como los órganos con la competencia específica, objetiva y funcional, para resolver este tipo de procedimiento. Asimismo, el Tribunal al que tengo el honor de dirigirme es competente territorialmente, al ser el del lugar en el que está sita la finca, según el art. 52.1.7º LEC.

II.- CAPACIDAD.

Demandante y demandado, personas físicas, tienen capacidad para ser parte (art. 6.1.1º LEC), titular de facultades y cargas del proceso, y asimismo plena capacidad procesal, al ser mayores de edad, sin limitación de ejercicio válido de derechos civiles, o para comparecer en juicio, en términos del art. 7 LEC, pretendiendo el actor y siendo pretendido el demandado, en sus respectivos nombres y derechos.

III.- LEGITIMACIÓN.

Corresponde a mi cliente la activa por ser parte arrendataria de la vivienda cuya transmisión se impugna. Y la pasiva corresponde al demandado Don [COMPLETAR], como adquirente de la vivienda y, por tanto, persona que ha de soportar los efectos derivados de las acciones ejercitadas en esta demanda.

IV.- CUANTÍA Y PROCEDIMIENTO.

Conforme al art. 253 LEC cifro la cuantía de la presente demanda en [IMPORTE] euros, correspondiente a una anualidad de renta del contrato de arrendamiento en el cual pretende subrogarse mi representado, según dispone el art. 251.9ª LEC.

Asimismo, el art. 249.1.6º LEC dice que se decidirá en juicio ordinario las demandas que versen sobre cualesquiera asuntos relativos a arrendamientos urbanos, salvo excepciones que no comprenden el presente supuesto. Son de aplicación, por tanto, el art. 399 y siguientes de la LEC.

V.- POSTULACIÓN Y DEFENSA.

Conforme a lo previsto en los arts. 23 y 31 LEC, se presenta la demanda por medio de Procurador/a. legalmente habilitado y bajo dirección de Letrado firmante de la misma.

VI. Cumplimiento de los requisitos de procedibilidad

La presente demanda cumple con los requisitos de procedibilidad exigidos por el art. 264.4º y art. 399.3 de la LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VII.- FONDO DE LA CUESTIÓN CONTROVERTIDA

a) Sobre la legislación aplicable

Dicha normativa viene constituida por la Disposición Transitoria 2ª de la Ley 29/1994, de 24 de noviembre, de Arrendamientos Urbanos (LAU), la cual determina la aplicación, para contratos subsistentes el 1 de enero de 1.995 y que hubieren sido otorgados antes del 9 de mayo de 1.985, del TRLAU, salvo las propias modificaciones reguladas en la norma transitoria precitada, que en nada afecta a la acción ejercitada a través de la presente demanda, de las prevenciones contenidas en los arts. 52 y 53 TRLAU de 1964.

b) Sobre la acción ejercitada

Se ejercita acción de impugnación de la transmisión en base al art. 53 TRLAU de 1964, a cuyo tenor el inquilino, y en supuestos de transmisión de la vivienda arrendada, si no ejercita el derecho de tanteo o retracto puede impugnar la transmisión en el caso de que el precio de la transmisión exceda de la capitalización de la renta anual que en el momento de la transmisión pague el inquilino al tipo del 3 por 100 si la vivienda hubiere sido ocupada por primera vez antes del 1 de enero de 1.942 y al 4,5 por 100 si lo fuere con posterioridad, y, caso de prosperar la acción, no podrá el adquirente negar la prórroga del contrato de arrendamiento fundándose en la causa primera del art. 62.

Respecto a la aplicación del art. 53 TRLAU de 1964, el TS establece como doctrina jurisprudencial en sendas sentencias de 15 de enero de 2009, números 1226/2009 y 1227/2009, que el predicho artículo está vigente, conforme a lo previsto en la Disposición Transitoria segunda A) LAU 1994, siendo plenamente aplicable a los arrendamientos celebrados con anterioridad al 9 de mayo de 1985, y su ejercicio no supone un abuso de derecho, al ejercitarse la acción impugnatoria con fundamento en una facultad reconocida legalmente, toda vez que la virtualidad del art. 2.2 CCiv en cuanto al principio de derogación de las normas, el principio de seguridad jurídica del art. 9.3 CE y la doctrina del Tribunal Constitucional en este particular, así como la regla de la tutela efectiva para la resolución de los pleitos "secundum legem", y de acuerdo con el sistema de fuentes establecido (art. 1.7 CCiv), sin que la interpretación sociológica permita la derogación de una norma que pretende proteger al inquilino, objetivo al que responde el mencionado art. 53.

c) Sobre la caducidad de la acción

La acción de impugnación caduca a los 60 días naturales contados desde que el adquirente notificó fehacientemente al inquilino las condiciones en que se efectuó la transmisión conforme exige el art. 48.2 TRLAU 1964.

Mi mandante recibió dicha notificación con fecha [FECHA], por lo que está dentro de plazo para el ejercicio de la referida acción.

VIII.- COSTAS.

Conforme al art. 394 LEC, las costas han de imponerse a la demandada.

Por lo expuesto,

SUPLICO AL TRIBUNAL:

Que habiendo por presentado este escrito de demanda con los documentos que lo acompañan y copias de uno y otros, los admita y me tenga por comparecido en parte en la representación que ostento y que acreditada dejo; y por promovido juicio declarativo ordinario frente a Don [COMPLETAR], acordando dar traslado la misma para que comparezca y la conteste, y, previo los trámites legales y recibimiento a prueba que desde ahora se interesa, se dicte en su día sentencia por la que, con íntegra estimación de esta demanda y de la acción impugnatoria ejercitada:

a) DECLARE que el precio por el que el demandado, Don [COMPLETAR], adquirió mediante escritura pública de compraventa de fecha [FECHA], el piso [COMPLETAR] de la calle [CALLE] n° [COMPLETAR] de [COMPLETAR], arrendado a mi patrocinado, supera la capitalización de la renta anual que a dicha fecha abonaba el inquilino demandante;
b) como consecuencia de lo anterior, DECLARE que el adquirente del piso mencionado, Don [COMPLETAR], no podrá negar la prórroga del contrato de arrendamiento fundándose en la causa primera del art. 62 TRLAU 1964 ya citado;
c) CONDENE a la parte demandada a estar y pasar por las anteriores declaraciones.

Todo ello con expresa imposición de las costas procesales a la parte demandada.

Es justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

	Firma de Procurador/a
