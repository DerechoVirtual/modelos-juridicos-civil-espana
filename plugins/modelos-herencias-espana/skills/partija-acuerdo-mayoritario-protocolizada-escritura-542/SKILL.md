---
name: partija-acuerdo-mayoritario-protocolizada-escritura-542
description: "Redacta el escrito «Partija por acuerdo mayoritario protocolizada en escritura (Galicia)» (formulario 542 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Partija por acuerdo mayoritario protocolizada en escritura (Galicia)

> Formulario 0542 del plugin **Sucesiones** · revisado el 17-11-2026.

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

- [ ] NÚMERO (9 veces)
- [ ] ÓRGANO
- [ ] FECHA
- [ ] NOMBRE Y APELLIDOS
- [ ] Otros 39 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…En»; «…En [COMPLETAR], mi residencia, a»; «…egio Notarial de Galicia, Comparecen Don»; «…, mayor de edad, estado civil, vecino de»; «…; con D.N.I. número [NÚMERO]. Don»; «…, mayor de edad, estado civil, vecino de»; «…; con D.N.I. número [NÚMERO]. Don»; «…, mayor de edad, estado civil, vecino de»; «…; con D.N.I. número [NÚMERO]. Don»; «…, mayor de edad, estado civil, vecino de»; «…; con D.N.I. número [NÚMERO]. Don»; «…, mayor de edad, estado civil, vecino de»; …

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

### Formulario 0542 · Partija por acuerdo mayoritario protocolizada en escritura (Galicia)

- Año del modelo: 2016
- Revisión 17-11-2026: 51 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Número [NÚMERO]

En [COMPLETAR], mi residencia, a [COMPLETAR]

Ante mí, Notario del Ilustre Colegio Notarial de Galicia,

 Comparecen

Don [COMPLETAR], mayor de edad, estado civil, vecino de [COMPLETAR]; con D.N.I. número [NÚMERO].

Don [COMPLETAR], mayor de edad, estado civil, vecino de [COMPLETAR]; con D.N.I. número [NÚMERO].

Don [COMPLETAR], mayor de edad, estado civil, vecino de [COMPLETAR]; con D.N.I. número [NÚMERO].

Don [COMPLETAR], mayor de edad, estado civil, vecino de [COMPLETAR]; con D.N.I. número [NÚMERO].

Don [COMPLETAR], mayor de edad, estado civil, vecino de [COMPLETAR]; con D.N.I. número [NÚMERO].

Intervienen todos en su propio nombre y derecho; los cuatro primeros en calidad de herederos y el último en calidad de contador-partidor designado a efectos de partir la herencia a que se contrae esta escritura

Les identifico por sus reseñados documentos y, tienen, a mi juicio, capacidad suficiente para esta escritura de PROTOCOLIZACIÓN DE CUADERNO DE PARTIJA DE HERENCIA POR ACUERDO MAYORITARIO, y, al efecto,

Exponen

1. Que el causante [ÓRGANO], que poseía vecindad civil gallega falleció en [COMPLETAR], el [COMPLETAR] en estado de viudo de su matrimonio con [COMPLETAR] y del que nacieron y viven cinco hijos llamados, [COMPLETAR], [COMPLETAR] y [COMPLETAR].

2. A su fallecimiento, dicho causante había otorgado testamento único y válido ante el Notario de [COMPLETAR], con [COMPLETAR], y en el que instituía como únicos y universales herederos a sus cinco citados hijos, [COMPLETAR], [COMPLETAR] y [COMPLETAR].

3. En el citado testamento no efectuó nombramiento alguno de contador-partidor.

Se une a este cuaderno certificación de la defunción del causante, copia autorizada de su testamento y certificación del Registro General de Actos de Última Voluntad.

4. Tras intentar, de manera infructuosa ?según declaran los cuatro otorgantes reseñados en primer lugar?, efectuar la partición por coherederos junto con [COMPLETAR], decidieron realizar la partija por acuerdo mayoritario conforme a las previsiones contenidas en el artículo 295 y siguientes de la Ley de Derecho Civil de Galicia, pues entre los promoventes ostentan más de la mitad del haber hereditario y así se lo comunicaron en su domicilio por medio de requerimiento en acta notarial realizado por mí, el [COMPLETAR], número [NÚMERO] de protocolo.

(han de transcurrir 30 días hábiles desde la última publicación o notificación y 60 desde el requerimiento inicial al notario; cfr. art. 298 LDCG)

5. El día [FECHA], y no habiéndose propuesto ningún contador-partidor por los demás partícipes en la herencia, se efectuó el sorteo ante mí, número [NÚMERO] de protocolo, cumpliéndose los requisitos y plazos legalmente establecidos al efecto, y se designó como contador-partidor a [COMPLETAR].

6. El contador-partidor efectuó el inventario de los bienes de [COMPLETAR] conforme a los documentos aportados por los interesados y sin necesidad de asesoramiento pericial. Ante la imposibilidad de formar lotes homogéneos, dada la cantidad y calidad de los bienes ?lo que me acredita y justifica en el cuaderno particional anejo? propuso el proyecto de partición que fue aprobado por los coherederos otorgantes de esta escritura por medio de documentos escritos ?que me acreditan y se adjuntan a esta matriz? y que se protocolizan por medio de esta escritura.

Y a tal efecto

Otorgan

[NOMBRE Y APELLIDOS], en calidad de contador-partidor de la herencia de [COMPLETAR], otorga la presente escritura de protocolización de cuaderno particional.

Los herederos de [COMPLETAR], arriba señalados,, [COMPLETAR] y [COMPLETAR], aprueban el proyecto de partición elaborado por el contador-partidor [COMPLETAR], nombrado por medio de acta notarial de [COMPLETAR], número [NÚMERO] de protocolo, al corresponderles en conjunto más de las tres cuartas partes de la herencia, tal y como exige la Ley de Derecho Civil de Galicia, y solicitan sea notificada al heredero no partícipe de esta escritura [COMPLETAR] en su domicilio de [COMPLETAR].

(si fuera desconocido el domicilio, hay que notificar por medio de edictos conforme a los artículos 295 y 296 LDCG, si bien debe entenderse artículos 296 y 297 LDCG, habiendo una errata en el artículo 307 LDCG)

Hago a los requirentes las reservas y advertencias legales y fiscales.

De acuerdo con lo establecido en la Ley, los comparecientes quedan informados y aceptan la incorporación de sus datos a los ficheros automatizados existentes en la Notaría, que se conservan en la misma con carácter confidencial, bajo el principio del secreto de protocolo, sin perjuicio de las remisiones de obligado cumplimiento legal.

Así lo dicen y otorgan los comparecientes cuyo consentimiento, libremente prestado, se adecua a la legalidad y a su voluntad debidamente informada.

Les advierto de su derecho a leer por sí esta escritura, cuyo ejercicio permito; eligen hacer uso de él y enterados de su contenido, según me indican, se ratifican y firman.

Y yo, el Notario, DOY FE:

a) De haber identificado a los comparecientes por medio de sus documentos identificativos, reseñados en la comparecencia, que me han sido exhibidos.

b) De que los comparecientes, a mi juicio, tienen capacidad y están legitimados para el presente otorgamiento.

c) De que el consentimiento de los otorgantes ha sido libremente prestado.

d) De que el otorgamiento se adecua a la legalidad y a la voluntad libre y debidamente informada de los comparecientes.

e) Y de quedar extendida en [COMPLETAR] folios de papel timbrado para uso exclusivo notarial, de la serie [COMPLETAR] números [COMPLETAR] y los [COMPLETAR] en número correlativo; yo, el Notario, DOY FE.

========================================================================
