---
name: ejecucion-tasacion-costas-contra-herencia-yacente-1466
description: "Redacta el escrito «Ejecución de tasación de costas contra la herencia yacente» (formulario 1466 de sucesiones, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Ejecución de tasación de costas contra la herencia yacente

> Formulario 1466 del plugin **Sucesiones** · revisado el 17-11-2026.

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

- [ ] NÚMERO
- [ ] SEDE
- [ ] FECHA (4 veces)
- [ ] NOMBRE Y APELLIDOS
- [ ] IMPORTE (3 veces)
- [ ] Nº DE DOCUMENTO
- [ ] Nº
- [ ] LOCALIDAD
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…iendo firme. (Se acompaña como documento»; «…se ha producido el fallecimiento de D»; «…Tribunal de Instancia, Sección Civil, de»; «… caso, ignorados herederos– del deudor D»; «… 1. Gerencia Territorial del Catastro de»; «… Territorial de la Agencia Tributaria de»; «…3. Registro de la Propiedad núm. [Nº] de»; «…5. Caja de Ahorros Provincial de»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 6.1.4 de la LEC
- artículo 548 de la LEC
- art. 5.3 LO 1/2025
- artículo 242.1 de la LEC
- artículo 590 LEC

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

### Formulario 1466 · Ejecución de tasación de costas contra la herencia yacente

- Año del modelo: 2014
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 20 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (FECHA, NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Encabezamiento
HECHOS
FUNDAMENTOS DE DERECHO
Suplico
Otrosí digo
Otrosí digo II
Adopción de medidas
Firmas

Formulario revisado conforme a la LO 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia

Proceso número [NÚMERO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

HECHOS

Que en fecha [FECHA] se dictó por parte del Tribunal resolución aprobando la tasación de costas que condenaba a D. [NOMBRE Y APELLIDOS] al pago de [IMPORTE] euros en concepto de costas, la cual no ha fue impugnada por ninguna de las partes, siendo firme.

(Se acompaña como documento [COMPLETAR] testimonio de la tasación de costas practicada en fecha [FECHA] y de la resolución de fecha [FECHA]).

Tras la aprobación de la tasación de costas, en fecha [FECHA] se ha producido el fallecimiento de D [COMPLETAR], según se acredita por certificado de defunción que se acompañaba como documento número [Nº DE DOCUMENTO], por lo que esta parte se ve en la obligación de dirigir la reclamación contra la herencia yacente del finado, al ignorar esta parte la posible identidad o existencia de herederos, siendo reiterada la interpretación de los Tribunales en cuanto a la posibilidad de que la herencia yacente pueda ser parte en el procedimiento, de conformidad a lo que dispone el art. 6.1.4 de la LEC, acreditándose por esta parte el fallecimiento del deudor al aportarse acreditación documental y designándose, a efectos de notificaciones y demás actos de comunicación, los domicilios que constan a esta parte donde viven sus familiares más cercanos –hijos-, quienes lógicamente parecen llamados a la herencia del finado.

Que habiendo transcurrido el plazo prevenido en el artículo 548 de la LEC sin que se haya hecho efectiva la deuda por la parte condenada al pago ni por su herencia yacente o herederos, es por lo que se interesa su ejecución.

FUNDAMENTOS DE DERECHO

Competencia

Artículo 545.1 LEC. La competencia es del Tribunal de Instancia, Sección Civil, de [COMPLETAR] ante el cual se formula esta demanda, por ser el que conoció del asunto en primera instancia.

Procedimiento

Artículo 548, procediéndose a despachar ejecución de la sentencia dentro de los veinte días posteriores a aquél en que la condena haya sido notificada al ejecutado.

Artículo 549 LEC en relación con el que debe ser el contenido de la demanda ejecutiva.

Artículos 551 a 554 LEC en relación al despacho de ejecución.

Artículo 517 LEC, en relación con los artículos 571 y ss. para la ejecución dineraria.

Cumplimiento de los requisitos de procedibilidad

Conforme a lo dispuesto en el art. 5.3 LO 1/2025, la presente demanda ejecutiva no está sujeta al requisito de MASC.

Título ejecutivo

Artículo 517.2.1 y 9 en relación con el artículo 242.1 de la LEC.

Costas

Artículo 539.2 LEC.

Por todo ello,

SUPLICO AL TRIBUNAL: Que teniendo por presentado este escrito con los documentos que lo acompañan y sus copias, se acuerde, sin necesidad de previo requerimiento al deudor, se dicte auto conteniendo la orden general de ejecución y despachando la misma contra la HERENCIA YACENTE –o, en su caso, ignorados herederos– del deudor D [COMPLETAR], en el que conforme al artículo 551.2.3º LEC fije la cantidad reclamada conforme a lo solicitado en la cantidad de [IMPORTE] euros en concepto de principal, más la cantidad de [IMPORTE] euros en concepto de intereses, gastos y costas.

OTROSÍ DIGO: Que, una vez dictado el auto general de ejecución y de conformidad con el art. 551.3.1º de la LEC, se solicita que por el Letrado de la Administración de Justicia responsable de la misma se dicte decreto procediéndose al embargo, sin previo requerimiento de pago del ejecutado por la cantidad indicada, de los siguientes bienes que se estiman suficientes para cubrir las indicadas responsabilidades en su totalidad:

Por lo que, SUPLICO que se dicte decreto en el que se contengan las medidas que dejo interesadas.

OTROSÍ DIGO II: Que desconociendo esta parte bienes que puedan ser objeto de embargo por parte de este Tribunal, al amparo de lo dispuesto en el artículo 590 LEC, esta parte solicita que, una vez dictado el auto general de ejecución y de conformidad con el art. 551.3.2º de la LEC, el Tribunal proceda a dirigirse a los efectos de determinación de la relación de bienes muebles e inmuebles, así como depósitos o imposiciones a plazo fijo que el ejecutado pueda tener a su nombre a los siguientes organismos:

1. Gerencia Territorial del Catastro de [COMPLETAR]

2. Delegación Territorial de la Agencia Tributaria de [COMPLETAR]

3. Registro de la Propiedad núm. [Nº] de [COMPLETAR]

4. Jefatura Provincial de Tráfico de [LOCALIDAD]

5. Caja de Ahorros Provincial de [COMPLETAR]

Por lo que, SUPLICO que se dicte decreto procediéndose a adoptar las medidas de localización y averiguación de bienes solicitadas.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma Abogado y Procurador

========================================================================
