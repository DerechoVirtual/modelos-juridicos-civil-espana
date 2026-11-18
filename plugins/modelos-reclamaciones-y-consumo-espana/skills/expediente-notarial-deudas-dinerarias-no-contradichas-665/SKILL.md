---
name: expediente-notarial-deudas-dinerarias-no-contradichas-665
description: "Redacta el escrito «Expediente notarial de deudas dinerarias no contradichas» (formulario 665 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Expediente notarial de deudas dinerarias no contradichas

> Formulario 0665 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] DNI/NIE
- [ ] FECHA (5 veces)
- [ ] LOCALIDAD
- [ ] IMPORTE (10 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…A LA NOTARÍA DE»; «…ndición de administrador de la mercantil»; «…, domiciliada en»; «…de»; «…de [COMPLETAR] de»; «…, comerciante dedicado a la actividad de»; «…de»; «…de [COMPLETAR] de»; «…de [COMPLETAR] y el día [FECHA] de»; «…y el día [FECHA] de [COMPLETAR] de»; «…de»; «…de [COMPLETAR] de»; …

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

### Formulario 0665 · Expediente notarial de deudas dinerarias no contradichas

- Año del modelo: 2015
- Revisión 17-11-2026: 31 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA NOTARÍA DE [COMPLETAR]

D. [NOMBRE Y APELLIDOS] con DNI [DNI/NIE], en su condición de administrador de la mercantil [COMPLETAR], domiciliada en [COMPLETAR], según acredito por escritura de fecha [FECHA] de [COMPLETAR] de [COMPLETAR], por medio de la presente formulo solicitud de expediente notarial de reclamación de deudas dinerarias no contradichas frente a D. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], reclamando la cantidad total de [IMPORTE] euros, desglosada en [IMPORTE] euros de principal, [IMPORTE] euros en concepto de intereses remuneratorios y [IMPORTE] euros en concepto de intereses de demora, en base a los siguientes

HECHOS Y FUNDAMENTOS

La deuda origen de la presente reclamación tiene su origen en los suministros que por parte de la mercantil de la que soy administrador se hicieron a D. [NOMBRE Y APELLIDOS], comerciante dedicado a la actividad de [COMPLETAR], en el periodo comprendido entre el día [FECHA] de [COMPLETAR] de [COMPLETAR] y el día [FECHA] de [COMPLETAR] de [COMPLETAR] ascendiendo su importe a [IMPORTE] euros.

Como consecuencia de dicho impago y ante las dificultades de tesorería alegadas por el deudor, la entidad que represento libró letra de cambio en fecha [FECHA] de [COMPLETAR] de [COMPLETAR], la cual fue aceptada por el deudor, por importe de [IMPORTE] euros y con vencimiento en fecha [FECHA] de [COMPLETAR] de

A fin de acreditar dicha deuda, se acompañan a esta solicitud los documentos núm. consistentes en facturas impagadas y el documento núm. letra de cambio aceptada por el deudor.

Atendido lo anterior, se insta la iniciación del expediente prevenido en los arts. 70 y 71 de la Ley del Notariado, al darse los requisitos exigidos en el precepto que son los siguientes:

1) la deuda es líquida, determinada, vencida y exigible, y asciende al importe total de [IMPORTE] euros, desglosada en [IMPORTE] euros de principal, [IMPORTE] euros de intereses remuneratorios y [IMPORTE] euros de intereses de demora.

2) el domicilio del deudor se encuentra en esta demarcación notarial pues así consta en las facturas y en la letra de cambio aceptada.

3) la deuda se acredita suficientemente por los documentos que se acompañan por original consistentes en facturas y letra de cambio aceptada.

En base a lo anterior,

SOLICITO AL NOTARIO que tenga por presentada esta solicitud de reclamación de deuda dineraria, la admita y proceda a requerir de pago al deudor en legal forma, siguiendo el expediente sus trámites según el resultado del requerimiento y, en su caso, dejando constancia en el acta para el caso que el deudor no abonare la deuda, no compareciere o no alegare motivos de oposición a fin de que pueda instarse el despacho de ejecución.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

(Firma del solicitante)

========================================================================
