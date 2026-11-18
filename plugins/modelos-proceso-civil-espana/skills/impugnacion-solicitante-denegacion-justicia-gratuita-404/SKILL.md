---
name: impugnacion-solicitante-denegacion-justicia-gratuita-404
description: "Redacta el escrito «Impugnación por el solicitante de la denegación de justicia gratuita» (formulario 404 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Impugnación por el solicitante de la denegación de justicia gratuita

> Formulario 0404 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO (2 veces)
- [ ] FECHA (7 veces)
- [ ] SEDE (3 veces)
- [ ] ACTO O RESOLUCIÓN
- [ ] IMPORTE
- [ ] LUGAR
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ISIÓN DE ASISTENCIA JURÍDICA GRATUITA DE»; «…numeración del juzgado de procedencia).]»; «…en reclamación de»; «…, nacido el»; «…, nacido el»; «…que se acompañan como documentos números»; «…y»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

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

### Formulario 0404 · Impugnación por el solicitante de la denegación de justicia gratuita

- Año del modelo: 2019
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 28 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Impugnación de la resolución de la comisión de asistencia jurídica gratuita denegatoria del derecho a la justicia gratuita.

Formulario adaptado a la reforma procesal de la LO 1/2025.

AL SECRETARIO DE LA COMISIÓN DE ASISTENCIA JURÍDICA GRATUITA DE [COMPLETAR]

D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD], calle [CALLE], provisto de D.N.I. n.º [NÚMERO], cuyas circunstancias personales constan en el expediente n.º [NÚMERO] que obra en esa Comisión, ante V.I. comparezco y, como mejor proceda en derecho, DIGO:

Que el pasado día [FECHA] se me ha notificado resolución de fecha [FECHA] por la que se deniega a quien suscribe el reconocimiento del derecho a la asistencia jurídica gratuita, por lo que, no estando conforme con dicha resolución, al amparo de lo dispuesto en el art. 20 de la Ley de Asistencia Jurídica Gratuita (LAJG), mediante el presente escrito deduzco en tiempo y forma IMPUGNACIÓN de la resolución para ante el Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], la cual baso en los siguientes

MOTIVOS

PRIMERO

Tal como consta en el expediente arriba referenciado, el que suscribe pretende interponer demanda contra [ACTO O RESOLUCIÓN] en reclamación de [COMPLETAR] ante el Tribunal de Instancia de [SEDE], habiendo deducido solicitud en demanda del reconocimiento de asistencia jurídica gratuita en fecha [FECHA], solicitando las prestaciones de defensa y representación gratuitas por abogado y procurador en el procedimiento judicial, por ser preceptiva su intervención, así como exención del pago de depósitos necesarios para la interposición de recursos.

Dicha solicitud fue desestimada por la resolución de la Comisión de fecha [FECHA] que ahora se impugna.

Dicha resolución me fue notificada el pasado día [FECHA], interponiendo la presente reclamación en plazo de diez días.

SEGUNDO

La citada resolución infringe lo dispuesto en el art. 3 LAJG, por cuanto que deniega el reconocimiento basándose en la percepción de ingresos superiores en dos veces y media el indicador público de renta de efectos múltiples, a cuyo efecto computa de forma errónea los ingresos correspondientes a la unidad familiar, por incluir los de mis hijos mayores de edad Don/Doña [NOMBRE Y APELLIDOS] y Don/Doña [NOMBRE Y APELLIDOS].

Por tanto, la impugnación se basa en que se han incluido dentro de la unidad familiar personas que no la constituyen, según la delimitación que realiza el art. 3.2 LAJG en relación con el art. 82 LIRPF, que únicamente incluye a los hijos menores de edad no emancipados.

Así, se incluyen en el cómputo los ingresos de mis dos hijos mayores Don/Doña [NOMBRE Y APELLIDOS], nacido el [COMPLETAR], y Don/Doña [NOMBRE Y APELLIDOS], nacido el [COMPLETAR], ambos mayores de edad con anterioridad a presentarse la solicitud, como se demuestra con sendas certificaciones registrales que se acompañan como documentos números [COMPLETAR] y [COMPLETAR].

Por tanto, los ingresos de mis hijos mayores de edad computados en la resolución impugnada deben excluirse por tratarse de personas que no forman parte del concepto legal de unidad familiar definido en el art. 3.2 LAJG.

TERCERO

La exclusión de los citados hijos de la unidad familiar supone que los únicos recursos e ingresos económicos computables son los del propio solicitante y de su cónyuge, que la propia Comisión fija en un total de [IMPORTE] euros anuales, importe inferior a dos veces y media al indicador público de renta de efectos múltiples, lo cual no impide el reconocimiento del derecho, solicitado a los efectos de representación y defensa y exención del pago de depósitos, puesto que mis ingresos son muy inferiores al máximo legal, y habida cuenta que carezco de bienes y de que están a mi cargo un hijo menor de edad, así como la madre de mi cónyuge, quien no percibe ningún ingreso, tal como se acreditó oportunamente con la documentación acompañada.

Por todo ello, solicito que se revoque la resolución y se me reconozca el derecho en los términos solicitados.

Por lo expuesto,

SOLICITO DE V.I.:

que tenga por presentado en tiempo y forma el presente escrito, por impugnado el Acuerdo de esa Comisión de Asistencia Jurídica Gratuita de fecha [FECHA] y proceda a dar traslado del mismo AL TRIBUNAL DE INSTANCIA DE [SEDE] que está conociendo del proceso (o, en su caso, al Tribunal de Instancia de esta ciudad, dado que el procedimiento no se ha iniciado), al cual SUPLICO estime la impugnación y reconozca el derecho del solicitante a la asistencia jurídica gratuita en las prestaciones establecidas en los apartados 3 y 5 del art. 6 LAJG.

Es justicia de hacerse en [LUGAR], a [FECHA].

Firma del Solicitante

========================================================================
