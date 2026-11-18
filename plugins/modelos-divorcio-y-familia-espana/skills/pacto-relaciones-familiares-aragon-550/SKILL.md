---
name: pacto-relaciones-familiares-aragon-550
description: "Redacta el escrito «Pacto de relaciones familiares (Aragón)» (formulario 550 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pacto de relaciones familiares (Aragón)

> Formulario 0550 del plugin **Familia** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.

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

- [ ] NÚMERO (3 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] CALLE
- [ ] IMPORTE (2 veces)
- [ ] FECHA
- [ ] Otros 16 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…n cada uno de sus hijos. En la ciudad de»; «…, a»; «…REUNIDOS DE UNA PARTE, D.»; «…los hijos habidos durante el matrimonio:»; «…, nacido el»; «…, nacido el [COMPLETAR]; y»; «…; y [COMPLETAR], nacido el»; «…,»; «…,»; «…. Los abuelos recogerán a los menores»; «…y los entregarán en»; «…cotitulares de forma indistinta: entidad»; …

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

### Formulario 0550 · Pacto de relaciones familiares (Aragón)

- Año del modelo: 2012
- Revisión 17-11-2026: 29 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Pacto de relaciones familiares conforme a Derecho civil especial de Aragón que regula las relaciones familiares en el futuro, así como la interacción entre ambos cónyuges y la de éstos con cada uno de sus hijos.

En la ciudad de [COMPLETAR], a [COMPLETAR]

REUNIDOS

DE UNA PARTE,

D. [COMPLETAR], mayor de edad, con Documento Nacional de Identidad número [NÚMERO] y domicilio en [LOCALIDAD].

Y DE OTRA,

Dña. [NOMBRE Y APELLIDOS], mayor de edad, con Documento Nacional de Identidad número [NÚMERO] y domicilio en [LOCALIDAD].

Ambas partes intervienen en su propio nombre e interés y se reconocen mutuamente la capacidad necesaria en derecho para obligarse y otorgar el presente pacto de relaciones familiares, y suscribir el documento que lo contiene, conforme al artículo 77 del Código del Derecho Foral de Aragón, lo que de común acuerdo efectúan con arreglo a los siguientes:

ACUERDOS

COMPROMISO GENERAL PRELIMINAR

Las partes se comprometen a no interferirse uno en la vida del otro y a respetarse mutuamente, y otorgan el presente pacto para regular sus relaciones familiares tras la ruptura de su convivencia, fijando los términos de sus nuevas relaciones con los hijos habidos durante el matrimonio: [COMPLETAR], nacido el [COMPLETAR]; y [COMPLETAR], nacido el [COMPLETAR].

PRIMERO. PATRIA POTESTAD Y GUARDA Y CUSTODIA DE LOS HIJOS

Los hijos menores de edad habidos del matrimonio,

-
+
Añadir más párrafos iguales

quedan sometidos a la patria potestad conjunta de ambos progenitores. Asimismo, la guarda y custodia de los hijos menores de los comparecientes será ejercida de forma compartida por ambos progenitores.

A tales efectos, las partes acuerdan que los hijos residirán en el domicilio familiar, cuyo uso se atribuye a la madre, durante los meses de enero, marzo, mayo, julio, septiembre y noviembre. Los comparecientes acuerdan asimismo que, durante los meses de febrero, abril, junio, agosto, octubre y diciembre, los menores se trasladarán a residir al domicilio del padre, sito en la Calle [CALLE].

SEGUNDO. DEL RÉGIMEN DE RELACIÓN DE LOS HIJOS CON SUS ABUELOS PATERNOS Y MATERNOS

Los hijos de los comparecientes estarán con sus abuelos paternos, D. y Dña. [NOMBRE Y APELLIDOS], [COMPLETAR]. Los menores pasarán con sus abuelos maternos, D. y Dña. [NOMBRE Y APELLIDOS], [COMPLETAR]. Los abuelos recogerán a los menores [COMPLETAR] y los entregarán en [COMPLETAR] en el mes que corresponda.

