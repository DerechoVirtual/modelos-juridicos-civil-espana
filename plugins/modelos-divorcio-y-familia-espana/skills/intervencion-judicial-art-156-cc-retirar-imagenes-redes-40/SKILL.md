---
name: intervencion-judicial-art-156-cc-retirar-imagenes-redes-40
description: "Redacta el escrito «Intervención judicial (art. 156 CC): retirar imágenes en redes de menor de 14 años» (formulario 40 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Intervención judicial (art. 156 CC): retirar imágenes en redes de menor de 14 años

> Formulario 0040 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] LOCALIDAD
- [ ] Nº DE DOCUMENTO
- [ ] ...
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…O DE LA PATRIA POTESTAD DEL/ DE LA MENOR»; «…enen un/una hijo/a en común, nacido/a el»; «…rajudicial. En este sentido, se acudió a»; «…por ser el que conoció del procedimiento»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 156 del Código Civil
- art. 5 de la Ley Orgánica 1/2025
- art. 156 del Código Civil
- artículo 18.1 de la Constitución
- artículo 5.1.f) del Real Decreto 1720/2007
- artículo 3 de la Ley Orgánica 1/1982
- artículo 13.1 del Real Decreto 1720/2007
- Ley Orgánica 15/1999

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

### Formulario 0040 · Intervención judicial (art. 156 CC): retirar imágenes en redes de menor de 14 años

- Año del modelo: 2024
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 10 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE] QUE POR TURNO CORRESPONDA

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, actuando en nombre y representación de [NOMBRE DEL REPRESENTADO/A], con domicilio en [LOCALIDAD], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, ante el Tribunal comparezco y como mejor proceda en Derecho,

DIGO

Que, al amparo de lo dispuesto en el artículo 156 del Código Civil en relación con los artículos 86 y siguientes de la Ley de Jurisdicción Voluntaria, mediante el presente escrito deduzco expediente de jurisdicción voluntaria en SOLICITUD DE INTERVENCIÓN JUDICIAL POR DESACUERDO EN EL EJERCICIO DE LA PATRIA POTESTAD DEL/ DE LA MENOR [COMPLETAR], en atención a los siguientes,

HECHOS

PRIMERO.- Mi representado/a y el/la demandado/a tienen un/una hijo/a en común, nacido/a el [COMPLETAR].

Se acompaña como DOCUMENTO NÚM. 1 el certificado de nacimiento del/ de la menor.

SEGUNDO El desacuerdo se ha producido respecto de la decisión tomada unilateralmente por el/la demandado/a de publicar fotografías y vídeos del/de la menor en sus redes sociales, siendo así, públicas para toda su red de contactos, así como terceros.

Se acompaña como BLOQUE DOCUMENTAL NÚM. 2 una recopilación de publicaciones efectuadas en dichas redes sociales.

A juicio de esta parte, la presencia del/ de la hijo/a de ambos en redes sociales es perjudicial para éste/ésta, poniendo en riesgo la tutela de su derecho al honor y la propia imagen.

El/la demandado/a se ha mostrado intransigente en cuanto a este aspecto, negándose a retirar las fotografías y videos que actualmente constan publicados en sus redes sociales.

TERCERO Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

A los anteriores hechos, resultan de aplicación los siguientes,

FUNDAMENTOS DE DERECHO

PRIMERO.- JURISDICCIÓN Y COMPETENCIA

Resultan competentes las secciones civiles de los tribunales de instancia de esta ciudad, por ser los del lugar del domicilio del/ de la menor conforme a lo dispuesto en los artículos 86.2 de la Ley de Jurisdicción Voluntaria y 85.1º LOPJ.

(alternativamente)

Resulta competente el Tribunal al que me dirijo por ser el que conoció del procedimiento [COMPLETAR] en que se dictó resolución judicial relativa al ejercicio conjunto de la patria potestad por ambos progenitores.

SEGUNDO .- PROCEDIMIENTO

TERCERO.- LEGITIMACIÓN, CUANTÍA Y POSTULACIÓN

Ambos progenitores ostentan legitimación activa y pasiva, respectivamente, de conformidad con lo establecido en el artículo 86.3 de la Ley de Jurisdicción Voluntaria.

Asimismo, esta parte comparece representada por Procurador y asistida por Abogado, pese a no ser preceptivo.

