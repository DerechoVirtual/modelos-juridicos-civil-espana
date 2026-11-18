---
name: apelacion-propiedad-horizontal-juicio-ordinario-verbal-1352
description: "Redacta el escrito «Apelación en propiedad horizontal (juicio ordinario o verbal)» (formulario 1352 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Apelación en propiedad horizontal (juicio ordinario o verbal)

> Formulario 1352 del plugin **Recursos civiles** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.

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

- [ ] NÚMERO (5 veces)
- [ ] ACTO O RESOLUCIÓN
- [ ] FECHA (3 veces)
- [ ] IMPORTE (2 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] DESCRIBIR
- [ ] ÓRGANO
- [ ] LUGAR
- [ ] Otros 19 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Juicio»; «…CIÓN CIVIL DE LA AUDIENCIA PROVINCIAL DE»; «…permiten los arts. 455.1 y 458 de la LEC»; «…s Alegaciones La resolución recurrida es»; «…o una defectuosa valoración de la prueba»; «…omprobar en el minuto de la grabación de»; «…expresamente reconoció que»; «…onocimiento de los hechos las siguientes»; «…os razonamientos de la demanda relativos»; «…antiene que en realidad lo que existe es»; «…de la norma es claro al respecto, ya que»; «…e dicte deberá declarar sobre las costas»; …

## Párrafos opcionales (7)

Inclúyelos solo si encajan en los hechos:

- Obligación abono…
- Condena en costas…
- Desestimación del pago…
- OTROSÍ I DIGO: Que con el presente escrito acompaño justificante de ingreso en la cuenta de depósitos y consig…
- OTROSÍ II DIGO: Que a los efectos previstos en el apartado 4 del art. 449 de la LEC [COMPLETAR], manifiesto qu…
- NUEVAMENTE SUPLICO A LA SALA: Tenga por formulada la anterior manifestación y por acreditada [COMPLETAR] en la…
- NUEVAMENTE SUPLICO: Que tenga por efectuados los anteriores pedimentos y por cumplimentados estos requisitos e…

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 455.1 y 458 de la LEC
- art. 460 de la LEC
- art. 449 de la LEC
- art. 449.4 de la LEC

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

### Formulario 1352 · Apelación en propiedad horizontal (juicio ordinario o verbal)

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 7 párrafos opcionales señalados; 33 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio [COMPLETAR], n.º [NÚMERO]

A LA SECCIÓN CIVIL DE LA AUDIENCIA PROVINCIAL DE [COMPLETAR]

[NOTA DE REVISIÓN (comprobar): La AP no tiene «Sección Civil» como denominación legal: se cita la Sección por su número (p. ej. «A LA SECCIÓN [ ] DE LA AUDIENCIA PROVINCIAL DE [ ]»). Fuente: LOPJ arts. 80 y 82 (Audiencia Provincial, sin cambio de denominación).]

Que según permiten los arts. 455.1 y 458 de la LEC [COMPLETAR], dentro del plazo legal de veinte días concedido a esta parte a tal efecto, mediante el presente escrito interpongo el recurso de apelación contra [ACTO O RESOLUCIÓN] n.º [NÚMERO] de fecha [FECHA] dictada en el presente procedimiento en atención a las siguientes

Alegaciones

La resolución recurrida es [COMPLETAR] n.º [NÚMERO] de fecha Dictada en el presente procedimiento.

Los pronunciamientos de la resolución recurrida que se impugnan mediante este recurso son los siguientes

Pronunciamientos

[OPCIONAL — incluir si procede]

Obligación abono

– La declaración de la obligación del demandado a abonar la cantidad de [IMPORTE] Euros por cuotas pendientes de la comunidad

[OPCIONAL — incluir si procede]

Condena en costas

– La condena en costas a esta parte

[OPCIONAL — incluir si procede]

Desestimación del pago

– La desestimación de la pretensión del actor de pago por el demandado de la cantidad de [IMPORTE] euros.

Defectuosa valoración de la prueba

