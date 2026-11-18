---
name: expediente-notarial-robo-titulo-valor-630
description: "Redacta el escrito «Expediente notarial por robo de título valor» (formulario 630 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Expediente notarial por robo de título valor

> Formulario 0630 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] NIF
- [ ] LOCALIDAD (4 veces)
- [ ] CORREO ELECTRÓNICO
- [ ] TELÉFONO
- [ ] Nº (2 veces)
- [ ] NÚMERO
- [ ] FECHA (2 veces)
- [ ] IMPORTE (2 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… el solicitante, librado contra el Banco»; «…, Oficina»; «…, en la localidad de»; «… está domiciliada en la entidad bancaria»; «…, número de cuenta»; «…, con vencimiento»; «…iéndose el cheque con el número de serie»; «…alonario emitido por la entidad bancaria»; «…, sucursal de»; «…reconocimiento de deuda en cuya cláusula»; «…mbio para su descuento en la sucursal de»; «… formulada en la Comisaría de Policía de»

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

### Formulario 0630 · Expediente notarial por robo de título valor

- Año del modelo: 2015
- Revisión 17-11-2026: 26 campos de relleno marcados en blanco; 6 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº, Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

D. [NOMBRE Y APELLIDOS], con NIF [NIF], con domicilio en [LOCALIDAD], correo electrónico [CORREO ELECTRÓNICO], teléfono [TELÉFONO], actuando en mi propio nombre comparezco ante esa Notaría y formulo solicitud de expediente notarial por robo del cheque núm. [Nº] del que es legítimo tenedor el solicitante, librado contra el Banco [COMPLETAR], Oficina [COMPLETAR], con domicilio en [LOCALIDAD], por el aceptante D. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], la cual fundo en los siguientes:

HECHOS Y FUNDAMENTOS

El solicitante es legítimo tenedor de la letra de cambio número [NÚMERO] emitida el pasado día [FECHA], en la localidad de [COMPLETAR], cuyo librado es D. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], por importe de [IMPORTE] euros, la cual está domiciliada en la entidad bancaria [COMPLETAR], número de cuenta [COMPLETAR], con vencimiento [COMPLETAR].

La citada cambial fue emitida como consecuencia de las relaciones comerciales entre el solicitante y el librado D. [NOMBRE Y APELLIDOS], en virtud de las cuales el firmante adeudaba la cantidad de [IMPORTE] euros, emitiéndose el cheque con el número de serie [COMPLETAR], del talonario emitido por la entidad bancaria [COMPLETAR], sucursal de [COMPLETAR] (se acompaña como documentos número [Nº DE DOCUMENTO], copia del contrato de reconocimiento de deuda en cuya cláusula [COMPLETAR] consta la emisión de la letra de cambio y copia de la misma).

En el día de la fecha, cuando el solicitante se dirigía a ingresar la letra de cambio para su descuento en la sucursal de [COMPLETAR] ha sido víctima de un robo con intimidación a las [Nº] horas del día [FECHA], en el cual le ha sido sustraído, entre otros bienes y efectos, la referida cambial, tal como consta relacionado en la denuncia formulada en la Comisaría de Policía de [COMPLETAR] que acompaño como documento núm. [Nº DE DOCUMENTO].

Atendido lo anterior, dirijo a V.I. la presente solicitud por ser competente al corresponder el distrito notarial con el de lugar del pago, de conformidad a lo dispuesto en el art. 78 de la Ley del Notariado, a fin de que se suspenda el pago y se autorice a mi representado a la percepción de su importe, una vez cumplidos los trámites legales.

Por todo lo expuesto,

SOLICITO A V.I.: Tenga por presentado este escrito y demás documentos junto con las copias que se acompañan, tenga por formulada solicitud de expediente de jurisdicción voluntaria por robo de la letra de cambio descrita en el hecho primero, disponiendo la citación del librado y dar publicidad al expediente, y tras los trámites correspondientes, acuerde la suspensión de la obligación de pago y, transcurrido el plazo legal, se dicte resolución autorizando a mi representado al cobro de su crédito en la fecha de vencimiento.

En(lugar, fecha y firma del solicitante)

========================================================================
