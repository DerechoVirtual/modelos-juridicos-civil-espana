---
name: accion-declarativa-sobre-condiciones-generales-1034
description: "Redacta el escrito «Acción declarativa sobre condiciones generales de la contratación (general)» (formulario 1034 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acción declarativa sobre condiciones generales de la contratación (general)

> Formulario 1034 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (3 veces)
- [ ] NIF
- [ ] CALLE
- [ ] NÚMERO (3 veces)
- [ ] DESCRIBIR (3 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] ACTO O RESOLUCIÓN
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 19 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…la Asociación de Consumidores y Usuarios»; «…rito formulo demanda contra la mercantil»; «…social según el art. de sus Estatutos es»; «…, presta servicios de»; «…en el ámbito de esta»; «…certificación del Registro Mercantil de»; «…ción de sus Estatutos. Dicho servicio de»; «…numerosas personas y en concreto en esta»; «…Administración para prestar servicios de»; «…se le obligaba a»; «…iones publicado en el boletín oficial de»; «…ionado de sus contratos la regulación de»; …

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- arts. 21 y 22.4 de la LOPJ
- art. 253.3 de la LEC
- arts. 23 y 31 de la LEC
- art. 5 de la Ley Orgánica 1/2025
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

### Formulario 1034 · Acción declarativa sobre condiciones generales de la contratación (general)

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 34 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, en nombre y representación de la Asociación de Consumidores y Usuarios [COMPLETAR], según acredito mediante poder notarial que acompaño otorgado por su presidente D./Dña. [NOMBRE Y APELLIDOS], que a su vez actúa en nombre de la misma, ante el Tribunal comparezco bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO:

Que mediante el presente escrito formulo demanda contra la mercantil [COMPLETAR], con NIF n.º [NIF] con sede en esta ciudad en la C/ [CALLE], n.º [NÚMERO] en ejercicio de acción colectiva sobre condiciones generales de contratación de carácter declarativa a fin de que se reconozca la cláusula que en el suplico se concretará como condición general de contratación en los contratos que suscribe la empresa demandada relativos a [DESCRIBIR], así como que se ordene su inscripción en el Registro de Condiciones Generales de Contratación. La presente demanda se tramitará por el cauce del juicio ordinario conforme a los siguientes

HECHOS

Se presenta listado de documentos que acompañan a la demanda.

La empresa demandada, cuyo objeto social según el art. de sus Estatutos es [COMPLETAR], presta servicios de [COMPLETAR] en el ámbito de esta [COMPLETAR] (ciudad, provincia, comunidad). Adjunto como documento n.º [NÚMERO] certificación del Registro Mercantil de [COMPLETAR] de la constitución de la Sociedad y la aprobación de sus Estatutos.

Dicho servicio de [COMPLETAR] es utilizado por numerosas personas y en concreto en esta [COMPLETAR] (ciudad, provincia), es la única empresa autorizada para realizar dicha actividad. Dejamos acotados a efectos probatorios los archivos de la Administración de

Esta situación le ha llevado a imponer sus condiciones de contratación de manera unilateral utilizando en sus relaciones con terceros unos contratos de adhesión que recogen una serie de condiciones generales de contratación. Se acompaña como doc. n.º [NÚMERO] modelo de contrato de común aplicación en las relaciones con esa Compañía.

Cuando dicha empresa fue autorizada por la Administración para prestar servicios de [COMPLETAR] se le obligaba a [COMPLETAR], según consta en el pliego de condiciones publicado en el boletín oficial de [COMPLETAR] que presentamos como doc. n.º [Nº DE DOCUMENTO]

En varias ocasiones se ha requerido a la Empresa para que incluyera en el condicionado de sus contratos la regulación de [COMPLETAR] Igualmente se ha solicitado de la Administración que se exigiera a la ahora demandada para que cumpliera con los requisitos que en su día se le impusieron para acceder a ser la prestataria del servicio de [COMPLETAR] pero no se ha conseguido ningún resultado satisfactorio.

