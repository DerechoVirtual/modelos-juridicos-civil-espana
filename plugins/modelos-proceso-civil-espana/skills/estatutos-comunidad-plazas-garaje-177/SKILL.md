---
name: estatutos-comunidad-plazas-garaje-177
description: "Redacta el escrito «Estatutos de la comunidad de plazas de garaje» (formulario 177 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Estatutos de la comunidad de plazas de garaje

> Formulario 0177 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] NÚMERO
- [ ] LOCALIDAD
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de la c/ de»; «…forma parte de la Comunidad del edificio»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 396 del Código Civil
- Ley 5/2006

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

### Formulario 0177 · Estatutos de la comunidad de plazas de garaje

- Año del modelo: 2021
- Revisión 17-11-2026: 4 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Estatutos de comunidad de propietarios de plazas de garaje

Formulario adaptado a la reforma de la LO 1/2025.

Estatutos de comunidad de propietarios de garaje del edificio sito en el número [NÚMERO] de la c/ de [COMPLETAR]

DISPOSICIÓN GENERAL

Los presentes estatutos tienen por objeto regular el régimen de uso, disfrute, funcionamiento, adopción de acuerdos y mantenimiento de la comunidad de usuarios del garaje sito en

El local objeto del presente régimen especial, forma parte de la Comunidad del edificio [COMPLETAR], en la proporción reconocida en la escritura de constitución de la propiedad horizontal, y se subdivide en plazas de garaje susceptibles de aprovechamiento independiente, que tienen asignada una cuota o coeficiente de participación, en proporción a su superficie, cuyo porcentaje se recoge en el título de constitución y que servirá de modulo para derechos y obligaciones.

TÍTULO I.-CONFIGURACIÓN OBJETIVA DE LA PROPIEDAD

Artículo 1.- Se consideran elementos comunes privativos del presente condominio:

a) los mencionados en el art. 396 del Código Civil.
b) las paredes interiores y elementos de cualquier clase del interior del local, destinadas al uso común y general.
c) las servidumbres establecidas y que se constituyan en el título de constitución.

Artículo 2.- Corresponde a cada uno de los titulares de las distintas plazas:

a) el derecho exclusivo de uso y disfrute en pleno dominio o en arrendamiento del espacio delimitado y numerado, susceptible de aprovechamiento independiente, pudiendo utilizar los demás servicios en la forma y condiciones que se indican en los artículos siguientes.

b) el uso y en su caso el dominio, en copropiedad con el resto de titulares, de las rampas y espacios de circulación, entrada y salida y maniobra, con todos los elementos comunes de disfrute y aprovechamiento general dentro del local subdividido.

Artículo 3.- Las distintas plazas de garaje podrán pertenecer a varios titulares. En caso de cotitularidad de una plaza de garaje, se designará un representante por cada una de las plazas para el ejercicio de sus derechos y todos los propietarios responderán solidariamente de sus obligaciones para con la comunidad. En caso de usufructo, la asistencia y voto en Junta corresponderá al nudo propietario.

TÍTULO II.- NORMAS DE USO GENERAL

Artículo 4.- Dada la finalidad esencial con que se ha construido el aparcamiento, el uso y disfrute de la misma se sujetará a las siguientes condiciones:

a) Cada plaza de garaje se dedicará a estacionamiento de vehículos automóviles del gálibo máximo autorizado (coches, motos, furgonetas, etc.) prohibiéndose destinarla a cualquier otro fin.
b) La plaza de garaje no podrá modificarse dividiéndola en dos o más agregándola a otra formar una plaza nueva.
c) Sobre la plaza de garaje no podrán realizarse obras que modifiquen su configuración, distribución, sus instalaciones o servicios.

Artículo 5.- Son obligaciones de los propietarios como, en su caso, de los usuarios:

a) Usar del aparcamiento y de la plaza adjudicada de modo que no perjudique los derechos de los demás usuarios.
b) Sufragar los gastos a cargo de la comunidad en proporción a su cuota o coeficiente de participación.

Artículo 6.- Son gastos a cargo de la comunidad:

1.- Los de limpieza, mantenimiento, funcionamiento, reparación de las instalaciones y administración del estacionamiento.
2.- Los del personal empleado por la comunidad.
3.- Los pagos por obligaciones fiscales que recaigan sobre el uso de la plaza de aparcamiento y otros que, en su caso, fueran procedentes, que se devenguen desde que se constituya la comunidad.
4.- Los gastos por primas de seguros que se hayan concertado, que en todo caso incluirá las pólizas de seguro.
5.- Cualquier otro que se acuerde por la comunidad.

