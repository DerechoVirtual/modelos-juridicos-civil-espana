---
name: sucesion-fiador-posicion-procesal-ejecutante-278
description: "Redacta el escrito «Sucesión del fiador en la posición procesal del ejecutante» (formulario 278 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Sucesión del fiador en la posición procesal del ejecutante

> Formulario 0278 del plugin **Sucesiones** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] Nº
- [ ] AÑO (2 veces)
- [ ] NOMBRE DEL SOLICITANTE
- [ ] IMPORTE (7 veces)
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 15 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Don»; «…, Procurador de los Tribunales y de Don»; «…, Hechos y consideraciones jurídicas: 1ª»; «…, en reclamación frente a Don»; «…dad de fiador solidario del anterior. 2ª»; «…go sobre la vivienda del codemandado Sr.»; «… pago de las sumas objeto de condena. 3ª»; «…nte, obra ya unido a las actuaciones. 4ª»; «…idad de fiador del también demandado Sr.»; «…del procedimiento frente al referido Sr.»; «…cesales que se devenguen en adelante. 5ª»; «…la persona del cedente por el cesionario»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 17.1 LEC
- art. 1.839 CCiv
- art. 1.838 CCiv
- art. 1.212 CCiv
- art. 17 LEC
- art. 17.2 LEC

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

### Formulario 0278 · Sucesión del fiador en la posición procesal del ejecutante

- Año del modelo: 2020
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 27 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito del fiador solicitando la sucesión en la posición procesal del ejecutante al haber pagado al mismo la cantidad reclamada.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

Don [COMPLETAR], Procurador de los Tribunales y de Don [COMPLETAR], conforme tengo acreditado en el presente proceso, que se sigue en el Tribunal como Ejecución de Título Judicial nº [Nº]/[AÑO], ante el Tribunal comparezco y en la forma que en Derecho mejor proceda, DIGO:

Que por medio del presente escrito vengo a interesar la sucesión procesal de mi patrocinado en la posición del ejecutante de este procedimiento, y ello al amparo de las siguientes,

Hechos y consideraciones jurídicas:

1ª [COMPLETAR])

Las presentes actuaciones se iniciaron a instancia de [NOMBRE DEL SOLICITANTE], en reclamación frente a Don [COMPLETAR] de la suma de [IMPORTE] euros, siendo parte codemandada mi patrocinado, en calidad de fiador solidario del anterior.

2ª [COMPLETAR])

Por ese Tribunal se dictó auto en fecha [FECHA], en que se despachó ejecución frente a ambos condenados, al objeto de cubrir la suma de [IMPORTE] euros de principal, más otros [IMPORTE] euros presupuestados para costas e intereses, habiéndose trabado embargo sobre la vivienda del codemandado Sr. [COMPLETAR], para el pago de las sumas objeto de condena.

3ª [COMPLETAR])

El pasado día [FECHA], mi patrocinado ha hecho pago al ejecutante de la suma de [IMPORTE] euros de principal, [IMPORTE] euros de intereses de demora y [IMPORTE] euros de costas procesales, suscribiendo la ejecutante documento de pago en que se da por saldada de cualquier reclamación derivada del presente procedimiento, sin tener suma alguna otra que exigir a ninguna de las partes.

El mencionado escrito, suscrito por la representación procesal de la ejecutante, obra ya unido a las actuaciones.

4ª [COMPLETAR])

Como quiera que dicho pago a la ejecutante lo ha realizado mi patrocinado en su calidad de fiador del también demandado Sr. [COMPLETAR], estamos en el caso de interesar la sucesión procesal de mi mandante en la posición de la ejecutante, al amparo del derecho de subrogación que corresponde al fiador.

Igualmente, procede la continuación del procedimiento frente al referido Sr. [COMPLETAR], hasta hacer pago a esta parte de las sumas abonadas al ejecutante originario, así como los intereses de demora y costas procesales que se devenguen en adelante.

5ª [COMPLETAR])

Dispone el art. 17.1 LEC que "Cuando se haya transmitido, pendiente un juicio, lo que sea objeto del mismo, el adquirente podrá solicitar, acreditando la transmisión, que se le tenga por parte en la posición que ocupaba el transmitente".

