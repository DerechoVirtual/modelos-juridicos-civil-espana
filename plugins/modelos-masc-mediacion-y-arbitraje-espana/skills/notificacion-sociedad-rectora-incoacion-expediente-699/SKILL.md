---
name: notificacion-sociedad-rectora-incoacion-expediente-699
description: "Redacta el escrito «Notificación a la sociedad rectora de la incoación del expediente» (formulario 699 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Notificación a la sociedad rectora de la incoación del expediente

> Formulario 0699 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS
- [ ] DNI/NIE
- [ ] PROFESIÓN
- [ ] LOCALIDAD
- [ ] CALLE
- [ ] NÚMERO (3 veces)
- [ ] FECHA (5 veces)
- [ ] SEDE (3 veces)
- [ ] Nº DE EXPEDIENTE (2 veces)
- [ ] LUGAR
- [ ] Otros 15 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…a interdicción previamente acordada. 1.ª»; «… tengo el honor de dirigirme, el robo de»; «…ercado de renta fija, en su modalidad de»; «…, emitidos por la entidad emisora»; «…, con número de serie»; «…, y numerados del»; «…, y numerados del [COMPLETAR] al»; «…al [COMPLETAR], ambos inclusive. 2.ª»; «…en un periódico de gran circulación. 3.ª»; «…numeración del juzgado de procedencia).]»; «…/»; «…tancia a la propia sociedad rectora. 4.ª»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 134.4 LJV
- art. 134 de la Ley 15/2015
- art. 134.3 LJV
- art. 134.4 de LJV
- art. 134 LJV

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

### Formulario 0699 · Notificación a la sociedad rectora de la incoación del expediente

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 33 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

La denuncia puede ser presentada por los poseedores legítimos de los títulos que hubieren sido desposeídos de los mismos, así como los que hubieren sufrido su destrucción o extravío, cuando se trate de valores admitidos a negociación en alguna Bolsa u otro mercado secundario oficial. Se debe dirigir a la Sociedad Rectora del mercado secundario oficial correspondiente al domicilio de la entidad emisora para denunciar el robo, hurto, destrucción o extravío del título. El denunciante debe solicitar la iniciación del expediente de jurisdicción voluntaria de los arts. 132 y ss. LJV en el plazo máximo de 9 días a contar desde la formalización de la denuncia. La incoación del expediente debe notificarse a la Sociedad Rectora del mercado secundario oficial. En caso contrario, ésta levantará la interdicción de los valores, lo comunicará a las Sociedades Rectoras de las restantes Bolsas o mercados oficiales y lo hará público mediante su fijación en el tablón de anuncios (art. 134.4 LJV

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SOCIEDAD RECTORA DEL MERCADO OFICIAL DE RENTA FIJA PRIVADA

D./Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante ese organismo comparezco y como mejor en Derecho proceda, DIGO:

Que por medio del presente escrito, y de conformidad con el art. 134 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), pongo en su conocimiento la iniciación del expediente de jurisdicción voluntaria en orden a ratificar la interdicción previamente acordada.

1.ª [COMPLETAR])

Que mediante escrito de fecha [FECHA], comuniqué a la Sociedad Rectora a la que tengo el honor de dirigirme, el robo de [COMPLETAR] valores admitidos a cotización oficial en el mercado de renta fija, en su modalidad de [COMPLETAR], emitidos por la entidad emisora [COMPLETAR], con número de serie [COMPLETAR], y numerados del [COMPLETAR] al [COMPLETAR], ambos inclusive.

2.ª [COMPLETAR])

Que el pasado [FECHA] la Sociedad Rectora indicada prohibió la negociación o transmisión de los valores indicados y el pago de capital, intereses o dividendos, y comunicó el robo a las restantes sociedades rectoras, con publicación en el tablón de anuncios, en el Tablón Judicial Edictal Único, y en un periódico de gran circulación.

3.ª [COMPLETAR])

Que cumpliendo con lo dispuesto en el art. 134.3 LJV, y dentro del plazo legal de nueve días, presenté ante la Sección de lo Mercantil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], solicitud para iniciar el expediente previsto en los arts. 132 y ss. LJV, y conseguir la ratificación en sede judicial de la prohibición acordada. El expediente se ha iniciado, con nº [Nº DE EXPEDIENTE] / [COMPLETAR], habiendo dictado el Letrado de la Administración de Justicia de dicho órgano judicial, diligencia de ordenación de fecha [FECHA], en la cual se ordenaba comunicar tal circunstancia a la propia sociedad rectora.

4.ª [COMPLETAR])

Que a los efectos de impedir que se levante la interdicción de la negociación o transmisión de los valores, y del pago de intereses, capital o dividendos; mediante el presente escrito se comunica la iniciación del citado expediente, según lo previsto en el art. 134.4 de LJV.

5.ª [COMPLETAR])

Se acompañan a este escrito copia de la solicitud de inicio del expediente, fechada el [COMPLETAR], y copia de la diligencia de ordenación dictada por el Letrado de la Administración de Justicia de la Sección de lo Mercantil del Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO], el pasado [FECHA].

Por todo lo expuesto, al amparo del art. 134 LJV,

SOLICITO A LA SOCIEDAD RECTORA DEL MERCADO OFICIAL DE RENTA FIJA

Que teniendo por presentado este escrito y documentos que lo acompañan, se tenga por comunicado el inicio del expediente de jurisdicción voluntaria previsto en los arts. 132 y ss. LJV ante la Sección de lo Mercantil del Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO], en el expediente tramitado con nº [Nº DE EXPEDIENTE] / [COMPLETAR].

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma el denunciante

========================================================================
