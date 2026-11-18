---
name: partija-conjunta-extratestamentaria-protocolizar-galicia-565
description: "Redacta el escrito «Partija conjunta extratestamentaria para protocolizar (Galicia)» (formulario 565 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Partija conjunta extratestamentaria para protocolizar (Galicia)

> Formulario 0565 del plugin **Sucesiones** · revisado el 17-11-2026.

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

- [ ] LOCALIDAD
- [ ] NIF
- [ ] NÚMERO (4 veces)
- [ ] IMPORTE (12 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 53 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…y»; «…régimen legal de gananciales, vecinos de»; «…, respectivamente, de cuyo matrimonio»; «…, único contraído, tienen»; «…hijos llamados»; «…hijos llamados [COMPLETAR] y»; «…II. Inventario: a) Bienes gananciales de»; «…y»; «…o General de Concentración Parcelaria de»; «…dedicado a labradío y monte, al sitio de»; «…, de una superficie de»; «…de una superficie de [COMPLETAR] áreas y»; …

## Normas que cita el formulario

No cita artículos concretos. Si añades alguno, compruébalo con `buscar_articulo`.

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

### Formulario 0565 · Partija conjunta extratestamentaria para protocolizar (Galicia)

- Año del modelo: 2016
- Revisión 17-11-2026: 66 campos de relleno marcados en blanco; 6 huecos del original que se habían perdido sin marca, marcados (IMPORTE)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

y [COMPLETAR], mayores de edad, casados bajo el régimen legal de gananciales, vecinos de [COMPLETAR] con domicilio en [LOCALIDAD], de vecindad civil gallega y titulares de los DNI y NIF [NIF], respectivamente, de cuyo matrimonio [COMPLETAR], único contraído, tienen [COMPLETAR] hijos llamados [COMPLETAR] y [COMPLETAR], se proponen realizar la partición inter-vivos de sus bienes, lo que hacen por medio del presente cuaderno particional, a cuyo fin,

Dicen:

I. Que se proponen realizar la partición de sus bienes de forma conjunta y como de si un único patrimonio se tratara, utilizando para ello la facultad que les confieren los artículos 273 y siguientes de la Ley de Derecho Civil de Galicia, a cuyo fin comienzan inventariando sus bienes.

II. Inventario:

a) Bienes gananciales de [COMPLETAR] y [COMPLETAR].

1. Rústica. Finca número [NÚMERO] del Plano General de Concentración Parcelaria de [COMPLETAR], terreno dedicado a labradío y monte, al sitio de [COMPLETAR], de una superficie de [COMPLETAR] áreas y [COMPLETAR] centiáreas.

Linda: Norte, terreno excluido; Sur, finca [COMPLETAR]; Este, camino y finca [COMPLETAR]; y Oeste, terreno excluido y [COMPLETAR].

Inscripción. Registro de la Propiedad de [COMPLETAR], tomo [COMPLETAR], libro [COMPLETAR], folio [COMPLETAR], finca [COMPLETAR].

Referencia catastral. Tiene asignada referencia catastral número [NÚMERO], según resulta de la fotocopia que se adjunta a este documento.

Título. Acta de reorganización de concentración parcelaria, autorizada por el Notario de [COMPLETAR], el [COMPLETAR] de [COMPLETAR] de [COMPLETAR], número [NÚMERO] de protocolo.

Valor. euros.

Total valor de bienes gananciales: [IMPORTE] euros.

b) Bienes privativos de [COMPLETAR].

2. Sepulturas números [COMPLETAR] y [COMPLETAR] en el Cementerio de [COMPLETAR], municipio de [COMPLETAR].

Valor. euros.

Total valor de bienes privativos de [IMPORTE]: euros.

c) Bienes privativos de [COMPLETAR].

3. Urbana. vivienda número [NÚMERO], con una extensión superficial de [COMPLETAR] metros cuadrados, que consta de planta baja, con una edificación de planta rectangular, y que ocupa un solar de [COMPLETAR] metros cuadrados, con una construcción o trastero de [COMPLETAR] metros cuadrados y un terreno anejo dedicado a huerta.

Linda: Norte, con herederos de [COMPLETAR]; Sur, con parcela denominada [COMPLETAR]; Este, con camino [COMPLETAR]; y Oeste, con vivienda unifamiliar [COMPLETAR] y parcela de terreno en que se asienta.

Referencia catastral. Tiene asignada la referencia catastral [COMPLETAR], como resulta de la certificación catastral descriptiva y gráfica que se adjunta a este documento.

Valor. euros.

Total valor de bienes privativos de [IMPORTE]: euros.

Total valor de la herencia de [COMPLETAR] incluida su mitad de gananciales: [IMPORTE] euros.

Total valor de la herencia de [COMPLETAR] incluida su mitad de gananciales: [IMPORTE] euros.

Total valor bienes inventariados: [IMPORTE] euros.

III. Que han decidido distribuir sus bienes a cuyo fin forman los siguientes cupos o adjudicaciones:

a) Cupo numero uno para el heredero [COMPLETAR]:

Adjudican a este heredero las partidas números [COMPLETAR] cuya descripción es la que sigue:

Se valora este cupo en: [IMPORTE] euros; cantidad de la que [IMPORTE] euros corresponden a la herencia de [COMPLETAR], y el resto, esto es, [IMPORTE] euros, corresponden a la herencia de [COMPLETAR].

b) Cupo numero dos para el heredero [COMPLETAR]:

Adjudican a este heredero las partidas números [COMPLETAR] cuya descripción es la que sigue:

Se valora este cupo en: [IMPORTE] euros; cantidad de la que [IMPORTE] euros corresponden a la herencia de [COMPLETAR], y el resto, esto es, [IMPORTE] euros, corresponden a la herencia de [COMPLETAR].

IV. Disposiciones finales:

Primera. Cada una de las fincas adjudicadas se entiende con todos los bienes existentes en ellas, incluso el arbolado.

Segunda. El metálico existente en las cuentas abiertas por los otorgantes en bancos y/o cajas de ahorros, así como cualquier otro producto financiero, se distribuirán entre todos hijos de los otorgantes antes citados a partes iguales.

Tercera. Ambos cónyuges [COMPLETAR] se atribuyen con carácter recíproco el usufructo voluntario de viudedad, por lo que las adjudicaciones efectuadas en esta partición se entenderán en nuda propiedad hasta el fallecimiento del último de los cónyuges [COMPLETAR].

Cuarta. La presente partición respeta las legítimas. El valor de lo adjudicado a cada heredero se imputará en primer lugar a su legítima.

Quinta. La liquidación de la sociedad de gananciales en la medida que fuere necesario, se entenderá producida al fallecimiento de cualquiera de los cónyuges, mediante la adjudicación de una mitad indivisa de los bienes que tuvieran aquel carácter, al cónyuge sobreviviente y la mitad indivisa restante al heredero que resulte adjudicatario con arreglo a esta partición.

Así lo dicen y otorgan en el presente documento extendido en [COMPLETAR] folios de papel de copia simple, números [COMPLETAR] y los [COMPLETAR] siguientes en orden correlativo, que firman a continuación en prueba de conformidad.

En [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma	Firma

========================================================================
