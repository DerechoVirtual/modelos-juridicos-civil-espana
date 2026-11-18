---
name: cuenta-participacion-construccion-edificio-venta-1179
description: "Redacta el escrito «Cuenta en participación en la construcción de edificio para la venta» (formulario 1179 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Cuenta en participación en la construcción de edificio para la venta

> Formulario 1179 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] FECHA (4 veces)
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] NOMBRE DEL NOTARIO
- [ ] NÚMERO (4 veces)
- [ ] Nº (3 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] C.P.
- [ ] ACTO O RESOLUCIÓN
- [ ] Nº DE EXPEDIENTE
- [ ] IMPORTE
- [ ] Otros 24 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, domiciliada en»; «…Notario de»; «…vigente mediante escritura autorizada en»; «…lla inscrita en el Registro Mercantil de»; «…, al»; «…, al [COMPLETAR]; su CIF es»; «…Notario de»; «…lla inscrita en el Registro Mercantil de»; «…Tiene una superficie de»; «…metros cuadrados. Linda: al frente, en»; «…metros lineales con»; «…, derecha entrando, en»; …

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

### Formulario 1179 · Cuenta en participación en la construcción de edificio para la venta

- Año del modelo: 2015
- Revisión 17-11-2026: 49 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [FECHA].

REUNIDOS

DE UNA PARTE D./Dña. [NOMBRE Y APELLIDOS]

Y DE OTRA D./Dña. [NOMBRE Y APELLIDOS]

INTERVIENEN

A) El primero en nombre y representación de la mercantil [NOMBRE DEL REPRESENTADO/A], domiciliada en [COMPLETAR], constituida por tiempo indefinido mediante escritura pública autorizada por D./Dña. [NOMBRE Y APELLIDOS] Notario de [COMPLETAR] en fecha [FECHA], (en su caso) habiendo sido adaptados sus estatutos a la normativa vigente mediante escritura autorizada en [COMPLETAR] el ante el Notario D./Dña. [NOMBRE DEL NOTARIO], con el número [NÚMERO] de los de su protocolo. La presente mercantil se halla inscrita en el Registro Mercantil de [COMPLETAR], al [COMPLETAR]; su CIF es [COMPLETAR], en lo sucesivo EL GESTOR.

Para el presente acto se encuentra facultado en virtud de su cargo de Secretario del Consejo de Administración, que asegura vigente, para el que fue designado por un plazo de [Nº] años por acuerdo de la Junta General de accionistas de la citada mercantil celebrada en fecha [FECHA], cuyos acuerdos fueron elevados a públicos en escritura otorgada ante D./Dña. [NOMBRE Y APELLIDOS] Notario de [COMPLETAR], el día [FECHA], escritura que cuenta con el número [NÚMERO] de las de su protocolo y se halla inscrita en el Registro Mercantil de [COMPLETAR], en el Tomo y Folios precedentemente señalados, inscripción

B) El segundo en su propio nombre y derecho, en lo sucesivo EL PARTÍCIPE.

Y reconociéndose mutuamente todos los comparecientes la capacidad necesaria para la firma del presente documento, a cuyo fin:

EXPONEN

I.- Que EL GESTOR es propietario del solar sito en [LOCALIDAD] C.P. [C.P.], con frente a la [ACTO O RESOLUCIÓN], donde le corresponde el número [NÚMERO]

Tiene una superficie de [COMPLETAR] metros cuadrados.

Linda: al frente, en [COMPLETAR] metros lineales con [COMPLETAR], derecha entrando, en [COMPLETAR] metros lineales con [COMPLETAR], fondo, en [COMPLETAR] metros lineales con [COMPLETAR] y con [COMPLETAR], a la izquierda en [COMPLETAR] metros lineales [COMPLETAR] con

Inscrito en el Registro de la Propiedad de [COMPLETAR], al [COMPLETAR],

Referencia catastral número [NÚMERO]

Sobre el solar que tiene la calificación urbanística de [COMPLETAR], se ha obtenido Licencia de Obras del Ayuntamiento de [LOCALIDAD], expediente número [Nº DE EXPEDIENTE] concedida el para construir un edificio de [COMPLETAR] plantas, habiendo redactado el proyecto el Arquitecto [COMPLETAR], todo ello de acuerdo con las Normas Urbanísticas en vigor en el municipio citado.

II.- Que EL PARTÍCIPE está interesado en contribuir económicamente en la ejecución del edificio a que se ha hecho referencia, destinado a la venta, intención ésta compartida por dicho GESTOR, haciéndose así partícipe de sus resultados prósperos o adversos en la proporción que se señala en el clausulado del presente contrato.

III.- Que por todo ello ambas partes acuerdan celebrar el presente contrato de CUENTAS EN PARTICIPACIÓN, que se regirá por las siguientes:

CLÁUSULAS

Primera.- Que las partes acuerdan celebrar, por el presente acto, un contrato de CUENTAS EN PARTICIPACIÓN que se regirá por lo previsto en el presente documento, y en su defecto, por las disposiciones contenidas en los artículos 239 y siguientes del Código de Comercio, así como por las restantes normas que resulten de aplicación.

Segunda.- El objeto del presente contrato lo constituye la participación en los resultados, prósperos o adversos, de la actividad desarrollada por el GESTOR mencionada en el Expositivo I que ambas partes declaran conocer.

Tercera.- A tal fin, EL PARTÍCIPE aporta al negocio del GESTOR [IMPORTE] euros, cantidad que entrega en el presente acto, y que EL GESTOR declara recibir.

Cuarta.- En mérito a la entrega referida en la cláusula Tercera, el PARTÍCIPE pasa a serlo en la proporción de un [COMPLETAR] % de los resultados prósperos o adversos del negocio al que se vincula el presente contrato que se generen durante la vigencia del mismo.

En todo caso, la cuantía máxima de las pérdidas imputables al PARTÍCIPE queda limitada a su aportación.

Quinta.- El GESTOR se compromete en su propio nombre y bajo su responsabilidad individual a construir el edificio mencionado en el plazo de [Nº] meses con las cantidades abonadas por EL PARTÍCIPE las cuales quedan estrictamente afectas a tal fin.

Sexta.- Concluida la venta se procederá al reparto de beneficios o a la reclamación de las pérdidas que haya ocasionado la operación, participando EL PARTÍCIPE en la proporción en que haya aportado los fondos.

Séptima.- El GESTOR rendirá cuentas justificadas de la marcha del negocio en el momento de la extinción del contrato. En aras a la comprobación de dichas rendiciones, el PARTÍCIPE podrá examinar, en el plazo de los [Nº] meses siguientes a la extinción del contrato la contabilidad del GESTOR, en el domicilio de éste.

Octava.- El GESTOR se compromete a la llevanza y dirección de su negocio según la diligencia de un ordenado empresario, comprometiéndose por su parte, el PARTÍCIPE, a no injerir en dicha labor.

Novena.- Serán causas de extinción del presente contrato las siguientes:

a) Voluntad conjunta de los contratantes en este sentido.
b) Incumplimiento de cualquiera de las condiciones estipuladas en el presente contrato.
c) Muerte o quiebra del GESTOR.
d) Imposibilidad de ejecución o conclusión del objeto para cuya realización se estipularon las cuentas en participación.
e) (Otras que quieran acordarse)

Y en prueba de conformidad, firman el presente por duplicado, uno para cada firmante.

EL GESTOR

EL PARTÍCIPE

Firmado: D./Dña. [NOMBRE Y APELLIDOS] 	Firmado: D./Dña. [NOMBRE Y APELLIDOS]

========================================================================
