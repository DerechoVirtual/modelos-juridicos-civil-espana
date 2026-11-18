---
name: otrosi-medidas-cautelares-art-727-lec-inventario-168
description: "Redacta el escrito «Otrosí de medidas cautelares del art. 727 LEC: inventario y administrador judicial» (formulario 168 de medidas cautelares y diligencias preliminares, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Otrosí de medidas cautelares del art. 727 LEC: inventario y administrador judicial

> Formulario 0168 del plugin **Medidas cautelares y diligencias preliminares** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.
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

- [ ] FECHA
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…1.- D. asesor fiscal del negocio. 2.- Dª»; «…tica. Por ser de Justicia, que pido en a»

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

### Formulario 0168 · Otrosí de medidas cautelares del art. 727 LEC: inventario y administrador judicial

- Año del modelo: 2021
- Revisión 17-11-2026: saltos de párrafo recuperados (texto venía pegado); 3 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Documento adaptado a la reforma orgánica de la LO 1/2025

OTROSÍ DIGO que en la representación que ostento y al amparo de lo dispuesto en los artículos 721 y ss., especialmente el artículo 727, todos de la LEC, venimos a interesar la ADOPCIÓN DE LAS SIGUIENTES MEDIDAS CAUTELARES:

1.- La formación de inventario de todos los bienes gananciales, incluidos los bienes ubicados en la clínica, en las condiciones que el tribunal disponga.
2.- El nombramiento por este Tribunal de un administrador judicial que dé cuenta a este Tribunal mensualmente del negocio, así como del estado contable y financiero.

Esta petición se ampara en los hechos que hemos relatado en la demanda que anteceden al presente Otrosí, que damos por reproducidos a fin de evitar reiteraciones innecesarias.

Se dan los requisitos legalmente establecidos para su adopción, es decir:

a.

Apariencia de buen derecho: Lo cierto es que el negocio es ganancial y tras la crisis matrimonial, el esposo ha expulsado del mismo a mi mandante, impidiendo no sólo la entrada en la clínica que ambos regentaban sino también el acceso a las cuentas sociales, desconociendo en este momento qué operaciones pudiera estar realizando sin el conocimiento ni consentimiento de mi mandante.

b.

Nuestra representada es copropietaria, y como se ha acreditado con el documento que se ha aportado, recibió un requerimiento notarial por el que se le prohibía la entrada a la clínica ganancial, permaneciendo desde entonces completamente apartada del mismo por decisión unilateral del demandado.

c.

Peligro de mora procesal: en caso de que no se provea a la adopción de las medidas solicitadas, mi mandante puede ver perjudicado su derecho sobre los bienes gananciales, y especialmente sobre el negocio común, en caso de que el esposo realice operaciones en fraude del derecho de Dª.

d.

No es precisa la caución toda vez que es derecho legítimo de nuestra representada defender su copropiedad en los bienes respecto de los cuales se han solicitado las medidas cautelares.

A fin de acreditar los hechos, se acompañan los documentos acreditativos del carácter ganancial del negocio, así como las cuentas depositadas de los últimos dos ejercicios, el listado de los trabajadores, el alta en el RETA de nuestra mandante, la baja causada en el RETA con fecha [FECHA], mismo día en que recibió el requerimiento notarial.

Y se ofrece la declaración testifical de:

1.- D. asesor fiscal del negocio.
2.- Dª [COMPLETAR] secretaria de la clínica.
3.- Dª administrativa de la clínica.

Por todo lo cual,

AL TRIBUNAL SUPLICO tenga por formulado el presente OTROSÍ DIGO y por interesada la ADOPCIÓN DE LAS MEDIDAS CAUTELARES referidas. Admita todo ello y dé el trámite legal. Convoque a las partes a una comparecencia y, tras la práctica de la prueba, dicte Auto por el que acuerde las medidas solicitadas y provea lo necesario para su práctica. Por ser de Justicia, que pido en a [COMPLETAR].

Fdo. Ldo. Fdo. Procurador
