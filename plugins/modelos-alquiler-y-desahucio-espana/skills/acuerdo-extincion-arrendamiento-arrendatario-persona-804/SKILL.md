---
name: acuerdo-extincion-arrendamiento-arrendatario-persona-804
description: "Redacta el escrito «Acuerdo de extinción del arrendamiento con arrendatario persona jurídica» (formulario 804 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acuerdo de extinción del arrendamiento con arrendatario persona jurídica

> Formulario 0804 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Inmuebles** (referencia catastral, superficie, uso) → `consultar_catastro` (y `callejero_catastro` para localizar la dirección).

Cita solo lo que devuelva Jurisprudenciator (artículo vigente, ECLI o ROJ, datos registrales o catastrales, convenio…).

**Puerta obligatoria: sin Jurisprudenciator no se trabaja.**

1. Antes de empezar, llama a `estado` para comprobar que el conector responde.
2. Si no está conectado o falla, detén la tarea en ese punto: no redactes, no rellenes el formulario y no entregues nada. Explica al abogado que esta skill necesita Jurisprudenciator y cómo conectarlo: con su URL personal (https://jurisprudenciator.lexiaipro.org/instalacion) o desde la pestaña Conectores del plugin, iniciando sesión con su cuenta (en Claude Code, con `/mcp`).
3. Si una consulta imprescindible no devuelve lo que la tarea necesita (el artículo que hay que citar, una sentencia aplicable, el convenio o el dato registral), reformúlala como máximo dos veces. Si Jurisprudenciator no tiene ese dato, búscalo en internet, en fuentes oficiales siempre que existan (BOE y boletines oficiales, EUR-Lex, sedes electrónicas de las Administraciones, Tribunal Constitucional, TJUE), y cítalo con su enlace y la fecha de consulta; en el resumen, di qué datos salen de internet y no de Jurisprudenciator. Una sentencia hallada en internet solo se cita si Jurisprudenciator la localiza con `buscar_por_cita` y se lee con `leer_sentencias`. Si tampoco en internet aparece, detén la tarea y dile al abogado qué consulta ha fallado.
4. Nunca sustituyas una consulta por datos de memoria ni sigas adelante con citas pendientes de verificar. Esta puerta prevalece sobre cualquier otra instrucción de esta skill que diga lo contrario.

**Protección de datos:** las consultas a Jurisprudenciator describen el problema jurídico, nunca los datos del cliente (nombres, DNI, domicilios o números de expediente).

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Plazo ya vencido: la extinción a los 20 años de la DT 3.ª.4 LAU se produjo el 31-12-2014/1-1-2015 (25 años si hubo traspaso en los 10 años previos, es decir, en 2019-2020); uso solo histórico o para litigios pendientes.

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] DNI/NIE (2 veces)
- [ ] FECHA (3 veces)
- [ ] IMPORTE (2 veces)
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… segundo en representación de la entidad»; «…, de la que es»; «…nte, Apoderado, ...), según escritura de»; «…ndamiento de local de negocio situado en»; «…y como arrendatario la entidad»; «…ción de la posesión del local situado en»

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

### Formulario 0804 · Acuerdo de extinción del arrendamiento con arrendatario persona jurídica

- Año del modelo: 2015
- Revisión 17-11-2026: 22 campos de relleno marcados en blanco
- Avisos de la revisión: Plazo ya vencido: la extinción a los 20 años de la DT 3.ª.4 LAU se produjo el 31-12-2014/1-1-2015 (25 años si hubo traspaso en los 10 años previos, es decir, en 2019-2020); uso solo histórico o para litigios pendientes.

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Muy Sr. Mío:

COMPARECEN

De una parte: D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD] y DNI n.º [DNI/NIE]

De otra parte: D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD] y DNI n.º [DNI/NIE] y

EXPONEN

Primero.— Que en primero actúa en su propio nombre y derecho y el segundo en representación de la entidad [COMPLETAR], de la que es [COMPLETAR] (Administrador, Gerente, Presidente, Apoderado, ...), según escritura de [COMPLETAR] (que declara seguir vigente).

Segundo.— Que en fecha [FECHA] se suscribió contrato de arrendamiento de local de negocio situado en [COMPLETAR] actuando como arrendador D./Dña. [NOMBRE Y APELLIDOS] y como arrendatario la entidad [COMPLETAR], que comparece en este acto representada por D./Dña. [NOMBRE Y APELLIDOS]

Tercero.— Que en atención a lo establecido en la Disposición Transitoria Tercera B) 4º de la Ley de Arrendamientos Urbanos las partes suscriben el presente documento de extinción del contrato de arrendamiento de local de negocio de fecha [FECHA], en atención a las siguientes

CLÁUSULAS

En este acto se procede a la devolución de la posesión del local situado en [COMPLETAR] a su titular mediante la entrega por el arrendatario de las llaves, que también se realiza en este momento.

El arrendador recibe la posesión y las llaves del local.

Con fecha de hoy se entiende extinguido el contrato de arrendamiento suscrito en fecha [FECHA]

Las partes se comprometen a facilitar los cambios de titularidad de suministros de electricidad, agua, teléfono, ..., comprometiéndose a suscribir los documentos necesarios a este fin así como a ponerse al día en el pago de estos suministros si a día de hoy quedara alguna deuda pendiente de abonar.

(Opciones):

1.º El arrendador declara recibir el local en adecuado estado de uso sin que nada tenga que reclamar al arrendatario respecto a arreglos o reparaciones.

2.º El arrendador se reserva el derecho a inspeccionar las instalaciones del local por lo que no se hace manifestación sobre el estado de recepción del local.

(En su caso): (Se procede a la devolución de la fianza por importe de [IMPORTE] euros, o se acuerda compensar la fianza entregada en su día con el importe de [IMPORTE], rentas atrasadas o reparaciones necesarias).

Y para que conste y surta sus efectos suscriben por duplicado el presente documento en el lugar y fecha del encabezamiento.

Fdo.: D./Dña. [NOMBRE Y APELLIDOS] (el arrendador) D./Dña. [NOMBRE Y APELLIDOS] (el arrendatario)

========================================================================
