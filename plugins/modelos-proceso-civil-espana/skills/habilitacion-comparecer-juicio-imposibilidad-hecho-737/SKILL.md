---
name: habilitacion-comparecer-juicio-imposibilidad-hecho-737
description: "Redacta el escrito «Habilitación para comparecer en juicio por imposibilidad de hecho» (formulario 737 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Habilitación para comparecer en juicio por imposibilidad de hecho

> Formulario 0737 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] NÚMERO DE (5 veces)
- [ ] LUGAR (6 veces)
- [ ] NOMBRE (3 veces)
- [ ] FECHA (4 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] NÚMERO / (2 veces)
- [ ] AÑO (2 veces)
- [ ] DENOMINACIÓN SA LA CANTIDAD DE 8
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…[LUGAR]D./Dña. [NOMBRE], Apellido»; «…Firma de Abogado/a Firma de Procurador/a»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 27.2.c) de la Ley 15/2015
- art. 29 LJV
- artículo 28.1 LJV
- art. 28.3 LJV

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

### Formulario 0737 · Habilitación para comparecer en juicio por imposibilidad de hecho

- Año del modelo: 2015
- Revisión 17-11-2026: 3 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; saltos de párrafo recuperados (texto venía pegado); restos de formato retirados; 2 llamadas a nota sin texto retiradas; 2 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Solicitud para que se inicie el expediente de jurisdicción voluntaria de habilitación de persona con provisión de medidas judiciales de apoyo a personas con discapacidad para comparecer en juicio, y ulterior nombramiento de defensor judicialFormulario adaptado a la reforma orgánica y procesal de la LO 1/2025. A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA [NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).] Nº [NÚMERO DE] [LUGAR]D./Dña. [NOMBRE], Apellido [COMPLETAR], Procurador/a y de D./Dña. [NOMBRE], Apellido, ante el Tribunal comparezco y como mejor proceda en derecho DIGO: Que por medio del presente escrito promuevo expediente de jurisdicción voluntaria para habilitación de persona con discapacidad para comparecer en juicio, y ulterior nombramiento de defensor judicial, en base a los siguientesHechos y consideraciones jurídicas:1.ª) Que mi mandante es persona con discapacidad provista de medidas judiciales para el ejercicio de su capacidad jurídica, en concreto, para la administración de sus bienes, por sentencia dictada por la Sección Civil del Tribunal de Instancia nº [NÚMERO DE] [LUGAR] en fecha [FECHA], la cual devino firme. En la misma se nombró curador a nuestro hermano D.nuestra hermana Dña. [NOMBRE Y APELLIDOS].2.º) Que en la Sección Civil del Tribunal de Instancia nº [NÚMERO DE] [LUGAR] se siguen autos de juicio ordinario con nº [NÚMERO /] [AÑO], en cuyo marco se ha emplazado a mi cliente para que en el plazo de 20 días comparezca ante el Tribunal y conteste a una demanda en la cual se le reclama por parte de la entidad financiera [DENOMINACIÓN SA LA CANTIDAD DE 8].000 euros por un contrato de arrendamiento financiero en relación a un vehículo de alta gama, firmado el [FECHA], en un momento previo a la referida provisión de medidas de apoyo.3.ª) Que la curadora se encuentra de viaje en Argentina, y no está prevista su vuelta hasta dentro de un mes, sin que se le haya podido localizar hasta el momento, dado que son diversas las ciudades a las que tenía previsto viajar.4.ª) Procede, en consecuencia, que se habilite a la persona con discapacidad para comparecer en juicio y contestar a la demanda, con ulterior nombramiento de defensor judicial, con arreglo a lo dispuesto en el art. 27.2.c) de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), toda vez que la curadora se encuentra en una situación de imposibilidad de hecho para la asistencia en juicio a mi mandante, sin que pueda regresar dentro del plazo concedido por el citado órgano judicial para representar a aquel a la hora de contestar a la demanda. En este sentido, la falta de habilitación ocasionaría un gran perjuicio al demandado en el referido procedimiento, toda vez que, al no poder comparecer por sí solo, sería declarado en rebeldía y por el efecto preclusivo del art. 499 de la Ley de Enjuiciamiento Civil, perdería la oportunidad de alegar hechos específicos que se opongan a la demanda, proponer determinadas pruebas que deben anunciarse en su contestación, o plantear excepciones procesales.5.ª) De conformidad con el art. 29 LJV, desde la presentación de esta solicitud hasta la aceptación del cargo por el defensor judicial finalmente designado, quedará suspendido el plazo para contestar a la demanda.6.ª) Que es competente la Sección Civil del Tribunal de Instancia al que me dirijo conforme al artículo 28.1 LJV, al encontrarse en su partido judicial el domicilio donde reside mi mandante, sito en la calle [NÚMERO DE] [LUGAR].7.ª) Se acompañan a este escrito copia de la sentencia de provisión de medidas judiciales de apoyo, [NOTA DE REVISIÓN: El propio formulario dice que se nombró curador en sentencia de medidas de apoyo. Fuente: LEC 1/2000 (BOE-A-2000-323) art. 760, redacción Ley 8/2021 (BOE-A-2021-9233).] diligencia de ordenación que advera su firmeza, copia de la demanda recibida y del decreto del Letrado de la Administración de Justicia en el que se le emplaza con fecha [FECHA]

Por todo lo expuesto, al amparo de los arts. 27 y ss. LJV,

SUPLICO AL TRIBUNALQue teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria, previa la convocatoria de comparecencia del Ministerio Fiscal, del hermano de mi mandante .Dña. [NOMBRE], Apellido, y de quien se estime pertinente; se dicte decreto por el Letrado de la Administración de Justicia habilitándole para comparecer en el procedimiento ordinario con nº [NÚMERO /] [AÑO], tramitado ante la Sección Civil del Tribunal de Instancia nº [NÚMERO DE] [LUGAR], con nombramiento ulterior de defensor judicial durante el transcurso del procedimiento. Y todo ello, con comunicación de la presentación de esta solicitud al referido órgano judicial para que suspenda el transcurso del plazo de contestación.

Por ser de Justicia que pido [LUGAR], a [FECHA].

Firma de Abogado/a

Firma de Procurador/a [COMPLETAR] La exigencia de abogado y procurador para presentar demanda de ejecución variará, según el art 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 28.3 LJV no exige dichos requisitos para la tramitación de la solicitud que nos ocupa; si bien parece lógico que la habilitación interesada sea cursada por dichos profesionales que estarán preparados para contestar a la demanda.

========================================================================
