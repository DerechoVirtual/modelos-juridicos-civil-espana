---
name: acta-aprobacion-obras-derrama-extraordinaria-1441
description: "Redacta el escrito «Acta de aprobación de obras y derrama extraordinaria» (formulario 1441 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acta de aprobación de obras y derrama extraordinaria

> Formulario 1441 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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

- [ ] HORA (2 veces)
- [ ] DESCRIBIR
- [ ] NOMBRE Y APELLIDOS (49 veces)
- [ ] IMPORTE (18 veces)
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, de los pisos y»; «…, piso»; «…, local»

## Elecciones que hay que hacer

- Siguiente orden del día

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

### Formulario 1441 · Acta de aprobación de obras y derrama extraordinaria

- Año del modelo: 2013
- Revisión 17-11-2026: 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 52 campos de relleno marcados en blanco; 21 huecos del original que se habían perdido sin marca, marcados (HORA, IMPORTE, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En la ciudad de a las [HORA] horas del día de de se reunieron los propietarios que a continuación se indicarán, en en en Junta Extraordinaria de la Comunidad de Propietarios situada en la C/ n.º previa convocatoria efectuada por su Presidente el día con el orden del día siguiente:

1.º Lectura y votación para la aprobación del acta de la Junta anterior.

2.º Exposición de la necesidad de obras en elementos comunes consistentes en [DESCRIBIR], según informe de y votación sobre la realización de éstas.

3.º Presentación de presupuestos para la ejecución de estas obras y elección de uno de ellos, en caso de haberse aprobado la obra.

4.º Exposición del estado actual de las cuentas, de la forma de pago a quienes realicen la obra y de la necesidad de adoptar una derrama extraordinaria en la forma que se propone en documento anexo.

Votación de la aprobación o no de la derrama extraordinaria.

5.º Ruegos y preguntas.

A esta reunión asistieron los siguientes propietarios:

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], local, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], local, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS], de los pisos y [COMPLETAR], con coeficientes de participación del y % respectivamente, son válidamente representados en la Junta por D./Dña. [NOMBRE Y APELLIDOS], en virtud de apoderamiento que se une a esta acta.

Se hace constar que el comunero D./Dña. [NOMBRE Y APELLIDOS], del piso, por no encontrarse al corriente del pago de las cuotas de Comunidad al adeudar euros por cuotas impagadas, sin que en esta fecha conste la liquidación de la deuda o la consignación de la cantidad, se encuentra privado del derecho de voto, aunque podrá participar en las deliberaciones de todos los asuntos a tratar. D./Dña. [NOMBRE Y APELLIDOS], que figuraba como moroso en la convocatoria a esta Junta, ha procedido a ponerse al día en el pago de cuotas, razón por la cual podrá participar con voz y voto en las deliberaciones.

A pesar de haber sido citados y constar la recepción de la carta, no asisten a la reunión:

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del %.

D./Dña. [NOMBRE Y APELLIDOS], local [COMPLETAR], con coeficiente de participación del %.

A estas personas se les remitirá copia de esta acta que incluye los acuerdos adoptados a efectos de alcanzar la mayoría necesaria para su aprobación o para que puedan impugnar éstos si no estuvieran de acuerdo con su contenido o forma.

Preside la reunión D./Dña. [NOMBRE Y APELLIDOS] y actúa como Secretario D./Dña. [NOMBRE Y APELLIDOS]

DELIBERACIONES Y ACUERDOS

DELIBERACIONES Y ACUERDOS:

El acta de la Junta anterior se aprobó por unanimidad de los asistentes.

Por parte del Presidente se pasa a exponer el informe emitido por D./Dña. [NOMBRE Y APELLIDOS], con título de sobre la de realizar obras de en los elementos comunes de.

Por parte de D./Dña. [NOMBRE Y APELLIDOS] se expone que considera que no son obras necesarias y que, en consecuencia, los propietarios que voten en contra no estarán obligados a participar en los gastos que ocasionen.

