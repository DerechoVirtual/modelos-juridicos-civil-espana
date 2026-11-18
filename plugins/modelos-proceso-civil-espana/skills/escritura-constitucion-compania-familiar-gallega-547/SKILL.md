---
name: escritura-constitucion-compania-familiar-gallega-547
description: "Redacta el escrito «Escritura de constitución de compañía familiar gallega» (formulario 547 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Escritura de constitución de compañía familiar gallega

> Formulario 0547 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] FECHA
- [ ] COLEGIO
- [ ] LOCALIDAD
- [ ] NIF
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] IMPORTE (3 veces)
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, con residencia en»; «…fesionales de la agricultura, vecinos de»; «…fesionales de la agricultura, vecinos de»; «…profesional de la agricultura, vecino de»; «…scrita en el Registro de la Propiedad de»; «…, al Tomo»; «…, al Tomo [COMPLETAR], libro»; «…, libro [COMPLETAR], folio, finca»; «…, folio, finca [COMPLETAR],»; «…[COMPLETAR] Cuya referencia catastral es»; «…euros y el uso y disfrute de la finca»; «…relacionan a continuación: D, %; Dña, %;»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- Ley 2/2006

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

### Formulario 0547 · Escritura de constitución de compañía familiar gallega

- Año del modelo: 2016
- Revisión 17-11-2026: 20 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (IMPORTE, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [FECHA].

ANTE MI, Notario del Ilustre Colegio de [COLEGIO], con residencia en [COMPLETAR],

COMPARECEN

D y Dña, cónyuges, mayores de edad, profesionales de la agricultura, vecinos de [COMPLETAR], con domicilio en [LOCALIDAD] Exhiben DNI/NIF [NIF], respectivamente.

D, hijo de los primeros, y la pareja de hecho (de acuerdo con la previsión de la D.A. 3ª LDCG) de éste Dña, mayores de edad, profesionales de la agricultura, vecinos de [COMPLETAR], con domicilio en Exhiben DNI/NIF, respectivamente.

D. [NOMBRE Y APELLIDOS], hijo de los primeros, soltero, mayor de edad, profesional de la agricultura, vecino de [COMPLETAR], con domicilio en Exhiben DNI/NIF, respectivamente.

Sujetos al Derecho civil de Galicia.

Intervienen en su propio nombre y derecho.

Les identifico por sus expresados Documentos Nacionales de Identidad, cuyos números coinciden con los de Identificación Fiscal; tienen, a mi juicio, capacidad y legitimación para otorgar la presente escritura de CONSTITUCIÓN DE COMPAÑÍA FAMILIAR GALLEGA y

EXPONEN

Que todos están sujetos al Derecho Civil de Galicia.

Que los cónyuges D. y Dña son propietarios, en régimen de gananciales, de las siguientes fincas (descripción de los bienes que se aportan a la compañía: inmuebles ?casa de labora-, fincas, lugar acasarado, aperos):

Descripción de los bienes

Inscrita en el Registro de la Propiedad de [COMPLETAR], al Tomo [COMPLETAR], libro [COMPLETAR], folio, finca [COMPLETAR], [COMPLETAR]

Cuya referencia catastral es [COMPLETAR]

Descripción de las cargas, si las hubiera

Que D. es propietario del siguiente vehículo tractor (o de otra finca, o de otro bien que quisiera aportar)

Descripción

Expuesto esto,

OTORGAN

Los comparecientes quieren constituir una Compañía familiar gallega, regulada en los arts. 157 y ss. de la Ley 2/2006, de 14 de junio, de Derecho Civil de Galicia, para vivir juntos y explotar en común las tierras y bienes descritos en esta escritura.

Las aportaciones que se harán por los comparecientes a dicha Compañía serán las siguientes:

1º) Los cónyuges D. y Dña aportan en propiedad la finca (descrita en el exponendo II), cuyo valor se estima en [IMPORTE] euros, y aportan el uso y disfrute del inmueble (descrito en el exponendo II), con un valor estimado de [IMPORTE] euros y el uso y disfrute de la finca [COMPLETAR] (descrita en el exponendo II), cuyo valor es de [IMPORTE] Euros.

2º) D aporta en propiedad el vehículo tractor, descrito en el exponendo III.

3º) D y la pareja de hecho formada por D y Dña aportarán su trabajo personal en la explotación de la Compañía.

En atención a lo precedente y a la regulación de la Ley de Derecho civil de Galicia, constituirán los bienes de esta Compañía los siguientes:

1º) Los aportados por los socios en la forma que se describe en la cláusula segunda.

2º) Los que se adquieran a título oneroso por cuenta del capital común, en tanto dure la compañía.

3º) Los frutos, rentas, ganancias e intereses percibidos o debidos durante el mismo tiempo, procedentes de los bienes sociales.

4º) Las edificaciones, reconstrucciones, plantaciones y cualquier tipo de mejora hecha en los bienes sociales.

Las cuotas de participación en la Compañía serán las que se relacionan a continuación: D, %; Dña, %; [COMPLETAR]: D, %; Dña, %; [COMPLETAR]: D, %.

La administración y representación de la Compañía se le atribuye a D./Dña. [NOMBRE Y APELLIDOS] quien precisará del consentimiento de los demás para tomar dinero a préstamo y realizar actos de disposición y gravamen sobre los inmuebles. En lo demás, tendrá facultades para adquirir para la Compañía y obligarse en su nombre y disponer de los semovientes y bienes muebles sociales.

No perderá la condición de partícipe en la Compañía aquel miembro de la misma que con el consentimiento de los demás habite bajo techo distinto del común ni el que desarrolle actividades ajenas a la explotación del patrimonio de la Compañía, siempre que siga vinculado en la vida y explotación comunitarias y aquellas actividades sean compatibles con la participación en dicha explotación.

En caso de modificación de la compañía por las causas establecidas en la Ley, el socio separado o sus derechohabientes no podrán retirar sus bienes propios ni la parte que les corresponda en los sociales hasta tanto que finalicen las operaciones pendientes y la recogida de los frutos, siempre que la realización de las mismas no supere el año.

En todo lo no previsto en esta escritura, se aplicarán las normas de la Ley 2/2006, de 14 de junio, de Derecho Civil de Galicia relativas a esta institución.

========================================================================
