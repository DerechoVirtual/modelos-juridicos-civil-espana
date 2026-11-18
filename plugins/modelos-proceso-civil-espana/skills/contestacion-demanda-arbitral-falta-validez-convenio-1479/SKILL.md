---
name: contestacion-demanda-arbitral-falta-validez-convenio-1479
description: "Redacta el escrito «Contestación a demanda arbitral por falta de validez del convenio» (formulario 1479 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a demanda arbitral por falta de validez del convenio

> Formulario 1479 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…venio arbitral, contenido en la cláusula»; «…ondo, se desestime la demanda presentada»

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

### Formulario 1479 · Contestación a demanda arbitral por falta de validez del convenio

- Año del modelo: 2014
- Revisión 17-11-2026: 7 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Encabezamiento
HECHOS
FUNDAMENTOS DE DERECHO
Solicitud a la Corte de Arbitraje
Firmas

Procedimiento arbitral número [Nº DE PROCEDIMIENTO]

AL TRIBUNAL ARBITRAL DE [LOCALIDAD]

HECHOS

Negamos los hechos relatados por la entidad demandante en su demanda arbitral, alegando, con carácter previo y al amparo de lo dispuesto en el artículo 22 de la Ley de Arbitraje la nulidad de pleno derecho del convenio arbitral, contenido en la cláusula [COMPLETAR] del contrato de fecha [FECHA] aportado de contrario.

La citada cláusula contractual está incluida en un contrato de adhesión celebrado con el demandado en su condición de consumidor, incluido en el ámbito del artículo 3 del Texto Refundido de la ley General para la Defensa de Consumidores y Usuarios, RDL 1/2007, el cual fija el concepto de consumidor al indicar que: "a efectos de esta norma y sin perjuicio de lo dispuesto expresamente en sus libros tercero y cuarto, son consumidores o usuarios las personas físicas que actúen con un propósito ajeno a su actividad comercial, empresarial, oficio o profesión. Son también consumidores a efectos de esta norma las personas jurídicas y las entidades sin personalidad jurídica que actúen sin ánimo de lucro en un ámbito ajeno a una actividad comercial o empresarial". En este supuesto, no cabe duda que el demandante concertó el préstamo con la entidad demandante para la adquisición de un vehículo particular, por lo que actúa fuera del ámbito propio de su actividad profesional.

Por tanto, la entidad demandante pretende hacer valer un convenio arbitral con el demandado, en su condición de consumidor, inserto en un contrato de adhesión, para dirimir controversias futuras, sin que el mismo produzca efectos vinculantes para el consumidor según dispone el art. 57.4 del Texto Refundido de la ley General para la Defensa de Consumidores y Usuarios, y haciendo valer una cláusula abusiva, definida como tal en el art. 90.1 del citado Texto Refundido, sancionándose en el art. 83 con la nulidad de pleno derecho.

Para el improbable caso que no se aceptara la excepción

FUNDAMENTOS DE DERECHO

PRIMERO.- Nulidad del Convenio arbitral

Son de aplicación los artículos 22.2 de la Ley de Arbitraje y 57.4, 82 y 90.1 del Texto Refundido de la Ley General para la Defensa de Consumidores y Usuarios.

El artículo 22.2 de la Ley de Arbitraje establece que el demandado puede oponer las excepciones relativas a la existencia y validez del convenio arbitral en el momento de presentar la contestación, sin que el hecho de haber designado o participado en el nombramiento de los árbitros se lo impida.

El art. 90.1 del citado TRLGDCU dispone que son abusivas las cláusulas que establezcan “la sumisión a arbitrajes distintos del arbitraje de consumo, salvo que se trate de órganos de arbitraje institucionales creados por normas legales para un sector o un supuesto específico” y el art. 83 sanciona que las cláusulas abusivas son nulas de pleno derecho.

SEGUNDO.-Oposición de fondo

TERCERO.-Costas y gastos

Es de aplicación lo establecido en el art. 37.6 de la Ley de Arbitraje y en los arts. del Reglamento de la Corte.

En atención a lo expuesto

SOLICITO A LA CORTE DE ARBITRAJE DE que teniendo por presentado este escrito con sus copias y documentos acompañados, se sirva admitirlo, y tener por contestada la demanda arbitral en tiempo y forma y, en su virtud, y tras los trámites legales

1.- Se declare la nulidad del convenio arbitral de fecha [FECHA] y, en consecuencia, se estime la excepción de falta de competencia de los árbitros para resolver la controversia, con desestimación de la demanda.

2.- Subsidiariamente y en cuanto al fondo, se desestime la demanda presentada [COMPLETAR]

3.- Condene al demandante a pagar las costas de este procedimiento así como a abonar los honorarios del árbitro y la tasa de administración que se determinen.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del demandado, representante y/o abogado

========================================================================