D./Dña. [NOMBRE Y APELLIDOS] propone que la obra se realice de otra manera, en concreto, lo que, según él, supondría una reducción considerable de su importe. Contesta el Presidente afirmando que.

Finalmente se procede a la votación de la propuesta con el siguiente resultado:

Propietarios que votaron a favor y cuota de participación que representan:

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], local, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], local, con coeficiente de participación del%.

Propietarios que votaron en contra y cuota de participación que representan:

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

Se aprueba la realización de la obra por la Comunidad con el voto favorable de propietarios que representan el % de las cuotas de participación.

Aprobada así la realización de la obra se procede al estudio de presupuestos y elección de contratista para la ejecución de la obra.

D./Dña. [NOMBRE Y APELLIDOS] pregunta sobre y el Presidente contesta.

Se procede al voto de las propuestas:

A favor del presupuesto de votan:

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], local, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], local, con coeficiente de participación del%.

En contra del presupuesto de votan:

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

En consecuencia se aprueba la elección del presupuesto de por importe de [IMPORTE] euros, delegando en el Presidente la firma del contrato definitivo en el que deberá incluir la condición propuesta por D./Dña. [NOMBRE Y APELLIDOS] de.

El Secretario de la Comunidad hace constar que el estado de cuentas actual no permite hacer frente a esos gastos y propone la creación de una derrama extraordinaria durante meses para cubrir la cantidad de [IMPORTE] euros que corresponde pagar.

D./Dña. [NOMBRE Y APELLIDOS] propone solicitar un préstamo a una entidad bancaria y D./Dña. [NOMBRE Y APELLIDOS] replica diciendo que.

D./Dña. [NOMBRE Y APELLIDOS] expone la posibilidad de conseguir subvención por parte de para la ejecución de la obra. El Presidente queda encargado de hacer las consultas oportunas, obligándose a dar cuenta de sus gestiones en junta que se convoque al efecto.

Se somete a votación la derrama extraordinaria que a continuación se expresa:

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%. Le corresponde abonar un total de [IMPORTE] euros dividido en cuotas mensuales a razón de [IMPORTE] euros/cuota.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%. Le corresponde abonar un total de [IMPORTE] euros dividido en cuotas mensuales a razón de [IMPORTE] euros/cuota.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%. Le corresponde abonar un total de [IMPORTE] euros dividido en cuotas mensuales a razón de [IMPORTE] euros/cuota.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%. Le corresponde abonar un total de [IMPORTE] euros dividido en cuotas mensuales a razón de [IMPORTE] euros/cuota.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%. Le corresponde abonar un total de [IMPORTE] euros dividido en cuotas mensuales a razón de [IMPORTE] euros/cuota.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%. Le corresponde abonar un total de [IMPORTE] euros dividido en cuotas mensuales a razón de [IMPORTE] euros/cuota.

D./Dña. [NOMBRE Y APELLIDOS], local, con coeficiente de participación del%. Le corresponde abonar un total de [IMPORTE] euros dividido en cuotas mensuales a razón de [IMPORTE] euros/cuota.

D./Dña. [NOMBRE Y APELLIDOS], local, con coeficiente de participación del%. Le corresponde abonar un total de [IMPORTE] euros dividido en cuotas mensuales a razón de [IMPORTE] euros/cuota.

El acuerdo sobre adopción de las derramas expresadas es aprobado por votos a favor que representan un% de las cuotas de participación.

Votos a favor:

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], local, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], local, con coeficiente de participación del%.

Votos en contra:

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%. Esta persona se reserva expresamente el derecho de impugnar este acuerdo.

En el apartado ruegos y preguntas.

[ELEGIR: Siguiente orden del día]

No habiendo más asuntos que tratar se dio por terminada la reunión a las [HORA] horas, firmando esta acta Presidente y Secretario.

Firmado:

========================================================================
