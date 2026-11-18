---
name: exhibicion-libros-quienes-deben-llevar-contabilidad-690
description: "Redacta el escrito «Exhibición de libros de quienes deben llevar contabilidad» (formulario 690 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Exhibición de libros de quienes deben llevar contabilidad

> Formulario 0690 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] Nº DE DOCUMENTO
- [ ] FECHA (2 veces)
- [ ] CALLE
- [ ] NÚMERO
- [ ] LUGAR
- [ ] Otros 11 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…en nombre y representación de la entidad»; «…SL»; «…or de artículos deportivos en la zona de»; «…, de»; «…on establecimiento abierto al público en»; «… nº [NÚMERO], con el nombre comercial de»; «…iente más importante. 2º) Que el próximo»; «…ales correspondiente a los ejercicios de»; «…y»; «…s de aquel, relativo a los ejercicios de»; «…y»

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 112 de la Ley 15/2015
- art. 114 LJV
- art. 113.1 LJV
- art. 112 LJV
- art. 114.2 LJV

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

### Formulario 0690 · Exhibición de libros de quienes deben llevar contabilidad

- Año del modelo: 2015
- Revisión 17-11-2026: restos de formato retirados; notas del formulario agrupadas al final (1); 24 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Por medio del presente escrito, y de conformidad con el art. 112 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria se promueve expediente en solicitud de exhibición de libros contables.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de la entidad [COMPLETAR] SL [COMPLETAR], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], como mejor proceda en derecho comparezco y DIGO: (1)

Que por medio del presente escrito, y de conformidad con el art. 112 de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud de exhibición de libros contables. Todo ello, en base a los siguientes

Hechos y consideraciones jurídicas:

1º) Que mi mandante es proveedor de artículos deportivos en la zona de [COMPLETAR], de [COMPLETAR], y mantiene un contrato de suministro periódico, de fecha [FECHA], con D./Dña. [NOMBRE Y APELLIDOS], comerciante con establecimiento abierto al público en [COMPLETAR], calle [CALLE], nº [NÚMERO], con el nombre comercial de [COMPLETAR]. En los últimos tres años, la facturación por dicho suministro ha supuesto un 60% del total del negocio de mi representado, convirtiéndose, de esta forma, en el cliente más importante.

2º) Que el próximo [COMPLETAR] debe renovarse el contrato de suministro, y D./Dña. [NOMBRE Y APELLIDOS] impone, o quiere imponer, una rebaja de casi la mitad en el precio de los productos, para continuar con la relación comercial. Y ello, con el argumento de la precaria situación económica del citado negocio generada con la crisis sufrida en el sector en los últimos dos años.

3º) Dado que esa drástica rebaja del precio de los suministros supondrá una reducción de los ingresos de mi mandante, que no se puede adecuar a su coste de adquisición, y pondrá en riesgo su situación económica; es interés de éste revisar la contabilidad de D./Dña. [NOMBRE Y APELLIDOS], para comprobar tal extremo, y poder negociar, o aceptar tal sacrificio, con conocimiento de la situación real de su cliente más importante. Se reúne, en este sentido, la condición de interesado exigida en el art. 32.2 del Código de Comercio, para solicitar la exhibición de libros y documentos. A los efectos de cumplir con las exigencias de tal precepto legal, se señala expresamente la voluntad de revisar el libro de inventario y cuentas anuales correspondiente a los ejercicios de [COMPLETAR] y [COMPLETAR].

4º) Se acude, por ello, al expediente previsto en los arts. 112 y ss. LJV, cumpliendo con los requisitos exigidos en su art. 114 LJV, al hacer constar el derecho o interés legítimo de mi representada, con especificación de los asientos a examinar, y el objeto y finalidad de la solicitud. La misma se dirige frente al propio D./Dña. [NOMBRE Y APELLIDOS], quien opera en el mercado en su propio nombre, reuniendo los requisitos de comerciante previstos en el art. 2 del Código de Comercio, y quien está obligado a llevar una contabilidad ordenada conforme al art. 25.1 del mismo texto legal.

5º) Que es competente el Tribunal al que me dirijo conforme al art. 113.1 LJV, al encontrarse en su partido judicial el establecimiento a cuya contabilidad se refieren los libros cuya revisión se pretende.

6º) Se acompañan a esta solicitud copia del contrato de suministro, copia de las cuentas anuales de mi mandante, donde se puede comprobar la importancia de D./Dña. [NOMBRE Y APELLIDOS] en su cartera de clientes, y comunicación de este último exigiendo la citada reducción del precio.

Por todo lo expuesto, al amparo del art. 32.3 del Código de Comercio, y del art. 112 LJV,

SOLICITO AL TRIBUNAL

Que teniendo por presentado este escrito y documentos que lo acompañan y por promovido expediente de jurisdicción voluntaria para la exhibición de libros de contabilidad, y previo el traslado a D./Dña. [NOMBRE Y APELLIDOS]; se cite a las partes a la comparecencia judicial prevista en el art. 114.2 LJV, a fin de que se autorice el examen del libro de inventario y cuentas anuales de aquel, relativo a los ejercicios de [COMPLETAR] y [COMPLETAR].

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

NOTAS DEL FORMULARIO

(1) La exigencia de abogado y procurador para plantear expediente de jurisdicción voluntaria variará, según el art 3.2 LJV, en función del expediente de que se trate, y la exigencia legal al respecto. En el supuesto específico del presente escrito, el art. 113.2 de la Ley de Jurisdicción Voluntaria exige de manera preceptiva la intervención de Abogado y Procurador para la solicitud en análisis.

========================================================================
