---
name: exhibicion-acto-ultima-voluntad-peticion-1041
description: "Redacta el escrito «Exhibición de acto de última voluntad: petición» (formulario 1041 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Exhibición de acto de última voluntad: petición

> Formulario 1041 del plugin **Sucesiones** · revisado el 17-11-2026.

## Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
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
- [ ] NOMBRE Y APELLIDOS (12 veces)
- [ ] Nº DE DOCUMENTO
- [ ] COLEGIO
- [ ] DNI/NIE
- [ ] TELÉFONO
- [ ] ACTO O RESOLUCIÓN
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] IMPORTE
- [ ] Otros 7 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…rovisto de DNI [DNI/NIE], domiciliado en»; «…y número de fax»; «…a tiene intención de promover demanda de»; «…bjeto concreto de la demanda consiste en»; «…Como documento núm.acompaño»; «…ibilidad de acceso al documento debido a»; «…nar interesada por las circunstancias de»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 263 de la LEC
- artículo 258 de la LEC

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

### Formulario 1041 · Exhibición de acto de última voluntad: petición

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 25 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en nombre de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], ante el Tribunal comparezco bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], colegiado núm.del Iltre. Colegio de Abogados de [COLEGIO], y como mejor proceda en derecho DIGO:

Que mediante el presente escrito, en nombre de mi representada y al amparo de lo dispuesto en el artículo 256.1.3.º de la LEC, promuevo DILIGENCIA PRELIMINAR de exhibición de acto de última voluntad del causante D./Dña. [NOMBRE Y APELLIDOS], dirigiendo esta solicitud contra D./Dña. [NOMBRE Y APELLIDOS], provisto de DNI [DNI/NIE], domiciliado en [COMPLETAR] y provisto de número de teléfono [TELÉFONO] y número de fax [COMPLETAR], basándome en los siguientes

ANTECEDENTES

Mi representada tiene intención de promover demanda de [COMPLETAR] en el ejercicio de la acción

 (por ejemplo de división de herencia) frente a [ACTO O RESOLUCIÓN]

El objeto concreto de la demanda consiste en [COMPLETAR] (detallar).

No dispone mi poderdante del documento en que consta el acto de última voluntad del causante D./Dña. [NOMBRE Y APELLIDOS], que se encuentra en poder de D. [NOMBRE Y APELLIDOS]

Como documento núm.acompaño [COMPLETAR] (por ejemplo, documento acreditativo de la condición de heredera que ostenta mi representada).

Para plantear adecuadamente la demanda precisa mi poderdante conocer el contenido del acto de última voluntad objeto de esta solicitud.

No tiene mi representado posibilidad de acceso al documento debido a [COMPLETAR] (justificar la necesidad de la diligencia preliminar solicitada; por ejemplo: por tratarse de un testamento ológrafo pendiente de protocolización, cuya única copia obra en poder de D./Dña. [NOMBRE Y APELLIDOS], que se ha negado sin justificación alguna a facilitar copia al resto de los herederos del causante D./Dña. [NOMBRE Y APELLIDOS]).

Resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

Es competente el Tribunal al que me dirijo en virtud de lo dispuesto por el artículo 257 de la Ley de Enjuiciamiento Civil (LEC), en relación con el art. 85.1º LOPJ.

Procedimiento

La solicitud se tramitará por el cauce establecido en las artículos 258 y siguientes de la LEC.

El artículo 263 de la LEC exige el ofrecimiento de prestación de caución para responder de eventuales gastos y daños y perjuicios que se pudieran irrogar a la parte frente a la que se promueven estas diligencias. Se realiza dicho ofrecimiento mediante otrosí.

Fondo

El artículo 256.1.3.° de la LEC habilita la preparación del juicio «Por petición del que se considere heredero, coheredero o legatario, de exhibición, por quien lo tenga en su poder, del acto de última voluntad del causante de la herencia o legado».

En el presente caso se justifican la pertinencia y proporcionalidad de la diligencia preliminar interesada por las circunstancias de [COMPLETAR] (justificar mediante la alegación de las circunstancias concurrentes).

La justa causa y el interés legítimo de mi mandante que exige el artículo 258 de la LEC radican en su condición de heredero del causante D. [NOMBRE Y APELLIDOS]

 (desarrollar cuantas razones contribuyan a plantear la diligencia como adecuada a la finalidad perseguida y acreditar que la medida guarda proporcionalidad con dicho fin).

Por lo expuesto,

SUPLICO AL TRIBUNAL: que tenga por presentado este escrito, con el poder y el documento que se acompañan con sus copias preceptivas, se sirva admitirlo, teniendo por promovida la diligencia preliminar solicitada, y en su virtud requiera a D./Dña. [NOMBRE Y APELLIDOS] para que exhiba el documento en que consta el acto de última voluntad del causante D./Dña. [NOMBRE Y APELLIDOS], acordando, si no atendiese el requerimiento ni formulase oposición, la entrada y registro en el local sito en [LOCALIDAD], donde se encuentra el documento objeto de esta diligencia, acordando que se ocupe dicho documento y se ponga a disposición de mi representado en la sede del Tribunal, todo ello con los demás pronunciamientos procedentes en derecho, y, una vez practicada la diligencia interesada, se me expida testimonio de su resultado.

Es Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

OTROSÍ DIGO: que a los efectos previstos en los artículos 256.3 y 258.3, y aun cuando esta parte entiende que la diligencia solicitada no la precisaría, ofrecemos prestar, en la forma y plazos legalmente establecidos, caución por [IMPORTE] euros, o subsidiariamente la que fije el Tribunal, comprometiéndonos a constituir la caución que se señale.

NUEVAMENTE SUPLICO AL TRIBUNAL: tenga por hecho el anterior ofrecimiento de prestación de caución a los efectos legales oportunos.

Es Justicia que reitero en igual lugar y fecha.

========================================================================
