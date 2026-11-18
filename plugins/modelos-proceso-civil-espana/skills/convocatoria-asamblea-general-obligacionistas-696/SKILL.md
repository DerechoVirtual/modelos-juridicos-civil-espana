---
name: convocatoria-asamblea-general-obligacionistas-696
description: "Redacta el escrito «Convocatoria de la asamblea general de obligacionistas» (formulario 696 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Convocatoria de la asamblea general de obligacionistas

> Formulario 0696 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (10 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] CALLE (5 veces)
- [ ] NÚMERO (6 veces)
- [ ] NIF
- [ ] FECHA (3 veces)
- [ ] IMPORTE (4 veces)
- [ ] LUGAR
- [ ] Otros 23 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…general de obligacionistas de la entidad»; «…s Hechos y consideraciones jurídicas: 1ª»; «…dantes son obligacionistas de la entidad»; «…SA, constituida el»; «…gún consta en la escritura autorizada el»; «…, Notario de»; «…de los de»; «…de los de [COMPLETAR] el»; «… los de [COMPLETAR] el [COMPLETAR], Tomo»; «…el [COMPLETAR], Tomo [COMPLETAR], Folio»; «…omo [COMPLETAR], Folio [COMPLETAR], Hoja»; «…, calle [CALLE], nº [NÚMERO];»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 422.1 Real Decreto Legislativo 1/2010
- art. 131 LJV
- art. 130.1 LJV
- art. 129 LJV
- art. 3.2 LJV
- art. 130.3 LJV
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

### Formulario 0696 · Convocatoria de la asamblea general de obligacionistas

- Año del modelo: 2015
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 56 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Por medio del presente escrito, y de conformidad con los arts. 129 y ss. de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria, se promueve expediente en solicitud de convocatoria de la asamblea general de obligacionistas

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], D./Dña. [NOMBRE Y APELLIDOS], y D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante copia fehaciente de la escritura de poderes, que acompaño para su unión a los autos por copia testimoniada con devolución de aquélla, como mejor proceda en derecho comparezco y DIGO: (1)

Que por medio del presente escrito, y de conformidad con los arts. 129 y ss. de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud de convocatoria de la asamblea general de obligacionistas de la entidad [COMPLETAR] SA. Todo ello, en base a los siguientes

Hechos y consideraciones jurídicas:

1ª [COMPLETAR])

Que mis mandantes son obligacionistas de la entidad [COMPLETAR] SA, constituida el [COMPLETAR], según consta en la escritura autorizada el [COMPLETAR] por D./Dña. [NOMBRE Y APELLIDOS], Notario de [COMPLETAR], su domicilio social se halla sito en [LOCALIDAD], calle [CALLE], nº [NÚMERO], y fue inscrita en el Registro Mercantil nº [NÚMERO] de los de [COMPLETAR] el [COMPLETAR], Tomo [COMPLETAR], Folio [COMPLETAR], Hoja [COMPLETAR], con CIF [NIF]. En fecha [FECHA] suscribieron obligaciones convertibles en acciones, por importe de [IMPORTE] euros (a razón de [IMPORTE] euros, [IMPORTE] euros, y [IMPORTE] euros, respectivamente), lo que supone un 24,99% de las obligaciones emitidas y no amortizadas. Los administradores sociales son D./Dña. [NOMBRE Y APELLIDOS], D./Dña. [NOMBRE Y APELLIDOS], y D./Dña. [NOMBRE Y APELLIDOS] con domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO]; [COMPLETAR], calle [CALLE], nº [NÚMERO]; y [COMPLETAR], calle [CALLE], nº [NÚMERO], respectivamente. El comisario nombrado es D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO]. Se aporta también listado de obligacionistas y sus direcciones.

2ª [COMPLETAR])

El pasado [FECHA], mis mandantes enviaron burofax al comisario, solicitando que convocaría asamblea general de obligacionistas con el siguiente orden del día:

.- [COMPLETAR].

.- [COMPLETAR]

.- [COMPLETAR]

.-etc. [COMPLETAR].

3ª [COMPLETAR])

A pesar de que los mismos reúnen un porcentaje de obligaciones emitidas y no amortizadas superior al 20%, el comisario desoyó la petición de convocatoria, incumpliendo la obligación prevista en el art. 422.1 Real Decreto Legislativo 1/2010, de 2 de julio, por el que se aprueba el texto refundido de la Ley de Sociedades de Capital (en lo sucesivo, TRLSC).

4ª [COMPLETAR])

Tales circunstancias habilitan la posibilidad, prevista en el art. 422.3 TRLSC, de que mi cliente inste ante el Letrado de la Administración de Justicia la convocatoria pretendida, previa audiencia del Comisario. En este sentido, mis clientes están legitimados para ello, al ostentar el 24% de las obligaciones indicadas. Por ello, se acude al expediente previsto los arts. 129 y ss. LJV, que, en su art. 131 LJV prevé la celebración de una comparecencia con citación del comisario designado y a los propios promotores de la asamblea.

5ª [COMPLETAR])

Que es competente la Sección de lo Mercantil del Tribunal de Instancia al que me dirijo conforme al art. 130.1 LJV, al encontrarse en su partido judicial el domicilio social de la entidad emisora de las obligaciones.

6ª [COMPLETAR])

Se acompañan a esta solicitud copia de los estatutos sociales, del reglamento de obligacionistas, registro de obligaciones emitidas, y burofax enviado al Comisario, con el orden del día expresado.

Por todo lo expuesto, al amparo del art. 422 TRLSC y del art. 129 LJV,

SOLICITO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria para la convocatoria de la asamblea general de obligacionistas; y previa convocatoria de comparecencia ante el Letrado de la Administración de Justicia prevista en el art. 131 LJV, con citación de del comisario D./Dña. [NOMBRE Y APELLIDOS], de los obligacionistas, y a quien se estime oportuno, se dicte decreto acordando la convocatoria de la asamblea general de obligacionistas de la entidad [COMPLETAR] SA, con el orden del día indicado.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito, el art. 130.3 LJV considera preceptiva la intervención de Abogado y Procurador para la solicitud en análisis.

========================================================================
