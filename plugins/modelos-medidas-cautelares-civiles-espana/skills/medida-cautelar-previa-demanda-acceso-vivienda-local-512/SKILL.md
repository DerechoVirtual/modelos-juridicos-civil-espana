---
name: medida-cautelar-previa-demanda-acceso-vivienda-local-512
description: "Redacta el escrito «Medida cautelar previa a la demanda: acceso a vivienda o local» (formulario 512 de medidas cautelares y diligencias preliminares, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Medida cautelar previa a la demanda: acceso a vivienda o local

> Formulario 0512 del plugin **Medidas cautelares y diligencias preliminares** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] COLEGIO (2 veces)
- [ ] LOCALIDAD
- [ ] CALLE (2 veces)
- [ ] NÚMERO (4 veces)
- [ ] FECHA (4 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] art. 727.11.ª LEC en relación a art. 9.1.d) LPH
- [ ] IMPORTE (2 veces)
- [ ] LUGAR
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…l piso sito en el mismo edificio, planta»; «…letra»; «…do. Se acompañan como documentos números»; «…,»; «…, [COMPLETAR] y»; «…que se acompañan como documentos números»; «…a»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 730 LEC
- art. 723.1 LEC
- arts. 85.1 LOPJ
- art. 730.2 LEC
- art. 733.2 LEC
- art. 9.1.d) LPH
- art. 728.3 LEC
- art. 732.2 LEC
- art. 732 LEC
- art. 730.1 y 2 LEC
- art. 32 LEC

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

### Formulario 0512 · Medida cautelar previa a la demanda: acceso a vivienda o local

- Año del modelo: 2016
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (2); 32 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Solicitud de medida cautelar de acceso a vivienda o local para la realización de obras en régimen de propiedad horizontal, sin audiencia del demandado.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, que actúa en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito con la copia de poder que acepto y se acompaña, dirigido por el Letrado D./Dña. [NOMBRE Y APELLIDOS], abogado ejerciente del Ilustre Colegio de [COLEGIO], con despacho abierto en [LOCALIDAD], calle [CALLE], ante el Tribunal comparezco y como mejor proceda en Derecho (1), DIGO:

Que por medio del presente escrito y al amparo de lo dispuesto en el art. 730 LEC, interpongo demanda en solicitud de la adopción de medidas cautelares previas a la interposición de demanda principal de entrada en domicilio, frente a D./Dña. [NOMBRE Y APELLIDOS], sirviendo de base a la presente demanda los siguientes:

HECHOS

PRIMERO

Mi mandante es Presidente de la Comunidad de Propietarios del edificio señalado con el n.º [NÚMERO], de la calle [CALLE], según consta en el acta de la Junta de Propietarios que se acompaña como documento n.º [NÚMERO].

SEGUNDO

El demandado es a su vez propietario del piso sito en el mismo edificio, planta [COMPLETAR] letra [COMPLETAR], cuyas demás circunstancias descriptivas constan en la certificación del Registro de la Propiedad correspondiente a la finca, que se acompaña como documento n.º [NÚMERO].

TERCERO

La Comunidad de Propietarios que represento, adoptó en la Junta celebrada el día [FECHA], el acuerdo de proceder a la instalación de un ascensor en el inmueble de referencia al objeto de suprimir las barreras arquitectónicas y facilitar el acceso a sus pisos a los distintos propietarios, siendo notificada el acta de la Junta de propietarios al demandado en fecha [FECHA], dada su inasistencia a la misma, sin que hasta el día de la fecha el mismo haya instado acción de nulidad del acuerdo adoptado.

Se acompaña copia del acta, como documento n.º [NÚMERO].

CUARTO

El ascensor y servicios inherentes al mismo se han de instalar en el patio de luces interior de la comunidad, a cuyo efecto, D./Dña. [NOMBRE Y APELLIDOS] ha de permitir a los operarios de la empresa instaladora el acceso a la azotea del inmueble a través de la terraza de uso privativo que tiene en la parte superior de su piso, al ser la única vía de acceso, al objeto de poder instalarse las conducciones necesarias para el funcionamiento del ascensor, así como ejecutar las obras necesarias para su encaje en el referido lugar.

