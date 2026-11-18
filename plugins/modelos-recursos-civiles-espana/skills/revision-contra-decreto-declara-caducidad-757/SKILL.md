---
name: revision-contra-decreto-declara-caducidad-757
description: "Redacta el escrito «Revisión contra el decreto que declara la caducidad» (formulario 757 de recursos civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Revisión contra el decreto que declara la caducidad

> Formulario 0757 del plugin **Recursos civiles** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] FECHA (13 veces)
- [ ] Nº DE EXPEDIENTE
- [ ] DESCRIBIR
- [ ] IMPORTE
- [ ] LUGAR
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA»; «…engo acreditada en los autos de juicio /»; «…/»; «…a de la herencia de su difunto esposo D.»; «…, depositados en la entidad bancaria»; «…una única representación, solicitaron el»; «…una suerte de traslado a esta parte para»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 20.2 de la Ley 15/2015
- art. 102 LJV
- art. 21 LJV
- art. 16.4 LJV
- art. 24 de la Constitución
- art. 3.2 LJV
- art. 101.2 LJV
- Ley 1/2000

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

### Formulario 0757 · Revisión contra el decreto que declara la caducidad

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 29 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Recurso de revisión contra el decreto del Letrado de la Administración de Justicia para que, una vez dado traslado a la contraria para que pueda impugnarlo, se dicte auto por el que se revise el decreto impugnado, se deje sin efecto, y se continúe con el expediente que ocupa, permitiendo al solicitante subsanar el defecto en su momento apreciado.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA [COMPLETAR] DE [LOCALIDAD]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], cuya representación tengo acreditada en los autos de juicio / [COMPLETAR], seguido contra D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco y como mejor proceda en derecho DIGO: (1)

Que el pasado día [FECHA] se me ha notificado el decreto del Letrado de la Administración de Justicia de fecha [FECHA], que decreta la caducidad al expediente de jurisdicción voluntaria con nº [Nº DE EXPEDIENTE] / [COMPLETAR] en la instancia, y estimando el mismo lesivo para los intereses de mi mandante, dicho sea en estrictos términos de defensa, dentro del plazo de cinco días legalmente establecido en el art. 454.bis.2 de la Ley 1/2000, de 7 de enero, de Enjuiciamiento Civil (en lo sucesivo, LEC), al cual se remite el art. 20.2 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), ante el Tribunal interpongo contra aquel recurso de revisión, fundamentándolo en las siguientes

ALEGACIONES

PRIMERA.- Por mi mandante se instó el pasado [FECHA], conforme a los arts. 100 y ss. LJV, la autorización judicial para reclamar los créditos vencidos, que como usufructuaria de la herencia de su difunto esposo D. [COMPLETAR], le corresponden en relación a los activos bancarios consistentes en [DESCRIBIR], depositados en la entidad bancaria [COMPLETAR], cuya nuda propiedad corresponde a sus hijos D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS], en virtud de herencia adjudicada mediante escritura pública de fecha [FECHA].

Desde la presentación de la solicitud, operada el día [FECHA], hasta el pasado [FECHA], no se notificó nada a mi cliente, teniendo conocimiento a través del Tribunal de Instancia, de que los autos se habían repartido al órgano judicial al cual tengo el honor de dirigirme.

SEGUNDA.- El pasado [FECHA], se nos notificó el Decreto dictado por el Letrado de la Administración de Justicia en fecha [FECHA], en el que se declaraba la caducidad del expediente, por entender que el mismo había permanecido sin actividad procesal durante más de seis meses, en concreto durante ocho meses, computados desde el día [FECHA], hasta el día [FECHA], en la que supuestamente se le había notificado la diligencia de ordenación de impulso procesal, de fecha [FECHA], en la cual se acordaba requerir la prueba de la falta de autorización del nudo propietario, conforme exige el art. 102 LJV.

TERCERA.- Pues bien, la citada diligencia de ordenación nunca fue me fue notificada, a pesar de constar mi representación como Procurador desde el mismo momento de la solicitud, en la que se acreditaba ante el órgano judicial el poder otorgado al efecto. Es decir, esta parte no ha tenido oportunidad de poder subsanar lo que el Letrado de la Administración de Justicia requería porque desconocía tal extremo. Asimismo, tras analizar los autos para plantear este recurso, se observa que los hijos de mi mandante, actuando bajo una única representación, solicitaron el [COMPLETAR] la caducidad que aquí se combate, en virtud de lo dispuesto en el art. 21 LJV, y tampoco se operó ninguna suerte de traslado a esta parte para [COMPLETAR], siquiera, poder hacer alegaciones, y ofrecer nuestra versión al órgano judicial.

Se señalan, por todo ello, expresamente infringidos: el art. 16.4 LJV, que impone la efectiva concesión de un plazo de cinco días para subsanar defectos, del que no se tuvo conocimiento; el art. 21 LJV, relativo a la caducidad, del cual se desprende que también debe oírse a las partes antes de decidir al respecto; y el art. 24 de la Constitución Española, puesto que mi mandante se queda en la más absoluta indefensión, al haber planteado una solicitud correcta, y encontrarse ocho meses después con un archivo del expediente, sin haber tenido oportunidad efectiva de subsanar, ni alegar nada. Procede, en consecuencia, revisar el decreto impugnado, dejarlo sin efecto, y continuar con el expediente que nos ocupa, permitiendo a mi cliente presentar la prueba de la falta de autorización del nudo propietario para cobrar los créditos vencidos del usufructo.

CUARTA.- Se acompaña a este escrito justificante acreditativo del depósito efectuado por importe de [IMPORTE] euros, en la cuenta de depósitos y consignaciones del Tribunal, conforme dispone la DA 15.ª LOPJ.

Por lo expuesto,

SE SOLICITA

que se tenga por presentado este escrito y por interpuesto recurso de revisión contra el decreto del Letrado de la Administración de Justicia de fecha [FECHA], para que, una vez dado traslado a la contraria para que pueda impugnarlo, se dicte auto por el que se revise el decreto impugnado, se deje sin efecto, y se continúe con el expediente que nos ocupa, permitiendo a mi cliente subsanar el defecto en su momento apreciado.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) Exigible para la interposición de cualquier recurso de revisión frente a decretos dictados por el Letrado de la Administración de Justicia que resuelvan definitivamente el expediente de jurisdicción voluntaria, conforme al art. 3.2 LJV. Y ello, independientemente de que las normas específicas de cada expediente no exijan tales requisitos de postulación para la primera instancia. En el expediente utilizado como ejemplo, la autorización judicial al usufructuario para reclamar créditos vencidos que formen parte del usufructo, el art. 101.2 LJV, no exige la representación de procurador y asistencia de abogado en la instancia, sin perjuicio de que la parte haya optado por tal posibilidad desde el inicio).

========================================================================
