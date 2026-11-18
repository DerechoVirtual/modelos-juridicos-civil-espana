---
name: acta-junta-comunidad-agrupada-acuerdos-mayoria-1223
description: "Redacta el escrito «Acta de junta de comunidad agrupada con acuerdos de mayoría cualificada» (formulario 1223 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acta de junta de comunidad agrupada con acuerdos de mayoría cualificada

> Formulario 1223 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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

- [ ] Nº (3 veces)
- [ ] CALLE
- [ ] NÚMERO
- [ ] FECHA
- [ ] NOMBRE Y APELLIDOS (29 veces)
- [ ] IMPORTE
- [ ] DESCRIBIR
- [ ] Otros 51 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…En»; «…a las [Nº] horas, se reúne en»; «…horas, se reúne en [COMPLETAR] en»; «…convocatoria la Junta General»; «…se hicieron constar y que consistían en»; «…pación de Comunidades de Propietarios de»; «…, piso»; «…, piso»; «…, piso»; «…, piso»; «…, piso»; «…, piso»; …

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

### Formulario 1223 · Acta de junta de comunidad agrupada con acuerdos de mayoría cualificada

- Año del modelo: 2013
- Revisión 17-11-2026: 88 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [COMPLETAR] a las [Nº] horas, se reúne en [COMPLETAR] en [COMPLETAR] convocatoria la Junta General [COMPLETAR] de la Comunidad de Propietarios de la C/ [CALLE] núm. [NÚMERO], previa convocatoria en forma a todos sus integrantes con las cuestiones a tratar que en el orden del día de fecha [FECHA] se hicieron constar y que consistían en [COMPLETAR].

Esta Junta de Propietarios está integrada en la Agrupación de Comunidades de Propietarios de [COMPLETAR]

A la Junta asisten los siguientes propietarios:

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del %.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del %.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del %.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del %.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del %.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del %.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del %.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del %.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del %.

D./Dña. [NOMBRE Y APELLIDOS], local [COMPLETAR], con coeficiente de participación del %.

 D./Dña. [NOMBRE Y APELLIDOS] propietario del piso [COMPLETAR] y con coeficiente de participación del % autorizó a D./Dña. [NOMBRE Y APELLIDOS] para que lo representara en la Junta y votara en su nombre, según escrito que presentó con esa autorización y cuya copia se une a este acta.

(En su caso) Se hace constar que D./Dña. [NOMBRE Y APELLIDOS] propietario del local [COMPLETAR] y con coeficiente de participación del [COMPLETAR] % no se encuentra al corriente del pago de las cuotas de la comunidad por adeudar las de los meses de [COMPLETAR] cuyo importe total asciende a [IMPORTE] euros. Al no haber procedido antes de la celebración de la Junta a pagar ni a consignar su importe y no constando que haya impugnado judicialmente esta deuda, su persona y cuota de participación no son tenidas en cuenta para los efectos de calcular la mayoría legalmente exigida para los acuerdos que se adoptaron.

Preside la Junta el Presidente D./Dña. [NOMBRE Y APELLIDOS] y actúa como Secretario D./Dña. [NOMBRE Y APELLIDOS].

El Presidente da inicio a la reunión en la que se debatieron los puntos recogidos en el orden del día con el siguiente resultado:

1.º Lectura y aprobación del acta de la Junta anterior: Se aprueba por unanimidad de todos los asistentes.

2.º Por parte de la Agrupación de Comunidades se propone la realización en [COMPLETAR] de una obra común consistente en [DESCRIBIR]. La aprobación de esta obra requerirá un acuerdo de mayoría cualificada de [COMPLETAR] de todas las comunidades que lo componen.

Por parte del vecino del piso [COMPLETAR], D./Dña. [NOMBRE Y APELLIDOS], se plantea la posibilidad de [COMPLETAR], replica el Presidente en el sentido de [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], de local núm. [Nº], se opone por considerar que

Estudiadas estas cuestiones se procede a la votación con el siguiente resultado:

Votos a favor: propietarios, [COMPLETAR] % de cuotas de participación:

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del [COMPLETAR] %.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del [COMPLETAR] %.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del [COMPLETAR] %.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del [COMPLETAR] %.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del [COMPLETAR] %.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del [COMPLETAR] %.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del [COMPLETAR] %.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del [COMPLETAR] %.

Votos en contra: propietarios, [COMPLETAR] % de cuotas de participación:

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del [COMPLETAR] %.

D./Dña. [NOMBRE Y APELLIDOS], local [COMPLETAR], con coeficiente de participación del [COMPLETAR] %.

Se aprueba la realización de la obra de [COMPLETAR] en atención al resultado anterior: Votos favorables que representan un [COMPLETAR] % de los propietarios y un [COMPLETAR] % de las cuotas de participación.

D./Dña. [NOMBRE Y APELLIDOS] salva su voto a los efectos de una posible impugnación ante el Tribunal.

3.º

4.ºEn el apartado ruegos y preguntas se expuso por D./Dña. [NOMBRE Y APELLIDOS] lo siguiente [COMPLETAR]

No habiendo más asuntos que tratar se dio por terminada la reunión a las [Nº] horas, firmando este acta Presidente y Secretario.

Firmado:

========================================================================
