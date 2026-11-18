---
name: contestacion-demanda-arbitral-reconvencion-arbitraje-1470
description: "Redacta el escrito «Contestación a demanda arbitral con reconvención (arbitraje de equidad)» (formulario 1470 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a demanda arbitral con reconvención (arbitraje de equidad)

> Formulario 1470 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] LOCALIDAD
- [ ] Nº DE DOCUMENTO
- [ ] FECHA (3 veces)
- [ ] NÚMERO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 5 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…dez del convenio arbitral de la cláusula»; «…, denominada «», sita en la localidad de»; «…los recibos que acompaño como documentos»; «…recibió un requerimiento notarial de Don»; «…y condene a D»

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 1470 · Contestación a demanda arbitral con reconvención (arbitraje de equidad)

- Año del modelo: 2014
- Revisión 17-11-2026: 13 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Encabezamiento
ALEGACIONES
Solicitud a la corte de arbitraje
Firmas

Procedimiento arbitral número [Nº DE PROCEDIMIENTO]

AL TRIBUNAL ARBITRAL DE [LOCALIDAD]

ALEGACIONES

Se niegan los hechos relatados en la demanda arbitral, salvo los que resulten expresamente reconocidos.

En este punto, se acepta la existencia del contrato de compraventa acompañado como documento número [Nº DE DOCUMENTO] y la existencia y validez del convenio arbitral de la cláusula [COMPLETAR] alegado de contrario, acordándose que se resolvería la controversia por un único árbitro en equidad.

La reclamación de la cantidad que pide el demandante en virtud del citado contrato privado de compraventa es improcedente a todas luces por cuanto que el demandante ha incumplido sus obligaciones como seguidamente se expondrá.

En efecto, al como consta en el contrato, el demandante enajenaba a esta parte la siguiente finca rústica «una parcela de terreno de secano, denominada «», sita en la localidad de [COMPLETAR], de la siguiente extensión: 53 hectáreas, 96 áreas y 70 centiáreas”, entrando en posesión de la finca.

Esta parte satisfizo mediante tres entregas las tres cuartas partes del precio de la venta, fijada en 20.000 euros, es decir, 15.000 euros, como se acredita por los recibos que acompaño como documentos [COMPLETAR], quedando pendientes de pago los 5.000 euros que ahora pretende reclamar el demandante.

No obstante, el pasado día [FECHA] esta parte recibió un requerimiento notarial de Don [COMPLETAR], que no es parte en este proceso, instándole a que desalojara una porción de la citada finca, de una extensión de 23 hectáreas, 46 áreas y 35 centiáreas, aduciendo que ésta porción le había sido enajenada por el demandado mediante un contrato privado de compraventa, elevado a escritura pública en fecha [FECHA], el cual me fue entregado por copia (acompaño dicha copia junto al presente escrito, como doc. núm [NÚMERO]).

Resulta claro, por tanto, la improcedencia de la reclamación del demandante, puesto que pretende percibir el total del precio por una finca que vendió dos veces, de lo que es patente que debe desestimarse la demanda.

Esta parte pretende asimismo deducir RECONVENCIÓN contra el actor, instando la resolución del contrato de compraventa, puesto que es obvio que esta parte al consentir sobre el objeto y precio de la compraventa, elementos esenciales de dicho contrato, se refería a la totalidad de la finca vendida de extensión “53 hectáreas, 96 áreas y 70 centiáreas”, y no a una porción de la misma, sensiblemente inferior, lo cual determina que deba resolverse el contrato e indemnizar el demandante a esta parte en la cantidad de 15.000 euros, importe de la parte del precio pagado, con más los intereses legales, por su mala fe al vender dos veces la misma finca.

Esta parte pretende proponer la prueba testifical de D, comprador de la parte de la finca que fue vendida por dos veces por el demandado.

Las costas y gastos del arbitraje deben ser satisfechos por el demandado, de acuerdo al art. 37.6 de la LA y al reglamento de la Corte y a lo pactado por las partes.

En atención a lo expuesto

SOLICITO A LA CORTE DE ARBITRAJE DE, que teniendo por presentado este escrito con sus copias y documentos acompañados, se sirva admitirlo, y tenga por contestada en tiempo y forma la demanda arbitral y por formulada reconvención, tras los trámites previstos en el Reglamento de la Corte de Arbitraje, dicte Laudo Arbitral en el que:

1.- Desestime íntegramente la demanda

2.- Estime la reconvención y, en su virtud, declare resuelto el contrato de compraventa de fecha [FECHA] y condene a D [COMPLETAR] a que indemnice a esta parte en la cantidad de 15.000 euros con más los intereses legales desde que fueron percibidos por el demandado reconvencional.

3.- Condene al demandado a pagar las costas de este procedimiento así como a abonar los honorarios del árbitro y la tasa de administración que se determinen.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del demandado reconviniente, representante y/o abogado

========================================================================
