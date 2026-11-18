---
name: alegaciones-solicitante-sobre-falta-competencia-objetiva-770
description: "Redacta el escrito «Alegaciones del solicitante sobre la falta de competencia objetiva del LAJ» (formulario 770 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Alegaciones del solicitante sobre la falta de competencia objetiva del LAJ

> Formulario 0770 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (2 veces)
- [ ] FECHA (3 veces)
- [ ] Nº DE EXPEDIENTE
- [ ] LUGAR
- [ ] Otros 3 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…ria de Asamblea General de la Asociación»; «…/»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 16.2 Ley 15/2015
- art. 16.2 LJV
- art. 86 bis.1 LOPJ
- art. 119.4 LJV
- Ley Orgánica 1/2002

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

### Formulario 0770 · Alegaciones del solicitante sobre la falta de competencia objetiva del LAJ

- Año del modelo: 2015
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 10 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Escrito de alegaciones en relación al traslado recibido sobre la posible falta de competencia objetiva del Letrado de la Administración de Justicia.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE LO MERCANTIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a y de D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco y como mejor en Derecho proceda, DIGO:

Que por medio del presente escrito, y al amparo de lo dispuesto en el art. 16.2 Ley 15/2015, de 2 de julio, de la Jurisdicción Voluntaria (en lo sucesivo, LJV), formulo ALEGACIONES en relación al traslado recibido sobre posible falta de competencia objetiva del Letrado de la Administración de Justicia, en base a las siguientes

ALEGACIONES

PRIMERA.- Que el pasado [FECHA], insté ante el órgano judicial al cual tengo el honor de dirigirme, la convocatoria de Asamblea General de la Asociación [COMPLETAR], con un orden del día concretado en cuatro puntos. Mediante diligencia de ordenación de fecha [FECHA], se incoó el presente expediente con nº [Nº DE EXPEDIENTE] / [COMPLETAR], y se me dio traslado, al igual que al Ministerio Fiscal, para que realizáramos alegaciones en relación a una posible falta de competencia objetiva del Letrado de la Administración de Justicia del Tribunal de lo mercantil que debe resolver el presente expediente, de conformidad con lo dispuesto en el art. 16.2 LJV.

SEGUNDO.- En este sentido, y tal y como se hacía constar en la solicitud inicial, el único procedimiento específico, no contencioso, establecido en nuestra legislación para suplir la falta de convocatoria de junta o asamblea, cuando no se convoca a pesar de haberse solicitado en forma, es el previsto en los arts. 117 y ss. LJV.

Así, los arts. 11.3 y 12.b) de la Ley Orgánica 1/2002, de 22 de marzo, reguladora del Derecho de Asociación, determinan una reunión convocatoria de la Asamblea General anual, así como la celebración con carácter extraordinaria cuando lo soliciten un número de asociados en cantidad no inferior al 10%. Habiéndose desatendido una petición de un 38% de los asociados para una convocatoria extraordinaria, se acude al auxilio judicial para la instar la misma, de manera similar a lo previsto en el art. 169 de la Ley de Sociedades de Capital, al carecer la legislación sobre asociaciones de previsión específica al respecto.

TERCERO.- En consecuencia, procede la puesta en marcha de este expediente de jurisdicción voluntaria para cuya resolución es competente el Letrado de la Administración de Justicia de la Sección de lo Mercantil del TI, en virtud de lo dispuesto en los arts. 118.1 y 119.5 de la Ley de Jurisdicción Voluntaria; con encaje en la competencia específica prevista para dichos órganos judiciales en el art. 86 bis.1 LOPJ.

Procede, en consecuencia, continuar con los trámites legales, de manera que, a partir de lo prevenido en el art. 119.4 de la Ley de Jurisdicción Voluntaria, el Letrado de la Administración de Justicia convoque la comparecencia prevista en tal precepto, con citación del órgano de gobierno de la asociación referida.

Por lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito y los documentos que se acompañan, y por deducidas alegaciones en relación a la competencia objetiva del Letrado de la Administración de Justicia del órgano judicial al cual tengo el honor de dirigirme, de conformidad con el art. 16.2 LJV; se resuelva continuar con el expediente, convocando la comparecencia prevista en el art. 119.4 LJV.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

========================================================================
