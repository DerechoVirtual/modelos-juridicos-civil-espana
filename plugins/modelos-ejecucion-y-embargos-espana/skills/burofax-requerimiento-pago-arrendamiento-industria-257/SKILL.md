---
name: burofax-requerimiento-pago-arrendamiento-industria-257
description: "Redacta el escrito «Burofax de requerimiento de pago en arrendamiento de industria» (formulario 257 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Burofax de requerimiento de pago en arrendamiento de industria

> Formulario 0257 del plugin **Ejecución civil** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.
- **Inmuebles** (referencia catastral, superficie, uso) → `consultar_catastro` (y `callejero_catastro` para localizar la dirección).

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
- [ ] CALLE
- [ ] FECHA
- [ ] Nº (3 veces)
- [ ] IMPORTE (2 veces)
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, de»; «… en el que se desarrolla la actividad de»; «…de arrendamiento de industria firmado en»; «… de la renta se efectuará entre los días»; «…y»; «…RRENDADORA tiene suscrita con la entidad»; «…en su sucursal»; «…hasta la fecha debe las mensualidades de»; «…a»

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

### Formulario 0257 · Burofax de requerimiento de pago en arrendamiento de industria

- Año del modelo: 2020
- Revisión 17-11-2026: 14 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (IMPORTE, NOMBRE Y APELLIDOS, Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

PARTE PROPIETARIA/ARRENDADORA:

PARTE ARRENDATARIA:

Estimado Sr./Sra. [NOMBRE Y APELLIDOS]:

Le mando la presente en calidad de ARRENDADORA del local situado en la calle [CALLE], de [COMPLETAR], con una superficie de metros2, en el que se desarrolla la actividad de [COMPLETAR]; local del que usted es ARRENDATARIA, conforme al contrato de arrendamiento de industria firmado en [COMPLETAR] el pasado día [FECHA].

Según consta en el citado contrato, el pago de la renta se efectuará entre los días [COMPLETAR] y [COMPLETAR] de cada mes en la cuenta corriente núm. [Nº] que la ARRENDADORA tiene suscrita con la entidad [COMPLETAR] en su sucursal [COMPLETAR].

En caso de retraso en el pago de más de [Nº] días en cualquiera de los pagos dará derecho a la ARRENDADORA a exigir a la ARRENDATARIA un interés moratorio del % respecto de cada uno de los pagos no satisfechos puntualmente.

Si la ARRENDATARIA se retrasara en el pago de dos plazos o en el pago del último, la ARRENDADORA podrá optar entre exigir el pago de los plazos pendientes o resolver el contrato, con abono en ambos casos de las indemnizaciones que puedan corresponder.

La renta mensual pactada asciende a la cantidad de [IMPORTE] €, que debe usted ingresar en la cuenta consignada en el contrato, constatando que hasta la fecha debe las mensualidades de [COMPLETAR] a [COMPLETAR] por lo que la deuda asciende a la cantidad de [IMPORTE] €.

Le ruego que en el plazo de [Nº] días proceda a hacerlo efectivo por el medio habitual, pues en caso contrario me vería obligado a interponer las acciones judiciales oportunas.

La presente comunicación sirve como requerimiento fehaciente previo al inicio de acciones legales y surtirá los efectos previstos en el artículo 22.4, párrafo 2.º de la Ley de Enjuiciamiento Civil a los efectos de impedir la enervación de la acción de desahucio en juicio celebrado al efecto.

A la espera de sus noticias, reciba un saludo.

Sin otro particular, a la espera de sus noticias.

Lugar:

Fecha:

Fdo.:
