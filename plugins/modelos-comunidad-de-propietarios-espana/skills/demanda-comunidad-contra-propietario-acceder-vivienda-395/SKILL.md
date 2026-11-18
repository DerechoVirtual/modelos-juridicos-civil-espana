---
name: demanda-comunidad-contra-propietario-acceder-vivienda-395
description: "Redacta el escrito «Demanda de la comunidad contra un propietario para acceder a su vivienda o local» (formulario 395 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de la comunidad contra un propietario para acceder a su vivienda o local

> Formulario 0395 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (8 veces)
- [ ] NÚMERO (11 veces)
- [ ] CALLE (4 veces)
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] FECHA (4 veces)
- [ ] LUGAR
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…de la calle [CALLE] de»; «…demandado es titular del local comercial»; «…iante correspondencia escrita, en fechas»; «…de la calle [CALLE] de»; «…ones que exija el servicio del inmueble.»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 9.1.d) LPH
- art. 45 LEC
- art. 85.1 LOPJ
- art. 13.3 LPH
- art. 7.1 LEC
- art. 25 LEC
- arts. 23 y 31 LEC
- art. 253.1 LEC
- art. 253.3 LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 33 CE
- art. 9.1 d) LPH
- art. 18.2 CE
- art. 394 LEC
- arts. 335 y 336.1 LEC

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

### Formulario 0395 · Demanda de la comunidad contra un propietario para acceder a su vivienda o local

- Año del modelo: 2019
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 39 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda instada por comunidad de propietarios solicitando acceso a vivienda o local de la propiedad horizontal en base al art. 9.1.d) LPH.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a. de los Tribunales, que actúa en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], en su condición de Presidente de la Comunidad de Propietarios del edificio señalado con el n.º [NÚMERO] de la calle [CALLE] de [COMPLETAR], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO]; bajo la dirección técnica del Letrado en ejercicio D./Dña. [NOMBRE Y APELLIDOS], con despacho profesional abierto en esta capital sito en [LOCALIDAD], ante el Tribunal comparezco y como mejor proceda en Derecho (1), DIGO:

Que mediante el presente escrito y siguiendo instrucciones de mi mandante formulo DEMANDA DE JUICIO ORDINARIO SOBRE ACCIÓN DE PROPIEDAD HORIZONTAL contra D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], a fin de que se declare la NECESIDAD DE ENTRAR EN SU LOCAL PARA PODER LLEVAR A CABO LA REPARACIÓN DE LAS ARQUETAS COMUNITARIAS.

Fundamento la misma en los siguientes hechos y consideraciones jurídicas:

HECHOS

PRIMERO.- Mi mandante es Presidente de la Comunidad de Propietarios del edificio señalado con el n.º [NÚMERO], de la calle [CALLE], según consta en el acta de la Junta de Propietarios que se acompaña como documento n.º [NÚMERO].

SEGUNDO.- El demandado es titular del local comercial [COMPLETAR], sito en la planta sótano del edificio en el que se asienta la comunidad de propietarios demandante.

El referido local constituye la finca registral n.º [NÚMERO] del Registro de la Propiedad de esta ciudad, figurando el demandado como propietario del mismo de conformidad con la nota informativa del mencionado registro que se acompaña bajo el n.º [NÚMERO] de documentos.

TERCERO.- En dicho local se encuentra una arqueta que da acceso a las tuberías por las que discurren las canalizaciones comunitarias.

Se aportan como documento n.º [NÚMERO] plano de dicha arqueta.

CUARTO.- Que como consecuencia de los atascos producidos en las bajantes comunitarias es preciso proceder a la limpieza de las referidas arquetas lo cual se acordó en la Junta celebrada por la Comunidad de propietarios el pasado día [FECHA].

Se acompaña copia del Acta, como documento n.º [NÚMERO].

