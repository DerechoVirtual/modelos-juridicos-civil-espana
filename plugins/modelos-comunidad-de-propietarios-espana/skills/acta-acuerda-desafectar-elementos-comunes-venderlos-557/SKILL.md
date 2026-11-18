---
name: acta-acuerda-desafectar-elementos-comunes-venderlos-557
description: "Redacta el escrito «Acta que acuerda desafectar elementos comunes para venderlos» (formulario 557 de propiedad horizontal, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Acta que acuerda desafectar elementos comunes para venderlos

> Formulario 0557 del plugin **Propiedad horizontal** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- Numeración del art. 17 LPH anterior a la Ley 8/2013; el cómputo de ausentes está hoy en el art. 17.8 (30 días naturales).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] Nº (2 veces)
- [ ] CALLE
- [ ] NÚMERO (6 veces)
- [ ] FECHA
- [ ] NOMBRE Y APELLIDOS (12 veces)
- [ ] IMPORTE (3 veces)
- [ ] Otros 27 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…En»; «…a las [Nº] horas, se reúne en»; «…horas, se reúne en [COMPLETAR] en»; «…, piso»; «…, con coeficiente de participación del»; «…%. D./Dña. [NOMBRE Y APELLIDOS], piso»; «…, con coeficiente de participación del»; «…%. D./Dña. [NOMBRE Y APELLIDOS], piso»; «…, con coeficiente de participación del»; «…%. D./Dña. [NOMBRE Y APELLIDOS], piso»; «…, con coeficiente de participación del»; «…, con coeficiente de participación del»; …

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 17.8 de la LPH

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

### Formulario 0557 · Acta que acuerda desafectar elementos comunes para venderlos

- Año del modelo: 2016
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 50 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (IMPORTE)
- Avisos de la revisión: Numeración del art. 17 LPH anterior a la Ley 8/2013; el cómputo de ausentes está hoy en el art. 17.8 (30 días naturales).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

En [COMPLETAR] a las [Nº] horas, se reúne en [COMPLETAR] en [COMPLETAR] convocatoria la Junta General extraordinaria de la Comunidad de Propietarios de la c/ [CALLE] n.º [NÚMERO], previa convocatoria en forma a todos sus integrantes con las siguientes cuestiones a tratar en el orden del día, a saber:

1.º Lectura y aprobación, en su caso, del acta de la Junta anterior de fecha [FECHA].

2.º Desafección de su condición de elementos comunes en el sótano del edificio dos zonas, atribuyéndoles el carácter de elementos privativos independientes con destino a trasteros, asignándoles la correspondiente cuota en los elementos comunes del edificio.

Descripción de los dos trasteros.-

3º.- Redistribución de las cuotas de participación en los elementos comunes de todas las unidades de la Propiedad Horizontal del Edificio.

4º.- Venta a dos copropietarios de los dos trasteros desafectados

5.º Delegación de facultades

6º.- Ruegos y preguntas.

A la Junta asisten los siguientes propietarios:

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del [COMPLETAR] %.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del [COMPLETAR] %.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del [COMPLETAR] %.

D./Dña. [NOMBRE Y APELLIDOS], piso [COMPLETAR], con coeficiente de participación del [COMPLETAR] %.

D./Dña. [NOMBRE Y APELLIDOS], local n.º [NÚMERO], con coeficiente de participación del [COMPLETAR] %.

D./Dña. [NOMBRE Y APELLIDOS], del piso y con coeficiente de participación del [COMPLETAR] % [COMPLETAR] y D./Dña. [NOMBRE Y APELLIDOS], del piso [COMPLETAR] y con coeficiente de participación del [COMPLETAR] %, otorgaron apoderamiento para comparecer y votar en su nombre en esta Junta a D./Dña. [NOMBRE Y APELLIDOS], que los representa.

Se hace constar que D./Dña. [NOMBRE Y APELLIDOS], del piso [COMPLETAR] y coeficiente de participación del [COMPLETAR] %, no se encuentra al corriente del pago de las cuotas de la Comunidad, por adeudar las de los meses de [COMPLETAR], que ascienden a [IMPORTE] euros. Al no haber procedido antes de la reunión al pago, a la consignación judicial o notarial o a la impugnación judicial de las cuotas, su persona y cuota de participación no son computadas a efectos de alcanzar las mayorías legales.

Se hace constar, igualmente, que D./Dña. [NOMBRE Y APELLIDOS] ha procedido ha ponerse al día en el pago de cuotas de comunidad, razón por la cual podrá participar con voz y voto en las deliberaciones.

Preside la Junta el Presidente D./Dña. [NOMBRE Y APELLIDOS] y actúa como Secretario el Administrador D./Dña. [NOMBRE Y APELLIDOS]