Artículo 7. Los titulares, por el título que sea, podrán hacer uso de los elementos comunes privativos del local subdividido, conforme al destino de los mismos, y siempre que no restrinjan los derechos de los demás titulares, y serán responsables de los daños causados en las cosas comunes o en la propiedad de otros titulares, cuando estos se hubieran causado por negligencia, dolo, omisión, o bien las que provengan de actos realizados por los usuarios de sus plazas, empleados o familiares.

Artículo 8. Podrá asignarse al conserje o vigilante, dentro del local subdividido, un cuarto o vivienda. En este caso, la comunidad se reservará para sí el dominio del mismo.

Artículo 9. La duración de la comunidad será indefinida, y sólo podrá ser disuelta en los casos previstos en la vigente legislación sobre propiedad horizontal.

Artículo 10. Solo podrán utilizar las plazas de garaje los titulares y los arrendatarios de los mismos, dedicándolos única y exclusivamente a aparcamiento de vehículos automóviles, prohibiéndose destinarla a cualquier otro fin.

No obstante, con autorización del titular, podrá admitirse el uso y utilización de las plazas de garaje, por empleados y/o familiares del mismo, con carácter temporal y/o permanente.

Artículo 11. No se podrán realizar ni en las plazas de garaje ni en las zonas comunes, obras de cualquier clase, ya sean temporales o fijas.

Artículo 12. Los propietarios deberán utilizar las zonas de maniobra, paso y circulación conforme a su destino específico, sin que se pueda estacionar en ellas, ni impedir en cualquier forma, su utilización por cualquier otro titular.

Artículo 13. No se podrán instalar en las plazas de garaje, en tanto están destinadas a aparcamiento, máquinas, motores, útiles o enseres de cualquier clase, ni utilizarlas como almacén o depósito.

Artículo 14. Los titulares de las plazas de aparcamiento, vendrán obligados a aparcar sus vehículos dentro de los límites señalados de cada plaza, quedando terminantemente prohibido el aparcamiento en pasillos, vías de acceso, rampas o espacios no destinados especialmente al aparcamiento.

Artículo 15. Las plazas de garaje serán abiertas, no pudiendo cerrar, tapiar ni delimitar su respectiva plaza con elemento alguno, fijo o móvil. La única delimitación será la que se presenta en las rayas pintadas en el suelo.

Artículo 16. La comunidad no será en ningún caso responsable de los objetos depositados en el interior de los vehículos aparcados.

Artículo 17. El conserje o vigilante se considerará como personal del servicio de la comunidad, por lo que ningún titular podrá utilizarlo para su servicio exclusivo.

Artículo 18. Los titulares vienen obligados a cumplir las normas y disposiciones, que además de las previstas en el presente reglamento se acuerden en Junta General.

Artículo 19. Las posibles quejas que tenga cualquier titular contra la comunidad o contra cualquier otro titular o usuario, por infracciones al presente reglamento, habrán de presentarse por escrito a la Administración, que queda facultada para resolver dichas quejas o para someter las mismas a la consideración de la junta general para su resolución.

En caso de no alcanzarse un acuerdo se dirimirán ante los Tribunales competentes o mediante arbitraje

TÍTULO III.- DISTRIBUCION DE CARGAS Y GASTOS

Artículo 20. Los titulares de plazas de garaje o cuartos trasteros, vendrán obligados a contribuir a los gastos del condominio. Para la distribución de dichos gastos se atenderá a las cuotas de participación atribuidas a cada plaza o trastero.

Artículo 21. Los gastos existentes serán los siguientes:

a) Los derivados de la participación atribuida a la totalidad del local subdividido en la Comunidad de vecinos del Inmueble, en la proporción conjunta establecida. Los gastos de conservación, utilización y reparación de la rampa de garaje, serán satisfechos por los propietarios de las plazas en la proporción que corresponda.
b) Los ordinarios que deriven de elementos comunes específicamente atribuidos a este condominio y causados por los servicios de mantenimiento del uso general y utilidad común.
c) Los extraordinarios que se produzcan por obras o reparaciones de carácter general y que hayan sido acordados por la Junta General.

