---
name: exhibicion-libros-contables-socio-frente-administrador-646
description: "Redacta el escrito «Exhibición de libros contables del socio frente al administrador (jurisdicción voluntaria)» (formulario 646 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Exhibición de libros contables del socio frente al administrador (jurisdicción voluntaria)

> Formulario 0646 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] LOCALIDAD (3 veces)
- [ ] FECHA (2 veces)
- [ ] Nº
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…y de»; «…rado de la Administración de Justicia de»; «…CONTABILIDAD Y DOCUMENTOS DE LA SOCIEDAD»; «… en su condición de socio de la Sociedad»; «…de la inscripción registral. La sociedad»; «…tiene como objeto social»; «…su domicilio social bajo la razón social»; «…manteniendo con la sociedad desde el año»; «…un contrato en exclusiva con la sociedad»; «…usiva firmado con la sociedad proveedora»; «…paldas de los demás socios, a efectos de»; «…ibros y documentación contra la sociedad»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 112 LJV
- art. 113.2 LJV
- art. 115 LJV
- art. 116 LJV

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

### Formulario 0646 · Exhibición de libros contables del socio frente al administrador (jurisdicción voluntaria)

- Año del modelo: 2015
- Revisión 17-11-2026: 20 campos de relleno marcados en blanco; 5 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

D. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en nombre y representación de [NOMBRE DEL REPRESENTADO/A] y de [COMPLETAR], según acredito apoderamiento apud acta otorgado ante el Letrado de la Administración de Justicia de [COMPLETAR], ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

- Que al amparo de lo dispuesto en los arts. 112 y siguientes de la Ley de Jurisdicción Voluntaria, mediante el presente escrito deduzco SOLICITUD DE EXHIBICIÓN DE LIBROS DE CONTABILIDAD Y DOCUMENTOS DE LA SOCIEDAD [COMPLETAR], con domicilio social en [LOCALIDAD], la cual dirijo contra la citada sociedad, en atención a los siguientes

HECHOS

Mi representado actúa en su condición de socio de la Sociedad [COMPLETAR], la cual fue constituida en fecha [FECHA] por mi representado y otros dos socios, D. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD] y D. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], distribuyéndose el capital social en las siguientes participaciones: ().

En el mismo acto de constitución fue nombrado administrador único el socio D. [NOMBRE Y APELLIDOS], sin que se hayan producido ulteriores modificaciones estatutarias.

Acompaño como documentos núm. copia de la escritura de constitución y de los estatutos, y certificación de la inscripción registral.

La sociedad [COMPLETAR] tiene como objeto social [COMPLETAR], el cual venía realizando en la sede de su domicilio social bajo la razón social [COMPLETAR], dedicándose a la venta de maquinaria y enseres de suministro industrial.

En fecha [FECHA], mi representado ha tenido conocimiento que se ha comunicado por la sociedad a todos los proveedores que se rescindía la relación negocial que venían manteniendo con la sociedad desde el año [COMPLETAR], y que se ha concertado un contrato en exclusiva con la sociedad [COMPLETAR], que se encargará de proveer toda la maquinaria y productos que se suministran en el referido negocio.

Al tener conocimiento de este hecho, mi representado se dirigió al socio administrador único solicitando información, habiéndose negado éste a facilitar cualquier tipo de información sobre el cambio de proveedores.

A efectos acreditativos acompaño como documentos núm. [Nº], cartas dirigidas por el administrador a anteriores proveedores y requerimiento notarial en demanda de información al administrador D. [NOMBRE Y APELLIDOS]

Ante esta actitud del administrador, esta parte se ve en la obligación de acudir al Tribunal para solicitar la exhibición de los libros de contabilidad y documentos relacionados con el cambio de proveedores, por ser de evidente interés para los socios y para la marcha de la sociedad.

Concretamente, se solicita la exhibición del contrato de exclusiva firmado con la sociedad proveedora [COMPLETAR], y el examen de los asientos contables y facturas que recogen los pagos a la referida sociedad.

Con ello se pretende conocer las circunstancias del negocio concertado de forma unilateral por el administrador a espaldas de los demás socios, a efectos de [COMPLETAR], en su caso, ejercitar las actuaciones y acciones que correspondan a mi representado en su condición de socio, incluso la de responsabilidad contra el administrador.

Lo anteriormente expuesto pone de manifiesto la procedencia de la exhibición de los libros y documentos expresados, al tener mi representado derecho e interés legítimo conforme a lo expuesto.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

Es competente la Sección de lo Mercantil del Tribunal de Instancia al que me dirijo al tener el domicilio social la Sociedad en esta localidad, conforme a lo dispuesto en el art. 113.1 de la Ley de Jurisdicción Voluntaria.

Procedimiento

Debe seguirse el expediente de jurisdicción voluntaria regulado en los artículos 112 a 116 de la Ley de Jurisdicción Voluntaria.

Legitimación y postulación

Mi representado está legitimado según lo dispuesto en los arts. 32 y 33 del Código de Comercio y concordantes en relación con el art. 112 LJV, y compareciendo representado por Procurador y asistido de Abogado de acuerdo a lo dispuesto en el art. 113.2 LJV.

Procedencia de la exhibición

Es de aplicación el art. 32 del Código de Comercio que establece: “1. La contabilidad de los empresarios es secreta, sin perjuicio de lo que se derive de lo dispuesto en las Leyes. 2. La comunicación o reconocimiento general de los libros, correspondencia y demás documentos de los empresarios, sólo podrá decretarse, de oficio o a instancia de parte, en los casos de sucesión universal, suspensión de pagos, quiebras, liquidaciones de sociedades o entidades mercantiles, expedientes de regulación de empleo, y cuando los socios o los representantes legales de los trabajadores tengan derecho a su examen directo. 3. En todo caso, fuera de los casos prefijados en el párrafo anterior, podrá decretarse la exhibición de los libros y documentos de los empresarios a instancia de parte o de oficio, cuando la persona a quien pertenezcan tenga interés o responsabilidad en el asunto en que proceda la exhibición. El reconocimiento se contraerá exclusivamente a los puntos que tengan relación con la cuestión de que se trate”.

Forma de realizar la exhibición

Es de aplicación el art. 33 del Código de Comercio y art. 115 LJV, debiendo procederse conforme a lo dispuesto en el art. 116 LJV en caso de negativa u obstaculización por el obligado.

Por lo anterior,

AL TRIBUNAL SUPLICO que tenga por presentada esta solicitud de exhibición de libros y documentación contra la sociedad [COMPLETAR] con los documentos acompañados y, en su virtud, la admita y, previos los trámites legales, se dicte resolución ordenando que se pongan de manifiesto los libros y documentos solicitados, señalando día y hora para la exhibición.

En(lugar y fecha)

(Firma Abogado y Procurador)

========================================================================
