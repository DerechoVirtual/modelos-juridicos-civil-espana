---
name: demanda-verbal-contra-comunidad-indemnizacion-cesar-306
description: "Redacta el escrito «Demanda verbal contra la comunidad por indemnización al cesar al administrador» (formulario 306 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda verbal contra la comunidad por indemnización al cesar al administrador

> Formulario 0306 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] IMPORTE (5 veces)
- [ ] FECHA (3 veces)
- [ ] Nº DE DOCUMENTO (5 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… fui designado Administrador de la Finca»; «…ltima de estas Juntas es la celebrada el»; «…de»; «…de [COMPLETAR] de»; «…e efectividad hasta el mismo día del año»; «…mino. Se aportan como documentos números»; «…y»; «…puesto aprobado en la Junta ordinaria de»; «…iante correspondencia escrita, en fechas»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 45 LEC
- art. 85.1 LOPJ
- art. 250.2 LEC
- art. 13.3 LPH
- art. 25 LEC
- arts. 23 y 31 LEC
- art. 253.1 LEC
- art. 251 LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 13.7 LPH
- art. 1.729 CCiv
- art. 1.124 CCiv
- art. 394 LEC

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

### Formulario 0306 · Demanda verbal contra la comunidad por indemnización al cesar al administrador

- Año del modelo: 2020
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 27 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda de reclamación a la Comunidad de indemnización por cese del Administrador.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dª. [NOMBRE Y APELLIDOS], Procurador/a. de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], como se acredita debidamente con escritura de poder que se acompaña, bajo la dirección Letrada del Abogado D./Dña. [NOMBRE Y APELLIDOS], comparezco ante el Tribunal y como en derecho mejor proceda, DIGO:

Que por medio del presente escrito formulo demanda de JUICIO VERBAL contra la Comunidad de Propietarios, en la persona de su representante legal, de la finca sita en [LOCALIDAD], en reclamación del pago de [IMPORTE] euros, que corresponden a los honorarios profesionales dejados de satisfacer por dicha Comunidad al actor.

La demanda se basa en los siguientes:

HECHOS

PRIMERO.- En virtud de acuerdo adoptado en la Junta de Propietarios celebrada el día [FECHA], fui designado Administrador de la Finca [COMPLETAR], sustituyendo al anterior Administrador, que cesó de tal cargo debido a su fallecimiento.

Se compaña copia del acta de designación acordada en la Junta como documento nº [Nº DE DOCUMENTO]

SEGUNDO.- Tal y como consta en dicha Acta, el nombramiento tenía una duración anual, con posibilidad de prórroga. Tras el transcurso de la primera anualidad el contrato ha venido prorrogándose en todas las Juntas anuales de propietarios, siempre con carácter anual.

La última de estas Juntas es la celebrada el [COMPLETAR] de [COMPLETAR] de [COMPLETAR], por lo que mi nombramiento tiene efectividad hasta el mismo día del año [COMPLETAR]. Se aporta copia del Acta de la última Junta como documento nº [Nº DE DOCUMENTO]

TERCERO.- Con fecha [FECHA], el nuevo Presidente de la Comunidad, sin tener en cuenta el plazo fijado de duración del cargo, envió una carta a mi representado comunicándole la decisión de prescindir de sus servicios, sin ser convocada Junta para ello ni exponer motivos concretos, más allá de su mera voluntad. Ante dicha comunicación el actor se opuso, alegando de una parte que la decisión de cese ha de ser tomada por la Comunidad de Propietarios y de otra que no está facultada la Comunidad para romper la relación contratual entre las partes establecida antes de su término.

Se aportan como documentos números [COMPLETAR] y [COMPLETAR] el escrito de comunicación del cese y la contestación de mi representado.

CUARTO.- La Comunidad demandada ha dejado de abonar la cantidad que aquí se reclama, pues del importe fijado en el Presupuesto anual de [IMPORTE] euros sólo se ha cobrado la cuantía de [IMPORTE] euros. Se adjunta este Presupuesto aprobado en la Junta ordinaria de [COMPLETAR] como documento nº [Nº DE DOCUMENTO]

QUINTO.- La parte actora manifiesta que, previo a la presentación de la presente demanda, se han llevado a cabo negociaciones con la parte demandada, con el objetivo de cumplir el requisito de procedibilidad, y resolver la controversia de manera amistosa y extrajudicial. Dichas negociaciones se desarrollaron en cumplimiento de los principios de buena fe, con la intención de alcanzar una solución satisfactoria; incluyéndose entre las acciones realizadas el intercambio de comunicaciones formales mediante correspondencia escrita, en fechas [COMPLETAR], en las cuales esta parte expresó su disposición para dialogar y propuso alternativas de solución.

