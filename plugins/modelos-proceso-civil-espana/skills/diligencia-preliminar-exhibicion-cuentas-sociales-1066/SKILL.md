---
name: diligencia-preliminar-exhibicion-cuentas-sociales-1066
description: "Redacta el escrito «Diligencia preliminar: exhibición de cuentas sociales» (formulario 1066 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Diligencia preliminar: exhibición de cuentas sociales

> Formulario 1066 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] NÚMERO
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] Nº DE DOCUMENTO
- [ ] Nº DE COLEGIADO
- [ ] COLEGIO
- [ ] NIF
- [ ] LOCALIDAD
- [ ] TELÉFONO
- [ ] ACTO O RESOLUCIÓN
- [ ] Nº (2 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] IMPORTE
- [ ] Otros 20 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…bición de cuentas sociales de la entidad»; «…y número de fax»; «…o tiene intención de promover demanda de»; «…en el ejercicio de la acción»; «…bjeto concreto de la demanda consiste en»; «…terposición de su demanda) de la entidad»; «…, S.L. referidas al ejercicio»; «…. Como documento núm. acompaño»; «…ondición de socio/comunero de la entidad»; «…s objeto de esta solicitud, toda vez que»; «…uentas cuya exhibición se pide, debido a»; «…del administrador de hecho de la entidad»; …

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

### Formulario 1066 · Diligencia preliminar: exhibición de cuentas sociales

- Año del modelo: 2013
- Revisión 17-11-2026: 36 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE COLEGIADO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE] PLAZA Nº [NÚMERO]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, actuando en nombre de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], ante el Tribunal comparezco bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], colegiado núm. [Nº DE COLEGIADO] del Iltre. Colegio de Abogados de [COLEGIO], y como mejor proceda en derecho DIGO:

Que mediante el presente escrito, en nombre de mi representado y al amparo de lo dispuesto en el artículo 256.1.4..º de la Ley de Enjuiciamiento Civil, promuevo DILIGENCIA PRELIMINAR de exhibición de cuentas sociales de la entidad [COMPLETAR], S.L., provista de CIF [NIF] y con domicilio social en [LOCALIDAD], provista de número de teléfono [TELÉFONO] y número de fax [COMPLETAR], basándome en los siguientes

ANTECEDENTES

Mi representado tiene intención de promover demanda de [COMPLETAR] en el ejercicio de la acción [COMPLETAR] (determinar contenido) frente a [ACTO O RESOLUCIÓN], S.L.

El objeto concreto de la demanda consiste en [COMPLETAR] (detallar).

No dispone mi poderdante de las cuentas sociales (u otros documentos necesarios para la interposición de su demanda) de la entidad [COMPLETAR], S.L. referidas al ejercicio [COMPLETAR].

Como documento núm. acompaño [COMPLETAR] (por ejemplo, documento acreditativo de la condición de socio/comunero de la entidad [COMPLETAR] que ostenta mi representado).

Para plantear adecuadamente su demanda precisa mi poderdante conocer el contenido de las cuentas sociales objeto de esta solicitud, toda vez que [COMPLETAR] (desarrollar justificación).

No tiene mi representado posibilidad de acceso a las cuentas cuya exhibición se pide, debido a [COMPLETAR] (justificar la necesidad de la diligencia preliminar solicitada; por ejemplo: por encontrarse dichas cuentas —o documentos— en poder del administrador de hecho de la entidad [COMPLETAR], S.L., D./Dña. [NOMBRE Y APELLIDOS] que se ha negado injustificadamente a facilitar copia al resto de los socios/comuneros).

A los efectos previstos en el artículo 261.4.ª de la LEC acompaño, reseñada como documento núm. [Nº], copia de las cuentas correspondientes a la contabilidad de la entidad [COMPLETAR] referidas al ejercicio [COMPLETAR] de que dispone mi mandante (o elaboradas con los datos de que dispone mi representado), con objeto de que si la persona requerida para que exhiba las cuentas oficiales no cumple el requerimiento ni formula oposición, las cuentas que se acompañan sean tenidas por ciertas a efectos del juicio posterior que pretende entablar mi poderdante.

Resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

Es competente el Tribunal al que me dirijo en virtud de lo dispuesto por el artículo 257 de la Ley de Enjuiciamiento Civil (LEC).

Procedimiento

La solicitud se tramitará por el cauce establecido en las artículos 258 y siguientes de la Ley de Enjuiciamiento Civil.

Caución

El artículo 263 de la LEC exige el ofrecimiento de prestación de caución para responder de eventuales gastos y daños y perjuicios que se pudieran irrogar a la parte frente a la que se promueven estas diligencias. Se verifica dicho ofrecimiento mediante otrosí.

Fondo

El artículo 256.1.4.° de la LEC habilita la preparación del juicio «Por petición de un socio o comunero para que se le exhiban los documentos y cuentas de la sociedad o comunidad, dirigida a éstas o al consocio o condueño que los tenga en su poder».

En el presente caso se justifican la pertinencia y proporcionalidad de la diligencia preliminar interesada por las circunstancias de [COMPLETAR] (justificar mediante la alegación de las circunstancias concurrentes).

La justa causa y el interés legítimo de mi mandante que exige el artículo 258 de la LEC radican en su condición de socio/comunero de la entidad [COMPLETAR].

Concurre en la persona frente a la que se dirige esta solicitud la condición de consocio/condueño a que hace referencia el artículo 256.1.4.º de la LEC.

 (desarrollar cuantas razones contribuyan a plantear la diligencia como adecuada a la finalidad perseguida y acreditar que la medida guarda proporcionalidad con dicho fin).

Determina el artículo 261.4.ª de la LEC que «Si se hubiera pedido la exhibición de documentos contables, se podrán tener por ciertos, a los efectos del juicio posterior, las cuentas y datos que presente el solicitante».

Por lo expuesto,

SUPLICO AL TRIBUNAL: que tenga por presentado este escrito, con el poder y el documento que se acompañan con sus preceptivas copias, se sirva admitirlo, teniendo por promovida la diligencia preliminar solicitada, y en su virtud requiera a [COMPLETAR], S.L. a través de su Legal Representante para que exhiba las cuentas sociales (el documento [COMPLETAR]) de la entidad [COMPLETAR], S.L. correspondientes al ejercicio [COMPLETAR], acordando, si no atendiese el requerimiento ni formulase oposición, tener por ciertos, a los efectos del juicio posterior, las cuentas y datos que presenta mi representado en el documento que se acompaña referenciado con núm. [Nº], todo ello con los demás pronunciamientos procedentes en derecho, y, una vez practicada la diligencia interesada, se me expida testimonio de su resultado.

Es Justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

OTROSÍ DIGO: que a los efectos previstos en los artículos 256.3 y 258.3, y aun cuando esta parte entiende que la diligencia solicitada no la precisaría, ofrecemos prestar, en la forma y plazos legalmente establecidos, la caución de [IMPORTE] euros, o subsidiariamente la que determine el Tribunal, comprometiéndonos a constituir la caución que se señale.

NUEVAMENTE SUPLICO AL TRIBUNAL que tenga por realizado el anterior ofrecimiento de prestación de caución a los efectos legales oportunos.

Es Justicia que reitero en igual lugar y fecha.

========================================================================
