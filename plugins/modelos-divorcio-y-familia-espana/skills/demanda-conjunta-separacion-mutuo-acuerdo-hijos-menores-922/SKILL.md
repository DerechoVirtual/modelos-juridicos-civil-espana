---
name: demanda-conjunta-separacion-mutuo-acuerdo-hijos-menores-922
description: "Redacta el escrito «Demanda conjunta de separación de mutuo acuerdo con hijos menores o con apoyos» (formulario 922 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Demanda conjunta de separación de mutuo acuerdo con hijos menores o con apoyos

> Formulario 0922 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (10 veces)
- [ ] FECHA (4 veces)
- [ ] Nº DE DOCUMENTO (3 veces)
- [ ] Nº
- [ ] NÚMERO
- [ ] LUGAR
- [ ] DÍA
- [ ] MES
- [ ] AÑO
- [ ] Otros 10 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… que acompañamos como documentos números»; «…ntrajeron matrimonio (civil canónico) en»; «…bajo el régimen económico de»; «…ron que el régimen económico sería el de»; «…De esa unión han nacido»; «…hijos: el día [FECHA] y»; «…el día [FECHA] y que cuentan, por tanto»; «…y [Nº] años»; «…años [COMPLETAR] es menor de edad, y»; «…o domicilio familiar ha estado fijado en»

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 81.1 del CC
- art. 777 de la LEC
- art. 10 de la LEC
- arts. 44 y 81 del CC
- art. 749.2 de la LEC
- art. 750 de la LEC
- arts. 775.2 y 777.9 LEC
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

### Formulario 0922 · Demanda conjunta de separación de mutuo acuerdo con hijos menores o con apoyos

- Año del modelo: 2013
- Revisión 17-11-2026: 2 citas normativas corregidas tras comprobarlas en el BOE; 28 campos de relleno marcados en blanco; 3 huecos del original que se habían perdido sin marca, marcados (Nº DE DOCUMENTO)
- Avisos de la revisión: (media) Afirma que el mutuo acuerdo «no está sujeto» a MASC: el art. 5.2 LO 1/2025 no lo excluye. Más seguro decir que el requisito se cumple con la negociación directa reflejada en el convenio firmado por ambas partes (arts. 5.1 y 10.2 LO 1/2025).

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Demanda de separación de mutuo acuerdo

A LA SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD DEL TRIBUNAL DE INSTANCIA DE [SEDE]

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

(Opciones)

D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS], Procuradores de los Tribunales, en nombre y representación de D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] según acreditamos mediante certificaciones del Registro Electrónico de Apoderamientos Judiciales que acompañamos como documentos números [COMPLETAR] y en los que constan sus datos personales, ante el Tribunal comparecemos bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] y como mejor proceda en derecho DECIMOS:

Que mediante el presente escrito y según permite el art. 81.1 del CC, interponemos DEMANDA DE SEPARACIÓN CONYUGAL que se tramitará por el cauce del mutuo acuerdo. De esta demanda deberá darse traslado al Ministerio Fiscal al existir hijos menores de edad. Basamos esta pretensión en los siguientes

HECHOS

Se presenta listado de documentos que acompañan a la demanda.

PRIMERO.— D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] contrajeron matrimonio (civil canónico) en [COMPLETAR] el día [FECHA] bajo el régimen económico de [COMPLETAR], según acredito mediante certificado del Registro Civil que acompaño como documento n.º [Nº DE DOCUMENTO]

(En su caso) En capitulaciones matrimoniales acordaron que el régimen económico sería el de [COMPLETAR], según acreditamos con escritura pública que adjuntamos como documento n.º [Nº DE DOCUMENTO]

De esa unión han nacido [COMPLETAR] hijos: el día [FECHA] y [COMPLETAR] el día [FECHA] y que cuentan, por tanto [COMPLETAR] y [Nº] años [COMPLETAR] es menor de edad, y [COMPLETAR] mayor, pero dependiente económicamente al carecer de ingresos propios y encontrarse en periodo de formación académica.

El ultimo domicilio familiar ha estado fijado en [COMPLETAR]

Los cónyuges de mutuo acuerdo han decidido presentar esta demanda de separación conyugal y someter a aprobación del Tribunal el convenio regulador suscrito por ambos de fecha [FECHA] que presentan como documento n.º [Nº DE DOCUMENTO]

