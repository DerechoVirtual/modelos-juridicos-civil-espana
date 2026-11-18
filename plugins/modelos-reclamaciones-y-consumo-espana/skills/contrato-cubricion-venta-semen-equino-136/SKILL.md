---
name: contrato-cubricion-venta-semen-equino-136
description: "Redacta el escrito «Contrato de cubrición o venta de semen equino» (formulario 136 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contrato de cubrición o venta de semen equino

> Formulario 0136 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] PROVINCIA (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] NIF (2 veces)
- [ ] FECHA (2 veces)
- [ ] TELÉFONO (2 veces)
- [ ] CORREO ELECTRÓNICO (2 veces)
- [ ] IMPORTE
- [ ] Otros 23 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…En la localidad/ciudad de»; «…, a»; «…, mayor de edad, vecino/a de»; «… con domicilio en la localidad/ciudad de»; «…, mayor de edad, vecino/a de»; «… con domicilio en la localidad/ciudad de»; «…provisto/a del N.I.F»; «…en nombre y representación de la entidad»; «…, CIF [NIF], domiciliada en»; «…y constituida en»; «…ante el Notario de»; «…e inscrita en el Registro Mercantil de»; …

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

### Formulario 0136 · Contrato de cubrición o venta de semen equino

- Año del modelo: 2021
- Revisión 17-11-2026: 40 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En la localidad/ciudad de [COMPLETAR], a [COMPLETAR]

REUNIDOS

De una parte D./Dª [NOMBRE Y APELLIDOS], mayor de edad, vecino/a de [COMPLETAR], con domicilio en la localidad/ciudad de [COMPLETAR], provincia de [PROVINCIA], provisto/a del N.I.F. número [NÚMERO].

Y de otra parte D./Dª [NOMBRE Y APELLIDOS], mayor de edad, vecino/a de [COMPLETAR], con domicilio en la localidad/ciudad de [COMPLETAR], provincia de [PROVINCIA] provisto/a del N.I.F [COMPLETAR].

INTERVIENEN

D./Dª [NOMBRE Y APELLIDOS], interviene en nombre y representación de la entidad [COMPLETAR], CIF [NIF], domiciliada en [COMPLETAR] y constituida en [COMPLETAR] ante el Notario de [COMPLETAR] D. [NOMBRE Y APELLIDOS], en fecha [FECHA] e inscrita en el Registro Mercantil de [COMPLETAR] inscripción [COMPLETAR]. A efectos de comunicaciones se designa los números de teléfono [TELÉFONO] y la dirección de correo electrónico [CORREO ELECTRÓNICO] (en adelante LA VENDEDORA).

D./Dª [NOMBRE Y APELLIDOS], interviene en nombre y representación de la entidad [COMPLETAR], CIF [NIF], domiciliada en [COMPLETAR] y constituida en [COMPLETAR] ante el Notario de [COMPLETAR] D. [NOMBRE Y APELLIDOS], en fecha [FECHA] e inscrita en el Registro Mercantil de [COMPLETAR] inscripción [COMPLETAR]. A efectos de comunicaciones se designa los números de teléfono [TELÉFONO] y la dirección de correo electrónico [CORREO ELECTRÓNICO] (en adelante LA COMPRADORA).

MANIFIESTAN

Que intervienen en la indicada representación, se reconocen mutua y plena capacidad legal de obrar y de obligarse para este acto, otorgando de forma libre y espontánea y a su tenor el presente CONTRATO DE CUBRICIÓN O COMPRAVENTA DE SEMEN DE CABALLO, asumiendo la responsabilidad que corresponda en función de la veracidad de sus manifestaciones, y, de mutuo acuerdo,

EXPONEN

PRIMERO - Que la VENDEDORA es titular del semental llamado [COMPLETAR], cuya raza, edad y demás características constan en la tarjeta de identificación que se adjunta como anexo número 1 de este contrato, e inscrito como reproductor en el Registro [COMPLETAR].

SEGUNDO.- Que la COMPRADORA está interesada en la adquisición de semen del citado semental para la cubrición de la yegua de su titularidad llamada [COMPLETAR], según consta en la tarjeta de identificación que se adjunta como anexo número 2 de este contrato.

TERCERO.- Y estando interesados en formalizar la compraventa de semen del citado semental para la cubrición de la yegua titularidad de la COMPRADORA, la convienen de acuerdo con las siguientes

CLÁUSULAS

PRIMERA.- La VENDEDORA vende [COMPLETAR] dosis de semen fresco del semental de su titularidad, descrito en el expositivo, para la cubrición mediante inseminación artificial de la yegua titularidad de la COMPRADORA, expresada en el expositivo, que lo adquiere a estos fines.

La COMPRADORA deberá realizar la petición de envío de semen, telefónicamente o por correo electrónico, con al menos 48 horas de antelación a la fecha probable de inseminación.

Caso de ser necesarias dosis de semen adicionales podrán encargarse por la COMPRADORA con la misma antelación, comprometiéndose la VENDEDORA a entregarlas en dicho plazo.

SEGUNDA.- El precio de la cubrición es de [IMPORTE] euros, que serán abonados en la siguiente forma:

-Un 50% a la firma de este contrato, manifestando ambas partes que dicha cantidad ha sido abonada en este acto.

-El 50% restante al momento en que se certifique la preñez de la yegua, el cual se realizará mediante transferencia bancaria a la cuenta número [NÚMERO] titularidad de la VENDEDORA.

Las dosis de semen adicionales tendrán un precio de … euros, que será abonado al momento en que se certifique la preñez de la yegua, mediante transferencia a la cuenta bancaria expresada.

El precio incluye los gastos de extracción, envasado especial y envío a la COMPRADORA.

TERCERA.- La VENDEDORA se obliga la entrega del semen en el plazo estipulado, encargándose de acondicionarlo para el transporte, mediante envase que cumpla toda la normativa aplicable, y haciéndose cargo de los gastos de envío que se incluyen en el precio.

CUARTA.- La COMPRADORA se responsabiliza del manejo del semen recibido y de la inseminación de la yegua. Una vez se confirme la preñez de la yegua, se remitirá certificado veterinario a la VENDEDORA, quien emitirá certificado de cubrición una vez abonado el total pago del precio. La COMPRADORA se responsabiliza de los trámites necesarios para la inscripción del potro.

QUINTA.- La VENDEDORA no garantiza que la yegua quede preñada. En caso de preñez, se garantiza una cría con una vida de veinticuatro horas después de nacer y sin enfermedad congénita. En caso de que muriera antes de este periodo o tuviera alguna enfermedad congénita, la VENDEDORA se obliga a devolver el 50% del precio satisfecho por la cubrición y dosis adicionales en su caso. Estas circunstancias deben estar certificadas por veterinario.

SEXTA.- La peticiones que se efectúen entre las partes relativas a la ejecución del contrato se harán con la agilidad necesaria en los teléfonos o correos electrónicos expresados en el encabezamiento de este contrato, o bien por escrito en los respectivos domicilios indicados en el citado encabezamiento. Cualquier cambio de teléfono, dirección de correo o domicilio de una de las partes deberá ser notificado a la otra de forma inmediata y por un medio que garantice la recepción del mensaje.

En prueba de conformidad, una vez leído el contrato y sus anexos, que forma parte integrante e inseparable del mismo, ambas partes firman el presente documento, por duplicado y aun sólo efecto, en el lugar y fecha indicados en el encabezamiento.

LA VENDEDORA LA COMPRADORA

Fdo. Fdo.

Fdo. Fdo.
