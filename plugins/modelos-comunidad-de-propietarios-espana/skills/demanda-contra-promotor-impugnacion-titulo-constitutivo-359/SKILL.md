---
name: demanda-contra-promotor-impugnacion-titulo-constitutivo-359
description: "Redacta el escrito «Demanda contra el promotor por impugnación del título constitutivo de propiedad horizontal» (formulario 359 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda contra el promotor por impugnación del título constitutivo de propiedad horizontal

> Formulario 0359 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] NÚMERO (4 veces)
- [ ] CALLE (3 veces)
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] FECHA (4 veces)
- [ ] LUGAR
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de la calle [CALLE] de»; «…ión técnica del Letrado en ejercicio Don»; «… concreto dicho documento tiene fecha de»; «…ueble, señalados como documentos números»; «…iante correspondencia escrita, en fechas»; «…de la calle [CALLE] de»; «…nº [NÚMERO] de»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 45 LEC
- art. 85.1 LOPJ
- art. 13.3 LPH
- art. 7.1 LEC
- art. 25 LEC
- arts. 23 y 31 LEC
- art. 253.3 LEC
- art. 5 de la Ley Orgánica 1/2025
- arts. 6.4 y 7.1 CCiv
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

### Formulario 0359 · Demanda contra el promotor por impugnación del título constitutivo de propiedad horizontal

- Año del modelo: 2019
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 29 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda de juicio ordinario solicitando nulidad del otorgamiento del título constitutivo de propiedad horizontal dirigido contra el Promotor; sólo tiene por objeto dejar sin efecto las cuotas o las reglas estatutarias, no establecer nuevos coeficientes o normas de funcionamiento, pues para esto se necesita del acuerdo unánime de la Junta, sin intervención judicial, o bien dirigir la demanda contra el resto de comuneros, que deben ser partes en el juicio.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, que actúa en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], en su condición de Presidente de la Comunidad de Propietarios del edificio señalado con el n.º [NÚMERO] de la calle [CALLE] de [COMPLETAR], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], bajo la dirección técnica del Letrado en ejercicio Don [COMPLETAR], con despacho profesional abierto en esta capital sito en [LOCALIDAD], ante el Tribunal comparezco y como mejor proceda en Derecho, DIGO:

Que mediante el presente escrito y siguiendo instrucciones de mi mandante formulo DEMANDA DE JUICIO ORDINARIO SOBRE ACCIÓN DE PROPIEDAD HORIZONTAL contra D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], con la finalidad de que se declare QUE CUANDO OTORGÓ LA ESCRITURA PÚBLICA ESTABLECIENDO LAS CUOTAS DE PARTICIPACIÓN, ASÍ COMO LOS ESTATUTOS DEL INMUEBLE, NO GOZABA DE LA CONDICIÓN DE DUEÑO ÚNICO, POR LO QUE DEBEN SER DECLARADOS NULOS ESTOS DOCUMENTOS Y LAS CORRESPONDIENTES INSCRIPCIONES REGISTRALES.

Fundamento la misma en los siguientes hechos y consideraciones jurídicas:

HECHOS

PRIMERO.- El actor es Presidente de la Comunidad de Propietarios del Edificio sito en [LOCALIDAD] y está facultado para el ejercicio de esta acción, en virtud del acuerdo adoptado en la Junta de Propietarios de fecha [FECHA], adjuntándose copia del Acta como documento n.º [NÚMERO].

SEGUNDO.- Que el Promotor y anterior propietario del edificio otorgó la correspondiente escritura pública determinando las cuotas de propiedad y estableciendo normas especiales de funcionamiento comunitario cuando ya no era el dueño único del inmueble.

En concreto dicho documento tiene fecha de [COMPLETAR] y ya entonces se habían vendido en firme la mayor parte de pisos y locales. Se acredita la anterior manifestación con copia de dicha Escritura Pública y los contratos de compraventa de varias fincas del inmueble, señalados como documentos números [COMPLETAR].

TERCERO.- En dichos contratos, todos de fecha anterior al otorgamiento del Título, no figura ninguna autorización ni apoderamiento al Promotor, por lo que su comparecencia notarial, indicando que era el dueño único del inmueble, está viciada de nulidad.

CUARTO.- En efecto, los propietarios ya eran propietarios al momento de otorgarse dichos títulos por lo que, en principio, tendrían que haber concurrido a tal otorgamiento.

El hecho de que con fecha posterior los propietarios tuvieran que firmar la escritura pública, donde se hacía constar de forma genérica que «se conoce y acepta el Título», no suponía nada más que una cláusula de estilo o de adhesión, pues es claro que en el citado documento público no se acompañan como anexo dichos Estatutos, habiendo utilizado el abuso de confianza para hacer firmar una escritura que podía significar una ratificación de un documento ilegal, sin un claro conocimiento por parte de los que comparecen como adquirentes.

Se acompaña copia de algunas de estas escrituras, todas iguales, con esa aceptación no querida expresamente por los compradores.

QUINTO.- La mencionada firma se trató en definitiva de una forma de coacción, toda vez que de negarse a firmar la escritura, no se entregarían las llaves, con los consiguientes perjuicios para los compradores.

SEXTO.- La parte actora manifiesta que, previo a la presentación de la presente demanda, se han llevado a cabo negociaciones con la parte demandada, con el objetivo de cumplir el requisito de procedibilidad, y resolver la controversia de manera amistosa y extrajudicial. Dichas negociaciones se desarrollaron en cumplimiento de los principios de buena fe, con la intención de alcanzar una solución satisfactoria; incluyéndose entre las acciones realizadas el intercambio de comunicaciones formales mediante correspondencia escrita, en fechas [COMPLETAR], en las cuales esta parte expresó su disposición para dialogar y propuso alternativas de solución.

