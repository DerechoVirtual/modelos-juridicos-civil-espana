---
name: guarda-custodia-mutuo-acuerdo-demanda-933
description: "Redacta el escrito «Guarda y custodia de mutuo acuerdo: demanda» (formulario 933 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Guarda y custodia de mutuo acuerdo: demanda

> Formulario 0933 del plugin **Familia** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- (media) Afirma que el mutuo acuerdo «no está sujeto» a MASC: el art. 5.2 LO 1/2025 no lo excluye. Más seguro decir que el requisito se cumple con la negociación directa reflejada en el convenio firmado por ambas partes (arts. 5.1 y 10.2 LO 1/2025).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] Nº DE DOCUMENTO
- [ ] FECHA (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…s representados a favor de su hijo menor»; «…un hijo llamado»; «…y Dña. lo tiene en»; «…o a su actividad laboral, D. se dedica a»; «…y Dña. a»; «…. El hijo común vive en el domicilio de»; «…(el padre o la madre) y la relación de»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 36 de la LEC
- arts. 21 y 22 de la LOPJ
- art. 769.3 de la LEC
- arts. 748.4 y 770.6 de la LEC
- art. 777 de la LEC
- art. 10 de la LEC
- art. 749.2 de la LEC
- art. 750 de la LEC
- arts. 775.2 y 777.9 LEC
- art. 90.3 CCiv
- Ley Orgánica 1/2025

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

### Formulario 0933 · Guarda y custodia de mutuo acuerdo: demanda

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 18 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)
- Avisos de la revisión: (media) Afirma que el mutuo acuerdo «no está sujeto» a MASC: el art. 5.2 LO 1/2025 no lo excluye. Más seguro decir que el requisito se cumple con la negociación directa reflejada en el convenio firmado por ambas partes (arts. 5.1 y 10.2 LO 1/2025).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda guarda y custodia

A LA SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: No existe «Tribunal de Instancia Decano». Guarda y custodia: Sección de Familia, Infancia y Capacidad (art. 86.5.b LOPJ) o, si no existe, Sección Civil (o Única). Fuente: LO 1/2025 DT 3.ª (los jueces decanos pasan a la Presidencia del TI) y LOPJ arts. 84.1, 84.3 y 166 (BOE-A-2025-76); LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D. [NOMBRE Y APELLIDOS] y de Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], ante el Tribunal comparezco con la asistencia letrada de D./Dña. [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO:

Que mediante el presente escrito formulo DEMANDA DE GUARDA Y CUSTODIA, RÉGIMEN DE VISITAS Y ALIMENTOS de común acuerdo sometiendo a aprobación judicial la propuesta de convenio regulador suscrito por mis representados a favor de su hijo menor [COMPLETAR]. En este procedimiento deberá intervenir el Ministerio Fiscal por existir un menor de edad. Basamos esta pretensión en los siguientes

HECHOS

De la relación de D. y Dña. nació el día [FECHA] un hijo llamado [COMPLETAR]. Adjunto como documento n.º [NÚMERO] certificado de nacimiento emitido por el Registro Civil.

Desde el nacimiento del menor hasta la fecha [FECHA] (cada progenitor ha continuado viviendo en el domicilio familiar de sus padres. Cada progenitor ha continuado viviendo en su domicilio, los progenitores han mantenido una relación de convivencia que ahora ha finalizado).

D. tiene su domicilio en [LOCALIDAD] y Dña. lo tiene en [COMPLETAR] En cuanto a su actividad laboral, D. se dedica a [COMPLETAR] y Dña. a [COMPLETAR].

El hijo común vive en el domicilio de [COMPLETAR] (el padre o la madre) y la relación de [COMPLETAR] (la madre o el padre) con el hijo es fluida.

 (En su caso explicar la razón de ser de algún punto del convenio que puede resultar no habitual)

De común acuerdo los padres han decidido regular las relaciones de ambos con relación a su hijo en atención a la propuesta de convenio que acompañamos como documento n.º [NÚMERO] y que se somete a aprobación judicial.

FUNDAMENTOS DE DERECHO

Jurisdicción y competencia

Son de aplicación el art. 36 de la LEC y arts. 21 y 22 de la LOPJ. La competencia de este Tribunal de [LOCALIDAD] viene determinada por ser éste el lugar de domicilio del menor, en aplicación del art. 769.3 de la LEC, en relación con lo dispuesto en el art. 85.1º LOPJ.

Tramitación

Los arts. 748.4 y 770.6 de la LEC remiten al cauce establecido para la adopción de medidas previas, simultáneas o definitivas en los procesos de nulidad, separación o divorcio. Entendemos que no existe problema para acudir al cauce del art. 777 de la LEC ratificando el convenio suscrito por ambos progenitores y dando traslado al Ministerio Fiscal.

Legitimación y postulación

Los titulares de la relación jurídica, art. 10 de la LEC, son los progenitores.

En aplicación del art. 749.2 de la LEC deberá intervenir el Ministerio Fiscal. El art. 750 de la LEC exige la comparecencia con Abogado y Procurador.

Cumplimiento de los requisitos de procedibilidad

La presente demanda no está sujeta al previo intento de resolución de controversias en vía no jurisdiccional, de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia, por tratarse en sí de un acuerdo consensual y voluntario entre las partes, necesitando únicamente la homologación del mismo por parte del Tribunal, siendo que el convenio regulador (arts. 775.2 y 777.9 LEC y art. 90.3 CCiv) se entiende acreditativo de haber realizado esa actividad negociadora.

Fondo del asunto

PRIMERO.— Art. 159 del CC que regula el derecho de los padres que viven separados a decidir al cuidado de qué progenitor quedará el hijo menor de edad.

SEGUNDO.— Art. 154 y 156 del Código Civil sobre el ejercicio y contenido de la patria potestad sobre menores no emancipados.

SEGUNDO.— Arts. 142 y siguientes y 158 del Código Civil sobre prestación de alimentos y contenido.

TERCERO.— Art. 162 del Código Civil: los padres que ostenten la patria potestad tienen la representación legal de sus hijos no emancipados.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño, admita a trámite la presente solicitud de mutuo acuerdo de regulación de patria potestad, guarda y custodia, régimen de visitas y alimentos respecto al hijo no matrimonial menor de edad de D. y Dña. [NOMBRE Y APELLIDOS], dando traslado al Ministerio Fiscal, citando a las partes para la ratificación del convenio y dictando en su día sentencia por la que se acuerde aprobar el mismo.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
