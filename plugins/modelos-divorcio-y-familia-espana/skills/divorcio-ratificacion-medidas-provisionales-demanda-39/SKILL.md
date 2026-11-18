---
name: divorcio-ratificacion-medidas-provisionales-demanda-39
description: "Redacta el escrito «Divorcio con ratificación de medidas provisionales: demanda» (formulario 39 de familia, revisado el 17-11-2026): pide los datos, decide las opciones, aplica las correcciones y comprueba las normas en el BOE. Requiere Jurisprudenciator."
---

# Divorcio con ratificación de medidas provisionales: demanda

> Formulario 0039 del plugin **Familia** · revisado el 17-11-2026.

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
- [ ] NOMBRE Y APELLIDOS (14 veces)
- [ ] NOMBRE DEL REPRESENTADO/A
- [ ] DNI/NIE (2 veces)
- [ ] FECHA (7 veces)
- [ ] IMPORTE (2 veces)
- [ ] Nº DE DOCUMENTO
- [ ] LUGAR
- [ ] Otros 12 datos sin etiqueta, marcados `[COMPLETAR]`. Su contexto en el formulario: «… domicilio a efecto de notificaciones en»; «…dictada»; «…en fecha [FECHA] por el Tribunal»; «…por el Tribunal [COMPLETAR] en los autos»; «… domicilio a efecto de notificaciones en»; «…l régimen económico matrimonial es el de»; «…o matrimonio nació un/una hijo/a llamado»; «…, cuyo nacimiento tuvo lugar el»; «…rajudicial. En este sentido, se acudió a»; «…dictadas por el Tribunal»; «…en el procedimiento»; «…a Ley de Enjuiciamiento Civil esta parte»

## Correcciones de la revisión (3)

El formulario lleva notas de revisión. Aplica lo que dicen y **quítalas** del escrito final.

## Normas que cita el formulario

Compruébalas **todas** con `buscar_articulo` antes de dejarlas en el escrito. Si una ha cambiado, usa la redacción vigente y dilo:

- artículo 104 del Código Civil
- artículo 86 del Código Civil
- art. 437.1 LEC
- art. 5 de la Ley Orgánica 1/2025
- artículo 91 del Código Civil
- artículo 92 del Código Civil
- artículo 93 del Código Civil
- artículo 94 del Código Civil
- artículo 95 del Código Civil
- artículo 96 del Código Civil
- artículo 154 del Código Civil

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

### Formulario 0039 · Divorcio con ratificación de medidas provisionales: demanda

- Año del modelo: 2024
- Revisión 17-11-2026: 3 citas normativas corregidas tras comprobarlas en el BOE; 40 campos de relleno marcados en blanco

> Cómo leerlo: [EN MAYÚSCULAS] = dato que hay que rellenar; [ELEGIR: a / b] = elegir una opción y borrar las demás; [OPCIONAL — incluir si procede] = el párrafo siguiente solo si encaja en el caso; [NOTA DE REVISIÓN: …] = corrección o aviso normativo de la revisión, no forma parte del escrito.

---

Formulario adaptado a la reforma procesal de la LO 1/2025.

A LA SECCIÓN DE FAMILIA, INFANCIA Y CAPACIDAD DEL TRIBUNAL DE INSTANCIA DE [SEDE] QUE POR TURNO CORRESPONDA

[NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).]

D./Dña. [NOMBRE Y APELLIDOS], Procurador/a de los Tribunales y de [NOMBRE DEL REPRESENTADO/A], mayor de edad, con DNI [DNI/NIE] y domicilio a efecto de notificaciones en [COMPLETAR], según se acredita mediante escritura de poder para pleitos que se acompaña, actuando bajo la dirección letrada de D./Dña. [NOMBRE Y APELLIDOS], ante el Tribunal comparezco y como mejor proceda en Derecho,

DIGO:

