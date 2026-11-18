---
name: demanda-ejecutiva-saldo-cuenta-937
description: "Redacta el escrito «Demanda ejecutiva por el saldo de una cuenta» (formulario 937 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda ejecutiva por el saldo de una cuenta

> Formulario 0937 del plugin **Ejecución civil** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO (2 veces)
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (8 veces)
- [ ] DNI/NIE (2 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (9 veces)
- [ ] IMPORTE (9 veces)
- [ ] NOMBRE DEL NOTARIO
- [ ] FECHA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Demanda ejecutiva Juicio»; «…D/.Dña»; «…s, interviniendo en nombre de la entidad»; «…, n.º [NÚMERO], de»; «…so en los siguientes HECHOS Con fecha de»; «… correspondientes a las mensualidades de»; «…del pasado año»; «…, y a las mensualidades de»; «…del presente año. La cláusula»; «… Acompaño reseñados como documentos núms»; «…euros más otros»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 517 de la LEC
- art. 592 LEC
- arts. 61 y 545 de la LEC
- art. 549 de la LEC
- art. 517.5 de la LEC
- art. 520 de la LEC
- art. 573 de la LEC
- art. 2.a) de la Ley 10/2012
- artículo 581.2 de la LEC

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

### Formulario 0937 · Demanda ejecutiva por el saldo de una cuenta

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 45 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda ejecutiva

