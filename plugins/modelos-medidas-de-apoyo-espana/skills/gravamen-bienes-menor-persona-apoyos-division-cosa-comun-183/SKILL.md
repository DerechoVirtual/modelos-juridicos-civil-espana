---
name: gravamen-bienes-menor-persona-apoyos-division-cosa-comun-183
description: "Redacta el escrito «Gravamen de bienes de menor o persona con apoyos: división de cosa común» (formulario 183 de capacidad y medidas de apoyo, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Gravamen de bienes de menor o persona con apoyos: división de cosa común

> Formulario 0183 del plugin **Capacidad y medidas de apoyo** · revisado el 17-11-2026.

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

- [ ] SEDE (2 veces)
- [ ] NOMBRE Y APELLIDOS (7 veces)
- [ ] Nº DE COLEGIADO/A
- [ ] COLEGIO
- [ ] LOCALIDAD (4 veces)
- [ ] FECHA (2 veces)
- [ ] Nº
- [ ] AÑO (2 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] NÚMERO
- [ ] IMPORTE (2 veces)
- [ ] DESCRIBIR
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 13 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…: Hechos y consideraciones jurídicas: 1ª»; «…numeración del juzgado de procedencia).]»; «…, con funciones representativas. 2ª»; «…, con referencia catastral»; «…, según resulta de»; «…de la referida vivienda sus hermanos Don»; «…y Doña»; «…de»; «…, de la vivienda ubicada en 3ª»; «… determine su precio real de mercado. 4ª»; «…. 5ª»; «…ún las previsiones del art. 62.2 LJV. 6ª»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 66 LJV
- art. 62.2 LJV
- art. 62.1 LJV
- Ley 15/2015

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

### Formulario 0183 · Gravamen de bienes de menor o persona con apoyos: división de cosa común

- Año del modelo: 2021
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 37 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 1 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito promoviendo el expediente para obtener la autorización judicial para extinción de condominio de una persona con discapacidad con medidas de apoyo para el ejercicio de su capacidad jurídica.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de D./Dña. [NOMBRE Y APELLIDOS], actuando en calidad de curador de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño a este escrito, bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], colegiado/a nº [Nº DE COLEGIADO/A] del Ilustre Colegio de Abogados de [COLEGIO], con despacho abierto en [LOCALIDAD], como mejor proceda en derecho comparezco y DIGO:

Que por medio del presente escrito, y de conformidad con los arts. 61 y ss. de la Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), promuevo expediente en solicitud de autorización judicial de extinción de condominio existente sobre la vivienda sita en [LOCALIDAD], en base a los siguientes:

Hechos y consideraciones jurídicas:

1ª [COMPLETAR])

Con fecha [FECHA], la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. «De los de» es residuo de los varios juzgados de una plaza. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR] dictó sentencia en proceso sobre discapacidad nº [Nº]/[AÑO], en cuya parte dispositiva, entre otras decisiones, se adoptó la medida judicial de apoyo consistente en el nombramiento de mi representado como curador de D./Dña. [NOMBRE Y APELLIDOS], con funciones representativas.

2ª [COMPLETAR])

El sujeto a curatela, D./Dña. [NOMBRE Y APELLIDOS], es copropietario de la vivienda sita en [LOCALIDAD], con referencia catastral [COMPLETAR], según resulta de [COMPLETAR], y cuya descripción según datos registrales es la siguiente:

Junto al sujeto a curatela, son copropietarios de la referida vivienda sus hermanos Don [COMPLETAR] y Doña [COMPLETAR]

Se acompaña como documento nº [Nº DE DOCUMENTO] nota simple informativa de fecha [FECHA], expedida por el Registro de la Propiedad nº [NÚMERO] de [COMPLETAR], de la vivienda ubicada en

3ª [COMPLETAR])

Siendo la referida vivienda indivisible, con nula rentabilidad, venimos a solicitar autorización judicial para extinguir el condominio existente sobre la misma, mediante venta directa y con relevación de subasta pública bajo la condición de que el precio de venta de la totalidad de la finca sea igual o superior a la cantidad de [IMPORTE] euros, facultando al curador para otorgar la correspondiente escritura pública de compraventa de la que deberá dar cuenta junto con la aplicación de los fondos resultantes al tribunal ante el que se está solicitando ahora la autorización.

Se adjunta al presente escrito como documento nº [Nº DE DOCUMENTO] dictamen pericial emitido por el perito D./Dña. [NOMBRE Y APELLIDOS] sobre valoración del inmueble en el que tras examinar todas las circunstancias del inmueble se determine su precio real de mercado.

4ª [COMPLETAR])

Con la extinción del condominio existente sobre la vivienda, con nula rentabilidad en la actualidad, se busca rentabilizar esta propiedad incrementando la liquidez del patrimonio de la persona con discapacidad con objeto de [DESCRIBIR].

5ª [COMPLETAR])

Por ello, se insta el presente expediente contemplado en los arts. 61 y ss. LJV. A tal fin, se ha identificado el bien, se ha expuesto la utilidad y el motivo de la hipoteca proyectada, y la finalidad a la que debe aplicarse la suma que finalmente se obtenga con el crédito concedido. En este sentido, mi mandante se muestra dispuesto a aceptar cualquier tipo de control judicial que asegure tal destino, tal y como prevé el art. 66 LJV.

Ostenta legitimación para promover el presente expediente su curador al ser la persona que tiene atribuidas las medidas de apoyo a la persona con discapacidad a los fines de realizar el acto jurídico de que se trata, según las previsiones del art. 62.2 LJV.

6ª [COMPLETAR])

Que es competente la Sección Civil del Tribunal de Instancia al que me dirijo conforme al art. 62.1 LJV, en relación con lo dispuesto en el art. 85.1º LOPJ, al encontrarse en su partido judicial el domicilio de la persona con discapacidad sujeta a curatela, sito en

7ª [COMPLETAR])

Establece el art. 287.2º CCiv que "El curador que ejerza funciones de representación de la persona que precisa el apoyo necesita autorización judicial para los actos que determine la resolución y, en todo caso, para los siguientes: 2º) Enajenar o gravar bienes inmuebles, establecimientos mercantiles o industriales, bienes o derechos de especial significado personal o familiar, bienes muebles de extraordinario valor, objetos preciosos y valores mobiliarios no cotizados en mercados oficiales de la persona con medidas de apoyo, dar inmuebles en arrendamiento por término inicial que exceda de seis años, o celebrar contratos o realizar actos que tengan carácter dispositivo y sean susceptibles de inscripción. Se exceptúa la venta del derecho de suscripción preferente de acciones. La enajenación de los bienes mencionados en este párrafo se realizará mediante venta directa salvo que el Tribunal considere que es necesaria la enajenación en subasta judicial para mejor y plena garantía de los derechos e intereses de su titular.".

Por todo lo expuesto, al amparo del art. 287.2º CCiv, y de los arts. 61 y ss. LJV,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que lo acompañan, lo admita y en su virtud tenga por formulado expediente de jurisdicción voluntaria y con intervención del Ministerio Fiscal, tras los trámites legales dicte la oportuna resolución por la que autorice la extinción del condominio existente sobre la vivienda sita en [LOCALIDAD], mediante venta directa y con relevación de subasta pública bajo la condición de que el precio de venta de la totalidad de la finca sea igual o superior a la cantidad de [IMPORTE] euros, facultando al curador para otorgar la correspondiente escritura pública de compraventa de la que deberá dar cuenta junto con la aplicación de los fondos resultantes al tribunal ante el que se está solicitando ahora la autorización.

Por ser de Justicia de hacerse en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma del Abogado

Firma del Procurador