Que en la representación que ostento, por medio del presente escrito, formulo DEMANDA DE DIVORCIO CON RATIFICACIÓN DE MEDIDAS PROVISIONALES acordadas en Auto de fecha [FECHA] dictada [COMPLETAR] en fecha [FECHA] por el Tribunal [COMPLETAR] en los autos [COMPLETAR], contra D./Dña. [NOMBRE Y APELLIDOS], mayor de edad, con DNI [DNI/NIE] y domicilio a efecto de notificaciones en [COMPLETAR]. Todo ello sobre la base de los siguientes,

HECHOS

PRIMERO.- D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS] contrajeron matrimonio el día [FECHA], tal como se acredita con la certificación literal de matrimonio que se acompaña como Documento núm. 1.

El régimen económico matrimonial es el de [COMPLETAR]

SEGUNDO.- De dicho matrimonio nació un/una hijo/a llamado [COMPLETAR], cuyo nacimiento tuvo lugar el [COMPLETAR], tal como se acredita con el certificado de nacimiento que se acompaña como Documento núm. 2.

TERCERO.- En fecha, transcurridos más de tres meses desde que se celebró el matrimonio, D./Dña. [NOMBRE Y APELLIDOS] y D./Dña. [NOMBRE Y APELLIDOS], por motivos personales y privados, los cónyuges pusieron fin a su convivencia.

CUARTO.- No existen bienes ni compromisos económicos comunes, por lo que, cada cónyuge se hace responsable de las deudas o compromisos económicos de manera independiente a partir de este momento.

(Opcional: Queda, por tanto, disuelta la sociedad de gananciales sin nada más que reclamarse los cónyuges entre sí).

QUINTO.- En fecha [FECHA], D./Dña. [NOMBRE Y APELLIDOS] formuló ante el Tribunal pertinente una solicitud de medidas provisionales previas a la demanda por las que se regulaba el uso de la vivienda familiar, custodia, régimen de visitas y pensión de alimentos.

SEXTO.- El Letrado de la Administración de Justicia citó a los cónyuges y al Ministerio Fiscal a una comparecencia en la que tuvo lugar en fecha [FECHA].

SÉPTIMO.- Al no haberse alcanzado un acuerdo entre las partes, el Tribunal, acordó mediante Auto, las siguientes medidas provisionales previas:

1. La separación provisional de los cónyuges.

2. La revocación de los consentimientos y poderes que cualquiera de los cónyuges hubiera otorgado al otro.

3.(Opcional) El cese de la posibilidad de vincular los bienes privativos del otro cónyuge en ejercicio de la potestad doméstica.

4. La atribución de la guarda y custodia del/ de la hijo/a menor a D./Dña. [NOMBRE Y APELLIDOS], siendo la patria potestad compartida por los progenitores.

(Opcional) La guarda y custodia del/ de la hijo/a menor será compartida por ambos progenitores, fijándose un régimen regulador de la convivencia con ambos caracterizado por la flexibilidad y adaptación a los horarios laborales de ambos progenitores. Todo ello sin perjuicio del derecho de comunicaciones, visitas y estancias con el progenitor con el que conviva el/la menor en cada momento.

5.(Opcional) El siguiente régimen de visitas ().

6.La atribución del uso de la vivienda familiar, así como el mobiliario y ajuar doméstico existente, a D./Dña [NOMBRE Y APELLIDOS] y al hijo/a.

(Opcional) El domicilio familiar es bien privativo de D./Dña [NOMBRE Y APELLIDOS], quien podrá continuar residiendo en el mismo teniendo al /a la menor en los periodos que le corresponda.

7.Fijar en [IMPORTE] euros mensuales la cantidad que deberá abonar D./Dña. [NOMBRE Y APELLIDOS] a D./Dña. [NOMBRE Y APELLIDOS] en concepto de pensión de alimentos a favor del/ de la hijo/a menor. Dicha cantidad se actualizará anualmente de acuerdo con las variaciones que experimente el IPC de los últimos 12 meses que publique el Instituto Nacional de Estadística.

(Opcional) Para atender los gastos ordinarios de manutención, cada progenitor ingresará en la cuenta bancaria abierta a tal efecto, la cantidad de [IMPORTE] con carácter mensual. Dicho importe se abonará entre los días 1 y 5 de cada mes y se actualizará anualmente de acuerdo con las variaciones que experimente el IPC de los últimos 12 meses que publique el Instituto Nacional de Estadística.

