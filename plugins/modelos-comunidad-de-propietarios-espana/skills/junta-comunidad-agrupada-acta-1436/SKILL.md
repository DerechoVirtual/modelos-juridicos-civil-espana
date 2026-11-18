---
name: junta-comunidad-agrupada-acta-1436
description: "Redacta el escrito «Junta de comunidad agrupada: acta» (formulario 1436 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Junta de comunidad agrupada: acta

> Formulario 1436 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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

- [ ] Nº (2 veces)
- [ ] NOMBRE Y APELLIDOS (9 veces)
- [ ] FECHA
- [ ] IMPORTE
- [ ] Otros 36 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…En»; «…a las [Nº] horas, se reúne en»; «…horas, se reúne en [COMPLETAR] en»; «…e Comunidades de Propietarios denominada»; «…ación en la zona de de la siguiente obra»; «…, de la Comunidad»; «…, con coeficiente de participación del»; «…, de la Comunidad»; «…, de la Comunidad»; «…, de la Comunidad»; «…, con coeficiente de participación del»; «… al Presidente a contratar a esa persona»; …

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

### Formulario 1436 · Junta de comunidad agrupada: acta

- Año del modelo: 2013
- Revisión 17-11-2026: 48 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [COMPLETAR] a las [Nº] horas, se reúne en [COMPLETAR] en [COMPLETAR] convocatoria la Junta General de la Agrupación de Comunidades de Propietarios denominada [COMPLETAR], previa convocatoria en forma a todos los presidentes de las Comunidades que la componen con el siguiente orden del día:

Punto primero: Lectura y aprobación del acta de la Junta anterior.

Punto segundo: Contratación para la temporada de verano de persona cualificada para el servicio de socorrista de la piscina.

Punto tercero: Realización en la zona de de la siguiente obra [COMPLETAR], en su caso, aceptación de presupuesto de entre los que se remiten con la presente convocatoria y autorización al Presidente para que firme los contratos oportunos.

Punto cuarto: En el caso de haberse aceptado el punto anterior, se someterá a votación la contribución a los gastos de la obra mediante la aprobación, en su caso, de derrama extraordinaria de cada Comunidad de la siguiente forma:

Punto quinto: Ruegos y preguntas:

A la Junta asisten todos los presidentes de las Comunidades:

D./Dña. [NOMBRE Y APELLIDOS], de la Comunidad [COMPLETAR], con coeficiente de participación del [COMPLETAR] %.

D./Dña. [NOMBRE Y APELLIDOS], de la Comunidad [COMPLETAR], con coeficiente de participación del %.

D./Dña. [NOMBRE Y APELLIDOS], de la Comunidad [COMPLETAR] con coeficiente de participación del %.

D./Dña. [NOMBRE Y APELLIDOS], de la Comunidad [COMPLETAR], con coeficiente de participación del [COMPLETAR] %.

Preside la Junta el Presidente D./Dña. [NOMBRE Y APELLIDOS] y actúa como Secretario D./Dña. [NOMBRE Y APELLIDOS]

El Presidente da inicio a la Junta en la que se adoptan los siguientes acuerdos:

1.º Lectura y aprobación del acta de la Junta anterior. Se aprueba por unanimidad el acta de la Junta de Agrupación de Comunidades de fecha [FECHA].

2.º Contratación para la temporada de verano de persona cualificada para el servicio de socorrista de la piscina.

El Presidente expone la propuesta ante la inminencia de la apertura de esa instalación común y la repentina comunicación de la persona que en los últimos años que ha ocupado ese cargo de que este año no renovará contrato.

Por D./Dña. [NOMBRE Y APELLIDOS] se expone que D./Dña. [NOMBRE Y APELLIDOS] estaría dispuesto a realizar esa función. Por unanimidad de los asistentes se acuerda autorizar al Presidente a contratar a esa persona [COMPLETAR] con las mismas condiciones de años anteriores salvo la elevación del sueldo a [IMPORTE] euros mensuales. En el caso de que no aceptara se le autoriza a acudir a una empresa de contratación o a la oficina pública de empleo.

3.º Realización en la zona de [COMPLETAR] de la siguiente obra [COMPLETAR], en su caso, aceptación de presupuesto de entre los que se remiten con la presente convocatoria y autorización al Presidente para que firme los contratos oportunos:

La naturaleza de la obra exigía el previo acuerdo de cada Comunidad. Por parte de los Presidentes de cada una de ellas se expone el resultado de la votación en cada Junta de Propietarios que fue el siguiente:

Comunidad de [COMPLETAR]: votos a favor, que representan el [COMPLETAR] % de las cuotas de participación y votos en contra que representan el [COMPLETAR] % de las cuotas de participación. Se aprueba.

Comunidad de [COMPLETAR]: votos a favor, que representan el [COMPLETAR] % de las cuotas de participación y votos en contra que representan el [COMPLETAR] % de las cuotas de participación. Se aprueba.

Comunidad de [COMPLETAR]: votos a favor, que representan el [COMPLETAR] % de las cuotas de participación y votos en contra que representan el [COMPLETAR] % de las cuotas de participación. Se aprueba.

Comunidad de [COMPLETAR]: votos a favor, que representan el [COMPLETAR] % de las cuotas de participación y votos en contra que representan el [COMPLETAR] % de las cuotas de participación. Se aprueba.

En atención a este resultado se somete a votación la propuesta de la ejecución de la obra que se aprueba por [COMPLETAR] votos a favor de los Presidentes de las Comunidades de [COMPLETAR] que representan una cuota de participación en la agrupación del [COMPLETAR] % y [COMPLETAR] votos en contra que representan una cuota de participación en la agrupación del [COMPLETAR] %.

En cuanto al presupuesto a adoptar, por parte del Presidente [COMPLETAR] de se solicita que se someta nuevamente a cada Junta de Propietarios la cuestión de la elección del más ventajoso, así como la determinación de la derrama extraordinaria que se derivará del resultado.

El presidente de [COMPLETAR] replica que [COMPLETAR] y finalmente se decide por unanimidad que el presupuesto y la derrama se acordará por [COMPLETAR].

4.º En el apartado ruegos y preguntas se expuso por D./Dña. [NOMBRE Y APELLIDOS] lo siguiente [COMPLETAR]

No habiendo más asuntos que tratar se dio por terminada la reunión a las [Nº] horas, firmando este acta Presidente y Secretario.

Firmado:

========================================================================
