---
name: denuncia-ejecutado-infracciones-actos-ejecucion-419
description: "Redacta el escrito «Denuncia por el ejecutado de infracciones en los actos de la ejecución» (formulario 419 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Denuncia por el ejecutado de infracciones en los actos de la ejecución

> Formulario 0419 del plugin **Ejecución civil** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] NÚMERO
- [ ] COLEGIO
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… devuelta por precisarla para otros usos»; «…, con despacho profesional en»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 24 CE
- art. 562.1 LEC
- arts. 553 y 556 LEC

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

### Formulario 0419 · Denuncia por el ejecutado de infracciones en los actos de la ejecución

- Año del modelo: 2018
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 10 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de la parte ejecutada compareciendo ante el Tribunal y denunciando la infracción de normas que regulan los actos concretos del proceso de ejecución, cuando no exista resolución expresa frente a la que recurrir.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante escritura pública de poderes que solicito, una vez incorporada por copia en autos, me sea devuelta por precisarla para otros usos [COMPLETAR], ante el Tribunal comparezco bajo la dirección de D./Dña. [NOMBRE Y APELLIDOS], colegiado n.º [NÚMERO] del Ilustre Colegio de Abogados de [COLEGIO], con despacho profesional en [COMPLETAR], y como mejor proceda en derecho DIGO:

Que por el presente escrito, sin perjuicio de las causas de oposición que en su caso puedan ser alegadas en tiempo y forma, en la representación que acredito, formulo denuncia de INFRACCIÓN DE LAS NORMAS QUE REGULAN LOS ACTOS CONCRETOS DEL PROCESO DE EJECUCIÓN, con base en los siguientes:

HECHOS

PRIMERO.- Que esta parte conoce extrajudicialmente que por auto de ese Tribunal de fecha [FECHA] se despacha ejecución en su contra.

SEGUNDO.- Que a pesar del tiempo transcurrido, esta parte no ha tenido noticia de este procedimiento, entendiendo que el vicio procesal aquí alegado constituye una infracción de las normas que rigen los actos y garantías del proceso, que en este caso serían las normas que consagran los principios de audiencia, contradicción, igualdad y derecho a una tutela judicial efectiva (art. 24 CE y normas concordantes).

Como fundamento de los anteriores hechos se adjuntan a la presente solicitud los siguientes DOCUMENTOS:

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS DE DERECHO

PRIMERO.- Dispone el art. 562.1 LEC que con independencia de la oposición a la ejecución por el ejecutado según lo dispuesto en los artículos anteriores, todas las personas a que se refiere el art. 538 podrán denunciar la infracción de normas que regulen los actos concretos del proceso de ejecución: (...) 3. Mediante escrito dirigido al Tribunal si no existiera resolución expresa frente a la que recurrir. En el escrito se expresará con claridad la resolución o actuación que se pretende para remediar la infracción alegada.

SEGUNDO.- Que los arts. 553 y 556 LEC obligan al Tribunal a notificar el auto de ejecución al ejecutado a fin de poder impugnarlo, y el art. 24 CE garantiza el derecho fundamental a la tutela judicial efectiva, en su vertiente de derecho al proceso con todas las garantías, incluido el principio de contradicción, defensa y audiencia

Por todo lo expuesto.

SUPLICO AL TRIBUNAL:

Que teniendo por presentada este escrito junto con sus documentos y copias de todo ello, se sirva admitirlo y tenerme por personado y parte en la representación que ostento y por formulada solicitud de declaración de infracción de las normas que regulan los actos del proceso de ejecución y, previos los trámites legales, dicte resolución por la que acuerde la notificación fehaciente a mi representado del auto despachando ejecución a fin de poder impugnarlo.

Es justicia que pido en [LUGAR], a [FECHA].

Firma del Abogado/a	Firma del Procurador/a

========================================================================
