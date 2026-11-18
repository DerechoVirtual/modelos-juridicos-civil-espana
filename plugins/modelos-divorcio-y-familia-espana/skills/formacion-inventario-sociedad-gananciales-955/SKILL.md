---
name: formacion-inventario-sociedad-gananciales-955
description: "Redacta el escrito «Formación de inventario de la sociedad de gananciales» (formulario 955 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Formación de inventario de la sociedad de gananciales

> Formulario 0955 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (6 veces)
- [ ] FECHA
- [ ] NÚMERO (6 veces)
- [ ] IMPORTE (7 veces)
- [ ] Nº (6 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…tud, como documento 0 o 1). Con fecha de»; «…mi poderdante presentó demanda de»; «…O DE BIENES ILEGALMENTE REALIZADOS por D»; «…. I.3.º CRÉDITOS DE LA SOCIEDAD CONTRA D»; «…). II.3.º CRÉDITO DEL CÓNYUGE Dña»; «…rtificación bancaria (libreta, extracto,»; «…)»; «… acompaña reseñada como doc. n.º 1). 2.º»; «…mpraventa u otros títulos de adquisición»

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 808 de la LEC
- art. 809 de la LEC

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

### Formulario 0955 · Formación de inventario de la sociedad de gananciales

- Año del modelo: 2013
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 31 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 6 huecos del original que se habían perdido sin marca, marcados (Nº)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales, en nombre y representación deD./Dña [NOMBRE Y APELLIDOS], según acredito mediante poder notarial que acompaño, rogando me sea devuelto una vez testimoniado en autos, ante el Tribunal comparezco bajo la dirección del Letrado

D./Dña. [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO:

Que en nombre de mi representado solicito mediante el presente escrito la FORMACIÓN DE INVENTARIO de la sociedad legal de gananciales de mi mandante y su cónyuge D./Dña [NOMBRE Y APELLIDOS], solicitud que baso en los siguientes

ANTECEDENTES DE HECHO

(En su caso, si en la circunscripción se hace presentación telemática)

Se presenta listado de documentos que acompañan a la solicitud, como documento 0 o 1).

Con fecha de [COMPLETAR] mi poderdante presentó demanda de [COMPLETAR] (separación, divorcio, nulidad) frente a su esposo D./Dña [NOMBRE Y APELLIDOS]

Dicha demanda fue admitida mediante resolución de fecha [FECHA] (en su caso), habiéndose dictado sentencia cuya copia acompaño como documento n.º [NÚMERO]

Mi mandante pretende la formación judicial de inventario de su sociedad económica conyugal de gananciales.

A los hechos antecedentes son de aplicación los siguientes

PRESUPUESTOS Y FUNDAMENTOS JURÍDICOS

Art. 807 de la LEC: COMPETENCIA: Es competente para conocer del procedimiento de liquidación el Tribunal de Instancia que esté conociendo o haya conocido del proceso de nulidad, separación o divorcio.

Se ampara esta solicitud en lo dispuesto en el art. 808 de la LEC.

Se tramitará esta solicitud por el cauce previsto en el art. 809 de la LEC, con citación de las partes por el Letrado de la Administración de Justicia para formación de inventario.

A los efectos previstos en el párrafo segundo del art. 808 de la LEC formulo la siguiente

PROPUESTA DE INVENTARIO:

I. ACTIVO:

1.º BIENES GANANCIALES EXISTENTES A ESTA FECHA: EFECTIVO Y DEPÓSITOS BANCARIOS:

 Valor [IMPORTE] euros (Docs. n.º [Nº]).

MUEBLES:

— Valor [IMPORTE] euros (Docs. n.º [NÚMERO]). INMUEBLES:

— Valor [IMPORTE] euros (Docs. n.º [NÚMERO]).

2.º IMPORTE ACTUALIZADO DE BIENES ILEGALMENTE REALIZADOS por D [COMPLETAR] Y NO RECUPERADOS:

— Valor [IMPORTE] euros (Docs. n.º [Nº]).

I.3.º CRÉDITOS DE LA SOCIEDAD CONTRA D [COMPLETAR]:

— Valor [IMPORTE] euros (Docs. n.º [Nº]).

II. PASIVO:

1.º DEUDAS CON CARGO A LA SOCIEDAD LEGAL DE GANANCIALES:

 Valor [IMPORTE] euros (Docs. n.º [NÚMERO]).

2.º IMPORTE ACTUALIZADO DE BIENES PRIVATIVOS GASTADOS EN FAVOR DE LA SOCIEDAD:

— Valor [IMPORTE] euros (Docs. n.º [NÚMERO]).

II.3.º CRÉDITO DEL CÓNYUGE Dña [COMPLETAR] CONTRA LA SOCIEDAD POR PAGO DE DEUDAS DE LA SOCIEDAD:

— Valor euros (Docs. n.º [Nº]).

RESUMEN:

IMPORTE DEL ACTIVO.— euros (Docs. n.º [Nº]).

IMPORTE DEL PASIVO.— euros (Docs. n.º [Nº]).

VALOR DEL INVENTARIO (DIFERENCIA).— euros (Docs. n.º [NÚMERO]).

En cumplimiento de lo dispuesto en el párrafo segundo del apartado 2.º del art. 808 de la LEC, acompaño a esta solicitud los siguientes documentos que justifican la inclusión de las partidas detalladas en la propuesta de inventario antecedente:

1.ºCertificación bancaria (libreta, extracto, [COMPLETAR]) [COMPLETAR] (Se acompaña reseñada como doc. n.º 1).

2.º [COMPLETAR] (acompañar, debidamente numerados los restantes documentos como facturas, escrituras de compraventa u otros títulos de adquisición [COMPLETAR] que justifiquen cada partida del activo y pasivo).

Desde este mismo momento, y para que sean acordadas en momento procesal oportuno, dejo solicitada la adopción de las siguientes medidas de administración (o disposición) de los bienes inventariados:

 (detallar las que interesen al derecho de la parte).

Por todo lo expuesto,

SUPLICO AL TRIBUNAL: Tenga por presentado este escrito y documentos adjuntos con sus copias preceptivas, se sirva admitir todo ello, teniendo por solicitada la formación de inventario de la sociedad económica conyugal de gananciales de mi poderdante y su cónyuge D./Dña [NOMBRE Y APELLIDOS], acordando la citación de los cónyuges por el Letrado de la Administración de Justicia para formación del inventario de la comunidad matrimonial, aprobando la propuesta de inventario contenida en el cuerpo del presente escrito y adoptando las medidas de administración o disposición que se dejan solicitadas si la parte contraria no compareciere o mostrare su conformidad con las mismas, o dando a esta solicitud el impulso procedimental pertinente si se formulare oposición a la propuesta presentada.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
