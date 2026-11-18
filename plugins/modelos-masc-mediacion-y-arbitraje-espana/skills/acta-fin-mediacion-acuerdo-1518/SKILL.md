---
name: acta-fin-mediacion-acuerdo-1518
description: "Redacta el escrito «Acta de fin de mediación con acuerdo» (formulario 1518 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acta de fin de mediación con acuerdo

> Formulario 1518 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] DNI/NIE (2 veces)
- [ ] CALLE (2 veces)
- [ ] Nº (2 veces)
- [ ] FECHA (3 veces)
- [ ] IMPORTE (2 veces)
- [ ] LOCALIDAD
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 20 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, y domiciliado en»; «…, C.P., calle [CALLE], núm. [Nº], piso»; «…, núm. [Nº], piso [COMPLETAR], letra»; «…letra [COMPLETAR], dirección electrónica»; «…, y domiciliado en»; «…, C.P., calle [CALLE], núm. [Nº], piso»; «…, núm. [Nº], piso [COMPLETAR], letra»; «…letra [COMPLETAR], dirección electrónica»; «…,»; «…licto entre ellas existente por razón de»; «…de»; «…e Que el objeto sometido a mediación fue»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 23 de la Ley 5/2012

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

### Formulario 1518 · Acta de fin de mediación con acuerdo

- Año del modelo: 2014
- Revisión 17-11-2026: 33 campos de relleno marcados en blanco; 6 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Parte
EXPONEN
TÉRMINOS
Firmas

ACTA FINAL DE MEDIACIÓN CON ACUERDO

Número de expediente

Institución de mediación

Partes:

Personas participantes

D. [NOMBRE Y APELLIDOS], mayor de edad, con DNI [DNI/NIE], y domiciliado en [COMPLETAR], C.P., calle [CALLE], núm. [Nº], piso [COMPLETAR], letra [COMPLETAR], dirección electrónica [COMPLETAR], y teléfono

Y D. [NOMBRE Y APELLIDOS], mayor de edad, con DNI [DNI/NIE], y domiciliado en [COMPLETAR], C.P., calle [CALLE], núm. [Nº], piso [COMPLETAR], letra [COMPLETAR], dirección electrónica [COMPLETAR], y teléfono

Mediador: D. [NOMBRE Y APELLIDOS], [COMPLETAR]

EXPONEN

Que las partes manifestaron su voluntad de someter a mediación el conflicto entre ellas existente por razón de [COMPLETAR], según consta en acta de sesión constitutiva de fecha [FECHA] de [COMPLETAR] de

Que el objeto sometido a mediación fue [COMPLETAR]

Que se ha seguido el procedimiento de mediación ajustado a las previsiones de la Ley 5/2012, habiendo intervenido el mediador que suscribe este acta.

Las partes declaran haber participado en la mediación de forma totalmente libre y voluntaria y un ACUERDO sobre su objeto, el cual se refleja a todos los efectos en este acta final, firmándose por las partes en prueba de conformidad conforme a lo dispuesto en el art. 23 de la Ley 5/2012, y el cual se conviene en los siguientes

TÉRMINOS

Ambas partes acuerdan la resolución del contrato de compraventa de fecha [FECHA] de [COMPLETAR] de [COMPLETAR] sobre la finca [COMPLETAR], restituyéndose mutuamente sus respectivas prestaciones, quedando desde este momento el vendedor D. [NOMBRE Y APELLIDOS] en la plena propiedad y posesión de la finca objeto del contrato, y recibiendo el comprador D. la cantidad de [IMPORTE] euros satisfecha en concepto de reintegro de precio de la compraventa.

Respecto de las obras realizada en la finca que fue objeto de compraventa, el vendedor D. indemnizará a D. [NOMBRE Y APELLIDOS] en la cantidad de [IMPORTE] euros, quedando totalmente satisfechas sus pretensiones y reservando en todo caso al vendedor D. el ejercicio de las acciones que pueda dirigir contra el Ayuntamiento de [LOCALIDAD] como consecuencia de los daños y perjuicios derivados del cambio de planeamiento.

El pago de la cantidad pactada se hará efectivo por el vendedor en la cuenta [COMPLETAR] del comprador antes del día [FECHA] de [COMPLETAR] de [COMPLETAR]

Los gastos derivados de la ejecución del presente acuerdo, serán de cargo exclusivamente del vendedor D. [NOMBRE Y APELLIDOS], comprometiéndose la otra parte a realizar cuantas actuaciones sean necesarias para la íntegra ejecución del presente acuerdo.

Ambas partes quedan informadas por el mediador del carácter vinculante del presente acuerdo y de la posibilidad de instar su elevación a escritura pública al objeto de configurar un título ejecutivo, facultándose recíprocamente a acudir al notario si así conviene a su derecho.

Y a los efectos de la finalización del procedimiento de mediación, se firma el presente acuerdo en tres ejemplares [COMPLETAR], por el mediador, y por las partes que en él han intervenido, con entrega de un ejemplar a cada uno de los intervinientes, en la ciudad de [COMPLETAR], a [DÍA] de [MES] de [AÑO]

Firma de las partes y del mediador

========================================================================
