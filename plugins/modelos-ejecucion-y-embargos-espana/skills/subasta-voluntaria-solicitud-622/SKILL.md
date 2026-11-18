---
name: subasta-voluntaria-solicitud-622
description: "Redacta el escrito «Subasta voluntaria: solicitud» (formulario 622 de ejecución civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Subasta voluntaria: solicitud

> Formulario 0622 del plugin **Ejecución civil** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] LUGAR
- [ ] FECHA
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…edido por el Registro de la Propiedad de»; «…samente el derecho de aprobar la subasta»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 109.1 LJV
- arts. 108 a 111 LJV
- art. 109.2 LJV
- Ley 15/2015

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

### Formulario 0622 · Subasta voluntaria: solicitud

- Año del modelo: 2016
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; restos de formato retirados; notas del formulario agrupadas al final (1); 13 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito por el que se solicita al Letrado de la Administración de Justicia la celebración de subasta voluntaria judicial de la finca descrita.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], número [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO (1):

Que al amparo de los arts. 108 y siguientes de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), solicito se celebre subasta voluntaria judicial de la finca que a continuación se describe:

Fundamento la solicitud en los siguientes:

Hechos y consideraciones jurídicas

1.ª) Que justifico la capacidad legal para contratar con el certificado de nacimiento que acredita mi mayoría de edad (documento número [Nº DE DOCUMENTO]).

2.ª) Que asimismo, puedo disponer de la finca por medio de la subasta, conforme resulta del certificado de dominio y cargas expedido por el Registro de la Propiedad de [COMPLETAR], en el que consta inscrita la plena propiedad sobre la referida finca (documento número [Nº DE DOCUMENTO]).

3.ª) Que en cumplimiento de lo dispuesto en el art. 110.1.c) de dicha Ley, se acompaña con esta solicitud el pliego de condiciones con arreglo a las cuales ha de celebrarse la subasta (documento número [Nº DE DOCUMENTO]).

4.ª) Que es competente la Sección Civil del Tribunal de Instancia al que me dirijo conforme al art. 109.1 LJV, al encontrarse en su partido judicial la finca descrita.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL:

Que presentado este escrito con los documentos que se acompañan, se sirva por el Letrado de la Administración de Justicia acceder a la celebración de la subasta con arreglo al pliego de condiciones que se acompaña, ordenando lo conducente para su práctica; haciendo constar que el solicitante se reserva expresamente el derecho de aprobar la subasta [COMPLETAR]; y terminado el expediente, con desglose y devolución a esta parte de los documentos acompañados.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma del solicitante

NOTAS DEL FORMULARIO

(1) La Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria atribuye de forma concurrente la tramitación y resolución de las subastas voluntarias a los Letrados de la Administración de Justicia (arts. 108 a 111 LJV) y a los Notarios (arts. 72 a 77 LN reformada por LJV).

En el caso de los expedientes que se residencian en sede judicial, la competencia objetiva corresponde a los Letrados de la Administración de Justicia de los Tribunales de Instancia.

La competencia territorial se determina, en el caso de bienes mueble, por el domicilio del titular de los bienes, y si fueran varios titulares, el correspondiente a cualquiera de ellos; y en caso de bienes inmuebles por el lugar donde éstos radiquen.

En las subastas voluntarias judiciales no es preceptiva la intervención de abogado ni procurador (art. 109.2 LJV). En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente.

El solicitante de la celebración de subasta judicial ha de acreditar la capacidad legal para la celebración del contrato que se propone realizar, y que puede disponer del bien que pretende que sea subastado. Debe aportarse, igualmente, el pliego de condiciones particulares a las que se ha de someter la subasta, con tasación de bienes y derechos.

La capacidad legal para realizar la subasta no se refiere únicamente a la capacidad de obrar, sino a la capacidad jurídica que permite al solicitante situarse en la posición de vendedor, es decir, la titularidad del derecho que pretende transmitir por pública subasta.

La tramitación y su publicidad se efectúan electrónicamente a través del portal de subastas del BOE, sometiéndose a la regulación de la LEC en todo lo no previsto en el pliego de condiciones antes indicado.

El remate se aprueba por decreto del Letrado de la Administración de Justicia a favor del único o mejor postor, siempre que se cubra el tipo mínimo fijado por el solicitante o no se hubiese reservado expresamente el derecho de aprobarla, en cuyo caso se le da vista del expediente por 3 días para alegaciones, lo que se hace también cuando algún licitador ofrezca aceptar el remate con modificación de condiciones. En defecto de licitadores, se sobresee el expediente.

========================================================================
