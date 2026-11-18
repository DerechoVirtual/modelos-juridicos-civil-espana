---
name: testamento-desheredacion-1185
description: "Redacta el escrito «Testamento con desheredación» (formulario 1185 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Testamento con desheredación

> Formulario 1185 del plugin **Sucesiones** · revisado el 17-11-2026.

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

- [ ] COLEGIO
- [ ] NOMBRE Y APELLIDOS (10 veces)
- [ ] FECHA
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO (2 veces)
- [ ] Nº (2 veces)
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…En»; «…, mi residencia, a»; «…, mi residencia, a [COMPLETAR] Ante mí,»; «…vecino de»; «…, número [NÚMERO], piso»; «…número [NÚMERO], piso [COMPLETAR], letra»; «…stando casada en únicas nupcias con Doña»; «…trumento público, que queda extendido en»; «…folios de la clase»; «…folios de la clase [COMPLETAR], serie»; «…, serie [COMPLETAR], números»

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

### Formulario 1185 · Testamento con desheredación

- Año del modelo: 2014
- Revisión 17-11-2026: 29 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [COMPLETAR], mi residencia, a [COMPLETAR]

Ante mí, [COMPLETAR], Notario del Ilustre Colegio de [COLEGIO].

COMPARECE

Don/Doña [NOMBRE Y APELLIDOS], mayor de edad, nacido el día [FECHA]

vecino de [COMPLETAR], con domicilio en [LOCALIDAD], en la calle [CALLE], número [NÚMERO], piso [COMPLETAR], letra [COMPLETAR], con D.N.I. número [NÚMERO]

Tiene a mi juicio el compareciente la capacidad legal necesaria para otorgar TESTAMENTO ABIERTO, y al efecto,

DICE

Que es hijo de los consortes Don/Doña [NOMBRE Y APELLIDOS], fallecido, y Don/Doña [NOMBRE Y APELLIDOS], que vive; estando casada en únicas nupcias con Doña [COMPLETAR], de cuyo matrimonio tiene tres hijos, llamados Don/Doña [NOMBRE Y APELLIDOS], Don/Doña [NOMBRE Y APELLIDOS], y Don/Doña [NOMBRE Y APELLIDOS], Que ordena su última voluntad a tenor de las siguientes

CLÁUSULAS

PRIMERA

Lega a su cónyuge el usufructo universal y vitalicio de su herencia, relevándole de la obligación de prestar fianza y hacer inventario. Si alguno de sus descendientes legitimarios no estuviese conforme con esta disposición, quedará reducido a su legítima estricta, acreciendo su parte en los tercios de mejora y libre disposición a los que lo estuvieren; y si ninguno fuese conforme, lega a su cónyuge el tercio de libre disposición en pleno dominio, además de su cuota legal usufructuaria.

Ordena a sus herederos respetar esta disposición testamentaria y determina que aquel que la impugnare, reciba en tal caso, del testador sólo lo que por legítima corta le conceda la Ley, acreciendo lo que perdiera en los tercios de mejora y libre disposición en favor de los que acaten su voluntad expresada.

SEGUNDA

Instituye por sus únicos universales herederos por partes iguales a sus antes mencionadas hijas, Don/Doña [NOMBRE Y APELLIDOS], y Don/Doña [NOMBRE Y APELLIDOS], quienes serán sustituidas vulgarmente, en caso de premoriencia o incapacidad, por sus respectivos descendientes.

TERCERA

Deshereda a su hijo Don/Doña [NOMBRE Y APELLIDOS], por la causa establecida en el artículo 853, número 2 del Código Civil, por haberle injuriado de palabra gravemente, y haberle abandonado en su grave enfermedad.

CUARTA

Nombra albacea, comisario, contador-partidor, con las más amplias facultades que el Código Civil le confiere, y por el plazo legal prorrogable por otro periodo igual, a su Abogado Don/Doña [NOMBRE Y APELLIDOS],

RESERVAS Y ADVERTENCIAS LEGALES

Así lo dice y otorga, siendo las [Nº] horas y [Nº] minutos.

Leo en alta voz el contenido de este testamento, por elección de su otorgante, advertida por mí de su derecho a leerlo por sí, y de explicarle yo, el Notario, su contenido del que me manifiesta su conformidad, por ser fiel y exacta expresión de su voluntad, y se ratifica y firma conmigo.

De conocer a la compareciente y, en general, de haberse observado las formalidades legales en un solo acto y de todo lo demás consignado en este instrumento público, que queda extendido en [COMPLETAR] folios de la clase [COMPLETAR], serie [COMPLETAR], números [COMPLETAR], el presente y el siguiente en orden, doy fe.

Firma del Notario/a:

========================================================================