Juicio [COMPLETAR] (ordinario/verbal) n.º [Nº DE PROCEDIMIENTO]/[AÑO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D/.Dña [COMPLETAR], Procurador/a de los Tribunales, interviniendo en nombre de la entidad [COMPLETAR] cuyas circunstancias constan en la escritura de poder que acompaño para acreditar mi representación y cuya devolución solicito previa su oportuna constancia en autos, ante el Tribunal comparezco bajo la dirección del Letrado D./Dña [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO:

Que por medio del presente escrito, y en la representación que acredito, formulo demanda ejecutiva, en la que ejercito la acción ejecutiva prevista en el art. 517 de la LEC, contra D./Dña [NOMBRE Y APELLIDOS], mayor de edad, provisto de DNI [DNI/NIE] y domiciliado en calle [CALLE], n.º [NÚMERO], de [COMPLETAR], con objeto de que, previa la tramitación oportuna, se dicte auto, por el Tribunal conteniendo orden general de ejecución y de despacho de ejecución por el principal de [IMPORTE] euros más [IMPORTE] euros que se calculan bastantes para intereses, gastos y costas y por el Secretario decreto para su efectividad en los términos interesados en el suplico de esta demanda ejecutiva que baso en los siguientes

HECHOS

Con fecha de [COMPLETAR] mi representada hizo entrega de un préstamo por la suma de [IMPORTE] euros al demandado mediante su abono en la cuenta corriente referenciada con n.º [NÚMERO] de la sucursal bancaria que mi mandante tiene abierta con domicilio en calle [CALLE], n.º [NÚMERO], de esta capital.

Para instrumentar la operación de préstamo ambas partes suscribieron la Póliza de Préstamo que acompaño referenciada como documento n.º [NÚMERO] Dicha póliza fue intervenida por el Notario D./Dña [NOMBRE DEL NOTARIO] Como documento n.º [NÚMERO] acompaño certificación del mencionado profesional acreditativa de su intervención y de la conformidad de dicha Póliza con el asiento relativo a la misma que aparece en su Libro Registro con fecha

Entre las condiciones pactadas en la Póliza referida en ordinales precedentes pueden destacarse las siguientes: (desarrollar las que sean de interés para el caso, y especialmente la que establezca el pacto de que la cantidad exigible en caso de ejecución será la resultante de la liquidación efectuada por el acreedor en la forma convenida por las partes en el propio título ejecutivo).

El demandado D./Dña [NOMBRE Y APELLIDOS] ha incumplido reiteradamente su obligación de pago de los plazos de amortización del capital e intereses del préstamo en las fechas convenidas, dejando de hacer efectivos los pagos correspondientes a las mensualidades de [COMPLETAR] del pasado año [COMPLETAR], y a las mensualidades de [COMPLETAR] del presente año.

La cláusula [COMPLETAR] de la Póliza adjunta autoriza a la Entidad crediticia para considerar vencido el préstamo en caso de incumplimiento de la obligación de pago de cualquiera de los plazos de amortización de capital e intereses del préstamo previstos, pudiendo exigir desde ese momento el resto de principal pendiente de pago, así como los intereses devengados y los gastos.

(Desarrollar con la debida extensión las circunstancias que justifican la solicitud de despacho de ejecución.)

Como documento n.º [NÚMERO] se acompaña certificación de extractos de los movimientos de cuenta con las partidas de cargo y abono y la aplicación de intereses de los que se desprende el saldo deudor por el que se pide ejecución, debidamente intervenidas por el Corredor de Comercio que intervino la Póliza.

Como documento n.º [NÚMERO] se adjunta certificación del Notario que ha intervenido la Póliza y la operación liquidatoria, acreditativa de que la liquidación practicada se ha verificado con arreglo a los términos convenidos entre las partes según exige el art. 573.1.2.º de la LEC.

Se ha notificado al deudor (en su caso, y al fiador) la cantidad exigible, exigiendo su pago, a los efectos previstos en el art. 573.1.3.º de la LEC. Como documento n.º [NÚMERO] acompaño certificación de la oficina de correos acreditativa de la entrega mediante servicio de burofax de la comunicación dirigida al deudor y del texto de dicha comunicación.

Son bienes del ejecutado susceptibles de embargo los siguientes: (detallar según el orden legal —art. 592 LEC—). Acompaño reseñados como documentos núms [COMPLETAR] notas registrales acreditativas de la inscripción de inmuebles de la titularidad del ejecutado.

Los bienes detallados en el ordinal precedente no parecen suficientes para cubrir las sumas reclamadas, por lo que para la localización de bienes del ejecutado con los que hacer frente a su obligación de pago aparecen como necesarias las siguientes medidas de investigación judicial

A los hechos antecedentes resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

Es competente para conocer de esta ejecución el Tribunal a que me dirijo por ser quien dictó la resolución cuya ejecución se pide (arts. 61 y 545 de la LEC).

Legitimación

Art. 549 de la LEC: La ejecución se despachará “a petición de parte”.

Trámite y requisitos procesales

• Sólo se despachará ejecución a petición de parte y en forma de demanda con los requisitos que se desarrollan en el art. 549 de la LEC.

• A los efectos previstos en el art. 549.1.1.º de la LEC se reseña que el título ejecutivo en que se funda esta demanda ejecutiva es la Póliza de Préstamo mercantil que se acompaña reseñada como documento n.º [NÚMERO], juntamente con la certificación del Notario que la intervino acreditativa de su intervención y de la conformidad de dicha Póliza con el asiento relativo a la misma que aparece en su Libro Registro con fecha [FECHA] Se cumple así el requisito previsto en el art. 550.1.1.º de la LEC.

• La tutela ejecutiva pretendida es la estimación de la presente reclamación que se formula contra el ejecutado D./Dña [NOMBRE Y APELLIDOS] del principal de [IMPORTE] euros correspondiente a principal del préstamo e intereses vencidos pendientes de pago, así como de otros [IMPORTE] euros presupuestados para intereses, gastos y costas que se causen.

• También se acompaña poder notarial que acredita la representación del procurador, a los efectos previstos en el art. 550.1.2 del mismo texto legal.

• El título que sirve de base a esta demanda ejecutiva tiene aparejada ejecución de conformidad con lo dispuesto en el art. 517.5 de la LEC.

• Se cumple el requisito exigido en el art. 520 de la LEC para el despacho de ejecución basado en título de los enumerados en los incisos 4.º a 7.º del apartado 2 del art. 517 de la LEC, al solicitarse despacho de ejecución por cantidad determinada superior a 300 euros.

• Art. 572.2.º de la LEC: Podrá despacharse ejecución por el importe del saldo resultante de operaciones derivadas de contratos formalizados en escritura pública o en póliza intervenida por fedatario público que incluyan pacto de que la cantidad exigible en caso de ejecución será la resultante de la liquidación efectuada por el acreedor en la forma convenida por las partes en el propio título ejecutivo.

• También se cumplen los requisitos documentales exigidos por el art. 573 de la LEC.

• (Solo para personas jurídicas que no tengan reconocido derecho de justicia gratuita) TASAS JUDICIALES: Acompañamos a la demanda modelo tributario 696 de liquidación de tasa por ejercicio de la potestad jurisdiccional debidamente cumplimentado, según exigen el art. 2.a) de la Ley 10/2012, de 20 de noviembre y la Orden que aprueba los modelos de autoliquidación de la tasa.

• Art. 581 de la LEC: Despachada la ejecución se formulará requerimiento de pago al ejecutado por la cantidad reclamada en concepto de principal e intereses devengados hasta la fecha de la demanda y si no pagase en el acto el Tribunal procederá al embargo. Pero no procede requerimiento si con la demanda se acompaña acta notarial que acredite haber requerido de pago al deudor con diez días de antelación.

• Arts. 551 y ss. sobre trámite para el despacho de la ejecución y oposición a la misma.

Fondo

El art. 517.5.º de la LEC reconoce ejecutividad a la sentencia firme. (Desarrollar los fundamentos específicos del caso.)

Costas

Deberán imponerse al demandado aun cuando pagase al ser requerido según el art. 561.1.1.ª y en el mismo sentido el art. 583, ambos de la LEC.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL: Tenga por presentado este escrito, certificaciones y demás documentos que acompaño, se sirva admitirlo, teniendo por interpuesta demanda ejecutiva frente a D./Dña [NOMBRE Y APELLIDOS], ya circunstanciado, la admita a trámite y en su virtud acuerde lo necesario para el impulso procedimental pertinente,

1.º dictando auto mediante el que se dicte orden general despachando ejecución a favor de D./Dña. [NOMBRE Y APELLIDOS] y contra el ejecutado D./Dña [NOMBRE Y APELLIDOS] por el principal de [IMPORTE] euros y otros [IMPORTE] euros que, sin perjuicio de ulterior liquidación, se calculan provisionalmente para el pago de intereses pactados y costas, requiriendo una vez despachada ejecución de pago al deudor ejecutado por la suma del principal de [IMPORTE] euros más otros [COMPLETAR] presupuestados para intereses y costas (si se hubiere adjuntado a la demanda acta notarial acreditativa de haber requerido el pago con diez días de antelación a la demanda: artículo 581.2 de la LEC no se practicará este requerimiento previo).

2.º y que por el Letrado de la Administración de Justicia se decrete, en caso de impago, el embargo de los siguientes bienes concretos del demandado:

Y se practiquen, si no paga el ejecutado al ser requerido, las siguientes medidas de averiguación de bienes: Que a través del punto neutro de información judicial se una a autos relación de bienes, derechos y cuentas bancarias de la que es titular D./Dña [NOMBRE Y APELLIDOS] con DNI n.º [DNI/NIE] dictando en su día, si mediare oposición, previa la tramitación oportuna, auto mediante el que se declare procedente que la ejecución siga adelante, y acordando, en todo caso, hacer trance y remate de los bienes embargados y pagar con el importe obtenido a mi poderdante el principal reclamado de [IMPORTE] euros más la cantidad correspondiente a los intereses pactados hasta el completo pago, así como las costas causadas y que se causen hasta la total efectividad de la ejecución que expresamente se impondrán al ejecutado.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
