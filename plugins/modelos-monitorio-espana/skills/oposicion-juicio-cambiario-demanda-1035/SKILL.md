---
name: oposicion-juicio-cambiario-demanda-1035
description: "Redacta el escrito «Oposición al juicio cambiario: demanda» (formulario 1035 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Oposición al juicio cambiario: demanda

> Formulario 1035 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (12 veces)
- [ ] DNI/NIE
- [ ] CALLE
- [ ] NÚMERO (3 veces)
- [ ] PROFESIÓN
- [ ] Nº DE DOCUMENTO
- [ ] COLEGIO
- [ ] FECHA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…, n.º [NÚMERO] de»; «…/»; «…roceda en derecho DIGO: Que con fecha de»; «…equisitos procesales invocados en cuanto»; «…deja desde este momento interesado, para»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 826 de la LEC
- art. 443 de la LEC
- art. 744 de la LEC
- art. 824 de la LEC
- art. 209 de la LEC
- art. 1902 del Código Civil
- art. 394 LEC
- art. 561 LEC
- Ley 19/1985

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

### Formulario 1035 · Oposición al juicio cambiario: demanda

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 29 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, interviniendo en nombre de D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, provisto de DNI [DNI/NIE], domiciliado en C/ [CALLE], n.º [NÚMERO] de [COMPLETAR], de profesión [PROFESIÓN], como acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], bajo la dirección del Letrado D./Dña. [NOMBRE Y APELLIDOS], Colegiado n.º [NÚMERO] del Colegio de Abogados de [COLEGIO], ante el Tribunal comparezco en los autos de proceso cambiario n.º [NÚMERO] / [COMPLETAR] promovidos a instancia de la representación procesal de D./Dña. [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO:

Que con fecha de [COMPLETAR] se me ha notificado el auto de fecha [FECHA] mediante el que se requiere a mi representado el pago de la suma reclamada en la demanda de juicio cambiario formulada por la representación procesal de D./Dña. [NOMBRE Y APELLIDOS]

Dentro del plazo legal de diez días que a tal efecto ha sido concedido a mi mandante, mediante el presente escrito interpongo DEMANDA DE OPOSICIÓN AL JUICIO CAMBIARIO promovido por la representación procesal de D./Dña. [NOMBRE Y APELLIDOS] que ha dado origen a estos autos, con objeto de que tramitada en forma se dicte sentencia estimando las causas de oposición invocadas en esta demanda, con la que siento, como correlativos a los de la demanda de juicio cambiario los siguientes

HECHOS

(Rebatir el relato fáctico de la demanda y aportar documentación que lo desacredite, o bien detallar los antecedentes de hecho que sirvan de base a las causas de oposición con su correspondiente acreditación documental.)

A los hechos antecedentes resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

Legitimación

Conformes con los correlativos.

Trámite y requisitos procesales

• La oposición se substanciará dando traslado al acreedor con citación para vista conforme a lo dispuesto en el art. 44 para los juicios verbales (art. 826 de la LEC).

• La vista se celebrará en el modo prevenido en el art. 443 de la LEC (art. 826 de la LEC).

• Con la estimación de la oposición se deberá acordar el inmediato levantamiento de los embargos acordados, según lo dispuesto en el art. 827.2 en relación con el art. 744 de la LEC.

• (Si se impugna alguno de los presupuestos invocados de contrario) Negamos la concurrencia de los requisitos procesales invocados en cuanto [COMPLETAR] (desarrollar las causas de oposición al que se impugne).

Fondo

El art. 824 de la LEC establece que el deudor cambiario podrá oponer al tenedor de la letra el cheque o el pagaré todas las causas o motivos de oposición previstos en el art. 67 de la Ley cambiaria y del cheque.

A su vez el art. 67 de la Ley cambiaria y del cheque, Ley 19/1985, de 16 de julio, modificada por la disposición final 10.ª de la LEC 1/2000, establece como causas de oposición:

1.º La inexistencia o falta de validez de la propia declaración cambiaria, incluida la falsedad de la firma.

2.º La falta de legitimación del tenedor o de las formalidades necesarias de la letra de cambio, conforme a lo dispuesto en esta ley.

3.º La extinción del crédito cambiario, cuyo cumplimiento se exige al demandado.

(Desarrollar los fundamentos específicos del caso, citar la jurisprudencia y doctrina de apoyo y DETERMINAR LAS CAUSAS DE OPOSICIÓN:)

Concurren, en definitiva, en el presente supuesto, y mediante esta demanda venimos a invocar las siguientes CAUSAS DE OPOSICIÓN:

1.

Costas

Deberán imponerse a D./Dña. [NOMBRE Y APELLIDOS] que formula la demanda de juicio cambiario con temeridad. El art. 209 de la LEC determina en su regla cuarta que la sentencia contendrá un pronunciamiento sobre costas. Deberán tenerse en cuanta los criterios establecidos por el art. 394 sobre la imposición de costas, imponiéndolas a D./Dña. [NOMBRE Y APELLIDOS] no sólo por su temeridad sino también por el propio rechazo de sus pretensiones. El contenido del art. 1902 del Código Civil justifica también la imposición de costas al demandante principal de juicio cambiario D./Dña. [NOMBRE Y APELLIDOS]

A este respecto resulta de interés el contenido de la Sentencia de fecha 13 de mayo de 2003 (recurso 67/2003; ponente ANDRÉS CUENCA, Rosa M.ª) dictada por la Sección 8.ª de la Audiencia Provincial de Valencia, que determinó que “En materia de costas ha de ser aplicable, en este caso, el precepto citado en la sentencia, art. 394 LEC, por la remisión que efectúa el art. 826 del mismo cuerpo Legal al juicio verbal, sin que se contenga específicamente, en el juicio cambiario otro precepto que aborde la imposición de costas que el art. 822, que regula su imposición para el caso en que el deudor requerido atienda el pago. La remisión al juicio verbal es completa y sin otra matización que deriva del precepto, lo que obviamente comporta que su finalización sea conforme las normas ordinarias y, por tanto, por éstas se rija la imposición de costas, siendo carente de consistencia jurídica suficiente la aplicación analógica del art. 561 LEC, que postula el recurrente, puesto que, si bien en origen existía identidad de principios, la actual regulación diferencia claramente su tramitación y el planteamiento de la oposición, aunque tenga ciertos elementos comunes, lo que impide acudir a la norma específica de otro procedimiento, debiendo, en su caso, integrarse las deficiencias de regulación —que tampoco aquí se producen— salvo remisión concreta, con las normas generales, que es lo que aquí procede, si bien por la genérica remisión a que anteriormente nos hemos referido”.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL: Tenga por presentado este escrito, documentos y copias de todo ello, se sirva admitirlo, teniendo por formulada demanda de oposición al juicio cambiario promovido por la representación procesal de D./Dña. [NOMBRE Y APELLIDOS], dando a la misma el impulso procedimental pertinente con el recibimiento a prueba que se deja desde este momento interesado, para [COMPLETAR], en definitiva, dictar sentencia mediante la que se estime la causa de oposición invocada, y en consecuencia se desestime la demanda de juicio cambiario formulada por la representación procesal de D./Dña. [NOMBRE Y APELLIDOS], absolviendo a nuestro representado de todas las pretensiones deducidas en su contra (en su caso: y ordenando el inmediato levantamiento de los embargos trabados), e imponiendo expresamente a D./Dña. [NOMBRE Y APELLIDOS] (demandante principal de juicio cambiario) las costas del proceso.

Por ser Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
