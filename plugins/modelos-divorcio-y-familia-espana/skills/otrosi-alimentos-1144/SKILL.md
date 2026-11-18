---
name: otrosi-alimentos-1144
description: "Redacta el escrito «Otrosí: alimentos» (formulario 1144 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Otrosí: alimentos

> Formulario 1144 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] IMPORTE (3 veces)
- [ ] Nº
- [ ] ÓRGANO
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…e acompaño reseñado como documentos n.os»; «…y»; «…esta servicios laborales para la empresa»; «…euros, como acredito con»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 158 del Código Civil
- arts. 734 a 736 de la LEC

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

### Formulario 1144 · Otrosí: alimentos

- Año del modelo: 2013
- Revisión 17-11-2026: 1 rangos de artículos despegados («25 a31» → «25 a 31»); 9 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

OTROSÍ DIGO: Que acompaño reseñado como documentos n.os [COMPLETAR] y [COMPLETAR] certificaciones acreditativas de que mi poderdante se encuentra en situación legal de desempleo (podrá, en su caso, resaltarse la condición de beneficiario de justicia gratuita del demandante) y de que no percibe prestación o subsidio alguno por tal motivo. Sus únicos medios de subsistencia derivan de la benevolencia de sus familiares, que aportan los recursos necesarios para el mantenimiento de mi poderdante y su hijo cuya declaración de paternidad persigue.

El demandado D. presta servicios laborales para la empresa [COMPLETAR], y percibe una retribución mensual de [IMPORTE] euros, como acredito con [COMPLETAR], documento que acompaño reseñado con n.º [Nº]

Por dicho motivo, y al amparo de lo dispuesto en los arts. 158 del Código Civil y 768 de la LEC, solicito que por el Tribunal se acuerde fijar alimentos provisionales con cargo al demandado y a favor del hijo de mi poderdante [ÓRGANO], en la suma de [IMPORTE] euros que resultan prudentes en atención a los ingresos del demandado, cantidad que éste deberá entregar a mi representada dentro de los cinco días de cada mes y actualizar, si llega el caso, anualmente, dicha cantidad en la proporción y sentido en que varíe el Índice de Precios al Consumo que fije el Instituto Nacional de Estadística u organismo que lo sustituyere.

Esta solicitud deberá tramitarse conforme a lo previsto en los arts. 734 a 736 de la LEC.

Procede, dadas las circunstancias, que no se fije caución con la adopción de la medida interesada.

NUEVAMENTE SUPLICO AL TRIBUNAL: Que tenga por formulada petición de alimentos provisionales, acordando, previa la tramitación oportuna, fijar en tal concepto, con cargo al demandado y a favor del hijo de mi representada [NOMBRE DEL REPRESENTADO/A], la suma de [IMPORTE] euros mensuales que el demandado deberá entregar a la madre dentro de los cinco días de cada mes y actualizar, si llega el caso, anualmente incrementando o minorando dicha cantidad en la proporción y sentido en que varíe el Índice de Precios al Consumo, y sin fijación de caución a la demandante. Es justicia que reitero en igual lugar y fecha.

========================================================================
