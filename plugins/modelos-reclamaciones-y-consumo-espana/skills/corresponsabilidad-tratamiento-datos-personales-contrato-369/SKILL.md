---
name: corresponsabilidad-tratamiento-datos-personales-contrato-369
description: "Redacta el escrito «Corresponsabilidad en el tratamiento de datos personales: contrato» (formulario 369 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Corresponsabilidad en el tratamiento de datos personales: contrato

> Formulario 0369 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] Nº (4 veces)
- [ ] LOCALIDAD (2 veces)
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] Otros 2 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, interviene en representación de la»; «…, interviene en representación de la»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 26 del RGPD
- Ley Orgánica 3/2018

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

### Formulario 0369 · Corresponsabilidad en el tratamiento de datos personales: contrato

- Año del modelo: 2019
- Revisión 17-11-2026: 11 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [LUGAR], a [DÍA] de [MES] de [AÑO].

REUNIDOS

De una parte, con DNI núm. [Nº], interviene en representación de la [COMPLETAR] con domicilio social en [LOCALIDAD], y CIF núm. [Nº], en su calidad de CORRESPONSABLE 1 DEL TRATAMIENTO DE DATOS de esta, en adelante “el CORRESPONSABLE 1”,

De otra parte, con DNI núm. [Nº], interviene en representación de la [COMPLETAR] con domicilio social en [LOCALIDAD], y CIF núm. [Nº], en su calidad de CORRESPONSABLE 2 DEL TRATAMIENTO DE DATOS de esta, en adelante “el CORRESPONSABLE 2”,

Ambos comparecientes se reconocen mutua y recíprocamente suficiente capacidad para obligarse entre sí por medio del presente CONTRATO DE CORRESPONSABILIDAD EN EL TRATAMIENTO DE DATOS PERSONALES, conforme a lo establecido en los artículos 4.7 y 26 del Reglamento (UE) 2016/679 del Parlamento Europeo y del Consejo, de 27 de abril de 2016, relativo a la protección de las personas físicas en lo que respecta al tratamiento de datos personales y a la libre circulación de estos datos (en adelante, RGPD), y a tal fin,

EXPONEN

A) Que ambas entidades han determinado conjuntamente los objetivos y los medios del tratamiento, por lo que son consideradas corresponsables del tratamiento.

B) Que, en cumplimiento con lo dispuesto en el artículo 26 del RGPD, el tratamiento de datos de carácter personal de los corresponsables requiere la determinación de modo transparente y de mutuo acuerdo de las responsabilidades respectivas, especialmente respecto al ejercicio de los derechos del interesado y sus obligaciones de suministro de información.

De acuerdo con lo anterior, las partes suscriben el presente contrato, que se regirá de conformidad con las siguientes

Cláusulas

PRIMERA.- Definiciones

Responsable del tratamiento: persona física o jurídica, de naturaleza pública o privada, u órgano administrativo, que decida sobre la finalidad, contenido y uso del tratamiento.

Corresponsables del tratamiento: aquellos responsables que determinan conjuntamente los objetivos y los medios del tratamiento.

SEGUNDA.- Objeto y alcance

Las presentes Cláusulas tienen por objeto regular las relaciones entre el ambos Corresponsables del tratamiento de los datos que sean necesarios para los tratamientos siguientes:

TERCERA. Confidencialidad

Toda la información de cualquier clase que obtenga o sea expuesta por ambas partes será tratada de forma confidencial, obligándose a proteger esta información del mismo modo que protege la confidencialidad de la información de su propiedad de similar naturaleza y a su no revelación a terceros bajo ningún concepto. Esta obligación de confidencialidad existirá aún después de la conclusión de los servicios objeto de este Convenio.

Los firmantes de este contrato se informan recíprocamente de que sus respectivos datos personales recogidos en el mismo serán tratados de acuerdo con la legislación vigente en materia de protección de datos de carácter personal, con la finalidad del desarrollo del presente convenio, sin que sean cedidos a terceros salvo que sea necesario por imposición legal.

Las partes se comprometen a tratar los datos personales de acuerdo con lo dispuesto en el RGPD y la Ley Orgánica 3/2018, de 5 de diciembre, de Protección de Datos Personales y garantía de los derechos digitales y en la normativa aplicable en la materia.

