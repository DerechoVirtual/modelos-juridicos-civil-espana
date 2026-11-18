---
name: inicio-expediente-valores-mobiliarios-695
description: "Redacta el escrito «Inicio de expediente de valores mobiliarios» (formulario 695 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Inicio de expediente de valores mobiliarios

> Formulario 0695 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] LOCALIDAD (4 veces)
- [ ] CALLE (3 veces)
- [ ] NÚMERO (3 veces)
- [ ] FECHA (5 veces)
- [ ] IMPORTE
- [ ] LUGAR
- [ ] Otros 27 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… Hechos y consideraciones jurídicas: 1.ª»; «…) Mi mandante es propietario de»; «…ercado de renta fija, en su modalidad de»; «…, emitidos por la entidad emisora»; «… Los valores disponen de número de serie»; «…, y se encuentran numerados del»; «…al»; «…ado específico otorgado por sui padre D.»; «…, quien falleció el»; «…ban depositados en la entidad financiera»; «…SA. 2.ª»; «…tulos no han podido ser recuperados. 3.ª»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 132 Ley 15/2015
- art. 134.3 LJV
- art. 133.2 LJV
- art. 135.6 LJV
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

### Formulario 0695 · Inicio de expediente de valores mobiliarios

- Año del modelo: 2015
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 46 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Expediente en solicitud de prohibición de negociar o transmitir valores mobiliarios y de suspensión del pago de capital, intereses o dividendos.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, como mejor proceda en derecho comparezco y DIGO: (1)

Que por medio del presente escrito, y de conformidad con el art. 132 Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud de prohibición de negociar o transmitir valores mobiliarios y de suspensión del pago de capital, intereses o dividendos. Todo ello, en base a los siguientes

Hechos y consideraciones jurídicas:

1.ª [COMPLETAR])

Mi mandante es propietario de [COMPLETAR] valores admitidos a cotización oficial en el mercado de renta fija, en su modalidad de [COMPLETAR], emitidos por la entidad emisora [COMPLETAR], con domicilio social en [LOCALIDAD], calle [CALLE], nº [NÚMERO]. Los valores disponen de número de serie [COMPLETAR], y se encuentran numerados del [COMPLETAR] al [COMPLETAR]. Fueron adquiridos mediante escritura de adjudicación de herencia de fecha [FECHA], tras legado específico otorgado por sui padre D. [COMPLETAR], quien falleció el [COMPLETAR]. Suponen un valor global de [IMPORTE] euros, y se encontraban depositados en la entidad financiera [COMPLETAR] SA.

2.ª [COMPLETAR])

El pasado [FECHA], la sucursal de la citada entidad sita en [LOCALIDAD], calle [CALLE], nº [NÚMERO] fue objeto de robo, denunciado ante el Cuerpo Nacional de Policía, y como consecuencia del cual se sustrajeron diversos títulos de clientes de aquella, entre ellos los indicados que eran de propiedad de mi representado en su totalidad. Hasta la fecha las investigaciones policiales no han dado sus frutos, y los títulos no han podido ser recuperados.

3.ª [COMPLETAR])

El pasado [FECHA] tal hecho se denunció ante la Sociedad Rectora del Mercado Oficial de Renta Fija, con solicitud de prohibición de la negociación o transmisión de los valores indicados y el pago de capital, intereses o dividendos. Lo que se materializó mediante acuerdo de fecha [FECHA], que, además, comunicaba tal decisión a las restantes sociedades rectoras, con publicación en el tablón de anuncios, en el Boletín Oficial del Estado, y en un periódico de gran circulación en la Comunidad Autónoma de [LOCALIDAD].

4.ª [COMPLETAR])

Que cumpliendo con lo dispuesto en el art. 134.3 LJV, y dentro del plazo legal de nueve días se acude al procedimiento previsto en los arts. 132 y ss. LJV, a fin de mantener la interdicción acordada, y que permite llevar a la práctica el derecho previsto en el art. 548 del Código de Comercio. En este sentido, mi mandante se encuentra legitimado para la solicitud que se plantea, al ser el legítimo propietario de los valores mobiliarios indicados, en virtud de lo dispuesto en el art. 133.2 LJV. Asimismo, procederá el anuncio del expediente en el Boletín Oficial del Estado, en un periódico de gran circulación en la Comunidad de [COMPLETAR] y la convocatoria de una comparecencia con citación de los interesados. Finalmente, y dado que los valores mobiliarios en cuestión ofrecen el derecho de asistencia y de voto en las juntas generales y especiales de la entidad emisora, se solicita, al amparo del art. 135.6 LJV, que se nombre un administrador para el ejercicio de los derechos referidos, y, en su caso, para la eventual impugnación de acuerdos sociales de la misma.

5.ª [COMPLETAR])

Que es competente la Sección de lo Mercantil del Tribunal de Instancia al que me dirijo conforme al artículo 133.1 LJV, al encontrarse en su partido judicial el domicilio de la entidad emisora de los valores sustraídos.

6.ª [COMPLETAR])

Se acompañan a este escrito copia del atestado elaborado por el Cuerpo Nacional de Policía, copia de la escritura pública de adjudicación de herencia, copia de la denuncia planteada ante la Sociedad Rectora del Mercado de Renta Fija, copia del acuerdo adoptado por la misma, certificación expedida por la entidad emisora [COMPLETAR], y por la entidad depositaria [COMPLETAR] SA.

Por todo lo expuesto, al amparo de los arts. 132 y ss. LJV, y del art. 548 del Código de Comercio,

SUPLICO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria; previa publicación en el Boletín Oficial del Estado y en un periódico de gran circulación en la Comunidad de [COMPLETAR], y previa convocatoria de comparecencia ante el Letrado de la Administración de Justicia prevista en el art. 135 LJV, con citación de la entidad [COMPLETAR] SA, y de quien se estime oportuno, se dicte decreto:

1.- Manteniendo la prohibición de negociación o transmisión de los [COMPLETAR] valores admitidos a cotización oficial en el mercado de renta fija, en su modalidad de [COMPLETAR], emitidos por la entidad emisora [COMPLETAR], con domicilio social en [LOCALIDAD], calle [CALLE], nº [NÚMERO], con número de serie [COMPLETAR], y numerados del [COMPLETAR] al [COMPLETAR]; así como el pago de capital, intereses o dividendos
2.- Se nombre administrador para el ejercicio de los derechos derecho de asistencia y de voto en las juntas generales y especiales de la entidad emisora [COMPLETAR] SA, y, en su caso, para la eventual impugnación de acuerdos sociales de la misma.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art. 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En todo caso, aun cuando no sea necesario, las partes que lo deseen podrán actuar asistidas o representadas por Abogado y Procurador, respectivamente. En el supuesto específico del presente escrito, el art. 133.3 LJV establece como preceptiva la intervención de Abogado y Procurador para la solicitud en análisis.

========================================================================
