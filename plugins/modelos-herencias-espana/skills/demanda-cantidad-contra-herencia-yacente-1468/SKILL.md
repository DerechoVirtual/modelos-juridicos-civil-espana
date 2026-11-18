---
name: demanda-cantidad-contra-herencia-yacente-1468
description: "Redacta el escrito «Demanda de cantidad contra herencia yacente» (formulario 1468 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de cantidad contra herencia yacente

> Formulario 1468 del plugin **Sucesiones** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] LOCALIDAD (4 veces)
- [ ] IMPORTE (8 veces)
- [ ] FECHA
- [ ] NÚMERO
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 25 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…do/a de la Administración de Justicia de»; «…que acompaño»; «…ntervención profesional del procurador D»; «…a intervención profesional del abogado D»; «…en su caso, los ignorados herederos de D»; «… en el domicilio del hijo del causante D»; «…, o bien de la viuda Dª»; «…los siguientes: HECHOS Los demandantes D»; «…a representación y defensa técnica por D»; «…on las respectivas facturas al cliente D»; «…minutas que se acompañan como documentos»; «…cimiento del fallecimiento del cliente D»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 6.1.4 de la LEC
- artículos 657 y 659 del Código Civil
- art. 50.1 de la LEC
- art. 72 de la LEC
- art. 6.1.4 y 7.5 de la LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 1100, 1101 y 1108 del Código Civil
- artículo 394 LEC
- arts. 251 y 252 de la LEC

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

### Formulario 1468 · Demanda de cantidad contra herencia yacente

- Año del modelo: 2014
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 46 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Parte
HECHOS
FUNDAMENTOS DE DERECHO
Suplico
Otro sí digo I
Abono de la tasa
Firmas

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales en representación de D./Dña. [NOMBRE Y APELLIDOS], y de D/Dña. [NOMBRE Y APELLIDOS], según acredito por certificación del registro electrónico de apoderamientos judiciales que acompaño o mediante apoderamiento apud acta otorgado ante el/la Letrado/a de la Administración de Justicia de [COMPLETAR] que acompaño [COMPLETAR] bajo la dirección letrada de D/Dª [NOMBRE Y APELLIDOS], Abogado/a del Iltre. Colegio de [LOCALIDAD], ante el Tribunal comparezco y como mejor en derecho proceda formulo demanda de juicio ordinario en ejercicio acumulado de la acción de reclamación por derechos y suplidos derivada de la intervención profesional del procurador D [COMPLETAR] y de la acción de reclamación de honorarios derivada de la intervención profesional del abogado D [COMPLETAR], contra la HERENCIA YACENTE o, en su caso, los ignorados herederos de D [COMPLETAR], pudiendo ser emplazados en el domicilio del hijo del causante D [COMPLETAR], sito en [LOCALIDAD], o bien de la viuda Dª [COMPLETAR], sito en [LOCALIDAD], en base a los siguientes:

HECHOS

Los demandantes D [COMPLETAR] y D. son, respectivamente, procurador de los tribunales y abogado, y en dicha condición profesional les fue encomendada la representación y defensa técnica por D [COMPLETAR] en los siguientes procesos: ().

Dichos procesos finalizaron con el siguiente resultado (:) habiendo cumplido los actores escrupulosamente su encargo profesional.

Finalizado los procesos que el demandado había encomendado a mis representados, los demandantes remitieron las respectivas facturas al cliente D [COMPLETAR] a fin de percibir sus derechos y honorarios que, ascendían, respectivamente a la cantidad de [IMPORTE] euros en concepto de derechos y suplidos del procurador y a la cantidad de [IMPORTE] euros en concepto de honorarios de abogado, de acuerdo a las respectivas minutas que se acompañan como documentos [COMPLETAR], donde constan detalladamente los correspondientes importes, una vez detraídas la provisión de fondos por importe de [IMPORTE] euros entregada al procurador y la de [IMPORTE] euros que fue entrega a cuenta del abogado, según resulta reflejado en las minutas.

Transcurridos unos días desde la remisión de las facturas, los demandantes tuvieron conocimiento del fallecimiento del cliente D [COMPLETAR], el pasado día [FECHA], lo cual se acredita mediante certificado de defunción que se acompaña como documento número

Ante este hecho, se dirigieron a los familiares más directos del fallecido para comunicarles la pendencia de las facturas, dándoles todo tipo de facilidades para poder abordar su pago, pero ni la viuda ni el hijo han dado respuesta alguna pese al tiempo transcurrido.

