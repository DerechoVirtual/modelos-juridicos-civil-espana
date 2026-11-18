---
name: solicitud-adopcion-art-176-2-1-cc-518
description: "Redacta el escrito «Solicitud de adopción (art. 176.2.1.ª CC)» (formulario 518 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Solicitud de adopción (art. 176.2.1.ª CC)

> Formulario 0518 del plugin **Familia** · revisado el 17-11-2026.

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

- [ ] NOMBRE Y APELLIDOS (8 veces)
- [ ] Nº DE DOCUMENTO (2 veces)
- [ ] NÚMERO (3 veces)
- [ ] COLEGIO
- [ ] CALLE (2 veces)
- [ ] FECHA (6 veces)
- [ ] Nº
- [ ] LOCALIDAD (2 veces)
- [ ] LUGAR
- [ ] Otros 23 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «…Procurador/a de los Tribunales, y de D.»; «…de»; «…UD DE CONSTITUCIÓN DE ADOPCIÓN del menor»; «…s: 1.ª) Que mi mandante es hermano de D.»; «…ón de ambos que hacen documentos números»; «…a»; «…Que en el momento de su fallecimiento D.»; «…, tenían un hijo, de nombre»; «…nacido el día [FECHA] en»; «…ue desde el fallecimiento de sus padres,»; «…o de los familiares, tratando aquél a D.»; «…llo que, tras dos años de convivencia de»; …

## Elecciones que hay que hacer

- SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL

## Partes que tienes que redactar tú

El original solo traía los rótulos de estas opciones o varias alternativas seguidas. Redacta la que corresponda con la norma vigente y los hechos, y avísalo al entregar:

- ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS

## Párrafos opcionales (1)

Inclúyelos solo si encajan en los hechos:

- También se adjunta resolución de fecha [FECHA] por la que mi mandante, en la actualidad tutor del menor, ha re…

## Correcciones de la revisión (2)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- art. 176 CCiv
- arts. 35.3 y 4 LJV
- art. 37 LJV
- art. 177 CCiv
- arts. 109 CCiv
- arts. 2 y 33 LJV
- arts. 3 y 34.2 LJV
- art. 175 CCiv
- arts. 4 y 34.1 LJV
- art. 39.5 LJV

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

### Formulario 0518 · Solicitud de adopción (art. 176.2.1.ª CC)

- Año del modelo: 2016
- Revisión 17-11-2026: 1 puntualizaciones normativas añadidas en el texto; 1 bloques de alternativas señalados; 1 párrafos opcionales señalados; 47 campos de relleno marcados en blanco; encabezamiento ajustado a los Tribunales de Instancia (plaza / Sección; LO 1/2025); 1 huecos del original que se habían perdido sin marca, marcados (NOMBRE Y APELLIDOS)

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Modelo de solicitud del adoptante interesando el inicio de expediente de jurisdicción voluntaria de adopción de pariente del adoptante en tercer grado por consanguinidad o afinidad.

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA [ELEGIR: SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD / SECCIÓN CIVIL] DEL TRIBUNAL DE INSTANCIA DE ()

[NOTA DE REVISIÓN: Regla general: el TI tiene Sección Única, de Civil y de Instrucción; solo en los partidos que fija la Ley 38/1988 hay Sección Civil separada. Donde no la haya: «A LA SECCIÓN ÚNICA, DE CIVIL Y DE INSTRUCCIÓN, DEL TRIBUNAL DE INSTANCIA DE…». Fuente: LOPJ art. 84.2 (redacc. LO 1/2025, BOE-A-2025-76).]

[NOTA DE REVISIÓN: desde la LO 1/2025 la familia, la infancia y los apoyos corresponden a la Sección de Familia, Infancia y Capacidad del Tribunal de Instancia (arts. 84.2.a y 86 LOPJ); donde no exista, a la Sección Civil o Única.]

D./Dña. [NOMBRE Y APELLIDOS] Procurador/a de los Tribunales, y de D. [COMPLETAR], según acredito mediante certificación del Registro Electrónico de Apoderamientos Judiciales que acompaño como documento nº [Nº DE DOCUMENTO], a quien asiste el Letrado/a en ejercicio D./Dña. [NOMBRE Y APELLIDOS], colegiado/a n.º [NÚMERO] del Iltre. Colegio de Abogados de [COLEGIO], con despacho abierto en esta localidad, calle [CALLE] de [COMPLETAR], ante el Tribunal comparezco y como mejor proceda en Derecho DIGO:

