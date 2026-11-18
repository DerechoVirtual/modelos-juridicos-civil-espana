---
name: autorizacion-tutor-curador-aceptar-sin-beneficio-733
description: "Redacta el escrito «Autorización del tutor o curador para aceptar sin beneficio de inventario o repudiar herencia» (formulario 733 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Autorización del tutor o curador para aceptar sin beneficio de inventario o repudiar herencia

> Formulario 0733 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Autorización para aceptar herencia por el «tutor» de una mayor («incapaz»): para mayores, curador representativo (art. 287.5.º CC y art. 93.2.b) LJV); si el tutor es anterior a 2021, DT 2.ª Ley 8/2021 (BOE-A-2021-9233).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LOCALIDAD (2 veces)
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] SEDE
- [ ] FECHA (4 veces)
- [ ] Nº DE PROCEDIMIENTO
- [ ] CALLE
- [ ] NÚMERO (3 veces)
- [ ] IMPORTE (3 veces)
- [ ] LUGAR
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…DEL TRIBUNAL DE INSTANCIA»; «…numeración del juzgado de procedencia).]»; «…/»; «…falleció el hermano de la tutelada, D.»; «…uales a aquella, y a su otro hermano, D.»; «…s amplio, compuesto por dos inmuebles en»; «…, sitos en las calles»; «…, nº [NÚMERO] y»; «…rcer inmueble en la localidad costera de»; «…enta corriente con la entidad financiera»; «…eneficio de inventario la herencia de D.»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (4)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 93.2.b) LJV
- art. 93.2.b) de la Ley 15/2015
- art. 224 del Código Civil
- art. 94.1 LJV
- arts. 17, 18 y 19 LJV
- art. 94.2 LJV
- art. 271 del Código Civil
- art. 93 LJV
- art. 18 LJV
- art. 3.2 LJV
- art. 94.4 LJV

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

### Formulario 0733 · Autorización del tutor o curador para aceptar sin beneficio de inventario o repudiar herencia

- Año del modelo: 2015
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 30 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025)
- Avisos de la revisión: Autorización para aceptar herencia por el «tutor» de una mayor («incapaz»): para mayores, curador representativo (art. 287.5.º CC y art. 93.2.b) LJV); si el tutor es anterior a 2021, DT 2.ª Ley 8/2021 (BOE-A-2021-9233).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito por el que se promueve expediente en solicitud de autorización judicial de tutor, del curador representativo o del defensor judicial para aceptar, en nombre de su tutelado, representado o defendido, herencia sin beneficio de inventario (art. 93.2.b) LJV).

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA [COMPLETAR] DE [LOCALIDAD]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

Que por medio del presente escrito, y de conformidad con el art. 93.2.b) de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud de autorización judicial de tutor para aceptar, en nombre de su tutelado, herencia sin beneficio de inventario. Todo ello, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que mi representado fue nombrado tutor de Dña. [NOMBRE Y APELLIDOS], por auto dictado por el Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] en fecha [FECHA], en los autos de tutela nº [Nº DE PROCEDIMIENTO] / [COMPLETAR], que devino firme al no ser recurrido, tomando posesión de su cargo el día [FECHA].

2.ª) Que el pasado [FECHA] falleció el hermano de la tutelada, D. [COMPLETAR], soltero y sin hijos, habiendo otorgado testamento en el cual se instituían como únicos herederos, a partes iguales a aquella, y a su otro hermano, D. [COMPLETAR], con domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO].

3.ª) Que el caudal hereditario del causante es amplio, compuesto por dos inmuebles en [COMPLETAR], sitos en las calles [COMPLETAR], nº [NÚMERO] y [COMPLETAR], nº [NÚMERO], un tercer inmueble en la localidad costera de [COMPLETAR], activos bancarios por importe global de [IMPORTE] euros, y la tercera parte del negocio de hostelería propiedad de los tres hermanos, que conforma actualmente una unidad de negocio en perfecto funcionamiento, con un valor estimado de mercado de [IMPORTE] euros. No se conocen deudas de importancia, limitándose las mismas a un pequeño descubierto en la cuenta corriente con la entidad financiera [COMPLETAR] SA, que se reduce a la cantidad de [IMPORTE] euros.

4.ª) Por ello, y de conformidad con lo previsto en el art. 287.5º con relacción al art. 224 del Código Civil, se acude al expediente previsto en el art. 93.2.b) LJV, que establece el cauce procesal para obtener la autorización judicial para aceptar la herencia sin beneficio de inventario en nombre del tutelado. El art. 94.1 LJV se remite a las normas comunes de la Ley de Jurisdicción Voluntaria, arts. 17, 18 y 19 LJV, que determinan la celebración de comparecencia con citación de interesados, por los trámites establecidos en los arts. 437 y ss. de la Ley de Enjuiciamiento Civil. Mi cliente se encuentra legitimado para ello, según art. 94.2 LJV, al ostentar la representación legal de la persona tutelada, [NOTA DE REVISIÓN (comprobar): Si la tutela es de una persona mayor con discapacidad nombrada antes del 3-9-2021, se rige por las normas del curador representativo (DT 2.ª Ley 8/2021). Fuente: Ley 15/2015 de la Jurisdicción Voluntaria (BOE-A-2015-7391) art. 93.2.b), redacción Ley 8/2021 (BOE-A-2021-9233); Ley 8/2021 (BOE-A-2021-9233) DT 2.ª.] siendo necesaria además la intervención del Ministerio Fiscal, tal y como ordena el apartado tercero del mismo precepto legal.

5.ª) Que es competente el Tribunal de Instancia al que me dirijo conforme al art. 94.1 LJV en relación con el art. 85.1º LOPJ, al encontrarse en su partido judicial el último domicilio del causante en el momento de su fallecimiento.

6.ª) Se acompañan a este escrito testimonio del auto de constitución de la tutela, de las escrituras de propiedad de los tres inmuebles referidos, y diversa documentación relativa a los activos bancarios y al negocio copropiedad de los tres hermanos.

Por todo lo expuesto, al amparo del art. 271 del Código Civil, y del art. 93 LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria, previa la convocatoria de comparecencia prevista en el art. 18 LJV, con citación del heredero indicados, del Ministerio Fiscal, de la tutelada si se considera preciso y de quien se estime pertinente; se dicte auto autorizando judicialmente a mi mandante para que acepte sin beneficio de inventario la herencia de D. [COMPLETAR], en nombre de la tutelada Dña. [NOMBRE Y APELLIDOS].

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 94.4 LJV exige esos requisitos para la tramitación del expediente cuando se trate de un haber hereditario con valor superior a 6.000 euros, como ocurre en el supuesto de este modelo.

========================================================================
