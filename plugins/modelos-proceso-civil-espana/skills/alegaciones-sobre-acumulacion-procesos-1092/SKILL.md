---
name: alegaciones-sobre-acumulacion-procesos-1092
description: "Redacta el escrito «Alegaciones sobre la acumulación de procesos» (formulario 1092 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones sobre la acumulación de procesos

> Formulario 1092 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO (3 veces)
- [ ] AÑO (2 veces)
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] DESCRIBIR (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Juicio»; «…, PLAZA N.º»; «…roceda en derecho DIGO: Que con fecha de»; «…e se solicita la acumulación, por cuanto»; «…, en los que concurre la circunstancia»; «…eferenciados con números de autos juicio»; «…stanciar el trámite en legal forma, para»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 82 de la LEC
- art. 81 de la LEC
- art. 76 de la LEC
- art. 78.2 de la LEC
- art. 85.2 de la LEC

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

### Formulario 1092 · Alegaciones sobre la acumulación de procesos

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 16 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio [COMPLETAR] n.º [Nº DE PROCEDIMIENTO]/[AÑO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS] según tengo acreditado en los autos referenciados, ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que con fecha de [COMPLETAR] se me ha dado traslado de la solicitud de acumulación de procesos formulada por la representación procesal del demandante D./Dña. [NOMBRE Y APELLIDOS], concediendo a esta parte plazo de diez días para manifestaciones acerca de la acumulación solicitada. Evacuando dicho trámite, mediante el presente escrito formulo las siguientes

ALEGACIONES

 (Desarrollar las que interesen al derecho de la parte).

Si se desea plantear oposición a la solicitud de acumulación pueden desarrollarse los fundamentos jurídicos de la oposición:

Aun cuando el Tribunal en atención al art. 82 de la LEC debería repeler las solicitudes que no cumplan los requisitos establecidos en el art. 81 de la LEC, entendemos no se cumplen los presupuestos procesales previstos en el citado art. 81 de la LEC, al no haberse identificado los procesos cuya acumulación se pide claramente y expresada la razón por la que se solicita la acumulación, por cuanto [COMPLETAR] (desarrollar causa de oposición).

El art. 76 de la LEC determina que procede la acumulación de procesos: “1.º Siempre que la sentencia que haya de recaer en uno de los procesos pueda producir efectos prejudiciales en el otro. 2.º Entre los objetos de los procesos cuya acumulación se trate exista tal conexión que, de seguirse por separado, pudieren dictarse sentencias con pronunciamientos o fundamentos contradictorios, incompatibles o mutuamente excluyentes.”

Se interesa la acumulación de dos procesos que versan respectivamente sobre [DESCRIBIR] y sobre [DESCRIBIR], en los que concurre la circunstancia [COMPLETAR] (desarrollar circunstancias que aconsejan el rechazo de la acumulación por falta de encaje en uno de los dos supuestos legales del art. 76 de la LEC.)

Los procesos cuya acumulación se pide fueron promovidos por el mismo demandante, quien tuvo ocasión de acumular las acciones en un mismo proceso, por lo que no procede la acumulación, según el art. 78.2 de la LEC. La justificación esgrimida de contrario carece de validez si consideramos que

(Desarrollar las restantes causas de oposición a la pretensión de acumular procesos).

Al rechazarse la pretensión de acumulación se impondrán las costas del inicidente al solicitante (art. 85.2 de la LEC).

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito, se sirva admitirlo, teniendo por evacuado el trámite conferido y por opuesta (o por conforme) a esta parte a la acumulación de los procesos referenciados con números de autos juicio [COMPLETAR] número [Nº DE PROCEDIMIENTO] y juicio número [Nº DE PROCEDIMIENTO] de este tribunal solicitada por la parte actora y ordenando sustanciar el trámite en legal forma, para [COMPLETAR], en definitiva, dictar auto mediante el que se acuerde desestimar (o estimar) la acumulación interesada, con expresa imposición de costas del incidente a la parte solicitante,

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
