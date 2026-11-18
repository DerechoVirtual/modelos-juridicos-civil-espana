---
name: cesion-derecho-uso-habitacion-243
description: "Redacta el escrito «Cesión del derecho de uso y habitación» (formulario 243 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Cesión del derecho de uso y habitación

> Formulario 0243 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] FECHA
- [ ] ESTADO CIVIL (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] Nº
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, a [FECHA]. REUNIDOS De una parte: Don»; «…, vecino de»; «…, vecino de [COMPLETAR], domiciliado en»; «… lo sucesivo "EL CEDENTE". De otra: Doña»; «…, vecina de»; «…, vecina de [COMPLETAR], domiciliada en»; «…scrita en el Registro de la Propiedad de»; «…, al»; «…, con una superficie aproximada de»; «…ENTE, con numero de referencia Catastral»; «…, en»

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

### Formulario 0243 · Cesión del derecho de uso y habitación

- Año del modelo: 2020
- Revisión 17-11-2026: 21 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Contrato privado de cesión gratuita de derecho de uso y habitación.

Formulario adaptado a la reforma de la LO 1/2025.

En [LUGAR], a [FECHA].

REUNIDOS

De una parte:

Don [COMPLETAR], mayor de edad, de estado civil [ESTADO CIVIL], vecino de [COMPLETAR], domiciliado en [COMPLETAR], con documento nacional de identidad número [NÚMERO], en lo sucesivo "EL CEDENTE".

De otra:

Doña [COMPLETAR], mayor de edad, de estado civil [ESTADO CIVIL], vecina de [COMPLETAR], domiciliada en [COMPLETAR], con documento nacional de identidad número [NÚMERO], en lo sucesivo "EL CESIONARIO".

INTERVIENEN

Ambas en su propio nombre y representación, reconociéndose mutua y plena capacidad legal de obrar y de obligarse para este acto y a tal efecto, libremente y de común acuerdo,

EXPONEN

I.- Que EL CEDENTE es titular de la finca sita en [LOCALIDAD], inscrita en el Registro de la Propiedad de [COMPLETAR], al [COMPLETAR], con una superficie aproximada de [COMPLETAR] metros cuadrados de planta. Dicha propiedad se encuentra catastrada a nombre de EL CEDENTE, con numero de referencia Catastral [COMPLETAR], según se justifica mediante certificado que se adjunta al presente como Anexo núm. I.

II.- Que La finca se halla libre de arrendatarios y ocupantes.

III.- Que EL CESIONARIO está interesado en adquirir el uso como derecho de habitación sobre la finca mencionada.

IV.- Que en vista de lo anterior, ambas partes de común acuerdo llevan a efecto el presente contrato con arreglo a las siguientes:

CLÁUSULAS

Primera.- Que EL CEDENTE permite y autoriza a EL CESIONARIO, el uso de la finca descrita para su uso personal e intransferible.

Segunda.- Que el único uso permitido será como vivienda, no pudiendo darle ningún otro uso diferente, prohibiéndose expresamente la cesión total o parcial a tercero.

Tercera.- Que no se fija contraprestación alguna por la cesión del uso de la finca.

Cuarta.- Que el mantenimiento y cuidados adecuados de la finca corren a cargo de EL CESIONARIO, por ocuparla en su totalidad, pudiendo verificar las cedentes el correcto cumplimiento visitando el inmueble, con un preaviso de dos días.

Quinta.- Que en caso de que el uso por EL CESIONARIO cree o provoque daños a terceros será responsabilidad de éste y tendrá que responder de los daños que se le reclamen a EL CEDENTE, extinguiéndose en este caso el derecho de habitación.

Sexta.- Que en caso de sanción administrativa por incumplimiento de la normativa local, autonómica, nacional o comunitaria durante el uso, serán responsables del cumplimiento de la sanción o condiciones impuestas por la Administración Pública correspondiente, extinguiéndose en este caso igualmente el derecho de habitación.

Séptima.- Que la duración del presente contrato privado será de [Nº] años prorrogables, sin derecho a adquisición preferente sobre la finca por EL CESIONARIO. La no ocupación de la vivienda por más de tres meses consecutivos o seis meses discontinuos dará lugar a la extinción del derecho de habitación finalizando la cesión.

Octava.- Que se establece un plazo de preaviso de 20 días, entre las partes, para cuando EL CESIONARIO decida terminar con el uso de la finca o EL CEDENTE decidan recuperar el uso total de su propiedad.

Novena.- Todos los gastos e impuestos que se originen como consecuencia de la formalización, cumplimiento o extinción del presente contrato y de las obligaciones que de él se deriven serán de cargo de EL CESIONARIO/EL CEDENTE.

Igualmente, los gastos judiciales que se ocasionen por incumplimiento del presente contrato serán por cuenta de la parte incumplidora, incluidos honorarios del Procurador y Abogado aunque sus intervenciones no fueran preceptivas.

Décima.- Para cuantas cuestiones o divergencias pudieran suscitarse en relación con el presente contrato, ambas partes establecen someterse a los Tribunales de [LOCALIDAD], en [COMPLETAR], renunciando expresamente a su fuero propio si lo tuvieran.

El presente contrato tiene exclusivamente carácter civil y se regirá por sus propias cláusulas, y en lo en ellas no dispuesto, por lo previsto en el Código Civil y, demás leyes especiales.

NOTIFICACIONES

Toda notificación que se efectúe entre las partes se hará por escrito y será entregada personalmente o de cualquier otra forma que certifique la recepción por la parte notificada en los respectivos domicilios indicados en el encabezamiento de este Contrato.

Cualquier cambio de domicilio de una de las partes deberá ser notificado a la otra de forma inmediata y por un medio que garantice la recepción del mensaje.

GENERALIDADES

El presente contrato anula y reemplaza cualquier contrato o acuerdo anterior entre las partes con el mismo objeto y sólo podrá ser modificado por un nuevo acuerdo firmado por ambas partes.

Si alguna de las cláusulas del presente contrato fuere declarada nula o inaplicable, dicha cláusula se considerará excluida del contrato, sin que implique la nulidad del mismo. En este caso las partes harán cuanto esté a su alcance para encontrar una solución equivalente que sea válida y que refleje debidamente sus intenciones.

Y en prueba de conformidad de cuanto antecede, las partes firman y rubrican el presente contrato al que se incorporan el anexo expresado como parte integrante de su contenido, a un solo efecto y por duplicado ejemplar, en todas sus hojas, en el lugar y fecha del encabezamiento.

Firma del cedente	Firma del cesionario
D./Dña. [NOMBRE Y APELLIDOS] 	D./Dña. [NOMBRE Y APELLIDOS]