Entiende esta parte, dicho sea con los debidos respetos y en términos de defensa de los intereses de mi representado, que ha existido una defectuosa valoración de la prueba [COMPLETAR], puesto que según se puede comprobar en el minuto de la grabación de [COMPLETAR], el testigo D./Dña. [NOMBRE Y APELLIDOS] expresamente reconoció que [COMPLETAR] y dio como razones de conocimiento de los hechos las siguientes [COMPLETAR] Quiere esto decir que nuestros razonamientos de la demanda relativos [COMPLETAR] a son ciertos y todas las razones dadas por el demandado en su contestación para desvirtuarlos no pueden ser tenido en cuenta.

Base del fallo de la sentencia

Se basa el fallo de la sentencia en la aplicación de los arts. De la Ley de Propiedad Horizontal relativos a [DESCRIBIR]. Esta parte alegó que nos encontramos ante [ÓRGANO] mientras que de contrario se mantiene que en realidad lo que existe es [COMPLETAR]. Entendemos que el espíritu de la norma es claro al respecto, ya que [COMPLETAR].

Jurisprudencia

Avala lo manifestado las siguientes resoluciones judiciales que como línea jurisprudencial aplicable al presente supuesto queremos citar:

Costas

La sentencia que se dicte deberá declarar sobre las costas [COMPLETAR].

Cuestión de nulidad

Cuando se pretenda reproducir en el recurso de apelación la cuestión de nulidad ya planteada por infracción de normas o garantías procesales se anunciará esta circunstancia, expresando: 1.º la norma infringida, 2.º la indefensión causada y 3.º la denuncia de la infracción formulada.

Prueba

Según permite el art. 460 de la LEC

Suplico

Por lo expuesto,

SUPLICO A LA SALA: Que tenga por presentado este escrito con sus copias, se sirva admitirlo y, en su virtud, dicte resolución mediante la que se tenga por interpuesto en tiempo y forma RECURSO DE APELACIÓN contra la sentencia n.º [NÚMERO] de fecha [FECHA] respecto de los pronunciamientos concretos que se dejan enunciados en el cuerpo del presente escrito, y, previo traslado a las demás partes de este escrito a los fines legales oportunos, y tras la pertinente tramitación [COMPLETAR], se dicte por la Sala sentencia mediante la que, estimando íntegramente este recurso, se revoque la resolución recurrida y se [COMPLETAR].

Es justicia que pido en [LUGAR], a [FECHA].

[OPCIONAL — incluir si procede]

OTROSÍ I DIGO: Que con el presente escrito acompaño justificante de ingreso en la cuenta de depósitos y consignaciones del Tribunal de la cantidad de 50 euros como depósito para recurrir, según exige la disposición adicional decimoquinta de la LOPJ.

[OPCIONAL — incluir si procede]

OTROSÍ II DIGO: Que a los efectos previstos en el apartado 4 del art. 449 de la LEC [COMPLETAR], manifiesto que mi representado ha procedido, con fecha de [COMPLETAR], a pagar [COMPLETAR] la cantidad líquida a que se contrae la sentencia condenatoria contra la que se interpone este recurso de apelación.

Acredito este extremo, a los efectos probatorios pertinentes, con el recibo [COMPLETAR] de la expresada cantidad que acompaño reseñado como documento n.º [NÚMERO].

[OPCIONAL — incluir si procede]

NUEVAMENTE SUPLICO A LA SALA: Tenga por formulada la anterior manifestación y por acreditada [COMPLETAR] en la cuenta del Tribunal de la cantidad líquida a que se contrae la sentencia condenatoria contra la que se prepara este recurso, teniendo por cumplido el requisito establecido por el art. 449.4 de la LEC y acuerde, en definitiva, tener por interpuesto el recurso de apelación a que se contrae el presente escrito.

[OPCIONAL — incluir si procede]

NUEVAMENTE SUPLICO: Que tenga por efectuados los anteriores pedimentos y por cumplimentados estos requisitos económicos para la formulación del recurso, por ser justicia que pido en mismo lugar y fecha.

========================================================================
