---
name: demanda-verbal-cantidad-compraventa-precio-aplazado-1152
description: "Redacta el escrito «Demanda verbal de cantidad por compraventa con precio aplazado» (formulario 1152 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda verbal de cantidad por compraventa con precio aplazado

> Formulario 1152 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (9 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] NÚMERO (3 veces)
- [ ] COLEGIO
- [ ] IMPORTE (4 veces)
- [ ] PROFESIÓN
- [ ] LOCALIDAD
- [ ] DNI/NIE
- [ ] FECHA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, con domicilio en [LOCALIDAD],»; «…(demandado) una escultura de»; «…l vendedor contrató a un especialista en»; «…rajudicial. En este sentido, se acudió a»; «…mplimiento de contrato de compraventa de»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 21 y 22 de la LOPJ
- arts. 45 y 50 de la LEC
- art. 250.2 de la LEC
- art. 10 de la LEC
- arts. 23 y 31 de la LEC
- art. 437.1 LEC
- art. 5 de la Ley Orgánica 1/2025
- art. 1500 del CC
- art. 1100 del CC
- art. 394 de la LEC
- arts. 149 y 152 de la LEC

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

### Formulario 1152 · Demanda verbal de cantidad por compraventa con precio aplazado

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 30 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda Juicio verbal

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] Q.P.T.R.C.

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], ante el Tribunal comparezco bajo la asistencia letrada de D./Dña. [NOMBRE Y APELLIDOS] (Colegiado n.º [NÚMERO] del Iltre. Colegio de Abogados de [COLEGIO]), y como mejor proceda en Derecho DIGO:

Que mediante el presente escrito interpongo demanda a tramitar por el cauce del juicio verbal ejercitando acción en reclamación de la cantidad de [IMPORTE] euros, más los intereses desde la interposición de la demanda, frente a D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, de profesión [PROFESIÓN], con domicilio en [LOCALIDAD], [COMPLETAR] (ciudad) y DNI n.º [DNI/NIE], con base en los siguientes

HECHOS

El día [FECHA] mi representado vendió a D./Dña. [NOMBRE Y APELLIDOS] (demandado) una escultura de [COMPLETAR] por un precio de [IMPORTE] euros. A la entrega del objeto en la vivienda del demandado se entregó la mitad de esa cantidad y de forma verbal se manifestó que el resto se entregaría diez días más tarde en el local del actor. Aunque no era esa la forma de liquidación de la deuda que se había acordado, el vendedor decidió aceptarla porque no dudó de la solvencia del comprador. Acompañamos como docs.

 el albarán de entrega donde consta el precio total, con el recibí firmado por el demandado y el recibo de la mitad del precio suscrito por el actor.

Transcurrido el plazo unilateralmente fijado por D./Dña. [NOMBRE Y APELLIDOS], mi representado le llamó por teléfono para preguntar cuál era el motivo del retraso del pago, a lo que el otro contestó que se sentía engañado porque la pieza no era original y que no pensaba pagar más.

Ante la duda suscitada el vendedor contrató a un especialista en [COMPLETAR] para que elaborara un informe sobre la calidad de la obra, tras consentir el comprador que la misma fuera inspeccionada por aquél. Acompañamos el citado informe pericial donde se manifiesta sin ningún género de dudas que la pieza es auténtica con el n.º [NÚMERO].

Presentado el citado informe al comprador, decidió no considerarlo cierto y mantenerse en su postura, motivo por el cual nos vemos obligados a reclamar el pago de la cantidad adeudada de [IMPORTE] euros, por vía judicial.

Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

(En su caso) Adjuntamos modelo 696 de liquidación de la tasa judicial como documento n.º [NÚMERO].

FUNDAMENTOS DE DERECHO

Jurisdicción y competencia

Los arts. 21 y 22 de la LOPJ consideran que la jurisdicción competente en esta materia es la española, y los arts. 45 y 50 de la LEC, en relación con lo dispuesto en el art. 85.1º LOPJ, atribuyen la competencia territorial al Tribunal al que nos dirigimos al ser éste el lugar del domicilio del demandado.

Tramitación

El art. 250.2 de la LEC remite al juicio verbal las demandas cuya cuantía no supere los 15.000 euros.

Legitimación

En aplicación del art. 10 de la LEC D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] son los legitimados de forma activa y pasiva al ser ambos titulares de la relación jurídica de la que se deriva la deuda.

Postulación

Los arts. 23 y 31 de la LEC exigen la intervención de Procurador y Abogado en los juicios verbales de cuantía superior a los 2.000 euros.

Cumplimiento de los requisitos de procedibilidad.

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC en relación con el art. 437.1 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Fondo del asunto

1.º Art. 1258 del CC: los contratos se perfeccionan por el mero consentimiento, y desde entonces obligan al cumplimiento de lo expresamente pactado. Aunque el pacto fue verbal, se acredita su existencia y contenido con el resto de los documentos que presentamos.

2.º El art. 1500 del CC fija la obligación del comprador de pago en los contratos de compraventa.

3.º Al haber incurrido en mora, según el art. 1100 del CC, el comprador está obligado al pago de intereses, según determina el art. 1501.3 del mismo texto.

Costas

En aplicación del art. 394 de la LEC deberán imponerse al demandado.

Por lo puesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño, adjuntando a este escrito listado de documentos, y copia de todo ello, lo admita y acuerde tener por interpuesta demanda a tramitar por el cauce del juicio verbal, a fin de que en su día, previos los trámites legales oportunos se dicte en su día sentencia por la que se condene a D./Dña. [NOMBRE Y APELLIDOS] al pago a mi representado de la cantidad de [IMPORTE] euros en cumplimiento de contrato de compraventa de [COMPLETAR] celebrado entre ambos, más el abono de intereses desde la interposición de la demanda y al pago de las costas de este procedimiento.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

OTROSI DIGO: que en aplicación de los arts. 149 y 152 de la LEC interesa esta parte que los actos de comunicación sean realizados por el Procurador que suscribe.

NUEVAMENTE SUPLICO: Que se de traslado directo de los actos de comunicación a este Procurador para su diligenciamiento, por ser justicia que pido en mismo lugar y fecha.

========================================================================
