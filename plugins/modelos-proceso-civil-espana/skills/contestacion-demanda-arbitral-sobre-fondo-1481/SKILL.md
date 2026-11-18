---
name: contestacion-demanda-arbitral-sobre-fondo-1481
description: "Redacta el escrito «Contestación a demanda arbitral sobre el fondo» (formulario 1481 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a demanda arbitral sobre el fondo

> Formulario 1481 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] FECHA
- [ ] IMPORTE
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…dez del convenio arbitral de la cláusula»; «…ofesional. Es cierto que en los meses de»; «…arte solicitó la presencia del notario D»; «…ue elaborado por el Arquitecto Técnico D»; «…ericial referido y factura de la empresa»; «…cal del empresario que realizó la obra D»; «…y la pericial del Arquitecto Técnico D»

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

### Formulario 1481 · Contestación a demanda arbitral sobre el fondo

- Año del modelo: 2014
- Revisión 17-11-2026: 14 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Encabezamiento
HECHOS
FUNDAMENTOS DE DERECHO
Solicitud a la corte de arbitraje
Firmas

Procedimiento arbitral número [Nº DE PROCEDIMIENTO]

AL TRIBUNAL ARBITRAL DE [LOCALIDAD]

HECHOS

Se niegan los hechos relatados en la demanda arbitral, salvo los que resulten expresamente reconocidos.

En este punto, se acepta la existencia del contrato acompañado como documento número [Nº DE DOCUMENTO] entre el demandante y el demandado, en su calidad de constructor, para la instalación de la carpintería para las ventanas de veinte viviendas y zonas comunes en el edificio sito en y la existencia y validez del convenio arbitral de la cláusula [COMPLETAR] alegado de contrario.

Negamos rotundamente que esta parte incumpliera el contrato, puesto que el único incumplimiento ha sido el del demandante, quien instaló defectuosamente todas las ventanas, presentado graves deficiencias en el material empleado que han determinado la necesidad de desmontarlas y reponerlas por parte de otro profesional.

Es cierto que en los meses de [COMPLETAR], el demandante instaló las ventanas, pero pronto aparecieron deficiencias, que se pusieron en su conocimiento, comprometiéndose el demandante a solucionarlas.

Ante el tiempo transcurrido sin que el demandante reparara los defectos, pese a los múltiples requerimientos, esta parte solicitó la presencia del notario D [COMPLETAR] en fecha [FECHA], quien levantó acta notarial donde se incorporan las fotografías de las ventanas en el estado en que se encontraban después de ser instaladas por el demandante, y que se acompañan como documento número

En la misma fecha, se dirigió nuevo requerimiento al demandado por conducto notarial para que subsanara las deficiencias, lo cual no hizo, por lo que esta parte se vio en la obligación de emitir un informe pericial sobre el estado de la obra, el cual fue elaborado por el Arquitecto Técnico D [COMPLETAR], y a contratar a otra empresa para finalizar la obra, ante la premura del plazo de entrega de las viviendas.

A efectos acreditativos, acompaño como documentos número [Nº DE DOCUMENTO] requerimiento dirigido al demandado, informe pericial referido y factura de la empresa [COMPLETAR] por importe de [IMPORTE] euros por la instalación de las ventanas.

En este punto, es interés de esta parte proponer en el procedimiento la testifical del empresario que realizó la obra D [COMPLETAR] y la pericial del Arquitecto Técnico D [COMPLETAR] que elaboró el dictamen que se acompaña.

FUNDAMENTOS DE DERECHO

Se aceptan los fundamentos de la demanda.

Oposición de fondo

Son de aplicación los preceptos invocados por el demandante, en sentido contrario, no ostentando derecho alguno a percibir el precio pactado ante los graves incumplimientos de contrato que han quedado expuestos, imputables a la mala fe y negligencia del demandante.

Costas y gastos

Es de aplicación lo establecido en el art. 37.6 de la Ley de Arbitraje y en los arts. del Reglamento de la Corte.

En atención a lo expuesto

SOLICITO A LA CORTE DE ARBITRAJE DE que teniendo por presentado este escrito con sus copias y documentos acompañados, se sirva admitirlo, y tenga por contestada en tiempo y forma la demanda arbitral y, tras los trámites previstos en el Reglamento de la Corte de Arbitraje, dicte Laudo Arbitral en el que desestime íntegramente la demanda y condene al demandado a pagar las costas de este procedimiento así como a abonar los honorarios del árbitro y la tasa de administración que se determinen.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del demandado, representante y/o abogado

========================================================================