Que por el presente escrito, en la representación que acredito y siguiendo instrucciones de mi mandante promuevo EXPEDIENTE DE JURISDICCIÓN VOLUNTARIA EN SOLICITUD DE CONSTITUCIÓN DE ADOPCIÓN del menor [COMPLETAR], todo ello de conformidad con lo previsto en el art. 176 CCiv y 33 y ss. LJV y en base a los siguientes:

Hechos y consideraciones jurídicas:

1.ª) Que mi mandante es hermano de D. [COMPLETAR]. y cuñado de Dña. [NOMBRE Y APELLIDOS], ambos tristemente fallecidos el pasado día [FECHA] en un desgraciado accidente de circulación, como se demuestra con la copia del atestado policial del expresado accidente y certificados de defunción de ambos que hacen documentos números [COMPLETAR] a [COMPLETAR].

2.ª) Que en el momento de su fallecimiento D. [COMPLETAR]. y Dña. [NOMBRE Y APELLIDOS], tenían un hijo, de nombre [COMPLETAR] nacido el día [FECHA] en [COMPLETAR], que cuenta con [Nº] años de edad en la actualidad, por lo tanto menor de edad, según se acredita con el certificado de nacimiento que se acompaña como documento número [Nº DE DOCUMENTO], sin que conste a mi mandante que el mismo esté emancipado.

3.ª) Que desde el fallecimiento de sus padres, [COMPLETAR]. convive con mi mandante, donde se ha integrado en el grupo familiar, constituido por la esposa del mismo y sus primos, y es visitado además por el resto de los familiares, tratando aquél a D. [COMPLETAR]. como si de su verdadero progenitor se tratara.

Es por ello que, tras dos años de convivencia de [COMPLETAR]. con mi mandante y su familia, y de estar designado el mismo como tutor del menor en resolución de fecha [FECHA], mi mandante considera que lo mejor para su sobrino es que el mismo se integre de forma jurídico plena en la unidad familiar de la que ya participa desde hace tiempo, por lo que interesa su adopción al entender que además de ser su interés y voluntad, la misma redundará en beneficio del mismo.

4.ª) Que mi representado es mayor de veinticinco años y tiene una diferencia de edad con el adoptando superior a dieciséis años, tal como se acredita por el certificado de nacimiento acompañados como documento n.º [NÚMERO].

No se aporta declaración previa de idoneidad del adoptante para el ejercicio de la patria potestad emitida por la Entidad Pública, por cuanto conforme a lo previsto en el art. 176 CCiv y los hechos expuestos no es el mismo preceptivo.

5.ª) Que en relación a la indicación de las condiciones personales, familiares y sociales y los medios de vida del adoptante y sus relaciones con el adoptando, la capacidad del solicitante para asumir las obligaciones que le corresponden como padre adoptivo está más que probada, por cuanto además de contar con suficientes recursos económicos (se aportan declaraciones de IRPF del solicitante de los últimos cinco años), ya se ha hecho mención expresa a que el menor [COMPLETAR] reside desde hace años con mi mandante, que es su tío, la esposa del mismo Dña. [NOMBRE Y APELLIDOS] y sus primos hermanos, en el domicilio del primero sito en la calle [CALLE] de [COMPLETAR] según se justifica con el certificado de empadronamiento, estando el menor matriculado en el mismo colegio al que acuden los hijos de mi mandante y realizando vida conjunta con todos ellos desde el primer momento del fallecimiento de sus padres, tanto a nivel personal, familiar y escolar según se acredita con el informe del colegio al que acude el menor y las notas de éste, a través de las que se advierte su plena integración escolar.

Se acompañan adjuntos documentos números [COMPLETAR] a [COMPLETAR], ofrecimiento por escrito para la adopción por parte del adoptante e informes y documentos de interés en prueba de lo anterior, conforme a los arts. 35.3 y 4 LJV.

[OPCIONAL — incluir si procede]

También se adjunta resolución de fecha [FECHA] por la que mi mandante, en la actualidad tutor del menor, ha rendido la cuenta anual del ejercicio de su cargo tutelar sin objeción por parte del Tribunal o del Ministerio Fiscal, cumpliendo así la exigencia del art. 175.3.3.º CCiv.