Se acompaña dictamen pericial del arquitecto técnico D./Dña. [NOMBRE Y APELLIDOS], como documento número [Nº DE DOCUMENTO].

QUINTO

El demandado, se ha negado reiteradamente a facilitar el acceso a los operarios de la entidad comisionada por mi mandante para el desarrollo de las obras mencionadas, pese a que se le ha advertido con antelación suficiente y de forma fehaciente las fechas en las que estaba prevista la realización de las referidas obras de instalación del ascensor, impidiendo con ello la correcta ejecución y desarrollo del mismo, ya que el único lugar por donde puede accederse a la azotea donde está proyectada la instalación de los motores y servicios de cableado general del ascensor es a través de la terraza superior del piso del demandado.

Se acompañan como documentos números [COMPLETAR], [COMPLETAR] y [COMPLETAR] los tres requerimientos realizados.

SEXTO

Concurre la urgencia y necesidad de la ejecución del acuerdo por la existencia de comuneros con discapacidad que precisan del ascensor para acceder a sus inmuebles, y exigen el inicio de las obras, como acreditan las correspondientes peticiones y certificados de discapacidad de cada uno de los peticionarios que se acompañan como documentos números [COMPLETAR] a [COMPLETAR].

SÉPTIMO

Por otro lado, además de impedir la ejecución de un acuerdo comunitario al que no se ha opuesto legalmente, la actitud del demandado de impedir de facto la ejecución del mismo, va a provocar que expire el plazo convenido en el presupuesto acordado por mi mandante con la empresa para la realización de las obras de instalación del ascensor, ya que la misma, a la vista de las dificultades existentes con el demandado, no mantendrá el precio del presupuesto suscrito entre las partes más allá del próximo día [FECHA].

Se acompaña presupuesto suscrito con la empresa instaladora como documento número [Nº DE DOCUMENTO].

OCTAVO.- Las circunstancias descritas son, a juicio de esta parte, suficientemente reveladoras de la necesidad y urgencia de solicitar la medida de entrada en el domicilio de D./Dña. [NOMBRE Y APELLIDOS], habida cuenta que resulta imprescindible para el inicio de las obras, con carácter previo a la interposición de la demanda y que se proceda a acordar la misma sin audiencia previa del demandado, para asegurar la efectividad de la sentencia que pudiera recaer, ofreciendo, prestar caución en la cuantía y forma que más adelante se dirá, sin perjuicio de atender a lo que, en tal sentido, se fije por el órgano jurisdiccional a que me dirijo.

A los hechos anteriores son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA

Con arreglo al art. 723.1 LEC, competente objetivamente el Juez de Primera Instancia, conforme a los arts. 85.1 LOPJ y 45 LEC, lo es territorialmente el que nos dirigimos, puesto que es ante el que habrá de presentarse la demanda de juicio ordinario del art. 249.1.8.º LEC, es decir, el del lugar en el que radica la finca, conforme al art. 52.1.8.º LEC.

II.- PROCEDIMIENTO

Art. 730 y ss. LEC, y especialmente el art. 730.2 LEC, que regula la posibilidad de solicitarse medidas cautelares antes de la presentación de la demanda, y en cuanto a la tramitación, se solicita que se sustancie sin la previa audiencia del adverso, conforme al art. 733.2 LEC, habida cuenta haber alegado y acreditado razones de urgencia y necesidad que comprometen el buen fin de la medida cautelar si se produce tal contradicción simultánea y la demora en resolver, que la convocatoria a vista aceleraría sin remedio.

III.- LEGITIMACIÓN

La activa corresponde a la actora en virtud de lo dispuesto en el art. 721.1 en relación con el 730.2, ambos de la LEC, pues es persona que interpondrá demanda dentro del plazo legal de veinte días, solicitando con anterioridad la medida cautelar por razones de urgencia y necesidad. La pasiva a la parte demandada por su condición de futuro demandado.

IV.- POSTULACIÓN

El actor está representado por el Procurador que suscribe, habilitado para ejercer en el territorio del Tribunal al que nos dirigimos, y asimismo asistido del Letrado del Ilustre Colegio de Abogados de [COLEGIO] (2).

