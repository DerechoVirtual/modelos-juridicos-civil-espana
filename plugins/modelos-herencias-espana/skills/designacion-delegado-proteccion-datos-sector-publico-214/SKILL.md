---
name: designacion-delegado-proteccion-datos-sector-publico-214
description: "Redacta el escrito «Designación del delegado de protección de datos en el sector público» (formulario 214 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Designación del delegado de protección de datos en el sector público

> Formulario 0214 del plugin **Sucesiones** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
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

- [ ] NIF
- [ ] LOCALIDAD (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Local. SE RESUELVE: Primero.- Designar a»; «…o a efectos del presente nombramiento en»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 35 del RGPD
- artículo 36 del RGPD
- Ley Orgánica 3/2018
- Ley 7/1985

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

### Formulario 0214 · Designación del delegado de protección de datos en el sector público

- Año del modelo: 2020
- Revisión 17-11-2026: 6 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D. adopta la siguiente RESOLUCIÓN:

Conforme a lo previsto en el artículo 37 del Reglamento (UE) 2016/679 del Parlamento Europeo y del Consejo de 27 de abril de 2016 relativo a la protección de las personas físicas en lo que respecta al tratamiento de datos personales y a la libre circulación de estos datos y por el que se deroga la Directiva 95/46/CE (RGPD), y arts. 34 y siguientes de la Ley Orgánica 3/2018, de 5 de diciembre, de Protección de Datos Personales y garantía de los derechos digitales (LOPDGDD), y con el fin de velar por el correcto cumplimiento de sus exigencias, una de las figuras claves en la nueva configuración del sistema de protección de los datos personales es la del Delegado de Protección de Datos (DPD).

En el ámbito de las entidades locales, la designación del Delegado de Protección de Datos es obligatoria al amparo de lo dispuesto en el artículo 37.1.a del RGPD y, permitiéndose por el punto 3 del citado artículo la designación de un único DPD para varias de estas autoridades u organismos, teniendo en cuenta su estructura organizativa y tamaño.

Asimismo, el artículo 37.6. del RGPD posibilita que la designación del DPD recaiga sobre una persona perteneciente a la plantilla del responsable o en una designada en virtud de un contrato administrativo de servicios, siempre que en ambos casos reúna los requisitos del punto 5.

A la vista de lo expuesto y de la documentación que obra en el expediente para la designación del DPD de este Ayuntamiento, y en el ejercicio de las atribuciones que me vienen conferidas al amparo de lo dispuesto en el artículo 21.1.s de la Ley 7/1985, de 2 de abril, reguladora de las Bases del Régimen Local.

SE RESUELVE:

Primero.- Designar a [COMPLETAR], con NIF [NIF] y domicilio a efectos del presente nombramiento en [COMPLETAR] como Delegado de Protección de Datos.

Segundo.- A tal efecto, y en su condición de Delegada de Protección de Datos de esta Entidad, desempeñará las siguientes funciones, prestando la debida atención a los riesgos asociados a las operaciones de tratamiento, teniendo en cuenta la naturaleza, el alcance, el contexto y fines del tratamiento, y en todo caso dentro de los términos y con los límites que resultan de los artículos del RGPD y de la LOPDGDD que regulan esta figura:

a. Informar y asesorar al responsable y a los funcionarios y/empleados que se ocupen del tratamiento de las obligaciones que les incumben en virtud del RGPD y de otras disposiciones de protección de datos.

b. Supervisar el cumplimiento de lo dispuesto en el RGPD, de otras disposiciones de protección de datos y de las políticas del responsable del tratamiento en materia de protección de datos personales, incluida la asignación de responsabilidades, la concienciación y formación del personal que participa en las operaciones de tratamiento, y las auditorías correspondientes.

c. Ofrecer el asesoramiento que se le solicite acerca de la evaluación de impacto relativa a la protección de datos y supervisar su aplicación de conformidad con el artículo 35 del RGPD.

d. Cooperar con la autoridad de control.

e. Actuar como punto de contacto de la autoridad de control para cuestiones relativas al tratamiento, incluida la consulta previa a que se refiere el artículo 36 del RGPD, y realizar consultas, en su caso, sobre cualquier otro asunto.

Tercero.- Ordenar la publicación en el tablón de anuncios y en la web de este Ayuntamiento, así como la de los datos de contacto del Delegado de Protección de Datos en la Web municipal, dando cuenta de la misma a la Agencia Española de Protección de Datos en su condición de autoridad de control.

Cuarto.- Notificar la Resolución a la interesada, a los efectos oportunos.

Contra esta Resolución, que pone fin a la vía administrativa, cabe interponer optativamente, uno de los siguientes

Recursos: Recurso de Reposición ante el mismo órgano del acto en el plazo de un mes contado a partir del día siguiente al de la notificación de esta Resolución.

Recurso Contencioso-Administrativo ante la Sala de lo Contencioso-Administrativo del Tribunal Superior de Justicia de [LOCALIDAD], en el plazo de dos meses contados desde el día siguiente al de la notificación de la Resolución. Recurso de Alzada ante el Tribunal Administrativo de [LOCALIDAD] dentro del mes siguiente a la fecha de notificación de esta Resolución.

En [LUGAR], a [DÍA] de [MES] de [AÑO].
