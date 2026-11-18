---
name: regimen-interior-reglamento-1392
description: "Redacta el escrito «Régimen interior: reglamento» (formulario 1392 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Régimen interior: reglamento

> Formulario 1392 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] FECHA
- [ ] Nº
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…temporada de baño comprende los meses de»

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 1392 · Régimen interior: reglamento

- Año del modelo: 2013
- Revisión 17-11-2026: 3 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (FECHA)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En Junta General de la Comunidad de Propietarios de de fecha [FECHA] se ha procedido a aprobar las siguientes normas que configuran el Reglamento de Régimen Interior de dicha Comunidad y que están destinadas a regular el uso y disposición que cada comunero puede hacer de los elementos comunes, así como las obligaciones que han de asumirse respecto a su conservación y adecuado mantenimiento.

USO Y DISFRUTE DE ELEMENTOS COMUNES

Con carácter general, el uso de los elementos comunes descritos en el punto n.º [Nº] de los Estatutos de la Comunidad de Propietarios está restringido a los propietarios e inquilinos de las viviendas y quienes con ellos convivan.

Todas las personas que vivan en las viviendas o ejerzan comercio, negocio o industria en los locales de negocio que configuran esta Comunidad deben respetar y conservar los elementos comunes. Está prohibida la realización de actividades o juegos que puedan ocasionar el deterioro de éstos, tales como, fuera de las zonas expresamente destinadas al efecto.

 Está prohibida la circulación de vehículos y bicicletas fuera de las vías públicas así como en las zonas peatonales y ajardinadas.

Los residuos y basuras sólo podrán depositarse en los contenedores destinados al efecto y siempre después de las 21 horas.

Está prohibido el almacenamiento o depósito permanente de objetos particulares o enseres en las zonas comunes.

Los animales domésticos de los que sean propietarios los comuneros sólo podrán pasear o permanecer en las zonas comunes si están provistos de collar y correa y siempre sujetos por persona responsable. Queda terminantemente prohibido el uso de las zonas comunes como evacuatorio de esos animales.

 está facultado para hacer guardar las obligaciones recogidas en este Reglamento y expresamente se le autoriza a realizar actuaciones disciplinarias contra quienes las incumplan. Las sanciones que, en su caso, se impongan tras ser escuchado el presunto infractor, deberán ser acordadas en Junta de Propietarios.

No está permitido fumar en las zonas comunes salvo

VIVIENDAS, LOCALES Y GARAJES

No se podrán realizar actividades molestas, insalubres, nocivas o peligrosas dentro de las viviendas o de las parcelas privadas.

Todos los locales destinados a servicio, comercio o industria deberán contar con las licencias oportunas. El Presidente queda facultado para comprobar que se cumplen estos requisitos.

Los propietarios de plazas de garajes estacionarán su vehículo siempre y únicamente dentro de la zona que delimitada mediante rayas en el suelo define su espacio. No se permite cerrar las plazas de garaje ni destinarlas a otra finalidad que no sea la citada de estacionamiento de vehículos (Si la propiedad del garaje es compartida por todos los copropietarios habrá que fijar también la adscripción a cada titular de vivienda o local de una determinada plaza de garaje).

Tras los oportunos avisos de limpieza del garaje colocados en las zonas de costumbre, deberán sacarse todos los vehículos del garaje durante el tiempo que se señale, para facilitar las tareas de limpieza.

ZONAS DEPORTIVAS

Las pistas deportivas sólo podrán utilizarse para su finalidad específica y sólo se podrá acceder a ellas con calzado deportivo.

Su uso y disfrute está reservado a los propietarios, inquilinos o personas que con ellos convivan, que se encuentren en posesión de la correspondiente tarjeta deportiva, así como a los invitados de éstos, siempre que utilicen las instalaciones en compañía de un titular de la tarjeta deportiva. Está prohibido fumar en todas las instalaciones deportivas de la Comunidad.

Deberá contar el usuario, además, con el correspondiente resguardo de abono del importe de la cuota de utilización, que se conseguirá de la siguiente manera.

Las reservas se realizarán (a través de la página web de la Junta de Propietarios o acudiendo al personal encargado de este servicio en horario de a). Cada día se colocará en la zona destinada al efecto el horario de ocupación de cada pista.

Cuando no se encontrare ocupada alguna de las pistas podrá servirse de ella cualquiera de las personas con derecho a ello, si se paga por este servicio, poniéndolo en conocimiento en ese momento del personal encargado de ello o, si éste no estuviera presente, haciendo constar su nombre en la lista y abonando al día siguiente la cuota correspondiente.

El Presidente está facultado para negociar la realización de cursos de aprendizaje o perfeccionamiento de actividades deportivas que, en todo caso, deberán ser abonados por quienes a ellos se suscriban.

En caso de incumplimiento de estas obligaciones, el Presidente podrá proponer a la Junta de Propietarios que el infractor sea sancionado con el impedimento de uso de estas instalaciones por un plazo de hasta meses.

PISCINA

El uso de la piscina está reservado a los propietarios o arrendatarios de los inmuebles que configuran la Comunidad de Propietarios así como a las personas que con ellos convivan. Para acceder a ella es necesario estar en posesión de la tarjeta de baño que se emitirá anualmente por el personal encargado de este servicio.

A este servicio podrán acceder también invitados siempre con algún titular y previa adquisición de la entrada de invitado.

Los precios de este servicio serán los siguientes.

La temporada de baño comprende los meses de [COMPLETAR], decidiéndose anualmente por el Presidente los días de inicio y cese de la actividad en función de la climatología anual y de las labores de puesta en funcionamiento necesarias.

El horario de la piscina será de a y durante todo ese tiempo se prestará el servicio de socorrista. La Comunidad rechaza toda responsabilidad por cualquier accidente o perjuicio que se pueda producir como consecuencia del uso fuera de ese horario.

Como normas de uso generales se acuerdan las siguientes:

a) Al recinto de la piscina se accederá con calzado adecuado.

b) Antes de introducirse en el cubo de la piscina los usuarios deberán utilizar las duchas por condiciones generales de higiene. Es obligatorio el uso de gorro de baño.

c) No se permite el acceso a animales domésticos.

d) Están prohibidos los juegos que puedan molestar al resto de los usuarios así como el uso de colchonetas y balones cuando causen el mismo efecto.

e) Los niños menores de siete años y los que no sepan nadar estarán siempre acompañados de persona mayor responsable.

f) No se permite introducir comidas y bebidas en la zona de césped.

g) Está prohibido fumar en todo el espacio de la piscina y su zona de esparcimiento.

El Presidente está facultado para negociar la realización de cursos de aprendizaje o perfeccionamiento de natación que, en todo caso, deberán ser abonados por quienes a ellos se suscriban.

En caso de incumplimiento de estas obligaciones, el Presidente podrá proponer a la Junta de Propietarios que el infractor sea sancionado con el impedimento de uso de estas instalaciones por un plazo de hasta meses.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
