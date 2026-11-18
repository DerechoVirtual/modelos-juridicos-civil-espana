---
name: contestacion-reconvencion-arbitraje-consumo-1491
description: "Redacta el escrito «Contestación a la reconvención en arbitraje de consumo» (formulario 1491 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestación a la reconvención en arbitraje de consumo

> Formulario 1491 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS
- [ ] Nº
- [ ] DOMICILIO A EFECTOS DE NOTIFICACIONES
- [ ] CORREO ELECTRÓNICO
- [ ] FECHA
- [ ] IMPORTE
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…e Arbitral Firmas A LA CORTE ARBITRAL DE»; «…a Secretaría de la Corte de Arbitraje de»; «…econvención formulada por el demandado D»; «…me dí de alta en la empresa de seguridad»; «… acreditativos, acompaño como documentos»; «…ato suscrito con la empresa de seguridad»; «… en el servicio, acompaño como documento»

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

### Formulario 1491 · Contestación a la reconvención en arbitraje de consumo

- Año del modelo: 2014
- Revisión 17-11-2026: 12 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Encabezamiento
PRIMERO
Solicitud a la Corte Arbitral
Firmas

A LA CORTE ARBITRAL DE [COMPLETAR]

D. [NOMBRE Y APELLIDOS], mayor de edad, con DNI núm. [Nº], con domicilio a efectos de notificaciones en [DOMICILIO A EFECTOS DE NOTIFICACIONES], con número de teléfono/ fax/ correo electrónico [CORREO ELECTRÓNICO], ante la Secretaría de la Corte de Arbitraje de [COMPLETAR] comparezco y como mejor proceda, DIGO;

Que en fecha [FECHA] se me ha dado traslado de la reconvención formulada por el demandado D [COMPLETAR] en solicitud de la cantidad de [IMPORTE] euros, por lo que, en el plazo concedido, mediante este escrito contesto a la reconvención, fundándome en las siguientes

PRIMERO Se niegan los hechos y fundamentos alegados por el demandado en su reconvención.

El demandado pretende el abono de los importes de un servicio que no fue prestado, puesto que había cursado oportunamente la baja en el servicio de alarma y me dí de alta en la empresa de seguridad [COMPLETAR], precisamente por las graves deficiencias en la prestación del servicio, que motiva la demanda rectora de este procedimiento, al producirse hasta cinco robos en mi empresa en el corto espacio de tiempo de dos meses.

A efectos acreditativos, acompaño como documentos [COMPLETAR] copia el contrato suscrito con la empresa de seguridad [COMPLETAR] en relación al mismo servicio, así como copia de los recibos abonados, los cuales se corresponden con el periodo que pretende percibir indebidamente la empresa reclamada.

En cuanto a la baja en el servicio, acompaño como documento [COMPLETAR] copia del correo electrónico enviado al servicio de atención del cliente de la empresa de seguridad demandante, donde se pone de manifiesto que cursé oportunamente la baja en el servicio y los hechos que lo motivaron, esto es, la comisión de cinco robos sin que se detectara en ningún momento por los servicios de la empresa de seguridad ni se diera ningún aviso a la Policía.

En virtud de lo expuesto, es de justicia y por ello

SOLICITO A LA CORTE ARBITRAL que tenga por formulada esta contestación a la reconvención y, tras los trámites legales y de conformidad a lo expuesto en este escrito, la desestime íntegramente en el laudo que ponga fin a este procedimiento, imponiendo las costas y gastos al demandante reconvencional.

Lugar y fecha

Firma del demandado reconvenido, representante y/o abogado

========================================================================