Las partes se comprometen a informar a los titulares de los datos de los fines para los que se van a tratar sus datos, así como recabar, en su caso, los consentimientos necesarios para poder tratar legítimamente los datos personales.

Para ejercitar los derechos de acceso, rectificación, supresión u oposición, así como del resto de derechos reconocidos en el RGPD y en la Ley Orgánica 3/2018, los firmantes deberán dirigirse en su caso a la dirección de quien, respectivamente, actúa como contraparte y cuya determinación figura en el encabezamiento de este Convenio.

CUARTA.- Obligaciones de los corresponsables del tratamiento

Los corresponsables del tratamiento se obligan a:

1. Garantizar por parte de los interesados ante cualquiera de los corresponsables el ejercicio de los derechos de: Acceso, rectificación, supresión y oposición; Limitación del tratamiento; Portabilidad de datos; A no ser objeto de decisiones individualizadas automatizadas (incluida la elaboración de perfiles).

2. Los corresponsables deben resolver dentro del plazo establecido las solicitudes de ejercicio de derechos y comunicar a la otra parte la recepción de la solicitud a fin de que puedan resolver conjuntamente dichas solicitudes.

3. Los corresponsables, en el momento de la recogida de los datos, deben facilitar la información relativa a los tratamientos de datos que se van a realizar, incluyendo la identidad de los diversos responsables del tratamiento.

4. Realizar conjuntamente las evaluaciones de impacto relativas a la protección de datos, cuando proceda.

5. Ambas partes se obligan a poner mutuamente a su disposición toda la información necesaria para demostrar el cumplimiento de sus obligaciones, así como para la realización de las auditorías o las inspecciones que realicen el corresponsable u otro auditor autorizado por él.

6. Implantar las medidas de seguridad necesarias.

7. Designar un delegado de protección de datos y comunicar su identidad y datos de contacto al otro corresponsable.

QUINTA.- Duración y resolución del contrato

El presente contrato se considera accesorio a la condición de las partes de corresponsables del tratamiento, por lo que su duración y extinción queda supeditada a la existencia de dicha condición.

SEXTA.- Subcontratación

Las partes se informarán recíprocamente de las subcontrataciones que realicen en el tratamiento de los datos objeto de este convenio.

Si fuera necesario subcontratar algún tratamiento, este hecho se deberá comunicar previamente y por escrito a la otra parte, con una antelación de 15 días, indicando los tratamientos que se pretende subcontratar e identificando de forma clara e inequívoca la empresa subcontratista y sus datos de contacto.

El subcontratista, tendrá la condición de encargado del tratamiento, está obligado igualmente a cumplir las obligaciones establecidas en este documento para el encargado del tratamiento y las instrucciones que dicte su Responsable. En el caso de incumplimiento por parte del subencargado, el encargado inicial seguirá siendo plenamente responsable ante el responsable en lo referente al cumplimiento de las obligaciones.

SÉPTIMA. Notificación de violaciones de la seguridad de los datos objeto de este Convenio

Las partes se comunicarán, sin dilación indebida, y a través de métodos que dejen constancia de tal comunicación, las violaciones de la seguridad de los datos personales a su cargo de las que tenga conocimiento, juntamente con toda la información relevante para la documentación y comunicación de la incidencia.

No será necesaria la notificación cuando sea improbable que dicha violación de la seguridad constituya un riesgo para los derechos y las libertades de las personas físicas. Si se dispone de ella se facilitará, como mínimo, la información siguiente:

• Descripción de la naturaleza de la violación de la seguridad de los datos personales, inclusive, cuando sea posible, las categorías y el número aproximado de interesados afectados, y las categorías y el número aproximado de registros de datos personales afectados.

• Descripción de las posibles consecuencias de la violación de la seguridad de los datos personales.

• Descripción de las medidas adoptadas o propuestas para poner remedio a la violación de la seguridad de los datos personales, incluyendo, si procede, las medidas adoptadas para mitigar los posibles efectos negativos.

Si no es posible facilitar la información simultáneamente, y en la medida en que no lo sea, la información se facilitará de manera gradual sin dilación indebida.

En prueba de conformidad las partes firman el presente contrato por duplicado y a un sólo efecto, en lugar y fecha indicados en el encabezamiento

D./D.ª [NOMBRE Y APELLIDOS] D./D.ª [NOMBRE Y APELLIDOS]
