---
name: oposicion-arrendatario-persona-fisica-extincion-veinte-814
description: "Redacta el escrito «Oposición del arrendatario persona física a la extinción por los veinte años» (formulario 814 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición del arrendatario persona física a la extinción por los veinte años

> Formulario 0814 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] CALLE (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] FECHA (3 veces)
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…(arrendatario) C/ [CALLE] (domicilio)»; «…(arrendador) C/ [CALLE] (domicilio)»; «…ndamiento de local de negocio situado en»; «…La causa de oposición es:»; «… haberse pactado un plazo de duración de»

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

### Formulario 0814 · Oposición del arrendatario persona física a la extinción por los veinte años

- Año del modelo: 2015
- Revisión 17-11-2026: 15 huecos del original que se habían perdido sin marca, marcados (CALLE, COMPLETAR, DÍA, FECHA, LUGAR, MES, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D./Dña. [NOMBRE Y APELLIDOS] (arrendatario)

C/ [CALLE] (domicilio)

[COMPLETAR] (ciudad)

A la atención de:

D./Dña. [NOMBRE Y APELLIDOS] (arrendador)

C/ [CALLE] (domicilio)

[COMPLETAR] (ciudad)

En [LUGAR], a [DÍA] de [MES] de [AÑO]

Muy Sr. Mío:

Mediante la presente procedo a oponerme a la extinción del contrato de arrendamiento de local de negocio situado en [COMPLETAR], de fecha [FECHA] y del que es Ud. propietario, comunicada en fecha [FECHA]

La causa de oposición es: [COMPLETAR] (Opciones):

1.º El contrato no se encuentra en situación de prórroga legal sino que, al haberse pactado un plazo de duración de [COMPLETAR] años, todavía se encuentra vigente. En aplicación de lo dispuesto en el nº 5 del apdo. B) de la D.T. Tercera de la LAU, en los contratos que a la fecha de entrada en vigor de dicha norma, es decir, el 1 de enero de 1995 no hubiera transcurrido el plazo determinado pactado, durarán el tiempo que reste para que dicho plazo se cumpla.

Por tanto el contrato se extinguirá el día [FECHA]

2.º El contrato se extinguirá por jubilación o fallecimiento del arrendatario titular del contrato, según lo establecido en el apdo. B) 3º de la D.T. Tercera de la LAU. No habiéndose producido ninguno de estos dos eventos procede mantener la vigencia del contrato, al continuar al frente del negocio quien en su día suscribió el contrato.

3.º El contrato se extinguirá por jubilación o fallecimiento del cónyuge del arrendatario subrogado en el contrato, tal como se notificó en su día. Así lo permite el apdo. B) 3º de la D.T. Tercera de la LAU. No habiéndose producido ninguno de estos dos eventos procede mantener la vigencia del contrato, al continuar al frente del negocio, y dada de alta en el IAE de la actividad para la que se pactó el arriendo, la misma persona subrogada.

Concluyo por tanto reiterando que el 1 de enero de 2015 continuaré ejerciendo en el local la misma actividad comercial hasta que se den las condiciones para la resolución del contrato.

========================================================================
