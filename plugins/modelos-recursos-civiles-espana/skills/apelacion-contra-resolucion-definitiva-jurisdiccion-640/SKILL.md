---
name: apelacion-contra-resolucion-definitiva-jurisdiccion-640
description: "Redacta el escrito «Apelación contra resolución definitiva en jurisdicción voluntaria» (formulario 640 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Apelación contra resolución definitiva en jurisdicción voluntaria

> Formulario 0640 del plugin **Recursos civiles** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD
- [ ] FECHA (4 veces)
- [ ] Nº DE EXPEDIENTE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 17 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Don»; «…y representación que tengo acreditada de»; «…de»; «…de [COMPLETAR] de»; «…de»; «…go contra la misma RECURSO DE APELACIÓN,»; «…de»; «…de [COMPLETAR] de»; «…do, al estar ingresado en el hospital de»; «…so y protesta, tal como consta en folios»; «…cumentación acompañada obrante en folios»; «…ado para el pago de los plazos en fechas»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 458 de la LEC
- art. 459 de la LEC
- artículos 183 y 188 de la LEC
- arts. 1176, 1177 y 1178 del Código Civil
- art. 1176 CC
- arts. 1177 y 1178 CC
- arts. 98 y 99 LJV

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

### Formulario 0640 · Apelación contra resolución definitiva en jurisdicción voluntaria

- Año del modelo: 2015
- Revisión 17-11-2026: 24 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA AUDIENCIA PROVINCIAL DE [LOCALIDAD]

Don [COMPLETAR], Procurador de los Tribunales, en nombre y representación que tengo acreditada de [COMPLETAR], promotor del expediente de jurisdicción voluntaria arriba referenciado, ante el Tribunal comparezco y

DIGO:

1) Que en fecha [FECHA] de [COMPLETAR] de [COMPLETAR] se dictó auto que ponía fin a este expediente, el cual fue notificado a esta parte en fecha [FECHA] de [COMPLETAR] de

2) Que entendiendo que dicha resolución no es ajustada a derecho, dicho sea con los debidos respetos y en términos de defensa, por medio del presente escrito interpongo contra la misma RECURSO DE APELACIÓN, [COMPLETAR] impugnando el pronunciamiento de no estar bien hecha la consignación.

3) Que, de conformidad a lo dispuesto en el art. 20.2 de la Ley de Jurisdicción Voluntaria, en relación con el art. 458 de la LEC, fundo el recurso de apelación en las siguientes

ALEGACIONES

Se alega como primer motivo la infracción de las garantías procesales del expediente, al amparo del art. 459 de la LEC, al haberse denegado la suspensión de la comparecencia con indefensión para esta parte.

Esta parte solicitó la suspensión de la comparecencia celebrada en fecha [FECHA] de [COMPLETAR] de [COMPLETAR] por la imposibilidad de asistencia de su abogado, al estar ingresado en el hospital de [COMPLETAR] aquejado de una dolencia grave, lo que fue denegado por el Letrado de la Administración de Justicia y posteriormente por el Juez, al reproducir la pretensión en la comparecencia, privándose de esta forma de la posibilidad de defenderse en el expediente, habiendo formulado esta parte el correspondiente recurso y protesta, tal como consta en folios [COMPLETAR] del expediente.

La denegación de la suspensión infringe lo dispuesto en los artículos 183 y 188 de la LEC, de aplicación supletoria conforme a lo dispuesto en el art. 8 de la Ley de Jurisdicción Voluntaria, pues la solicitud de suspensión se ajustaba perfectamente a los requisitos legales y estaba plenamente justificada, según se desprende de la documentación acompañada obrante en folios [COMPLETAR] del proceso, de donde se infiere claramente la imposibilidad del abogado de esta parte de asistir a la comparecencia.

La actuación del órgano judicial ha supuesto una vulneración del derecho de defensa de esta parte, pues mi representado se ha visto indefenso al no poder intervenir mediante su letrado en la comparecencia, tal como le autoriza el art. 3.2 de la Ley de Jurisdicción Voluntaria, lo cual generó una situación de patente desigualdad pues el acreedor actuó defendido por letrado.

