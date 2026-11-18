---
name: reconocimiento-espana-actos-jurisdiccion-voluntaria-768
description: "Redacta el escrito «Reconocimiento en España de actos de jurisdicción voluntaria extranjeros» (formulario 768 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reconocimiento en España de actos de jurisdicción voluntaria extranjeros

> Formulario 0768 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] FECHA (3 veces)
- [ ] ÓRGANO
- [ ] LOCALIDAD (2 veces)
- [ ] LUGAR
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…acto de conciliación frente a la entidad»; «…o Civil. Por ello, y dado que la entidad»; «…, en»; «…on ninguno de los derechos de la entidad»; «…. 12 LJV, y previo traslado a la entidad»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 12 de la Ley 15/2015
- art. 147 LJV
- art. 9.2 LJV
- art. 12 LJV
- art. 87.6 LOPJ
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

### Formulario 0768 · Reconocimiento en España de actos de jurisdicción voluntaria extranjeros

- Año del modelo: 2015
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 15 campos de relleno marcados en blanco; 1 menciones a órganos y cargos actualizadas (LO 1/2025; LO 7/2015)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Solicitud de reconocimiento de un acto de conciliación entre un particular y una entidad para la que había prestado sus servicios profesionales, acordado por autoridades extranjeras, para poder proceder a su ejecución forzosa.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] QUE POR TURNO CORRESPONDA

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO: (1)

Que por medio del presente escrito, y al amparo de lo dispuesto en el art. 12 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo EXPEDIENTE PARA EL RECONOCIMIENTO DE ACTO DE JURISDICCIÓN VOLUNTARIA DE CONCILIACIÓN, ACORDADO POR AUTORIDADES EXTRANJERAS, en base a las siguientes

ALEGACIONES

PRIMERA.- Que el pasado [FECHA], insté ante el [ÓRGANO], un acto de conciliación frente a la entidad [COMPLETAR] SL, con objeto de intentar un acuerdo que pudiera evitar el planteamiento de una reclamación judicial en relación con unos servicios prestados como arquitecto en dicha localidad a tal mercantil, y que no habían sido abonados. Instado el correspondiente expediente, según la legislación marroquí, se alcanzó un acuerdo con D./Dña. [NOMBRE Y APELLIDOS], administrador social de aquélla con poderes legales de representación, para fijar la deuda existente en 18.000 euros a abonar en el plazo de cinco meses en un número de cuenta determinado. Todo lo cual fue recogido en resolución del referido órgano judicial dictada el pasado [FECHA], que devino finalmente firme, al no ser recurrida por ninguna de las partes.

SEGUNDO.- El plazo de cinco meses ha transcurrido sin que la cantidad haya sido pagada, siquiera en una mínima parte, y sin que haya recibido respuesta alguna a los múltiples requerimientos realizados desde entonces. Dado que el trabajo desarrollado en Fez fue coyuntural y la mercantil deudora carece de delegación en Marruecos, me veo obligado a instar el reconocimiento de tal acto en España, a los efectos de poder instar su ejecución forzosa de conformidad con el art. 147 LJV, y del art. 517.2.9º de la Ley de Enjuiciamiento Civil. Por ello, y dado que la entidad [COMPLETAR] SL tiene su domicilio social en [LOCALIDAD], en [COMPLETAR], que es donde se tratará de que el acto de jurisdicción voluntaria tenga sus efectos, se acude al órgano judicial al cual tengo el honor de dirigirme, conforme al art. 9.2 LJV.

TERCERO.- Que concurren los requisitos exigidos en art. 12 LJV, para el reconocimiento pretendido:

1.- El acto en cuestión es firme, tal y como se puede comprobar con la documentación que se anexa a la presente solicitud.
2.- La sección civil del Tribunal de Instancia al cual tengo el honor de dirigirme es competente para otorgar incidentalmente el reconocimiento pretendido, a los efectos de poder ejecutar forzosamente el acto de jurisdicción voluntaria frente a la entidad deudora. En este sentido, se trata de una resolución que recoge un acuerdo tras una reclamación de cantidad derivada de un contrato de prestación de servicios de arquitecto, que no se encuentra listada dentro de las materias expresamente atribuidas por el art. 87.6 LOPJ a las secciones de lo Mercantil. Asimismo, la deudora frente a la que se dirigirá la ejecución individual tiene su domicilio en Madrid, y, por lo tanto, dentro del partido judicial del Tribunal. Todo ello, previo traslado a la citada mercantil para que alegue lo que a su derecho convenga.
3.- No concurren ninguna de las causas de denegación previstas en el apartado tercero del mencionado precepto legal: el acto se acordó por Tribunal competente según el art. de la Ley Procesal Marroquí, sin que afecte a una competencia exclusiva de los órganos o autoridades españolas. Asimismo, no se infringieron ninguno de los derechos de la entidad [COMPLETAR] SL, la cual fue oportunamente citada y acudió al acto, negociando con total libertad y llegando al acuerdo finalmente rubricado por uno de sus representantes legales con poder suficiente para ello. Finalmente, y por los mismos motivos, ni se han producido actos contrarios al orden público español (la materia es perfectamente transigible en nuestra legislación), ni se ha violado derecho fundamental o libertad pública alguna de nuestro ordenamiento jurídico. El acto se desarrolló, tal y como se hubiera llevado a cabo ante cualquier Tribunal de Instancia de nuestro país, de manera similar a lo que ordenan los arts. 139 y ss. LJV para los actos de conciliación ante Tribunales españoles.

Que acompaño a este escrito copias testimoniadas y debidamente legalizadas, de la resolución que recoge el acto de conciliación cuyo reconocimiento se pretende, de la resolución de la Secretaría Judicial del Tribunal de Instancia de Fez que certifica la firmeza de la misma, y copia de la Ley Procesal Marroquí. Todo ello con las traducciones al castellano de cada uno de los documentos enumerados, elaboradas por traductor o intérprete jurado oficial.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito y los documentos que se acompañan, y por promovido expediente de reconocimiento de acto de jurisdicción voluntaria de conciliación, acordado por autoridad extranjera; de conformidad con el art. 12 LJV, y previo traslado a la entidad [COMPLETAR] SL, con domicilio en [LOCALIDAD], para que efectúe alegaciones; se reconozca el citado acto de conciliación, para poder proceder a su ejecución forzosa.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) No exigible en el expediente expresamente, pero facultativo conforme art. 3.2 LJV.

========================================================================
