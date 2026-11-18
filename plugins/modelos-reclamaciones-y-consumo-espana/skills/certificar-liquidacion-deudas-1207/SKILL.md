---
name: certificar-liquidacion-deudas-1207
description: "Redacta el escrito «Certificar la liquidación de deudas» (formulario 1207 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Certificar la liquidación de deudas

> Formulario 1207 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] NOMBRE Y APELLIDOS (22 veces)
- [ ] Nº (3 veces)
- [ ] DNI/NIE
- [ ] DOMICILIO A EFECTOS DE NOTIFICACIONES
- [ ] FECHA (2 veces)
- [ ] HORA
- [ ] IMPORTE (6 veces)
- [ ] ÓRGANO
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, local»; «…, local»; «…del local»; «…er a favor de Procuradores y Abogados de»; «…, local»; «…, local»; «…del local»

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

### Formulario 1207 · Certificar la liquidación de deudas

- Año del modelo: 2013
- Revisión 17-11-2026: 33 campos de relleno marcados en blanco; 12 huecos del original que se habían perdido sin marca, marcados (DNI/NIE, FECHA, HORA, IMPORTE, Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [DÍA] de [MES] de [AÑO].

D./Dña. [NOMBRE Y APELLIDOS] de la Comunidad de Propietarios de la C/ n.º [Nº], mayor de edad, con DNI n.º [DNI/NIE] y domicilio a efectos de notificaciones en [DOMICILIO A EFECTOS DE NOTIFICACIONES], certifico lo siguiente:

A la Junta de la Comunidad de Propietarios de fecha [FECHA], celebrada en a las [HORA] horas en convocatoria, asistieron los propietarios que a continuación se indican:

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], local [COMPLETAR], con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], local [COMPLETAR], con coeficiente de participación del%.

Asistieron en definitiva propietarios de los que componen el total de la Comunidad y que representaban una cuota de participación de%.

D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] estaban privados del derecho de voto por no encontrarse al corriente del pago de las cuotas, tal como constaba en la convocatoria, y por no haber procedido a abonarlas antes de la celebración de la Junta, o a consignar su importe o a reclamar judicialmente.

Los comuneros habían sido convocados debidamente a la Junta teniendo conocimiento previo del orden del día.

El punto n.º [Nº] del orden del día se refería a la siguiente cuestión: «Estudio y aprobación, en su caso, de la presentación de reclamación judicial contra los propietarios morosos D./Dña. [NOMBRE Y APELLIDOS] del piso y D./Dña. [NOMBRE Y APELLIDOS] del local [COMPLETAR], que adeudan en estos momentos y cuotas respectivamente. Aprobación en caso afirmativo de la liquidación de la deuda y autorización al Sr. Presidente para que en nombre de la Comunidad otorgue poder a favor de Procuradores y Abogados de [COMPLETAR] para la presentación de la oportuna demanda reclamando las cuotas no pagadas y los gastos que ello ocasione».

En el debate por D./Dña. [NOMBRE Y APELLIDOS] se sugirió la posibilidad de realizar un requerimiento extrajudicial previo, aceptando someter también a votación esta posibilidad.

Sometido este punto a votación con el inciso indicado el resultado fue el que a continuación se transcribe:

Votos a favor:

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], piso, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], local [COMPLETAR], con coeficiente de participación del%.

Votos en contra

D./Dña. [NOMBRE Y APELLIDOS], piso+, con coeficiente de participación del%.

D./Dña. [NOMBRE Y APELLIDOS], local [COMPLETAR], con coeficiente de participación del%.

En consecuencia, se aprueba con votos a favor que representan el % de cuotas de participación y votos en contra, que representan el % cuotas de participación el siguiente acuerdo: «Acuerdo de la Comunidad de Propietarios de la C/ n.º para reclamar a D./Dña. [NOMBRE Y APELLIDOS] del piso y a D./Dña. [NOMBRE Y APELLIDOS] del local [COMPLETAR], las cantidades que adeudan en estos momentos a la Comunidad por y cuotas impagadas por importe de [IMPORTE] euros y [IMPORTE] euros, respectivamente. En primer lugar se practicará un requerimiento extrajudicial mediante [ÓRGANO] y si en el plazo de siete días no se liquidaran las cantidades indicadas se presentará la reclamación judicialmente. En este caso se autoriza al Secretario para emitir este certificado de liquidación de las deudas y al Presidente para que en nombre de la Comunidad otorgue poder a favor de Procuradores y Abogados de para la presentación de la demanda o de la petición inicial de juicio monitorio para reclamación de las cuotas no pagadas y los gastos que ello ocasione.

En cuanto a la liquidación de estado de cuentas se concretan las deudas con los siguientes cálculos:

D./Dña. [NOMBRE Y APELLIDOS], del piso: cuotas impagadas a [IMPORTE] euros cada cuota, total [IMPORTE] euros, más los gastos de requerimiento previo, y

D./Dña. [NOMBRE Y APELLIDOS], del local n.º [Nº]: cuotas impagadas a [IMPORTE] euros cada cuota, total [IMPORTE] euros, más los gastos de requerimiento previo».

Lo expuesto es trascripción literal del acuerdo adoptado, según figura en el acta de la Junta de la Comunidad de Propietarios de fecha [FECHA], y así lo certifico yo el Secretario de la Comunidad con el visto bueno del Presidente.

Firmado:V.B. El Presidente

========================================================================
