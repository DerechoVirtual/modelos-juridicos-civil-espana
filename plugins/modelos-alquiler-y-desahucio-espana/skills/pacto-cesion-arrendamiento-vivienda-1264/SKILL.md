---
name: pacto-cesion-arrendamiento-vivienda-1264
description: "Redacta el escrito «Pacto de cesión del arrendamiento de vivienda» (formulario 1264 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pacto de cesión del arrendamiento de vivienda

> Formulario 1264 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS (10 veces)
- [ ] LOCALIDAD (3 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] FECHA (2 veces)
- [ ] DNI/NIE
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, C/ [CALLE], n.º [NÚMERO] piso»; «…contrato de arrendamiento de la vivienda»; «…ios comunes como gas, agua, electricidad»; «…opietario e inquilino en cada uno de los»

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

### Formulario 1264 · Pacto de cesión del arrendamiento de vivienda

- Año del modelo: 2013
- Revisión 17-11-2026: 24 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [DÍA] de [MES] de [AÑO].

MANIFIESTA

Que D./Dña. [NOMBRE Y APELLIDOS] es propietario de la vivienda sita en [LOCALIDAD], C/ [CALLE], n.º [NÚMERO] piso [COMPLETAR]

Que D./Dña. [NOMBRE Y APELLIDOS] es inquilino de tal inmueble en virtud de contrato de arrendamiento suscrito entre ambos en fecha [FECHA], y que de tal documento tiene cada una de las partes una copia.

Que el inquilino ha puesto en conocimiento del propietario su intención de ceder el contrato de arrendamiento citado, cuya copia simple se une a este documento como anexo n.º 1, a D./Dña. [NOMBRE Y APELLIDOS], con domicilio en [LOCALIDAD], C/ [CALLE], n.º [NÚMERO] y DNI n.º [DNI/NIE], por lo que solicita consentimiento expreso para realizar tal negocio jurídico.

Que ambos se reconocen mutuamente la capacidad necesaria para otorgar por el propietario y admitir por el inquilino, la presente autorización para la cesión del contrato de arrendamiento con arreglo a las siguientes

CLÁUSULAS

Que mediante el presente documento D./Dña. [NOMBRE Y APELLIDOS], declara conocer la indentidad del cesionario, las condiciones de la cesión y sus derechos y obligaciones futuras respecto a la subrogación del cesionario en la posición del cedente en el contrato de arrendamiento de la vivienda [COMPLETAR] de fecha [FECHA], y que autoriza expresamente a D./Dña. [NOMBRE Y APELLIDOS] a firmar el contrato de cesión con D./Dña. [NOMBRE Y APELLIDOS]

Que D./Dña. [NOMBRE Y APELLIDOS] se compromete a no alterar las condiciones del arrendamiento pactado, a entregar una copia al cesionario del contrato de arrendamiento y al propietario otra copia del contrato de cesión.

Igualmente el cedente se obliga a realizar los pagos oportunos de todos los servicios comunes como gas, agua, electricidad [COMPLETAR], de que se haya servido hasta la fecha de abandono de la vivienda, y al pago de las rentas hasta esa fecha.

El cesionario se subrogará en la fianza entregada por D./Dña. [NOMBRE Y APELLIDOS], sin que, en consecuencia, nada tenga que reclamar por este concepto.

Y para que sirva de prueba de conformidad y aceptación del contrato de cesión del contrato de arrendamiento de la vivienda sita en [LOCALIDAD], lo firman propietario e inquilino en cada uno de los [COMPLETAR] folios de los tres ejemplares que se otorgan mutuamente y para el cesionario, en el lugar y fecha del encabezamiento.

Fdo.: D./Dña. [NOMBRE Y APELLIDOS] Fdo.: D./Dña. [NOMBRE Y APELLIDOS]

========================================================================