TERCERO. DEL USO DE LA VIVIENDA Y AJUAR FAMILIAR

El uso de la vivienda que ha venido constituyendo el domicilio familiar, sita en [LOCALIDAD], con su ajuar familiar, se atribuye a la esposa, hasta que todos los hijos sean económicamente independientes y dejen de residir con sus progenitores. También se extinguirá el uso en el caso de convivir maritalmente con otra persona.

D. podrá retirar de dicho domicilio sus objetos personales.

El préstamo hipotecario que grava el piso, el Impuesto sobre Bienes Inmuebles y el seguro de la vivienda se abonarán al 50%, así como las cuotas ordinarias de la Comunidad de Propietarios. Las cuotas extraordinarias serán de cuenta exclusiva de Dña. [NOMBRE Y APELLIDOS]

Se calculará el monto anual de todo ello y cada mes. D. ingresará en la cuenta que indique Dña. la doceava parte de dicho importe, siendo ella la que se ocupe del pago efectivo, compensándose a final de año los excesos o defectos de la cantidad ingresada respecto del costo real.

CUARTO. DE LA CONTRIBUCIÓN A LOS ALIMENTOS DE LOS HIJOS

Ambos progenitores contribuirán a satisfacer los gastos ordinarios de asistencia de los hijos a su cargo, de manera proporcional con sus recursos económicos. Tendrán carácter ordinario

A tales efectos, los comparecientes acuerdan que la esposa contribuirá a estos gastos ordinarios en la cantidad de [IMPORTE] euros mensuales y el esposo en la cantidad de [IMPORTE] euros mensuales. Las referidas cantidades serán ingresadas por meses anticipados, dentro de los cinco primeros días de cada mes, en la cuenta corriente designada por los comparecientes, de la que ambos son cotitulares de forma indistinta: entidad [COMPLETAR] número de cuenta

Esta contribución persistirá aun cuando los hijos adquieran la mayoría de edad, siempre y cuando carezcan de ingresos propios que les permita desarrollar una vida independiente de sus progenitores y vivan en el domicilio de la madre o del padre.

La reseñada contribución que debe realizar cada progenitor se actualizará anualmente en el mes de enero de acuerdo con los incrementos que experimente el Índice de Precios al Consumo que publica el Instituto Nacional de Estadística correspondiente al año inmediatamente anterior. La actualización se efectuará sobre la pensión base más las actualizaciones que sobre la misma se vayan produciendo anualmente.

Se considerarán gastos extraordinarios [COMPLETAR].

Los comparecientes acuerdan que los gastos extraordinarios no necesarios se abonarán en función de los acuerdos a los que lleguen los progenitores y, en defecto de acuerdo, los abonará el progenitor que haya decidido la realización del gasto.

QUINTO. DE LA LIQUIDACIÓN DEL RÉGIMEN ECONÓMICO DEL MATRIMONIO

El matrimonio se celebró habiendo otorgado con anterioridad escritura de capitulaciones matrimoniales ante el Notario de [COMPLETAR], D. [COMPLETAR], en fecha [FECHA], número [NÚMERO] de su protocolo, en las que se estipula el régimen de separación de bienes, sin que posteriormente haya sido objeto de modificación.

El piso que es la vivienda familiar había sido adquirido por mitades indivisas en estado de solteros. Tras el matrimonio y con dinero propiedad por iguales de ambos cónyuges se han adquirido [COMPLETAR], que seguirán perteneciendo a los cónyuges por iguales partes.

SEXTO. DE LA ASIGNACIÓN FAMILIAR COMPENSATORIA

Ambos cónyuges manifiestan que no se dan las circunstancias para que exista asignación familiar compensatoria a favor de ninguno de ellos.

Firma de D.	Firma de Dña. [NOMBRE Y APELLIDOS]

========================================================================
