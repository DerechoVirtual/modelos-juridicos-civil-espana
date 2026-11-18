---
name: contestacion-demanda-impugnacion-acuerdo-lesivo-1333
description: "Redacta el escrito «Contestación a demanda de impugnación de acuerdo lesivo o perjudicial» (formulario 1333 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a demanda de impugnación de acuerdo lesivo o perjudicial

> Formulario 1333 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO (2 veces)
- [ ] SEDE
- [ ] Nº (2 veces)
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] FECHA (3 veces)
- [ ] IMPORTE
- [ ] FECHA DE LA JUNTA
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otro dato sin etiqueta, marcado `[COMPLETAR]`. Su contexto en el formulario: «…te caso se ha incumplido el requisito de»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 17.1 de la LPH
- artículo 9.c) de la LPH
- artículo 394 de la LEC

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

### Formulario 1333 · Contestación a demanda de impugnación de acuerdo lesivo o perjudicial

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 9 campos de relleno marcados en blanco; 8 huecos del original que se habían perdido sin marca, marcados (FECHA, FECHA DE LA JUNTA, IMPORTE, Nº, Nº DE DOCUMENTO, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio Ordinario n.º [Nº DE PROCEDIMIENTO]/[AÑO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [Nº]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

Que mediante el presente escrito procedo a contestar a la demanda promovida por el comunero de nuestra Comunidad D./Dña. [NOMBRE Y APELLIDOS] impugnando el acuerdo de la Junta de Propietarios de fecha [FECHA] en el sentido de oponernos a ella en atención a los siguientes

HECHOS

(Para los Tribunales en los que se haya implantado la presentación de escritos a través del sistema telemático con firma electrónica-Lex Net).

Acompañamos como documento nº 1 índice numerado de los documentos que se presentan con la contestación a la demanda.

Cierto el correlativo sobre la convocatoria de la Junta y la citación en forma a todos los copropietarios.

Se ajusta también a la realidad el orden del día que se trascribe en la demanda, aunque hay que hacer constar que en la Junta y a propuesta de D./Dña. [NOMBRE Y APELLIDOS] en el apartado «otros asuntos a tratar» se incluyó el relativo a.

La polémica a la que se refiere la parte actora no fue ni tan acalorada ni tan tensa como se nos quiere transmitir de contrario. Es cierto que la cuestión objeto de la polémica se viene discutiendo desde hace tiempo, y así se acredita con las actas de las Juntas de fechas.

Curiosamente se puede apreciar en la primera de ellas que el actor no votó en contra, sino que en aquel momento se abstuvo, y en la segunda que figura como no asistente, aunque no impugnó el acuerdo, a pesar de que se le notificó ese acta.

Acreditamos, por tanto, que las obras se habían estudiado en otras reuniones y que el actor no se había opuesto expresamente a ellas.

Tal y como se trascribe en el acta, D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] mostraron su oposición a la reforma planteada y dieron sus razones, y luego se votó con el resultado que consta.

Las obras no resultan.

Se acredita con el informe pericial de D./Dña. [NOMBRE Y APELLIDOS] con título en y que acompañamos con el n.º [Nº] que.

A esto hay que añadir que el acuerdo se alcanzó por amplia mayoría, de donde se deduce que sus efectos son beneficiosos para la Comunidad.

Es cierto que el actor es titular de la vivienda, según acredita, pero en estos momentos no se encuentra al corriente del pago de todos los conceptos que tiene que abonar a la Comunidad.

En concreto, D./Dña. [NOMBRE Y APELLIDOS] adeuda la cifra de [IMPORTE] euros por los siguientes conceptos:, a razón de.

Se acredita este deuda con.

Este motivo debe ser suficiente para que, sin más, se desestime la pretensión del actor, pues constituye requisito necesario e imprescindible para impugnar los acuerdos de la Junta de Propietarios que el comunero esté al corriente en el pago de la totalidad de las deudas vencidas o que haya consignado la deuda. En este caso ni ha cumplido el primer requisito ni se ha valido de la segunda opción.

En efecto, el actor votó en contra del acuerdo adoptado y se reservó su derecho a impugnar el acuerdo, lo que efectivamente ha llevado a cabo con su demanda.

Pero esta parte mantiene que el acuerdo debe mantenerse porque las obras.

FUNDAMENTOS DE DERECHO

Conforme con el correlativo, será competente el Tribunal de Instancia del lugar donde radique la finca.

Conforme igualmente con el correlativo que remite al cauce del juicio ordinario para la resolución del conflicto.

Está legitimado de forma activa el comunero y de forma pasiva la Comunidad de Propietarios.

El Presidente de la Comunidad actúa en nombre de la Comunidad de Propietarios de en virtud de nombramiento en ese cargo en Junta de fecha [FECHA DE LA JUNTA], y se le ha autorizado expresamente a dar poder a favor del Procurador que suscribe esta demanda para contestar a ésta en Junta de Propietarios de fecha [FECHA], según se acredita con copias de las actas que adjuntamos como documentos n.º [Nº DE DOCUMENTO].

Los artículos 23 y 31 de la Ley de Enjuiciamiento Civil (LEC) exigen la comparecencia a través de Procurador y la asistencia letrada.

El artículo 18.2 de la Ley de Propiedad Horizontal exige, para poder impugnar los acuerdos de la Junta de Propietarios, que el comunero disidente haya salvado su voto si compareció a la Junta. Si no compareció, o si fue indebidamente privado de su voto, también tendrá esa facultad de impugnación. Es también imprescindible que esté al corriente de pago de la totalidad de las deudas vencidas con la Comunidad o que haya procedido previamente a su consignación judicial, salvo que la impugnación se refiera precisamente al establecimiento o alteración de las cuotas de participación.

En este caso se ha incumplido el requisito de [COMPLETAR], motivo por el que sin entrar en más valoraciones se deberá desestimar la demanda.

Si no se apreciara la anterior excepción y se entrara a valorar la oportunidad, necesidad y efectos de las obras que se acordaron realizar, debemos acudir al artículo 17.1 de la LPH 1960 que regula las mayorías necesarias para acordar la realización de obras. En el presente caso.

Finalmente, el artículo 9.c) de la LPH 1960 considera obligación de los propietarios permitir la servidumbres imprescindibles requeridas para la instalación de servicios comunes de interés general acordada en la forma legalmente establecida. Se establece además el derecho de resarcimiento. Según se ha acreditado.

En aplicación del artículo 394 de la LEC las costas deberán imponerse a la parte demandante.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y copia de todo ello, o por contestada la demanda a fin de que en su día, previos los trámites oportunos, dicte sentencia por la que se desestime la pretensión del actor por carecer la impugnación de los requisitos necesarios para su validez o, en caso de considerar que sí se han cumplido, al resultar el acuerdo ajustado a las necesidades de la Comunidad, se mantenga su validez declarando la vigencia del acuerdo de la Junta de Propietarios de la C/ de de fecha [FECHA] y condenando expresamente a las costas de este juicio a la parte actora.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firmas de abogado y procurador

========================================================================