6.ª) Que en relación a los consentimientos, asentimientos y audiencias que son preceptivas para la válida constitución de la adopción, a los efectos de lo establecido por el art. 37 LJV en relación al art. 177 CCiv, el adoptando deberá consentir la adopción por ser mayor de 12 años y se tendrá que recabar el consentimiento de mi mandante en su calidad de adoptante.

[ELEGIR UNA DE LAS ALTERNATIVAS QUE SIGUEN Y SUPRIMIR LAS DEMÁS]

Asimismo, deberá prestar su asentimiento Dña. [NOMBRE Y APELLIDOS], cónyuge de mi mandante, sin que haya más personas en condiciones de asentir la adopción y, sin que la misma haya efectuado de forma previa el indicado asentimiento en documento público, debiendo ser citada en el mismo domicilio de mi mandante, sito en [LOCALIDAD].

En relación a Dña. [NOMBRE Y APELLIDOS], cónyuge de mi mandante, no será preceptiva su citación por cuanto la misma prestó su asentimiento en documento público que se adjunta a la presente solicitud, al efecto, acta de fecha [FECHA] otorgada ante el Notario de [COMPLETAR], D./Dña. [NOMBRE Y APELLIDOS], bajo el número [NÚMERO] de su protocolo.

7.ª) Que en cuanto a la extinción de los vínculos jurídicos del adoptado con su familia anterior, una vez constituida la adopción, conforme a lo dispuesto en los arts. 109 CCiv y 201 RRC, el adoptado ostentará los apellidos del adoptante.

Consecuentemente deberá acordarse la sustitución del segundo apellido, de [COMPLETAR]), por el de [COMPLETAR] quedando [COMPLETAR] como nombre y apellidos del mismo.

8.ª) Que es competente el Tribunal de Instancia al que me dirijo a tenor de lo previsto en los arts. 2 y 33 LJV en relación con lo dispuesto en el art. 85.1º LOPJ, por ser el del lugar del domicilio del adoptante, sin que quepa modificarla por sumisión expresa o tácita.

9.ª) Que mi representado está legitimado activamente para el ejercicio de la solicitud efectuada en petición de adopción, conforme a lo dispuesto en los arts. 176.2.1.ª CCiv y 35.3 LJV, por cuanto concurre la circunstancia de ser el adoptando sobrino de mi mandante, y huérfano de padre y madre, no siendo necesario entonces la propuesta previa de la entidad pública.

10.ª) Que conforme a lo dispuesto en los arts. 3 y 34.2 LJV la solicitud está firmada por abogado y procurador, pese a que su intervención no es preceptiva en el caso de autos.

11.ª) Que la presente solicitud deberá ser tramitada por las normas establecidas para la jurisdicción voluntaria en los arts. 17 a 20 y 33 y ss. LJV.

12.ª) Que se cumplen todos los requisitos legales establecidos en el art. 175 CCiv para la adopción, en cuanto a las edades de adoptante y de adoptando, diferencias de edad entre los mismos, y no hallarse incurso en ninguna de las prohibiciones establecidas en el precepto.

13.ª) Que conforme a los arts. 4 y 34.1 LJV la tramitación del expediente de adopción se practicará con intervención del Ministerio Fiscal.

14.ª) Que el testimonio de la resolución firme en que se acuerde la adopción deberá remitirse al Registro Civil para que se practique su inscripción, conforme al art. 39.5 LJV.

Por todo lo expuesto,

SUPLICO AL TRIBUNAL

que teniendo por presentado este escrito con los documentos y copias que se acompañan, se inicie EXPEDIENTE DE JURISDICCIÓN VOLUNTARIA EN SOLICITUD DECONSTITUCIÓN DE ADOPCIÓN por mi mandante del menor [COMPLETAR] y, tras recabar todos los consentimientos y asentimientos requeridos al efecto, todo ello con intervención del Ministerio Fiscal, en interés del menor, se sirva dicte Auto constituyendo la adopción solicitada, con todos los efectos legales inherentes al respecto, designando como adoptante a D. [COMPLETAR], acordando igualmente que en adelante el adoptado pase a llamarse [COMPLETAR], librándose, una vez firme la resolución, testimonio de la misma para su inscripción en el Registro Civil de [LOCALIDAD], junto a lo demás que en Derecho proceda.

Por ser de Justicia que pido en [LUGAR], a [FECHA].

Firma de Abogado/a	Firma de Procurador/a

========================================================================
