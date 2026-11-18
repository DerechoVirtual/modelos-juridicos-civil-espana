---
name: conversion-adopcion-simple-plena-solicitud-775
description: "Redacta el escrito «Conversión de adopción simple en plena: solicitud» (formulario 775 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Conversión de adopción simple en plena: solicitud

> Formulario 0775 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] Nº
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE (3 veces)
- [ ] NÚMERO
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… Hechos y consideraciones jurídicas: 1.ª»; «…es, se constituyó la adopción a mi favor»; «…nte de tráfico ocurrido en dicho país el»; «…. 2.ª»; «…de origen. En este sentido, tal adopción»; «…. 3.ª»; «…de»; «…l efecto la he matriculado en el Colegio»; «…ta previa de entidad pública alguna. 4.ª»; «…, D.»; «…ia, a celebrar según el art. 36 LJV. 5.ª»; «…de»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL
- del menor / de la menor
- El menor / La menor

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 42 de la Ley 15/2015
- art. 42.1.b) LJV
- art. 30.4 de la Ley 54/2007
- art. 42.3 LJV
- art. 36 LJV
- art. 33 LJV
- art. 3.2 LJV

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

### Formulario 0775 · Conversión de adopción simple en plena: solicitud

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 2 desplegables convertidos en elección en blanco; 26 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 3 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015); 6 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [Nº]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

Que por medio del presente escrito, y al amparo de lo dispuesto en el art. 42 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente de jurisdicción voluntaria para la conversión de la adopción simple
del menor D. [NOMBRE Y APELLIDOS]
de la menor Dña. [NOMBRE Y APELLIDOS]
 en adopción plena, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª [COMPLETAR]) Que el pasado [FECHA] por resolución adoptada por el Tribunal de Familia de Buenos Aires, se constituyó la adopción a mi favor [COMPLETAR]
del menor D. [NOMBRE Y APELLIDOS]
de la menor Dña. [NOMBRE Y APELLIDOS]
  de 11 años de edad y de nacionalidad argentina, al reunir todos los requisitos previstos en los arts. y ss. del Código Civil de la República Argentina. Dicha menor no tiene hermanos, y sus progenitores, con quien yo mantenía una íntima relación de amistad, fallecieron en un accidente de tráfico ocurrido en dicho país el [COMPLETAR].

2.ª [COMPLETAR]) Que la adopción regulada en el derecho argentino no alcanza el grado de plenitud que tal institución tiene en España, conforme a lo preceptuado por los arts. 175 y ss. de nuestro Código Civil, toda vez que el adoptante no goza de todas las obligaciones y derechos que el referido texto legal, en sus arts. 154 y ss. confiere, a quien ostenta la patria potestad de un menor, y no se extinguen definitivamente los vínculos entre el adoptado y su familia de origen. En este sentido, tal adopción [COMPLETAR].

3.ª [COMPLETAR]) La menor ha sido recientemente traslada a España, en concreto a mi residencia en la calle [CALLE] de [COMPLETAR], con la intención de establecer allí su residencia habitual. A tal efecto la he matriculado en el Colegio [COMPLETAR] para que continúe con sus estudios de primero de la ESO. Tal situación tiene encaje, por ello, en el supuesto establecido por el art. 42.1.b) LJV, presentándose la solicitud conforme ordena el apartado segundo de dicho precepto legal, sin necesidad de propuesta previa de entidad pública alguna.

4.ª [COMPLETAR]) Asimismo, concurren los extremos exigidos por el art. 30.4 de la Ley 54/2007, de 28 de diciembre, de Adopción Internacional, al que se remite el art. 42.3 LJV:

.- Durante el procedimiento de adopción las autoridades argentinas fueron informadas en todo momento sobre la voluntad de instar finalmente la adopción plena que aquí nos ocupa, con efecto legal de extinción de los vínculos jurídicos de la menor con su familia de origen. Así se reconoce en la resolución del Tribunal de Familia de Buenos Aires, en la que se añade que la familia más cercana de la misma ya no existía, al no tener hermanos y haber fallecido desgraciadamente sus progenitores.

.- Que el único tío [ELEGIR: del menor / de la menor], D. [COMPLETAR], hermano de su madre, manifestó libremente su asentimiento ante el citado órgano judicial, por escrito y en la forma exigida por el art. del Código Civil argentino. Así, se recoge en la resolución judicial que constituyó aquella, la cual excluye cualquier tipo de pago o compensación alguna; y sin que conste la revocación de dicho asentimiento.
.- El consentimiento de la madre de la menor, Dña. no pudo prestarse por causa del citado fallecimiento.
.- [ELEGIR: El menor / La menor], de 11 años, cuenta con madurez para prestar su consentimiento, tal y como hizo en el expediente tramitado en Argentina. Ha sido convenientemente asesorada sobre los efectos de la adopción española, y tiene una relación excelente con mis dos hijas de 13 y 11 años. Todo lo cual se podrá poner de manifiesto en su eventual audiencia, a celebrar según el art. 36 LJV.

5.ª [COMPLETAR]) Que es competente el Tribunal de Instancia al que me dirijo conforme al art. 33 LJV en relación con lo dispuesto en el art. 85.1º LOPJ, al encontrarse en su partido judicial mi domicilio como adoptante, sito en la calle [CALLE] de [COMPLETAR].

6.ª [COMPLETAR]) Se acompañan a este escrito testimonio de la resolución judicial argentina de adopción, copia íntegra del expediente tramitado al efecto, libro de familia de la menor, certificados de defunción de sus dos progenitores, tarjeta de embarque utilizada por aquella para desplazarse a España, y copia de la matrícula realizada en el Colegio [COMPLETAR] de [LOCALIDAD].

Por todo lo expuesto, al amparo de los arts. 175 y ss. del Código Civil, y de los arts. 33 y ss. LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria, previos los trámites de consentimiento, audiencias y diligencias que se estimen oportunas, oído el Ministerio Fiscal, y
el menor D. [NOMBRE Y APELLIDOS]
la menor Dña. [NOMBRE Y APELLIDOS]
  ; se dicte auto convirtiendo la adopción no plena acordada por el Tribunal de Familia de Buenos Aires en adopción plena, a todos los efectos legales; librándose, una vez firme la resolución, testimonio de la misma para su inscripción en el Registro Civil de Madrid.

Es Justicia que solicito en [LUGAR], a [FECHA].

Firma del solicitante:

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 34.2 de la Ley de Jurisdicción Voluntaria, no exige dichos requisitos para la tramitación de la solicitud que nos ocupa.

========================================================================
