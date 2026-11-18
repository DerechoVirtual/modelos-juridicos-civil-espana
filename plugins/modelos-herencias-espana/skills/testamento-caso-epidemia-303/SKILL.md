---
name: testamento-caso-epidemia-303
description: "Redacta el escrito «Testamento en caso de epidemia» (formulario 303 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Testamento en caso de epidemia

> Formulario 0303 del plugin **Sucesiones** · revisado el 17-11-2026.

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

- [ ] LUGAR (2 veces)
- [ ] DÍA (2 veces)
- [ ] MES (2 veces)
- [ ] AÑO (2 veces)
- [ ] Nº
- [ ] FECHA
- [ ] LOCALIDAD
- [ ] NÚMERO
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de [AÑO].a las [Nº] horas. Yo, Don»; «…, vecino de»; «… DIGO: Que soy hijo de los consortes Don»; «…y Doña»; «…stando casado en únicas nupcias con Doña»; «…atrimonio tengo tres hijos, llamados Don»; «…, Doña»; «…uales a mis antes mencionados hijos, Don»; «…, Doña»; «…, Doña [COMPLETAR] y Doña»; «…, nacido enel día, hijo dey, vecino de»; «…, nacido enel día, hijo dey, vecino de»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 701 CCiv

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

### Formulario 0303 · Testamento en caso de epidemia

- Año del modelo: 2020
- Revisión 17-11-2026: 22 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Testamento abierto especial otorgado en tiempo de epidemia sin intervención de Notario.

En [LUGAR], a [DÍA] de [MES] de [AÑO].a las [Nº] horas.

Yo, Don [COMPLETAR], mayor de edad, nacido el día [FECHA], vecino de [COMPLETAR], con domicilio en [LOCALIDAD], con D.N.I. nº [NÚMERO], por el presente documento vengo a otorgar testamento abierto, y a tal efecto, DIGO:

Que soy hijo de los consortes Don [COMPLETAR] y Doña [COMPLETAR], ambos ya fallecidos; estando casado en únicas nupcias con Doña [COMPLETAR], de cuyo matrimonio tengo tres hijos, llamados Don [COMPLETAR], Doña [COMPLETAR] y Doña [NOMBRE Y APELLIDOS]

Que ordeno mi última voluntad a tenor de las siguientes

CLAÚSULAS

PRIMERA.- Lego a mi cónyuge el usufructo universal y vitalicio de mi herencia, relevándole de la obligación de prestar fianza y hacer inventario. Si alguno de mis descendientes legitimarios no estuviese conforme con esta disposición, quedará reducido a su legítima estricta, acreciendo su parte en los tercios de mejora y libre disposición a los que lo estuvieren; y si ninguno fuese conforme, lega a su cónyuge el tercio de libre disposición en pleno dominio, además de su cuota legal usufructuaria.

Ordeno a mis herederos respetar esta disposición testamentaria y determino que aquel que la impugnare, reciba en tal caso, del testador sólo lo que por legítima corta le conceda la Ley, acreciendo lo que perdiera en los tercios de mejora y libre disposición en favor de los que acaten su voluntad expresada.

SEGUNDA.- Instituyo por mis únicos universales herederos por partes iguales a mis antes mencionados hijos, Don [COMPLETAR], Doña [COMPLETAR] y Doña [COMPLETAR], quienes serán sustituidos vulgarmente, en caso de premoriencia o incapacidad, por sus respectivos descendientes.

TERCERA.- Nombro albacea, comisario, contador-partidor, con las más amplias facultades que el Código Civil le confiere, y por el plazo legal prorrogable por otro periodo igual, a mi Abogado Don [NOMBRE Y APELLIDOS]

CUARTA.- Revoco y dejo sin efecto alguno, cualquier disposición testamentaria anterior.

TESTIGOS

Debido a las circunstancias excepcionales de epidemia (art. 701 CCiv) bajo las que se redacta este testamento, son testigos de mis últimas voluntades las siguientes personas, todas ellas mayores de edad y con capacidad suficiente para testificar, quienes firman conmigo este documento en prueba de veracidad de cuanto se ha recogido en el mismo.

D./Dª [NOMBRE Y APELLIDOS], nacido enel día, hijo dey, vecino de [COMPLETAR], con domicilio, y provisto de DNI.

D./Dª [NOMBRE Y APELLIDOS], nacido enel día, hijo dey, vecino de [COMPLETAR], con domicilio, y provisto de DNI.

D./Dª [NOMBRE Y APELLIDOS], nacido enel día, hijo dey, vecino de [COMPLETAR], con domicilio, y provisto de DNI.

Es justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del testador

	Firma de los testigos
