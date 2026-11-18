---
name: denuncia-sociedad-rectora-robo-hurto-extravio-valores-693
description: "Redacta el escrito «Denuncia a la sociedad rectora por robo, hurto o extravío de valores cotizados» (formulario 693 de jurisdicción voluntaria, masc, mediación y arbitraje, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Denuncia a la sociedad rectora por robo, hurto o extravío de valores cotizados

> Formulario 0693 del plugin **Jurisdicción voluntaria, MASC, mediación y arbitraje** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD (2 veces)
- [ ] CALLE (2 veces)
- [ ] NÚMERO (2 veces)
- [ ] FECHA (3 veces)
- [ ] IMPORTE
- [ ] LUGAR
- [ ] Otros 22 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…ociados en el mercado de renta fija. 1.ª»; «…) Que soy propietario de»; «…ercado de renta fija, en su modalidad de»; «…, emitidos por la entidad emisora»; «… Los valores disponen de número de serie»; «…, y se encuentran numerados del»; «…al»; «…gado específico otorgado por mi padre D.»; «…, quien falleció el»; «…ban depositados en la entidad financiera»; «…SA. 2.ª»; «…tulos no han podido ser recuperados. 3.ª»; …

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 134 de la Ley 15/2015
- art. 134.1 LJV
- art. 134.2 LJV
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

### Formulario 0693 · Denuncia a la sociedad rectora por robo, hurto o extravío de valores cotizados

- Año del modelo: 2015
- Revisión 17-11-2026: 35 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Esta denuncia puede ser presentada por los poseedores legítimos de los títulos que hubieren sido desposeídos de los mismos, así como los que hubieren sufrido su destrucción o extravío, cuando se trate de valores admitidos a negociación en alguna Bolsa u otro mercado secundario oficial. Se debe dirigir a la Sociedad Rectora del mercado secundario oficial correspondiente al domicilio de la entidad emisora para denunciar el robo, hurto, destrucción o extravío del título. El denunciante debe solicitar la iniciación del expediente de jurisdicción voluntaria de los arts. 132 y ss. LJV en el plazo máximo de 9 días a contar desde la formalización de la denuncia.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SOCIEDAD RECTORA DEL MERCADO OFICIAL DE RENTA FIJA PRIVADA

D./Dña. [NOMBRE Y APELLIDOS], con DNI [DNI/NIE], de profesión [PROFESIÓN], y domicilio en [LOCALIDAD], calle [CALLE], nº [NÚMERO], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO:

Que por medio del presente escrito, y de conformidad con el art. 134 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), pongo en su conocimiento el robo de los títulos representativos de valores de mi propiedad, negociados en el mercado de renta fija.

1.ª [COMPLETAR])

Que soy propietario de [COMPLETAR] valores admitidos a cotización oficial en el mercado de renta fija, en su modalidad de [COMPLETAR], emitidos por la entidad emisora [COMPLETAR]. Los valores disponen de número de serie [COMPLETAR], y se encuentran numerados del [COMPLETAR] al [COMPLETAR], ambos inclusive. Fueron adquiridos mediante escritura de adjudicación de herencia de fecha [FECHA], tras legado específico otorgado por mi padre D. [COMPLETAR], quien falleció el [COMPLETAR]. Suponen un valor global de [IMPORTE] euros, y se encontraban depositados en la entidad financiera [COMPLETAR] SA.

2.ª [COMPLETAR])

El pasado [FECHA], la sucursal de la citada entidad sita en [LOCALIDAD], calle [CALLE], nº [NÚMERO], fue objeto de robo, denunciado ante el Cuerpo Nacional de Policía, y como consecuencia del cual se sustrajeron diversos títulos de clientes de aquélla, entre ellos los indicados que eran de mi propiedad en su totalidad. Hasta la fecha las investigaciones policiales no han dado sus frutos, y los títulos no han podido ser recuperados.

3.ª [COMPLETAR])

Por ello, de conformidad con el art. 134.1 LJV y el art. 549 del Código de Comercio, comunico el robo a la Sociedad Rectora del mercado secundario de renta fija, a la que tengo el honor de dirigirme, al ser la correspondiente a la referida entidad emisora.

4.ª [COMPLETAR])

El objeto de la presente comunicación es impedir, de manera inmediata, la negociación o transmisión de los valores indicados y el pago de capital, intereses o dividendos. En este sentido, me comprometo a solicitar, en el plazo de nueve días, la iniciación del expediente previsto en los arts. 132 y ss. LJV, a fin de que se ratifique dicha prohibición por el Letrado de la Administración de Justicia de la Sección de lo Mercantil del Tribunal de Instancia que corresponda. Asimismo, solicito que se comunique el robo a las restantes sociedades rectoras, con publicación en el Tablón Judicial Edictal Único, y en un periódico de gran circulación, tal y como habilita el art. 134.2 LJV.

5.ª [COMPLETAR])

Se acompañan a este escrito copia del atestado elaborado por Cuerpo Nacional de Policía, copia de la escritura pública de adjudicación de herencia, y certificación expedida por la entidad emisora [COMPLETAR], y por la entidad depositaria [COMPLETAR] SA.

Por todo lo expuesto, al amparo del art. 134 LJV y del art. 549 del Código de Comercio,

SOLICITO A LA SOCIEDAD RECTORA DEL MERCADO OFICIAL DE RENTA FIJA

Que teniendo por presentado este escrito y documentos que lo acompañan:

1.- Se tenga por comunicado el robo de [COMPLETAR] valores admitidos a cotización oficial en el mercado de renta fija, en su modalidad de [COMPLETAR], emitidos por la entidad emisora [COMPLETAR], con número de serie [COMPLETAR], y numerados del [COMPLETAR] al [COMPLETAR], ambos inclusive.
2.- Se prohíba la negociación o transmisión de los valores indicados y el pago de capital, intereses o dividendos.
3.- Se comunique el robo a las restantes sociedades rectoras, con publicación en el tablón de anuncios, en el Tablón Judicial Edictal Único, y en un periódico de gran circulación.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma el denunciante

========================================================================