CUARTO.- INTERVENCIÓN DEL MINISTERIO FISCAL

De conformidad con lo establecido en el artículo 85 de la Ley de Jurisdicción Voluntaria, el Ministerio Fiscal deberá estar presente en la comparecencia a la que sean citadas las partes.

QUINTO.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD

La presente demanda cumple con los requisitos de procedibilidad exigidos por el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

SEXTO.- FONDO

Resultan aplicables los siguientes preceptos:

- El art. 156 del Código Civil en cuanto a la posibilidad de ambos progenitores de acudir al Juez en caso de desacuerdo puntual en relación con el ejercicio de las funciones de la patria potestad.

- Los artículos 85 y 86 de la Ley de Jurisdicción Voluntaria en cuanto a la tramitación del presente expediente.

En cuanto a pronunciamientos jurisprudenciales, citamos el Auto de la Audiencia Provincial de Asturias núm. 31/2019 de 13 de marzo en cuyo F.J 3 se indica:

“Hechas tales precisiones, resulta indudable que el derecho al honor, a la intimidad y a la propia imagen que establece el artículo 18.1 de la Constitución también corresponde a los menores, y así lo declara expresamente el artículo 4.1 de la Ley Orgánica de Protección Jurídica del Menor, y en cuanto se configura como un derecho de la personalidad que atribuye a su titular la facultad de disponer de la representación de su aspecto físico que permita su identificación y la representación fotográfica del menor, constituye un dato de carácter personal (artículo 5.1.f) del Real Decreto 1720/2007, de 21 de diciembre, por el que se aprueba el Reglamento de desarrollo de la Ley Orgánica 15/1999, de 13 de diciembre, de protección de datos de carácter personal).

Tanto desde la perspectiva de la protección del derecho a la propia imagen como de la de protección de datos de carácter personal se requiere el consentimiento del titular del derecho para excluir la intromisión ilegítima o el tratamiento no autorizado de los datos.

En el primer caso, el artículo 3 de la Ley Orgánica 1/1982, de 5 de mayo, establece que el consentimiento de los menores deberá prestarse por ellos mismos si sus condiciones de madurez lo permiten de acuerdo con la legislación civil, siendo en otro caso su representante legal quien habrá de otorgarlo comunicándolo previamente el Ministerio Fiscal.

En el segundo, el artículo 13.1 del Real Decreto 1720/2007, de 21 de diciembre, considera suficiente el consentimiento de los mayores de catorce años, precisando los menores de esa edad el consentimiento de los padres o tutores [...].

Queda claro, por tanto, que la difusión y publicación de fotografías de la menor requiere en este caso el consentimiento de ambos progenitores.

Ahora bien, ante la discrepancia surgida entre ellos por la negativa a que así se haga en el caso de la madre, que se ha mostrado contraria a que la imagen de su hija se difunda a través de las redes sociales, lo que surge es un desacuerdo en el ejercicio de la patria potestad que debería dar lugar a que fuese el Juez quien, oídos ambos progenitores, atribuyera a uno de ellos la facultad de decidir, esto es, si se consiente en la publicación o difusión de las fotos, en caso de atribuirla al padre, o si no debe consentirse, caso de hacerlo a la madre”

SÉPTIMO.- IURA NOVIT CURIA

En todo lo no invocado, resulta de aplicación el principio iura novit curia.

Por lo anterior,

SUPLICO AL TRIBUNAL: Que teniendo por presentado este escrito junto con sus copias y documentos que le acompañan, se sirva admitirlo y tenga por promovido expediente de jurisdicción voluntaria en solicitud de I NTERVENCIÓN JUDICIAL POR DESACUERDO EN EL EJERCICIO DE LA PATRIA POTESTAD DEL/DE LA MENOR.,y, tras los trámites legales oportunos, previa audiencia de los progenitores y del/ de la menor, acuerde atribuir a mi mandante la facultad de decidir respecto a la presencia del/ de la menor en redes sociales.

OTROSÍ PRIMERO DIGO: Que al amparo de lo dispuesto en el artículo 231 de la Ley de Enjuiciamiento Civil, esta parte manifiesta su voluntad de corregir cualquier defecto de carácter procesal en que pudiera haber incurrido.

En su virtud,

AL TRIBUNAL SUPLICO: Que tenga por hecha la anterior manifestación a los efectos oportunos.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Ldo…. Proc……
