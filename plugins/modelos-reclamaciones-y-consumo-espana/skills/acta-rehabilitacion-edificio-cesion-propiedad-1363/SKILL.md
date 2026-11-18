---
name: acta-rehabilitacion-edificio-cesion-propiedad-1363
description: "Redacta el escrito «Acta de rehabilitación del edificio con cesión de propiedad al contratista» (formulario 1363 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acta de rehabilitación del edificio con cesión de propiedad al contratista

> Formulario 1363 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] Nº (2 veces)
- [ ] CALLE
- [ ] NÚMERO (3 veces)
- [ ] FECHA
- [ ] NOMBRE Y APELLIDOS (14 veces)
- [ ] IMPORTE
- [ ] DESCRIBIR
- [ ] ÓRGANO
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…En»; «…(ciudad) a las [Nº] horas, se reúne en»; «…horas, se reúne en [COMPLETAR] en»; «…del edificio elaborado por el arquitecto»; «…a la ejecución de la obra por la empresa»; «… local del que es propietaria situado en»; «…, piso»; «…, piso»; «…, piso»; «…, piso»; «…munidad, por adeudar las de los meses de»; «…n del edificio. Por todos los asistentes»; …

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

### Formulario 1363 · Acta de rehabilitación del edificio con cesión de propiedad al contratista

- Año del modelo: 2013
- Revisión 17-11-2026: 38 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [COMPLETAR] (ciudad) a las [Nº] horas, se reúne en [COMPLETAR] en [COMPLETAR] convocatoria la Junta General extraordinaria de la Comunidad de Propietarios de la c/ [CALLE] n.º [NÚMERO], previa convocatoria en forma a todos sus integrantes con las siguientes cuestiones a tratar en el orden del día, a saber:

1.º Lectura y aprobación, en su caso, del acta de la Junta anterior de fecha [FECHA].

2.º Estudio y aprobación en su caso del proyecto de rehabilitación del edificio elaborado por el arquitecto [COMPLETAR] que ha estado a disposición de los comuneros en la oficina del Administrador.

3.º Estudio y aprobación en su caso de la propuesta de convenio para la ejecución de la obra por la empresa [COMPLETAR] con ejecución a su costa y compensación mediante cesión por la Comunidad del local del que es propietaria situado en [COMPLETAR].

4.º Ruegos y preguntas.

A la Junta asisten los siguientes propietarios:

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], local n.º [NÚMERO], con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], del piso y con coeficiente de participación del% y D./Dña. [NOMBRE Y APELLIDOS], del piso y con coeficiente de participación del%, otorgaron apoderamiento para comparecer y votar en su nombre en esta Junta a D./Dña. [NOMBRE Y APELLIDOS], que los representa.

Se hace constar que D./Dña. [NOMBRE Y APELLIDOS], del piso y coeficiente de participación del%, no se encuentra al corriente del pago de las cuotas de la Comunidad, por adeudar las de los meses de [COMPLETAR], que ascienden a [IMPORTE] euros. Al no haber procedido antes de la reunión al pago, a la consignación judicial o notarial o a la impugnación judicial de las cuotas, su persona y cuota de participación no son computadas a efectos de alcanzar las mayorías legales.

Se hace constar, igualmente, que D./Dña. [NOMBRE Y APELLIDOS] ha procedido a ponerse al día en el pago de cuotas de comunidad, razón por la cual podrá participar con voz y voto en las deliberaciones.

Preside la Junta el Presidente D./Dña. [NOMBRE Y APELLIDOS] y actúa como Secretario el Administrador D./Dña. [NOMBRE Y APELLIDOS]

Da comienzo la deliberación y se desarrolla la reunión de la siguiente manera:

1.º Lectura y aprobación del acta de la Junta anterior:

Se aprueba por todos los asistentes.

2.º Proyecto de rehabilitación del edificio.

Por todos los asistentes [COMPLETAR] que representan una cuota de participación de% se alcanza el siguiente acuerdo:

La realización en [COMPLETAR] de la obra consistente en [DESCRIBIR], aprobando el proyecto de fecha elaborado por D./Dña. [NOMBRE Y APELLIDOS] que se une a esta acta como documento n.º [NÚMERO], autorizando a D./Dña. [NOMBRE Y APELLIDOS] para que en nombre de la Comunidad realice las gestiones necesarias ante [ÓRGANO] para la legalización del proyecto y la obra y la consecución de las preceptivas licencias. La obra no se llevará a cabo hasta que se concedan todos los permisos oportunos.

Se acuerda igualmente respecto a los propietarios ausentes notificar el presente acuerdo a los efectos del artículo 17.1 de la Ley de Propiedad Horizontal.

3.º Encargo de la obra a la empresa y pago por cesión de propiedad de local

Por todos los asistentes [COMPLETAR] que representan una cuota de participación de% se aprueba la propuesta, facultando al presidente a realizar las gestiones oportunas para la firma del contrato y las actuaciones notariales y registrales precisas.

Se acuerda igualmente respecto a los propietarios ausentes notificar el presente acuerdo a los efectos del artículo 17.1 de la Ley de Propiedad Horizontal.

4.º Ruegos y preguntas:

No se presentan.

No habiendo más asuntos que tratar se da por terminada la reunión a las [Nº] horas, que se documenta en la presente acta que firman los Sres. Presidente y Secretario.

Firmado:

========================================================================