QUINTO.- Que ante la negativa del demandado a permitir el acceso a su local para dichas reparaciones, la Comunidad a la que represento, le ha remitido con fecha [FECHA] burofax, cuya copia se acompaña como documento n.º [NÚMERO], que no ha tenido contestación, requiriéndole para que le permitiese el acceso con la advertencia de que en caso de negativa se ejercerían las acciones legales correspondientes y se exigirían los daños y perjuicios que su negativa suponga para la Comunidad y para el resto de propietarios.

Debe indicarse que la limpieza de las bajantes comunitarias, teniendo presente la antigüedad de edificio y a las labores en tal sentido ya realizadas precedentemente, resulta una labor de mantenimiento totalmente necesaria, y que dicha labor de limpieza, en la situación actual, precisa de o requiere la entrada en el local propiedad de D./Dña. [NOMBRE Y APELLIDOS], tal y como de forma incuestionable resulta del dictamen pericial del arquitecto técnico D./Dña. [NOMBRE Y APELLIDOS], que se acompaña documento n.º [NÚMERO], pues no es posible llevar a cabo la limpieza de forma total sin acceder al local en cuestión y utilizar la arqueta en el mismo existente a tal efecto.

SEXTO.- Que la negativa del demandado está perjudicando a la Comunidad y al resto de los propietarios, ya que los atascos existentes están produciendo olores insoportables en la finca.

SÉPTIMO.- La parte actora manifiesta que, previo a la presentación de la presente demanda, se han llevado a cabo negociaciones con la parte demandada, con el objetivo de cumplir el requisito de procedibilidad, y resolver la controversia de manera amistosa y extrajudicial. Dichas negociaciones se desarrollaron en cumplimiento de los principios de buena fe, con la intención de alcanzar una solución satisfactoria; incluyéndose entre las acciones realizadas el intercambio de comunicaciones formales mediante correspondencia escrita, en fechas [COMPLETAR], en las cuales esta parte expresó su disposición para dialogar y propuso alternativas de solución.

Finalmente, mi representado envió un requerimiento fehaciente al demandado con fecha [FECHA], fijando un plazo de 30 días naturales para llegar a un acuerdo amistoso, a través del abogado que firma este escrito, el cual fue contestado por el demandado por el mismo medio, rechazando el acuerdo/ habiendo sido solo posible un acuerdo parcial, viéndonos en la necesidad de acudir a la presente vía judicial, respecto a los extremos de la controversia en los que se mantiene la discrepancia.

Acompaño como documento nº [Nº DE DOCUMENTO], el requerimiento efectuado y como documento nº [Nº DE DOCUMENTO], la contestación del demandado.

A los anteriores hechos son de aplicación los siguientes:

FUNDAMENTOS DE DERECHO

I.- COMPETENCIA.

Es competente objetivamente el Tribunal al que tengo el honor de dirigirme, de conformidad con el art. 45 LEC, en cuanto dispone, en armonía con el art. 85.1 LOPJ, que a las Secciones Civiles de los Tribunales de Instancia corresponde el conocimiento, en primera instancia, de todos los asuntos civiles que por disposición legal expresa no se hallen atribuidos a otro tribunales, e igualmente lo es por razón de territorio, dado que en esta circunscripción radica la finca, siendo la materia litigiosa de propiedad horizontal, conforme al art. 52.1.8.º LEC.

II.- PROCEDIMIENTO.

El modelo de procedimiento con arreglo al que deberá sustanciará este proceso, será el determinado para el Juicio Ordinario regulado en los arts. 399 y ss. LEC, conforme a lo establecido para esta materia de propiedad horizontal en el art. 249.1.8.º LEC, sin que esta acción suponga reclamación de cantidad.

III.- LEGITIMACIÓN ACTIVA Y PASIVA.

En cuanto a la activa corresponde a mi mandante, a tenor del art. 13.3 LPH; y en cuanto a la legitimación pasiva corresponde al demandado como propietario del local que impide la entrada.

IV.- CAPACIDAD Y REPRESENTACIÓN.

Mi mandante es el representante legal de la entidad sin personalidad que es la Comunidad de propietarios del edificio señalado con n.º [NÚMERO] de la calle [CALLE] de [COMPLETAR], por lo que detentando capacidad para ser parte por ministerio de la ley dicha comunidad, la capacidad procesal, o para comparecer en juicio, corresponde a su Presidente (arts. 6.1.5.º y 7.6 LEC).

