---
name: caducidad-expediente-solicitud-763
description: "Redacta el escrito «Caducidad del expediente: solicitud» (formulario 763 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Caducidad del expediente: solicitud

> Formulario 0763 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD (2 veces)
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] CALLE
- [ ] NÚMERO
- [ ] Nº DE EXPEDIENTE
- [ ] FECHA (4 veces)
- [ ] ÓRGANO
- [ ] LUGAR
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA»; «…engo acreditada en los autos de juicio /»; «…/»; «…ditado, y que se instaron por la entidad»; «…tengo el honor de dirigirme se decidiera»; «…la parte actora para aportación de datos»

## Elecciones que hay que hacer

- Firma de Abogado/a	Firma de Procurador/a

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 21 de la Ley 15/2015
- art. 21 LJV
- art. 240.2 de la Ley 1/2000
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

### Formulario 0763 · Caducidad del expediente: solicitud

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 1 bloques de opciones sin texto dejados en blanco con sus rótulos; 1 bloques de alternativas señalados; 22 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito que solicita que se declare mediante decreto la caducidad de la instancia en el presente expediente de jurisdicción voluntaria.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA [COMPLETAR] DE [LOCALIDAD]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], cuya representación tengo acreditada en los autos de juicio / [COMPLETAR], seguido contra D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco y como mejor proceda en derecho DIGO: (1)

D./Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO:

Que por medio del presente escrito, y al amparo de lo dispuesto en el art. 21 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), procedo a solicitar la DECLARACIÓN DE CADUCIDAD del presente expediente, con arreglo a las siguientes

ALEGACIONES

PRIMERA.- Soy parte en los presentes autos de expediente de jurisdicción voluntaria nº [Nº DE EXPEDIENTE] / [COMPLETAR], conforme tengo debidamente acreditado, y que se instaron por la entidad [COMPLETAR] SA con objeto de que por el Letrado de la Administración de Justicia del Tribunal al cual tengo el honor de dirigirme se decidiera [COMPLETAR].

Que el presente expediente ha permanecido sin actividad procesal durante más de seis meses, en concreto durante 10 meses y 20 días hasta la fecha, computados desde el día [FECHA] de hasta el día [FECHA], en que tuvo lugar la última notificación a las partes de la diligencia de ordenación de impulso procesal, de fecha [FECHA], acordando requerir a la parte actora para aportación de datos [COMPLETAR].

SEGUNDA.- Dispone el art. 21 LJV que se tendrá por abandonado el expediente, si pese al impulso de oficio de las actuaciones, no se produce actividad promovida por los interesados en el plazo de seis meses desde la última notificación practicada. Y, tal y como se puede observar en el presente expediente, el referido plazo se ha cumplido con creces, sin que por la parte solicitante e interesada en el mismo se haya cumplimentado lo requerido, ni interesado ningún tipo de actuación.

Procede, en consecuencia, que, previo traslado a la parte solicitante para que evacue las alegaciones que tenga por conveniente, por el Letrado de la Administración de Justicia se decrete la caducidad del expediente. En este sentido, según lo dispuesto en el art. 240.2 de la Ley 1/2000, de 7 de enero, de Enjuiciamiento Civil, la caducidad que se produzca en primera instancia tendrá como efecto el desistimiento en dicha instancia. En todo caso, podrá interponerse nueva solicitud, de modo que no se extingue la acción sino que se abandona el expediente, como acontece con el desistimiento propio, a menos que aquélla hubiera prescrito, no llevando efecto interruptivo el plazo de paralización al que falta animus conservandi.

En su virtud,

SUPLICO AL TRIBUNAL

que, teniendo por presentado este escrito, y constando haber sido trasladado al Procurador de la parte contraria, se digne admitirlo, y en mérito a lo manifestado y tras traslado al solicitante para alegaciones, se declare mediante decreto la caducidad de la instancia en el presente expediente de jurisdicción voluntaria, teniendo a la entidad solicitante [ÓRGANO] SA por desistida, con lo demás que proceda.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

[ELEGIR: Firma de Abogado/a	Firma de Procurador/a]

Firma del solicitante

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para presentar solicitud de caducidad, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente.

========================================================================
