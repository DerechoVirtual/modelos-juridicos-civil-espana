---
name: aviso-declarado-fallecido-ha-reaparecido-747
description: "Redacta el escrito «Aviso del declarado fallecido de que ha reaparecido» (formulario 747 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Aviso del declarado fallecido de que ha reaparecido

> Formulario 0747 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] LOCALIDAD
- [ ] CALLE (2 veces)
- [ ] NÚMERO
- [ ] Nº DE EXPEDIENTE
- [ ] FECHA (4 veces)
- [ ] NACIONALIDAD
- [ ] NOMBRE Y APELLIDOS
- [ ] LUGAR
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…D.»; «…/»; «…/ [COMPLETAR], el»; «…etuvieron a todo el pasaje en la Isla de»; «…por efectivos de las fuerzas armadas de»; «…de»; «…e la propia declaración, y de mi hijo D.»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 75 de la Ley 15/2015
- art. 75 LJV
- art. 197 del Código Civil
- art. 68.1 LJV
- art. 3.2 LJV
- art. 68.4 LJV

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

### Formulario 0747 · Aviso del declarado fallecido de que ha reaparecido

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 22 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito por el que se promueve el expediente en solicitud de que se deje sin efecto la declaración de fallecimiento de una persona.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D. [COMPLETAR], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

Que por medio del presente escrito, y de conformidad con el art. 75 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud de que se deje sin efecto la declaración de fallecimiento de mi persona, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que por el Tribunal al que tengo el honor de dirigirme, en el marco del expediente de jurisdicción voluntaria nº [Nº DE EXPEDIENTE] / [COMPLETAR], el [COMPLETAR] se dictó decreto por el Letrado de la Administración de Justicia declarando mi fallecimiento con fecha [FECHA], de conformidad con lo dispuesto en el art. 194.4º del Código Civil, a partir del supuesto naufragio del buque en el que realizaba un crucero por el mar Caribe, que nunca llegó a su destino en La Habana (Cuba), una vez que había transcurrido más de un mes sin noticia alguna. Dicha resolución devino firme, al no ser recurrida.

2.ª) El barco nunca naufragó, sino que fue secuestrado por unos piratas de nacionalidad [NACIONALIDAD] que lo hundieron, y retuvieron a todo el pasaje en la Isla de [COMPLETAR], con objeto de pedir un rescate a nuestros respectivos gobiernos. Tras pasar más de seis meses en condiciones penosas, sufriendo todo tipo de penalidades y sin noticia alguna sobre eventuales negociaciones, fuimos liberados el pasado [FECHA] por efectivos de las fuerzas armadas de [COMPLETAR].

3.ª) Una vez regresado a España, y tras conocer mi declaración legal de fallecimiento, acudo al expediente previsto en el art. 75 LJV, para revocar la misma, aportando documentación relativa a mi identidad, y ofreciéndome para cualquier prueba que se considere necesaria al respecto. Dado que se ha aperturado mi propia herencia, mi objetivo, en virtud de lo dispuesto en el art. 197 del Código Civil, es recuperar mis bienes en el estado en que se encuentren, y el precio de los que se hayan venido o los bienes comprados con dicho producto.

4.ª) Que es competente la Sección Civil del Tribunal de Instancia al que me dirijo conforme al art. 68.1 LJV, en relación con lo dispuesto en el art. 85.1º LOPJ, al encontrarse en su partido judicial mi último domicilio de sito en la calle [CALLE] de [COMPLETAR]; y ser el órgano judicial que declaró el fallecimiento que ahora se pretende impugnar.

5.ª) Se acompañan a este escrito testimonio de la declaración de fallecimiento, copia del informe militar sobre el secuestro, copia de mi DNI, reportaje fotográfico mío anterior al secuestro, y certificado literal de nacimiento. Se ofrece información testifical de mi mujer Dña. [NOMBRE Y APELLIDOS], quien fue promotora de la propia declaración, y de mi hijo D. [COMPLETAR], de 18 años de edad.

Por todo lo expuesto, al amparo del art. 197 del Código Civil, y del art. 75 LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria; se proceda por el Letrado de la Administración de Justicia a identificarme por los medios propuestos o los que estime adecuados, y previa convocatoria de comparecencia, con citación del Ministerio Fiscal, mi persona, testigos propuestos y a quien se considere interesado; se dicte decreto revocando la declaración de fallecimiento realizada por decreto de fecha [FECHA], a todos los efectos legales.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma del solicitante

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 68.4 LJV, no exige requisito alguno de postulación.

========================================================================
