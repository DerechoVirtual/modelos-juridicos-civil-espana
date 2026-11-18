---
name: reconvencion-danos-perjuicios-juicio-verbal-840
description: "Redacta el escrito «Reconvención de daños y perjuicios en juicio verbal» (formulario 840 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Reconvención de daños y perjuicios en juicio verbal

> Formulario 0840 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] DNI/NIE
- [ ] LOCALIDAD
- [ ] FECHA
- [ ] IMPORTE (5 veces)
- [ ] NÚMERO (4 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, (demandante principal,»; «…a la que tenía prevista la asistencia de»; «…y con el certificado de»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 438.2 de la LEC
- art. 10 de la LEC
- art. 1902 del CC
- art. 394 de la LEC

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

### Formulario 0840 · Reconvención de daños y perjuicios en juicio verbal

- Año del modelo: 2013
- Revisión 17-11-2026: 19 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (FECHA)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

OTROSI DIGO: Que según permite el art. 438 en relación con el 406 de la LEC, procedemos a formular RECONVENCIÓN frente a D./Dña. [NOMBRE Y APELLIDOS], (demandante principal, [COMPLETAR] y, en su caso, frente a D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con DNI nº [DNI/NIE] y domicilio en [LOCALIDAD], por su relación de litisconsorte con el anterior), en atención a los siguientes:

HECHOS

El actor demanda el pago del precio de una obra de arte cuando en realidad no nos encontramos ante tal, sino ante una simple copia. La venta de este objeto falsificado determinó que mi representado tuviera que suspender la exposición pública que había organizado para el día [FECHA]

Efectivamente con ocasión de la adquisición de lo que entonces se pensaba que era una obra de arte, mi representado, que es titular del establecimiento, organizó una fiesta para la que tenía prevista la asistencia de [COMPLETAR] personas, a las que había cobrado una entrada de [IMPORTE] euros. Acreditamos estos extremos con el cartel elaborado para el evento, que presentamos como doc. n.º [NÚMERO] y con el certificado de [COMPLETAR] sobre el aforo máximo del local.

Los gastos de publicidad fueron de [IMPORTE] euros tal y como aparece en la factura que adjuntamos como doc. n.º [NÚMERO]

En definitiva mi representado gastó [IMPORTE] euros en la preparación del espectáculo, y dejó de ganar [IMPORTE] euros al no poder celebrarlo. De todo ello es responsable el vendedor de la estatua, ya que el especialista D./Dña. [NOMBRE Y APELLIDOS] emitió un informe para mi representado en el que se afirma su falsedad, tal como consta en el dictamen que acompañamos con el n.º [NÚMERO] Evidentemente tras conocer este dato D./Dña. [NOMBRE Y APELLIDOS] se vio obligado a suspender el acto público previsto y a devolver el precio de las entradas. De todos estos perjuicios es responsable directo el vendedor de una obra de arte no auténtica.

(en su caso) Adjuntamos modelo 696 de liquidación de la tasa judicial como documento n.º [NÚMERO] (para cuantías superiores a 2.000 € y reconveniente persona jurídica sin justicia gratuita reconocida).

FUNDAMENTOS DE DERECHO

Jurisdicción y competencia

Serán de aplicación los preceptos citados de contrario en este apartado.

Tramitación

El art. 438.2 de la LEC permite la interposición de reconvención si por la cuantía o materia procede la utilización del cauce del juicio verbal y si existe conexión entre las pretensiones de esta demanda y las de la principal.

Legitimación

En aplicación del art. 10 de la LEC están legitimados los titulares de la relación jurídica.

Fondo del asunto

1.º Art. 1093 del CC que reconoce la existencia de obligaciones que se derivan de culpa o negligencia.

2.º El art. 1902 del CC permite reclamar la indemnización por daños y perjuicios a los que causen un perjuicio a otro interviniendo culpa o negligencia.

Costas

En aplicación del art. 394 de la LEC deberán imponerse al demandado en esta reconvención (demandante principal).

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y copia de todo ello, lo admita y, previos los trámites legales oportunos, se dicte en su día sentencia en la que desestimando la demanda principal por las razones que se alegarán en el acto de la vista, estime íntegramente las pretensiones recogidas en esta demanda reconvencional, condenando a D./ Dña. a indemnizar a mi representado con la cantidad de [IMPORTE] euros, y a que abone los intereses de esa cifra desde la interposición de la demanda y las costas del juicio.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
