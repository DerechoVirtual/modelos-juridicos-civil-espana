---
name: autorizacion-acreedor-aceptar-herencia-735
description: "Redacta el escrito «Autorización al acreedor para aceptar la herencia» (formulario 735 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Autorización al acreedor para aceptar la herencia

> Formulario 0735 del plugin **Sucesiones** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (4 veces)
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] CALLE (3 veces)
- [ ] NÚMERO (4 veces)
- [ ] IMPORTE
- [ ] SEDE
- [ ] FECHA (4 veces)
- [ ] LUGAR
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA»; «…ª) Que mi representado es acreedor de D.»; «…numeración del juzgado de procedencia).]»; «…/»; «…el»; «…falleció D.»; «…lleció D. [COMPLETAR], en el Hospital de»; «…r otorgado testamento ante el Notario de»; «…nicos herederos, a partes iguales, a sus»; «…te una finca libre de cargas, sita en en»; «…ndante para que acepte la herencia de D.»

## Elecciones que hay que hacer

- Firma del solicitante

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 18 LJV
- art. 93.2.c) de la Ley 15/2015
- art. 1.001 del Código Civil
- art. 93.2.c) LJV
- art. 94.1 LJV
- arts. 17, 18 y 19 LJV
- art. 94.2 LJV
- artículo 94.1 LJV
- art. 93 LJV
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

### Formulario 0735 · Autorización al acreedor para aceptar la herencia

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 1 bloques de alternativas señalados; 35 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito por el que se promueve expediente en solicitud de auto que autorice judicialmente para la aceptación de herencia por parte de acreedor del causante, previa la convocatoria de comparecencia prevista en el art. 18 LJV, con citación de los herederos indicados, y de quien se estime pertinente.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA [COMPLETAR] DE [LOCALIDAD]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

D./Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO:

Que por medio del presente escrito, y de conformidad el art. 93.2.c) de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud de autorización judicial para aceptación de herencia por parte de acreedor del causante. Todo ello, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª) Que mi representado es acreedor de D. [COMPLETAR], por importe de [IMPORTE] euros, a partir de los impagos sufridos en el marco de un contrato de agencia, tal y como se fijó en sentencia dictada por el Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] en fecha [FECHA], en el marco del juicio ordinario nº [NÚMERO] / [COMPLETAR], confirmada posteriormente por sentencia dictada por la Audiencia Provincial de [LOCALIDAD] el [COMPLETAR], la cual, a su vez, devino firme al no ser recurrida.

2.ª) Que el pasado [FECHA] falleció D. [COMPLETAR], en el Hospital de [COMPLETAR], tras haber otorgado testamento ante el Notario de [COMPLETAR] D./Dña. [NOMBRE Y APELLIDOS], en el cual se instituía como únicos herederos, a partes iguales, a sus [COMPLETAR] hijos

-
+
Añadir más párrafos iguales

D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO].

3.ª) Los referidos herederos repudiaron la herencia de su padre, mediante escritura pública, otorgada el pasado [FECHA] ante el mismo Notario. Extremo que perjudica claramente a mi mandante, puesto que en el caudal hereditario existe una finca libre de cargas, sita en en [COMPLETAR], calle [CALLE], nº [NÚMERO], cuyo valor de mercado probablemente sea inferior al crédito que le legitima a aquel, pero que serviría para cobrarse una parte sustancial de aquel. De esta forma, el bloqueo en la adjudicación del caudal hereditario, impide a mi cliente iniciar los trámites para realizar el crédito al que tiene derecho por sentencia firme.

4.ª) Por ello, y de conformidad con lo previsto en el art. 1.001 del Código Civil, se acude al expediente previsto el art. 93.2.c) LJV, que establece el cauce procesal para obtener la autorización judicial para que el acreedor pueda aceptar la herencia, tras la repudiación de los herederos instituidos como tales. El art. 94.1 LJV se remite a las normas comunes de la Ley de Jurisdicción Voluntaria, arts. 17, 18 y 19 LJV, que determinan la celebración de comparecencia con citación de interesados, por los trámites establecidos en los arts. 437 y ss. de la Ley de Enjuiciamiento Civil. Mi cliente se encuentra legitimado para ello, según art. 94.2 LJV, en su condición de acreedor, sin que sea necesaria la intervención del Ministerio Fiscal.

5.ª) Que es competente la sección civil del Tribunal de Instancia al que me dirijo conforme al artículo 94.1 LJV en relación con el art. 85.1º LOPJ, al encontrarse en su partido judicial el último domicilio del causante en el momento de su fallecimiento.

6.ª) Se acompañan a este escrito testimonio de las sentencias que fijan el crédito en primera y segunda instancia, de la diligencia de ordenación que declara la firmeza de esta última, del testamento del causante, y de la escritura que recoge la referida repudiación de los citados herederos.

Por todo lo expuesto, al amparo del art. 1.001 del Código Civil, y del art. 93 LJV,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria, previa la convocatoria de comparecencia prevista en el art. 18 LJV, con citación de los herederos indicados, y de quien se estime pertinente; se dicte auto autorizando judicialmente a mi mandante para que acepte la herencia de D. [COMPLETAR].

Por ser de Justicia que pido en [LUGAR], a [FECHA].

[ELEGIR: Firma del solicitante]

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito el art. 94.4 LJV exige esos requisitos para la tramitación del expediente cuando se trate de un haber hereditario con valor superior a 6.000 euros.

========================================================================