Dicha transmisión se ha operado, en nuestro caso, por virtud del pago realizado al ejecutante por mi representado en virtud de su condición de fiador del otro demandado, tal y como consta en estas actuaciones. Ello confiere a mi patrocinado el derecho de subrogación en todos los derechos del acreedor, a tenor del art. 1.839 CCiv.

Ciertamente, en virtud de dicho precepto y como dispone la Sentencia del Tribunal Supremo de 13 de febrero de 1988, consecuente al pago surge la subrogación, que no es sino la mera sustitución de la persona del cedente por el cesionario [COMPLETAR], el que en razón del crédito en que se subroga es sucesor, sin que por tanto se pueda hablar del nacimiento de un derecho, como puede ser el derecho a ser indemnizado a que se refiere el art. 1.838 CCiv, y que éste sí nace, nada tiene que ver con la subrogación. Por virtud, pues, de la subrogación, el fiador que intervino en el cumplimiento de la obligación pasa a ocupar, frente al deudor, las mismas acciones que a dicho acreedor correspondían, tal y como recoge el art. 1.212 CCiv cuando señala que "la subrogación transfiere al subrogado el crédito con los derechos a él anexos, ya contra el deudor, ya contra los terceros, sean fiadores o poseedores de las hipotecas".

Esta subrogación alcanza también a las posiciones y derechos procesales, de tal forma que se encuentra justificada la sustitución procesal del fiador (hasta ahora ejecutado) en la posición del acreedor (ejecutante en este procedimiento), tal y como se interesa.

Doctrina reiterada en las SSAP de Navarra de 27 de enero de 1999 y de Girona de 23 de febrero de 1999, rec. 276/1998; AAAP Cáceres de 28 de julio de 2003, rec. 192/2003, Córdoba de 6 de febrero de 2001, rec. 436/2000. Así en la primera de ellas se manifiesta que, atendiendo a lo dispuesto en el art. 1.839 CCiv, el fiador se subroga por el pago en todos los derechos que el acreedor tenía contra el deudor; así las cosas por el pago surge la subrogación, que no es sino la mera sustitución de la persona del cedente por el cesionario (SSTS de 11 de junio de 1984 y de 13 de febrero de 1988, antes citada). El art. 1.212 CCiv establece que la subrogación confiere al subrogado el crédito con los derechos a él anexos, ya contra el deudor, ya contra terceros, siendo forzoso entender que el crédito que se transmite es el mismo en toda su integridad, extensión y contenido, sin que sufra la más mínima alteración, salvo el cambio en la persona del cedente por la del cesionario subrogado como nuevo acreedor, quien puede exigir el cumplimiento en los términos en los que los hubiera podido ejercer el anterior acreedor, pues el título mantiene todo su valor y eficacia, sin alteración alguna, pues la ley no establece diferencia alguna entre los derechos materiales y procesales anexos al crédito transferido. Y en la segunda, se concluye que la novación subjetiva del vínculo obligatorio principal, legalmente prevista, no extingue la obligación principal ni los derechos derivados de la póliza, sino que ésta mantiene su virtualidad y fuerza ejecutiva con los mismos derechos para el subrogado que los que disponía el acreedor original que recibió el pago, incluidos los intereses pactados en la póliza.

6ª [COMPLETAR])

Justificada así la transmisión del derecho de crédito actuado en este procedimiento, procede seguir los trámites previstos en el art. 17 LEC, dando audiencia de esta pretensión a la parte ejecutada, aprobando la sucesión pretendida, si la parte contraria no se opusiera, y resolviendo lo procedente si formulara oposición con arreglo a alguno de los fundamentos previsto en el art. 17.2 LEC.

Por todo lo cual,

SUPLICO AL TRIBUNAL

tenga por presentado este escrito, por realizada la solicitud que se contiene, y en mérito a lo expuesto, y previa audiencia a la parte ejecutada, acuerde la sucesión de mi patrocinado en la posición ejecutante, en sustitución de la ejecutante inicial [COMPLETAR], ordenando seguir adelante la ejecución frente a Don [COMPLETAR], hasta hacer pago a mi patrocinado de la suma de [IMPORTE] euros ya abonados, más los intereses legales y costes que se devenguen en adelante.

Es justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado

	Firma de Procurador