Da comienzo la deliberación y se desarrolla la reunión de la siguiente manera:

1.º Lectura y aprobación del acta de la Junta anterior:

Se aprueba por todos los asistentes.

2.º Desafección de su condición de elementos comunes en el sótano del edificio dos zonas, atribuyéndoles el carácter de elementos privativos independientes con destino a trasteros, asignándoles la correspondiente cuota en los elementos comunes del edificio.

Los trasteros se describen de la siguiente manera:

- Trastero número [NÚMERO] en el sótano de la casa número de la [COMPLETAR]: Superficie [COMPLETAR] Linderos: Linda por frente entrando al mismo con zona común de paso, derecha entrando con subsuelo del propio edificio, izquierda con subsuelo del propio edificio, y fondo con subsuelo de la casa [COMPLETAR] Cuota de participación en elementos comunes, %.

- Trastero número [NÚMERO] en el sótano de la casa número de la [COMPLETAR]: Superficie [COMPLETAR] Linderos: Linda por frente entrando al mismo con zona común de paso, derecha entrando con cuarto de limpieza – elemento común del edificio- y subsuelo del edificio, izquierda con zona común de paso, y fondo subsuelo del edificio. Cuota de participación en elementos comunes, %.

Todos los asistentes votan favorablemente este acuerdo.

De conformidad con lo previsto en el artículo 17.8 de la LPH [NOTA DE REVISIÓN: Numeración anterior a la Ley 8/2013. Art. 17.8 LPH: los ausentes debidamente citados que no manifiesten su discrepancia en 30 días naturales computan como votos favorables. Fuente: LPH (Ley 49/1960), BOE-A-1960-10906, art. 17.8.] se ha enviado la información del citado acuerdo a los propietarios ausentes, mediante el procedimiento del artículo 9 de la misma ley, sin que, habiendo transcurrido 30 días desde la recepción de dicha información, hayan manifestado su discrepancia con el mismo, por lo que sus votos se computan como favorables y se tiene por aprobado el acuerdo por unanimidad.

3º.- Redistribución de las cuotas de participación en los elementos comunes de todas las unidades de la Propiedad Horizontal del Edificio

Como consecuencia de la asignación de cuotas de participación a los dos nuevos trasteros desafectados, se redistribuyen las cuotas de participación en los elementos comunes de todas las unidades de la Propiedad Horizontal de la siguiente manera:

Todos los asistentes votan favorablemente este acuerdo.

De conformidad con lo previsto en el artículo 17.8 de la LPH [NOTA DE REVISIÓN: Numeración anterior a la Ley 8/2013 (segunda mención). Fuente: LPH (Ley 49/1960), BOE-A-1960-10906, art. 17.8.] se ha enviado la información del citado acuerdo a los propietarios ausentes, mediante el procedimiento del artículo 9 de la misma ley, sin que, habiendo transcurrido 30 días desde la recepción de dicha información, hayan manifestado su discrepancia con el mismo, por lo que sus votos se computan como favorables y se tiene por aprobado el acuerdo por unanimidad.

4º.- Venta de los trasteros a dos copropietarios de los dos trasteros desafectados, el número [NÚMERO] al copropietario Don [COMPLETAR], y el número [NÚMERO] al también copropietario Don [COMPLETAR], por el precio respectivo de [IMPORTE] € y [IMPORTE] €, que será satisfecho, al contado a la firma de las escrituras de compra venta o confesado recibido con anterioridad, siendo todos los gastos de Notaría, Registro de la Propiedad e Impuestos de todas clases que se originen por las respectivas compra-ventas incluso el de Plus-Valía Municipal si fuere exigible por cuenta de los compradores.

Todos los asistentes votan favorablemente este acuerdo.

5.º Delegación de facultades. Se somete a votación facultar al Presidente de la Comunidad, Don [COMPLETAR], a fin de que, en ejecución de los acuerdos adoptados y transcritos, comparezca ante Notario al efecto de formalizar los correspondiente documentos públicos o privados con las demás condiciones y requisitos que fueren necesarios o convenientes, realizando cuantas gestiones o trámites fueren precisos, incluso escrituras públicas de rectificación o modificación hasta obtener la inscripción de los presentes acuerdos en el Registro de la Propiedad.

Se aprueba este acuerdo por unanimidad de los asistentes.

6º Ruegos y preguntas:

Algunos propietarios exponen sus quejas respecto a la calefacción. Varios radiadores no calientan bien. Se volverá a hablar con la empresa de mantenimiento del servicio de mantenimiento.

No habiendo más asuntos que tratar se da por terminada la reunión a las [Nº] horas, que se documenta en la presente acta que firman los Sres. Presidente y Secretario.

Firmado:

========================================================================
