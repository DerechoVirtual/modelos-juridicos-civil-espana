---
name: contestar-oralmente-desahucio-impago-rentas-1262
description: "Redacta el escrito «Contestar oralmente en el desahucio por impago de rentas» (formulario 1262 de arrendamientos y desahucio, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Contestar oralmente en el desahucio por impago de rentas

> Formulario 1262 del plugin **Arrendamientos y desahucio** · revisado el 17-11-2026.

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

- [ ] NÚMERO (4 veces)
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS
- [ ] IMPORTE (3 veces)
- [ ] FECHA
- [ ] Otros 4 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…os a desarrollar a continuación. Previo:»; «…da. El importe de la renta actual era de»; «…según el cual»

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA OPCIÓN Y REDACTARLA: Compensación obras / Acuerdo por disminución ingresos arrendatario — el texto de cada opción no venía en el formulario original
- ELEGIR UNA OPCIÓN Y REDACTARLA: Conformidad / Disconformidad / Otros — el texto de cada opción no venía en el formulario original

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 1555.1 del Código Civil

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

### Formulario 1262 · Contestar oralmente en el desahucio por impago de rentas

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 2 bloques de opciones sin texto dejados en blanco con sus rótulos; 14 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio de desahucio n.º [NÚMERO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

Con la venia, para interesar la desestimación de la demanda interpuesta por D./Dña. [NOMBRE Y APELLIDOS] contra nuestro patrocinado en atención a las razones que expusimos en nuestro escrito de oposición y pasamos a desarrollar a continuación.

Previo: [COMPLETAR]) En aplicación del artículo 439.3 de la Ley de Enjuiciamiento Civil debería haberse inadmitido la demanda por no haber indicado el actor si cabe o no la enervación de la acción. Esta causa de inadmisión debe en este momento transformarse en causa de desestimación de la demanda.

En relación con los hechos:

1.º El actor afirma ser propietario del inmueble arrendado:

pero no acredita la titularidad sobre la finca o la cualidad que le legitima como arrendador, razón por lo que existe falta de legitimación «ad causam».

2.º Sobre el contrato de arrendamiento y la renta actual:

En efecto las partes suscribieron el contrato que se presenta como documento n.º [NÚMERO] de la demanda.

El importe de la renta actual era de [COMPLETAR], pero tras las actualizaciones oportunas su importe actual debe ser de [IMPORTE] € y no de [IMPORTE] € como se afirma de contrario. Adjunto como documento n.º [NÚMERO] certificado del INE en la que se recogen las sucesivas actualizaciones a aplicar. Según los índices que aporto en realidad en este momento debe abonarse al mes una renta de [IMPORTE] €, que es lo que ha venido haciendo esta parte, según se acredita con justificantes de ingreso bancario que acompaño como documentos n.º [NÚMERO].

3.º Sobre la deuda que se dice existente:

Olvida la parte demandante hacer referencia a un acuerdo entre las partes de fecha [FECHA] según el cual [COMPLETAR]:

[ELEGIR UNA OPCIÓN Y REDACTARLA: Compensación obras / Acuerdo por disminución ingresos arrendatario — el texto de cada opción no venía en el formulario original]

En cuanto a los fundamentos jurídicos

Sobre los de carácter procesal (Opciones):

[ELEGIR UNA OPCIÓN Y REDACTARLA: Conformidad / Disconformidad / Otros — el texto de cada opción no venía en el formulario original]

Sobre el fondo del asunto:

El artículo 1555.1 del Código Civil afirma que el arrendatario está obligado a pagar el precio del arrendamiento en los términos convenidos. En este caso, aunque en el contrato de arrendamiento se pactó un precio y una forma de pago, acuerdos posteriores han reformado esas cláusulas y, en este momento, la forma de liquidar la deuda y el importe eran otros, según se ha explicado.

El artículo 17 de la ley de Arrendamientos Urbanos dice que la renta será la que estipulen las partes, pero a este acuerdo se puede llegar no solo en el contrato inicial, puesto que caben modificaciones del mismo.

Las costas deberán imponerse a la parte actora al desestimar sus pretensiones.

Concluyendo, interesamos la desestimación de la demanda con expresa imposición de costas a la parte actora y solicitamos el recibimiento del pleito a prueba.

========================================================================