En este sentido el Tribunal Constitucional ha precisado —entre otras, en las sentencias 130/1986 y 237/1988— que, cuando alguna de las partes en un litigio solicita razonadamente la suspensión de la vista o del juicio, el órgano judicial competente no puede ignorar su petición y llevar a cabo la actuación judicial sin resolver motivadamente acerca de su solicitud, si con ello perjudica sus derechos de defensa. La razón estriba en que en todo proceso judicial debe respetarse el derecho de defensa contradictoria de las partes contendientes mediante la oportunidad de alegar y probar procesalmente sus derechos o intereses, sin que pueda justificarse la resolución judicial inaudita parte más que en el caso de incomparecencia por voluntad expresa o tácita, o por negligencia imputable a las partes; por lo que no es válido celebrar sin más la vista o la actuación oral de que se trate ignorando la petición de suspensión, siendo que la enfermedad del Abogado es considerada causa justa de suspensión, habiendo afirmado el Tribunal Supremo de 28 de enero de 2008, Rec. 5502/2000, con cita de las SSTC 101/2001 de 23 de abril y 143/2001 de 18 de junio, que "la celebración de la vista sin la participación de las partes, implica la omisión de una formalidad esencial que determina la indefensión, salvo que esta sea imputable al mismo justiciable, como es la privación o limitación de cualesquiera medios legales de defensa de su propia posición dentro del proceso, lo que ciertamente ocurre cuando falta la plena posibilidad de contradecir.

En consecuencia, y de acuerdo a la grave infracción denunciada, entendemos que procede decretar la nulidad de todo lo actuado a partir de la celebración de la comparecencia, debiendo retrotraerse las actuaciones a dicho momento procesal.

Se alega como segundo motivo, para el improbable caso que no se estimara el anterior, la errónea apreciación de prueba, con infracción de los arts. 1176, 1177 y 1178 del Código Civil, al haberse cumplido el requisito del ofrecimiento de pago.

El auto recurrido declara no estar bien hecha la consignación con el único argumento de que no se hizo ofrecimiento de pago previo al acreedor.

Esta conclusión fáctica debe entenderse errónea por cuanto que en la documentación acompañada a la solicitud consta expresamente la devolución de las transferencias bancarias realizadas por mi representado para el pago de los plazos en fechas [COMPLETAR] y [COMPLETAR], y que obran en los folios [COMPLETAR] del expediente.

Se cumplen, por tanto, los requisitos del art. 1176 CC para la cancelación de la obligación cuando establece que si el acreedor a quien se hiciere el ofrecimiento de pago conforme a las disposiciones que regulan éste, se negare, de manera expresa o de hecho, sin razón a admitirlo, a otorgar el documento justificativo de haberse efectuado o a la cancelación de la garantía, si la hubiere, el deudor quedará libre de responsabilidad mediante la consignación de la cosa debida.

Por lo demás, mi representado cumplió escrupulosamente los requisitos de la consignación establecidos en los arts. 1177 y 1178 CC en relación con los arts. 98 y 99 LJV, tal como consta en folios [COMPLETAR], por lo que procede la estimación de la solicitud con los efectos legales procedentes pretendidos en nuestro escrito inicial.

Por lo expuesto,

SUPLICO AL TRIBUNAL que tenga por interpuesto recurso de apelación contra el auto de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] dictado en el expediente de jurisdicción voluntaria número [Nº DE EXPEDIENTE], y, previos los trámites legales, estime el recurso interpuesto, declarando la nulidad de todo lo actuado a partir de la celebración de la comparecencia, y acordando la retroacción de las actuaciones al momento anterior a su celebración dicho momento procesal. Subsidiariamente, y para el caso de no estimarse dicha pretensión principal y entrarse en el fondo del recurso, solicitamos que se revoque el auto recurrido y en su lugar se declare bien hecha la consignación con los efectos legales procedentes.

OTROSÍ PRIMERO DIGO que, de conformidad con lo dispuesto en los apartados 3.b) y 6 de la disposición adicional decimoquinta de la LOPJ acompaño a este escrito resguardo de consignación en la cuenta de Depósitos y Consignaciones abierta a nombre del Tribunal del depósito exigido para interponer el recurso por importe de 50 euros.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma Procurador y Abogado

========================================================================
