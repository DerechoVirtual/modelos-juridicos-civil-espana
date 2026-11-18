---
name: demanda-separacion-conyuge-consentimiento-otro-sin-hijos-1155
description: "Redacta el escrito «Demanda de separación de un cónyuge con consentimiento del otro y sin hijos dependientes» (formulario 1155 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda de separación de un cónyuge con consentimiento del otro y sin hijos dependientes

> Formulario 1155 del plugin **Familia** · revisado el 17-11-2026.

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

## Antes de usarlo: avisos de la revisión

El planteamiento del formulario está desfasado en algo. Corrígelo antes de redactar:

- (media) Afirma que el mutuo acuerdo «no está sujeto» a MASC: el art. 5.2 LO 1/2025 no lo excluye. Más seguro decir que el requisito se cumple con la negociación directa reflejada en el convenio firmado por ambas partes (arts. 5.1 y 10.2 LO 1/2025).

## Qué tienes en esta carpeta

- «Texto del formulario», al final de este fichero: el texto del formulario revisado, con las marcas de la revisión.
- `../indice/marco.md` (en la carpeta de la skill `indice` de este plugin): guía del tema con las reglas y plazos vigentes comprobados en el BOE.

## Datos que hay que pedir al usuario

Pídelos en una sola tanda. Si un dato aparece varias veces, aclara a qué persona o acto corresponde cada vez.

- [ ] SEDE
- [ ] NOMBRE Y APELLIDOS (8 veces)
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] LOCALIDAD
- [ ] DNI/NIE
- [ ] FECHA (2 veces)
- [ ] NÚMERO (3 veces)
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 6 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…contrajeron matrimonio»; «…(civil canónico) en»; «…bajo el régimen económico de»; «…ron que el régimen económico sería el de»; «…rimonio no han nacido hijos. 2.º Existen»; «…amente. El domicilio familiar se fijó en»

## Correcciones de la revisión (1)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 81.1 del CC
- art. 777 de la LEC
- art. 10 de la LEC
- arts. 44 y 81 del CC
- art. 750 de la LEC
- arts. 775.2 y 777.9 LEC
- art. 82 CC
- art. 90 del CC
- art. 755 de la LEC
- art. 777.2 de la LEC
- Ley Orgánica 1/2025

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

### Formulario 1155 · Demanda de separación de un cónyuge con consentimiento del otro y sin hijos dependientes

- Año del modelo: 2013
- Revisión 17-11-2026: 1 citas normativas corregidas tras comprobarlas en el BOE; 24 campos de relleno marcados en blanco; 2 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO)
- Avisos de la revisión: (media) Afirma que el mutuo acuerdo «no está sujeto» a MASC: el art. 5.2 LO 1/2025 no lo excluye. Más seguro decir que el requisito se cumple con la negociación directa reflejada en el convenio firmado por ambas partes (arts. 5.1 y 10.2 LO 1/2025).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda de separación con consentimiento de la otra parte

A LA SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD DEL TRIBUNAL DE INSTANCIA DE [SEDE], para el Letrado de la Administración de Justicia

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], en el que constan sus datos personales, ante el Tribunal comparezco bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DIGO:

Que mediante el presente escrito y según permite el art. 81.1 del CC, formulo DEMANDA DE SEPARACIÓN CONYUGAL con el consentimiento de D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con domicilio en [LOCALIDAD] y DNI n.º [DNI/NIE] que deberá ser citado para el acto de la ratificación. Basamos esta pretensión en los siguientes

HECHOS

Se presenta listado de documentos que acompañan a la demanda.

D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] contrajeron matrimonio [COMPLETAR] (civil canónico) en [COMPLETAR] el día [FECHA] bajo el régimen económico de [COMPLETAR], según acredito mediante certificado del Registro Civil que acompaño como documento n.º [NÚMERO] (En su caso) En capitulaciones matrimoniales acordaron que el régimen económico sería el de [COMPLETAR], según acreditamos con escritura pública que adjuntamos como documento n.º [Nº DE DOCUMENTO]

