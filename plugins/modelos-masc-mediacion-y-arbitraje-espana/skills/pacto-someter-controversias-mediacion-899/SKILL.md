---
name: pacto-someter-controversias-mediacion-899
description: "Redacta el escrito «Pacto para someter las controversias a mediación» (formulario 899 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Pacto para someter las controversias a mediación

> Formulario 0899 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] DNI/NIE (2 veces)
- [ ] DESCRIBIR (3 veces)
- [ ] ÓRGANO
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…a como representante legal de la entidad»; «…, con sede en»; «…y CIF de la que declara ser»; «…ón vigentes según consta en escritura de»; «…ambos comparecientes existe una relación»; «…UERDAN Primero.— La sumisión a mediación»; «… controversias que surjan en su relación»; «…en concreto a la mediación realizada por»; «… pudiera llevarse a cabo se distribuirán»

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

### Formulario 0899 · Pacto para someter las controversias a mediación

- Año del modelo: 2013
- Revisión 17-11-2026: 24 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [DÍA] de [MES] de [AÑO].

REUNIDOS

De una parte D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD] y DNI n.º [DNI/NIE]

De otra parte D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD] y DNI n.º [DNI/NIE]

EXPONEN

1.º Que (Opciones)

• D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] actúan en su propio nombre y derecho.

• D./Dña. [NOMBRE Y APELLIDOS] actúa en su propio nombre y derecho y D./Dña. [NOMBRE Y APELLIDOS] actúa como representante legal de la entidad [COMPLETAR], con sede en [COMPLETAR] y CIF de la que declara ser [COMPLETAR] (administrador, gerente, ...) con facultades de representación vigentes según consta en escritura de [COMPLETAR] de fecha

2.º Que entre ambos comparecientes existe una relación [COMPLETAR] (de comercio, de arrendamiento, de aparcería, ...) que recae sobre [DESCRIBIR]

3.º Que para resolver las controversias que puedan surgir entre ellas derivadas de la relación descrita en el apartado anterior

ACUERDAN

Primero.— La sumisión a mediación [COMPLETAR] (civil o mercantil) de las controversias que surjan en su relación [COMPLETAR], y en concreto las relativas a [DESCRIBIR]

(En su caso) Se excluyen de la sumisión a mediación las cuestiones relativas a [DESCRIBIR] (obras, tipo de cultivos, solicitud de ayudas, desahucio por cualquier causa,...) que, en caso de no poder resolverse entre las partes se someterán a la resolución judicial o administrativa que corresponda.

Segundo.— Las partes se someterán a mediación ante [ÓRGANO] (uno o varios) mediadores, (en su caso) en concreto a la mediación realizada por [COMPLETAR] (persona u órgano), con sede en

Tercero.— Desde este momento aceptan que la resolución que el acuerdo que en su día se pueda suscribir vincule a las partes comprometiéndose a cumplirlo en los términos que incluya. En el caso de incumplimiento se autorizan los comparecientes a acudir a la vía judicial para la ejecución de lo pactado.

Cuarto.— Cualquiera de las partes podrá renunciar a esta sumisión a mediación comunicándoselo a la otra de forma fehaciente y surtiendo efectos la renuncia desde la recepción de la comunicación.

Quinto.— Los costes de la mediación que pudiera llevarse a cabo se distribuirán [COMPLETAR] (Opciones):

• dividiendo su importe al cincuenta por ciento entre las partes.

• dividiendo su importe al cincuenta por ciento entre las partes, salvo que una de las partes aceptara íntegramente las pretensiones de la otra, en cuyo caso la primera asumiría íntegramente el coste.

Y para que conste y surta los efectos oportunos, suscriben los comparecientes este documento en el lugar y fecha del encabezamiento.

========================================================================