(En su caso) Acompañamos el acuerdo alcanzado en el procedimiento de mediación familiar que ha servido de base para la elaboración de la propuesta de convenio regulador (Doc. n.º [NÚMERO])

La demanda de separación de mutuo acuerdo no devenga tasa judicial.

FUNDAMENTOS DE DERECHO

Jurisdicción y competencia

Los arts. 21, 22 y 86.5.a) de la LOPJ y 36, 46 y 769 de la LEC atribuyen a la jurisdicción española y a las Secciones de Familia, Infancia y Capacidad de los Tribunales de Instancia el conocimiento de esta materia. Será competente el Tribunal del último domicilio del matrimonio y, en los partidos con sección especializada de Familia, es éste el que conoce del asunto.

Tramitación

Se seguirá el cauce establecido en el art. 777 de la LEC, citando el Letrado de la Administración de Justicia a las partes para ratificar el convenio.

Legitimación

Están legitimados los cónyuges en aplicación del art. 10 de la LEC con relación a los arts. 44 y 81 del CC.

(En su caso) El art. 749.2 de la LEC exige la intervención del Ministerio Fiscal en estos pleitos cuando existan hijos menores o personas con discapacidad. [NOTA DE REVISIÓN: El art. 749.2 LEC ya no habla de «incapacitados». Fuente: LEC 1/2000 (BOE-A-2000-323) art. 749.2, redacción Ley 8/2021 (BOE-A-2021-9233): «sea menor, persona con discapacidad o esté en situación de ausencia legal».]

Postulación

Según exige el art. 750 de la LEC las partes deberán comparecer representadas por procurador y asistidas de letrado, aunque en los juicios de separación de mutuo acuerdo se permite que los cónyuges se valgan de una única representación y defensa.

Cumplimiento de los requisitos de procedibilidad

La presente demanda no está sujeta al previo intento de resolución de controversias en vía no jurisdiccional, de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia, por tratarse en sí de un acuerdo consensual y voluntario entre las partes, necesitando únicamente la homologación del mismo por parte del Tribunal, siendo que el convenio regulador (arts. 775.2 y 777.9 LEC y 90.3 CCiv) se entiende acreditativo de haber realizado esa actividad negociadora.

Fondo del asunto

PRIMERO.— El art. 81.1 del CC dice que se decretará judicialmente la separación cuando existan hijos menores no emancipados o hijos mayores respecto de los que se hayan establecido judicialmente medidas de apoyo atribuidas a sus progenitores, cualquiera que sea la forma de celebración del matrimonio, a petición de ambos cónyuges una vez transcurridos tres meses desde la celebración del matrimonio.

SEGUNDO.— El precepto anteriormente citado exige en su último inciso que a la demanda se acompañe un convenio regulador redactado conforme al art. 90 del CC. En la redacción del convenio se ha respetado lo establecido en los arts. 92 a 97 del mismo texto legal sobre las concretas cuestiones que debe recoger.

TERCERO.— La sentencia que se dicte tendrá acceso, art. 755 de la LEC, al Registro Civil mediante actuación de oficio del Letrado de la Administración de Justicia y en aplicación del art. 263 del Reglamento del Registro Civil, la inscripción precisará su alcance y las determinaciones sobre patria potestad y cuidado de los hijos.

CUARTO.— (En su caso) Antes de la presentación de esta demanda las partes se sometieron a mediación familiar, alcanzando el acuerdo que acompaña a este escrito, conforme previene el art. 777.2 de la LEC.

Por lo expuesto,

SUPLICAMOS AL TRIBUNAL: Que tenga por presentado este escrito con los documentos que acompañamos, admita a trámite la presente demanda, acuerde el Letrado de la Administración de Justicia citar a los cónyuges a la ratificación del convenio regulador y, en su día, se dicte sentencia por la que se acuerde la separación conyugal de D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] y se apruebe en todos sus términos el convenio regulador suscrito por ambos, así como que el se acuerde lo necesario, una vez firme la sentencia, para su inscripción en el Registro Civil.

Es justicia que pedimos en [LUGAR], a [DÍA] de [MES] de [AÑO].

========================================================================