Finalmente, mi representado envió un requerimiento fehaciente al demandado con fecha [FECHA], fijando un plazo de 30 días naturales para llegar a un acuerdo amistoso, a través del abogado que firma este escrito, el cual fue contestado por el demandado por el mismo medio, rechazando el acuerdo/ habiendo sido solo posible un acuerdo parcial, viéndonos en la necesidad de acudir a la presente vía judicial, respecto a los extremos de la controversia en los que se mantiene la discrepancia.

Acompaño como documento nº [Nº DE DOCUMENTO], el requerimiento efectuado y como documento nº [Nº DE DOCUMENTO], la contestación del demandado.

A los anteriores hechos se les deben aplicar los siguientes

FUNDAMENTOS JURÍDICOS

I.- COMPETENCIA.

Es competente objetivamente el Tribunal al que tengo el honor de dirigirme, de conformidad con el art. 45 LEC, en cuanto dispone, en armonía con el art. 85.1 LOPJ, que a los Tribunales de Instancia corresponde el conocimiento, en primera instancia, de todos los asuntos civiles que por disposición legal expresa no se hallen atribuidos a otro tribunales, e igualmente lo es por razón de territorio, dado que en esta circunscripción radica la finca, siendo la materia litigiosa de propiedad horizontal, conforme al art. 52.1.8.º LEC.

II.- PROCEDIMIENTO.

El modelo de procedimiento con arreglo al que deberá sustanciará este proceso, será el determinado para el Juicio Ordinario regulado en los arts. 399 y ss. LEC, conforme a lo establecido para esta materia de propiedad horizontal en el art. 249.1.8.º LEC, sin que esta acción suponga reclamación de cantidad.

III.- LEGITIMACIÓN ACTIVA Y PASIVA.

En cuanto a la activa corresponde a mi mandante, a tenor del art. 13.3 LPH; y en cuanto a la legitimación pasiva corresponde al demandado por haber sido quien otorgó el Título que ahora se impugna.

IV.- CAPACIDAD Y REPRESENTACIÓN.

Mi mandante es el representante legal de la entidad sin personalidad que es la comunidad de propietarios del edificio señalado con n.º [NÚMERO] de la calle [CALLE] de [COMPLETAR], por lo que detentando capacidad para ser parte por ministerio de la ley dicha comunidad, la capacidad procesal, o para comparecer en juicio, corresponde a su Presidente (arts. 6.1.5.º y 7.6 LEC).

El demandado es persona física, mayor de edad, respecto de las que no consta limitación de ejercicio de derechos civiles, por lo que detenta capacidad para ser parte (art. 6.1.1.º LEC), y capacidad procesal, o de obrar en este concreto juicio (art. 7.1 LEC), siempre que cumpla los oportunos requisitos de postulación para oponerse a la presente demanda.

V.- POSTULACIÓN Y DEFENSA.

El actor ha otorgado poder notarial al Procurador de los Tribunales que encabeza este escrito, habilitado en el partido del Tribunal, cuya copia auténtica se ha aportado, general para pleitos (art. 25 LEC), siendo redactada y firmada la demanda por el abogado ejerciente colegiado que dirige el asunto y se identifica en el encabezamiento, según resulta preceptivo conforme a los arts. 23 y 31 LEC.

VI.- CUANTÍA.

La cuantía de este procedimiento es indeterminada, por darse las circunstancias del art. 253.3 LEC.

VII.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VIII.- FONDO DEL ASUNTO.

Como ha quedado expuesto en la parte fáctica de esta demanda, en fecha [FECHA], el promotor D./Dña. [NOMBRE Y APELLIDOS], no era propietario único del edificio, por lo que no podía otorgar unilateralmente el título constitutivo de declaración de obra nueva y división horizontal, sin el consentimiento de los propietarios de los pisos y locales en el otorgamiento de la escritura pública.

Conforme al art. 5, apartados 2 y 3, LPH, solamente cabe que se puedan fijar los coeficientes o cuotas y las reglas especiales por el dueño único, naturalmente cuando así ocurra, pero no si en el momento del otorgamiento hay ya varios propietarios, que deben de mostrar su conformidad unánime, lo que no ha sucedido en este caso.

El Promotor ha actuado en fraude de Ley y asimismo con abuso y mala fe, en contra de lo dispuesto en los arts. 6.4 y 7.1 CCiv.

IX.- COSTAS.

Conforme al art. 394 LEC las costas han de imponerse a la parte demandada, por principio objetivo del vencimiento.

Por todo ello,

SUPLICO AL TRIBUNAL

que, teniendo por presentado este escrito, por el/la Letrado/a de la Administración de Justicia se admita la demanda y se emplace a la parte demandada, siguiendo la correspondiente tramitación procesal, a fin de que finalmente por el tribunal se dicte Sentencia declarando LA NULIDAD DE LA ESCRITURA PÚBLICA EN QUE SE ESTABLECEN LAS CUOTAS DE PARTICIPACIÓN, COMO ASÍ TAMBIÉN DEL ESTATUTO de la comunidad otorgado en relación al inmueble de la c/ [CALLE] nº [NÚMERO] de [COMPLETAR], Y SUS CORRESPONDIENTES INSCRIPCIONES EN EL REGISTRO DE LA PROPIEDAD, con expresa imposición de costas.

Por ser de justicia que solicito en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a