V.- MEDIDA SOLICITADA

Se solicita medida cautelar consistente en la entrada al domicilio del demandado para iniciar las obras de instalación de ascensor [art. 727.11.ª LEC en relación a art. 9.1.d) LPH], ya que el demandado se niega y no existe constancia en la comunidad de acuerdo de un juez civil de suspensión del acuerdo adoptado por la Junta, por lo que el perjuicio para la comunidad es notable, como se ha razonado.

VI.- CAUCIÓN

Presupuesto de la ejecución de la medida cautelar (art. 728.3 LEC), se ofrece prestar caución, para responder de los daños y perjuicios que la adopción de la medida pudiera causar, en cuantía justificada de [IMPORTE] euros, que se estima procedente atendiendo a la importancia real de la pretensión que se quiere asegurar, al fundamento del derecho reclamado, y a la efectividad y cuantía de los posibles daños y perjuicios derivados de la ejecución de la medida, que se reputan mínimos.

En su virtud,

SUPLICO AL TRIBUNAL

que, teniendo por recibida la presente solicitud de medida cautelar, se digne admitirla y, sin audiencia previa de la parte contraria, a la mayor brevedad dicte Auto por el que se acuerde la entrada en la vivienda del demandado para el inicio de la obra de instalación de ascensor, bajo condición de prestarse caución por cuantía de [IMPORTE] euros, o la que prudencialmente fije S.S.ª.

OTROSÍ PRIMERO DIGO: Que siendo el poder general para pleitos y necesitándolo para otros usos,

SUPLICO AL TRIBUNAL Que una vez tomada nota en autos, sea desglosado y devuelto a esta parte.

OTROSÍ SEGUNDO DIGO: Que de conformidad con lo dispuesto en el art. 732.2 LEC, esta parte propone como prueba, a fin de justificar la procedencia en la adopción de la medida cautelar interesada inaudita parte, los documentos acompañados junto con este escrito.

SUPLICO AL TRIBUNAL Que tenga por hecha la anterior manifestación teniendo por propuesta en su caso la prueba que acredita los presupuestos que autorizan la adopción de la medida cautelar interesada, de conformidad con lo dispuesto en el art. 732 LEC.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

NOTAS DEL FORMULARIO

(1) El art. 9.1.d) LPH determina que es obligación de cada propietario "Permitir la entrada en su piso o local a los efectos prevenidos en los tres apartados anteriores" y, al efecto, el apartado c) del mismo artículo dispone la obligación del propietario de "Consentir en su vivienda o local las reparaciones que exija el servicio del inmueble y permitir en él las servidumbres imprescindibles requeridas para la realización de obras, actuaciones o la creación de servicios comunes llevadas a cabo o acordadas conforme a lo establecido en la presente Ley, teniendo derecho a que la comunidad le resarza de los daños y perjuicios ocasionados".

Esta obligación sólo es exigible si realmente es el único modo de poder realizar la obra y si el propietario se niega.

Si la obra es tan urgente que no se puede esperar a la tramitación de una cautelar civil (escapes, peligro para el edificio o terceros...) puede acudirse al Tribunal de Instancia en funciones de guardia para que autorice la entrada forzosa.

Si se piden medidas cautelares ante el Juez de Primera Instancia, se solicitarán, de ordinario, junto con la demanda principal —normalmente por otrosí—; pero podrán también solicitarse medidas cautelares antes de la demanda —como en el caso que contempla el formulario— si quien en ese momento las pide alega y acredita razones de urgencia o necesidad. En este caso, las medidas que se hubieran acordado quedarán sin efecto si la demanda no se presentare ante el mismo Tribunal que conoció de la solicitud de aquéllas en los veinte días siguientes a su adopción (art. 730.1 y 2 LEC).

(2) En cuanto a la debida postulación, si la medida cautelar se solicita antes de la demanda, y necesariamente entonces será urgente, no es preceptiva la representación mediante Procurador de los tribunales, ni la dirección letrada —arts. 23.2.3.º y 31.2.2.º LEC—, aunque si se utiliza, debe enterarse al objeto de poner en marcha el dispositivo de igualdad procesal del art. 32 LEC.

========================================================================