Finalmente, mi representado envió un requerimiento fehaciente al demandado con fecha [FECHA], fijando un plazo de 30 días naturales para llegar a un acuerdo amistoso, a través del abogado que firma este escrito, el cual fue contestado por el demandado por el mismo medio, rechazando el acuerdo/ habiendo sido solo posible un acuerdo parcial, viéndonos en la necesidad de acudir a la presente vía judicial, respecto a los extremos de la controversia en los que se mantiene la discrepancia.

Acompaño como documento nº [Nº DE DOCUMENTO], el requerimiento efectuado y como documento nº [Nº DE DOCUMENTO], la contestación del demandado.

A los anteriores hechos son de aplicación los siguientes

FUNDAMENTOS JURÍDICOS

I.- COMPETENCIA.

Es competente objetivamente el Tribunal al que tengo el honor de dirigirme, de conformidad con el art. 45 LEC, en cuanto dispone, en armonía con el art. 85.1 LOPJ, que a las secciones civiles de los tribunales de instancia corresponde el conocimiento, en primera instancia, de todos los asuntos civiles que por disposición legal expresa no se hallen atribuidos a otro tribunales, e igualmente lo es por razón de territorio, dado que en esta circunscripción radica la finca, siendo la materia litigiosa de propiedad horizontal, conforme al art. 52.1.8º LEC.

II.- PROCEDIMIENTO.

Deberán seguirse los trámites previstos para el juicio verbal, por ser la cuantía del presente proceso inferior a 15.000 euros, según dispone el art. 250.2 LEC, y no llevar asignado cauce procesal por materia la pretensión (1).

III.- LEGITIMACIÓN ACTIVA Y PASIVA.

En cuanto a la activa corresponde a mi mandante, por ser el directamente perjudicado y el Presidente lo está pasivamente como representante legal de la Comunidad, conforme al art. 13.3 LPH.

IV.- CAPACIDAD Y REPRESENTACIÓN.

Mi mandante es persona física, mayor de edad sin discapacidad, que tiene capacidad para ser parte y para comparecer, por sí, en su propio nombre y derecho, en este juicio (art. 6.1.1º y 7.1 LEC).

La Comunidad carece de personalidad jurídica, pero tiene capacidad para ser parte y capacidad procesal por específica disposición legal, a través de sus órganos (arts. 6.1.5º y 7.6 LEC).

V.- POSTULACIÓN Y DEFENSA.

El actor ha otorgado poder notarial al Procurador/a de los Tribunales que encabeza este escrito, habilitado en el partido del Tribunal, cuya copia auténtica se ha aportado, general para pleitos (art. 25 LEC), siendo redactada y firmada la demanda por el abogado ejerciente colegiado que dirige el asunto y se identifica en el encabezamiento, según resulta preceptivo conforme a los arts. 23 y 31 LEC.

VI.- CUANTÍA DE LA DEMANDA.

La cuantía de la demanda a los efectos de lo dispuesto en el art. 253.1 LEC, es la de [IMPORTE] euros en aplicación de la regla 1.ª del art. 251 LEC, según el cual, si se reclama una cantidad de dinero determinada, la cuantía de la demanda estará representada por dicha cantidad, que es la valoración por la reparación de los daños causados,

VII. CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VIII.- FUNDAMENTOS MATERIALES.

El art. 13.7 LPH, que establece que los nombramientos son anuales, sin perjuicio de la facultad de la Junta para remover en cualquier momento.

El art. 1.729 CCiv, en cuanto a la obligación de indemnizar por el mandante en cuantos daños y perjuicios haya ocasionado al mandatario, sin culpa o negligencia del mismo.

El art. 1.124 CCiv, que igualmente obliga a satisfacer indemnización por incumplimiento contractual de una de las partes.

IX.- COSTAS.

El total vencimiento de la parte demandada, unida a su temeridad y mala fe determina, según el art. 394 LEC que ésta deba satisfacer todas las costas del presente procedimiento.

Por todo lo expuesto,

Por lo expuesto,

SUPLICO AL TRIBUNAL

que, teniendo por presentado este escrito, junto con los documentos que se acompañan, se admita la demanda y se emplace a la parte demandada, siguiendo la correspondiente tramitación procesal, a fin de que en su día se dicte Sentencia condenando a la Comunidad de Propietarios de la finca sita en [LOCALIDAD] al pago de [IMPORTE] euros, que corresponden al importe dejado de percibir por el demandante por el cese injustificado en su puesto de Administrador de dicha Comunidad, con expresa imposición de costas.

Es justicia que solicito en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma de Abogado/a

	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) El art. 249.1.8º LEC se refiere exclusivamente a las acciones que concede la propia Ley de Propiedad Horizontal, bien a la Junta o a los propietarios. Por lo tanto, cuando interviene un tercero, ajeno completamente a la Comunidad y por cuestiones no contempladas en la Ley especial, ya sea como demandante o demandado, hay que ajustarse en todos los aspectos a las normas generales y no aplicar la reserva del juicio ordinario.