Se acompaña dicho Auto como Documento núm. 9.

OCTAVO.- Siendo deseo de mi mandante disolver definitivamente su matrimonio con el/la demandado/a, mediante el presente escrito se interpone demanda de divorcio, conforme a lo dispuesto en los artículos 748 y siguientes de la Ley de Enjuiciamiento Civil, solicitando, además, la ratificación de las medidas acordadas por Auto de fecha

NOVENO.- Previamente a la interposición de la presente demanda, se efectuaron diversas gestiones negociadoras con la parte demandada, con el propósito de cumplir con el requisito de procedibilidad y resolver el litigio de manera amistosa y extrajudicial.

En este sentido, se acudió a [COMPLETAR], no habiendo sido posible alcanzar un acuerdo definitivo.

Se acompaña como documento nº [Nº DE DOCUMENTO]

A los anteriores hechos, le son de aplicación los siguientes,

FUNDAMENTOS DE DERECHO

PRIMERO. - JURISDICCIÓN Y COMPETENCIA

Son competentes los tribunales civiles, de conformidad con lo establecido en el artículo 21.1 de la Ley Orgánica del Poder Judicial y art. 36 de la Ley de Enjuiciamiento Civil.

Asimismo, al amparo de lo establecido en el artículo 769.1 de la Ley de Enjuiciamiento Civil, en relación con lo dispuesto en el art. 85.1º LOPJ, es competente la Sección de Familia, Infancia y Capacidad del Tribunal [NOTA DE REVISIÓN: Denominación legal: Sección de Familia, Infancia y Capacidad. Si no existe en el partido, conoce la Sección Civil o la Única (art. 86.3-4 LOPJ). Fuente: LOPJ arts. 84.2.a) y 86 (redacc. LO 1/2025, BOE-A-2025-76).] de Instancia de esta localidad al ser el del lugar en que se encuentra el domicilio conyugal.

SEGUNDO. – PROCEDIMIENTO Y CUANTÍA

En virtud de lo establecido en los artículos 770 y 771.5 de la Ley de Enjuiciamiento Civil, los efectos y medidas acordados sólo subsistirán si, dentro de los 30 días siguientes a su adopción, se presenta demanda de nulidad, separación o divorcio.

Por su parte, el artículo 104 del Código Civil determina que los efectos y medidas provisionales previas sólo subsistirán si, dentro de los 30 días siguientes a su adopción, se presenta demanda ante el Juez o tribunal competente.

El artículo 753 de la Ley de Enjuiciamiento Civil determina que el presente proceso se tramitará por los cauces del juicio verbal. Asimismo, conforme al apartado 3 del mismo precepto, existiendo menores, el proceso será de tramitación preferente.

TERCERO. – CAPACIDAD Y LEGITIMACIÓN

Las partes poseen capacidad para intervenir en el presente procedimiento, al amparo de lo establecido en el artículo 6 y siguientes de la Ley de Enjuiciamiento Civil y del artículo 86 del Código Civil.

CUARTO. - REPRESENTACIÓN PROCESAL

La parte actora comparece debidamente representada por Abogado y Procurador, tal como prevé el artículo 750 de la Ley de Enjuiciamiento Civil.

QUINTO.- INTERVENCIÓN DEL MINISTERIO FISCAL

De conformidad con lo dispuesto en el artículo 749 de la Ley de Enjuiciamiento Civil, resulta preceptiva la intervención del Ministerio Fiscal.

SEXTO.- CUMPLIMIENTO DE LOS REQUISITOS DE PROCEDIBILIDAD

La presente demanda cumple con los requisitos de procedibilidad exigidos por los arts. 264.4º y 399.3 LEC en relación con el art. 437.1 LEC, así como con lo dispuesto en el art. 5 de la Ley Orgánica 1/2025, de 2 de enero, de medidas en materia de eficiencia del Servicio Público de Justicia.

SÉPTIMO.- FONDO DEL ASUNTO

