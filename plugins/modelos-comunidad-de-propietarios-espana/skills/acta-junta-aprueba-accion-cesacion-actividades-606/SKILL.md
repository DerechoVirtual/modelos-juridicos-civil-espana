---
name: acta-junta-aprueba-accion-cesacion-actividades-606
description: "Redacta el escrito «Acta de la junta que aprueba la acción de cesación por actividades prohibidas» (formulario 606 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acta de la junta que aprueba la acción de cesación por actividades prohibidas

> Formulario 0606 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (9 veces)
- [ ] NÚMERO
- [ ] Nº (2 veces)
- [ ] DESCRIBIR
- [ ] Otros 15 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, cuota de participación»; «…cuota de participación [COMPLETAR], piso»; «…, piso [COMPLETAR], letra»; «…, cuota de participación»; «…cuota de participación [COMPLETAR], piso»; «…, piso [COMPLETAR], letra»; «…, piso [COMPLETAR], letra [COMPLETAR] En»; «…, letra [COMPLETAR] En [COMPLETAR], a»; «…, y promovida dicha convocatoria por»; «…de la vivienda ubicada en este edificio»; «…an la palabra los siguientes asistentes:»; «…, que hacen constar que»; …

## Elecciones que hay que hacer

- Presidente / Presidenta
- Secretario / Secretaria
- propietario / propietaria / ocupante
- el / la

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

### Formulario 0606 · Acta de la junta que aprueba la acción de cesación por actividades prohibidas

- Año del modelo: 2016
- Revisión 17-11-2026: 7 desplegables convertidos en elección en blanco; 28 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Acta de la junta de propietarios, debidamente convocada al efecto, autorizando al presidente para el ejercicio de acción de cesación por actividades prohibidas en los estatutos, que resulten dañosas para la finca o que contravengan las disposiciones generales sobre actividades molestas, insalubres, nocivas, peligrosas o ilícitas.

ACTA

Relación de personas asistentes y personas que ostentan representación.

-
+
Añadir más párrafos iguales

D./Dña. [NOMBRE Y APELLIDOS], cuota de participación [COMPLETAR], piso [COMPLETAR], letra [COMPLETAR]

Representaciones acreditadas.

-
+
Añadir más párrafos iguales

D./Dña. [NOMBRE Y APELLIDOS], D.N.I. n.º [NÚMERO], representa a D./Dña. [NOMBRE Y APELLIDOS], cuota de participación [COMPLETAR], piso [COMPLETAR], letra [COMPLETAR]

En [COMPLETAR], a [COMPLETAR], siendo las [Nº] horas queda constituida, en primera convocatoria, la Junta Extraordinaria, actuando en calidad de [ELEGIR: Presidente / Presidenta] D./Dña. [NOMBRE Y APELLIDOS], y en calidad de [ELEGIR: Secretario / Secretaria] D./Dña. [NOMBRE Y APELLIDOS], y promovida dicha convocatoria por [COMPLETAR].

ORDEN DEL DIA

Estudio y adopción de resolución sobre el siguiente asunto:

1º.- Que D./Dña. [NOMBRE Y APELLIDOS], [ELEGIR: propietario / propietaria / ocupante] de la vivienda ubicada en este edificio [COMPLETAR], desarrolla en la misma la actividad consistente en [DESCRIBIR], catalogada y sancionada por la Ley de Propiedad Horizontal en el art. 7.2 como prohibida
2º.- Que previa petición de uno de los propietarios de este edificio, asumida como propia iniciativa por [ELEGIR: el / la]

Presidente
Presidenta
 de la comunidad, se ha requerido de forma fehaciente al infractor para que cese en las actividades mencionadas, sin obtenerse resultado alguno.
3º.- Que un conjunto de propietarios, que representan más del 25 por 100 de las cuotas de participación, han solicitado la convocatoria de la Junta de propietarios con el fin de analizar y adoptar, en su caso, la decisión de iniciar acciones judiciales contra el precitado infractor.

Puesto a discusión el único punto del orden del día, relativo al análisis y adopción, en su caso, de la decisión de iniciar acciones judiciales contra D./Dña. [NOMBRE Y APELLIDOS] por la realización de actividades prohibidas por el art. 7.2 de la Ley de Propiedad Horizontal, toman la palabra los siguientes asistentes: [COMPLETAR], que hacen constar que [COMPLETAR].

Sometido a votación, lo hacen a favor [COMPLETAR]; y en contra, [COMPLETAR].

En consecuencia, una vez realizado el cómputo de votos queda aprobada la propuesta, otorgándose la correspondiente autorización al [ELEGIR: Presidente / Presidenta] de la Comunidad para entablar contra D./Dña. [NOMBRE Y APELLIDOS] la acción de cesación prevista en el art. 7.2 de la Ley de Propiedad Horizontal.

Se hace constar que los propietarios de los pisos [COMPLETAR], al no hallarse al corriente de las deudas con la Comunidad, se encontraban privados del derecho a voto.

No habiendo otros asuntos que tratar, se levanta la sesión por [ELEGIR: el / la]

Presidente
Presidenta
 a las [Nº] horas, disponiendo se notifique el acuerdo adoptado a los propietarios en la forma dispuesta en el art. 9 de la Ley de Propiedad Horizontal.

Extendiendo yo, [ELEGIR: el / la]

Secretario
Secretaria
[NOMBRE Y APELLIDOS], la presente acta, que es leída, y considerándola conforme firman todos los asistentes, de lo que certifico.

Firma del Presidente/a	Firma del Secretario/a

========================================================================
