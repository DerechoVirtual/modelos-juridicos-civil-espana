---
name: condiciones-particulares-contrato-pliego-485
description: "Redacta el escrito «Condiciones particulares del contrato (pliego)» (formulario 485 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Condiciones particulares del contrato (pliego)

> Formulario 0485 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] NÚMERO (4 veces)
- [ ] CALLE (3 veces)
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] IMPORTE
- [ ] TELÉFONO
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, bajo comercial, de las casas números»; «…y»; «…y [COMPLETAR] de la calle [CALLE] de»; «… una superficie construida aproximada de»; «…. Le corresponde una cuota de»; «…, folio»; «…, folio [COMPLETAR] del libro»; «…del libro [COMPLETAR] de la Sección»; «…de la Sección [COMPLETAR], tomo»; «…de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 110.1.c) LJV
- Ley 6/2020

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

### Formulario 0485 · Condiciones particulares del contrato (pliego)

- Año del modelo: 2017
- Revisión 17-11-2026: 23 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (IMPORTE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de pliego de condiciones particulares con arreglo a las cuales ha de celebrarse la subasta y donde se recoge la valoración de los bienes o derechos a subastar, cuya aportación a la solicitud de inicio del expediente de subasta voluntaria judicial requiere el art. 110.1.c) LJV.

A) Bien objeto de la subasta

A.1.- Título: departamento n.º [NÚMERO], bajo comercial, de las casas números [COMPLETAR] y [COMPLETAR] de la calle [CALLE] de [COMPLETAR].

A.2.- Descripción: Urbana. Local comercial situado en la planta baja al fondo del portal n.º [NÚMERO]. Ocupa una superficie construida aproximada de [COMPLETAR] metros cuadrados y linda: al frente, con la calle [CALLE] y con rampa de acceso al sótano; derecha desde ese frente, con dicha rampa de acceso al sótano y con calle [CALLE]; por la izquierda, con locales de Don/Doña [NOMBRE Y APELLIDOS] y Don/Doña [NOMBRE Y APELLIDOS]; y por el fondo, con local de Don/Doña [NOMBRE Y APELLIDOS] y Don/Doña [NOMBRE Y APELLIDOS]. Le corresponde una cuota de [COMPLETAR] %.

A.3.- Inscripción registral: finca n.º [NÚMERO], folio [COMPLETAR] del libro [COMPLETAR] de la Sección [COMPLETAR], tomo [COMPLETAR] del Archivo, del Registro de la Propiedad n.º [NÚMERO] de [COMPLETAR].

A.4.- Referencia catastral:

A.5.- Valor del bien a efectos de subasta: [IMPORTE] euros.

A.6.- Cargas y situación posesoria: libre de cargas y gravámenes y sin arrendatarios u otros ocupantes.

B) Requisitos para tomar parte en la subasta

B.1.- Los solicitantes del expediente podrán participar sin necesidad de consignar previamente cantidad alguna.

B.2.- Los interesados distintos de los solicitantes deberán consignar previamente el 5% del tipo del avalúo ( euros) para poder participar en la subasta. La consignación se realizará por medios electrónicos a través del Portal de Subastas, que utilizará los servicios telemáticos que la Agencia Estatal de la Administración Tributaria pondrá a su disposición, quien a su vez recibirá los ingresos a través de sus entidades colaboradoras.

B.3.- Los interesados deberán estar dados de alta como usuarios del sistema, accediendo al mismo mediante mecanismos seguros de identificación y firma electrónicos de acuerdo con lo previsto en la Ley 6/2020, de 11 de noviembre, reguladora de determinados aspectos de los servicios electrónicos de confianza.

B.4.- Los interesados pueden visitar la finca antes o después de realizar la consignación, para lo cual deberán ponerse en contacto con Don/Doña [NOMBRE Y APELLIDOS] en el teléfono [TELÉFONO], con una antelación mínima de cinco días al de la fecha de cierre de la subasta.

B.5.- Solamente los solicitantes podrán realizarse posturas con la facultad de ceder el remate a un tercero.

C) Forma de celebración de la subasta

C.1.- La subasta se celebrará electrónicamente a través del Portal de Subastas del BOE.

C.2.- La subasta se abrirá transcurridas veinticuatro horas desde la publicación del anuncio en el BOE, cuando haya sido remitida al Portal de Subastas la información necesaria para el comienzo de la misma.

C.3.- Una vez abierta la subasta las pujas serán exclusivamente electrónicas.

C.4.- Se admitirán posturas durante un plazo de veinte días naturales desde su apertura. La subasta se cerrará transcurrida una hora desde la realización de la última postura, aunque ello conlleve la ampliación del plazo inicial de veinte días por un máximo de 24 horas.

C.5.- Las posturas no podrán ser inferiores al 70% del tipo de licitación. El postor deberá indicar si consiente o no la reserva a que se refiere el art. 652.1 párrafo 2.º LEC y si puja en nombre propio o en nombre de un tercero. Serán admisibles posturas por importe superior, igual o inferior a la más alta ya realizada, entendiéndose en los dos últimos casos que consienten desde ese momento la reserva de consignación y serán tenidas en cuenta para el supuesto de que el licitador que haya realizado la puja igual o más alta no consigne finalmente el resto del precio de adquisición. En el caso de que existan posturas por el mismo importe, se preferirá la anterior en el tiempo. El portal de subastas sólo publicará la puja más alta entre las realizadas hasta ese momento.

D) Aprobación del remate

D.1.- Se aprobará el remate a favor de la mejor postura económica.

D.2.- El rematante habrá de consignar en la Cuenta de Depósitos y Consignaciones el importe de dicha postura, menos el del depósito, en el plazo de 40 días hábiles a contar desde la resolución judicial que apruebe el remate.

D.3.- Si alguno de los solicitantes del expediente resultare adjudicataria sólo habrá de consignar la cantidad resultante de excluir su parte proporcional de copropiedad del precio del remate.

D.4.- Cerrada la subasta, si la mejor postura no cubriera el 100% del tipo de licitación, los solicitantes se reservan expresamente el derecho a aprobarla en el plazo de tres días desde la comunicación del cierre de la subasta.

D.5.- La devolución de las consignaciones hechas para tomar parte en la subasta por personas que no hayan resultado adjudicatarias, no se efectuará hasta que no se haya abonado el total del precio de la adjudicación si así se hubiera solicitado por parte de los postores. Si el adjudicatario incumpliere su obligación de entrega de la diferencia del precio entre lo consignado y lo efectivamente rematado, la adjudicación se realizará al segundo o sucesivo mejor postor que hubiera solicitado la reserva de su consignación, perdiendo las consignaciones los incumplidores.

========================================================================