Entendemos que una adecuada defensa de los intereses generales de los consumidores y usuarios exige que se cumpla con lo exigido por la Administración y, por tanto, debe incluirse en los contratos de adhesión que emite la empresa [COMPLETAR] para los que utilicen los servicios de [COMPLETAR], que incluya la regulación de la materia de [COMPLETAR] dentro de las condiciones generales de la contratación de la forma siguiente:

Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

FUNDAMENTOS DE DERECHO

Jurisdicción y competencia

Los arts. 21 y 22.4 de la LOPJ y 36 de la LEC atribuyen al orden civil el conocimiento de esta materia.

Los arts. 85.1º de la LOPJ y 45 de la LEC determinan la competencia de las secciones civiles de los Tribunales de Instancia, salvo que la ley expresamente designe otro Tribunal para conocer del pleito.

Finalmente el art. 52.1.14.º la LEC dice que en los procesos en los que se ejercite la acción de declarativas sobre cláusulas de condiciones generales de contratación será competente el Tribunal del lugar donde el demandado tenga su establecimiento y, a falta de éste, el de su domicilio y si carece de domicilio en territorio español, el del lugar en que se hubiere realizado la adhesión.

Tramitación y cuantía de la demanda

Se seguirá el CAUCE del juicio ordinario en aplicación del art. 249.1.5.º de la LEC que remite a este trámite en las demandas en que se ejerciten acciones relativas a condiciones generales de contratación.

Consideramos en aplicación del art. 253.3 de la LEC que la CUANTÍA es indeterminada por tratarse de una acción mero declarativa.

Legitimación

Activa: El art. 16.3 de la Ley sobre Condiciones Generales de la Contratación faculta a las asociaciones de consumidores y usuarios legalmente constituidas para interponer las acciones recogidas en esta norma.

Pasiva: El art. 17.3 de la Ley de Condiciones Generales de la Contratación establece que procede la acción declarativa contra cualquier profesional que utilice las condiciones generales.

Postulación

Será preceptiva la intervención de Procurador y Abogado en aplicación de los arts. 23 y 31 de la LEC.

Cumplimiento de los requisitos de procedibilidad

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

Fondo del asunto

1.º El art. 12.4 de la Ley sobre Condiciones Generales de Contratación reconoce el derecho a interponer acción declarativa dirigida a obtener una sentencia que reconozca una cláusula como condición general de la contratación y ordene su inscripción cuando proceda.

En este caso entendemos que debe incluirse la cláusula relativa a [DESCRIBIR] por [COMPLETAR]

2.º El art. 11.2 de la Ley sobre Condiciones Generales de la Contratación permite la inscripción en el Registro de Condiciones Generales de Contratación de las que tengan tal carácter.

3.º Los arts. 8 a 10 del R.D.Leg. 1/2007, de 16 de noviembre, por el que se aprueba el Texto Refundido de la Ley General para la Defensa de los Consumidores y Usuarios regulan las facultades de éstos y la inclusión de sus derechos en los contratos que se pactan con ellos.

Costas

En aplicación del art. 394 de la LEC deberán imponerse a la parte demandada. Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño y tenga por formulada demanda de juicio ordinario contra [ACTO O RESOLUCIÓN], la admita a trámite y de traslado de la misma a la parte contraria a los efectos oportunos convocando posteriormente a las partes a la audiencia previa a fin de que en su día dicte sentencia:

1.º Por la que se declare la obligación de reconocer como válida y vigente la obligación del demandado de [COMPLETAR]

2.º Que en consecuencia se declare la obligación de incluir en todos sus contratos relativos a [DESCRIBIR] la siguiente cláusula como condición general de contratación:

3.º Que igualmente se ordene la inscripción de la citada cláusula a costa del demandado en el Registro de Condiciones Generales de la Contratación.

4.º Que se impongan las costas a la parte demandada.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
