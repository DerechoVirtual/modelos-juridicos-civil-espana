---
name: reconvencion-otrosi-988
description: "Redacta el escrito «Reconvención por otrosí» (formulario 988 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reconvención por otrosí

> Formulario 0988 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] IMPORTE (5 veces)
- [ ] NÚMERO (5 veces)
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…en nombre y representación de la empresa»; «…(actor de la demanda principal), y»; «…a que se le condene al pago a la empresa»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 406 de la LEC
- art. 409 de la LEC
- art. 406.2 de la LEC
- art. 406.1 de la LEC
- art. 1594 del CC
- art. 1588 del CC
- art. 394 de la LEC

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

### Formulario 0988 · Reconvención por otrosí

- Año del modelo: 2013
- Revisión 17-11-2026: 15 campos de relleno marcados en blanco; 7 huecos del original que se habían perdido sin marca, marcados (IMPORTE, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

OTROSÍ DIGO: Que mediante el presente escrito y en aplicación del art. 406 de la LEC, D. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de la empresa [COMPLETAR], según acredito con poder notarial que se acompaña con la contestación, formulo demanda reconvencional contra D. [NOMBRE Y APELLIDOS] (actor de la demanda principal), y [COMPLETAR] (en su caso, frente a D. [NOMBRE Y APELLIDOS]) en reclamación de [IMPORTE] euros que adeuda a mi representado, por impago de prestaciones derivadas de contrato, con base en los siguientes

HECHOS

Hasta que se impidió a mi representado finalizar la obra que D. había contratado con él mediante la exigencia de la devolución de las llaves de la vivienda, los operarios de la empresa habían realizado una parte de la obra que se valora en [IMPORTE] euros.

Adjuntamos como doc. n.º [NÚMERO] de la reconvención escrito en el que se reconoce por el actor que a su instancia, el día [FECHA] se le han entregado las llaves de su vivienda, y con el n.º [NÚMERO] el informe elaborado por el perito D. ese mismo día en el que se hace constar la obra realizada hasta ese momento y su valoración económica.

Aunque es cierto que el actor había entregado a esta parte la cantidad de [IMPORTE] euros antes de iniciarse la obra, esa cantidad estaba destinada a la adquisición del material que se iba a instalar en su vivienda. Nos remitimos al doc. n.º [NÚMERO] presentado con la contestación a la demanda en el que se justifica la adquisición, el precio y la fecha. Por este motivo no puede pretender D. [NOMBRE Y APELLIDOS] que no adeuda nada a esta parte, ya que no ha pagado la obra realizada.

Según el informe pericial y conforme a lo pactado en el contrato de fecha [FECHA] que el actor ha presentado como doc. n.º [NÚMERO] D. adeuda a mi representado la cantidad de [IMPORTE] euros.

Acompaño modelo 696 de liquidación de tasa judicial como documento n.º [NÚMERO]

FUNDAMENTOS DE DERECHO

Nos remitimos a los argumentos jurídicos ya alegados en la contestación, añadiendo lo establecido en el art. 61 respecto a la competencia funcional, que otorga el conocimiento de todas las incidencias al mismo Tribunal que esté conociendo del pleito principal.

Tramitación

El art. 409 de la LEC dice que las pretensiones que deduzca el demandado en la reconvención se sustancian y resuelven al propio tiempo y en la misma forma que las que sean objeto de la demanda principal.

Se cumplen los requisitos del art. 406.2 de la LEC, ya que el Tribunal tiene competencia objetiva en esta materia.

Legitimación

El art. 406.1 de la LEC reconoce la legitimación de demandado y demandante. (En su caso, Y el n.º 3 de ese artículo permite interponer demanda reconvencional frente a otros sujetos, además de frente al demandante.)

Fondo del asunto

PRIMERO.— El art. 1594 del CC condiciona la validez del desistimiento de dueño a que indemnice al contratista de todos sus gastos, trabajo y utilidad que pudiera obtener de ella.

En este caso se ha realizado parte de una obra hasta que el propietario ha impedido su continuación, y no se ha liquidado la mano de obra, puesto que ya hemos dicho que lo que se pagó fue el material.

SEGUNDO.— El art. 1588 del CC permite convenir además de la realización de la obra la aportación del material, y el art. 1599 del mismo texto dice que el precio deberá pagarse a la entrega, es decir, como se había pactado.

TERCERO.— Art. 1109 del CC que permite reclamar intereses cuando se acude a la vía judicial.

Costas

En aplicación del art. 394 de la LEC deberán imponerse íntegramente las costas de la reconvención al actor principal, demandado en esta reconvención.

NUEVAMENTE SUPLICO: Que tenga por presentado este escrito con los documentos que acompaño y copia de todo ello, lo admita y tenga formulada demanda reconvencional contra D. [NOMBRE Y APELLIDOS] (en su caso, y contra D. [NOMBRE Y APELLIDOS]) a fin de que en su día, previa la tramitación oportuna con el recibimiento del juicio a prueba que se deja solicitado, se dicte sentencia por la que se le condene al pago a la empresa [COMPLETAR] de [IMPORTE] euros de principal en concepto de pago por prestaciones contratadas, más intereses desde la fecha de interposición de esta pretensión así como que igualmente se le condene al pago de las costas procesales.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
