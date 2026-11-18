---
name: declaracion-fallecimiento-749
description: "Redacta el escrito «Declaración de fallecimiento» (formulario 749 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Declaración de fallecimiento

> Formulario 0749 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE (3 veces)
- [ ] NÚMERO
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ciones jurídicas: 1.ª) Que mi marido, D.»; «…, embarcó el día [FECHA] en la aeronave»; «…de la compañía aérea»; «…y yo vivíamos juntos con nuestro hijo D.»; «…de»; «…, y su superior en la empresa»; «…SL, con domicilio en [LOCALIDAD] de»; «…rtido judicial el último domicilio de D.»; «…, sito en la calle [CALLE] de»; «…ecreto declarando el fallecimiento de D.»; «…l mismo que será la del día de viaje, el»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 74.2 LJV
- art. 70.2 LJV
- art. 68.1 LJV
- art. 193 del Código Civil
- art. 3.2 LJV
- art. 68.4 LJV
- Ley 15/2015

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

### Formulario 0749 · Declaración de fallecimiento

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 23 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito por el que se promueve el expediente en solicitud de declaración de fallecimiento.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

Que por medio del presente escrito, y de conformidad con los arts. 67 y ss. de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud de declaración de fallecimiento, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que mi marido, D. [COMPLETAR], embarcó el día [FECHA] en la aeronave [COMPLETAR] de la compañía aérea [COMPLETAR] para realizar un viaje de carácter laboral de Madrid a La Habana (Cuba) que desapareció en el Océano Atlántico, sin llegar a su destino, y sin que hasta la fecha se haya obtenido noticia alguna de su paradero. El último radar que tuvo contacto con la nave la situaba en medio del mar Caribe. Concurren, en consecuencia, los presupuestos legales previstos en el art. 194.4º del Código Civil para la declaración de fallecimiento, al haber transcurrido más de un mes desde el siniestro, acaecido a cientos de kilómetros de tierra firme, no haber recuperado señala alguna ningún otro radar, y no haberse localizado rastro alguno. De lo que se desprenden evidencias racionales de ausencia de supervivientes.

2.ª) Que en el momento del accidente, mi marido y yo vivíamos juntos con nuestro hijo D. [COMPLETAR], menor de edad. Habíamos otorgado recíprocamente testamento, en el que determinábamos como herederos al citado hijo y a cada uno de nosotros. Por ello, siendo cónyuge no separado de la persona desaparecida, legítima heredera, y representante legal del otro heredero; me encuentro legitimada para instar la declaración interesada de conformidad con lo dispuesto en el art. 74.2 LJV.

3.ª) Procede, por ello, seguir los trámites previstos en citado precepto legal, que se remite al art. 70.2 LJV, con análisis de la amplia documental que se acompaña a este escrito, la práctica de las pruebas que se consideren necesarias, la publicación de edictos y la convocatoria de comparecencia con citación del Ministerio Fiscal y demás interesados; a los efectos de comprobar las requisitos antes expuestos. Se ofrecen, para ello, los siguientes testigos: el hermano de mi marido, con domicilio en calle [CALLE] de [COMPLETAR], y su superior en la empresa [COMPLETAR] SL, con domicilio en [LOCALIDAD] de [COMPLETAR], y quien le encargó y contrató el viaje finalmente siniestrado.

4.ª) Que es competente el Tribunal de Instancia al que me dirijo conforme al art. 68.1 LJV en relación con lo dispuesto en el art. 85.1º LOPJ, al encontrarse en su partido judicial el último domicilio de D. [COMPLETAR], sito en la calle [CALLE] de [COMPLETAR].

5.ª) Se acompañan a este escrito copia del atestado policial del accidente aéreo, recortes de periódicos que recogieron la noticia, copia del billete contratado por mi marido, libro de familia, copia del testamento otorgado por el mismo, y certificación del registro de últimas voluntades.

Por todo lo expuesto, al amparo del art. 193 del Código Civil, y de los arts. 67 y ss. LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria; se admita a trámite por el Letrado de la Administración de Justicia la solicitud y se fije hora para la comparecencia, con publicación de tal resolución dos veces, mediante edictos, con intervalo mínimo de ocho días, en la forma establecida en la Ley de Enjuiciamiento Civil en el Boletín Oficial del Estado y en el tablón de anuncios del ayuntamiento de Madrid haciendo constar que cualquier interesado pueda intervenir en la comparecencia; se cite para la misma al Ministerio Fiscal, a los testigos propuestos y a quien se considere interesados, se analice la documental presentada, se practiquen las pruebas que se consideren necesarias; para dictar decreto declarando el fallecimiento de D. [COMPLETAR], con expresión de la fecha del mismo que será la del día de viaje, el [COMPLETAR].

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma del solicitante

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 68.4 LJV, no exige requisito alguno de postulación.

========================================================================