Resultan de aplicación los siguientes preceptos del Código Civil:

- El artículo 86 del Código Civil en cuanto a la disolución del matrimonio a petición de uno de los cónyuges, siempre que concurran los requisitos previstos en el artículo 81 del mismo texto legal.

- El artículo 91 del Código Civil que establece que la sentencia que se dicte en este procedimiento determinará las medidas que hayan de sustituir a las ya adoptadas con anterioridad con relación a los hijos, la vivienda familiar, el destino de los animales de compañía, las cargas del matrimonio y la liquidación del régimen económico. [NOTA DE REVISIÓN: Paráfrasis del art. 91 CC anterior a la Ley 17/2021. Fuente: Código Civil (BOE-A-1889-4763) art. 91, redacción Ley 17/2021 (BOE-A-2021-20727).]

- El artículo 92 del Código Civil que establece:

a)En su apartado primero, que la separación, nulidad o divorcio no exime a los padres de sus obligaciones para con los hijos.

b)En su apartado segundo, que el Juez debe velar por el cumplimiento del derecho de los menores a ser oídos y emitir una resolución motivada en interés del menor.

c)En su apartado sexto, que, antes de acordar el régimen de guarda y custodia, el Juez deberá recabar del informe del Ministerio Fiscal, oír al menor que tenga suficiente juicio cuando se estime necesario de oficio o a petición del Fiscal, las partes o miembros del Equipo Técnico Judicial, o del propio menor, y valorar las alegaciones de las partes, la prueba practicada, y la relación que los padres mantengan entre sí y con sus hijos para determinar su idoneidad con el régimen de guarda.

- El artículo 93 del Código Civil en cuanto a la contribución de los progenitores para satisfacer los alimentos del/ de la menor, así como al resto de medidas convenientes para asegurar la efectividad y acomodación de las prestaciones a las circunstancias económicas y necesidades de los hijos en cada momento.

- El artículo 94 del Código Civil en cuanto al establecimiento de un régimen de visitas.

- El artículo 95 del Código Civil en cuanto a la disolución del régimen económico matrimonial.

- El artículo 96 del Código Civil en cuanto al uso de la vivienda familiar.

- El artículo 154 del Código Civil en cuanto al ejercicio de la patria potestad.

OCTAVO.- IURA NOVIT CURIA

En todo lo no invocado en la presente demanda, opera el principio iura novit curia.

NOVENO.- REGISTROS PÚBLICOS

De acuerdo con el artículo 755 de la Ley de Enjuiciamiento Civil, “el letrado de la Administración de Justicia acordará que las sentencias y demás resoluciones dictadas en los procedimientos a que se refiere este Título se comuniquen de oficio a los Registros Civiles para la práctica de los asientos que correspondan."

DÉCIMO.- COSTAS

Deberán ser impuestas a la parte demandada en virtud de lo establecido en el artículo 394 de la Ley de Enjuiciamiento Civil.

En su virtud,

AL TRIBUNAL SUPLICO: Que teniendo por presentado este escrito junto con sus copias y documentos que le acompañan, se sirva admitirlo, teniendo por formulada DEMANDA DE DIVORCIO CON RATIFICACIÓN DE LAS MEDIDAS PROVISIONALES adoptadas en Auto de [FECHA] dictadas por el Tribunal [COMPLETAR] en el procedimiento [COMPLETAR] contra D./Dña. [NOMBRE Y APELLIDOS] y, en su virtud, previos los trámites legales oportunos, dicte en su día sentencia por la que, estimando íntegramente la demanda, acuerde el divorcio de mi mandante y el/la demandado/a, manteniéndose las medidas establecidas en el mencionado Auto y que se han dado por reproducidas en el Hecho Séptimo de la demanda.

OTROSI PRIMERO DIGO: Que en virtud de lo establecido en el artículo 231 de la Ley de Enjuiciamiento Civil esta parte [COMPLETAR]

AL TRIBUNAL SUPLICO: Que tenga por hecha la anterior manifestación a los efectos oportunos.

En [LUGAR], a [FECHA].

Ldo.

Proc.
