---
name: demanda-declaracion-indignidad-heredero-330
description: "Redacta el escrito «Demanda de declaración de indignidad del heredero» (formulario 330 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de declaración de indignidad del heredero

> Formulario 0330 del plugin **Sucesiones** · revisado el 17-11-2026.

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
- [ ] CALLE (3 veces)
- [ ] NÚMERO (4 veces)
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] COLEGIO
- [ ] LOCALIDAD
- [ ] FECHA (4 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 25 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Doña»; «… Procuradora de los Tribunales y de Doña»; «…, dirigida por la Letrada suscrita Doña»; «…l patrimonio hereditario del difunto Don»; «…, contra Don»; «…, contra Don [COMPLETAR], domiciliado en»; «…tada y el hoy demandado son hijos de Don»; «…to de los litigantes (documentos números»; «…), así como la de defunción de Don»; «… Última Voluntad acreditativa de que Don»; «…y en estado de viudo (documentos números»; «… el fedatario público de esta ciudad Don»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 85.1 LOPJ
- art. 7.1 LEC
- arts. 248, 249.2 y 253.3 LEC
- art. 251 LEC
- art. 253.1 y 3 LEC
- art. 399 LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 394.1 LEC

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

### Formulario 0330 · Demanda de declaración de indignidad del heredero

- Año del modelo: 2020
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 45 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda de juicio ordinario en ejercicio de acción declarativa de indignidad para suceder por concurrir la causa del art. 756.1º CCiv.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: Un solo TI por partido judicial (art. 84.1 LOPJ): sobra «de los de». Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

Doña [COMPLETAR], Procuradora de los Tribunales y de Doña [COMPLETAR], provista de D.N.I. nº [Nº], y domiciliada en esta ciudad, calle [CALLE], nº [NÚMERO], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], dirigida por la Letrada suscrita Doña [COMPLETAR], colegiada nº [Nº DE COLEGIADO/A] del Iltre. Colegio de Abogados de [COLEGIO], con despacho abierto en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO:

Que por medio del presente escrito, vengo a interponer DEMANDA de JUICIO DECLARATIVO ORDINARIO ejercitando ACCIÓN DECLARATIVA DE INDIGNIDAD PARA SUCEDER respecto al patrimonio hereditario del difunto Don [COMPLETAR], contra Don [COMPLETAR], domiciliado en [COMPLETAR], calle [CALLE], con base en los siguientes:

HECHOS

PRIMERO.- Mi representada y el hoy demandado son hijos de Don [COMPLETAR], el cual falleció intestado en esta ciudad, en fecha [FECHA]

Se acredita lo anterior con las certificaciones de nacimiento de los litigantes (documentos números [COMPLETAR]), así como la de defunción de Don [COMPLETAR] y certificación del Registro de Actos de Última Voluntad acreditativa de que Don [COMPLETAR] falleció sin testar y en estado de viudo (documentos números [COMPLETAR]).

SEGUNDO.- En virtud de acta de notoriedad intervenida por el fedatario público de esta ciudad Don [COMPLETAR], de fecha [FECHA], realizada a instancia del hoy demandado Don [COMPLETAR], se declararon herederos ab intestato del fallecido Don [COMPLETAR] a sus hijos, mi representada y Don [COMPLETAR], acompañando bajo el nº [NÚMERO] de documentos copia autorizada de la referida acta de declaración de herederos ab intestato.

TERCERO.- Esto no obstante, la persona del demandado incurre en causa de indignidad para suceder, toda vez que en fecha [FECHA] el citado señor fue condenado por haber atentado contra la vida del causante, nuestro padre, Don [COMPLETAR], tal y como resulta de la sentencia cuyo testimonio acompaño bajo el nº [NÚMERO] de documentos.

CUARTO.- Es por ello por lo que esta parte ejerce acción, a fin de que se declare la indignidad para suceder a Don [COMPLETAR] por parte del demandado Don [COMPLETAR], que debe ser excluido de la sucesión hereditaria del causante, al darse la circunstancia prevista legalmente para ello, sin que conste que el demandado haya sido rehabilitado.

QUINTO.- La parte actora manifiesta que, previo a la presentación de la presente demanda, se han llevado a cabo negociaciones con la parte demandada, con el objetivo de cumplir el requisito de procedibilidad, y resolver la controversia de manera amistosa y extrajudicial. Dichas negociaciones se desarrollaron en cumplimiento de los principios de buena fe, con la intención de alcanzar una solución satisfactoria; incluyéndose entre las acciones realizadas el intercambio de comunicaciones formales mediante correspondencia escrita, en fechas [COMPLETAR], en las cuales esta parte expresó su disposición para dialogar y propuso alternativas de solución.

Finalmente, mi representado envió un requerimiento fehaciente al demandado con fecha [FECHA], fijando un plazo de 30 días naturales para llegar a un acuerdo amistoso, a través del abogado que firma este escrito, el cual fue contestado por el demandado por el mismo medio, rechazando el acuerdo/ habiendo sido solo posible un acuerdo parcial, viéndonos en la necesidad de acudir a la presente vía judicial, respecto a los extremos de la controversia en los que se mantiene la discrepancia.

Acompaño como documento nº [Nº DE DOCUMENTO], el requerimiento efectuado y como documento nº [Nº DE DOCUMENTO], la contestación del demandado.

A los hechos anteriores son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- JURISDICCIÓN Y COMPETENCIA

Radicando la competencia genérica en el orden civil de la jurisdicción, detenta la competencia objetiva y funcional la Sección Civil del Tribunal de Instancia, por aplicación de lo dispuesto en los arts. 85.1 LOPJ y 45 LEC, y territorialmente es competente el Tribunal a que me dirijo, puesto que está prevenido el fuero territorial preceptivo específico para los juicios sobre cuestiones hereditarias, con arreglo a lo previsto en el art. 52.1.4.º LEC, del lugar del último domicilio del finado, siendo de este partido la población en que se hallaba la residencia donde murió Don [COMPLETAR].

II.- CAPACIDAD Y LEGITIMACIÓN

Demandante y demandado, personas físicas, tienen capacidad para ser parte (art. 6.1.1.º LEC), titular de facultades y cargas del proceso, y asimismo plena capacidad procesal, al ser mayores de edad, sin limitación de ejercicio válido de derechos civiles, o para comparecer en juicio, en términos del art. 7.1 LEC, pretendiendo el actor y siendo pretendido el demandado, en sus respectivos nombres y derechos.

Corresponde la legitimación activa directa a mi mandante, habida cuenta su condición de legítimo heredero del fallecido Don [COMPLETAR], y está legitimada pasivamente de forma directa la demandada, en su condición de incapaz de suceder a su padre por causa de indignidad.

III.- PROCEDIMIENTO

La presente demanda deberá sustanciarse por las normas del juicio ordinario, a tenor de lo prevenido en los arts. 248, 249.2 y 253.3 LEC, toda vez que ningún criterio de atribución preferente de la materia objeto del proceso resulta aplicable, puesto que la regla 12.ª del art. 251 LEC, referida a pleitos relativos a una herencia, se corresponde con condenas afectantes a los bienes o masas patrimoniales, y no a la mera declaración de causa de indignidad para suceder.

IV.- CUANTÍA

Cumpliendo lo prevenido en el art. 253.1 y 3 LEC, hacemos constar que la cuantía de esta demanda es indeterminada, al no existir inventario de activo y pasivo que pudiera conformar el caudal relicto de la herencia

V.- REQUISITOS FORMALES

No aparecen, aparte de los requisitos genéricos de la demanda en juicio ordinario del art. 399 LEC, otros de carácter formal cuya falta, por el tipo de acción, invalidarían el proceso para pronunciarse sobre el fondo del asunto.

VI.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VII.- FONDO DEL ASUNTO

La indignidad para suceder es una causa de exclusión de una determinada herencia. La define ALBALADEJO como la tacha con que la Ley marca a las personas que han cometido determinados actos especialmente reprensibles, en virtud de la que su autor queda inhabilitado para suceder al causante que los padeció, al menos que éste lo rehabilite. Esta inhabilitación comprende tanto la sucesión testada como la intestada, a título de heredero o como legatario, e incluso la forzosa.

El fundamento y la naturaleza de la indignidad es de sanción civil a hechos que son gravemente perjudiciales -materiales o morales- al causante, y tal sanción no satisface ni reintegra el derecho violado. Se fundamenta en la norma legal, más que en la presunta voluntad del causante, si bien éste puede evitar los efectos que establece la ley para la indignidad mediante la rehabilitación.

Establece el art. 756.1º CCiv, que resulta incapaz de suceder por causa de indignidad "El que fuera condenado por sentencia firme por haber atentado contra la vida, o a pena grave por haber causado lesiones o por haber ejercido habitualmente violencia física o psíquica en el ámbito familiar al causante, su cónyuge, persona a la que esté unida por análoga relación de afectividad o alguno de sus descendientes o ascendientes".

En el caso que nos ocupa, el delito por el que resultó condenado el demandado Sr. es encuadrable dentro del Título I del Libro II del Código Penal, bajo el epígrafe "Del homicidio y sus formas", siendo la víctima el causante, por lo que es evidente que se da la causa prevista en el precepto que alegamos.

El profesor Puig Peña mantiene, con acertado criterio, que existirá esta causa de indignidad tanto si se ha consumado el delito, como si éste ha quedado frustrado o en grado de tentativa, ya que lo realmente importante es la intencionalidad del homicida y sucesor del causante.

Entiende la mayoría de la Doctrina que el indigno podrá ser llamado a la herencia del causante, pero quien esté interesado en ello, podrá anular dicha sucesión; en cuyo caso se borrarán retroactivamente las consecuencias de haber sido llamado el indigno a la sucesión.

VIII.- COSTAS

Conforme al principio del art. 394.1 LEC, del vencimiento objetivo, las costas irrogadas a esta parte en el juicio declarativo en la primera instancia se han de pronunciar a cargo del demandado.

En su virtud,

SUPLICO AL TRIBUNAL:

Que, habiendo por presentado este escrito con sus documentos y copias, se sirva admitirlo, me tenga por parte en la representación que ostento de Doña [COMPLETAR] y por interpuesta demanda en ejercicio de acción de declaración de indignidad para suceder frente a Don [COMPLETAR], emplazarle para que comparezca y conteste, seguir el procedimiento por sus trámites y, en su momento, dictar sentencia por la que, estimando íntegramente la demanda, declare que el demandado Don [COMPLETAR] ha incurrido en la causa de indignidad prevista en el art. 756.1º CCiv y que, en consecuencia, es indigno de suceder en la herencia de su finado padre, Don [COMPLETAR], perdiendo todo derecho a su legítima, con expresa imposición de las costas procesales al demandado.

Es justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

	Firma de Procurador/a
