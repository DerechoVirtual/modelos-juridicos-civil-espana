---
name: autorizacion-disponer-gravar-bienes-persona-discapacidad-654
description: "Redacta el escrito «Autorización para disponer o gravar bienes de persona con discapacidad» (formulario 654 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Autorización para disponer o gravar bienes de persona con discapacidad

> Formulario 0654 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO
- [ ] FECHA
- [ ] Nº (3 veces)
- [ ] IMPORTE
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de la localidad de»; «… era el local donde tenían su negocio de»; «…ecimiento del padre, titular del negocio»; «…ularidad de mi representado a la empresa»; «…e ha expresado anteriormente, la empresa»; «…de la localidad de»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 287 del Código Civil

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

### Formulario 0654 · Autorización para disponer o gravar bienes de persona con discapacidad

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 20 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 6 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en nombre y representación de [NOMBRE DEL REPRESENTADO/A], en su condición de curador de D. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, ante el Tribunal comparezco y como mejor proceda en Derecho

DIGO:

-Que al amparo de lo dispuesto en el art. 61 y siguientes de la Ley de Jurisdicción Voluntaria, mediante el presente escrito deduzco expediente de jurisdicción voluntaria en SOLICITUD DE AUTORIZACIÓN PARA LA CELEBRACIÓN DE UN CONTRATO DE ARRENDAMIENTO el inmueble propiedad de la persona con discapacidad que precisa el apoyo D. [NOMBRE Y APELLIDOS], sito en la calle [CALLE] de la localidad de [COMPLETAR], en atención a los siguientes

HECHOS

Mi representado fue nombrado curador con funciones de representación en el procedimiento de adopción de medidas judiciales de apoyo número [NÚMERO], tal como se acredita en la resolución que se acompaña por testimonio como documento número

Mi representado solicita la autorización judicial para el arrendamiento del inmueble propiedad de la persona que precisa el apoyo D. [NOMBRE Y APELLIDOS], actuando en la representación y asistencia que tiene conferida, por ser necesario, útil y conveniente para la persona con discapacidad.

El inmueble cuyo arrendamiento se pretende tiene la siguiente descripción:

“Urbana. Local sito en [LOCALIDAD]

”

El referido inmueble fue adquirido por la persona con discapacidad por herencia de sus padres el pasado día [FECHA], y era el local donde tenían su negocio de [COMPLETAR], el cual fue cerrado como consecuencia del fallecimiento del padre, titular del negocio [COMPLETAR].

El arrendamiento cuya autorización se pretende es necesario y útil para el tutelado por cuanto que el local se encuentra en la actualidad desocupado, sin ningún tipo de actividad.

La solución del arrendamiento es la más conveniente puesto que permite asegurar unos ingresos mensuales a la persona que precisa el apoyo para hacer frente a sus necesidades vitales, habiendo optado por un arrendamiento de larga duración por la solvencia de la empresa arrendataria ofertante y la ventajosa oferta económica realizada según se pasa a exponer seguidamente.

El objeto de la autorización es el arrendamiento del local titularidad de mi representado a la empresa [COMPLETAR] por un periodo inicial de más de seis años, concretamente de [Nº] años, y a cambio una renta mensual de [IMPORTE] euros, con las condiciones que se especifican en el acuerdo condicionado a la obtención de esta autorización que se acompaña como documento núm. [Nº DE DOCUMENTO]

Tal como se ha expresado anteriormente, la empresa [COMPLETAR] es solvente, según es notoriamente conocido, y el precio del arriendo pactado excede con mucho del que se está pagando en el mercado, según acredito mediante certificado del agente de la propiedad inmobiliaria D. [NOMBRE Y APELLIDOS], que se acompaña como documento núm. [Nº], por lo cual es muy ventajoso pactar un contrato de larga duración, puesto que asegura unos ingresos regulares a la persona que precisa el apoyo con los que hacer frente a sus necesidades y ahorrar unas cantidades con las que hacer frente a las necesidades futuras.

El importe íntegro que se obtenga del arriendo se destinará a hacer frente las necesidades vitales de la persona que precisa el apoyo y, en la cantidad excedente, al ahorro para hacer frente a eventuales necesidades futuras.

Todas estas circunstancias han sido comunicadas a la persona que precisa el apoyo quien ha mostrado su voluntad de concertar el negocio en los términos expresados.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

Son competentes las secciones civiles de los tribunales de instancia de esta ciudad, por ser el lugar del domicilio de la persona con discapacidad conforme a lo dispuesto en el art. 62.1 de la Ley de Jurisdicción Voluntaria.

Procedimiento

Teniendo en cuenta que se solicita la autorización para un acto de disposición sujeto a autorización judicial, debe seguirse el procedimiento de jurisdicción voluntaria regulado en los artículos 61 y siguientes de la Ley de Jurisdicción Voluntaria.

Legitimación, cuantía y postulación

Mi representado está legitimado en su condición de curador conforme a lo dispuesto en el art. 287 del Código Civil, compareciendo representado por Procurador y asistido por Abogado según lo dispuesto en el art. 62.3 de la Ley de Jurisdicción Voluntaria, al exceder el valor del arriendo del importe de 6.000 euros.

Fundamentos de fondo

El art. 287.2º del Código Civil establece que el curador que ejerza funciones de representación necesita autorización judicial, de acuerdo con lo que determina la resolución para: “Enajenar o gravar bienes inmuebles, establecimientos mercantiles o industriales, bienes o derechos de especial significado personal o familiar, bienes muebles de extraordinario valor, objetos preciosos y valores mobiliarios no cotizados en mercados oficiales de la persona con medidas de apoyo, dar inmuebles en arrendamiento por término inicial que exceda de seis años, o celebrar contratos o realizar actos que tengan carácter dispositivo y sean susceptibles de inscripción. Se exceptúa la venta del derecho de suscripción preferente de acciones. La enajenación de los bienes mencionados en este párrafo se realizará mediante venta directa salvo que el Tribunal considere que es necesaria la enajenación en subasta judicial para mejor y plena garantía de los derechos e intereses de su titular”.

En este caso, tal como ha quedado expuesto, es de interés de la persona que precisa el apoyo la concertación del arrendamiento en los términos expresados, además de ser concorde a su voluntad.

Por lo anterior,

AL TRIBUNAL SUPLICO que tenga por presentada esta solicitud de autorización para el arrendamiento del inmueble sito en la calle [CALLE] de la localidad de [COMPLETAR], propiedad de la persona que precisa el apoyo por un periodo de [Nº] años en las condiciones expuestas en esta solicitud y, tras los trámites legales, con audiencia de la persona que precisa el apoyo e intervención del Ministerio Fiscal, dicte auto por el que conceda la autorización para arrendar el inmueble antes referido de acuerdo con las condiciones expresadas en este escrito.

OTROSÍ PRIMERO DIGO: Que a los efectos establecidos en el art. 64.1 de la Ley de Jurisdicción Voluntaria, solicito que sea citado a la comparecencia la persona que precisa el apoyo D/Dª [NOMBRE Y APELLIDOS], a fin de ser oído, cuidando esta parte de su comparecencia el día y hora que se señale.

Por lo que,

SUPLICO AL TRIBUNAL: Tenga por propuesta la audiencia de la persona que precisa el apoyo y acuerde de conformidad.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

(Firma Procurador y Abogado)

========================================================================
