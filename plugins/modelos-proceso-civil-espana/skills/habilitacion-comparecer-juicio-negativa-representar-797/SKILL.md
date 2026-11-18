---
name: habilitacion-comparecer-juicio-negativa-representar-797
description: "Redacta el escrito «Habilitación para comparecer en juicio por negativa a representar: inicio del expediente» (formulario 797 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Habilitación para comparecer en juicio por negativa a representar: inicio del expediente

> Formulario 0797 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE (3 veces)
- [ ] NÚMERO (3 veces)
- [ ] FECHA (2 veces)
- [ ] DESCRIBIR
- [ ] IMPORTE
- [ ] LUGAR
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…bajo la patria potestad de sus padres D.»; «…; con quienes reside en»; «…o conductor y de su compañía aseguradora»; «…y a la entidad aseguradora»; «…y a la entidad aseguradora»

## Elecciones que hay que hacer

- Firma del solicitante

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 27.2.b) de la Ley 15/2015
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

### Formulario 0797 · Habilitación para comparecer en juicio por negativa a representar: inicio del expediente

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 1 bloques de alternativas señalados; 28 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Solicitud para que se inicie el expediente de jurisdicción voluntaria de habilitación del menor no emancipado para comparecer en juicio planteando demanda, con posterior nombramiento de defensor judicial.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco y como mejor proceda en derecho DIGO: (1)

D./Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO:

Que por medio del presente escrito promuevo expediente de jurisdicción voluntaria para habilitación de menor no emancipado para comparecer en juicio planteando demanda, y ulterior nombramiento de defensor judicial, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que mi mandante actualmente cuenta con 17 años, y está bajo la patria potestad de sus padres D. [COMPLETAR], y Dña. [NOMBRE Y APELLIDOS]; con quienes reside en [COMPLETAR], calle [CALLE], nº [NÚMERO]. No se encuentra emancipado legalmente, ni se ha solicitado, ni está en tramitación, nada al respecto.

2.º) Que el pasado [FECHA] sufrió un accidente de tráfico con la motocicleta que conducía, al ser atropellado por un vehículo, conducido por D./Dña. [NOMBRE Y APELLIDOS], quien circulaba a excesiva velocidad y no respetó un semáforo en rojo. Como consecuencia del accidente estuvo hospitalizado ocho días, pasó tres meses de baja, y sufrió secuelas permanentes consistentes en [DESCRIBIR].

3.ª) Que, a pesar de haberlo intentado en los últimos meses, ha sido imposible alcanzar un acuerdo con la representación letrada del citado conductor y de su compañía aseguradora [COMPLETAR] SA; y es preciso iniciar la vía judicial para reclamar el pago de una indemnización de [IMPORTE] euros. Si bien, y a pesar de que apenas falte un mes para que transcurra un año desde el accidente, los citados progenitores del menor se niegan a representar legalmente a su hijo presentando la correspondiente demanda.

4.ª) Procede, en consecuencia, que se habilite al menor para poder codemandar a D./Dña. [NOMBRE Y APELLIDOS] y a la entidad aseguradora [COMPLETAR] SA, con ulterior nombramiento de defensor judicial, con arreglo a lo dispuesto en el art. 27.2.b) de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), toda vez que ha sido imposible hasta la fecha obtener la colaboración de alguno de los dos padres para iniciar los trámites necesarios para presentar la demanda. En este sentido, la falta de habilitación ocasionaría un gran perjuicio al menor, dado que transcurriría el plazo de prescripción de un año para ejercitar la acción de responsabilidad extracontractual, en virtud de lo dispuesto en el art. 1.968.2º del Código Civil. Y así, en el supuesto altamente probable de que la prescripción se alegare en alguna de las eventuales contestaciones, mi cliente perdería la posibilidad de obtener una indemnización a la que tiene derecho por las lesiones sufridas.

5.ª) De conformidad con el art. 29 LJV, desde la presentación de esta solicitud hasta la aceptación del cargo por el defensor judicial finalmente designado, quedará suspendido el plazo de prescripción citado.

6.ª) Que es competente la Sección Civil del Tribunal de Instancia al que me dirijo conforme al artículo 28.1 LJV, al encontrarse en su partido judicial el domicilio donde reside mi mandante, sito en [LOCALIDAD], calle [CALLE], nº [NÚMERO].

7.ª) Se acompañan a este escrito certificado de nacimiento de mi cliente, certificado médico de las secuelas sufridas, correos electrónicos enviados a sus padres sin contestación alguna, y atestado del accidente de tráfico en el que se puede comprobar la fecha del mismo.

Por todo lo expuesto, al amparo de los arts. 27 y ss. LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria, previa la convocatoria de comparecencia del Ministerio Fiscal, de los progenitores antes relacionados, de mi cliente, y de quien se estime pertinente; se dicte decreto por el Letrado de la Administración de Justicia habilitándole para presentar demanda frente a D./Dña. [NOMBRE Y APELLIDOS] y a la entidad aseguradora [COMPLETAR] SA, con nombramiento ulterior de defensor judicial durante el transcurso del procedimiento.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

[ELEGIR: Firma del solicitante]

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 28.3 LJV, no exige dichos requisitos para la tramitación de la solicitud que nos ocupa; si bien parece lógico que la habilitación interesada sea cursada por dichos profesionales que estarán preparados para contestar a la demanda, por lo que el escrito se desarrolla en esos términos.

========================================================================