(Opciones):

1.º De este matrimonio no han nacido hijos.

2.º Existen [COMPLETAR] hijos comunes, según se acredita con certificados del Registro Civil que acompañamos como documentos n.º [NÚMERO], pero todos ellos son mayores de edad e independientes económicamente.

El domicilio familiar se fijó en [COMPLETAR]

Los cónyuges de mutuo acuerdo han decidido suscribir el convenio regulador de fecha [FECHA] que se presenta para su aprobación por el Letrado de la Administración de Justicia como documento n.º [Nº DE DOCUMENTO]

(En su caso) Acompaño el acuerdo alcanzado en el procedimiento de mediación familiar que ha servido de base para la elaboración de la propuesta de convenio regulador (Doc. n.º [NÚMERO])

FUNDAMENTOS DE DERECHO

Jurisdicción y competencia

Los arts. 21, 22 y 86.5.a) de la LOPJ y 36, 46 y 769 de la LEC atribuyen a la jurisdicción española y a las Secciones de Familia, Infancia y Capacidad de los Tribunales de Instancia el conocimiento de esta materia. Será competente el Tribunal del último domicilio del matrimonio y, en los partidos con sección especializada de Familia, es éste el que conoce del asunto.

Tramitación

Se seguirá el cauce establecido en el art. 777 de la LEC, citando el Letrado de Administración de Justicia a las partes para ratificar el convenio.

Las partes comparecerán ante el Letrado de la Administración de Justicia quien, una vez practicada la ratificación de los cónyuges, dictará decreto declarando la separación conyugal y aprobando el convenio que se presenta.

Legitimación

Están legitimados los cónyuges en aplicación del art. 10 de la LEC con relación a los arts. 44 y 81 del CC.

Postulación

Según exige el art. 750 de la LEC esta parte comparece representada por procurador y asistida de letrado.

Cumplimiento de los requisitos de procedibilidad

La presente demanda no está sujeta al previo intento de resolución de controversias en vía no jurisdiccional, de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia, por tratarse en sí de un acuerdo consensual y voluntario entre las partes, necesitando únicamente la homologación del mismo por parte del Tribunal, siendo que el convenio regulador (arts. 775.2 y 777.9 LEC y 90.3 CCiv) se entiende acreditativo de haber realizado esa actividad negociadora.

Fondo del asunto

PRIMERO.— El art. 82 CC permite acordar la separación de mutuo acuerdo transcurridos tres meses desde la celebración del matrimonio mediante la formulación de un convenio regulador ante el Letrado de la Administración de Justicia.

SEGUNDO.— El precepto anteriormente citado exige que a la demanda se acompañe un convenio regulador redactado conforme al art. 90 del CC. En la redacción del convenio se ha respetado lo establecido en los arts. 92 a 97 del mismo texto legal sobre las concretas cuestiones que debe recoger.

TERCERO.— La sentencia que se dicte tendrá acceso, art. 755 de la LEC, al Registro Civil mediante actuación de oficio del Letrado de la Administración de Justicia y en aplicación del art. 263 del Reglamento del Registro Civil, la inscripción precisará su alcance.

CUARTO.— (En su caso) Antes de la presentación de esta demanda las partes se sometieron a mediación familiar, alcanzando el acuerdo que acompaña a este escrito, conforme previene el art. 777.2 de la LEC.

Por lo expuesto,

SUPLICO AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompaño admitiendo a trámite la presente demanda, acuerde el Letrado de la Administración de Justicia citar a los cónyuges a la ratificación del convenio regulador y, en su día, dicte decreto por la que se acuerde la separación conyugal de D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] aprobando en todos sus términos el convenio regulador suscrito por ambos y acordando lo necesario para su inscripción en el Registro Civil.

Es justicia que pido en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
