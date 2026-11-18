---
name: apelacion-contra-auto-sobreseimiento-ejecucion-clausula-832
description: "Redacta el escrito «Apelación contra el auto de sobreseimiento de la ejecución por cláusula abusiva» (formulario 832 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Apelación contra el auto de sobreseimiento de la ejecución por cláusula abusiva

> Formulario 0832 del plugin **Ejecución civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.
- **Inmuebles** (referencia catastral, superficie, uso) → `consultar_catastro` (y `callejero_catastro` para localizar la dirección).

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
- [ ] AÑO (5 veces)
- [ ] LOCALIDAD
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] Nº (3 veces)
- [ ] FECHA (3 veces)
- [ ] NÚMERO (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…/[AÑO] de»; «…se el acuerdo de su parte dispositiva de»; «… ejecución, inaplicación de una cláusula»; «…del contrato de préstamo hipotecario»; «…del contrato de préstamo hipotecario»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 455.1 y 695.4 de la LEC
- art. 458.2 de la LEC
- art. 458.1 de la LEC
- art. 398 de la LEC

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

### Formulario 0832 · Apelación contra el auto de sobreseimiento de la ejecución por cláusula abusiva

- Año del modelo: 2013
- Revisión 17-11-2026: 14 campos de relleno marcados en blanco; 4 huecos del original que se habían perdido sin marca, marcados (Nº, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Ejecución hipotecaria n.º [Nº DE PROCEDIMIENTO]/[AÑO]

A LA AUDIENCIA PROVINCIAL DE [LOCALIDAD]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según tengo debidamente acreditado en el procedimiento referenciado, ante la Sala comparezco y como mejor proceda en derecho DIGO:

Que según permite el art. 695.4 en relación con el art. 455.1 ambos de la LEC, interpongo recurso de apelación contra el auto nº [Nº]/[AÑO] de [COMPLETAR] (fecha), por el que se acuerda (Opciones):

• El sobreseimiento de la ejecución

• La inaplicación de una cláusula abusiva

• La desestimación de la oposición por la causa cláusula abusiva

en atención a los siguientes:

Presupuestos

1.º Los arts. 455.1 y 695.4 de la LEC permiten la interposición del presente recurso de apelación.

2º Hacemos constar según exige el art. 458.2 de la LEC contra el auto nº [Nº]/[AÑO] de fecha [FECHA]. Impugnándose el acuerdo de su parte dispositiva de [COMPLETAR] (sobreseimiento de la ejecución, inaplicación de una cláusula [COMPLETAR] del contrato de préstamo hipotecario de fecha [FECHA] por declararla abusiva, desestimación de la oposición por la causa cláusula abusiva).

3.º El recurso se interpone dentro del plazo legalmente establecido en el art. 458.1 de la LEC y se funda en las siguientes:

ALEGACIONES

 (se desarrollarán los motivos de impugnación al recurso que se estimen oportunos).

Por las razones expuestas deberá dejarse sin efecto la resolución recurrida, de modo que se acuerde (Opciones):

•Dejar sin efecto el sobreseimiento, ordenando la continuación de los trámites de ejecución

• Declarar que la cláusula nº… de contrato de préstamo hipotecario de fecha no es conforme a derecho y no abusiva, ordenando continuar los trámites de la ejecución en los términos indicados en la demanda.

• Estimar la oposición de esta parte por la causa de cláusula abusiva, declarando tal la cláusula nº [NÚMERO] del contrato de préstamo hipotecario [COMPLETAR] y, por tanto, sin efecto.

Costas

En aplicación del art. 398 de la LEC deberán imponerse las costas a la parte contraria.

Por lo expuesto,

SUPLICO A LA SALA: Que tenga por presentado este escrito y por formulado recurso de apelación contra el auto n.º [Nº]/[AÑO] de fecha [FECHA] dictado en el presente procedimiento a fin de que en su día la Audiencia Provincial acuerde:

•Dejar sin efecto el sobreseimiento, ordenando la continuación de los trámites de la ejecución.

•Declarar que la cláusula nº… de contrato de préstamo hipotecario de fecha no es conforme a derecho y no abusiva, ordenando continuar los trámites de la ejecución en los términos indicados en la demanda.

•Estimar la oposición de esta parte por la causa de cláusula abusiva, declarando tal la cláusula nº [NÚMERO] del contrato de préstamo hipotecario [COMPLETAR] y, por tanto, sin efecto.

Todo ello con imposición de costas a la parte contraria.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
