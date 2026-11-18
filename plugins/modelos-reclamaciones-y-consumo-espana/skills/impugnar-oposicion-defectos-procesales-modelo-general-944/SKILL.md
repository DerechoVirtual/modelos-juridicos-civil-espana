---
name: impugnar-oposicion-defectos-procesales-modelo-general-944
description: "Redacta el escrito «Impugnar la oposición por defectos procesales: modelo general» (formulario 944 de contratos, consumo y responsabilidad civil, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Impugnar la oposición por defectos procesales: modelo general

> Formulario 0944 del plugin **Contratos, consumo y responsabilidad civil** · revisado el 17-11-2026.

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

- [ ] Nº DE PROCEDIMIENTO
- [ ] AÑO (2 veces)
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (4 veces)
- [ ] Nº
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…, PLAZA N.º»; «…roceda en derecho DIGO: Que con fecha de»; «…uientes HECHOS En el presente caso: • El»; «…presentación que se le atribuye ya que •»; «…El laudo arbitral no es auténtico porque»; «…correlativo. Legitimación Opciones: • el»; «…e o ejecutado) no está legitimado porque»; «…ce el ejecutado la causa de oposición de»; «…prevista en el art»; «…entendiendo esta parte que el defecto es»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 560 de la LEC
- artículo 559.1 de la LEC
- art. 559 LEC

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

### Formulario 0944 · Impugnar la oposición por defectos procesales: modelo general

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 16 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (Nº, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio ejecutivo n.º [Nº DE PROCEDIMIENTO]/[AÑO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, interviniendo en nombre de D./Dña [NOMBRE Y APELLIDOS], en virtud de la representación que consta debidamente acreditada en los autos referenciados, ante el Tribunal comparezco y como mejor proceda en derecho DIGO:

Que con fecha de [COMPLETAR] me ha sido notificado el escrito de oposición a la ejecución formulado por la representación procesal del ejecutado D./Dña [NOMBRE Y APELLIDOS], concediéndome plazo legal de cinco días para formalizar su impugnación. Evacuando dicho trámite, mediante el presente escrito impugno el escrito de oposición formulado de contrario por motivos de forma, señalando los siguientes

HECHOS

En el presente caso:

• El [COMPLETAR] (ejecutado o ejecutante) carece del carácter o representación que se le atribuye ya que

• [COMPLETAR] (la sentencia o laudo arbitral) que se pretende ejecutar no es ejecutable porque es meramente declarativo y carece de pronunciamiento condenatorio.

• La cuantía es inferior a 300 euros.

• El laudo arbitral no es auténtico porque [COMPLETAR]

 (rebatir los restantes hechos del correlativo).

A los hechos antecedentes resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Competencia

Conforme con el correlativo.

Legitimación

Opciones:

• el [COMPLETAR] (ejecutante o ejecutado) no está legitimado porque [COMPLETAR]

• Conforme con el correlativo/tiva.

Requisitos procesales y trámite

Se reproducen los del escrito de demanda ejecutiva

Se formula este escrito de impugnación dentro del plazo legal de cinco días desde el traslado de la oposición previsto en el art. 560 de la LEC.

Fondo

Aduce el ejecutado la causa de oposición de [COMPLETAR] prevista en el art [COMPLETAR] de la LEC. En el presente asunto concurre, sin embargo, la circunstancia de oposición por defecto procesal descrita en el n.º [Nº] del artículo 559.1 de la LEC; razón por la cual deberá proceder el Tribunal a resolver sobre esta cuestión. Para ello se seguirá el cauce previsto en el apartado 2.º del citado art. 559 LEC entendiendo esta parte que el defecto es [COMPLETAR] (subsanable o insubsanable).

Costas

En aplicación del art. 559.2, párr. 2.º de la LEC, al rechazarse la oposición, las costas deberán ser impuestas al ejecutado.

Por lo expuesto

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito (y en su caso, documentos que lo acompañan), se sirva admitirlo y, en su virtud tenga por impugnado por defectos procesales en tiempo y forma el escrito de oposición presentado por la representación procesal del ejecutado D./Dña [NOMBRE Y APELLIDOS], dando traslado a la otra parte, para en definitiva dictar auto mediante el que se declare procedente que la ejecución siga adelante, y acordando, en todo caso, hacer trance y remate de los bienes embargados y pagar con el importe obtenido al demandante el principal reclamado, intereses, gastos y las costas causa- das y que se causen hasta el completo pago que expresamente se impondrán al ejecutado.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

(En su caso)

OTROSÍ DIGO: Que la presente impugnación por motivos procesales se realiza sin perjuicio de la que pueda proceder por motivos de fondo razón por la cual interesamos que, si se desestima aquella, se nos dé traslado para formular ésta.

NUEVAMENTE SUPLICO: Que se atienda a la presente solicitud por ser justicia que pido en mismo lugar y fecha

========================================================================
