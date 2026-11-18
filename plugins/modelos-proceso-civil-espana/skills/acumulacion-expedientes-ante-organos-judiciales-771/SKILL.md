---
name: acumulacion-expedientes-ante-organos-judiciales-771
description: "Redacta el escrito «Acumulación de expedientes ante órganos judiciales distintos» (formulario 771 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acumulación de expedientes ante órganos judiciales distintos

> Formulario 0771 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] SEDE (3 veces)
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] FECHA (3 veces)
- [ ] Nº DE EXPEDIENTE (3 veces)
- [ ] NÚMERO (2 veces)
- [ ] LUGAR
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…nta General Extraordinaria de la entidad»; «…/»; «…ración de Justicia a celebrar el próximo»; «…./Dña. [NOMBRE Y APELLIDOS] y la entidad»; «…/»; «…recencia a celebrar un mes más tarde, el»; «… refieren a la misma sociedad mercantil,»; «…numeración del juzgado de procedencia).]»; «…ribunal superior común, en este caso, la»; «…/»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 15 Ley 15/2015
- art. 119.4 LJV
- art. 15 LJV
- art. 12 LJV
- art. 15.2 LJV
- art. 88 LEC
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

### Formulario 0771 · Acumulación de expedientes ante órganos judiciales distintos

- Año del modelo: 2015
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; restos de formato retirados; notas del formulario agrupadas al final (1); 26 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Solicitud de acumulación de expedientes de jurisdicción voluntaria ante distintos órganos judiciales mediante decreto dictado por el Letrado de la Administración de Justicia, previo traslado al órgano de administración social y previa comunicación de la solicitud al Tribunal para que suspenda el expediente.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

Que por medio del presente escrito, y al amparo de lo dispuesto en el art. 15 Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), solicito la ACUMULACIÓN DE EXPEDIENTES FORMULADOS ANTE DISTINTOS ÓRGANOS JUDICIALES, en base a las siguientes

ALEGACIONES

PRIMERA.- Que el pasado [FECHA], insté ante el órgano judicial al cual tengo el honor de dirigirme, la convocatoria de Junta General Extraordinaria de la entidad [COMPLETAR] SL, con un orden del día concretado en seis puntos. Mediante diligencia de ordenación de fecha [FECHA], se incoó el presente expediente con nº [Nº DE EXPEDIENTE] / [COMPLETAR], y se citó al órgano de administración de la citada mercantil y a mi persona a una comparecencia ante el Letrado de la Administración de Justicia a celebrar el próximo [COMPLETAR], de conformidad con lo dispuesto en el art. 119.4 LJV.

SEGUNDO.- Posteriormente, un grupo de socios conformado por D./Dña. [NOMBRE Y APELLIDOS], D./Dña. [NOMBRE Y APELLIDOS] y la entidad [COMPLETAR] SL, realizó similar solicitud, que fue repartida a la Sección de lo Mercantil del Tribunal de Instancia nº [NÚMERO], también de Madrid, para la convocatoria de otra Junta General Extraordinaria, con un orden del día diferente, salvo en dos de sus puntos, prácticamente idénticos. Se dictó, por el Letrado de la Administración de Justicia de dicho órgano judicial diligencia de ordenación, incoando expediente con nº [Nº DE EXPEDIENTE] / [COMPLETAR], citando a tales socios y al órgano de administración a otra segunda comparecencia a celebrar un mes más tarde, el [COMPLETAR]. Ambas solicitudes son correctas, y se contraen a los requisitos legales exigidos por los arts. 168 y 169 del Texto Refundido de la Ley de Sociedades de Capital aprobado por RDLeg. 1/2010, reuniendo cada solicitante el porcentaje mínimo de capital social, y habiendo realizado el preceptivo requerimiento notarial previo, finalmente inatendido por los administradores sociales.

TERCERO.- Que, tratándose de dos solicitudes similares, a pesar de que los puntos del día difieren parcialmente, procede, en virtud de lo dispuesto en el art. 15 LJV, su acumulación en el presente expediente, por ser el primero incoado, a efectos de verificar la comparecencia previa ante el Letrado de la Administración de Justicia en un mismo acto, de manera que los administradores sociales puedan admitir la celebración de la Junta con los órdenes del día interesados; o, en su caso, se convoque judicialmente con ambos órdenes convenientemente integrados. Concurren, en este sentido, los requisitos exigidos por el mencionado precepto legal:

1.- Ambas peticiones tienen por objeto la convocatoria del mismo tipo de Junta General de socios, coincidiendo en dos de los puntos del día, y teniendo una cierta relación los restantes. Es evidente, por ello, esa conexión entre las dos juntas que aconsejan que los correspondientes debates y votaciones se hagan en un solo acto.
2.- Las dos convocatorias se refieren a la misma sociedad mercantil, [COMPLETAR] SL, independientemente de que se solicite por sujetos distintos, todos ellos socios de la primera.
3.- Tratándose de expedientes pendientes ante distintos órganos judiciales, la presente petición se realiza por escrito ante el este Tribunal, a quien se considera competente, por haber sido el primero en el tiempo en conocer de la primera solicitud.
4.- Ninguno de los dos expedientes tiene naturaleza contenciosa que haga entrar en juego la prohibición contenida en el apartado tercero del citado art. 12 LJV.

CUARTO.- A partir de lo dispuesto en el art. 15.2 LJV, y por remisión al art. 88 LEC, se solicita que el Letrado de la Administración de Justicia dé noticia de la petición de acumulación a la Sección de lo Mercantil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] a fin de que suspenda la tramitación del expediente. Asimismo, se solicita que se dé traslado al órgano de administración social para que formule alegaciones en el plazo de diez días, y que por el citado Letrado de la Administración de Justicia se dicte finalmente decreto requiriendo a dicho órgano judicial de acumulación. En el supuesto de que el órgano requerido no accediere a la acumulación, resolverá el Tribunal superior común, en este caso, la [COMPLETAR].

QUINTO.- Que acompaño a este escrito testimonio de las dos diligencias de ordenación dictadas en cada uno de los dos Tribunales de lo Mercantil por cada Letrado de la Administración de Justicia, donde se pueden comprobar la incoación de ambos expedientes y todas las circunstancias reseñadas.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito y los documentos que se acompañan, y por promovida solicitud de acumulación de expedientes de jurisdicción voluntaria en tramitación ante distintos órganos judiciales, de conformidad con el art. 15 LJV, y previo traslado al órgano de administración social por plazo de 10 días, y previa comunicación de la solicitud a la Sección de lo Mercantil del Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO] a fin de que suspenda el expediente; se proceda por el Letrado de la Administración de Justicia a dictar decreto en el cual se requiera de acumulación a dicho órgano judicial, en relación al expediente que tramita como nº [Nº DE EXPEDIENTE] / [COMPLETAR] al presente, dejando sin efecto la segunda comparecencia fijada en aquel.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) Exigible en este expediente expresamente, conforme art. 118.3 LJV.

========================================================================