En atención a lo anterior, los demandantes se ven en la obligación de ejercitar la acción jurisdiccional para la percepción de sus respectivos importes adeudados, la cual dirigen contra la herencia yacente del finado, o sus ignorados herederos, al desconocer esta parte la posible identidad o existencia de herederos, siendo reiterada la interpretación de los Tribunales en cuanto a la posibilidad de que la herencia yacente pueda ser parte en el procedimiento, de conformidad a lo que dispone el art. 6.1.4 de la LEC, al contemplar expresamente la capacidad para ser parte que en el proceso civil pueden ostentar las masas patrimoniales o los patrimonios separados que carezcan transitoriamente de titular, señalando en el artículo siguiente que en estos casos la comparecencia en juicio se efectuará por medio de quienes legalmente les administren (art. 7.5), como habían reiterado las SSTS 20-9-1982, 12-3-1987 y 31-1-1994 ,entre otras. Como se reitera en la interpretación de nuestros tribunales, esta situación interina y provisional que supone la herencia yacente [COMPLETAR], es decir, la existencia de un patrimonio cuyo titular ha fallecido y aún no se han realizado todas las operaciones para adjudicarlo a los herederos, no impide que los procesos que se sigan con el fallecido se paralicen, o no puedan iniciarse, porque se permite dirigir las actuaciones contra la herencia yacente [COMPLETAR], en la persona de sus herederos, y estos pueden iniciar los procesos necesarios en defensa de la misma

Por tanto, se dirige la acción contra «la herencia yacente o ignorados herederos» del deudor D [COMPLETAR] de cuyo fallecimiento se aporta acreditación documental por esta parte, designándose, a efectos de notificaciones y demás actos de comunicación, los domicilios que constan a esta parte donde viven sus familiares más cercanos –esposa e hijo-, quienes lógicamente parece que pueden estar llamados a la herencia o más directamente interesados en el asunto.

En cuanto a la procedencia de las acciones que se acumulan, debe indicarse que ambas se fundan en los mismos hechos –actuación profesional de representación procesal y defensa en los procesos número [NÚMERO] en los que fue parte el fallecido D – y, desde el punto de vista jurídico, son procedentes por aplicación, respectivamente, de las normas del contrato de mandato y del contrato de arrendamiento de servicios, habiéndose pactado que los profesionales serían retribuidos conforme a la aplicación de las normas de los Colegios de Procuradores y Abogados de [COMPLETAR], según consta en el documento de encargo aceptado por el cliente que se acompaña como documento número

En cuanto a la procedencia del pronunciamiento condenatorio de la herencia yacente de D [COMPLETAR] o, en su caso, de quienes resulten ser sus herederos, son de aplicación los preceptos del Código Civil en relación a la herencia, singularmente los artículos 657 y 659 del Código Civil, de los cuales resulta que la herencia yacente o, en su caso, los herederos deben asumir las obligaciones del causante, que en este caso ascienden a la cantidad de [IMPORTE] euros como ha quedado expuesto, debiendo incrementarse con los intereses correspondientes. [COMPLETAR].

Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

Competencia

Corresponde a los Tribunales de Instancia de [LOCALIDAD] conforme a lo que dispone el art. 50.1 de la LEC, que asigna competencia territorial a los Tribunales del domicilio actual de los demandados.

Acumulación de acciones

Es de aplicación el art. 72 de la LEC al ser conexas las acciones ejercitadas simultáneamente contra la herencia yacente o los ignorados herederos de D [COMPLETAR]

Legitimación

Le corresponde a esta parte la activa, respectivamente, a D [COMPLETAR] como procurador que actuó en cumplimiento del contrato de mandato, y a D. [NOMBRE Y APELLIDOS], como abogado que actuó en cumplimiento del arrendamiento de servicios pactado. En cuanto a la legitimación pasiva corresponde a la herencia yacente del causante, conforme a lo que disponen el art. 6.1.4 y 7.5 de la LEC en relación con los artículos 657 y 659 del Código Civil.

Procedimiento

Es el juicio ordinario con fundamento en el artículo 249.2º LEC al exceder la cuantía de este proceso de 15.000 euros.

Cumplimiento de los requisitos de procedibilidad

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Acciones acumuladas de reclamación de cantidad por contrato de mandato y de arrendamiento de servicios

Se ejercitan de forma acumulada la acciones contra la herencia yacente, conforme a lo dispuesto en el art. 1709 y ss. del Código Civil (mandato) y 1544 y concordantes del mismo texto legal (arrendamiento de servicios).

Intereses

Son de aplicación el art. 1100, 1101 y 1108 del Código Civil.

En materia de costas, es de aplicación el artículo 394 LEC debiendo imponerse a las demandadas.

En base a lo anterior,

SUPLICO al Tribunal que tenga por presentada la presente demanda con los documentos a ella adjuntos y en la representación que ostento se tenga por formulada demanda acumulada de reclamación de cantidad por D [COMPLETAR] y D [COMPLETAR] frente a la HERENCIA YACENTE –o, en su caso, ignorados herederos- de D y, en su virtud, tras los trámites legales, se dicte sentencia por la que por la que se condene a la demandada a indemnizar al procurador D [COMPLETAR] en la cantidad de [IMPORTE] euros, y a indemnizar al abogado D [COMPLETAR] en la cantidad de [IMPORTE] euros, con más los intereses correspondientes, todo ello con imposición de costas a la demandada.

OTROSÍ DIGO I que, de conformidad con lo dispuesto en los arts. 251 y 252 de la LEC se fija la cuantía del presente proceso en [IMPORTE] euros.

SUPLICO AL TRIBUNAL que tenga por hechas las anteriores manifestaciones a los efectos pertinentes y por acompañado el documento justificativo del abono de la tasa.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma Abogado y Procurador

========================================================================
