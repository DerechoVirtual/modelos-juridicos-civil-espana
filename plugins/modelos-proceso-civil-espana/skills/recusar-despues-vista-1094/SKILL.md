---
name: recusar-despues-vista-1094
description: "Redacta el escrito «Recusar después de la vista» (formulario 1094 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Recusar después de la vista

> Formulario 1094 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] SEDE (3 veces)
- [ ] NOMBRE Y APELLIDOS (9 veces)
- [ ] DESCRIBIR (2 veces)
- [ ] ÓRGANO
- [ ] NÚMERO (2 veces)
- [ ] FECHA
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 9 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Juicio»; «…, PLAZA N.º»; «…roceda en Derecho DIGO: Que con fecha de»; «…numeración del juzgado de procedencia).]»; «…ón en los siguientes HECHOS Con fecha de»; «…so en causa de recusación legal debido a»; «…otivo). Concurre la circunstancia de que»; «…concretamente la prevista en el apartado»; «…ontra el Sr. Magistrado-Juez Ilmo. Sr./a»

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 191 de la LEC
- art. 107 de la LEC

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

### Formulario 1094 · Recusar después de la vista

- Año del modelo: 2013
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 1 puntualizaciones normativas añadidas en el texto; 28 campos de relleno marcados en blanco; 1 huecos del original que se habían perdido sin marca, marcados (Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Juicio [COMPLETAR] n.º [Nº DE PROCEDIMIENTO]/[AÑO]

A LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR]

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, interviniendo en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS] según tengo acreditado en el procedimiento referenciado ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que con fecha de [COMPLETAR] se celebró la vista sobre [DESCRIBIR] que venía acordada en la tramitación del presente proceso. Dentro de los tres días hábiles siguiente a la celebración de dicha vista y mediante el presente escrito promuevo incidente de RECUSACIÓN del Magistrado-Juez Ilmo, Sr./Sra. D./Dña. [NOMBRE Y APELLIDOS], que intervino en la mencionada vista en sustitución del titular de la Sección Civil del Tribunal de Instancia de [SEDE], plaza n.º [NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).] [COMPLETAR], a quien ha correspondido en turno de reparto el conocimiento de dicha demanda. Baso la recusación en los siguientes

HECHOS

Con fecha de [COMPLETAR] se celebró la vista sobre [DESCRIBIR] que venía acordada, en la que intervino el Magistrado-Juez Ilmo. Sr./Sra. D./Dña. [NOMBRE Y APELLIDOS], en sustitución del titular (puede darse el caso de que la sustitución obedezca a toma de posesión de nuevo titular, en cuyo caso habría que estar a las normas generales sobre recusación) de este Tribunal.

Esta parte no ha podido tener conocimiento con anterioridad a dicho trámite de que el Magistrado-Juez contra el que se promueve esta recusación aparece incurso en causa de recusación legal debido a [COMPLETAR] (desarrollar motivo).

Concurre la circunstancia de que [COMPLETAR] (detallar grado de parentesco entre el Magistrado-Juez titular del Tribunal y el litigante contrario, relación tutelar, anterior condición de defensor de alguna de las partes, la existencia de denuncia previa, la causa de interés en el resultado del pleito, amistad íntima o enemistad manifiesta o cualesquiera otra causa legal en que se funde la recusación). Acredito estos extremos mediante [ÓRGANO], que acompaño reseñado como documento n.º [NÚMERO] (debe acompañarse un “principio de prueba” sobre la causa de recusación).

El Procurador firmante tiene conferidas, entre las que constan en su escritura de apoderamiento, facultades especiales para recusar Jueces. Firman este escrito también el Letrado D./Dña [NOMBRE Y APELLIDOS] y mi poderdante D./Dña. [NOMBRE Y APELLIDOS]

A los hechos antecedentes resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Legitimación

Art. 101 de la LEC: En los asuntos civiles podrán recusar únicamente las partes y el Ministerio Fiscal en aquellos asuntos en que deba o pueda intervenir.

El art. 218 de la Ley Orgánica del Poder Judicial sienta idéntico principio.

Causas de recusación

Arts. 219 y 220 de la Ley Orgánica del Poder Judicial. Son causas de recusación: (detallar la que proceda).

Trámite

El art. 191 de la LEC establece que en caso de cambio de Juez, y cuando se hubiere celebrado la vista por no haber mediado recusación, podrá ser recusado dicho Juez dentro de los tres días siguientes a la celebración de la vista, admitiéndose únicamente las causas de recusación que no hubieran podido conocerse antes de la vista, como ocurre en el presente supuesto.

Se señala expresamente causa de recusación, concretamente la prevista en el apartado [COMPLETAR] del art. (detallar), y se acompaña principio de prueba sobre la concurrencia de dicha prueba, en cumplimiento de lo dispuesto en el inciso 2. apdo. 2.º del art. 107 de la LEC.

Firman conmigo este escrito, también en cumplimiento de lo dispuesto en el art. 107.2.2.º de la LEC, el Letrado D./Dña. [NOMBRE Y APELLIDOS], que suscribió la demanda, y mi poderdante D./Dña. [NOMBRE Y APELLIDOS]

Deberá instruir el correspondiente expediente de recusación un Magistrado de la Audiencia Provincial de esta ciudad (art. 108.5.º de la LEC)

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito, documentos y las copias preceptivas de todo ello que se acompañan, se sirva admitirlo, admitiendo a trámite la recusación propuesta contra el Sr. Magistrado-Juez Ilmo. Sr./a [COMPLETAR] del Tribunal de Instancia de [SEDE], plaza n.º [NÚMERO] y dar traslado a las partes de la causa invocada para la presente recusación, para que puedan adherirse u oponerse, y, evacuado que sea el trámite, impulsar la pieza de recusación con el traslado del escrito y documentos de recusación al instructor que proceda, para que en definitiva por el Tribunal competente se resuelva lo siguiente:

1.º Si el recusado estimare como procedente la causa de recusación invocada, dar, sin más trámite, por recusado al Sr. Juez Ilmo. Sr./a D./Dña. [NOMBRE Y APELLIDOS] que intervino en la vista celebrada el día [FECHA], acordando dejar sin efecto la vista celebrada y señalando fecha en el día más próximo posible para su nueva celebración y entregando los autos a quien deba continuar su tramitación, o

2.º Subsidiariamente, en caso de rechazarse por el juez la causa de recusación alegada, y tramitada que sea la instrucción conforme a legal procedimiento y con audiencia previa del Ministerio Fiscal, dictar auto estimando la recusación y acordando dejar sin efecto la vista practicada y señalando fecha en el día más próximo posible para su nueva celebración.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

Firma y nombre del Abogado Firma y nombre del poderdante Firma y nombre del Procurador

========================================================================