Artículo 22. Para el pago que corresponda a cada titular se establecerá una cuota anual en Junta General, la cual será pagadera por trimestres adelantados y quedará a resultas de la liquidación definitiva que se establecerá también anualmente. La efectividad de los pagos a efectuar por los titulares, quedará sujeto a la vigente Ley de Propiedad Horizontal.

TÍTULO IV.- GOBIERNO Y ADMINISTRACIÓN

Artículo 23.- El gobierno y la administración de la comunidad estarán encomendados a los siguientes órganos:

a) La junta.
b) El presidente.
c) La comisión de gobierno.
d) El secretario-administrador.

Para desempeñar el cargo de secretario-administrador no será necesario ser propietario de una plaza de garaje.

Artículo 24.- El presidente de la comunidad, y por su delegación expresa, el administrador, serán los únicos facultados para:

a) Contratar y despedir el personal necesario para el servicio del aparcamiento.
b) Pagar por cuenta de quien corresponda, los tributos, vados, cánones, tasas y demás gastos del aparcamiento, así como los de limpieza, conservación, funcionamiento u mantenimiento.
c) Suscribir contratos de seguros y suministros para los servicios comunes.
d) En general, hacer todo lo necesario o útil para el buen funcionamiento del aparcamiento, disponiendo los gastos pertinentes siempre que, de no hallarse autorizados por la junta de usuarios, no sobrepasen del 20 % del presupuesto anual.

Artículo 25.- Con el fin de que puedan ser atendidas las obligaciones y los gastos de mantenimiento, el presidente y administrador establecerán anualmente un presupuesto estimativo de los gastos, pagando los cesionarios, por trimestres adelantados y a título de provisión, la cantidad que, según su cuota o coeficiente, les corresponda.

Artículo 26.- El administrador llevará las cuentas del aparcamiento, que deberá presentarlas anualmente a la junta y a la comisión de gobierno, cuantas veces le sean solicitadas.

Artículo 27.- La junta se reunirá al menos una vez cada año para la elección del presidente, de los miembros de la junta de gobierno y del secretario-administrador, así como para la aprobación del presupuesto anual y de las cuentas del aparcamiento.

Asimismo, la junta podrá reunirse también por decisión del presidente o de la junta de gobierno, o cuando lo soliciten al menos un tercio del total de los usuarios para conocer, tratar y decidir sobre asuntos de relevante importancia para la comunidad.

Artículo 28.- La comisión de gobierno estará formada por el presidente, tres vocales, y el secretario-administrador elegidos de entre los propietarios de plazas de aparcamientos. En el caso de que el secretario-administrador no tenga la condición de propietario, tendrá derecho a voz pero no a voto.

La comisión de gobierno colaborará con el presidente en la ejecución de las funciones que le correspondan y le asesorará en cuantas cuestiones someta a su consideración.

La comisión de gobierno deberá reunirse al menos cada dos meses, así como cuantas veces la convoque el presidente, y podrá decidir con respecto a todos aquellos asuntos que afecten a la administración de los intereses de la comunidad y a la ejecución de acuerdos adoptados por la junta y a la ejecución de acuerdos adoptados por la junta.

Artículo 29.- Los acuerdos que hayan de tomarse por la junta y por la comisión de gobierno se adoptarán siempre por mayoría de los asistentes a la reunión, decidiendo, en caso de empate, el presidente, con voto de calidad. De las reuniones que se celebren, el secretario-administrador levantará la oportuna acta.

Artículo 30.- Todo usuario quedará sometido a la jurisdicción de los Tribunales de [LOCALIDAD] para cuantas incidencias puedan derivarse del incumplimiento de estos estatutos.

Artículo 31.- La modificación de los presentes estatutos deberá ser aprobada por la Junta, realizada a propuesta de los propietarios, previo acuerdo de la misma adoptado por unanimidad.

Artículo 32.- Los propietarios como, en su caso, todos los usuarios del referido aparcamiento quedan sujetos a lo dispuesto en los presentes estatutos.

Artículo 33.- En todo lo no previsto en los presentes estatutos, que afecta a todos los titulares presentes y futuros, y comenzará a regir a partir de la fecha de adquisición de sus derechos por cada titular, se estará a lo previsto en la Ley de Propiedad Horizontal (Régimen común)/Ley 5/2006, de 10 de mayo, del libro quinto del Código civil de Cataluña, relativo a los derechos reales (Cataluña), en lo que le sea aplicable por analogía.
