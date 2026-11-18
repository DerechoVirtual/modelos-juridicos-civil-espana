---
name: inicio-expediente-titulo-credito-letra-cambio-711
description: "Redacta el escrito «Inicio de expediente de título de crédito: letra de cambio» (formulario 711 de monitorio y cambiario, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Inicio de expediente de título de crédito: letra de cambio

> Formulario 0711 del plugin **Monitorio y cambiario** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] IMPORTE (5 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] FECHA (2 veces)
- [ ] LUGAR
- [ ] Otros 14 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… Hechos y consideraciones jurídicas: 1.ª»; «… en las letras de cambio numeradas como,»; «…, y»; «… como aceptante de las mismas la entidad»; «…ban depositadas en la entidad financiera»; «…SA. 2.ª»; «…tulos no han podido ser recuperados. 3.ª»; «…cia con citación de los interesados. 4.ª»; «…micilio social del aceptante, la entidad»; «…SL. 5.ª»; «…, certificación de la entidad financiera»; «…art. 135 LJV, con citación de la entidad»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 132 de la Ley 15/2015
- art. 133.2 LJV
- artículo 133.1 LJV
- art. 135 LJV
- art. 3.2 LJV
- art. 133.3 LJV

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

### Formulario 0711 · Inicio de expediente de título de crédito: letra de cambio

- Año del modelo: 2015
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 32 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Expediente en solicitud de prohibición de transmisión y pago de títulos de crédito sustraídos

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, como mejor proceda en derecho comparezco y DIGO: (1)

Que por medio del presente escrito, y de conformidad con el art. 132 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud de prohibición de transmisión y pago de títulos de crédito sustraídos. Todo ello, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª [COMPLETAR])

Mi mandante era poseedor de cuatro títulos de crédito consistentes en las letras de cambio numeradas como, [COMPLETAR], y [COMPLETAR]; que le daba derecho a cobrar las cantidades de [IMPORTE] euros, [IMPORTE] euros [IMPORTE], [IMPORTE] euros, y [IMPORTE] euros respectivamente. Las letras de cambio habían sido adquiridas mediante endoso de D./Dña. [NOMBRE Y APELLIDOS], y en ellas figuraba como aceptante de las mismas la entidad [COMPLETAR] SL con domicilio social en [LOCALIDAD], calle [CALLE], nº [NÚMERO]. Las mismas se encontraban depositadas en la entidad financiera [COMPLETAR] SA.

2.ª [COMPLETAR])

El pasado [FECHA], la sucursal de la citada entidad sita en [LOCALIDAD], calle [CALLE], nº [NÚMERO], fue objeto de robo, denunciado ante el Cuerpo Nacional de Policía, y como consecuencia del cual se sustrajeron diversos títulos de clientes de aquélla, entre ellos las cuatro letras de cambio de mi representado. Hasta la fecha las investigaciones policiales no han dado sus frutos, y los títulos no han podido ser recuperados.

3.ª [COMPLETAR])

Por ello, es interés de mi cliente que se prohíba que las letras de cambio sustraídas puedan ser transmitidas, o se pueda pagar su importe a su eventual tenedor, y que se le dé a tal hecho la publicidad legalmente procedente. Se acude, en consecuencia, al procedimiento previsto en los arts. 132 y ss. LJV, que permite llevar a la práctica el derecho previsto en el art. 548 del Código de Comercio. En este sentido, mi mandante se encuentra legitimado para la solicitud que se plantea, al haber sido el legítimo tenedor de los títulos de crédito indicados, en virtud de lo dispuesto en el art. 133.2 LJV. Asimismo, procederá el anuncio del expediente en el Boletín Oficial del Estado, en un periódico de gran circulación en la Comunidad de Madrid, y la convocatoria de una comparecencia con citación de los interesados.

4.ª [COMPLETAR])

Que es competente la Sección de lo Mercantil del Tribunal de Instancia al que me dirijo conforme al artículo 133.1 LJV, al encontrarse en su partido judicial el lugar de pago previsto en las letras de cambio, el domicilio social del aceptante, la entidad [COMPLETAR] SL.

5.ª [COMPLETAR])

Se acompañan a esta solicitud copia del atestado policial, certificación de la entidad financiera [COMPLETAR] SA donde las letras de cambio se encontraban depositadas, y declaración jurada del endosante D./Dña. [NOMBRE Y APELLIDOS].

Por todo lo expuesto, al amparo de los arts. 132 y ss. LJV, y del art. 548 del Código de Comercio,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria; previa publicación en el Boletín Oficial del Estado y en un periódico de gran circulación en la Comunidad de Madrid, y previa convocatoria de comparecencia ante el Letrado de la Administración de Justicia prevista en el art. 135 LJV, con citación de la entidad [COMPLETAR] SL, y de quien se estime oportuno, se dicte decreto acordando prohibir la transmisión de letras de cambio numeradas como, [COMPLETAR], y [COMPLETAR] y el pago de las sumas fijadas en las mismas.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito, el art. 133.3 LJV establece como preceptiva la intervención de Abogado y Procurador para la solicitud en análisis.

========================================================================
