---
name: acumulacion-proceso-universal-solicitud-912
description: "Redacta el escrito «Acumulación a proceso universal: solicitud» (formulario 912 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acumulación a proceso universal: solicitud

> Formulario 0912 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] SEDE (5 veces)
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] DESCRIBIR (6 veces)
- [ ] ACTO O RESOLUCIÓN (3 veces)
- [ ] NÚMERO (7 veces)
- [ ] Nº
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Juicio»; «…, PLAZA N.º»; «…ferenciado con número de autos de juicio»; «…tado se siguen, también, autos de juicio»; «…numeración del juzgado de procedencia).]»; «…referenciados como autos de juicio»; «…que se sigue con n.º [Nº] de autos»; «…ncursal que se sigue con dicha mercantil»; «…la solicitud el trámite pertinente, para»; «…que se acuerde la acumulación del juicio»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 98 de la LEC
- arts. 81 y 87 de la LEC

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

### Formulario 0912 · Acumulación a proceso universal: solicitud

- Año del modelo: 2013
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 36 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio [COMPLETAR] n.º [Nº DE PROCEDIMIENTO]/[AÑO]

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, interviniendo en nombre de D./Dña. [NOMBRE Y APELLIDOS], cuyas circunstancias personales constan en la escritura de poder que acompaño en debida forma para acreditar mi representación, ante el Tribunal comparezco en el procedimiento referenciado bajo la dirección del Letrado D./Dña. [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO:

Que ante este Tribunal se sigue proceso universal/sucesorio sobre [DESCRIBIR] contra [ACTO O RESOLUCIÓN], referenciado con número de autos de juicio [COMPLETAR] n.º [NÚMERO].

A instancias de mi representado se siguen, también, autos de juicio [COMPLETAR] sobre [DESCRIBIR] contra [ACTO O RESOLUCIÓN] que se tramitan ante la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] referenciados como autos de juicio [COMPLETAR] n.º [NÚMERO].

Se sigue, en consecuencia, dicho proceso singular contra la empresa concursa/el caudal relicto que es objeto del expediente universal /sucesorio sobre [DESCRIBIR] que se tramita ante este Tribunal.

Por dicho motivo, mediante el presente escrito venimos a solicitar la acumulación del proceso singular sobre [DESCRIBIR] que se sigue con n.º [Nº] de autos [COMPLETAR] de la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO] al presente proceso universal.

A los efectos previstos en el art. 98 de la LEC se expone como razón que justifica la acumulación

 (desarrollar la razón en que se fundamenta la solicitud de acumulación: p. ej.: la concurrencia de un proceso singular —el que se sigue a instancias de mi mandante contra la empresa “, SL” aquí sometida a proceso concursal—).

Baso esta solicitud de acumulación de procesos en los siguientes

FUNDAMENTOS DE DERECHO

El art. 98 de la LEC determina que procede la acumulación de procesos: “1.º Cuando esté pendiente un proceso concursal al que se halle sujeto el caudal contra el que se haya formulado o formule cualquier demanda. En estos casos se procederá conforme a la legislación concursal. 2.º Cuando se esté siguiendo un proceso sucesorio al que se halle sujeto el caudal contra el que se haya formulado o se formule una acción relativa a dicho caudal”. Por su parte, el art. 138.1 del Texto Refundido de la Ley Concursal establece: “Los juicios en los que se hubieran ejercitado acciones de responsabilidad contra los administradores o liquidadores, de derecho o hecho; contra la persona natural designada para el ejercicio permanente de las funciones propias del cargo de administrador persona jurídica, contra la persona, cualquiera que sea su denominación, que tenga atribuidas facultades de más alta dirección de la sociedad cuando no exista delegación permanente de facultades del consejo en uno o varios consejeros delegados, y contra los auditores por los daños y perjuicios causados a la persona jurídica concursada, se acumularán de oficio al concurso, siempre que se encuentren en primera instancia y no haya finalizado el acto del juicio o la vista”.

(desarrollar circunstancias que aconsejan la acumulación y acrediten su encaje en uno de los dos supuestos legales del art. 98 de la LEC: p.ej.: Se interesa la acumulación de un proceso singular que versa sobre [DESCRIBIR] dirigido contra la empresa “X, SL”, al proceso concursal que se sigue con dicha mercantil [COMPLETAR]).

La acumulación habrá de solicitarse ante el Tribunal que conozca del proceso universal o sucesorio: art. 98.2. de la LEC.

Se cumplen los presupuestos procesales previstos en los arts. 81 y 87 de la LEC, al solicitarse la acumulación por escrito, dejarse perfectamente identificados los procesos cuya acumulación se pide, el tribunal para el que procede la acumulación, y expresada la razón por la que se solicita la acumulación.

(desarrollar los restantes fundamentos jurídicos de la pretensión de acumulación).

Por todo lo expuesto,

SUPLICO AL TRIBUNAL: Tenga por presentado este escrito, se sirva admitirlo, teniendo por solicitada la acumulación del proceso singular que se sigue a instancia de mi mandante contra [ACTO O RESOLUCIÓN] que se deja referenciado en el cuerpo del presente escrito al presente proceso universal, dando a la solicitud el trámite pertinente, para [COMPLETAR], en definitiva, dictar auto mediante el que se acuerde la acumulación del juicio [COMPLETAR] n.º [NÚMERO] de la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO] al juicio universal sobre [DESCRIBIR] n.º [NÚMERO] de este tribunal y dirigir oficio con testimonio de los antecedentes precisos a la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO] requiriendo la acumulación del juicio y el envío de los autos, con el impulso de los demás trámites para la completa efectividad de la acumulación solicitada.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
