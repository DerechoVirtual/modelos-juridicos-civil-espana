---
name: recusar-peritos-modelo-general-868
description: "Redacta el escrito «Recusar a peritos: modelo general» (formulario 868 de escritos procesales civiles, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Recusar a peritos: modelo general

> Formulario 0868 del plugin **Escritos procesales civiles** · revisado el 17-11-2026.

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
- [ ] LOCALIDAD
- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (5 veces)
- [ ] NÚMERO (2 veces)
- [ ] FECHA (2 veces)
- [ ] DESCRIBIR
- [ ] ÓRGANO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] Otros 8 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…reforma procesal de la LO 1/2025. Juicio»; «…O. SR. (MAGISTRADO PONENTE DE LA SECCIÓN»; «…, PLAZA N.º»; «…itada, comparezco en los autos de Juicio»; «…e ha acordado el nombramiento del Perito»; «…tificación. Concurre la circunstancia de»; «…cia de que el Perito nombrado por sorteo»; «…la recusación propuesta contra el Perito»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 125 de la LEC
- art. 125.2 de la LEC
- art. 125.1 de la LEC

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

### Formulario 0868 · Recusar a peritos: modelo general

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 21 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS, Nº DE PROCEDIMIENTO)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

Juicio [COMPLETAR] n.º [Nº DE PROCEDIMIENTO]/[AÑO].

AL ILMO. SR. (MAGISTRADO PONENTE DE LA SECCIÓN [COMPLETAR] DE LA AUDIENCIA PROVINCIAL DE [LOCALIDAD] JUEZ TITULAR DE LA SECCIÓN CIVIL DEL TRIBUNAL DE INSTANCIA DE [SEDE], PLAZA N.º [COMPLETAR])

[NOTA DE REVISIÓN: El Tribunal de Instancia es único por partido judicial (art. 84.1 LOPJ); lo que se numera es la plaza dentro de la Sección (DT 1.ª LO 1/2025). En escritos iniciales (demanda, solicitud, petición monitoria) no se indica plaza: «…DEL TRIBUNAL DE INSTANCIA DE [partido]», para reparto. Fuente: LOPJ art. 84.1-2 (redacc. LO 1/2025, BOE-A-2025-76; consolidado BOE-A-1985-12666) y LO 1/2025 DT 1.ª (plazas con la numeración del juzgado de procedencia).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador de los Tribunales, interviniendo en nombre de D./Dña. [NOMBRE Y APELLIDOS], en virtud de la representación que tengo acreditada, comparezco en los autos de Juicio [COMPLETAR] n.º [NÚMERO], y como mejor proceda en Derecho DIGO:

Que en el desarrollo de la fase probatoria del presente procedimiento, y mediante resolución de fecha [FECHA] se ha acordado el nombramiento del Perito [COMPLETAR] (profesión) D./Dña. [NOMBRE Y APELLIDOS] designado por sorteo para la elaboración de un informe pericial sobre [DESCRIBIR]. Encontrándose incurso dicho Perito en causa legal de recusación, mediante el presente escrito promuevo, en tiempo y forma, incidente de RECUSACIÓN contra dicho Perito. Baso la recusación propuesta en los siguientes

HECHOS

Esta parte ha conocido el nombramiento del Perito recusado con fecha [FECHA], lo que acredita que este escrito se interpone dentro de los dos días siguientes a dicha notificación.

Concurre la circunstancia de [COMPLETAR] (detallar causa de recusación). Acredito estos extremos mediante [ÓRGANO], que acompaño reseñado como documento n.º [NÚMERO] (debe acompañarse un “principio de prueba” sobre la causa de recusación). Las circunstancias expresadas también podrán ser corroboradas mediante los siguientes medios de prueba: (determinar medios probatorios de la causa de recusación).

El Procurador firmante tiene conferidas, entre las que constan en su escritura de apoderamiento, facultades especiales para recusar Peritos. Firma también este escrito el Letrado D./Dña. [NOMBRE Y APELLIDOS]

A los hechos antecedentes resultan de aplicación los siguientes

FUNDAMENTOS DE DERECHO

Legitimación

Corresponde a las partes, que, a tenor de lo dispuesto en el art. 125 de la LEC promoverán la recusación mediante escrito firmado por su Abogado y Procurador si intervinieren.

Causas de recusación de peritos

Art. 124 de la LEC: Además de las previstas en la Ley Orgánica del Poder Judicial, son causas de recusación: 1.ª Haber dado anteriormente sobre el mismo asunto dictamen contrario a la parte recusante, ya sea dentro o fuera del proceso. 2.ª Haber prestado servicios como tal Perito al litigante contrario o ser dependiente o socio del mismo. 3.ª Tener participación en la sociedad, establecimiento o empresa que sea parte del proceso.

En el presente supuesto concurre la circunstancia de que el Perito nombrado por sorteo [COMPLETAR] (desarrollar circunstancia y encaje legal de la causa).

Requisitos procesales

El presente escrito de recusación se presenta dentro de los dos días siguientes a la notificación del nombramiento del Perito recusado (art. 125.2 de la LEC).

Se formula este escrito bajo firma del abogado y Procurador de la parte recusante (art. 125.1 de la LEC).

Se acompañan copias del escrito y documentos para el Perito recusado y para las demás partes.

Trámite

Arts. 126 y 127 de la LEC Deberá manifestar el Perito recusado ante el Letrado de la Administración de Justicia si es o no cierta la causa de recusación invocada. Si la acepta, se le tendrá por recusado sin otro trámite y será reemplazado por el suplente. Si la niega o el Letrado de la Administración de Justicia no acepta su conformidad éste convocará a las partes a comparecencia a presencia del Tribunal en el que se practicarán las pruebas que se consideren oportunas, resolviendo seguidamente por auto.

Por lo expuesto,

SUPLICO A LA SALA O AL TRIBUNAL: Que tenga por presentado este escrito, documentos y las copias preceptivas de todo ello que se acompañan, admitiendo a trámite la recusación propuesta contra el Perito [COMPLETAR] (profesión) D./Dña. [NOMBRE Y APELLIDOS] y, en su virtud, acuerde tramitar el correspondiente incidente de recusación, con audiencia del Perito recusado sobre la causa invocada y traslado a las partes de la recusación, dando a la pieza el impulso procedimental pertinente para que en definitiva se estime como cierta la causa de recusación y se tenga por recusado al mencionado Perito y se acuerde su reemplazo por el designado como sustituto.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