El demandado es persona física, mayor de edad, respecto de las que no consta limitación de ejercicio de derechos civiles, por lo que detenta capacidad para ser parte (art. 6.1.1.º LEC), y capacidad procesal, o de obrar en este concreto juicio (art. 7.1 LEC), siempre que cumpla los oportunos requisitos de postulación para oponerse a la presente demanda.

V.- POSTULACIÓN Y DEFENSA.

El actor ha otorgado poder notarial al Procurador/a. de los Tribunales que encabeza este escrito, habilitado en el partido del Tribunal, cuya copia auténtica se ha aportado, general para pleitos (art. 25 LEC), siendo redactada y firmada la demanda por el abogado ejerciente colegiado que dirige el asunto y se identifica en el encabezamiento, según resulta preceptivo conforme a los arts. 23 y 31 LEC.

VI.- CUANTÍA.

En cumplimiento del art. 253.1 LEC se hace constar que la cuantía de este procedimiento es indeterminada, por concurrir las circunstancias del art. 253.3 LEC.

VII.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

VIII.- FONDO DEL ASUNTO.

Resultando ya del art. 33 CE que el derecho a la propiedad privada no es absoluto, el art. 9.1 d) LPH establece que, es obligación (diferenciada por tanto de otras) de cada propietario permitir la entrada en su piso o local a los efectos prevenidos en los tres apartados anteriores, y en el apartado anterior, el c), se recoge que es, asimismo, obligación de cada propietario consentir en su vivienda o local las reparaciones que exija el servicio del inmueble. [COMPLETAR], englobando el concepto de reparaciones no sólo las extraordinarias sino también las normales de conservación y mantenimiento que exija el servicio del inmueble, siendo incuestionable el encuadre dentro de tales labores normales de conservación y mantenimiento, la de la limpieza, siendo que la entrada en el piso o local a los efectos precedentes necesita de la autorización judicial, conforme al art. 18.2 CE.

IX.- COSTAS.

Conforme al art. 394 LEC las costas han de imponerse a la parte demandada, por principio objetivo del vencimiento.

Por lo expuesto,

SUPLICO AL TRIBUNAL:

Que teniendo por presentado este escrito y documentos que le acompañan, con sus copias, lo admita a trámite, me tenga por comparecido y parte, y admita a trámite la demanda que se formula, acordando conferir traslado de la misma al demandado D./Dña. [NOMBRE Y APELLIDOS] emplazándole para que, si es su interés, comparezca y la conteste, y seguido el juicio por sus trámites, se dicte en definitiva sentencia por la que estimando íntegramente la demanda se DECLARE LA OBLIGACIÓN DEL DEMANDADO DE PERMITIR EL ACCESO AL LOCAL DE SU PROPIEDAD CON EL FIN DE LLEVAR A CABO LAS OBRAS DE LIMPIEZA Y DESATRANCO DE LAS CANALIZACIONES, sin perjuicio de solicitar, en su caso, el resarcimiento de los daños y perjuicios que le pudiera ocasionar su negativa a la comunidad de propietarios y que se acrediten cumplidamente, y todo ello con expresa imposición de las costas al demandado.

OTROSÍ PRIMERO DIGO: Se acompaña dictamen pericial de Arquitecto Técnico, con arreglo a los arts. 335 y 336.1 LEC, el que hace documento n.º [NÚMERO], emitido por D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], calle [CALLE].

Por lo expuesto,

AL TRIBUNAL SUPLICO que, teniendo por hecha la anterior afirmación, y por presentadas pruebas periciales, se admitan y quede anunciada su proposición como prueba.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) Podrá solicitarse como medida cautelar que se dicte orden de entrada provisional para los arreglos urgentes, por darse las circunstancias previstas en los arts. 726, apartado 2, y 727, regla 11.ª. Esta medida se solicitará, normalmente mediante otrosí, conforme a las reglas ordinarias.
