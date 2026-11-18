---
name: alegacion-cosa-juzgada-760
description: "Redacta el escrito «Alegación de cosa juzgada» (formulario 760 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegación de cosa juzgada

> Formulario 0760 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] SEDE (2 veces)
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] FECHA (7 veces)
- [ ] Nº DE EXPEDIENTE (2 veces)
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…numeración del juzgado de procedencia).]»; «…nta General Extraordinaria de la entidad»; «…/»; «…/»; «…ueva comparecencia a celebrar el próximo»; «…a liquidación y disolución de la entidad»; «…numeración del juzgado de procedencia).]»

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 19.3 de la Ley 15/2015
- art. 119 LJV
- art. 119.5 LJV
- art. 19.3 LJV
- art. 118.3 LJV

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

### Formulario 0760 · Alegación de cosa juzgada

- Año del modelo: 2015
- Revisión 17-11-2026: 3 citas normativas corregidas tras comprobarlas en el BOE; restos de formato retirados; notas del formulario agrupadas al final (1); 24 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito por el que se pone de manifiesto la existencia de cosa juzgada en relación con lo solicitado en el expediente, previo traslado al solicitante para que formule alegaciones al respecto; a fin de que se resuelva apreciar dicha excepción, dictándose decreto que archive el presente expediente.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

Que por medio del presente escrito, y al amparo de lo dispuesto en el art. 19.3 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), procedo a poner de manifiesto la EXISTENCIA DE COSA JUZGADA en relación con lo solicitado en el presente expediente, con arreglo a las siguientes

ALEGACIONES

PRIMERA.- Que el pasado [FECHA], D./Dña. [NOMBRE Y APELLIDOS] instó ante la Sección de lo Mercantil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], la convocatoria de Junta General Extraordinaria de la entidad [COMPLETAR] SL, de la cual es socio, con un orden del día concretado en apreciación de la causa de disolución legal de dicha mercantil, y consiguiente apertura de la fase de liquidación. El expediente con nº [Nº DE EXPEDIENTE] / [COMPLETAR], se tramitó conforme al art. 119 LJV, y se citó al solicitante y al administrador social único de aquella a una comparecencia celebrada el pasado [FECHA]. En la misma se puso de manifiesto que el solicitante no representaba el capital social mínimo del 5%, exigido en el art. 168 de la Ley de Sociedad de Capital para poder instar aquella, dictándose decreto de fecha [FECHA] por el Letrado de la Administración de Justicia del citado órgano judicial, en el cual declaraba no haber lugar a la convocatoria pretendida, al no reunirse los requisitos legalmente exigidos. Dicha resolución no fue recurrida por el solicitante, y devino firme.

SEGUNDO.- A pesar de ello, el pasado [FECHA] D./Dña. [NOMBRE Y APELLIDOS] volvió a solicitar la convocatoria de Junta General Extraordinaria de la misma entidad, añadiendo un segundo punto del día que consistía en el cese del administrador social, y sin que se haya producido ninguna suerte de cambio en el capital social que permita al mismo alcanzar el citado mínimo del 5%. Tras operarse el oportuno reparto en el Servicio Común de Registro y Reparto del Tribunal de Instancia, los autos correspondieron al órgano judicial al cual tengo el honor de dirigirme, incoándose el presente expediente con nº [Nº DE EXPEDIENTE] / [COMPLETAR], mediante diligencia de ordenación de fecha [FECHA], en la que se volvía a citar a mi mandante y al solicitante a nueva comparecencia a celebrar el próximo [COMPLETAR].

TERCERO.- Nos encontramos, de esta forma, con un segundo expediente de jurisdicción voluntaria sobre idéntico objeto del ya resuelto mediante decreto firme del Letrado de la Administración de Justicia antes indicado. El hecho de que la petición que aquí nos ocupa contenga un segundo punto del orden del día, no altera tal circunstancia, toda vez que es el mismo socio, sin haberse modificado las participaciones en las que está dividido el capital social, quien intenta que se vuelva a discutir el porcentaje del que dispone, para lograr una convocatoria de Junta General Extraordinaria. En la que, además, persigue finalmente lo mismo, instar la liquidación y disolución de la entidad [COMPLETAR] SL, actualmente en pleno funcionamiento. Y ello, sin que haya recurrido el decreto que le vedó tal posibilidad, el cual no estaba exento de vía de impugnación, a sensu contrario de lo dispuesto en el último párrafo del art. 119.5 LJV.

Al respecto, el art. 19.3 LJV impide iniciar un segundo expediente de jurisdicción voluntaria, salvo que cambien las circunstancias que dieron lugar al primero; lo que, en modo alguno ha ocurrido. Y ello, a diferencia de un proceso jurisdiccional posterior, que sí que podría tramitarse conforme al apartado cuarto de tal precepto legal. Es decir, la Ley de Jurisdicción Voluntaria establece un precepto que debe conectarse con el art. 222 de la Ley de Enjuiciamiento Civil, que también excluye los procesos posteriores en su primer apartado por efecto de la cosa juzgada. En consecuencia, al prohibirse legalmente el inicio de este expediente, lo que el Tribunal no pudo tener en cuenta al desconocer la circunstancia aquí alegada; procede ponerle fin, sin necesidad de celebrar la comparecencia convocada, dictando decreto de archivo del mismo.

CUARTO.- Que acompaño a este escrito testimonio del decreto del Letrado de la Administración de Justicia de la Sección de lo Mercantil del TI de [LOCALIDAD], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], de fecha [FECHA], y de la diligencia de ordenación que determina su firmeza al no haberse recurrido.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito y por alegada la existencia de cosa juzgada, de conformidad con el art. 19.3 LJV, y previo traslado al solicitante para que formule alegaciones al respecto; se resuelva apreciar dicha excepción, dictándose decreto que archive el presente expediente, dejando sin efecto la comparecencia convocada.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) Exigible en este expediente expresamente, conforme art. 118.3 LJV.

========================================================================
