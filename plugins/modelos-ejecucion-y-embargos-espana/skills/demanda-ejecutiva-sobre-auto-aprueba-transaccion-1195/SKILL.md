---
name: demanda-ejecutiva-sobre-auto-aprueba-transaccion-1195
description: "Redacta el escrito «Demanda ejecutiva sobre auto que aprueba una transacción judicial» (formulario 1195 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda ejecutiva sobre auto que aprueba una transacción judicial

> Formulario 1195 del plugin **Ejecución civil** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] NÚMERO (4 veces)
- [ ] ACTO O RESOLUCIÓN (2 veces)
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] IMPORTE (4 veces)
- [ ] FECHA (5 veces)
- [ ] Nº
- [ ] LUGAR
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…mulo DEMANDA EJECUTIVA contra la entidad»; «…la audiencia previa del juicio ordinario»; «…de»; «…de [COMPLETAR], el»; «…, el [COMPLETAR], en el libro»; «…, en el libro [COMPLETAR], folio»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 19.2 LEC
- art. 517.1 LEC
- art. 545.1 LEC
- art. 538.1 LEC
- art. 539.1 LEC
- art. 549 LEC
- art. 548 LEC
- art. 576 LEC

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

### Formulario 1195 · Demanda ejecutiva sobre auto que aprueba una transacción judicial

- Año del modelo: 2014
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 28 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a. de los Tribunales, que actúa en nombre y representación de [NOMBRE DEL REPRESENTADO/A] SL, cuya representación procesal tengo acreditada en los autos de juicio ordinario, registrados con el número [NÚMERO], seguidos frente a [ACTO O RESOLUCIÓN] SA, ante este Tribunal comparezco y como mejor proceda, DIGO:

Que en la representación que ostento formulo DEMANDA EJECUTIVA contra la entidad [COMPLETAR] SA, con domicilio en [LOCALIDAD], calle [CALLE], en reclamación de la cantidad de [IMPORTE] euros en concepto de principal, más la de [IMPORTE] euros en concepto de intereses moratorios procesales y costas de la ejecución, presupuestadas provisionalmente, con base en los siguientes:

HECHOS

PRIMERO.- Tras la audiencia previa del juicio ordinario [COMPLETAR] celebrada en fecha [FECHA], las partes ejecutante y ejecutada llegaron a un acuerdo que fue presentado ante el Tribunal para su homologación de acuerdo con lo establecido en el art. 19.2 LEC.

Dicho acuerdo tenía el siguiente contenido:

"SA ySL ponen fin a sus diferencias en relación con el contrato defirmado entre ambos el, y resuelto el, acordando que la primera abonará a la segunda la cantidad deeuros en el plazo de un mes desde la fecha de la resolución judicial que homologue el acuerdo alcanzado"

SEGUNDO.- Mediante auto de fecha [FECHA] se homologó por el Tribunal el citado acuerdo.

Se acompaña como documento n.º [NÚMERO] testimonio de dicho auto homologando el acuerdo, así como de este último.

TERCERO.- Han transcurrido más de veinte días desde el día [Nº], mes posterior a la homologación judicial, habiéndose intentado por mi representada infructuosamente percibir de la parte contraria la cantidad pactada, viéndose obligado a interponer la presente demanda.

CUARTO.- Mi mandante tiene conocimiento de que la entidad ejecutada es titular del siguiente bien susceptible de embargo, que se considera suficiente para el fin de la ejecución:

- Finca n.º [NÚMERO] inscrita en el Registro de la Propiedad n.º [NÚMERO] de [COMPLETAR], el [COMPLETAR], en el libro [COMPLETAR], folio [COMPLETAR], inscripción

A los anteriores hechos resultan de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

PRIMERO.- Conforme al art. 517.1 LEC la acción ejecutiva deberá fundarse en un título que tenga aparejada ejecución, encontrándose entre éstos, como dispone el art. 517.2.3.º del mismo texto legal, las resoluciones judiciales que aprueben u homologuen transacciones judiciales y acuerdos logrados en el proceso.

SEGUNDO.- El Tribunal al que me dirijo es el tribunal competente, según lo establecido por el art. 545.1 LEC, por ser el órgano judicial que homologó el acuerdo suscrito entre las partes para poner fin al proceso declarativo indicado.

TERCERO.- Las partes en este concreto proceso de ejecución, ejecutante y ejecutado, quedan determinadas mediante legitimación ordinaria directa, con arreglo al art. 538.1 LEC como acreedor y deudor que figuran en el título ejecutivo, siendo mi mandante titular de crédito pecuniario de la cantidad indicada frente a la sociedad demandada.

CUARTO.- Conforme a lo dispuesto en el art. 539.1 LEC, la demanda viene firmada por abogado y Procurador/a., ya que estamos ante la ejecución de una resolución dictada en un proceso en que es preceptiva la intervención de dichos profesionales.

QUINTO.- La presente demanda contiene todos los requisitos enumerados en el art. 549 LEC, ya que se ha indicado cuál es el título en que se funda, la tutela ejecutiva que se pretende y la entidad frente a la que se interesa el despacho de la ejecución, así como los bienes del ejecutado susceptibles de embargo conocidos por mi poderdante. Por último se acompaña a la demanda ejecutiva la documentación necesaria de la contemplada en el art. 550 del mismo texto legal. Asimismo, se ha superado con creces el plazo de espera de 20 días del art. 548 LEC, desde la homologación en sí, dado que ha transcurrido el plazo del mes específicamente previsto en el acuerdo que aquí se pretende ejecutar.

SEXTO.- Procede la imposición del pago del interés por mora procesal del art. 576 LEC, dado que si el auto resulta ejecutable por los trámites establecidos para la ejecución forzosa en la Ley de Enjuiciamiento Civil, el establecimiento de una obligación de pago de suma en aquél se hace equivalente a una condena firme de cantidad líquida, tal y como se dispone en el apartado tercero de aquel precepto legal.

SÉPTIMO.- En virtud de lo dispuesto en el art. 539.2, párrafo 2.º en relación con el 583.2 LEC, las costas de la ejecución serán a cargo del ejecutado, puesto que no es preciso ninguna imposición expresa.

Por lo anteriormente expuesto,

SUPLICO AL TRIBUNAL

que, teniendo por presentado este escrito con los documentos que se acompañan, y sus copias, se sirva admitirlo, ordenando se entiendan conmigo las sucesivas diligencias y en nombre de mi patrocinado se me tenga por comparecido y parte, y por presentada demanda ejecutiva, se digne, previo el traslado legal, despachar ejecución frente a [ACTO O RESOLUCIÓN] SA, en cumplimiento del auto de fecha [FECHA], por el cual se homologó el acuerdo alcanzado entre ejecutante y ejecutados en fecha [FECHA], por el importe de la cantidad de [IMPORTE] euros ( €) en concepto de principal, más otros [IMPORTE] euros ( €) presupuestados provisionalmente para los intereses que puedan generarse durante la ejecución y las costas de ésta, procediéndose, mediante decreto del Letrado de la Administración de Justicia, al embargo de la finca designada en el ordinal 4.º de los hechos de esta demanda, que deberá asegurarse mediante mandamiento dirigido al Registrador de la Propiedad de

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

========================================================================
