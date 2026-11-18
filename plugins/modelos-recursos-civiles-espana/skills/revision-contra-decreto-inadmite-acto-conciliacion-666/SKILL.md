---
name: revision-contra-decreto-inadmite-acto-conciliacion-666
description: "Redacta el escrito «Revisión contra el decreto que inadmite un acto de conciliación» (formulario 666 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Revisión contra el decreto que inadmite un acto de conciliación

> Formulario 0666 del plugin **Recursos civiles** · revisado el 17-11-2026.

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
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…D»; «…de»; «…de [COMPLETAR] de»; «…idumbre acerca de la deuda del demandado»; «…de»; «…de [COMPLETAR] de»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 139 y 142 de la LJV
- art. 139.1 LJV
- art. 139.1 de la LJV
- artículo 256.1 LEC

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

### Formulario 0666 · Revisión contra el decreto que inadmite un acto de conciliación

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 12 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D [COMPLETAR], Procurador de los Tribunales y de [NOMBRE DEL REPRESENTADO/A], según tengo acreditado en el procedimiento de conciliación arriba referenciado, ante el Tribunal comparezco y como mejor proceda en derecho

DIGO:

Que habiendo sido notificado a esta representación el decreto de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] dictado por el Letrado de la Administración de Justicia del órgano al que me dirijo, por el que se inadmite la solicitud de conciliación deducida por esta parte, mediante el presente escrito, al amparo del art. 20 de la Ley de Jurisdicción Voluntaria (LJV) en relación con el art. 452.2 y 454.bis de la LEC, interpongo recurso directo de revisión de la mencionada resolución citando como infringidos los arts. 139 y 142 de la LJV, en base a los siguientes

MOTIVOS

La inadmisión se funda en que la solicitud cumple una finalidad distinta de la prevista en el art. 139.1 LJV por cuanto supone un fraude procesal al pretenderse un mero reconocimiento de hechos.

Entendemos que esta interpretación infringe lo dispuesto en el art. 139.1 de la LJV, puesto que esta representación dedujo la solicitud de conciliación con la única finalidad de evitar un pleito con el demandado D

En efecto, la solicitud presentada por esta parte cumple las exigencias de fondo de la tutela preventiva formulada por ese conducto, puesto que no se reclama un mero "reconocimiento de hechos" carentes de trascendencia jurídica como se apunta en el decreto impugnado, sino que se insta del demandado la admisión de una deuda líquida ( euros), vencida y exigible, de origen contractual.

Por tanto, la solicitud de esta parte, en contra de lo afirmado en el decreto que ahora se somete a revisión, persigue una finalidad (reconocimiento de deuda) acorde con la naturaleza del instrumento empleado (acto de conciliación): un negocio de fijación de derechos que elimine toda incertidumbre acerca de la deuda del demandado [COMPLETAR] y que culmine con la creación de un título ejecutivo, lo que a su vez comportaría la evitación del consiguiente proceso declarativo tendente a la condena de la persona frente a la que se promueve el acto conciliatorio.

De otra parte, no se trata sólo de un "reconocimiento de hechos" vinculados con los diversos supuestos de diligencias preliminares enumerados en el artículo 256.1 LEC al que parece referirse el Letrado de la Administración de Justicia, sino de la puesta en marcha de un mecanismo voluntario que posibilita el eventual reconocimiento inatacable de derechos susceptibles de posterior demanda ejecutiva.

En definitiva, consideramos que la solicitud de esta parte cumple plenamente la finalidad propia de la conciliación que no es otra que la evitación de un ulterior proceso contencioso, por lo que se ajusta a lo que dispone el art. 139.1 LJV, por lo que solicitamos la estimación del recurso a fin de que se acuerde la admisión de la conciliación instada por esta parte.

En su virtud,

SUPLICO AL TRIBUNAL que teniendo por presentado este escrito, se sirva admitirlo, tener por interpuesto recurso directo de revisión contra el decreto dictado por el Letrado de la Administración de Justicia de ese órgano de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] y, tras los trámites legales, se dicte por V.I. auto por el que se revoque y deje sin efecto el decreto impugnado, ordenando en su lugar la admisión de la solicitud de conciliación instada por esta parte.

OTROSÍ DIGO que, de conformidad con lo dispuesto en los apartados 4 y 6 de la disposición adicional decimoquinta de la LOPJ acompaño a este escrito resguardo de consignación en la cuenta de Depósitos y Consignaciones abierta a nombre del Tribunal del depósito exigido para interponer el recurso por importe de 25 euros.

Por lo que,

SUPLICO AL TRIBUNAL que tenga por constituido el depósito, dejando interesada desde este momento su devolución para el caso de estimación total o parcial del recurso.

En [LUGAR], a [DÍA] de [MES] de [AÑO].l año

========================================================================
