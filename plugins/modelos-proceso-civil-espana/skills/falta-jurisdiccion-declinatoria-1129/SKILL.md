---
name: falta-jurisdiccion-declinatoria-1129
description: "Redacta el escrito «Falta de jurisdicción: declinatoria» (formulario 1129 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Falta de jurisdicción: declinatoria

> Formulario 1129 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] NÚMERO (3 veces)
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] Nº DE DOCUMENTO
- [ ] COLEGIO
- [ ] FECHA (2 veces)
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Juicio»; «…, PLAZA N.º»; «… del demandante Sr. durante los meses de»; «…a»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 37 de la LEC
- artículo 63 de la LEC
- artículo 63.2 de la LEC
- artículo 65 de la LEC

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

### Formulario 1129 · Falta de jurisdicción: declinatoria

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 19 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio [COMPLETAR], n.º [NÚMERO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, interviniendo en nombre de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], ante el Tribunal comparezco bajo dirección del letrado D./Dña. [NOMBRE Y APELLIDOS], colegiado n.º [NÚMERO] del Iltre. Colegio de Abogados de [COLEGIO], en los autos referenciados, y como mejor proceda en derecho DIGO:

Que con fecha [FECHA] se ha dado traslado a mi poderdante de la demanda interpuesta por la representación procesal de D./Dña. [NOMBRE Y APELLIDOS] en reclamación sobre [DESCRIBIR] para que la conteste en el plazo de veinte días.

Dentro del plazo legal de los primeros diez días concedidos para contestar a la demanda (o cinco días posteriores a la citación para la vista, si se tratase de juicio verbal), denuncio la falta de jurisdicción de este Tribunal de Instancia para el conocimiento de la demanda que ha dado origen a los presentes autos, promoviendo, mediante el presente escrito, cuestión de competencia por DECLINATORIA, que apoyo en los siguientes

HECHOS

La demanda presentada por la representación de D./Dña. [NOMBRE Y APELLIDOS] se dirige a reclamar una deuda que el actor pretende tener pendiente de cobro ante mi poderdante, sirviéndose, como apoyo documental de su pretensión, de unos documentos que se acompañan a dicha demanda de los que pretendidamente se desprende un hipotético reconocimiento de deuda realizado por mi principal en beneficio del actor.

Silencia, sin embargo, el actor que tales documentos se suscribieron para documentar la falta circunstancial de pago de algunos salarios que mi poderdante debía haber hecho efectivos al actor como consecuencia de la prestación de servicios laborales a mi representado. Este inadecuado planteamiento se concreta en que el Tribunal de Instancia ante el que se presenta la demanda se ha visto inducido a considerarse competente para el conocimiento de ésta, al plantearse la deuda como derivada de una simple relación económica particular, de naturaleza civil, habida entre las partes.

Con fecha [FECHA] el actor suscribió, con mi mandante el contrato de trabajo que, debidamente visado por la Oficina del Instituto Nacional de Empleo de esta capital, acompaño por ejemplar original como documento n.º [NÚMERO] Dado que mi poderdante atravesó serias dificultades económicas en el desarrollo de su actividad empresarial, hubo de aplazar el pago de los salarios correspondientes a la actividad laboral del demandante Sr. durante los meses de [COMPLETAR] a [COMPLETAR] del presente año. Para documentar el aplazamiento de pago de los salarios que las partes convinieron, se redactaron los documentos acompañados a la demanda, en los que se establecía un calendario de pagos de efectivo, que, aun cuando en los mencionados documentos no se recogió, por obvia, esta circunstancia, correspondía a la retribución salarial del ahora demandante. Dichos documentos han sido aportados con la demanda como base de su reclamación, silenciando la evidente naturaleza laboral de la deuda de la que son expresión.

 (desarrollar las restantes situaciones fácticas en la que se apoya la declinatoria y aportar los documentos que sirvan de apoyo a la cuestión de competencia planteada).

A los hechos antecedentes resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Artículos 45 de la LEC y 85 de la Ley Orgánica del Poder Judicial. Las Secciones Civiles de los Tribunales de Instancia conocerán, en primera instancia, de los asuntos civiles que no se hallen atribuidos por disposición legal expresa a otros Tribunales.

El artículo 37 de la LEC establece —apartado 2— que “se abstendrán igualmente de conocer los tribunales civiles cuando se les sometan asuntos de los que corresponda conocer a los tribunales de otro orden jurisdiccional de la jurisdicción ordinaria”.

La deuda que se reclama mediante la demanda tiene una naturaleza inequívocamente laboral, por lo que, en cualquier supuesto y con independencia de su exigibilidad, deben ser los órganos de la jurisdicción social quienes conozcan de posibles reclamaciones relativas a los mismos.

Nos encontramos, en consecuencia, ante un evidente supuesto de falta de jurisdicción del Tribunal de Instancia ante el que se presenta la demanda.

El artículo 63 de la LEC regula el tratamiento de la declinatoria, y establece el cauce por el que el demandado y los que puedan ser parte legítima en el juicio promovido pueden “denunciar la falta de jurisdicción del tribunal ante el que se ha interpuesto la demanda, por corresponder el conocimiento de ésta a tribunales extranjeros, a órganos de otro orden jurisdiccional o a árbitros”.

El artículo 63.2 de la LEC determina que la “declinatoria se propondrá ante el mismo tribunal que esté conociendo del pleito ...”.

Artículo 64 de la LEC: La declinatoria debe proponerse dentro de los diez días primeros días del plazo para contestar a la demanda o en los cinco días siguientes a la citación para vista. Surtirá el efecto de suspender el plazo de contestación o el cómputo de días para la vista, así como el de suspender la propia tramitación del procedimiento judicial.

Se acompañan, en cumplimiento de lo dispuesto en el artículo 65 de la LEC, los documentos que acreditan la falta de jurisdicción de este Tribunal.

El auto que resuelva la cuestión de competencia por declinatoria planteada, además de acordar la abstención de conocimiento sobre el asunto y el sobreseimiento del proceso, indicará el órgano jurisdiccional ante el que el demandante usará su derecho, que en el presente supuesto será la Sección de lo Social de los Tribunales de instancia de esta capital.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL que tenga por presentados este escrito, poder, documentos y las copias preceptivas de todo ello que se acompañan, se sirva admitirlos, teniendo por denunciada la falta de jurisdicción de este Tribunal y por promovida en tiempo y forma cuestión de competencia por DECLINATORIA, y en virtud de las alegaciones formuladas y la acreditación documental que se acompaña, y previa la tramitación oportuna con suspensión en todo caso del plazo para contestar a la demanda y del propio curso del procedimiento, dicte auto mediante el que, apreciando la falta de jurisdicción de este Tribunal, se acuerde abstenerse de conocer del presente asunto, sobreseyendo el proceso y señalando el órgano jurisdiccional ante el que la parte actora ha de usar su derecho, con expresa imposición de costas al demandante.

Por ser Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
